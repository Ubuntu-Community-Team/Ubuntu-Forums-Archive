---
title: "symlink to ftp"
date: 2008-08-15
forum: General Help
---

### Post by 7raTEYdCql on 2008-08-15
I wanted to know if there is anyway i can link a folder on my comp to a folder that is hosted on the ftp server.

Will this ln command work in this situation, my friend said that he wrote a script for it. Didnt want to ask him thought i will work it out on my own.

Please help.

---

### Post by justleen on 2008-08-15
you cant create a symbolic link to a remote site (not with ftp anyway).
you can create a bookmark in the gui though.
If you need a "link" from the command line, I'd suggest using .netrc, which will auto connect to predefined sites, and run macro's there.. I use this quite often to script ftp actions

---

### Post by mcduck on 2008-08-15
Mounting FTP locations should be possible, I've seen many different instructions how to do that, but I have no info about which would be the best way/program to use these days. FUSE should be bale to do that, and I've seen "mount_ftp"-command mentioned a couple of times..

But, in Gnome, the easiest way would be to just use the Places/Connect to Server. That will give you a desktop shortcut that you can use to browse the FTP location with Nautilus just like you would browse any local directory..

---

