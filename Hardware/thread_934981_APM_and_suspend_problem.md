---
title: "APM and suspend problem"
date: 2008-10-01
forum: Hardware
---

### Post by grw on 2008-10-01
Hi, 

I have been trying to get my old Dell Inspiron 2500 laptop to suspend. I am running 8.04. No luck. And now I get an fsck failed message on start up.

This is what I did (following another thread):

1) Added 'noacpi acpi=off apm=on nolapic' to kernel options in /boot/grub/menu.lst (also tried acpi=off between ro and quiet - this is what I used to have to do with previous versions of Ubuntu to stop sudden power off probs)
2) Added 'apm' to /etc/modules
3) Created a file /etc/modprobe.d/power with the following line: options apm power_off=1 realmode_power_off=1

The problem:
During restart I get a message saying fsck failed ... exited with signal 11 ... fsck dies with exit status 8.

I press CNTL D to restart and edit the menu.lst kernal options, removing acpi=off, and teh computer boots up. But no suspend.

Any ideas?

Gwyn

---

### Post by pihhan on 2008-10-01
Are you sure turning off acpi is good idea? I dont know how old is laptop you are trying to suspend, but APM is deprecated and not enough supported. No new features are added to APM support for some years i think. If computer is not old 5 years or older, APM is not thing that should help you, acpi is right technology.

If you have problems with acpi, it can be fixed maybe by correcting acpi tables. I dont think APM is way to go, but i dont have experience whith Dell laptop myself.

If you have crashing fsck (that is signal 11), you have a problem. If another run does not fix that, you might need reinstall system, as it might get corrupted.

---

### Post by grw on 2008-10-01
Thanks Petr. My computer is 7 years old. (Too old, perhaps!) It doesn't work with acpi. So APM is the only option it seems.
Gwyn

---

### Post by grw on 2008-10-02
bump!

---

### Post by grw on 2008-10-07
No one can help?

---

