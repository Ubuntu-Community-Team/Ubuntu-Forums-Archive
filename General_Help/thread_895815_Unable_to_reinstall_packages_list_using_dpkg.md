---
title: "Unable to reinstall packages list using dpkg"
date: 2008-08-20
forum: General Help
---

### Post by sofasurfer on 2008-08-20
I saved a list of all my installed packages using 

'dpkg --get-selections > /media/disk/backup/Documents/list-of-installed-packages". This was successful.

Next, I went to my other Ubuntu setup and tried to install the packages by using "sudo dpkg --set-selections < /media/disk/backup/Documents/list-of-installed-packages".

I then create a new list and I see that it is STILL the old list of packages. The new list is not being installed.

I then did a "sudo apt-get update" and sudo apt-get upgrade".
I still do not have the new list or any of the new packages.

Are my stepps correct? What am I doing wrong?

---

### Post by prshah on 2008-08-20
> **sofasurfer said:**
> 
Next, I went to my other Ubuntu setup and tried to install the packages by using "sudo dpkg --set-selections < /media/disk/backup/Documents/list-of-installed-packages".

According to the man, you should use "--clear-selections" before using "--set-selections"; just a pointer, I have no idea if it will work or not so use with caution. I'd suggest you read the man before you try this.

Are you sure the selections file is being read correctly? What do you get with the following command```
tail /media/disk/backup/Documents/list-of-installed-packages
``` (Note no "sudo").

---

### Post by sofasurfer on 2008-08-23
I have accomplished installing the packages from the package-list. Here are my steps, taken from this website...

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

Package list should have been created and saved to file and stored to backup disk by using this command...
dpkg --get-selections | grep -v deinstall > /media/disk/backup/installed-package-list
The above command creates the list and saves it to my backup disk.

To use this list to recreate the Linux system follow these steps...
1) Reinstall base system
2) Copy nessessary files from backup - entire network directory copied back to /etc/, sources.list copied back to etc/apt/
3) Open network config window and enter encryption key. You now have internet access and the proper source.list to reinstall your packages.
4) sudo apt-get update
5) sudo apt-get dist-upgrade
6) dpkg --set-selections < /media/disk/backup/installed-package-list
7) sudo apt-get install dselect
8) sudo dselect
9) when promted, choose to install packages

You can now use...
dpkg --get-selections | grep -v deinstall > /new-system-installed-package-list
...to create a new list to compare with package-list from old system.

When I am in dselect there is an option to configure non-configured packages. This option does nothing that I can see.

EDIT::
Am I missing any steps to a fully cloned system? To replace all the config files would I just copy the /etc directory from ny backup drive onto mt new system?

EDIT::
P.S. I just saved this post and for some reason step eight has a smily face instead of the number "8". Just letting you know that it should be an "8". I tried to edit it out but it didn't work. Hmmmmm

---

