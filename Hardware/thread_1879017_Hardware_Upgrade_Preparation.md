---
title: "Hardware Upgrade Preparation ???"
date: 2011-11-10
forum: Hardware
---

### Post by tbzep on 2011-11-10
Will there be any conflicts/issues if I upgrade my system from an Athlon 64 X2 processor to a Phenom II X4 cpu with accompanying new motherboard and memory?  I'm running 10.10 64 bit version. Anything I need to do to prepare for the hardware upgrade?

I've done many upgrades over the years with WinBlows systems by removing drivers before the upgrade...Sometimes seamless, sometimes nightmares, sometimes giving up and doing a fresh install.  This is the first time I've upgraded hardware on this machine, which has been running Ubuntu since 2007.

---

### Post by tbzep on 2011-11-11
Nobody upgrades hardware? :?:

---

### Post by northd_tech on 2011-11-11
I would just give it a try using a LiveCD/DVD (as in DO NOT install) to test with the new motherboard/CPU(s).  From my experience, video/X server, wireless, sound, and possibly ethernet will be your most likely problem areas.

Alternately, I've had good success installing Ubuntu over an existing Ubuntu partition **without formatting**, and it seems to save some of the system installation time.

I would take a backup copy of the **/var/cache/apt/** directory and its contents before you do the hardware/motherboard upgrade though (to either external hard disk, USB stick, or CD/DVD).  Then I like to run a **dpkg -i *.deb** from the directory **/var/cache/apt/archives**  with all those .DEB packages that you just backed up BEFORE running Update Manager on the "new" Ubuntu install, which saves A LOT of download time (and my time selecting .DEB packages to install in Synaptic, etc.)

Have you looked at the motherboard specs and done a search here for that specific hardware to see what module and other troubles that other people have been having?

---

### Post by tbzep on 2011-11-12
> **northd_tech said:**
> 

Have you looked at the motherboard specs and done a search here for that specific hardware to see what module and other troubles that other people have been having?
It's a fairly new board, an Asrock 970 Extreme3. I got no hits when I searched for it here.

---

### Post by northd_tech on 2011-11-13
> **tbzep said:**
> It's a fairly new board, an Asrock 970 Extreme3. 

First- here's the manufacturer specifications website:

