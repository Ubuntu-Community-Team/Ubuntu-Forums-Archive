---
title: "32bit Installed Pae kernel - Need to remove urgently"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by rajivv on 2009-05-14
Hi,

Installed 32bit Ubuntu with pae kernel to recognise the 4gb ram.
However before anyone asks I tried 64bit earlier but the system kept restarting randomly
after 2 minute of use so went to 32 bit and no problems.

Now the pae kernel has slowed down system like scrolling, moving windows, sysinfo the left menu shows after 3 seconds plus other slowdowns.

WHAT TO DO HOW DO I REMOVE PAE KERNEL.\
AND IF I GO TO 64 BIT AGAIN DO I NEED TO REINSTALL ALL SOFTWARES AGAIN.
ALSO HOW DO I GET RID OF THE CONTINUOUS RESTARTS IN 64BIT.

PLEASE HELP URGENLY WANT TO MOVE INTO UBUNTU FULL TIME.

Regards
rajiv

---

### Post by kpkeerthi on 2009-05-14
Open synaptic and search for **linux-image**. Find the installed pae kernel and mark it for complete removal. Reboot.

---

### Post by rajivv on 2009-05-16
> **kpkeerthi said:**
> Open synaptic and search for **linux-image**. Find the installed pae kernel and mark it for complete removal. Reboot.

There are a lot of linux images which one to remove

Regards
Rajiv

---

### Post by kpkeerthi on 2009-05-16
You can remove everything other than the one you are currently running. To find out the version of the kernel you are running, enter this command:
```
uname -r
```

I usually keep atleast two of the latest kernel versions.

---

### Post by 73ckn797 on 2009-05-24
You will want to remove the kernel that states "server" at the end of the kernel name in Synaptic.

---

