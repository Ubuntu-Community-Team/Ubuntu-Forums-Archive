---
title: "Laptop Touchpad crashes on right click"
date: 2016-11-26
forum: Hardware
---

### Post by dooglex2 on 2016-11-26
I have a random noname laptop with an unknown Elantech touchpad. (I installed windows and found it was using an elan driver).

The symptoms are that I have no multitouch (possibly not supported) but more annoyingly whenever I press the right click button the trackpad the trackpad crashes, left click doesnt work, neither do taps or movement, but the keyboard and system still work fine, after a few more taps and a few seconds the touchpad usually comes back, but never triggers the right click action. 

if I do cat /proc/bus/input/devices

```

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
[CODE]

and dmesg | grep mouse before an error

 [CODE]
[    1.266564] mousedev: PS/2 mouse device common for all mice

```

and
```
dmesg | grep PS/2[    1.259948] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.266564] mousedev: PS/2 mouse device common for all mice
[    3.792144] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio2/input/input10



```

after i press right click it shows
```

dmesg | grep mouse[    1.266564] mousedev: PS/2 mouse device common for all mice
[  544.159004] psmouse serio2: Wheel Mouse at isa0060/serio2/input0 lost synchronization, throwing 1 bytes away.
[  545.394115] psmouse serio2: resync failed, issuing reconnect request



```

Thanks

---update 1---
```

root@nath-sdwbld:/home/nath/Downloads# xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=11    [slave  pointer  (2)]

```

---update 2---
I tried to build the elantech v7 drivers like this

```

 
 cd /usr/src/
sudo dkms remove psmouse/elantech-v6 --all
sudo wget http://www.ouam.fr/~madko/ubuntu/elantech/psmouse-elantech-v7.tar.bz2 
sudo tar jxvf psmouse-elantech-v7.tar.bz2 
sudo dkms add -m psmouse -v elantech-v7
sudo dkms build -m psmouse -v elantech-v7 
sudo dkms install -m psmouse -v elantech-v7

```

but it wont let me build them on my kernel with error

```

/var/lib/dkms/psmouse/elantech-v7/build/src/cypress_ps2.c: In function &#8216;cypress_process_packet&#8217;:
/var/lib/dkms/psmouse/elantech-v7/build/src/cypress_ps2.c:570:2: error: too few arguments to function &#8216;input_mt_assign_slots&#8217;
  input_mt_assign_slots(input, slots, pos, n);
  ^
In file included from /var/lib/dkms/psmouse/elantech-v7/build/src/cypress_ps2.c:25:0:
include/linux/input/mt.h:121:5: note: declared here
 int input_mt_assign_slots(struct input_dev *dev, int *slots,
     ^
scripts/Makefile.build:258: recipe for target '/var/lib/dkms/psmouse/elantech-v7/build/src/cypress_ps2.o' failed
make[1]: *** [/var/lib/dkms/psmouse/elantech-v7/build/src/cypress_ps2.o] Error 1
Makefile:1588: recipe for target 'psmouse.ko' failed
make: *** [psmouse.ko] Error 2
make: Leaving directory '/usr/src/linux-headers-4.4.0-47-generic'



```

---update4----

xinput --test 11 gives

```

nath@nath-sdwbld:~$ xinput --test 11
button press   1 
button release 1 
button press   1 
button release 1 
button press   1 
button release 1 
button press   1 
button release 1 
button press   1 
button release 1 
motion a[3]=-1695 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 
button press   4 
button release 4 



```

---

