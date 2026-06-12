---
title: "Ubuntu Server 11.10 Always Failed to Recognize USB Device"
date: 2011-11-11
forum: Hardware
---

### Post by robson9776 on 2011-11-11
Hi,

I have a new PC with Ubuntu Server 11.10 previously installed, then after it cannot detect my Huawei 3G Modem, I decided to use Ubuntu Desktop 11.10. and my modem is perfectly recognized as /dev/ttyUSB0 when I ran this command :

$ dmesg | grep tty

my question is... what makes Ubuntu Server can't detect USB Modem and what package should I install to make it works like Ubuntu Desktop in terms of USB detection feature. because I don't need Libre Office or even Gnome to be installed. I just need Ubuntu Server with USB detection capabilities.

thanks.

---

### Post by northd_tech on 2011-11-11
Can you open a terminal (either by pressing Ctrl-Alt-T or going into Applications > Accessories > Terminal) and copy/paste the results when you run these terminal commands from the working Ubuntu 11.10 Desktop system:

```
lsusb
lsmod
```

---

### Post by robson9776 on 2011-11-12
here's from 'lsmod' command :

> Module                  Size  Used by
cdc_ether              13312  0 
option                 21205  0 
usb_wwan               19779  1 option
usbserial              37203  2 option,usb_wwan
usbnet                 25214  1 cdc_ether
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
usbhid                 41905  0 
usb_storage            44173  0 
uas                    17699  0 
hid                    77367  1 usbhid
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               663211  2 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
drm                   192226  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
shpchp                 32356  0 
mei                    36466  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
xhci_hcd               72915  0

and here's from 'lsusb' command :

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 004 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd. 

---

### Post by northd_tech on 2011-11-12
> **robson9776 said:**
> **lsmod**
**Module                  Size  Used by**
[COLOR=Green]**cdc_ether**[/COLOR]              13312  0 
**option**                 21205  0 
**usb_wwan**               19779  1 **option**
usbserial              37203  2 option,**usb_wwan**
[COLOR=Green]**usbnet**[/COLOR]                 25214  1 [COLOR=Green]**cdc_ether**[/COLOR]
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep


I believe that the above bolded modules are probably all used for that USB 3G modem (although I haven't ever worked on one of those personally).

Also, this is how your Huawei 3G modem is reported on the USB bus:
> 
**lsusb**:
Bus 005 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd.


Let's see how that USB address is translated into an Ubuntu 'device'- can you also cut/paste the results of these terminal commands:

```
ls /dev/bus/usb/

ls /dev/bus/usb/005/

ls -l /dev/bus/usb/005/004

```

Here are a few threads that appear to be applicable to your Huawei 'E173" device with ID: "12d1:1436" currently located on USB Bus #005 Device #004:

[http://ubuntuforums.org/tags.php?tag=huawei+e173](http://ubuntuforums.org/tags.php?tag=huawei+e173)

this looks to be the better of those to me:
[http://ubuntuforums.org/showthread.php?t=1741762](http://ubuntuforums.org/showthread.php?t=1741762)

Although these might not apply to your specific Huawei hardware, here are Huawei 3G threads that might have something helpful:

[http://ubuntuforums.org/tags.php?tag=huawei+3g](http://ubuntuforums.org/tags.php?tag=huawei+3g)

---

### Post by robson9776 on 2011-11-12
there you go, bro... I really appreciate what you're doing to me. although I'm still figuring out what you're trying to do... because I have bad experience dealing with linux driver / module since Red Hat 6.0, hopefully I will find some enlightenment with Ubuntu from you.

> $ ls /dev/bus/usb/
001  002  003  004  005  006  007  008  009  010  011  012  013

> $ ls /dev/bus/usb/005/
001  004


> $ ls -l /dev/bus/usb/005/004
crw-rw-r-- 1 root root 189, 515 Nov 12 05:07 /dev/bus/usb/005/004

---

### Post by northd_tech on 2011-11-12
I missed this before- your Huawei is showing up as 3 devices on 3 USB buses:
> **robson9776 said:**
> 
Bus 003 Device 003: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 004 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 005 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd.                      

I really do not know if that is a normal setup for that Huawei 3G device.  An earlier **lsusb** command told us that those buses are:

> Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubI was guessing that those would be USB root hubs with different speeds (USB 1.x to 3.0 maybe), but they ALL appear to be USB 2.0 hubs here- that seems strange to me.

My understanding is that Device 001 will be the USB port/hub itself and will always show up whether any USB device is connected or not, whereas your Huawei 3G WWAN modem is currently showing up as Device(s) 003 & 004 on the respective USB Bus (003 through 005 in this case).

Looking at that 'better?' thread, there are a few more diagnostics to run:

```
ls -la /dev/ttyUSB*

usb-devices

nm-tool

egrep -v '#|^ *$' /etc/ppp/options

```Then you could try installing Sakis3G as recommended in post #5 on that thread:

> What Sakis3G is?       
Sakis3G is a tweaked shell script which is supposed to work out-of-the-box for establishing a 3G connection with any combination of modem or operator.   It **automagically** setups your USB or Bluetooth&#8482; modem, and may even detect operator settings. You should try it when anything else fails! [http://www.sakis3g.org/](http://www.sakis3g.org/)

Then you could try the send & receive terminal stuff from post #8 onward;
[http://ubuntuforums.org/showpost.php?p=10745034&postcount=8](http://ubuntuforums.org/showpost.php?p=10745034&postcount=8)

Unfortunately, it does not sound like Lars Nooden was able to get anything better than intermittent results (and it sounds like Mac OS X was the best choice for that device).

That pretty well exhausts what I've been able to read/learn so far about Huawei 3G WWAN devices though.

Also, 13 seems like a LOT of USB Buses to me, but maybe that's how the 'new' USB 3.0 wants to do things and is normal.  My USB 2.0 setup only sees 4 buses though (2 at each speed):

> **ls /dev/bus/usb/**
001  002  003  004

** lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Although I don't expect it to help, here is how my working external USB HDD shows up (under USB 2.0):

> **lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 002: ID 18a5:0216 ** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**ls -la /dev/bus/usb/001/**
total 0
drwxr-xr-x 2 root root     80 2011-11-12 08:56 .
drwxr-xr-x 6 root root    120 2011-11-12 00:35 ..
crw-rw-r-- 1 root root 189, 0 2011-11-12 07:36 001
**crw-rw-r-- 1 root root 189, 1 2011-11-12 08:56 002**
At this point, I'm suspecting something in those kernel driver modules, but I really don't know what you need for a 'working' setup there.  Have you considered contacting alexfish from that thread I linked above or running his script at post #19?

[http://ubuntuforums.org/showpost.php?p=10751248&postcount=19](http://ubuntuforums.org/showpost.php?p=10751248&postcount=19)

---

