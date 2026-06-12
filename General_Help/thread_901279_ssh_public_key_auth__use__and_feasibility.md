---
title: "ssh public key auth:  use  and feasibility"
date: 2008-08-26
forum: General Help
---

### Post by vortmax on 2008-08-26
This is a two part question.

First off, I have a main server here at the corporate office and several servers out in the field which are connected back through the internet (non-secure).  All machines are running ubuntu server.

I am continually logging into the remote machines for various purposes as well as transferring files back and forth. So far I have been using ssh and scp.

I would like to set up public key authorization so that I can access these servers (and script much of the actions) from the main server without having to enter a password every time.  I've read that public key with a blank pass-phrase is bad, but it seems to be the only way to accomplish this.  So how bad is it really?

secondly, I can't seem to get it working.

These are the exact steps I've taken:

_Client_
1. > cd ~/.ssh/
2. > ssh-keygen -t rsa
3. > ssh-copy-id -i ~/.ssh/id_rsa.pub username@remotehost

When I ssh into 'remotehost', it still asks for a password.  I checked '/etc/ssh/sshd_config' and PublicKey auth is set to yes.

I also tried it by manually copying the public key over and appending it to authorized_keys, still with no luck.
Any ideas?

---

### Post by vortmax on 2008-08-26
i made some headway,
It appears the the public keys I'm generating are all blacklisted.

How is it that every rsa key I generate is on the blacklist?

---

### Post by kevmitch on 2008-09-18
I don't know why nobody has replied to you yet given the amount of attention the ssh key issue has received. My guess would be that your server has an up to date openssh-server which has a blacklist of known weak keys. The machine you're generating the keys on on the other hand has not been upgraded to fix a significant vulnerability that is causing it to generate weak keys. My advice would be to upgrade openssh-client on the machine where you're generating the keys.

---

### Post by hytek on 2008-09-30
To chime in...

I am having this same problem.

Both servers are Ubuntu 8.04 amd64 server updated completely.

Not sure about this particular problem.

I'm still working on the issue and if I find a work around I'll post it. (or link it)

cheers.

---

### Post by hytek on 2008-09-30
Fixed it.

@:ssh-keygen -t rsa -b 4096 -S *randomHEXlettersnumbers*


The random HEX letters and numbers doesn't have to be very long.

For ex. 

```
@: ssh-keygen -t rsa -b 4096 -S 8C:4D:2A
@: ssh-copy-id -i id_rsa.pub root@servername
```

Cheers

---

