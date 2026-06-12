---
title: "Enabling DMA"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by cuoog on 2005-01-23
Hi everyone,

I'm having problems enabling DMA on my DVD drive.  Any help would be appreciated.

I've seen this thread already:

[http://ubuntuforums.org/showthread.php?t=5271&highlight=enable+dma](http://ubuntuforums.org/showthread.php?t=5271&highlight=enable+dma)

When I try $ sudo hdparm -d1 /dev/hda  I get the "operation not permitted" error.  I have tried it with the -X option also but I get the same error.

I have also tried editing my grub menu.lst to include an ide0=dma option, but it did not work.

I think my problem might be, as mentioned in the referenced thread, that I need to move up the module for my chipset, but I don't seem to have a chipset specific module.

My hardware:
ECS 755A2 Mobo, SiS755 chipset
Lite-On SOHW-1633 DVD Burner as the only IDE device
SATA HD

My /etc/modules:
sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
nvidia

Anyone with a similar chipset have any ideas?  Anything else to try?  Anywhere to actually get a module for the SiS chipset?

Thanks,
dan

---

### Post by Gnobody on 2005-01-31
Hi, I have the exact same problem with my AMD64 machine.  I have a VIA chipset with a GA-kt800 mobo and on-board SATA controller.   I have been searching for a answer to this problem since October. :(

---

### Post by henla464 on 2005-03-04
Gnobody:
Try to add via82cxxx in your /etc/modules file before ide-cd. Then reboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


cuoog:
You probably need to add something else to your /etc/modules file, unfortunatly I don't know what.


----
If you have a nForce chipset (and amd) then it might help to add amd74xx to your /etc/modules file.


Hope this will help someone

---

### Post by danko on 2005-07-22
Hi,
Maybe it's little late to post reply in this thread, but I assume that it is still possible that someone will find this helpful.
I am running Hoary for 386 on AMD64 with VIA KT800Pro chipset.
I have one SATA HDD. I am using default Hoary kernel.
After commenting &#8220;ide_cd&#8221;, &#8220;ide_disk&#8221; and &#8220;ide_generic&#8221; in /etc/modules,
the problem with DMA access to my IDE CDR and DVD dissapiered (and commented modules are still loaded on boot).

---

