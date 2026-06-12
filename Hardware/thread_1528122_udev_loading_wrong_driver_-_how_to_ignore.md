---
title: "udev loading wrong driver - how to ignore"
date: 2010-07-10
forum: Hardware
---

### Post by piginabox on 2010-07-10
I've got a dvb-t usb tuner (device 15a4:1001).
udev treats it like a keyboard with usbhid.
i've tried adding a quirks rule as a boot parameter and as a rule in /etc/udev/rules.d/ but to no avail.

lots of the online info relates to pre-lucid and doesn't seem to apply.

what is the best way to specify which driver loads a USB device or at least to tell usbhid to ignore my device?

thanks

---

### Post by efflandt on 2010-07-10
You might take a look at the files in /lib/udev/rules.d especially 70-hid2hci.rules to see if something there is throwing it off.

For example something was changed between 9.10 and 10.04 that broke my Logitech diNovo wireless keyboard/mousepad, and simply commenting out the Logitech section allowed it to work (since it does not need any special drivers, works from BIOS even without any OS loaded).

---

### Post by piginabox on 2010-07-11
Thanks for the reply

In /etc/udev/rules.d I've only got:

10-vboxdrv.rules
70-persistent-cd.rules
70-persistent-net.rules

(after a vanilla 10.04 install yesterday.)

Can you post you 70-hid2hci.rules please?

---

### Post by piginabox on 2010-07-12
ah! /lib/udev and /etc/udev!
/lib/udev for system rules and /etc/udev for user rules (i think)?

---

### Post by piginabox on 2010-07-13
Does anyone know how to load a specific driver for a specific device?
I have all the ATTR info i need from udevadm.

I've tried to get my head round udev and i think my first task is to make the usbhid driver ignore my device.

I've made a /etc/udev/rules.d/10-my.rules which should have precedence over the /lib/udev rules.
I've tried ignoring the device with
ATTRS{serial}=="AF0102020700001", OPTIONS=={ignore_device}
or
ATTRS{serial}=="AF0102020700001", OPTIONS={ignore_device} (this one is correct?)
or
ATTRS{serial}=="AF0102020700001", OPTIONS+={ignore_device}

and then
ATTRS{serial}=="AF0102020700001", OPTIONS+={last_rule}


What am i doing wrong? The device still loads incorrectly as a keyboard and isn't ignored?

---

### Post by piginabox on 2010-07-18
No-one seems to have any knowledge on how to use udev. Bah! I give up.

---

### Post by IcarusR on 2010-07-18
This device being identified as an HID device is common, see this page it has a remody & instructions how to install correct module....

