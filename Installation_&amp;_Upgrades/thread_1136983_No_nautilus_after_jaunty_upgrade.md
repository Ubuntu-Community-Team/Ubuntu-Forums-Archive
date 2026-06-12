---
title: "No nautilus after jaunty upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by albertjvm on 2009-04-25
The title pretty much says it all, after upgrading 9.04, I've got no nautilus. no icons on the desktop and I can't open a nautilus window. 

Any ideas?

---

### Post by reswob on 2009-04-25
I have the same problem.  I did a straight upgrade and had so many problems, I did a fresh install.  Most of my problems disappeared but I still have this one.

Why for no nautilus?

---

### Post by reswob on 2009-04-25
OK, I checked the log and here is the entries:

Apr 25 22:40:31 Joshua syslogd 1.5.0#5ubuntu3: restart.
Apr 25 22:48:28 Joshua kernel: [ 1096.688608] nautilus[4350]: segfault at 928f000 ip b58fa7dd sp b58e8fc0 error 4 in libbrasero-media.so.0.1.1[b58ea000+1e000]
Apr 25 22:51:23 Joshua kernel: [ 1271.137516] nautilus-file-m[4476]: segfault at 92e8000 ip b63b27dd sp b635ffc0 error 4 in libbrasero-media.so.0.1.1[b63a2000+1e000]
Apr 25 22:56:26 Joshua kernel: [ 1574.083054] nautilus[4486]: segfault at 99fb000 ip b5a227dd sp b5a10fc0 error 4 in libbrasero-media.so.0.1.1[b5a12000+1e000]
Apr 25 22:56:53 Joshua kernel: [ 1601.124767] nautilus[4490]: segfault at a06f008 ip b59857dd sp b5973fc0 error 4 in libbrasero-media.so.0.1.1[b5975000+1e000]

Now what?

---

### Post by SimonM on 2009-04-26
I've got the same problem. Any suggestions or should I consider a clean upgrade?

---

### Post by ssam on 2009-04-26
can you try running update manager and checking you are completely up to date. there are a few bugs in launchpad about libbrasero crashing nuatilus, but they are all marked as fixed.

if you are up to date could you file a bug. see [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash) for how to get a back trace.

---

### Post by reswob on 2009-04-26
I checked update manager and I'm completely up to date.

When I try to set up the debugging program, I get the following error when I try to import the debug symbol archive signing key.  Any idea of how to fix this?


> sudo gpg --keyserver keyserver.ubuntu.com --recv-key 428D7C01 5E0577F2
gpg: WARNING: unsafe ownership on configuration file `/home/craig/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

BTW, I installed Krusader and that works just fine, but without Nautilus, I cannot use my desktop.

Craig

---

### Post by reswob on 2009-04-26
I found that someone has reported a bug regarding this error.  It's #355986.

Also, I should say what my configuration is set at.

I have three partitions.  The first is EXT4 and the second is EXT3 and the third is SWAP.  Ubuntu is installed on the first partition.  My data is on the second.

Could this be an issue with EXT4?

---

### Post by reswob on 2009-04-27
OH MY GOSH!  My fix is so simple it's scary.

I had a CD in the second drive.  I removed it.  Nautilus worked.  Kind of.  I still can't copy a file to the desktop

I was going through the suggested fixes in this thread:  [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=844990](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=844990)

This HAS to be some kind of bug.  

More testing another night....

---

### Post by reswob on 2009-04-29
OK, I've verified that I have full desktop and folder functionality.

Still not sure why this caused so many problems...

---

