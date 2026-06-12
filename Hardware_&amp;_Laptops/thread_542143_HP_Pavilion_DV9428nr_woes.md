---
title: "HP Pavilion DV9428nr woes"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by rwmcgwier on 2007-09-03
My company purchased me a HP Pavilion 9428nr. They did me no favors. After 2 days of slave labor on labor day weekend, I managed to get XP SP2 on the main drive after finding Vista Home Premium on the machine with LOADS of bloatware that reinstalled itself if you tried to remove it (the laptop has DV9000 on it and the DV9000 drivers for XP worked perfectly). Now I am trying to get Ubuntu to install on the second drive. The box for the computer says this is a "dual drive". In the installation for Ubuntu 7.04 and Ubuntu-7.10-Tribe 5, the install hangs at the partitioning. After much investigation, there is a superblock error issued when formating is attempted on the root partition. It appears this is some kind of weird single drive divided into two. With Feisty, I get an error message saying the error is a RAID/LVM problem and Gutsy Tribe-5 reports superblock problems.

Has anyone solved this?

Thanks
Bob McGwier

---

### Post by jonathanmotes on 2007-10-15
I have same laptop (dv9428nr) and I just divided my first drive into three partitions (vista, ubuntu root, swap) and used the second hard drive to store files that I could access from both OS's. This might be a better configuration if you can't find a solution. In manual mode, the installer should allow you to shrink your XP partition to give room for Ubuntu - just don't go lower than the preselected shrink size! 

As a side note, if you need help with the live disc or getting things like wireless to work, I just recently figured out how to do that on this laptop...

---

### Post by ycomp on 2007-12-30
Hi guys...

if I have this Laptop in a factory state... Vista Preinstalled... how do I install XP SP2 and Vista to Dual Boot?

---

