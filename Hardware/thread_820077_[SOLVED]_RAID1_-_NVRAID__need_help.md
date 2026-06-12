---
title: "[SOLVED] RAID1 - NVRAID : need help"
date: 2008-06-05
forum: Hardware
---

### Post by formol on 2008-06-05
hello,

I buyed two 500gb today to build Raid1 (mirror) into my computer.

Apparently, I need software to do that, instead my motherboard got NVRAID
here is my motherboard Tyan S2895 : [http://www.tyan.com/archive/products/html/thunderk8we.html]("http://www.tyan.com/archive/products/html/thunderk8we.html")

here is the guide [ftp://ftp.tyan.com/manuals/m_NVRAID_Users_Guide_v20.pdf]("ftp://ftp.tyan.com/manuals/m_NVRAID_Users_Guide_v20.pdf")

the goal to all that is to have 4 partitions :
- Ubuntu
- Swap
- XP
- Data

if you know a software I should use with NVRAID in Ubuntu, please tell me.
(or if you have any other information about that, please tell me :))

thank you very much

---

### Post by hotweiss on 2008-06-06
> **formol said:**
> hello,

I buyed two 500gb today to build Raid1 (mirror) into my computer.

Apparently, I need software to do that, instead my motherboard got NVRAID
here is my motherboard Tyan S2895 : [http://www.tyan.com/archive/products/html/thunderk8we.html]("http://www.tyan.com/archive/products/html/thunderk8we.html")

here is the guide [ftp://ftp.tyan.com/manuals/m_NVRAID_Users_Guide_v20.pdf]("ftp://ftp.tyan.com/manuals/m_NVRAID_Users_Guide_v20.pdf")

the goal to all that is to have 4 partitions :
- Ubuntu
- Swap
- XP
- Data

if you know a software I should use with NVRAID in Ubuntu, please tell me.
(or if you have any other information about that, please tell me :))

thank you very much

As far as I know you will not be able to use that motherboard's RAID functionality due to the fact that it does not have a true RAID controller. All it has is a RAID interface that Windows manages, also known as soft RAID.

---

### Post by formol on 2008-06-06
thank you hotweiss for anwsering

after reading about raid with ubuntu, i found this website 
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

i tryed a configuration like this guy did [http://advosys.ca/viewpoints/wp-content/uploads/ubunturaid024.png]("http://advosys.ca/viewpoints/wp-content/uploads/ubunturaid024.png")  but the installation asked me for a / partition.

so I try one like you can see on the picture send with this post.

with that, it instant great, but, when at reboot, it didn't work, my computer wouldn't see the raid partition.

(raid is working, I tryed to boot with ubuntu-desktop and then "fdisk -l", all the partition where "Linux Raid", at least...)

so, want should I do, looking around the grub configuration?

---

### Post by formol on 2008-06-06
same result with this configuration [http://http://img181.imageshack.us/img181/4771/0002dn4.jpg]("http://img181.imageshack.us/img181/4771/0002dn4.jpg")

at reboot: "Operation System not found".

I found this : [http://blogs.techrepublic.com.com/networking/?p=381]("http://blogs.techrepublic.com.com/networking/?p=381")

following this guide, I shoud do in console (alt-f2 during the install of ubuntu-server)

# mkdir /mnt/md0
# mount /dev/md0 /mnt/md0
# chroot /mnt/md0

but I don't have /dev/md0, so I guest my RAID is not mounted?  how mount it?

thank you in advance

---

### Post by formol on 2008-06-06
doh doh doh doh doh doh...

I forgot to set the raid in the boot order...  

Now, I saw a white underscore " _ " flashing black and white on the top of the screen.

---

### Post by allbread on 2010-12-07
Sorry to revive a old thread... 

I have a similar system ( Opteron 856 x 2 / 4GB DDR / Nvidia 8800GPU x 2  ) and aim to get either 10.04 or 10.10 booting off a RAID 1 striping  partition using the integrated chipset on the motherboard... I noticed that you are (were?) running a Tyan Thunder K8WE (S2895)  system and was wondering if you'd had any success setting up RAID under  Ubuntu 10.10? 

From the thread above it seems you did have some success setting up the RAID partition...  do you know if support for this chipset is included in the latest  kernels 2.6.3x+? 

Thanks!

---

### Post by formol on 2010-12-07
Hi allbread

I did not try with these version of Ubuntu. 

This tread was, how say, an unsuccessful one. I wrote at the time a small guide elsewhere with a unorthodox way to install software RAID with Ubuntu. I'm confident that it could work with newer version of Ubuntu. 

- disabled RAID in the Bios if it's enable
- boot with the server edition of Ubuntu (I did not try the alternate, it could work too, maybe)
- create the raid array and launch the install process.
- adjust bios configuration to boot on the raid array
- after, just install gnome and the desktop kernel

As far as I know, it should work.

---

