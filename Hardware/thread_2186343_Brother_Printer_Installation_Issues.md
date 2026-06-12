---
title: "Brother Printer Installation Issues"
date: 2013-11-07
forum: Hardware
---

### Post by DJRepresent on 2013-11-07
Hi Everyone, I am fairly new to Ubuntu, and am trying it out on the boot disc.  One of the problems I am having is installing my printer.  I have a Brother MFC 7360N.  

Anyways, I went to their website and it gives me the options to install either an RPM or DEB.  I picked DEB and then it gives me the options to download the following:

LPR printer driver (deb package)
CUPSwrapper printer driver (deb package)
Linux-brprinter-installer 

I really don't know where to go from here!  I tried using the automatic printer installer that comes with Ubuntu but it gave me drivers for a Lexmark!  And after I finally installed something, it asked if I wanted to print a test page.  I said "yes", and it started unloading all the papers in the printer's cassette!  I don't know what to try!


Any help?

Thanks!

---

### Post by Bucky Ball on 2013-11-07
You won't have much luck installing third-party drivers if you are running from the CD/Install media. Where they going to install to? RAM?

You will have better luck with a full hard drive install. Brother is well supported. 

While it may be possible, I don't know about your chances (incidentally, DEB packages will install automagically with Software Centre once downloaded - just double click it).

You could try downloading both files, say to the desktop, and simply double clicking them. Then go to 'Printers', add printer and those drivers will show up, as I say, if it works at all on a CD boot. Your paper-wasting experience would be due to the wrong drivers I expect.

---

### Post by kurt18947 on 2013-11-07
> **Bucky Ball said:**
> You won't have much luck installing third-party drivers if you are running from the CD/Install media. Where they going to install to? RAM?

You will have better luck with a full hard drive install. Brother is well supported. 

While it may be possible, I don't know about your chances (incidentally, DEB packages will install automagically with Software Centre once downloaded - just double click it).

You could try downloading both files, say to the desktop, and simply double clicking them. Then go to 'Printers', add printer and those drivers will show up, as I say, if it works at all on a CD boot. Your paper-wasting experience would be due to the wrong drivers I expect.

I'm not certain about the current software center but I believe installing Brother printer drivers on 64 bit systems does require the use of terminal commands.  For example

```
Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)
```

My understanding - which may be flawed - is that Brother printer drivers are 32 bit and require the --force-all switch when installing on 64 bit system.  I have installed using the Software Center or my preferred Gdebi on 32 bit O.S.s and that worked fine.

---

### Post by Bucky Ball on 2013-11-07
.deb packages require no terminal commands. I have a Brother printer myself and it was straightforward, no terminal required.

---

### Post by DJRepresent on 2013-11-07
I'm actually using the boot disc to decide if I want to go to Ubuntu full-on as Windows 8 has annoyed me enough.  I basically need printer / scanner support and be able to access virtual machines.  I'm also hoping I can avoid having to use the command line unless I prefer to go that route.

OK, let me restart into Ubuntu and see if that will work.

---

### Post by Bucky Ball on 2013-11-08
You can dual-boot. You don't have to go all the way if you're not ready (that doesn't sound right!). ;)

VMs are not an issue and print/scanning shouldn't be either.

---

### Post by kurt18947 on 2013-11-08
If you have a Windows 8 machine, I presume you're aware of the potential complications with Secure Boot, UEFI, etc.?

---

### Post by frankauteri on 2013-12-12
There are a large number of Brother Intellifax models, good solid laser printer engines, that have a glitch in the installation scripts. Not supported by Brother directly and not much documentation elsewhere. There is an easy fix that I discovered after a good deal of time, and might be widely applicable to other Brother printer drivers under Ubuntu 8 and later (I'm using 10.10).

Download fax4100lpr-1.1.2-1.i386.deb cupswrapperFAX4100-1.0.2-1.i386.deb

from

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#FAX-4100](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#FAX-4100)

In a standard archive manager,
go to fax4100lpr-1.1.2-1.i386.deb/DEBIAN

Modify postinst and postrm scripts by:
1) add "sudo service cups stop" at the top,
2) comment out "/etc/init.d/lpd restart",
3) add "sudo service cups start" below that line

