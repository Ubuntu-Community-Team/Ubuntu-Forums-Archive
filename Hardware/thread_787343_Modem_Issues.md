---
title: "Modem Issues"
date: 2008-05-08
forum: Hardware
---

### Post by King Buttons I on 2008-05-08
I have a pci modem and have the drivers for it, but I can't figure out what port it is. Can somebody help me?
Buttons

---

### Post by Whiffle on 2008-05-08
Should be something along the lines of /dev/ttyS0 

You could try removing the kernel module with modprobe -r, and then reinserting it with modprobe, and then running dmesg.  Usually it will put a couple of lines in dmesg that tell that device something is.

---

### Post by King Buttons I on 2008-05-08
Whiffle
What kernel module am I supposed to remove and reinsert?
Buttons

---

### Post by Whiffle on 2008-05-08
Oh, I assumed you knew since you said you had the drivers.  What kind of modem is it?

---

### Post by King Buttons I on 2008-05-09
I figured out what kernel module to remove and reload. Is there a certain part of dmesg that I will need or will I need all of it. If I need all of it can you tell me how to display the entire output of dmesg, whenever I run it I only get part of it.
Button

---

### Post by Whiffle on 2008-05-09
It should show up at the end of dmesg.

---

### Post by King Buttons I on 2008-05-09
Here is the latest output from dmesg after loading and unloading the module.
```
[87055.744934] martian loaded - 20061202
[87055.745661] PCI: Found IRQ 9 for device 0000:02:0b.0
[87055.745682] PCI: Sharing IRQ 9 with 0000:00:1f.4
[87055.745696] PCI: Sharing IRQ 9 with 0000:02:0a.1
[87055.745737] "martian_dev": added device 11c1:44e BaseAddress = 0xd000, CommAddres = 0xd400, irq = 9

```

---

### Post by Whiffle on 2008-05-09
[http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)

According to that, it should be /dev/SM0.  Do you have the martian_modem program running?

---

### Post by King Buttons I on 2008-05-10
Thanks Whiffle it worked. Do you know of any way to keep martian_modem running without keeping the terminal open?
Buttons

---

### Post by Whiffle on 2008-05-10
add it to /etc/rc.local, then it will run on bootup.  I think it should looks something like this


martian_modem &

---

### Post by King Buttons I on 2008-05-11
Thanks Whiffle everything works fine.
Eric

---

