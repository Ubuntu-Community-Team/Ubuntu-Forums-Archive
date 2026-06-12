---
title: "AlpsPS/2 ALPS DualPoint Stick not correctly assigned"
date: 2018-03-25
forum: Hardware
---

### Post by pablokolo78 on 2018-03-25
[COLOR=#333333][FONT=Ubuntu]Hello, seems that there's a bad assigment of my AlpsPS/2 ALPS DualPoint Stick from kernel to devices list.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
Despite it's not listed on the device list, it work like a charm BUT I want to disable it, because the stick is in the middle of the keyboard.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
The device is recognized by the kernel:
[/FONT][/COLOR]```

[COLOR=#333333][FONT=Ubuntu]pablo@loki:~$ dmesg | grep AlpsPS[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][ 2.545463] input: AlpsPS/2 ALPS DualPoint Stick as /devices/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]platform/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]i8042/serio1/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]input/input10[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][ 2.558606] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]platform/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]i8042/serio1/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]input/input6[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]
```

[COLOR=#333333][FONT=Ubuntu]But not listed on xlist[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]```

pablo@loki:~$ xinput --list
&#9121; Virtual core pointer id=2    [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4    [slave pointer (2)]
&#9116; &#8627; xwayland-pointer:13 id=6    [slave pointer (2)]
&#9116; &#8627; xwayland-relative-pointer:13 id=7    [slave pointer (2)]
&#9123; Virtual core keyboard id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5    [slave keyboard (3)]
    &#8627; xwayland-keyboard:13 id=8    [slave keyboard (3)]
```[/FONT][/COLOR]

```

[COLOR=#333333][FONT=Ubuntu]pablo@loki:~$ lsb_release -rd[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Description:    Ubuntu 17.10[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Release:    17.10[/FONT][/COLOR]

```

[COLOR=#333333][FONT=Ubuntu]Please let me know if this should be submitted as a bug or there's something I can try before.
Thanks in advance.
Regards,
Pablo
[/FONT][/COLOR]

---

### Post by cruzer001 on 2018-03-25
Looks like your on wayland, have you tried switching to xorg?  Xinput may yield different results.

---

### Post by pablokolo78 on 2018-03-25
> **cruzer001 said:**
> Looks like your on wayland, have you tried switching to xorg?  Xinput may yield different results.

[FONT=arial]cruzer001 you're right. Switching to Xorg solve the problem and xlist show all the devices! :)[/FONT]

---

### Post by cruzer001 on 2018-03-25
How cool is that :)

Don't forget to mark this solved (in thread tools).

---