Do the prerequisits:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)
and
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Then:
sudo service cups stop
sudo dpkg -i --force-all ./fax4100lpr-1.1.2-1.i386.deb
sudo dpkg -i --force-all ./cupswrapperFAX4100-1.0.2-1.i386.deb
sudo service cups start

Hope this will save someone else some time and trouble.

---

### Post by frankauteri on 2013-12-12
Not all Brother printer drivers can be installed from the Synaptic package manager.  It depends on the printer and version of Ubuntu you are using. Using Ubuntu 10.10, the installation of the Intellifax4100 driver was anything but easy. That appears to be true of many other Brother printers under Ubuntu 10.10. Not only was command line intervention necessary but modification of the Debian install package scripts as well. Easy once you know what to do.

---

### Post by Bucky Ball on 2013-12-12
> **frankauteri said:**
> Using Ubuntu 10.10 ...

10.10 has not been supported since April 2012 so firstly I would advise you to upgrade or reinstall to a supported release. At the moment you are running a vulnerable system as you have not had security updates for a year and a half.

Secondly, not sure how relevant your advice is as you are running a release that has been out of support for a long time.

---

### Post by frankauteri on 2013-12-13
> **Bucky Ball said:**
> 10.10 has not been supported since April 2012 so firstly I would advise you to upgrade or reinstall to a supported release. At the moment you are running a vulnerable system as you have not had security updates for a year and a half.

Secondly, not sure how relevant your advice is as you are running a release that has been out of support for a long time.

Buck,

1) Thanks for the advice on upgrading. I am long overdue, it's true.

2) Regarding the relevance, here is the issue I have. Brother stopped supporting dozens or more 
of its printers at Ubuntu 8.04 ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)). Anything later than that, up to and including 12.04, will need this very same modification in the script to work (see the now closed thread: "brother fax 4100 broken install" begun by JeremySchubert May 7, 2012, and BTW his link in a second posting no longer has the fixed packages he claims to have found there). The very simple fix in the Debian installation package revolves around the fact that the "restart(8) utility" was introduced and/or "sudo" should be used before the invocation of the line in the Debian package. This could fix a great many -not working older brother installs- in Ubuntu 8.04 through 12.04, or whatever is the very latest and greatest. I don't have the 

Thanks all and Cheers [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG] , 
Frank

---

### Post by frankauteri on 2013-12-13
A script like the following shows the steps, beginning to end, for a BrotherFAX4100 reinstallation:

function ask{
    read -p "$1" -r
    if [[ $REPLY =~ ^[Yy]$ ]]
    then
            return 1;
    else
            exit
            echo "Abort.."
    fi
}
# Has the (e.g. fax4100lpr) package been modified for Ubuntu 8.04
# and later (Y/N)? If no, do that first with the aid of an archive
# manager (right-click the package in a GUI) before proceeding.
# See: Brother Printer Installation Issues
# See: "http://ubuntuforums.org/showthread.php?t=2186343"

# Redirect script output to log file GP_Log.out for debugging.
exec > >(tee GoLog.out)
exec 2>&1

ask "Have you read the top of this script? (y/n)"

# Stop cups service.
sudo service cups stop

# Remove "bad ol' installation" and repair if problem present.
sudo rm /var/lib/dpkg/info/*fax4100*
sudo apt-get install -f # Will complain that it cant find package fax4100.

# Run pre-requisits if necessary.
sudo lppasswd -g sys -a root
sudo ln -s /etc/init.d/cups /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo apt-get install sane-utils
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo apt-get install psutils

# Force install both packages, as recommended by Brother.
sudo dpkg -i --force-all ./fax4100lpr-1.1.2-1.i386.deb
sudo dpkg -i --force-all ./cupswrapperFAX4100-1.0.2-1.i386.deb
# Check for successful package installation (eg lpr and cups).
sudo dpkg -l | grep 4100
# For UBUNTU08 and earlier, might need "sudo /etc/init.d/cups restart".
# For later versions:
sudo service cups start
# Check for cups process.
ps -ef | grep cups
#sudo service cups stop
#sudo service cups start
echo "#### Finis #####"

---

