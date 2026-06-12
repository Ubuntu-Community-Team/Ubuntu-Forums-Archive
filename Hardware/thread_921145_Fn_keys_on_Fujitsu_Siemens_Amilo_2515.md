---
title: "Fn keys on Fujitsu Siemens Amilo 2515"
date: 2008-09-15
forum: Hardware
---

### Post by artpol84 on 2008-09-15
Hello all!
I faced a problem on my new laptop (subj model). It has several Fn keys and they work partially:
1. Fn+F1 - Hibernate - works OK
2. Fn+F3 - Mute - OK
3. Fn+F4 - Display switch - NOT WORK
4. Fn+F5/F6 - Volume UP/DOWN - OK
5. Fn+F7/F8 - Brightness UP/DOWN - NOT WORK

I searched Internet and studied this problem on my laptop and get following results:
1. Brightness can be controlled through sysfs file /sys/class/backlight/acpi_video0/brightness
2. If I assign keys (for example UP/DOWN or any non Fn key) in HAL configuration (/usr/share/hal/....) - this keys starts to control brightness!
3. In BIOS mode and in Windows Vista (was preinstalled and later removed by me :) this keys WORK!
3. Fn+F4,Fn+F7 and Fn+F8 don't rise interrupts while Fn+F1,Fn+F3 and other working keys do. I check this by executing:
```
watch cat /proc/interrupts
```
and watching interrupt counters of i8042 keyboard controller

So I gess that something in kernel blocks part of my Fn keys. But I don't know where it can be. I have not found corresponding keyboard layout in Ubuntu so I don't know where to move now.

---

### Post by napsy on 2008-12-08
The same laptop with the same problem. I've commited a bug report at [https://bugs.launchpad.net/ubuntu/+bug/305997](https://bugs.launchpad.net/ubuntu/+bug/305997). Please confirm the bug.

---

### Post by artpol84 on 2008-12-09
I solved this problem temporary. If you interested in it here is my solution:

As I sad I found that no interrupts generated on this Fn keys. So I assigned brightness controll functions on F11,F12 keys. You can change it as you wish. Here is what you need to do:

Scan codes for F11, F12:
F11 - 0x57
F12 - 0x58

Now in 
/usr/share/hal/fdi/information/10freedesktop
Change file 
30-keymap-misc.fdi
In this way:

      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="FUJITSU">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="AMILO">
          <append key="input.keymap.data" type="strlist">e020:mute</append> <!-- Fn-F9   Sound On/Off -->
          <append key="input.keymap.data" type="strlist">e02e:volumedown</append> <!-- Fn-F7   Volume down -->
          <append key="input.keymap.data" type="strlist">e030:volumeup</append> <!-- Fn-F8   Volume up -->
          <append key="input.keymap.data" type="strlist">57:brightnessdown</append> <!--   Brightness down -->
          <append key="input.keymap.data" type="strlist">58:brightnessup</append> <!--   Brightness up -->
          <append key="info.capabilities" type="strlist">input.keymap</append>
        </match>
      </match>

For me it works, but it is unpleasant to have F11 & F12 busy. They cannot perform nothing else but changing brightness.

By the way, I cannot loag page with bug: [https://bugs.launchpad.net/ubuntu/+bug/305997](https://bugs.launchpad.net/ubuntu/+bug/305997)
Is this link correct?

---

