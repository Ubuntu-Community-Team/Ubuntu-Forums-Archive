---
title: "Can I shut down X?"
date: 2004-10-17
forum: Installation &amp; Upgrades
---

### Post by Simon on 2004-10-17
Is there a run level that doesn't start the X server? I need to install the nvidia binary drivers, (which also means I have to install a bunch of software that isn't included by default so that I can compile a new kernel module) but I can't do that with X running. It seems all run levels above 2 start X.

I'm having a lot of trouble convincing myself to continue using Ubuntu lately. I just setup a new system and I have no mp3, no video support, no nvidia drivers, no ms fonts  (all my word docs opened in OpenOffice don't look right without them).

I moved from slackware because I was tired of tweaking every thing manually at a comand line, but that's all I have been doing ever since I installed Ubuntu and its getting old real fast.

---

### Post by HungSquirrel on 2004-10-17
Installing the things you mentioned are a snap in Ubuntu.  This site and the official sire have FAQs and HOWTOs.

Runlevel 1 will work fine for what you need to do.  When asked for your root password, just hit Enter if you haven't set one.

---

### Post by Simon on 2004-10-17
> Installing the things you mentioned are a snap in Ubuntu

They **were** a snap, but not any more. Most of the legally questionable stuff has been removed from the repositories recently so you can no longer apt-get mplayer, gstreamer-mad, totem-xine or the nvidia drivers. I have another system that I setup just before the RC was released and it was great.

About runlevel 1, the installer gives me warnings about single user mode. I'll give it a try though.

---

### Post by Simon on 2004-10-17
Would you know where I can find the kernel souce? I can only seem to find the headers, but I need the source to install the nvidia driver.

---

### Post by Simon on 2004-10-17
Sweet, I switched back to the restricted repository and the nvidia drivers were in there, and all the mplayer dependecies! Things are looking up.

---

### Post by im_ka on 2004-10-17
for mplayer, you need a new apt source.
add this

```
deb ftp&#58;//ftp.nerim.net/debian-marillat/ unstable main
```

line to /etc/apt/sources.list

and do

```
sudo apt-get update
```

you will now be able to install mplayer (and some other multimedia packages)

hth

---

### Post by renato on 2004-10-22
ctrl+alt+f1 to switch from X to console

alt+f7 (or ctrl+f7?? I am at work using windows so I can't be sure) to go back to X

---

### Post by process91 on 2007-02-15
Try switching to a terminal console (Ctrl+Alt+F1) and typing 
init 3

I'm also trying to install the new NVidia drivers for my NVidia GeForce 4 card, and I'm having a bitch of a time getting it to work. First it cannot find the linux kernel sources and then after it tries to download it and can't it also tells me that it can't find 'cc' or 'gcc' and that I should download the package.

Edit: I've learned a lot in the last month or two, and this message is actually embarrassing to me at this point. To anyone else who reads my above frustration I will leave what I did for others benefit.

First off, if you install the "build-essential" package (use sudo apt-get install build-essential or search for it in the synaptic package manager) you will get cc, gcc, and the headers no problem

Also, the NVidia Binaries are easier than ever to install on Ubuntu 7.04, as well as the wireless card in my laptop and a whole bunch of other stuff so download that - it's worth the reformat!

---

