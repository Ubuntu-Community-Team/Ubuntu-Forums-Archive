---
title: "HP Pavilion Entertainment PC dv6-1360us IR Reciever"
date: 2010-09-17
forum: Hardware
---

### Post by serverfarm on 2010-09-17
Hi all, I have a HP Pavilion Entertainment PC that comes with a built in IR receiver.  Now it was designed for use with Windows Media Center, but I used it when doing presentations at school.   Now I have experience with the terminal and am not afraid of config files.  I neglected to check if the IR receiver worked, it is only a minor inconvenience, but I used the feature quite a bit and would appreciate help.  Here is some interesting dmesg output:
[ 1551.529497] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[ 1551.529556] usbcore: registered new interface driver lirc_imon
[ 1553.940984] usbcore: registered new interface driver lirc_streamzap
[ 1553.941233] lirc_streamzap $Revision: 1.48 $ registered
[ 2904.080719] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[ 2904.080723] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[ 2904.087419] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[ 2904.087423] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[ 2904.576957] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
This may have been me playing around with LIRC...
Also, on the System Profiler and Benchmark an IR receiver is not listed in Input Devices section.
Thanks in Advance!

---

### Post by serverfarm on 2010-09-18
Solved the problem, for others having same problem: [http://h30434.www3.hp.com/t5/Hardware/ENE-CIR-under-Linux-HDX16/m-p/34808](http://h30434.www3.hp.com/t5/Hardware/ENE-CIR-under-Linux-HDX16/m-p/34808)

---

