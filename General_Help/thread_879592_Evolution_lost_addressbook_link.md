---
title: "Evolution lost addressbook link"
date: 2008-08-04
forum: General Help
---

### Post by agamemnon1 on 2008-08-04
Am running ubuntu 7.10 - following unsuccessful installation of 8.04 returned to 7.10, running without fault, however;
Evolution now will not display an addressbook.

Error message:

Error loading addressbook.

We were unable to open this addressbook. Please check that the path /home/matthew/.evolution/addressbook/local/system exists and that you have permission to access it.

I have checked for this file, and it exists in my system, and my permissions appear to allow write and read access.
Have also checked under system tools and evolution appears to be directed toward this file.

Any help would be appreciated, as I have to write my email contacts down.!!

Cheers,

agamemnon

---

### Post by dimeotane on 2008-09-16
I had a similar problem.  I changed my username folder and copied the contents from /home/dimeo-dell to /home/dimeo and reset all the permissions.

But now evolution is still looking for the /home/dimeo-dell directory for my contacts.  The little mini 'contacts' package can still load up my contacts, but not evolution. 

How do I change or reset the path to Evolution's contacts?

---

### Post by fragos on 2008-09-17
In ~/.evolution/addressbook/local/system make addressbook.db a link to the addressbook.db file you wish to use.

---

### Post by dimeotane on 2008-09-21
Ok I think I found a solution.


Make sure you've fully quit evolution:
$ evolution --force-shutdown
$ killall gconfd-2

use gedit to change 
/home/username/.gconf/apps/evolution/addressbook/%gconf.xml

change all references to the old username to the new username. 

I think that did it for me.

---

