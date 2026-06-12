---
title: "No_pubkey, I thought I knew how to do this"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2009-04-08
Solved, I changed permissions on the file /.gnupg/pubring.gpg from root to username (me)



I am getting this error when I try to add a key. Can someone tell me what I need to do.

```
stevepoulton@stevepoulton-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/stevepoulton/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
stevepoulton@stevepoulton-laptop:~$ 

```

Now I am getting this error when I try to fix this,

chown: cannot access `/home/stevepoulton/.gnupg/pubring.conf': No such file or directory

---

### Post by garyedwardjohnston on 2009-04-28
in terminal try this:

```
http://cultoffree.wordpress.com/2009/02/03/w-gpg-errorno_pubkey-60d11217247d1cff-wtf/
```

then this:

```
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```

---

