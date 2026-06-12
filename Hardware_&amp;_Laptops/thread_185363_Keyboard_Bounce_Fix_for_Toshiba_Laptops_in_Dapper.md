---
title: "Keyboard Bounce Fix for Toshiba Laptops in Dapper"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by Technoviking on 2006-05-31
The fix for the Synaptics bug that causes the keyboard to print multiple characters on some Toshiba laptops no longer works on Ubuntu Dapper 6.06. This is because the nvidia module is no longer loaded by /etc/modules.

The easiest workaround I have found is to add the following lines to /etc/rc.local:
```
modprobe -r psmouse
modprobe psmouse rate=40
```
This sets the psmouse rate after the nvidia module is loaded.

---

### Post by RobertH on 2006-06-17
After I did this I had to change the order that rc.local was executed
I had to rename the symlinks
**S99rc.local**
in the directories
[B]/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d[/B]
to
**S12rc.local**

The links had to be renamed so that this happens before gdm starts because if this is done afterwards then X does not detect the synaptics driver properly and the touchpad loses much of its functionality.

---

