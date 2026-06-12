---
title: "Sucess: Dell Inspiron 4000 C800"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by Dingo_aus on 2006-09-23
Just a quick post for those thinking of installing Dapper Drake (6.06) on their oldish Dell Inspiron 4000.

Having just put a fresh install on a Inspiron 4000 (Intel PIII 800, 128 mb RAM, DVD burner, synaptic touch pad, ATI M3 (Mobility) 8Mb video card) it all works perfectly out of the box.

Even the Xircom PCMCIA 10/100 Ethernet card works out of the box.

Sounds works. Touchpad works, floppy, DVD etc etc....all "just works"

Only note of caution, with only 128Mb in the standard config, don't even think about using the LiveCD then install option, go straight for the "Alternate" release and install to the harddrive.

Standard Gnome is fast enough to not drive you crazy but I'm thinking a lighterweight WM like Xfce is probably the way to go.

....and with the price of RAM what it is, another 128/256 isn't going to kill me.

All in all, the easiest Linux install EVER!

EDIT: Xfce makes a pretty big difference, difinitely go with it if you only have 128 megs of RAM

Also, to get the ATI mobility M3 to use 3d acceleration I needed to do:
sudo dpkg-reconfigure xserver-xorg and go through the obvious choices there, after that, glxinfo|grep "direct" spat back "yes" and OpenGL acceleration was in place.

I think the fact I dropped the default resolution to 16 bbp meant framebuffers could fit in the 8mb memory

Also, the Mic was setup automatically and works with Skype from the get go too!

EDIT2: Even all the little things work like automatically changing the brightness of screen based on whether on AC or Batt. Including turning the screen off when you close the lid etc etc - gw Ubunut Team!

---

### Post by vinodmenon on 2006-09-23
I have a Dell Inspiron 510m laptop and would like to install the latest "Dapper Drake" version of Linux along with my windows running together. My current specs for the laptop are as follows:

Features/Specs: Pentium M 1.6GHz; 512MB RAM; 15in screen; 64MB shared Intel Extreme Graphics 2; 60GB hard drive; DVD-RW/CD-RW

Is there any way anyone could assist me with the installation procedures for having a dual-boot system on this laptop? Any guides or website? I believe that i have to recreate the partitions in order to have the dual-boot work properly. Currently my laptop has been reset to factory conditions ie like brand new when i got it delivered with Windows OS etc. I have just installed Partition Magic after ghosting the hard disk.

Hoping to resolve this matter asap.
-- 
Regards,
Vinod Menon

---

### Post by xyz on 2006-09-23
[Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning")

I like that one. Hope it helps you too.

---

