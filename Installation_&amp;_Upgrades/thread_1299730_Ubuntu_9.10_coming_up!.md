---
title: "Ubuntu 9.10 coming up!"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Struki on 2009-10-24
Ok It's simple, I got 3 questions:
1. If I wanna upgrade from 9.04 to 9.10 do I need a fresh new install, or I can simply upgrade tru ubuntus automatic updates?

2. If I upgrade will I have to reconfigure all of my settings regarding audio video etc. conf. or will 9.10 just register my current settings and apply them.

3. I there a reason for me to upgrade in terms of some technical improvements?

Thnx!

---

### Post by slakkie on 2009-10-24
> **Struki said:**
> Ok It's simple, I got 3 questions:
1. If I wanna upgrade from 9.04 to 9.10 do I need a fresh new install, or I can simply upgrade tru ubuntus automatic updates?


Both are valid options.

> 
2. If I upgrade will I have to reconfigure all of my settings regarding audio video etc. conf. or will 9.10 just register my current settings and apply them.


That is the benefit of an upgrade, get a new OS, with your old settings. If things change, you will get a prompt asking you to change the given config file, or do other actions.

> 
3. I there a reason for me to upgrade in terms of some technical improvements?


For the upgrade to Karmic I would consider doing a fresh install. The ext4 filesystem which becomes the default, grub2 are main reasons for me to reinstall, rather then upgrade. That said, I'm running an upgraded version of Karmic, with ext3 and grub-legacy.

---

### Post by motsteve on 2009-10-24
The technician in me has one simple answer: If it isn't broken, don't fix it.  The gizmo kid in me says to go for it.  If you are going from 32 bit, I think you are pretty safe, but I would recommend a clean install if you have room on one of your disks. I always back up my /home with fwbackups as this gives me a tar file that I can use in any Linux setting for extraction.  I also use the command: dpkg --get-selections > filename for holding my package list that you can reinstall with package manager in the new place.  I would also advise backing up your evolution settings to a file if you use that as your mail tool.  Install Karmic wherever you have room and then make sure it's working before transferring all the old stuff over.  Remember also to write down any apps that you installed manually in case you want to do the same in the new place.

I'm 64 bit and happy with 9.04, but 9.10 offers a lot of new, neat stuff that's more sizzle than taste for me, but it does have a really nice kernel and I think it's sporting the new grub2 bootloader as near as I can tell.  It is the future of Linux so stepping up to it is probably a good idea.

---

### Post by Struki on 2009-10-24
> **slakkie said:**
> 
For the upgrade to Karmic I would consider doing a fresh install. The ext4 filesystem which becomes the default, grub2 are main reasons for me to reinstall, rather then upgrade. That said, I'm running an upgraded version of Karmic, with ext3 and grub-legacy.

That sounds reasonable, but based on Win experience, does fresh install mean formating partitions and backing up data, cause to tell you the truth that's kinda of a big no no. I would like to upgrade and get all the new benefits and perks, but if that means a complete data recovery, I'll pass. So any thoughts on that matter?

---

### Post by slakkie on 2009-10-24
> **Struki said:**
> That sounds reasonable, but based on Win experience, does fresh install mean formating partitions and backing up data, cause to tell you the truth that's kinda of a big no no. I would like to upgrade and get all the new benefits and perks, but if that means a complete data recovery, I'll pass. So any thoughts on that matter?

