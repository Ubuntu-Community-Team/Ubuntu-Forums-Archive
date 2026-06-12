---
title: "Prevent second IDE drive from sleeping."
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by ex-slacker on 2007-01-10
hi all,

in my ubuntu (6.10) i have second IDE drive. If there are no disk activity, he goes in standby.

But i dont want it. I need time-to-time some stuff from there and it is not good for drive "healthy" :p .

Does it some userland process or ubuntu kernel?

PS. In my slack it was never happen.

thx in advance

---

### Post by simonn on 2007-01-10
Install hdparm

```

$ sudo apt-get install hdparm

```

Use hdparm to set the time out. You may want to put this in an init script e.g. /etc/rc.local to make sure that it is still in effect after a reboot.

```

$ hdparm -S 0 /dev/[drive e.g. hda, sda etc]

```

See man hdparm for more info.

---

