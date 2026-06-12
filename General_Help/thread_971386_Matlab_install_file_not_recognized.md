---
title: "Matlab install file not recognized?"
date: 2008-11-04
forum: General Help
---

### Post by swirlz on 2008-11-04
Hi all,

I just installed ibex, and I am having problems installing matlab 2008a. I have the unix version of matlab and previously with hardy the matlab install file worked. Now, ibex does not recognize the install file type and just opens the install code with the editor. 

What can i do? thanks in advance

---

### Post by taurus on 2008-11-04
How did you run it to install it and is it a script, bash, file?

---

### Post by swirlz on 2008-11-04
previously with hardy i just opened the install file and it worked. And I don't know what a script or bash are..

---

### Post by taurus on 2008-11-04
What does the first line of the file look like when you tried to run it but it opened with a text editor instead?  Also, what is the name of the file and permissions?

Applications -> Accessories -> Terminal
```
ls -la **filename**
```
Replace the **filename** with the actual name of that file you want to run.

---

### Post by swirlz on 2008-11-04
#!/bin/sh
#
#  Name:
#     install	point of entry for MATLAB installation
#
#  Usage:
#     install -h | [-<arch>] [-debug] [ [-t] | [-x] ]
#
#  Description:
#     "install" is the point of entry for all MATLAB installations.
#     The system administrator should be logged in as "root".

---

### Post by taurus on 2008-11-04
Try changing the permissions of that file and execute it from a terminal to install MatLab.

```
chmod 755 filename
sudo ./filename
```
Again, replace the filename with the actual name of that file.

---

### Post by swirlz on 2008-11-04
i dont know how to change the directory i thought it was:

 cd ~ \desktop\matlab

So i cant change the permissions

---

### Post by taurus on 2008-11-05
Linux/Unix is case sensitive so Desktop is not the same as desktop.  Try something like

```
cd ~/Desktop
chmod 755 **matlab**
sudo ./**matlab**
```
Assuming **matlab** is the actual name of that file (instead of Matlab, MatLab, MATLAB, or whatever it's called).  If you are not sure the actual name of it, just look it up with

```
ls -la
```

---

### Post by swirlz on 2008-11-05
nvm...

I changed the permisions but got this:

An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/j/Desktop/Matlab/update/install/main.sh: 178: /home/j/Desktop/Matlab/update/bin/glnx86/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

---

### Post by taurus on 2008-11-05
Need to make that file an executable also.

```
chmod 755 /home/j/Desktop/Matlab/update/bin/glnx86/xsetup
```
Now, run the setup again and see if you can install matlab this time.

---

### Post by swirlz on 2008-11-05
btw the install program is calle "install" is that a problem?

---

### Post by taurus on 2008-11-05
> **swirlz said:**
> btw the install program is calle "install" is that a problem?

Not at all.

---

### Post by swirlz on 2008-11-05
sweet! it looks like it is working. Thanks

---

