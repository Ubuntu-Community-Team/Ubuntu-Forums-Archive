---
title: "Problems installing ndiswrapper"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by elementboarder on 2006-01-25
I recently tried installing ndiswrapper via synaptics package manager, and I was able to install "ndiswrapper-utils_1.14....".  Then when i tried to install "ndisgtk", it couldnt find it.  When i double click on ndisgtk, it says that the archive type is not supported.  What am I doing wrong?  Any suggestions?  I think i will try just downloading it again.  Thanks.

---

### Post by jasmuz on 2006-01-25
open a terminal and type:

sudo apt-get install ndiswrapper-utils ndisgtk

That should be it

---

### Post by elementboarder on 2006-01-25
Would that require internet access?  I do not have internet access in ubuntu untill i install the driver.

---

### Post by elementboarder on 2006-01-27
Got some errors when i tried that....

harry@HARRY:~$ sudo apt-get install ndiswrapper-utils ndisgtk
Password:
Reading package lists... Done
Building dependency tree... Done
ndiswrapper-utils is already the newest version.
E: Couldn't find package ndisgtk

Then i tried...

harry@HARRY:~$ sudo dpkg --install ~/home/linux/ndiswrapper/ndisgtk-0.5_1ubuntu1_all.deb
dpkg: error processing /home/harry/home/linux/ndiswrapper/ndisgtk-0.5_1ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/harry/home/linux/ndiswrapper/ndisgtk-0.5_1ubuntu1_all.deb

Any ideas?

---

### Post by az on 2006-01-27
You are not typing in the correct path, it seems.

1.  ndisgtk would really be useful if it were on the cd.  As it is, you would already be running ndiswrapper if you were not trying to solve this.
2.  Don't type in the path by hand.  Use tab completion - it is faster and you avoid these problems

try

sudo dpkg -i h(TAB)  (press h and then tab without a space)
that should show you
/home/harry/home/

type l(TAB)
that should now be
/home/harry/home/linux/

and so on until you get to your file.  It will complete the file name too.  If you do have the correct file name, well, the file is borked.  Just install your driver by hand

sudo ndiswrapper -i Deskto(tab) and so on........
Good luck.

---

### Post by Reggie on 2006-01-27
[QUOTE=elementboarder]Would that require internet access?  I do not have internet access in ubuntu untill i install the driver.[/QUOTE]

I've been strungeling with ndiswrapper too. Now I'm using a more stable driver instead of ndiswrapper. Check out [http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware) . If your NIC is listed, I suggest you use this driver, it's really easy to install too.

---

### Post by elementboarder on 2006-01-27
[QUOTE=Reggie]I've been strungeling with ndiswrapper too. Now I'm using a more stable driver instead of ndiswrapper. Check out [http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware) . If your NIC is listed, I suggest you use this driver, it's really easy to install too.[/QUOTE]

I already have that, just havent got around to installing it... ill try right now thanks.

---

