FROM ubuntu:latest

# Run a system update to get it up to speed
# Then install python and pip
RUN apt-get update && apt-get install -y python \
    python-pip

# Install jupyter
RUN pip install jupyter

# install git
RUN apt-get install git-core -y

# Create a new system user
RUN useradd -ms /bin/bash jupyter

# Change to this new user
USER jupyter

# Set the container working directory to the user home folder
WORKDIR /home/jupyter/

#RUN echo "$PWD"
# Clone the desired repo
RUN git clone https://github.com/sid0972/JupyterOneClick.git

#Change workdir to cloned repo
WORKDIR /home/jupyter/JupyterOneClick

#Display current directory
RUN echo "$PWD"

RUN cat jupyterServer.ipynb

#COPY the file to the jupyter directory
#COPY jupyterServer1.ipynb /home/jupyter/

#Convert the jupyter notebook to python script
RUN jupyter nbconvert --to python jupyterServer1.ipynb

#copy the converted script to jupyter folder
#COPY jupyterServer1.py /home/jupyter

EXPOSE 8888

#RUN cat jupyterServer1.py 

#execute the script 
ENTRYPOINT ["python","-m","jupyterServer1.py","8888"]