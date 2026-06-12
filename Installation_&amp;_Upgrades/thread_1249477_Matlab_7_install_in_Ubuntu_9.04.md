---
title: "Matlab 7 install in Ubuntu 9.04"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by tom.swartz07 on 2009-08-25
Hi everyone,

I have recently obtained Matlab for Linux, for use while I am studying here at my University. After several attempts, I am unable to figure out how to install it on my system.

I have the install disc, and following the instructions in the provided .pdf, it should work like a dream- yet I keep receiving the error
```

The installer is unable to copy files to /tmp.
Make sure that /tmp exists, is writable, and has
at least 5 megabytes of available space.
```The installation directions simply say to mount the cd, change terminal directory to /usr/local/matlab7, then run the install.sh file from the disc. I cannot change the permissions of the file, as they are read only on the cd, and even after copying the entire disc image to my computer hard drive, I was still unable to execute the install file.

Does anyone have any hints or tips on how to get this to work?
Thanks a ton! It'll make my Physics courses so much easier!
Tom

---

### Post by tom.swartz07 on 2009-08-25
bump

I would like to get this installed before the weekend so I could start on my projects.

Thanks everyone

---

### Post by pooja on 2009-11-25
[Look here]("https://help.ubuntu.com/community/MATLAB")

---

### Post by calbaker on 2009-12-18
> **pooja said:**
> [Look here]("https://help.ubuntu.com/community/MATLAB")

These instructions are irrelevant for Matlab 7.  The install file contained in the top level directory of the install cd is install_unix.sh.  I can't figure out how to use this.

---

### Post by calbaker on 2009-12-21
To be more specific, after creating the directory /usr/local/matlabR14, I tried to run the installer from the Matlab cd, and I got this:

```
chad@chad-laptop:/usr/local/matlabR14$ sudo sh /media/MATLAB_SV14\ \ \ \ \ /install_unix.sh 

dirname: extra operand `/install_unix.sh'
Try `dirname --help' for more information.
exec: 4: /unix/install: not found

```

Ideas?

---

### Post by calbaker on 2009-12-21
> **calbaker said:**
> To be more specific, after creating the directory /usr/local/matlabR14, I tried to run the installer from the Matlab cd, and I got this:

```
chad@chad-laptop:/usr/local/matlabR14$ sudo sh /media/MATLAB_SV14\ \ \ \ \ /install_unix.sh 

dirname: extra operand `/install_unix.sh'
Try `dirname --help' for more information.
exec: 4: /unix/install: not found

```

Ideas?

and then I tried 
```
 sudo sh /media/MATLAB_SV14\ \ \ \ \ /unix/install
```

which produced:
```
Internal error 1: We could not determine the path of the
                  MATLAB root directory.

                  original command path = /media/MATLAB_SV14     /unix/install
                  current  command path = /media/MATLAB_SV14     /unix/install

                  Please contact Mathworks Technical Support
                  for further assistance.

```

---

