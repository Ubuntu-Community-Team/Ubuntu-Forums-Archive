---
title: "This is very simple: access disk partition"
date: 2010-03-06
forum: Hardware
---

### Post by ExScientiaVera on 2010-03-06
My disk has two partitions: C:\ where Windows7 is currently installed and D:\ where Ubuntu is installed. For some reason I can't access D:\ when I0m using Ubuntu. Does anyone know why?

Stay well.

---

### Post by IcarusR on 2010-03-06
From what OS are you trying to access the drive ??
How are you trying to access it ??
ie be more specific.

---

### Post by howefield on 2010-03-06
Windows can't read ext file systems without third party applications, if that is what you are asking.

---

### Post by coffeecat on 2010-03-06
Do you mean you can't access "D:" from Windows? That's because Windows cannot read the Linux filesystem used for your Ubuntu root partition - default is ext3 in Jaunty and the newer ext4 in Karmic.

Granted, there are 3rd party Windows drivers for the ext* family of filesystems but, last time I looked, they couldn't cope with ext4 and, personally, I wouldn't touch them with a 30 foot bargepole.

And please don't refer to D: when referring to a Linux partition. :p "C:", "D:", etc is a quaint Microsoft convention for referring to a "drive" (when they often mean a partition) and is meaningless in Linux. Calling a Linux root partition "D:" makes my head ache. :wink:

---

### Post by Morbius1 on 2010-03-06
> **coffeecat said:**
> And please don't refer to D: when referring to a Linux partition. :p "C:", "D:", etc is a quaint Microsoft convention for referring to a "drive" (when they often mean a partition) and is meaningless in Linux. Calling a Linux root partition "D:" makes my head ache. :wink:

Unless of course it really is in D - as in wubi. Are you using Wubi - Install within Windows? Don't know much about it myself but can't you access the "host" from /host or /media or something like that.

---

