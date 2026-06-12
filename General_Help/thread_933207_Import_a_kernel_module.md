---
title: "Import a kernel module"
date: 2008-09-29
forum: General Help
---

### Post by Kooothor on 2008-09-29
Ok, so this is a very naïve question.

I have a kernel module on my MacBook wich is "applesmc". Wich I can modprobe.
And I would like to put this module on my Archbox on an iMac aluminium. How can I manage it ? Because the Arch kernel can't allow me to modprobe such module.


thx :)

---

### Post by Ayuthia on 2008-09-29
I am not for sure if you can really move a .ko module from one computer to another or not.  They are kernel specific so if the versions are different, they are going to cause problems.  Also, they might have some dependencies that you did not transfer over.  

However, are you sure that the module is not there?  I am able to find the module in Arch:
/lib/modules/2.6.26-ARCH/kernel/drivers/hwmon/applesmc.ko

---

### Post by Kooothor on 2010-09-21
Hello, 

Sorry for the late answer, I've been afk.
Yes indeed it is in the kernel \o/

But I'm not using apple products anymore...

Thanks for you answer though.

@+
~ktr

---

