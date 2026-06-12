---
title: "Touchpad not working on HP Pavilion X2 12"
date: 2016-05-06
forum: Hardware
---

### Post by Imerion on 2016-05-06
Hello everyone! Was a long time since I posted here. :)

I recently bought an HP Pavilion X2 12 ([http://store.hp.com/UKStore/Merch/Product.aspx?id=T1E48EA&opt=ABU&sel=NTB](http://store.hp.com/UKStore/Merch/Product.aspx?id=T1E48EA&opt=ABU&sel=NTB))

I installed Ubuntu Gnome 16.04 and all hardware worked perfectly out of the box, but not my touchpad. Even touchscreen worked, but not the touchpad.

Xinput doesn't list the device :
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HP Pro 10 EE G1 Keyboard Base           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ELAN2285:00 04F3:2285                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ELAN2285:00 04F3:2285 Pen               	id=13	[slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP TrueVision HD                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)]
    &#8627; HP Pro 10 EE G1 Keyboard Base           	id=16	[slave  keyboard (3)]


And in the boot log I find this :

> [    2.440927] hid-rmi 0003:06CB:7D29.0001: rmi_scan_pdt: Done with PDT scan.
[    2.453918] hid-rmi 0003:06CB:7D29.0001: No 2D sensor found, giving up.
[    2.453919] hid-rmi 0003:06CB:7D29.0001: Error while initializing F11 (-19).
[    2.456476] hid-rmi 0003:06CB:7D29.0001: hiddev0,hidraw0: USB HID v1.11 Mouse [SYNAPTICS Synaptics HIDUSB TouchPad V03] on usb-0000:00:14.0-2.1/input0
[    2.456478] hid-rmi 0003:06CB:7D29.0001: Device failed to be properly configured


I have tried upgrading the the latest kernel, but that didn't help. Any idea what might be causing this?

Somewhere someone suggested the touchpad was switched off at boot. But how would I turn it on?

Any help would be highly appreciated! Thanks!

---

### Post by conch on 2016-05-06
Hi I have the same problem, looking at dmesg below it looks as though the problem is with the hd-rmi driver.


2.296276] usb 1-2.1: new full-speed USB device number 4 using xhci_hcd
[    2.387323] usb 1-2.1: New USB device found, idVendor=06cb, idProduct=7d29
[    2.387324] usb 1-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.387326] usb 1-2.1: Product: Synaptics HIDUSB TouchPad V03
[    2.387326] usb 1-2.1: Manufacturer: SYNAPTICS
[    2.391645] usbcore: registered new interface driver usbhid
[    2.391645] usbhid: USB HID core driver
[    2.450345] hid-rmi 0003:06CB:7D29.0001: Scanning PDT...
[    2.452347] hid-rmi 0003:06CB:7D29.0001: Found F34 on page 0x00
[    2.454340] hid-rmi 0003:06CB:7D29.0001: Found F01 on page 0x00
[    2.456231] hid-rmi 0003:06CB:7D29.0001: Found F12 on page 0x00
[    2.461212] hid-rmi 0003:06CB:7D29.0001: Found F54 on page 0x01
[    2.466349] hid-rmi 0003:06CB:7D29.0001: Found F30 on page 0x02
[    2.471223] hid-rmi 0003:06CB:7D29.0001: Found F55 on page 0x03
[    2.476228] hid-rmi 0003:06CB:7D29.0001: Found F51 on page 0x04
[    2.481221] hid-rmi 0003:06CB:7D29.0001: rmi_scan_pdt: Done with PDT scan.
[    2.494226] hid-rmi 0003:06CB:7D29.0001: No 2D sensor found, giving up.
[    2.494228] hid-rmi 0003:06CB:7D29.0001: Error while initializing F11 (-19).
[    2.496565] hid-rmi 0003:06CB:7D29.0001: hiddev0,hidraw0: USB HID v1.11 Mouse [SYNAPTICS Synaptics HIDUSB TouchPad V03] on usb-0000:00:14.0-2.1/
input0
[    2.496567] hid-rmi 0003:06CB:7D29.0001: Device failed to be properly configured

---

### Post by Imerion on 2016-05-07
I tried upgrading the kernel to 4.5 and 4.6RC6, but none of these helped. Can that driver be replaced or exchanged somehow?

I was curious about if installing without UEFI would help. The BIOS does have a Legacy Mode, so it should be possible to install without UEFI. But I have no idea if that would help. Booting a USB-disk of Gnome Ubuntu 16.04 in legacy mode did not help.

I also found this : [https://alpha-labs.net/2015/08/lenovo-s21e-linux-and-the-touchpad/](https://alpha-labs.net/2015/08/lenovo-s21e-linux-and-the-touchpad/)

The last comments seem to indicate problems with new kernels as well. Perhaps that patch could be used somehow? But I have no idea if it's the same hid driver.

I found a tip to try using hid-generic instead. This could be done like this :

To force hid-generic, remove hid-rmi, load hid-generic and run:
echo echo 3 06cb a001 0 | sudo tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id

Not sure how to remove hid-rmi och lod hid-generic instead though. Anyone who knows?

OMG! I figured this out! I hope this will help you too conch. Here is what I did :

1. sudo gedit /etc/modules
2. Add "hid_generic" at the bottom of that file.
3. Save and close.

4. sudo gedit /etc/modprobe.d/blacklist.conf
5. Add "blacklist hid_rmi" at the bottom of that file.
6. Save and close.

7. sudo echo 3 06cb 7d29 1 | sudo tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id

The numbers above correspond to the dmesg output. We seem to have the same. This will load and use the less advanced hid-generic instead of hid_rmi. It won't handle gestures and such, but for me that is ok. All I need is move, click and scroll. :)

Hopefully a future update will fix hid_rmi for this device too, allowing more advanced functions.

Oh, and to make the change permanent I did this :

1. sudo gedit /etc/rc.local
2. Add the line "echo 3 06cb 7d29 1 | tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id"
3. sudo chmod 755 /etc/rc.local

Now it works after every boot. :)

