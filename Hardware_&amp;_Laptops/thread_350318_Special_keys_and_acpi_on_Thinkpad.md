---
title: "Special keys and acpi on Thinkpad?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by Lari on 2007-01-31
I'm quite a newbie with Kubuntu 6.06 on my Thinkpad a22p and wondering how to get special keys work, e.g. Fn-F3, Fn-F7 with ibm_acpi. Fn and F3 should blank the screen, Fn and F7 should enable the external display etc.

I've read the instructions, but I would need a more specific help. I've followed instructions fromhttp://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2004-December/022325.html

I added these lines to /etc/rc.d/rc.local:

```
# modprobe ibm_acpi
# echo enable > /proc/acpi/ibm/hotkey
# echo 0x1003 > /proc/acpi/ibm/hotkey
```

Created config file /etc/acpi/events/ Fn-F3.conf

```
event=ibm/hotkey HKEY 00000080 00001003
action=sh /etc/acpi/actions/Fn-F3.sh
```

There was no other -conf files in that directory, so I wonder if it's the right one.

I want the Fn-F3 combination to blank the screen, so I continued nevertheless. Created

/etc/acpi/actions/Fn-F3.sh

```
xset +dpms
xset dpms force off
```

But nothing happens.

Any ideas?

Lari

---

### Post by gnychis on 2007-06-14
i don't know if you're still active, but maybe someone else will search this post in the future

i asked this before on LKML and the xorg mailing list, and the general response was that its because the acpi daemon is not tied to the X process, and so when it executes these commands it does not know what X session to use ... unlike when you execute them they work because you're tied to an X session

---

