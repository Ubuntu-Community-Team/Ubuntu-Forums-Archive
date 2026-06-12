---
title: "problem with install"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by MaaSTaaR on 2005-12-22
Hello ...

i created Ext3 partiton with MagicPartiton , and when i try to install ubuntu , it's show for me partiton list (included Ext3 partition) i choose Ext3 partiton to format it , after format the installer show for me this massege

no file system is defined.

please correct this from the partitioning menu


what should i do to install ubuntu ? and why this massege show for me ?

---

### Post by darth_vector on 2005-12-22
hi,

the message is showing because when you formated you deleted the partition that you created with partition magic.

to install ubuntu i would recommend using the partition manager on the install cd. it is easy to use and works well. if you have any problems, post back and we will help you more.

---

### Post by MaaSTaaR on 2005-12-22
Hello ...

thanks darth_vector for your reply , ok what should i do now , format Ext3 partition to FAT then start install ?

---

### Post by darth_vector on 2005-12-22
i would use the partition manager on the ubuntu cd. boot from the cd. after setting up your language, keyboard and a few other little things you will get to the partitioning screen.

1) choose to set up partitions manualy
2) delete all of the non windows partitions
3) create the following partitions:
swap - should be about twice the size of the ram that you have (so if you have 256MB of RAM your swap partition should be 512MB)
/home - this is where your files go. it is a good idea to have a seperate partition for your files to that if linux fails you dont lose everything.
/ - this is where the system goes.

the size of /home and / really depend on how much disk space you have.

EDIT: make /home and / ext3 partitions.

---

