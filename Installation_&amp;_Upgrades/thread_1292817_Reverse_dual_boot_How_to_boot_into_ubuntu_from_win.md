---
title: "Reverse dual boot: How to boot into ubuntu from windows boot meun?"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by ajsc on 2009-10-16
I have a peculiar problem. Windows XP is already installed on my pc. While installing (for double boot) Ubuntu Jaunty i noticed that during the grub installation we have a choice of installing grub boot loader in the boot sectors of various partitions viz. windows MBR or Partion 1,2,3,etc including ubuntus own partition. So if i install the grub boot loader in boot sector of any partition other than windows MBR, will i be able to boot into linux through windows boot menu.  And if not what are the benefits of installing grub boot loader in the boot sector of any partition other than windows MBR.

---

### Post by phillw on 2009-10-16
> **ajsc said:**
> I have a peculiar problem. Windows XP is already installed on my pc. While installing (for double boot) Ubuntu Jaunty i noticed that during the grub installation we have a choice of installing grub boot loader in the boot sectors of various partitions viz. windows MBR or Partion 1,2,3,etc including ubuntus own partition. So if i install the grub boot loader in boot sector of any partition other than windows MBR, will i be able to boot into linux through windows boot menu.  And if not what are the benefits of installing grub boot loader in the boot sector of any partition other than windows MBR.

When you do the ubuntu install, grub will spot that you have windows installed and pop it on the list of boot options- This replaces the MBR that windows installs for itself

Many, many moons ago - I did edit boot.ini (the file windows uses) to dual boot with knoppix (About 15 years ago !!) - So, you can alter the windows one, just don't ask me to remember how :)

I let grub rule, it happily saw that I have vista and windows appears in my list of operating systems on boot up.

Regards,

Phill.

---

### Post by oldfred on 2009-10-16
The main reason to install grub to a partition is if you are chainbooting. Mostly for those of us who have enough hard drive space and want to try different systems. 

You use chainbooting for systems where you have many operating systems and want one master menu that links to the grub in the partition and then a sub menu in each partition for each install. The sub menus will get updated automatically. If you put all the installs into one giant menu you would have to manually update the menu with each kernel update of each operating system.

---

### Post by disophisis on 2009-10-16
GRUB has always worked fine for me... it's always spotted my windows installs and puts them in the menu to choose from

---

### Post by Mark Phelps on 2009-10-17
If you're determined to NOT replace the MS Windows MBR, there are alternatives available from the NeoSmart Technology forums.  They have a couple of alternatives -- NeoGRUB and EasyBCD.  I know the second works with Vista, but I don't know if it will work with XP.

You need to check the forums for details.

---

