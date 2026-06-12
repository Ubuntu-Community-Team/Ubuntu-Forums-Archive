---
title: "Installing Windows ISO using Ubuntu and USB"
date: 2010-07-12
forum: Hardware
---

### Post by Aerial Ac3 on 2010-07-12
I have had a problem with my windows and I just got so mad I cleared everything off my netbook and installed Ubuntu. Its a great OS but I have programs I need for school coming soon that only run under windows and WINE won't run most of them and I also need usb support of windows but Virtual box and others won't allow usb support. So I am asking this wonderful community if you would know a way how to get a windows iso image onto a bootable usb. UNetbootin will not do the job either. Thank you for your time.


Solved, Using Oracle VB I was able to install windows and run my programs for school. Thank you ubuntu community.

---

### Post by wilee-nilee on 2010-07-12
I have used this to load a thumb with XP.
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

It has to be run from a windows environment and it has to be a legit ISO, to run.

I assume that you know you can have a shared folder with Vbox to transfer from host to guest.

---

### Post by jocko on 2010-07-12
> **Aerial Ac3 said:**
> ... but Virtual box and others won't allow usb support. ...
Virtualbox (the PUEL version, not the open source edition) supports usb just fine. Get it from [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by C.S.Cameron on 2010-07-12
If you want to install windows from USB stick:

> 1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

Amedac


If you want to run Windows from USB stick:

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

### Post by Aerial Ac3 on 2010-07-13
For some reason, I did the WinToFlash method on wine but it wasn't finding the usb drives. And then I looked for usb support on wine but had no luck with that. For my version of vbox, I know nothing of folder sharing from host guest or anything so I would appreciate if you could fill me in on that. Ill try this other version of virtual box and then Ill see if things work out. And thank you for responding quick guys it really helps me out a bunch.

---

