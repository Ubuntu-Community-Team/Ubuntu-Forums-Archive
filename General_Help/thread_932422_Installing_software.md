---
title: "Installing software"
date: 2008-09-28
forum: General Help
---

### Post by gandalf458 on 2008-09-28
I've only installed software using the package manager before. Now I have a tar.gz archive I want to install to usr/local/bin/gtm - at least I think that's where I want it - but I need to do it in root I think.

Can anyone tell me what I need to do please?

---

### Post by mickyt1992 on 2008-09-28
Hi, this might work.

Extract the .tar.gz by right clicking the folder and clicking extract here.  This will create a folder.  I'll call the folder X, but you should substitute in the name of the folder that appears when ever X comes up below.

Open up your terminal and type "su" and hit return.  Then enter your root password. (Note: when typing the password won't show up at all)

Now navigate in to X using cd.  For example ```
cd "/home/michael/desktop/X"
```

Now type 
```
./configure
``` 
then 
```
make
```

---

### Post by lswb on 2008-09-28
If this is the GTransferManager program there is a package in the repositories. Just start synaptic and search for "gtm" It's always a good idea to check for a regular .deb package in the repo before installing anything from a .tar file. Using the package in the repository will ensure a compatible, standard installation that can be easily uninstalled if desired.

If for some reason you must install from the .tar.gz, it can be uncompressed by opening a terminal or vt, changing to the directory where the tarfile is located, and using the command 

tar xvf name-of-tarfile.tar.gz

This will create a new directory where the gunzipped and untarred files are placed. cd to that directory and look for a README file, INSTALL file, HELP file or folder, etc. or other text file whose name suggests it might have directions. If you can't find anything check the site where you downloaded the .tar.gz file from, or do a google search on the program name.

---

### Post by gandalf458 on 2008-09-28
Thanks guys.
The package is GT.M - MUMPS programming system from Sourceforge.

Cheers G :)

---

### Post by oldos2er on 2008-09-28
> **mickyt1992 said:**
>   
Open up your terminal and type "su" and hit return.  Then enter your root password. (Note: when typing the password won't show up at all)

 Ubuntu disables the root account by default, so this won't work (assuming the OP has not enabled the root account). Use the "sudo" command with the user password.

---

### Post by gandalf458 on 2008-09-29
> **oldos2er said:**
> Ubuntu disables the root account by default, so this won't work (assuming the OP has not enabled the root account). Use the "sudo" command with the user password.

I invariably have to try root and user password when I uses sudo! LOL

G :)

---

