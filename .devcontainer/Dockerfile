# start from CUDA 10 image and with OpenGL
FROM nvidia/cudagl:10.2-devel-ubuntu18.04


# install all required dependencies
RUN apt-get update && \
     apt-get install -y wget git && \
     apt-get install -y libglib2.0-dev libsm6 libxext6 libxrender-dev libxt6 && \
     apt-get install -y fonts-dejavu && \
     apt-get clean all && \
     rm -rf /var/lib/apt/lists/*

# install conda
ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
RUN wget \
    https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && mkdir /root/.conda \
    && bash Miniconda3-latest-Linux-x86_64.sh -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh


# create Total3D environment
COPY environment.yml /root/environment.yml
RUN conda env create -f /root/environment.yml
SHELL ["/bin/bash", "-c"]

RUN conda init bash && \
    echo -e "\nconda  activate Total3D\n" >> /root/.bashrc