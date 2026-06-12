---
title: "[SOLVED] Mac to linux public key ssh fails, but works from other linux"
date: 2008-09-01
forum: General Help
---

### Post by cpbl on 2008-09-01
Hello. I want to use public key (pubkey, publickey, public-key) authentication to ssh from a MacOSX to a linux Ubuntu box. That is, I want to be able to ssh without entering a password.

I can use this method (ssh-keygen etc) from other linux boxes to my linux box. But doing it from the Mac fails: it just asks me for a password.

Has anyone else had this problem?

Here is the output from ssh -v:
```
 ssh -v lkb@myhost.com
OpenSSH_4.7p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /Users/louise/.ssh/config
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to ahost.com [myipaddress] port 22.
debug1: Connection established.
debug1: identity file /Users/louise/.ssh/id_rsa type 1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'ahost.com' is known and matches the RSA host key.
debug1: Found key in /Users/louise/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/louise/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
lkb@ahost.com's password: 

```

What is happening?

---

### Post by bingoUV on 2008-09-01
Anything interesting in the sshd server logs? Try starting the server in debug mode (-d) and see what it gives when you try to connect from your mac.

---

### Post by joenix on 2008-09-01
Are you perhaps using the lsh-server? I found that public key authentication from OS X to the lsh server does not work properly.
Besides that I found out while researching this that a lot of people have problems with file permissions on OS X. Maybe you can have a look at this:
[http://www.macosxhints.com/article.php?story=20080424055927442&query=ssh%2Bpublic%2Bkey](http://www.macosxhints.com/article.php?story=20080424055927442&query=ssh%2Bpublic%2Bkey)

---

### Post by cpbl on 2008-09-01
> **bingoUV said:**
> Anything interesting in the sshd server logs? 

Thanks! Yep, it says:

 ```

 Authentication refused: bad ownership or modes for directory /home/auser
```

which was my fault, and quickly fixed.

I claimed above that the pubkey method worked when from a different machine but not from the Mac... but I didn't try it with the same user! oops. Anyway, lesson: look at the log files, duh.

regards,
c

---

