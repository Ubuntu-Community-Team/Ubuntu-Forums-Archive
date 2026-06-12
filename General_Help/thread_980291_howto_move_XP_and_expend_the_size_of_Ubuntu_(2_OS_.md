---
title: "howto move XP and expend the size of Ubuntu? (2 OS on HD, XP must go)"
date: 2008-11-12
forum: General Help
---

### Post by adhg on 2008-11-12
Hi all,

My ubuntu is installed as a partition with XP (when reboot, I'm given the option to use either XP or Ubuntu).

I'm not using the XP anymore and it takes a lot of space. XP has 70Gb and Ubuntu only 30Gb (give or take)

Question: How can I permanently remove the XP and expend the size of Ubunto?

Thank you
Adriana

---

### Post by tuxxy on 2008-11-12
Boot the Ubuntu Live CD and open the application gparted also known as the partition editor.

Format your XP partition if you sure you dont want it anymore and then you will be able to increase the size of your Ubuntu partition with the free space you just created.  Its a graphical tool so should be easy to figure out :)

---

### Post by adhg on 2008-11-12
can I boot with a newer version of ubuntu?

---

### Post by James- on 2008-11-12
you could, if your partitions are in ext3 you may grow them(shrinking them is another story) in "gparted". if you want to upgrade to a newer version you can, just use update manager

---

### Post by bgs100 on 2008-11-12
Here is how to uninstall windows, make ubuntu bigger, and make grub go to ubuntu in 3 seconds:
1.Goto [gparted.sourceforge.net/]("gparted.sourceforge.net/")
2.Get the live cd.
3.Boot on the live cd
4.Edit your partitions
5.Boot on ubuntu
6.Go to a terminal and type in:
```
sudo gedit /boot/grub/menu.lst
```
6.Scroll down and take out all the windows stuff (but leave the comments)
7.Scroll up, and before the ubuntu stuff, type "hiddenmenu"
8.Look for a line that says "timeout    10" (or any number)
9.Replace the 10 (or other number) with a "3"
10.Save it.

---

