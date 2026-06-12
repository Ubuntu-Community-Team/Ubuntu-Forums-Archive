---
title: "scp cronjob"
date: 2008-10-04
forum: General Help
---

### Post by iason on 2008-10-04
can anyone tell me why this isn't working?

Subject: Cron <root@box> /usr/bin/scp -i /root/.ssh/id_rsa /var/log/ac/claud.log [email]user@remote.org:~/dir/dir2/us2.log[/email]
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/bash>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>

Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
lost connection


when i run the string by it self it works fine. i've used the -i switch and set the shell to bash. I can't think of anything else. what am i missing here?

---

### Post by iason on 2008-10-05
here is what im doing with -v option

new string running in cron:

/usr/bin/scp -2 -B -v -i /root/.ssh/id_rsa /home/dir/file.cfg [email]username@remotehost.org:~/dir/file.cfg[/email]

Executing: program /usr/bin/ssh host remotehost.org, user myuser, command scp -v -t ~/dir/file
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to remotehost.org [*] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch3
debug1: match: OpenSSH_4.3p2 Debian-9etch3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'remotehost.org' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: No more authentication methods to try.
Permission denied (publickey,password).
lost connection

---

### Post by michaelrepucci on 2009-05-14
I'm having the exact same problem. Has anyone found a solution?

---

### Post by michaelrepucci on 2009-05-22
For me the solution involved created a passkey that had an empty passphrase. I suppose it's a bit less secure (I'm no SSH expert), but for my purposes, it doesn't matter. Since it took a lot of Googling to finally find this solution, here are some references:
[http://marc.info/?l=secure-shell&m=100705479617280&w=2](http://marc.info/?l=secure-shell&m=100705479617280&w=2)
[http://www.derkeiler.com/Newsgroups/comp.security.ssh/2004-10/0153.html](http://www.derkeiler.com/Newsgroups/comp.security.ssh/2004-10/0153.html)
[http://forums.fedoraforum.org/archive/index.php/t-53479.html](http://forums.fedoraforum.org/archive/index.php/t-53479.html)

Hope that helps the next person!

:) Michael

---

