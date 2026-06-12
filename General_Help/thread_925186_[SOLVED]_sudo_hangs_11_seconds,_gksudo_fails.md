---
title: "[SOLVED] sudo hangs 11 seconds, gksudo fails"
date: 2008-09-20
forum: General Help
---

### Post by artships on 2008-09-20
We've seen the gksudo error before:
```
bash > gksudo -d echo hi
No ask_pass set, using default!
xauth: /tmp/libgksu-2sr5I4/.Xauthority
STARTUP_ID: gksudo/echo 'hi'/6014-0-serenity_TIME1973577
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: echo
cmd[9]: hi
buffer: --
buffer: --
buffer: --

<lots more "buffer: --" lines until...>

buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.

```

And that's it.  "sudo echo hi" solicits a password after an 11 second pause.  Of course, once "sudo" succeeds, subsequent executions still take 11 seconds to succeed, and as does gksudo.

It just started doing this a couple of days ago, as a result of no known changes to my Hardy system.  So, Why does sudo imagine dozens of carriage returns after a command, or has some system file suffered a grossly inconvenient modification?

---

### Post by artships on 2008-09-22
The hint was here:

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234879](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234879)

The bug is about there not being an entry for localhost in /etc/hosts.  Well, it was there, on the first line, BUT it was more than 256 characters in on that line.  Why was the line so big?  I was using it to filter-out adverts in web pages.  Used to I could have multiple 127.0.0.1 lines, until the latest or next-to-latest Opera release.  For Opera there could only be one 127.0.0.1 line, so mine was very long.

I also had my system name "mysystem", listed twice, once next to 127.0.0.1 and again after 192.168.1.150.  Took the system name off of the 127.0.0.1 line.

---

### Post by Timmah06 on 2012-05-23
I know this is an old thread.. but it's high up in the google results, and didn't quite get me to a fix.

I encountered this exact same issue on Ubuntu 12.04.  I had changed my hostname in /etc/hostname, but didn't update the localhost entry in /etc/hosts.  [Whoops!]

The fix, of course, was to replace my old hostname with the new one in /etc/hosts.  

Thanks for the start, artships!  It was very helpful, even almost 4 years later

---

