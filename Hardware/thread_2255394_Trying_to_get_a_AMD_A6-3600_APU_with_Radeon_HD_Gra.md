---
title: "Trying to get a AMD A6-3600 APU with Radeon HD Graphics to work with my nvidia gpu"
date: 2014-12-04
forum: Hardware
---

### Post by teamonster on 2014-12-04
[IMG]http://i.imgur.com/syLFx3A.jpg[/IMG]

So what I am thinking I need to do is switch it from the apu graphics to the discrete one right? But how would I go about doing that I have tried Bumblebee also my system is a fresh install which was just updated so.

glxinfo says:

```
client glx vendor string: Mesa Project and SGI

```

my nvidia gpu is the 750 gtx

and it doesn't show up in additional drivers so

should I just do this ([http://ubuntuforums.org/showthread.php?t=2246963](http://ubuntuforums.org/showthread.php?t=2246963)) ?

```
sudo apt-get update
sudo apt-get install nvidia-304

```

[img]http://i.imgur.com/NWrey0L.jpg[/img]

I'm gonna try 

```
sudo apt-get install nvidia-current
sudo nvidia-xconfig

```

---

