---
title: "Elements for newest compiz"
date: 2008-11-13
forum: General Help
---

### Post by feelinggood on 2008-11-13
Anybody have any idea when elements for compiz might be updated for the 0.7.8 version of compiz.  Is there a workaround to make it compatible with the newest version.  Steve

---

### Post by eternalnewbee on 2008-11-13
> 
Anybody have any idea when elements for compiz might be updated for the 0.7.8 version of compiz. Is there a workaround to make it compatible with the newest version. Steve
You might be able to find the answer here:
[http://forlong.blogage.de/entries/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/entries/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

---

### Post by binbash on 2008-11-13
I am using compiz 0.7.8 and elements working fine for me

---

### Post by loomsen on 2008-11-13
Working fine here too, running 0.7.9 from shames repo, link to the howto in my sig...

---

### Post by feelinggood on 2008-11-13
This is what I get when trying to install elements.



steven@steven-laptop:~$ bash ./elementsinstall.sh

[sudo] password for steven: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package compiz-bcop is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source

However the following packages replace it:

  compiz-fusion-bcop

E: Package compiz-bcop has no installation candidate

mkdir: cannot create directory `/home/steven/.elements': File exists

--2008-11-13 10:35:02--  [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)

Resolving [www.elementsplugin.com](www.elementsplugin.com)... 69.89.31.238

Connecting to [www.elementsplugin.com|69.89.31.238|:80](www.elementsplugin.com|69.89.31.238|:80)... connected.

HTTP request sent, awaiting response... 200 OK

Length: 81464 (80K) [application/x-gzip]

Saving to: `/home/steven/.elements/elements.tar.gz'



100%[======================================>] 81,464       257K/s   in 0.3s    



2008-11-13 10:35:03 (257 KB/s) - `/home/steven/.elements/elements.tar.gz' saved [81464/81464]



images/

images/stars1.png

images/snow2.png

images/snow1.png

images/plugin-elements.png

images/fireflies2.svg

images/fireflies1.svg

images/bubbles2.png

images/bubbles1.png

images/autumn2.png

images/autumn1.png

elements.c

elements.xml.in

Makefile

plugin.info

install   : /home/steven/.compiz/plugins/libelements.so

install   : /home/steven/.compiz/metadata/elements.xml

install   : build/compiz-elements.schema

install   : /home/steven/.compiz/images/snow1.png

install   : /home/steven/.compiz/images/plugin-elements.png

install   : /home/steven/.compiz/images/fireflies2.svg

install   : /home/steven/.compiz/images/stars1.png

install   : /home/steven/.compiz/images/bubbles2.png

install   : /home/steven/.compiz/images/autumn1.png

install   : /home/steven/.compiz/images/autumn2.png

install   : /home/steven/.compiz/images/snow2.png

install   : /home/steven/.compiz/images/fireflies1.svg

install   : /home/steven/.compiz/images/bubbles1.png

Checking for Xgl: steven@steven-laptop:~$ not present. 

Detected PCI ID for VGA: 

Checking for texture_from_pixmap: present. 

Checking for non power of two support: present. 

Checking for Composite extension: present. 

Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.

Checking for Software Rasterizer: Not present. 

Checking for nVidia: present. 

Checking for FBConfig: present. 

Checking for Xgl: not present. 

/usr/bin/compiz.real (firefly) - Info: Loaded Texture firefly1.png

/usr/bin/compiz.real (firefly) - Info: Loaded Texture firefly2.png

/usr/bin/compiz.real (firefly) - Info: Loaded Texture firefly3.png

/usr/bin/compiz.real (firefly) - Info: Loaded Texture firefly4.png

/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png

/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png

/usr/bin/compiz.real (snow) - Info: Loaded Texture snowflake.png

/usr/bin/compiz.real (snow) - Warn: Texture not found : 

/usr/bin/compiz.real (snow) - Info: Loaded Texture star.png

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /home/steven/Desktop/Downloads/72037-cups_girl.png

steven@steven-laptop:~$

---

### Post by binbash on 2008-11-13
Please try this : 

$cd
$mkdir compiz
$sudo apt-get install compiz-fusion-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core

$git clone git://anongit.compiz-fusion.org/users/pat/elements
$cd elements
$make clean
$make
$make install

---

### Post by feelinggood on 2008-11-13
Everything works fine until this stage.  




steven@steven-laptop:~/elements$ make install
install   : /home/steven/.compiz/plugins/libelements.so
install   : /home/steven/.compiz/metadata/elements.xmlcp: cannot create regular file `/home/steven/.compiz/metadata/elements.xml': Permission denied
install   : /home/steven/.compiz/metadata/elements.xml
install   : build/compiz-elements.schema
install   : /home/steven/.compiz/images/snow1.pngcp: cannot create regular file `/home/steven/.compiz/images/snow1.png': Permission denied
install   : /home/steven/.compiz/images/snow1.png
install   : /home/steven/.compiz/images/plugin-elements.pngcp: cannot create regular file `/home/steven/.compiz/images/plugin-elements.png': Permission denied
install   : /home/steven/.compiz/images/plugin-elements.png
install   : /home/steven/.compiz/images/fireflies2.svgcp: cannot create regular file `/home/steven/.compiz/images/fireflies2.svg': Permission denied
install   : /home/steven/.compiz/images/fireflies2.svg
install   : /home/steven/.compiz/images/stars1.pngcp: cannot create regular file `/home/steven/.compiz/images/stars1.png': Permission denied
install   : /home/steven/.compiz/images/stars1.png
install   : /home/steven/.compiz/images/bubbles2.pngcp: cannot create regular file `/home/steven/.compiz/images/bubbles2.png': Permission denied
install   : /home/steven/.compiz/images/bubbles2.png
install   : /home/steven/.compiz/images/autumn1.pngcp: cannot create regular file `/home/steven/.compiz/images/autumn1.png': Permission denied
install   : /home/steven/.compiz/images/autumn1.png
install   : /home/steven/.compiz/images/autumn2.pngcp: cannot create regular file `/home/steven/.compiz/images/autumn2.png': Permission denied
install   : /home/steven/.compiz/images/autumn2.png
install   : /home/steven/.compiz/images/snow2.pngcp: cannot create regular file `/home/steven/.compiz/images/snow2.png': Permission denied
install   : /home/steven/.compiz/images/snow2.png
install   : /home/steven/.compiz/images/fireflies1.svgcp: cannot create regular file `/home/steven/.compiz/images/fireflies1.svg': Permission denied
install   : /home/steven/.compiz/images/fireflies1.svg
install   : /home/steven/.compiz/images/bubbles1.pngcp: cannot create regular file `/home/steven/.compiz/images/bubbles1.png': Permission denied
install   : /home/steven/.compiz/images/bubbles1.png
steven@steven-laptop:~/elements$

---

### Post by binbash on 2008-11-13
That is permission denied error , you have to get .compiz folder to your username and make sure it is writable.Or try sudo chmod 755 /home/steven/.compiz/ -R

after this it will work fine ;)

---

### Post by feelinggood on 2008-11-13
How do I put in the command or check on whether I can write to the file.

---

### Post by loomsen on 2008-11-13
If you wanna do it like that you also need to enable the userspace-filesystem plugin I think...

---

