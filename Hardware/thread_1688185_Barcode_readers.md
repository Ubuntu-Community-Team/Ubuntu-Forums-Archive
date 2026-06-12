---
title: "Barcode readers"
date: 2011-02-15
forum: Hardware
---

### Post by arimaniac on 2011-02-15
Hello there..

I have purchased a Cypress barcode reader...
I have tested it under Windows XP and works out of the box.
 
Now I NEED to get it running on my Ubuntu 10.04 box and it does not. I get the following on dmesg:
```

[ 2131.280305] usb 7-2: new low speed USB device using uhci_hcd and address 8
[ 2131.505808] usb 7-2: configuration #1 chosen from 1 choice
[ 2131.535800] generic-usb: probe of 0003:04B4:BCA1.0009 failed with error -22

```
I understand that this error comes from module: usbhid .. 
And ubuntu 10.04 lacks module usbkbd to switch to it... .   

the device details.... lsusb -v
```

Bus 007 Device 008: ID 04b4:bca1 Cypress Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0xbca1 
  bcdDevice            2.52
  iManufacturer           1 Guest
  iProduct                2 Barcode Reader
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Barcode Reader
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              5 EP1
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      64
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```
 lsmod
```

Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
vboxnetadp              6326  0 
vboxnetflt             15344  0 
vboxdrv               190370  2 vboxnetadp,vboxnetflt
btusb                  10957  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_atihdmi     2367  1 
joydev                  8740  0 
snd_hda_codec_idt      52010  1 
snd_hda_intel          22005  2 
arc4                    1153  2 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
usbhid                 36110  0 
iwlagn                106815  0 
dell_wmi                1793  0 
iwlcore               106050  1 iwlagn
uvcvideo               57310  0 
snd_pcm                70694  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
hid                    67064  1 usbhid
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
mac80211              205402  2 iwlagn,iwlcore
videodev               34361  1 uvcvideo
fglrx                2092908  29 
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6856  0 
v4l1_compat            13251  2 uvcvideo,videodev
dcdbas                  5422  1 dell_laptop
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  2 iwlcore,sdhci
video                  17375  0 
output                  1871  1 video
vga16fb                11385  1 
cfg80211              126528  3 iwlagn,iwlcore,mac80211
intel_agp              24375  0 
vgastate                8961  1 vga16fb
agpgart                31724  2 fglrx,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
tg3                   109324  0 
ahci                   32200  2 

```

my ubuntu version:
```

Linux arimaniac-laptop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

```

PLEASE HELP.. any ideas?
thank you

---

### Post by arimaniac on 2011-02-15
nobody knows nothing?

I tried on my old opensuse 11 box... dmesg: 
```

usb 2-1: new full speed USB device using ohci_hcd and address 4
usb 2-1: configuration #1 chosen from 1 choice
usb 2-1: New USB device found, idVendor=04b4, idProduct=bca1
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 2-1: Product: Barcode Reader
usb 2-1: Manufacturer: Guest

```
but still not working... 

WHY was the usbkbd module removed from linux if the its replacement does  not work properly...  AND COME ON... ITS JUST A SIMPLE BARCODE READER... nothing more than a serial device....  :(:(  

ok is it possible to:
configure the usbhid kernel module..?
maybe tweak the driver to read the device?

HOW CAN I READ RAW DATA from the usb bus?
(there is no device in /dev though) 
I already tried loading the usbmon module... and cat the /sys/kernel/debug/usb/usbmon directory...
NOTHING but the usb mouse traffic....

come on man .... anybody?
please any ideas??????????????????? anything....

---

### Post by tgalati4 on 2011-02-15
Here's a long shot.  In the BIOS on the computer, did you set: "Enable legacy USB keyboard support"?

While troubleshooting something else, I found the usbkbd has been blacklisted in:

/etc/modprobe.d/blacklist.conf

Try removing the blacklist so that it loads the module properly.  This was done because of a substitution of the HID (Human Interface Device, I presume) module.

So much for progress.  Move forward, break stuff.

---

### Post by arimaniac on 2011-02-16
Hello..

yes the usb legacy option is enabled, and the module usbkbd is not blacklisted... but the latter would not make any difference as it the module is not present in the kernel... it was removed a couple of years ago... :(:(:(:(:(:(
I have tested the barcode reader on gentoo linux (sabayon LIVE cd) and works out of the box... 

lsmod on sabayon shows that the usbhid module is not present...
(but neither the usbkbd)

any more suggestions...???
compiling the usbkbd module? ???????????????

---

### Post by arimaniac on 2011-02-16
solution at :

[http://ubuntuforums.org/showthread.php?t=1689031](http://ubuntuforums.org/showthread.php?t=1689031)

---

