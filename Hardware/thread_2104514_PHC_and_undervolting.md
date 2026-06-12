---
title: "PHC and undervolting"
date: 2013-01-13
forum: Hardware
---

### Post by ivotkl on 2013-01-13
> **ivotkl said:**
> Reviving an old thread here. Apparently PHC is no longer available (or not supported on 3.0+ Kernels).

Please see below and if you can help me, I would really appreciate it. For those who read this and cannot assist me, thank you as well for your time. =)

```
$ sudo apt-get install linux-generic-phc linux-headers-generic-phc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic-phc : Depends: linux-headers-3.2.0-25-generic-phc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Same / similar error appeared before and I did update -f, which I thought fixed it. It did not.

Ok, being the above said, I'm creating this new thread since last post on [the other thread](http://ubuntuforums.org/showthread.php?t=786402) was dated Oct 2012 excluding [the one made by me](http://ubuntuforums.org/showthread.php?p=12453276#post12453276).

I've used [these instructions](http://linuxsolver.blogspot.it/2012/05/undervolting-cpu-in-ubuntu-1204.html) meant for Ubuntu 12.04, which is my current system.

Any help will be highly appreciated. =)

---

### Post by linrunner on 2013-01-13
Hi,

you may try the tp-Kernel from my [ppa]("https://launchpad.net/~linrunner/+archive/thinkpad-extras"). It comes "ready to use" with the necessary module (builtin).

---

### Post by ivotkl on 2013-01-14
Thank you linrunner. Will do and edit this post once I'm done. =)
 
**Edit:** By the way, will it work under an AMD based desktop? You can find my box hardware specs on my signature's link. Thanks!

---

### Post by ivotkl on 2013-01-15
Shameless bump after almost 24 hours. :P
Anyone? Thanks!

---

### Post by linrunner on 2013-01-15
No AMD, sorry.

---

### Post by ivotkl on 2013-01-17
Oh, OK. Then I'll just go ahead and buy a nice heatsink + heatpipes + cooler. I'm planning on getting Deep Cool's Gammaxx 200, which would work for current settings and also fits LGA1155 slots for my future box with an i3.

I'll mark thread as solved after I get the i3 and test your PHC. Will it work on destkops?

---

### Post by ivotkl on 2013-01-19
Marking thread as solved as I've thought twice and an AMD APU would suit better my needs.

---

