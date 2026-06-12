---
title: "[SOLVED] Firefox - Could not initialize applicaiton security component"
date: 2008-08-29
forum: General Help
---

### Post by speedkreature on 2008-08-29
First a note:
Firefox 3 gives me this error, the browser appears after clicking "Ok" on the Alert dialog, then *POOF!* it's gone.
Firefox 2 gives me the same error but the browser opens as normal, but SSL is disabled.  Hooray for Ubuntu forums not requiring https.

The error reads:
==========

Could not initialize the application's security component.  The most likely cause is problems with files in your application's profile directory.  Please check that this directory has no read/write restrictions and our hard disk is not full or close to full.  It is recommended that you exit the application and fix the problem.  If you continue to use this session, you might see incorrect application behaviour when accessing security features.

==========

So I took the alerts advise and checked permissions..
```

speedkreature@M31-M2:~$ cd /home
speedkreature@M31-M2:/home$ ls -l
total 4
drwxrwxr-x 67 speedkreature speedkreature 4096 2008-08-29 16:12 speedkreature
speedkreature@M31-M2:/home$ cd ~
speedkreature@M31-M2:~$ ls -l
total 36
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-08-29 15:56 Desktop
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-29 16:12 Documents
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-27 14:17 Downloads
lrwxrwxrwx  1 speedkreature speedkreature   26 2008-07-24 11:53 Examples -> /usr/share/example-content
drwxr-xr-x 12 speedkreature speedkreature 4096 2008-08-21 21:26 Music
drwxr-xr-x  5 speedkreature speedkreature 4096 2008-08-26 14:41 Pictures
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-07-24 12:01 Public
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-29 16:11 TEMP
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-08-03 02:44 Templates
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-07-24 12:01 Videos
speedkreature@M31-M2:~$ 

```...didn't seem unusual but I'm still at the beginner stage so, yeah.

I also took a look at hard drive space.  Turns out I was, in fact, out of space.  A run-away backup job was backing up to /media/disk though no external disk was attached...the directory for some reason remained.  Space has since been cleared and the problem persists.

---

### Post by speedkreature on 2008-09-01
I have foxmarks installed so my bookmarks were already saved.  I took note of the other extensions installed then completely removed (purged) firefox and then in my home directory (~) remove the .mozilla folder and all of it's contents by typing...

* rm -rf .mozilla*

...in a terminal window.

Installed Firefox 3, and ran it.  At this point, it recreated the .mozilla directory, and I added foxmarks and several other extensions that I'd had, restarted and now here I am.

Regardless of what happened, Firefox is fixed and faster than ever!  :guitar:

Ciao!

---

### Post by tiberyus on 2008-12-21
BUMP!

Sorry to say this, but this doesn't sound like a solution..
I'm having the same problem and I didn't have free disk space. It's freed up now, but I can't uninstall firefox because there are some other applications dependant upon it; and, because I don't really know how to - Add/Remove programs just tells me to use Synaptec, which either keeps the problem when removed and re-added, or requires to remove other important apps when asked for "complete removal" can anyone help me out with a fix and not a reinstall based solution?

thanks in advance!

~ Tibby, first post
Moved from vista, never looked back.

---

### Post by speedkreature on 2008-12-23
What packages does it say it had to remove?  There are often several packages that are meta packages and removing won't create any problems (i.e. ubuntu-desktop).

I remember how frustrated I was with this so I'll do everything I can to help.  Hopefully some others will chime in as well.

---

### Post by tiberyus on 2008-12-27
evolution-rss-reader
Something I've been working really hard to get installed and working. :(

---

### Post by tiberyus on 2008-12-29
Okay, I did what you did, and it fixed. Now just to get my bookmarks and addons back installed and configured..

---

### Post by speedkreature on 2008-12-29
I'll admit that it's not pretty, elegant or graceful--in fact it's a rather brutish approach, but at least it works.  Glad to know you got things sorted.

---

### Post by Cosmosis on 2009-02-28
I have been using Ubuntu on a netbook for a while without problems, and decided today to take the plunge and dual-boot it on my XP desktop. Install went fine, but immediately upon booting and installing all 200+ recommended updates, I started getting this security error when trying to open Firefox. Firefox has never opened at all, either giving me the error, or after uninstalling it and reinstalling it, not opening at all. I can see a box in the taskbar at the bottom that shows Firefox trying to open, but then it just vanishes and nothing happens. I looked and no longer have a .mozilla folder anymore (even checking with "show hidden files" activated). So....anyone else gotten to this point? I can't get on the web, and I tried installing a different browser, which has it's own problems and won't load. Sigh. Never had this much trouble with Ubuntu before! Anyway, any suggestions or help would be appreciated. Thanks.

