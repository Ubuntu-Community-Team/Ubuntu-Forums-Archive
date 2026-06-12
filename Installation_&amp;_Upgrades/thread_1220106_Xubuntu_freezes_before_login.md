---
title: "Xubuntu freezes before login"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Mugga on 2009-07-22
Hi :)

I just got an old laptop, and I decided to try out Linux as Windows was really slow on it. First I tried to run the Ubuntu LiveCD, but that froze. Then I tried the Xubuntu LiveCD as I was told that my laptop was to slow to run Ubuntu.

Then I was told that my laptop was to slow to run the LiveCD itself, so I decided to make an install next to my Windows XP with the Xubuntu alternate CD. The install went perfectly fine, but when I got to the login-screen it froze.

Here are my specs:

> ------------------
System Information
------------------
Time of this report: 7/22/2009, 11:03:51
       Machine name: DIT-F3F513180D1
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.090206-1233)
           Language: Danish (Regional Setting: Danish)
System Manufacturer: MTC
       System Model: Montara-GML 
               BIOS: Insyde Software MobilePRO BIOS Version 4.00.00
          Processor: Intel(R) Celeron(R) M processor         1.30GHz
             Memory: 256MB RAM
          Page File: 359MB used, 258MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

---------------
Display Devices
---------------
        Card name: ATI MOBILITY RADEON 9600/9700 Series 
     Manufacturer: ATI Technologies Inc.
        Chip type: ATI MOBILITY RADEON 9700 AGP (0x4E50)
         DAC type: Internal DAC(400MHz)
       Device Key: Enum\PCI\VEN_1002&DEV_4E50&SUBSYS_80501071&REV_00
   Display Memory: 128.0 MB
     Current Mode: 1280 x 800 (32 bit) (60Hz)
          Monitor: Standardskærm

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 30.8 GB
Total Space: 38.2 GB
File System: NTFS
      Model: SAMSUNG MP0402H

      Drive: D:
      Model: QSI CDRW/DVD SBW242C
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (Danish), 8/27/2004 14:00:00, 49536 bytes

I hope that you guys can help me.

---

### Post by dstew on 2009-07-22
Can you boot in Recovery Mode (a grub boot menu option)?

---

### Post by Mugga on 2009-07-22
In the recovery menu I get the following options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

Which should I choose?

EDIT: Just now I was able to enter username but before finising entering my password it crashed and the screen got full of hundreds of small vertical lines in different colors filling up the entire screen. I've seen it before where it's only the top or bottom that graphicly screw up.

---

### Post by Mugga on 2009-07-23
*Bump*

---

### Post by dstew on 2009-07-23
First try **xfix**, to see if you can get a useable interface. If that doesn't work, use **root** to get a command line. If you can get a command line, there are other things we might try.

---

### Post by Mugga on 2009-07-24
I appreciate the help!

xfix didn't do anything to the problem. Still freezes at the login screen.

I searched google to find a solution to my problem and I came across this

> With the newest realease of Ubuntu (9.04 Jaunty Jackalope) came a major problem with support for older ATI graphics cards. Though these cards work with generic drivers, the ability to use dual heads and more advanced configurations has been lost. You may think that you can simply head over to AMD&#8217;s ATI driver page and get a driver, but the latest version of Catalyst does not support the older cards. &#8220;Maybe I can just download an older version of the driver,&#8221; might be what you are thinking, but the old driver is not compatible with the new version of xserver that is included with Ubuntu Jaunty.[http://tan-com.com/posts/technology/linux-os/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/linux-os/fix-ubuntu-904-ati-driver-issue)

I see that there is a topic on this here, but no one mentions how to solve my problem with not being able to log in at all :( [http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by dstew on 2009-07-24
The ATI driver may have a bug in it. If you remove it, Xubuntu will default to another driver that should work, but have less features. To remove the ATI driver, boot in recovery mode, and select "root" to get a command line. On the command line enter```
sudo apt-get remove xorg-driver-fglrx
```That should remove the bad driver. Then, you can shutdown and reboot. To shutdown, do```
sudo shutdown -h now
```

---

### Post by Mugga on 2009-07-25
It says **E: Couldn't find package xorg-driver-fglrx** :(

---

### Post by Mugga on 2009-07-26
What to do now? Any ideas?

---

### Post by dstew on 2009-07-27
You can get a command line boot, correct? If so, try **startx** and see if you get any errors. Maybe that will give a clue.

---

### Post by Mugga on 2009-07-28
It jumped almost right away to my desktop with **startx**, but unfortunately I can't move the cursor at all :(

I just tried again, and it logged in again, but shortly after the screen went all blue in  the same kind of pattern I've seen before.

---

### Post by dstew on 2009-07-28
Clearly the xserver is having trouble with your hardware. You could keep trying to fix it, but it might be better to try an earlier release, like 8.04. That would probably work. Since you had install problems before with a live CD, I would recommend installing [8.04 using the Alternate Install CD]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate"). The 8.04 iso's are listed below the 9.04 ones.

---

### Post by Mugga on 2009-07-30
Previous version of both Xubuntu and Ubuntu still freezes.

Ive given up on this. I installed Ubuntu via Wubi on my main laptop to test it out.

Thanks for your help!

---

