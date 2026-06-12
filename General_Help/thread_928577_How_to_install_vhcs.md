---
title: "How to install vhcs"
date: 2008-09-24
forum: General Help
---

### Post by Cool Surfer on 2008-09-24
When I try to install vhcs, using this guide in vhcs folder , 
[I]
VHCS HowTo Install
========================================================================

Use the user root when installing VHCS.

Install all requiered packages a list could be found at:
	docs/debian-packages.txt
	docs/suse-packages.txt

Download the vhcs software.

Extract the installation files to a secure directory.
tangra: # cd /root
tangra: # tar -xjf vhcs2-2.4.7.1.tar.bz2

Change to the newly created directory.
tangra: # cd vhcs2-2.4.7.1/configs/

Open vhcs2.conf and make some changes. You
have to setting up some configuration variables
for your linux distribution. Currently delivers
VHCS vhcs2.conf preconfiguratet for linux debian.
If you using linux debian, you don't need to make
this changes. We will provide soon configuration files
for all linux distribution such as SuSE, RH, Gentoo,
Fedora, etc.

Change to the newly created directory.
tangra: # cd ../vhcs2-2.4.7.1

[B]Now You have to make buld for your system
tangra: # make install[/B]

Your build is now stored in /tmp/vhcs-2.4.7.1

Copy all directory forum the buil into your system 
(do not forget to make backups)
tangra: # cp -R /tmp/vhcs-2.4.7.1/* /[/I]


but when i try to run this command 
**make install**
```

i get this error

dfx@dfx-desktop:~/Desktop/cp$ sudo tar -xjf vhcs2-2.4.7.1.tar.bz2
dfx@dfx-desktop:~/Desktop/cp$ cd vhcs2-2.4.7.1/configs/
dfx@dfx-desktop:~/Desktop/cp/vhcs2-2.4.7.1/configs$ make install
if [[  == debian ]] ; then \
		cp ./vhcs2.conf  ; \
		cd ./apache && make install ; cd .. ; \
		cd ./bind && make install ; cd .. ; \
		cd ./crontab && make install ; cd .. ; \
		cd ./database && make install ; cd .. ;  \
		cd ./init.d && make install ; cd .. ; \
		cd ./postfix && make install ; cd .. ; \
		cd ./courier && make install ; cd .. ; \
		cd ./proftpd && make install ; cd .. ; \
		cd ./logrotate && make install ; cd .. ; \
	elif [[  == suse ]] ; then \
		cd ./dists/suse && make install ; \
	fi
/bin/sh: -c: line 0: conditional binary operator expected
/bin/sh: -c: line 0: syntax error near `debian'
/bin/sh: -c: line 0: `if [[  == debian ]] ; then \'
make: *** [install] Error 2
dfx@dfx-desktop:~/Desktop/cp/vhcs2-2.4.7.1/configs$ 
```

---

### Post by Cool Surfer on 2008-09-24
How can I fix it pl.

---

