---
title: "Canon mp540 drivers installed but printer does not work"
date: 2010-10-20
forum: Hardware
---

### Post by jacopastorius82 on 2010-10-20
I installed printer drivers, the i went to "administration>printers>" created a new printer, selected cnijusb:/dev/usb/lp0 which is mp540 the selected Canon onnext page but mp540 is not in the list. So i tried mp520 and mp 500 but printer does not print. 
Any ideas?

---

### Post by jacopastorius82 on 2010-10-21
anyone can help me? :(

---

### Post by pajeck on 2010-11-13
I had a problem getting my Canon MP540 printer to work with Ubuntu10.10,this is how I solved the problem:

1. Download linux deb drivers from Canon (there are two - cnijfilter-common_3.00-1_i386 and cnijfilter-mp540series_3.00-1_i386) and get 
   libcupsys2_1.3.9-17ubuntu3.9_all.deb from [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/).

2. Extract and install cnijfilter-common_3.00-1_i386.deb.

3. Install libcupsys2_1.3.9-17ubuntu3.9_all.deb.

4. Extract and install cnijfilter-mp540series_3.00-1_i386.deb.

5. I got an error message when I tried to use the printer this was resolved by this command 'sudo chown root  
   /usr/lib/cups/filter/pstocanonij'.

Hope it works for you.

---

### Post by Montfinal on 2011-04-24
Hi,

yes, this works ! However I find it appealing to repackage the drivers in order to remove the libcupsys2 dependency once and forever.

I read this thread [here]("http://ubuntuforums.org/showthread.php?t=1305248"), but somehow this doesn't work anymore under Ubuntu 10.04, the dpkg-deb -x doesn't extract the "control" file as described.

Here how I finally succeeded to repackage the drivers:

From the Canon website or elsewhere, get the two installation packages:

cnijfilter-common_3.00-1_i386.deb
cnijfilter-mp540series_3.00-1_i386.deb

1. in the directory where they are, type

> dpkg-deb -e cnijfilter-common_3.00-1_i386.deb tempThis will extract the control file and others to the "temp" directory. 
2. Edit the control file (gedit control), change the reference libcupsys2 into libcups2 and save the file
3. Now create a subdirectory "DEBIAN" under the temp directory and move all the previously extracted files there, including the one you modified.
4. Run > dpkg-deb -x cnijfilter-common_3.00-1_i386.deb temp to extract the rest
5. Now rebuild the package with > dpkg -b temp cnijfilter-common_3.00-1_i386.deb
6. Delete the temp directory

Now follow steps 1 to 6 with cnijfilter-mp540series_3.00-1_i386.deb.

Then install the packages by double-clicking them,
1st cnijfilter-common_3.00-1_i386.deb, then cnijfilter-mp540series_3.00-1_i386.deb

Goto System -> Administration -> Printing and add the printer.

In my case, I had as well the error "scheduler could not execute a filter" when I wanted to use the printer. Apparently the pstocanonij was not owned by root (whysoever).

Changing its owner to root as described in the post above made the printer work.

Cheers

Montfinal

---

