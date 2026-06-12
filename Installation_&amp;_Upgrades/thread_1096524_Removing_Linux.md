---
title: "Removing Linux"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by feralbyte on 2009-03-15
I have decided to remove linux from my dual boot system. I have spent 3 days of reading post and swapping systems simply to get my wireless network running. And I still have to reset it everytime I restart into linux. I have no 3D and after downloading drivers and getting the error need to be run as root and then seeing the pages of terminal commands I need to enter while at a text screen I have decided it is not worth the effort to continue trying to get things working. Especially seeing as I have no printer setup in linux yet either. Now I need to remove the boot loader and linux from my system but do not know how without losing all the information on the entire drive. Any help on this issue please?
PS: I have huge amounts of respect to all the work that has gone into the creation of this operating system. If I had all the knowledge needed to run the commands in terminal I'm sure I would find it a great deal easier. But for me, putting up with windows is by far a huge amount simpler than learning the linux language.

---

### Post by lisati on 2009-03-15
We feel your frustration! 

First of all, are you using "Dual Boot"? If not, a clean install of whatever you choose to have on your system will probably suffice.

---

### Post by ad_267 on 2009-03-15
Most hardware is pretty well supported now, but unfortunately there are still some things that aren't well supported in Linux as you've found.

You can use the Ubuntu live CD and run gparted (System - Administration - Partition Editor) to delete your Ubuntu partition and swap partition if you have one. Then resize your Windows partition to take up the extra space. You will then have to use your Windows install CD to restore the Windows boot loader by running fixmbr.

---

### Post by feralbyte on 2009-03-15
Yeah thats what I had thought. Thought perhaps there may have been a magic restore button. lol. Altho I had forgot about the windows install CD. that was a lat easier than what I had planned. lol. Thanks for the help. Appreciate it. :o)

---

