---
title: "extraction not performed"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Z3r0t0l0rEnCe on 2009-01-15
I having a little issue as far as extracting .tar files.  Everytime I try to extract a file I get this error.  If I need to log in as root how do I do that?  Sorry I'm still learning, I understand a lot but still new to Linux.

---

### Post by unutbu on 2009-01-15
file:/// is your root directory, also known as /

The error means that you need root permissions to place the extracted files in the root (/) directory.

Usually tar files do not install directly into the root directory, unless the tar file is a backup of your system. Apps usually install into some sub directory like /opt or /usr/local or /home/user. Are you sure this is where you want to the extracted files to go? If not, move the tar file to the directory into which you want the extracted files to be placed.

To extract the files: you could 

[list]
[*]Open a terminal (Applications>Accessories>Terminal) and type
```
gksu nautilus
```
Navigate to the tar file
Double-click the file. The files should automatically be extracted.

[*]Open a terminal (Applications>Accessories>Terminal) and type
```
sudo tar xvjf FILE.tar.bz2
```
if the file is a tar.bz2 file. 
or```

sudo tar xvzf FILE.tar.gz
```
if the file is a tar.gz file.
or```

sudo tar xvf FILE.tar
```
if the file is a plain tar file.
(Change FILE to whatever is appropriate, of course)
[/list]

---

