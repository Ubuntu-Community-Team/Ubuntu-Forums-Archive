---
title: "backup app..."
date: 2008-11-28
forum: General Help
---

### Post by zander1013 on 2008-11-28
hi,

what app should i use to backup my ibm thinkpad t42 run by ubuntu 8.10 to a usb hdd?

thank  you.

---

### Post by Coreigh on 2008-11-28
That really depends what kind of back up you want. Do you simply want to protect your documents, picture music etc.? Then just copy them using Nautilus.

Or are you wanting a system back up to restore functionality of the machine after a major failure. Not as easy and honestly I don't know. I just back up my "stuff" and re-install if I have a major failure.

---

### Post by zander1013 on 2008-11-28
> **Coreigh said:**
> That really depends what kind of back up you want. Do you simply want to protect your documents, picture music etc.? Then just copy them using Nautilus.

Or are you wanting a system back up to restore functionality of the machine after a major failure. Not as easy and honestly I don't know. I just back up my "stuff" and re-install if I have a major failure.

the latter... i would like to be able to do a system restore. the process you described is where i am at too. i would like to 'take it to the next level' as it were. i was hoping that i could find something like mac os 'time machine' backup app or better.

perhaps i can just search the package tools and get some idea that way.

---

### Post by zander1013 on 2008-11-28
okay,

i just searched with the term "backup" in the add/remove package tool and it has offered a number of apps that can do various types of backups.

... i was just hoping that someone had experience and could say "just install app x, y and z".

peace.

---

### Post by michaelzap on 2008-11-28
> **zander1013 said:**
> the latter... i would like to be able to do a system restore.

I use Grsync to copy my home directory to a network drive, and you could do the same thing with your USB HD. Grsync is a graphical user interface for rsync, which is a very powerful and popular backup tool. It will copy every file the first time that you run it and then after that it can be set to only copy changed files.

This is the data that you really need in order to do a system restore. When I upgraded to Ibex recently, I ran the backup and then did a fresh installation of Ubuntu (reformatting the drive) and then copied my home folder from the backup on the network drive to my new installation. I still needed to install all of the non-standard software that I use, but everything (including this software) was configured just as it had been on the old system.

I also backup all of my most important files to a remote server using Jungle Disk/Amazon S3, but that's mostly because I don't take the network drive off-site after backing up to it (so if there were a fire or a robbery I could lose it).

---

### Post by EvilRobotDrew on 2008-11-28
if you want an image of your current drive, as in a complete and total copy of your system today, then you should look into remastersys. i used it recently to create a custom liveDVD (this also may be a good option for you) and there is an option to create an image of your current setup. i haven't used this option, but the liveDVD seems to work fairly well.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by zander1013 on 2008-11-28
cool! i will check these apps out.

i like the one that backs up the system to a cd/dvd. that sounds like what i had in mind. something similar to what you would do with a store bought system.

in the meantime i have installed 'keep' and just set it to backup /home.
keep looks like a nice medium between the whole system backup and a personal file backup.

thank you for your good advise.

-zander

---

