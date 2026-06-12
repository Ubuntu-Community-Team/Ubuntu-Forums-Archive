---
title: "was running out of disk space and cannot log in after rebooting"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by tevang on 2009-07-13
I am using Kubuntu 7.10 and after a reboot, whenever I try to log in the screen goes black for a while and then I am re-prompted to log in. No error message about my password is displayed. 
Before I reboot I was getting some warnings that I'm  running out of disk space, but I had deleted most of the large directories. Apparently my user partition wasn't mounted.
Can anyone shed some light on this please?

thanks,
Tom

---

### Post by unlimitedz on 2009-07-13
Can you remember specifically what directories you deleted?  Were they in your /home directory? Perhaps you deleted some system files...

---

### Post by stefangr1 on 2009-07-13
At the login menu you have to choose session type "console login".

After entering your username and password, you are in a terminal. Here you can move or delete files using commands.

You can navigate trough your filesystem using "cd" "folder name", using "ls" gives you the files in the current folder, "ls -l" gives you the size of each file (such that you can check what files make sense to delete).

If you only have to move files to another partition, you can use commands like:

mv /home/username/dvd.iso /media/something/dvd.iso

If you have no space left at all, you have to remove files using:

rm /home/username/dvd.iso

WARNING: don't do strange things with the rm command as it can wipe out your entire filesystem.

If this doesn't work for you, and you have a live cd you can use, you can boot from the cd and free some space from a graphical environment.

---

### Post by tevang on 2009-07-13
Thanks for the replies, I had someone to help me eventually. My /home/thomas/.local had 2.8 G of trash and occuppied all my account partition.

---

### Post by unlimitedz on 2009-07-13
You can avoid problems like this if you have a separate partition for /home.  That way if /home gets full, you don't break your install.

---

