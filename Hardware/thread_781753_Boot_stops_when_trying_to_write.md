---
title: "Boot stops when trying to write"
date: 2008-05-04
forum: Hardware
---

### Post by helixness on 2008-05-04
Hi, i've been searching on the forums and found a few threads but none helped even though the issues were similar, and no one could help on IRC so I decided to post and be a little more patient.

So what happened is that I reinstalled Ubuntu over my old one (by formating before of course) to have a nice new installation, so after rebooting from the CD after installation I added all my favorite programs, codecs, web server etc... I then went out for diner, came back and finished a little config on Evolution and there were also 2 updates to install and so I did.

I then decided to reboot to apply some changes, but my boot just stops at 2-3 bars and half... so I did alt f3 trying to see what application might be stoping the boot, and seems to be different every time, one time it would stop at something about my webcam, the other time at ndiswrapper. I just to do ctrl+alt+del to continue but then respawns and just reboots my computer.

So What i tried doing to solve was:

1 - Rebooting into recovery mode and try in root: apt-get remove ndiswrapper (which i suspected to cause my problem), but the output to this is that I haven't unlock /var/lib/dpkg/lock because it is a read-only file. I also noted that i cannot edit any files on my system even in root because It replies that it is a READ ONLY filesystem...

2 - fsck which was suggested in other threads but that did nothing but return CLEAN.

Any ideas and suggestions about what's going on?
I greatly appreciate your help, I do need my computer asap to finish a website project due tomorrow....

Thanks again, Helix.

PS: Using my windows partition right now.

PPS: Oh and I forgot specifying that I have a shared partition between ubuntu and windows, could that be the cause to my problem as I am reading right now on this thread: [http://ubuntuforums.org/showthread.php?t=181903](http://ubuntuforums.org/showthread.php?t=181903)

---

