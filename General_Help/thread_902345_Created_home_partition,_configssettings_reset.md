---
title: "Created /home partition, configs/settings reset"
date: 2008-08-27
forum: General Help
---

### Post by Inane_Asylum on 2008-08-27
I created a separate /home partition as described on the [psychocats]("http://www.psychocats.net/ubuntu/separatehome") website, and now it looks like a freshly-installed OS.  All of my programs are there, but none of my settings are.  The desktop background is default, no desktop icons, quicklaunch bar is back to default, firefox goes to its default homepage on startup and not the one I set, etc.  I can access my /home folder, so I know it can read it.  Is this normal? Am I going to have to reset all my personal settings?  Is it because I'm using KDE and not Gnome?:confused:

Any help is much appreciated.

---

### Post by Taxman415a on 2008-08-27
No it probably has nothing to do with KDE vs Gnome. Those types of settings are stored in so called dotfiles (because the files and directories start with a . and you need to use the -a option to ls to see them normally) so it looks like either those didn't get copied into your backup correctly, copied out of your backup correctly, or there is a permissions problem. Go into your home directory, and if you followed the guide exactly, your home directory under /home_backup and compare the output of ```
ls -al
``` from each. Now that you've run a few things you've created the .mozilla directory for firefox, so that one won't help you tell the difference, but other things will. Compare carefully and see if things are missing from your new home directory's dotfiles or if everything is there, there will be differences in the stuff that looks like -rw-r--r--  1 taxman  taxman, ie, the permissions and ownership stuff.

Perhaps you didn't type a command perfectly from the guide, or did you use sudo for the find line in the guide?

---

### Post by Inane_Asylum on 2008-08-27
Didn't use sudo...saw that after I copy/pasted the find line...mebbe I'll undo all the changes and redo with the sudo find command.

At work right now and away from the computer, so I'll post updates as soon as I can get to it.

Thanks.

---

### Post by Inane_Asylum on 2008-08-27
Instead of formatting the /home partition, would I be able to just go back to my home_backup, rename it as home again, and then paste the sudo find?  Would it overwrite everything and/or add in what's missing, or would it just not work?

---

### Post by Elfy on 2008-08-27
Have you tried to use the part at the end of the psychocat page to get the backup back?

---

### Post by Inane_Asylum on 2008-08-27
Well, I know the backup's intact...that's not the problem.  I just know it would be more work reformatting the /home partition, restoring the fstab and home backups, and redoing the whole process again.  I was wondering if it was possible just to paste in the 'sudo find' command to add in the rest of the files (if the permissions/.files really was the problem).

---

### Post by Inane_Asylum on 2008-08-27
Weird...this time I booted up the laptop, everything's on my desktop that should be there (just the files, still not the superkaramba stuff).  Everthing seems to be working fine except my personal settings...

ls -al gave me this:
```
total 861248
drwxr-xr-x 51 cullens cullens      4096 2008-08-27 21:12 .
drwxr-xr-x  4 root    root         4096 2008-08-26 23:40 ..
-rw-------  1 cullens cullens  13105863 2008-08-26 23:57 2008-08-23-18-04-15.019-VirtualBox-6492.log
-rw-------  1 cullens cullens 213626940 2008-08-26 23:57 2008-08-24-23-07-38.029-VirtualBox-9486.log
-rw-r--r--  1 cullens cullens      6363 2008-08-26 23:57 2.6.24.patch
-rw-r--r--  1 cullens cullens    364775 2008-08-26 23:56 84109-SigmaDock-v1.2.tar.gz
drwx------  2 cullens cullens      4096 2008-08-26 23:40 .adobe
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 Alcohol 120 v.1.9.6 full version+serial
-rw-r--r--  1 cullens cullens      3271 2008-08-26 23:56 Alcohol_120_v.1.9.6_full_version+serial.torrent
drwxr-xr-x 28 cullens cullens      4096 2008-08-26 23:57 alsa-driver-1.0.17
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:56 A Perfect Circle - Thirteenth Step (kibgdom Music by def)
drwx------  2 cullens cullens      4096 2008-08-26 23:56 .aptitude
-rw-------  1 cullens cullens      6000 2008-08-26 23:56 .bash_history
-rw-r--r--  1 cullens cullens       220 2008-08-26 23:57 .bash_logout
-rw-r--r--  1 cullens cullens      2940 2008-08-26 23:56 .bashrc
drwxr-xr-x  5 cullens cullens      4096 2008-08-26 23:56 .blender
-rw-r--r--  1 cullens cullens    114079 2008-08-26 23:56 C4_Bullriding_Poster.jpg
drwxr-xr-x  5 cullens cullens      4096 2008-08-26 23:56 .config
drwx------  2 cullens cullens      4096 2008-08-26 23:48 .dbus
-rw-r--r--  1 cullens cullens        58 2008-08-27 21:12 .DCOPserver_CullenLappy__0
lrwxrwxrwx  1 cullens cullens        40 2008-08-27 21:12 .DCOPserver_CullenLappy_:0 -> /home/cullens/.DCOPserver_CullenLappy__0
drwxr-xr-x  6 cullens cullens      4096 2008-08-26 23:56 Desktop
-rw-------  1 cullens cullens        26 2008-08-26 23:58 .dmrc
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:58 Documents
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:48 .dvdrip
-rw-r--r--  1 cullens cullens     25765 2008-08-26 23:56 .dvdriprc
drwxr-xr-x  4 cullens cullens      4096 2008-08-26 23:56 .emerald
drwx------  2 cullens cullens      4096 2008-08-26 23:57 .filezilla
drwxr-xr-x  2 cullens cullens      4096 2008-08-27 00:04 .fontconfig
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 .fonts
-rw-r--r--  1 cullens cullens       514 2008-08-26 23:56 .fonts.conf
drwx------  2 cullens cullens      4096 2008-08-27 21:14 .gconf
drwx------  2 cullens cullens      4096 2008-08-27 21:14 .gconfd
drwxr-xr-x 22 cullens cullens      4096 2008-08-26 23:58 .gimp-2.4
-rw-r-----  1 cullens cullens         0 2008-08-26 23:56 .gksu.lock
drwx------  3 cullens cullens      4096 2008-08-27 00:05 .gnome2
drwx------  2 cullens cullens      4096 2008-08-26 23:56 .gnome2_private
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 .gnome-mud
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:57 .gstreamer-0.10
-rw-r--r--  1 cullens cullens     25507 2008-08-26 23:56 .gtk_qt_engine_rc
-rw-r--r--  1 cullens cullens       285 2008-08-26 23:58 .gtkrc-2.0-kde
-rw-------  1 cullens cullens       199 2008-08-27 21:12 .ICEauthority
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:57 install_flash_player_9_linux
drwxr-xr-x  6 cullens cullens      4096 2008-08-26 23:56 kcometen3-1.1
drwx------  5 cullens cullens      4096 2008-08-27 00:04 .kde
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:57 kde icons
drwx------  2 cullens cullens      4096 2008-08-26 23:56 .kildclient
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:40 .kompozer
-rw-r-----  1 cullens cullens         6 2008-08-26 23:56 .ktorrent.lock
drwx------  3 cullens cullens      4096 2008-08-27 00:04 .local
drwx------  2 cullens cullens      4096 2008-08-26 23:58 .macromedia
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:57 .mcop
drwx------  4 cullens cullens      4096 2008-08-27 00:05 .mozilla
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 Music
drwxr-xr-x  5 cullens cullens      4096 2008-08-26 23:56 mystuff
drwx------  2 cullens cullens      4096 2008-08-26 23:40 .openoffice.org2
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:56 Pictures
-rw-r--r--  1 cullens cullens       586 2008-08-26 23:56 .profile
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 Public
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:40 .pulse
-rw-------  1 cullens cullens       256 2008-08-26 23:57 .pulse-cookie
drwxr-xr-x  2 cullens cullens      4096 2008-08-27 21:12 .qt
-rw-------  1 cullens cullens       330 2008-08-26 23:57 .recently-used
-rw-r--r--  1 cullens cullens       830 2008-08-26 23:56 .recently-used.xbel
drwxr-xr-x  5 cullens cullens      4096 2008-08-26 23:48 rtl8187b-modified
-rw-r--r--  1 cullens cullens   3724912 2008-08-26 23:40 rtl8187b-modified-dist.tar.gz
drwxr-xr-x  5 cullens cullens      4096 2008-08-26 23:48 SigmaDock-v1.2
drwx------  2 cullens cullens      4096 2008-08-26 23:56 .strigi
-rw-r--r--  1 cullens cullens         0 2008-08-26 23:57 .sudo_as_admin_successful
drwxr-xr-x  3 cullens cullens      4096 2008-08-26 23:40 .superkaramba
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:58 Templates
drwx------  3 cullens cullens      4096 2008-08-27 00:05 .thumbnails
-rw-r--r--  1 cullens cullens 651517952 2008-08-26 23:58 ubuntu-eee-8.04.1-RC.iso
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:57 Videos
drwxr-xr-x  4 cullens cullens      4096 2008-08-26 23:48 .VirtualBox
drwxr-xr-x  4 cullens cullens      4096 2008-08-26 23:40 .wine
-rw-------  1 cullens cullens        56 2008-08-27 21:12 .Xauthority
drwxr-xr-x  2 cullens cullens      4096 2008-08-26 23:56 .xine
-rw-r--r--  1 cullens cullens     10306 2008-08-26 23:56 .xscreensaver
-rw-------  1 cullens cullens      1362 2008-08-27 21:14 .xsession-errors

