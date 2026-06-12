---
title: "Reclaiming Lost Space by Gparted"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by apanda02 on 2009-10-06
Hi, 

I wasn't getting into linux by doing a dual-boot b/c windows was simply much more convenient -- so I decided to run ubuntu as a virtual machine. 

1. To do this, I ran Gparted -- merged my Ubuntu/swap partition back into the XP partition. The operation went well w/ deletion but gave me a error when merging back.

2. When I ran G-parted again it showed only the windows partition.

3. When I rebooted into windows it doesn't show the extra space I merged in! Is there any way I can get the space back w/o reformatting?

Thanks in advance!!

panda

---

### Post by pawhtiobo on 2009-10-06
Hi :)

That depends...in the properties of the windows partition does it show the correct size? if so... you can boot yout PC with the XP CD, get into the recovery console and do a chkdsk /f (force), to see if it corrects the error...another option is to do a scandisk in Windows and choose all the repair options, after the reboot the process will begin...and see whats the result :)... final option is to install software for managing partitions in windows, i use partition magic, resize again the HD as it was before and merge it again, i advice you to resize the HD, create the new partions, reboot, start again Partition magic, delete the new created partitions and then resize the XP partition to use the all HD space...

Hope that helps...

See ya...

---

### Post by apanda02 on 2009-10-06
Thanks for your help pawhtiobo, my windows partition doesn't actually show the right size. Its still showing the original...so I guess I will go w/ the third option of installing parition magic and then report back the results.

Thanks!
Panda

---

### Post by Bucky Ball on 2009-10-06
My advice is to defrag before doing any resizing in Windows or with a Windows partition.

---

### Post by apanda02 on 2009-10-07
Hmm funny thing...when I go into Control Panel->Admin Tools->Computer Management->Disk Managment it shows C: as the total size...but where it shows the detailed information it shows C: as only the pre-merging partition size...chkdsk didn't work...I guess time to use partition magic...

---

