---
title: "EX HDD is read only but shouldn't be"
date: 2012-10-08
forum: Hardware
---

### Post by Crazy K on 2012-10-08
Hi I posted a similar topic about this, but I've decided to make a whole new topic as the other topic is far too old.  

Anyways I checked out the program "Storage Device Manager" because I wanted to automount my 500GB EX HDD. Well it automounts now, but it's read-only for some reason. I checked off that option so it should allow me to move and delete files as I please. 

Can anyone help me fix this problem? I really don't want to have to use nautilus every single time I want to add and delete files. If I can't do it, is there a possible way of making nautilus open up when I open my EX HDD?

---

### Post by Crazy K on 2012-10-08
Also I used Nautilus to change permission and that doesn't work. It says I do not have permission to change the permission. I'm on root so why can't I do this? 

Is there anything I can do to remedy this situation? Because this is extremely annoying to me.

---

### Post by Crazy K on 2012-10-08
Also I'll need easy to understand steps. Even though I've been using Ubuntu since 2008, I still have trouble with a lot of the stuff.

Also I should add that it's a Fat32 filesystem (my EX HDD that is)

---

### Post by ahallubuntu on 2012-10-08
I'm not familiar with "Storage Device Manager" so I can't help you there.

You could simply add the external drive to your /etc/fstab file and then it will automatically get mounted on every startup, just like the internal drive.  However, it MUST be plugged in, otherwise Ubuntu will get stuck looking for it upon startup.  That's one reason I prefer  not to do this.  Instead, I simply choose the drive from the "Places" menu (in Ubuntu 10.04 LTS) and that mounts the drive plus opens a Nautilus window for it.  I find that easy enough, and I don't have to worry about whether it is plugged in/turned on or not when I start up Ubuntu.  I'm not sure what you find annoying about it.

You could use Gparted to change the label of your external drive so it has some meaningful name in Ubuntu instead of some random string of letters and numbers (the UUID) or the size.

FYI, FAT32 is not the ideal filesystem for Ubuntu.  If you plan to use it with Windows, NTFS is better - it is more robust than FAT32 and Ubuntu handles NTFS disks just fine these days.  One big drawback of FAT32 is that you can't store large files on it (larger than about 4.1GB).  Of course, you probably have many files already on it and don't want to move them/reformat the drive.  But if you were starting over - I recommend NTFS.  Or if you were NEVER using Windows again, I'd recommend ext4 format.

---

### Post by Crazy K on 2012-10-09
Last night I re-started and it seemed to give me permission on the drive. When I get home today I'll see how things are going. 

I understand Fat32 isn't really ideal for Ubuntu, but I have all of my documents on it, well over 100GB so I'm not going to be formatting it to NTFS anytime soon. 

I like having everything set up at startup as my music is stored on my EX HDD. It takes forever to load my music to rythmbox because the HDD isn't automatically mounted (though I think it might be now). 

It worked wonderfully fine in Ubuntu 8.04. 

And I'm never installing Windows on this machine again. I only have Xubuntu on it and that's it. 

I might actually go with Bodhi since Xubuntu is freezing up, slowing down and just not working right.

---

### Post by Crazy K on 2012-10-09
Yeah, I for some reason had to import all my music to rhythmebox again, but it seemed to stop importing after a while saying that nearly all files were missing. I go to my EX HDD and noticed a lock on the folder. I can access it fine, and it says I can add and delete files. 


Anyways I need some legit help on this, otherwise I'm going to just install Bodhi and start from scratch again. I'm lazy, sorry.

---

### Post by Crazy K on 2012-10-09
Yeah I'm going to do a fresh install, but this time with Bodhi.

---

