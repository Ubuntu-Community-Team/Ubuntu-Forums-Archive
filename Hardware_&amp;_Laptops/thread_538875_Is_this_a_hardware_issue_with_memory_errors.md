---
title: "Is this a hardware issue with memory errors?"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Julian David Pitt on 2007-08-30
Hi All
I am getting issues with Amarok which is causing the App to crash. When I run the executable with Alleyoop I get the following file produced that seems to point to errors with the RAM if I read it correctly, please see text below:

==10432== Memcheck, a memory error detector.
==10432== Using valgrind-3.2.1-Debian, a dynamic binary instrumentation framework.
==10432== Copyright (C) 2000-2006, and GNU GPL'd, by Julian Seward et al.
==10432== For more details, rerun with: -v
==10432==
==10432== Invalid read of size 4
==10432==
==10432== ERROR SUMMARY: 28 errors from 16 contexts (suppressed: 95 from 1)
==10432== malloc/free: in use at exit: 114,180 bytes in 3,114 blocks.
==10432== malloc/free: 58,890 allocs, 55,776 frees, 2,869,003 bytes allocated.
==10432== For counts of detected errors, rerun with: -v
==10432== searching for pointers to 3,114 not-freed blocks.
==10432== checked 852,464 bytes.
==10432==
==10432== 38 bytes in 2 blocks are definitely lost in loss record 40 of 102

==10432== 316 (256 direct, 60 indirect) bytes in 2 blocks are definitely lost in loss record 67 of 102

---

### Post by 5-HT on 2007-08-30
Yup, seems like it. You can rerun memcheck manually  it with the -v (verbose) option to get more descriptives but there are some problems with your RAM-- at least it's cheap at the moment!
cheers,

---

