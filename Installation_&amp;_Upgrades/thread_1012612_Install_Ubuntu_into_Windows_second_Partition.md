---
title: "Install Ubuntu into Windows second Partition"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by why2000 on 2008-12-16
Hi,

I tried to install ubuntu from Windows XP by using the Wubi engine. It is successfully installed, however, when I reboot my Notebook and then select "ubuntu" from the boot menu, I just "jump" out from the Splash screen and initramfs>. I checked all of the error messages from the log and I got that ubuntu cannot fine the partition. I think it is because I installed the ubuntu into C:\ and it is my second partition. My first partition is being used by my Notebook as the backup recovery partition. Could anyone help me how to configure ubuntu to be run in the second partition? Many thanks.

---

### Post by joff13 on 2008-12-16
hummm, not completely understood... and never used wubi....

If I were you I would use the live CD (booting it) and not from winzoz...

anyway, help us understand your HDs layout... Run the live CD and in a terminal 

```
fdisk -lu
```

or open the partion tool..
or whatever you  want to make us know your disks

---

### Post by why2000 on 2008-12-19
> **joff13 said:**
> hummm, not completely understood... and never used wubi....

If I were you I would use the live CD (booting it) and not from winzoz...

anyway, help us understand your HDs layout... Run the live CD and in a terminal 

```
fdisk -lu
```

or open the partion tool..
or whatever you  want to make us know your disks

Actually, my Notebook containes 3 partitions in the Harddisk. The first one is the hidden partition which contains the recovery partition. My Windows XP actually installed into second partition. The third one is the Data partition and it is not for boot up the Notebook. Also, the ubuntu is installed into the second partition as well. However, then I boot up my notebook, ubuntu just search the boot module from the first partition and of course it is invalid and just prompt out to initramfs.

Could you guys know how to "edit" any config files in ubuntu so that it can be booted from the second partition? Many thanks.

---

### Post by louistan3 on 2008-12-19
you could just edit the menu.lst file if you use grub.


it should say > (hd0,1)

so that it indicates that its going to the 2nd partition.

I personally havent used wubi before. so im not sure how it works.

---

### Post by louistan3 on 2008-12-19
Edit: double post

---

### Post by pietjanjaap on 2008-12-19
Wenn you start ubuntu, then the first thing you see is grub.
Wenn you see grub press "esc" or/and "e", then change your hd number.
Then go 1 step back, and press "b" to boot.
Now you can try all different harddisks/partitions to boot from.

Wenn you find the wright one, then put the hd number in the file "menu.lst"

---

### Post by charankumarbr on 2008-12-19
Hi...

i have deleted a logical drive from win XP to install ubuntu(FULL INSTALLATION) with 11 GB. But, i dont no how to full install into one logical drive.Please anyone help me.

I alone started installing it, but, its showing some error to swap space and root... I did not understand it, please provide me complete steps in full installation of ubuntu please urgent..

---

### Post by pietjanjaap on 2008-12-19
Look for bootcd like "gparted live cd".
Then delete the partition where you want ubuntu to install.
Then install ubuntu, that's all.
Ubuntu will make the partition how he wants it. And you know you have the empty partiton and not the windows partition.

---

### Post by why2000 on 2008-12-29
> **louistan3 said:**
> you could just edit the menu.lst file if you use grub.


it should say 

so that it indicates that its going to the 2nd partition.

I personally havent used wubi before. so im not sure how it works.

Could you advise how can I change the (hdd0,1) parameter into the command? I cannot find that parameter.....:(

---

### Post by logos34 on 2008-12-29
> **why2000 said:**
> Could you advise how can I change the (hdd0,1) parameter into the command? I cannot find that parameter.....:(


that's not going to work because Wubi installs linux INSIDE your windows partition on a loopmounted filesystem

['Cannot boot into Ubuntu']("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")

---

