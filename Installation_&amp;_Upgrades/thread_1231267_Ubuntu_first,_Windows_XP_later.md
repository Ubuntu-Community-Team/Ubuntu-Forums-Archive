---
title: "Ubuntu first, Windows XP later?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by metalmakker on 2009-08-04
Hi!
 
I'm brandnew to Ubuntu but I'm looking forward to getting to know the OS and all of its' possibilities! I'm sure I'll run into problems being a Windows user, so I guess this won't be my first and last post... ;-)
 
I've got the install cd ready (9.04, 64 bit version), but I've got one question left before I start the install. Can I add a windows install at a later time and make it a dual boot **after** I've installed Ubuntu?
 
I know the other way around is no problem.
 
Thanks!

---

### Post by realzippy on 2009-08-04
You can,but its easier to install windows first,because it overrides
the ubuntu bootloader (GRUB)..
Have a look:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by wojox on 2009-08-04
This help doc should be of assistance:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by metalmakker on 2009-08-04
> **realzippy said:**
> You can,but its easier to install windows first,because it overrides
the ubuntu bootloader (GRUB)..
Have a look:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
Ok, I'll check. Problem is I have my new laptop here, the Ubuntu cd, but the Windows install cd I won't be able to get my hands on in the coming days and I want to GO! :-)
 
But I understand it CAN be done, I'll have to fix stuff to get Ubuntu working again?

---

### Post by blur xc on 2009-08-04
I used this site- [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) do do exactly that except I dual boot vista/ubuntu...

As for the boot loader option, there were two choices (not sure if xp is the same) to use the vista boot loader or grub, I chose to use grub.  The steps were pretty easy, and worked 100%.

BM

---

### Post by realzippy on 2009-08-04
"Ok, I'll check. Problem is I have my new laptop here, the Ubuntu cd, but the Windows install cd I won't be able to get my hands on in the coming days and I want to GO!"

...so install Ubuntu,play around,learn a little,configurate Ubuntu
to your needs.When your Windows CD arrives,you could make an installable
backup of your Ubuntu (with a tool called  "remastersys").Install Windows,what will wipe your Ubuntu from the disc (But you have a backup),
then install your Ubuntu remastersys backup,which will not wipe Windows and install the linux bootloader,which lets you choose between Windows/Linux during boot.
Not the smartest way,but you would not have to hussle around with bootloader
reinstallations...

---

### Post by merlinus on 2009-08-04
Reinstalling grub is very easy, after installing xp.

But windows always wants to be in a primary partition, and better that it is the first one on your hdd.  So you may wish to either set up partitions in advance using gparted live cd, or select manual at the partitioning screen during installation and do it that way.

It should be formatted as ntfs.

If you find that you change your mind about installing xp, then you can format that partition as ext3 and use it for storing files.

---

