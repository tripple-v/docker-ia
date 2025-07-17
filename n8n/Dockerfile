FROM docker.n8n.io/n8nio/n8n:latest

USER root

RUN apk update && \
    apk add --no-cache \
      cmake \
      build-base \
      wget \
      libsndfile \
      ffmpeg \
      git

# Cloner et compiler whisper.cpp
WORKDIR /home/node/whisper
RUN git clone https://github.com/ggerganov/whisper.cpp.git . \
  && mkdir build && cd build \
  && cmake .. && make

# Télécharger le modèle medium
RUN cd /home/node/whisper/models \
  && ./download-ggml-model.sh medium

USER node