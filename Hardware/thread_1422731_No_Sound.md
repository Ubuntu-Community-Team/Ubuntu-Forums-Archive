---
title: "No Sound"
date: 2010-03-05
forum: Hardware
---

### Post by andrew_a72 on 2010-03-05
Ive been using 9.10 for about a month, the sound has always worked until today. Ive spent the past hour or so trying to figure this out (Im not to tech savvy), heres what I have tried so far:

--- The Possible Cause
As soon as I started my computer this morning, update manager came up, I performed all the listed updates, restarted the computer, and then (I have dual boot set up with windows) a new option came up being 2.6.31-20, so I chose it and turned on the computer. As this was the first thing I did this morning, Im not entirely sure if this is the cause of the no sound issue, but it seems somewhat likely as the sound worked fine up till today.

--- What Ive tried so far
Heres a list of what various troubleshooting guides told me to do in terminal, and the results.

I forget what the command was for this one, but it gave me this link. ([http://www.alsa-project.org/db/?f=295d1af6ed99df7984b0c378f8269368f8acdea8](http://www.alsa-project.org/db/?f=295d1af6ed99df7984b0c378f8269368f8acdea8))

> lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 8a100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.31-20-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.31-20-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.31-20-generic 
  linux-sound-base 
The following packages will be REMOVED:
  airstrike-common{pu} avant-window-navigator-data{pu} awn-manager{pu} 
  libawn-extras0{pu} libawn0{pu} python-alsaaudio{pu} python-awn{pu} 
  python-awn-extras{pu} python-awnlib{pu} python-gnomedesktop{pu} 
  sqlite3{pu} 
0 packages upgraded, 0 newly installed, 5 reinstalled, 11 to remove and 0 not upgraded.
Need to get 1,381kB/30.6MB of archives. After unpacking 6,197kB will be freed.


Any help would be very much appreciated, as this is very annoying. Once again, I am a noob, so whatever ideas anyone has please explain in simple terms.

Once again, I'm a noob.

---

### Post by Robster2 on 2010-03-05
I hate to put a response like this but you would be surprised how often it is the case.

Check the volume settings sometimes they get set to zero after an update.  Speaker settings on your panel.

---

### Post by Ghost|BTFH on 2010-03-05
^^^^^

What Robster said.  Run in terminal:
[I]
alsamixer[/I]

and check to make sure your volume is not at zero and make sure you don't have a grayed out box that says **MM** inside of any of your playback volume controllers.  Make sure you see the pretty green **OO** for it to work properly.

Hope that helps.

Cheers,
Ghost|BTFH

---

### Post by andrew_a72 on 2010-03-05
no dice.

volume controls where the first thing I checked by I checked again anyway.

tried alsamixer and everything is turned up, master was up about halfway so i turned it up all the way and still nothing. However when i open alsamixer and first change the volume on master I hear a short (fraction of a second) blip and then nothing.

also I should mention I have tried sound in firefox, using vlc media, amarok, everything so its not just the sound from one application.

Other Ideas?

---

### Post by Ghost|BTFH on 2010-03-06
Silly question, I know, but since we've already gone past the volume part (Although did you make sure PCM, etc was at 100% too?) might as well go for it...

Can you see your sound card?

*lspci*

and then 
[I]
asoundconf list[/I]


Cheers,
Ghost|BTFH

---

### Post by andrew_a72 on 2010-03-07
PCI volume is indeed turned up all the way, also, this may or may not be normal, but when I go into sound preferences and click on the hardware tab, there is nothing listed under "Choose a device to configure".

Heres what I got from putting the previous post recommendations in terminal:

I dont know if im typing it wrong, but I copy and pasted what was written above and got this
$ asoundconf list
asoundconf: command not found

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller



Bottom line, sound still does not work, 

btw even though sound still isnt working, thanks to everyone for your ideas thus far.

Anything else I should try?

---

### Post by andrew_a72 on 2010-03-07
another failed test, I tried plugging in earphones (after I checked to make sure they work) into the laptop to see if the speakers were just broken, once again, no dice. Got no sound through the earphones either.

---

### Post by Ghost|BTFH on 2010-03-07
Well, here's another silly question - just what exactly are you using for sound?

When I saw alsa-utilities on the list, I assumed you were using *alsa*.

But now it sounds like you might be using *PulseAudio*...

If you're trying to use *alsa* only, then part of the issue is that *PulseAudio* is obviously still in the system, as is the server and it's taking over the sound.

If you're trying to use *PulseAudio*, it sounds like you might have an issue with the packages.  The *lspci* shows your audio card, so Linux is recognizing it - the next step is to have whichever version of sound you prefer to see it.

So, first things first - what flavor of audio are you wanting?  *alsa* or *PulseAudio*, or you don't give a damn, as long as it works?  :)

Cheers,
Ghost|BTFH

---

### Post by andrew_a72 on 2010-03-07
Doesn't really make a difference, I just want it to work. I don't even know what the differences are between the two.

I figured out that it was something to do with the update that messed up the sound, not sure what, but something. I figured this out by formatting the drive and reinstalling ubuntu completely, when I did this the sound worked fine. That is, untill I preformed all of the updates again at which point it was back to the start with no sound. So I am now once again reinstalling ubuntu and just wont do any updates untill I can figure out whatever caused the issue. So though the sound works for now, I want to get all the updates once I know how to fix the issue.

---

### Post by Ghost|BTFH on 2010-03-08
I would suggest trying to run pure alsa then.

I have a "simple" guide [Here.]("http://ubuntuforums.org/showthread.php?t=1306679")

If you need more detailed instructions, or if the process doesn't work, please let me know and I'll try to help.

Just realize, after doing this, you won't have a simple gui volume controller - your volume controls will be accessed from opening a terminal and typing *alsamixer* but it works great for me.

Cheers,
Ghost|BTFH

---

### Post by gradinaruvasile on 2010-03-08
You might have a muted device somewhere. Check alsamixer for muted devices (that have "MM" under them. Unmute everything except microphone and CD (these 2 are obviously not your problem).

---

### Post by andrew_a72 on 2010-03-09
Ghost man, your awesome. I followed the guide, restarted my computer, and it works. Thanks!

So one question then, now in order to turn sound up and down I have to run alsamixer in terminal, is there any other way for me to edit sound preferences or is it just that. Also, what is the "off-hook" part of alsamixer?

Thanks Ghost man, as well as everyone else for your input!

---

