---
title: "make best use of RAM"
date: 2009-11-17
forum: Hardware
---

### Post by Hakimjo on 2009-11-17
I have 4 x 1 gb RAM in my Lenovo Think Centre (Intel dualcore, etc.)

At boot, the system tests and shows 4 gb.  In 9.10 (up-to-date clean install), the Sysinfo tool only shows 3 and so does the system monitor.  And even when I use many programs at the same time (Digikam editor, rhythmbox, OO, Opera, Skype, etc.), it hardly uses 1 gb.

But some operations (gnome desktop, even window movements, digikam) seem too slow while the processors do not work at full speed.  Thus my suspicion that something is not optimal in regard to memory management.

Thanks for all good suggestions on how to make full use of the 4 gb.

Joachim

---

### Post by fromthehill on 2009-11-17
a 32-bit system can only adress 4GB of ram
this includes the memory on your graphic card

the best would be to install ubuntu 64 bit
but because I had several problems with that (flash, vmware) I went back to 32-bit

to get all your ram on a 32-bit system:
sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae linux-backports-modules-karmic-generic-pae

if this doesn't work after you installed it you should still be able to select the normal kernel in the bootloader


if window-movements go slow I suspect it has something to do with your graphic drivers. but I'm not sure about that

---

### Post by Hakimjo on 2009-11-18
> **fromthehill said:**
> a 32-bit system can only adress 4GB of ram
this includes the memory on your graphic card

to get all your ram on a 32-bit system:
sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae linux-backports-modules-karmic-generic-pae

if this doesn't work after you installed it you should still be able to select the normal kernel in the bootloader



Thanks

So, if I see only 3 gb instead of 4 gb, it is because the handling of the graphic card uses 1 gb of kernel handling capacity ?

I did the install as suggested.  The dialogue also asked me to confirm a grub list update, which I did.

Prompted to restart immediately, but everything restarts as before. No sign of PAE in the startup menu or in sysinfo.  The loaded kernel is 2.6.14-generic.  But 2.6.14-generic-pae does show as installed in synaptic.  Almost there, I guess ?

Joachim

---

### Post by Yellow Pasque on 2009-11-18
> But some operations (gnome desktop, even window movements, digikam) seem too slow while the processors do not work at full speed. Thus my suspicion that something is not optimal in regard to memory management.

It sounds more like a video issue to me. For RAM, what does a 'free -m' command show? Is swap being used when plenty of free RAM is still available?

Personally, I would not bother running the server kernel if you cannot even make use of 1GB of RAM.

---

### Post by realzippy on 2009-11-18
*"Is swap being used when plenty of free RAM is still available?"*

It depends on the "swappiness" setting:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Hakimjo on 2009-11-18
Thanks for the coaching.

Since I made the change, I have the impression that the swap is more empty (virtually totally empty) than before.

My objective is of course not to use RAM for the pleasure of playing brain muscles.  I am learning that Linux actually does not need much RAM ... this is a new reality for a former OSX user.

So, I will let this rest and be happy that I have plenty of spare resource.

Btw I use 32 bit because I want to be able to run or even install a usb stick copy on any computer I use.  This brings me to the next issue and a new post to the installation forum ...

---

