---
title: "problem with FN brithness"
date: 2008-11-13
forum: Hardware
---

### Post by alain57 on 2008-11-13
Hello,
i bought a netbook (samsung NC10)
by default the FN brightness won't work, but after searching i found out a way to make them work, **but there are 2 problems**

i added this to the /etc/rc.local file

```

setkeycodes e009 224
setkeycodes e008 225

```
i found the first number with dmesg and the second one with /usr/include/linux/input.h


the keys now work, but with TWO problems

first one, the brightness go to minimum or maximum even if i only decrease or increase by 1

second one : the keyboard is like frozen, i need to do a CTRL + ALT + F1 to switch to a console and then switch back to graphical mode to have the keyboard again


any idea what i need to do to correct ?

ps: sorry for my bad English, i'm french

---

### Post by Jon Bradbury on 2008-11-21
I have the same problem.

It appears as if the nc10 brightness keys (fn-up / fn-down arrow) don't send key relase events for some reason, so the operating system thinks you have held the button down.

Does this work in the console as well? I read it was OK in console but behaved as you say in the desktop. I also suffered a keyboard lockup.

---

### Post by alain57 on 2008-11-21
yes it work well in console
i open 2 bug report, one for ACPI
and one for xorg intel driver

it apears that it is not an ACPI bug
for the driver, there are no answer :(

i also saw a bug report for gnome-power-manager and i upload a verbose file hopping this will help

---

