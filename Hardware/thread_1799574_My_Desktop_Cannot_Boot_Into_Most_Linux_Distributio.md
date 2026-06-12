---
title: "My Desktop Cannot Boot Into Most Linux Distributions"
date: 2011-07-07
forum: Hardware
---

### Post by Sotanaht on 2011-07-07
I have a custom built desktop, with an AMD Phenom II x6 1055T @2.8GHz, an ATi Radeon HD 4870 with 1GB GDDR5 memory, an ASUS M4A87TD/USB3 motherboard, an ASUS Xonar Essence ST sound card, and 2x2GB G.SKILL Ripjaws 240-pin 1600MHz DDR3 SDRAM.  I have tried booting into many Linux LiveCDs and LiveUSBs, and have simply gotten a blank screen on most of them.  At first I tried installing Ubuntu, Kubuntu, Xubuntu, and Lubuntu 10.10, all with the same problem.  Then I tried several non-'buntu variants, including Slitaz and TinyCore, which actually ran just fine.  I didn't want either of those distros, though, so I continued trying different versions of Ubuntu.  10.04LTS and 11.04 both have the same issue, but 9.10 actually ran, but with all sorts of graphical glitches, including flickering pixels around the mouse cursor, and a bar that starts at the top-left of the screen, and shrinks whenever I make a box on the desktop.  The only thing that I could get to play sound was through my video card's HDMI output, but I found that that issue was fixable by disabling the video card's built-in sound card.  Then one day, the system crashed, and I became unable to boot into it again.  Whenever I booted into it, it checked the disk, and then went into a (root) maintenance shell.  All my files were still there, and I've since moved them and reformatted the partition.  I recently booted into a Debian NetInstall CD, and successfully got it to boot and install, but after restarting, it gets the same blank screen every time.
So as you can see, my desktop has something against Linux, specifically Debian-based distributions.  Nobody I've asked has had any clue as to why, so I hope one of you has dealt with an issue like this before, because I'm sick of my desktop running on Windows.
Thank you

---

### Post by Yellow Pasque on 2011-07-08
It's hard to say without seeing an Xorg.0.log from a failed attempt to start X, but my initial hunch is that your monitor's EDID isn't being detected correctly.

---

### Post by charliewhizbeez on 2011-07-08
Hmmm, sounds a bit like a graphics card problem.

Also, if worst comes to worst there is always Suse, fedora, etc.

---

### Post by Sotanaht on 2011-07-18
I've plugged a different monitor in, and now I was able to boot into Debian, which I had already installed , without a single hiccup.  I wonder if it might have to do with how my usual monitor is connected.  My gpu has 2 DVI-I out ports, so I use a DVI-I to HDMI adapter that came with it.  The monitor that works is connected with just a DVI-I cable.  Whatever it is though, the problem's been narrowed down much more than it's ever been :D

---

### Post by Sotanaht on 2011-07-18
I'm going to try installing Ubuntu 10.04LTS on here, and then editing the x.org config file, since it's obviously not being configured properly.  Come to think of it, one of the distros I successfully booted into before, Slitaz, had the resolution set to something ridiculously high, so that letters were made of about 4 pixels.  It has to be the EDID that's the problem.

---

### Post by Sotanaht on 2011-07-18
ok, I'm lost in trying to configure xorg.conf
my monitor is an LG 26LE5300, the resolution is 1360x768@60Hz.  Could somebody tell me what I have to change in xorg.conf?

I've also tried a dual monitor setup, so I can see if I can get my monitor working without having zero output if I don't, but I'm having no luck with this.  The Monitor Preferences program is showing my LG monitor as a 'Goldstar Company Ltd 52"' monitor, which is completely inaccurate.

---

### Post by Sotanaht on 2011-07-18
From what I've read online, I need to edit this line
ModeLine <name> <clock> <4 horiz. timings> <4 vert. timings>
with my monitor's settings, but I have no idea what to put for the horizontal and vertical timings

---

### Post by Sotanaht on 2011-07-18
The issue has been solved.  My friend told me to install ATi's proprietary drivers.  When I restarted, I got an error with X starting up, but after a minute I got it working.  Thanks for helping me identify that it was an issue with the monitor.  I've spent countless hours trying to get Linux running on this machine, and it finally works :D

---

