---
title: "No internet = No apt-get = No kernel recompiling"
date: 2005-11-17
forum: General Help
---

### Post by axelred66 on 2005-11-17
I can't connect to the internet with Ubuntu, because I only have a non-standard USB ADSL modem. I found the drivers I need, but to get these working, I have to recompile the kernel. Recompiling the kernel means I have to "apt-get install..." quite a lot of things, which doesn't work because, guess what, I can't connect to the internet! A real chicken and egg problem...
How can I solve this? Are there other ways to install stuff that's not on the Ubuntu CD, but can only be found on the net???
Please help, I'm tired of rebooting into MSWindows just for surfing the internet!:(

---

### Post by Lambert on 2005-11-17
1. what model of modem do you have? You may be able to get it working with the windows drivers using a module called ndiswrapper. Then if you want you can download what you need, uninstall ndiswrapper and use the driver you want.
2. See if [this]("http://www.ubuntuforums.org/showthread.php?t=20217&highlight=apt-cdrom") thread helps. You can download the repository to a disk and add the programs.
3. Programs not in the repository can be downloaded and installed depending on the type of package they are.

---

### Post by ivanhelguera on 2005-11-17
Recompiling the kernel was necessary for running ADSL in 2.4 Kernels. The modern 2.6 used i.a. by Ubuntu (all the versions) do not need it (maybe somtimes they do, but often they do not)
Do you happen have a speedtouch modem?
best, 
IH

---

### Post by axelred66 on 2005-11-17
Hi folks,

Thanks very much for the tips. :D I'll certainly try them out one of these days. But at first sight it looks like this is really what I need. I hope I can also download the packages I need with my MSWindows and copy them to the right place...

For your information : my modem is an E-Tech (Connexant chip). The only linux-driver for this modem was designed for kernels >= 2.6.10.

---

### Post by ivanhelguera on 2005-11-18
If you'ree using Ubuntu Breezy, it has the the 2.6.12 kernel... and Hoary has the 2.6.10 one if I remember correctly
So if you're using those systems (which I suppose you do), you won't need to modify the kernel

---

### Post by Specialsauce on 2005-11-18
what modem do you have?

---

