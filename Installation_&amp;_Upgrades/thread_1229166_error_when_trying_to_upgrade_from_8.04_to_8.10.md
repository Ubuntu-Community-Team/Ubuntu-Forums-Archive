---
title: "error when trying to upgrade from 8.04 to 8.10"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by sblok on 2009-08-01
I almost was finished upgrading from ver 8.04 to 8.10 when it asked for a CD - Ubuntuo 9.04_jauntjackalop--Releasei.386 (20090420.1)
I had the 9.04 CD, but the program didn't recognize it.  I hit cancel and it continued.  This happened twice.
Then it came up with an error saying  it failed to fetch
cdrom: Ubuntuo 9.04_jauntjackalop--Releasei.386 (20090420.1)/pool/main/f/fakeroot/fakeroot1.12.1ubuntul_i386.debcdrom: 
cdrom: Ubuntuo 9.04_jauntjackalop--Releasei.386 (20090420.1)/pool/main/p/patch/patch_2.5.9-5-i386.deb

What should I do?

thanks

---

### Post by slakkie on 2009-08-01
you have some kind of cdrom line in your sources.list, remove it.

Looks something like this (hardy cdrom in this case):
```

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ feisty main restricted

```

Just put a # at the start of the line, run sudo aptitude update afterwards. And then try to upgrade.

---

### Post by sblok on 2009-08-01
I found the cdrom in my sources.list, but it won''t let me save it.  It says permission denied, and doesn't give me an option to enter a password.

---

### Post by merlinus on 2009-08-01
Preface the command(s) with sudo, or gksudo if wanting to run a graphical app.

---

### Post by sblok on 2009-08-01
Thanks that worked.

I get a bit further in the upgrade "installing upgrades' and I got the following error:
IDL:omg.org/CORBA./COMM_FAILURE:1.0

Once the error was cleared, it is continuing to complete the upgrade.
Should I stop the upgrade? and try to correct the error?

---

### Post by merlinus on 2009-08-01
When you say "upgrade," exactly how are you doing this?  From a live cd, via the Internet, etc.

---

### Post by sblok on 2009-08-01
it was from the internet.

The upgrade finished and after I restarted the computer, all I get is a full screen in the terminal context.

It asked me for my user name then my passord, and the sits there waiting for another command.

I am only able to access the internet now when I reboot and go into windows.

---

### Post by merlinus on 2009-08-02
My suggestion is to do a fresh install of 8.10.

---

