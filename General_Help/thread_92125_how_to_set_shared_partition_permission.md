---
title: "how to set shared partition permission?"
date: 2005-11-18
forum: General Help
---

### Post by nandasunu on 2005-11-18
Hi, I'm pretty new to the whole linux scene. I've just installed ubuntu on my laptop as a dual boot with winXP. It seems that the shared fat32 partition is set to read-only for all users apart from root. I have no idea how to change this so i can actually use the partition. Any advice would be much appreciated.

thanks.

---

### Post by ember on 2005-11-18
I guess, you mount it from /etc/fstab, so look at that file (you have to edit it as root or with sudo) and correct the line corresponding to you fat32 driver to something like:

/dev/sdc3 /media/DATEIEN vfat rw,noexec,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8

Best,
ember

---

### Post by schdefan on 2005-11-18
I think you don't give users permission to access the partition. 
Edit the /etc/fstab if you want to mount at boot time
> /dev/hda5       /media/windows  vfat    umask=0222      0       0
or run 
> sudo mount /dev/hda5 /media/windows/ -t vfat -o umask=000
in a terminal.
Change hda5 to your partition number.
Check out the starterguide.
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514804]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514804")

schdefan

---

### Post by nandasunu on 2005-11-18
Thanks for the help, but I still can't solve this problem. I logged in as root and tried changing the permissions - this is not possible. 

[QUOTE=schdefan]Edit the /etc/fstab if you want to mount at boot time[/QUOTE]

I tried this and it lets me view the partition, but as read only. 

I am sure there are many users with a similar setup, what is the most common way to do this?

thanks.

---

### Post by aysiu on 2005-11-18
[QUOTE=nandasunu]
I am sure there are many users with a similar setup, what is the most common way to do this?[/QUOTE] [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by schdefan on 2005-11-18
you cannot change permissions on a fat32 (because it comes from the windows world) from a linux box which does not mean that you can't write on it.
Are you able to write as user because you said it viewed the partition but as read only.
schdefan

---

### Post by nandasunu on 2005-11-18
Thanks for the link and the extra information. This is my first linux excursion... 

I think it is working now (cross fingers). I removed the original line from etc/fstab and started again following the instructions on that link. I can now use most of the files on the fat32 with no problem! :D  There are still a few that are read-only, but I'll look into that later.

Thanks again for all the help!! I'd be lost without it.

---

