---
title: "HP C310 hplip-3.10.9 on Ubuntu 10.10"
date: 2010-12-14
forum: Hardware
---

### Post by Joshimitsu on 2010-12-14
Hi everyone.

I'm trying to install my HP Photosmart Perm C310 and have tried to  install hplip.  I get the following error in terminal when I run sh  hplip-3.10.9.run

error: 'make' command failed with status code 2

I've done a few searches online and a few suggest there's a space in the  path name, but that's not the case with me.  There's no space in the  path name.

Any ideas what I need to to?

Thanks

---

### Post by Joshimitsu on 2010-12-14
Really noob question, but what does the following mean?

[https://answers.launchpad.net/hplip/+faq/1356](https://answers.launchpad.net/hplip/+faq/1356)

> Following diff content is for HPLIP Auto installation on Ubuntu Maverick.
 open installer/distroes.dat file in the hplip-3.10.9 directory and apply the following diff patch content on the file.
from hplip-3.10.9 directory launch ./install.py file to continue auto installation.
 Thanks,
Naga Samrat Chowdary, Narla
 Index: installer/distros.dat
===================================================================
--- installer/distros.dat	(revision 14020)
+++ installer/distros.dat	(revision 14021)
@@ -3777,14 +3777,14 @@
 # ****************************************
 [ubuntu]
 index=12
-versions=5.04,5.1,6.06,6.10,7.04,7.10,8.04,8.04.1,8.04.2,8.10,9.04,9.10,10.04
+versions=5.04,5.1,6.06,6.10,7.04,7.10,8.04,8.04.1,8.04.2,8.10,9.04,9.10,10.04,10.10
 display_name=Ubuntu
 alt_names=kubuntu,edubuntu,xubuntu


Am I meant to just copy and paste the above into distroes.dat file?

---

### Post by Joshimitsu on 2010-12-16
I managed to install hplip by following the instructions in the link in post 2.  I got a nice little hp logo in the status bar top right-hand corner of my desktop.  The hp-setup also allowed me to find my printer wirelessly, but when I send a test page to the printer it says a filter is missing.

Could someone tell me how I can find out what filter is missing, as it doesn't say in the notification?

Thanks

---

### Post by Joshimitsu on 2010-12-17
Okay, I've finally managed to install this printer.  I've noted down what I had to do which might be useful for anyone else trying to get this thing to work.

My setup:

Ubuntu 10.10 64-bit
HP Photo Prem C310 wireless

The installation was done in two parts.  If you're lucky, part one should be all you need.  If that doesn't work go onto part two.

**Part 1.**

This part was taken from here: [http://newyork.ubuntuforums.org/showthread.php?t=1630487&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1630487&page=2) 

1.  Download hplip from hp website and leave the file hplip-3.10.9.run on your desktop.

2.  Open terminal and run:

```
cd ~/Desktop
sh hplip-3.10.9.run
```This will start the installer and create a folder called hplip-3.10.9 on your desktop.  You can close the terminal at this point.

4. Open this folder (hplip-3.10.9) and then open the folder called installer

5. In the installer folder open the file called distros.dat

6. Select all the text in this file and delete it. Save the file - so it is empty.

7. Open browser and navigate to URL [http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat](http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat) and copy all the text.

8. Go back to Desktop/hplip-3.10.9/installer/ and open the empty distros.dat file

9. Paste the text from the web site into the empty file - save the file and close

***EDIT***  Alternatively, just download the distros.dat file I've attached here at the end of this post and replace the one in your installer folder (you will need to unzip it first).

10.  Close all windows and go back to the desktop, open the hplip-3.10.9 folder and double click the file called hplip-install and choose Run in Terminal.

... and everything should install!  But when I did this I still had some dependencies missing.  


**Part 2.**

**If hplip installed successfully but you get a 'missing filter' or 'foomatic' error when trying to print, read the numbered points below.**

If you get a 'missing dependencies' error like below, keep reading from here.

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: This installer cannot install 'python-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

As you can see, my system had 5 missing dependencies, but it only tells me the name of the first one so I went back into terminal and run:

```
hp-check
```This gives you a long list of stuff. Scroll down to the COMPILE AND RUNTIME DEPENDENCIES section and take a look at what you need.  Go into the Synaptics repositories and do a search for each one.  For example, I had the CUPS DDK (CUPS development kit) missing so I typed "CUPS" in Synaptic and installed "cupsddk".

I also had CUPS DEV missing, so I installed anything that said "cups dev".  Yea, not a very scientific approach but I had no idea what I needed so I went for brute force.

Once you're done with this, try the installation again and see if there are any dependencies you've missed.  I allowed the installation to complete to make sure it goes through to the end.  You will be prompted to select your printer and send a test page.  At this point you will probably get a 'missing filters' error or a 'foomatic' error.  To resolve this I did the following.

1.  Go to System>Administration>Printing and delete the printer you just installed

2.  Uninstall hplip with:

```
cd ~/Desktop/hplip-3.10.9
sudo make uninstall
```then run:

```
sudo rm -rf /usr/share/hplip
```and finally:

```
sudo rm -rf /etc/hp

sudo rm -rf ~/.hplip

sudo rm -rf /var/lib/hp
```3.  Next you need to configure some of the runtime dependencies (I think that's what its called!).

In terminal, make sure your are still in cd ~/Desktop/hplip-3.10.9

First:

```
make clean
```Then:

```
./configure --prefix=/usr --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --enable-foomatic-ppd-install --enable-hpijs-install --disable-policykit --disable-cups-drv-install --disable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --disable-fax-build --disable-foomatic-rip-install --enable-foomatic-rip-hplip-install
```Next if your machine is 64-bit run:

```
./configure --prefix=/usr --libdir=/usr/lib64
```Then run:

```
make
```Once this finishes:

```
sudo make install
```And that should be it!  The hp-gui should start up automatically allowing you to finish the installation.  If it doesn't come up automatically, in terminal run:

```
hp-toolbox
```which should bring up the hp screen.  Go to Device>Setup Device and add your printer.  This time the test page should print successfully.

Please note that I'm a complete noob so the above was done through trial and error whilst not really understanding what I was doing.  I'm sure there's an easier way of installing this printer but I couldn't find it!  Hopefully someone can make use of this.

Thanks

---

### Post by bvpainter on 2010-12-18
I did all this and still got the same missing foomatic message.

---

### Post by ghostborg on 2010-12-18
He seems to have moved his page around, I found it here.

[http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat]("http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat")

If he moves it again just start at [http://jamesmcdonald.id.au](http://jamesmcdonald.id.au) and look for his article about HP Officejet Pro 8500A A910a on Ubuntu 10.10

---

### Post by xpresshred on 2010-12-18
Hi,thanks for sharing the information regarding to installation of **[B]HP C310 hplip-3.10.9 on Ubuntu 10.10. Really very nice steps are provided by you.Thanks a lot again for sharing the information...**
[/B]

---

### Post by Joshimitsu on 2010-12-18
> **bvpainter said:**
> I did all this and still got the same missing foomatic message.

Hi bvpainter,

Your details say that you're on Karmic, is that still right?  If so, you shouldn't really need my steps as hplip supposedly installs fine on everything up to 10.04.

Did you try installing hplip without any modifications?  What was the result?
Is your machine 32 or 64 bit?
During the installation were you warned of any missing dependencies as I mentioned in part 1?

Also, please could you post the result of hp-check.

Thanks

---

### Post by Joshimitsu on 2010-12-18
> **ghostborg said:**
> He seems to have moved his page around, I found it here.

[http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat](http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat)

If he moves it again just start at [http://jamesmcdonald.id.au](http://jamesmcdonald.id.au) and look for his article about HP Officejet Pro 8500A A910a on Ubuntu 10.10

Thanks ghostborg, I've edited my post with the correct link.

> **xpresshred said:**
> Hi,thanks for sharing the information regarding to installation of **[B]HP C310 hplip-3.10.9 on Ubuntu 10.10. Really very nice steps are provided by you.Thanks a lot again for sharing the information...**
[/B]

No problem xpresshred, glad you found it useful.

---

### Post by zeta30 on 2010-12-25
[Joshimitsu]("http://ubuntuforums.org/member.php?u=1098241")

Thank you so much for this tutorial. It worked perfectly the first time I tried.

---

### Post by Virus692 on 2011-01-04
> **Joshimitsu said:**
> Okay, I've finally managed to install this printer.  I've noted down what I had to do which might be useful for anyone else trying to get this thing to work.

My setup:

Ubuntu 10.10 64-bit
HP Photo Prem C310 wireless

The installation was done in two parts.  If you're lucky, part one should be all you need.  If that doesn't work go onto part two.

**Part 1.**

This part was taken from here: [http://newyork.ubuntuforums.org/showthread.php?t=1630487&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1630487&page=2) 

1.  Download hplip from hp website and leave the file hplip-3.10.9.run on your desktop.

2.  Open terminal and run:

```
cd ~/Desktop
sh hplip-3.10.9.run
```This will start the installer and create a folder called hplip-3.10.9 on your desktop.  You can close the terminal at this point.

4. Open this folder (hplip-3.10.9) and then open the folder called installer

5. In the installer folder open the file called distros.dat

6. Select all the text in this file and delete it. Save the file - so it is empty.

7. Open browser and navigate to URL [http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat](http://jamesmcdonald.id.au/blog/wp-content/uploads/2010/11/distros.dat) and copy all the text.

8. Go back to Desktop/hplip-3.10.9/installer/ and open the empty distros.dat file

9. Paste the text from the web site into the empty file - save the file and close

***EDIT***  Alternatively, just download the distros.dat file I've attached here at the end of this post and replace the one in your installer folder (you will need to unzip it first).

[COLOR=Red]Now at this point, theoretically you should be able to just open terminal again, run

[/COLOR]```
[COLOR=Red]
[/COLOR][COLOR=Red]cd ~/Desktop[/COLOR][COLOR=Red]
sh hplip-3.10.9.run[/COLOR]
```[COLOR=Red]and everything should install.  But when I did this I still had some dependencies missing.  
[/COLOR] 


Error :
If you just re run the Red text you will simply over write the file and have the same issues!!!

what you want to do is:
```

Close all windows - back to Desktop. 
Open the **hplip-3.10.9** folder 
Double click on a file called **hplip-install** 
choose Run in Terminal.

```

---

### Post by Joshimitsu on 2011-01-04
> **Virus692 said:**
> Error :
If you just re run the Red text you will simply over write the file and have the same issues!!!

what you want to do is:
```

Close all windows - back to Desktop. 
Open the **hplip-3.10.9** folder 
Double click on a file called **hplip-install** 
choose Run in Terminal.

```

Thanks Virus692, I've edited my post as you've suggested.  :-)

---

### Post by Lluispa on 2011-01-04
Joshimitsu, Thanks a lot for the post, It has been usefully for me, 

Just one question, after install the HPLIP -the first step has been enough for me-, it has created a lot of files and folders in my home directory!! do you know if I can delete or hide all of them?

Thanks again
Lluispa
Ubuntu 10.10 - 64 bits

---

### Post by Joshimitsu on 2011-01-05
> **Lluispa said:**
> Joshimitsu, Thanks a lot for the post, It has been usefully for me, 

Just one question, after install the HPLIP -the first step has been enough for me-, it has created a lot of files and folders in my home directory!! do you know if I can delete or hide all of them?

Thanks again
Lluispa
Ubuntu 10.10 - 64 bits

Hmm, I've done this on three different machines and it's never created folders in my home directory.  What folders are they and what do they contain?

---

### Post by Lluispa on 2011-01-07
Good Morning Joshimitsu

Below I have attached the folder & files list appear in may home folder after installation...

Anyway after your reply, I have moved all of this files to one "temporal" folder and if all working well in a few weeks I will remove it...., at the moment, all test I have done with the printer (HP OfficejetA Plus) and scanner are working well

Maybe it is not from your "steps", as I have done some tries to install the HPLIP drivers before find your post!! and I'm not sure exactly when appear it [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Thanks 
Lluispa
Ubuntu 10.10 - 64 bits

list of files & folders
drwxr-----  2 lluis lluis   4096 2011-01-04 22:29 installer
drwxr-----  2 lluis lluis   4096 2011-01-04 22:29 base
drwxr----- 17 root  root    4096 2011-01-04 22:28 hplip-3.10.9
drwxr-----  3 lluis lluis   4096 2010-09-26 19:12 pcard
drwxr-----  2 lluis lluis   4096 2010-09-26 19:12 ip
drwxr-----  4 lluis lluis   4096 2010-09-26 19:12 doc
drwxr-----  2 lluis lluis   4096 2010-09-26 19:12 ui
drwxr-----  9 lluis lluis   4096 2010-09-26 19:12 prnt
drwxr-----  4 lluis lluis   4096 2010-09-26 19:12 scan
drwxr-----  2 lluis lluis   4096 2010-09-26 19:12 ui4
drwxr-----  2 lluis lluis   4096 2010-09-26 19:11 plugins
drwxr-----  2 lluis lluis   4096 2010-09-26 19:11 copier
drwxr-----  5 lluis lluis   4096 2010-09-26 19:11 fax
drwxr----- 10 lluis lluis   4096 2010-09-26 19:11 data
drwxr-----  4 lluis lluis   4096 2010-09-26 19:11 io
drwxr-----  4 lluis lluis   4096 2010-09-26 19:11 ppd
-rwxr-----  1 lluis lluis 825001 2010-09-26 19:09 configure
-rw-r-----  1 lluis lluis 560459 2010-09-26 19:09 Makefile.in
-rw-r-----  1 lluis lluis 285985 2010-09-26 19:09 aclocal.m4
-rw-r-----  1 lluis lluis  29138 2010-09-26 19:09 cups_drv.inc
-rw-r-----  1 lluis lluis  41593 2010-09-26 19:09 foomatic_drv.inc
-rw-r-----  1 lluis lluis     29 2010-09-26 19:09 unreleased.inc
-rwxr-----  1 lluis lluis  21052 2010-09-26 19:08 configure.in
-rwxr-----  1 lluis lluis   8511 2010-09-26 19:07 align.py
-rwxr-----  1 lluis lluis  32226 2010-09-26 19:07 check.py
-rwxr-----  1 lluis lluis   6444 2010-09-26 19:07 clean.py
-rwxr-----  1 lluis lluis   9168 2010-09-26 19:07 colorcal.py
-rw-r-----  1 lluis lluis  17941 2010-09-26 19:07 COPYING
-rwxr-----  1 lluis lluis  18229 2010-09-26 19:07 copyright
-rwxr-----  1 lluis lluis  28704 2010-09-26 19:07 dat2drv.py
-rwxr-----  1 lluis lluis   2418 2010-09-26 19:07 devicesettings.py
-rwxr-----  1 lluis lluis  24861 2010-09-26 19:07 fab.py
-rwxr-----  1 lluis lluis   2299 2010-09-26 19:07 faxsetup.py
-rwxr-----  1 lluis lluis   5477 2010-09-26 19:07 firmware.py
-rwxr-----  1 lluis lluis   6992 2010-09-26 19:07 hpdio.py
-rw-r-----  1 lluis lluis   1112 2010-09-26 19:07 hplip.conf.in
-rw-r-----  1 lluis lluis    344 2010-09-26 19:07 hplip.desktop.in
-rwxr-----  1 lluis lluis     43 2010-09-26 19:07 hplip-install
-rw-r-----  1 lluis lluis  20151 2010-09-26 19:07 hplip.list.in
-rw-r-----  1 lluis lluis     83 2010-09-26 19:07 hplip.state
-rw-r-----  1 lluis lluis    304 2010-09-26 19:07 hplip-systray.desktop.in
-rwxr-----  1 lluis lluis  18593 2010-09-26 19:07 hpssd.py
-rwxr-----  1 lluis lluis   6338 2010-09-26 19:07 info.py
-rw-r-----  1 lluis lluis    345 2010-09-26 19:07 init-iptables-firewall
-rw-r-----  1 lluis lluis    799 2010-09-26 19:07 __init__.py
-rwxr-----  1 lluis lluis    532 2010-09-26 19:07 init-suse-firewall
-rwxr-----  1 lluis lluis   7674 2010-09-26 19:07 install.py
-rwxr-----  1 lluis lluis   6887 2010-09-26 19:07 levels.py
-rwxr-----  1 lluis lluis   2541 2010-09-26 19:07 linefeedcal.py
-rwxr-----  1 lluis lluis  11572 2010-09-26 19:07 makecopies.py
-rw-r-----  1 lluis lluis  26071 2010-09-26 19:07 Makefile.am
-rwxr-----  1 lluis lluis   5744 2010-09-26 19:07 makeuri.py
-rwxr-----  1 lluis lluis   3202 2010-09-26 19:07 pkservice.py
-rwxr-----  1 lluis lluis  15418 2010-09-26 19:07 plugin.py
-rwxr-----  1 lluis lluis   2393 2010-09-26 19:07 pqdiag.py
-rwxr-----  1 lluis lluis   4024 2010-09-26 19:07 print.py
-rwxr-----  1 lluis lluis   2696 2010-09-26 19:07 printsettings.py
-rwxr-----  1 lluis lluis   8190 2010-09-26 19:07 probe.py
-rwxr-----  1 lluis lluis   5020 2010-09-26 19:07 query.py
-rwxr-----  1 lluis lluis  45196 2010-09-26 19:07 scan.py

---

