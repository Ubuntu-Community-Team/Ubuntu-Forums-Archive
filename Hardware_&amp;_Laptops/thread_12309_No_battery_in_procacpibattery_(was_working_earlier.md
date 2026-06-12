---
title: "No battery in /proc/acpi/battery (was working earlier!)"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-01-23
I'm using hoary on a Panasonic R1, and had the battery monitor working just fine under hoary (and warty)--but at some point (I don't remember if it was an update, or if it was me getting the screen dimming to work), the battery just disappeared?! Now when I try to find it, I get the following:

dean@lappy:/etc/acpi$ ls -l /proc/acpi/battery/
total 0

I have tried moving the entire acpi directory to acpi.old, and completely uninstalling acpi, acpid, and acpi-support in synaptic, and then reinstalling them. I still have the same problem :(

Does anyone have any advice?

Thanks,
Dean

---

### Post by ceekay on 2005-01-24
Do you need to add acpi=on or acpi=force to your /boot/grub/menu.lst to get acpi turned on? I know on my thinkpad 600x I have to force ACPI on to make it work.

---

### Post by ming0 on 2005-01-24
I have never had to do either of those, but just to rule them out--I tried them :)

Unfortunately, neither of them worked...

Thanks tho :neutral:

---

### Post by stateq2 on 2005-02-02
same problems here....worked fine in warty...after hoary...no battery detected :confused:

---

### Post by Jspired on 2005-02-02
Mine was working until today, but suddenly...no battery detection either.  I'm on a Toshiba Satellite.

---

### Post by ming0 on 2005-02-02
You just need to roll back which kernel you are using... 

Check this thread for details:

[http://ubuntuforums.org/showthread.php?t=12317](http://ubuntuforums.org/showthread.php?t=12317)

Good Luck :)

---

### Post by ming0 on 2005-03-02
This issue seems to have been fixed, so if you're on backports or hoary--I'd try updating the kernel, and see what happens :)

---

