---
title: "Problem with modconf. I really need help now!"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by XPerienced on 2006-04-06
Hi!

I'm having problem with modconf when I'm trying to encrypt a harddrive with this HOWTO: [http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO)

I found aes-i586 and installed it. I think it worked fine, but I can't find dm_crypt and dm_mod in the kernel (modconf).

So does anyone know how I find it? Cause I'm running out of time and patient!

I need to get the harddrives encrypt before the end of this weekend so please help me.

I have Ubuntu 5.10 Server without Gnome, KDE and Xfce. Only X or what the terminal calls.

XPerienced

---

### Post by ranf on 2006-04-07
What kernel version do you have installed?
```
uname -a
```

I have 2.6.12-10-686 and can find the modules:
```
modprobe -l | grep dm-
```

---

### Post by XPerienced on 2006-04-07
I have
"Linux mycomputer 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux"

And find this:

mycomputer@mycomputer:~$ modprobe -l | grep dm-
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-zero.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-snapshot.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-round-robin.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-mod.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-emc.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-crypt.ko
/lib/modules/2.6.12-9-686/kernel/drivers/md/dm-mirror.ko
/lib/modules/2.6.12-9-686/kernel/cluster/cmirror/dm-cmirror.ko

Is this correct? Should I upgrade the kernel?

Atm, I don't have any WM or Desktop manager. 

XPerienced

---

### Post by ranf on 2006-04-07
This listing shows that the modules are there. It doesn't matter if you 
modprobe dm_crypt 
-or-
modprobe dm-crypt

I haven't worked with modconf yet.

The newer kernel has a lot of security fixes applied.

---

### Post by XPerienced on 2006-04-07
So you think it might work if I update the kernel to the latest version?

XPerienced

---

### Post by ranf on 2006-04-07
I think it should also work with the kernel you have.

---

### Post by XPerienced on 2006-04-07
Do you have any idea why I get so many problems if the files are there?

I just need to encrypt the damn harddrive in a secure way. Mounting with password every reboot is the best way for me. And it still have to work after a kernel upgrade.

Do you have another idea with there's another method?

XPerienced

---

### Post by ranf on 2006-04-08
I haven't done any disk encryption. Still on my ToDo-list.

---

### Post by XPerienced on 2006-04-08
The problem is solved right now. I don't know what cauced the problem, but it finally done. And I set the SU-reservation to 0%. 

XPerienced

---

