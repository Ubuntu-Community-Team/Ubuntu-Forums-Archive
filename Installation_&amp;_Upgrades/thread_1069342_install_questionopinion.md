---
title: "install question/opinion"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by muck76 on 2009-02-13
Ok, i have been playing with K,X,and Ubuntu on a P3 desktop. It has a 20G hdd with windows 2K and a separate 10G HDD with ubuntu now.
Install and running went well with grub running this way. (I put this in so you know i am a little familiar with it) 


For many reasons i find i am on my laptop way more than the desktop i put ubuntu on andi want to play with it more. 
So i am thinking of running ubuntu and Vista on my LT. 

My question is what way, dualboot or virtual? 

I have read that dualbooting with EasyBDC is a good way to go instead of Grub. 

One of my classmates recommended doing it in a virtual setting. He has a Dell laptop like mine and had issues with it running Ububtu and also uninstalling Ubuntu. The partition he created for Ubuntu was never the same and he could not get rid of ubuntu with out wiping the whole hard drive. The MBR would not allow Vista to take it back over. 

So now i am a little gun shy but want to run Ubuntu. 
I have no idea on how to use virtual. 

thanks for your time..

---

### Post by Taemojitsu on 2009-02-13
virtual is the Wubi program, which creates a file on your windows partition and installs Linux into that file.

You could always delete a Ubuntu partition using Gparted on the LiveCD/LiveUSB. Then easily 'reclaim' it by resizing the ntfs partition. Vista not being able to take it over sounds like Vista just can't install onto a specified partition? -.- The MBR is edited when the Vista bootloader is installed, the same way the MBR is edited when GRUB is installed. Maybe it was still formatted as ext3, in which case Vista on another partition would not be able to read the ext3 partition.

---

### Post by muck76 on 2009-02-13
Wubi, thanks. I will look into that. 

I assume by your post that virtually with Wubi is the way to go over a standard install. 

I am not 100% sure on his issues as he did nto show me but tried his best to describe them to me. I am still green to many aspects of computers.

---

### Post by gabo.cr on 2009-02-13
I have a Laptop with dual boot (Vista/Ubuntu)
It works just fine.
Taemojitsu is right about the HDD format, you would have to format it as FAT32 so Vista can use it.

---

### Post by Taemojitsu on 2009-02-13
I've never used Wubi. A few disadvantages I could think of...
-can you mount the windows partition in linux, if the linux filesystem is in a file ON the windows partition?
-you wouldn't be able to use a LiveCD to edit files in the Ubuntu installation if you had problems, because it would be hidden in the Wubi file. (Unless you knew how to mount it, but not everyone is an expert!)

---

### Post by muck76 on 2009-02-13
> **gabo.cr said:**
> I have a Laptop with dual boot (Vista/Ubuntu)
It works just fine.
Taemojitsu is right about the HDD format, you would have to format it as FAT32 so Vista can use it.

Are you just using Grub?

> I've never used Wubi. A few disadvantages I could think of...
-can you mount the windows partition in linux, if the linux filesystem is in a file ON the windows partition?
-you wouldn't be able to use a LiveCD to edit files in the Ubuntu installation if you had problems, because it would be hidden in the Wubi file. (Unless you knew how to mount it, but not everyone is an expert!)

hmm, i am far from an expert...

---

### Post by gabo.cr on 2009-02-14
Yes, I'm using grub.
I even had a splash image on grub, but it made the boot slow.

---

### Post by 2hot6ft2 on 2009-02-14
Personally I have never used wubi and have always opted for real installs. I am currently dual booting both my desktop and laptop with xp and ubuntu. Soon to triple boot the laptop and maybe the desktop with bt4 as well.

So obviously I would say real install with dual boot.

---

### Post by gabo.cr on 2009-02-14
> **2hot6ft2 said:**
> I am currently dual booting both my desktop and laptop with xp and ubuntu. Soon to triple boot the laptop

I want to triple boot my Laptop too!! but maybe I don't have the courage to do it. I would like to have Suse or Fedora.

8-[

---

### Post by muck76 on 2009-02-15
thanks for the replies, it helped...

---

