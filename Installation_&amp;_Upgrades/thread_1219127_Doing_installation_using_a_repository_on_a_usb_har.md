---
title: "Doing installation using a repository on a usb harddisk."
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by vverheijen on 2009-07-21
I have to do a installation on a few servers that have no cd-rom or internet.
So i took a usb stick, formatted it as ext2, put grub on it and the hd-media kernel image + a installation iso. This works.

But what i prefer to have is a repository on the usb disk so i can easily add packages i need without having to remaster the iso. It sounds like something that should be easy to do. But i am looking for information on how to get the installer to use the repository, and i don't find anything.

I am using jaunty server i386 and amd64

Is this possible? If yes, how to do it?

Thanks, Vincent

---

### Post by running_rabbit07 on 2009-07-21
I am not familier with servers nor have I made my own custom disk before but I see the program in this screenshot and I think you can use it to make a custom install that should have all the programs on it that you choose. Which means you shouldn't have to download anything during nor after the install.

You should install it and check it out to see if it does what you want.

I hope this helps.

---

### Post by vverheijen on 2009-07-21
I know it is possible to make a iso image with everything i need and put that on the stick. But i find it stupid to use iso's when i am not using cd's. So i am looking for a better way.

---

### Post by running_rabbit07 on 2009-07-21
> **vverheijen said:**
> I know it is possible to make a iso image with everything i need and put that on the stick. But i find it stupid to use iso's when i am not using cd's. So i am looking for a better way.

Have you checked out the USB Startup Disk Creator under the System>Administration menu?

You can also burn ISOs to USB using [Unetbootin.]("http://unetbootin.sourceforge.net/")

So, you can make an ISO with everything you want and but it on a stick but, it would be stupid to make an ISO? I am just trying to help. Maybe[ this link]("http://www.ubuntu.com/support/paid") will be able to help you better.

---

### Post by vverheijen on 2009-07-22
Maybe it is not stupid, but it is not necessary if you don't use cd's. For example if i want to add a package i have to unpack the iso, add the package, make the iso and put it back on the usb disk. If i have just the repository i can add the package to it. and that's it.

That's why i would like to not use iso's.

But i am making some progress with it, I now put a iso with only the things that let debian installer detect that there is a iso available on the disk (i could not find how to disable looking for the iso and mounting it). And i modified the path where it looks for the mounted iso (to a directory on the usb disk with a unpacked iso). I am gonna try this now and i hope it will work. 

Maybe someone has a les hackish solution?

Thanks

---

### Post by running_rabbit07 on 2009-07-22
Yeah, I tried both of the possibilities I threw out there yesterday and was quite disappointed with how hard it is just to beef up the ISO to get it where I want. 

Sorry it wasn't what you wanted, I'll be watching the thread to see if anything better comes up.

I'm just wanting to make an ISO to where I don't have to reinstall 20 programs and do 180 updates every time I jack up my system and have to reinstall.

---

### Post by Theory5 on 2009-07-22
Ever heard of a persistant file system? I am using it with puppy linux on a flash drive it works great. Its basically a file system on a USB drive that you can change, add or remove packages and save your stuff on it. I am not sure how Ubuntu does it, but you can look into it. ask around. Its not a certain program or anything, its just the way you setup the filesystem because most USB OS's are read-only. Hope this helps!

---

### Post by running_rabbit07 on 2009-07-22
> **Theory5 said:**
> Ever heard of a persistant file system? I am using it with puppy linux on a flash drive it works great. Its basically a file system on a USB drive that you can change, add or remove packages and save your stuff on it. I am not sure how Ubuntu does it, but you can look into it. ask around. Its not a certain program or anything, its just the way you setup the filesystem because most USB OS's are read-only. Hope this helps!

I'll look in to it, thanks.

---

### Post by vverheijen on 2009-07-22
I am not using the usb disk as my root fs. Just to install some servers in locations where there is no internet access. So the persistent fs from puppylinux has nothing to do with this.

---

### Post by running_rabbit07 on 2009-07-27
I found a program that may be able to help you. It is in Synaptic and it is called APTonCD. I have used it to make a CD but I think you may be able to use it.

---

