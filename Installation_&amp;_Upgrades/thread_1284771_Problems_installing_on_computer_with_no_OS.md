---
title: "Problems installing on computer with no OS"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by Newandexcited on 2009-10-07
I have had an Acer Aspire 5610 for two years now and it has caused me nothing but trouble.  I finally had enough with Vista and then attempted to load XP but 5 product keys wouldn't work (3 of which came from the microsoft themselves via telephone).  I tried to reload my recovery disks to no avail.  I can load a livecd of mandriva but would like to use ubuntu instead but whenever I try to install ubuntu, it never goes past the first screen where it asks me what I want to do.  As of right now my computer has no OS,  what should I do?  Please help!

---

### Post by tommcd on 2009-10-07
When you boot up the Ubuntu live CD what happens if you try running the option "check disc for defects"? (Note: this takes a minute or 2 to run. It will report if the disc has errors or not).
You should check the CD first in order to verify that the CD is good. If you are not even able to run the option to check for defects it is likely that the CD is bad.
How did you burn the Ubuntu CD? If you are burning it from Windows use Iso Recorder or Info Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the slowest possible speed to avoid data corruption. Then boot the CD and run the option to check for defects. 
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by Newandexcited on 2009-10-07
I tried first to install ubuntu but nothing happened, I then tried to check the disc for defects and again nothing happened.  It is extremely frustrating that nothing is working, as my computer seems stuck in the middle of a downgrade to XP but won't continue.  Any ideas on whether I can reverse a install that hasn't finished?  I know that by changing loading XP is used FAT32 not NTSF, whihc may be the problem with my recovery discs but what does ubuntu use?

---

### Post by gchand7 on 2009-10-07
You may have to wipe the hard drive with gparted using the live cd. I have an Acer
5920 and had to go in the bios and change my hard drive from sata to the other choice can't 
remember but there was only 1 other choice.. good luck

---

### Post by tommcd on 2009-10-08
> **Newandexcited said:**
> I tried first to install ubuntu but nothing happened, I then tried to check the disc for defects and again nothing happened.
Just running the live CD to check for defects should not be dependent on the hard drive. It is likely that your CD is bad. You could try running the live CD on a different computer if you can just to verify this.
 Try burning a new CD if you can using Iso Recorder or Infra Recorder as per the link in my last post. Burn the CD at the slowest possible speed. Then boot the new CD and check it for defects. If it passes, then try to run the live CD to "use Ubuntu without making any changes to your system" (as it says on the live CD). 
You can then use gparted to format the hard drive to ext3 or ext4 as Gchand7 said. Then try to install Ubuntu.

---

### Post by presence1960 on 2009-10-08
> **tommcd said:**
> Just running the live CD to check for defects should not be dependent on the hard drive. It is likely that your CD is bad. You could try running the live CD on a different computer if you can just to verify this.
 Try burning a new CD if you can using Iso Recorder or Infra Recorder as per the link in my last post. Burn the CD at the slowest possible speed. Then boot the new CD and check it for defects. If it passes, then try to run the live CD to "use Ubuntu without making any changes to your system" (as it says on the live CD). 
You can then use gparted to format the hard drive to ext3 or ext4 as Gchand7 said. Then try to install Ubuntu.

+1

you should also [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it to CD. If even one charcter is off the iso is no good. Try dowloading the iso from a torrent as they check the hashes during the download process.

---

### Post by 3rdalbum on 2009-10-08
If you can get a hold of a copy of the Ubuntu Alternate CD, this is more likely to be successful in installing Ubuntu. It loads up a small operating system and a text-GUI installer program that you can use to install a full copy of Ubuntu. If you're having troubles with the live CD's boot menu, then the Alternate CD doesn't have a boot menu :-)

---

