---
title: "Not enough free disk space"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by davidlukens on 2008-12-27
When I try to upgrade form 8.04 to 8.10, I get the message "The upgrade aborts now.  The upgrade needs a total of 113M free space on disk '/boot'.  Please free at least an additional 71.9 of disk space on '/boot'.  Empty your trash and remove temporary packages of former installations using 'sudo apt-get-clean'.
I have done all that, and find that '/boot' is full of items like
/boot/initrd.img-2.6.20-16-generic
/boot/initrd.img-2.6.20-16-generic.bak There are eight pairs of these at about 14M each; they cannot be moved to the trash, and I am told when I look at the 'Properties' of the files that I do not own them.  What can I do to get rid of these files?  I have now idea where they came from.::confused:

---

### Post by speed32219 on 2008-12-27
Try change owernship of the file.

Sudo chown Your_login_name_here /boot/initrd.img-2.6.20-16-generic.bak 

Next change mod:
sudo chmod 777 /boot/initrd.img-2.6.20-16-generic.bak 

Than you should be able to remove.
sudo rm /boot/initrd.img-2.6.20-16-generic.bak 

or use navigator to do it.

---

### Post by davidlukens on 2008-12-28
Thank you.  
"Sudo chown your name /boot/initrd.img-2.6.20-16-generic.bak" returns "Bash command not recognized" but the next two lines work.  I will repeat it for the other 14 files.  It looks as if you have saved me!  Many thanks

---

