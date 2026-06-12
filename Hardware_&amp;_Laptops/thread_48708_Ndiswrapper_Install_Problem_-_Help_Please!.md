---
title: "Ndiswrapper Install Problem - Help Please!"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by jordanj1969 on 2005-07-13
the error I'm receive is below with the command I performed:

--------------------------------------------------------------------------------------------------

jjordan@ubuntujj:~$ sudo apt-get install ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.2kB of archives.
After unpacking 111kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

-----------------------------------------------------------------------------------------------------------------

I have the Ubuntu cd in my cdrom drive.  My drive reads cdrom0.  Not sure if that is causing the problem.  I have a cd for Ubuntu that I downloaded.  Could that be causing the problem?

Help Please

---

### Post by ProNoblem on 2005-07-13
It could be that i'm wrong, but it looks like your sources.list entry for the Hoary cd-rom is pointing to /cdrom/
You could edit your sources.list so that it points to /media/cdrom, or you can comment the line out by adding an # in front of it so that you only use the ubuntu archives (which means that you'll be using newer packages)

---

### Post by jordanj1969 on 2005-07-13
What should the deb line read in the sources.list file?

---

### Post by jordanj1969 on 2005-07-13
that step didn't work, do you have any other ideas?

---

### Post by az on 2005-07-13
Use synaptic.  Look at your list of repositories.  Remove your cd as a repository.  The add your cd as a new repository.  Update and try to install ndiswrapper-utils again.

---

