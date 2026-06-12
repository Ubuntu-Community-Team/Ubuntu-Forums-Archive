---
title: "Need Help with Brother DCP-110C"
date: 2005-12-09
forum: Hardware &amp; Laptops
---

### Post by BoredOutOfMyMind on 2005-12-09
I have a new Brother DCP110-c. I purchased this to replace a canon I never could get to run in Kooka. I have read the most excellent howto by wanger123 located at [http://doc.gwos.org/index.php/Print/](http://doc.gwos.org/index.php/Print/) and yet it simply sits here. 

No print jobs arrive and no scanner found in Kooka. 

Any suggestions?

:D

---

### Post by BoredOutOfMyMind on 2005-12-12
[QUOTE=BoredOutOfMyMind]I have a new Brother DCP110-c. I purchased this to replace a canon I never could get to run in Kooka. I have read the most excellent howto by wanger123 located at [http://doc.gwos.org/index.php/Print/](http://doc.gwos.org/index.php/Print/) and yet it simply sits here. 

No print jobs arrive and no scanner found in Kooka. 

Any suggestions?

[/QUOTE]

:razz: 


bored@ursa-major:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04f9:0169 Brother Industries, Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
bored@ursa-major:~$ ps -A| grep cups
20153 ?        00:00:00 cupsd
bored@ursa-major:~$ sudo /etc/init.d/cupsys restart
Password:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

:razz:

---

### Post by wanger123 on 2005-12-14
Hi BOOMM, I too experienced this once and I think from memory (not very good) that I unplugged the usb cable, then plugged it back in, and I could then print a test page (or do this and then reboot and try to print). Hope this helps. I am happy to try and talk you through this installation procedure, as I found it most frustrating at the time as well. 
In fact, after a failed pc-bsd installation (very poor hardware compatability) which did very bad things to my mbr and boot sector causing me to have to reinstall WINXP so I could boot it before reinstalling GRUB for dual booting with Kubuntu (take a breath), I need to follow my howto to get my printer working again. I shall do this tonight and let you know how it goes :smile: 

Cheers
wanger

---

### Post by wanger123 on 2005-12-14
OK, I had a few probs following my own how-to (lol). Could not install using sudo dpkg ........... (later realised I was not in the sudo group) DOH!! :???: 
So anyway without realising that initially, I logged into kde as root and needed to install csh (tcsh). Then I made a new folder called /Brother under the / directory and put the drivers in there. After this I installed the various drivers using right-click ---> install package. Then I set up the add printer wizard. The unbelievable part is that after these simple steps (and despite what my how-to says) I decided to try and print an openoffice document -- guess what? It worked  :confused: So no need to do anything with chmod etc...... But I did add my user name to the lp, sudo and user groups before this. So I thought surely I couldnt reboot and try to print using my user name instead of root could I? Wrong again as usual, everything is working a treat.
All I can put the difference down to, between the how-to guide and my recent experience, is that the how-to was written using a hoary upgraded to breezy system, whereas my current system is a clean breezy install.
Note I havent installed the scanner yet as I need to download sane, but I'm on dialup and it takes ages to update my repositories, but I suspect the notes in the how-to will still apply

[EDIT]
```
wayne@ubuntu:~$ lsusb
Bus 003 Device 003: ID 0e39:1700 Smart Modular Technologies, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04f9:0169 Brother Industries, Ltd
Bus 001 Device 001: ID 0000:0000
wayne@ubuntu:~$ ps -A| grep cups
 7124 ?        00:00:00 cupsd
```

cheers
wanger

---

### Post by BoredOutOfMyMind on 2005-12-14
[QUOTE=wanger123]
All I can put the difference down to, between the how-to guide and my recent experience, is that the how-to was written using a hoary upgraded to breezy system, whereas my current system is a clean breezy install.
Note I havent installed the scanner yet as I need to download sane, but I'm on dialup and it takes ages to update my repositories, but I suspect the notes in the how-to will still apply[/QUOTE]

I took the first printer back as I could not even get windows to recognize it. I thought it was a bad box, and found there is a patch for windows. I then was able to scan and print in XP. I have dual boot with xp on one drive and Kubuntu on another. I rebooted to Kubuntu, which is a hoary upgraded to breezy and can view the sd card as a drive, so thought good, but alas nothing. I have uninstalled and reinstalled. I will try the /brother directory and see if that helps. Brother tech email support was a joke. They told me to uninstall Linux SE- shich is NOT installed. Then they did not reply again. I am ready to return this printer and pay the extra $$ for an HP that will work.... I have 14 days to return with no penalty. 

Thanks for the post.

---

### Post by wanger123 on 2005-12-14
Not sure exactly how you are trying to print, but there is no way that the SD card reader will work in linux

wanger

---

### Post by BoredOutOfMyMind on 2005-12-14
[QUOTE=wanger123]Not sure exactly how you are trying to print, but there is no way that the SD card reader will work in linux

wanger[/QUOTE]

If I boot the machine, this box discovers the SD card reader. I have music saved on a 1 Gig SD card. I even burned 2 CD's from the card!

I would be happy to simply print from OO2 or even from Kate with a simple text file. 

:p

---

### Post by wanger123 on 2005-12-14
Oh I stand corrected then. I assume you mean the brother dcp110c printer sd card reader? 
I guess I was thinking about my dell laptop sd card reader which won't work in linux (Ricoh).

Thanks for the info.

wanger

[EDIT] I also wanted to add that I didn't need any patches for XP. I wonder whether the printer is the same in Australia as it is in other countries? I assume you are not in Australia?

---

### Post by BoredOutOfMyMind on 2005-12-15
[QUOTE=wanger123]Oh I stand corrected then. I assume you mean the brother dcp110c printer sd card reader? 
I guess I was thinking about my dell laptop sd card reader which won't work in linux (Ricoh).

Thanks for the info.

wanger

[EDIT] I also wanted to add that I didn't need any patches for XP. I wonder whether the printer is the same in Australia as it is in other countries? I assume you are not in Australia?[/QUOTE]


I am in Northern California.  [http://www.sunnyfortuna.com](http://www.sunnyfortuna.com) 

The media card is about all that works on this printer. I took heart that you had it running in Ubuntu, but now wonder if I can do the same. I am calling Brother customer disservice tomorrow and see what they can walk me through.....

Thanks for the help.

---

### Post by BoredOutOfMyMind on 2005-12-19
I returned the Brother printer to Staples and bought an HP PSC 1610. I had loaded HP printers in synaptic already and so it was plug and play. Kooka found it first off and XSane did a better job of scanning. 

It took over an hour and two boots to set up on the XP side. 

This is how I expected the Brother to go. What a disappointment. 

8(

---

### Post by bwtranch on 2007-08-13
All the Brother drivers go like this one. See my post.

[http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000](http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000)

---

