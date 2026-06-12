---
title: "[SOLVED] nVidia binary X.org driver issues"
date: 2008-09-08
forum: Hardware
---

### Post by Thomas Andresen on 2008-09-08
Hi

I've just been installing Ubuntu on this laptop of mine, and I think I managed to install the wrong nVidia graphics driver. When I try to activate the driver I get the following error: ```
 E: nvidia-glx: subprocess post-removal script returned error exit status 2

```
So I try to remove the driver to install the newer version, but when I try to uncheck the old one, the "add/remove" application won't respond.

Any ideas as to what I may do?

---

### Post by in-dust-rial on 2008-09-08
start a shell and try to remove it from aptitude or apt-get.
how to use commandline packagetools is explained on most of the documentary sites (while using google i found severeal wiki sites in my language).
```
$sudo aptitude search glx | grep -i ^i
```
this will use aptitude to list all packages with glx in the name, and then only show the lines that start with i (i means installed).
so you will see what packages are installed.
try yourself to remove the packages you dont want.



use backups of xorg.conf  
```
$sudo cp /etc/X11/xorg.conf /"backupplace"/"backupfilename"
```
(/"backupplace"/"backupfilename" means you have to write here /etc/X11/xorg.conf.BACKUP or simular)
, and if you fail to startx or you messed it up, try:
```
sudo dkpg-reconfigure phigh xserver-xorg
```
this will regenerate a xorg.conf.

maybe you want to have a look at envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

you can download it from repos (apt-stuff).
because envy tries automatically to remove other configurations first AND installs then the correct drivers (in most cases).

good-luck

p.s.: its always a good idea to have build-essential installed...

---

### Post by Thomas Andresen on 2008-09-08
Thank you, I will try this.

---

### Post by Thomas Andresen on 2008-09-08
Hmm..

Using envy to remove the nVidia package produced the following:
(Reading database ... 102468 files and directories currently installed.)
```
Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by in-dust-rial on 2008-09-08
```
subprocess post-removal script returned error exit status 2
```
mm thats the same in your first post, right?

mmm i am not a pro and have no idea, what the lib32 exaxtly does...

but have you tried:
```
$ sudo aptitude remove "put in GLX-packagename"
```
allready?

did you ever install build essentials?
$sudo aptitude search build-essential 
(you should install them)

what kernel do you use?
$sudo uname -r

---

### Post by in-dust-rial on 2008-09-08
```
http://ubuntuforums.org/archive/index.php/t-770097.html
```

---

### Post by Thomas Andresen on 2008-09-08
> **in-dust-rial said:**
> ```
subprocess post-removal script returned error exit status 2
```
mm thats the same in your first post, right?

mmm i am not a pro and have no idea, what the lib32 exaxtly does...

but have you tried:
```
$ sudo aptitude remove "put in GLX-packagename"
```
allready?

did you ever install build essentials?
$sudo aptitude search build-essential 
(you should install them)

what kernel do you use?
$sudo uname -r

$sudo aptitude search build-essential returned:
```
p   build-essential                                         - informational list of build-essential packages  
```

and $sudo uname -r returned:
```
2.6.24-19-generic
```

What should this tell me?

And how should I proceed?

---

### Post by in-dust-rial on 2008-09-08
```
http://ubuntuforums.org/archive/index.php/t-770097.html
```
firt have a look here.
i found that page after searching your error massage in google.
the solution you can find there says, you have to use the 'ln' command, which makes links.
you may try this!

and you should install build-essential, because this is required to many installations and maybe also in your drivers installation.

did you try to remove the package with aptitude?

---

### Post by Thomas Andresen on 2008-09-08
says further down that page that symlinking would be a bad idea when running 64-bit system, wich is what I have, so I don't think I'll risk it.

---

### Post by in-dust-rial on 2008-09-08
okay, so read the following posts as well and try to link just that file.
or just link the folder for the process of deinstalling and afterwords use the comment on removing link in nautilus (or simular).

and pls still try to remove with aptitude(and report).
thx

---

### Post by in-dust-rial on 2008-09-08
```
https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/130208
```
and still try google, its a known bug

good luck

---

### Post by Thomas Andresen on 2008-09-08
hmm...
```
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libgl1-mesa-dri
nvidia-glx
ubuntu-desktop

Install the following packages:
libgl1-mesa-swx11 [7.0.3~rc2-1ubuntu3 (hardy)]
libosmesa6 [7.0.3~rc2-1ubuntu3 (hardy)]

Downgrade the following packages:
xserver-xorg [1:7.3+10ubuntu10.2 (hardy-updates, now) -> 1:7.3+10ubuntu10 (hardy)]

Leave the following dependencies unresolved:
xserver-xorg recommends libgl1-mesa-dri
Score is 69

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libgl1-mesa-swx11 libosmesa6 
The following packages will be automatically REMOVED:
  libgl1-mesa-dri nvidia-glx ubuntu-desktop 
The following packages will be DOWNGRADED:
  xserver-xorg 
The following NEW packages will be installed:
  libgl1-mesa-swx11 libosmesa6 
The following packages will be REMOVED:
  libgl1-mesa-dri libgl1-mesa-glx nvidia-glx ubuntu-desktop 
0 packages upgraded, 2 newly installed, 1 downgraded, 4 to remove and 0 not upgraded.
Need to get 3817kB of archives. After unpacking 51.2MB will be freed.
Do you want to continue? [Y/n/?] 
```
does this look any good?

