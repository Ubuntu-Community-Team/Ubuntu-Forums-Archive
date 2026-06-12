---
title: "Can I seperate my Up/Down volume key?"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by Kanucker on 2007-11-15
Hello all, this is my first time trying for support in the community, so be gentle! I am having a hardware issue on a GRT 100 Sony laptop. It pertains to my hardware volume key. They both seem to be bound to the same command "XF86LaunchA" up and down both return this same accelerator. Is there some way i can help ubuntu recognize the difference between the 2?

Thanks in advance if anyone can toss me a bone!

---

### Post by Linicks on 2007-11-15
In a console run:

```
lshal -m
```

This will report 'reported' key presses;  press the required keys to see output... post the output in here so people can see to help.

Nick

---

### Post by Kanucker on 2007-11-16
> In a console run:

Code:
lshal -m

Did this, thanks Nick. Here are the results for the button presses.
These are laptop volume buttons. Not the regular keys.

Start monitoring devicelist:
-------------------------------------------------
16:13:44.566: computer_logicaldev_input_4 condition ButtonPressed = prog1 -- 1st key press V-down
16:13:44.770: computer_logicaldev_input_4 condition ButtonPressed = prog1 -- 1st key press V-down
16:13:46.383: computer_logicaldev_input_4 condition ButtonPressed = prog1 -- 2nd key press V-up
16:13:46.682: computer_logicaldev_input_4 condition ButtonPressed = prog1 -- 2nd key press V-up
16:13:52.096: acpi_BAT1 property battery.charge_level.rate = 99 (0x63)
16:13:52.102: acpi_BAT1 property battery.voltage.current = 16559 (0x40af)
16:13:52.105: acpi_BAT1 property battery.reporting.rate = 99 (0x63)

They are both recognized as the same input in the "key input" assigner. I can assign one of them, and it works, but if i try to assign the second, the manager tells me the button is already assigned.

---

### Post by Linicks on 2007-11-16
Sorry, I don't know, but for info, here is the volume keys on my Dell Inspiron 6400:

[09:21:53.563: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = volume-down
09:21:55.641: platform_i8042_i8042_KBD_port_logicaldev_input condition ButtonPressed = volume-up

All the external keys work fine here.

Nick

**EDIT**

Actually, if you run:

gnome-keybinding-properties

here is what it has bound to my keys:

Volume UP:   0xb0
Volume Down:  0xae

Try those.

Nick

---

### Post by Kanucker on 2007-11-17
Hi Nick,

Thanks for the reply, I appreciate the help.

Originally, they up down volume keys did nothing. I went to the key bindings and tried to associate. It worked, but both keys make a call to the same things in software. I need a way to tell gutsy they are not the same key.

XF86LaunchA is the binding gutsy sees for both up and down on the frame (it's below my touch pad)

---

### Post by Kanucker on 2007-11-22
bump

---

