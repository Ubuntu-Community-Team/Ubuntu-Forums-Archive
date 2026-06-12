---
title: "Can't log into GNOME (Solved)"
date: 2005-12-04
forum: General Help
---

### Post by Brunellus on 2005-12-04
**EDIT**:  PROBLEM NOW RESOLVED, thanks to the proper use of the search function. doh.

Solution:

had to chown .ICEauthority to me, using

$ sudo chown luigi .ICEauthority

Question now becomes:  I don't remember executing $ chown root .ICEauthority ....ever.  So how could the file ownership have changed, and how can I prevent this from happening in the future?


I'm trying to log into GNOME from GDM, but GDM returns this error:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "luigi"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/Funes:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/Funes:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/Funes:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8307): WARNING **: Unable to read ICE authority file: /home/luigi/.ICEauthority

```

Consulting google tells me I should work around this by renaming ~/.ICEauthority to something like ~/.ICEauthority.bak but I don't know how to do this from the console (man rename tells me I have to know perl to do this, and I wouldn't know perl from grit in an oyster).

Can anyone shed any light on this?

---

### Post by Iandefor on 2005-12-04
There's no dedicated "rename" function in linux (Perl aside) because mv does essentially the same job. for your application, it would be ```
mv .ICEauthority .ICEauthority.bak 
``` while you're in your home directory.

---

### Post by BobSongs on 2005-12-05
I've run into this problem 3 times now.

Golly. I wish I could pin it down to one thing I did. But there are so many changes I apply to the system.

I just got this the third time. And rather than reformatting and starting again I decided to see if anyone else ran into this.

I deleted the /home/bob/.ICEauthority file and I was able to log in again. Any ideas on what might make this file go weird?

Thanks.

---

### Post by smgil on 2005-12-05
I had that problem and it get solved changing owner to .ICEAuthority file.

```
chown <yourloginname> .ICEauthority
```

---

### Post by teaker1s on 2005-12-10
groans happened to me too

---

### Post by invalid on 2005-12-10
This is a known bug (it's on file, but I am too lazy to get the link, search bugzilla ;)

Anyhow, it is known to be caused when you run kde apps with sudo.
There also seems to be, but not documented yet, an package upgrade that somehow changes it (maybe running a config script for some kde app).

Cb

---

### Post by sudokubuntu on 2005-12-12
hey I can't get it to work either, but I sudo apt-get fluxbox so at least I have a desktop to work from

---

### Post by BobSongs on 2005-12-15
[QUOTE=invalid]This is a known bug (it's on file, but I am too lazy to get the link, search bugzilla ;)

Anyhow, it is known to be caused when you run kde apps with sudo.
There also seems to be, but not documented yet, an package upgrade that somehow changes it (maybe running a config script for some kde app).

Cb[/QUOTE]

Okayyyyy. That explains it. Thanks! I'll keep an eye out for that.

Bob

---

