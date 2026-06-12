---
title: "partimaged seg faulting"
date: 2005-11-25
forum: General Help
---

### Post by peterx14 on 2005-11-25
Hi all,

When I **sudo partimaged**, it starts up fine, but seg faults when a partimage client connects (it shows them as connected, and then immediately terminates).

I have tried adding my own user name and root to the partimagedusers file, and I've also chown/chgrp'ed it so that the user partimag is the owner and group of that file (**man partimagedusers** indicated that this should be the case).
None of this helps though!

I also set a root password using **sudo passwd root** since I *believe* Ubuntu gives root a random password (I'm unclear how sudo works with this arrangement... but I'm happy to accept that it *does *work :D  ) so I thought that maybe using username and password I enter in the partimage client wasn't valid in Ubuntu.
Anyway.... that didn't help either!

The only way I've been able to get it to work is by booting using a Knoppix CD and running partimaged from that.

Both the client (partimage) and the server (partimaged) are running the same version (0.6.4 I think). The client is running from a Knoppix CD. The server is Ubuntu 5.10.

Any ideas?
-- 
TIA, Peter.

---

### Post by peterx14 on 2005-12-03
I'm still at a loss!

I did find [this bug (Debian #339745)](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=339745) which sounds very like my symptoms, so I:

[LIST=1]
[*]completely-uninstalled and then reinstalled the partimage-server package,
[*]re-disabled my root account password using **sudo passwd -l root** [(I'd read that Ubuntu prefers the root account disabled)](https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d)
[*]added the **partimag** user to the **shadow** group using **sudo addgroup partimag shadow**
[/LIST]
but that didn't work either! I've since played with re-enabling my root account by giving it a password (as I did previously), and adding the root user to the shadow group. Again, all to no avail. :(

Can *anyone* suggest how I sould proceed here, or am I best just waiting for the package maintainers to spot a problem?

---

### Post by Ruskie on 2006-01-02
just a quick note to point that I have the same problem. Client is partimage 0.6.4 on Gentoo Linux (the one in System Rescue CD), server is partimaged 0.6.4 on Kubuntu 5.10.

As soon as server detects connection, it writes it to the screen and then goes in segmentation fault.

---

### Post by peterx14 on 2006-01-04
I didn't manage to get any further with it myself, despite my best efforts! It *appears* to me that partimage is not really being supported anymore, so I'm inclined towards finding an alternative. I haven't settled on anything just yet, but [this usenet thread did have a few pointers for partimage alternatives](http://groups.google.com/group/linux.debian.user/browse_thread/thread/3e00e145203ad15/4242bf0f1372bb03?lnk=st&q=partimage&rnum=7&hl=en#4242bf0f1372bb03).

The job I needed to do at the time, I managed to do by booting the server using a Knoppix CD, mounting the HD for RW and running the partimaged server that way.

HTH!! :)

---

### Post by Ruskie on 2006-01-06
I switched, instead, to g4u. I prefered partimage because it did not require an ftp server, but g4u works, and works good. :)

---

