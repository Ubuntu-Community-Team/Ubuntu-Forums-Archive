---
title: "Update help?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by zyx on 2009-04-14
I have a weird problem to connect to internet! My web browser is okay to connect to internet, but I cannot update! If I type "sudo aptitude update", there are following error message:

sudo aptitude update 
Err [http://ftp.netspace.net.au](http://ftp.netspace.net.au) hardy Release.gpg
  Could not resolve 'a11781'
Err [http://ftp.netspace.net.au](http://ftp.netspace.net.au) hardy/main Translation-en_AU
  Could not resolve 'a11781'
Err [http://ftp.netspace.net.au](http://ftp.netspace.net.au) hardy/restricted Translation-en_AU
  Could not resolve 'a11781'

a11781 is my login name.

I have a proxy to connect to internet, even I set follows:

export http_proxy=http://loginname:mypassword@proxy_server:8080

I still have above problems. Does anyone have suggestions? Thanks!

---

### Post by abn91c on 2009-04-14
remove that ftp.netspace.net lines from the repos

---

### Post by zyx on 2009-04-14
It does not work, error message looks like:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'a11781'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2)  Could not resolve 'a11781'

Any suggestions? Thanks!

---

### Post by zyx on 2009-04-15
[solved] I find the problem, it is my password including "/", remove it, everything's fine!

---

