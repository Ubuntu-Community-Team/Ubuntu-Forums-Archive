---
title: "Apport error in update"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by Jay Car on 2009-03-30
I upgraded from Ibex to Jaunty Beta on Friday night.  My computer seems to be working just fine. But right after the Jaunty update finished a notification popped up that reported some sort of error and asked if I'd allow it to send a report, which I did.  But the report wouldn't go through. I didn't think much about it at the time, it didn't seem to be anything serious.

However, today when I checked for updates there was one particular option at the top of the update list titled "Apport (automatically generate crash reports for debugging)".  A few seconds after clicking the "Install updates" button a small window popped up saying an error had occured.  Here is the error text:

"E: /var/cache/apt/archives/apport_0.146_all.deb: 
subprocess new pre-removal script returned error exit status 2"

No updates were installed that time. I tried taking the checkmark out of the "Apport" item, but it wouldn't allow me to do so.  So I just clicked the "Install updates" button again and that time it did install all of the other updates, but returned the same Apport error at the end.  

Since one of the reasons to use Beta software is to help find and report problems, I'd really like to be able to use the automatic crash report option. Any ideas of how I can fix this? 

Also, except for the small Apport problem, Jaunty is working absolutely beautifully on my computer...so far, so good!

---

### Post by Jay Car on 2009-03-30
just a quiet little bump...

---

### Post by Jay Car on 2009-03-31
Hmmm.  A question without any replies generally means I've phrased the question poorly. 

The only annoying part of this problem is that no matter whether I am installing software through Synaptic Package Manager, or checking for updates, the process always ends with an error message about "Apport". The worry is that I don't know if things are being properly installed as a result of that error.

I'm not upset (just a little frustrated because I wish I knew more), and I don't expect absolute answers...just some guidence.

I've read the Apport wiki, but I still don't fully understand what it does or why it isn't working.  I can't uninstall it (to try reinstalling), and I'm not sure how to go about reporting a problem with the very tool that (I think) should be the means of reporting problems...

I won't be discouraged if no one answers this, but I'd be very grateful if they do (if only to help me understand a bit better).  I'm also happy to provide more info if I know what extra info is needed.

Jay Car

---

### Post by Jay Car on 2009-04-01
Okay, another possible reason for no answers to my post is that the answer may be an obviously easy one and I'm just too dense to see it.  If that's the case, then I understand. There are folks with more pressing problems that need help sooner.

I'm not a total noob, but I am still learning...haven't really had to face error problems on my Ubuntu machine before now.

So maybe I can turn this post into a good learning experience and see if I can think it through for myself. 

Here is the longer error message that I get whenever I receive updates now (This error only began after an upgrade to Jaunty Beta.)

NOTE: I was unable to copy the error message, so I typed it out. I tried to be very careful, but typos still may have occured.

> Not all changes and updates succeeded. For further details of the failure, please expand the 'Details' panel below

(content of 'Details' panel)

> subprocess new pre-removal script returned error exit status 2
* starting automatic crash report generation: apport
/etc/init.d/apport: 24: runlevel: not found
exit: 24: illegal number: starting
invoke-rc.d: initscript apport, action "start" failed.
dpkg: error while cleaning up:
subprocess post-installation script returned error exit status 2
errors were encountered while processing:
/var/cache/apt/archives/apport_0.147_all.deb
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing apport (--configure):
Package is in a very bad inconsistant state - you should reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of apport-gtk:
apport-gtk depends on apport (>= 0,41); however:
Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
apport
apport-gtk 

Here's what I've tried on my own, so far:

Pasted the error message into Google, resulting in no returns, so I continued searching using smaller fragments of the error. I did get some returns, but most were dated 2007 or earlier, and none were related to apport errors. 

Tried to take the checkmark out of the apport box in the updates list, so it wouldn't keep trying to install it.  The checkmark could not be removed.

Tried to uninstall apport using Synaptic Package Manager, the checkmark could not be removed from the apport items.

Tried to uninstall apport through add/remove, which was also unsuccessful.

Posted here. :)  Began feeling a bit silly and embarrassed for having done so...Decided to turn it into something positive. After all, showing patience with a problem is a good trait to acquire. :)

So, after reading through the error message more carefully, and after determining that uninstalling apport is not an option, maybe I need to clear the old "/var/cache/apt/archives/apport_0.147_all.deb" file (folder?) out?  

My worry is that, if it isn't possible to uninstall apport in add/remove, or block it from the updates list, then maybe it's because it's important. Just deleting it might cause more problems...which I don't want, but I know that's sometimes the price of learning, and I do have my old system backed up and ready to reinstall.  

Soooo, I'll see what happens and report back. This might not be helpful to others, but maybe it will. I guess it's worth a try, right?

---

### Post by Jay Car on 2009-04-01
By the way, is it just me, or is Ubuntu Forums very very pink today? 
Painfully Pink. (I forgot, it's April Fools day, could be the cause of blinding pinkness...very cute). ;)

---

### Post by Jay Car on 2009-04-01
Well, in spite of my Jaunty Beta system seeming to be running okay (so far the only problem in everyday usage has been a few Opera freeze-ups, but Opera's always been a little quirky and I only use it for one website, so I didn't consider Opera problems to be Jaunty-caused), however, I did confirm that the strange apport error does stop any further updates from happening.  I also have not been able to install or uninstall any software since the Jaunty upgrade.  All attempts to install the 104 updates that are available to me always end with the error message (shown in my comment above), and no further updates get installed.  

I'm thinking it's just an odd problem on my machine. If I were to make a guess at the culprit, I'd guess Wine...a file in the apport folder made a reference to wine. I'm probably wrong, just guessing.  Tried to uninstall Wine though, just in case it was part of the problem, but it failed to uninstall. (Used "sudo apt-get remove wine" but got the same error and Wine's still here).

And, out of habit (because old Windows habits die hard) I did a restart to see if it would magically fix things. It didn't.

So, I've backed up my Firefox profile and a few folders and am downloading an ISO of Jaunty now.  

This was the first time I'd ever enabled an upgrade to a Beta using "update-manager -d", and it was fun to do, but not being able to get further updates is worrisome, so I'll try a fresh install now. If all else fails I'll just put the old Ibex system back on for a couple more weeks. 

Things I've learned today were:
1. That sometimes I can work things out by myself, and sometimes not.
2. experimenting is fun (as long as it's done on a spare computer).
3. I need to learn how to do bug reports instead of relying on the automated kind.
4. Posting an entire thread of comments to myself on Ubuntu Forums is embarrassing (and lonely), so I should stop now.

---

### Post by lijenstina on 2009-05-03
I don¨t know how much this is related but i had problems with update apport using update manager and synaptic because i could not remove the old one. Every attempt to update apport had failed. Even the apt-get remove command didn't work, 

However, after manually deleting  the folders where apport was installed (using root privileged gnome commander) i could update apport from synaptic without a problem. (right click in synaptic on the file >> /propreties/ installed files will show where the package is installed in the file system. Deleting the */usr/share/doc/apport, /usr/share/apport, /usr/bin/apport-cli /usr/bin/apport-collect /usr/bin/apport-unpack /etc/apport* and installing it from synaptic  had solved the problem for me, at least. :)

---

