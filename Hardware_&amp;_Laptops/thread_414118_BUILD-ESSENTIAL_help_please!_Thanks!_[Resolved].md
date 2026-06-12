---
title: "BUILD-ESSENTIAL help please! Thanks! [Resolved]"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by adampyre on 2007-04-19
Hello, I just upgraded my dell to 7.04 and have no wireless. I need to install the drivers, so i need to install ndiswapper. but i can't install ndiswrapper until I install build-essential apparently.... I copied all the files over with a pen drive since I have no internet at the moment. I attempted to "sudo dpkg -i build-essential_11.3_i386.deb" but I got a message about libc6-dev | libc-dev not being installed? 

Before I get myself any more confused am I even going about this the right way? Or is there a better way to get the win drivers for my wireless card on Ubuntu? I have a Linksys WPC54G v.3

Thanks!

Adam

---

### Post by eyelessfade on 2007-04-19
Seems you need the wrapper.
Use the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find all the dependencies for the build packages. It will save a lot of time.

---

### Post by adampyre on 2007-04-19
> **eyelessfade said:**
> Seems you need the wrapper.
Use the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find all the dependencies for the build packages. It will save a lot of time.

Yeah, that's where I got the wrapper from and build essential 11.3

See, when I try to make ndswrapper, it gives me a bunch of errors. i looked it up and apparantly it means i need build-essential, so I got build-essential and I am still getting the libc6 error. Any other suggestions?

Thanks.

---

### Post by macker3 on 2007-04-19
you need libc6-dev

---

### Post by adampyre on 2007-04-19
I beg of someone for help. I need to have this set up for school tomorrow! 

Thank you!

---

### Post by taurus on 2007-04-19
The package build-essential and all it dependencies should be on the CD.  From a terminal, do

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by macker3 on 2007-04-19
> **taurus said:**
> The package build-essential and all it dependencies should be on the CD.  From a terminal, do

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

with an alternate CD or does it work with the Live CD?

---

### Post by aysiu on 2007-04-19
> **macker3 said:**
> with an alternative CD or does it work with the Live CD?
It's on both CDs.

---

### Post by macker3 on 2007-04-19
> **aysiu said:**
> It's on both CDs.

yeah right! I always use the alternate ones :D

---

### Post by adampyre on 2007-04-19
> **macker3 said:**
> with an alternative CD or does it work with the Live CD?

thank you! I'll try his and repost if it doesn't work. Don't have time at the moment...

---

### Post by adampyre on 2007-04-20
> **taurus said:**
> The package build-essential and all it dependencies should be on the CD.  From a terminal, do

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

taurus, you rule. that worked great! I was able to get build-essential installed which in turned enabled me to get the wrapper installed and my drivers worked! This is why the Linux community rules!!!!!

Thanks!

Adam

---

