---
title: "Function Keys don't work in Ubuntu 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by mdd5 on 2010-05-03
Hi there,

I have a Sony Vaio Laptop, VGN-CR354.

On Ubuntu 9.10, the function keys were working correctly.

However, on Ubuntu 10.04, when I try to increase\decrease the brightness using the function keys,  OSD appears but **nothing is changing**.

Could anyone help me?

---

### Post by mdd5 on 2010-05-03
Anybody??

---

### Post by pschroth on 2010-05-03
Same problem here on an hp 6830s. No solution until now.

---

### Post by mdd5 on 2010-05-03
The problem is, the keys are working perfectly in Ubuntu 9.10 .

I don't know why they are not working in the new Ubuntu 10.04 (Lucid).

Now when I try to change the brightness, the OSD appears but neither the OSD nor the brightness is  changed.

---

### Post by pschroth on 2010-05-03
Here the same. In 9.10 working. When i install the ATI fglrx drivers no brightness settings, but after uninstall I can use the Brightness applet, but not the keys.

---

### Post by hsoulen on 2010-05-03
Hey Guys,

Try adding "acpi_osi=linux" (without quotes) to your grub entry for the default Linux entry.

You can "try it before you buy it" by adding it at the grub menu during boot and see if it works for you before you edit grub.

Cheers,

Hank

---

### Post by pschroth on 2010-05-03
Already tried. Not solved.

---

### Post by mdd5 on 2010-05-03
Not Working here too.

---

### Post by dreadwarrior on 2010-05-03
@pschrot: I also have a HP 6830s and brightness keys don't work, too.

Furthermore, if I run a while without power cord plugged in, the brightness is at 100%.
If I attach the power cord because of battery running low, 
the brightness gets decreased to ~30%.

```
less /etc/proc/acpi/video/DGFX/LCD/brightness
```shows (also after increasing/decreasing value with Fn-keys "100").

@pschrot: Can you confirm the location /etc/proc/acpi/video/DGFX/LCD/brightness for your system?

Anyway, I've created a shell script in my home directory with the following content:

```
#!/bin/bash
echo 100 > /proc/acpi/video/DGFX/LCD/brightness

```As I'm running Compiz, I've created at Shortcut in CompizConfig Configuration-Manager and bound it to the Fn-F8 key.

---

### Post by hsoulen on 2010-05-03
> **pschroth said:**
> Already tried. Not solved.

Sorry the ACPI trick did not work.

You can try running xev to see if the special keys are recognized by input, just open a terminal and type "xev":

$xev (don't need to be root).

You will then see some output in the terminal, it will also display a small box next to the terminal which records mouse input. Try hitting the special key/keys (if fn is required) and see if there is output in the terminal e.g.

FocusIn event, serial 37, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

If this works then you can probably use the gnome keyboard shortcuts app (assuming gnome) to re-map the keystroke.

System->Preferences->Keyboard Shortcuts

Look for the action (brightness up/down, volume etc.), click on the current assigned shortcut on the left and when it is highlighted click the button or key combo you want to assign.

If you get no xev output for the button then you are kind of up the creek. For me, the combination of ACPI kernel parameter plus the Keyboard Shortcuts app worked, but depends on the laptop.

Hope this works for you.

Hank

---

### Post by dreadwarrior on 2010-05-04
> **hsoulen said:**
> For me, the combination of ACPI kernel parameter [...] worked [...]

Hello hsoulen,

which ACPI kernel parameter did you use?

**SORRY, saw that you've posted it before. You used "acpi_osi=linux".**

---

### Post by pschroth on 2010-05-04
Out frustation about the acpi issue reverted to 9.10. Waiting for a bug fix.

---

### Post by mdd5 on 2010-05-04
Hey Hank,

I did try xev in terminal, it show me something similar when I press the function key.

So I went to the "Keyboard Shortcuts" window

And I tried to find Brightness Up/Down actions, but I did not find it.

I guess I can't change them in Ubuntu 10.04, you as the help stated.

I also try to follow the instructions in [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting), which is similar to your way.

But I can't find the brightness up/down to re-map the keys.

---

### Post by mdd5 on 2010-05-04
Is it a bug??

Is Ubuntu 10.04 no longer  supports the hardware??

---

### Post by 00arthuryu on 2010-05-05
Same problem here with 10.04 :(

---

### Post by leithon on 2010-05-07
> 

Anyway, I've created a shell script in my home directory with the following content:

Code:
#!/bin/bash
echo 100 > /proc/acpi/video/DGFX/LCD/brightness
As I'm running Compiz, I've created at Shortcut in CompizConfig Configuration-Manager and bound it to the Fn-F8 key.


It doesn't work for me, permission denied.

---

### Post by Hausi on 2010-05-07
Hi, I have an old Latitude C610 and for me the brightness controls work but _only_ with the Ubuntu kernel. As soon as I compile my own 2.6.34 kernel there is no more brightness control apart from going the CTRL-ALT-F1 way.
In both cases xev does not see the function keys.

I hope that somebody has figured out the diffs between the dist kernel and kernel.org one.
_Hans

---

