---
title: "dmrc file"
date: 2008-10-14
forum: General Help
---

### Post by pcjunkie on 2008-10-14
It seems if I change the hard drives in /media/ my dmrc file crashes and burns/

Today I formatted 1 and had to reset the dmrc file
Changed partitions in another again same result
and later I had to change the order of drives and now I have to do it again.

I have also had problems with /.trash not deleting on one of the deleted hard drives. I had to totally format it without deleting it first. admin (root) would not delete these files either. The HDD show empty in GIU yet is has 260gb of trash hat does not exist unless you open nautilus under root.

is there a major bug in gnome regarding this issue? 

$ sudo chown user:user 
# sudo chmod 700  

and 


# sudo chown user:user .dmrc
# sudo chmod 600 .dmrc
 
seem to work but not always

---

