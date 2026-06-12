---
title: "Tomboy-sshfs file permissions (world writable files)"
date: 2008-09-05
forum: General Help
---

### Post by gaussian on 2008-09-05
I am trying to figure out the following:

I just started using Tomboy few weeks ago, syncing with my university's Linux server using sshfs so my files are kept in sync over three different computers. This morning I received an auto-generated email from the server's security scan complaining about world writable files. That is correct, my Tomboy-directory is world writable on the server and any new notes that I create are world writable. This is true even after having resetted the permissions of the directory and all the existing Tomboy-files on the server.

Anyone know how to fix this (maybe a configuration file somewhere for either sshfs/fuse or tomboy)? I doubt Tomboy passes any parameters setting permissions to fuse, so maybe there could be a default fuse setting somewhere?

Alternatively I could just start a Cron-job to reset the permissions every hour. But that is not an elegant solution.

Update: This seems to be known feature request [http://bugzilla.gnome.org/show_bug.cgi?id=522426](http://bugzilla.gnome.org/show_bug.cgi?id=522426)

---

