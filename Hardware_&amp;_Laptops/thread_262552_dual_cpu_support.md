---
title: "dual cpu support"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by trifgabi on 2006-09-21
hi
  i'd like to know how to set up ubuntu to see both procs.on my INSP1505
 i have the 686 smtp installed and updated but still shows only one on less /proc/cpuinfo.
I tried to post it in the abs beginner talk but no answers.

thank you

---

### Post by ohrock on 2006-09-22
What kernel are you running?  To find out go to the terminal window and type 'uname -a'   post that back in here.

Also I just checked with 'cat /proc/cpuinfo'  and it shows one core for my computer,  but when I go to the system monitor  (System  -> Administration -> System Monitor )   it shows two CPUs under the resources tab.

Check that as well,  because I think CPUinfo might not be telling you all the truth!  :-)

OhRock - Roberto

---

### Post by trifgabi on 2006-09-22
2.6.15-27-686 and it does show up in the system monitor.
any idea how to set up or check the display driver?

thanx

---

### Post by trifgabi on 2006-09-22
actually it's using the vesa driver. i'd like to try the howto for insp6400 on this page, i hope it's going to work.

---

