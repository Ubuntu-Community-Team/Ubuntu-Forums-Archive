---
title: "Gedit on file in a sshfs'd folder"
date: 2008-10-08
forum: General Help
---

### Post by Jojan on 2008-10-08
I have a folder from UNIX system at school that I have sshfs'd to make it a folder at home. When I edit my code with Gedit and try to save, Gedit won't let me. It seems to be a bug. I have nog probelm copying files to my school folder. Gedit tells me I don't have the permission to save.

Is it a bug, or do I have to do something?

I noticed now that when I open from my terminal ([FONT="Courier New"]gedit folder/file[/FONT]) that it says that I don't have the persmission to open it, but I can open it when Gedit is allready running. I am allowed to open and save with nano, vim and emacs.

---

### Post by jerome1232 on 2008-10-08
I can't duplicate the problem I am however on Intrepid Alpha

I connected via Places->Connect to server->ssh, which mounts an sshfs connection on your desktop. Perhaps it's a bug with hardy, I'm going to go find my laptop it's running hardy and retest it.

gedit 2.24.0
OpenSSH_5.1p1 Debian-1ubuntu2
OpenSSL 0.9.8g 19 Oct 2007

---

### Post by jerome1232 on 2008-10-08
Okay I can confirm you problem on hardy, I'm guessing it's a bug with gedit since other text editor works fine

on hardy gedit is version 2.22.3

I would check backports to see if a newer version of gedit has been backported and file a bug against gedit.

---

### Post by Jojan on 2008-10-08
Thank you for confirming the bug.

I will backport then to get it to work.

---

### Post by Felix1983 on 2008-11-27
try mounting the remote folder with the command:

$ sshfs -o idmap=user USER(AT)MACHINE:FOLDER MOUNTFOLDER

---

### Post by Tharmas on 2009-10-30
> **Felix1983 said:**
> try mounting the remote folder with the command:

$ sshfs -o idmap=user USER(AT)MACHINE:FOLDER MOUNTFOLDER

Thanks. I guess this (kind of) works:
I can now save remote files in gedit, but ...
it only translates the user ID but not the group.

It should be possible according to the manual, although there is no option for group:
>        -o idmap=TYPE
              user/group ID mapping, possible types are:

               none   no translation of the ID space (default)

               user   only translate UID of connecting user



---

### Post by proycon on 2009-11-07
I all of a sudden have the very same problem, on Ubuntu Karmic. The cause seems to be the backup file, for some reason it refused to overwrite it, even though permissions were fine. Removing the backup file solved the problem.

---

### Post by dr20 on 2009-12-23
Problem for me too all of sudden. Backup file cannot be deleted.  Happens on emacs too but it continues regardless so it's not just a gedit problem.

---

### Post by dcstar on 2009-12-24
Remote filesystems are not all Linux compatible. NTFS cannot handle the hidden backup files Gedit creates. You cannot assume correct operation using Linux utilities on foreign filesystems.

Turn off the Gedit auto backup function and it will work.

---

### Post by m0ns00n on 2010-06-17
It's a gedit bug. It's *old*. Please, rid us of this annoyance! =)

---

### Post by eggdeng on 2010-06-17
Just to muddy the waters a bit more: I am having this problem on Lucid but not on Karmic. It does seem to be a gedit problem as I can edit & save OK with other editors. However, the problem persists in spite of backups being turned off in gedit. :confused:

Edit: Stranger and stranger. Turning _on_ automatic backups allows me to save.

---

### Post by marius311 on 2010-06-21
> **eggdeng said:**
> Edit: Stranger and stranger. Turning _on_ automatic backups allows me to save.

Same problem on Lucid, and turning on "create backup before saving" fixes it for me also. 

Bug report here: [https://bugs.launchpad.net/gedit/+bug/34813](https://bugs.launchpad.net/gedit/+bug/34813)

---

### Post by ennaj on 2010-07-10
> **dcstar said:**
> Turn off the Gedit auto backup function and it will work.

It was just the opposite (as explained in [this  post]("http://ubuntuforums.org/showpost.php?p=9248113&postcount=4") by headlessspider) that worked for me, too.

---

