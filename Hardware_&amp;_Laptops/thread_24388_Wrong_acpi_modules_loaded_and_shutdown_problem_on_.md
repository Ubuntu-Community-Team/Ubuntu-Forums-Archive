---
title: "Wrong acpi modules loaded and shutdown problem on Sony VGN A117"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by hypno on 2005-04-06
Hello together,
I installed Kubuntu on my Sony VGN A117 everything is fine except two problems:
When KDE starts up I get in short intervals onscreen menus with messages like "display off.." "brightness xx%" after long searching I made an lsmod and found 
there not only sony_acpi  but also asus_acpi, pcc_acpi after rmmod asus_acpi the maniac onscreen menus are gone. Tried to put asus_acpi in the hotplug blacklist but it wont work! 

Where can I remove the module so that it doesn't get loaded after a restart?

Another problem is that after a shutdown my laptop does not poweroff, how can I fix this?

Any help would be appreciated

---

### Post by soul_rebel on 2005-04-07
```
$cd /etc/modprobe.d
$sudo touch custom
$sudo nano custom
```
add this stuff:
```
alias pcc-acpi off
alias asus-acpi off
```
and any other you like
```
$sudo update-modules
```

Bye

---

### Post by hypno on 2005-04-07
Thanks, I will try it!

---

### Post by souki on 2005-11-03
same problem with Sony Vaio VGN-A517B and Breezy

the solution works

---

