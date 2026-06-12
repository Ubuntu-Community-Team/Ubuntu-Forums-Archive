---
title: "Upgrade Strategy"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by petersra on 2009-04-11
Hi,

I plan on upgrading my desktop system from 8.04 to 9.04 in the near future.  The 8.04 system is pretty complex with lots of apps, Wine, Virtual Box, LAMP, USB scanner, etc. and I am very happy with it.  

So, what is the best strategy for the upgrade?  My thoughts are to use Ubuntu to upgrade the system.  Once completed then save all my Synaptic markings, etc and do a fresh install.  Its a two step process but seems like the best option.  

Ideas, comments?

---

### Post by Partyboi2 on 2009-04-11
I would suggest using the recommend network upgrade path and upgrade to 8.10 then 9.04 
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by OrangeCrate on 2009-04-11
Adding to what Partyboi2 has said, see post #96 in this thread:

[http://ubuntuforums.org/showthread.php?p=6063808](http://ubuntuforums.org/showthread.php?p=6063808)

---

### Post by jchiar on 2009-04-11
I would also suggest a good backup of the data that you feel or is crucial in your operations and use.
The update transition is fairly smooth, and works easily, but , stuff could happen. 
This link is known as The Smiley Thread, if you look it is from a backup that was made in 1982 and recovered in 2001.
A dump of the CMU CS general bboard contents from the 1982 year-end g vax (cmu-780g) backup tape spanning the dates 25-Nov-82 to 31-Dec-82 is below.  This was retrieved by Jeff Baird on July 15, 2002 while searching for the original bboard post in which Scott Fahlman invented the smiley :-).
[http://research.microsoft.com/en-us/um/people/mbj/Smiley/Smiley.html](http://research.microsoft.com/en-us/um/people/mbj/Smiley/Smiley.html)
Because stuff happens.

---

### Post by petersra on 2009-04-20
Thanks for the reply.  

So, I updated from 8.04 to 8.10 - no problem.  Then I updated to 9.04 via the update-manager -d option.  Everything went well until boot.  I entered my un/pw and then a blank screen.  

I dropped out of the GUI to CLI and logged in with my un/pw.  The problem was that most of the files in /home/rob had the owner and permissions set to 1000 not rob.  Tried to change them but it required root access.  Tried sudo and it would not allow me to use
change the permissions.  Finally, I threw in the towel and did a clean reinstall with a no mount on /home. :o

---

