---
title: "Ubuntu will not shut down when share is mounted(cifs)"
date: 2008-11-29
forum: General Help
---

### Post by _sAm_ on 2008-11-29
I can not shut down Ubuntu 8.10 if have mounted a share from a windows server(using cifs). It will hang almost before the shutdown is complete(hard reboot is the only solution). 
This happens _every_ time have tried.

Ubuntu will shut down as normal if I first unmount the share.

This is not a problem for me since I can unmount the share when I want(but I always forget to:-/ ), but want to know if this is a known bug or something?

---

### Post by _sAm_ on 2008-12-05
Time for a bump

---

### Post by doubled on 2008-12-07
Not sure what you mean by time for a bump, but the shutdown hang with mounted shares has been around since 8.04 and occurs on all other Ubuntu-based distros I've tried. It is not, however, on all Debian-based distros and does not afflict RPM distros.

The problem is that networking is shutting down before the shares are unmounted. In March 2008 I ran across what then was a solution, but which is no longer a solution. That solution was to go into /etc/rc6.d and /etc/rc0.d and change S31umountnfs.sh to S14umountnfs.sh. Theoretically, that should release the mounts prior to shutting down the network, but, as I say, it no longer works for me in 8.10 as it did in 8.04

Now there also appears to be an alsa-utils problem that has complicated the problem. I think the problems are multiple.

So, unfortunately, all I can tell you is that you are not alone.

---

