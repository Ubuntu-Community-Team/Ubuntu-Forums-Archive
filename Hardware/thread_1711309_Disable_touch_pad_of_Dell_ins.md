---
title: "Disable touch pad of Dell ins"
date: 2011-03-21
forum: Hardware
---

### Post by Vinh Phat on 2011-03-21
when i press disable/enable touchpad button. i got a notification about its status (disable/enable) but there no happened with my touchpad.
is there any way for disable my touchpad?
I'm suing Dell ins M5030 and ubuntu lucid 64 bit

P/S: Sr for my english! :)

---

### Post by Vinh Phat on 2011-03-22
pls.. help

---

### Post by vto on 2011-03-23
Same problem with asus A52F.

---

### Post by theremper on 2011-05-22
to disable your touchpad in 11.04 hit alt+f2 and enter the command 

 xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0

to enable enter the command 

xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1

for previous versions. use the command to disable

xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0

to enable
xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1

I use a usb mouse most of the time so I have the command to disable setup in start up, and I have created keyboard shortcuts for both commands.

---

### Post by Sith Lord Kyle on 2011-05-22
@theremper - Oh man, thank you so much! I've been looking for a solution since installed 11.04 (which has been a rather disappointing release).  The software didn't help nor any start-up scripts I had found, even though this one isn't too different.  But, apparently the extra dash before set-prop made the difference in allowing the device to be identified by name instead of ID number. Why is this not better known or more clear?

Oddly, if I used ID number in the star-tup command, the touchpad would switch ID's with my webcam, killing that on start-up instead. I was either going to physically remove the touchpad or go back to 10.10 or 10.04 where I could disable it in xOrg.

Thanks again!

---

### Post by patricklcam on 2011-09-04
I know this thread is a little older but thought I would update with some additional generic information.

To list devices, do:
   xinput list

My system returned:
  &#9121; Virtual core pointer       	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver      id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard          id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5	[slave  keyboard (3)]
    &#8627; Video Bus                   id=6	[slave  keyboard (3)]
    &#8627; Power Button                id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver       id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=11 [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys             id=13 [slave  keyboard (3)]


ID 12 is my touchpad device

To disable do:
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0

Change trailing 0 to a 1 to enable.

---

### Post by 192709 on 2011-09-11
@patricklcam:

That was the info I was missing - thank you ! :P
(... works on Dell Vostro 3700)

Best Regards,
192709

---

### Post by Wobblybob on 2012-03-10
On my Sony Vaio VGN_NS11J
$ xinput list
got me;

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (05ca:18b3)                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

So these commands work for me
Turn Off TouchPad::
$  xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0

Turn On TouchPad::
$  xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1

Thanks to everyone for the help

---

### Post by tom king on 2012-03-14
[SIZE=3]Great free tool in Software Center > dconf Editor < that allows  you to fix/change anything (almost) in 11.10. Using the check boxes I  turned my touch pad off when only typing or you can disable it  completely.  Great tool):P[/SIZE]

---

