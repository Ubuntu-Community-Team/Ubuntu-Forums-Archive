---
title: "Dual boot attempt with XP grinds to a halt"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by seabrighter on 2009-10-18
I've been running Ubuntu 9.04 for several months now, and enjoying it.  However, I recently found the need to dip back into Windows for a few things, so I decided to go for a dual boot.  I followed [these instructions]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1") to the letter.  When I repartitioned, I had to make a new XP boot disc with my SATA drivers on it so that XP's setup would recognize the space on the drive.

After going through all that, I was able to run the XP Pro setup on the new partition and it seemed to install fine.  On the final reboot, it seemed to reject my installation and bumps me out to an error window.  I can't get XP to proceed.  I know it's kind of an XP question, but I'm hoping someone has encountered this and knows what to do?  Here's a "screenshot" of my error message:

---

### Post by bulldog on 2009-10-18
Can you perform in a terminal ```
sudo fdisk -l
``` and copy the output on the forum? (l is a lower case L not a one)

---

### Post by seabrighter on 2009-10-18
Yup, here you have it:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca441c87

     Device Boot     Start            End            Blocks     Id  System
/dev/sda1                     1       21634   173775073+  83  Linux
/dev/sda2     *     21635       23566     15518790       7  HPFS/NTFS
/dev/sda3            23567       24321       6064537+     5  Extended
/dev/sda5            23567       24321       6064506     82  Linux swap / Solaris

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders
Units = cylinders of 240 * 512 = 122880 bytes
Disk identifier: 0x48d848d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       16384     1965952+   6  FAT16
```

---

### Post by bulldog on 2009-10-18
Nothing wrong as far as I can see.
Safe boot isn't working either?
If you can boot into safe mode try and disable your sata controller.
I have sata hdd's as well and never made a boot disk for it.

---

### Post by seabrighter on 2009-10-18
I tried booting XP in all the available modes:  Safe Mode, Safe w/Command Prompt, Debugging Mode, etc....all ended with the same blue screen that I showed above.  I wonder if XP sees my EXT partitions and treats them like some kind of threat because it doesn't know how to read them?  I mean, wouldn't it be just like Microsoft to call Linux a "virus?"

---

### Post by river226 on 2009-10-18
if i remember correctly that is a problem with some corrupt files in windows, or worse yet a possible hard drive problem: [http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)
make sure your copy of xp is a good copy and try a reinstall, if that doesn't fix the problem i suggest looking into the condition of your hard drive.

---

### Post by bulldog on 2009-10-18
I have XP installed besides ubuntu for some years now,and never had the impression XP sees linux as a threat.
I have to agree with river226,try to reinstall XP and watch carefully for any error.
Try it without the sata drivers as well,but I'm not sure if XP wants them to be installed to recognize your sata hdd.

---

### Post by seabrighter on 2009-10-18
Well, the whole reason I had to use nLite to make a new XP install disk was because I initially could not get the XP setup to recognize my partitions.  The first time I tried to install XP, setup did not see the 15GB partition that I set aside for it, plus it reported my other partitions incorrectly (size and free space).

Upon using the install disk made with nLite, XP setup was able to load my SATA drivers and correctly report all the partitions.  It then let me run setup as normal, and made it through the whole process without any errors.  The only time I got this error was when XP tried to boot for the first time.

So, I could run the install again, but I don't see why it would come out any different.  However, running the install without the SATA drivers would be a step backwards, as it will not even find the partition.  I will wipe the NTFS partition and try installing again, just to eliminate that question.

---

### Post by seabrighter on 2009-10-18
I wiped the NTFS partition and started over from raw unallocated space.  I let XP setup repartition the space and install again.  It went through the whole setup routine as before, and on the final boot attempt it came up with the same error window.  I'm stumped :confused:

---

### Post by seabrighter on 2009-10-20
bump?  I'm kind of desperate...have a brand new ipod that I can't even use  :(

---

### Post by river226 on 2009-10-20
> **seabrighter said:**
> bump?  I'm kind of desperate...have a brand new ipod that I can't even use  :(

Well, for your ipod you can set up ubuntu since you know that works. 
also Run a full hardware dignostic, since the trouble shooter from windows shows that may be a problem, and your BSOD also suggest the Hard drive as a culprit. here: [http://www.linux.com/archive/articles/55366](http://www.linux.com/archive/articles/55366)

---

### Post by seabrighter on 2009-10-20
Can't set up my ipod because it needs iTunes to initialize, and ubuntu can't run iTunes.  I'm not convinced that this is a problem with the physical drive.  The drive itself has never given me a problem, and ubuntu seems to like it just fine.  I am going to try slipstreaming SP2 into my XP install and see if that helps.

---

### Post by Mark Phelps on 2009-10-21
It's like it's using the drivers to boot, but it's not loading them properly for the install such that, during the final reboot, the drivers aren't loaded.

To get XP to load the SATA drivers, why not just copy them to a disk and, when installing XP (from a regular XP CD), press F6 and load the drivers?  That way, XP will have them loaded for all of its reboots?

---

### Post by raprap30 on 2009-10-21
You could try dskchk at the XP disk CMd

---

### Post by mikechant on 2009-10-21
Doesn't XP need to be either 
a) in the first partition on the disc,
 or 
b) if it's not, have some sort of small boot partition first on the disc?

(Not a Windows expert, I may be wrong, but I thought I read this somewhere...).

---

### Post by seabrighter on 2009-10-22
I don't know how, but I'd like to mark this thread as "SOLVED."  I did some research on that blue screen error message, and my hypothesis was correct.  After using nLite to make another boot disk with the Abit SATA drivers AND SP2 "slipstreamed" into the installation, the whole process was seamless.  I completed the install last night, reinstated my GRUB, and now I have a perfect dual boot system with XP and Ubuntu 9.04.

Funny how it feels to revisit Windows; installing driver after driver...nothing works until you install the drivers.  And yet, it's still a little faster and smoother than Ubuntu.  You take the good with the bad.  I hope Ubuntu continues to catch up, but for now I'll take a little of each.  Thanks for all your help, forum people.

---

