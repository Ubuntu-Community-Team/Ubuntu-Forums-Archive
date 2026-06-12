---
title: "Help On Restoring Files And XP After Failed Ubuntu Install"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by DCX on 2006-02-17
Alright, I was on here before asking for help with installing Linux, but to make a long story short it didn't work.

Now I believe that I have deleted my XP Media Center Edition through the partitioning process. Even though I made a new partition and a swap, leaving the main free space alone, I thought that was what I had to do, is that not right?

Anyways, now I couldn't load Windows at the boot screen, it doesn't even come up as an option. I put in the system restore CD included with my laptotp (Toshiba Qosmio F10) and went through the entire system restore.

Upon restarting my computer, it still tried to load Ubuntu but had a "error 22 Y (y had two dots above it) I still didn't have the option to boot Windows.

After talking to Toshiba, they told me to go through the Ubuntu CD install and remove the partitions in the partion process. I deleted all of them, exceot the normal "free space" was still there but that is supposed to be right. Then I aborted the install and shutdown and rerun the windows system restore disk. 

Well, I still had the same problem, extremely frustrating that I can't use Ubuntu or XP Media Center Edition.

Can anybody tell me what I can do, the Toshiba support guy reccomended Fdisk, will that work.

Also, are all of my Windows files lost forever now? I saw that I can use programs which can restore data even if it is deleted during a format or partition error. Will those get me back my Windows files?

---

### Post by aysiu on 2006-02-17
Do you have the Ubuntu live CD or just the installer one?
If you have the live CD, you can back up your Windows files with it and then reinstall Windows.

If not, you can try using the XP installer CD to [fix the Master Boot Record](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx) and restore it to Windows.

---

### Post by DCX on 2006-02-17
I do have the Ubuntu Live CD as well as the Install CD, do I just put it in and boot with it? It will give me those backup and reinstall options. If so that sounds great!

I can't try that right now, I am at school. I will go home tonight and attempt that. I really hope it works.

Thank you very much for your help:-D

---

### Post by aysiu on 2006-02-17
[QUOTE=DCX]I do have the Ubuntu Live CD as well as the Install CD, do I just put it in and boot with it? It will give me those backup and reinstall options. If so that sounds great![/QUOTE] No, unfortunately, backing up with the Ubuntu live CD requires a little bit of command-line (it's not hard, but you do have to get instructions, and I can give them to you).

If you had a Knoppix live CD, it'd be a lot easier to back up. You'd just boot up, and your Windows partition would be sitting as an icon on your Knoppix desktop. You click on the icon, and it automounts and opens. Then you could copy those files over to something (blank CDs, an external hard drive, an iPod, whatever).

With the Ubuntu live CD, after booting it up, you would need to find out where your Windows partition is first.

You would go to Applications > Accessories > Terminal and type ```
sudo fdisk -l
``` When I do that, I get ```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS**
/dev/hda2            1912       19457   140938245    5  Extended
/dev/hda5            1912       18174   130632516   83  Linux
/dev/hda6           18175       18295      971901   82  Linux swap / Solaris
/dev/hda7           18296       19457     9333733+  83  Linux
``` Then, I would see that my NTFS partition is /dev/hda1. So I would create a temporary mount point: ```
sudo mkdir /windows_recovery
``` and then mount my Windows partition there ```
sudo mount -t ntfs /dev/hda1 /windows_recovery
``` and finally, open a file browser with root privileges so I could copy over the Windows file to the external media ```
gksudo nautilus
``` I'm sorry Ubuntu didn't work out for you. If you try Linux again in the future, get a hold of Knoppix CD and play around with it (live CDs run off the CD and your computer's RAM--they don't affect the hard drive) for a while (a week or two) and really get to know things before installing it. I know some people like to dive right in and install things, but I played around with Knoppix before installing anything on my Windows computer. Wish you the best of luck in getting everything working again.

Please post in this thread any further questions you have about the backup process.

---

### Post by DCX on 2006-02-18
Alright, I figured it out from what you told me, now I have access to a folder called "windows_recovery"

It seems to have access to all of the standard Windows files. Unfortunately, I can't seem to find my documents... If I don't see them in here, are they gone forever or can I retrieve them some how, like with a program or something?

---

