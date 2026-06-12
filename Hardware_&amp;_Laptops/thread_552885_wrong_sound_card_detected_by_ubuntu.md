---
title: "wrong sound card detected by ubuntu"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by vanakush on 2007-09-17
hi
 i'm new to linux and having problem with my sound card.i have intel 945 gnt motherbaord with builtin sigmatel sound card chip and  also using a pci 5.1 creative sound card. when i use live cd of ubuntu sometimes it recognises the wrong card of motherboard but i want to use my creative card pls help me n tell me how can i switch between these two sound cards the os detects both of the sound card but some times it detects creative and sometimes sigmatel motherboard card.
pls tell me how to switch between these card 
i have tried this command in terminal and the result is shown here
this time recognised card is creative but sometimes it recognises intel 
 
ubuntu@ubuntu:~$ cat /proc/asound/modules
 0 snd_emu10k1x
 1 snd_hda_intel
ubuntu@ubuntu:~$  now what 
 another problem  is i don't know how to modify the etc/module file using nano so pls if somebody have any idea pls give me step by step instruction to do it. thanks in advance

---

