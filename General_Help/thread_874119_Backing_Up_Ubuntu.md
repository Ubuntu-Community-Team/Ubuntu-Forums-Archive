---
title: "Backing Up Ubuntu"
date: 2008-07-29
forum: General Help
---

### Post by BlueKnight84 on 2008-07-29
Hello everyone.

I am running Ubuntu 6.10 and desperately need to catch up with the times.  I'm about to do a clean install, but I need to back everything up first.

My biggest concern is saving my website settings, because the machine runs my email and part of my website, so I'll need to definitely preserve the apache and mail configuration settings.

The machine is without a CD writer, as well.

How do I go about backing up my system?  Thanks for reading!

---

### Post by nbayiha on 2008-07-29
Why do you want to backup your system.
You wont loose anything if you did create a /home partition when u were installing ubuntu.
When you are going to do a clean install just keep you /home partition and you will have everything just as fine as before ,and you can erase the /swap partition and the / (system) partion .

---

### Post by DagMan on 2008-07-29
His webserver settings would probably be in /etc if not in various places given his own files to go along with it.  I actually don't know where specifically though, and you could be right that they reside in his home folder but to be safe...

---

### Post by RuleMaker on 2008-07-29
I'm not sure if I'm doing something wrong, but when I installed my ubuntu I've set it's mount point to "/" so my home directory is on the partition with other system directories.

---

### Post by BlueKnight84 on 2008-07-29
> **DagMan said:**
> His webserver settings would probably be in /etc if not in various places given his own files to go along with it.  I actually don't know where specifically though, and you could be right that they reside in his home folder but to be safe...

Thanks to the both of you for offering advice.

So even with a clean install, I would be keeping my /home folder?  That's cool.  And let's just say that the majority of what I need is the /etc folder, I could back that up over a network just to be safe?

Also, if I'm doing a clean install, I wouldn't have to do it sequentially from 6.10 > 7.04, etc., right?  I could just clean install 8.04?

---

### Post by DagMan on 2008-07-29
> **RuleMaker said:**
> I'm not sure if I'm doing something wrong, but when I installed my ubuntu I've set it's mount point to "/" so my home directory is on the partition with other system directories.
Can you start a separate thread for this please, and when you do, it would help if you specify if you have a working install or not, if you have a folder with the name /home/USERNAME where username is what you use to log in with, and how many partitions you have.  I think you are asking if it is okay to have just / and swap partitions, and the answer is yes, but if that isn't what you're after then it's confusing to have 2 differant questions in 2 differant threads.
Thanks.:)

---

### Post by nbayiha on 2008-07-29
```
Also, if I'm doing a clean install, I wouldn't have to do it sequentially from 6.10 > 7.04, etc., right? I could just clean install 8.04
```

Nope you dont have to do sequentially , just go to the 8.04 straight away.

You can sent the etc/folder to your mail, just for more assurance, but keeping you /home partition untouched should do the thing.

I have a question ,why don't try to upgrade the system straight from 6.10 to 8.04 without having to do a clean installation ?

@DagMan it's not the guy who posted the thread who asked that question . Check the name :D

---

### Post by BlueKnight84 on 2008-07-29
> **nbayiha said:**
> ```
Also, if I'm doing a clean install, I wouldn't have to do it sequentially from 6.10 > 7.04, etc., right? I could just clean install 8.04
```

Nope you dont have to do sequentially , just go to the 8.04 straight away.

You can sent the etc/folder to your mail, just for more assurance, but keeping you /home partition untouched should do the thing.

I have a question ,why don't try to upgrade the system straight from 6.10 to 8.04 without having to do a clean installation ?

I wanted to just upgrade it (since I'm totally new to Ubuntu and it's easier and less risky), but as I understand it, I can't.  Here's a thread I posted about an hour ago, which is how I came to the conclusion that I needed to do a clean install.

