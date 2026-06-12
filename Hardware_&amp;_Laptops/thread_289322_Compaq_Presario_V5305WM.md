---
title: "Compaq Presario V5305WM"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Cartwheels4amile on 2006-10-30
[http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=py&dlc=es&product=3231960](http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=py&dlc=es&product=3231960)

I'm looking to buy a Compaq Presario V5305WM, and I was wondering if all the hardware will work right with Edgy, specifically the graphics card and the internal wireless.

---

### Post by madelephant on 2006-11-03
Also wondering if anyone has any experience with Ubuntu and this laptop or any of the same hardware, here's a list-
[I]
2.00 GHz Mobile AMD Sempron™ Processor 3300+

ATI RADEON XPRESS 200M IGP

Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)

54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support- **Broadcom (according to driver download)**

Altec Lansing Sound[/I]


Most likely no one has used this laptop yet so if anyone has any experience with the Presario V5000 series I'd like to hear.

Link to Compaq site- [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960&dlc=es](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960&dlc=es)
Thanks

---

### Post by articnomad on 2006-11-03
Everything should work except for the wireless card, and the card reader. Compaq/HP computers usually work great with Linux.

---

### Post by tlp on 2006-11-07
I have this machine and am running Ubuntu 6.10 Edgy on it as we speak. The wired ethernet port works, the volume control buttons work, hibernation works, etc. Wireless also works with the help of ndiswrapper (see URL at the bottom).

However, I wasn't able to resume it after going into suspend mode, nor have I tested the PC Card slot. 

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by nate66s on 2006-11-08
I also bought this machine and I just tried to install 6.10 on it.  The spec sheet for this laptop claims that the Sempron chip is 64-bit.  However, when I try to install the AMD64 version, I get the message that says, "This is not an AMD64 machine.  Please install the i386 distribution of Ubuntu."  I'm not against installing the i386 version (and I probably will), but is there any reason why I shouldn't be able to install the AMD64 version on this 64-bit chip?

---

### Post by mrc on 2006-11-10
I'm actually typing this in Kubuntu Edgy on the Compaq V5305WM right now.  I have both the full graphics driver (ATI 200M) and wireless card (Broadcom "Airforce One") working:-D , but this was pretty difficult information to find, so I'll fill you in.

Broadcom wireless card:
1.) Get **bcmwl5.inf** and **BCMWL5.SYS** from the Windows installation that you have and place them in your home folder.
2.) Follow the directions on this link: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

ATI Graphics Driver for 200M
1.) Go to the terminal (Konsole in KDE).
2.) Type: **sudo apt-get install xorg-driver-fglrx**
2.5) IMPORTANT: Type: **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old**.  If anything goes wrong with this, that will help you to get back to your original graphics configuration.
3.) Type: **sudo kwrite /etc/X11/xorg.conf** (**sudo gedit /etc/X11/xorg.conf** in Ubuntu)
4.) Replace **Driver "ati"** with **Driver "fglrx"**
5.) Go to the end of the file and type the following on new lines:
[B]Section "Extensions"
Option "Composite" "false"
EndSection[/B]
6.) save the file and exit
7.) Reboot
8.) Test what you've done by typing **fglrxinfo** in konsole.  You should get the following:
  display: :0.0  screen: 0
  OpenGL vendor string: ATI Technologies Inc.
  OpenGL renderer string: RADEON XPRESS Series Generic
  OpenGL version string: 2.0.6011 (8.28.8)
9.) To really test your stuff, try running **fgl_glxgears**, or install something like planetpenguin racer (the game runs beautifully on mine in 1280x800 resolution).
(NOTE THAT THESE STEPS WERE TAKEN FROM: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html"))
SHOULD SOMETHING GO WRONG WITH THE STEPS ABOVE (Graphics stuff)
Upon rebooting to a non-working XWindow session do the following.
1.) Press Ctrl-Alt-F2
2.) log in
3.) Type: sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
4.) Reboot.  This should bring you back to your old (non-accelerated) XWindows session.
5.) Try the steps again, but be very careful about spelling, etc.

I hope this helps everyone trying to do this.  Once I followed these steps, everything seemed to work really well!  Let me know if there are any problems with this. By the way, has anyone tested the card reader yet?

---

### Post by mrc on 2006-11-10
I wanted to add two other things that I've noticed.  One I've solved, the other I haven't.

DISABLING TOUCHPAD TAPPING:
This was something that was really annoying (I would be single clicking while typing).  To disable this, type **sudo kwrite /etc/X11/xorg.conf** and find the section that has **Identifier "Synaptics Touchpad"**. In this section, add the line **Option "MaxTapTime" "0"**.  Save and reboot (or restart X).

SUSPEND NOT WORKING
As someone else mentioned, suspend doesn't work.  Has anyone found out how to get it to work?  Thanks in advance for the help.

---

### Post by nate66s on 2006-11-11
For the wireless, I had luck using the firmware method detailed here:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I couldn't use the driver that came with Windows (it's too new, apparently), but I downloaded the one provided by the link and it worked great.

