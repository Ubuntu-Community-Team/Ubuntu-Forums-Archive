---
title: "Problem with Preseeding"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Thomy23 on 2009-07-03
Hi guys

I'm currently trying to automate an ubuntu installation (jaunty) using a custom preseed file. I ran into a couple of problems although i think that the preseed.cgf is correct:


1. I want to use a local mirror for the base installation of the system. My mirror section looks like:

d-i  mirror/country                     string  enter information manually
d-i  mirror/http/hostname               string  xxx
d-i  mirror/http/mirror                 select  ubuntu-mirror.sit.fraunhofer.de
d-i  mirror/http/directory              string  /ubuntu/ubuntu
d-i  mirror/http/proxy                  string
d-i  mirror/protocol                    select  http
d-i  mirror/suite                       string  jaunty

and 

d-i apt-setup/country		select	enter information manually
d-i apt-setup/uri_type		select	http
d-i apt-setup/hostname		string	xxx
d-i apt-setup/directory		string	/ubuntu/ubuntu
d-i apt-setup/another		boolean	false
d-i apt-setup/mirror		select	xxx
d-i apt-setup/security_host     string  xxx
d-i apt-setup/use_mirror boolean true
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/non-free boolean true
d-i apt-setup/security-updates boolean true
d-i apt-setup/backports boolean false

During the installation, the index files (.bz2) are downloaded from the mirror but the packages are fetched locally from the cd. What have i made wrong, and where are the differences between the mirror and the apt-section (is the apt-section only for configuring the sources.list?)?

2. How can i disable the dialogue asking if i want to install language support and install language support (germany) by default?

3. I want to create a user during installation using these commands:

d-i passwd/root-login boolean false
d-i passwd/make-user boolean true
d-i passwd/user-fullname string Admin
d-i passwd/username string admin
d-i passwd/user-password password changeme
d-i passwd/user-password-again password changeme

but it doesnt work, why?


Thanks in advance


Greets Thomas

---

