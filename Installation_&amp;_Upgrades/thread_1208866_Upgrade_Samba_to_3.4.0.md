---
title: "Upgrade Samba to 3.4.0"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by dave562 on 2009-07-09
I am trying to integrate Samba with Active Directory.  Despite having everything configured correctly, Kerberos working, etc, I am having some issues authenticating to Samba shares using AD credentials.  I want to upgrade to the latest version, but I'm stuck.

I have downloaded the latest tarball and installed it (configure, make, make install, etc).  I realized that the system doesn't even have a default smb.conf file to work with.  The smbd daemon isn't in the various /etc/init.d/rc folders.  There is obviously a lot of work to do.

What is the best way to get up and running with the most recent version of Samba on Ubuntu?  Using apt-get only brings down 3.0.28a.  Unfortunately for me that version doesn't support some of the functionality that I need in my environment.

For what it's worth, I didn't install Samba during installation.  When I used make, it put Samba in /usr/local/samba instead of /usr/sbin.

If I had used apt-get to install the version from the repository, would the make file have then updated that version?  I don't know enough about make files and configure scripts to verify if that functionality is in there.

---

### Post by sbirulino on 2010-01-17
I'm having a problem similar to yours. To have the files in usual position you shoud take a look at the file rules inside the packaging directory (packaging/Debian/debian-sarge). Here you can find some options to add to the configure script to have a better resuld when compiling. Some scripts would be missing but in my opinion you can use those you can find in lower verion of samba (3.0.28a too).

I hope this was helpful for you.

Good luck!

PS: I was very happy with Ubuntu but in this circumstances I think debian would be better. In fact the newer version you need are disposable for debian in enterprisesamba.org.

---