The ext3 to ext4 conversion is possible to do, but the biggest drawback is that for already existing files it will not matter if you have ext3 or ext4. The performance increase in that case almost none. For files that are created after you converted ext3 to ext4 you will have a performance increase and have all the ext4 benefits. [http://ubuntuforums.org/showthread.php?t=1293615](http://ubuntuforums.org/showthread.php?t=1293615)

I know what I'm going to do. Once Karmic hits final I will create a list of packages currently installed and copy /etc to somewhere.

Then install Karmic via a minimal installation CD, make my root filesystem ext4. When that installation is done, I will copy my backed up /etc dir over to the newly installed OS. And install all packages I currently have installed. This way I will have my old install but on a new and fresh ext4 filesystem. 

I can do it because I already have Karmic. You could do the same for your Jaunty install. Then upgrade to Karmic and do the grub-legacy to grub2 upgrade manual (it is rather trivial).

I must say I have a seperate /home, /var/log, /opt directories which will stay ext3 for now. When ext4 becomes more and more supported I'll change them to ext4 as well, moving data off-site, convert to ext4, restore data.

---

### Post by deusdara on 2009-10-24
Hi

Dont worry, but fresh install is more safe.

---

### Post by killabee44 on 2009-10-24
> **slakkie said:**
> The ext3 to ext4 conversion is possible to do, but the biggest drawback is that for already existing files it will not matter if you have ext3 or ext4. The performance increase in that case almost none. For files that are created after you converted ext3 to ext4 you will have a performance increase and have all the ext4 benefits. [http://ubuntuforums.org/showthread.php?t=1293615](http://ubuntuforums.org/showthread.php?t=1293615)

I know what I'm going to do. Once Karmic hits final I will create a list of packages currently installed and copy /etc to somewhere.

Then install Karmic via a minimal installation CD, make my root filesystem ext4. When that installation is done, I will copy my backed up /etc dir over to the newly installed OS. And install all packages I currently have installed. This way I will have my old install but on a new and fresh ext4 filesystem. 

I can do it because I already have Karmic. You could do the same for your Jaunty install. Then upgrade to Karmic and do the grub-legacy to grub2 upgrade manual (it is rather trivial).

I must say I have a seperate /home, /var/log, /opt directories which will stay ext3 for now. When ext4 becomes more and more supported I'll change them to ext4 as well, moving data off-site, convert to ext4, restore data.

Slakkie,

I am running Jaunty 32 and want to do a clean install of Karmic 64 when ext4 it is released. I am kind of new to Linux so if you could please help me with some questions.

I see you said that you would:

 "create a list of packages currently installed and copy /etc to somewhere" 

then: 

"copy my backed up /etc dir over to the newly installed OS. And install all packages I currently have installed"

Also: 

"Then upgrade to Karmic and do the grub-legacy to grub2 upgrade manual (it is rather trivial)"

Could you go into more detail? I have a HD and can copy my /etc dir to it, but is it as simple as copying the contents over to the /etc dir in Karmic?

Please explain your other steps. I would really appreciate it. Thanks.

---

### Post by slakkie on 2009-10-25
> **killabee44 said:**
> 
I am running Jaunty 32 and want to do a clean install of Karmic 64 when ext4 it is released. I am kind of new to Linux so if you could please help me with some questions.

I see you said that you would:

 "create a list of packages currently installed and copy /etc to somewhere" 



This is what I do:

```

# Backup /etc
sudo tar zcvf $HOME/etc/etc.tgz /etc
# Create a list of installed packages:
dpgk --get-selections > $HOME/etc/dpkg.list

```


> 
then: 

"copy my backed up /etc dir over to the newly installed OS. And install all packages I currently have installed"


```

# Restore /etc
sudo tar zxvf $HOME/etc/etc.tgz
# Restore package list
sudo dpgk --set-selections < $HOME/etc/dpkg.list
sudo apt-get dselect-upgrade

```

When you do this when you backup your /etc dir on Jaunty, be aware that you will override certain config files. For example the lsb-release packages stores a file in /etc which you will override by Jaunty's version. So you might want to reinstall the lsb-release package in that case.. YMMV

> 
"Then upgrade to Karmic and do the grub-legacy to grub2 upgrade manual (it is rather trivial)"



The short version:
```

sudo aptitude install grub-pc

```

This will install grub2 and you need to follow the instructions on screen. Make sure you chainload from grub-legacy to grub2. Then reboot and check if the chainload from grub to grub2 works as expected and that grub2 lists all your operating systems. If all works well, run update-grub-from-legacy (it is called different, but the installer will say the correct script to run). And you have migrated from grub-legacy to grub2. This is the short version of course, have a search on the forums for a more documented transition. But since you'll install Karmic rather then upgrade you will not have to do this, grub2 is the default on new installs.

---

### Post by killabee44 on 2009-10-26
Thanks for the help. I will let you know how it goes after Karmic final is released.

---

