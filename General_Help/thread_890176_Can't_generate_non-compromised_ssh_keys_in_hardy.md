---
title: "Can't generate non-compromised ssh keys in hardy"
date: 2008-08-14
forum: General Help
---

### Post by wonko the sane on 2008-08-14
All the keys I generate are reported to be compromised. I'm using hardy, and have purged and reinstalled *ssh*. Anyone have any idea what's going on?

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/bork/.ssh/id_rsa): test
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in test.
Your public key has been saved in test.pub.
The key fingerprint is:
39:19:e1:fb:c3:96:78:37:3a:6e:a9:e1:37:78:17:6e bork@andromeda
$ ssh-vulnkey test
COMPROMISED: 2048 39:19:e1:fb:c3:96:78:37:3a:6e:a9:e1:37:78:17:6e test.pub
```

---

### Post by bbogart on 2008-10-21
I can confirm this on hardy (up to date as of today) on ppc. 

Did you report a bug?

---

### Post by cariboo on 2008-10-21
Please create a  bug report here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

You'll have to create an account. Please include as much information as possible.

If the devs don't know about a problem, they can't fix it.

Jim

---

