---
title: "how to get GPG keys"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by Its Me on 2009-07-02
Hi -

How do I get the GPG keys for the following repositories/packages? 

thanks...

old-repositories.ubuntu.com

packages.ubuntu.com

---

### Post by raymondh on 2009-07-04
are you asking for the format to source and add the public key?

```
gpg --keyserver subkeys.pgp.net --recv 000000000000000AAAA
gpg --export --armor 000000000000000AAA | sudo apt-key add -
sudo apt-get update
```


000000000000AAA being the pubkey listed (when you get the "no pubkey" error).

Hope I got your question right.

---

### Post by jherskow on 2009-09-11
> josh@JoshBook:~$ gpg --keyserver.pgp.net --recv 0F2D1009066ADE1D
gpg: Invalid option "--keyserver.pgp.net"
josh@JoshBook:~$ gpg --keyserver subkeys.pgp.net --recv 0F2D1009066ADE1D
gpg: requesting key 066ADE1D from hkp server subkeys.pgp.net
     

gpg --export --armor 0F2D1009066ADE1D |gpg: can't open `/home/josh/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
josh@JoshBook:~$ 
josh@JoshBook:~$ 
josh@JoshBook:~$ gpg --export --armor 0F2D1009066ADE1D | audo apt-key add
gpg: can't open `/home/josh/.gnupg/pubring.gpg'
gpg: WARNING: nothing exported
gpg: key export failed: file open error
bash: audo: command not found




now what? ugh...

---

### Post by raymondh on 2009-09-11
> **jherskow said:**
> now what? ugh...

josh@JoshBook:~$ gpg --export --armor 0F2D1009066ADE1D | [COLOR="Red"]audo[/COLOR] apt-key add

Try (if you want, copy and paste)

```
gpg --export --armor 0F2D1009066ADE1D | sudo apt-key add -
```

and then

```
sudo apt-get update
```

---

