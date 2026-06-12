---
title: "Is my harddrive defect?"
date: 2009-07-11
forum: Hardware
---

### Post by baju on 2009-07-11
Hi there.

My System Samsung Q70 / T9300 / 4gb ram / 320 gb hd / Ubuntu 64Bit Jaunty

Since I upgraded to Jaunty some strange things happen on my notebook:
From time to time my filesystem becomes corrupted. I run fsck and everything is fine again, except for the fact that some files that were open before shutdown were put in the lost+found folder. This happens especaly to firefox and gnome-do config-files. The files are not damaged or something like that, they are just in the wrong folder. If I put them back everything's fine.
The question is: Is it a weird driver problem or is my hd defective?

Is there a reliable way to test it?

---

### Post by mikewhatever on 2009-07-11
Install smartmontools from Synaptic and run some tests. [Read here for more...]("http://www.linuxjournal.com/content/know-when-your-drives-are-failing-smartd")

---

### Post by lisati on 2009-07-11
This might be obvious to some who read this, but it's always a good idea to close files properly before shutdown and to shut your system down properly (i.e. avoiding a forced shutdown with the power button or pulling the plug)

---

### Post by baju on 2009-07-12
Thanks for the tip.
I installed smartmon and run a selftest which reported no error.
I think I will watch my hd some time with it and see whether it finds an error.

---

