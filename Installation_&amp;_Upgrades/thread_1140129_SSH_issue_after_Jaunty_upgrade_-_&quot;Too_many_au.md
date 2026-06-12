---
title: "SSH issue after Jaunty upgrade - &quot;Too many authentication failures&quot;"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by steenbras on 2009-04-27
After upgrading to Jaunty, I'm now getting issues trying to ssh into any server. I frequently ssh into Amazon EC2 instances, using private key files, and now I get this error: "Received disconnect from xxx.xxx.xxx.xxx: 2: Too many authentication failures for root".

However, it's got nothing to do with the private key file - I get similar behaviour logging into a work server with standard username/password authentication. I even get it on a local ssh attempt:

```
steenbras@steenbras:~$ ssh localhost
Received disconnect from 127.0.0.1: 2: Too many authentication failures for steenbras
```

The interesting thing, though, is that this doesn't happen if I sudo any of the above commands. I am in the admin group, which is defined in sudoers as having root privileges.

---

### Post by steenbras on 2009-04-28
In case this helps, here's some verbose output from the ssh attempt:

```
$ssh -v -i .ec2/.ec2-keys/id_mykeypair root@myserver.com

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to myserver.com [xxx.xxx.xxx.xxx] port 22.
debug1: Connection established.
debug1: identity file .ec2/.ec2-keys/id_rsa-swat_pair1 type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'myserver.com' is known and matches the RSA host key.
debug1: Found key in /home/steenbras/.ssh/known_hosts:70
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: steenbras@steenbras
Received disconnect from xxx.xxx.xxx.xxx: 2: Too many authentication failures for root

```

I'm not sure what the public key offering at the end is all about. I'm specifying a different private key in the first ssh, but it seems to be looking for a different public key locally.

---

### Post by iponeverything on 2009-04-28
To see if it clears it up try:

```
mv ~/.ssh ~/ssh.old

```

then try to login.

---

### Post by steenbras on 2009-04-28
Thanks iponeverything - that did indeed clear it up.

---

