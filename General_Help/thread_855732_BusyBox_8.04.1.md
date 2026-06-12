---
title: "BusyBox 8.04.1"
date: 2008-07-10
forum: General Help
---

### Post by MyBrainReallyHurts on 2008-07-10
Downloaded 8.04.1 and let it download the ISO

The PC reboots and then I get to the BusyBox prompt. 

After researching I have already done the chkdsk /r and I have shut down the PC several different times in several different ways. 

When I try to do the following:

1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug"
3. reboot
4, at the command line type "cat /tmp/*.debug" <enter>
5. there should be an error in the latest few lines, post it here.

It isnt even there. The grub foldet is there, but the menu.lst is not. 

Ok, now I am stumped. I was able to get Ubuntu working in VMware, but I wanted it to run using Wubi so I could use all of the features. 

Any ideas anyone?

MyBrainReallyHurts

---

### Post by MyBrainReallyHurts on 2008-07-10
I was able to change the Quick Splash entries. Same problem. Going to try chkdsk /r again.

---

### Post by Animus Stealth on 2008-07-10
Did you try installing the UBUNTU from an windows XP account? Instead of the startup ?

---

### Post by MyBrainReallyHurts on 2008-07-11
> **Animus Stealth said:**
> Did you try installing the UBUNTU from an windows XP account? Instead of the startup ?

Yes, I am installing it from an XP account that has Administrator rights to the workstation. 

Everytime I try to install, it always stops with a BusyBox. 

I changed everything I could change with posts from the forums, and I ran the chkdsk /r. It still stops with a BusyBox. It should run on this hardware, as I was able to install it into VMware. 

I ran the install in verbose, and these are the last two lines before it stops. 

[ 27.712943] SGI XFS Quota Management subsystem
[ 27.718343] JFS: nTxBlock = 7975, nTxLock = 63803

Any and all suggestions would be appreciated. 

HP nx7400 laptop. 
Windows XP Pro SP3
1 GB of RAM
68 GB Hard Drive. I had 22 GB free before installing Wubi. 
There is also a HP_Recovery Partition that is FAT32. 6.5 GB. 

I am wondering if that Recovery Partition is the culprit. 

Any ideas?

---

### Post by MyBrainReallyHurts on 2008-07-11
By the way, I am using Wubi-8.04.1-rev506.exe

...

I think I just realized what happened. Even though my Windows is the 32 bit version, Wubi downloaded the 64 bit version. I will download and try the 32 bit version and see if that works.

---

### Post by MyBrainReallyHurts on 2008-07-11
Ubuntu successfully installed with Wubi. 

It is strange that Wubi kept grabbing the 64 bit iso when I only have a 32 bit workstation. Could this be because it has XP SP3 on it? 

Once I had the right iso and Wubi in the same folder, it worked correctly.

---

### Post by plastichero on 2008-07-15
try replacing "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works.

---

### Post by smo0th on 2008-07-17
> **MyBrainReallyHurts said:**
> Downloaded 8.04.1 and let it download the ISO

The PC reboots and then I get to the BusyBox prompt. 

After researching I have already done the chkdsk /r and I have shut down the PC several different times in several different ways. 

When I try to do the following:

1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug"
3. reboot
4, at the command line type "cat /tmp/*.debug" <enter>
5. there should be an error in the latest few lines, post it here.

It isnt even there. The grub foldet is there, but the menu.lst is not. 

Ok, now I am stumped. I was able to get Ubuntu working in VMware, but I wanted it to run using Wubi so I could use all of the features. 

Any ideas anyone?

MyBrainReallyHurts

try the following:

from your xp, open cmd and type ```
chkdsk /f d:
``` assuming drive d is where you installed your wubi. Reboot and you should be able to use ubuntu again :)

PS: by typing "cat /tmp/*.debug" you will get nothing, you need to specify the complete filename, don't use * with cat or it won't work ;)

---

### Post by ago on 2008-07-17
> **MyBrainReallyHurts said:**
> Ubuntu successfully installed with Wubi. 

It is strange that Wubi kept grabbing the 64 bit iso when I only have a 32 bit workstation. Could this be because it has XP SP3 on it? 

Once I had the right iso and Wubi in the same folder, it worked correctly.

What processor do you have exactly?

---

