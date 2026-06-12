---
title: "Battery Problems on a Gateway M275"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by boyfromthedwarf9 on 2006-06-07
I have a Gateway M275 with Dapper.  I had to disable ACPI to get it to boot up.  Now Ubuntu says I am plugged in, even when I unplug it.  It still works unplugged though.

---

### Post by unique on 2006-06-07
I also have this same problem with my Convertable Gateway M275. In breezy I also had to add the acpi=off to grub to get it to boot and the power manager applet was working correctly. Dapper however tells me that there is no battery detected and the applet always shows me a running on ac. I also had no probs with the same version if gnome-power-manager on Fedora core 5.

Any insight would be really be of help!
Sucks cause this is the only thing not working on my lappy.


TIA -Unique

---

### Post by boyfromthedwarf9 on 2006-06-08
I forgot to mention, when I had ACPI on, when installing Dapper and just now when I changed the boot menu options, I got a kernel panic before seeing the Ubuntu loading screen.

---

### Post by Augi on 2006-06-08
Any possible fix would be helpful, I have the same problem on my M275 notebook as well. Other than that though everything works great!

---

### Post by unique on 2006-06-18
Ok guys I have a fix!

I followed this thread [How To Compile the new 2.6.16 kernel from kernel.org]("http://ubuntuforums.org/showthread.php?t=157560")  After I did that I was able to remove apci=off from my boot grub menu.list and it worked! Even the gnome-power-manager battery applet worked! The only thing I had to do was copy the ipw2200 firmware to my /lib/firmware dir and then my wireless was back!

---

### Post by boyfromthedwarf9 on 2006-06-28
Anyone know how to fix this, without installing the unstable kernel?  Any idea when 2.6.17 comes out?  (I heard that the odd number ones are stable, and the evens are unstable.  Or do I have it backwards?)

---

### Post by patrickfromspain on 2006-06-28
2.6.16 is stable, the same as 2.6.17. The  unstable ones are 2.5.x, 2.7.x etc..

---

### Post by boyfromthedwarf9 on 2006-06-28
Oh, ok, I was confused.  Any idea how long until kernel 2.6.16 is released through updates?

---

