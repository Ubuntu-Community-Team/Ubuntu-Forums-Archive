---
title: "openssh-server gone wrong.."
date: 2008-09-06
forum: General Help
---

### Post by buggiz on 2008-09-06
so.. some time ago I did a "apt-get upgrade" and my openssh-server wanted to be upgraded, so I went to have a smoke. when I got back I was disconnected from my server and it wont let me in anymore.

buggiz@playground:~$ ssh -vvv -p 222 buggiz@hostname
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to hostname [hostname] port 222.
debug1: Connection established.
debug1: identity file /home/buggiz/.ssh/identity type -1
debug1: identity file /home/buggiz/.ssh/id_rsa type -1
debug1: identity file /home/buggiz/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by hostname

The only way to connect to it is by ftpin' to it, and I have to drive like 4hours to get to the server. Is there anything I can do remotly to fix this problem. I can supply any logfile from the servere if that is needed.

---

