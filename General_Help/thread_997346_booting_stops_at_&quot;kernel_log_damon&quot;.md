---
title: "booting stops at &quot;kernel log damon&quot;"
date: 2008-11-29
forum: General Help
---

### Post by osterchrisi on 2008-11-29
hi guys,

after installing ubuntu 8.10 today i approximately spent 12 hours trying to geht my soundcard to work - still doesn't.
however, after a reboot (not the first one) i wasn't able anymore to do "sudo" actions because i suddenly wasn't on the sudoers list anymore.
so i went into recovery mode to edit the sudoers file via "visudo" as root. i soon discoverd that this was way to high for me and left nano without saving - it even said something like "saved unedited" or something, can't remember exactly.

so i tried to reboot but there seems to be something broken now. after the line
"System log daemon [OK]" it says
"chown: invalid group: 'syslog:adm'" thirteen times (i guess these are my "unauthorized" sudo tryings)
and a few lines beneath it says
"kernel log daemon [OK]" and then
"chown: invalid group: 'klog:klog'" twice and then it stops right there.

i updated ubuntu right after installing so i guess i have all the newest kernel an stuff.

what is bloody wrong with my ubuntu?
thanks for any help i really appreciate it!

---

### Post by inspired on 2009-01-25
How did you get on with this?
Is there a solution?
I am having the same issue.
Not sure what did it, but this morning I could not do anything on the system that required admin permissions.
Sudo was hosed.
Following instructions in the forums I took a look at the sudo file using visudo. Everything seemed to be the way it was meant to be so I changed nothing and exited ( :q<enter> )

I then tried issuing an adduser command to add me to the admin group. But it gave an error saying the admin group does not exist.

Now when I start up the system it seems completely hosed. Many lines relating to missing groups come up. It then hangs.

I may post this in more detail in a new thread. Just posting here because you've described the same issue... although there was no follow-up.

Thanks...
Jonathan

---

### Post by inspired on 2009-01-25
Just a note to say I have decided to take this issue up over on [http://ubuntuforums.org/showthread.php?p=6614344](http://ubuntuforums.org/showthread.php?p=6614344) where there appeared to be discussion related to this exact issue.

Jonathan

---

