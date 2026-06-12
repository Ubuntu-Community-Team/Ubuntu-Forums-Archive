---
title: "problems installing xubuntu base system"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by mountev on 2009-06-16
Complete noob here. I have a compaq presario 5900T 
256MB RAM
pentium III processor
80 GB HD
 
That being said, I have downloaded the alternate CD and verified the checksums. I copied to disc at 2x. I get all the way to installing base system when I get all kinds of corrupt messages. The HD was wiped so there is no OS on it. I can't seem to get past this point. Any suggestions?

---

### Post by izizzle on 2009-06-16
Why did you download the alternate CD? Try it with the LiveCD and see if it gives you the same errors.

edit: w00t 500 posts!

---

### Post by mountev on 2009-06-16
I did try the live CD and it just stops installation with error code 127.  I thought that with only 256MB RAM that I was on the border so I tried the alternate CD.

---

### Post by mountev on 2009-06-16
The live CD now says the ext3 file system creation in partition #1 failed.  I can format the disc when I use the alternate CD though.

---

### Post by izizzle on 2009-06-16
It seems like either it's a hard drive problem or a problem with the cd. Did you compare checksums for the LiveCD. Also, when you boot up the LiveCD, select the "Check CD for defects" option.

---

### Post by paulbyr on 2009-06-16
I apologize for tagging on but I too am having install trouble-  But with the 
HDD install of Ubuntu 9.10.

 I can use the Livecd version ok and it seems to be able to install onto a totally blank 160GB HDD.  Then when I reboot and select Ubuntu in the dual boot screen, it says:
"Missing or Corrupt
Windows root>\system32\hal.dll
please reinstall a copy"

I then have to do cntrl/alt/del to reboot and select WindowsXP and that works fine.

The HDD which contains Ubuntu and its swap area shows 146 GB for Linux Ext3 and 6GB for Linux swap according to my PartitionMagic ver. 8

Does it seem that something happen when I installed that affected the boot area on the Linux HDD?

I am a total newbie at Linus/Ubuntu (as you probably guessed).



Thanks

---

### Post by mountev on 2009-06-16
Yes, all of the checksums matched.  I hate to admit it probably is the HD.  This is an older computer that was given to me and I have been waiting to give xubuntu a try.  Thanks.

---

