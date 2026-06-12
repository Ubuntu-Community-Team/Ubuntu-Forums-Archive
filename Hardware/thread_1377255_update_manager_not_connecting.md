---
title: "update manager not connecting"
date: 2010-01-10
forum: Hardware
---

### Post by ep1.za on 2010-01-10
Hi all
Could someone please help with the following, I've installed 8.10 on my Acer laptop and cannot get the update manager to work, when I try and update I get the following error

 W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_ZA.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_ZA.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_ZA.bz2)  Could not connect to za.archive.ubuntu.com:80 (155.232.191.229). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


.Some info, the laptop connects to the internet when firefox is open. I am using a university wired lan. 


Please advise,
Thanks
E

---

### Post by labinnsw on 2010-01-11
Go to System >> Administration >> Software Sources

[ATTACH]143269[/ATTACH]

Under the "Ubuntu Software" tab, look for the "Download From" window.

Change to "Main Server"

[ATTACH]143270[/ATTACH]

---

### Post by konqueror7 on 2010-01-11
> **labinnsw said:**
> Go to System >> Administration >> Software Sources

Under the "Ubuntu Software" tab, look for the "Download From" window.

Change to "Main Server"

or better yet, select 'select best server'...;)

---

### Post by ep1.za on 2010-01-11
Thanks guys, still no dice. I've tried at home using my mobile broadband account and it connected (though way too expensive to update all at the moment) so must be something with the Uni's LAN. Will keep tinkering and let you know.
E

---

### Post by ep1.za on 2010-01-26
Update,
two weks and still have not been able to solve problem. Will be wipin driving and starting fresh with a 9.1 installation.

---

### Post by konqueror7 on 2010-01-26
> **ep1.za said:**
> Update,
two weks and still have not been able to solve problem. Will be wipin driving and starting fresh with a 9.1 installation.

oh, it could be your uni's problem,,,sorry for the late reply, just read it,,,:D

---

