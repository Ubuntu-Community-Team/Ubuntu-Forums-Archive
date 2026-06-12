---
title: "MSI SBAR - GT780DX - Eject CD"
date: 2013-05-31
forum: Hardware
---

### Post by Shark711 on 2013-05-31
For 12.04 LTS

Good day all,

I was battling with this for some time until I've discovered Linux's "dmesg" and "xev"
Long story short, you need to do the following to get your keys to work:
Create a new mapping file and paste the content and save it
CTRL + ALT + T

gksudo gedit /lib/udev/keymaps/msi-gt780dx
```
0xA8 prog1 # backlight key
0xBB media # movie key
0xBD prog3 # fan key
0xC2 ejectcd # eject key
0xD5 f24 # P1 key
```

Now we need to determine the keyboard details:
/lib/udev/findkeyboards
This should give you something along the lines of:
```
AT keyboard: input/event3
```
The important part here is input/event**3**

No that we know the event (and number), let's get the name:
dmesg | grep -i input**3**
This should give you something  similar to:
```
input: **AT Translated Set 2 keyboard** as /devices/platform/i8042/serio0/input/input3
```


Next step is to load this mapping during startup
gksudo gedit /etc/udev/rules.d/10-msi-sbar.rules
```
SUBSYSTEM=="input", ATTRS{name}=="**AT Translated Set 2 keyboard**", RUN+="/lib/udev/keymap input/event**3** /lib/udev/keymaps/msi-gt780dx"
```

Test this by running the command directly (i.e. no need to restart):
```
sudo /lib/udev/keymap input/event3 /lib/udev/keymaps/msi-gt780dx
```

Setup your newly mapped keys with (you can run the following from the terminal too):
gnome-control-center keyboard

And done.
Changing your backlight colour (KLM), you might want to look at:
[https://github.com/PaNaVTEC/MSI_GT_GE_Led_Enabler](https://github.com/PaNaVTEC/MSI_GT_GE_Led_Enabler)
(Didn't work 100%, wrong colours were displayed, so I changed the source and recompiled)

from
```
arguments[kLevel] = (unsigned char)argv[x + 1][0];
```
to
```
arguments[kLevel] = (unsigned char)argv[x + 1][0]** - 49**;
```

---

### Post by Shark711 on 2014-02-23
> **Shark711 said:**
> Changing your backlight colour (KLM), you might want to look at:
[https://github.com/PaNaVTEC/MSI_GT_GE_Led_Enabler](https://github.com/PaNaVTEC/MSI_GT_GE_Led_Enabler)
I've also added this execution to:
[LIST]
[*]/etc/rc.local - So it puts it on during start-up
[*]/etc/pm/sleep.d/ - New bash script to  switch it back on after it resume from sleep
[/LIST]

---

### Post by Shark711 on 2014-08-18
14.04 LTS

create a new file:
gksudo gedit /lib/udev/hwdb.d/61-keyboard.hwdb
```
keyboard:dmi:bvn*:bvr*:bd*:svn*:pn*:pvr*
 KEYBOARD_KEY_d5=prog1        # P1 key
 KEYBOARD_KEY_bb=media        # movie key
 KEYBOARD_KEY_bd=prog2        # fan key
 KEYBOARD_KEY_a8=prog3        # backlight key
 KEYBOARD_KEY_c2=ejectcd    # eject key
```

Update the Harware Database:
```
sudo udevadm hwdb --update
```

reboot

---

