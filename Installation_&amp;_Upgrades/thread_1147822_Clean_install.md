---
title: "Clean install?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Sivan on 2009-05-03
I'm having several odd problems with 9.04 that I think a clean install will fix.

I do have a /home partition. Is there anything I should do in preparation for doing a clean install other than backing up my data?

I assume I would do the install from the live cd and then format the non-home partition.

Does this sound right?

---

### Post by justjoshingyou on 2009-05-03
I dont have the same settup you do but I do remember when I installed Intrepid. I guess all you have to do is select the partition and install the "/" under it. then mark your home partion- like hda/sda1 (idk if thats right)- as home.

---

### Post by blackgr on 2009-05-03
home in general is enough. if yoou have any custom cron jobs or special configs in etc make sure you back up those too

---

### Post by Sivan on 2009-05-03
Is it still a good idea to use a /home partition? I read somewhere that when installing if you have a /home directory that the install process will not format it. Is that correct?

---

### Post by lovinglinux on 2009-05-03
You must choose the manual installation option. Then format the root partition, but just mount the home.

You might also want to create a list of installed applications, so you can re-install them after the "upgrade". Folow the instructions below:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

> **Sivan said:**
> Is it still a good idea to use a /home partition? I read somewhere that when installing if you have a /home directory that the install process will not format it. Is that correct?

You want to know if your current home will carry bad things with it right? I'm not sure, but it is possible. Keeping home is standard procedure, but since you already upgraded and are experiencing issues, then maybe a pristine install is the best way. To do this you should backup and format home, then copy only your documents and the configuration files that are complex to configure (the essential). 

What I did when installing Jaunty was a backup of my home, then I formated the home too (because I wanted ext4) and copied just the necessary files to the new home. For example, I didn't copied the menu configuration files, because that is easy to setup again and my home backup was probably full of junk menus. But I did copy my TV remote configuration files, because the are not so easy to configure. Sometimes I compared the files from the new home with my backup using meld, to make sure nothing weird was being copied and nothing new was overwritten.

---

