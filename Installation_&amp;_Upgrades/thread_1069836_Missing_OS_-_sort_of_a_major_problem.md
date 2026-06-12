---
title: "Missing OS - sort of a major problem"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by DManX04 on 2009-02-14
I was partitioning my HD to install Ubuntu. My computer went into sleep mode during the partitioning, and now it says it's missing the operating system. I'm currently booting from an Ubuntu live CD, and I could really use some help or advice on fixing this problem. I have a Dell Inspiron 1720, about a year and a half old, with Windows Vista Home Premium.

---

### Post by kellemes on 2009-02-14
> **DManX04 said:**
> I was partitioning my HD to install Ubuntu. My computer went into sleep mode during the partitioning, and now it says it's missing the operating system. I'm currently booting from an Ubuntu live CD, and I could really use some help or advice on fixing this problem. I have a Dell Inspiron 1720, about a year and a half old, with Windows Vista Home Premium.

You can use the liveCD to view your partitions and repartition if needed.
Or simply delete the partitions you intended to use for Ubuntu and start the install again..
For this you need to startup GParted, don't remember where it's to be found in the Ubuntu menu, but it's there.

Just don't delete the NTFS-partition that's used by Windows.

Don't forget to shut off sleepmode, probably in BIOS. Or move your mouse every now and then ;-)

---

### Post by Mark Phelps on 2009-02-14
Did you shrink the Vista partition using the Ubuntu installer?  If so, there's a strong likelihood that you corrupted the Vista OS partition in the process.  If you have a Vista DVD handy (you DO have one, right?), suggest you boot into it and do a Startup Repair -- to confirm that Vista still works.

---

