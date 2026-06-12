---
title: "Kubuntu Startup Programs"
date: 2008-09-21
forum: General Help
---

### Post by infinitelink on 2008-09-21
Well, I keep seeing threads on this (too old to edit though) and never solutions that are very helpful.

How does one add programs to start-up when a user logs-in to KDE? For instance, if someone logs in, Firestarter starts up (though I'd like that to happen just by turning the computer on, even without logging in), and how does one set them to start with permissions (i.e. Firestarter requires the admin password to be turned on)? 

Someone asked about this for kwifi and the replies were "just install KDE". ? That's not what that person asked for. Another threat I saw said to drop to shell and go to ~/.kde/share/Autostart. However I tried opening that in kate (the KDE text editor) and it says it's not a file that exists (perhaps I need to fill-in details for what "~" represents?). Where is that file located if it does? (I presume something like it does because else much of the functions of KDE probably wouldn't just start-up upon initialization of the desktop). 

Also, another reply to this was that one should install some app from KDEapps, however, it's almost three years outdated and I wouldn't dare trust it because of that.

And who do I punch in the gut for foregoing such basic functionality as accessing a GUI for this? ...

Just kidding: I can't complain since this is all free. Oh yeah, and 'Way to GO!' to Canonical for offering legal codecs for sale! (boo to you software religionists!). : )

---

### Post by Atsuko on 2008-09-21
If you go to System > Preferences you can add programs to start up with the Sessions program.

---

### Post by SuperSonic4 on 2008-09-21
> **infinitelink said:**
> Another thread I saw said to drop to shell and go to ~/.kde/share/Autostart. However I tried opening that in kate (the KDE text editor) and it says it's not a file that exists (perhaps I need to fill-in details for what "~" represents?). Where is that file located if it does? (I presume something like it does because else much of the functions of KDE probably wouldn't just start-up upon initialization of the desktop). 

~ means /home/<username> so ~/Desktop is /home/<username>/Desktop

(where <username> is your login name)

I found it [Autostart] (in Kubuntu Hardy x86) in /home/<user>/.kde/Autostart

As far as I know you copy and paste programs in there? I'm not sure where to go from there

---

### Post by infinitelink on 2008-09-21
Thanks so far, you guys rock. : )  Anyway "system-->preferences" is for Ubuntu, not Kubuntu, but thanks a bunch for replying. As far as the ~ location I appreciate that; besides perhaps the permissions enablement I think I may be able to figure-out how to proceed from there if the file is there and if it already has some other data in it alike to what I would like to add.

---

### Post by infinitelink on 2008-09-21
The bad news...it's not a file, but a folder. : (  So I'm guessing that one must add run-files/shortcuts to the folder. Anyone know how to do this, and also how to give them permissions?

---

### Post by tarahmarie on 2008-09-21
I'm fighting with this right now.  I'm trying to add tilda, azureus, and a few others to my ~/.kde4/Autostart folder, and I'm coming across these two big problems:

(1) I've put tilda in the Autostart folder like this:

#!/bin/bash
/usr/bin/tilda

as a text file.  Unfortunately, tilda seems to open on reboot with three separate instances of it running.  What am I doing wrong?

(2) Azureus is in the Autostart folder like this:

#!/bin/bash
/usr/bin/azureus

and when it starts, it isn't in the Emerald theme; it's got the basic blah beige window theme.  

Any ideas?

PS: thanks to the OP for posting such a useful thread.  I have been having problems with these things for a while.

---

### Post by SuperSonic4 on 2008-09-21
If you copy and paste a XXX.desktop file into that folder it will launch at startup, I just tried it with *desktop-effects-kde.desktop* and it worked.

[IMG]http://img.photobucket.com/albums/v365/SuperSonic4/Crap/screeni.png[/IMG]

I copied these from the K menu, it just seemed easiest lol although under properties it has *[COLOR="Red"]amarok %U[/COLOR]*

---

### Post by tarahmarie on 2008-09-21
pasting azureus.desktop into my ~/.kde4/Autostart folder worked like a charm; it's loading properly with the right windows decoration theme now.

Tilda is still problematic; it starts just fine after I got rid of the bash script and pasted tilda.desktop into the autostart folder.  I am, however, still seeing two different instances of tilda overlaid.  How is this happening?  When I don't have tilda (either in bash script or by pasting the shortcut) in the autostart folder, NO instances of it start; when I do, TWO instances of it start.  That is insane troll logic.

---

### Post by tarahmarie on 2008-09-21
Also something that might help; it may have something to do with Konsole.  I have different colored fonts in Konsole than in Tilda.  When the two overlaid Tildas autostart after reboot, one has the Konsole-colored font, and the other has the Tilda-colored font.  Does that mean something?

---

### Post by infinitelink on 2008-09-25
Just for anyone who needs it, I don't personally know how to create a "[something].desktop" file in any right-clicking-->new-->[some file] kind of way, so if you need it I figured-out how to make a file by going to the Kmenu, right-clicking an application, and selecting "Add item to Desktop", and then you can just copy this over to your Autostart folder.

: )  You're all probably already on top of this (or have a better way), but since these forums are saved, this ought to benefit someone at some point. Cheers!  : )

---

### Post by wladicus on 2008-09-25
Hello infinitelink,
Perhaps I can help. I am running Kubuntu 8.04 LTS (Hardy Heron) and recently I wrote a 'How to' on turning the touchpad off/on with a single shortcut key. In that 'how to' I added information on how to activate the autostart feature for one of my scripts.
If you would like to have a look at how I did the Autostart part, it is very simple.  You will find it at the following URL.  The actual 'How to' is the last post of the thread the URL points to and the Autostart portion in at the very bottom of the last post.
You will need KDE Control Centre to activate the Autostart feature.  I did not have KDE Control Centre with my Kubuntu install so I had to install it (see Step 6 at the beginning in the Quote). 
The Autostart portion starts in Step # 6 [b].  I used the file name > /usr/local/bin/set-tpon.shfor my Autostart programme but you will be entering the name of the particular programmes that you wish to access. Take your time and do one programme at a time. The Autostart worked very well for me.
Here is the link to the "HOW TO" (Let me know if it worked for you):
>  [http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html](http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html) 
You may not have to check the box in front of "Run in terminal". I had to do this because I wrote a script that runs in terminal mode.  Try it without this box checked.  If it does not work you can go back and check the box.  Good luck!
walt  :)

---

