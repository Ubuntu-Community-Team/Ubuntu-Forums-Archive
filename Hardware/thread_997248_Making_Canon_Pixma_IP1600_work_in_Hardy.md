---
title: "Making Canon Pixma IP1600 work in Hardy"
date: 2008-11-29
forum: Hardware
---

### Post by Midnightsun on 2008-11-29
Hi Guys,

Was setting up Ubuntu on my gf's dad's computer and ran into trouble getting his printer installed.  Noticed other people have also struggled with the ip1600 and there didn't seem to be a definitive guide so I thought I'd post the instructions I followed to get it working. 

When it was first plugged in Ubuntu recognised it as the right make and model but no driver was available.  It is possible however to use the ip2200 driver by doing the following:

Make sure you've got alien installed:

```
sudo apt-get update && sudo apt-get install alien libxml1 libpng3
```

Get the driver:

```
wget http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz
```

Extract: 

```
tar -zxf iP2200_Linux_260.tar.gz
```

Get rid of the useless ones:

```
rm -f cnijfilter-common-2.60-1.src.rpm cnijfilter-ip2200-lprng-2.60-1.i386.rpm
```

Convert the .rpms to .debs

```
sudo alien cnijfilter-common-2.60-1.i386.rpm
```
```
sudo alien cnijfilter-ip2200-2.60-1.i386.rpm
```

Then install them:

```
sudo dpkg -i cnijfilter-common_2.60-2_i386.deb
```
```
sudo dpkg -i cnijfilter-ip2200_2.60-2_i386.deb
```

Do some more magic I don't even understand:

```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```
```
sudo ldconfig
```

Then restart cups:

```
sudo /etc/init.d/cupsys restart
```

Make sure the printer is connected then go to System > Administration > Printing

If the printer is already in the list highlight it and delete it.  Then click new printer.  You should be able to see it listed on the left.  Select it then click forward.  When it asks for a driver choose "Canon" from the list of manufacturers and then scroll right to the bottom of the list.  You should see "iP2200 Ver.2.60"  - select that.  

That should be it...at least that did it for me.  Hopefully this helps some people avoid searching around like I had to.  

Thanks go to the gentleman at this blog for the instructions: [http://suratno.wordpress.com/2008/02/22/pixma-ip1600-linux-driver-instalation-3/]("http://suratno.wordpress.com/2008/02/22/pixma-ip1600-linux-driver-instalation-3/")

---

### Post by Littlejohn on 2009-01-03
Hi,

I'm very new to Ubuntu and I'm trying to set up my Canon Pixma ip1600.

I was following your directions (after having tried a few other things...) and the rpm conversion failed:

Can someone help? ...printing would make me popular again in our household...

Thanks,


jean@ubuntu-desktop:/tmp$ ls
cnijfilter-common-2.60               orbit-jean
cnijfilter-common-2.60-1.i386.rpm    orbit-root
cnijfilter-ip2200-2.60-1.i386.rpm    pulse-jean
gconfd-jean                          seahorse-8ydEWJ
gconfd-root                          tmp2PS7Xz
gnome-system-monitor.jean.748878375  tmp.BqDYPR5732
gs_0q5KcX                            tmpQyB-8n
gs_aqpgUk                            Tracker-jean.6051
gs_rTeWpu                            turboprint-2.06-1
gs_SiWGno                            turboprint_2.06-1_i386.deb
iP2200_Linux_260.tar.gz              turboprint-2.06-1.i586.tgz
keyring-ihLHvv                       virtual-jean.LQtzCa
jean@ubuntu-desktop:/tmp$ sudo alien cnijfilter-common-2.60-1.i386.rpm 
mkdir: cannot create directory `cnijfilter-common-2.60': File exists
unable to mkdir cnijfilter-common-2.60:  at /usr/share/perl5/Alien/Package.pm line 257.
jean@ubuntu-desktop:/tmp$ sudo alien cnijfilter-ip2200-2.60-1.i386.rpm 
Warning: Skipping conversion of scripts in package cnijfilter-ip2200: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-ip2200
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libc.so.6 needed by debian/cnijfilter-ip2200/usr/lib/libcnbpo256.so.1.01.1 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cnijfilter-ip2200-2.60: No such file or directory
jean@ubuntu-desktop:/tmp$

---

### Post by Tavathlon on 2009-01-05
Thank you Midnightsun, for a nice guide! Good initiative!  =)

However, also I ran into some problems, although not the same ones as Littlejohn had. The alien part worked just fine for me. However, once the printer was installed and everything seemed fine at first, the printing icon appeared in the "sys tray" with a warning symbol on top of it, and it gives me the following message: ```
Printer 'iP1300': 'cups-missing-filter'.
```

Any ideas?
(As you surely understand, I have a Pixma iP1300, not iP1600, but according to this link, it should be the same driver also for this printer. [http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1300]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1300"))

Best regards
Patrik

---

### Post by Tavathlon on 2009-01-06
Hello all

By following this guide ([http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/](http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/)) I managed to get that error message to disappear. It's in Spanish, but I managed to understand as much as them having a newer version of the *.deb, and also one that seems to be specifically for iP1800, that according to them should work for iP1300. Since they provide links there, I simply downloaded those *.deb's, and installed them. The error message disappeared, but I have not yet been able to check whether the printer does actually work, since I'm not at the same place as the printer right now. I will get back to you about that.

---

