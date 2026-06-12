---
title: "Intrepid mini installation getting stuck.."
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by strife242 on 2009-03-22
Hello,

Just trying to install the 8.10 mini install fresh on a system.

Pretty much everything goes through but I've been waiting an hour now for the extra packages to install, and the only thing I marked for installation was OpenSSH. Now I don't believe this should take that long..

It seems the installation get stuck in the GUI "Select and install software" meter at 2% and a nice little note that say "please wait".

When switching to tty2 and tty3 I see BusyBox consoles and tty4 seems to indicate updates to the system.. except the same entry reappears every time.

It has gone up to:

in-target: Get:100 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main perl-base 5.10.0-11.1ubuntu2.2 [874kB]

and still rising...

So, what can I do now?

Any way to abort the security updates for now and complete installation?

Or can I just remove the install CD and reboot, then fix this manually?

ctrl+c doesn't seem to work, it just restarts again.

---

### Post by strife242 on 2009-03-22
Turned out to be my firewall...

what can I say.. oops? :D

---

