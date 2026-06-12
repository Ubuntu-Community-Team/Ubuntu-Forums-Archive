---
title: "Re-installin Ubuntu"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by ed_d on 2005-12-11
If I want to do a "fresh" re-install of ubuntu, and I have all my documents on a seperate drive that is now mounted as /home/multimedia, will I lose if if I reinstall the os? I figured that if its mounted under another filesystem and if during the install I dont mess with it, as far as trying to format it, it should be good, right?

Thanks,
Ed

---

### Post by taurus on 2005-12-11
You have to be careful with that since Ubuntu will create /home to store users' info there.  Therefore, I recommand you either backup all your important stuff on a CD/DVD, or create another partition and call it /data.  Once you have re-installed Ubuntu, mount /data somewhere and copy back your important stuff...

---

### Post by aysiu on 2005-12-11
[QUOTE=ed_d]If I want to do a "fresh" re-install of ubuntu, and I have all my documents on a seperate drive that is now mounted as /home/multimedia, will I lose if if I reinstall the os?[/QUOTE] If you know what you're doing, you can do a fresh re=install and keep your documents and settings intact (since they are on a separate drive). However, you have to know what you're doing.

For example, do you know where the separate drive is in the partition table? (I'm guessing something like /dev/hdb1). Do you know how to manually edit the partition table during installation?

---

### Post by ed_d on 2005-12-11
I know that during the install it gives you the option to "erase" everything on the partitions. Also, its a 36gb scsi drive that has the data and that my OS disk is a 18 gb scsi drive.

I think if I just "view that partition info and ensure the mount point is correct and then "leave alone" it should be ok. I will also try to move my stuff to another PC on my home network too.

I guess Ill take a look and see, not alot of data to lose if happens anyway.

I guess sometimes you have to roll the dice to learn some things. I will give update when finished.

---

### Post by kori.mendocino on 2005-12-11
as a rule of thumb, to prevent the risk of erasing your personal data & settings in the case of reinstallation, /home is always on a separate partition. if you want to keep your installed software, too, you should separate /usr on a different partition, too. then, during reinstallation, you reformat your root & swap partitions, and mount your /home and /usr as, well, /home and /usr :)

---

### Post by az on 2005-12-11
Why do you need to reinstall?

---

### Post by ed_d on 2005-12-11
Well......
I think i really messed up on some things, like my samba just stopped working after a test run of Automatix (not saying it was the culprit (sp)) Thinking that I did something on my own. Plus, want to do it to just clean up a few things.

I also read that when you install or update to another release, such as Dapper, thet the recommend path is to install rather than upgrade, and this might give me the practice. Its just my home box, but also if I choose to help others, its best to know whats going on first.

---

### Post by ed_d on 2005-12-11
Sucsessful re-install and still have the other disk with all data intact. Now I know how to do this agian if necessary

---

### Post by az on 2005-12-11
[QUOTE=ed_d]
I also read that when you install or update to another release, such as Dapper, thet the recommend path is to install rather than upgrade, a.[/QUOTE]


No, you can dist-upgrade from one version to another.  You can even dist-upgrade from Woody to Ubuntu.

If you dist-upgrade from Breezy to Dapper today (Dapper will be broken for another littel while) and want to revert your box, you will probably bork it up and will have to reinstall.  Package management works upwards, not downwards.  Well, not easily.

---

### Post by NotJustANewbie on 2005-12-12
I've seen many articles claiming that upgrading by just changing repositories' names to the new stable name and hitting apt-get dist-upgrade (after apt-get update) doesn't work and it just "borks" up your system.  I've also read that this is the best way to updgrade and it works fine...

I'm on breezy at the moment, I'll have to see what happenes when I upgrade to Dapper when the time comes... Fingers crossed :???:

---