[http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick#General_important_note.21_.281.29__USB_DVB_is_wrongly_identified_as_a_HID_device]("http://linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick#General_important_note.21_.281.29__USB_DVB_is_wrongly_identified_as_a_HID_device")

---

### Post by piginabox on 2010-07-19
works for pre-lucid kernels, though. i'm using the latest ubuntu 10.04.

---

### Post by IcarusR on 2010-07-19
> works for pre-lucid kernels

What makes you say that ? There is nothing saying that in the instructions.

The author says he has used it on kernel 2.6.31 so it ought to work on Lucid.

Have you tried it ?

---

### Post by piginabox on 2010-07-19
Trying again as I probably did mess something up with all the previous changes I'd made.
/etc/modprobe.d/usbhid.conf doesn't work
adding the usbhid.quirks to the boot options has done something. i'll dig more.
cheers for earlier link.

---

### Post by dino99 on 2010-07-19
changing default settings and config is a risky idea

sudo update-usbids && sudo update-pciids
sudo dpkg --configure -a

---

### Post by Clewster on 2010-07-21
Did you get any further with this. i'm having exactly the same issue :(

---

### Post by piginabox on 2010-07-22
I managed to stop the keyboard driver claiming it by changing /etc/default/grub
I think the default GRUB_CMDLINE_LINUX_DEFAULT is "quiet splash".
I changed it to
GRUB_CMDLINE_LINUX_DEFAULT="usbhid.quirks=0x15a4:0x1001:0x0004"
I then ran
> sudo update-grub
(something i probably failed to do first time around).

My DVB-T device in dmesg now showed up as being in a warm state. I couldn't get any further than that.

What USB device is it that you have? 15a4:1001? (lsusb)


P.S. usbhid.quirks=0x15a4:0x1001:0x0004 is usbhid.quirks=0x"YOUR VENDOR ID":0x"YOUR DEVICE ID":0x0004

---

### Post by Clewster on 2010-07-22
Yes my device is the same 15a4:1001
Done the grub bit but the DVB-T is listed slightly different


```
[ 5613.069250] usb 1-1: USB disconnect, address 11
[ 5618.353051] usb 1-1: new high speed USB device using ehci_hcd and address 12
[ 5618.504207] usb 1-1: configuration #1 chosen from 1 choice
```

I have prob screwed something up trying various other things so think ill just set off a rebuild. ill let you know if anything changes

---

### Post by piginabox on 2010-07-22
cheers,
I'm going to try fresh 10.04 and then 9.10 over the weekend. I'll let you know how i do.
What firmware did you put in /lib/firmware?
Linuxtv suggests dvb-usb-wt220-01 and dvb-usb-wt220-01 for one 15a4:1001 device.

---

### Post by Clewster on 2010-07-22
firmware downloaded from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw)
but i dont think im that far yet because im sure i would get firmware error in dmesg :(

strange thing is even with the grub quirks usbhid is still loading when the device is plugged in it just doesn't give it a driver. I have played round with udev rules but its happening before udev kicks in and creating /etc/modprobe.d/usbhid.conf with options usbhid quirks=0x15a4:0x1001:0x0004 doesnt seem to have any affect.
Machine almost built so hopefully ill get to post back assuming the kids leave me to it

---

### Post by piginabox on 2010-07-22
i could only get the quirks to work by editing /etc/default/grub
i changed the default boot command from "quiet splash" to
"usbhid.quirks=0x15a4:0x1001:0x0004"
save it and remember to run
sudo update-grub
before rebooting

---

### Post by Clewster on 2010-07-22
Without modifying anything in 10.04
> [  267.033112] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  267.200991] usb 1-1: configuration #1 chosen from 1 choice
[  267.369210] usbcore: registered new interface driver hiddev
[  267.391285] input: TBS Technologies Inc. TBS-DTB05 as /devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.1/input/input4
[  267.394078] generic-usb 0003:15A4:1001.0001: input,hidraw0: USB HID v1.01 Keyboard [TBS Technologies Inc. TBS-DTB05] on usb-0000:02:03.0-1/input1
[  267.394371] usbcore: registered new interface driver usbhid
[  267.395800] usbhid: v2.6:USB HID core driver

with usbhid.quirks=0x15a4.0x1001:0x0004 in /etc/default/grub, sudo update-grub and reboot


> [   58.016460] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   58.173458] usb 1-1: configuration #1 chosen from 1 choice
[   58.259259] usbcore: registered new interface driver hiddev
[   58.265460] usbcore: registered new interface driver usbhid
[   58.267270] usbhid: v2.6:USB HID core driver

---

### Post by piginabox on 2010-07-23
here's the firmware i've been sticking in /lib/firmware

[attached]

---

### Post by Clewster on 2010-07-23
after some more playing today which has been a total waste of time until now i decided to pop the case of my USB DVB-T device and interestingly enough its actually AF9035 chip and not the AF9015 chip both windows and Linux seem to think it is. If your still having issues it may be worth popping the top off just to check the chips

---

### Post by Clewster on 2010-07-23
Ive got mine all working now. Like i said even though the product code was the same as yours and it was reporting as AF9015 in both windows and Linux the chip is actually AF9035.
if you or anyone else is having problems setting AF9035 up let me know and ill write something up.

---

### Post by dmm1000 on 2011-03-13
hi clewster 
i'd be grateful if you could write something up ive managed to get rid of the HID conflict and this is what im getting now in dmesg output

  281.260028] usb 2-4: new high speed USB device using ehci_hcd and address 7

using the Wand Tv as sold by dealextreme

HELP !! (anyone) :)

---

