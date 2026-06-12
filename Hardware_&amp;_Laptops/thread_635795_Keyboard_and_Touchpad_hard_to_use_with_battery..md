---
title: "Keyboard and Touchpad hard to use with battery."
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by lszanto on 2007-12-09
On my new benq joybook a52 I have found the problem that even if my battery is fully charged my touchpad and keyboard and really hard to use and take alot of pressing and force just to press one key, is there anyway to fix this as I don't like having to have my computer plugged in all the time.

Thanks for any help, Luke.

---

### Post by lszanto on 2007-12-09
*BUMP* Nobody?

---

### Post by lszanto on 2007-12-11
> **lszanto said:**
> *BUMP*  Nobody? Hasen't anybody else had this problem?

---

### Post by szaddam on 2007-12-11
I have the same problem with the same type of laptop (benq joybook a52).
The keyboard and the touchpad don't work correctly after I unplug or plug the power cord. If I don't change the source of the power it mainly works normally.

The problem doesn't have effect to my USB mouse. It always works correctly.

The problem doesn't exist if I boot windows.

Thanks in advance.
Adam

---

### Post by Computer_playa666 on 2007-12-11
so its your keyboard thats not working?

---

### Post by Computer_playa666 on 2007-12-11
The only thing i can think of is sticky keys.

---

### Post by szaddam on 2007-12-11
Thanks for the quick reply.

Yes my keyboard lags after unplug the power cable.
And my touchpad does the same behaviour.
My USB mouse works correctly.

---

### Post by szaddam on 2007-12-11
Thanks for the advice,
I've checked, but the keyboard accessibility features are not enabled.

---

### Post by szaddam on 2007-12-14
I've figured out something:

The problem source is in the acpi battery module. If I turn off it, the keyboard & touchpad problem go away. But In this case I can't monitor my battery status and so on.

lszanto: You can turn it off if you edit with sudo the next file: /etc/default/acpid
You have the change the line:
MODULES="all"
to
MODULES="ac processor button fan thermal"

Anybody has an idea how can the battery module run without this keyboard touchpad problem?

Thanks

---

### Post by antario91 on 2008-01-16
Hi, Guys,
I have exactly the same problem with the same laptop. I tried it on several Linuxes, but none worked (Fedora 8, Mandriva 2008, openSuse, Ubuntu, Kubuntu, Debian, Red Hat, Linux Mint), although the acpi worked in DesktopBSD and Windows. It would be a good idea, to report as a bug. Maybe this laptop's battery acpi is different. And it would also be good, if this could be repaired in version 8.04. I wonder why this problem consists...

Ok, now I found something. The Ubuntu Launchpad archive also lists this bug for a joybook a53. It says, that the problem is with the HAL. Can anybody explain this to me? :D
More info: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/152633](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/152633)
 Zsolt

---

