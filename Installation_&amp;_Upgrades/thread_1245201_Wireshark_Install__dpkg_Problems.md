---
title: "Wireshark Install / dpkg Problems"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by krimzen85 on 2009-08-20
Hey All,
As I had a feeling, I am having problems getting Wireshark installed and unpackaged in Ubuntu. Here is the procedure I've taken:
 
**(Note: I DO NOT have internet on the Linux machine yet)**
 
1. Downloaded i386 .deb file onto my Windows desktop and threw the .deb file onto USB stick. Site: [Ubuntu -- Error]("http://packages.ubuntu.com/jaunty/i3...shark/download")
 
2. Plugged USB into the drive, mounted it without a problem
 
3. Sudo dpkg -i wireshark_1.0.7-1ubuntu1_i386.deb
 
Following error message given:
 
*pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"*
*dpkg: error processing wireshark_1.0.7-1ubuntu1_i386.deb (--install):*
*cannot access archive: no such file or directory*
*Errors were encountered while processing:*
*wireshark_1.0.7-1ubuntu1_i386.deb*
 
Any ideas?

---

### Post by krimzen85 on 2009-08-20
Actually I've made some progress, but I am still being halted.
 
I wasn't in the USB directory when I ran the previous command, so I went to cd /media/Cruzer, and I ran the same command, and now:
 
I get errors stating that the Wireshark dependencies are not installed.
 
Needs:
libadns1
liblua5.1-0
wireshark-common
 
Do you know where I can find them?

---

### Post by dstew on 2009-08-20
Here is the page for [wireshark-common]("http://packages.ubuntu.com/jaunty/wireshark-common"), for Jaunty. You will have to go to the links for the libadns1 and liblua5.1-0 dependencies. These might trigger other dependencies, but hopefully not.

If you have access to another Ubuntu Jaunty computer that has an internet connection, you can get the package you want plus all the dependencies at once using  Synaptic, but check the "Download Packages Only" button. Then copy the packages over to your off-line computer, and install using dpkg.

---

