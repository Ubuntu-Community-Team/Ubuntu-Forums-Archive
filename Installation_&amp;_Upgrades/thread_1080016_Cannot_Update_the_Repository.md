---
title: "Cannot Update the Repository"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by virus2 on 2009-02-25
I have a peculiar issue with my Fiesty Fawn system.Everytime I run 
"sudo apt-get update",it reports some closed links in between.
i.e i get the message for some of the packages as 'Cannot fetch from server <ip address>.error 404 Not found'.
Also,when i try to install any package through adept manager,I get error as "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."
I suppose the above error is caused by the broken packages not getting downloaded on update.
pls help in this regard....

---

### Post by iaculallad on 2009-02-25
Ubuntu 7.04 aka Feisty Fawn had already reached its End-Of-Life last [October 19, 2008]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-September/000113.html"). Thus, their will be no available updates starting from that date.

---

### Post by virus2 on 2009-02-25
Does that mean that there can be no solution to this...and one has to revert to windows??

---

### Post by konqueror7 on 2009-02-25
no, you don't need to revert to windows, you can just upgrade your existing ubuntu to a new version like 8.04 or 8.10...

---

### Post by iaculallad on 2009-02-25
> **virus2 said:**
> Does that mean that there can be no solution to this...and one has to revert to windows??

Best possible solution would be to upgrade from Feisty to Hardy. Hardy Heron will have it's EOL on April 2011.

Upgrading would also mean harnessing updated kernel, applications, and other important updates.

---

### Post by stumbleUpon on 2009-02-25
> **virus2 said:**
> Does that mean that there can be no solution to this...and one has to revert to windows??

Of course not...!

You just need to upgrade to a newer version of ubuntu. See here for more info

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by virus2 on 2009-02-25
> **stumbleUpon said:**
> Of course not...!

You just need to upgrade to a newer version of ubuntu. See here for more info

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Thanks for that link..
But,I must say that i got disappointed after reading that article in link,as it says that one has to upgrade progressively to next version.
I have CD of 8.04 with me and I assumed that I can directly upgrade from 7.04 to 8.04,but now where can I get the CD of the intermediate version(Pls do not suggest downloading it as iam facing frequent connection issues with my ISP).
I think I better look for a solution to this problem,and,if no success,then i should move back to windows...

---

### Post by Partyboi2 on 2009-02-25
You could backup all your important stuff and do a fresh install of 8.04 this will save you having to upgrade all the releases between your current one and hardy 8.04.

---

### Post by virus2 on 2009-02-25
> **iaculallad said:**
> Ubuntu 7.04 aka Feisty Fawn had already reached its End-Of-Life last [October 19, 2008]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-September/000113.html"). Thus, their will be no available updates starting from that date.

Case is Iam NOT able to download the updates FOR SOME OF THE PACKAGES(NOT FOR ALL)..
If they have stopped updates,then i should have got the error message for all packages..
will post the screenshot of the same when i go home today...

---

### Post by iaculallad on 2009-02-25
> **virus2 said:**
> Case is Iam NOT able to download the updates FOR SOME OF THE PACKAGES(NOT FOR ALL)..
If they have stopped updates,then i should have got the error message for all packages..
will post the screenshot of the same when i go home today...

If for some reason you're not able to update some of your packages (not Feisty's updates), try using different server repository.

---

### Post by virus2 on 2009-02-25
> **Partyboi2 said:**
> You could backup all your important stuff and do a fresh install of 8.04 this will save you having to upgrade all the releases between your current one and hardy 8.04.

I have kept this option available,but the problem is that I will have to re-install my softwares like PHP,MySql,Apache on the new version,which again means downloading the same from repositories..

---

### Post by Partyboi2 on 2009-02-25
To update feisty you should be able to comment out your current ones and  add these to your sources.list
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

---

### Post by avtolle on 2009-02-25
> **Partyboi2 said:**
> To update feisty you should be able to comment out your current ones and  add these to your sources.list
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```
That should get your Feisty as upgraded as you can get it. To go further, though, you would need to do a "network upgrade" to 7.10 which, as I understand your post, presents problems to you. Be aware that if you would d/l and install 8.04, as an example, the repositories would be updated to those with the 8.04 applications and you wouldn't run into the same error messages.

---

### Post by virus2 on 2009-02-26
Well,Thanks everyone for your time.
After seeing all the responses,I thought I better go with the new version,took the backup of all imp stuff and installed 8.04.
Initially,I thought of moving back to windows(which is ready) as Iam dual-booting the two(but i never used go to windows),but after using Linux for about 6 mnths,I liked many of its features and didn't wished to move back to windows.So,installed a fresh copy of 8.04.
But,I had to keep windows also as it is being used by my brother.I was really scared of removing 7.04 as I thought it may affect XP also(which means my brother would go mad at me:mad::mad:).But,after googling,i found that it is very easy.So,took the bold step and installed 8.04.
Now,I have again 2 OS on my machine(1 for me and 1 for my brother)
Happy Ending..:p:p
BTW,Can anyone tell me the EOL of this version...

---

### Post by Partyboi2 on 2009-02-26
Its good to hear you had a happy ending :)
You can see the EOL dates for the different releases from [[COLOR=Blue]here[/COLOR]]("https://wiki.ubuntu.com/Releases")

---

