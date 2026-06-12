---
title: "ATI x1950 driver problem?"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by Crosscheck on 2008-12-09
Dear Ubuntu lords,

I think I'm missing a step when trying to install (or load upon boot?) the driver for my ATI X1950 card.

I tried Installing Ubuntu from the latest 8.10 Boot CD. After the orange status bar slid back and forth for a minute, it then filled up and went black.

After that, every now and then there would be a quick flash - nothing perceptable - and the black would continue. As it was an "active" black, it seemed to me that the card just wasn't talking to the monitor correctly, but was trying.

I then installed from the Alternate CD (no custom options, just default, save for the required entries...username, time and so on). I saw this through to completion. However it continues to boot into the same darkness.

I searched as much as I could before posting, so as not to waste anyone's time. I found out how to boot into the console. I tried a few suggestions; loading the VGA driver, editing the boot menu and so on. I was unable to make any progress.

I did verify that the video card was supported via the appropriate command (sorry...I don't recall it at the moment).

If it helps your reply, I am a fairly advanced Windows user, but with Linux I am a completely green, wet-behind-the-ears noob.

Should I attempt to make a slipstream disc with my specific drivers included?

I am installing on:

CPU: Intel Q9450 2.66 Quad Core
Mobo: ASUS P5WDG2 WS Pro
RAM: 4x1 GB OCZ DDR2 800
Video Card: ATI Radeon X1950
HDD: Seagate 750GB 32MB Cache

Can't thank you enough for your time and thoughts. :p

---

### Post by Dynaflow on 2008-12-09
I'm having a similar problem with that very same ATI card right at this very moment.  For some reason, the driver isn't activating itself properly.  I'll post back if I figure anything out.

---

### Post by Dynaflow on 2008-12-09
Try this:  When you see the message that GRUB is starting as your computer begins to boot, press ESC to go into the GRUB menu.  Select the choose-a-kernel option that says "recovery mode."  After a goodly amount of computerese flowing by on the screen, you'll find yourself at a menu.  Choose "xfix," and let that program have a crack at what ails you.  It works wonders, and in fact it fixed my problem pretty effortlessly.

---

### Post by Crosscheck on 2008-12-09
Thanks for that suggestion.

I went into the recovery console and gave xfix a shot. It ran as you described, but unfortunately with results unchanged.

I then tried fsck, followed by dpkg. Based on the text flying up the screen on dpkg, I thought my problems were over, as it reported I needed about 250MB of updates.

But alas, I then noticed the abundance of "Could not resolve..." for various addresses. At the end of that, it said that files were updated, so I don't know if that is a static message displayed whether the files actually downloaded and installed or not, OR if the command tries many addresses until it succeeds.

I tried both NICs on this motherboard and I know our DHCP server is working smoothly, so I don't know if I now need to solve a NIC driver problem as well.

After all this, I still boot into darkness, but at least I got to try something new.

I'm not trying to mount a dual boot system or run a live CD here, I'm just trying to run a fresh install of Ubuntu with nothing else. I'll deal with the cream and sugar later...

---

### Post by Crosscheck on 2008-12-09
I don't know if this helps, but I also tried installing CentOS 5.2, as it came with a Linux magazine I picked up. Same end result.

---

### Post by Dynaflow on 2008-12-09
Do you have another graphics card sitting around, or is there some sort of motherboard-integrated-graphics output on your computer?  I would pull the ATI card completely out of the loop, run xfix, and see if you can boot into a graphical environment.  It would be good to make sure it is Ubuntu's handling of the graphics card (or the card itself) that is the problem, rather than something else.  

As for the update thing, it goes through a lot of alternative addresses, so seeing some failed hits when watching its detailed output in the terminal is normal.

---

### Post by Crosscheck on 2008-12-09
Thanks, Dynaflow.

The only other video card I have available is an EVGA 8800GTX, which I'm guessing will be a bigger problem than the ATI. This mobo doesn't have onboard video, so that's out.

There was a two-year-old book on Ubuntu laying around (referencing Ubuntu 6.10), so I grabbed it. I flipped to the "post-installation problems" section and started skimming.

They suggested running **dpkg-reconfigure xserver-xorg** which I did. The first thing it asked was if I wanted to use **kernel framebuffer device interface**. I tried this twice. First I chose 'Yes' and the second time I tried 'No'. Both times it produced the same result, detailed below:

The book described this process as starting with configuring the video card, then the keyboard, then the mouse, and finally the monitor.

What actually happened was that it went straight to the keyboard config, ending up at a command prompt. So it skipped the video card entirely and never even moved on to the mouse or monitor.

For grins, I tried logging in blindly, assuming that perhaps it's sitting there at the login screen with the graphics card under protest. So after entering my user name and password, the HDD activity light went nuts.

So I'm absolutely convinced that it's a graphics driver issue, but I don't have another card to test with (hell, except for the nvidia beast, so I'll try that). There has to be a way of tweaking some config file, I just haven't found the instructions to do so.

---

### Post by Crosscheck on 2008-12-09
This power supply can't handle the 8800GTX, either in wattage or connectors. :(

---

### Post by MosesX8 on 2009-02-25
has anybody successfully installed drivers for this card? is it just not possible?

---

