---
title: "Canon LBP7110Cw printing problem"
date: 2017-02-19
forum: Hardware
---

### Post by jet-bundle on 2017-02-19
I have an HP laptop with Lubuntu 16.04 installed, and a Canon LBP7110Cw printer with a wired network connection. The printer works with Windows PCs, but does not work with this laptop.

To install the printer I downloaded and extracted version 130 of the Canon UFR II LT driver from the Canon website, extracted the files, and installed cndrvcups-common-3.50-1_amd64.deb and cndrvcups-ufr2lt_uk_1.30-1_amd64.deb using the GDebi Package Installer.

I then added the network printer "Canon LBP7100Cw (Canon204e90, 192.168.1.7)", choosing under Connections "AppSocket/JetDirect network printer via DNS-SD" and under
Driver (from database) "Canon (recommended)" and "LBP7100C/7110C ver 1.3 [en] (recommended)".


But when printing a test page, the printer state is reported first as "processing", and then "Idle - Waiting for printer to finish". Nothing is printed.

 I can ping the printer on 192.168.1.7.

Any advice would be appreciated.

---

### Post by pdc on 2017-02-20
Hi jet-bundle; 

so that latest version of the Canon's driver comes down as a tar.gz and when uncompressed should be in your Downloads folder as Linux_UFRIILT_PrinterDriver_V130_uk-EN

Canon provide an install script inside that directory; so if one runs that, it should do the install; 

I wonder if you would be willing to delete whatever printer icons you have in your PRINTER folder for your Canon; and then run the install script in the terminal: it should interact with you to allow you to choose what you want: we can only hope that will work; I would suggest if you open a terminal and paste the following commands in: (if you right-click at the prompt in the terminal, you can select the PASTE command from the list displayed .......)

> [COLOR="#FF0000"]cd Downloads/Linux_UFRIILT_PrinterDriver_V130_uk-EN[/COLOR]    

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]           and that should run the install script; ........... in the enclosed thumbnail, Canon explain what happens in the registration of the printer; after driver install ...... hopefully the install script will cover that for you

---

### Post by jet-bundle on 2017-02-20
Thank you. I've done that, and it appears that there are some missing packages: libbeecrypt7:1386 and libbeecrypt-dev:i386. I can't find these using Synaptic Package Manager (both universe and multiverse are enabled). Any idea where they might be?

Here is the output from the install:

```
This installer is recommended for Fedora or Ubuntu distributions that are currently supported as of the release of this installer.

If this installer is run under earlier or later distributions, the installation of additional system libraries may be necessary after driver installation is complete.
Do you want to continue with installation? (y/n) y


#----------------------------------------------------#
# Install Start
#----------------------------------------------------#
Machine Type = amd64
Package Type = deb
Package list = 
    ./64-bit_Driver/Debian/cndrvcups-common_3.50-1_amd64.deb
    ./64-bit_Driver/Debian/cndrvcups-ufr2lt-uk_1.30-1_amd64.deb


#----------------------------------------------------#
# apt-get update
#----------------------------------------------------#
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:4 http://ppa.launchpad.net/stellarium/stellarium-releases/ubuntu xenial InRelease
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [472 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [463 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [397 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [392 kB]
Fetched 2,031 kB in 3s (531 kB/s)                      
Reading package lists... Done


#----------------------------------------------------#
# apt-get install
#----------------------------------------------------#
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libbeecrypt7:i386
E: Unable to locate package libbeecrypt-dev:i386


#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 OK: libglade2-0
 NG: libstdc++6:i386
 NG: libxml2:i386
 NG: libjpeg62:i386
 NG: libbeecrypt7:i386
 NG: libbeecrypt-dev:i386


Some system libraries could not be installed.
Refer to the online manual for more information.
Do you want to continue with installation? (y/n) y


#----------------------------------------------------#
# Install Printer Driver (dpkg -i --force-overwrite)
#----------------------------------------------------#
(Reading database ... 156120 files and directories currently installed.)
Preparing to unpack .../cndrvcups-common_3.50-1_amd64.deb ...
Unpacking cndrvcups-common (3.50-1) over (3.50-1) ...
Setting up cndrvcups-common (3.50-1) ...
(Reading database ... 156120 files and directories currently installed.)
Preparing to unpack .../cndrvcups-ufr2lt-uk_1.30-1_amd64.deb ...
Unpacking cndrvcups-ufr2lt-uk (1.30-1) over (1.30-1) ...
Setting up cndrvcups-ufr2lt-uk (1.30-1) ...


#----------------------------------------------------#
# cups restart
#----------------------------------------------------#
/etc/init.d/cups restart
[ ok ] Restarting cups (via systemctl): cups.service.


Complete

```

Thank you.

---

### Post by oldrocker99 on 2017-02-20
I found libeecrypt here:[https://rpmfind.net/linux/rpm2html/search.php?query=libbeecrypt.so.7()(64bit)](https://rpmfind.net/linux/rpm2html/search.php?query=libbeecrypt.so.7()(64bit)). Unfortunately, there's all .rpm files, for Red Hat distros. There is a conversion program called alien:```
sudo apt install alien
```.

Then, type```
sudo alien -k name_of_.rpm_file
```

That should convert the .rpm to a .deb file, which you can install thus:```
sudo dpkg -i name_of_the_file.deb
```

---

### Post by pdc on 2017-02-20
thanks oldrocker

Debian often seem to have things stored away in their repositories: libbeecrypt7:i386 seems to be here [https://packages.debian.org/jessie/libbeecrypt7](https://packages.debian.org/jessie/libbeecrypt7)

If you scroll down to the bottom of the page and choose i386: 

______________

and actually as I google further 

this link [http://askubuntu.com/questions/763171/printer-driver-depends-on-libbeecrypt7i386-but-its-not-in-repositories](http://askubuntu.com/questions/763171/printer-driver-depends-on-libbeecrypt7i386-but-its-not-in-repositories) says that 


Ubuntu has it [http://packages.ubuntu.com/trusty/libbeecrypt7](http://packages.ubuntu.com/trusty/libbeecrypt7)

so another source of the i386

___________

I would hope that if you install this file; then re-run the install script, it should all be good

---

### Post by jet-bundle on 2017-02-20
Thanks to both. I managed to find the two Debian packages at [http://packages.ubuntu.com/trusty/i386/libbeecrypt7/download](http://packages.ubuntu.com/trusty/i386/libbeecrypt7/download) (which I installed first) and then [http://packages.ubuntu.com/trusty/i386/libbeecrypt-dev/download](http://packages.ubuntu.com/trusty/i386/libbeecrypt-dev/download). Installation now completes, and the printer works.

Problem solved!

---

### Post by pdc on 2017-02-20
great! delighted to hear your printer is working: sounds like a very fine machine; enjoy!!

so summary for anyone following who wants to install UFRIILT is:

1) install libbeecrypt7:i386
2) download UFRIILT driver from canon
3) decompress and run install script

---

