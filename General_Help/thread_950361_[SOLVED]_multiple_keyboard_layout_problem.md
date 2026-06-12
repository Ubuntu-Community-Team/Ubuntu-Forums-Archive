---
title: "[SOLVED] multiple keyboard layout problem"
date: 2008-10-17
forum: General Help
---

### Post by giuspen on 2008-10-17
Hi, I have the default keyboard layout set ITALIAN and second layout is RUSSIAN. Every time I reboot, the russian layout gives me fake letters instead the normal kirillik; to solve the problem I have to all the time remove and re-add the russian layout.
I think this is a bug... If anybody had the same problem and was able to solve with some workarounds, please tell me.
Bye and thanks.

---

### Post by loomsen on 2008-10-17
Which one is configured in your xorg.conf? Most likely this will be the best solution, not even a workaround :)

---

### Post by Elfy on 2008-10-17
+1 I would make sure both are in the keyboard section of your xorg.conf, if it's not there add it in.

Mine looks like

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "uk"
Edit file and change Xkblayout to suit,

```
sudo nano -B /etc/X11/xorg.conf
```
Ctrl+O, enter to save, Ctrl+X to exit

---

### Post by giuspen on 2008-10-17
> **forestpixie said:**
> +1 I would make sure both are in the keyboard section of your xorg.conf, if it's not there add it in.

Mine looks like


Edit file and change Xkblayout to suit,

```
sudo nano -B /etc/X11/xorg.conf
```
Ctrl+O, enter to save, Ctrl+X to exit


So I have to be sure to have something like

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
Option "XkbLayout" "ru"

Did I understand good?
I will try this in evening, now I'm in office. Thanks a lot.

---

### Post by loomsen on 2008-10-17
Kinda...

```

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it,ru"

```

now you gotta specify how you want to change your layout. 

For instance, you could use shift+Alt to toggle. Then append
```

Option "XkbOptions"  "grp:alt_shift_toggle"

```

You may also specify an indicator. You could either use gnome-panel application, or, if you removed your gnome-panel like I did, you could specify a LED - given you're using a notebook - or write a script to draw an icon on your desktop or such.

```

Option "XkbOptions"  "grp:alt_shift_toggle,grp_led:caps" ## would make your caps lock light up
Option "XkbOptions"  "grp:alt_shift_toggle,grp_led:num"  ## would make your num-lock light up

```

and so on...

Take a look at the manual pages of X for many many many more options to handle your X. Group handling should be what you want to read for this issue tho.

---

### Post by giuspen on 2008-10-17
> **loomsen said:**
> Kinda...

```

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it,ru"

```

now you gotta specify how you want to change your layout. 

For instance, you could use shift+Alt to toggle. Then append
```

Option "XkbOptions"  "grp:alt_shift_toggle"

```

You may also specify an indicator. You could either use gnome-panel application, or, if you removed your gnome-panel like I did, you could specify a LED - given you're using a notebook - or write a script to draw an icon on your desktop or such.

```

Option "XkbOptions"  "grp:alt_shift_toggle,grp_led:caps" ## would make your caps lock light up
Option "XkbOptions"  "grp:alt_shift_toggle,grp_led:num"  ## would make your num-lock light up

```

and so on...

Take a look at the manual pages of X for many many many more options to handle your X. Group handling should be what you want to read for this issue tho.

Thanks a lot, in the evening I will try.
Giuseppe.

---

### Post by giuspen on 2008-10-17
ok this is what I made:

sudo gedit /etc/X11/xorg.conf

and the lines that I edited:

Option "XkbLayout" "it,ru"
Option "XKbOptions" "grp:ctrl_shift_toggle"

it works good, with the switching enabled by control + shift
except for the gnome panel applet "keyboard indicator" that 
doesn't work anymore, so I removed it

finally I found that this is a bug:
[https://bugs.launchpad.net/xorg-server/+bug/228196](https://bugs.launchpad.net/xorg-server/+bug/228196)
that seems to be fixed in 8.10

---

### Post by loomsen on 2008-10-17
Worked? Good.

---

