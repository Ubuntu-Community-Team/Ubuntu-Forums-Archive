---
title: "Toshiba L10 laptop: general impressions. How to set up hotkeys?"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by patrickfromspain on 2006-02-22
Hi there!

I've been setting up ubuntu to look and feel the way I like. My notebook is a Toshiba L10, with a celeron M 370 (1,5Ghz), 512mb RAM, DVD-+RW/ CD-RW Matsushita drive, intel 852 chipset with integrated graphic card, Intel Audio and an Ambit IPN2220 wireless card.

**What works:**

-I've had no problems installing, didn't have any issue with acpi or whatever. Just pressed enter and all fine
-The intel graphics card was automatically set up with the i810 driver and with 1024x768 resolution. Just perfect
-DVD/ CD burner: works perfect.
-Sound: working fine after installation, even the mic.
-Touchpad: works perfect after installation.
-The buttons controling LCD brightness and sound work fine (FN + key). When adjusting the volume it displays in the screen, adjusting the LCD doesn't. Not a problem.
-Print screen key: works fine after installation.

**What needs a work around to work:**

-Batery monitor: toshiba and toshiba_acpi modules don't do anything, as my notebook is using a phoenix bios. Used [this site]("http://www.minet.uni-jena.de/~ferdy/l10.html#way1") to get it working. Some important things: the 2.6.12 kernel-source that's in synaptic doesn't work, the patch fails when applying. So I downloaded and compiled a 2.6.12 from kernel.org, on which I could apply the patches fine.
-Suspend to ram: works fine, after activating it in /etc/default/acpi-support. Although it works, the hotkey (FN + F3) doesn't, and doesn't seem to be even a valid key combination.
-Suspend to disk: works fine. In the the /etc/default/acpi-support file I've had to set DOUBLE_CONSOLE_SWITCH=true instead of =false. The hotkey (FN + F4) doens't work.
-Wireless card: works fine with ndiswrapper and the drivers included in the CDs that came with the notebook.
-CPU scaling: work fine after installing emifreq and loading the p4-clockmod module.

**Untested**

-Ethernet card: will try one of these days.
-Modem: don't think I'll test it at the moment.

**What works but I don't know how to set up:**

My lappy has 4 keys, being those ones next, preview, play/ pause and stop. I know they work, and in System -> Preferences -> Key combination those keys appear as XFAudioWhatever: Prev, Next, Play and Stop. So, I am able to set them to launch Rhythmbox and so on, but I want to set them up to work in Beep Media Player, as that's the app I use to play music. Any ideas on how to make this work?



And that's it! Hope that's useful to anybody.

---

### Post by apt on 2006-05-01
How did you manager to get WiFI working|.  I've tried everything to get this working on my L10 , I've managed to get the windows wifi driver installed using ndiswrapper and it is recognised by the hardware but everytime I try and load the driver is gives me an error in the log something about not being able to load the driver.

Ay suggestions?

Regards

Adrian

---

### Post by patrickfromspain on 2006-05-01
First uninstall the driver with sudo ndiswrapper -e and check you have no drivers installed with sudo ndiswrapper -l.

Then, cd to the folder where the driver si and to install sudo ndiswrapper -i drivername.inf

Know, check if it is installed. It should say something like hardware present, driver present.

Then, sudo ndiswrapper -m and sudo modprobe ndiswrapper and that should do the trick.

---