[http://ubuntuforums.org/showthread.php?t=874091]("http://ubuntuforums.org/showthread.php?t=874091")

---

### Post by nbayiha on 2008-07-29
After reading, i think too that it will be wise for you to do a clean installation :d.  Just keep your /home folder untouched , and format the swap partition and the / (system) one.

---

### Post by BlueKnight84 on 2008-07-29
> **nbayiha said:**
> After reading, i think too that it will be wise for you to do a clean installation :d.  Just keep your /home folder untouched , and format the swap partition and the / (system) one.

I guess I'll know what you mean when I start the upgrade, huh?  I'd hate to skip the step or oversee the step where I tell it to keep my /home folder.

---

### Post by RuleMaker on 2008-07-29
Im not sure about mail server, but to backup apache configuration do this:
```
cd /etc/apache2/
cp apache2.conf ports.conf envvars httpd.conf ~
```

---

### Post by DagMan on 2008-07-29
> **BlueKnight84 said:**
> Thanks to the both of you for offering advice.

So even with a clean install, I would be keeping my /home folder?  That's cool.  And let's just say that the majority of what I need is the /etc folder, I could back that up over a network just to be safe?

Also, if I'm doing a clean install, I wouldn't have to do it sequentially from 6.10 > 7.04, etc., right?  I could just clean install 8.04?I think the best thing is to try to look back over how you configured your apache and mail and see where the files live, all of them, not just the configuration files.  If you want to have a look at the config files though, you can download the packages that are involved in the setup, for example 
apt-get install --reinstall -d apache
and the -d tells it to download the file only.  then get the .deb file to your home folder
cp /var/cache/apt/archives/*apache* ~/
right click on it and select file-roller pr archive manager, then double click on the file in there thats called 'data' and browse what files were involved in the install.  That is just for the apache package.  I don't know what other packages are involved in your setup and am not familiar with webservers.  You also want to look at where files that it uses are stored on the drive and save them.

As for the upgrade, two things stick out at me.  One is that it's quite an upstream jump to go from 6.10 to 8.04, and even if you use a clean from disk, you should seek better assistance on the compatability of your webserver configuration files from the version your run now to the current version.  Hopefully there will be someone who can answer better if it will be a problem or not or what needs to be done, if anything at all.  That there seems like a new topic entirely.

For upgrading using the  dist-upgrade... upgrading over the net, I've read in the past that it isn't recommended to upgrade more than one version, and it looks like you want to go up 3 versions.  There's usually a few things to work out with proper dependencies when it is just going up one version, so if that's the method you mean I think it's better to use a new install.  

BTW, I was just thinking, perhaps you can run hardy in a VM and try to get all your webserver working from the VM alone and then you'lle have a better idea of what to backup.

---

### Post by BlueKnight84 on 2008-07-29
> **DagMan said:**
> I think the best thing is to try to look back over how you configured your apache and mail and see where the files live, all of them, not just the configuration files.  If you want to have a look at the config files though, you can download the packages that are involved in the setup, for example 
apt-get install --reinstall -d apache
and the -d tells it to download the file only.  then get the .deb file to your home folder
cp /var/cache/apt/archives/*apache* ~/
right click on it and select file-roller pr archive manager, then double click on the file in there thats called 'data' and browse what files were involved in the install.  That is just for the apache package.  I don't know what other packages are involved in your setup and am not familiar with webservers.  You also want to look at where files that it uses are stored on the drive and save them.

As for the upgrade, two things stick out at me.  One is that it's quite an upstream jump to go from 6.10 to 8.04, and even if you use a clean from disk, you should seek better assistance on the compatability of your webserver configuration files from the version your run now to the current version.  Hopefully there will be someone who can answer better if it will be a problem or not or what needs to be done, if anything at all.  That there seems like a new topic entirely.

For upgrading using the  dist-upgrade... upgrading over the net, I've read in the past that it isn't recommended to upgrade more than one version, and it looks like you want to go up 3 versions.  There's usually a few things to work out with proper dependencies when it is just going up one version, so if that's the method you mean I think it's better to use a new install.  

BTW, I was just thinking, perhaps you can run hardy in a VM and try to get all your webserver working from the VM alone and then you'lle have a better idea of what to backup.

I can't thank each one of you enough for your help.  I really do appreciate it.

I'll give these ideas a 'go' and see what happens.

> **RuleMaker said:**
> Im not sure about mail server, but to backup apache configuration do this:
```
cd /etc/apache2/
cp apache2.conf ports.conf envvars httpd.conf ~
```

I'll try this out, as well.

Thank you all again and I'll update this thread appropriately!

---

### Post by nbayiha on 2008-07-29
:lolflag:
Keep us update .

---

### Post by nfox on 2008-07-29
If your home folder is on a separate partition then you're good as long as you don't reformat it and leave it's path set in the partitioner when you reinstall. 

If not, then just back up your files and go for the config files. What could you possibly have set up that the apache config, php.ini, etc. won't cover? If you know the answer then you already know the files to back up.

My advice would be to tar it up (space permitting and only the folders like /etc that matter anyways) and reinstall. The untar and copy your config files later onto your newly install server. 


My main point is that the config files for an older version of an app is not going to be very useful. Just take notes from now on and rewrite the new configs.

---

### Post by BlueKnight84 on 2008-08-16
Thanks to everyone for their help.  I'm sorry for just now updating all of you, as I went on vacation and have just now been able to resume tackling this issue.

Well I have good news!  I updated my sources.list to:

```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

...then I ran "sudo apt-get update" and voila!- it worked!  Now I shouldn't have any problems simply "upgrading" my Ubuntu installation.

Thanks again to all of you who helped me!!!

---

