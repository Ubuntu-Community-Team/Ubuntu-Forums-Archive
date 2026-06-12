---
title: "save email and bookmarks"
date: 2005-11-18
forum: General Help
---

### Post by wanger123 on 2005-11-18
Hey guys, I just upgraded from hoary to breezy and then to kde 3.5 rc1 today, and all seems fairly good (well I can work around some things lol). I must admit that I didnt do a fresh install as I wasnt sure how to save my hundreds (thousands?) of emails and bookmarks. Is there a way (certain folders etc) to backup these things up and then copy them back into the new version of the distro?
thanks in advance
wayne

---

### Post by lerrup on 2005-11-18
/home/user/.kde - this will contain all your kde specific info.

Have a look in there first.

---

### Post by wanger123 on 2005-11-18
thanks lerrup. I actually found it here already. 
/home/wayne/.kde/share/apps/
You have to "show hidden files" in the browser first.
I really should have a thorough look before posting lol.
So in theory, I could do a clean install, then edit the appropriate files (/home/wayne/.kde/share/apps/, fstab, etc, etc, etc) with kate as root, and everything should be how I had it before right??
Many thanks              
wayne

---

### Post by wanger123 on 2005-11-18
Just spent 2 frickin' hours on this, and no matter what I do (login as root etc), I cant copy the email messages from /home/wayne/.kde/share/apps to another hard disk. I can do everything else eg bookmarks etc but not the actual messages. I can copy them to the same hard disk partition (ie linux partition) but not to a fat32 partition. This kind of makes it hard to do a clean install without losing all the messages. Shouldn't there be an export option? Any ideas guys? Someone else must have done this before
thanks
wayne

---

### Post by megamania on 2005-11-18
*Warning: I'm a newbie and use Gnome*

Why don't you try opening the file browser with sudo? In Gnome I'd do

sudo nautilus

from the terminal. You would then act as root, being able to copy everything.

---

### Post by aysiu on 2005-11-18
/home/username/.kde won't back up my emails and bookmarks.
What programs are you using for email and the internet?
When I back up my emails and bookmarks, I back up these two folders:
/home/username/.mozilla
/home/username/.mozilla-thunderbird

---

### Post by wanger123 on 2005-11-18
Thanks for the reply aysiu. I am using kmail and konqueror. 
I think I have solved this by saving my /home folder using ARK and creating a .tar.gz file. This can then be saved to an external device or another hard drive. Then I can extract the appropriate files (/home/wayne/.kde/share/apps/kmail etc) back to my new installation's /home folder.
Hope this helps others
wayne

---

