---
title: "Wiping an SSD drive"
date: 2021-02-04
forum: Hardware
---

### Post by rsteinmetz70112 on 2021-02-04
I have a SSD drive that became infected in a Windows machine. 
I want to wipe it and reuse it. 
I know "shred" is included in Ubuntu. 
Is that an appropriate tool and if so how long should it take to run on a 240GB drive?

---

### Post by CelticWarrior on 2021-02-04
If it's for your own personal use - as opposed to re-selling it and wanting to assure no sensitive information can be recovered from it - just delete the partitions and create new ones. There's no reason for any more in dept tool.

---

### Post by rsteinmetz70112 on 2021-02-05
OK I ran **shred** and it seems to have worked. The drive is completely empty and **sfdisk** sees it and is willing to create a new partition table. It took several hours, I don't know how long because I went home before it finished it was done in the morning.

While looking into **shred** I came across a command new to me **hdparm**. It seems to directly control the  drive. Reading the man page is pretty scary with warnings about experimental features not being well tested. There are lots of warnings about how it can screw up especially with older kernels like 2.6.xx. **hdparam** also seems to have erase options **--security-erase**  and **--security-erase-enhanced**, which one web page says makes **shred** obsolete. One man page doesn't say what it actually does and implies it might actually overwrite the drive firmware. **shred** appears to overwrite every sector 3 times.

I think I'm done. In a little while I'll mark this thread solved.

---

