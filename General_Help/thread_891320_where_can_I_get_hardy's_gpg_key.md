---
title: "where can I get hardy's gpg key?"
date: 2008-08-15
forum: General Help
---

### Post by dodle on 2008-08-15
I need to install the gpg key for hardy so that Synaptic will quit giving me error messages.  I think I have to use "wget" but I don't know how to do it.

---

### Post by todak on 2008-08-15
```
sudo apt-get install ubuntu-keyring
```

---

### Post by dodle on 2008-08-15
I've already got that installed.  Here is the error:[QUOTE=Synaptic]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.kernel.org](http://mirrors.kernel.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.kernel.org](http://mirrors.kernel.org) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://mirrors.kernel.org](http://mirrors.kernel.org) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
[/QUOTE]

---

### Post by todak on 2008-08-15
Shut down Synaptic then restart it. Or if you are using the terminal do the same. Then the error messages will disappear. I am assuming you installed the key and haven't restarted your package manager.

---

### Post by BobDoLe on 2008-08-23
i had a similar problem for adding medibuntu repository, then ran
apt-get install medibuntu-keyring

but your specific gpg key will be needed of course.

---

