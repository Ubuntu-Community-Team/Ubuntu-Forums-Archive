---
title: "Question about Dualbooting Ubuntu/XP"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Nuz on 2009-04-02
I have a 120GB hardrive partitioned into 2 already. One 15GB partition where windows is installed and another 100GB partition.

The guide here: [https://help.ubuntu.com/8.10/switching/installing-partitioning.html#installing-partitioning-dual](https://help.ubuntu.com/8.10/switching/installing-partitioning.html#installing-partitioning-dual)

says I need to do the manaul instructions. I was wondering if I would be able to use the "Guided - resize SCSI1 (0,0,0), partition #5 (sda) and use freed space" option. If I can do this fine, and this question may seem a bit obvious  but I want to make sure, is the "Ubuntu 8.10" slider the one where the important installation stuff (root, swap, whatever) will be? And /dev/sda5 slider will be free space?

Thank you for the help

Edit: Actually I found why manual wouldn't work like it was supposed to before, I needed to delete that partition and change it to freespace. I am going to install now. Hopefully it goes well. 

Edit2:I clicked INSTALL then went to the toliet. I then realised that instead of making a huge HOME using ex3  partition, I should've made a huge NTFS one so I could access it in windows as well. Oh well, I might reinstall later.

Edit3:Well it went fine

---

### Post by Mark Phelps on 2009-04-02
> **Nuz said:**
> 
Edit2:I clicked INSTALL then went to the toliet. I then realised that instead of making a huge HOME using ex3  partition, I should've made a huge NTFS one so I could access it in windows as well. Oh well, I might reinstall later.

Edit3:Well it went fine
You mean you have Ubuntu installed in an NTFS partition?  Did you install via Wubi or did you install for dual-boot?

---

### Post by Nuz on 2009-04-02
> **Mark Phelps said:**
> You mean you have Ubuntu installed in an NTFS partition?  Did you install via Wubi or did you install for dual-boot?

Nono. I installed /root in a ex3 partition. I was just meaning a partition for general file saving so I could use it in Ubuntu and Windows(does it actually work this way?).

Yeah I was installing for dual boot, it all works fine

---

### Post by Mark Phelps on 2009-04-02
> **Nuz said:**
>  I was just meaning a partition for general file saving so I could use it in Ubuntu and Windows(does it actually work this way?).

Would recommend formatting a shared partition as NTFS.  Both MS Windows and Ubuntu can handle that file format.

---

