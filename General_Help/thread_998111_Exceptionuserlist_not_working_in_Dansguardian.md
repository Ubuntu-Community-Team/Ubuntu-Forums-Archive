---
title: "Exceptionuserlist not working in Dansguardian"
date: 2008-11-30
forum: General Help
---

### Post by Kawa800 on 2008-11-30
I added my user name to the file but I am still getting blocked.  Do I need to add some sort of a tag?  Or is there a setting somewhere else that I need to activate?

---

### Post by linuxaz on 2008-11-30
Kawa,
I use Dansguardian too.  When you make changes to the lists, make sure to restart Dansguardian.   Then it should pick up the new configuration.

$/etc/init.d/Dansguardian restart

linuxaz

---

### Post by Kawa800 on 2008-11-30
I tried restarting using your command, but that gave an error.  One of the steps in the guide that I followed had me restart 3 things so I tried that:

david@Air:~$ sudo /etc/init.d/tinyproxy restart
Restarting tinyproxy: tinyproxy.
david@Air:~$ sudo /etc/init.d/firehol restart
 * Restarting Firewall configuration                                     [ OK ] 
david@Air:~$ sudo /etc/init.d/dansguardian restart
Restarting DansGuardian:  * Restarting DansGuardian:                     [ OK ] 
david@Air:~$ 

The guide that I used is this one:  [http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian](http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian)

any other ideas?

---

### Post by Kawa800 on 2008-11-30
I tried restarting using your command, but that gave an error.  One of the steps in the guide that I followed had me restart 3 things so I tried that:

david@Air:~$ sudo /etc/init.d/tinyproxy restart
Restarting tinyproxy: tinyproxy.
david@Air:~$ sudo /etc/init.d/firehol restart
 * Restarting Firewall configuration                                     [ OK ] 
david@Air:~$ sudo /etc/init.d/dansguardian restart
Restarting DansGuardian:  * Restarting DansGuardian:                     [ OK ] 
david@Air:~$ 

The guide that I used is this one:  [http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian](http://ubuntuforums.org/showthread.php?t=207008&highlight=dansguardian)

any other ideas?

---

