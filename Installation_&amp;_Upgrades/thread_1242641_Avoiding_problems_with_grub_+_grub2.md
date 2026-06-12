---
title: "Avoiding problems with grub + grub2"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by edgue on 2009-08-17
Hello there,

In addition to my kubuntu 9.04 I installed 9.10 alpha 4 for some testing.

AFAIK 9.10 came with grub2 ... which I can now use to boot new and old linux kernels. So far, everything works fine. I even found the files in /etc/grub.d that I need to update ...

Nonetheless I have two questions:

1) we have some security guidelines ... basically anything that I can boot on my laptop needs to be "compliant". My production system 9.04 is compliant (as I installed all our company security stuff); the test 9.10 install isnt.
So ... is there a good way for me to remove the 9.10 ... and have the (now defunct i guess) grub from my 9.04 installation back in place?

2) I am expecting some linux kernel updates for 9.04 soon (to fix those bugs that were recently found). Will that go smooth? I assume that my 9.04 ubuntu will do an update as usual ... so, it will update the existing no-longer-in-use /boot/grub/menu.lst from my 9.04 install. 
Sounds like a problem to me. Any guidance on that?

thanks for your help,

---

