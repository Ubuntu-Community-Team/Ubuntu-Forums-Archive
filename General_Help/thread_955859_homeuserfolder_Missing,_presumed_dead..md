---
title: "/home/userfolder Missing, presumed dead."
date: 2008-10-22
forum: General Help
---

### Post by greymullet on 2008-10-22
Yesterday my laptop found an error with sda2 (my /home partition).   It told me to do a manual fsck, which, after logging into an xterm session, I did.  I couldn't log into a normal session because my settings could not be found.

fsck found an error in block 279995 (for what it's worth - unless any of you live inside my hard drive I doubt that will be of use to you).  I allowed it to fix the problem, but the filesystem, apparently, still had errors (3.9% non-contiguous).

Trying to login still did not work.

Going back into the xterm session, I navigated to home, and asked  for a directory list (ls -l).

0 files.

ls -la (list all, even hidden) gave me two folders: . & ..

Neither /home/root, nor /home/greymullet are anywhere to be seen. 

My question, therefore, is this:  As my /home folder is on a seperate partition, is it possible to create a new /home, with default user contents & settings for both myself and root?  I would rather not have to do a full install, as that would involve redownloading all of the many weird and wonderful packages that I use.

I feel that this should be a relatively simple operation, but I've only been a Linux user for a few months.  My flatmate, a Ubuntu veteran of a few years now, is also stumped.


Disclaimers:
This may seem like a rambling introduction for a simple question, but it helps to make clear what I am trying to do, and why. I know how to re-install Ubuntu and keep my /home intact, but that is very much the opposite of what I wish to do.

Apologies if you think that this would be better placed under hardware; while it could, perhaps, be considered a drive problem, I'm (fairly) sure that it's not physical, and is thus a software issue.  This isn't posted under xubuntu specifically even though that's my flavour of choice, as it's not really an xfce problem.

---

### Post by caleb12 on 2008-10-22
Wow, that kinda sucks... I assume you have a good back up of your home directory, or the important stuff anyways. 

At any rate, you're heading in the right direction. Although, fsck and format, etc. until you are satisfied that your partition is ok. Then make sure /home is in your fstab, and the entry points to that partition. Mount the drive manually from the command line to /home. Root doesn't live in /home, root lives on / so your root home directory should be fine. 

Now, here's the tricky part so maybe someone else can fill in the gaps. There are certain files (.bashrc and .profile for instance) that are created automatically when a user is created - they are usually located in /etc/skel/. So,  you could create a new user and use that home directory... 

However, if you have a full backup of your /home then just copy that in place - recreating the same folder structure you had previously. That's how I backup my /home - tar ball to an external - unzip after I re-install. For the most part everything is back to where you left it, some minor stuff is off but it's livable - and only takes a second to fix.  

hope that helps...

---

### Post by greymullet on 2008-10-22
I have a backup of all of the important content, but not of the user directory in its entirety.

If it's just the one user folder that's gone, I'll try creating a new user and see if that works.

Thanks a lot, caleb12.

---

### Post by Old Marcus on 2008-10-22
I know this is completely off topic, but I loved your title. :D

---

### Post by The Cog on 2008-10-22
Is there a lost+found folder lying around? Recovered files go in there (I think) when fsck recovers things.

---

### Post by caleb12 on 2008-10-22
> **greymullet said:**
> I have a backup of all of the important content, but not of the user directory in its entirety.

If it's just the one user folder that's gone, I'll try creating a new user and see if that works.

Thanks a lot, caleb12.

That's the basic idea... that will create the user home skeleton and everything else kinda falls into place after that. 

Personally, I tar up the whole home dir when I back up since that will keep all my config files as well. So, themes, icons, app colors, fonts, etc. all of it... 

The Cog - I hadn't even thought about the lost+found folder that may be an option as well...

---

### Post by greymullet on 2008-10-25
Thank you again for all of your help.  I started up my laptop today in order to get on with creating a new user etc. and found that, despite what xterm had told me after I tried fixing the system, it had managed to recover everything (or so it seems).  I'll run fsck again to check that there are no remaining errors but, otherwise, everything seems alright for now.

I do feel like an idiot for not rebooting before checking, but "0 files" seemed pretty self-explanatory.  I hope that this thread will be of help to someone.

---

