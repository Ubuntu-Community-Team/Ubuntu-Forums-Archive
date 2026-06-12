---
title: "Touchpad on Dell Latitude E5410"
date: 2010-11-28
forum: Hardware
---

### Post by p.w_ssi on 2010-11-28
Hey guys,

I've just set up Ubuntu 10.10 on my new Dell Latitude E5410 notebook.
Everything works fine except the touchpad.
Would be nice if we could get this fixed ;-)

Before patching the driver the device was detected as Generic Mouse.
I've read through a lot of threads and finally got the ALPS-driver patched, so at least it gets detected as touchpad.
Here are my "debugging"-outputs:

grep -B 5 mouse /proc/bus/input/devices 
```
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="DualPoint Stick"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
--
I: Bus=0011 Vendor=0002 Product=0008 Version=7326
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7
```sudo cat /var/log/Xorg.0.log | grep -i touch
```

[    21.021] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event7)
[    21.021] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.021] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    21.059] (II) Synaptics touchpad driver version 1.2.2
[    21.132] (II) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
[    21.132] (II) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
[    21.132] (II) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    21.132] (II) AlpsPS/2 ALPS DualPoint TouchPad: finger width range 0 - 0
[    21.132] (II) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    21.196] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    21.196] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    21.264] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
[    21.264] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    21.264] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 0
[    21.264] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    21.264] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    21.316] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    21.316] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse1)
[  1365.008] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[  1376.168] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[  1386.800] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found

```/dev/psaux, /dev/input/mice and /dev/input/mouse0 give output, whereas /dev/input/mouse1 (which was added by xorg in second 21.316) doesn't give any output at all.
I've tested this by running the command

sudo cat /dev/psaux | hexdump
which will output something like this
```
0000000 0528 28fc fc07 0a28 08fd 000a 0a08 0801
0000010 040b 0908 0806 0605 0208 0804 0202 fe18
0000020 1802 02fb f718 1802 01f6 f718 3800 fef6
0000030 f738 38fd fbf9 fa38 38fb fcfb fe38 38fc
0000040 fcfe 0028 28fb fb02 0528 28fb fb07 0928
0000050 28fc fe09 0a08 0800 0109 0708 0803 0505
0000060 0308 0805 0402 0008 0805 0400 0008 1803
0000070 03fe fd18 1802 01fb fa18 1801 00fa fa18
0000080 1800 00f9 fb38 38ff fdfc fe38 38fd fbff
0000090 0028 28f9 f804 0528 28f9 fb06 0828 28fc
```

My kernel is 2.6.35-22-generic.

Maybe now I should tell you where my problem is ;-)
The touchpads extended functions do not work at all (e.g. I can not scroll by sliding my finger on the edges), although scrolling is enabled in System->Preferences->Mouse

Can I check if the synaptic drivers work with the input device or at least if they try to communicate?

Thanks in advance,
p.w_ssi

---

### Post by simisimis on 2011-01-05
seems that a lot of people experience this and few more problems, as in this thread:
[http://ubuntuforums.org/showthread.php?t=1621879](http://ubuntuforums.org/showthread.php?t=1621879)

really would like to get some help on this, cause a bit annoying when you cant scroll connect additional monitor or use sdcard

---

### Post by p.w_ssi on 2011-04-30
Just for information: running Natty now everything works fine.
external monitors via VGA work, the SD-cardreader works and the touchpad does what I want...
THANK YOU, DEVELOPERS !

---

