---
title: "problem restoring evolution addressbooks"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by argie01 on 2005-12-14
Hello,

I had a problem with Breezy and I've reinstalled (from zero) Breezy 5.10.
Before it, I did a backup of the entire .evolution directory.

Then, to restore it, I've overwrited the original .evolution directory with the one I've saved on.
So, now I get my emails correctly, but I just can see 1 address book, and before the new installation I had 3 ones.

When I see /.evolution/addressbook/local$ y get it:

drwxr-xr-x 2 german german 4096 2005-12-13 17:02 1123758982.8478.10@itd053
drwxr-xr-x 2 german german 4096 2005-12-05 18:56 1123761116.8478.14@itd053
drwxr-xr-x 2 german german 4096 2005-12-05 18:56 1127406601.30192.21@itd053
drwxr-xr-x 2 german german 4096 2005-12-05 18:56 1127838161.8461.2@itd053
drwxr-xr-x 2 german german 4096 2005-12-13 17:03 1134489789.8139.0@ITD053
drwxr-xr-x 2 german german 4096 2005-12-05 18:56 system

Inside each of these directories there are the following files:

-rw-r--r-- 1 german german 12288 2005-12-05 18:54 addressbook.db
-rw-r--r-- 1 german german 217 2005-12-05 18:56 addressbook.db.summary

When I edit the file .db I can see there are all my contacts.
But, how can I do to restore all my addressbooks, by using this files... ???

Thank you !

---

### Post by Herman on 2005-12-14
argie01, hello, I tried something like what you are doing but I just did it in 'GUI'

What I did to back up: I clicked 'show hidden file', in my /home/herman directory, and opened .evolution, and just copied out the addressbook and mail. I pasted them both into another folder named 14dec05bkup.

Then I moved this folder by SSH to another computer with a fresh 'Breezy' install and pasted it into my /home/herman directory there. 

Then I set up evolution for the first time in the new install, it had never been started before.

To restore: I copied the addressbook out of the 14dec05bkup, and clicked 'show hidden files', once again, but this time in the new installation. I pasted the old addressbook into the new .evolution directory, then did the same with my mail folder.

When I started evolution, there was all my mail and my addresses!:D 
I'm not too sure about three addressbooks though, I think you have to use only one at a time, but I'm not sure, maybe you know some tricks better than me, but what I just described worked for me when I tried it. I hope this is some help for you. (Herman)

---

