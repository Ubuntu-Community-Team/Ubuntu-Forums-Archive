---
title: "Wireless card not detected"
date: 2008-10-17
forum: Hardware
---

### Post by c707176 on 2008-10-17
Hi, 

I have installed Ubuntu on a lenovo W500 laptop. I have the problem that my wireless card is not detected. Does anybody know how to fix this? The output of lspci is:

00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Cantiga MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Cantiga PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Cantiga AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3650
03:00.0 Network controller: Intel Corporation Unknown device 4237
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by gatman3 on 2008-10-18
I just got a W500 today as well and the Intel 5100AGN wi-fi is not working either (I think that's the same device listed in your lspci as device 4237).  I attempted with 8.04.

There seems to be a fair amount of confusion on this topic.  The best I can figure, the kernel driver in 8.04 (2.6.24 kernel) doesn't properly support this card.  However, it appears that many people are having good successful with the 8.10 beta that just came out which runs the new 2.6.27 kernel.  Seems like at least some are still having trouble with the new kernel, but they may also be running 64-bit (a little hard to correlate some of the posts).

I am in the process right now of downloading the 8.10 beta to try it out.  If that doesn't work, I have read that some people need to also upgrade the firmware from the intellinuxwireless.org website.  I would first try the 8.10 beta before upgrading the firmware.

If you don't want to go to the 8.10 beta, I did read that someone was successful pointing their 8.04 install to the intrepid (8.10) repositories and upgrading just their kernel to 2.6.27.  That seems a little dicey to me, but might be worth a shot.  Your old kernel should still be left in the grub install menus, so you can always drop back to 2.6.24 if the 2.6.27 kernel hoses up 8.04 for some reason.

Good luck.  Let me know if you figure it out.

---

### Post by gatman3 on 2008-10-18
Well, looks like the 8.10 beta release fixes it.  The 5100AGN wi-fi appears to work.  However, 8.10 beta has other "issues".  The networkmanager, while promising, still doesn't seem to work quite right.  I was not able to get it to recognize my secured network at home, and I had to drop back to manual configuration in /etc/network/interfaces.  That, however, worked just fine.

8.10 beta seems to have some other problems too.  It gave me three update notifications right out of the box (three light bulb icons on the task bar), but none of them can get past some problem with language configuration.  I'm running an update in adept now (I run KDE) so maybe things will improve after an update and reboot.

I also had a problem where the icon switched to some goofy line (no longer an arrow).  Ultimately it fixed itself when I moved it back over the trash can icon in the corner.  Weird.  I think that's probably a KDE4 problem.  Maybe GNOME in 8.10 beta works better.

Otherwise, KDE4 is beautiful.

At this point I think I am going to try limping along with 8.10 beta.  Good luck.

---

### Post by c707176 on 2008-10-18
I think I don`t want ro replace one problem with another. Is there somebody how figured out how to properly configure this type of wireless card in Ubuntu?

---

### Post by iponeverything on 2008-10-18
Please see. It should fix you right up..

ref: [http://ubuntuforums.org/showthread.php?p=5662925](http://ubuntuforums.org/showthread.php?p=5662925)

---

