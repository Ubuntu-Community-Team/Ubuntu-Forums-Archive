---
title: "Which ISO?"
date: 2008-11-26
forum: General Help
---

### Post by falconed7 on 2008-11-26
Hey all! I'm going to be building a homer file server based upon Hardy Server Edition and AMD hardware:

Gigabyte GA-M78SM-S2H
AMD Athlon™64 X2 4850e

Which .iso file will I need? The i386 or the amd64? I assume I need the amd64 version, however, I was planning on running the 32bit version. Can I still use the i386 on AMD components?

---

### Post by Archmage on 2008-11-26
If you want the 32-bit version, than you need the i386-ISO. It should work on your PC.

---

### Post by falconed7 on 2008-11-26
> **Archmage said:**
> If you want the 32-bit version, than you need the i386-ISO. It should work on your PC.

Would it be better to use the 64bit version? Does it offer anything different?

---

### Post by hyper_ch on 2008-11-26
why do you want to use the 32bit one?

---

### Post by l0wender on 2008-11-26
If you need to have more than 4G of RAM memory on your system, then 64-bit is the way to go. This is the primary reason to go 64-bit. Otherwise, 64 bits may not be that necessary, especially on a home server. I've read somewhere on the Net that sometimes 64 bit systems are slower than 32-bit ones. Besides, they may take a little bit more disk space (not much though) since many operations now deal with the twice as big atomic data samples. Perhaps there may be other reasons to favor 64 bits - may the others with more experience express their opinions as well.

---

### Post by Kevbert on 2008-11-26
You can use either server version to address more than 4Gb of RAM as the 32 bit version has PAE support built in. Regardless of this 64 bit is the better way to go as the AMD64 version is tailor made for your processors.

---

### Post by felker2 on 2008-11-26
> **falconed7 said:**
> Hey all! I'm going to be building a homer file server based upon Hardy Server Edition and AMD hardware:

Gigabyte GA-M78SM-S2H
AMD Athlon™64 X2 4850e

Which .iso file will I need? The i386 or the amd64? I assume I need the amd64 version, however, I was planning on running the 32bit version. Can I still use the i386 on AMD components?

You can use both version: 32-bit and 64-bit. That's the great thing about the Athlon64 (and Intel x86-64) processors.

If you have got more than 3 GB RAM, it's better to use the 64-bit version.

BTW: Why do you want to use the Hardy version (=8.04), and not the current Intrepid (=8.10)?

---

### Post by falconed7 on 2008-11-26
> **felker2 said:**
> BTW: Why do you want to use the Hardy version (=8.04), and not the current Intrepid (=8.10)?

Just because it's Long term support. I've read a fair bit of other threads and people we're saying to use Hardy just because of this reason. Is 8.10 fairly stable? Anyone found any bugs yet?

---

### Post by Kevbert on 2008-11-26
If the 8.10 server version is like the standard one, accessing floppy drives, ntfs formatted drivers is a problem (but there are some workarounds). Sound is also work in progress.

---

### Post by felker2 on 2008-11-26
> **falconed7 said:**
> Just because it's Long term support. I've read a fair bit of other threads and people we're saying to use Hardy just because of this reason. Is 8.10 fairly stable? Anyone found any bugs yet?

OK, good point. 8.04 is very stable: a lot of bugs are ironed out.

The disadvantage of an 'older' OS-version is less/no support for brand new hardware. So if some of your hardware is not recognized by 8.04, you should try 8.10.

I myself use 8.10 and have only one annoying bug with 8.10: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970)

---

### Post by blazemore on 2008-11-26
No offense meant, but if you're having to ask which architecture to download for, are you going to be cool with the install just dumping you at the terminal and essentially saying Have Fun...?

To answer your question, go for the 64 bit version since you can. Might as well future proof it in case you want to add more RAM, since with 64 bit you can just drop in more than 4gb RAM. With 32 bit you'd have to reinstall the 64 bit version (Or use PAE but they don't work imo)

---

