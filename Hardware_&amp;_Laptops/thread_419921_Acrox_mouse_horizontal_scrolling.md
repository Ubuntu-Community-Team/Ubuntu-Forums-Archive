---
title: "Acrox mouse horizontal scrolling"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by Ace2016 on 2007-04-23
I want horizontal scrolling to work.This is the mouse: [http://www.amparo.net/gadgets/acrox-mini8d/](http://www.amparo.net/gadgets/acrox-mini8d/)

In linux the rotating the scroll ball up and down scrolls up and down, thats fine, however rotating it left and right also scroll up and down, but act more like page up and page down, they tend to scroll by a larger amount.

xev: scroll up = 4, scroll down = 5 scroll left = 4 and scrolling right =5

Totally messed up

So i ran sudo hexdump /dev/input/event2      

Scroll UP:  

0005c30 ca52 462c b35b 0008 0002 0008 0001 0000
0005c40 ca52 462c b36a 0008 0000 0000 0000 0000
0005c50 ca52 462c 6ff7   000e 0002 0008 0001 0000
0005c60 ca52 462c 7005 000e 0000 0000 0000 0000
0005c70 ca53 462c 0875 0000 0002 0008 0001 0000
0005c80 ca53 462c 0887 0000 0000 0000 0000 0000
0005c90 ca53 462c 21aa 0001 0002 0008 0001 0000
0005ca0 ca53 462c 21b9 0001 0000 0000 0000 0000

Scroll DOWN:

0001620 ca98 462c 5c4b 000d 0002 0008 ffff ffff
0001630 ca98 462c 5c5b 000d 0000 0000 0000 0000
0001640 ca99 462c 67f6  000b 0002 0008 ffff ffff
0001650 ca99 462c 6805 000b 0000 0000 0000 0000
0001660 ca9a 462c 20d2 0002 0002 0008 ffff ffff
0001670 ca9a 462c 20e2 0002 0000 0000 0000 0000
0001680 ca9a 462c bd0e 0002 0002 0008 ffff ffff
0001690 ca9a 462c bd22 0002 0000 0000 0000 0000

Scroll LEFT:

0001970 caeb 462c 0b58 000b 0002 0008 0007 0000
0001980 caeb 462c 0b67 000b 0000 0000 0000 0000
0001990 caec 462c b948 0008 0002 0008 0007 0000
00019a0 caec 462c b957 0008 0000 0000 0000 0000
00019b0 caec 462c 8dfd 000a 0002 0008 0007 0000
00019c0 caec 462c 8e0c 000a 0000 0000 0000 0000
00019d0 caed 462c 0254 0002 0002 0008 0007 0000
00019e0 caed 462c 0263 0002 0000 0000 0000 0000

Scroll RIGHT:

0000bc0 cb06 462c 0d79 0009 0002 0008 fff9 ffff
0000bd0 cb06 462c 0d87 0009 0000 0000 0000 0000
0000be0 cb06 462c 4d1b 000e 0002 0008 fff9 ffff
0000bf0 cb06 462c 4d2c 000e 0000 0000 0000 0000
0000c00 cb07 462c eddb 0008 0002 0008 fff9 ffff
0000c10 cb07 462c edea 0008 0000 0000 0000 0000
0000c20 cb07 462c aa79 000e 0002 0008 fff9 ffff
0000c30 cb07 462c aa89 000e 0000 0000 0000 0000



Is there any way to get xorg to detect the mouse buttons, in windows the program in the screenshot enables the horizontal scrolling what can i do in ubuntu???

---

### Post by Ace2016 on 2007-04-23
Oh i forgot this:

ace@Linux:~$ dmesg | grep Acr
[   53.709818] input: Acrox USB & PS/2 Mouse as /class/input/input2
[   53.709963] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:03.0-1



ace@Linux:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=0f62 Product=1001 Version=0110
N: Name="Acrox USB & PS/2 Mouse"
P: Phys=usb-0000:00:03.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 ts1 event2
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=062a Product=0000 Version=0110
N: Name="HID 062a:0000"
P: Phys=usb-0000:00:03.1-1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse2 ts2 event3
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event7
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

ace@Linux:~$

---

### Post by Ace2016 on 2007-04-23
up

---

### Post by Ace2016 on 2007-04-24
Any ideas? at all?

---

### Post by Ace2016 on 2007-04-25
I broke the mouse while taking it apart :(

I was messing with it while the computer was on, i took it apart and now the mouse works for about a minute before it totally stops and i see Ctrl+F1 full of just errors

---

### Post by Ace2016 on 2007-04-25
Oh wait lol, the mouse got unplugged by mistake, its still working fine

So can someone help to get it to scroll horizontally?

---

