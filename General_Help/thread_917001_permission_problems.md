---
title: "permission problems ????"
date: 2008-09-11
forum: General Help
---

### Post by justgrant2009 on 2008-09-11
Ok, so here's my situation.  I'm not exactly a newbie but i'm still learning (as people always do with linux) and i was trying to install a game that the script told me i did not have permission to change the folder it was going to install it to.  So, like an idiot, i sudo chmod 777 -R on everything from / down. (whoops) bad idea, (better than sudo rm -rf / at least) but anyways, now when i log in, it tells me that my home drive permissions are wrong and there are problems and what not.  Is there a way that i can return everything to it's original permissions? or am i just screwed?

---

### Post by drs305 on 2008-09-11
As you know, your HOME permissions have become messed up. The good news is that you can run the commands below to correct the ".dmrc" permission errors you get on boot. If you can't use 'sudo' or log into any account, choose 'Recovery mode' > 'root' from the grub menu and boot to a root prompt. 

This will probably resolve your home permissions. The bad news is that if you used the '-R' switch to change your / permissions you will probably end up having to reinstall in the end. The permissions are not uniform throughout the system and trying to restore them is probably going to be harder than a reinstall. That being said, here are the initial steps you should take:

In these instructions I've used the common 755 permissions, but you can use 750, 700 or some other setting:
```

sudo chown *username*: /home/*username*
chmod 755 ~/ && chmod 644 ~/.dmrc
sudo shutdown -r now

```

---

### Post by drs305 on 2008-09-11
As you know, your HOME permissions have become messed up. The good news is that you can run the commands below to correct the ".dmrc" permission errors you get on boot. If you can't use 'sudo' or log into any account, choose 'Recovery mode' > 'root' from the grub menu and boot to a root prompt. 

This will probably resolve your home permissions. The bad news is that if you used the '-R' switch to change your / permissions you will probably end up having to reinstall in the end. The permissions are not uniform throughout the system and trying to restore them is probably going to be harder than a reinstall. That being said, here are the initial steps you should take:

In these instructions I've used the common 755 permissions, but you can use 750, 700 or some other setting. You can also use the -R switch to include subfolders if desired. *The last command will shutdown and reboot the system, so close down your other apps before running it.*
```

sudo chown *username*: /home/*username*
chmod 755 ~/ && chmod 644 ~/.dmrc
sudo shutdown -r now

```

---

### Post by justgrant2009 on 2008-09-11
Thank you that's pretty much what i was looking for, i knew i wouldn't be able to completely reverse everything without a complete reinstall but just needed to go back a bit at least to get rid of the login problem.  I"m the only one who uses this computer so i'm not worried about others messing with things.  Thanks a ton!

---

