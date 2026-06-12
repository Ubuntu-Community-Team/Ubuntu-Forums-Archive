---
title: "Fujitu Lifebook T935 Touchpad Not Working, Even After my Ameteur Efforts"
date: 2020-04-12
forum: Hardware
---

### Post by Zeti-G on 2020-04-12
Hello folks!
I can't seem to get my touchpad working on 19.10 on my Fujitsu T935. I have searched for an answer but the solutions I have tried have not worked. I would appreciate any help!
I think the touchpad is recognized:

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input8
U: Uniq=
H: Handlers=mouse2 event5 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003


xinput gives me this, which seems promising:

virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom MultiTouch Sensor Finger              id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom MultiTouch Sensor Pen stylus          id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom MultiTouch Sensor Pen eraser          id=15    [slave  pointer  (2)]

I tried editing grub but have no confidence that I know what I'm doing there. I would appreciate some direction, with the warning that I am new at the more technical side of Ubuntu. Thank you!

---

### Post by CelticWarrior on 2020-04-12
19.04 is out of support. There's no point in beating a dead horse.

---

### Post by Zeti-G on 2020-04-12
Sorry. Edited. 19.10.

---

