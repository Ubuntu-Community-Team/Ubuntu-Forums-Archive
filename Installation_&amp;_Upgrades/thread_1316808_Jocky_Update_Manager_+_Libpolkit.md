---
title: "Jocky Update Manager + Libpolkit"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2009-11-06
Hello,

I've just installed Xubuntu to my computer and I can't remove/install programs or receive updates because of this error Update manager gives me:

"Preconfiguring packages ...
(reading database ...
dpkg: warning: files list file for package 'libpolkit-gobject-1-0' missing, assuming
package has no files currently installed.
(Reading database ... 10%dpkg: unrecoverable fatal error, aborting:
  unable to open files list file for package 'libpolkit-dbus2': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to Recover:"

And thats it... It doesn't do anything after that. Although I can't install/remove much Synaptec did let me reinstall libpolkit-gobect-1-0 and libpolkit-dbus2 but it didn't work.

Just before this though I was installing updates and it froze - so I restarted Xubuntu and it went into a maintainance shell so I retried booting with CTRL-D, that didn't work so I ran fsck with no parameters and It cleared out a lot and it Xubuntu booted up again without error but now this error is showing up so what can I do?

---

