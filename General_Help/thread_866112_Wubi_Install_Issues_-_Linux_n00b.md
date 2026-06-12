---
title: "Wubi Install Issues - Linux n00b"
date: 2008-07-21
forum: General Help
---

### Post by The Patched Fool on 2008-07-21
Good morning.

First, let me say I have no experience with Linux at all. But all of the Linux fanatics I know seem to adore Ubuntu, so I thought I'd install it on an external harddrive and give it a whirl.

Obviously, since I know no Linux, I failed dismally with the traditional Ubuntu install. It threw Error 5 - I/O Error - complaining about either a dead HDD, or a scratched/mis-burned disc.
The disc was sent out to me by Canonical, so I assume that's not the issue, and the exty harddrive is also brand new.

So I tried Wubi. Again, initially I tried installing to my external harddrive, but when it came time to reboot & actually install Ubuntu, it couldn't see the external harddrive.

Ok, I figured it might not like external harddrives (more likely an issue with my near-ancient mobo, I assume), and instead I tried to install to a folder on one of my internal SATA HDDs.

Reboot went fine, install was ok until it started detecting hardware, then it suddenly threw an error complaining about my eth0 (I'm assuming, since I'm not using wired networking, that it objects to my DLink wireless card) and refused to let me continue.


I don't have the logs for any of this, because I'm not game to reboot and start typing arcane Linux commands into a command line.

Can anyone offer any suggestions? Is there an easy way to install Linux? (I thought Wubi was it, but apparently I'm wrong.)

Did I miss something obvious? I'm quite happy to try the whole thing again, if someone can tell me what to look out for (so I can report it back).


Hope you can help, and I'm sorry for the long, rantish nature of the post.

---

### Post by ago on 2008-07-21
During linux-side installation, press ctrl+alt+f4 to see more message (shift+pgup to scroll), to get to a terminal ctrl+alt+f2, the relevant log is /var/log/syslog.

---

