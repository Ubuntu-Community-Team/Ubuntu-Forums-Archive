---
title: "mount sshfs with script in WICD"
date: 2008-07-28
forum: General Help
---

### Post by jimv on 2008-07-28
I'm trying to use WICD to run a script that mounts a folder with sshfs.  I've got ssh using key authentication, and I am able to mount the folder just fine with a script I made.  However, when I try to run the script from inside WICD, the folder does not get mounted.

I think this has something to do it not using my key, but I don't know how to tell or how to fix it.  Any ideas?

---

### Post by Dr Small on 2008-07-28
Can you run the script and see if you get any output, and, is the script being executed by the same user who has the ssh key?

Dr Small

---

### Post by imdano on 2008-07-28
Running scripts through wicd in version 1.4.2 is broken.  You can try [1.5.0](http://www.wicd.net/latest) and see if that works any better.

---

### Post by jimv on 2008-07-28
No love in 1.5 either.  Its odd.  When the script runs, it does a few things.  First it sets the Gnome proxy settings to manual.  Then it renames a ssh config file that I need to get through my proxy at work.  Both of those steps work.  But the next step, where it mounts the sshfs folder, fails.  The command looks like this:

sshfs somedomain.com:/some/folder /home/jim/HomeStorage -p someport

When WICD gets to that part, it throws up a window asking for a password for [email]jim@somedomain.com[/email].  So it's attempting to login as me...but it's not using my key.  When I type the password in, the mount fails.

---

### Post by jimv on 2008-07-28
Well, I found a hell of a work around.

WICD tries to run as you, but it doesn't work real well...for some reason it won't see my SSH key.  So what I did was go into /opt/wicd/run-script.py and change the uid from 1000 to 0 (so WICD runs all scripts as root).  THEN I modified all my commands in the my WICD scripts to use the 'su jim -c' in order to run as me, which worked fine.

To get sshfs working, I made a script to dump my SSH_AUTH_SOCKET environment variable to a file.  Then I made another script for WICD to run that sets an environmental variable to the path in that file, and then mounts my sshfs folder.  It worked, hurray!

:guitar:

---

### Post by imdano on 2008-07-28
In 1.5.0, wicd executes all scripts as root.  When you install 1.5.0, you should no longer be running the copy of wicd that lives in /opt/wicd.  Remove that from your Sessions entry (if it's there), and instead add "wicd-client", which is the new command to open the tray icon.  Once you've done that, kill the open tray and restart the daemon by running
```
sudo /etc/init.d/wicd stop
sudo /etc/init.d/wicd start
```It may not kill the daemon when you run the stop command the first time, so do a ps -ef | grep wicd and manually kill any daemon.py processes kicking around.

Then open up the 1.5.0 tray icon.  You'll have to re-enter your settings, but scripts should work as expected.

see [here](http://www.wicd.net/latest/changes) for more info.

---

### Post by jimv on 2008-07-29
Meh, I'm happy with 1.42 now.  After spending all day getting it to work, I think I'll just leave it be for now ;)

---

