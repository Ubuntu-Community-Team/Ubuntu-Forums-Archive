---
title: "Use Fn+F6 to toggle Bluetooth on ThinkPad T42?"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-10-23
On an IBM ThinkPad T42, I've been trying to use the scripts in message #2 in this thread

[http://www.ubuntuforums.org/showthread.php?t=25453](http://www.ubuntuforums.org/showthread.php?t=25453)

to enable Fn+F6 for use in toggling Bluetooth (Fn+F5 toggles all wireless, including WiFi, and that isn't what I want). I can't get these to work (even after changing the shell from sh to bash), and I'd be grateful for any advice on what needs to be done.

Many thanks for any help

---

### Post by emendelson on 2005-10-24
OK, I've figured out that these scripts will work if this command is given first from a root terminal:

```
echo 0xffff > /proc/acpi/ibm/hotkey
```

But I can't figure out how to make this run at startup after acpid loads. I've tried putting it that command in an executable script in init.d, and using "sudo update-rc.d scriptname 99 ." to make it run very late during bootup, but that doesn't seem to be good enough. The script itself works when I run it as sudu after logging in - but how would one assure that it runs as root, and after acpid loads?

---

### Post by zielony on 2008-05-11
try to add this into /etc/rc.local

---

