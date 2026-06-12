---
title: "Sony Vaio VGN-TT2 - Globetrotter M040x 3G Modem"
date: 2009-03-15
forum: Hardware
---

### Post by alex.davies on 2009-03-15
Hi Everyone,

I've got a Sony Vaio VGN-TT2 laptop, and have a problem getting the modem to work.

The device, as reported in Windows (where it works) is a Globetrotter M040x 3G Modem. From the IMEI #, I have manged to discover that this device is a "GTM382 W" ([http://www.option.com/en/support/software-download/modules/gtm382w/articles/](http://www.option.com/en/support/software-download/modules/gtm382w/articles/)). This devices is listed as "Works but requires some hacks" @ [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G). Does anyone know how to carry out these "hacks"?

Any help would be much appreciated.

Many thanks,

Alex

PS - other than that, the Sony Vaio PCG-TT2 works extremely well under Ubuntu Jaunty (64-bit) - video/sound/wifi/ethernet all are fine.

PPS Not sure if any of this is useful:

```
alex@alex-minilaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
alex@alex-minilaptop:~$ lsmod
Module                  Size  Used by
usbhid                 47040  0 
i915                   75400  2 
drm                   123232  3 i915
binfmt_misc            18572  1 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
joydev                 20864  0 
ppdev                  16776  0 
parport_pc             45096  0 
lp                     19588  0 
parport                49712  3 ppdev,parport_pc,lp
pcmcia                 47640  0 
snd_hda_intel         545716  3 
snd_pcm_oss            52224  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                98952  2 snd_hda_intel,snd_pcm_oss
pcspkr                 11136  0 
snd_seq_dummy          11524  0 
arc4                   10240  2 
yenta_socket           35596  1 
rsrc_nonstatic         19584  1 yenta_socket
psmouse                64284  0 
serio_raw              14468  0 
snd_seq_oss            41856  0 
pcmcia_core            49188  3 pcmcia,yenta_socket,rsrc_nonstatic
ecb                    11392  2 
sdhci_pci              16896  0 
sdhci                  27268  1 sdhci_pci
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66144  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               21712  0 
iwlagn                115332  0 
iwlcore               106752  1 iwlagn
iTCO_vendor_support    12420  1 iTCO_wdt
uvcvideo               69512  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
led_class              13064  1 iwlcore
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
mac80211              251400  2 iwlagn,iwlcore
cfg80211               43168  3 iwlagn,iwlcore,mac80211
sony_laptop            46000  0 
video                  29332  0 
output                 11648  1 video
tpm_infineon           18748  0 
tpm                    25920  1 tpm_infineon
tpm_bios               15360  1 tpm
intel_agp              39536  1 
ohci1394               42036  0 
ieee1394              108416  1 ohci1394
ehci_hcd               49676  0 
uhci_hcd               34464  0 
e1000e                137264  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
fuse                   67392  3 
alex@alex-minilaptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 05ca:18b1 Ricoh Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 147e:1000  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
alex@alex-minilaptop:~$ 
```

When I use the hardware "kill switch" for wifi (on and off), I see this output:

On "off":
```
[ 1043.167937] iwlagn: Radio Frequency Kill Switch is On:
[ 1043.167942] Kill switch must be turned off for wireless networking to work.
[ 1043.168879] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 1046.771757] wlan0: disassociating by local choice (reason=3)
[ 1046.809193] iwlagn: Error sending REPLY_WEPKEY: enqueue_hcmd failed: -5
[ 1046.809207] mac80211-phy0: failed to remove key (0, ff:ff:ff:ff:ff:ff) from hardware (-5)
```

On "on":
```
[ 1073.601185] Registered led device: iwl-phy0:radio
[ 1073.601234] Registered led device: iwl-phy0:assoc
[ 1073.601271] Registered led device: iwl-phy0:RX
[ 1073.607837] Registered led device: iwl-phy0:TX
[ 1073.624576] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1073.678824] wlan0: direct probe to AP 02:18:f6:09:94:24 try 1
[ 1073.704000] wlan0 direct probe responded
[ 1073.704017] wlan0: authenticate with AP 02:18:f6:09:94:24
[ 1073.705843] wlan0: authenticated
[ 1073.705850] wlan0: associate with AP 02:18:f6:09:94:24
[ 1073.711385] wlan0: RX AssocResp from 02:18:f6:09:94:24 (capab=0x401 status=0 aid=1)
[ 1073.711392] wlan0: associated
[ 1073.743323] phy0: failed to restore operational channel after scan
[ 1073.743579] wlan0: disassociating by local choice (reason=3)
```

I dont see any sign at all of any sort of modem here, or even a unrecognised device!

In Windows, if I query the modem I get this:

