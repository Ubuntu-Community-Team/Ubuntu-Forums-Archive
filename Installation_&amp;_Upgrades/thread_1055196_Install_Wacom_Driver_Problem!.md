---
title: "Install Wacom Driver Problem!"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-01-30
Hi there,

I attempted to install wacom driver on a tablet PC with Ubuntu 8.04. But when I entered the command
> sudo ./install
it showed this:
> root@ACERC100:/home/stephen/Desktop/linuxwacom-0.8.2-2/prebuilt# ./install
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......

Warning: wacomcpl requires tcl/tk being installed

There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

If you cannot solve this problem yourself, please send this
message to <yum@lists.linux.duke.edu>.

There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named cElementTree

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

If you cannot solve this problem yourself, please send this
message to <yum@lists.linux.duke.edu>.


Please install tcl/tk then run this script again

You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.


Does anyone know how to handle this issue? I appreciate your step by step guide.

---

### Post by Favux on 2009-01-30
Hi again huruixd,

I think you would be best served to install the 0.8.1-6 debs at Loic2's Wacom wiki.  Please find the link towards the top at the following HOW TO:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

I hope this is helpful.

---

### Post by huruixd on 2009-01-30
Thank you.

---

