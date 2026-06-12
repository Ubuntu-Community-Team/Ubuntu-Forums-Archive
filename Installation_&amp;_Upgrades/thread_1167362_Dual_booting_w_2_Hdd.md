---
title: "Dual booting w/ 2 Hdd"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by ssulaco on 2009-05-22
I am currently running XP and just purchased another drive so that I can install Ubuntu on that drive so I can Dual boot,Ive been leaning toward this procedure by confused57:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

,but really dont want to keep pulling my windows drive when upgrading or switching Distros,
Can I install the new hdd as slave/cable select and install ubuntu on this drive and also direct grub to this drive also, without effecting my windows drive(mbr) or should I install Ubuntu on new drive,set as master and xp as slave...what Im wanting to know is it possible to install grub just to the ubuntu drive and still be able to dual boot,
Thanks

---

### Post by logos34 on 2009-05-22
yes, put ubuntu on the slave (+ grub on slave MBR); make that your boot disk in the bios...Edit windows entry in /boot/grub/menu.lst in order to [chainload XP on a non-first hdd]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

*Make sure during installation to select the correct hdd for grub bootloader--by default it will go on '(hd0)', which will probably be windows drive.  You will need to change that (>'ready to install' screen>advanced button) to (hd1)

---

### Post by ssulaco on 2009-05-22
> **logos34 said:**
> Edit windows entry in /boot/grub/menu.lst in order to [chainload XP on a non-first hdd]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")


(logos....follow this procedure here).............

You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)

Code:
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
Code:
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

