---
title: "Java Programmer"
date: 2008-09-04
forum: General Help
---

### Post by Tag_yer_dead on 2008-09-04
Hey guys,
I'm having a bit of trouble running bluej, a java editor.  i found a guide on how to install ([http://www.bluej.org/download/install.html](http://www.bluej.org/download/install.html)) but im most of all having trouble with getting the sdk.  what command do i run to download the most up-to-date sdk?

Thanks

---

### Post by T_W on 2008-09-04
```
$ sudo apt-get install sun-java6-jdk
$ sudo update-java-alternatives -s java-6-sun

```
After running these try doing a 

'java -version' to confirm you are running JDK 6 from Sun.

```
$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```


Are you sure the OpenJDK which came with the OS cannot run the program?

---

### Post by Tag_yer_dead on 2008-09-04
i tried that but i got the following error

```
$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

```

Earlier i messed with my repositories so that might be the problem....

---

### Post by Tag_yer_dead on 2008-09-05
bump...

---

### Post by aloshbennett on 2008-09-05
They are available under multiverse repositories for 32 bit.

---

### Post by Tag_yer_dead on 2008-09-05
ok well I was messing with the repositories and completely f***ed them up....... does any one have the default list of repositories?????

---