---

### Post by conch on 2016-05-12
Hi Imerion,

Excellent work, many thanks!

It works for me too!

---

### Post by Imerion on 2016-05-26
Oh, and if anyone else is reading this. You might need to run "sudo update-initramfs -u" after blacklisting hid_rmi.

---

### Post by hardkorova on 2016-06-16
> **Imerion said:**
> I installed Ubuntu Gnome 16.04 and all hardware worked perfectly out of the box, but not my touchpad.

Hello, **Imerion** and **conch**.
Could you confirm, that there is no problem with suspend, sound, touchscreen on this device? Will touchpad and keyboard work well after joining tablet to base?
There is no reports about linux on this PC, except this topic.
I have plans to buy this device but not sure how good linux (especially, Ubuntu) on it. Should I buy it, please advice.

---

### Post by krusty8 on 2017-03-31
> **hardkorova said:**
> Hello, **Imerion** and **conch**.
Could you confirm, that there is no problem with suspend, sound, touchscreen on this device? Will touchpad and keyboard work well after joining tablet to base?

hardkorova, (or anybody else), in case you still care for a reply - I just got a x2 12 and it's working largely fine.

 Even with a 4.10 kernel I still need to blacklist hid_rmi to make the touchpad work. 

The touchscreen works fine - I think the only limiting factor is the somewhat dire state of support from software to actually take advantage of touch input. 

Sound is ok, not great, not very loud, but ok. Not sure whether there is a driver improvement possible, or the speakers are simply not louder. 

Suspend works. 

No battery complaints - I haven't done any specific tests, and I don't have it very long, but I get by a couple of hours. 

No problems when disconnecting/reconnecting the keyboard.

---

### Post by jeff123816 on 2017-09-28
I'm having a little trouble applying this fix. Hopefully someone can assist me. I was not familiar with dmesg before making this attempt so I think that I may not be configured the with same hardware addresses as the other people here. I can't figure out what dmesg command to use in order to display my machine's specific info. I've pasted in the output from "dmesg | grep -i usb" but am not getting the hardware id and using the id's from the previous person who posted a solution to this is not working. No touchpad for me yet. Any assistance would be greaty appreciated! Thanks!

[    2.678678] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.678680] usb 1-2.2: Product: Pro 10 EE G1 Keyboard Base
[    2.678682] usb 1-2.2: Manufacturer: HP
[    2.825196] input: HP Pro 10 EE G1 Keyboard Base as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.2/1-2.2:1.0/0003:048D:8910.0005/input/input6
[    2.882403] hid-generic 0003:048D:8910.0005: input,hiddev0,hidraw0: USB HID v1.10 Keyboard [HP Pro 10 EE G1 Keyboard Base] on usb-0000:00:14.0-2.2/input0
[    2.883140] usbcore: registered new interface driver usbhid
[    2.883142] usbhid: USB HID core driver
[    2.905982] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input7
[    2.906094] usbcore: registered new interface driver uvcvideo
[    2.906096] USB Video Class driver (1.1.1)
[   33.285774] usb 1-7: new low-speed USB device number 7 using xhci_hcd
[   33.432883] usb 1-7: string descriptor 0 read error: -75
[   33.432903] usb 1-7: New USB device found, idVendor=062a, idProduct=0000
[   33.432908] usb 1-7: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   33.433413] usb 1-7: config 0 descriptor??
[   33.439078] input: HID 062a:0000 as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:0.0/0003:062A:0000.0007/input/input21
[   33.498656] hid-generic 0003:062A:0000.0007: input,hidraw2: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:14.0-7/input0

---

### Post by rgold on 2017-11-01
> Oh, and if anyone else is reading this. You might need to run "[FONT=arial]**sudo update-initramfs -u**[/FONT]" after blacklisting hid_rmi.

Thank you!!!  After everything above, this was a _vital_ step to get Kali Linux to recognize the touchpad on my HP Pavillion X2 2-in-1 (model 12-b020nr).

---

### Post by rgold on 2017-11-02
A little more about the Kali Linux / HP Pavillion X2 2-in-1 (model  12-b020nr) setup.  After following the various steps detailed above, I found  that the touchpad didn't work upon reboot.  As a test, I did a 
[SIZE=4][FONT=century gothic]**sudo bash /etc/rc.local**[/FONT][/SIZE]  and the touchpad came alive again.  I was about to research how to make  the change permanent when I realized that I'll often have an external  mouse handy and having to manually turn the touchpad on means that, when  I have other mice in play, I won't have to worry about the "wandering  cursor" or random clicks when my palm strays too close to the touchpad  while typing.

---

### Post by coffeecat on 2017-11-02
Back to sleep. old thread.

Closed, to prevent further necromancy.

If anyone needs help with this hardware and Ubuntu or one of the Ubuntu flavours, please start a new thread, linking back to this if relevant.

Kali != Ubuntu . Kali questions should go here: [https://ubuntuforums.org/forumdisplay.php?f=452](https://ubuntuforums.org/forumdisplay.php?f=452)

---

