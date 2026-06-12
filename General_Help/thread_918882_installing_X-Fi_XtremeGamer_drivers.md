---
title: "installing X-Fi XtremeGamer drivers"
date: 2008-09-13
forum: General Help
---

### Post by Static42 on 2008-09-13
Hi,

I have a Creative SoundBlaster X-Fi XtremeGamer sound card, and I'm trying to install the linux drivers for it. I got the drivers from [here]("http://opensource.creative.com/soundcard.html"). To install it, I type in **sudo ./install** But when I do that, I receive an error:

> 
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful


I don't know what that means. Can someone help me with this?

---

### Post by Nepherte on 2008-09-13
You are probably missing the build-essential package which is necessary to compile from source. Unfortunately you can't install the official x-fi drivers with the supplied install file. You will have to recompile the whole kernel and install a patched driver afterwards. Here are instructions how to do so: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

The previous method might seem a little difficult if you're not experienced with linux. There is however a easier method using OSS (open sound system) drivers. Instructions can be found here: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

I found the first method to give better sound than the second method (subjected to my opinion). It is up to you which method you prefer.

---

