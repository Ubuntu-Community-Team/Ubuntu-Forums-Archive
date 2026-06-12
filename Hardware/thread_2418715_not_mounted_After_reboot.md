---
title: "not mounted After reboot"
date: 2019-05-10
forum: Hardware
---

### Post by hashen on 2019-05-10
[ATTACH=CONFIG]283238[/ATTACH] 

In this There is my second harddisk drive.[B]SKULLCANYON

[/B]Always after reboot i have manually mount that..

I want to know a way to set that drive as auto mounted...

---

### Post by dino99 on 2019-05-10
use /etc/fstab to add it into.

---

### Post by hashen on 2019-05-10
I located the file but i have no idea about how to add it...

Can you please guide me?:)

---

### Post by him610 on 2019-05-10
Don't know your confidence level working in a terminal.
You need to do a little prep work first.
From the command line interface (CLI)in a terminal, run *sudo blkid* , you will see a line for each one of your disks.
Determine which one is skullcanyon; look for the part that begins UUID=....
Make note of it, and type
Make a backup copy of fstab
Open /etc/fstab for editing with *sudo nano /etc/fstab* Uses arrow keys to move cursor.
At the bottom, add a line, you will need the exact UUID information you noted earlier
UUID=xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx /(toplevelfolder)         type     defaults   0    2
Save the file, exit, and reboot

If you have any problems, check *man fstab*

---

### Post by sisco311 on 2019-05-11
You can use gnome-disks to create the fstab entry via the GUI:
[https://www.linuxuprising.com/2018/12/how-to-auto-mount-partitions-on-startup.html](https://www.linuxuprising.com/2018/12/how-to-auto-mount-partitions-on-startup.html)

---

