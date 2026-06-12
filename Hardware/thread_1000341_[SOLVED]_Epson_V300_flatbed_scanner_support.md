---
title: "[SOLVED] Epson V300 flatbed scanner support"
date: 2008-12-02
forum: Hardware
---

### Post by kaibob on 2008-12-02
I wondered if anyone has gotten the Epson V300 flatbed scanner working with Ubuntu 8.04 or 8.10. I checked the Avasys and Sane sites but neither shows the V300 as a supported model. In another thread, Tuxi had no success getting this scanner working.

BTW, the V300 is the successor to the V200 and is Epson's current budget flatbed scanner. 

AVASYS SITE:
[http://avasys.jp/hp/page000001300/hpg000001243.htm](http://avasys.jp/hp/page000001300/hpg000001243.htm)

THREAD CONTAINING TUXI'S POST
[http://ubuntuforums.org/showthread.php?p=6257709&highlight=v300#post6257709](http://ubuntuforums.org/showthread.php?p=6257709&highlight=v300#post6257709)

SANE SITE
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Epson&model=&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Epson&model=&bus=any&v=&p=)

---

### Post by kaibob on 2008-12-29
I just checked the Avasys site, and the V300 is now supported. Also, for the first time, Ubuntu is shown as a distribution. Sounds great :D

---

### Post by Jonam on 2009-01-01
I have got the V300 working using the drivers provided on the Avasys site for Ubuntu 8.04.

You need to make sure that:

- Sane and Sane-utils are installed prior to installing the Avasys drivers,
- Both the iscan and esci-interpreter packages from Avasys are installed and,
- A line with "epkowa" is added to the /etc/sane.d/dll.conf file

Running "sane-find-scanner" and "scanimage -L" in a terminal window should confirm that your scanner is recognised and then running "iscan" should allow you to scan images.

I have tested both paper and transparency (film negative) scanning using iscan and they work fine.

I tried Xsane but found that it would not run previews when scanning film negatives. The error message "Failed to start scanner: invalid argument" would appear when I pressed the Preview button in Xsane.


Jonam

---

### Post by bailout on 2009-01-03
I have just tried following your method but there is a dependency problem with iscan on intrepid. It needs libltdl3 which isn't available in the 8.10 repos.

---

### Post by bailout on 2009-01-03
I installed libltdl3 using the hardy package.

[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

Then just followed Jonam's instructions (thanks)

The avasys iscan app works but is very basic. Xsane works as well and gives much more control.

---

### Post by Tuxi on 2009-01-04
> **bailout said:**
> I installed libltdl3 using the hardy package.

[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

Then just followed Jonam's instructions (thanks)

The avasys iscan app works but is very basic. Xsane works as well and gives much more control.

Thanks to everyone on this thread.  I was able to get the 64-bit version to work!  (I used the libltdl3 package from Hardy.)  Interestingly enough, running iscan from the command line gave me a message that it was unable to communicate with the scanner, but running "Image Scan!" from the graphics menu started the scanner right up :-)

---

### Post by nlz on 2009-01-18
I need to run iscan with root permissions, can i do something about that? Maybe change the permissions of the mountpoint or something like that?

---

### Post by ogger on 2009-02-22
to install  libltdl3 it asks me to remove the current software manager. Does that mean I need to remove libltdl7? Looks like a big deal. any other way to get V300 to work? [EDIT: Never mind, I might have had Synaptic open which caused a conflict !?]

---

### Post by HighSide on 2009-04-02
Hi,

Just got one of these scanners and have tried to follow this thread to get it working but when I tried to install the .deb package I got the following errors:

root@Office-desktop:/home/stuart# dpkg --install iscan_2.19.0-4_i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `iscan' missing, assuming package has no files currently installed.
145760 files and directories currently installed.)
Preparing to replace iscan 2.19.0-4 (using iscan_2.19.0-4_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 17: Syntax error: Bad substitution
dpkg: error processing iscan_2.19.0-4_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
/var/lib/dpkg/tmp.ci/postrm: 25: Syntax error: Bad substitution
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 iscan_2.19.0-4_i386.deb

I have 7.10 installed at the moment on my 32bit box, I have also tried it on my 64bit box running 8.04.

Cheers 
Stu

---

### Post by nlz on 2009-04-03
I think you first have to remove all iscan packages before you install new ones.

---

### Post by kenn e on 2009-04-06
Hello,

nlz that was such a helpful comment, HOW?

```
ken@ken-desktop:~$ cd Desk*
ken@ken-desktop:~/Desktop$ sudo dpkg --force-overwrite -i iscan_2.19.0-4_i386.deb
[sudo] password for ken: 
(Reading database ... 149626 files and directories currently installed.)
Unpacking iscan (from iscan_2.19.0-4_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 29: Bad substitution
dpkg: error processing iscan_2.19.0-4_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Processing triggers for menu ...
Errors were encountered while processing:
 iscan_2.19.0-4_i386.deb
ken@ken-desktop:~/Desktop$ 
```


I have deleted every bit of scanner stuff i could find. I'm new to Linux (I'm a amd64 BSD'er who needs a few things like this scannner to work and am, trying Ubuntu (again) so go easy on me, i'm really missing the port collection and the tools i am familiar with to fix such problems.)

---

### Post by HighSide on 2009-04-06
I have just tried to remove the packages and got this error message:

 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

I think the package has been corrupted or is missing something. 

Does anyone have an earlier working version than 2.19.0-4

---

### Post by HighSide on 2009-04-06
kenn e

I got it sorted! 

This is how I did it

I Downloaded the 2.18.0-2.deb from here [http://avasys.jp/hp/menu000001300/hpg000001249.htm]("http://avasys.jp/hp/menu000001300/hpg000001249.htm")

install from terminal  [B]dpkg --install iscan_2.18.0-2_i386.deb
[/B]

Then installed the pakage esci-interpreter-gt-f720_0.0.1-1_i386.deb on the same page.

---

### Post by kenn e on 2009-04-08
[SIZE="5"]Thank you![/SIZE]:p

the older iscan 2.18 worked for me too!

now to get Avermedia TV Tuner and MS VX-1000 webcam working... the only problem i'm having with ubuntu - video0, video1 & video2

---

### Post by lamegaptop on 2009-04-12
Thanks to all!! The older Iscan worked here on amd64.

I've been struggling with this for weeks.

---

### Post by BetterSense on 2009-05-03
I've been unable to get on the avasys website for 2 days running now. I had my V500 working with iscan and Epson scan in virtualbox on Intrepid but now that I upgraded to Jaunty I cannot get my scanner working, because I can't download the drivers from the website. I tried running the command here

[http://ubuntu.flowconsult.at/en/epson-v500-installation/9.04/](http://ubuntu.flowconsult.at/en/epson-v500-installation/9.04/)

but it phails since I have a 64bit system. I tried replacing all instances of "i386" with "amd64" and it looked like it was working but somehow still failed. Halp?

```
chaz@brutus:~/desktop$ cd $HOME/desktop && wget http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/libt/libtool/libltdl3_1.5.26-1ubuntu1_amd64.deb && wget http://linux.avasys.jp/drivers/iscan/2.18.0/iscan_2.18.0-2_amd64.deb && wget http://linux.avasys.jp/drivers/iscan/plugins/iscan-plugin-gt-x770_2.1.1-1_amd64.deb && sudo dpkg -i lib*.deb && sudo dpkg -i iscan_2*.deb && sudo dpkg -i iscan-plugin*.deb && sudo perl -p -i.bak -e 's/epson\n/#epson\n/g' /etc/sane.d/dll.conf && sudo perl -p -i.bak -e 's/Provides: iscan-interpreter \(= 2\.1\)\n//g' /var/lib/dpkg/status
--2009-05-03 13:59:55--  http://mirror.switch.ch/ftp/mirror/ubuntu/pool/main/libt/libtool/libltdl3_1.5.26-1ubuntu1_amd64.deb
Resolving mirror.switch.ch... 130.59.10.36
Connecting to mirror.switch.ch|130.59.10.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 179540 (175K) [text/plain]
Saving to: `libltdl3_1.5.26-1ubuntu1_amd64.deb'

100%[==========================================================================================================================================>] 179,540      179K/s   in 1.0s

2009-05-03 13:59:57 (179 KB/s) - `libltdl3_1.5.26-1ubuntu1_amd64.deb' saved [179540/179540]

--2009-05-03 13:59:57--  http://linux.avasys.jp/drivers/iscan/2.18.0/iscan_2.18.0-2_amd64.deb
Resolving linux.avasys.jp... 202.41.220.50
Connecting to linux.avasys.jp|202.41.220.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 360352 (352K) [application/x-deb]
Saving to: `iscan_2.18.0-2_amd64.deb'

100%[==========================================================================================================================================>] 360,352      209K/s   in 1.7s

2009-05-03 13:59:59 (209 KB/s) - `iscan_2.18.0-2_amd64.deb' saved [360352/360352]

--2009-05-03 13:59:59--  http://linux.avasys.jp/drivers/iscan/plugins/iscan-plugin-gt-x770_2.1.1-1_amd64.deb
Resolving linux.avasys.jp... 202.41.220.50
Connecting to linux.avasys.jp|202.41.220.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 172164 (168K) [application/x-deb]
Saving to: `iscan-plugin-gt-x770_2.1.1-1_amd64.deb'

100%[==========================================================================================================================================>] 172,164      150K/s   in 1.1s

2009-05-03 14:00:01 (150 KB/s) - `iscan-plugin-gt-x770_2.1.1-1_amd64.deb' saved [172164/172164]

Selecting previously deselected package libltdl3.
(Reading database ... 130373 files and directories currently installed.)
[B]Unpacking libltdl3 (from libltdl3_1.5.26-1ubuntu1_amd64.deb) ...
dpkg: error processing libltdl3_1.5.26-1ubuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)[/B]
Setting up libltdl3 (1.5.26-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libltdl3_1.5.26-1ubuntu1_i386.deb

```

---

### Post by elvanor on 2009-06-08
Hi, I just bought this scanner and so far am unable to make it work correctly under Gentoo.

It recognizes the USB device but running scanimage -L always reports it cannot find an indentified scanner.

I would like to ask, for those that made the scanner work, did you add a line on epkowa.conf like this:

usb 0x04b8 0x0131

Or did you leave your epkowa.conf file intact?

Thanks

---

### Post by m.lp.ql.m on 2009-07-12
I was having problems on K/Ubuntu 9.04 after installing the DEB 32bit core package [libltdl7] (for Ubuntu 8.10 or later) [ iscan_2.20.0-6.ltdl7_i386.deb ], where sane-find-scanner detected my V300, but scanimage -L didn't.

Fixed by also installing the esci-interpreter-gt-f720_0.0.1-2_i386.deb package listed right above it on the Avasys download page under Deb 32bit package.

The "epkowa" line added to the /etc/sane.d/dll.conf file, per Jonam's post [ [http://ubuntuforums.org/showpost.php?p=6472280&postcount=3](http://ubuntuforums.org/showpost.php?p=6472280&postcount=3) ] is also needed.

---

### Post by ravn-hawk on 2009-08-15
Hi all,

I have a new problem with the Epson V300 scanner. I managed to install the iscan package from AVASYS on Ubuntu 9.04 w.o. a problem.

According to the manual on the AVASYS website everything is now suppose to work just by running iscan. I however get an error (both from GNOME menu, and from command line. Also when run as root on command line) saying:

Could not send command to scanner.
Check the scanner's status.

Anyone have got any idea about how to solve this?

EDIT:
I find the scanner with sane-find-scanner, it outputs:

found USB scanner (vendor=0x04b8 [EPSON], product=0x0131 [EPSON Scanner]) at libusb:001:006

but scanimage -L does not work, saying:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by Rain-In-The-Face on 2009-09-06
I've searched the forums on my peculiar problem and so far I haven't found a solution yet. I run 8.04 on an AMD 64 platform.   The trouble is that my V300 Photo scans documents and photos perfectly, but whenever I try to get it to scan 35mm negatives, iscan states &quot;Could not send command to scanner. Check the scanner's status&quot;. Xsane states &quot;Failed to start scanner. Invalid argument&quot;. Has anyone else faced this problem? I looked up Avasys' documentation and they state that we need to use sane 1.0.3 while my release's current version is 1.0.19. Could that be a problem?

---

### Post by jarkoos on 2009-11-09
Hello,

> **Rain-In-The-Face said:**
> I've searched the forums on my peculiar problem and so far I haven't found a solution yet. I run 8.04 on an AMD 64 platform.   The trouble is that my V300 Photo scans documents and photos perfectly, but whenever I try to get it to scan 35mm negatives, iscan states &quot;Could not send command to scanner. Check the scanner's status&quot;. Xsane states &quot;Failed to start scanner. Invalid argument&quot;. Has anyone else faced this problem? I looked up Avasys' documentation and they state that we need to use sane 1.0.3 while my release's current version is 1.0.19. Could that be a problem?

I've just bought this scanner and have exactly the same problem. It scans all the material fine, but when it comes to 35mm negatives it gives the message you wrote.
Don't know what to do. My system is Kubuntu 9.10.
Have you found any solution to this problem?

---

### Post by bailout on 2009-12-06
> **jarkoos said:**
> Hello,



I've just bought this scanner and have exactly the same problem. It scans all the material fine, but when it comes to 35mm negatives it gives the message you wrote.
Don't know what to do. My system is Kubuntu 9.10.
Have you found any solution to this problem?

Just a bump. I have just installed my v300 in 9.10 and am having the same problem. Flatbed works fine but tranparancies don't. Anyone come up with a fix?

---

### Post by bob12564 on 2009-12-06
The transparency unit is not supported by SANE.  See this:

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson)

You have to use the proprietary Epson/Avasys Image Scan software instead.

---

### Post by bailout on 2009-12-07
I replied to your other thread. I was getting the error message simply because I had forgotten to remove the panel to expose the transparancy strip.

Since doing that it scans slides in both iscan and xsane although the exposure in xsane is off.

---

### Post by joserod on 2010-02-26
Hi:

I have been trying to install a  V300 scanner in my Ubuntu 8.04 system, following suggestions from previous postings in this thread.  I have already installed Sane and the iscan package from Avasys.  However, when I try to install the corresponding esci-interpreter package  ([esci-interpreter-gt-f720_0.0.0-1_i386.deb]("http://linux.avasys.jp/drivers/iscan/plugins/esci-interpreter-gt-f720_0.0.0-1_i386.deb")) using the GDebi packege installer it gives me the Dependency is not satisfiable: iscan error.  Since I have already installed the iscan package I assume that GDebi is not recognizing the new packages installed.  Is there any way to overcome this error.  Am I missing something.  I am not very familiar with Linux and would appreciate any help.

---

### Post by neigun on 2010-02-28
> **joserod said:**
> Hi:

I have been trying to install a  V300 scanner in my Ubuntu 8.04 system, following suggestions from previous postings in this thread.  I have already installed Sane and the iscan package from Avasys.  However, when I try to install the corresponding esci-interpreter package  ([esci-interpreter-gt-f720_0.0.0-1_i386.deb]("http://linux.avasys.jp/drivers/iscan/plugins/esci-interpreter-gt-f720_0.0.0-1_i386.deb")) using the GDebi packege installer it gives me the Dependency is not satisfiable: iscan error.  Since I have already installed the iscan package I assume that GDebi is not recognizing the new packages installed.  Is there any way to overcome this error.  Am I missing something.  I am not very familiar with Linux and would appreciate any help.

joserod 

try this package, esci-interpreter-gt-f720_0.0.1-2_i386.deb, available on the Avasys website [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

The package you are trying to install would appear to be an earlier version.

Neil

---

### Post by stevecoh1 on 2010-12-28
Grrrrrr!  [SOLVED] - NOT!

I had this scanner working under another system running Ubuntu 8.04.  There, it was an effortless install.

On 10.04 it doesn't work.  I've installed the sane, sane-utils, and the avasys iscan-data thing.  I created an /etc/sane.d/epkowa file with the correct product id etc.  So many "helpful" hints, none of it accurate.

This is such a bunch of crap.  Can't Ubuntu step up to the plate and provide an authoritative solution as it usually does?

Has anyone got this scanner working with 10.04 and if so how????

Thanks.

---

### Post by stevecoh1 on 2010-12-28
A little more information:


> $ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0131 [EPSON Scanner]) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

What's with this "(probably) detected" nonsense?  How can I get this to work?

Ironically, I AM able to get the scanner to work inside a VMWare Windows XP virtual machine on this box.  So it looks like what is missing is some piece of the driver.

I'd be grateful for anyone's help and would be happy to write up a solid HOW-TO if I can figure this thing out.

---

### Post by stevecoh1 on 2010-12-29
Okay, working now.

Here are the steps I followed for getting the V300 working under 10.04.  I'm not sure this order is absolutely required (except where noted) but it worked for me.

1. Get rid of everything you might have installed

```
sudo apt-get remove xsane sane-utils sane iscan iscan-data
```

Your list of failed attempts may differ and you may have to remove some of the above items from the list.  You can also remove them individually

2. 
```
sudo apt-get install sane
```

3.  Go here 
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

and fill in the questionnaire.  It will tell you what to download.  Note that there are THREE packages that must be downloaded.  My mistake was in only seeing the first one.  For 10.04 32-bit these were:

```
iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
esci-interpreter-gt-f720_0.0.1-2_i386.deb
```

Download all of these and install them.  **These three items must be installed in this order** or you will have dependency issues.

You can install them with gdebi (which will come up if you click on them in Nautilus in the folder you downloaded them to.)

4.
```
sudo apt-get install sane-utils
```

5.  Now if you plug in your scanner (if it was already plugged in, please power it off and on now or this won't work)

and type this in a terminal window

```
$ scanimage -L
```

you should see the output
```
device `epkowa:interpreter:002:008' is a Epson Perfection V300 flatbed scanner 
```

(SCSI bus numbers will vary), and you will hear the lovely sound of the scanner coming to life.



You should now have Image Scan! for Linux on your Applications -> Graphics menu.  You can run this, and it works, but I don't like it.  I couldn't find a way to do multipage PDF scans with it, which is what I need it to be able to do.

To get that and other advanced capabilities:

6.  

```
sudo apt-get install xsane
```

xsane is the gold standard for Linux scanning, does everything you want it to.

If you do these steps you can ignore all the old information about permissions, creating a "scanner" group for users, messing around with "epkowa" and other poorly documented stuff that floats to the top of the Google search.

---

### Post by stevecoh1 on 2010-12-29
please delete

---

### Post by nss0000 on 2011-03-04
> **stevecoh1 said:**
> Okay, working now.

Here are the steps I followed for getting the V300 working under 10.04.  I'm not sure this order is absolutely required (except where noted) but it worked for me.

1. Get rid of everything you might have installed

```
sudo apt-get remove xsane sane-utils sane iscan iscan-data
```

Your list of failed attempts may differ and you may have to remove some of the above items from the list.  You can also remove them individually

2. 
```
sudo apt-get install sane
```

3.  Go here 
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

and fill in the questionnaire.  It will tell you what to download.  Note that there are THREE packages that must be downloaded.  My mistake was in only seeing the first one.  For 10.04 32-bit these were:

```
iscan-data_1.6.0-0_all.deb
iscan_2.26.1-3.ltdl7_i386.deb
esci-interpreter-gt-f720_0.0.1-2_i386.deb
```

Download all of these and install them.  **These three items must be installed in this order** or you will have dependency issues.

You can install them with gdebi (which will come up if you click on them in Nautilus in the folder you downloaded them to.)

4.
```
sudo apt-get install sane-utils
```

5.  Now if you plug in your scanner (if it was already plugged in, please power it off and on now or this won't work)

and type this in a terminal window

```
$ scanimage -L
```

you should see the output
```
device `epkowa:interpreter:002:008' is a Epson Perfection V300 flatbed scanner 
```

(SCSI bus numbers will vary), and you will hear the lovely sound of the scanner coming to life.



You should now have Image Scan! for Linux on your Applications -> Graphics menu.  You can run this, and it works, but I don't like it.  I couldn't find a way to do multipage PDF scans with it, which is what I need it to be able to do.

To get that and other advanced capabilities:

6.  

```
sudo apt-get install xsane
```

xsane is the gold standard for Linux scanning, does everything you want it to.

If you do these steps you can ignore all the old information about permissions, creating a "scanner" group for users, messing around with "epkowa" and other poorly documented stuff that floats to the top of the Google search.

SteveC:

Many thanks for your thoughtful and detailed instruction. I'm a casual Ubuntu lusr, with zero (0) admin skills. I followed your instructions closely ... obvious variations show on the **avsys** site, like choosing x64bit file versions.  After the 3-file plus sane-utils installation my Epson V300 punched up exactly as  it should. Then, XSANE works also.

Many thanks again .... you saved my bacon.

---

### Post by cb_rex on 2011-05-26
I agree that is a great streamlined guide that works fine with 11.04 thanks stevecoh1.

I initially got stuck installing the 3 packages, I think I installed one of the wrong versions then got an error, so I just ran the first step again to remove everything, then went through the steps again installing the correct packages and it worked. :)

---

### Post by Clive McCarthy on 2011-07-19
Thanks for writing this up. It worked perfectly.

---

### Post by ABNormal62 on 2012-01-28
Thanks from me too!
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

