---
title: "SSH: &quot;SSH2_MSG_KEXINIT sent&quot; hangs"
date: 2008-09-09
forum: General Help
---

### Post by ungluun on 2008-09-09
Hi,

After the holidays (last week) I decided to update my system.
The result is that i'm unable to connect to my ssh servers.

```

debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to [my sshd server ip] port 22.
debug1: Connection established.
debug1: identity file /home/orlonth/.ssh/identity type -1
debug1: identity file /home/orlonth/.ssh/id_rsa type -1
debug1: identity file /home/orlonth/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch2
debug1: match: OpenSSH_4.3p2 Debian-9etch2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-2
debug1: SSH2_MSG_KEXINIT sent

-----!!Here it hangs for several minutes!

Connection closed by [ip my sshdserver]

```


I already searched on google and other forums, but nothing usefull turned up.
I'm sure the problem is caused by the update on my machine and not by the sshd server.

Has anyone found a solution for this problem?

---

### Post by HalPomeranz on 2008-09-09
This thread might be relevant to your problem:

[http://ubuntuforums.org/showthread.php?t=838873](http://ubuntuforums.org/showthread.php?t=838873)

---

