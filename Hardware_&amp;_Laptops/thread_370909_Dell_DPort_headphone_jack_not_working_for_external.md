---
title: "Dell D/Port headphone jack not working for external speakers"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Meson on 2007-02-26
When I plug my speakers (Soundbar for dell monitor) into the headphone jack on the docking station (DPort) there is no sound.  When the speakers are unplugged sound works fine.  Also, when the speakers are plugged into the headphone jack built into the laptop, sound works fine.

Also notable, the other features of the dock such as USB and the Ethernet port all work as expected.

I've opened the volume control and turned everything to a max - no help.

---

### Post by jmacdonagh on 2007-02-26
I have the same issue. This has been noted here:

[http://ubuntuforums.org/showthread.php?t=80193](http://ubuntuforums.org/showthread.php?t=80193)

Post a reply to that thread to bring it back to life. I'll keep everyone updated on the bug report I have filed.

---

### Post by Meson on 2007-02-26
I found a solution to this problem.

In the volume control, under the switches tab, enable IEC958.  If the switch isn't there, unhide it from within the preferences menu.  You may now plug your external speakers into the headphone jack of the dock.

I hope this works for everyone with a dell docking station!

---

### Post by Meson on 2007-02-26
Unfortunately this option appears to output at line level from the jack.  This should be a problem if you have a volume control on your speakers.  I'm not sure what'll happen if you plug in headphones though (be careful! =P)

---

### Post by shotgunefx on 2007-02-28
> **Meson said:**
> Unfortunately this option appears to output at line level from the jack.  This should be a problem if you have a volume control on your speakers.  I'm not sure what'll happen if you plug in headphones though (be careful! =P)

I've got an Inspiron 8600 and a Dell APR (PR01x) and I've tried this and I still get no sound.

Any suggestions? I'd really appreciate this as it's a carpc and it's a hassle to not just have everything plugged into the dock. 

I had given up on it as my previous install (a Dell latitude) had the same problem but at the time it was due to the driver not supported the outputs on the chipset it used.

**update**
Duh, have to apply the patch first :\

**update again**
No I don't, I'm running 2.6.20 and it still doesn't work, guess I'll need to make a new patch. :(

---

### Post by shotgunefx on 2007-02-28
Don't need the patch, running 2.6.20, but still no dice for the PR01x D/Port APR

Looks like another patch is needed.

Could someone who has this working post the results of lspci -v (and the dell model) so I can see what corresponds to what?

---

### Post by Meson on 2007-02-28
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 014e
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Prefetchable memory behind bridge: 88000000-8bffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Latitude D400
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 8c000000 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 014e
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5650] (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 019c
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
        Subsystem: Dell Latitude D400
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at faff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
        Subsystem: Dell Latitude D800
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at fa000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: f6000000-f7fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
        Subsystem: Dell Latitude D800
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at fa001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 8a000000-8bfff000 (prefetchable)
        Memory window 1: f8000000-f9fff000
        I/O window 0: 0000d800-0000d8ff
        I/O window 1: 0000dc00-0000dcff
        16-bit legacy interface ports at 0001

02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller (prog-if 10 [OHCI])
        Subsystem: Dell PCI7410,7510,7610 OHCI-Lynx Controller (Dell Latitude D800)
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at fafef800 (32-bit, non-prefetchable) [size=2K]
        Memory at fafe8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
        Subsystem: Dell Latitude D800
        Flags: medium devsel
        I/O ports at ecf8 [size=8]
        Capabilities: <access denied>

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
        Subsystem: Dell Truemobile 1450 MiniPCI
        Flags: bus master, fast devsel, latency 32, IRQ 7
        Memory at fafec000 (32-bit, non-prefetchable) [size=8K]
```

Hope that helps - just so you know the video card and wireless card i don't ahve working yet.

---

### Post by shotgunefx on 2007-02-28
> **Meson said:**
> [CODE]
Hope that helps - just so you know the video card and wireless card i don't ahve working yet.

Thank you much! 

I've had no problems with the wireless built into the laptop or the geforce card either, including dual heads, I've got the GeForce FX Go5200  and Intel  PRO/Wireless LAN 2100 though.

---

### Post by Meson on 2007-02-28
Yeah I think my problem is that I have the Dell Wireless card not the intel.  And I'm not a great wrestler on the Linux mats yet...

For the NVidia though, by no problem do you mean the card works fine as is, or did you install the driver from the nvidia website?  After I install it my screen refuses to display the picture.  I can get he right resolution and color depth without it, I'm just wondering if I'll benefit from having the nvidia drivers or not.

---

### Post by shotgunefx on 2007-02-28
Success with modding patch_sigmatel.c

Added the entry for the 8600 and now the dock audio works after rebuilding, also managed to knock off a few other nagging lingering problems with my install at the same time. 
> 
static struct hda_board_config stac9200_cfg_tbl[] = {
  { .modelname = "ref",
    .pci_subvendor = PCI_VENDOR_ID_INTEL,
    .pci_subdevice = 0x2668,  /* DFI LanParty */
    .config = STAC_REF },
  /* Dell laptops have BIOS problem */
  { .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01b5,
    .config = STAC_REF }, /* Dell Inspiron 630m */
  { .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01c2,
    .config = STAC_REF }, /* Dell Latitude D620 */
  { .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x01cb,
    .config = STAC_REF }, /* Dell Latitude 120L */
[B]  { .pci_subvendor = PCI_VENDOR_ID_DELL, .pci_subdevice = 0x016a,
    .config = STAC_REF }, /* Dell Inspiron 8600 */[/B]
  {} /* terminator */
};

> **Meson said:**
> Yeah I think my problem is that I have the Dell Wireless card not the intel.  And I'm not a great wrestler on the Linux mats yet...

For the NVidia though, by no problem do you mean the card works fine as is, or did you install the driver from the nvidia website?  After I install it my screen refuses to display the picture.  I can get he right resolution and color depth without it, I'm just wondering if I'll benefit from having the nvidia drivers or not.

I'm using the proprietary drivers from Nvidia's website. I wanted the 3d acceleration as part of the software I'm writing (for my car) is a digital dash and eventually I want to integrate a 3d model of the car to show the locations of the trouble codes. 

Also my understanding was you can't use dual heads with the "nv" driver, I have one lcd for the dash, and a touchscreen where the stereo was so using the closed drivers was pretty much neccassary.

That being said, the nv drivers worked ok (the brief amount of time I used them).

What errors are you finding in the log file? 
```

cat /var/log/Xorg.0.log | grep "(EE)"

```

---

### Post by jmacdonagh on 2007-03-02
> **shotgunefx said:**
> Success with modding patch_sigmatel.c

Added the entry for the 8600 and now the dock audio works after rebuilding, also managed to knock off a few other nagging lingering problems with my install at the same time. 



I tried applying the patch you gave. I downloaded the deb source using apt-get source, applied the patch (I didn't have as many *quirks* in my cfg_tbl as you did), rebuild the package, installed them, restarted, and nothing.

Any idea?

---

### Post by shotgunefx on 2007-03-02
> **jmacdonagh said:**
> I tried applying the patch you gave. I downloaded the deb source using apt-get source, applied the patch (I didn't have as many *quirks* in my cfg_tbl as you did), rebuild the package, installed them, restarted, and nothing.

Any idea?

Do you have the same device number? (16a) when you lspci -v?

Also, one oddity I forgot to mention, when using the mixer, once you unmute the chip (can't think of the name at the moment), you have to set the volume for it to zero, any non-zero volume cuts off the output.

Hope this helps.

---

### Post by caldevil on 2007-03-05
Guys, the new alsa-base 1.0.14rc3 has added support to the following models:

Dell D820, D620, M90, 630m, 120L, 9400/E1705, M1710, M90.

I have added support request for 600m/D600 and 8600.

If you any other model and want to see d/port replicator working can you please post the output of:
/proc/asound/card0/codec*/ac* file.

---

### Post by cRoMo on 2007-03-05
Dell Precision M20 (basically same as Dell Latitude D610). Meson's solution seems to work here, although I get no volume control either :| 

```

506:cromo@kromka:~$ cat /proc/asound/card0/codec97#0/ac97#0-0*
0-0/0: SigmaTel STAC9750,51

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x01a0

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +20dB [+20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=10/11 VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz
0:00 = 6a90
0:02 = 0000
0:04 = 0505
0:06 = 801f
0:08 = 0000
0:0a = 001a
0:0c = 801f
0:0e = 8052
0:10 = 8202
0:12 = 9f1f
0:14 = 9f1f
0:16 = 9f1f
0:18 = 1616
0:1a = 0000
0:1c = 8000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0605
0:2a = 0431
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0100
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0003
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0002
0:6e = 1000
0:70 = 0000
0:72 = 0000
0:74 = 0800
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 8384
0:7e = 7650
```

---

### Post by shotgunefx on 2007-03-08
From my Dell Inspiron 8600
```

0-0/0: SigmaTel STAC9750,51

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x016a

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : post 3D
Sim. stereo      : off
3D enhancement   : on
Loudness         : off
Mono output      : Mic
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=3/4 SPDIF VRA
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz
0:00 = 6a90
0:02 = 0101
0:04 = 8000
0:06 = 8000
0:08 = 0000
0:0a = 0000
0:0c = 0007
0:0e = 0006
0:10 = 0003
0:12 = 0000
0:14 = 0404
0:16 = 0000
0:18 = 0000
0:1a = 0202
0:1c = 0000
0:1e = 0000
0:20 = a200
0:22 = 000c
0:24 = 0000
0:26 = 000f
0:28 = 0605
0:2a = 0405
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0100
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0003
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0002
0:6e = 1000
0:70 = 0000
0:72 = 0000
0:74 = 0800
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 8384
0:7e = 7650

```

---

### Post by eidur on 2007-06-07
Had the same problem, but with a D400, no audio from dock but fine on internal speaker.  Followed Meson's advice,  and got sound, after muting ICE958 in the volume control dialog. Also no control over volume, but fine for me.

---

### Post by jprince on 2007-06-14
:KS:KS> **Meson said:**
> I found a solution to this problem.

In the volume control, under the switches tab, enable IEC958.  If the switch isn't there, unhide it from within the preferences menu.  You may now plug your external speakers into the headphone jack of the dock.

I hope this works for everyone with a dell docking station!:KS:KS


this fixed mine. I had to switch it from ALSA to OSS first and then enable all of the tabs. No more moving the speaker cable.. YEAH!


Jeff:popcorn:

---

### Post by ibeetalk on 2007-09-01
> **Meson said:**
> I found a solution to this problem.

In the volume control, under the switches tab, enable IEC958.  If the switch isn't there, unhide it from within the preferences menu.  You may now plug your external speakers into the headphone jack of the dock.

I hope this works for everyone with a dell docking station!



The posting quoted here worked for my Dell Latitude D600 ... Everything is working fine now. 

PS - I am a Linux novice

---

### Post by c0reyf on 2007-09-04
This feature worked for me and I can use my external speakers on the dock station. I have a D610 Lat and now I can't reverse the process. My volume buttons no longer function docked or undocked. Any ideas would be appreciated

---

### Post by c0reyf on 2007-09-04
Fixed. I had to toggle the PC volume button off.

---

### Post by nutz on 2007-10-27
I have not been able to solve this issue just yet. I have enabled the ICE958 but still no sound is available from the line out port on the dock or its S/PDIF connection.

There is also another thread on this here...
[http://ubuntuforums.org/showthread.php?t=80193&page=2](http://ubuntuforums.org/showthread.php?t=80193&page=2)

---

### Post by Meson on 2007-10-27
> **nutz said:**
> I have not been able to solve this issue just yet. I have enabled the ICE958 but still no sound is available from the line out port on the dock or its S/PDIF connection.]

To get it to work I needed to mute the IEC968 Playback in the volume control. (For the ALSA driver).  This seemed to unmute the Digital-1 control in the OSS driver.  If I mute Digital-1, my sound goes off.  So the control really seems to be effective when  you do it through the OSS driver

---

### Post by nutz on 2007-10-27
> **Meson said:**
> To get it to work I needed to mute the IEC968 Playback in the volume control. (For the ALSA driver).  This seemed to unmute the Digital-1 control in the OSS driver.  If I mute Digital-1, my sound goes off.  So the control really seems to be effective when  you do it through the OSS driver

Thank you for the advice. I tried that and it still doesn't work. I have tried every setting possible within the volume control both on the ALSA mixer and the OSS. One thing worth noting is that it places the Digital-1 option under the recording tab and not the playback one on the OSS mixer. And on the ALSA mixer is has two check boxes; one to enable the IEC958 and one to enable capture on the IEC958 but I have tried messing with these setting and they don't seem to have any effect. To the best of my knowledge the sound hardware on my setup does not support digital recording through the S/PDIF port.

---

