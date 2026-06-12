---
title: "Disable particular memory addresses"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by voidlogic on 2008-01-25
Hey everyone,

I have had a couple of strange crashes with video buffer corruption that led me to suspect there was a problem with the memory installed in my system. After running memtest I found two words of memory that are bad. 
For my system replacing my memory would be extremely expensive due to it being picky, old and of large capacity. 
I am wounding if it is possible to perhaps pass arguments to the kernel telling it to not use the two bad words of memory?

My bad addresses are 0001C69A7B4 (~454.6 mb) and word 00039693884 (~ 918.1 mb).

My machine is an older laptop, an IBM thinkpad T23 with 1 GB of PC-133 SDRAM.
I am running Ubuntu 7.10

Any help is welcome

---

### Post by jeffus_il on 2008-01-26
It's not simple but read this, I think there is a badram kernel parameter.
[http://www.linuxjournal.com/article/4489](http://www.linuxjournal.com/article/4489)

---

### Post by voidlogic on 2008-01-26
Does ubuntu have the badmem or badram kernel patches? :confused:

---

### Post by jeffus_il on 2008-01-26
The linux kernel can accept parameters at boot thru the grub bootloader, the grub menu is displayed soon after the bios, and loads the linux kernel. While the grub menu is displayed you can type e to edit the command line which loads the linux kernel. type end and add "badram=<address_list>" then <enter> and b to resume the boot, after your first boot you can edit it permenantly into the grub menu file.
See this example:
 [http://www.usenet-forums.com/linux-general/94904-memtest86-kernel-badram.html](http://www.usenet-forums.com/linux-general/94904-memtest86-kernel-badram.html)

---

### Post by voidlogic on 2008-01-27
Hey jeffus_il's,

I think you misunderstood my question. I know how to use badram and pass it my bad addresses. What I need to know is if the Ubuntu kernel is patched with this patch. I know there was talk of debian starting to include it by default a few months back, but I don't know if ubuntu has. Do you know who I could ask to find out? Thanks.

---

