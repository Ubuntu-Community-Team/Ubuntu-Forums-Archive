---
title: "Setting up Canon Pixma IP1500"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by tjb891 on 2006-09-01
Does anyone know how to set a  Canon Pixma IP1500 with Ubuntu 6.06?

---

### Post by awkward1234 on 2006-09-01
you could try 

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

or these instruction, if your feeling technical, might be a bit old tho

[http://ubuntuforums.org/showthread.php?t=56725](http://ubuntuforums.org/showthread.php?t=56725)

---

### Post by Dr. Nick on 2006-09-01
almost all modern canon printers i have used will run off the bjc7000/ bjc 800 drivers, Including my pixma 3000

---

### Post by uxworks on 2006-10-21
Let me share you with my Pixma ip1500 on Ubuntu (Dapper) experience...

At first I downloaded driver for Linux from Canon site - iP1500Linux.tar.gz
They say it works for SuSE but even on this it's not supported...blah blah ;-)

I extracted the archive
```
tar -xzf iP1500Linux.tar.gz
```
It contains files
```

iP1500/bjfilter-common-2.50-2.i386.rpm
iP1500/bjfilter-pixmaip1500-2.50-2.i386.rpm
iP1500/bjfilter-common-2.50-2.src.rpm
iP1500/bjfilter-pixmaip1500-lprng-2.50-2.i386.rpm
```
So I converted every i386 rpm with alien to debian
```

cd iP1500
sudo alien *i386.rpm
```
Then to install the deb files:
```
sudo dpkg -i *.deb
```
Everything went ok. I've already had all needed deps. If you are not that lucky and something says 'failed dependencies' try fixing it with apt-get install or apt-get -f install.
After that I suggest creating symlinks:
```
$cd /usr/lib
$sudo ln -s libpng12.so.0 libpng.so.2
$sudo ln -s libtiff.so.4 libtiff.so.3
$sudo ln -s libxml2.so.2 libxml.so.1
```
Without these symlinks the printer will install succesfully but it won't print anything (and I also haven't found anything in cups error logs).

