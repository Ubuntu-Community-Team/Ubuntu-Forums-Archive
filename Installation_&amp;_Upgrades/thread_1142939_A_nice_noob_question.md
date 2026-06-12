---
title: "A nice noob question"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Ubudireh on 2009-04-29
Hellos!  Apologies if starting a fresh thread for this is wrong, but couldn't find a better place to put it.  I have a little upgrading problem with Firefox that neither I nor my friend can figure out how to fix.  Here's the little story (I'll try to be succinct. :) )

When going to upgrade Firefox this morning (while doing a couple of other things at the time), the upgrade manager was tooling along just fine.  Had downloaded the packages and was (I think) starting to install.  I'm not totally sure as I had it minimised at the time.

Anyway, computer (which hates me) decides to do a weird locking up thing where the mouse-cursor still moves but doesn't actually -do- anything.  Reboot and try to restart the upgrade.  No dice.  It tells me there is a problem and i'll have to run "dpkg --configure -a" manually to fix it.  Not a problem, right?

Go to terminal and try to run manually like it asks and it returns:
user@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0043' near line 1:
 newline in field name `#padding'

My friend gives me the idea to remove firefox to reinstall.  Seems like a good idea; but no:
user@ubuntu:~$ sudo apt-get remove firefox
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Now i can't even get FF open under Ubuntu.  Thank the Gods for dual-boots! :D

Now we are both confused, as she says she's never had an install conk out like this before.  Please help?

---

### Post by Mze on 2009-04-29
check this [thread]("http://ubuntuforums.org/showthread.php?t=1142171&highlight=firefox") out...

---

### Post by Ubudireh on 2009-04-29
Whoo-hoo!  Thank you so much!  As soon as i finish reading that thread, I'll hop back over and give it a try. :D

---

### Post by Cordate on 2009-04-29
Hello, Ubuntu-folks. I'm the semi-knowledgeable friend and am trying to help newbie-Ubudireh have a happy new platform.

Her browser problem persists, dpkg not allowing any installs or removes until its current problem is resolved. I am thinking maybe if we renamed the 0043 file, that might force DPKG to grab it again and maybe it woul dhave better luck then. 

I have little experience with using dpkg, it usually does things in the background aside from the rare occasion when I use it from the command line- maybe someone here could offer advice on clearing its current hangup?

---

### Post by Ubudireh on 2009-04-29
Between the two of us, we managed to hash it out and got the thing to work; basically having to create a new directory, move the bad stuff into it, then remake the original directory.  After that, FF updated just fine and is now working smoothly! :D

---

### Post by Cordate on 2009-04-29
I was able to track down some related threads on this

[http://ubuntuforums.org/showthread.php?t=941125](http://ubuntuforums.org/showthread.php?t=941125)

[http://ubuntuforums.org/showthread.php?t=1069232](http://ubuntuforums.org/showthread.php?t=1069232)

[http://ubuntuforums.org/showthread.php?t=1069198](http://ubuntuforums.org/showthread.php?t=1069198)

And first we tried renaming 0043 but then it was complaining about 0044, so we moved the entire updates directory to a new folder in case we needed it later.

```
sudo mkdir /var/lib/dpkg/updates-orig

sudo mv /var/lib/dpkg/updates /var/lib/dpkg/updates-orig
```


And then it complained about the lack of the folder, so we added in a new empty one

```
sudo mkdir /var/lib/dpkg/update
```

And then we were able to get things to clear up and her browser works again as well. Hurrah for finding answers through searches! ^_^

---

