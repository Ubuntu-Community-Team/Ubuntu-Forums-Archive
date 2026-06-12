---
title: "xsession errors, can't login to gnome!"
date: 2005-11-27
forum: General Help
---

### Post by starfleetcaptainrob on 2005-11-27
Hi there, bear with me as I am a Linux noob.  I'm trying my hardest at learning this stuff, but Windows is so embedded into my brain it's slow going.  I'm not exactly sure what I did but can't login to gnome anymore.  It tells me I've been logged in for less than 10 seconds and that there is either an error or I'm out of  disk space.  I know I'm not out of disk space.  I've copied down my xsession errors below, but I'm having a difficult time trying to figure them out and was hoping some of the wonderful folks here could help!

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "fredbear"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/robert:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/robert:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/robert:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9332): WARNING **: Unable to read ICE authority file: /home/fredbear/.ICEauthority
```

I can login to terminal right now still, but that's about it.  Any help would be greatly appreciated!

---

### Post by invalid on 2005-11-27
Try
```
sudo chmod 644 ~/.ICEauthority
```

Cb

---

### Post by sugarat on 2005-11-28
Hi,

 I've just installed Ubuntu and have the same problem.  .ICEauthority belongs to me and has rw permissions. I've even tried deleting it but I still can't login to Ubuntu or do anything. 

 Doing a little searching it seems that a lot of people have had this problem, which is surprising for such a popular distro as Ubuntu. 

 How can this be fixed!?

---

### Post by starfleetcaptainrob on 2005-11-28
> Try
Code:

sudo chmod 644 ~/.ICEauthority


Cb

I gave the above a try and it did nothing.  Terminal just went to another line and I still can't login.

---

### Post by starfleetcaptainrob on 2005-11-28
Nevermind, I'm back in!  After using a different set of search parameters in the forums here I found this solution just incase anyone else comes to this thread looking for a solution:

[http://www.ubuntuforums.org/showthread.php?t=73961&highlight=ICE+authority]("http://www.ubuntuforums.org/showthread.php?t=73961&highlight=ICE+authority")

Thanks for the help!

---

