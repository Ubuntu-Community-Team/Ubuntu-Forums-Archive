---
title: "multy installs and partitions"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by geektobe on 2009-03-31
Hi
Seems that I have caused myself a few problems because i don't totally know what I am doing.
I had a dual boot with win xp sp2 and ubuntu 7.04. I decided i would install Ubuntu 8.10 so I tried to uninstall 7.04 but I did not do it right.
Took out boot ladder for 7.04 -done ok
Insalled 8.10 thinking 7.04 files were delete.
Would not boot into ubuntu
Installed it 8.10 2 more times still no boot
Succesfully installed boot ladder so it boots into ubuntu 
Trouble is I now realize it boots into 7.04 
Now I realize that I have installed 8.10 3 times so I have all these extra partitions and files.
I need to get rid of all the installs and partitions
Please how do I do this!!e

---

### Post by Mark Phelps on 2009-04-01
You don't need to "uninstall" Ubuntu.  The easiest way to remove it is to simply reformat or remove the partition containing it.

The quickest way to do what you want is to boot from the LiveCD, open the Partition Editor, and remove the Ubuntu partitions.

BTW, it's a boot "loader", not "ladder", and the version you're installing in Ubuntu is known as GRUB.

---

### Post by geektobe on 2009-04-01
Thanks for the info
So booting from a live cd means reinstalling again?

---

### Post by geektobe on 2009-04-01
Okay I really don't see where partition manager is???

---

### Post by Mark Phelps on 2009-04-01
No, booting from a LiveCD means running Ubuntu from the CD, not installing it.

The Partition Editor is System --> Administration --> Partition Editor.

---