This step is optional but advised - change the .ppd file to get other resolutions (300x300, 1200x1200).
I modified file /usr/share/cups/model/canonpixmaip1500.ppd
(don't forget to backup before changing!)
here's a diff of new and old ppd files:
```
105a106
> *Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
106a108
> *Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
108a111,118
> *OpenUI *CNQuality/Quality: PickOne
> *DefaultCNQuality: 3
> *CNQuality 2/High: "2"
> *CNQuality 3/Normal: "3"
> *CNQuality 4/Standard: "4"
> *CNQuality 5/Economy: "5"
> *CloseUI: *CNQuality
>

```

Now turn the printer on and restart cups
```
/etc/init.d/cupsys restart
```
It's time to add a printer to the system so```
$gnome-cups-manager
``` or if you don't have gnome try using the cups web interface (on localhost)
The printer should be detected as "Canon iP1500" and you should select driver "PIXMA iP1500 Ver.2.50".
That's it!

All done thanks to those people:
[http://forum.pld-linux.org/viewtopic.php?t=1362&start=15]("http://forum.pld-linux.org/viewtopic.php?t=1362&start=15")
[http://ubuntuforums.org/showthread.php?t=38995]("http://ubuntuforums.org/showthread.php?t=38995")

---

### Post by findus on 2006-10-30
Thanks uxworks, that method works for me too using Edgy.  :)

---

### Post by ansalon5 on 2006-11-10
When I tried to install the package from root it gave me the following error.  I am a new to ubuntu and im not quite sure how to fix it.  I tried the apt-get -f install command and it still errored out.  Any help would be greatly appreciated.

```

Unpacking bjfilter-common (from bjfilter-common_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500.
Unpacking bjfilter-pixmaip1500 (from bjfilter-pixmaip1500_2.50-3_i386.deb) ...
Selecting previously deselected package bjfilter-pixmaip1500-lprng.
Unpacking bjfilter-pixmaip1500-lprng (from bjfilter-pixmaip1500-lprng_2.50-3_i386.deb) ...
dpkg: dependency problems prevent configuration of bjfilter-common:
 bjfilter-common depends on libcupsys2-gnutls10 (>= 1.1.23-1); however:
  Package libcupsys2-gnutls10 is not installed.
dpkg: error processing bjfilter-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bjfilter-pixmaip1500:
 bjfilter-pixmaip1500 depends on libcupsys2-gnutls10 (>= 1.1.23-1); however:
  Package libcupsys2-gnutls10 is not installed.
 bjfilter-pixmaip1500 depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 bjfilter-pixmaip1500 depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 bjfilter-pixmaip1500 depends on libpng10-0 (>= 1.0.18); however:
  Package libpng10-0 is not installed.
 bjfilter-pixmaip1500 depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
dpkg: error processing bjfilter-pixmaip1500 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bjfilter-pixmaip1500-lprng:
 bjfilter-pixmaip1500-lprng depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 bjfilter-pixmaip1500-lprng depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing bjfilter-pixmaip1500-lprng (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bjfilter-common
 bjfilter-pixmaip1500
 bjfilter-pixmaip1500-lprng
root@ubuntu:/home/zak# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by pRq on 2007-01-21
Thanks to uxworks it worked fine for me (Edgy).
being not quite knowledgeable of linux, I preferred after having set the symlinks, to:
- start the System Settings -> Printers
- Add -Printer / Class and bei printer model selection, choose "Other" 
- point to /usr/share/cups/model/canonpixmaip1500.ppd

cheers
pR

---

### Post by BjarneJ on 2007-01-26
I've not been as successful. After downloading iP1500Linux.tar.gz and unpacking, I cd iP1500 and get:
~$ cd iP1500
bash: cd: iP1500: No such file or directory

As you've probably guessed, I'm fairly new to Linux.

---

### Post by johndoe32102002 on 2007-01-26
To most recent user's problem:
Try using cd iP* and watch your caps.

My problems with this printer driver:
I can't get it to work because of these errors:

sudo apt-get -f install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcnbj-2.5 is already the newest version.
bjfilter-2.5 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
pstocanonbj: Depends: libcupsys2-gnutls10 (>= 1.1.23-1)

AND WHEN I TRY IT THIS WAY ON THE FORUM:

sudo dpkg -i *.deb
(Reading database ... 104000 files and directories currently installed.)
Preparing to replace bjfilter-common 2.50-3 (using bjfilter-common_2.50-3_i386.deb) ...
Unpacking replacement bjfilter-common ...
Unpacking bjfilter-pixmaip1500 (from bjfilter-pixmaip1500_2.50-3_i386.deb) ...
dpkg: error processing bjfilter-pixmaip1500_2.50-3_i386.deb (--install):
 trying to overwrite `/usr/lib/bjlib/bjfilterpixmaip1500.conf', which is also in package libcnbj-2.5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace bjfilter-pixmaip1500-lprng 2.50-3 (using bjfilter-pixmaip1500-lprng_2.50-3_i386.deb) ...
Unpacking replacement bjfilter-pixmaip1500-lprng ...
Setting up bjfilter-common (2.50-3) ...
Setting up bjfilter-pixmaip1500-lprng (2.50-3) ...

Errors were encountered while processing:
bjfilter-pixmaip1500_2.50-3_i386.deb

NOTE: I tried these with the printer service stopped and when it was running - same result.

---

### Post by BjarneJ on 2007-01-28
bjarne@PC2:~/iP1500$ sudo alien *i386.rpm
Password:
bjfilter-common_2.50-3_i386.deb generated
[COLOR="Red"]Warning: Skipping conversion of scripts in package bjfilter-pixmaip1500: postinst postrm
Warning: Use the --scripts parameter to include the scripts.[/COLOR]
bjfilter-pixmaip1500_2.50-3_i386.deb generated
[COLOR="Red"]Warning: Skipping conversion of scripts in package bjfilter-pixmaip1500-lprng: postrm
Warning: Use the --scripts parameter to include the scripts.[/COLOR]
bjfilter-pixmaip1500-lprng_2.50-3_i386.deb generated

I guess I'm going to have a problem when I go onto installing the .deb packages. What is the scripts parameter?

---

### Post by FluorescentDuck on 2007-02-01
:D Thank you so much...I realized this thread was started a long time ago, but I've been switching back to windows to print and it was extremely annoying.

> bjarne@PC2:~/iP1500$ sudo alien *i386.rpm
Password:
bjfilter-common_2.50-3_i386.deb generated
Warning: Skipping conversion of scripts in package bjfilter-pixmaip1500: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
bjfilter-pixmaip1500_2.50-3_i386.deb generated
Warning: Skipping conversion of scripts in package bjfilter-pixmaip1500-lprng: postrm
Warning: Use the --scripts parameter to include the scripts.
bjfilter-pixmaip1500-lprng_2.50-3_i386.deb generated

I guess I'm going to have a problem when I go onto installing the .deb packages. What is the scripts parameter?

I had that problem too. You have to add the scripts parameter:

```
sudo alien *i386.rpm --scripts
```

That worked for me...good luck.

---

### Post by BjarneJ on 2007-02-02
Thanks for your help. I've stumbled a couple of steps further down the track towards success, but then the next hurdle:

bjarne@PC2:/usr/lib$ $sudo ln -s libpng12.so.0 libpng.so.2
ln: opret symbolsk lænke 'libpng.so.2' til 'libpng12.so.0': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libpng12.so.0 libpng.so.2
ln: opret symbolsk lænke 'libpng.so.2' til 'libpng12.so.0': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libtiff.so.4 libtiff.so.3
ln: opret symbolsk lænke 'libtiff.so.3' til 'libtiff.so.4': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libxml2.so.2 libxml.so 
:confused:

---

### Post by FluorescentDuck on 2007-02-04
> **BjarneJ said:**
> Thanks for your help. I've stumbled a couple of steps further down the track towards success, but then the next hurdle:

bjarne@PC2:/usr/lib$ $sudo ln -s libpng12.so.0 libpng.so.2
ln: opret symbolsk lænke 'libpng.so.2' til 'libpng12.so.0': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libpng12.so.0 libpng.so.2
ln: opret symbolsk lænke 'libpng.so.2' til 'libpng12.so.0': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libtiff.so.4 libtiff.so.3
ln: opret symbolsk lænke 'libtiff.so.3' til 'libtiff.so.4': [COLOR="Red"]Permission denied[/COLOR]
bjarne@PC2:/usr/lib$ $sudo ln -s libxml2.so.2 libxml.so 
:confused:

Hm. The point of typing sudo is so you can act as root, the "superuser". If you're receiving permission denied messages, then sudo isn't working. 

Try removing the $ before sudo, see if that helps. You should be prompted for your password.:-k

---

### Post by BjarneJ on 2007-02-05
Right again FluorescentDuck. I copy/ pasted to make sure I got it right, and copied a $ sign too many.

So I created symlinks, but to no avail I'm afraid, detects the printer, but the driver doesn't appear in the list.

---

### Post by jarondl on 2007-05-11
I've made a howto on the wiki, based on uxworks's great advice..
if you have ideas for it, change it freely , it's Wiki!


[https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)

---

### Post by lllllinux on 2007-09-16
no i had the same problem with converting the rpm and i successed to print

---

### Post by whorush on 2007-09-30
running amd64 7.04.

i can't seem to convert the rpm's to debs.

this is my output for just one deb, i guess, i need to do it for all 4.  i don't really get what its saying.

please help :-).  thanks!

-----

brad@amd64:~/Desktop/iP1500$ sudo alien bjfilter-common-2.50-2.i386.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/bjfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: bjfilter-common-2.50: No such file or directory

---

### Post by buntunub on 2007-10-28
Hey, just thought I should say that this guide and the posted wiki worked awesome for me in Gutsy. Thanks guys.

---

### Post by jakovina on 2008-01-13
Wiki [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) works for me too on Ubuntu 7.10 (Gutsy Gibbon)

---

