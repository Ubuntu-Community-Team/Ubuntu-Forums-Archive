---
title: "Missing 1GB of RAM"
date: 2009-12-20
forum: Hardware
---

### Post by billyauhk on 2009-12-20
I suddenly find out that 1GB of RAM gone to who-know-where in my Ubuntu notebook...

I have ran memtest in the GRUB page which successfully gives me 4094MB, but the Ubuntu itself always list 3.0GiB in both System Monitor and the command lshw.

lshw Abstract:
     *-memory
          description: System memory
          physical id: 0
          size: 3022MiB

Where did that 1GB go to?? Can anyone help me?

(My notebook is Toshiba Satellite L500)

---

### Post by scott_g on 2009-12-20
Are you running a 32bit version of Ubuntu?  

Do you know what sized chips make up the 4GB?  (ie: 2x2GB chips)?

Thanks,
Scott

---

### Post by oldfred on 2009-12-20
32 bit systems only use just over 3GB whether Windows or Ubuntu. You can install a version of the kernel that is primarily for servers that will address more memory. If your cpu is 64 bit capable it may be time to upgrade to 64 bit. 

I ran 32bit on my system for the last three years as there were some issues with 64bit, I just updated to 64 bit Karmic and have not had any problems. This has the the best update of the last 3 years and my first clean install. All the others were upgrades that required some config file to change or video issues or whatever.

---

### Post by billyauhk on 2009-12-21
I cannot confirm whether I am using a 32-bit kernel. I have (just) used the method described in [http://ubuntuforums.org/showthread.php?t=278606](http://ubuntuforums.org/showthread.php?t=278606) and my terminal says, after uname -a:
 
Linux bill-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
 
mm...pls tell me what's happening. If it is not 64-bit, how can I upgrade the kernel??

---

### Post by Some Penguin on 2009-12-21
That would be 32-bit -- the architecture would otherwise read 'x86_64'.  There's no easy upgrade path from 32-bit to 64-bit -- it's a clean install.

---

### Post by billyauhk on 2009-12-21
Thanks. How can I figure out where are my configuration files so that I can move it to the new installation? Is there any HowTo on that??
 
Please give me a pointer and I can happily mark the thread as SOLVED :)

---

### Post by oldfred on 2009-12-21
For me, since I had 3 years of upgrades I was leery of a clean install. I also had /home inside my install. I was kinda keeping a list of config files that I had edited, but on the upgrades they often needed a new version anyway. I had installed 9.04 64 bit to test and copied all my packages over but found it installed many old things that I did not now want. I moved home to a separate partition but since I want other operating systems also I moved all data to aother separate partition. Now I do not think I even need a separate /home as it only has the hidden config files and a few misc things. I even found in my home a lot of old stuff so I only copied part of it over. I did my Karmic install to a new partition so I could go back and find a config file if necessary. So far it has been fstab so I could just copy my new data partition set up and I saved a copy of my samba config, but still have not set up samba as I only use it ocassionly.  I am not finding much else that I edited that still exists.

---

### Post by HappyFeet on 2009-12-21
> **billyauhk said:**
> Thanks. How can I figure out where are my configuration files so that I can move it to the new installation? Is there any HowTo on that??
 
Please give me a pointer and I can happily mark the thread as SOLVED :)

Go to your home folder and do Ctrl-H. You will then see your hidden configuration directories beginning with a dot. (.)

Just copy the ones you think you might want to keep, and put them where you see fit. Then after the new install, just paste them into the new home folder.

---

