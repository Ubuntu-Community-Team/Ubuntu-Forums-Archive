---
title: "Sys monitor reports one core on a dual core machine ?!"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by ronintiger on 2006-08-22
Hi there.

I have an Asus w5f, cetrino dual core. 

After reading some disturbing post of dual core laptops with problems (due probably to overheat for using only one of the processing cores) I checked my system monitor and verified that it only reported one CPU. :frown: 

This is starting to worry me, under windows (aparently) both cores are working... Is there some kernel upgrade I must do?... Is this normal? How can I be sure that both cores are working fine under Ubuntu ?  If I do:  cat /proc/cpuinfo  shouldn't I see processor 1 and processor 2 ?


Can anyone help me.. please? :)

---

### Post by vanilla.gorilla on 2006-08-22
I am a newbie but I had this same problem, so hope this helps. Yes, you need to have the 686 kernal.  The 386 one you see when you are booting up is only one cpu.  Use the synaptic package manager and search for 686.  It is very easy to use.  After a reboot you should see multiple kernal options for booting, and the default should be 686.

---

### Post by ronintiger on 2006-08-22
It worked !! Fantastic!! :D 
I now can check the frequency of each processor with the frequency scale monitor, and it reads diferent for each... :-D 
Thanx a lot ;-)

---

