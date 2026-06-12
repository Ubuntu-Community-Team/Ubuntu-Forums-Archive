---
title: "SFTP Permissions Issue - username vs UID"
date: 2008-10-17
forum: General Help
---

### Post by IMSargon on 2008-10-17
The issue sounds so simple, but I can't think of a fix.

I've got an chrooted sftp setup just how I want it, using OpenSSH's ChrootDirectory and internal-sftp features.
[http://adamsworld.name/chrootjail5.php](http://adamsworld.name/chrootjail5.php)

My problem is that if I try to log into this setup using Ubuntu's "Connect to Server..." dialogue, I do not have write access despite owning the files. The properties for one such folder reveal that it is owned by 1001 - the user id of the user I logged into the server as. 

Interestingly, if I ssh into the server and set the permissions of some folders to 777, I am able to create a subfolder from Gnome but do not have write permissions in the folder I just created!

If I use sftp from the command line, everything works great. 

Any guesses? I can make any necessary changes on the client side or the server side.

---

### Post by IMSargon on 2008-10-17
This bug sound like my problem:
[http://myt.ag/URLWeb.aspx?email=steve%40fooworks.com&url=http%3a%2f%2fbugzilla.gnome.org%2fshow_bug.cgi%3fid%3d346676&sn=](http://myt.ag/URLWeb.aspx?email=steve%40fooworks.com&url=http%3a%2f%2fbugzilla.gnome.org%2fshow_bug.cgi%3fid%3d346676&sn=)
[http://osdir.com/ml/gnome.vfs.general/2006-07/msg00024.html](http://osdir.com/ml/gnome.vfs.general/2006-07/msg00024.html)

However, they are quite old - these posts are from 2006. Am I facing a very old unfixed bug or is something else at work here?

---

### Post by IMSargon on 2008-10-17
I have replicated this problem on a desktop install. After logging in I am unable to write to the folders, despite owning them. 

Difference in this case are that the host is localhost (and thus the UIDs for users would match) and under permissions the correct username is shown, rather than the UID number.

I hope there's some expert out there for whom this clarifies the issue.

Edit:

Next I installed FileZilla. This program works properly with my folders and files. This really seems to be a problem with Gnome/Nautilus/underlying subsystems on the client side.

Edit:

Sure looks like this bug - [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/229270](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/229270)

---

### Post by beetlejuice_masterson on 2009-01-10
I'm having the same problem with gedit over sftp.  All files are opening as read only despite the fact that i'm logged in as root.  gedit 2.22.3 works fine w/sftp, but 2.24 which i've got completely sucks.  Anybody know what's going on w/this?  I assume it's a bug.

---

### Post by oraknabo on 2009-02-06
I just described essentially the same problem [here]("http://ubuntuforums.org/showthread.php?t=1051775") I wasn't having this issue at all on a different laptop running Hardy, but I've had it ever since setting up a new one on Ibex.

This is making it impossible for me to add new files and folders on the remote machine, even connected as root, unless I make them on my desktop and then drag them in.

It's also making any attempt to edit remote files with gedit impossible.

---

