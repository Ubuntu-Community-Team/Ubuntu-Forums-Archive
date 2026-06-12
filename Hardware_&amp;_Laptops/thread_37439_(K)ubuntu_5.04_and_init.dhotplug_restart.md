---
title: "(K)ubuntu 5.04 and /init.d/hotplug restart"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by Skyes on 2005-05-27
Hi experts,

I'm new to Linux but I start to like it and refuse to go back to XP again [-X 
After some days of playing with the installation my HP nx7010 laptop is now quite usable. One issue remains...
If I hibernate (suspend-to-disk) and resume my USB-Mouse refuses to work with me while the internal touch-pad works. I can bring the mouse back to life again by re-starting the hotplug system in the shell. Is there some way to automize this? I thought about modifying resume.sh but either I didn't understand the script (quite likely :roll: ) or it's the wrong file for adding the command.

Any ideas? 

So far my resume.sh looks like this (at the end):
```
-------- 
... 
# Some hardware gets unhappy about button events unless we do this 
rmmod button 
modprobe button 

# Let acpid process events again 
(sleep 1 && rm /var/lock/acpid)& 

# Begin of my modification
[COLOR=RoyalBlue]/etc/init.d/hotplug restart [/COLOR]
# End of my modification
# End of resume.sh
-------- 
``` 

TIA,
Skyes

---

### Post by phen on 2005-06-06
[QUOTE=Skyes]Hi experts,

I'm new to Linux but I start to like it and refuse to go back to XP again [-X 
After some days of playing with the installation my HP nx7010 laptop is now quite usable. One issue remains...
If I hibernate (suspend-to-disk) and resume my USB-Mouse refuses to work with me while the internal touch-pad works. I can bring the mouse back to life again by re-starting the hotplug system in the shell. Is there some way to automize this? I thought about modifying resume.sh but either I didn't understand the script (quite likely :roll: ) or it's the wrong file for adding the command.

Any ideas? 

So far my resume.sh looks like this (at the end):
```
-------- 
... 
# Some hardware gets unhappy about button events unless we do this 
rmmod button 
modprobe button 

# Let acpid process events again 
(sleep 1 && rm /var/lock/acpid)& 

# Begin of my modification
[COLOR=RoyalBlue]/etc/init.d/hotplug restart [/COLOR]
# End of my modification
# End of resume.sh
-------- 
``` 

TIA,
Skyes[/QUOTE]
 got the same problem, tried to fix it by the same modification. didnt work either :-(

perhaps somebody around has a clue?

thank you all! :-)

kai

---

