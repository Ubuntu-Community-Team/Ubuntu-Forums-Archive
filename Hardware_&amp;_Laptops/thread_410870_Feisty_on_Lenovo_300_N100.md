---
title: "Feisty on Lenovo 300 N100"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by MZaza on 2007-04-16
I've installed ubuntu 7.04 on my lenovo 3000 N100. And I've got lots of hardware not working like the internal webcam, internal mic, finger print and memory card reader. But when I checked the wiki page for my laptop I found that the memory card reader works on the edgy, so I think that it should also work on the feisty. Any Ideas?

Also I think it would be great if the ubuntu team gives more time to make drivers for various commonly used hardware drivers.

---

### Post by kingy89 on 2007-04-16
true, it would also be nice if the hardware makers made linux compatible drivers!

anyway!

Did any of the hardware work using the LiveCD? or just after install?

---

### Post by MZaza on 2007-04-16
I don't get you, what do you mean by any of the kit?

---

### Post by kingy89 on 2007-04-16
sorry, i meant the webcam etc, 

i used kit because it was faster for me to type than hardware.

I was being lazy!

What i mean is, does the memory card reader etc, work when using the LiveCD?

---

### Post by flammenwurfer on 2007-04-16
Finally, someone else with the same laptop and problem as I.  Did you upgrade after install Feisty?

Upon a fresh install of 7.04 my card reader works like a charm, however after I upgrade through synaptic it quits working.  I think we just need figure which package is causing the trouble during the upgrade.

---

### Post by flammenwurfer on 2007-04-18
Well, if I boot with kernel 2.6.20-12 my card reader will work, with an SD card atleast.  However, a Memory Stick does not.  Was anybody else able to get a memory stick to be recognized at all?

---

### Post by MZaza on 2007-04-18
Well guys, I've tried to get the MMC reader work while using the LiveCD but it didn't work. So I think that we need to solve these problems our selves, I'll post here what is not working and we should try to find solutions for these problems our selves.

1- Internal Mic
2- MMC Reader
3- Finger Print
4- Internal Cam

---

### Post by sanku on 2007-04-20
Hey Guys, 

                 good to find someone using the N100. I have just installed Ubuntu 7.04, but unable to get the widescreen resolution working. the maximum it gives is 1024x768. Any clue how to resolve this issue.

Thanks in advance.

---

### Post by MZaza on 2007-04-20
I've got the same problem, i'll try google.

---

### Post by Donnieb on 2007-04-20
Sanku either use apt-get, adept, or synaptic, and download the 915 resolution, it should fix it to use the default 1280x800, if it doesn't go to that after a restart run the command xrandr -s (the number of the correct resolution. Unfortunately this isn't a permanent fix, someone more wise than me will have to explain how to change it permanently.

MZaza, there are some early alpha drivers for the webcam and fingerprint reader, but they are def early alpha. If you have any software developing skills you might check them out, links are [http://www.mail-archive.com/linux-uvc-devel%40lists.berlios.de/msg00542.html]("http://www.mail-archive.com/linux-uvc-devel%40lists.berlios.de/msg00542.html") for info on webcam projects and [http://gkall.hobby.nl/authentec.html](http://gkall.hobby.nl/authentec.html)[http://gkall.hobby.nl/authentec.html]("http://gkall.hobby.nl/authentec.html") for the fingerprint reader. As far as the MMC slot goes I've seem posts with mixed success, looks like the chipset is a Rioch and people have had mixed success. As far as built in mic, I don't see one built into my 3000 n100 but it does show up in the mixer program, this could be because the sound card is actually also a modem. 

I hope this clears some stuff up.

---

### Post by MZaza on 2007-04-20
Thanks alot Donnieb, i really appreciate this information.

---

### Post by kingy89 on 2007-04-21
Ok...if nothing else works you can do this as a fix. Beware it involves altering a system file and therefore a backup should be made first.

Run:
sudo gedit /etc/X11/xorg.conf

Put your password in and scroll down to the area where the resolutions are. You need to manually add 1280x800 to each of the depths. Make sure you keep it the same as how the rest of them look. Save the file, close any programs and then restart X (Ctrl-Alt-Backspace). 

This is a fix to your problem as a last resort, but is more risky (if you do it wrong X might not work anymore)

---

### Post by macogw on 2007-04-23
What kind of card reader is it?
In the terminal, type:
lspci

then post the output here

---

### Post by MZaza on 2007-04-24
Here you go.

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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by macogw on 2007-04-24
if you do
lsmod | grep sd
what comes up?

---

### Post by 0jjjjjjjjjj0 on 2007-04-24
I have model 0768-A52. Widescreen is fine, SD memory is fine, but no sound or XD/Memory Stick as yet. Googling away, will post resolution/s as they come to hand. Oh, wireless is fine as of this morning also ...

---

### Post by 0jjjjjjjjjj0 on 2007-04-24
> **macogw said:**
> if you do
lsmod | grep sd
what comes up?

$ lsmod | grep sd
sdhci                  18700  0 
mmc_core               26756  2 mmc_block,sdhci
tsdev                   8768  0 
sd_mod                 23428  6 
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata

---

### Post by 0jjjjjjjjjj0 on 2007-04-24
> **macogw said:**
> What kind of card reader is it?
In the terminal, type:
lspci

then post the output here

05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

To recap, I don't have MMC to test but SD works fine, XD and MS do not.

---

### Post by macogw on 2007-04-25
There are no drivers (at all) for xD and MS and MS Pro.  Only SD and MMC have drivers.  I guess someone's working on writing those drivers, but they're not done.

---

### Post by sphirad on 2007-04-27
Hi,

I'm also using the lenovo 3000 N100 actually on debian, but the distros are almost identical on the technical side. I'm suffering the same problems with the microphone, camera and card reader, but I've found this blog by the laptop testing team:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

It has solutions for various problems including the sound. I've started following it but I probably have to recompile my kernel which I don't have time for now. Hope you find it helpful.

---

### Post by sprv on 2007-05-07
> **sanku said:**
> Hey Guys, 

                 good to find someone using the N100. I have just installed Ubuntu 7.04, but unable to get the widescreen resolution working. the maximum it gives is 1024x768. Any clue how to resolve this issue.

Thanks in advance.

intel video bios driver needs a patch.
try to install 918resolution package from ubuntu repos and restart your system.
and fixed.

---

### Post by macogw on 2007-05-07
It's 915resolution

---

### Post by honghai on 2007-05-08
Using the new driver from debian repository for intel card may solve the problem:
Check my reply in this thread:
[http://ubuntuforums.org/showthread.php?t=428134&highlight=badalloc](http://ubuntuforums.org/showthread.php?t=428134&highlight=badalloc)

---

### Post by LukaCMF on 2007-05-22
Hi people,
if anybody didn't yet figure out how to solve problem with sound on any intel hda sound device on laptop here is a good link [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)
it should work on any intel hda ich7 and maybe more.

---

