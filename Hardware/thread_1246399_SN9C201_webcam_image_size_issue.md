---
title: "SN9C201 webcam image size issue"
date: 2009-08-21
forum: Hardware
---

### Post by jpr0 on 2009-08-21
Hi, I'm wondering if anyone can help me. I recently bought a webcam, and after struggling to find drivers for it, I managed to get it working. The webcam is the following: 

```
$ lsusb
Bus 001 Device 005: ID 0c45:627b Microdia PC Camera (SN9C201)
```

I installed the drivers following instructions from this page:

[http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/]("http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/")

I'm using jaunty, and the kernal is 

```
$ uname -r
2.6.28-15-generic
```


The problem is that the image appears to be "zoomed". Apparently this is when there is some kind of resolution/sizing problem - only part of the captured image is being displayed on the screen. Does anybody know how I might fix the problem?

I've attached two images to illustrate the problem, one from the built-in camera on my laptop (which gives me upside down images), and another image from the Microdia camera (the location of each camera are seperated by only 2 inches at most). 

Thanks

---

### Post by ChrisWebb on 2009-09-06
Hello,

I don't know if you're still having this issue but you probably want to talk to Hans de Goede who is working on a project to address this very problem. 

[See this post here: http://ubuntuforums.org/showpost.php?p=7761400&postcount=147]("http://ubuntuforums.org/showpost.php?p=7761400&postcount=147")

---

