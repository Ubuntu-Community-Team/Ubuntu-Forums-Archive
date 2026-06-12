---
title: "Undo an update?"
date: 2005-11-28
forum: General Help
---

### Post by shane2peru on 2005-11-28
Ok, no one seems to be able to solve my other posts, so How can I undo my update.  I'm on the verge of re-installing to get this fixed, but that is a hassle.  Can I undo an update that has messed up Gnome?

Shane

---

### Post by invalid on 2005-11-28
Without knowing exactly what was updated, it is hard to go back and fix the problem. You can not "undo an update" so to speak. If you tell us what is wrong with gnome, maybe we can suggest a plan of action.

Cb

---

### Post by ecobuntu on 2005-11-28
theoretically...as long as you don't run sudo apt-get clean often you should have packages on your local cache that could be used to force an installation...what is the  bad package?

---

### Post by shane2peru on 2005-11-28
Well, I'm not sure exaclty.  There were just a bunch of updates so I updated them all, and now Gnome don't boot right.  I think it may have updated Gnome.  That would be my first guess.  How do I undo that?  Thanks for the help!

Shane

---

### Post by Gustav on 2005-11-28
Please describe more detailed how Gnome doesn't boot right. 
Do you just end up in a console? If so it's probably a kernel update without the corresponding graphics driver update that is your problem.

---

### Post by shane2peru on 2005-11-28
No, it gives me an error message, and none the icons are right.  It is something about the background settings.  I just installed KDE and it seems to work right, so it is a problem with Gnome.  How can I uninstall Gnome and re-install it to work correctly?  Thanks again for the help!

Shane

---

### Post by invalid on 2005-11-28
You have to be more specific.

What is the error message _exactly_?

Cb

---

### Post by shane2peru on 2005-11-29
Here is the error I get:

[B]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

The last error message was:

Child process did not give an error message, unknown failure occurred

GNOME will still try to restart the Settings Daemon next time you log in.
[/B]

I don't konw what all this means.  On top of this I have installed KDE and deleted Gnome.  I re-installed Gnome and got the same error.  I'm in the process of deleteing Gnome and the Gconf folder in the etc because that seems to hold the original file info.  It really seems like gconf is the Daemon controller for Gnome.  I really don't know and am guessing and trying to fix this.  If you have any ideas I'm open to suggestions!  Thanks!:p 

Shane

---

### Post by Gustav on 2005-11-29
The problem might be that you installed KDE I've heard (havn't tried myself) that that might cause problems with gnome configuration.

One solution might be to completly remove gnome and install it again. Normal remove will not remove configuration files so you must use complete remove.

Although I'm not at all sure of this so do it at own risk.

---

### Post by Gustav on 2005-11-29
Look at this [http://www.ubuntuforums.org/showthread.php?t=96621](http://www.ubuntuforums.org/showthread.php?t=96621) before you do as I said in my last post :-P

---

### Post by shane2peru on 2005-11-29
Gustavo,

I had the problem before I installed KDE.  I installed KDE to give me something to work with.  Thanks for the help.  I'm trying to get rid of the config files now.  It is very time consuming since I'm not that proficient with the cl.  I can't find a way to run a file manager in root with KDE, so I can't just go and delete the directory.  I tried the rmdir but it told me that the directory is not empty, so I have to go into each directory and empty it, then delete it.  If you know the command to delete a directory that is not empty that would be wonderful!  Thanks again.

Shane

---

### Post by shane2peru on 2005-11-29
Ok, I tried it at my own risk since I was thinking I had to re-install to fix it anyway ..... ..... and it was a flop!  Didn't work.  Now Gnome is completely destroyed.  Won't even start up now, so I will be doing a re-install.  Glad I at least have KDE to back up my data!  Thanks any way for the help!

Shane

---

### Post by siddhant on 2008-01-31
> **ecobuntu said:**
> theoretically...as long as you don't run sudo apt-get clean often you should have packages on your local cache that could be used to force an installation...what is the  bad package?

this post is quite old. but maybe relevant. i accidentally did a sudo apt-get clean. can i get all those deleted packages back??? :confused:

---

