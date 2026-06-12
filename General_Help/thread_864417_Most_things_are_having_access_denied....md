---
title: "Most things are having access denied..."
date: 2008-07-19
forum: General Help
---

### Post by spudthebinx on 2008-07-19
Hi, I have a feisty lamp server set up, or at least I did until today. I copied over my main boot driv to a new drive, then upgraded my pretty much all my hardware. Now when I boot up quite a few things refuse to start, most significantly apache2 and mysql. If I try to start apache2 through webmin it gives an error message 'sh: /etc/init.d/apache2: Permission denied. Mysql just fails to start every time without giving an error. I am guessing I have shafted everything, unless this is rescuable? If it is not savable I will reinstall the latest version of Ubuntu, but I really need to save my database as my missus has been editing a wordpress blog. is there a bunch of sql files that represent the databse itself that I can copy over before I reinstall? Funniest thing is I always tell my missus to back up but I never did it myself :( Oh and I already formatted the original drive and it is in my xbox.

---

### Post by spiderbatdad on 2008-07-19
it is obviously a permissions problem you are having. I'm thinking you created a new user id before copying the files? I would also look at ownership. The data should still be there. You just need to get the ownership straightened out.
Are you starting apache as root? for example: sudo /etc/init.d/apache2 start

---

### Post by spudthebinx on 2008-07-19
I click on start apache in webmin. I thought it may be to do with permissions and tried to chmod the whole etc directory and now I can't even connect into webmin or using putty. I did not create any new users when I cloned my drive, I just copied the ext3 and swap partition onto the new drive and installed grub. I am happy to reinstall and start again as long as I can somehow back up my databases and website. All my main data is on 2 seperate 200 gb drives which is safe as far as I can tell.

---

### Post by spiderbatdad on 2008-07-19
oh no! to chmoding the whole /etc directory...that would be difficult to recover from. If you are happy to reinstall, that might be the best option at this point. The default permissions of the system directories are necessary, it is always possible to change permissions of particular files, but never ever alter an entire directory...especially /etc unless you know exactly what you are doing.

You should be able to back up all personal file onto disk. Is this a problem? Have you lost your config files, html indexes, or database?

---

### Post by spudthebinx on 2008-07-20
Thats the problem, I don't know where my databases or my apache web folders are, and they are the only things I am particularly bothered about that are on my ubuntu drive. As long as I can copy those over onto my other two drives and then restore them after a reinstall it really is no big deal. Plus I get the latest version of ubuntu which is surely a bonus.

Many thanks for the help so far :)

---

### Post by spudthebinx on 2008-07-20
Sorry for the double post, but I had a thought. Can I put my ubuntu drive out of my server and into this pc (Kubuntu) and back up the contents to a dvd? The data on the system drive is only 2gb so it wil fit nice and easily. Sorry if this is a silly question but I have no clue with linux permissions and if I can see the files I need that way.

---

### Post by spudthebinx on 2008-07-21
Just to update, it looks like it is a hardware issue. I can't even do a fresh install of ubuntu server. After buring the iso on many different burners and different media, each disc is having checksum errors, but in different places each time even on the same disc. Looks like it was a wild goose chase :(

---

