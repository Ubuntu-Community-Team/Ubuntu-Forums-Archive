---
title: "Vista in C:, Ubuntu in D:"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by urgood2 on 2009-09-08
Hi everyone! I need some help... I downloaded Ubuntu today, and am using the demo version (does nothing to computer)... Is it possible to install ubuntu in hard disk D? Because I have hard disks C: and D:, and I'm using Vista in C:. What can I do?

---

### Post by Megaptera on 2009-09-08
What do you have in 'D' at present?
In my case I had a Dell 'factory restore' partition in 'E' and my docs etc in 'D' with Vista in 'C'.

As I have the three Dell recovery discs as well, I deleted the content of 'E' giving free space of 20gb (having checked the discs did work beforehand!!). I then installed Ubuntu to 'largest continuous free space' and let the installer do the rest. 

I hope that's the type of info you're looking for?

---

### Post by Partyboi2 on 2009-09-08
If you are wanting to install Ubuntu to its own partition you can follow [[COLOR=Blue]this[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm"). If you are wanting to use  your "d" partition to install Ubuntu, use the disk management tool that comes with Vista and delete your d partition. Make sure there is nothing on it that you want to keep, or that it is a backup partition, as deleting it will wipe all data on the partition. Then skip to page 3 of the how to and install Ubuntu. Linux does not use letters to name partitions like windows does, you will usually see linux partitions listed as /dev/sda1, /dev/sda2 etc...

---

