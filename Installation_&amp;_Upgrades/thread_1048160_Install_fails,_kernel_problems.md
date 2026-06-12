---
title: "Install fails, kernel problems?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by Temppu on 2009-01-23
Ok, description of events:

Live CD(64bit) in, Install -> Kernel panics, attempted to kill init!
Adding acpi=off to bootoptions(or what they are f6 anyways), installer goes forwards, but ends up in shell.

Tried also with iommu=noaperture, noapic, nolapic, usually with same results, although with someofthose it ends up in busybox. Same problem with 32bit.

Machinery:

Asus Pundit P2-M3A3200 with AMD Athlon 64 X2 6000+
4gb ram
Hd in Sata1(Seagate Barracuda) and dvd in sata2.

---

### Post by Kevbert on 2009-01-23
Welcome to Ubuntu.
Have you burnt the live CD yourself ?  It may be a bad download (have you md5sum checked the downloaded ISO file). Have you performed a memory check from the start-up menu ?  Have you performed a CD integrity check from the menu ?
What are your system specs ?

---

### Post by Temppu on 2009-01-23
Memory is checked, and CD:s are fine(as far the checker on the menu goes).

Asus Pundit P2-M3A3200 with AMD Athlon 64 X2 6000+
4gb ram
Ati HD3450.
Hd in Sata1(Seagate Barracuda) and dvd in sata2.

---

### Post by Temppu on 2009-01-23
And BIOS is updated.

---

### Post by Temppu on 2009-01-25
Anyone?

It seems that the problem is not SATA drives, as I tried it with IDE hd with same results.

---

### Post by Temppu on 2009-01-26
Nobody knows or nobody cares?

Well, I'll be continuing my monolog :)

Same problem is with 8.04. I can deliver dmesg | less output and if needed. I really don't have any clue how to deal with this.

---

### Post by Temppu on 2009-01-28
Jumping to conclusions, it is probably something to do with SATA.

So when's the next kernel arrives?

---

### Post by em4r1z on 2009-01-28
Many people is having problems with the newest kernel, thus if you installed your system while connected to the Internet, the installer updated the kernel and it's causing a kernel panic. My system has been unusable since the last kernel update.

---

### Post by conholster on 2009-02-03
If you remove the hd3450 gpu you'll be able to install. Plug the card back in after installation and the computer will not boot. Tried this with both Intrepid and Jaunty Alpha3. Also tried booting Eurosoft's PCcheck but it freezes after a while too. Windows install works.

Looks like it's a case of works-on-windows....

---

### Post by Temppu on 2009-02-05
> **conholster said:**
> If you remove the hd3450 gpu you'll be able to install. Plug the card back in after installation and the computer will not boot. Tried this with both Intrepid and Jaunty Alpha3. Also tried booting Eurosoft's PCcheck but it freezes after a while too. Windows install works.

Looks like it's a case of works-on-windows....


It seems that you're right. Have anyone told to kernel-team this? And have you tried this with newest kernel?

---

### Post by conholster on 2009-02-05
> It seems that you're right. Have anyone told to kernel-team this? And have you tried this with newest kernel?

Didnt try the latest kernel. Was playing with it at work and the boss thought we were wasting time with it.

Should've done a bug-report but as I said it was at work and boss got frustrated ;)

Oh, yea we switched the 3450 for a nvidia 8400GS gpu..works fine. Could it possibly be Crossfirex thats cause of these problems?

---

