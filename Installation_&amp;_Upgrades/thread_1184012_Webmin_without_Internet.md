---
title: "Webmin without Internet"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Logger_MCP on 2009-06-10
Hello All,
 
I am a newbie trying to install webmin on a 9.04 Ubuntu server.
 
I am trying to install Webmin without access to the Internet from the local machine. 
What I have done is basically download the packages I need to my local repository, then use apt-get update to install the packages. The files I have 
downloaded are as follows:
 
libauthen-pam-perl_0.16-1_i386.deb
libmd5-perl_2.03-1_all.deb
libnet-ssleay-perl_1.35-1_i386.deb
libperl5.10_5.10.0-19_i386.deb
perl-base_5.8.7-10ubuntu1.2_i386.deb
webmin_1.470_all.deb
 
The command I use to install these files is as follows:
sudo apt-get perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
 
I think most of the packages installed, but I get an error telling me the following packages have unmet dependences:
libauthen-pam-perl But it is not going to be installed
libmd5-perl But it is not installable
 
I tried using aptitude to install the above packages, and I got the following message:
The following packages are broken:
libauthen-pam-perl
 
libauthen-pam-perl depends on perlapi-5.8.7 (provided by perl-base5.8.7-10ubuntu1.2)
perlapi-5.8.7 is unsatisfied
 
I have access to the Internet from other machines so I am able to download files and
copy them to the server. 
 
Thanks in advance for your help.
 
 
Logger

---

