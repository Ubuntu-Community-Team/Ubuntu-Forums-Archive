---
title: "Avermedia RM-KV (Super 007) IR Remote Problem"
date: 2009-10-29
forum: Hardware
---

### Post by AranelSurion on 2009-10-29
I recently installed a Avermedia TV Tuner (Super 007) with an IR Remote named RM-KV. On LSPCI output, it recognized as SAA7134 and seems working. But I could not get its remote to work.

I've installed Mythbuntu, and tried to configure it with MCC, failed. When I push buttons and "cat /dev/input/event7" , It displayed some characters, so its recognized, but I cannot assign(I dont know how to do it) this characters to meaningful buttons. Tried gnome-keybinding-properties, didnt work.

After all this mess, I tried to edit xorg.conf ([http://ubuntuforums.org/showthread.php?t=444278](http://ubuntuforums.org/showthread.php?t=444278)) and restarted X. Now, *some* (6-7 of nearly 20~ buttons) buttons work, but not correctly, if I push "Volume up", It enters "7" on screen, If I push "6", It recognizes it as "Enter" key etc.

So;

a) Is it possible to handle /dev/input/event7 with LIRC and How?
b) Cant I assign characters on event7 to meaningful buttons?
c) My remote seems to work with Xorg way, so, can I map a new button layout for Xorg and How?

Thanks =)

---

### Post by Kolyanovich on 2009-12-15
I have the same problem. Has anyone solved this problem?

---

### Post by L_V on 2010-11-08
Still problem with Maverick/2.6.35-22 and Avermedia RM-KV remote control.

Does somebody know which modules should be loaded to detect RM-KV remote control ??

 "cat /proc/bus/input/devices" only giving:

```
N: Name="Sleep Button"
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0

N: Name="Power Button"
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

N: Name="AT Translated Set 2 keyboard"
S: Sysfs=/devices/platform/i8042/serio0/input/input2

N: Name="PC Speaker"
S: Sysfs=/devices/platform/pcspkr/input/input3

N: Name="ImPS/2 Logitech Wheel Mouse"
S: Sysfs=/devices/platform/i8042/serio1/input/input4
```

---

### Post by Kolyanovich on 2010-11-08
> **L_V said:**
> Still problem with Maverick/2.6.35-22 and Avermedia RM-KV remote control.

Does somebody know which modules should be loaded to detect RM-KV remote control ??

 "cat /proc/bus/input/devices" only giving:

```
N: Name="Sleep Button"
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0

N: Name="Power Button"
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

N: Name="AT Translated Set 2 keyboard"
S: Sysfs=/devices/platform/i8042/serio0/input/input2

N: Name="PC Speaker"
S: Sysfs=/devices/platform/pcspkr/input/input3

N: Name="ImPS/2 Logitech Wheel Mouse"
S: Sysfs=/devices/platform/i8042/serio1/input/input4
```

I guess, those modules should be loaded: saa7134, ir_common, ir_core, rc_avermedia_m135a

---

### Post by L_V on 2010-11-08
This is the IR modules I have:

```
lsmod | grep ir_

ir_common               5167  1 saa7134
ir_lirc_codec           3092  0
lirc_dev                9393  1 ir_lirc_codec
ir_sony_decoder         1889  0
ir_jvc_decoder          1950  0
ir_rc6_decoder          2334  0
ir_rc5_decoder          1950  0
ir_nec_decoder          2014  0
ir_core                14654  9 saa7134,ir_common,ir_lirc_codec,,rc_avermedia_m135a,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
```

Lirc seems correctly launched, and RM-KV config file well detected.

However, what should be the next step to test the RC ??

"irw" does not listen to the remote control.
The RC input is not detected as a /proc/bus/input/devices event.

May be close to the target, but something is missing, at least to test the remote.

---

