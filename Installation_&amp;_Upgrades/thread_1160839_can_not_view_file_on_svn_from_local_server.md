---
title: "can not view file on svn from local server"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by sondt.hcm on 2009-05-16
Dear all,

I've got an ubuntu 9.04 with subversion installed. It's working fine

I commit a lot of files into that svn server and can access these file via web (example: [www.abc.com/svn]("http://www.abc.com/svn"))

The problem is when I open my SVN folder on the server (Places -> home -> svn ) . It's does not appear any file which I uploaded, just default folder **db, hook, conf, locks..**

Sorry for my english skill and thanks for attention 

Anyone help me plz

**This is my httpd.conf file**
[I]<Location /svn>
cation /svn>
DAV svn
SVNPath /home/FTP

AuthType Basic
AuthName "Subversion Repository"
AuthUserFile /etc/apache2/dav_svn.passwd
Require valid-user
</Location>[/I]

---

