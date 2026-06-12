---
title: "what can i do if gigabyte mother does nt support linux?"
date: 2012-12-04
forum: Hardware
---

### Post by gabak on 2012-12-04
this is the mobo i got , when i run ubuntu 12.10 it does nt recognize the hdd. Then i went to read the OS support at their site and that is the ugly answer i found

GA-MA770T-UD3 (rev. 1.0)



[http://ar.gigabyte.com/support-downloads/faq-page.aspx?fid=1681&pid=3243](http://ar.gigabyte.com/support-downloads/faq-page.aspx?fid=1681&pid=3243)

any suggestion? besides changing the mother?

---

### Post by ahallubuntu on 2012-12-04
Most motherboard manufacturers don't advertise explicit Linux support.  If you can boot up the live CD ("Try it") then it must have SOME support for the motherboard.  This is an old motherboard so is probably supported by now.

Try to figure out why your hard drive isn't recognized.  If you boot the live CD, open the Terminal program and type

```
ls /dev/disk/by-label/
```

What are the results?

---

### Post by Yellow Pasque on 2012-12-05
I have a Biostar motherboard with the same AMD 770 chipset and it works well. If the motherboard cannot physically see the disk, then it has nothing to do with the operating system.
What make/model of hard disk is it? What size is the disk?

---

### Post by gabak on 2012-12-05
this pc was working great with windows 7.
bios see hdd.
it is a hdd wd 500 blue


> **Temüjin said:**
> I have a Biostar motherboard with the same AMD 770 chipset and it works well. If the motherboard cannot physically see the disk, then it has nothing to do with the operating system.
What make/model of hard disk is it? What size is the disk?

---

### Post by gabak on 2012-12-05
it says:

ubuntu\x2012.10\x20amd64


now what else can i do?


> **ahallubuntu said:**
> Most motherboard manufacturers don't advertise explicit Linux support.  If you can boot up the live CD ("Try it") then it must have SOME support for the motherboard.  This is an old motherboard so is probably supported by now.

Try to figure out why your hard drive isn't recognized.  If you boot the live CD, open the Terminal program and type

```
ls /dev/disk/by-label/
```

What are the results?

---

