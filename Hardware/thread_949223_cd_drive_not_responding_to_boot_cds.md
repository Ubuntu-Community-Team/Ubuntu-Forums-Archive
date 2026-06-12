---
title: "cd drive not responding to boot cds"
date: 2008-10-15
forum: Hardware
---

### Post by jackBnimble on 2008-10-15
I need a solution to my mistake of upgrading to 8.10 beta. In order to downgrade back to 8.04 I need to reboot, right?  I have a freshly burned 8.04.1 live cd.  Tried to reboot; nothing responds, goes right to my login.  I think it's yet another bug thats affecting the cd-drive.  I also tried to use gparted live 0.3.9-4 stable, man I'm into stable now! Same deal with it, nada.  Tried using a USB, I not sure if just putting the image on the thumbdrive and using the bios to boot from the USB is all there is too it. I don't have another harddrive to use. 

Help pleeeeease

---

### Post by jerome1232 on 2008-10-15
Is your BIOS set to boot from a cd-rom? Does the cd-rom spin up during the boot process like it's trying to read the cd?

---

### Post by jackBnimble on 2008-10-15
Yes, the bios was selected to run when I was using the disks.  The cd drive does go but it seems like it should be starting up sooner.  It starts running after Ubuntu starts to load.

---

### Post by jerome1232 on 2008-10-15
Are you sure the cd-rom is selected as the First boot device (otherwise it'll pick up that the hard disk is bootable and never try the cd-rom)

It sounds like it's not even attempting to boot from cd to me. Normally they'll at least spin the cd-rom up a little bit before grub would start to load.

---

### Post by jackBnimble on 2008-10-15
I've tried three time and check the bios each time, so yah I sure the drive is the selected boot.

---

### Post by jerome1232 on 2008-10-15
Then either the cd was burned badly and isn't bootable, or that cd-rom is seeing the end of it's days. Can other computers boot off of that cd? Do you have any spare cd-rom's you can swap out?

---

### Post by jackBnimble on 2008-10-16
I will find someone to test the cds on tomorrow.  The burner and drive worked fine with things just the other day and I haven't dropped my laptop.  Brasero works pretty good for me, but you maybe right. I check back tomorrow.

Thanks

---

### Post by jerome1232 on 2008-10-16
> **jackBnimble said:**
> I will find someone to test the cds on tomorrow.  The burner and drive worked fine with things just the other day and I haven't dropped my laptop.  Brasero works pretty good for me, but you maybe right. I check back tomorrow.

Thanks

It's a laptop! (makes swapping out cd-roms a bit hard :) ) 

 Those are the only things it really can be if the BIOS is configed to boot off of the cd-rom before the hard drive, I know I had one dvd-rom that worked just fine but refuesed to boot any cd/dvd discs that would work fine in every other cd/dvd-rom I tried.

That why I was triple asking about the bios config ;)

---

### Post by jackBnimble on 2008-10-16
I hope it was the burning process then.  thanks again.  out-

---

### Post by jackBnimble on 2008-10-16
I've now tried loading these same disks up with a friends laptop.  The bios seemed to be defaulted to boot via disk like mine. The disks failed to boot on his machine as well. So I reburned the disks from the same files I downloaded from the parent sites on new media.  Tried the new disks on both machines and struck out again.  I really don't think that they are both faulty.  Maybe there's more to setting the bios to read the boot from the disk drive?  Maybe I did something wrong with burning?  My friends machine is only a year old, runs vista premium only, hp laptop.  The disks I've tried to boot with are a live Ubuntu 8.04.1 and Gparted 0.3.9-4 live.

Again I can't see both laptops tops failing at the same time coincidently or I'd be plam ying the lotto today.  Are there viruses that both systems could have?  My best guess now is I've screwed up the processes somehow.  I doubt that too, but what gives? :confused:

---

### Post by jerome1232 on 2008-10-16
Okay lets cover all of the bases.

md5sum your downloaded file (this insures integrity of the file)
ensure you are burning the disc as an image not as a data cd
burn at a slow speed, 4x is a great speed (well for reliability)
Ensure that in your bios that only the cd-rom is selected as a boot option. This way we are sure it's trying the cd-rom.

how to do an md5sum [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
how to burn an iso [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Bios varies by manufacturer so There's no conclusive good guide I can link for that step, just make sure it's the only thing the machine is allowed to boot off of (if no disk is in the cdrom the computer will fail to boot so you will know if you have it set right)

hope all of that helps

these are the md5sums for the various 8.04.1 disks
```
38e3f4d0774a143bd24f1f2e42e80d63 *ubuntu-8.04.1-alternate-amd64.iso
bbd21ded02c06b41c59485266833937a *ubuntu-8.04.1-alternate-i386.iso
b78ef719e3361e726b89bab78c526ad0 *ubuntu-8.04.1-desktop-amd64.iso
c69e34e92d5402d1b87e6babc739f774 *ubuntu-8.04.1-desktop-i386.iso
e7351d79903588699a383ae77854f734 *ubuntu-8.04.1-server-amd64.iso
7232c6004ba438890cd09aded162dc8e *ubuntu-8.04.1-server-i386.iso

```

---

