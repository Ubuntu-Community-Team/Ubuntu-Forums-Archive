---
title: "Share the same /home with another distro"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by shaakunthala on 2009-05-12
Hello,
I'm using Jaunty and I want to install Fedora Leonidas aside as well (dual boot). I use a separate partition for /home and plan to share this same /home among the two distros.

Will this be possible?
Any Ideas?
Any possible problems that I may encounter?

Thank you in advance. :)

---

### Post by Dngrsone on 2009-05-12
It's possible, but I'm not really sure it's advisable.

I know people have shared /home between *buntu installations, but sharing between two different distributions may have some unintended side effects-- dependancies may be at odds or something.

---

### Post by agathian on 2009-05-12
IMHO, sharing the same /home partition/directory shouldnt be an issue per se. 

If any, I would watch out for potential quirks emanating from sharing the dot/config files in your home directories driving the config for things like - shell, windowmanager, X, etc.

---

### Post by Locutus_of_Borg on 2009-05-12
Sharing the same /home is fine
sharing the same /home/<user> is not

---

### Post by shaakunthala on 2009-05-12
Thank you for your replies. :)

Meanwhile I found another hard disk and I could try it out. Sharing the same /home within Fedora and Ubuntu with the same username causes problems. :(

---

### Post by agathian on 2009-05-12
> **shaakunthala said:**
> Thank you for your replies. :)

Meanwhile I found another hard disk and I could try it out. Sharing the same /home within Fedora and Ubuntu with the same username causes problems. :(

Yeah- i totally forgot about that. 
it  is critical that userid is same - since that is what determines ownership of files.

---

### Post by orange-wedge on 2009-05-13
in theory in order to use the same user's /home directory across distros, you would definitely need to setup the same user ids.  this might be your initial problem.  then the next issue becomes how each distro/application inside the distro use all those hidden configuration files in your /home directory.

you could possibly write a custom boot script to move the hidden config files to your home directory between distros...

for example make the directories:

/home/username/.ubuntu-confs
/home/username/.other-distro-confs
/home/username/.active-$distroname.lck

where .ubuntu-confs holds all the hidden config files for your user and at boot copies them over to your home directory.

and .active-$distroname.lck is a directory flag to tell you which was the previous active distro used so that you could copy all the current contents to the correct "backup" directory at boot.

---

### Post by tommcd on 2009-05-13
What I do is create a /data partition for all my data. I then use a separate root partition for each distro I use (currently ubuntu, slackware, and arch). This way all the hidden config directories and files are contained in the home directory of each distros root partition, so they can not conflict with each other. All distros share /data and swap. This method works well and without any chance for conflicts. This is from my fdisk -l:
>   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4080    12289725   83  Linux
/dev/sda3            4081        4207     1020127+  82  Linux swap
/dev/sda4            4208       30401   210403305    5  Extended
/dev/sda5            4208        5737    12289693+  83  Linux
/dev/sda6            5738        7267    12289693+  83  Linux
/dev/sda7            7268       30401   185823823+  83  Linux

/dev/sda2 is ubuntu, /dev/sda5 is slackware, and /dev/sda6 is arch. /dev/sda7 is my data partition that all distros share.

---

