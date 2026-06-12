---
title: "Microphone stops working after suspend"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by tbraun on 2007-11-27
Hello!

I have a Dell Latitude D820, running Ubuntu 7.04 (Feisty). All works well, including suspend to RAM. However, once it comes back from suspend, the microphone has stopped working. Sound itself still works, but I cannot record sounds, or use VoIP anymore. Logging in and out doesn't help, I actually have to reboot the machine to make it work again, which of course defeats the whole purpose of suspend.

Below is the output from lspci.

Does anyone know what I can do to get the microphone operational again after suspend? Is there maybe something I can change in the suspend scripts? Or a command to 'reset' the responsible sound drivers?

Any help is greatly appreciated.

Tom


- - - - - - - - - - - - -

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by tbraun on 2008-01-09
Bump...

Any help anyone? Please?

---

### Post by superchris on 2008-01-10
I have the same problem on a Dell Inspiron 9400.  Anyone have a fix for it?

---

### Post by tbraun on 2008-01-10
Hello!

[ I posted this in the general support forum before, but didn't get a response there. Since other Dell users apparently have the same problem, I thought I ask here again... ]

I have a Dell Latitude D820, running Ubuntu 7.04 (Feisty). All works well, including suspend to RAM. However, once it comes back from suspend, the microphone has stopped working. Sound itself still works, but I cannot record sounds, or use VoIP anymore. Logging in and out doesn't help, I actually have to reboot the machine to make it work again, which of course defeats the whole purpose of suspend.

Below is the output from lspci.

Does anyone know what I can do to get the microphone operational again after suspend? Is there maybe something I can change in the suspend scripts? Or a command to 'reset' the responsible sound drivers?

Any help is greatly appreciated.

Tom


- - - - - - - - - - - - -

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by tbraun on 2008-01-21
I have a Dell Latitude D820 with Gutsy. After returning from suspend the microphone is gone. There doesn't seem to be anything I can do to get it back.

Is it possible to restart the sound system somehow in its entirety, so that it has a chance to rediscover the microphone?

Thank you very much...

---

### Post by PhilipGanchev on 2008-01-21
Try this. Open a terminal and issue the command "lsmod | less".  Then scroll through the list and look for something that might be the name of the sound driver.  If you find it, issue the command "sudo modprobe -r <modulename>" and "sudo modprobe <modulename>".  That sometimes fixes it until you suspend again. That's not ideal, but I don't know how to make it work automatically.

---

### Post by tbraun on 2008-01-21
Thank you very much, this worked!

In my particular case, the name of the driver is snd_hda_intel. I added the following two lines to /etc/acpi/resume.d/67-sound.sh so that the necessary commands are executed automatically after the computer comes back from suspend:

[INDENT]modprobe -r snd_hda_intel
modprobe snd_hda_intel
[/INDENT]

Thanks again. This solves one of my longest standing issues with Ubuntu on my laptop. Something I asked several times before in different forums.

You just made my day! :)

---

### Post by tbraun on 2008-01-21
Found the solution. It's in this thread:

[http://ubuntuforums.org/showthread.php?p=4182623]("http://ubuntuforums.org/showthread.php?p=4182623")

---

### Post by tbraun on 2008-01-21
Found the solution!

It's in this thread: [http://ubuntuforums.org/showthread.php?p=4182623]("http://ubuntuforums.org/showthread.php?p=4182623")

---

