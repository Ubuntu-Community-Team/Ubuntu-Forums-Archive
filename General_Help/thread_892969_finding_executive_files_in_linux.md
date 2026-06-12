---
title: "finding executive files in linux"
date: 2008-08-17
forum: General Help
---

### Post by jmsgz on 2008-08-17
New here so bear with me. Reading a turorial about Ubuntu and use of the "ln" or link command. I am from dos/wind and understand "ln" is used to execute a file (program) in another directory from say a home directory. In dos i would just update "path" or change to the directory and execute the file by name using the file name followed by extensions ".exe or .com or .bat.  

Can someone out there tell me what type of file extensions do i look for in Linux that represent an executable program? What do they look like in GUI or with file characteristics or extensions. 

This will help when downloading programs not in (Ubuntu archive or SPM) in trying to set them up for running once unzipped or untarred !

thanks in advance jmsgz:)

---

### Post by tuxulin on 2008-08-17
in linux the best thing to do when downloading any sofware is to READ the file that mostly comes with a package telling on how to install the software. some software are easy install by just clicking on a foo.deb file while other softwares requires you to compile, make to build the software before execution is even possible. 

there are a few ways to execute a program for example ./software.sh, .bin, .deb, .sh and there could be more. but reading the readme file will almost in most cases solve your situation

Tuxulin

---

### Post by unutbu on 2008-08-17
The PATH variable is a colon-separated list of directories. It enumerates the order in which directories are searched whenever a shell command is called.

You can check what your current PATH is by typing
```

echo $PATH

```
How to change your PATH variable:

Edit your ~/.profile by adding to the end:
```

PATH=$PATH:/path/to/directory
export PATH

```

or create ~/.profile if it does not already exist.

The new PATH will take effect the next time you log in.

Once your $PATH has been altered to include /path/to/directory, any executables inside of this directory can be called upon by name without having to supply the full path.

---

### Post by unutbu on 2008-08-17
> 
Can someone out there tell me what type of file extensions do i look for in Linux that represent an executable program?


Some programs have no extension, others do.
In Linux, any file can be an executable as long as its executable permission bit is set.

Type "ls -l /bin/ls" and you should see
```

% ls -l /bin/ls
-rwxr-xr-x 1 root root 78004 2007-09-29 08:51 /bin/ls
```

"-rwxr-xr-x" is the permission string. 

"r" stand for read, "w" for write, and "x" for executable. 
The above permission string says that the owner (root), members of the root group, and all others have permission to execute the file /bin/ls. ("ls -l /bin/ls" uses ls to look at itself).

See [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for the full story.

> What do they look like in GUI or with file characteristics or extensions. 

What icon Nautilus or Thunar or other GUI file manager uses probably is configurable. 
Perhaps go to /bin to see what icon is used by your file manager. (Just about everything in /bin should be executable.)

---

