---
title: "error while ./configure"
date: 2008-10-28
forum: General Help
---

### Post by unnati on 2008-10-28
Hi 
i am trying to install a program but all i get is just errors
./configure gives the following

./configure
configuring ImageMagick 6.4.4
checking build system type... armv6l-unknown-linux-gnueabi checking host system type... armv6l-unknown-linux-gnueabi checking target system type... armv6l-unknown-linux-gnueabi checking whether build environment is sane... yes checking for a BSD-compatible install... config/install-sh -c checking for a thread-safe mkdir -p... config/install-sh -c -d checking for gawk... no checking for mawk... no checking for nawk... no checking for awk... awk checking whether make sets $(MAKE)... no checking for gcc... gcc checking for C compiler default output file name...
configure: error: in `/home/user/MyDocs/ImageMagick-6.4.4':
configure: error: C compiler cannot create executables See `config.log' for more details.


apt-get install libc-dev gives the following

apt-get install libc-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libc6-dev instead of libc-dev Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libc6-dev: Depends: libc6 (= 2.5.0-1osso7) but 2.5.0-1osso9 is to be installed
E: Broken packages

and finally apt-get install libc6

apt-get install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


can anyone (please*10^10) help me get rid of these errors?

thanks
unnati

---

### Post by oldos2er on 2008-10-28
Try to fix your broken packages first. Run this in a terminal: sudo apt-get install -f

 If you want to compile programs from source, you first need to install the package "build-essential". Imagemagick is in the repositories.

---

### Post by unnati on 2008-10-28
ok so this is what i get for apt-get install -f and build-essential
now i am really confused and i couldn't find imagemagick when i did
apt-cache search imagemagick :(

apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
			    libc-dev
		   Depends: g++ (>= 3:3.3) but it is not going to be installed
		   Depends: dpkg-dev (>= 1.4.1.19) but it is not going to be installed
E: Broken packages

---

### Post by spiderbatdad on 2008-10-28
idk...are your sources enabled?

---

### Post by oldos2er on 2008-10-28
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by unnati on 2008-10-28
this is the reuslt of cat /etc/apt.sources.list

#maemo:name Devicescape
deb [http://www.devicescape.com/download/debian/chinook](http://www.devicescape.com/download/debian/chinook) user

btw i am working on N810

---

### Post by mc4man on 2008-10-29
Why don't you try going System -> Administration -> Software Sources and under 'ubuntu software' tab make sure all 5 boxes are enabled.
Under the 'updates tab' the first 2 boxes. 

Then open synaptic and if it reports broken packages go -> edit -> 'fix broken packages' and when done click the Apply button.

After that try your install

---

