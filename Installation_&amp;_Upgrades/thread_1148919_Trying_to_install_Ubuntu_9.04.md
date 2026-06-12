---
title: "Trying to install Ubuntu 9.04"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Raygreen on 2009-05-04
I don't know how similar this is to you, but I have been running Ubuntu on 2 PC's from within Windows XP. One is a desktop Compaq computer, the other an older Dell Latitude laptop. Both running Ubuntu 9.04 fine. 

I recently have another Dell Desktop that I wiped the harddrive with wipedrive and it was running Windows XP, I want to sell the computer but was going to just install Ubuntu 9.04 on it as the sole operating system. I can get it to run live from the CD but it keeps failing when I try to load it as the operating system on this computer. I went and loaded Windows XP and it loads fine onto the computer. Then tried to add Ubuntu side by side, and that failed too. I even took my Ubuntu 8.1 version and tried that and it failed too. I can only get them to run live from the CD. I know I had success in loading Ubuntu 8.1 as the sole operationg system on the Dell Latitude laptop in the past. I just keep getting errors when I try and do it with this Dell Tower that has a Maxtor 163GB harddrive. 

I have run all kinds of fdisk commands to repartition it and then every time I go to load Ubuntu to the harddrive, it locks up or gives me an error message. Not sure if it is a harddrive incompatibility.

When I run sudo  lshw -C disk

gives me 
description: ATA Disk
product: Maxtor 4G168J8
vendor: Maxtor
physical id: 0
bus info: scsi@0:0:0:0
logical name: /dev/sda
version: GAK8
serial: 153GiB (163GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=0002d8c3

Prepare disk space

This computer has no operating system on it. 

I tell it to use the entire disk
shows /dev/sda1 150.5 GB swap (/dev/sda5) 2.1 GB

Partitions formatting
*Creating ext3 file system for / in partition #1 of SCSI1 (0,0,...*

then at 5% this time sometimes it gets to 25% it gives me a message

[COLOR="Red"]Failed to create a file system
The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.[/COLOR]

Then get
[B][COLOR="DarkOrange"]ConsoleSetup crashed
ConsoleSetup failed with exit code2. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.[/COLOR][/B][B][COLOR="Purple"]

Any help would be appreciated!!![/COLOR][/B]:confused::confused:

---

### Post by Raygreen on 2009-05-05
After reading some other posts I went and burnt a new iso file that I downloaded last night from a different site. This time I burnt it to DVD. I did it through Ubuntu on my other computer, since my Windows XP doesn't have a problem to burn iso to DVD. When I ran the Check Disk for defects, it found 3 bad files on the DVD burning. When I did it on the CD version it didn't find any. Some posters said they had better luck loading from a DVD. I will have to try reburning the DVD again.

I am starting to think burning a DVD is not really the answer. :(

---

### Post by 73ckn797 on 2009-05-25
Did you verify the md5sum's on the downloaded iso?

---

### Post by Raygreen on 2009-05-28
I burnt the disk 3 times and ran verification on it. I am able to run Ubuntu Live on the computer, also I can get it to run Wubi through windows. It just will not load onto the harddrive by itself. I think there is a conflict with the hard drive or the DVD on that computer. I had the same problem loading Fedora, Kubuntu, PClinux, Linux Lime, Mandriva, the only 2 that loaded were Freespire and openSUSE, which is on it now solely.

---

### Post by Raygreen on 2009-05-31
I was able to get openSUSE to load on the computer, but I really wanted to get Ubuntu to load. There is a problem with the sound playback with openSUSE. When I run live Ubuntu on this computer the sound works fine when I load Flash and run it through Firefox. But everytime I try to load Ubuntu on the harddrive, I get error messages. Very frustrating. Trying to resolve the sound issue with openSUSE is just as frustrating.:(:(

*[COLOR="DarkRed"]I am trying to stay positive, but very hard to get much feedback. Yet others that seem to get immediate responses when they are trying to go back to Windows. I have had success with Ubuntu on my other 2 computers. The only distro that works on this computer is Freespire which is a KDE version. I prefer to go with Gnome. It loads on the harddrive and it has great sound with youtube feedbacks.[/COLOR]*

---

### Post by 73ckn797 on 2009-05-31
> **Raygreen said:**
> I burnt the disk 3 times and ran verification on it. I am able to run Ubuntu Live on the computer, also I can get it to run Wubi through windows. It just will not load onto the harddrive by itself. I think there is a conflict with the hard drive or the DVD on that computer. I had the same problem loading Fedora, Kubuntu, PClinux, Linux Lime, Mandriva, the only 2 that loaded were Freespire and openSUSE, which is on it now solely.

I see that you burned the disk and ran checks but that is not the same as running a md5sum on the iso prior to burning. You have not stated that you did that. I would assume that you burned the disk at  the slowest speed. There can be issues if it is burned too fast.

---

### Post by Raygreen on 2009-05-31
Thanks for responding to my last post. Well, I went downloaded **[COLOR="Red"]winmd5sum[/COLOR]** and ran it and everything checked out. I also ran the check disk for defects. I even tried running Ubuntu 8.10 and it also had problems loading onto the computer's harddrive. 

[COLOR="Purple"]Now I was able to get openSUSE and Freespire to load on the harddrive. Not sure what the difference is between Ubuntu's grub versus the others.[/COLOR]

---

### Post by Raygreen on 2009-08-04
Well I guess I kept trying and I finally got Ubuntu to load on the computer. I first tried to load Ubuntu 9.04, that didn't work. I then tried to load Ubuntu 8.1 and that didn't work. I then tried to load Kubuntu 8.10 and that failed to load. In between I got Windows XP to load, I got Freespire Linux to work. I also got a few other versions of Linux to work, but each had its own set of limitations and I really wanted to get Ubuntu to work. 

Finally, I went and tried and successfully got Ubuntu 7.10 to load. I am now in the process of upgrading it to 8.04. Then I will try and see if I can at least get it up to 8.10. Maybe then go for Ubuntu 9.04. Will let you know if it works. :)

---

### Post by Raygreen on 2009-08-05
Ok, I am now in the process of upgrading to Ubuntu 9.04!!!

---

### Post by Raygreen on 2009-08-06
Finally, I have Ubuntu 9.04 running on this computer. I just had one glitch, which I found a remedy. I got a tracer applet index error message, that kept popping up every time I booted into Ubuntu. Ran some lines in terminal and able to stop them.

---

### Post by exemplarstudent on 2009-08-20
hey, thanks for writing this down in here (even if it was mainly for your own help)- i have the exact same problem with a dell inspiron B130, and although i havent got to the 9.04 upgrade yet, it looks like your solution is working for me, too.

---

