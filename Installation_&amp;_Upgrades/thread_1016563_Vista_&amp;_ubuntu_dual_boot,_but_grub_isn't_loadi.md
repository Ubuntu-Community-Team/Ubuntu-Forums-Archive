---
title: "Vista &amp; ubuntu dual boot, but grub isn't loading..."
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by JCasper on 2008-12-20
Hey all, I have just installed Ubuntu alongside my Vista, but when I reboot it boots straight to vista, no linux and no grub. Is there something special I have to do when dual booting Vista?

Thanks

---

### Post by logos34 on 2008-12-20
one or two hard disks?  if the latter, grub might be on the other disk--go into the Bios and change the hdd boot order.  If only one disk then maybe you have an MBR write-protect feature preventing grub frm installing. You can find out by reinstalling grub from the live cd (see link my signature)

---

### Post by infamous-online on 2008-12-20
What's your setup like? Like are you using one or two harddrives for this?

---

### Post by JCasper on 2008-12-20
OK, sorry I didn't include it. I have two hdds in raid 0. I used the alternate cd so the drivers were included and my raid was picked up. I partitioned in vista then partitioned my swap in the linux set up.

Everything seemed to go smoothly, but no grub and therefore no linux.

Also, I did notice that in the setup my vista partition did not have a mount point like /sda/ blah blah. It was just blank, but I decided not to mess with it.

I also left the bootable flag option off for my root drive, should that be on?

---

### Post by caljohnsmith on 2008-12-20
> **JCasper said:**
> OK, sorry I didn't include it. I have two hdds in raid 0. I used the alternate cd so the drivers were included and my raid was picked up. I partitioned in vista then partitioned my swap in the linux set up.
I think you usually have to follow special steps to successfully install Grub to a RAID setup. Have you seen this tutorial:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I would try the steps in that tutorial for manually installing Grub. How about giving that a shot and let us know how it goes.

---

### Post by JCasper on 2008-12-20
Wow, that looks like a mess. Thanks for the help. I just read to where it says 8.10 and alternate CD should work without further configuration.

I only have to mess with grub atleast? Not follow this whole guide?

---

### Post by JCasper on 2008-12-20
I installed grub in the MBR. Should I make my ext root drive bootable? It was defaulted as bootable flag off.

---

### Post by caljohnsmith on 2008-12-20
What's the current status with your setup? Is Ubuntu fully installed? Which drive has Grub in the MBR? In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your current setup.

---

### Post by JCasper on 2008-12-20
OK, I will have to download a live CD. I used the alternate CD because it comes with the raid drivers. Everything installed fine, but it boots straight to vista. It installed grub into the MBR. Default location.

Also, my root partition is not set as bootable. Should it be? It is defaulted as bootable flag off. Vista is bootable though.

Thanks man, I will search for an older live CD I Guess.

---

### Post by caljohnsmith on 2008-12-20
> **JCasper said:**
> 
Also, my root partition is not set as bootable. Should it be? It is defaulted as bootable flag off. Vista is bootable though.

Actually, only one partition can be marked bootable, and since you are going to be using Grub, it is arbitrary which partition is marked bootable; Grub can boot a partition regardless of whether the boot flag is set on it or not. The boot flag is mainly for brainless boot loaders like a Windows MBR that merely looks for whichever partition is marked bootable, and then it tries to boot that partition's boot sector. So its fine if Vista is the partition marked as bootable. :)

---

### Post by JCasper on 2008-12-20
Well damn. I don't know what to do then. I have tried to reinstall it all, and same result. It's either grub or my MBR. It just isn't loading grub.

---