```
ATQ0V1E0 - OK
AT+GMM - GTM382
AT+FCLASS=? - +FCLASS: (0-1)
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - COMMAND NOT SUPPORTED
AT+GCI=? - COMMAND NOT SUPPORTED
ATI1 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI2 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI3 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI4 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI5 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI6 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
ATI7 - Manufacturer: Option N.V.
       Model: GTM382
       Revision: 1.4.3.0Hd (Date: Aug 18 2008, Time: 16:45:58)
```

NB Bug #Bug #343235 filed - not 100% sure that this is the right thing to do, hope so.

---

### Post by anttu on 2009-07-25
I am challenged with the same problem with Acer Aspire A531 having GTM382 embedded. 

It would be really cool to get this working with Ubuntu. Now I need to boot to Vista side  every time I need to use 3G. :cry:

---

### Post by GeorgeVita on 2009-08-03
Hi **alex.davies** and **anttu**,
searching your links found that this is an internal card. Can you check if there is any h/w (physical) switch or any enable flag via BIOS because as you can see it is not listed at all!

Can you check **lsusb** and **sudo lshw** and **lspci** after 'enabling' it (if found)?

Regards,
George

---

### Post by anttu on 2009-08-04
Thanks George for somewhat catching the ball!

This is a PCI Express Mini card, to my understanding used pretty much like a USB device.

Here is what I get with lsusb: (the card is shown as "Option", I think)

anttu@atu-mini:~$ lsusb 
Bus 001 Device 003: ID 0af0:7601 Option 
Bus 001 Device 002: ID 0c45:6310 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

And in dmesg I think this is about the Option:

anttu@atu-mini:~$ dmesg |grep "usb 1" 
[    3.433043] usb 1-1: new high speed USB device using ehci_hcd and  address 2 
[    3.619079] usb 1-1: configuration #1 chosen from 1 choice 
[    3.732631] usb 1-6: new high speed USB device using ehci_hcd and  address 3 
[    3.875388] usb 1-6: configuration #1 chosen from 1 choice 

There is no usbserial stuff seen in dmesg as there typically is with a working modem.

There is a switch named "3G" for the modem, but it really does nothing else but turns on and off the "3G" LED. This is shown in dmesg:

[  663.477076] atkbd.c: Unknown key pressed (translated set 2, code 0xba  on isa0060/serio0). 
[  663.477086] atkbd.c: Use 'setkeycodes e03a <keycode>' to make it known. 
[  663.483781] atkbd.c: Unknown key released (translated set 2, code  0xba on isa0060/serio0). 
[  663.483791] atkbd.c: Use 'setkeycodes e03a <keycode>' to make it known. 


A bit off-topic:
The similar WLAN switch shows the log:

[  728.275822] atkbd.c: Unknown key pressed (translated set 2, code 0xc4  on isa0060/serio0). 
[  728.275841] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known. 
[  728.282471] atkbd.c: Unknown key released (translated set 2, code  0xc4 on isa0060/serio0). 
[  728.282489] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known. 

This switch really does turn the WLAN on and off, but the LED stays dark. Any idea how to make the LED work with the switch?

---

### Post by GeorgeVita on 2009-08-04
Hi **anttu**,
your modem seems to be **0af0:7601 Option**

**>>> EDIT <<<**
try: **sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**
search into this file for **af0** and some lines below for **7601**
(above data exist into my 9.04 updated file)

Also have you tried usbserial?
```
sudo modprobe usbserial vendor=0x0af0 product=0x7601
```

and check **dmesg** for any /dev/ttyUSBx port created?

Regards,
George

---

### Post by anttu on 2009-08-05
Thanks!

I did the modprobe thing and the tty's were attached to the generic converter. 

Then, to my disappointment the system keeps pumping the ports down and up again, and trying to make the connection with NWM responds just with "GSM disconnected".

