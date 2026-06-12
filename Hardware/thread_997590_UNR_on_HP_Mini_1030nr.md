---
title: "UNR on HP Mini 1030nr"
date: 2008-11-30
forum: Hardware
---

### Post by eric.rost on 2008-11-30
Just wanted the post I was searching for out there that the Ubuntu Netbook Remix (UNR) works flawlessly out of the box on the HP Mini 1030nr netbook.

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

I used the USB installer directions and was online with the Broadcom wireless and taking pics of myself with the webcam in 15 minutes.

Only 2 caveats. The internal mic seems non-functional (if it exists) and you want to select the PCM in the Preferences -> Sound panel for the volume control to adjust as the Master doesn't control anything.

Hope this helps someone since I couldn't find a post before I blew Windows away off of my mother's brand new netbook with no path to recover. (I'm brave and checked out the wifi chipset finding out that Broadcom finally put out a binary linux driver!)

---

### Post by Jeff Johnston on 2008-11-30
Thanks for the post! I am torn on which Netbook I want to get. Finding out that this one works with Ubuntu flawless will help me make a decision easier.

Are you pretty happy with the HP Netbook?

---

### Post by eric.rost on 2008-12-03
Well, for the day or so that I got to play with it, I was in geek heaven. Then my mother headed home and took her new toy with her. I'm pretty sure I'm going to buy one since it hits the "nebook sweet spot" that no one else seems to have been able to find:

Good size keyboard (all the 9" netbooks fail at this)
SSD instead of HDD
Ubuntu runs flawlessly with the Hardy UNR installer!

Let me know if you have more questions. She just threw it online on her home wireless, and is using it for schoolwork for her Master's Degree. No complaints so far, and I imagine I will be getting a call soon to convert her home pc over Christmas from XP to Ubuntu as they CONSTANTLY manage to have virus issues and are tired of paying the extorion.. err I mean protection.. er I mean subscription fees to Norton.

---

### Post by MN_Moose on 2008-12-18
The 8.04 UNR ISO installed over the incumbent OS without a hitch, in a blazing 10 minutes (compared to 90 for the XP restore disks)...

I have had three occasions where the MBR seems to be getting clobbered (at boot, blank screen with blinking cursor). This is after a full shutdown. After this occurs, attempting to reinstall with the installer ISO hangs in the PNP initialization sequence and will not continue. I have had to reload XP before the UNR ISO would successfully boot and install the OS.

The HP site has generic instructions for black screen/blinking cursor that allude to removed storage as a potential culprit. I don't believe removing the external USB DVD drive used in the installation would cause the initial "no boot" problem, and am puzzled as to what in the hardware could be so stateful that a subsequent reinstall attempt would fail until a full XP install cleared the problem. Just reformatting the SSD isn't enough.

There are so few choices in the system BIOS that I can't see a BIOS setting as being the culprit (I did disable the S4 sleep to no avail). I saw (and can't relocate) a reference to a couple of kernel options someone used on an Inspiron 9 hat involving ACPI settings at boot. Any ideas?

From a hardware aesthetics perspective this is a lovely, solidly constructed machine. I particularly like the keyboard compared to the MSI Wind and the ASUS EeePC. And UNR is a good fit for the Netbook paradigm.

---

### Post by KhristosEuangelion on 2008-12-25
> **MN_Moose said:**
> After this occurs, attempting to reinstall with the installer ISO hangs in the PNP initialization sequence and will not continue. I have had to reload XP before the UNR ISO would successfully boot and install the OS.

So your not the only person having this problem!
try booting with pnpacpi=off it worked for me (a couple of times) I'm currently trying to trace this problem down in openSUSE, Redhat 9. I'm installing UNR to see if it has the same problem. 

--Zack

---

### Post by ArdentMoth on 2009-01-27
Anyone have a work around for the volume control problem?

if there is a way to configure alsa to allow PCM to be controlled by THE KEYBOARD (via fn + f10/f11), this would be a flawless Ubuntu netbook. controlling the volume via mouse is one thing, but part of the beauty of being able to control the volume is doing it without the mouse. It's why man invented the clicker, and later the remote control. 

So any work-around involving controlling PCM from the keyboard is welcome and needed; for some reason, i just can't wrap my head around it.

The HP Mini netbook really is a brilliantly put together little thing. I love it.

*gets ready to sand off the window$ logo on the keyboard, and replace it with a tiny Ubuntu sticker*

---

### Post by eric.rost on 2009-02-06
Hey guys, try this:
[http://en.kioskea.net/forum/affich-24155-laptop-screen-is-blank-when-it-is-switched-on](http://en.kioskea.net/forum/affich-24155-laptop-screen-is-blank-when-it-is-switched-on)

Worked for me.

Unplug laptop, remove battery, hold power button down for 30-60 seconds reassemble and boot. Its a hardware issue.

---

### Post by eric.rost on 2009-02-06
Re: the volume issue, the fix I mentioned in my original post fixes that.

Go to System -> Preferences -> Sound and in the bottom pane select PCM (not in front of my Ubuntu machine so can't remember what the bottom pane is called). That selects what control the "Volume" slider and thus keyboard control runs.

---

### Post by ArdentMoth on 2009-02-13
> **eric.rost said:**
> Re: the volume issue, the fix I mentioned in my original post fixes that.

Go to System -> Preferences -> Sound and in the bottom pane select PCM (not in front of my Ubuntu machine so can't remember what the bottom pane is called). That selects what control the "Volume" slider and thus keyboard control runs.

you assume too much; i'm not a dolt.

I already did that; the slider works, the keyboard -does not-.

I asked for a work around for the keyboard, -not- for the slider.

And whatever; it's liveable... I can deal with it, I just can't think of why there would be a difference between what the slider is set at, and what the keys control.

---

### Post by tntc on 2009-03-02
I'm running 8.04, and I did the following to get my sound working (including the mic): 

1) Edit /etc/modprobe.d/alsa-base and add the following line:
options snd-hda-intel model=ref

2) Right click the Volume Control on the panel and click preferences.  Click on PCM to highlight it.  

3) Double click on the Volume Control on the panel, click Edit, and then click preferences.  Check off "Digital Input Source", and both "Input Source" check boxes.

4) Click on the options tab, and set "Digital Input Source" to "Analog Inputs", the first "Input Source" to "Line", and the second "Input Source" to "Mic".  Everything should now be working.

