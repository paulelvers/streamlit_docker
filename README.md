# streamlit_docker

A slim base repository for a [streamlit](https://streamlit.io/) app in a docker container.

### The project structure

```
├── Dockerfile         <- needed to built the docker image with your app in it.      
├── app
│   ├── app.py         <- this is were your main source code will live.
│
├── requirements.txt   <- here you add all dependencies needed for your app.
├── README.md    
├── LICENSE
```

### The Dockerfile
```
FROM python:3.7
EXPOSE 8501
WORKDIR /app
COPY requirements.txt ./requirements.txt
RUN pip3 install -r requirements.txt
COPY ./app /app
CMD streamlit run app.py
```

# Quickstart

#### 1. Fork the repository
```bash
$ git fork https://github.com/paulelvers/streamlit_docker
```  

#### 2. Navigate into the directory
```bash
$ cd streamlit_docker
```  

#### 3. Build the docker image
```bash
$ docker build -t streamlit_app:latest .
```  
The `.` dot tells docker to build from the Dockerfile in your current directory.
With `-t` you will set a tag (a name for the image) and add a version like this `name:version`

#### 4. Run the image
```bash
$ docker run -p 8501:8501 streamlit_app
```  
With `-p` you map the port of the docker container (5401) to your localhost (5401).
and `streamlit_app` tells the docker run command, which image to run.

#### 5. Visit your app on your local machine
Open your browser and go to `http://localhost:8501`.

Now you should be able to interact with your app.


### Develop yourself
No you can start developing your own application. Just change the source code in app.py
add more python modules and additional dependencies (which you should always add to requirements.txt).

Have a look at the [Streamlit Gallery](https://streamlit.io/gallery), if you need some inspiration.
