---
title: "Battery Died During Upgrade to 9.04"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by dedukes on 2009-07-03
I was upgrading to 9.04 this morning.  It was downloading through upgrade manager.  I left the room (forgetting the laptop was running on battery power).  I returned and the battery had died.

When I rebooted I got the newfangled 9.04 login screen.  But after I log in I get a black beige screen and a cursor.

Help.  I've used Ubuntu for a couple years now and love it.  But I'm also pretty ignorant about troubleshooting.

---

### Post by Sef on 2009-07-03
At the log in screen, is there an options button on the bottom left?  One option is to go into the terminal.

---

### Post by HavocXphere on 2009-07-03
> **dedukes said:**
> IBut after I log in I get a black beige screen and a cursor.
That sounds like a graphics issue. Many have reported that cursor on blank screen thing. afaik it hits most ATI hardware. What type of hardware are you running?

Try safe grpahics options on login...forgot how exactly to do that. I think its in the boot menu:oops:

---

### Post by dedukes on 2009-07-03
There is an option button at the login screen.

the options are:

Select Language
Select Session
Remote Login via SDMCP

Restart
Shut Down
Suspend
Hibernate

"Select Session" takes me to the following menu:

Last Session
Run Xclient script
GNOME
Secure Remote connection
Failsafe GNOME
Failsafe Terminel

Cancel
Change Session

Is "Failsafe Terminal" my only and best way to the Terminal?

---

### Post by dedukes on 2009-07-03
I'm using a Toshiba Satellite A135-S4542 laptop.


Here are the specs:
    * Processor: Intel Core Duo T2250 (1.73 GHz/2MB L2 Cache)
    * OS: Microsoft Windows Vista Home Premium
    * Hard Drive: 120 GB SATA @ 5400RPM
    * Screen: 15.4" WXGA TruBrite Widescreen (1280 x 800)
    * Graphics: Intel Graphics Media Accelerator 950, Up To 224 MB Shared
    * RAM: 2GB DDR2 SDRAM @533 MHz (2x512MB)
    * Optical Drive: DVD SuperMulti Drive (CD/DVD burner)
    * Battery: 6-cell lithium ion
    * Wireless: Intel PRO/Wireless 3945 802.11 a/b/g
    * Weight: 6 lbs.
    * Dimensions: 1.47” (H) x 14.2 “ (W) x 10.5" (D) 
    * Ports/Slots: 1 IEEE 1394 (FireWire); 4 Universal Serial Bus (USB 2.0); VGA monitor out port; S-video out; RJ-45 Ethernet LAN; RJ-11 modem; Type I/II PC Card Slot; headphone/speaker jack; microphone; 5-in-1 bridge media adapter supports Secure Digital, Multi Media Card, Memory Stick, Memory Stick PRO and xD Picture Card; Secure Digital slot supports SDIO

---

### Post by dedukes on 2009-07-03
I'm trying to piece together solutions for other forum posts.

I just figured out how to get to terminal at login screen (Ctrl+Alt+F3).

I ran this command:

grep -i driver /etc/X11/xorg.conf



this is the output:


# Driver "kbd"
# Driver "mouse"
# Driver "synaptics"
# Driver "wacom"
# Driver "wacom"
# Driver "wacom"
Driver "intel"


Um, does any of this help?

---

### Post by dedukes on 2009-07-03
Tons of research, and I'm starting to understand that I did a dumb thing by upgrading, seeing as I have a computer with Intel graphics.

I found this article and wonder if it's a possible solution?

[http://www.linuxpromagazine.com/Online/News/Ubuntu-9.04-New-Intel-Graphics-Drivers](http://www.linuxpromagazine.com/Online/News/Ubuntu-9.04-New-Intel-Graphics-Drivers)

I managed to open my xorg.conf file and find the device section, but i'm uncertain about how to enter the fix this guy suggests.  sigh.

---

### Post by Favux on 2009-07-03
Hi dedukes,

I'm pretty clueless when it comes to video but I remember reading some of this stuff in the Jaunty Dev. and Testing forum so I went to the archive and found this (post #82):  [http://ubuntuforums.org/showthread.php?t=1076014&highlight=intel&page=9](http://ubuntuforums.org/showthread.php?t=1076014&highlight=intel&page=9)
```
Section "Device"
Identifier "Configured Video Device"
Option "AccelMethod" "exa"
Option "EXAOptimizeMigration" "true"
EndSection 
```
It probably should look something like that.  I don't know about the "EXAOptimizeMigration" line though.

Hope this helps.

---

