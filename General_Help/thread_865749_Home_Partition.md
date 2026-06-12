---
title: "Home Partition"
date: 2008-07-20
forum: General Help
---

### Post by MarshyTheKid on 2008-07-20
So I just tried to reformat my computer and I don't know why, but it didn't reformat, just installed a new partition of Ubuntu.
I figured, rather than reformat, I can just take my old home folder and make it the new home partition.
I wasn't sure how to go about doing this.
I've found how I can move the home folder to a new partition, but not how to do this. 
Can someone lend a hand?
Thanks

---

### Post by Tim Sharitt on 2008-07-21
Are you saying that your home folder on the previous installation was on its own partition? If that's the case, edit fstab to have that partition mounted as /home/USERNAME.

---

### Post by MarshyTheKid on 2008-07-21
> **Tim Sharitt said:**
> Are you saying that your home folder on the previous installation was on its own partition? If that's the case, edit fstab to have that partition mounted as /home/USERNAME.
No. I have 2 versions of Ubuntu on it now. I want to take the old version, save the home and remove the OS on that.

---

### Post by Dr. C on 2008-07-21
There are many guides for creating a separate /home partition in Ubuntu for example [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") I found this from Google. 

Once the separate /home partition is set up one can reformat the / (root) partition and reinstall. The trick is to keep the same user name and password. When reaching the partitioner during the reinstall choose manual partitioning and mount the old /home partition as /home

I have done this repeatedly and it works like a charm.

---

### Post by MarshyTheKid on 2008-07-21
> **FineE said:**
> There are many guides for creating a separate /home partition in Ubuntu for example [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") I found this from Google. 

Once the separate /home partition is set up one can reformat the / (root) partition and reinstall. The trick is to keep the same user name and password. When reaching the partitioner during the reinstall choose manual partitioning and mount the old /home partition as /home

I have done this repeatedly and it works like a charm.
So what I will do with the old system is delete everything but the home folder and edit my fstab to focus the home folder to that?

---

### Post by MarshyTheKid on 2008-07-21
> **MarshyTheKid said:**
> So what I will do with the old system is delete everything but the home folder and edit my fstab to focus the home folder to that?
Ugh. I changed my fstab and rebooted. It said it couldn't load the home folder and it would try to load my home folder as root, but that failed for some reason.
I realized that for some reason the permissions to my home folder was for root and I probably should change that. However my live disk was damaged today. 
I hate not having blank cds when I need them.

---

### Post by Potatoj316 on 2008-07-21
You could just move the files from the old home to the new home.  You have already mounted it so it should just be a simple drag and drop in nautilus (the file manager)

---

### Post by MarshyTheKid on 2008-07-21
Hmm. Actually it looks like when I type /home there is a folder called home. So the path would be /home/home/marshythekid
I could just go sudo cp /home/home/marshythekid /home
Right?

Edit: Actually it would have to have the flag -R and I can't copy it, it would be mv.


Sorry I'm just kinda thinking outloud and hoping if something is wrong, someone will correct me

---

### Post by Potatoj316 on 2008-07-21
i dont think you need the sudo and you probably want to move not copy so I would try this (actually i have no idea if this will work, I just made up the -r part, i hope its recursive you might want to check on that first with mv --help)
```
mv -r /home/home /home
```

or you could open 2 nautilus windows one in /home and the other in /home/home.  Then drag the files from /home/home to the /home one and then delete the home directory in home (wow thats confusing), did I get that right?


Oh shure, go and edit your post while im replying

---

### Post by MarshyTheKid on 2008-07-21
> **Potatoj316 said:**
> i dont think you need the sudo and you probably want to move not copy so I would try this (actually i have no idea if this will work, I just made up the -r part, i hope its recursive you might want to check on that first with mv --help)
```
mv -r /home/home /home
```

or you could open 2 nautilus windows one in /home and the other in /home/home.  Then drag the files from /home/home to the /home one and then delete the home directory in home (wow thats confusing), did I get that right?


Oh shure, go and edit your post while im replying
Haha, thanks bud.
Yeah -r doesn't work with mv. I have it all working now. I had to go into terminal recover mode to edit it. I hadn't realized that my top bar would be recovered too. :) That makes me so happy because I realized I forgot to screenshot it to recreate it. Oh Linux, how I love you.
I appreciate the help. Now I just need to figure out what packages I had installed and reinstall. :(

---

### Post by Potatoj316 on 2008-07-21
I dont know if your other install is still working but you might be able to use aptitude to tell you what packages are installed, maybe aptitude -l or something like that

---

### Post by MarshyTheKid on 2008-07-21
> **Potatoj316 said:**
> I dont know if your other install is still working but you might be able to use aptitude to tell you what packages are installed, maybe aptitude -l or something like that
Haha. Nope. I just deleted all of the files about an hour ago.
Its not big deal. My old install was so fubar'd that I wouldn't want to blindly reinstall all of the same packages.

---

