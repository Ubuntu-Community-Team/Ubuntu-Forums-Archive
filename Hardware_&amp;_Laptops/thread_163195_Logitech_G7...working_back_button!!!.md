---
title: "Logitech G7...working back button?!?!?!"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by mrazster on 2006-04-20
Was just wondering if there's anyone running the G7 mouse and had all buttons working? Essentially I'm only interested in the "back" button.

I tried both [*THIS*](http://doc.gwos.org/index.php/5ButtonMouse) and [*THIS*](http://doc.gwos.org/index.php/LogitechMouse) howto...butt none of them worked. And I read and did every step of them very carefuly....to make sure I got it all wright.

Any other suggestion..?!?!?

---

### Post by mrazster on 2006-04-22
Anyone..?!?!?  

PLZZ...!!!

---

### Post by ubuntu-mike022465 on 2006-05-23
Have a look here, this might help

[http://ubuntuforums.org/showthread.php?t=125752&highlight=logitech+g7]("http://ubuntuforums.org/showthread.php?t=125752&highlight=logitech+g7")

Hope this helps

M.

---

### Post by mrazster on 2006-05-23
THNX for the reply...muck appreciated.

However..I didn't get it working.
After modifying the Xorg file and restarting X...I end up in CLI.

When I do:
```
cat /proc/bus/input/devices
```

I get this:
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

[B]I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143[/B]

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6639fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd
B: EV=40001
B: SND=6

```

When I look at the output...I get the feeling I got some collision. If you look at the bolded part...and then the section below. Both have the same "Phys" except for the "Input"..one is 1 oand one is 0.
And then look at the handlers, one says "kbd" and one says "mouse0 ts0". Thing is... I DONT have a USB keyboard konected...it's konected to the PS2.
I might be wrong...but somehow it feels like the problem is here.
Any suggestions..???

---

### Post by mrazster on 2006-05-25
Still nobody...with any suggestions..?!?!?

---

