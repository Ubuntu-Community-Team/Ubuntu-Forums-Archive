---
title: "HP pavilion n5444 can't install ubuntu"
date: 2009-08-24
forum: Hardware
---

### Post by djcrash1981 on 2009-08-24
Hello to everyone.

I've been trying to install ubuntu in many different way's, liveCD, alternative, 9.04, 8.10, 8.04; And all of them finish in the same way, the partitioner freeze when it tries to write the info to the disk.

I've tried with different options at the CD boot like acpi=force, acpi=off and ide=nodma

The Hardware is an old laptop HP Pavilion 5444 with celeron processor.

I'm trying to install any flavor of ubuntu in x86 mode.

Thanks and I hope someone can point me the way.

Thanks.

---

### Post by djcrash1981 on 2009-08-26
Ok, finally I've passed the part of the partitioning, what i did was define the / filesystem with a different format than ext3.

But now it gives me the next error:
*** glibc detected *** /bin/sh: double free or corruption (out): 0x08092500 *** glibc detected *** /bin/sh: free (): invalid next size (normal): 0x08085358
*** glibc detected *** /bin/sh: double free or corruption (out): 0x08087360

I hope someone can help me :'(

---

