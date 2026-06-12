---
title: "[SOLVED] Mouse problems"
date: 2008-10-06
forum: General Help
---

### Post by juanmanuelagueda on 2008-10-06
Hi!

I have some problems using my mouse on Ubuntu Hardy:

Everything seems okay on the desktop but when I press Ctrl+c or ctrl+v, the mouse stops responding a couple of seconds. This is not a severe problems but its quite annoying.

And yesterday, I installed warsow from playdeb.net, and a I wasn´t able to use the keys and the mouse at the same time. Whenever I a pressed any key, the mouse stopped working until the key was released. 

I know that I should check warsow forums, (I´ve already done, without too much luck :(. I´ve tried a couple of tips: disable compiz, disable mouse acceleration in the game ... None of them worked :() So I´m trying here :D. 

Thanks in advance :D

---

### Post by Calmatory on 2008-10-06
Which mouse are you having?

Could you also post what

```

lspci

```

returns, so others with similar problem MIGHT be able to track it down to a hardware devide IF that is the problem. :)

---

### Post by juanmanuelagueda on 2008-10-06
Ops sorry my fault! My mouse is a logitech one connected via ps2 interface. If I do a dmesg | grep mouse it shows:

[   33.455775] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.480314] mice: PS/2 mouse device common for all mice
[   58.028882] logips2pp: Detected unknown logitech mouse model 127
[   83.929685] input: Mouseemu virtual mouse as /devices/virtual/input/input8


And the output of lspci is:


00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
03:06.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

If I can add any information of value just tell me ;) 

Thanks!

---

### Post by juanmanuelagueda on 2008-10-07
Hi! 

Finally Ive managed to solve the problem with the mouse. Reading through the forums, Ive came across a daemon called mouseemu, used to "emulate" events like keys being pressed, mouse buttons not present on macs... etc. This daemon by default is configured to block the "events" for 300ms after pressing any key on the keyboard. (Sorry, I exaggerated a lot when I said a couple of seconds) This is done to avoid clicking by mistake while typing on laptops. Since I don't like this behavior, Ive changed it by editing:

/etc/default/mouseemu

(do something like
sudo cp /etc/default/mouseemu /etc/default/mouseemu.old
gksudo gvim /etc/default/mouseemu)

and adding at the end of the file the following statement:

TYPING_BLOCK="-typing-block 0" 

Now the mouse is still responsive after pressing ctrl+c or ctr+v and warsow works flawlessly.

This is the bug on launchpad I think:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344)

Bye!

---

### Post by juanmanuelagueda on 2008-10-08
After editing the mouseemu conf file, all multimedia keys of my keyboard stopped working. So checked the forums again and the best option seems like removing the mouseemu package

after 

sudo apt-get remove mouseemu

I'm able to play warsow, move the pointer while pressing any key, and my multimedia keys work again!

Ill post back if I found any more problems!

---

