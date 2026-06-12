---
title: "Synaptic Broken"
date: 2008-11-03
forum: General Help
---

### Post by pillu on 2008-11-03
Hi all,

I use Ubuntu 7.10 on a Lenovo centrino duo laptop. I tried to install a statistical package called [_Macanova_]("http://www.stat.umn.edu/macanova/") from its rpm using alien. The process exited with errors. Here is a listing from the terminal commands

> $ sudo alien -k --scripts macanova-5.05-1.i586.rpm 
macanova_5.05-1_i386.deb generated

$ sudo dpkg -i macanova_5.05-1_i386.deb 
(Reading database ... 163689 files and directories currently installed.)
Preparing to replace macanova 5.05-2 (using macanova_5.05-1_i386.deb) ...
Unpacking replacement macanova ...
[: 5: unexpected operator
rm: cannot remove `/bin/macanovacpc': No such file or directory
rm: cannot remove `/bin/macanova': No such file or directory
rmdir: /lib/macanova: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
[: 5: unexpected operator
rm: cannot remove `/bin/macanovacpc': No such file or directory
rm: cannot remove `/bin/macanova': No such file or directory
rmdir: /lib/macanova: No such file or directory
dpkg: error processing macanova_5.05-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
[: 5: unexpected operator
rm: cannot remove `/bin/macanovacpc': No such file or directory
rm: cannot remove `/bin/macanova': No such file or directory
rmdir: /lib/macanova: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 macanova_5.05-1_i386.deb


Now synaptic is broken. The error message I get is

> 'E:The package macanova needs to be reinstalled, but I can't find an archive for it.

I tried to force remove the macanova package. That didn't work either. The output of that command is

> $ sudo dpkg --remove --force-remove-reinstreq macanova
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 163688 files and directories currently installed.)
Removing macanova ...
[: 5: unexpected operator
rm: cannot remove `/bin/macanovacpc': No such file or directory
rm: cannot remove `/bin/macanova': No such file or directory
rmdir: /lib/macanova: No such file or directory
dpkg: error processing macanova (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 macanova


It seems that my synaptic is really screwed. How do I recover/reinstall synaptic and remove the darned macanova package?

Thanks a lot,
pillu

---

### Post by drs305 on 2008-11-03
It seems like you have tried the normal routes. Here is an option I use in these cases that often works - I remove the offending app listing from the status file. It isn't a clean solution but it has never caused me problems. (There is actually a system-created status-old that may be designed to restore screwed up systems, but usually by the time I've run all my other restoration steps the 'status-old' seems to be the same as the original.):
Rename old status file and open for editing:
```

sudo cp /var/lib/dpkg/status /var/log/dpkg/status.bak
gksudo gedit /var/lib/dpkg/status

```

Find the section containing the macanova information and delete it.
Save the file, then run your updates (sudo apt-get update).

If it doesn't work, restore things as they were:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status.bak /var/lib/dpkg/status

```

---

### Post by pillu on 2008-11-03
This solution worked! Though I think the correct path is /var/lib instead of /var/log
-pillu

---

### Post by drs305 on 2008-11-03
Yes, of course. I'll correct the original as well - glad it worked (with variations).

If you don't have any other issues would you please mark it solved via the Thread Tools link at the top right of the original post?

---

