---
title: "Dual Boot 9.10 with Windows 7, Grub issues"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Demented ZA on 2009-11-07
Hi All,

I'm having problems getting Windows 7 and Ubuntu running on the same hdd on the same machine.

I've searched the the forums and it doesn't look like many are having the same problems.

I'm installing onto a single 500gb fakeraid array consisting of two 250gb hdd's. I have no other hdd's in my machine.

I have followed the advice from [http://www.overclockers.com/index.php?option=com_content&view=article&id=4569:how-to-dual-boot-windows-and-linux-on-a-fake-raid-array&catid=58:software&Itemid=4264](http://www.overclockers.com/index.php?option=com_content&view=article&id=4569:how-to-dual-boot-windows-and-linux-on-a-fake-raid-array&catid=58:software&Itemid=4264)

and 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

_All I require partition-wise is the following:_
-Ubuntu 9.10 partitions (root + swap)
-Windows 7 partition (boot+c drive)
-Data Partition

my partition table so far:


Disk nvidia_eahedccc: 500.1 GB, 500118585344 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b830b

          Device                  Boot     Start     End        Blocks         Id       System
nvidia_eahedccc1              1          10443     83883366     83      Linux
nvidia_eahedccc2              10444   10456     102400         7       HPFS/NTFS
nvidia_eahedccc3     *       10456    20899     83884032     7       HPFS/NTFS
nvidia_eahedccc4              20900   60802     320520847+  5       Extended
nvidia_eahedccc5              60053   60802     6024343+     82     Linux swap

I havn't formatted my data partition yet, which i'll add to the logical partition. But thats not important right now as I can always do that afterwards.

So far, I have installed linux first, perfectly working on the fakeraid array (nvidia_eahedccc1 as root and nvidia_eahedccc5 as swap inside nvidia_eahedccc4). 

Afterwards, I install Windows 7, creating nvidia_eahedccc2 (system reserved partition) and nvidia_eahedccc3 (c drive).

Obviously only Windows 7 boots now. Now I have to repair grub so as to get Linux booting, and then manually add Win7 to grub's menu.lst.

I follow the steps at [www.overclockers.com]("http://www.overclockers.com/index.php?option=com_content&view=article&id=4569:how-to-dual-boot-windows-and-linux-on-a-fake-raid-array&catid=58:software&Itemid=4264") to install grub again. However, I notice that its Grub, and not Grub2 as is native to Karmic Koala.

Anyways, everything goes smooth and grub installs. I edit menu.lst and add the following:

title        Windows 7
rootnoverify    (hd0,1)
makeactive
chainloader+1

After rebooting, grub loads and I have a choice between Ubuntu or Windows 7. Ubuntu loads fine, but when I select Windows 7, it doesn't boot. (I forgot the error. I'll reboot and make note of it again)

I'm not sure if the problem is grub's menu.lst, if its because I went back to grub instad of grub2, or if i have a problem with my partition layout.

I suppose it could also be the raid array, but I doubt it. I'm trying the same setup on my laptop now to see if i can replicate the error. If so, its not raid, but something i'm doing wrong.

Any help would be greatly appreciated.

---

### Post by Maheriano on 2009-11-10
Same problem here. Any help here?

---

### Post by jakswa on 2009-11-13
I'm in this same boat.  Had fakeraid working on 9.04... 9.10 just doesn't seem to want to cooperate with me though.

I think some of my problems are stemming from fakeraid being "supported out-of-the-box" in this release:  [https://bugs.launchpad.net/ubuntu-release-notes/+bug/462631](https://bugs.launchpad.net/ubuntu-release-notes/+bug/462631)

Which is funny...

---

### Post by weaselnet on 2009-11-17
I had the same problem and finally from some research found a solution.

I had Windows 7 installed first. When I couldn't get Grub2 to see Windows 7 I decided to restore the windows boot loader.

Step 1. Boot to the CD.
Step 2. Repair Computer.
Step 3. Open a Command Prompt.
Step 4. (Use the CD drive letter on the following commands.)
        
bootrec.exe /FixMbr
\boot\bootsect.exe /nt60 all /force
exit

Step 5. Restart into windows. 

Download EasyBCD beta 2.0 from neosmart and install. (Must register as a member to access.)

Add a Entry, Linux, Grub2, Name and save. 
Reboot.

---

### Post by miguelm on 2010-02-21
My experience with almost the same problems:
2x250gb WD with ICH9R
Win 7 
Ubuntu 9.10 installed after win.


I didn't have the Windows 7 boot partition.

Ubuntu installed GRUB ( not grub2 ) I don't know why... so just adding:

title Windows
root (hd0,0) # change your numbers 
makeactive
chainloader +1


hd0,0 is the standart for the first partition of the fakeraid 

IF YOU NEED TO REINSTALL GRUB on the fakeraid:
look post #5 ( maybe you only need since the 7 step )
[http://ubuntuforums.org/showthread.php?t=1305138](http://ubuntuforums.org/showthread.php?t=1305138)  

I needed beacuse I used the windows 7 dvd to reinstall bcd.

---

