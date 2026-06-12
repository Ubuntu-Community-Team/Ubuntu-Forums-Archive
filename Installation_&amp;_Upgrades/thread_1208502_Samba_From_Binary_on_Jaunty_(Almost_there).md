---
title: "Samba From Binary on Jaunty (Almost there)"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Daimones on 2009-07-09
As the title states I am working on installing Samba from binary and have been having some issues, currently trying to install v3.0.35.

The configuring/compiling/making/installing all seems to run fine, but then there is no entry in /etc/init.d/ to start samba. So basically what I did was copy the file from another machine, and threw it in there and also copied the files that it referenced from that same machine. List of files copied:

/etc/init.d/samba
/etc/default/samba
/var/run/samba
/usr/sbin/nmbd 
/usr/sbin/smbd

Now when I try to start samba using /etc/init.d/samba it fails, with no error. Also testparm doesn't work, do I need to install an older version of that or can I just use the newest version via "sudo aptitude install samba-common"?

Any help would be appreciated, even if it's just a guess. 
Thanks in advance!

EDIT: This may be in the wrong place, I get the feeling this forum is just for Ubuntu-OS installs. If I am correct could a moderator move it to the correct place please?

---

### Post by madverb on 2009-07-09
How do you know it has failed if you don't get an error? Have you looked through the logs?

There should also be a walkthrough on how to compile samba on the samba site.

P.S. you installed it from source not binary. Just for future reference.

---

### Post by Daimones on 2009-07-09
Oops, I knew it was from source, I was discussing this in a different thread another guy started, which he had labeled from Binary, threw me off, hah.

I don't get an error message per say but I do get an error  "Starting Samba Daemon                [Fail]", I just meant that there was no description of what was going wrong saying what went wrong.

Wasn't sure which log it would be in exactly, tried to look through a few of them and found nothing referencing the fail.

---

