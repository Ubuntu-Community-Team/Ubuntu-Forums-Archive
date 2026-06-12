---
title: "Cannot install from USB after using unetbootin"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by levicc00123 on 2009-11-05
Hi, I downloaded the Ubuntu 9.10 ISO from BitTorrent, and ran unetbootin to prepare my 2GB thumb drive. After rebooting my computer, I started the installation, I got a Input/Output error during the installation. I run

```
cd /cdrom && md5sum -c md5.txt
``` to check for problems and find filesystem.squashfs is corrupt. Is there another way to install ubuntu from USB?, and is there a way to make sure my thumb drive is still working in peak condition?

---

### Post by RMJohn on 2009-11-05
Hi, I have a similar issue. I tried preparing my USB drive based on what is told [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")
It says "usb-creator.exe is located in the CD image already for you! "

However, I dont see a usb-creator.exe file anywhere on the iso file. In fact the only .exe file in my ubuntu-9.10-desktop-amd64.iso is wubi.exe. I did check the MD5checksum and its correct. 

Someone please advise how to install ubuntu from usb. My laptop does not have a DVD/CD drive.

---

### Post by mr chip on 2009-11-06
RMjohn, I'm having the same problems as you are. I've downloaded the same ISO as you, and the MD5 is correct, but there's no usb-creator.exe.  I also tried using unetbootin to make my usb drive bootable with this ISO, but without success.  I know that my USB drive set up with unetbootin does work with my system, as I have gotten it working with ubuntu 9.04 and with damn small linux 4.4.10
 
I'm beginning to suspect that there's something wrong with the 9.10 x64 release that's causing our problems.

---

### Post by RMJohn on 2009-11-06
Its not just the amd64 version.. I have also downloaded the desktop i386 version. That doesnt have the usb-creator.exe too. Are we missing something.. its my first foray into linux.. someone please help us.

---

### Post by RMJohn on 2009-11-06
Someone please help.. I heard Linux community is very helpful. I dont see much response here though.

---

### Post by jaduvet on 2009-11-06
Seems there is a problem with the dist. At least i havent found a solution to the same problem. And there is some other threads reporting same problem in different ways
  
   there is no usb-creator.exe on the 9.10 x64 disk and it seams the problems applies also if you try to use unetbootin 
  
  But still no explanation if this is a user (you, me and her rest) error or a ubuntu error (embarasing then)
  
  threads:
  
  [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1317008)
  [http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508](http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8255508)
  [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1310707)
  [http://ubuntuforums.org/showthread.php?p=8257120](http://ubuntuforums.org/showthread.php?p=8257120)
  [http://newyork.ubuntuforums.org/showthread.php?t=1313987](http://newyork.ubuntuforums.org/showthread.php?t=1313987)

---

### Post by RMJohn on 2009-11-06
> **jaduvet said:**
> 
   there is no usb-creator.exe on the 9.10 x64 disk and it seams the problems applies also if you try to use unetbootin 
  

Interesting.. But please note that this invisible usb-creator.exe does not exist in desktop i386 version as well. I had downloaded that first and couldnt find this animal in there too.. I had no patience to download the other versions and check whether usb-creator.exe is missing from all other distributions... 

Thanks for putting together all those links.. So the answer is clear... either all of us who report this problem are dumb enough not to be able to find a non-existing file..  Or folks behind Ubuntu were in a lot of hurry while creating those .iso files, didnt have time to check whether their files contain what they claim it did.

Meanwhile I found this link... yet to check whether this solution will work. If someone wants to give it a try.........
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by mr chip on 2009-11-06
> **RMJohn said:**
> 
Meanwhile I found this link... yet to check whether this solution will work. If someone wants to give it a try.........
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)


Excellent, this has worked for me with the 9.10 AMD64 version.  I can't believe I forgot about Pendrivelinux.

I'm going to see about updating the Ubuntu documentation, the current doc for creating USB live install is worse than useless.

---

### Post by RMJohn on 2009-11-06
> **mr chip said:**
> Excellent, this has worked for me with the 9.10 AMD64 version.  I can't believe I forgot about Pendrivelinux.

I'm going to see about updating the Ubuntu documentation, the current doc for creating USB live install is worse than useless.


Nice... it worked for me too.............

---

### Post by JustinR on 2009-11-06
Yes I couldn't find the usb-creator.exe too - but all I did to install Ubuntu to a thumbdrive was to use the Install Ubuntu 9.10 icon on the ubuntu desktop (in a VMware machine) and it installed everything from there to the flashdrive - it worked perfectly.

---

### Post by levicc00123 on 2009-11-07
> **RMJohn said:**
> 
Meanwhile I found this link... yet to check whether this solution will work. If someone wants to give it a try.........
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

I tried that link and got the same result, md5 check on filesystem.squashfs fails. I just bought a set of CDs and I'll just burn the ISO.

---

### Post by JustinR on 2009-11-07
Hey I don't know if this matters now but I found USB Creator in  Synaptec Package Manager and it works.

---

### Post by leorolla on 2009-11-10
You can try this, that's what I do all the time:

[http://ubuntuforums.org/showthread.php?t=1316536&page=2](http://ubuntuforums.org/showthread.php?t=1316536&page=2)

---

### Post by duanedesign on 2010-01-02
Guide to creating a Llive USB:
[http://ubuntuforums.org/showthread.php?t=1193680](http://ubuntuforums.org/showthread.php?t=1193680)

**Known Issues**
The 9.10 CDs and DVDs are [COLOR="Red"]missing the usb-creator.exe program[/COLOR]. To install to a flash drive from a disk image on Windows, use the incredibly easy process described at:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) 
-

---

