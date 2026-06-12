---
title: "Installing windows xp again"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Sherina on 2009-10-29
I want to dual boot ubuntu 8.04 to windows xp. I already formatted my drive to use ntfs file system but when I try to install windows using my recovery disk it will show a black screen for about 30 seconds then boot into ubuntu. How do I install windows on my ubuntu desktop?

I am using a gateway desktop.

Thank you.

---

### Post by prcm311 on 2009-10-29
Can you provide a little more information about your system?

How many hard drives do you have?  What size/format are the partitions?

Here are the basic steps you will need to follow although I'm not sure of your exact system configuration:

1.) Create a partition for Windows XP, NTFS (Sounds like you used Ubuntu to accomplish this part already)

2.)  Insert the Windows XP install disk, restart and boot from CD.  *You may need to change the boot settings in your BIOS in order to boot from the Windows install CD.

3.)  Follow the Windows installation instructions and install to the partition you've already created.

4.)  Because you are installing Windows XP after you've already installed Ubuntu you will have to re-install GRUB.  You can find instructions on that [COLOR="Blue"][here]("http://ubuntuforums.org/archive/index.php/t-24113.html")[/COLOR].

---

### Post by Sherina on 2009-10-29
Its a gatway 420gr with 512mb ram, 2.93 ghz pentium 4, and intel graphics

Ok this is a stupid question but, how do I change the settings in my BIOS?

---

### Post by mikewhatever on 2009-10-29
Changing the BIOS settings is probably unnecessary, since you've installed Ubuntu successfully before. Be aware, that a recovery disk provided by the manufacturer is usually not the same as a standard Windows installation media. Recovery disks are usually designed to blank the entire hdd, repartition and copy the installation image over. Backup your files and be prepared to reinstall Ubuntu.

---

### Post by Sherina on 2009-10-29
Well it appears that my dvd drive can no longer read dvds. But thank you for all your help.

---

