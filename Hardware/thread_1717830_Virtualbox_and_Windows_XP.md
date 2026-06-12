---
title: "Virtualbox and Windows XP"
date: 2011-03-30
forum: Hardware
---

### Post by 3rdvincetheman on 2011-03-30
hey guys sorry if I'm in the wrong section. 

I have a quick question. I installed Virtualbox on my laptop (which has Ubuntu 10.10) then I created a windows XP user. when I go to open it it says "Fatal no bootable machine found system halted!" 

how do I get XP to work? do I need to aquire a copy of it and install it in the user on virtual box?

---

### Post by gyussz on 2011-03-30
> **3rdvincetheman said:**
> how do I get XP to work? do I need to aquire a copy of it and install it in the user on virtual box?
Sure you do, VirtualBox doesn't come with all the Operating Systems which are supported.

When you create a new Virtual machine you are allowed to choose the desired operating system. When you first start your Virtual machine a wizard will come up to ask how you want to install the guest OS. You can attach an iso image, or use a CD.

If no wizard: 
1. Start the virtual machine. On the menu bar: Devices -> CD/DVD drives -> then attach an iso image, or click on your CD/DVD reader.
2. Restart the virtual machine, and press F12 during the virtualbox splash image. This will allow you to change the boot medium, press c, this choose the virtual CD drive and will boot up the install iso/CD.

I hope I could help :)

---

