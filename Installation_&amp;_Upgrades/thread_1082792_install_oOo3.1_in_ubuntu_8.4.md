---
title: "install oOo3.1 in ubuntu 8.4"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by 24dhruv on 2009-02-28
hello there,
i am using [COLOR="Red"]hardy-64bit[/COLOR] on a 64bit machine and already having oOo suit installed there i recently downloaded apropriate openoffice.org packages for my distribution i can't get any specific instructions for 64bit istalation so i thought i should ask you people before taking any risk

---

### Post by 24dhruv on 2009-02-28
for your king info i downloaded this package
OOo_3.0.1_LinuxX86-64_install_en-US_deb.tar.gz

---

### Post by taurus on 2009-02-28
Maybe try something like (assuming you've saved it to your desktop)

```
cd ~/Desktop
tar xvzf OOo_3.0.1_LinuxX86-64_install_en-US_deb.tar.gz
cd OOo_3.0.1_LinuxX86-64_install_en-US 
(or whatever the new directory is)
sudo dpkg -i *.deb
```

---

### Post by 24dhruv on 2009-02-28
i will try this and i know it will work but i need to know that what is the abreviation of dpkg and what will the tag -i will do?

---

### Post by 24dhruv on 2009-02-28
some more details  :

i extracted the file on my desktop
so here is the hierarchy

OOO300_m15_native_packed-1_en-US.9379

```
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379$ dir
DEBS  licenses	readmes  update
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379$
``` 

in debs there are .deb files which i installedand there was one folder named "desktop-integration" there is one .deb file so i go there and try to install it but failed in that the file name is "openoffice.org3.0-debian-menus_3.0-9376_all.deb"
i have tried twice to install this file one i failed so i UNINSTALLED THE OLD OPENOFFICE.ORG again i tried again failed 
and the messages i have got are here 


```
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.0-debian-menus_3.0-9376_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9376_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9376_all.deb
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ 
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ 


```

---

### Post by 24dhruv on 2009-02-28
is there any problem i am just checking by restarting

---

### Post by taurus on 2009-02-28
It's a package manager for Debian.  It is  a  tool to install, build, remove and manage Debian packages (.deb).  

```

ACTIONS
       -i, --install package_file...
              Install the package. If --recursive or -R option  is  specified,
              package_file must refer to a directory instead.

              Installation consists of the following steps:

              1. Extract the control files of the new package.

              2.  If  another version of the same package was installed before
              the new installation, execute prerm script of the old package.

              3. Run preinst script, if provided by the package.

              4. Unpack the new files, and at the same time back  up  the  old
              files, so that if something goes wrong, they can be restored.

              5.  If  another version of the same package was installed before
              the new installation, execute the postrm script of the old pack&#8208;age.  Note that this script is executed after the preinst script of the new package, because new files are written  at  the  same time old files are removed.

              6.  Configure the package. See --configure for detailed information about how this is done.

```

---

### Post by WildeBeest on 2009-02-28
Try this, it worked for me.

[http://howtoforge.org/how-to-install-openoffice-3.0.0-on-ubuntu-8.04]("http://howtoforge.org/how-to-install-openoffice-3.0.0-on-ubuntu-8.04")

---

### Post by 24dhruv on 2009-02-28
as i told earlier the desktop integration package is not working for me i mean not getting installed with dpkg
so should i need to uninstall some packages which are conflictiong?if yes then tell me
here is the screenshot of my synaptic package manager pls check

[http://picasaweb.google.com/lh/photo/j-m73mBQFu9evdRgkvANfw?authkey=Gv1sRgCKLU8JrDtYOgRA&feat=directlink](http://picasaweb.google.com/lh/photo/j-m73mBQFu9evdRgkvANfw?authkey=Gv1sRgCKLU8JrDtYOgRA&feat=directlink)

---

### Post by taurus on 2009-02-28
You still have openoffice.org-gtk (version 2.4) on your machine.  How about remove it also?  You need to close down synaptic first before you can run the dpkg command.

---

### Post by 24dhruv on 2009-02-28
i unistalled that packege by sy.pack. man. ithink it doesnt make any diffrence is it??
still getting errors

```
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: status database area is locked by another process
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.0-debian-menus_3.0-9376_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9376_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9376_all.deb
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ 
dhruv@dhruv-laptop:~/Desktop/OOO300_m15_native_packed-1_en-US.9379/DEBS/desktop-integration$ 

```

---

### Post by 24dhruv on 2009-02-28
what should i do now :confused: the deb package of desktop integration is not getting install please guide me and is there any other way to get started with OOo untill that?

---

### Post by 24dhruv on 2009-03-01
finally what i do is uninstalled all the OOo packages by

```
sudo apt-get remove openoffice*
```

then istalled the new packages worked

---

