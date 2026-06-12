---
title: "Installing new printer woes"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Acupuncture Doc on 2007-02-10
Hi,

I recently tried to install new HP printer onto my system (celeron 1.3 256meg ram) and ran into some troubles. I downloaded the latest HPLIP which was 1.7.1 and did the following

sudo apt-get install -f

then

sudo apt-get install libcupsys2-dev

then ran

sh hplip-1.7.1.run

The file extracted and went through several steps before freezing the entire computer. I had to do a cold restart. Then I attempted installation again. All was fine until the following occurred:

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
warning: A previous install of HPLIP is installed and/or running.
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.
Running 'sudo /etc/init.d/hplip stop'
Please wait, this may take several minutes...

Running 'sudo apt-get remove --force-yes --yes hplip hpijs'
Please wait, this may take several minutes...
error: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
error: Continuing to run installer - this installation should overwrite the previous one.


BUILD AND INSTALL
-----------------
note: You may be prompted for a password. Please enter the appropriate password for your system for 'sudo' when prompted.

Running './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr'
Please wait, this may take several minutes...

error: './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr' command failed with status code 1

Any ideas??

---

### Post by passonno on 2007-02-10
Just an idea, but, have you enabled Universe and Multiverse in /etc/apt/sources.list ?

I am installing a printer right now, and that seems to have done the job for me.

---

### Post by Acupuncture Doc on 2007-02-10
Yes, I have already tried that...no luck

---

