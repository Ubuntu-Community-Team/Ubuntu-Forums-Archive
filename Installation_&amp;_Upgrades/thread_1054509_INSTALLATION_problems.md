---
title: "INSTALLATION problems"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by (b)ananartista on 2009-01-29
i'm new in the linux world.

while i'm installing ubuntu on my computer i have this error:
"the display server has been shut down about 6 times in the last 90 seconds.
it is likely something bad is going on.
.... "

i've already tried two times the installation.
i've checked the cd and it's ok.
ubuntu live without installation works.

what can i do?


help me please.


thanks

---

### Post by taurus on 2009-01-29
What kind of graphic card do you have?  What kind of monitor do you have?  What's the spec of your machine?

---

### Post by (b)ananartista on 2009-01-29
> **taurus said:**
> What kind of graphic card do you have?  What kind of monitor do you have?  What's the spec of your machine?

graphic card: radeon 9200
monitor: acer al1716
motherboard: asus a7v600

---

### Post by (b)ananartista on 2009-01-29
so what i have to do?


thanks

---

### Post by spcwingo on 2009-01-29
You can try booting into recovery mode and choosing xfix.

---

### Post by spcwingo on 2009-01-29
I just thought of something else.  If xfix doesn't work you can reboot into recovery mode and drop out to the root terminal and enter:

```
nano /boot/grub/menu.lst
```

When nano opens scroll down to the section that looks like this:

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

and add:

```
xforcevesa
```

to you kernel line.  It should now look something like this:

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro [COLOR="Red"]xforcevesa[/COLOR] quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```

Let us know if any of this helps.

---

### Post by (b)ananartista on 2009-01-30
how can i go to recovery mode while i'm installing ?

cause i can't finish installation ...

---

### Post by spcwingo on 2009-01-30
I misread your post.:oops:  Have you tried booting into safe graphics mode (it's doing the same thing, but from the live CD)?

---

