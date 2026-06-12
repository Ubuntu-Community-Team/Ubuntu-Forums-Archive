---
title: "apt/ldconfig problem"
date: 2008-11-18
forum: General Help
---

### Post by galning on 2008-11-18
I have a slight problem with my laptop...  I somehow managed to break apt, and ldcofig.

Last monday i was updating Xubuntu 8.04 (i think the update was ldconfig-gnome or something of the like) when the update randomly stopped, and i got logged out.  I figured it was all part of the process, and continued to use it normally.  The computer then started to run really really hot, but i didn't think it was related...

The next morning, i went to book it up, and i got an error while trying to load up the system drivers.  I fsck'd and fixed all the problems it encountered.  It started working again, marginally.  I went to run amarock, and realized that i didn't quite fix everything, as it didn't load up.  I went into synaptic, and it told me to configure dpkg.  While configuring dpkg, I got an error that part of python-apt wasn't working, because apparently part of the python 2.5 folder was missing.  I tried apt-getting python-apt and got this error:

```
me@mycomputer:~$ sudo apt-get install python-apt
Reading package lists... Done
Building dependency tree
Reading state information... Done
python-apt is already the newest version.
The following packages were automatically installed and are no longer required:
ttf-sil-andika libsdl-ttf2.0-0 libsdl-pango1 libsdl-mixer1.2 ttf-sil-doulos
libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-apt (0.7.4ubuntu7.3) ...
file does not exist: /usr/lib/python2.5/site-packages/apt/__init__.py
file does not exist: /usr/lib/python2.5/site-packages/apt/cache.py
file does not exist: /usr/lib/python2.5/site-packages/apt/cdrom.py
file does not exist: /usr/lib/python2.5/site-packages/apt/debfile.py
file does not exist: /usr/lib/python2.5/site-packages/apt/package.py
file does not exist: /usr/lib/python2.5/site-packages/apt/progress.py
file does not exist: /usr/lib/python2.5/site-packages/aptsources/__init__.py
file does not exist: /usr/lib/python2.5/site-packages/aptsources/distinfo.py
file does not exist: /usr/lib/python2.5/site-packages/aptsources/distro.py
file does not exist: /usr/lib/python2.5/site-packages/aptsources/sourceslist.py
pycentral: pycentral pkginstall: error byte-compiling files (10)
pycentral pkginstall: error byte-compiling files (10)
dpkg: error processing python-apt (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
python-apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried re-installing python (version 2.52) and it still didn't fix itself.

Jump ahead a few days.  I figured that i would just re-install apt via the ubuntu repositories.  I ran the command 
```
sudo dpkg -i apt_0.7.9ubuntu17.1_i386.deb 
```
It worked fine, until i got the following error regarding ldconfig:
```
(Reading database ... 125275 files and directories currently installed.)
Preparing to replace apt 0.7.9ubuntu17.1 (using apt_0.7.9ubuntu17.1_i386.deb) ...
Unpacking replacement apt ...
Setting up apt (0.7.9ubuntu17.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libmysqlclient.so.15 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libmysqlclient.so.15.0.0 is not an ELF file - it has the wrong magic bytes at the start.
```

I have no idea how to fix this, and i can't find ldconfig to attempt to re-install it.  Does anyone know how I could attempt to fix this?  Or would it be better for me to just re-install Xubuntu 8.04?

---

