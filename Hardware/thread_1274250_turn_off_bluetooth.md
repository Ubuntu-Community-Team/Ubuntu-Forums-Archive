---
title: "turn off bluetooth"
date: 2009-09-24
forum: Hardware
---

### Post by barnskybeat on 2009-09-24
since a couple of days I am searching in all types of ubuntu fora to find a simple solution to turn off my bluetooth (lenovo X61s, ubuntu 9.01) but none of the provided solutions seem to work. Since I never use any bluetooth devices I am simply after a "turn off". Even if the service is stoped the bluetooth indicator light remains on. the hardware switch turns of both wifi and bluetooth and thus this does not doe the trick!

---

### Post by barnskybeat on 2009-09-24
fund the solution for thinkpad in another thread:

echo disable >/proc/acpi/ibm/bluetooth

---

### Post by pmlxuser on 2009-09-24
> administration > services > bluetooth device management 

unlock...
unselect it....
does that work.

---

### Post by swoody on 2009-09-24
barnskybeat, That's good to hear you found a solution. Have you tried looking into your BIOS to see if there's an option to disable Bluetooth? I don't know if you're looking for something easier, that you can switch on/off while in Ubuntu, or if you're not planning on using Bluetooth, you can do something a little more permanent in the BIOS.

---

### Post by barnskybeat on 2009-09-24
no,tired that first

---

### Post by barnskybeat on 2009-09-24
found a post from neocortex which worked but I have no idea what I have actually been doing, just logged in as root and did what i was told to do :-)

[http://ubuntuforums.org/showthread.php?t=1199813&highlight=echo+disable](http://ubuntuforums.org/showthread.php?t=1199813&highlight=echo+disable)


 SOLVED: Bluetooth is always on at (re)boot, but why?!
Hello,
With the help from nice people of ThinkPad helping list, I managed to (re)boot with the bluetooth disabled, but with possibility to turn it on. In brief, only thing that needs to be done is to add the following line at the end of "/etc/init.d/rc.local":
Quote:
echo disable > /proc/acpi/ibm/bluetooth
All acknowledgements goes to Richard Neill!

Best,
PM

---

### Post by barnskybeat on 2009-09-24
thanks swoody,for the hint, will check it out.

---

