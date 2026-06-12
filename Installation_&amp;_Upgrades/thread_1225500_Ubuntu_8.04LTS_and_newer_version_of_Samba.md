---
title: "Ubuntu 8.04LTS and newer version of Samba"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by zounder on 2009-07-28
Hi,
I was wondering if anyone has experience upgrading Samba to a newer version than available with 8.04LTS.  8.04LTS seems to be stuck at 3.0.28a which is getting very old in the Samba world.

I am motivated here as I want to upgrade to 3.3.4 in order to support Windows 7 clients in a Samba PDC setup.  Earlier verions of Samba are not working with Windows 7.  

Thanks in advance for any suggestions.

PS:  Admins, please feel free to move this post to where it seems appropriate.  Being a new user I was struggling to know where to post this in the forum.

---

### Post by kimnzl on 2009-07-30
Samba 3.3.4 for Hardy 8.04 LTS to support Windows 7 Domain Logins

Reference: http://www.1stbyte.com/2009/05/31/join-windows-7-to-samba-pdc/

Fix the windows 7 machine settings:

create a domainfix.reg file with the contents of:
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\LanmanWorkstation\Parameters]
"DomainCompatibilityMode"=dword:00000001
"DNSNameResolutionRequired"=dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Netlogon\Parameters]
"RequireSignOnSeal"=dword:00000000
"RequireStrongKey"=dword:00000000

right click on it then merge it with the registry.


Build Samba 3.4.0/3.3.x

I am using the source packages from:
https://launchpad.net/ubuntu/karmic/+source/samba/2:3.3.4-2ubuntu1
I did not test installing anything except 3.4.0. 3.3.5 and 3.3.4 compile and created the debs but I did not install them.
Update: Samba 3.3.5, 3.3.6 and 3.4.0 allow joining but on reboot you get:
"The trust relationship between this workstation and the primary domain failed"
You NEED to use 3.3.4!

Note all lines starting with # are comments and not actual commands you do not need to run them.
In a terminal run the following:

#You do need the build-essentials, dpkg-dev installed
sudo apt-get install build-essentials dpkg-dev

mkdir samba_build
cd samba_build

# I had to add --no-check-certificate to wget to get past the SSL cert error I got.


#NOTE:
#if dpkg-buildpackage -rfakeroot give the following type error:
#If you get dpkg-checkbuilddeps: Unmet build dependencies: then apt-get install those (without the extra numbers in "()") and try again
#Example: dpkg-checkbuilddeps: Unmet build dependencies: libreadline5-dev libcups2-dev | libcupsys2-dev libacl1-dev libpopt-dev quilt uuid-dev libkeyutils-dev
#note some packages are or (the | symbol, Example libcups2-dev | libcupsys2-dev) and one does not exist on ubuntu. try one then the other
#sudo apt-get install libcups2-dev; sudo apt-get install libcupsys2-dev; 
#Example: sudo apt-get install libreadline5-dev libcupsys2-dev libacl1-dev libpopt-dev quilt uuid-dev libkeyutils-dev

# ignore warnings like: dpkg-buildpackage: warning: Failed to sign .dsc and .changes file
# and gpg related ones

####
#   Samba
####

#Build the depends
#libtalloc-dev
#https://launchpad.net/ubuntu/karmic/+source/talloc/1.4.0~git20090718-1
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/talloc/1.4.0~git20090718-1/+files/talloc_1.4.0~git20090718.orig.tar.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/talloc/1.4.0~git20090718-1/+files/talloc_1.4.0~git20090718-1.diff.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/talloc/1.4.0~git20090718-1/+files/talloc_1.4.0~git20090718-1.dsc

sudo apt-get install docbook-xsl xsltproc swig

dpkg-source -x talloc_1.4.0~git20090718-1.dsc
cd talloc-1.4.0~git20090718
dpkg-buildpackage -rfakeroot
cd ..
mkdir deb-libtalloc
mv *.deb deb-libtalloc
sudo dpkg -i deb-libtalloc/*.deb


#libcap2-dev
#https://launchpad.net/ubuntu/karmic/+source/libcap2/1:2.16-5ubuntu1
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/libcap2/1:2.16-5ubuntu1/+files/libcap2_2.16.orig.tar.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/libcap2/1:2.16-5ubuntu1/+files/libcap2_2.16-5ubuntu1.diff.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/libcap2/1:2.16-5ubuntu1/+files/libcap2_2.16-5ubuntu1.dsc

sudo apt-get install cdbs indent

dpkg-source -x libcap2_2.16-5ubuntu1.dsc
cd libcap2-2.16
dpkg-buildpackage -rfakeroot
cd ..
mkdir deb-libcap2
mv *.deb deb-libcap2
sudo dpkg -i deb-libcap2/*.deb


#build Samba 3.3.4

wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/samba/2:3.3.4-2ubuntu1/+files/samba_3.3.4.orig.tar.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/samba/2:3.3.4-2ubuntu1/+files/samba_3.3.4-2ubuntu1.diff.gz
wget --no-check-certificate https://launchpad.net/ubuntu/karmic/+source/samba/2:3.3.4-2ubuntu1/+files/samba_3.3.4-2ubuntu1.dsc

sudo apt-get install libreadline5-dev libcupsys2-dev libacl1-dev libpopt-dev quilt uuid-dev libkeyutils-dev

dpkg-source -x samba_3.3.4-2ubuntu1.dsc
cd samba-3.3.4/
dpkg-buildpackage -rfakeroot
cd ..
mkdir deb-samba334
mv *.deb deb-samba334
#install the debs. Pick the ones you want if you do not want them all.
sudo dpkg -i deb-samba334/*.deb

#remove the: libpam-smbpass depends on libpam-runtime (>= 1.0.1-6);
#I am not willing to modify pam on a server! Go to jaunty if you want it!
sudo apt-get purge libpam-smbpass
#Fix up any apt-get errors or deps
sudo apt-get -f install

#restart samba
sudo /etc/init.d/winbind restart
sudo /etc/init.d/samba restart
################################    END

---

### Post by chrisalavoine on 2009-11-27
Hi there,

Are there any inherent difficulties if you use an LDAP backend? Does it break?

Am thinking about following this guide to update our samba.

Regards,

c:)

---

### Post by MrTuTu on 2010-01-10
@kimnzl: thx !!. I tried to compile the 3.4.4 version, could start the server, but had problem with auth.

@chrisalavoine: you must perhaps update the schema.
Take a look at this page : [Upgrade Samba 3.0.28a to 3.4.3 on Ubuntu 8.04 LTS]("http://www.jeremycole.com/blog/2009/12/01/upgrade-samba-3-0-28a-to-3-4-3-on-ubuntu-8-04-lts/")

---

