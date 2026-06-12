---
title: "New install questions"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by rmiami on 2009-04-27
OK, I just made the first attempt to install Ubuntu using Fusion on my Macbook pro ... and despite my complete lack of knowledge (I know enough to be dangerous) it seemed to install OK until I went to run an update or tried to upgrade to the newer version and it said something about, .... I don't know, when I went to install it it asked a million questions, and I just hit enter and said (IN the name of the father, the son ....) so it actually starts up, I can go on the net so I assume I answered something wrong in the configuration during the install or maybe because I'm not catholic.
 
 I guess I can wipe it off and start over ... but is there a cheat sheet or something I can work off of ????
 
I have Vista in a virtual as well with Dragon 10 installed ... and I'm interested in keeping up with any developments in Voice-recognition with this OS


Just the quick time I spent mulling around, the OS seemed easy to figure out. It loads quick, ...

Ok, it is saying Sudo does not allow my to run the updates or upgrade .... if that helps

---

### Post by cariboo on 2009-04-27
If you want to upgrade to Juanty press ALt-F2 and type:

```
gksu update-manager -d
```

Enter the password you entered during installation. This will start the update manager as root, and update to Jaunty

---

### Post by rmiami on 2009-04-27
That didn't work ... it returns control back to the Mac ....I don't yet have full functionality because VMware tools will not install.  I also tried to re-install the OS but that didn't work ether ... it still says sudo will not allow. I don't even know what sudo is????? I get a similar response when I tried to do updates ...

---

### Post by acreech on 2009-04-28
I am not sure that I completely understand what you are trying to do, other than install Jaunty. To start with Sudo gives you root permisions. You have to have it to update or upgrade. So you can open a terminal and type "sudo apt-get update" then type "sudo apt-get upgrade". It will asked for your password after you enter the first command. 

Onto the bigger problem. It sounds like you are working on a Mac. Are you trying to do a dual boot? Do you have a version of Ubuntu installed already? Or are you trying do a fresh install from a cd?

---

### Post by rmiami on 2009-04-28
Yes I have a new Macbook Pro ... I installed Vista in Bootcamp, and then installed Fusion to run it in a virtual ... and other than all of the babysitting crap, Vista is running smoothly both in Bootcamp and virtual.
 
 I'm using fusion to install Ubuntu 8.10 Desktop in a virtual ... or trying to. Fusions procedures are vague ... attempting  install of VMware tools, if a gui does not pop up they say to go into administrator login ... but it's not there, nor do I see a terminal access? trying to access Users ... I'm told I don't have access permissions.

So, it has to be something I or fusion is not configuring right during the install.

---

### Post by rmiami on 2009-04-28
I installed 64 bit Vista, because I wanted to run the 64 bit version of Dragon 10 ... I've been attempting to install the 64 bit version of Ubuntu 8.10 ... maybe if I try again I should drop back to the 32 bit version. 

I've had them all running at the same time , Vista , Ubuntu and OSX bouncing back and forth and this machine handled it with ease ... if ubuntu is installed right, my trackpad will work accross platforms and other cool stuff.

---

