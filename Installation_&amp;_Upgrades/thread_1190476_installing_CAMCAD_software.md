---
title: "installing CAM/CAD software"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by trojvirus on 2009-06-17
good day,  i'm just a newbie on linux. I'm having problem installing a software in ubuntu,  it was running fine on red hat 9,  but we've decided to use another distro due to some reasons..  the installer runs fine on fedora and centOS but have problem in other issues.

We tried ubuntu, but at the start of the installation which is copying files, it is stuck up on "calculating checksum".
i was thinking if there are incompatibilities to be considered?

any idea will be a great help. thanks.

Unix platform requirements:
HP-UX 9.05 and up
Sun OS
Solaris with more than 300 MB of swap space
AIX

---

### Post by 123456789123456789123456 on 2009-06-18
is the installer a .run file?
If so, installation may not work, the installer may need supporting packages that are not installed or checked for.
how is the program being run?
do you have to use terminal, or is it running from GUI?
if it is a .run file, convert it to a debuin core install file aka (.deb)
if it is a .run file, try the folling
first download this
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms
this will download and install a convereter
then type sh "program name".run --buildpkg Ubuntu/jaunty
the command should have created several .deb files, you will probably have to search for them, but after you find them, type them in to install them, with sudo dpkg -i command followed by the file name, with a space between each.  this should install them all.

---

### Post by trojvirus on 2009-06-18
it's install.csh that run on terminal.

when i command  

(converted using dos2unix first)

./install.csh

a GUI will appear, but when i click start button. 
1st task is copy the files from a certain folder, i just input the location path, then it should automatically copy it, . but it was stucked up on calcucating checksum of a tgz file.

---

