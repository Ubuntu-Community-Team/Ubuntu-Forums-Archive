---
title: "Grub got wtfpwned?"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by linuxguru1 on 2009-05-02
Hi,

Yesterday I decided to install a 2nd windows partition. My disk containted Win XP and Ubuntu 9.04 already and I couldn't find any good partitioning tools. 

What I did is the following: I slided in my Ubuntu 8.10 disk and used the partitionmanager that's in the installer. Then I installed ubuntu 8.10 on that partition, only to reboot, slide in the windows disk and install a second win XP on that partition. 
During the install I selected "do not install a bootmanager" cause I thought Grub from Ubuntu 9.04 would have a conflict with the grub from 8.10

Now Grub got wtfpwned by the windowsbootmanager. I can't start up Ubuntu anymore. Is there a way to disable this windowsbootmanager and get Grub back up and running?

Thanks!!

PS: Before you all start asking why in God's name I'd want 2 windows partitions: I created the 2nd win XP partition for entertainment purposes only. Yeah, I got bored and thought "hey, let's try creating a tripple boot!"

---

### Post by easybake on 2009-05-02
[QUOTE=linuxguru1;7196885]Hi,

Yesterday I decided to install a 2nd windows partition. My disk containted Win XP and Ubuntu 9.04 already and I couldn't find any good partitioning tools. 

What I did is the following: I slided in my Ubuntu 8.10 disk and used the partitionmanager that's in the installer. Then I installed ubuntu 8.10 on that partition, only to reboot, slide in the windows disk and install a second win XP on that partition. 
During the install I selected "do not install a bootmanager" cause I thought Grub from Ubuntu 9.04 would have a conflict with the grub from 8.10

Now Grub got wtfpwned by the windowsbootmanager. I can't start up Ubuntu anymore. Is there a way to disable this windowsbootmanager and get Grub back up and running?

You can reinstall grub from the live disc. 

in terminal on the livecd (replace the X's):

sudo grub

find /boot/grub/stage1

root (hdX,X)

setup (hdX)

quit

In order to do this and maintain 2 working windows installs. You should use gparted on the live cd and select "hidden" on "manage flags" this will hide the other windows install so it will not conflict with the other. 

You really didn't need to install 8.10 just to write over it with windows. You could have just formatted it to be ntfs with gparted on the livecd.

---

### Post by linuxguru1 on 2009-05-02
lol I know... but 12 hours ago, I didn't know gparted :P

I'll try doing the livecd stuff soon, and i'll edit this post when anything comes up.

EDIT:

I did as you wrote in your post; grub works again. Thanks :)

---

