---
title: "libc6-sparc64b Gutsy"
date: 2008-09-08
forum: General Help
---

### Post by boupartac on 2008-09-08
Hi all,

I just installed Ubuntu Gutsy on a Sun Fire T2000 and everything went well. I fired up the installation by typing "boot cdrom". When the system was installed, I did a usual "apt-get update" and "apt-get upgrade" to update the packages. It's a 16Gig RAM and 32 processors server.

Now, the server is setting up libc6-sparc64b and is stuck there:

> 
Setting up libc6-sparcv9b (2.6.1-1ubuntu10) ...
Setting up libc6-sparc64v (2.6.1-1ubuntu10) ...
Setting up libc6-sparc64b (2.6.1-1ubuntu10) ...


The load if 3.99 and when I do a "ps -aux | grep -i sparc":
> 
root      6997  0.0  0.0   5032  2576 pts/1    Ss+  12:15   0:00 /usr/bin/dpkg --status-fd 20 --configure libc6-sparcv9b libc6-sparc64v libc6-sparc64b libc6-sparc64 libc6-sparcv9v libdb4.4 perl perl-modules apt-utils python-apt linux-image-2.6.22-14-sparc64-smp linux-ubuntu-modules-2.6.22-14-sparc64-smp libbz2-1.0 bzip2 libssl0.9.8 python2.5 libgnutls13 libkrb53 libvolume-id0 volumeid udev libisc32 libdns32 libisccc30 libisccfg30 libbind9-30 liblwres30 bind9-host dnsutils rsync update-manager-core linux-restricted-modules-common linux-restricted-modules-2.6.22-14-sparc64-smp
root      7024  0.0  0.0   2128   704 pts/1    S+   12:15   0:00 /bin/sh /var/lib/dpkg/info/libc6-sparc64b.postinst configure 2.6.1-1ubuntu9
root      7029  0.0  0.0   2128   416 pts/1    S+   12:15   0:00 /bin/sh /var/lib/dpkg/info/libc6-sparc64b.postinst configure 2.6.1-1ubuntu9
root      7030  100  0.0   4624  2392 pts/1    R+   12:15 138:37 dpkg-query --list libc6-sparcv9b
root      7031  0.0  0.0   3368  1136 pts/1    S+   12:15   0:00 sed -e /^i/!d; -e s/^i.\s\+libc6-sparcv9b\s\+//;s/\s.*//g
apache    7302  0.0  0.0   3408  1152 pts/3    S+   14:33   0:00 grep -i sparc


Does anybody have any ideas of why it has been stuck for more than 2 hours?

Thanks,

boupartac

---