I did not need to change anything for the hot keys to work.

---

### Post by kennethmsmith on 2009-07-22
i have hp mini 110-1030nr and running ubuntu 9.04.  headphones work, but speakers don't work.  Any help?

---

### Post by rmp5s on 2009-08-14
I too have a Mini 1030NR, which I LOVE, and I've been considering switching from XP to dual booting Windows 7 and Linux.  I stumbled apon this thread while searching for what kind of Broadcom WIC is in this thing (a Broadcom 4xxx-something or something...???) and I'm intrigued by a "Netbook specific" Linux distro.  I have a few questions though:

How can I DO the actual installs with no optical drive?  USB drive?  Maybe even use my USB external HDD?

How would this setup work?  I'd like to use the Linux side for web surfing (no/not many viruses and/or adware), to learn Linux and as a network administration tool (I'm an IT guy).  I'd like the Windows side mostly just to have Windows as an option and to see how Win7 is.  I've heard it's much better than Vista and it's supposed to work pretty well on the Mini.

And, since I'm here, I'll see if anyone knows the answer to the original question that brought me here...can the Broadcom WIC in this thing go into monitor mode?...rfmon?...whatever you wanna call it?

Any and all help on either topics is GREATLY appreciated!  Thanks!

PFC Bialik
USMC

---

### Post by tooCanad on 2009-08-19
> **eric.rost said:**
> Re: the volume issue, the fix I mentioned in my original post fixes that.

Go to System -> Preferences -> Sound and in the bottom pane select PCM (not in front of my Ubuntu machine so can't remember what the bottom pane is called). That selects what control the "Volume" slider and thus keyboard control runs.

I don't have an option to select PCM. All I have is Monitor of Null Output (Pulse Audio Mixer).

Insights are appreciated. Never mind I got it.

---

### Post by timbck2 on 2009-09-14
I had just the opposite experience; I installed Ubuntu UNR on my newly-purchased HP Mini 1030nr, and for the life of me I can't get the Wifi to work! I have an Apple Airport Extreme Base Station with WPA/WPA2 Personal enabled on a closed network. I enter the network SSID and WPA2 password, it spins for a while, then gives up.

Any ideas?

---

### Post by Craig Shackleton on 2009-09-20
> **tntc said:**
> I'm running 8.04, and I did the following to get my sound working (including the mic): 

1) Edit /etc/modprobe.d/alsa-base and add the following line:
options snd-hda-intel model=ref

2) Right click the Volume Control on the panel and click preferences.  Click on PCM to highlight it.  

3) Double click on the Volume Control on the panel, click Edit, and then click preferences.  Check off "Digital Input Source", and both "Input Source" check boxes.

4) Click on the options tab, and set "Digital Input Source" to "Analog Inputs", the first "Input Source" to "Line", and the second "Input Source" to "Mic".  Everything should now be working.

I did not need to change anything for the hot keys to work.I tried to follow these instructions, however, I apparently don't have permission to modify the alsa-base file. Any help on that?

---

### Post by ownasaur on 2010-01-05
> **timbck2 said:**
> I had just the opposite experience; I installed Ubuntu UNR on my newly-purchased HP Mini 1030nr, and for the life of me I can't get the Wifi to work! I have an Apple Airport Extreme Base Station with WPA/WPA2 Personal enabled on a closed network. I enter the network SSID and WPA2 password, it spins for a while, then gives up.

Any ideas?

I have a 1030nr which came with windows xp and all other hp junkware. The official setup didn't last as the computer got a terrible infection and then had to reinstall xp. After installing xp the system wouldn't shut down.. something about a registry error, blah blah blah. I got tired of having to deal with such a slow and glitchy system that I decided to try an alternative.

I ran the live version (usb) of netbook remix (9.10?) and the wi-fi was working then. Once I installed UNR, the wi-fi decided not to work anymore. It was fixed after I plugged into an ethernet connection, downloaded updates/drives, etc and re-enabled the broadcom driver then it was back on business.

Like others report here, the mic does not appear to be working as of yet, but I hope that could be fixed in future releases. I have not tried using the card reader since I've never used it. Everything else is fine (wi-fi/video/sound/ethernet)

My netbook is superfast now with UNR! It takes about 30-35 seconds (including the time it takes me to login) to boot up the system, instead of the 5 mins it took under win xp.:lolflag:

---

### Post by ownasaur on 2010-01-28
> **ownasaur said:**
> 
Like others report here, the mic does not appear to be working as of yet

The integrated mic works :D.. all we need now is bluetooth!

---