---

### Post by Thomas Andresen on 2008-09-08
hmm..
$sudo aptitude search glx | grep -i ^i
returns no lines..

is that a good sign?

---

### Post by in-dust-rial on 2008-09-08
read post below first!!!!!


well looks not tooo bad...
but maybe apt-get is the better choise then (over aptitude).
```
$apt-get remove 'NAME'
```
howto is here:
```
http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html
```
maybe the post here are also interesting for removing a 'mess'
```
http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/
```

because aptitude tries to remove dependencies,... maybe it is unecessary to remove desktop and stuff...
apt-get will not remove dependencies. try to remove the package via apt-get then.

BUT first:

```
This bug was fixed in the package linux-restricted-modules-2.6.24 - 2.6.24.9-8.20
```
so ```
$sudo aptitude update
$sudo aptitude seaarch linux-restricted-modules-2.6.24 
```

maybe thats what is needed.

i really have no idea what this 32bit 64 bit issue is, maybe should try to find a pro in #ubuntu channel in IRC!
(should be preinstalled in your ubuntu irc client)...

---

### Post by in-dust-rial on 2008-09-08
yeah, that 
aptitude search does not return a line menas there is no glx stuff installed...

you should NOW try:
```
$sudo aptitude update
$sudo aptitude search linux-restricted-modules-2.6.24
```
you need version .6.24.9-8.20
give it a try

---

### Post by in-dust-rial on 2008-09-08
and be sure, that you have 64 bit repos in your sources-list...
just in case there is something wrong...
because u need a 64bit nvidia driver, i dont know if there are different packages...

---

### Post by Thomas Andresen on 2008-09-08
the aptitude search provided:
```
p   linux-restricted-modules-2.6.24-16-generic              - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-16-openvz               - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled ke
p   linux-restricted-modules-2.6.24-16-rt                   - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-16-server               - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-16-xen                  - Non-free Linux 2.6.24 modules on Xen                             
p   linux-restricted-modules-2.6.24-18-generic              - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-18-openvz               - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled ke
p   linux-restricted-modules-2.6.24-18-rt                   - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-18-server               - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-18-xen                  - Non-free Linux 2.6.24 modules on Xen                             
i   linux-restricted-modules-2.6.24-19-generic              - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-19-openvz               - Non-free Linux 2.6.24 modules on OpenVZ Virtualization enabled ke
p   linux-restricted-modules-2.6.24-19-rt                   - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-19-server               - Non-free Linux 2.6.24 modules on x86/x86_64                      
p   linux-restricted-modules-2.6.24-19-xen                  - Non-free Linux 2.6.24 modules on Xen                             

```

---

### Post by in-dust-rial on 2008-09-08
```
$sudo aptitude show linux-restricted-modules-2.6.24-19-generic
```
there will be a lot of output, but in the beginning there is the version printed.
the bug report says you need version .6.24.9-8.20
if it is installed:

install build essential and try to install the driver you want.

i recommend useing envy (for this you dont need restricted modules package... i guess)
```
http://ubuntuforums.org/showthread.php?t=433023
```
it works with 64bit.

---

### Post by Thomas Andresen on 2008-09-08
hmm..

Version: 2.6.24.13-19.45

I would automatically assume that this is a later version, and it shouldn't be necessary to install another version, but then the issue would already have been solved, no?

---

### Post by Thomas Andresen on 2008-09-08
Also, when I enter Add/Remove...

I get the following error:
```
**Failed to check for installed and available applications**

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```
Should I do something about this or ignore it for the time being?

---

### Post by in-dust-rial on 2008-09-08
:O
you should do something about this. synaptic will help you find broken packages:
```
http://ubuntuforums.org/showthread.php?t=850532
```
=> replay to this topic if you got problems...


does this appear when pressing the "add/remove" button?
or when trying to install restricted drivers?
if the later:
you may try to reinstall the package
$sudo aptitude update 
$sudo aptitude reinstall linux-restricted-modules-2.6.24-19-generic


but i guess, now you need somebody who is familiar with the organization of package dependencies (so replay to the link above).
if there is wrong sources in the sources-list, it can be fatal at all.
( i really have no idea of 64bit sources (or even if they are different at all?))

good luck

p.s.:
to the nvidia problem, you just have to wait for the package to work again or to install envy.

OR go "system => hardware-drivers" that should also list restricted drivers.
but if something is broken you should fix it first, seems to be fundamentel to package manager.

---

### Post by Thomas Andresen on 2008-09-08
Problem solved..

I just went through the steps before updating the system, and envy worked fine :)

I must thank you for all the help, I really appreciate it.

---

### Post by in-dust-rial on 2008-09-08
:) np

but i realized that my help was not 100% the easy way always...
for example... i thought that maybe you need build-esential for building a kernel module...
but you need more you need the kernel headers for your kernel version...

its a great idea to install them, always :D

so good luck with your system

may the errors be conventional

---

