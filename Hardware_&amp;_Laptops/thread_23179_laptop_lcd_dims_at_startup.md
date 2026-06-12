---
title: "laptop lcd dims at startup"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by Monkey Paws on 2005-03-31
Hi, I am a noob to ubuntu and this forum...

I have a emachines 6805 amd64 laptop and when it boots up, the backlight dims to min brightness.  I have to use fn+f8 to increase the brightness.  Is there any way to default the brightness on boot up?  Pressing fn+f8 several times each reboot is annoying. 
Is there a boot kernel switch I need to use???

Thanks

---

### Post by candc540 on 2005-04-01
[QUOTE=Monkey Paws]Hi, I am a noob to ubuntu and this forum...

I have a emachines 6805 amd64 laptop and when it boots up, the backlight dims to min brightness.  I have to use fn+f8 to increase the brightness.  Is there any way to default the brightness on boot up?  Pressing fn+f8 several times each reboot is annoying. 
Is there a boot kernel switch I need to use???

Thanks[/QUOTE]
 try acpi=off 

if that fixes the problem, then you have issues with acpi.

---

### Post by Monkey Paws on 2005-04-02
The acpi=off did kept the lcd form dimming.  Thanks... :razz: 

Ok, what do you think could be wrong in the acpi??

Thanks
MP

---

