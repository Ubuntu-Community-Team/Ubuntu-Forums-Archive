---
title: "LIRC in 8.04 using Chronos Video Shuttle 2 remote"
date: 2008-06-24
forum: Hardware
---

### Post by the_mouse on 2008-06-24
Hey guys,
For a while I've been trying to set up my remote control on my Kubuntu 8.04 system.
I read [this document in the community docs]("https://help.ubuntu.com/community/InstallLirc/Hardy?highlight=%28lirc%29") section, but I seem to get confused at some parts.
Apparantly, my remote is used via the gpio module, which in the current Hardy kernel is kind of unsupported and I should:
> Instead all gpio devices will load from the dev/input native lirc driver. You will be asked for what "event" device you want to use for your remote. This information can be found via
$ cat /proc/bus/input/devices

when configuring the lirc package I get to this step and can't figure out what I should do next:

> Many remotes that were previously supported by the lirc_gpio interface now need to be set up via the dev/input interface.  You will need to custom select your remote's event character device.  This can be determined by 'cat /proc/bus/input/devices'.                                                                                      



Select your custom event interface for your dev/input device: 
 &#9474;                 /devlirc0                                                             &#9474;
 &#9474;                 /dev/input/by-path/platform-i8042-serio-0-event-kbd                    &#9474;
 &#9474;                 /dev/input/by-path/platform-i8042-serio-1-event-mouse                  &#9474;
 &#9474;                 /dev/input/by-path/platform-i8042-serio-1-mouse                        &#9474;
 &#9474;                 /dev/input/by-path/platform-pcspkr-event-spkr                          &#9474;
 &#9474;                 /dev/input/event0                                                      &#9474;
 &#9474;                 /dev/input/event1                                                      &#9474;
 &#9474;                 /dev/input/event2                                                      &#9474;
 &#9474;                 /dev/input/event3                                                      &#9474;
 &#9474;                 /dev/input/event4                                                      &#9474;
 &#9474;                 /dev/input/event5                                                      &#9474;
 &#9474;                 /dev/input/mice                                                        &#9474;
 &#9474;                 /dev/input/mouse0                                                      &#9474;
 &#9474;                 /dev/input/mouse1                                                      &#9474;
 &#9474;                                                                                        &#9474;
 &#9474;                                                                                        &#9474;
 &#9474;                                         <OK>                                           &#9474;
 &#9474;                                                                                        &#9474;

When I do cat /proc/bus/input/devices I get:
> I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

So I can't find my remote control on the list and can't finish the setup.

I'll appreciate any help you can give me on this subject :)

---

### Post by the_mouse on 2008-11-06
Hi again, I'm still struggling with the tv card, do you have ideas about running lirc with it? Thank you.

---

