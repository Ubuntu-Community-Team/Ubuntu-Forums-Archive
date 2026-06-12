---
title: "Wireless Keyboard Works, Wireless Mouse Doesn't"
date: 2012-04-11
forum: Hardware
---

### Post by JustinBenner on 2012-04-11
Hey folks,

First, I am running Ubuntu 12.04. Don't know if it matters for my issue, but I thought I'd make that clear in case it does.

I just purchased a cheap wireless keyboard/mouse set. I managed to get the keyboard working - all I had to do was select it under System Settings > Keyboard. However, I have not been able to get the mouse working.

I looked around, and taught myself a bit about xinput. I ran xinput --list. This is what came up:

>  Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. Wireless Keyboard & Mouse  	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; MOSART Semi. Wireless Keyboard & Mouse  	id=8	[slave  keyboard (3)]


I also ran xinput --list props 9... and the results seem to show that everything is fine, and that just about everything my mouse can do should be working.

The mouse has lit up, and the light responds to clicks and movement... HOWEVER, it simply won't work. My cursor does not move. I tried disabling and reenabling the device using xinput, but that didn't work either.

Does anyone know a fix for this?

I really appreciate any help I can get. Thanks!

Justin Benner

---

### Post by whitethunder922 on 2012-04-27
Same problem here with Logitech M510 on upgrade from 11.10 to 12.04. Extremely irritating that the keyboard works but the mouse doesn't.

---

### Post by JustinBenner on 2012-05-09
Anybody have a clue what to do about this? The wireless mouse/keyboard set is recognized by the computer... I am typing on the keyboard right now, but the mouse simply will not work. I ran dmesg... This is what came up that is relevant to my problem.

$dmesg


[    2.965466] input: MOSART Semi. Wireless Keyboard & Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    2.965703] generic-usb 0003:062A:0102.0001: input,hidraw0: USB HID v1.10 Keyboard [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:1d.0-2/input0
[    2.999861] input: MOSART Semi. Wireless Keyboard & Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input3
[    3.000516] generic-usb 0003:062A:0102.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:1d.0-2/input1

---

### Post by JustinBenner on 2012-05-09
I tried to use NDISWrapper to convert the driver file, but the disc that came with the set doesn't provide the .inf, only .exe setup files...

---

### Post by JustinBenner on 2012-05-09
I ran lsusb and it displayed my keyboard and wireless set as "Creative Labs Wireless/Keyboard Mouse Combo [MK1152]"

When I run xinput, however, it is shown as a "Mosart Semi. Wireless Keyboard/Mouse Combo"

Would this make a difference?

---

### Post by finny388 on 2012-05-09
What are the make and model numbers?

---

### Post by JustinBenner on 2012-05-09
Not sure what the make is, it came repackaged by the business I bought it from. The model number is LKM-802FA

I Google'd that, and the only company name that popped up a few times in the results was Lantian Electronics Co. I looked at their website, and couldn't even find my model number.

Thanks for any help you can give :)

---

### Post by JustinBenner on 2012-05-15
Well, I've exhausted every avenue I could think of. If anyone has any ideas, please, please help, lol.

---

