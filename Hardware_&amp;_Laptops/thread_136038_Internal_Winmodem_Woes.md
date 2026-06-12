---
title: "Internal Winmodem Woes"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by ubuntumaybe on 2006-02-25
Hi,

 I am relatively new to Linux. I had Mandrake installed for awhile. 
I have an internal winmodem. I downloaded and run the scanmodem program. Reported that I have pc-tel and the sl-modem package would solve all my modem problems. I checked the wiki page 
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)
and read the instructions. Unfortunately the page assumes that I already have internet access and that I can use the apt-get command. In order to install packages on my laptop I download and burn them onto a cd at my local library. I need instructions that assume I have no internet connectivity. I know that I am not the only person suffering with an internal winmodem since I have been perusing the various forums. Thanks for your help.

---

### Post by shams2 on 2006-02-25
nearly all winmodem has linux driver you can find from your modem official website or try  google com to find one, download wiht other os, because you don't have internet connection presently in linux and install it.

---

### Post by ubuntumaybe on 2006-02-27
Hi,

 Thanks for the response. The information contained in the dialuphowto requires that the modem source be compiled with the linux kernel code. If I upgrade to the next release of ubuntu will I have to go through the same procedure again for dial up connectivity. I have downloaded a number of .gz files from various sites , unzipped them and followed the directions. They all require compilation of code with kernel files. Are you aware of a specific site which will permit me to download a .deb file? Thanks.

---

### Post by newuser111 on 2006-02-27
yes you will probably have to recompile the drives with if you upgrade to a newer kernel, such as 2.6.15, but of course you dont have to if you dont want to...

---

### Post by ubuntumaybe on 2006-04-05
Hi,

With all of the problems I am seeing on the various forums for winmodems why has no one prepared a .deb file from the slmodem source and made it available to all.

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=ubuntumaybe]Unfortunately the page assumes that I already have internet access and that I can use the apt-get command.[/QUOTE]
I fixed the page and put a notice on top of it just now. Basically, you can search and download packages using [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . You have to be careful with the dependencies though. 

for example: 
build-essential: [http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)
have the following dependencies: 
dpkg-dev (>= 1.13.5)
g++ (>= 4:4.0)
gcc (>= 4:4.0)
libc6-dev
make
==> So you have to make sure these are installed before you install build-essentials... 

An easier way to go about would be: 
1. Find a computer with internet access and a CD burner and boot using the live CD. 
2. Install whatever the wiki wants you to install (sudo apt-get install blabla) using the live cd
3. burn the packages under /var/cache/apt/archive to the CD
4. go home, boot your ubuntu, put in cd and mount it, copy all the packages in that cd to /var/cache/apt/archive
5. go back to the wiki and sudo apt-get install wahtever it wants. 

/var/cache/apt/archive is the temporary file directory of apt-get when it installs stuff from the internet repos.

> 
With all of the problems I am seeing on the various forums for winmodems why has no one prepared a .deb file from the slmodem source and made it available to all.
I have no idea. but that someone should be an ubuntu devel and have privileges to upload stuff to the ubuntu repositories...

---

### Post by ubuntumaybe on 2006-04-05
Hi,

 Thanks for all this information. I have just checked the dial howto and dowloaded a number of files.  I will check for the dependencies when I get home and then download and burn any missing files. I will keep you informed.

ubuntumaybe

---

### Post by ubuntumaybe on 2006-04-06
Hi,

I downloaded the suggested files or at least I believe I did. I executed the suggested sudo command and I am pasting the output from /var/cache. As you can see there is a reference to gcc 3.4 but I downloaded and installed the gcc 4.4.  Where to now?

ubuntumaybe

%%%%%%%%%%%% START %%%%%%%%
dh_testdir

dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp

# Add here commands to clean up after the build process.

/usr/bin/make clean SUPPORT_ALSA=1

make[1]: Entering directory `/usr/src/modules/sl-modem'

make[1]: Leaving directory `/usr/src/modules/sl-modem'

cd modem; /usr/bin/make clean SUPPORT_ALSA=1

make[1]: Entering directory `/usr/src/modules/sl-modem/modem'

make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'

dh_clean

/usr/bin/make -C drivers clean

make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'

rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~

rm -f -r .tmp_versions

make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'

/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules

make[1]: Entering directory `/usr/src/modules/sl-modem'

dh_testdir

dh_testroot

rm -f build-arch-stamp build-indep-stamp configure-stamp

# Add here commands to clean up after the build process.

/usr/bin/make clean SUPPORT_ALSA=1

make[2]: Entering directory `/usr/src/modules/sl-modem'

make[2]: *** No rule to make target `clean'.  Stop.

make[2]: Leaving directory `/usr/src/modules/sl-modem'

make[1]: [clean] Error 2 (ignored)

cd modem; /usr/bin/make clean SUPPORT_ALSA=1

make[2]: Entering directory `/usr/src/modules/sl-modem/modem'

make[2]: *** No rule to make target `clean'.  Stop.

make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'

make[1]: [clean] Error 2 (ignored)

dh_clean

/usr/bin/make -C drivers clean

make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'

rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~

rm -f -r .tmp_versions

make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'

for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \

    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.12-9-386/g'` ; \

  done

for templ in `ls debian/*.modules.in` ; do \

    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \

    sed -e 's/##KVERS##/2.6.12-9-386/g ;s/#KVERS#/2.6.12-9-386/g ; s/_KVERS_/2.6.12-9-386/g ; s/##KDREV##/2.6.12-9.23/g ; s/#KDREV#/2.6.12-9.23/g ; s/_KDREV_/2.6.12-9.23/g' < $templ > ${templ%.modules.in}; \

  done

dh_clean -k

dh_install
dirs lib/modules/2.6.12-9-386/misc usr/lib/sl-modem

if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi

/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux-headers-2.6.12-9-386 KVERS=2.6.12-9-386

make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'

gcc-3.4 -I/usr/src/linux-headers-2.6.12-9-386/include -o kernel-ver kernel-ver.c

make[2]: gcc-3.4: Command not found

make[2]: *** [kernel-ver] Error 127

make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'

make[1]: *** [binary-modules] Error 2

make[1]: Leaving directory `/usr/src/modules/sl-modem'

make: *** [kdist_build] Error 2

%%%%%%%%%%%% END %%%%%%%%%

---

### Post by HairyDave on 2006-04-06
Hi,

I don't claim to be an expert or anything but if you visit:

[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

and download:

BreezyGCC_3.4_i386.tar.gz 

it might help with the problems you are having.

If it works let me know, I had the same snags with my winmodem and this seemed to cure the problem.

---

### Post by towsonu2003 on 2006-04-07
you could download gcc-3.4 and install it. it may be on the install cd and apt-gettable after mounting the install cd, sudo apt-get update sudo apt-get install gcc-3.4. Than your command (that led to this output) should start with "CC=gcc-3.4 commandhere" (no quotes)

This may be incorrect (as a command), I'm not sure. Dave's reply may be an easier solution than this.

---

### Post by ubuntumaybe on 2006-04-20
Hi,

 I downloaded the breezy gcc from linmodems and attempted to compile. The compilation proceeded further but there were still problems.

 I have managed to locate and external modem which functioned first time without any form of configuration.

 I am a little annoyed that the winmodem will not function and I would still like to proceed with the compilation. The error message stated that I had not loaded the sl-modem-module .deb file but it is loaded so what could the problem be? Thanks.

joe

---

