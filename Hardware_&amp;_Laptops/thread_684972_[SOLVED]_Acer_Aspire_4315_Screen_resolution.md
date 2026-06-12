---
title: "[SOLVED] Acer Aspire 4315 Screen resolution"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by FrancesL on 2008-02-01
Help please! I am SO VERY NEW to Ubuntu, only had this notebook 3 days..was so happy with how all was progressing when suddenly everything locked up while I was on the net. Playing Pogo actually:confused: on restart the screen resolution has set itself to 640x480 which is so enormous I can only read about 25% of screen at a time. I have tried to reset but there is NO OTHER CHOICES? what have i done?????? can anyone help this aging newbie? thanks. 
Aspire 4315-100508Ci
Intel 540 1.86GHz/1M
LCD 14.1
Ram 512 MB DDR2
Hdd 80GB
DVD/CDRW combo 
Linux Ubuntu 7.10

---

### Post by taurus on 2008-02-01
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to the X with <Alt>F7.  Now, restart X again so it will read in the new configs with <Ctrl><Alt>Backspace.

---

### Post by FrancesL on 2008-02-01
:) thank you so very much for you prompt replay! followed the directions and all seems fixed now! you are a star! At 61 this learning curve from Apple Mac at 50 , first computer, to Windows , cost driven really, to this wish list fulfillment of a notebook, learning the terminology etc of Ubuntu is a challenge..and i am loving it.! thanks again for being there and with the right answer! Big grateful hugs!:)
PS: Still have absolutely no idea what I did!

---

### Post by Flymo on 2008-02-19
Me too, many thanks for that.  I had managed to snafu X whilst attempting to enable TV-Out on an Acer Aspire 4315 with installed Ubuntu GG 710.  All good again now! :)

Ben

---

### Post by samborambo on 2008-02-21
Is this the laptop being sold at DSE in New Zealand preinstalled with ubuntu gutsy? The new xorg safe mode feature didn't pick this up since it didn't cause X to fail to start. Somehow the file /etc/X11/xorg.conf has become corrupted and doing the package reconfigure will autodetect your graphics hardware and screen and rebuild xorg.conf. What's interesting is how it managed to become corrupted in the first place.

I see you're new to Linux/Ubuntu. Since the development of open source software usually relies on users giving feedback to developers, it would be really good if you reported a bug on launchpad against xorg. 

If you're curious about whats going on, check the logs. Log files reside in [File System] /var/log/ and are rotated by a service called logrotate every day or on every system boot. If you find an error in the logs somewhere, first port of call would be to paste the error line into google and see if it turns up something relevant. Also try searching these forums and the ubuntu wiki.

The next port of call would be IRC - especially if it is an urgent fix required. Install the package xchat-gnome and start it with Applications -> Internet -> Xchat-Gnome. It should start automatically in the #ubuntu channel (chatroom) on the Freenode IRC network.

If you get nowhere, file a bug report at launchpad. See:

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") 

Once you come up with a fix or find a solution DOCUMENT IT!!! The laptop testing team wiki page documents every laptop and any installation issues and workarounds. Check it out here:

[https://wiki.ubuntu.com/LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam")

There's no page for this laptop so it would be great if you could create one. The first thing to post is the device info by opening a terminal and typing:
```

sudo lspci -nnv
```

This scans the PCI bus for devices such as graphics controller, memory controller, network adaptor, wireless adaptor, etc. Also check the usb bus as its becoming more common for internal devices (like sound cards) to be attached via usb:
```

sudo lsusb -v
```

Paste this info into the laptop wiki page. This info is invaluable to people shopping around for a laptop to run Linux (even though these particular laptops are being sold with Gutsy pre-installed).

---

### Post by Flymo on 2008-03-14
Hi, and thanks for the links - been offline for a bit....

The good news is that  the Acer 4315 TV-Out now works - but only if the TV is connected via the S-video lead when the laptop is booted up.  Very simple indeed, but what a long time it took us to find.  

When we stop moving around the world I'll document what we find as you suggested.

All the best, Ben

---

### Post by jmac05r1 on 2008-04-29
> **taurus said:**
> Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to the X with <Alt>F7.  Now, restart X again so it will read in the new configs with <Ctrl><Alt>Backspace.

Thank you so much "taurus" helped me out greatly!!

---

