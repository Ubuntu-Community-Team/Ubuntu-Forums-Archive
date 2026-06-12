---
title: "Problem with java plugin"
date: 2008-08-11
forum: General Help
---

### Post by hybrid180 on 2008-08-11
Hi,

Just to let you guys know up front I am a newbie with linux so I really don't know what I am doing.

Anyways, with that out of the way here is my problem.

I tried to install the sun java plug in via the command line but every time I run this command:

```
sudo apt-get install sun-java6-plugin
```

I get the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

What should I be doing to solve this problem?

Thanks for any help you can give me,
Aaron

---

### Post by txcrackers on 2008-08-12
Do you have the "multiverse" repository enabled in Synaptic/Adept/apt?

---

### Post by hybrid180 on 2008-08-12
Yes, I have the multiverse repository setup.

Also, I already have sun java 1.6u6 installed, which I installed via multiverse repository.  There just seems to be some problem with getting the plug in.

Thanks,
Aaron

---

### Post by Nepherte on 2008-08-12
Are you running 64bit Ubuntu? If so, there's no 64bit sun java plugin.
There is however the icedtea plugin. [http://ubuntuforums.org/showthread.php?t=774956](http://ubuntuforums.org/showthread.php?t=774956)

---

### Post by hybrid180 on 2008-08-12
Actually yes, it is 64 bit Ubuntu, so that is the problem then.

Thank you Nepherte,
Aaron

---

### Post by Nepherte on 2008-08-12
Use the openjdk java. It has a 64 bit plugin. Type this in a terminal:
```
sudo apt-get install openjdk-6-jre icedtea-gcjwebplugin
```

---

