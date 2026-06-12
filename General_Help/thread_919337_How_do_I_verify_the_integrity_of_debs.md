---
title: "How do I verify the integrity of debs?"
date: 2008-09-13
forum: General Help
---

### Post by shaggy999 on 2008-09-13
I have mirrored the main, restricted, universe, and multiverse sections hardy, hardy-updates, and hardy-security to an external usb drive which recently had some filesystem errors on it. Everything seems ok, but I would like to be able to verify the integrity of my debs. Does anyone know how to do this? I know it should be possible because if you do 'apt-cache show packagename' it always has an MD5sum line. I searched through the repository but couldn't find anything. The only package I could find was a package called debsums, but that program looks like it just verifies that the files installed to your system from a package are good, it doesn't seem to actually check the deb file.

Anyone have any ideas? I need to somehow be able to extract the MD5sum from the package info and then run md5sum on the deb file and compare the two results.

---

### Post by Pro-reason on 2008-09-13
To extract the checksum from the package (e.g. *lzop*):

```

apt-cache show *lzop* | grep MD5

```

To generate a checksum for the file you have:

```

md5sum *lzop_1.01-4_i386.deb*

```

With a simple bash script, you could automate the checking of hundreds of packages.

---

### Post by ad_267 on 2008-09-13
You could use this line to get the MD5 of the package from apt-cache show:
```
apt-cache show package-name | grep MD5sum | awk '{print $2}'
```

And then to get the MD5 sum from the .deb:
```
md5sum package-name_version.deb | awk '{print $1}'
```

---

### Post by aysiu on 2008-09-14
Doesn't the package manager already verify them?

---

### Post by Pro-reason on 2008-09-14
> **aysiu said:**
> Doesn't the package manager already verify them?

I believe he wants to check them *en masse*, before installing any.

---

### Post by shaggy999 on 2008-09-14
Thanks for the input. I've now partially solved my problem with a bash script. Here it is for others that are interested:

```

#!/bin/bash

FILENAME=$1

#Get what package this deb file provides
PACKAGE=`dpkg-deb -f $FILENAME Package`

#Get MD5sum listed for package
PACKAGE_MD5=`apt-cache show $PACKAGE | grep MD5sum | awk '{print $2}'`
#Calculate actual MD5sum
ACTUAL_MD5=`md5sum $FILENAME | awk '{print $1}'`

#Compare MD5sums
if ["$PACKAGE_MD5" -eq "$ACTUAL_MD5"]; then
   echo "OK";
else
   echo "BAD";
fi

```

This code is not foolproof, though and needs to be reworked. Sometimes there are multiple debs providing the same package, each with a different MD5sum. So when you "apt-cache search $PACKAGE | grep MD5sum" you will get *multiple* lines, one for each version. The code above needs to be reworked so that awk provides a *list* of MD5sums and instead of a simple if-then clause we a do a loop through the list and if any of the md5sums match we mark the file good, else bad. I'm not in the mood to do that right now, but I thought I'd post what I have at this point so if anybody else runs into this problem they know where to start. Once I get around to implement this fix I'll post the code.

Oh, one last thing. This script is obviously for a single deb file. The way to run it on an entire cache of debs is:

```
find /root/dir/of/mirror -iname="*.deb" -exec ./scriptname.sh {} \;
```

Weee!

---

### Post by ad_267 on 2008-09-14
Maybe it would be a better idea to compare the version from "apt-cache show" with the version of the package and then only compare the md5sum for the correct version.

---

### Post by shaggy999 on 2008-09-14
True, but my reasoning for going through the loop instead of checking the version is

1) Checking for the version seems like it would complicate things because I don't think there is an easy way to do that (I have to do a lot more comparisons of different data and saving of variables) and

2) We know that if any of the MD5sums from apt-cache match the deb file then that deb file is good and since the MD5sum from apt-cache is pre-calculated it practically costs nothing in terms of computation time and the fix is easy for me to come up with and understand in terms of actually producing code that I'm sure will work.

---

### Post by shaggy999 on 2008-09-14
Ok, I got a perfect script now!

```

#Get filename
FILENAME=$1

#Query what package the deb file provides
PACKAGE=`dpkg-deb -f $PACKAGE Package`

#Calculuate MD5SUM of the file
ACTUAL_MD5=`md5sum $FILENAME | awk '{print $1}'`

#The meat of the script is right here
#Compare actual md5sum to known md5sums
RESULTS=`apt-cache show $PACKAGE | grep MD5sum | awk -v md=$ACTUAL_MD5 'BEGIN {res=BAD} {if (md == $2) res="OK"} END {print res}'`

```

You run the code like this: find /path/to/mirror -iname "*.deb" -exec ./scriptname {} \;

---

### Post by Michael-Williams on 2010-12-22
Deleted by, Michael-Williams. Post was retarded and uncalled for.

---

### Post by Michael-Williams on 2010-12-22
Or, better yet, How do I check the whole entire system file integrity. There is something wrong. Errors all over from trying to "make" things and there are half "make" crap lingering all over my file system. I really need some help here. All I can find is a bunch of code that I have no idea what to do with if my life depended on it. Make the stuff yourself, if you design some software. Don't make others do your dirty work for you. People like me get stuck pulling their hair out and screaming weird noises and smashing keyboards. I get error after error, too long to list. glx, files not found or don't exist. It's been five or so years since my last encounter with linux, its gotten really bad. Whats up with the 9.x and higher. Yuk, a bunch of badly coded Distros. Video drivers failing.......blah blah blah.

---

### Post by Michael-Williams on 2010-12-22
> **Michael-Williams said:**
> How do I start a brand spanking new post thread for a new problem. Not listed in help. Not found in any thread or post of how to START A NEW POST. HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
compiz --debug
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcore.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libmove.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libresize.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libplace.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libdecoration.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libanimation.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libccp.so : No such file or directory
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsession.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libworkarounds.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsvg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libtext.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libshift.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libpng.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcommands.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libgnomecompat.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libregex.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libresizeinfo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsplash.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libmousepoll.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libneg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libextrawm.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libimgjpeg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcrashhandler.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libvpswitch.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libput.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libdbus.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libfirepaint.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libvideo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libkdecompat.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libannotate.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libring.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libwobbly.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libanimationaddon.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libthumbnail.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libfade.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcube.so : No such file or directory
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libgears.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/lib3d.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libscale.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/librotate.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcubeaddon.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libscaleaddon.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libexpo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libezoom.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libstaticswitcher.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libbench.so : No such file or directory

Hangs until Ctrl+C then goes back to no cube and no fires or explosions. :(

---

