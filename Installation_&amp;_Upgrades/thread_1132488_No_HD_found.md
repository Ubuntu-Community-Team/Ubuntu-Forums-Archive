---
title: "No HD found"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by FlamingIfrit on 2009-04-21
So I am trying to install Ubuntu 8.04 onto my computer as a dual boot with Windows Vista, and I am able to boot from the CD, but everytime I go to install I encounter a slight error...

It does not recognize/register/see my hard drive. I have partitions, but every time it gets to teh partition table, it is completely blank. non of the buttons even work, they are all grayed out. I can exit the installation and continue to "try ubuntu without making any changes to my computer", however I cannot install the OS. 

Any suggestions?

---

### Post by pytheas22 on 2009-04-21
It's possible that Ubuntu doesn't have the drivers to recognize your hard disk.  It's rare, but I've seen it happen elsewhere.  What is the output of these commands while running from the live CD:
```

sudo lshw
lspci -nn
ls /dev | grep -e sd -e hd
```

---

### Post by FlamingIfrit on 2009-04-22
Umm, sorry but I am only slightly knowledgeable on these things, so you would need to help me out on how to find these things out.

---

### Post by pytheas22 on 2009-04-22
You just need to boot to the Ubuntu live CD, open a terminal from the Applications>Accessories menu, and run the commands from my first post (one per line).  Then please copy and paste the output here.

---

