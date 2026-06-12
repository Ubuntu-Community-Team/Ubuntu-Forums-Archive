---
title: "Mouse wheel sometimes doesn't work"
date: 2013-12-11
forum: Hardware
---

### Post by nicks27 on 2013-12-11
When I boot my machine, sometimes the mouse wheel works, sometimes it doesn't.
It seems to depend if it's detected as "[SIZE=2]PS/2 Generic Mouse[/SIZE]" or "[SIZE=2]ImPS/2 Generic Wheel Mouse[/SIZE]".

Is there some configuration that will make sure the mouse wheel always works?

It's currently not working:

```

[SIZE=2]$ **grep -i "mouse" /var/log/Xorg.0.log **[/SIZE]
 [SIZE=2][    24.684] (==) NOUVEAU(0): Silken mouse enabled [/SIZE]
 [SIZE=2][    24.794] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event3) [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall" [/SIZE]
 [SIZE=2][    24.794] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse' [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: always reports core events [/SIZE]
 [SIZE=2][    24.794] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event3" [/SIZE]

 [SIZE=2][    24.794] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1 [/SIZE]
 [SIZE=2][    24.794] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons [/SIZE]
 [SIZE=2][    24.794] (--) evdev: PS/2 Generic Mouse: Found relative axes [/SIZE]
 [SIZE=2][    24.794] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes [/SIZE]
 [SIZE=2][    24.794] (II) evdev: PS/2 Generic Mouse: Configuring as mouse [/SIZE]
 [SIZE=2][    24.794] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5 [/SIZE]
 [SIZE=2][    24.794] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 [/SIZE]
 [SIZE=2][    24.794] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 9) [/SIZE]
 [SIZE=2][    24.794] (II) evdev: PS/2 Generic Mouse: initialized for relative axes. [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1 [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: (accel) acceleration profile 0 [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000 [/SIZE]
 [SIZE=2][    24.794] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4 [/SIZE]
 [SIZE=2][    24.794] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0) 

   [/SIZE]
[SIZE=2]$ **cat /proc/bus/input/devices | grep -B 1 -A 7 -i "mouse"** [/SIZE]
 [SIZE=2]I: Bus=0011 Vendor=0002 Product=0001 Version=0000 [/SIZE]
 [SIZE=2]N: Name="PS/2 Generic Mouse" [/SIZE]
 [SIZE=2]P: Phys=isa0060/serio1/input0 [/SIZE]
 [SIZE=2]S: Sysfs=/devices/platform/i8042/serio1/input/input3 [/SIZE]
 [SIZE=2]U: Uniq= [/SIZE]
 [SIZE=2]H: Handlers=mouse0 event3  [/SIZE]
 [SIZE=2]B: PROP=0 [/SIZE]
 [SIZE=2]B: EV=7 [/SIZE]
 [SIZE=2]B: KEY=70000 0 0 0 0 [/SIZE]
 [SIZE=2]B: REL=3 [/SIZE]



 
```

but on the previous boot it was working:

```

   [SIZE=2]$ **grep -i "mouse" /var/log/Xorg.0.log.old **[/SIZE]
 [SIZE=2][    26.132] (==) NOUVEAU(0): Silken mouse enabled [/SIZE]
 [SIZE=2][    26.243] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3) [/SIZE]
 [SIZE=2][    26.243] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall" [/SIZE]
 [SIZE=2][    26.243] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse' [/SIZE]
 [SIZE=2][    26.243] (**) ImPS/2 Generic Wheel Mouse: always reports core events [/SIZE]
 [SIZE=2][    26.243] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3" [/SIZE]

 [SIZE=2][    26.243] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5 [/SIZE]
 [SIZE=2][    26.243] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons [/SIZE]
 [SIZE=2][    26.243] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s) [/SIZE]
 [SIZE=2][    26.243] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes [/SIZE]
 [SIZE=2][    26.243] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes [/SIZE]
 [SIZE=2][    26.243] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse [/SIZE]
 [SIZE=2][    26.243] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support [/SIZE]
 [SIZE=2][    26.243] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5 [/SIZE]
 [SIZE=2][    26.243] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 [/SIZE]
 [SIZE=2][    26.243] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 9) [/SIZE]
 [SIZE=2][    26.243] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes. [/SIZE]
 [SIZE=2][    26.244] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1 [/SIZE]
 [SIZE=2][    26.244] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0 [/SIZE]
 [SIZE=2][    26.244] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000 [/SIZE]
 [SIZE=2][    26.244] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4 [/SIZE]
 [SIZE=2][    26.244] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0) [/SIZE]
 [SIZE=2][  1116.400] (II) evdev: ImPS/2 Generic Wheel Mouse: Close [/SIZE]
 
```

---

### Post by nicks27 on 2013-12-22
After some searching, I found this bug and workaround:
[INDENT][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587134/comments/]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587134/comments/9")
[/INDENT]
  > ... editing this line in /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT="psmouse.proto=imps quiet nosplash"
 then running "sudo update-grub" at the command line. When I rebooted, my wheel worked...

This worked for me.

---

### Post by nicks27 on 2013-12-27
> I am also facing the same problem bu i am failed to find any solution.If  you will get any solution then share this with us. I will thankful to  you for this kindness.

You may find the details on the following page useful:
 [INDENT][http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml)
[/INDENT]
 
Maybe you can try the suggested commands but with "imps" instead of "bare":
```
# **modprobe -r psmouse**  # Unloads the driver; your mouse will stop working at this point
# **modprobe psmouse proto=imps**    # Re-load the driver using the correct parameter
```

and if that works for you then maybe putting:
```
options psmouse proto=imps
```
in your [FONT=courier new]/etc/modprobe.conf[/FONT] file (instead of the GRUB option) will make the change persistent after rebooting.

---

