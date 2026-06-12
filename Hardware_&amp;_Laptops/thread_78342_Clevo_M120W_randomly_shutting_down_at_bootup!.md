---
title: "Clevo M120W randomly shutting down at bootup!"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by sneax on 2005-10-18
Ok, my laptop randomly shuts down. I once had a glimpse of these letters on screen: "critical temperature reached, shutting down ...".

Now I have a few questions:
- Can I stop linux for checking my temp and so prevent it from shutting down?
- It's a Centrino laptop, isn't the temp/fan regulated by the hardware?
- How would I go at disabling this 'feaure' that is causing me trouble?
- What would a regular Ubuntu/linux user advice me to do? Please don't say revert to Hoary :(

Hoary worked fine, I'm trying to do a clean install of Breezy but often it would shut down even while installing (after the first reboot)!

Thanks in advance for any help I get!

---

### Post by sneax on 2005-10-19
Anyone? :(

---

### Post by civilwarlord on 2005-10-19
Some people have had success with using acpi=off

---

### Post by sneax on 2005-10-19
Yes but how exactly would I go at doing that?

---

### Post by civilwarlord on 2005-10-19
This may or may not help.  If it doesn't it can always be undone.

if your laptop can stay on long enough, try this

go into a terminal
sudo nano /boot/grub/menu.lst
look for the # kopt= line and add acpi=off to the end
Press Ctrl-X
Press Y
Press Enter
sudo update-grub (this will append the acpi=off to the kernel lines)
reboot



Also, I read on some site where a person removed the thermal module from the MODULES line in /etc/default/acpid.  I don't think you'd have to do the acpi=off thing if you did this.

---

