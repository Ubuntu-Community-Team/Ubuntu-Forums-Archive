---
title: "Ubuntu and Dual Booting Windows 10"
date: 2020-04-25
forum: Hardware
---

### Post by jjhange on 2020-04-25
Hello
Any personal opinions about dual booting Windows 10 with Ubuntu (currently I'm running 20.04 LTS)?  
Machine specs are:
Intel(R) Pentium(R) CPU  N3710  @ 1.60GHz, 4 GIB memory, 500 GB disk space.

Reason I'm asking is because I've considered trying to have an option to use Windows 10 for purposes of work.  However I have heard a pretty mixed reviews about doing so was curious to get some more feedback from people who have experienced dual booting.

---

### Post by CelticWarrior on 2020-04-25
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

has all you need to know.

---

### Post by cybrsaylr on 2020-04-26
Been dual booting all my PCs and laptops for years with no issues. When buying a new PC  W10 is on it. So I always kept W10, why dump it you paid for it, split the drive in half with Ubuntu going on the newly created half partition . This way you 2 OSs to use. Never had any problems doing this for over 10 years. 

My main PC, in signature below came with W7. However right now after adding a couple new SSDs,  has 5 OSs on it. W7, W10, Ubuntu LTS 14.04, 16.04 and 18.04 and all run fine. When starting up PC, the bootloader shows all 5 OSs with 18.04 being the default OS. If one of the others is desired, I just select it from the bootloader choices and it boots up and runs trouble free.

---

### Post by Autodave on 2020-04-26
You may want to consider a lighter desktop than Ubuntu with that slower processor that you have.  Perhaps take a look at Xubuntu.

---

### Post by CelticWarrior on 2020-04-26
> **Autodave said:**
> You may want to consider a lighter desktop than Ubuntu with that slower processor that you have.  Perhaps take a look at Xubuntu.

Not really.

I've been using vanilla Ubuntu (already with Gnome) in older and slower  Celerons and it runs perfectly. Also tried a few other flavors and couldn't tell the difference.
The embedded graphics in an Intel(R) Pentium(R) CPU  N3710  @ 1.60GHz is good enough for any modern desktop environment.

---

### Post by jjhange on 2020-04-26
Thank you everyone for your help!

---

### Post by jjhange on 2020-04-27
Another question I forgot to ask...is there a recommended program to create the bootable USB with the Windows 10 .iso on Ubuntu?  I tried WoeUSB but I can't seem to get the installation completed.

---

### Post by CelticWarrior on 2020-04-27
> **jjhange said:**
> Another question I forgot to ask...is there a recommended program to create the bootable USB with the Windows 10 .iso on Ubuntu?  I tried WoeUSB but I can't seem to get the installation completed.

That would fit better a new thread but the answer is a one-liner only so...
Yes, WoeUSB is the way to go but you need to select NTFS for compatibility with the new non-standard Microsoft ISOs.

---

