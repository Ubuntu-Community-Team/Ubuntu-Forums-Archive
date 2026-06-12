---
title: "USB TV Tuner not on after boot (unplug works)?"
date: 2009-08-06
forum: Hardware
---

### Post by lindsayward on 2009-08-06
Hi there.
I have an Artec T14BR USB TV Tuner that works just fine if I plug it in after I boot up, but the little power light on it is off when I first boot up and mythTV can't use it. 
I've looked for a couple of hours and the best I can find is this thread ([http://ubuntuforums.org/archive/index.php/t-898939.html](http://ubuntuforums.org/archive/index.php/t-898939.html)) that says to try disabling ehci_hcd, but I don't seem to have that module installed.

After boot:
lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
(nothing)

Here is my dmesg|grep usb (part of):
```
[    4.916564] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    5.108513] usb 3-3: device descriptor read/64, error -62
[    5.412531] usb 3-3: device descriptor read/64, error -62
[    5.692019] usb 3-3: new full speed USB device using ohci_hcd and address 3
[    5.872017] usb 3-3: device descriptor read/64, error -62
[    6.156015] usb 3-3: device descriptor read/64, error -62
[    6.436014] usb 3-3: new full speed USB device using ohci_hcd and address 4
[    6.844013] usb 3-3: device not accepting address 4, error -62
[    7.020013] usb 3-3: new full speed USB device using ohci_hcd and address 5
[    7.428011] usb 3-3: device not accepting address 5, error -62
[   19.752011] usb 3-3: new full speed USB device using ohci_hcd and address 6
```

When I unplug then plug the tuner in again:

dmesg:
```
[ 1609.168018] usb 3-3: new full speed USB device using ohci_hcd and address 17
[ 1609.576018] usb 3-3: device not accepting address 17, error -62
[ 1609.576028] hub 3-0:1.0: unable to enumerate USB device on port 3
[ 1666.344017] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 1666.477323] usb 1-3: configuration #1 chosen from 1 choice
[ 1667.084966] dib0700: loaded with support for 8 different device-types
[ 1667.085115] dvb-usb: found a 'Artec T14BR DVB-T' in cold state, will try to load a firmware
[ 1667.085119] usb 1-3: firmware: requesting dvb-usb-dib0700-1.20.fw
[ 1667.119425] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 1669.587347] dib0700: firmware started successfully.
[ 1670.088029] dvb-usb: found a 'Artec T14BR DVB-T' in warm state.
[ 1670.088074] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 1670.088310] DVB: registering new adapter (Artec T14BR DVB-T)
[ 1670.293848] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[ 1670.464095] DiB0070: successfully identified
[ 1670.464190] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.1/usb1/1-3/input/input7
[ 1670.466577] dvb-usb: schedule remote query interval to 50 msecs.
[ 1670.466582] dvb-usb: Artec T14BR DVB-T successfully initialized and connected.
[ 1670.466744] usbcore: registered new interface driver dvb_usb_dib0700
```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05d8:810f Ultima Electronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I'm using ubuntu 9.04
uname -r
2.6.28-14-generic

lsmod | grep hci
gives nothing

When I tried what was suggested as the main 'fix', this is what I get:
modprobe -r ehci_hcd
FATAL: Module ehci_hcd not found.

My motherboard is a DFI Lanparty-Jr 9400 (nVidia 9400 chipset).

I have searched for most of the error messages I read here and get lots of hits but really no results. I don't know what else to try. I would really appreciate some help - thank you!

---

### Post by lindsayward on 2009-08-06
I should add that it works fine in Vista. If I boot into Vista and run the poxy TV program that came with the card, the light comes on on the card and I can watch TV.

Thanks?

---

### Post by lindsayward on 2009-08-11
Hi. Am I asking in the wrong place? I don't seem to get responses to my posts...
Is there a better forum for asking ubuntu questions?
I've tried to list all the information I can about the issue - is there something more I should do or provide?
Thank you.

---

### Post by lindsayward on 2009-08-13
bump - is there a better place for questions like these?

---

### Post by lindsayward on 2009-08-17
I guess the silence answers one of my questions. I might try the LinuxQuestions forum...

---

### Post by caish5 on 2009-08-17
Answers for that sort of hardware are always a little tricky.
I've solved problems in the past at linuxtv.org

---

### Post by rarsa on 2009-10-07
Actually the silence confirms that there is little information about this error. I have a laptop with this error 

"5.872017] usb 3-3: device descriptor read/64, error -62"

and I have been searching for information for a long time. I am sure it was caused by a kernel upgrade but I cannot pinpoint it.

Meanwhile I changed the USB device I am using (in my case a wireless dongle) for a PCMCI card. i.e. no technical solutino but a workaround.

---

### Post by Emilianio on 2010-02-23
Hi, 

I can confirm this problem on pegatron ipx7a with nv 9400 chipset and dvb-t03 tuner. 
uname -r
2.6.31-20-generic-pae

unplug and plug is the only solution that i found

---

### Post by jayeff_69 on 2010-04-01
I have this problem too and would like a solution. I'm using a Gigabyte U7000 attached to a Slave Backend and works perfectly if I unplug and replug but isn't recognised upon reboot. Would like a solution as I've removed the Video source at the moment.

---

### Post by Jose Catre-Vandis on 2010-06-12
I'll join  in with this one too.

I have a media centre set up with XBMC live (Ubuntu 9.04/10) (but the problem existed in XP and W7 too) so I think it may be hardware related.

Using the same usb dvb stick (PEAK Afatech af9015) on a newer machine and kernel doesn't cause a problem and the stick works through cold boots.

So, for me, If Pc is off, I can unplug the stick, plug it back in and it will be there when I boot (cold state). The stick stays with me if I reboot (warm state). If I shut down, and then restart the stick is not there (lsusb) but if I unplug and plug it back in, it comes to life (cold state).

I have tried playing with power settings in /sys/bus/usb/devices/"device"/power/ for both the device and the underlying usb port but these all reset on cold boot. Interestingly (?) when the stick is recognised, you can turn it on and off using the power level settings, but you do need to be proper root to do it) So it seems like the stick needs to completely power off in order to be recognised from cold boot, but never gets de-initialised / disconnected "completely" on a reboot (even though dmesg says it does).

---

### Post by HandeH on 2011-05-12
I have also a buggy afatech af9015 dvb tuner, that forces me to shutdown the computer every now and then. I'd be happy to find a remedy.

---

