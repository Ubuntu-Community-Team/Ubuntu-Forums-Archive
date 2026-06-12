---
title: "Sound Driver Issues"
date: 2011-04-14
forum: Hardware
---

### Post by Enlightened Shadow on 2011-04-14
Hey everyone. I have been dealing with this issue for about a week now and am here asking for help.

I reinstalled Windows XP Home Edition Service Pack 2 on this machine. I have the original driver disks that came with the computer but they have been pretty much useless. I don't know why either (since this is all factory hardware).

So not being able to get the drivers I need off the disk, I needed to get online to go to the Nvidia website to retrieve my Motherboard driver. I don't know exactly what the models of the hardware are but it's a Dell Inspiron 531. Maybe you guys know how to find out that way.

Anyway, I ended up getting a Motherboard driver off of my PS3 as I have no other way to access the Internet. It worked and I was able to connect to the Internet on this machine. However now the Sound card doesn't seem to register.

I have done everything I can possibly think of. The closest I got was on the Nvidia website, I had it scan my PC. It found that I was missing the HDMI HD Audio driver and I downloaded it, but when I try to install it, I get an error message saying there is no compatible hardware found.

I'm really frustrated with it. I boot up in a fresh Ubuntu 10.10 install and it finds all of my drivers and gets them working without me having to do anything! I mean come on, why does Micro$oft have to be so crappy that they can't even do simple tasks like that (granted that it is XP and really outdated now).

Anyway, I was looking in the Ubuntu Software Center and I saw something called Dell Recovery ISO. Do you guys think I could use that or something similar to back up the working drivers in Ubuntu to be found in Windows?

I just don't know what else to do at this point. Any help is appreciated.

---

### Post by Enlightened Shadow on 2011-04-14
Bump.

---

### Post by Yellow Pasque on 2011-04-14
So you're looking for Windows support? :?

---

### Post by Enlightened Shadow on 2011-04-14
No not exactly. I'm looking for a way to see what my exact drivers are so I can download the ones I need in Windows.

---

### Post by Yellow Pasque on 2011-04-14
Maybe this helps:
```
lspci -vv
sudo lshw
```

---

### Post by Enlightened Shadow on 2011-04-15
I got it working. Thanks for the help. I used DriverMax and it worked fine.

---

