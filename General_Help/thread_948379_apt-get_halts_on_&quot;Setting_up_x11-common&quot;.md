---
title: "apt-get halts on &quot;Setting up x11-common&quot;"
date: 2008-10-15
forum: General Help
---

### Post by frode1 on 2008-10-15
Hello,

The root of this problem was me trying to enable syntax highlighting in vim. I'm working remotely on a server running Ubuntu 8.04.

I started by running "apt-get install vim-runtime". This appeared to go well up until a certain point, some 24mb were downloaded, and some packages were unpacked. Next, however, apt-get would stop on "Setting up x11-common (1:7.3+10ubuntu10.2) ..."

I can press Ctrl-c, in which case I get the following message before apt-get exits:
> dpkg: error processing x11-common (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 x11-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now it appears that apt-get will not install anything anymore. It always halts after the "Setting up x11-common" message.

Additionally, although I don't know if it's related in any way, I get lots of "4gb seg fixup, process xyz" messages in dmesg and /var/log/messages (where xyz is everything from httpd to sshd and pager).

Any clues?

--
Frode

---