[http://www.asrock.com/mb/overview.asp?Model=970%20Extreme3&cat=Specifications](http://www.asrock.com/mb/overview.asp?Model=970%20Extreme3&cat=Specifications)

It looks like the Realtek ALC892 8 channel sound might be a problem (but you can compile your own ALSA support according to the first link):
[http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html](http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html)
[https://bbs.archlinux.org/viewtopic.php?id=128514](https://bbs.archlinux.org/viewtopic.php?id=128514)

I'm not finding much on the Web about the "Xfast USB" and "Xfast LAN" ethernet though- and this probably isn't a very good sign (probably it's too new).  I also didn't find anything for "Xfast" here at ubuntuforums...

It looks like ALL the manufacturer support downloads are for Windows XP, Vista, or 7:
[http://www.asrock.com/mb/download.asp?Model=970%20Extreme3](http://www.asrock.com/mb/download.asp?Model=970%20Extreme3)

You might need to wait a while (and do a lot of your own hacking/tweaking) to play with that motherboard under Linux very soon...

---

### Post by wmdvanzyl on 2011-11-13
I recently did a similar upgrade. Not the same hardware, but i also moved from that CPU to your new CPU. I just swapped out the hdd and it worked seamlessly - well it booted without problem. Have one or two little things to sort out though. 

So i can't say for sure that your upgrade will work, but i can confirm that a very similar upgrade worked for me. :D Now i just need to update the drivers a bit. How does one do that under Ubuntu? I come from a Gentoo background.

---

### Post by kimda on 2011-11-13
My dad has the Asrock 770 extreme 3. Which has similar specs like the board you want to buy. Everything worked with this board so I do not expect mayor problems migrating to this board.

---

### Post by northd_tech on 2011-11-13
> **wmdvanzyl said:**
> I recently did a similar upgrade. Not the same hardware, but i also moved from that CPU to your new CPU. I just swapped out the hdd and it worked seamlessly - well it booted without problem. Have one or two little things to sort out though. 

So i can't say for sure that your upgrade will work, but i can confirm that a very similar upgrade worked for me. :D Now i just need to update the drivers a bit. How does one do that under Ubuntu? I come from a Gentoo background.

Which drivers in particular (or which are the highest 1 or 2 driver priorities for you)?  Sometimes, the 'low priority' drivers never do seem to get fixed under Linux- I've got some hardware that falls under that category, but running WinXP under a VMware or VirtualBox virtual machine with WinXP drivers "worked around" that for me well enough to get most of my archived data recovered and converted to better media and formats.

Can you start a new thread that is more specific to your hardware (thread titles get lost quickly here at UFo, and the vague ones often get ignored)?  

Copy/paste the results of these terminal commands in that new thread if you will:

```
lspci
lsusb
lsmod
cat /etc/lsb-release
uname -a
```I'm not sure how it's done in Gentoo or Ubuntu Unity, but Ctrl-Alt-T will get you a quick-n-dirty terminal window under Gnome Ubuntu versions.  Many distros like the F2 key for terminal windows.

Have you tried System > Administration > Hardware Drivers yet?  Or System > Administration > Synaptic Package Manager and searching for that hardware manufacturer or device name or number under Synaptic?  [I REALLY don't like Unity, so I'm not sure what is involved in Ubuntu 11.xx for package management and hardware drivers there]

---

### Post by MoreOrLess on 2011-11-13
The kernel in Maverick predates the newest AMD chipsets (though the 9xx chips are basically rebadged 8xx chips). I think you'll be able to get it running in Maverick, but ideally, you'll want something newer. I'd recommend doing a fresh install of 12.04 when it comes out, since it seems you don't like to upgrade, and 12.04 is supported for five years.

- The Realtek 8111E LAN chip could be an issue: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393)

- The ALC892 audio shouldn't be problematic. Support for it was added in ALSA 1.022 and IIRC, Mav uses 1.0.23. 

- One thing that probably won't work in Mav is support for the sensor chip (though the CPU sensor should be supported).

---

### Post by wmdvanzyl on 2011-11-14
> **northd_tech said:**
> Which drivers in particular (or which are the highest 1 or 2 driver priorities for you)?  Sometimes, the 'low priority' drivers never do seem to get fixed under Linux- I've got some hardware that falls under that category, but running WinXP under a VMware or VirtualBox virtual machine with WinXP drivers "worked around" that for me well enough to get most of my archived data recovered and converted to better media and formats.

Can you start a new thread that is more specific to your hardware (thread titles get lost quickly here at UFo, and the vague ones often get ignored)?  

Copy/paste the results of these terminal commands in that new thread if you will:

```
lspci
lsusb
lsmod
cat /etc/lsb-release
uname -a
```I'm not sure how it's done in Gentoo or Ubuntu Unity, but Ctrl-Alt-T will get you a quick-n-dirty terminal window under Gnome Ubuntu versions.  Many distros like the F2 key for terminal windows.

Have you tried System > Administration > Hardware Drivers yet?  Or System > Administration > Synaptic Package Manager and searching for that hardware manufacturer or device name or number under Synaptic?  [I REALLY don't like Unity, so I'm not sure what is involved in Ubuntu 11.xx for package management and hardware drivers there]

Yes, that was very vague, but not without reason. I didn't want to hijack this thread and still i feel that these questions has great relevance for the original poster. He is about to go into a an upgrade that i just finished. 

Almost everything worked after the swap-out (after a bit more work), but the major concern now is my system no longer detecting one of my hard drives. I think i will start a new thread to continue this discussion though. :-) Thanks for the advice.

Here is the new [thread]("http://ubuntuforums.org/showthread.php?p=11455101#post11455101").

---

