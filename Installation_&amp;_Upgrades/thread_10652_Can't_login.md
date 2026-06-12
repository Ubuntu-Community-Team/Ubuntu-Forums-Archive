---
title: "Can't login?"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by Dissonance on 2005-01-09
Well, I'm COMPLETELY new to Ubuntu. (In fact, I hadn't heard about it untill 2 hours ago) I'm just through installing, and I'm sitting at the GNOME login screen.

I try to login, and I get logged back out, with an error.  

"Your session lasted less than 10 seconds.... ect ect"


The log shows this:
> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/lib/gdm/:0.Xservers"  -h " " -l ":0" "dissonance"
/ect/gdm/Xsession: Beginning session setup. . .

(gnome-session: 19865): libgnomevfs-WARNING **: Unable to create ~/.gnome directory: Permission denied
Could not create per-user gnome configuration directory `/home/dissonance/.gnome2/': Permission denied


Edit: I was told by a friend I should post my partition information.

hda1 = windows XP (which I don't boot into, because it's broken, but I need to recover data from it)
hda5 = ubuntu boot
hda6 = Swap partition
hda7 = This is where I mounted /home 

I think the problem is that hda7 is getting mounted as a READ-ONLY file-system.  That might explain this, right?  If that's the case, any idea on how I can change it/fix it?

---

### Post by randy on 2005-01-10
Have the partition mounted as read-only would definitely be a problem.  Have you modified anything in your fstab to make it mount read only?  If not it may be a filesystems with errors so you should run e2fsck on it before you reboot.  That may take care of your problem.

---

### Post by Dissonance on 2005-01-10
[QUOTE=randy]Have the partition mounted as read-only would definitely be a problem.  Have you modified anything in your fstab to make it mount read only?  If not it may be a filesystems with errors so you should run e2fsck on it before you reboot.  That may take care of your problem.[/QUOTE]
 I have solved it.  The problem was that I was "re-using" an existing partition.  (From SUSE 9.1)  I had it as /home, and when I installed ubuntu, I didn't reformat it.  Somehow, throughout the course of the install, it became Read-Only, and refused to let me login.  

I simply went through the install again, and told it to format that particular partition.  All is find now.  

Thanks. :)

---

