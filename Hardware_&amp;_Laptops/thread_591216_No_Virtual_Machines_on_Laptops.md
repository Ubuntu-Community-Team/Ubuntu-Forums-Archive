---
title: "No Virtual Machines on Laptops?"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by ryandamartini on 2007-10-25
I have a fairly powerful laptop, C2D 2ghz, 2gb RAM, 80gb HD and a quadro graphics card, Ive been using this for engineering duties just fine. With Windows, I tested many things inside Virtual machines as well as played around with reducing system usage of XP and Vista for side projects using nlite and vlite.


I just installed about two days ago the newest Ubuntu and I have been ecstatic to say the least about the distro. Now I go to the package manager and I cant install VMWare? It says it is not supported my this machine type? 

Any help would be appreciated. Id rather not go back to windows just for this one problem.


Thanks!

RYan M

---

### Post by MaximusTG on 2007-10-25
I don't know which repository you have enabled, but VMware isn't in mine. VMware is a commercial application.. You can download vmware player for free from their website, but not vmware workstation.

---

### Post by ravenon on 2007-10-25
There is also something called vmserver which I believe is available free from Vmware.

---

### Post by ryandamartini on 2007-10-25
@ravenon 

Thanks, I will definately check into that. Is there any other way of running virtual servers in Ubuntu that is supported? 


Thank You,,
Ryan M

---

### Post by LaRoza on 2007-10-25
You can use VirtualBox, you can get a deb for it: [http://www.virtualbox.org/](http://www.virtualbox.org/)

This has a very nice GUI, and is easy to configure, but remember to make the group it requires (the site explains it).

I use it on Windows, mostly, but have used it on Ubuntu.

---

### Post by Steve1961 on 2007-10-25
I use Virtualbox on Ubuntu to run Windows for the odd application that I need.  It works really well.

---

### Post by ryandamartini on 2007-10-25
thank you guys :D

This helps ALOT for what I do. 

Well now I Ubuntu meets 100% of my needs! Bye Windows!


edit: wow! virtualbox is great! :) only a few clicks and installed! I do say Ubuntu is spoiling me!

---

### Post by Steve1961 on 2007-10-26
> wow! virtualbox is great!  only a few clicks and installed! I do say Ubuntu is spoiling me!

It is good isn't it.  Best to add the virtualbox repo to your /etc/apt/sources.list to make sure you get all the updates.  For gutsy that's:

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

If you have trouble getting usb to work just add the following line in /etc/fstab:

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

then type sudo mount -a

note: the devgid number should be the group id of the vboxusers group

---

