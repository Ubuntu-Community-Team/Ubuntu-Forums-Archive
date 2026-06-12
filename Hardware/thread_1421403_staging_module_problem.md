---
title: "staging module problem"
date: 2010-03-04
forum: Hardware
---

### Post by m3tr0g33k on 2010-03-04
I have compiled the staging/winbond module w35und.ko using the instructions here
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html")

insmod w35und.ko

gives me:

error inserting 'w35und.ko': -1 Unknown symbol in module

modinfo show the vermagic as:

vermagic: 2.6.28-18-generic SMP mod_unload modeversion 586

and my running kernel (`uname -r`) is:

2.6.28-18-generic

The linux-image and linux-source packages I am using are both 2.6.28-18.59. Obviously I am missing something obvious. Anyone point me to what my schoolboy error is?

Thanks in advance!

---

### Post by m3tr0g33k on 2010-03-04
OK, talking to myself for a while I checked dmesg.

Got some errors about ieee802.11 calls not being found - guess there is an unsatisfied dependency from compiling the module in-place in the tree.

I am going to move the winbond directory into the main kernel tree and try again.

Is this likely to work?

---

### Post by m3tr0g33k on 2010-03-04
OK, so with even closer inspection...

THe make menuconfig on the kernel has an option to compile staging drivers now.

That's great - I didn't know that was in there nowadays.

Am currently doing 'make modules'. We'll see what happens...

---

