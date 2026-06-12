---
title: "Installing VMWare Tools"
date: 2005-12-05
forum: General Help
---

### Post by ubuntuforme on 2005-12-05
Hi,

I have installed Kubuntu 5.10 i386 into a VMWare session, but do not know how to install the VMWare Tools package? Sorry I am a newbie to Linux and do not know the commands to install software.

Any suggestions/help much appreciated.

Mitch

---

### Post by Mathboy on 2005-12-05
Hi, the VmWare page in the wiki describes getting the basics going.

[https://wiki.ubuntu.com/VmWare]("https://wiki.ubuntu.com/VmWare")

FWIW I have Breezy working wonderfully both as host and guest OS under VmWare 5.0.
It's been a week since I went through it, but the general steps for the tools (in the virtual machine) were:

1) get the kernel headers
sudo apt-get install linux-headers-$(uname -r)

then I linked the headers to the 'linux' directory:
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux

2) install gcc-3.4
sudo apt-get install build-essential
sudo apt-get install gcc-3.4
sudo apt-get install g++-3.4

3) Set the cc environment variable:
export CC="gcc-3.4"

4) From there it's all the normal vmware tools install process... use the install vmware tools thing in VmWare, which connects the vmware tools drive as the cdrom in the virtual machine, go to the cdrom directory (/mnt/cdrom maybe?), and run the script as usual, compiling things when asked to.

Hope this helps!

---

