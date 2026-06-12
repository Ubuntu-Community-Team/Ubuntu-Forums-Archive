---
title: "Compaq Presario V6105NR"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by matt_risi on 2007-02-13
This is a plea for help.

I've searched through the web and these forums, looking for a fix to the following problems, but (obviously) to no reasonable avail. I'll list the issues I'm having in order of importance to me.

Well, I should probably post my lspci output first.

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)

```

Okay. Here goes:

1) I'm getting random shutdowns, when my battery is at around 40%. Just before it shuts down, power management notifies me saying "Power is critically low and the computer will now shut down" or something to the likeness. I'm sure it has something to do with the power meter showing the completely wrong amount of time remaining (48 hours remaining at 79%? I WISH!). I've tried discharging and charging my laptop fully in an attempt to "calibrate" the battery to Ubuntu, but no dice. Any ideas?

2) My headphone jack doesn't work, which is HUGE for me, as I can't use Ubuntu and listen to music in the library. I know it has something to do with there not being an ALSA driver for my sound card, if I'm not mistaken. Are they any workarounds with this?

3) Although wireless is working with latest version of ndiswrapper, I have to input ```
sudo modprobe ndiswrapper
``` at each boot in order to activate it. This isn't such a big deal really, and is actually a little nicer than waiting 2+ minutes for my laptop to boot while I'm at school because of the change in networks. (Also, I still cannot get wireless working on the new -11 kernel update, but that's not a very big deal as I just boot straight to -10.)

Other than that this computer is so AWESOME. It's a fresh install of Ubuntu Edgy, about 2 days old by the way. (When wireless wasn't working on -11 I took it as an opportunity to much about) :)

Thanks in advance to anyone who can offer me a little help.

---

### Post by matt_risi on 2007-02-15
Bump!

---

### Post by matt_risi on 2007-02-19
Bump!

PLEASE guys give me a little guidance, even if it's just something that would help me a little!

---

### Post by cadamr on 2007-02-19
problem 1: 
Try going to System>> Preferences>> Power Management  >> Running On Battery
and change what it does when battery power is critical. Sorry it's just a quick fix, and won't take care of your 48 hr battery life, lol.

problem 2:
Try  :~$ sudo apt-get update
        :~$ sudo apt-get install alsa
and cross your fingers.

problem 3::confused:

Hope this helps some.

---

### Post by cadamr on 2007-02-20
Just had another thought. If all you have to do is modprobe ndiswrapper to get it working correctly, you could just do it automatically on startup.
System >> Preferences >> Sessions >> Startup Programs >> Add
and type "sudo modprobe ndiswrapper"

---

### Post by matt_risi on 2007-02-26
Thanks for trying, but the sound is still problematic. And also, I've grown accustomed to manually inputting ndiswrapper on startup, it's just more convinient than waiting 2 minutes for the computer to boot when it tries to find a network that isn't there.

Any other ideas for the headphone jack problem?

---

### Post by matt_risi on 2007-03-27
Pleeeeeeeeeassse guys, this is killing me!

---

### Post by matt_risi on 2007-04-20
Upgrade to Feisty resolved headphone jack issue! Also way better hotkey detection.

---

