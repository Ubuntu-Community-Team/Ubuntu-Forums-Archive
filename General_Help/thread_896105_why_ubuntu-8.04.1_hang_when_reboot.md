---
title: "why ubuntu-8.04.1 hang when reboot"
date: 2008-08-20
forum: General Help
---

### Post by tjflymonkey on 2008-08-20
Hello, 
I am new to linux.I wish to run Ubuntu and window. So I installed ubuntu-8.04.1-desktop-amd64.iso on my D: drive with 20G space recently by using Wubi. 

It all went very well, except when install reached second reboot it just hang.I have tried all kind of method to install. But every time it just hang at second reboot. However if I restart my computer and select Ubuntu, I can successfully enter ubuntu. I assume the install is successful. When I want to reboot, it hang again. Exactly like previous hang. So my problem is Ubuntu hang when reboot. 

I wish I can find out the reason cause the hang. Could somebody please show me how? 

My laptop is ASUS z99D series AMDTurion64 nvidia geforce 8400 

Thank you very much.    :confused:

---

### Post by Orlsend on 2008-08-21
Maybe do a Defrag on windows,epecially on where the Ubuntu files are.

---

### Post by tjflymonkey on 2008-08-22
> **Orlsend said:**
> Maybe do a Defrag on windows,epecially on where the Ubuntu files are.

It still doesn't work...? Help please~~

---

### Post by triin mack on 2008-11-26
My suggest is you can use VMware. From this software you can easily install windows into a linux operating system. Simple search in google, its your friend.

---

### Post by Zaraphrax on 2008-11-26
There could be some incompatibility with some hardware on your machine. Have you tried booting the Live CD? I've heard of ACPI messing with things like that with Ubuntu installs. You *could* try the following (but be careful here):

```

sudo nano /boot/grub/menu.lst
```

Then, find the list of kernels towards the bottom. Add the following parameters to the end of the kernel line:

```
pci=noacpi acpi=off
```

However, that may make stuff worse, so I'd make a backup of your menu.lst before you tried it. Use at your own risk.

But yeah, I'd also recommend VMWare (or Virtualbox, whatever tickles your pickle).

---

### Post by Dareajoe on 2009-01-27
How can I reboot my computer to its original factory settings?My computer is a Windows Millenium, but I dont have the recover Disk. I've tried everything is there another way to reboot the whole thing.

---

### Post by papenpj on 2009-03-18
@Dareajoe
I beleive you mean recover.  Unless you have a hidden restore partition your likely not going to be able to recover anything especially the operating system without disks. Of course if you know someone who has a similar copy of Windows ME then you could borrow their disk and use your serial # located on the side of your computer. Do you currently have ubuntu installed also?

---

