---
title: "Installing Mathematica 6.01 Problems"
date: 2008-10-16
forum: General Help
---

### Post by raiderleaf on 2008-10-16
[LEFT]Hello. I was trying to install Mathematica 6.01 on my Ubuntu 8.04 when I ran into the following error:

--------------------------------------------------------------------------------
                     Wolfram Mathematica 6.0.1 Installer 
--------------------------------------------------------------------------------

Copyright (c) 1988-2007 Wolfram Research, Inc. All rights reserved.

WARNING: Mathematica is protected by copyright law and international
treaties. Unauthorized reproduction or distribution may result in severe
civil and criminal penalties and will be prosecuted to the maximum extent
possible under law.

Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/6.0:
> 

The selected directory contains files and/or directories that may be
overwritten during installation. If you have any files you wish to keep
in this directory, you should exit the installer and move the files to a
separate directory before continuing.

Overwrite directory (y/n)?
> y

Now installing...

[*****************************************************************************]

Type the directory path in which the Mathematica script(s) will be created,
or press ENTER to select /usr/local/bin:
> 

The scripts 'MathKernel', 'Mathematica', 'math', 'mathematica', 'mcc' already
exist in the directory /usr/local/bin. The following actions can be performed
on the existing file(s).

  (1) Overwrite
  (2) Rename

Type your selection, or press ENTER to select (1):
> 1


Error: The installer was unable to check for a valid password file. Your
Mathematica installation may be incomplete or corrupted.


Installation failed. See /usr/local/Wolfram/Mathematica/6.0/InstallErrors.

A copy of the previous contents of the directory
"/usr/local/Wolfram/Mathematica/6.0" can be found at
"/usr/local/Wolfram/Mathematica/6.0/BackupDir-26025".




When I opened the file they specified "InstallErrors" , this is what it stated:

/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux/MathKernel: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

What should I do to fix this?[LEFT][/LEFT]
[/LEFT]

---

### Post by RequinB4 on 2008-10-16
I had the exact same problem, and i'm not sure what i did that fixed it, but here's what i did:

delete the /usr/local/Wolfram directory

take the CD out and put it in again.

cd to the install, ./ the install script.

I think this was a problem with the CD during install as my installation right now has the MathKernel executable in that directory

---

### Post by raiderleaf on 2008-10-16
> **RequinB4 said:**
> I had the exact same problem, and i'm not sure what i did that fixed it, but here's what i did:

delete the /usr/local/Wolfram directory

take the CD out and put it in again.

cd to the install, ./ the install script.

I think this was a problem with the CD during install as my installation right now has the MathKernel executable in that directory

I didn't use a CD, I just downloaded the installation folder and unpacked it and ran the installation. what should I do?

---

### Post by Yellow Pasque on 2008-10-16
```
sudo apt-get install libstdc++5
```

---

