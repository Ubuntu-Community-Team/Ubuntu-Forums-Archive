---
title: "Stability of Upgrades"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by nnutter on 2009-08-07
I can't imagine that this hasn't been discussed but I think because of the words I wasn't able to find it.

In general is it considered safe/stable to upgrade from one major version of Ubuntu to another? I know it is doable and instructions are posted. I just want to know if there is an advantage to doing a clean install. I'd prefer proof/example than a simple yes/no.

---

### Post by pmlxuser on 2009-08-07
clean install = loosing all your settings
upgrade = keep all settings and use the latest technology coming with stable verison.

I have done both, when i have messed up my system so much that i thing i can't make it better again i do a clean install. when a new release come i upgrade to it.

New release have advanced features that did not exist in the previous one and its nice to be inline with technology. same reason why people don't use windows 95 but vista/ xp (in windows world)

clean install gives you the assurance of having things likely to work because if it works on the live cd its likely to work after install, upgrades have sometimes an element of suprise and if you don't know how to deal with that you might be in for a suprise.

to me both works because all my data are mounted on a difernt partition that the OS files (so I upgrade if system is screwed, i do clean install) at the end i achieve having the most recent stable version of my ubuntu.

---

### Post by oldfred on 2009-08-07
I have been updating every 6 months since 6.06 Dapper Drake. While Ubuntu gets better many times I have had some issue with something. I am not afraid of breaking things and like solving problems so each time is an adventure.
In these forums I find the suggestion of a separate /home so you do not lose most of your settings. I still find I like having copies of certain system config files where I may have made changes like menu.lst, fstab, sources.list, smb.conf etc. Some of these end up being obsolete in a new version. xorg.cong has almost completely been replaced by hal. menu.lst will be replaced when grub2 is used. But I still like to see what settings I had. I also export a packages list but found I was reinstalling old packages I did not need as new ones have replaced them.
I am following pmlxuser's logic as I am using 32 bit ubuntu but installed the 64 bit in a new partition and migrating to 64 bit. I now have a separate /data partition for shared data, but because of the potential of 32 bit and 64 bit configs in /home I am not sharing /home.

---

### Post by slakkie on 2009-08-08
I prefer to do upgrades over clean installations, since all of my configs (/etc) will stay the same, same goes for init.d scripts.

If you really mess up your system, you can either restore a backup (see clonezilla.org for backup software) or you can reinstall.

If I do a clean install I will always use the alternate CD or minimal CD. The latter allows you to install packages straight from the web, so no updates are required after installation.

If you install after the release date there will always be the following cycle, depening on the way you upgrade/install.

LiveCD:
clean install/apply upgrades/install previous software/reconfigure all apps

Minimal cd:
clean install/install previous software/reconfigure all apps

Upgrade:
upgrade

I've done all, and I prefer the upgrade over a clean reinstall any day. The only reason for a clean install would be if I lost a backup or if all fails.. 

PS. Having a seperate /home slice makes your live easy. Whatever ou will do.

---

### Post by nnutter on 2009-08-08
It definitely sounds like having a partition for /home is a good idea. Is there any reason not to also keep one for /etc?

Otherwise it pretty much sounds like you're all saying, upgrade either works or it doesn't and be prepared if it doesn't. Nobody has really made any comments on how often an upgrade has or hasn't worked though.

---

### Post by slakkie on 2009-08-08
/etc is a bit tricky, since all the init scripts and configuration files (like fstab) reside there, which are needed to boot/mount partitions. 

See also: 
* [https://bugs.launchpad.net/ubuntu/+bug/148331](https://bugs.launchpad.net/ubuntu/+bug/148331)
* [http://ubuntuforums.org/showthread.php?t=1228970](http://ubuntuforums.org/showthread.php?t=1228970)

As for the upgrades, yes, it either works or doesn't work, but IMHO same applies for a clean install. If an upgrade will install a package which causes a bug then the clean install will also install that bug. 

For me personally the only upgrade I really had problems with was 8.04 to 8.10, which was related to an intel driver within xorg. And I was put off by the switch to kde4.0 in that release. That problem would have occurred even when I did a clean install.. 

A friend of mine had real issues with the switch to UUID's in fstab since it broke his mirrors. In that case he would have needed to setup the mirrors again after the clean install (same thing he needed to do with the upgrade). That was 5 -> 6 iirc. 

I've done many upgrades, from 4.10 to 6.06 to 8.04 and from 6.10 to 8.04 and last week I've upgraded from 8.04 to 9.10.

On the forums most people advise a clean install because they had one upgrade that went sour. I sometimes wonder how they would act if an installation went bad..

---

### Post by nnutter on 2009-08-15
> **slakkie said:**
> 
On the forums most people advise a clean install because they had one upgrade that went sour. I sometimes wonder how they would act if an installation went bad..

;-) That's kinda what I've been experiencing.

I've always assumed but a confirmation would be nice...Does apt remove all the unused old files when it upgrades things, e.g. would upgrading leave "cruft" behind?

---

