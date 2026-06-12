---
title: "laptop over heating when AC disconnected"
date: 2009-10-21
forum: Hardware
---

### Post by selectstar on 2009-10-21
I have Ubuntu Jaunty updated to the latest updates
it's just a few weeks that I have installed it (before I was using Vista)
I noticed that the laptop overheats when I disconnect the battery charger. The system monitor utility shows that temperatures reach 80 C
whereas when mains power is attached temperatures reach maximum 50 C

Is there anything I can do?

---

### Post by selectstar on 2009-12-03
I know nobody answered. But I thought of keeping this thread updated in just in case....

I am still having exactly the same problems even now that I have upgraded to Ubuntu 9.10.
To correct what I said in my previous post. The problem occurs every time that the system recovers from suspend mode or hibernate mode. Independetly if the battery charger is connected or not

I have logged the bug on the launchpad website [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491139](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491139)

Hope some Linux 'guru' could give this issue a look :)

---

### Post by trundlenut on 2009-12-03
this problemm could relate to ACPI, I had some problems on my toshiba laptop initially and I cured it by adding something along the lines of acpi_os=linux to the the appropriate lines in grub and then in menu.lst to make it permanent.

IIRC on my laptop the fan wouldn't start until temperature got quite high and then the fan would run at full blast.  Don't forget though that temperatures in laptops tend to get higher than in desktop machines simply beacuse of the construction and ventilation of them.

There have been quite a few threads on this, try searching and you should find the information you are looking for.

---

### Post by selectstar on 2009-12-03
Hi trundlenut. I have already done a lot of research but haven't found anything directly related to my problem or haven't found anything that could solve the problem.
I do not think that 90 centigrade degrees is an acceptable temperature, also considering that running Windows Vista the temperature is never above 55 centigrades.

Anyway I will definitely try your suggestion chaning something in grub. Thank you

---

### Post by trundlenut on 2009-12-03
trying adding 

```
acpi_osi=Linux
```

to the appropriate entry in grub, you can go into the grub menu on booting and add it in manually just to see if it makes any difference and then add it in to the correct place in menu.lst if it works OK

---

### Post by selectstar on 2009-12-03
thanks trundlenut
I have tried following your advice but the issue is still there. As soon as I recover from standby mode the CPU temp rises up to 85-90 centigrades

---