EDIT: Okay, so this has some goofy side effects.  I pressed the wireless button on the laptop and it put the hardware into a strange state.  I rebooted multiple times and the wireless nic wouldn't fix itself.  I finally booted into Windows (twice) and it seems to have fixed the state of nic.  I booted back in to Linux and it's working fine again.  So, don't press the wireless button. :)

---

### Post by tlp on 2006-11-11
> **nate66s said:**
> I also bought this machine and I just tried to install 6.10 on it.  The spec sheet for this laptop claims that the Sempron chip is 64-bit.  However, when I try to install the AMD64 version, I get the message that says, "This is not an AMD64 machine.  Please install the i386 distribution of Ubuntu."  I'm not against installing the i386 version (and I probably will), but is there any reason why I shouldn't be able to install the AMD64 version on this 64-bit chip?

What spec sheet is this? I was never under the impression that this was a 64-bit machine. I cannot find any mention of it on the official HP specifications located here:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960&dlc=es](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960&dlc=es)

---

### Post by madelephant on 2006-11-11
So I went ahead and got the Presario and I'm thrilled with the result.  Edgy runs great and Beryl is beautiful.  Suspend doesn't work for me either but I haven't investigated any solutions for it yet.

I'm apprehensive about installing the ATI drivers for the 200M as it might break Beryl.  Has anyone tried both, @mrc maybe?

As for the wireless card ndiswrapper sucks (no passive mode, I wanna watch packets!) but it's nice to have wifi despite the fact.  Also a warning:  *don't even bother purchasing a replacement mini-pci wifi card for this laptop* as **Compaq has that hardware restricted in the BIOS**.  If you change the card you will get an error about an "unsupported ethernet adapter" at boot and can't get any farther.  There's a couple sites out there where some guys hacked the BIOS to get other cards to work but it's not well documented.

---

### Post by tlp on 2006-11-11
> **madelephant said:**
> So I went ahead and got the Presario and I'm thrilled with the result.  Edgy runs great and Beryl is beautiful.  Hibernate doesn't work for me either but I haven't investigated any solutions for it yet.


Hibernate _does_ work for me, but suspend doesn't.

---

### Post by ddgbosi on 2006-11-11
Wow! Kinda new on here, cos I'm new to Ubuntu. Like when I was slave to W1ndows, I was slave too to $use, till I found the light. I'm now a believer.

And on my Presario v5000, EVERYTHING works, exept the suspend, and hey, I don't plan on using suspend anyways.

Howdy ya'll.

---

### Post by madelephant on 2006-11-12
Correction- Hibernate works, suspend doesn't.

---

### Post by denverb8 on 2006-11-21
I've the new v5305wm. Go walmart.
Ubuntu dapper drake works great, graphic card, everything, wired card,. Only things that don't work are the wireless, and I haven't tried suspend yet. 

the touchpad is extra touchy in ubuntu.

---

### Post by D10 on 2006-12-12
I have this laptop as well. I am running Xubuntu 6.10 and everything works great, except for the modem. The wireless card needs ndiswrapper, but was working within 5 mins of install.

Like I said the modem is not working as of yet. I have added the sl-modem-daemon pkg, but still get no dial tone when I try to dial out. I would like to get it working as broadband isn't available in my area, but I can still access through my proxy server.

All in all very happy with Xubuntu on this laptop.

---

### Post by lyceum on 2006-12-12
I have Ubuntu on my Compacq laptop and it works great, except for the Broadcom. I tried all of "How To's" and even the one time when it did work, it was buggy and only worked when it wanted to. It is a nice machine, but you would need a new wireless. Sorry. If you can find something else with supported WiFi I would say to get that.

---

### Post by bubazoo on 2007-04-22
Has anyone tried this Laptop with ubuntu 7.04 series yet?

was thinking about trying xubuntu, but I was concerned about wireless not working,  since I don't have a wired eithernet connection at home to use.

is ndiswrapper still the only way to do it?

I too got this Laptop from walmart, couldn't pass it up :P
I also ordered the WIndows Vista DVD's when they were released, talk about a majpr pain to get I tell yah. They kept trying to tell me the Laptop didn't qualify for the upgrade, was a good thing I made a copy of the receipt, because HP wasn't going to let me get it at first.

but anyway, I too prefer linux, but I haven't found a distribution that will support the wireless card yet.

thanks

---

### Post by biscrage on 2007-04-22
I am posting this from 7.04 (feisty) using the wireless on the compaq v5305wm right now:)
I read a couple of tutorials but couldnt get the wireless to work until i found a post somewhere saying to install the fwcutter package, then it works flawlessly (2 days so far)
search for bcm43xx in synaptic.  I also have the bcm43xx-firmware package installed, not sure if it is also nesesarry, but i know the bcm43xx-fwcutter is.  if you need more help look for broadcom 4318 (thats the wireless card from this laptop) on the forums, that is how i found it.  This works WITHOUT ndiswrapper!  Good luck.  
Now if I can just get suspend working (the computer will not boot back up after its been asleep)  Everything will be in working order :)

---

