---
title: "weirdness with ssh client on 10.04 LTS laptop install"
date: 2011-11-19
forum: Hardware
---

### Post by MakOwner on 2011-11-19
I recently installed an Ubuntu server.

I was doing some setup and was doing some quick login, change parms and reboots via ssh from my laptop.

After the last time, I can no longer login via ssh - I can't find any logs on the laptop or the server as to why the login isn't working.

ssh debug looks like this:

$ ssh -vvv pe8502
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to pe8502 [192.168.20.42] port 22.
debug1: connect to address 192.168.20.42 port 22: Connection timed out
ssh: connect to host pe8502 port 22: Connection timed out

This is using the wireless connection from my laptop.
The wired connection works fine, and I can ssh into another server from the laptop, then into the server fine -- so it's only the conneciton directly from the wireless interface to the serve that's the issue.

Can anyone point me where to look to solve this?

---

