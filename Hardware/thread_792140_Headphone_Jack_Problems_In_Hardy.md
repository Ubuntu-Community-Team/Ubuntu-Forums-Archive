---
title: "Headphone Jack Problems In Hardy"
date: 2008-05-12
forum: Hardware
---

### Post by amtur_poet on 2008-05-12
Whenever I plug a set of headphones into the headphone jack in Ubuntu, no sound comes out. My speakers, however, work fine.

---

### Post by otrojake on 2008-05-12
Let's start with the easy stuff.  Double-click on the speaker icon in the top-right of the screen.  From there, check Edit>Preferences to see if there's a headphone channel you can enable by checking one of the boxes.  If you can enable it and it works, fantastic.

If not, could you post the output of these codes?```
lspci
``` and ```
aplay -l
```

---

### Post by amtur_poet on 2008-05-12
lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


aplay -1
> aplay: invalid option -- 1
Try `aplay --help' for more information.


---

### Post by otrojake on 2008-05-12
Could you post the output of aplay again?  The option is supposed to be a lowercase L, not a one.```
aplay -l
```  Sorry if the first one confused you.  Those l's and 1's can be tricky.:)

---

### Post by amtur_poet on 2008-05-12
aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by otrojake on 2008-05-12
Well, it looks like the only thing to do now is this:

Edit the /etc/modprobe.d/alsa-base file with this code```
sudo gedit /etc/modprobe.d/alsa-base
```  The next part is inserting a model name at the last line of that file.  After saving the changes to the file, reboot--that's really important; do a full restart--and see if that model works.  If it doesn't, move on to the next.

Here are some models that stand the best chance of working with that chip:  > laptop
hp
laptop-hp

To use one of those models, add this line to the bottom of the /etc/modprobe.d/alsa-base file

> options snd-hda-intel model=model_name replacing one of the models above in the place of "model_name."  Let me know if you run into any more issues.

---

### Post by amtur_poet on 2008-05-25
Sorry for the late reply, but it didn't work.

---

### Post by worc on 2008-05-26
Same problem here.
TOSHIBA p105 S9337

Actually, there is sound coming out from the headphone if you plug the headphone out a little bit, it's very sensitive.

Don't know how to fix it.

---

### Post by drpaul on 2008-05-26
Check another posting by worc. He just solved his problem [very similar].

HTH

Paul

---

