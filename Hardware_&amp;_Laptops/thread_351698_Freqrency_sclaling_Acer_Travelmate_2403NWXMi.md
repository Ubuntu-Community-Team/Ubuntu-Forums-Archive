---
title: "Freqrency sclaling Acer Travelmate 2403NWXMi"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by stitchie on 2007-02-02
Hello everyone,

I am having a problem with freq scaling using Ubuntu 6.10 on my laptop.
I managed to get it working, bu the only way to force it is:

1. using this command
sudo modprobe p4-clockmod
2. installing kpowersave (which also installs powersaved at the same time) using synaptic

It all seems to work perfectly (even the hibernation and suspend features).

Then I restart my computer.

And when booting ubuntu I get a message that freq scaling is not supported.
To make it work again I have to uninstall kpowersave and powersaved and start it all aver again.

Could anyone help me with this problem ?

Regards

---

### Post by stitchie on 2007-02-02
Guys, anyone ? Please .....

---

### Post by stitchie on 2007-02-03
Hello ?
Maybe you know other freqrency managers which I could use ?

---

### Post by stitchie on 2007-02-04
I added "p4-clockmod" to my /etc/modules and it works.
Maybe it is useful for somebody.
Still, the kpowersave does not start automatically (I tried to add it everywhere .......)
but the main problem is solved.

I wonder why I did not get a reply from anyone .....

---

