---
title: "HP EliteBook 8730w Install and Boot issues"
date: 2008-12-08
forum: Hardware
---

### Post by hugov on 2008-12-08
HI, I am using an HP EliteBook 8730w, I tried to install Ubuntu 8.10 last night, with no luck, I then installed OpenSuse after disabling noacip (or something in that line), everything worked fine. I then decided that I really want Ubuntu 8.10, so I tried to do the same when installing, I selected noacip (something like that) which allowed me to install Ubuntu 8.10, but after reboot, no go, it does the little orange Knight Rider thing, and then gives me a black screen with a blinking cursor. I rebooted and then pressed Ctrl + Alt + F1, I then saw a CPU softlock error, CPU0 got stuck on 61s. What to do? I was so looking forward to 8.10 and reaaaaly don't want to go back to OpenSuse 11. Please help me out.

---

### Post by andreasis on 2008-12-08
I found this and it seems to be related to the wireless card driver. [http://ubuntuforums.org/showthread.php?t=358112](http://ubuntuforums.org/showthread.php?t=358112)

If you (can) disable your wireless card from your BIOS or with a wifi kill switch, if your laptop comes with this, then it should let you boot into the system.  Do you remember what wireless drivers you installed/were in use when you installed opensuse?

---

### Post by hugov on 2008-12-08
Thanks for the reply, I will have a look at which Wi-Fi options I have. I did not pay attention to which drivers OpenSuse use unfortunately. How would I go about updating my Wifi driver for Ubuntu if I can get it to boot into it?

Thanks once again.

---

### Post by andreasis on 2008-12-08
If you can get your live-cd to run or otherwise make it into ubuntu or any version of linux with your wireless card enabled (as it had been until now), could you type into a terminal ```
lspci
``` and post the line that refers to the wireless card? It should tell you what type of wireless card you have, and once we know that, we can look at what the correct driver for that card is.

[EDIT] hugov, I will return in about 18 hours to continue helping you with this.  My apologies/ hope other users can provide help in the meantime, although I will be more than happy to continue from where we left off : )

---

### Post by hugov on 2008-12-08
I disabled the WI-FI but still no go, it made no difference :(

---

### Post by hugov on 2008-12-08
I managed to get it to boot into the live cd, here is the results of the command you gave me to run:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 063a (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
86:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 14)
86:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 14)
86:06.5 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)

---

### Post by hugov on 2008-12-08
I also noticed the following error:

Your PnPBios caused a fatal error. You may need to reboot with "no-pnpbios"

How do I do this?

---

### Post by hugov on 2008-12-10
I managed to get Ubuntu up and running. I have set acpi=off in my grub and it is working ok now, I have a major delay when I log in though which is irritating me a lot, but at least it is in.

---

### Post by andreasis on 2008-12-16
I'm very glad to hear that!  We can take a look at the lag problem if you'd like.  Let me konw if you'd like to do that.

---