```

Don't know that much about permissions yet, so I'll let you gurus decipher that (and explain it, if you don't mind:p)

---

### Post by Elfy on 2008-08-28
When you say personal settings what ones are you tlaking about in particular?

---

### Post by Inane_Asylum on 2008-08-28
Superkaramba widgets, firefox bookmarks/history, quicklaunch bar, desktop background, things like that.  It basically looks like I created a new user...

If it's just a matter of setting all that again, then it's really no biggie.  I'm just making sure this isn't a small symptom of a bigger problem.

I'm gonna go in later after I get home and compare all the files in home and home_backup to see if there's any difference.  I guess that's my next step :/

---

### Post by Elfy on 2008-08-28
well I've ususally backed up ff bookmarks and e-mail myselfso don't know if copying wouldbe ok - more for the e-mail that one, I know that evolution complains. It could be that you'll need to but perhaps check it here on this thread [http://ubuntuforums.org/showthread.php?t=416802&page=8](http://ubuntuforums.org/showthread.php?t=416802&page=8) , I can't see aysiu having a problem with it.

Check the permissions between the two ```
ls -al
```

---

### Post by Inane_Asylum on 2008-08-28
Well, it turns out the files in some of my .folders didn't make it over to the new partition.

Would I be able to just go over to my home_backup folder and enter the "sudo find..." command, or do I have to use a liveCD, etc.?

---

### Post by Elfy on 2008-08-29
I don't think that there is a reason why moving them would be a problem - it owuldn't hurt to try anyway.

---

