---
title: "Server-kernel unusably slow"
date: 2008-10-15
forum: General Help
---

### Post by Johann Spies on 2008-10-15
I have a new PC with Intel chipset, a quad-core CPU and 4G of Ram.  The 2.6.24-21-generic kernel boots fast and works without problems.  But it does not 'see' all the RAM.  I then thought that this problem can be solved  by either compiling a PAE-enabled kernel or by installing the server-kernel.

Both this options resulted in a PC that takes about 15-20 minutes to boot.  Just to login on a console takes about 30 seconds after the correct password was entered.

I have read several reports about Hardy being slow and most of them refers to X11-issues and Compiz.  This, however is a problem that makes me think that there is some timing issue that makes the kernel being very ineffective in it's communication with the hardware.

Any idea how to solve it?

---

### Post by Johann Spies on 2008-10-15
I have further information:

There is a core dump in my home directory.

I attach two files.

One is a sdiff between the dmesg of the generic kernel and the pae-enabled kernel that I compiled.

The other is a sdiff between the dmesg of the generic kernel and the server kernel.

Maybe some with more knowledge about kernel boot processes can identify what is wrong.  To me it seems that the framebuffer and the lvm-setup may be part of the problem.

---

### Post by cilkay on 2008-10-15
Your question reminded me of [a recent post to the GTALUG mailing list]("http://search.gmane.org/?query=+learnings+from+upgrading+a+notebook&group=gmane.org.user-groups.linux.tolug"). I've read reports of Intel motherboards with bugs in their BIOS that would cause them to take hours to boot. Might be related your problem.

---

