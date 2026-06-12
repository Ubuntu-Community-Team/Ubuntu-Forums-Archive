---
title: "Kernal Panic"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by loyal one on 2008-12-11
I was running Ver 8.04, kernal 2.6.24.21, everthing was fine: but, I downloaded -- via update manager -- kernal 2.6.24.22. Now the computer will not boot. Instead of my nice desktop, I am greeted with this notice:

Starting up
[ 25.575053 crc recovery error
[ 25.577099 Kernal panic -- not syncing: VFS: Unable to mount root
fs on unknown block(0,0)

Looks like the upgrade to ver 22 croaked the boot loader, or worse. 
So, how can I do one of the following:

1. Manually configure whatever is wrong with the boot loader, or whatever, and direct the boot process to the root partition?

2. Use synaptic to remove the corrupt ver 22 download and return to version 2.6.23.21?

Please be specific, I will need step by step directions. Thanks in advance for any help offered.

Loyal01

---

### Post by inobe on 2008-12-11
on the boot menu' do you have multiple kernels to choose from ?

example: [http://img257.imageshack.us/img257/125/06122008305ev6.jpg](http://img257.imageshack.us/img257/125/06122008305ev6.jpg)

if yes, select another kernel.

---

### Post by loyal one on 2008-12-11
Inobe:

Thanks for the response; I have been booting via the menu choices, but it is a pain to do this every time. However, the problem has been resolve via another update that included a grub update which eliminated the problem.

Thanks 
Loyal01

---

### Post by inobe on 2008-12-13
i am glad you posted the solution, this will help others :smile:

---

