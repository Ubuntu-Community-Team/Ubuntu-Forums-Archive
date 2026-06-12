---
title: "apt-get: not found"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-02-26
I'm in the command shell of the alternate installer (8.10 AMD64) trying to fix some problems. I need to run blkid, but it isn't available. So I need to install it.

But when I try to install it, this is what I get:
```
/bin/sh: apt-get: not found
```

How should I proceed? Thanks.

---

### Post by smani on 2009-02-26
Try with the full-path: /usr/bin/apt-get. Strange though,seems that your PATH environment variable is missing or similar, does
```
echo $PATH
```
display anything?

---

### Post by Simian Man on 2009-02-26
[LIST=1]
[*]Check your PATH environment varaible with 'echo $PATH'
[*]Check for apt-get in /usr/bin, /bin, and /sbin (I'm not sure where it should be) with 'ls /usr/bin | grep apt'
[*]I see you are using sh where the default shell is bash.  Try running 'bash' then enter the apt-get command and see if bash has it in the path.
[/LIST]

---

### Post by MountainX on 2009-02-26
PATH is
/sbin:/usr/sbin:/bin:/usr/bin

when I type "apt" followed by tab, here is what I get:
apt-install
apt-setup
apt-setup-verify
apt-setup-signed-release

apt-install is found in
/bin/
/var/lib/

apt-setup is found in 
/usr/lib/
/usr/bin/
/usr/share/


BTW, I'm in the installer shell - the default (and only choice?) is /bin/sh

---

