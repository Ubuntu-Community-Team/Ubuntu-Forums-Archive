---
title: "Need help with Tomboy issue"
date: 2008-09-26
forum: General Help
---

### Post by jakev383 on 2008-09-26
I have Tomboy installed from the repo, and I believe all the packages needed for it to work with WebDAV (wdfs, neon, etc).
I have Tomboy running on my dekstop, using Gutsy. It works fine. I can sync my notes to my own webdav that I run. I used to have Gutsy installed on my laptop, and could sync there as well just fine.
I did a fresh install of Hardy on my laptop. When I set up the sync to use webdav/fuse, I enter all the information as it shows on my desktop.  Upon clicking "Save", I get the following error:
Saving configuration to the GNOME keyring failed with the following message:
Unknown error

Does anyone know what the cause may be, or a fix?
Thanks!

---

### Post by jakev383 on 2008-09-26
Tried again while watching the logs. Said it was missing sshfs (even though I'm not using it, so I installed it). Here's what the logs show when they fail:
```

9/26/2008 7:32:52 PM [DEBUG]: Mounting sync path with this command: /usr/local/bin/wdfs /home/jake/.tomboy/sync-wdfs -a http://jake.mydomain.com:5600/tomboy/ -u jake -p ***** -o fsname=tomboywdfs
9/26/2008 7:32:52 PM [WARN]: Saving configuration to the GNOME keyring failed with the following message: Unknown error

```
I run my web server on a non standard port in case you're wondering.

---

### Post by jakev383 on 2008-09-26
Seems there's a bug with the version that ships with 8.04:
[http://bugzilla.gnome.org/show_bug.cgi?id=499841](http://bugzilla.gnome.org/show_bug.cgi?id=499841)
The patch instructions are on there, but I figured since I had to recompile from source I might as well install the new version (0.13.0 at the time of this).
I got the latest svn source, and installed some deps then installed it:
```

svn co http://svn.gnome.org/svn/tomboy/trunk tomboy
sudo apt-get build-dep tomboy
sudo apt-get install gnome-common
cd tomboy
./autogen.sh --prefix=/opt/apps/tomboy --disable-scrollkeeper
make
sudo make install

```

Hope that helps someone else out.

---

