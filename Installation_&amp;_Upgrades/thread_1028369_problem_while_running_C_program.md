---
title: "problem while running C program"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by ravinderreddy37 on 2009-01-02
hi i m new to ubuntu.
when i m trying to run C program after giving 
sudo apt-get install build-essential 

i m getting the following errors.


Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-21.42
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6
  Could not resolve 'in.archive.ubuntu.com'

like this i m getting 10 -15 errors .i dont know what to do
plez help me
thanks for all.

---

### Post by taurus on 2009-01-02
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and select another server.  Click Close and shut down synaptic.  Then from a terminal, run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by ravinderreddy37 on 2009-01-02
thanks for your response but when i tried for this also i m getting the following errors 



Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy Release.gpg
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/main Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/restricted Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/universe Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/multiverse Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates Release.gpg
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/main Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/restricted Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/universe Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/multiverse Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security Release.gpg
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/main Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/restricted Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/universe Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-security/multiverse Translation-en_IN
  Could not resolve 'ftp.iitm.ac.in'
Reading package lists... Done
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/Release.gpg](http://ftp.iitm.ac.in/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/Release.gpg](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'ftp.iitm.ac.in'


and as you said i have chosen another server but it when i click on it displaying countries names..

---

### Post by taurus on 2009-01-02
Try the Main Server.

---

### Post by Coder543 on 2009-01-02
Make sure you are connected to the internet from the Ubuntu machine.... (if this is not being posted from the Ubuntu computer)

---

