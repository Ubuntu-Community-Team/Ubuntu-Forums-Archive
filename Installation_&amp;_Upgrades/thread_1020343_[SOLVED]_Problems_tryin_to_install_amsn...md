---
title: "[SOLVED] Problems tryin to install amsn.."
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by MrJoeyUK on 2008-12-24
Ok so I'm trying to install amsn. I'm using Hardy Heron.. anyway,

Synaptic gives me the following...

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tcl8.5/tcl8.5_8.5.0-2ubuntu1_i386.deb
  Could not resolve ‘proxy’


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2_2.2.10-dfsg1-5_i386.deb
  Could not resolve ‘proxy’


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0.dfsg-6_i386.deb
  Could not resolve ‘proxy’


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/t/tk8.5/tk8.5_8.5.0-3_i386.deb
  Could not resolve ‘proxy’


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97+final-0ubuntu5.1_i386.deb
  Could not resolve ‘proxy’

```

And the terminal also unfortunately gives me the following..

```
joe@joe-laptop:~$ sudo apt-get install amsn
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
joe@joe-laptop:~$


```

Any help here would be greatly appreciated, thanks.

---

### Post by MrJoeyUK on 2008-12-24
Nevermind, worked it out.. I had a closer look at the terminal output and looked at the process bit, closed synaptic, tried again in terminal and wala, it worked.

---

### Post by scragar on 2008-12-24
Are you using a proxy server?

It's not working from the command line because you still have synaptic open.

---

