---
title: "Hasee laptop assistance"
date: 2008-05-17
forum: Hardware
---

### Post by fdhionly on 2008-05-17
I recently purchased a new Hasee laptop, all excited at the thought of getting one pre-loaded with Linux.  Now, I am faced with the possibility of my first international return, so before I send it back to Asia I want to get second opinions.

The main problem is no sound.  Are there any known bugs with 7.10?  What steps should I go through?

Also, is there something I can do to test all the features of this laptop and post it as a review?  

Thanks.

---

### Post by nicedude on 2008-05-17
Post your model number of hasee laptop here along with output of following command below also try the second command to check alsamixer volume levels. I would definitely not send it back yet as this is probably a software situation not hardware so wait and let the good guys here help diagnose first.

Run the following in a terminal window -> Applications -> Accessories -> terminal

command to list devices
lspci

Command to check sound volume levels - just run and see if volume is up
alsamixer

---

### Post by fdhionly on 2008-05-18
The model I am working with is:  **HASEE Model# HP520**

1)  Output of #lspci command to list devices:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
0b:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0b:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0b:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0b:09.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
frances@hasee-laptop:~$ 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
bash: syntax error near unexpected token `('


2)  Output of #alsamixer command to check sound volume levels:

Card:  HDA Intel
Chip:  Realtek Id 268
View:  Playback
Item:  Master [dB gain=-24.00, -24.00

Master 63<>63  (was initially 94<>94 not sure why it changed)
PCM    100<>100
Digital 50<>50

Thanks!

---

### Post by nicedude on 2008-05-20
Did you get the sound working? Sorry but I did not understand whether this is now solved or not if so please mark thread as solved, If not PM me by clicking my name and selecting "send private message" and I will help all I can.

---

