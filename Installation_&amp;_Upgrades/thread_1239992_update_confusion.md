---
title: "update confusion"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by beacon on 2009-08-14
I have had a notice in the task bar that updates are available, and I can't get rid of it. I want to update, but there are always two problems. The first is a message       'failed to detect distribution'. Then there is a warning about unauthenticated programs. Finally, the following: 

                                 [LEFT]GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BEFailed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/deb-src/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/deb-src/binary-i386/Packages)  404 Not Found[/LEFT]
    [LEFT]Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/binary-i386/Packages)  404 Not Found[/LEFT]
    [LEFT]Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/karmic/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/karmic/binary-i386/Packages)  404 Not Found[/LEFT]
    [LEFT]Some index files failed to download, they have been ignored, or old ones used instead.


I am utterly confused and would appreciate any advice or help.


Thanks
[/LEFT]

---

### Post by dai_bach on 2009-08-14
I notice that the error message refers to the Karmic release, but your user information has you down as using Jaunty.  You might want to check the corresponding lines of your /etc/apt/sources.list...

I don't know if that has anything to do with the problems you're having, mind you.  I'm having almost exactly the same issue.

---

### Post by dai_bach on 2009-08-14
I've just found the following post which might help

[http://ubuntuforums.org/showthread.php?t=1239561&highlight=launchpad.net+public+key](http://ubuntuforums.org/showthread.php?t=1239561&highlight=launchpad.net+public+key)

The problem appeas to be that we need to download the corresponding public keys.

---

### Post by dai_bach on 2009-08-14
...however the keyserver.ubuntu.com appears to be down.

[http://ubuntuforums.org/showthread.php?t=1059892](http://ubuntuforums.org/showthread.php?t=1059892)

---

### Post by beacon on 2009-08-16
Thanks very much dai_bach. I checked the sources and removed any reference to Karmic. (I don't know how they got there.) Anyway, that seems to have done the job at least on a temporary basis, so I won't worry about the key unless there is another problem.

---

