---
title: "Clean out /root folder"
date: 2008-08-07
forum: General Help
---

### Post by itzfritz on 2008-08-07
rot's home folder is mounted on the same partition as / (contrary to the other home folders), and since I unfortunately did a lot of initial work as the root user (not sudo-ing), that /root folder has become bloated and is threatening to fill up my root partition completely.

Can anyone recommend methods/best practices/tips for cleaning out the /root folder without screwing anything up for those times that I have to log in as root (single-user mode, for example).

This is what is in there:
total 3230
drwxr-xr-x 26 root root    1024 2008-08-07 11:31 .
drwxr-xr-x 23 root root    1024 2008-08-07 06:46 ..
drwx------  2 root root    1024 2008-08-02 00:25 .aptitude
-rw-------  1 root root    2709 2008-08-07 12:01 .bash_history
-rw-r--r--  1 root root     444 2008-08-02 00:45 .bashrc
-rw-r--r--  1 root root     412 2004-12-15 17:53 .bashrc~
drwx------  3 root root    1024 2008-02-02 13:24 .config
drwxr-xr-x  2 root root    1024 2008-08-02 00:39 Desktop
-rw-------  1 root root      26 2008-02-02 12:01 .dmrc
drwx------  4 root root    1024 2008-08-07 11:31 .gconf
drwx------  2 root root    1024 2008-08-07 11:57 .gconfd
drwx------  3 root root    1024 2007-06-23 11:56 .gftp
drwxr-xr-x 21 root root    1024 2008-08-05 12:24 .gimp-2.2
drwxr-xr-x  3 root root    1024 2008-02-02 12:01 .gnome
drwx------ 10 root root    1024 2008-08-03 15:22 .gnome2
drwx------  2 root root    1024 2007-06-23 11:23 .gnome2_private
drwxr-xr-x  2 root root    1024 2008-02-02 12:01 .gstreamer-0.10
-rw-r--r--  1 root root      81 2008-02-02 12:01 .gtkrc-1.2-gnome2
-rw-------  1 root root    6132 2008-08-07 11:31 .ICEauthority
drwx------  3 root root    1024 2008-07-29 23:39 .kde
-rw-------  1 root root      35 2008-08-04 00:14 .lesshst
drwxr-xr-x  3 root root    1024 2008-07-29 23:40 .mcop
-rw-------  1 root root      31 2008-07-29 23:40 .mcoprc
drwx------  3 root root    1024 2008-02-02 12:01 .metacity
drwx------  3 root root    1024 2008-03-12 22:09 .mozilla
drwx------  3 root root    1024 2008-07-30 15:45 .mysqlgui
-rw-------  1 root root      99 2008-07-09 00:43 .mysql_history
drwxr-xr-x  3 root root    1024 2008-02-02 12:01 .nautilus
drwx------  2 root root    1024 2008-07-30 15:31 PDF
-rw-r--r--  1 root root     110 2004-11-10 11:10 .profile
drwxr-xr-x  2 root root    1024 2008-07-29 23:39 .qt
-rw-------  1 root root   15078 2008-08-07 11:37 .recently-used
drwx------  3 root root    1024 2008-03-14 00:44 .synaptic
drwx------  4 root root    1024 2008-07-30 00:53 .thumbnails
drwx------  2 root root    1024 2008-07-30 15:34 .Trash
drwx------  2 root root    1024 2008-02-02 12:01 .update-notifier
drwxr-xr-x  2 root root    1024 2008-08-07 11:31 .vnc
-rw-------  1 root root     421 2008-08-07 11:31 .Xauthority
-rw-------  1 root root 3230526 2008-08-07 11:35 .xsession-errors

What can I get rid of?

Thanks!

---

### Post by mannheim on 2008-08-07
I don't think you'd do any harm by deleting all the contents of /root here. But why bother? You shouldn't worry that the /root folder is "threatening to fill up [your] root partition completely". The top-level contents in that list is just a few megabytes. To see how much space it is actually using, you can do this in a terminal:

```
sudo du -hs /root
```

If it's only 10M or so, then you are only using less than a tenth of one percent of your partition. If it is much much larger, then find out which directory is taking up space.

---

### Post by cariboo on 2008-08-07
I've got the same list of files in /root it only takes up 8MB, the only thing I would woory about is the .local/share/Tash, if you are using root a lot to delete files.

Jim

---

### Post by y@w on 2008-08-07
Right, your du command should tell you exactly how much space /root is actually using. If it's a lot and you're concerned about keeping profiles around, you can do: ```
sudo du -sch /root/*
```

That will give you a list of files inside root's home dir and the amount of space they are using. That way you can narrow down exactly what in /root is taking up space. Most of the files listed are going to be extremely small and insignificant.

---

### Post by x1a4 on 2008-08-07
This is what I would do.  Keep in mind that when you run something using sudo, the config files will be saved in /root/

.aptitude - leave as is

.bash_history
.bashrc
.bashrc~

unless you run sudo with the -i option you can delete your shell config and history.  Although it's a good idea to keep them--I would.

.config

configuration files for X apps.  You can safely delete this directory, although it will be recreated by GUI apps that make use of it, when you run them for the first time.

Desktop -remove

.dmrc

default GUI session.  Might want to leave it.

.gconf
.gconfd

GNOME configuration.  You can delete them, but they will be recreated when you run an app that uses them.

.gftp

gFTP config. Remove

.gimp-2.2

GIMP config. Remove

.gnome
.gnome2
.gnome2_private

More GNOME config

.gstreamer-0.10

gStreamer plugin info. Remove

.gtkrc-1.2-gnome2

GTK config.  Might want to leave it.  GUI apps started using sudo will use the themes in here

.ICEauthority

?? Probably should keep this one.

.kde

KDE config. Remove

.lesshst
.mcop
.mcoprc
.metacity
.mozilla
.mysqlgui
.mysql_history

Remove

.nautilus

Keep for when you run Nautilus as root 

PDF

Keep/Remove depending on what you have in there.  You'll probably want to move the files elsewhere, then delete this directory.

.profile

Keep for when you use sudo -i or login as root

.qt
.recently-used

Remove

.synaptic

Keep

.thumbnails

Remove

.Trash
.update-notifier
.vnc
.Xauthority
.xsession-errors

Remove

---

### Post by bodhi.zazen on 2008-08-07
Best way to keep /root clean is not to run X as root.

If you are going to continue to log in as root, all those config files will be re-generated, so no need to clean it out.

If you are going to change the way you use your system, by all means clean it out.

---

### Post by y@w on 2008-08-07
> **bodhi.zazen said:**
> Best way to keep /root clean is not to run X as root.

If you are going to continue to log in as root, all those config files will be re-generated, so no need to clean it out.

If you are going to change the way you use your system, by all means clean it out.

Yes.. I'd like to add to that: It's best not to login to X as root anyway.

---

### Post by itzfritz on 2008-08-10
Thanks everyone.

Very helpful advice, all around!

---

