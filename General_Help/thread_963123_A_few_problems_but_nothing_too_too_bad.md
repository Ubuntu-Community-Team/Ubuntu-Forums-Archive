---
title: "A few problems but nothing too too bad"
date: 2008-10-29
forum: General Help
---

### Post by schmidtbag on 2008-10-29
Just as some background info, I recently updated 8.04 to 8.10.  It completely screwed up my system so I reinstalled, in 8.10, while keeping my home folder.  I copied it elsewhere as the OS reinstalled and then just put it back when the setup finished.

My first problem is with wallpapoz.  I never had any problems with it before but now I can't get it the configuration app or the daemon to start up anymore - both complain about privileges.  When I run the configuration app as SU, it does start but the file browser is working under root yet the configuration file is saved under my home.  Wallpapoz also has no icon anymore.  So why is this whole program considered an administrative task?

My second problem regards my floppy drive.  When I first installed Ubuntu 8.10, the drive acted normally.  When I re-copied my configuration files boot up the computer, the read light turns on and stays on, forever.  Ubuntu doesn't recognize the drive either.

My third problem is probably the most annoying, but apparently many formats have lost the programs they are associated with.  I'm assuming this is related to why not only wallpapoz but other programs are reading root's documents instead of mine when I use a file browser within a program.  I set my right-win button on the keyboard to open up my home folder but that doesn't work anymore either.  What can I do about this?


Sorry for the long questions, I would greatly appreciate any help given.

---

### Post by sdennie on 2008-10-30
Depending on how you did your backup/restore, some of your problems could be attributed to you not having proper permissions to your home directory.  What is the output of:

```

ls -l /home
ls -la ~

```

If you see things owned as something other than your username, it's probably safe to do the following (actually, if you still have the backup, it's surely safe):

```

sudo chown -R your_username:your_username /home/your_username

```

That will make you own your home directory and everything in it (substitute your_username for... your username).

Edit: Changed your_username to your_username:your_username on the chown.  It's admittedly slightly redundant but, it's more in line with the way Ubuntu does things.

---

### Post by schmidtbag on 2008-10-30
I tried the chown code and I think it worked but it said the .gvfs folder wasn't changed.  Theres nothing in it as far as I know, so I'm assuming that makes no difference.

If this is supposed to solve my first question, it still doesn't change the fact that wallpapoz or its daemon can't start up.  Like I said, they're both required to be run by root.  I've never needed to do this before.  Do I have to reinstall it?  If this solves my 3rd problem then I'm sure it works and thanks.  I've been using workarounds so far so I can't tell if this worked or not.

EDIT:
I realized the floppy drive problem is a bug in 8.10, and I guess I just have to wait for a fix.  Luckily I don't use floppy disks much.


So right now, wallpapoz still won't start up and my right-win key on the keyboard still won't start up my home folder.

---

### Post by schmidtbag on 2008-10-30
I created a dummy account to see if my problems differed.  Apparently not.  Luckily I have compiz installed so I'll just use it to configure my r-win key to open up my home folder.

But, I really don't understand why wallpapoz STILL doesn't work.  Is there any way to run it as me and not as root?


I downloaded the .deb version of wallpapoz and it works fine.  I never had to do this before so I'm wondering if everything I compile is going to do this.  O well

---

