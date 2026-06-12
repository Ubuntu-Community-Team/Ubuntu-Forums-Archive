---
title: "mini dell with ubuntu crashed during updates intallation"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by itodorut on 2009-10-21
Hi, I've just bought this dell mini 9, and I clicked to install the automatic updates that appeared on my desktop. I guess that was a mistake since I have so little space on the disk. The installation crashed, the disk is full, and no application works, no internet connection wtc. The message given is 
"the configuration defaults for gnome have not been installed correctly:
Is there a way to restore the system? 
I really know very little about Ubuntu and I would be grateful for any help. Thanks!

---

### Post by earthpigg on 2009-10-21
hi!

if it's still under warranty, you can probably send it in to dell if you wish. my vote is "screw that! doing things ourselves is best!"

i have a mini 9. i love it. but i will state that Dell's modifications to ubuntu where crap. regular ubuntu is far better.

-find a 1gb or larger USB thumb drive.
-find a USB drive with enough space to back up all your important data. 
-find a computer with a windows or linux installed and functional, and a USB port.

now, let's get started....

-***first***, let's go ahead and get a USB thumb drive with ubuntu on it:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

that will work on any windows or linux computer. if you only have a mac around, let us know and we can explain that process too.

you can pick normal ubuntu or ubuntu netbook remix, your choice.

-***then***, lets go ahead and boot from that USB drive:
put it in, and turn the computer on.

ya know the "press delete to enter setup?" press it, and tell it to boot from USB as first priority.

exit saving changes.

-***"try ubuntu without making changes"***

let it boot.

now, you should be at a basic ubuntu desktop... grab another USB drive and put it in.

using places -> computer, find all your important documents and copy them over to the 2nd usb drive.

if you wish, you can back up your whole /home folder - that will also backup all your application settings such as firefox bookmarks, etc.

now that our important stuff is backed up, take that 2nd thumb drive out.

double click the 'install' icon on the desktop. to save us a step, go ahead and pick the same username as you had before. password can be different.

-***let's restore settings and stuff.***

remove the install thumb drive and boot into your shiny new ubuntu desktop.

put the USB drive in that you backed your stuff up onto in.

if you want to do a full restore of /home with all your documents and settings and whatnot,

applications -> accessories -> terminal

```
sudo nautilus
```

drag and drop the backup /home from your USB backup, replacing the one currently on your computer. (if you picked a different user name, there will be an extra step. let us know and we can help with that.)

restart computer.

all the programs themselves that you had before won't be installed, but as soon as you install them they will use the personal settings that we restored from your old /home.

let us know if you have any questions!


it may seem like a bit of a pain, but once you have done all of this you will have learned a whole lot and be much more of a "do it yourself" capable computer user. self reliance is a good thing, right?

---

### Post by tenndave on 2009-10-23
new mini user (8 gig HD) and had same issue with upgrades for hardy heron.  hours to recover as three new external drives to recover.  going to thumb drive as Rescue. Gonna follow instructions of post.
So this means ignore updates?  how does one update and turn off update icon?
reading other posts, so take questions kindly.
EAT THE APPLE.........






































q

---

### Post by snowpine on 2009-10-23
> **tenndave said:**
> new mini user (8 gig HD) and had same issue with upgrades for hardy heron.  hours to recover as three new external drives to recover.  going to thumb drive as Rescue. Gonna follow instructions of post.
So this means ignore updates?  how does one update and turn off update icon?

You should always apply updates, for the security and stability of your system. If you follow Earthpigg's tutorial, you will have "regular" Ubuntu and not the flawed Dell version with the update issue.

Not sure why you'd need to spend hours recovering your 3 external drives though. You can just unplug them, then plug them back in once Ubuntu is reinstalled, and all the data will still be there. :) (maybe I misread your post?)

---

### Post by tenndave on 2009-10-25
two stores and purchased three drives and two defective, out of box.  driving back & forth to city took hours, should have made clear.  also thanks for helping, newbie.

---

