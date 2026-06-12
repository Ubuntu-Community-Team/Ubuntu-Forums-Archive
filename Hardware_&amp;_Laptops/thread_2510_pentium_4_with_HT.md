---
title: "pentium 4 with HT"
date: 2004-10-28
forum: Hardware &amp; Laptops
---

### Post by dasfiend on 2004-10-28
what kernel should I be using with this processor?

currently i'm on 2.6.8.1-2-386 #1 Tue Sep 14 10:30:08 BST 2004 i686 GNU/Linux

was wondering if I should switch to the smp kernel to get the most out of my P4 w/HT support.

---

### Post by mark on 2004-10-29
[QUOTE=dasfiend]what kernel should I be using with this processor?

currently i'm on 2.6.8.1-2-386 #1 Tue Sep 14 10:30:08 BST 2004 i686 GNU/Linux

was wondering if I should switch to the smp kernel to get the most out of my P4 w/HT support.[/QUOTE]Technically, yes.  I'm currently running the 2.6.8.1-3-686-smp #1 SMP Tue Oct 12 13:40:26 BST 2004 i686 GNU/Linux kernel.

Subjectively speaking, I don't find a noticeable performance difference between the smp and non-smp kernels.

---

### Post by jcooper on 2004-12-09
Did you ever  find a difference between running a non-SMP and an SMP kernel? I too have a HT processor and would be interested in any feedback.

---

### Post by randy on 2004-12-09
I've tested the difference between the SMP and Non SMP kernels on a 2 way Xeon box with hyper threading.  Performance levels do increase in terms of cpu performance but IO perfomance decreases with the SMP kernel.

---

### Post by Rui Pais on 2004-12-17
Hi
i moved for a HT/smp kernell a few days and as far as i can tell everything seems slower, at least the start of programs, with the one or two exceptions. Graphs usually never show a load on cpu larger then 50~60%... 
I search the web for stuff on speed of HT use and everyone i read seems to focus more on penaltys then any real advantage. 

Some had use it with some real gains in velocity? 
(I've been using 2.6.8 pre-compiled kernels, i will tried with a 2.6.9 one compiled in this machine)

any thoughts on the subject?

---

### Post by gasparov on 2005-02-23
[QUOTE=Rui Pais]Hi
i moved for a HT/smp kernell a few days and as far as i can tell everything seems slower, at least the start of programs, with the one or two exceptions. Graphs usually never show a load on cpu larger then 50~60%... 
I search the web for stuff on speed of HT use and everyone i read seems to focus more on penaltys then any real advantage. 

Some had use it with some real gains in velocity? 
(I've been using 2.6.8 pre-compiled kernels, i will tried with a 2.6.9 one compiled in this machine)

any thoughts on the subject?[/QUOTE]
 Hi,
   probably you'll even found that graph is dark and light blue, that is your ht proc seen as two procs, even in windows it doesn't go over 50% on my system...I switched from mandrake 2.6.8.1 smp to ubuntu 2.6.8.1-686 "simple" so it's difficult to make a comparison, if I'm not wrong  you should particulary feel the different during hard multitasking....

---

### Post by fenix03 on 2005-02-24
Technically you should get better multitasking performance with SMP. For example watching a movie and compiling at the same time should be smoother.

---

