---
title: "How to install a Debain package?"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by pf22 on 2009-06-17
I have installed duplicity from the default repository on my Ubuntu 8.04LTS server. However, there is a bug in duplicity that causes it to fail. 

The bug was fixed in duplicity 0.5.12 (see [http://savannah.nongnu.org/bugs/?24198](http://savannah.nongnu.org/bugs/?24198)). The version I have is 0.4.10.  I found a Debain package which is 0.5.16 ([http://packages.debian.org/squeeze/duplicity](http://packages.debian.org/squeeze/duplicity)) which should contain the fix.

The current version is installed using "apt-get install duplicity". I do not know how to install the above Debian package using apt-get. Can anyone help?

---

### Post by pytheas22 on 2009-06-17
Either double-click on the package to open an installer, or install it from the command line by typing:
```

sudo dpkg -i duplicity.deb
```

(You would need to cd into the directory first and change the package name as appropriate, of course.)

As long as the newer version of Duplicity doesn't depend on any other packages that are no in the Ubuntu repositories, this should work.  If you receive errors about unmet dependencies, you will need to hunt down those packages manually and install them first.

---

### Post by pf22 on 2009-06-17
I get an error running dpkg command.

root@leon:/usr/test# dpkg -i duplicity.deb
dpkg: error processing duplicity.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 duplicity.deb

---

### Post by pytheas22 on 2009-06-17
You need to change the command to contain the real name of the file--I just used 'duplicity.deb' as an example; the real file's name is probably different.  You also have to cd into the correct directory before running the command.  For example, if the file is saved on your desktop, you would need to type:
```

cd ~/Desktop
sudo dpkg -i **duplicity.deb**
```

Be sure to replace the part in bold with the correct name of the file.

Also, double-clicking the package would be much easier.  Is there a reason you can't just do that?

---

### Post by pf22 on 2009-06-17
Got it. Here is what I did.

1. Download Debian package

cd /tmp
wget [http://http.us.debian.org/debian/pool/main/d/duplicity/duplicity_0.5.16-1_i386.deb](http://http.us.debian.org/debian/pool/main/d/duplicity/duplicity_0.5.16-1_i386.deb)

2. Install

dpkg -i duplicity_0.5.16-1_i386.deb

Thanks very much for the help.

---

### Post by pastalavista on 2009-06-17
When you download a .deb file, you can just double-click the file and it will launch the gdebi package manager (included with 9.04) and install it and automatically create an apt listing for it in Synaptic. Just make sure you uninstall previous versions of the program from Synaptic first.

---

### Post by pf22 on 2009-06-18
Thanks for the info. I use commandline install because I am using ssh to connect to my server and my server does not have X-Window installed.

---

