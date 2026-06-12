---
title: "Problem in updating my system"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by bulls_eye on 2009-02-05
Hi,
I have am very new to Ubuntu and I have installed Ubuntu inside windows like a software.
As I started using Ubuntu I realized the need to use vlc media player and flash player.
I browsed the web to search for the method to install them and i got the commands
sudo apt-get update
sudo spt-get install "software name"

but sadly I am unable to update my system and whenever I try I get error


Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy Release.gpg                                    
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/main Translation-en_US                         
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/restricted Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/multiverse Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy/universe Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates Release.gpg
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/main Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/restricted Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/multiverse Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Err [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) hardy-updates/universe Translation-en_US
  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/Release.gpg](http://ftp.iitm.ac.in/ubuntu/dists/hardy/Release.gpg)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/Release.gpg](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://ftp.iitm.ac.in/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to ftp.iitm.ac.in:80 (203.199.213.69). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
 old ones used instead.
W: You may want to run apt-get update to correct these problems

Note that my internet is working fine and I also made network settings in the terminal with commands like

http_proxy=http://user:password@hostname:port
https_proxy=http://user:password@hostname:port
ftp_proxy=http://user:password@hostname:port

still no results.

Please help.

---

