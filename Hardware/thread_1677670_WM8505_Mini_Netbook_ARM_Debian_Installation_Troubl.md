---
title: "WM8505 Mini Netbook ARM Debian Installation Trouble D:"
date: 2011-01-29
forum: Hardware
---

### Post by ihackedit on 2011-01-29
Okay so I bought [this]("http://www.dealextreme.com/p/7-tft-lcd-windows-ce-6-0-arm-cpu-wifi-umpc-netbook-green-300mhz-2gb-flash-usb-host-sd-slot-lan-44026") and it worked perfectly out of the box when I got it. I then didn't like the boot up logo so used [this]("http://bento-linux.org/wiki/wm8505-bento-linux/changing-bootlogo") and I just had that one change boot logo file on my sd card and it said it changed the boot logo successfully and than followed on saying looking for OS. It didn't find the the OS so I downloaded the files for Linux (Debian) Android and WinCE. I put the Linux files on the sd card without the change boot logo files on and it started the installation process. It then said it could not find a file which was there and I know it was and then it had a terminal thingy that didn't do anything. I tried Android and it didn't work (got to the end of install and said take out SD and I did and it said it would reboot but it didn't start up) I tried WinCE and it worked but was in chinese and when I took out the SD card it said critically low battery please save files and didn't boot up without the SD card in. I found the script to type into the non working terminal (then it had a terminal thingy that didn't do anything) and I tried to boot up Debian again but it wouldn't get past [Erasing kernal....... Done! writing to nand... done!] or something like that and just sort of froze. Please help me find a solution. I promise next time I wont buy a shitty netbook thing from hong kong that cant get Ubuntu 10.10 on it :D

---

### Post by ihackedit on 2011-01-29
BUUMMMP! Anyone? Please help me :)

---

### Post by ihackedit on 2011-01-30
BUMP. Help me, please!!!

---

### Post by dchrono on 2011-01-30
sudo update-initramfs -u

---

### Post by arifalisyed on 2012-10-28
Hi There,
Could you please tell me how did you install Ubuntu onto your device?

I am also looking for the same information here
[http://ubuntuforums.org/showthread.php?p=12323287#post12323287](http://ubuntuforums.org/showthread.php?p=12323287#post12323287)

---

### Post by overdrank on 2012-10-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

