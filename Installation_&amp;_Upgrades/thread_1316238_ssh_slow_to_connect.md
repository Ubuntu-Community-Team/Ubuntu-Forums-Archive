---
title: "ssh slow to connect"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by schuelaw on 2009-11-05
Karmic, i386, Thinkpad R52, ssh client takes a long time to connect to my work machine.  Here's verbose output of the command.  It hangs at the last line for what appears to be exactly 20 seconds and then proceeds normally with the connection.  I've disabled ipv6 at the kernel level, no change.  Server side accepts connections normally from other machines.  Tried setting UseDNS no in /etc/ssh/ssh_config, no change.

(mathlap1)~> ssh -vvv carrot.whitman.edu
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/schuelaw/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0

---

### Post by schuelaw on 2009-11-05
Solved it by setting:

AddressFamily inet

in /etc/ssh_config.

---