(I posted this to another thread dealing with the same issue - hope no one minds!)

---

### Post by SPACEQWERTY on 2009-06-16
> **speedkreature said:**
> First a note:
Firefox 3 gives me this error, the browser appears after clicking "Ok" on the Alert dialog, then *POOF!* it's gone.
Firefox 2 gives me the same error but the browser opens as normal, but SSL is disabled. Hooray for Ubuntu forums not requiring https.
 
The error reads:
==========
 
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and our hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
 
==========
 
So I took the alerts advise and checked permissions..
```

speedkreature@M31-M2:~$ cd /home
speedkreature@M31-M2:/home$ ls -l
total 4
drwxrwxr-x 67 speedkreature speedkreature 4096 2008-08-29 16:12 speedkreature
speedkreature@M31-M2:/home$ cd ~
speedkreature@M31-M2:~$ ls -l
total 36
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-08-29 15:56 Desktop
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-29 16:12 Documents
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-27 14:17 Downloads
lrwxrwxrwx  1 speedkreature speedkreature   26 2008-07-24 11:53 Examples -> /usr/share/example-content
drwxr-xr-x 12 speedkreature speedkreature 4096 2008-08-21 21:26 Music
drwxr-xr-x  5 speedkreature speedkreature 4096 2008-08-26 14:41 Pictures
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-07-24 12:01 Public
drwxr-xr-x  4 speedkreature speedkreature 4096 2008-08-29 16:11 TEMP
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-08-03 02:44 Templates
drwxr-xr-x  2 speedkreature speedkreature 4096 2008-07-24 12:01 Videos
speedkreature@M31-M2:~$ 

```...didn't seem unusual but I'm still at the beginner stage so, yeah.
 
I also took a look at hard drive space. Turns out I was, in fact, out of space. A run-away backup job was backing up to /media/disk though no external disk was attached...the directory for some reason remained. Space has since been cleared and the problem persists.
 
 
 
 
 
 
 
IT'S SO SIMPLE PEOPLE, ALL YOU HAVE TO DO IS GO TO YOUR PROFILE DIRECTORY:
C:\Documents and Settings\yourprofile\Application Data\Mozilla\Firefox\Profiles\someweirdlettersand#'s.default AND RIGHT CLICK(ANYWHERE IN THE BACKROUND), CLICK PROPERTIES, AND UNCHECK THE READ ONLY BOX, CLICK APLLY, THEN CLICK "APPLY TO CHANGES TO THIS FOLDER, SUBFOLDERS, AND FILES", CLICK OK, AND YOUR DONE, EVERYTHING SHOULD BE BACK TO NORMAL. POSTED BY SPACE.

---

### Post by jhansonxi on 2011-01-05
Correct solution [**is here**]("http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component").

---

### Post by simpy63 on 2011-06-01
simply enter into the terminal
type the command:
[FONT="Lucida Console"][COLOR="Red"]firefox -profilemanager [/COLOR][/FONT] [Hit enter]

Then mozilla will prompt to create/delete/rename a profile
Delete the corrupted profile and Create a new one.. and Walla! the Firefox runs with no error alerts!! :D

---

### Post by rickatnight11 on 2011-09-05
The link 2 posts before helped me out.  It wasn't a disk space or permissions issue, but rather a corrupted **cert8.db** file:

```
rm -f ~/.mozilla/firefox/*[profile]*.default/cert8.db
```

---

### Post by Gnu2ubuntoo on 2012-01-19
The following steps fixed the problem for me:

1. Make sure firefox is closed/not running
2. username@host:~$ mv .mozilla mozilla_old      #cd to home directory
3. Start firefox


OS: Ubuntu 11.10
Firefox 9.0.1

---

### Post by yeahdef on 2012-02-03
> **Gnu2ubuntoo said:**
> The following steps fixed the problem for me:

1. Make sure firefox is closed/not running
2. username@host:~$ mv .mozilla mozilla_old      #cd to home directory
3. Start firefox


OS: Ubuntu 11.10
Firefox 9.0.1

Thank you! this worked for me and also solved an issue I was having with my VPN at work! thank you!

---

