---
title: "Reload error on synaptic package manager- help"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by mountaintop on 2009-05-12
Dear Friends

I have a problem that when I click the Reload button in synaptic Package Manager, I get the following errors

[IMG]http://ubuntuforums.org/picture.php?albumid=1090&pictureid=3885[/IMG]
[IMG]http://ubuntuforums.org/picture.php?albumid=1090&pictureid=3886[/IMG]

and this my software sources
[IMG]http://ubuntuforums.org/picture.php?albumid=1090&pictureid=3887[/IMG]

---

### Post by Partyboi2 on 2009-05-12
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
```

---

### Post by mountaintop on 2009-05-12
Dear Partyboi2

I tried this but it give me the same error. please any hint

---

### Post by Partyboi2 on 2009-05-12
> **mountaintop said:**
> Dear Partyboi2

I tried this but it give me the same error. please any hint
:lolflag:, even with my glasses on I find it hard to see the error message, could you please post the output to 
sudo apt-get update so we can see it. :)

---

### Post by mountaintop on 2009-05-13
Hello Dear Partyboi2

I'm so sorry for the output was not clear in the last post. Please help me

_**The output of sudo apt-get update is **_

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (111 Connection refused) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (111 Connection refused) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (111 Connection refused) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (111 Connection refused) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (111 Connection refused) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by Partyboi2 on 2009-05-13
Do you use a proxy to connect to the Internet? If you do use a proxy open up Synaptic Package Manager (System>Admin>Synaptic) and under Settings>Pref>Network check that it is configured.

---

### Post by mountaintop on 2009-05-13
Dear Partyboi2

Thank you for your response. Yes I'm using a proxy in my network. And I make the changes as you said. But now the error messages are changed as follows

What do u think I should do? I think there is a problem with some network setting but I do not know how to figure it out. Please help meeeeeeeeeeeeeeee:KS


The new output after I configure the proxy server (my proxy server is 10.20.1.23:8080) is  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve '@10.20.1.23'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

