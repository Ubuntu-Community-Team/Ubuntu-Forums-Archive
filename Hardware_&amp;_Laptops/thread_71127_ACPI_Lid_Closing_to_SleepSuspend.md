---
title: "ACPI Lid Closing to Sleep/Suspend"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by Starman on 2005-10-02
Dell Latitude D400, Colony-4 + updates

I noticed that /proc/acpi/button/ has sub-directories and files that are empty. Does anyone know what needs to go in them to get the system to sleep or suspend when the lid is closed?

I can hibernate the system by pushing the power button but closing the lid only turns off the screen. The system remains energized, draining the battery.

thanks in advance...

---

### Post by JLB on 2005-10-02
this is from my wiki page on my hp nc6120 laptop. it should help you out. blanking the screen is the default behavior. I've copied  note #6 from [https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6120](https://wiki.ubuntu.com/LaptopTestingTeam/HPNC6120)


*NOTE 6: Suspend to RAM works but you must edit /etc/default/acpi-support and uncomment the line that states : ACPI_SLEEP=true . Then you will find that after a reboot you will be able to use the Fn-F3 key and/or the logout applet to suspend to RAM. To get the lid switch to activate suspend to RAM, edit /etc/acpi/events/lidbtn and change "action=/etc/acpi/lid.sh" to "action=/etc/acpi/sleep.sh"

---

### Post by Starman on 2005-10-03
Thanks, that did it, although I seem to experience higher battery usage under normal operation than when booted to XPSP2. Speed-step maybe?

---

### Post by JLB on 2005-10-03
I am not familiar with your laptop, but on mine, speedstep works properly and i get similar battery performance under linux. glad that little bit of info helped you out.

---

### Post by Starman on 2005-10-08
Anyone know how to prevent the laptop from beeping when I open the lid? Suspend on lid closing is working ok but the beep is annoying to others, especially in meetings.

I tried bios settings but nothing in the dell bios seems to prevent the LOUD beeping.

---

### Post by JediPottsy on 2005-10-16
ok suspend works :D i can close the lind and the laptop will "sleep" however when i open up the laptop again and press any button, the system loads but the screen doesnt turn on....im using an acer 1672LMi

---

### Post by sonojacker on 2005-10-21
[QUOTE=JediPottsy]ok suspend works :D i can close the lind and the laptop will "sleep" however when i open up the laptop again and press any button, the system loads but the screen doesnt turn on....im using an acer 1672LMi[/QUOTE]

Hello Jedi.  Solutions for laptops coming back from hibernation or suspend do not have an universal formula.  Your problem could come from the X server and its ability to warm-boot the video hardware (for which acpi-support has clue workarounds), and the set of kernel modules and/or services in memory at the moment of suspension.  Add some of those services and modules to the /etc/default/acpi-support file, that might tell suspension script to stop and restart those.

The procedure has been thoroughly quoted at the Wiki's LaptopTestingTeam entries.

1. Get to your /etc/default/acpi-support file, and do test and trial adding the modules and services that should be stopped and restarted.
2. As to Breezy final, the acpi-support file is very useful; play with it activating options such as the X double video post, the disk_drive resetting, or disabling DMA.

My bets were:
MODULES="ndiswrapper uhci-hcd ehci-hcd raw1394 ohci1394 ieee1394 3c59x"
STOP_SERVICES="hotplug mysql apache2 networking"
(with no X reposting)

and my laptop does almost seamless suspend-to-ram.  Sometimes I find new services and progs conflicting, but suspend is rather usable.

sonojacker
- Emachines AMD64 (Arima chipset), Breezy Final.

---

