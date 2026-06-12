---
title: "DEB packages install error - need a fix"
date: 2008-11-30
forum: General Help
---

### Post by TheForkOfJustice on 2008-11-30
I recently tried to install Care2x using the DEB files they offer on their website [https://sourceforge.net/project/showfiles.php?group_id=53886&package_id=133412](https://sourceforge.net/project/showfiles.php?group_id=53886&package_id=133412)

It only half-installed (I have no idea as to why) so I decided to uninstall but it wouldn't do so properly, giving me output like this:

> 
dpkg: error processing care2x (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 care2x
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.


I removed all of the files it installed (to my knowledge they were in these directories)

/var/www/care
/usr/share/doc/care2x

and I also removed the postinst and related scripts in /var/lib/dpkg

The files may be gone now but I still get the error.  It keeps asking for the original package but I deleted it and downloading a new package didn't help at all.  Using aptitude to remove it didn't work and this error is preventing me from using Synaptic.

Any idea on how to get rid of the error now?

---

### Post by fragos on 2008-11-30
Run "sudo dpkg --purge care2x" and see what it says. Removing files can be a risky action.

---

### Post by TheForkOfJustice on 2008-12-01
> **fragos said:**
> Run "sudo dpkg --purge care2x" and see what it says. Removing files can be a risky action.

I already removed everything and even apt is behaving now.  It checked for updates via the Update Manager and after that was done apt began working again.

I'll remember that command if I attempt to install the package again.

---

