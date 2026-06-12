---
title: "Partitioning on installation"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by cygnis1 on 2009-10-05
I have been trying to create a /home directory on a separate partition on my test machine.  I first created a second partition (/dev/sda3) using gparted on a live cd. When I went to install Jaunty from a live cd, all went well until the partitioning part.  My choices were: 1. install the new OS side by side, preserving the second partion.  2. A clean install using the whole hard drive, erasing the second partition.3. Manually partitioning the hd.  I chose to manually partition the hard drive.  I chose /dev/sda1 and the options were to choose the 1. file system (I chose ext3) 2.the mount point.3.format.  The first time I chose the mount point of / and formated.  When the installation continued, I got a fatal error that there was a boot loader failure.  It did not seem to give me the option to put in a boot partition as well as the / partition. In order to get /dev/sda1 with /boot and / as well as /dev/sda3, I had to go back into the live cd/gparted and create a separate /boot partition, but it is too large (2gig).You can only make your partitions so small.  I have read about guided partitioning in the installation process, but only have found two options,automatic and manual.  Should I be using anther kind of cd,ie alternate installion?  Please help, so that I can go on to my next project/problem using a /home directory.
Thanks,
Cygnis1

---

### Post by Bartender on 2009-10-05
*I got a fatal error that there was a boot loader failure*

My top guess is your CD is flawed.  Did you check it?

---

### Post by cygnis1 on 2009-10-05
The cd is fine,and the computer boots now with the added /boot partition.  But no  option in the installer to add /boot to the / partition.

---

### Post by Atten-dev on 2009-10-05
Hmm. I don't think that should have happened. I have had a separate partition for /home before, but I believe I used the text-based alternate install CD. I'd give that a shot.

---

### Post by raymondh on 2009-10-05
Are you trying to install a /boot because of BIOS access problems leading to an error 18?  If so, try installing root within the first 137GB of the HD. 

If you want a separate /boot ... see his tutorial by herman.

[http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition)

Re : GRUB (just in case you plan to have root (/) in 1 HD while GRUB in a second HD)

in step 7, by choosing advanced, you can choose where to install GRUB

Happy ubuntuing.

---

### Post by cygnis1 on 2009-10-05
Thanks,I will give it a try.

---

