---
title: "Filesystem Over FTP"
date: 2008-10-10
forum: General Help
---

### Post by solarwind on 2008-10-10
What's the best way to mount a remote FTP server as a local filesystem in Linux?

---

### Post by -Zeus- on 2008-10-10
Places > Connect to Server.  It won't mount as a filesystem though, but as a folder in nautilus.

---

### Post by solarwind on 2008-10-10
> **-Zeus- said:**
> Places > Connect to Server.  It won't mount as a filesystem though, but as a folder in nautilus.

But I can still use as a filesystem? Like, play videos with VLC as if they were on my hard drive?

---

### Post by Mister.Vash on 2008-10-11
You could use fuse.  Here is an example:


If using Nautilus works as -Zeus- suggested, that will probably be the quickest and easiest way to do it.  If some of your applications don't work, take a look at fuse.  I've had issues with vlc and other applications being able to access files via the nautilus mounts - Using fuse is a little more in depth than just using nautilus, so try nautilus first, if that doesn't work, take a look here for an example of settings it up. [http://linux.byexamples.com/archives/344/mounting-ftp-host-to-local-directory-on-top-of-fuse/](http://linux.byexamples.com/archives/344/mounting-ftp-host-to-local-directory-on-top-of-fuse/)

It was the First guide I ran across, looked decent, I'm sure if needed more help than that you could find it on the forums here.

---

