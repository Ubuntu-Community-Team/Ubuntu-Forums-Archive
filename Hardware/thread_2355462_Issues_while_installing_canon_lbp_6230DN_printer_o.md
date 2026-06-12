---
title: "Issues while installing canon lbp 6230DN printer on 16.10"
date: 2017-03-13
forum: Hardware
---

### Post by gnvrvikram on 2017-03-13
I am trying to install Canon LBP 6230dn network pritner on ubuntu 16.10 using the method suggeted on the page: [installing Canon LBP 6230dn network printer on Ubuntu 14.04]("http://askubuntu.com/questions/711584/installing-canon-lbp-6230dn-network-printer-on-ubuntu-14-04") I am getting the following error messages. Please help.
```

*This installer is recommended for Fedora or Ubuntu distributions that are currently supported as of the release of this installer.
If this installer is run under earlier or later distributions, the installation of additional system libraries may be necessary after driver installation is complete.
Do you want to continue with installation? (y/n) y
#----------------------------------------------------#
# Install Start
#----------------------------------------------------#
Machine Type = x86_64
Package Type = rpm
Package list = 
    ./64-bit_Driver/RPM/cndrvcups-common-3.30-1.x86_64.rpm
    ./64-bit_Driver/RPM/cndrvcups-ufr2lt-uk-1.20-1.x86_64.rpm
#----------------------------------------------------#
# dnf upgrade
#----------------------------------------------------#
pangox-compat
./install.sh: line 196: dnf: command not found
libxml2
./install.sh: line 196: dnf: command not found
libxml2.i686
./install.sh: line 196: dnf: command not found
glibc
./install.sh: line 196: dnf: command not found
glibc.i686
./install.sh: line 196: dnf: command not found
libstdc++
./install.sh: line 196: dnf: command not found
libstdc++.i686
./install.sh: line 196: dnf: command not found
libjpeg-turbo
./install.sh: line 196: dnf: command not found
libjpeg-turbo.i686
./install.sh: line 196: dnf: command not found
beecrypt.i686
./install.sh: line 196: dnf: command not found
beecrypt-devel.i686
./install.sh: line 196: dnf: command not found
#----------------------------------------------------#
# dnf install
#----------------------------------------------------#
./install.sh: line 204: dnf: command not found
#----------------------------------------------------#
# Install Package Check
#----------------------------------------------------#
 NG: pangox-compat
 NG: libxml2
 NG: libxml2.i686
 NG: glibc
 NG: glibc.i686
 NG: libstdc++
 NG: libstdc++.i686
 NG: libjpeg-turbo
 NG: libjpeg-turbo.i686
 NG: beecrypt.i686
 NG: beecrypt-devel.i686
Some system libraries could not be installed.
Refer to the online manual for more information. 
Do you want to continue with installation? (y/n)*

```

---

### Post by QIII on 2017-03-13
Hello!

Please do not use html formatting or any other formatting that is not provided by the Forums software.

Enclose terminal commands and their output in [noparse]```
[/noparse] and [noparse]
```[/noparse] tags.

Thanks.

---

### Post by pdc on 2017-03-13
so I would recommend starting again by going to here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100595001.html)

you will be downloading the Canon UFR II driver and it comes down as [COLOR="#008000"]Linux_UFRIILT_PrinterDriver_V130_uk-EN.tar.g[/COLOR]z          if you click to SAVE it please and by default, it should end up in your Downloads folder

________________

before you do install it though .... you need to install a very small library file called [COLOR="#0000FF"]libbeecrypt[/COLOR]7 and you get it from the Debian repositories via this page [http://packages.ubuntu.com/trusty/i386/libbeecrypt7/download](http://packages.ubuntu.com/trusty/i386/libbeecrypt7/download) .... please click on a source that is near you or whatever and take the "open with package installer" option that comes up ..... as that will install it for you as it comes down;

and for good measure, if you go here [http://packages.ubuntu.com/trusty/i386/libbeecrypt-dev/download](http://packages.ubuntu.com/trusty/i386/libbeecrypt-dev/download) and download and install the -dev version as well ........ to be sure ...........

___________

now back to installing Linux_UFRIILT_PrinterDriver_V130_uk-EN.tar.gz ....... if you open the terminal and paste these commands in, one by one please

```
cd Downloads
```

```
tar -zxvf Linux_UFRIILT_PrinterDriver_V130_uk-EN.tar.gz
```

```
cd Linux_UFRIILT_PrinterDriver_V130_uk-EN
```

```
sudo ./install.sh
```

that should run the install script and all should be good ....... how is the printer connected to your computer please?

---

