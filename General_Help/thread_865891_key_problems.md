---
title: "key problems"
date: 2008-07-21
forum: General Help
---

### Post by kuantum_fizax on 2008-07-21
Hi, so I don't really understand the whole keyring buisiness. I seem to be having some trouble installing a physics analysis package called ROOT. The gpg--export key step is having errors. The instructions were:

add the line:
> 
deb [http://mirror.phy.bnl.gov/debian-root/ubuntu](http://mirror.phy.bnl.gov/debian-root/ubuntu) gutsy main contrib


to my sources.list. I then needed to add this guy's key, with: 
> 
gpg --keyserver subkeys.pgp.net --recv-keys 6620D4F5
gpg --export 6620D4F5 | apt-key add -

When I run the first line, I get:
> 
gpg: requesting key 6620D4F5 from hkp server subkeys.pgp.net
gpg: key 6620D4F5: "Christian Holm Christensen <cholm@nbi.dk>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

When I run the second I get
> 
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

If I try just the gpg --export key part, without piping to apt-key, I get junk that corrupts my terminal. The prompt and the title of the terminal window both become nonsense characters. I guess its changing the ASCII set or something...

Any advice?

Thanks

---

### Post by Heinzelotto on 2008-07-21
try "gpg -v" rather than just "gpg" for verbose mode. This should give more information about why the key is not being 'changed'

---

### Post by kuantum_fizax on 2008-07-21
Not much difference:
> 
lampen@vash:~$ gpg -v --keyserver subkeys.pgp.net --recv-keys 6620D4F5
gpg: requesting key 6620D4F5 from hkp server subkeys.pgp.net
gpg: armor header: Version: SKS 1.0.10
gpg: pub  1024D/6620D4F5 2006-08-21  Christian Holm Christensen <cholm@nbi.dk>
gpg: key 6620D4F5: "Christian Holm Christensen <cholm@nbi.dk>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
lampen@vash:~$ gpg -v --export 6620D4F5 | apt-key add -
gpg: writing to stdout
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error


---

### Post by Tim Sharitt on 2008-07-21
I tried it and had the same problem, but adding sudo worked:
```
gpg -v --export 6620D4F5 | sudo apt-key add -
```

---

### Post by kuantum_fizax on 2008-07-21
Alright, thanks!

BTW, in case someone finds this thread looking for how to install root on ubuntu, you finish it from this point with:
> 
sudo apt-get update
sudo apt-get install root-system


I got these instructions from [http://mirror.phy.bnl.gov/debian-root/ubuntu/](http://mirror.phy.bnl.gov/debian-root/ubuntu/)

Thanks again all.

---

