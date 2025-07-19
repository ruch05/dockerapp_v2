

## 🚀 Docker App - Second Project

This is the second project where we carry over from [`Docker_Mongo`](https://github.com/ruch05/Docker_Mongo) and after running all the commands manually, we reach to a place where we made a docker compose file through which we run **MongoDB** and **Mongo Express**, while the app was first run individually with:

```
node server.js
```

Then we learnt about a **Dockerfile** which will dockerize our app and create an image when we build the app with the command:

```
docker build -t app_name:v1 .
```

This creates an image that we can share with our teams and they can simply use it by running a container from this image. **Amazing, right?!**

---

Now, we have an image and we run a container:

```
docker run -p5050:5050 --network docker-testapp_default testapp:1.6
```

We need to pass the port and network variables here as flags and then again saving these variables in a file could be useful if we were to edit something or the command becomes super long or we need to run multiple containers, so our solution to that was:

 **DOCKERRRRRRRRRRRRRR drumrollllllllllllll COMPOSEEEEEEEEEE!!**

---

So, in this project, we are just using the **docker compose file** to include this image as well, and that way one **BIG advantage** is:

> All 3 images would be on the **same network**!!

So we don’t even need to worry about the network interface anymore. That means no need to mention `--network` as a variable in this config.

```yaml
testapp:
  build: .
  image: "testapp_v2"
  ports:
    - "5050:5050"
```

* `testapp` is the name for this config.
* `build: .` means the Dockerfile needs to be built from `.` i.e., the current folder.
* `image` is gonna name this image `testapp_v2`.

---

So it's as simple as this.

Now, instead of running:

```
docker run -p5050:5050 --network docker-testapp_default testapp:1.6
```

We just do:

```
docker compose -f mongodb.yaml up
```

And then all the images just run by themselves without running us anymore commands. **Cool, right?**

Need to stop and delete all containers?

No need to do it in multiple commands manually, simply just do:

```
docker compose -f mongodb.yaml down
```

and **voila! Everything cleared up!!**

---

So this was our **Lesson 2** basically. Super quick and super easy!

**Can't believe I am learning Docker after being confused for years about this super simple tech!!**
ALL you really need is a good teacher tbh.

**Kudos to [@Shradha Khapra](https://www.youtube.com/@ApnaCollegeOfficial)**
📺 [Watch the Docker Tutorial here](https://youtu.be/exmSJpJvIPs?si=15YGCsd3lFhg44bN)

> *(Credit is really due here, no?! 🙂)*
