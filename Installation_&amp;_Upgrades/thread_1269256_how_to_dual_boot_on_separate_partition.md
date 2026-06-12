---
title: "how to dual boot on separate partition?"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by lellyville on 2009-09-18
ok if i don't use the shrink volume method, and i just wanted to put ubuntu on 2nd partition. After installation will i just see ubuntu and not vista? i think i have tried it before and that was my result but it was long time ago so anyone know how to dual boot under my condition?

---

### Post by Cheezespread on 2009-09-18
> **lellyville said:**
> ok if i don't use the shrink volume method, and i just wanted to put ubuntu on 2nd partition. After installation will i just see ubuntu and not vista? i think i have tried it before and that was my result but it was long time ago so anyone know how to dual boot under my condition?

The shrink partition option is for folks who don't have space to spare for another partition. Most of the laptops come with a single drive dedicated to the OS and a recovery drive. In this case , you would be required to shrink the partition to allow some space for a new OS.

If you already have another partition which you can devote for UBuntu , you would just need to format and leave it as unallocated space ( I believe ) and pick the same parition/space for installing Ubuntu on it.The GRUB ; which will be your bootloader will recognize both your OS's and give you options to log into both without fail : unless you mess it up ( It goes smoothly most of the time.)

What anyone would require to give an advice to you would be drive structure or the details of partitions you have. Please provide a screenshot for the same.

---

### Post by lellyville on 2009-09-18
o ok thanks alot

---

### Post by stlsaint on 2009-09-18
depends on your setup...as stated in previous post we need to know how many partitions you have and what they are for...by you saying your second partition i think you are referring to your recovery partition in which you DO NOT WANT to delete if you are new to ubuntu. You can take the partition that has vista and shrink it to make space for ubuntu then during install of ubuntu you will see that unallocated space to install to. Then after you install and reboot...Grub will have added the vista partition to your menu.lst and you will have the option of booting both. IF...thats a big IF...IF something was to go wrong you could just add the vista partition maunally and be just fine. Please post more if you need help...

FYI...see my sig on Dual boot and installtion of ubuntu!!

Welcome to Ubuntu

---

### Post by lellyville on 2009-09-18
the 2nd partition is not recover, and how do i add vista back into grub if i do mess up and didn't get a choice of dual boot during start?
o another thing while i'm here is the hard drive parking issue fixed in 9.04?

---

