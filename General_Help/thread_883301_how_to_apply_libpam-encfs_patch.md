---
title: "how to apply libpam-encfs patch?"
date: 2008-08-07
forum: General Help
---

### Post by yaph on 2008-08-07
I'm currently locked out of my Hardy system due to a bug I discover was reported 4 months ago!
[INDENT][https://bugs.launchpad.net/ubuntu/+source/libpam-encfs/+bug/205783](https://bugs.launchpad.net/ubuntu/+source/libpam-encfs/+bug/205783)
[/INDENT]
A couple of people have offered patched packages (PPAs)
[LIST][https://launchpad.net/~rrenomeron/+archive](https://launchpad.net/~rrenomeron/+archive) (libpam-encfs - 0.1.4.1-2~ppa1)
[/LIST][LIST][https://launchpad.net/~andrearatto/+archive](https://launchpad.net/~andrearatto/+archive) (libpam-encfs - 0.1.4.1-3~ppa1 and libpam-encfs - 0.1.4.2-3~ppa1)
[/LIST]
but when I do apt-get update and apt-get upgrade the libpam-encfs package isn't shown as being due for upgrade. The version I have currently installed is 0.1.4.1-2. Shouldn't either of these PPA versions take precedence? Is it something I have to get apt-get to do explicitly?

Failing that there's a makefile patch listed at [http://launchpadlibrarian.net/12832602/libpam-encfs-Makefile.patch](http://launchpadlibrarian.net/12832602/libpam-encfs-Makefile.patch)
How would I use that? Presumably I have to download the sources, run some command to apply the patch, and then compile and install the libpam-encfs program?

Any help appreciated

---

### Post by damoxc on 2008-08-07
You could download the deb from the archive and then install it via dpkg:
```
wget http://launchpadlibrarian.net/14866523/libpam-encfs_0.1.4.1-3%7Eppa1_i386.deb
dpkg -i libpam-encfs_0.1.4.1-3~ppa1_i386.deb
```

That will replace the current copy.

---

### Post by yaph on 2008-08-07
OK I found a way:

[LIST]
edited /etc/pam.d/common-auth to revert to pre-encfs config and was able to login again
[/LIST][LIST]
then ran Adept 
[LIST]in Manage Repositories I found that the deb [http://ppa.launchpad.net/andrearatto/ubuntu](http://ppa.launchpad.net/andrearatto/ubuntu) ... lines were greyed out
[/LIST][LIST]right-click -> Enable
[/LIST]
then I was able to update & upgrade to get the patched version
[/LIST][LIST]
changed /etc/pam.d/common-auth again and it all works OK now!
[/LIST]

However I think there must be a way of doing at the command line  whatever the Adept right-click->Enable did - can anyone say what?

---

### Post by yaph on 2008-08-07
Oh, and WTF is Ubuntu doing shipping something that will seriously break things for some of its users, months after a patch has been available?

I really like libpam-encfs: I have it on my laptop and it gives me the reassurance that if the laptop gets stolen or breaks and has to go for repair my personal data is private. Not that it's military secrets or bank credentials in the plain or kiddie porn or anything, but it's my data and I don't want anyone else poking around in it. Since laptops do get stolen and data on them probably does get misused that's a big factor I'd use to 'sell' ubuntu + libpam-encfs to a reasonably security conscious friend or relative (or anyone else if they were paying me, should I be so lucky!).

However for a bug of this severity to be allowed to ship at all, let alone go uncorrected so long after it's potentially been fixed, makes me think twice about it.

---

