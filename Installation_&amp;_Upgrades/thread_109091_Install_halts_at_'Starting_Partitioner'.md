---
title: "Install halts at 'Starting Partitioner'"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2005-12-27
Ubuntu 5.10 (breezy badger) - my install consistently stops at 'Starting the partitioner' - with 52% done.  

Any ideas?

Also - re post earlier tonight, 'Install to a Slave' - I'm hoping to install it to a small HD, currently jumpered to Slave.  The answers to the last post told me I should be given the option of which HD to install to...only...I had a look in Expert install, and there was nothing obvious.  (I'll be wanting to dual boot with my current Master '98 HD)

---

### Post by tinsami1 on 2005-12-28
I had the same problem.  I deleted all partitions the primary harddisk and restarted the machine.  The problem went away.  I guess there is a problem with the installer if there are no more space in the primary hd.

try manually creating the partitions in the second hd:  
1. hit Alt-F2 or Ctrl-Alt-F2 to go to the second session.
2. Press any key to start the session
3. run cfdisk on /dev/hdb
4. create the / (root) and swap partitions.
5. Save the table and reboot.

---

### Post by Edward The Bonobo on 2005-12-28
Thanks...

But can we assume I'm a total dunce, please and explain steps 3 to 5 in total detail...with subtitles for the hard of thinking? :???:

---

