---
title: "[SOLVED] can't use nokia 5300 as usb mass storage device"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by mainalisuyog on 2007-05-24
well, the thing is, my nokia 5300 is recognised as a mass storage device, and i can browse the files. But when i try to copy anything to/from it, the copying process stalls and hangs. It's a problem with all distros using the newer kernels. Everything is fine in old kernels (upto 2.6.12, i think). Is there some patch to fix this? I hate booting into vmware xp. Please help.

---

### Post by McLogic on 2007-05-30
I'm running an older Ubuntu and have not updated my kernal in the last couple of months, but my 5300 is working fine. Sometimes it mounts as a usbmemory and sometimes as MemoryCard, but it always works. When it looks like it is hanging, it may just need more time as it is a USB 1 device.

I'll post back if it is not working after my kernal upgrade.

---

### Post by mainalisuyog on 2007-06-01
Thanks. Please let me know what happens after u upgrade the kernel.

---

### Post by McLogic on 2007-06-10
Eveything is working fine, still.

I had one problem on an old kernal -- that it was resolved by a reformat of the card. I did lose my SD formating, but it all still works. The problem was a folder with thousands of items in it, it would not open. I could not delete it from the command line. 

I had to format the card to get rid of it. I have a Dell 700m -- 855 chipset, 2x512, 120 Gb Samsung.

---

### Post by Pablasso on 2007-06-14
i have the same problem, it also fails on sabayon

---

### Post by omarino on 2007-06-15
Can confirm the problem!

---

### Post by mainalisuyog on 2007-06-15
Do you know if i can install some type of linux on nokia 5300?

---

### Post by mainalisuyog on 2007-06-15
success! I just formatted the card and it works fine now :) Thank you for helping!

---