Here is the dmesg:
```
[  126.308498] usbcore: registered new interface driver usbserial 
[  126.308584] USB Serial support registered for generic 
[  126.308693] usbserial_generic 1-6:1.1: generic converter detected 
[  126.308953] usb 1-6: generic converter now attached to ttyUSB0 
[  126.308990] usbserial_generic 1-6:1.2: generic converter detected 
[  126.309207] usb 1-6: generic converter now attached to ttyUSB1 
[  126.309245] usbserial_generic 1-6:1.4: generic converter detected 
[  126.309451] usb 1-6: generic converter now attached to ttyUSB2 
[  126.309487] usbserial_generic 1-6:1.5: generic converter detected 
[  126.309706] usb 1-6: generic converter now attached to ttyUSB3 
[  126.309745] usbserial_generic 1-6:1.8: generic converter detected 
[  126.309954] usb 1-6: generic converter now attached to ttyUSB4 
[  126.310250] usbcore: registered new interface driver usbserial_generic 
[  126.310264] usbserial: USB Serial Driver core 
[  127.383814] wlan0: authenticate with AP f64526b8 
[  127.385800] wlan0: authenticated 
[  127.385809] wlan0: associate with AP f64526b8 
[  127.387926] wlan0: RX ReassocResp from f35e308a (capab=0x401 status=0  aid=2) 
[  127.387935] wlan0: associated 
[  149.053083] usb 1-6: USB disconnect, address 3 
[  149.054876] generic ttyUSB0: generic converter now disconnected from  ttyUSB0 
[  149.054959] usbserial_generic 1-6:1.1: device disconnected 
[  149.059399] generic ttyUSB1: generic converter now disconnected from  ttyUSB1 
[  149.059482] usbserial_generic 1-6:1.2: device disconnected 
[  149.063933] generic ttyUSB2: generic converter now disconnected from  ttyUSB2 
[  149.065619] usbserial_generic 1-6:1.4: device disconnected 
[  149.066567] generic ttyUSB3: generic converter now disconnected from  ttyUSB3 
[  149.066657] usbserial_generic 1-6:1.5: device disconnected 
[  149.124441] generic ttyUSB4: generic converter now disconnected from  ttyUSB4 
[  149.124515] usbserial_generic 1-6:1.8: device disconnected 
[  153.892129] usb 1-6: new high speed USB device using ehci_hcd and  address 4 
[  154.035466] usb 1-6: configuration #1 chosen from 1 choice 
[  154.042319] usbserial_generic 1-6:1.1: generic converter detected 
[  154.042723] usb 1-6: generic converter now attached to ttyUSB0 
[  154.101848] usbserial_generic 1-6:1.2: generic converter detected 
[  154.102190] usb 1-6: generic converter now attached to ttyUSB1 
[  154.112422] usbserial_generic 1-6:1.4: generic converter detected 
[  154.112745] usb 1-6: generic converter now attached to ttyUSB2 
[  154.118619] usbserial_generic 1-6:1.5: generic converter detected 
[  154.118938] usb 1-6: generic converter now attached to ttyUSB3 
[  154.131090] hso0: Disabled Privacy Extensions 
[  154.137367] usbserial_generic 1-6:1.8: generic converter detected 
[  154.137689] usb 1-6: generic converter now attached to ttyUSB4 
[  217.644382] usb 1-6: USB disconnect, address 4 
...

```

---

### Post by GeorgeVita on 2009-08-05
Can you check also if data 0af0:7601 exist into HAL definition file:> try: sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
search into this file for af0 and some lines below for 7601
(above data exist into my 9.04 updated file)

Post here all lines regarding **7601** (if any).

G

---

### Post by anttu on 2009-08-05
Here you are:
```
        <match key="@info.parent:usb.product_id" int="0x7601">
          <match key="@info.parent:usb.interface.number" int="6">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
          </match>
        </match>

```

---

### Post by GeorgeVita on 2009-08-05
Hi **anttu**, the funny thing is that the looping creation/disconnection on the ttyUSBx ports is my problem with ZTE MF636 which seems to be present here also!

Possible cause: HAL uses wrong port (...usb.interface.number" int="6") or the loop comes when HAL info conflicts with usbserial or network-manager parameters.

Some ideas for tests:
1. change '...usb.product_id" int="0x7601">' to 0xabcd so HAL will no longer see the modem and try again usbserial
2. try another 'usb.interface.number' like 2,3,4 (I searched internet for more info on this but did not found anything!)

The 'hard' is that you have to shut down, boot again to be sure that modem did a h/w reset (as you cannot disconnect it).

Regards,
George

---

### Post by excogitation on 2009-09-06
Have you made it work?

For me - if I enable the Globetrotter Modem in Win (dual boot setup) and then boot into Ubuntu the Modem shows as

0af0:7601 Option (lsusb)

If it is disabled in Win - it won't show although /sys/devices/platform/sony-laptop/wwanpower shows 1.

---

### Post by quini on 2009-10-19
> **excogitation said:**
> Have you made it work?

For me - if I enable the Globetrotter Modem in Win (dual boot setup) and then boot into Ubuntu the Modem shows as

0af0:7601 Option (lsusb)

If it is disabled in Win - it won't show although /sys/devices/platform/sony-laptop/wwanpower shows 1.

Hi!  I've got a TT11LN (3G modem is called "us 001 Device 004: ID 0af0:7601" by lsusb), and I've noticed that echoing 0 or 1 to /sys/devices/platform/sony-laptop/wwanpower has no effect, as the modem always works.

I've filed [a bug at launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414833"), so feel free to join.

Note: the modem works for me when cold booting -I don't use win at all-; I'm running Karmic beta 64b.

Regards ;)

---

