---
title: "Dell Latitude D620 -- Problem with suspend/hibernate"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by sanz on 2006-12-04
I followed instructions on  [UbuntuWiki for D620]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620"), trying to fix the problem of suspend/hibernate problem.

Now the suspend function works, but the monitor does not wake up at all after I wake up the system. The monitor is just remain completely black always. Everything else looks working fine, as the hard disk indicator, power indicator and Wifi indicator seem back on successfully. And I even can shut down the laptop though pressing the main switch button followed by Alt-S and Enter.

The hibernate function just does not work. When I restart the laptop, during boot-up, it says the filesystem is not clean marked with a "failed". The Ubuntu system starts okay yet without any traces of last session.

My system: Ubuntu Edgy (utf8 locale), GNome
 lspci -->
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by jbeiter on 2006-12-25
Did you have to do anything to get the wireless adapter to come back up after suspension?

I have a D820 with the same wireless adapter. Once it suspends, I have to reboot for the wireless to come back up.

- Joe

---

### Post by shutterbc on 2006-12-28
Hmm... I'm having a slightly different problem.  Seems to me that sometimes my D620 won't suspend correctly; the monitor blanks but the CPU fan and HD remain on, and I can't seem to wake the system back up.

I haven't tried this yet, but I'm thinking about trying out some nvidia hibernate howtos to fix my unstable suspend condition:
[http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)

Joe, I had a similar issue but was able to workaround by bringing the interface down and back up again.  Does that work for you?

---

### Post by mattyj on 2006-12-30
Does this work on a D820 as well?  I am thinking of getting one.

[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620)

Are there any other good sites for getting suspend/resume to work on ubuntu with laptops, especially with the nvidia drivers.

I really like ubuntu on my desktop, but suspend is pretty important to me for a laptop.

---

### Post by strabes on 2007-01-03
mattyj: [http://ubuntuforums.org/archive/index.php/t-79295.html](http://ubuntuforums.org/archive/index.php/t-79295.html)

---

