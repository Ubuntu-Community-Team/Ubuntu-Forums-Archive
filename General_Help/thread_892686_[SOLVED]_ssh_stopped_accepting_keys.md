---
title: "[SOLVED] ssh stopped accepting keys"
date: 2008-08-17
forum: General Help
---

### Post by jerome1232 on 2008-08-17
My machine that has ssh open to the internet has stopped accepting keys, This happened after fiddling with keychain program so that I could have passphrase protected keys and use scp to store some backups in a script that gets run by crontab. 

I have undone all changes made by keychain, and can't correct this problem.

I'm currently using openssh on a windows computer but I get the same type of thing on other linux computers as well.

```
ssh-keygen -t dsa
scp /cygdrive/c/Users/Jeremy/.ssh/id_dsa.pub jeremy@server.home.lan:.ssh/authorized_keys
ssh -v jeremy@server.home.lan
OpenSSH_3.8.1p1, OpenSSL 0.9.7d 17 Mar 2004
debug1: Connecting to server.home.lan [192.168.1.3] port 22.
debug1: Connection established.
debug1: identity file /cygdrive/c/Users/Jeremy/.ssh/identity type -1
debug1: identity file /cygdrive/c/Users/Jeremy/.ssh/id_rsa type -1
debug1: identity file /cygdrive/c/Users/Jeremy/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debia
n-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.8.1p1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server.home.lan' is known and matches the RSA host key.
debug1: Found key in /cygdrive/c/Users/Jeremy/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /cygdrive/c/Users/Jeremy/.ssh/identity
debug1: Trying private key: /cygdrive/c/Users/Jeremy/.ssh/id_rsa
debug1: Offering public key: /cygdrive/c/Users/Jeremy/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
jeremy@server.home.lan's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
```

This attempt is with a passphrase protected key and it never even asks for the passphrase. It doesn't auth if I don't put a passphrase on the key either.

I'll post the contents of /etc/ssh/sshd_config in a second dos is a pain to copy/paste out off :)

edit: ok on the linux machine
```
cat .ssh/id_dsa.pub | ssh jeremy@server "cat >>.ssh/authorized_keys"
jeremy@server's password: 
ssh -v server
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [192.168.1.3] port 22.
debug1: Connection established.
debug1: identity file /home/jeremy/.ssh/identity type -1
debug1: identity file /home/jeremy/.ssh/id_rsa type -1
debug1: identity file /home/jeremy/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
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
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /home/jeremy/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/jeremy/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jeremy/.ssh/identity
debug1: Trying private key: /home/jeremy/.ssh/id_rsa
debug1: Next authentication method: password
jeremy@server's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
```

I don't get it looks like it's trying the keys...

okay I noticed this in the auth logs on the server

```
Aug 17 17:27:19 tss2 sshd[5271]: Authentication refused: bad ownership or modes for directory /home/jeremy/.ssh
Aug 17 17:27:19 tss2 sshd[5271]: Authentication refused: bad ownership or modes for directory /home/jeremy/.ssh
Aug 17 17:27:19 tss2 sshd[5271]: Failed publickey for jeremy from 192.168.1.4 port 60819 ssh2
```

this is the ownership for .ssh on the server
```
ls -lahd .ssh
drwxrw---- 2 jeremy jeremy 4.0K 2008-08-17 16:50 .ssh
```

---

### Post by jerome1232 on 2008-08-18
* bump *

I've tried regenerating host keys on both server and client, removing .ssh on server and client to no avail. I'm still getting the same error in my ssh logs whenever it tries to auth with a key.

```
Aug 18 01:07:42 tss2 sshd[5419]: Authentication refused: bad ownership or modes 
for directory /home/jeremy/.ssh
Aug 18 01:07:42 tss2 sshd[5419]: Authentication refused: bad ownership or modes 
for directory /home/jeremy/.ssh
Aug 18 01:07:42 tss2 sshd[5419]: Failed publickey for jeremy from 192.168.1.4 po
rt 52757 ssh2

```

---

### Post by jerome1232 on 2008-08-19
*bump*

---

### Post by qpieus on 2008-08-19
I think the permissions on the ~/.ssh directory are supposed to be drwx------
That's why you are getting the "bad ownership or modes" error.

Change the permissions:```
chmod 0700 ~/.ssh
```

---

### Post by jerome1232 on 2008-08-19
Okay thanks, it got me on the right track.

First I did

```
chmod 700 .ssh
chmod 600 .ssh/authorized keys
```

that didn't work, then I read on this page [http://sial.org/howto/openssh/publickey-auth/problems/](http://sial.org/howto/openssh/publickey-auth/problems/) that it could be your home directory so I removed group write to ~/

```
chmod g-w ~/
```

and it works again! Yay!

---

### Post by qpieus on 2008-08-19
Good job. I didn't know about the group write thing on ~/

---

