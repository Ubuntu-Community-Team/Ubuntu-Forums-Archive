---
title: "noapic nolapic......why?"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by velozoom on 2006-10-29
Some noob questions- 

What do the boot parameters 'noapic' and 'nolapic' do, or undo as the case may be?  

What do I need to do to not have to edit the boot command each time I start up? 

Thanks!

---

### Post by picpak on 2006-10-29
Edit your menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Go to a line that looks like:

```
# defoptions=quiet splash
```

and at the end of it put:

```
noapic nolapic
```

Save it and exit. Then, run

```
sudo update-grub
```.

Enjoy!

---

### Post by velozoom on 2006-10-29
thanks, Pic, I'll do that asap....but but I'm still curious what those parameters do....

---

### Post by Night on 2006-10-29
[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

---

### Post by velozoom on 2006-10-29
Thanks Night.  Good info.

---

