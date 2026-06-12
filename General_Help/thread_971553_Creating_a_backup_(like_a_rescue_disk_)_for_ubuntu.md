---
title: "Creating a backup (like a rescue disk ) for ubuntu install"
date: 2008-11-05
forum: General Help
---

### Post by super_czar on 2008-11-05
I have a server that runs ubuntu and works as my NAS , seedbox , proxy server and several other things.

I was a complete n00b to linux when I started on the project and it took me a lot of time & effort to set it up.
It has been now been at least a year since I setup the server, and since I do not use Linux on a daily basis, whatever knowledge I had picked up back then is nearly gone now.

Last night ( I may have imagined this), I heard some noises coming from the server's primary HDD
Now If the primary HDD crashes, I am not sure if I'll have the time & patience to redo the whole thing again.

Is there some way I can clone the entire installation to some kind of a rescue disk..so that in case the drive gives up the ghost, I would be able to restore the installation with minimum fuss and effort (similar to The way Acronis does it for windows installs)

Oh, And I also wish I can skip the media folders since I want the backup to be a system rescue option
Media (and other non system files) in my home directory are backed up separately on a standalone NAS

---

### Post by indytim on 2008-11-05
If you have the "offline" storage capacity (i.e. an external h/d), I'd recommend a look at partimage.  It's a partition backup app.  From your posting, the downside is that it will back up the entire partition.  You mentioned that there are some directories that you do not want to backup.

I can tell you from first-hand experience that partimage works well.  I backup all of my partitions on a weekly basis.  I've had occasion to restore partitions from a backup and it has done so with good speed and no issues with respect to integrity. 

If you're interested, take a look at the backup link in my sig for more detailed information on how I back things up.

Hope this helps.

IndyTim

---

