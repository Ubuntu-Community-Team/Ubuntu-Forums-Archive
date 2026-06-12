---
title: "Upgrade, but want to clean /home first."
date: 2008-09-07
forum: General Help
---

### Post by plamen_todoroff on 2008-09-07
I want to install 8.04.1 as I'm using Gutsy at the moment. I have /home on a separate partition so it's going to be easy, but I'm a little worried about all those config files in it (.files).

I'd like to get rid of them because I want a clean default install, and I don't think I really need them anyway.

So my plan is to boot the live cd, delete all that I don't need in this /home partition and then install 8.04.1 without formating /home.

Is this possible? Will there be permission problems when I try to delete these .files & .directories in /home by booting into the live cd and doing it from there?

Are the permissions kept when there's no OS? And will the permission be the same for the files I left intact in /home, when I install 8.04.1? Should I use the same login name when I install 8.04.1, the same as I got in Gutsy?

Thanks, I hope you understand my English.

---

### Post by drs305 on 2008-09-07
What exactly do you want to *keep* from the current contents of your home folder? 

If you don't want to keep any of the config files and are worried about permissions, I would recommend just moving your data files somewhere else (another drive, another partition, CD/DVD) and just reformat the /home partition as well. 

The main reason people have a separate home partition is to be able to keep their configuration settings when doing an upgrade. Since you don't want to do this, why keep any of the /home partitions? I've always maintained a separate partition for my *data* files - it sounds like you might want to do the same - at least until you have reinstalled the OS.

Just one person's opinion.

---

### Post by sdennie on 2008-09-07
Another option would be to just move your home directory to something like, "/home/username.bak" and then reinstall.  The idea being that it's much safer to bring files into a "clean" user than it is to remove them from an old user.  Ownership is by UID and not username so, you will be owner of both directories on reinstall as long as you only have a single user so, the process is very simple.

---

