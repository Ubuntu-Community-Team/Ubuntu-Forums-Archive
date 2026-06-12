---
title: "How do I get my USB key working (minimal Edgy install)"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by pebkac on 2007-03-02
Hello all

I have Ubuntu Edgy 6.10 installed on a server. I would like to use a USB memory key to move some files. Problem is I installed only minimal packages and stuff I would need for my network services. There is NO GUI, I even had to apt-get gcc and make. 

My question is what packages do I need to be able to use my memory key. I do have Samba installed, so maybe I just have to mount it? If so what would the command be? When it gets recognised by the system, what directory do I go to to access files? (Yeah, I'm used to the F:\ drive or something). Linux and Learn, right? hehe.

Thanks for your help!

---

### Post by pebkac on 2007-03-07
Ok who wants to help me out???

---

### Post by eggdeng on 2007-03-07
Plug in the key and run in a terminal ```
df
```
In the output, you should see the key recognised, probably as sda.
Create a directory to mount to, for example
```
sudo mkdir /media/usbdrive
```
When you mount the drive to the folder, make sure you mount the partition (sda1) & not the drive as such (sda) 
```
sudo mount /dev/sda1 /media/usbdrive
```
Et voliá.

---

