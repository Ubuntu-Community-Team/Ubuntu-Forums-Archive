---
title: "Scanner Drivers"
date: 2018-10-30
forum: Hardware
---

### Post by daniell59 on 2018-10-30
Every time I install a later operating system I have difficulty installing the drivers for the scanner. The last time I did so with the kind help of this forum. I tried to do it on my own but it is too much for me.

Ubuntu 16.04 64
Epson perfection V30

Download page [http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=1.0.1](http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=1.0.1)

Any assistance will be greatly appreciated. This time I will try even harder to comprehend what is going on.

Thanks

---

### Post by dino99 on 2018-10-30
Why are you thinking you need to install a private driver, ubuntu archive have the required one and utility. Simply use 'synaptic' and search for 'epson' to get the packages name.

---

### Post by daniell59 on 2018-10-30
> **dino99 said:**
> Why are you thinking you need to install a private driver, ubuntu archive have the required one and utility. Simply use 'synaptic' and search for 'epson' to get the packages name.

I would appreciate it if you would elaborate.

---

### Post by daniell59 on 2018-10-30
I read the instructions on the Epson site. They are beyond my comprehension. Someone please come to my rescue.

Thanks

---

### Post by Holger_Gehrke on 2018-10-30
@dino99: He thinks he needs a proprietary driver because he does. According to the list of supported devices at [sane-project.org]("http://www.sane-project.org/sane-mfgs.html#Z-EPSON") the Perfection V30 is unsupported and works with the epkowa backend (which is a nonfree driver provided at the link he gives). And searching for 'epson' in synaptic does not find any scanner drivers (though it does find quite a few utilities for Epson inkjet printers). The scanner drivers are all hidden away in the sane (Scanner Access Now Easy) packages, and the epkowa backend - being proprietary - is not included.

@daniell59: I believe the basic sane libraries (and some utilities) are installed by default, but lets check that. Open a terminal and enter ```
apt-cache policy libsane-common
```If sane is installed, the second line of the output should be 'Installed:' followed by a version (1.0.27-1-experimental3ubuntu2 on 18.04, probably something else on your 16.04). If it says 'Installed: (none)' than you need to install sane first. To do that, enter ```
sudo apt-get install sane-utils
```This will ask for your password and then install the sane utilities, and since they need the sane libraries those will be installed too. The driver at the site you give exist in four variants: rpm or deb each in 32bit (i386) or 64bit (amd64). Ubuntu uses deb-packages. Which of the two offered files you need to download depends on your CPU and the variant of the OS you've installed. To find out whether you've got a 64 bit system, enter```
uname -p
```If that outputs 'x86_64' it's a 64bit system and you need the second of the two deb-package archives. I don't have a 32bit system at hand to check, but it will probably output something like 'i386' or 'x86_32'. You'd need the first archive for one of those. Download the file and double click it in your file manager. That should open it in your archive manager. There's one directory in that archive. Unpack it by simply dragging it from the archiver into the file manager. Switch back to the terminal or open a new one. Use the 'cd' command to change to the directory you just unpacked ('cd ~/Download/iscan-gt-f720-bundle-1.0.1.x64.deb' if you've got the 64bit package and unpacked it into the Download-folder;'cd ~/Download/iscan-gt-f720-bundle-1.0.1.x86.deb' for the 32bit package). Enter```
./install.sh
```This will ask for your password and then install the driver. You should be done at this point.

Holger

---

### Post by daniell59 on 2018-10-31
Thanks for your kind and informative post. I am now trying to digest all of this. I definitely have 64 bit.
daniel@daniel-P5Q-PRO:~$ apt-cache policy libsane-common
libsane-common:
  Installed: 1.0.27-1~experimental3ubuntu2
  Candidate: 1.0.27-1~experimental3ubuntu2
  Version table:
 *** 1.0.27-1~experimental3ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main i386 Packages
        100 /var/lib/dpkg/status
daniel@daniel-P5Q-PRO:~$ sudo apt-get install sane-utils
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sane-utils is already the newest version (1.0.27-1~experimental3ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
daniel@daniel-P5Q-PRO:~$ uname -p
x86_64
daniel@daniel-P5Q-PRO:~$ ./install.sh
bash: ./install.sh: No such file or directory
daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ ./install.sh
bash: ./install.sh: No such file or directory
daniel@daniel-P5Q-PRO:~/Downloads$ apt-cache policy libsane-common
libsane-common:
  Installed: 1.0.27-1~experimental3ubuntu2
  Candidate: 1.0.27-1~experimental3ubuntu2
  Version table:
 *** 1.0.27-1~experimental3ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main i386 Packages
        100 /var/lib/dpkg/status
daniel@daniel-P5Q-PRO:~/Downloads$

---

### Post by Holger_Gehrke on 2018-10-31
It seems like you skipped over an important step in the text before the last code-block, namely unpacking the downloaded file and changing to the directory you unpacked it to. Also, since apt told you that libsane was already installed, you could have skipped the installation of sane-utils, but it doesn't do any harm, because apt saw that it was already installed and skipped the installation.

So once more from the top. In a terminal change to the 'Downloads' directory in your home directory```
cd ~/Downloads
```download the package```
wget https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
```unpack the package```
tar -xzf iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
```change to the directory which was created by unpacking```
cd iscan-gt-f720-bundle-1.0.1.x64.deb
```run the installer```
./install.sh
```

Holger

---

### Post by daniell59 on 2018-10-31
I am sorry to say that I am confused. I feel like I am in quicksand. I am attaching a screenshot of my downloads folder in the hope that somebody can help me.

---

### Post by daniell59 on 2018-11-01
First code executed without problem.
I am stuck here however.
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
[email]daniel@daniel-P5Q-PRO:~/Downloads/iscan-gt-f720-bundle-1.0.1.x64.deb[/email]$ tar -xzf iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
tar (child): iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
[email]daniel@daniel-P5Q-PRO:~/Downloads/iscan-gt-f720-bundle-1.0.1.x64.deb[/email]$ 

Thanks again

---

### Post by slickymaster on 2018-11-01
*Thread moved to **Hardware**.*

---

### Post by daniell59 on 2018-11-01
I don't know where to go from here. I tried everything. I re-read the instructions, I followed the advice of forum members yet I cannot get the scanner to work. It is working in my other computer with Ubuntu 16.04. I would love to have it work in this one. 
I would really hate to give up and put in a windows partition. Any further assistance will be appreciated.

---

### Post by davethesteam2 on 2018-11-02
Hi all
Yes, I sympathise with Daniel. I have exactly the same problem - my Epson V370 photo worked fine on 16.04 LTS but not on 18.04 LTS.
I understand there is a known 'bug' blamed on the new coniguration of SANE.
I have done exactly the procedures outlined, rebooted and still I get 'Could not snnd command to scanner. Check the scanner status.
I have doe search for scanner and it was recognied.
I have done as described above (thanks for the efforts for Daniel) But still no access to scanner.
The following is the log for the last try:
```
david@david-All-Series:~$ cd ~/Downloads
david@david-All-Series:~/Downloads$ wget [https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz](https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz)
 --2018-11-02 17:03:57--  [https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz](https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz)
 Resolving download2.ebz.epson.net (download2.ebz.epson.net)... 2.21.184.180
 Connecting to download2.ebz.epson.net (download2.ebz.epson.net)|2.21.184.180|:443... connected.
 HTTP request sent, awaiting response... 200 OK
 Length: 601523 (587K) [application/x-gzip]
 Saving to: ‘iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz’
 
 
 iscan-gt-f720-bundl 100%[===================>] 587.42K   540KB/s    in 1.1s     
 
 
 2018-11-02 17:04:00 (540 KB/s) - ‘iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz’ saved [601523/601523]
 
 
 david@david-All-Series:~/Downloads$ tar -xzf iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
 david@david-All-Series:~/Downloads$ cd iscan-gt-f720-bundle-1.0.1.x64.deb
 [email]david@david-All-Series:~/Downloads/iscan-gt-f720-bundle-1.0.1.x64.deb[/email]$ ./install.sh
 [sudo] password for david:  
 Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
 Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
 Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]    
 Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]  
 Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [204 B]
 Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [9,412 B]
 Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [9,087 B]
 Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [16.3 kB]
 Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [419 kB]
 Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [374 kB]
 Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [185 kB]
 Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [44.5 kB]
 Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [83.3 kB]
 Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [566 kB]
 Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [571 kB]
 Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [194 kB]
 Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [182 kB]
 Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [309 kB]
 Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
 Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [5,104 B]
 Fetched 3,217 kB in 3s (1,276 kB/s)                                       
 Reading package lists... Done
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Note, selecting 'libsane1' instead of 'libsane'
 libsane1 is already the newest version (1.0.27-1~experimental3ubuntu2).
 The following packages were automatically installed and are no longer required:
   djvulibre-bin gir1.2-goocanvas-2.0 libalgorithm-c3-perl
   libb-hooks-endofscope-perl libb-hooks-op-check-perl libbit-vector-perl
   libcarp-clan-perl libclass-c3-perl libclass-c3-xs-perl
   libconfig-general-perl libdata-optlist-perl libdate-calc-perl
   libdate-calc-xs-perl libdevel-callchecker-perl libdevel-caller-perl
   libdevel-globaldestruction-perl libdevel-lexalias-perl
   libdevel-stacktrace-perl libdist-checkconflicts-perl
   libdynaloader-functions-perl libemail-date-format-perl libeval-closure-perl
   libexception-class-perl libfilesys-df-perl libfont-ttf-perl
   libgoocanvas-2.0-9 libgoocanvas-2.0-common libgoocanvas2-perl
   libgraphicsmagick++-q16-12 libgraphicsmagick-q16-3 libgtk3-simplelist-perl
   libhocr-python libimage-sane-perl libipc-shareable-perl liblog-dispatch-perl
   liblog-log4perl-perl libmail-sendmail-perl libmime-lite-perl
   libmime-types-perl libmodule-implementation-perl libmodule-runtime-perl
   libmro-compat-perl libnamespace-autoclean-perl libnamespace-clean-perl
   libossp-uuid-perl libossp-uuid16 libpackage-stash-perl
   libpackage-stash-xs-perl libpadwalker-perl libparams-classify-perl
   libparams-util-perl libparams-validationcompiler-perl libpdf-api2-perl
   libreadonly-perl libref-util-perl libref-util-xs-perl librole-tiny-perl
   libset-intspan-perl libspecio-perl libsub-exporter-perl
   libsub-exporter-progressive-perl libsub-identify-perl libsub-install-perl
   libsub-quote-perl libsys-hostname-long-perl libtiff-tools libusb-0.1-4
   libvariable-magic-perl pdf2djvu python-glade2 python-numpy python-olefile
   python-pil python-sane
 Use 'sudo apt autoremove' to remove them.
 0 to upgrade, 0 to newly install, 0 to remove and 15 not to upgrade.
 (Reading database ... 185351 files and directories currently installed.)
 Preparing to unpack .../core/iscan_2.30.2-2_amd64.deb ...
 Unpacking iscan (2.30.2-2) over (2.30.2-2) ...
 Preparing to unpack .../iscan-data_1.36.0-1_all.deb ...
 Unpacking iscan-data (1.36.0-1) over (1.36.0-1) ...
 Selecting previously unselected package esci-interpreter-gt-f720.
 Preparing to unpack .../esci-interpreter-gt-f720_0.1.1-2_amd64.deb ...
 Unpacking esci-interpreter-gt-f720 (0.1.1-2) ...
 Setting up iscan-data (1.36.0-1) ...
 Setting up iscan (2.30.2-2) ...
 Setting up esci-interpreter-gt-f720 (0.1.1-2) ...
 Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
 Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
 Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
 Processing triggers for mime-support (3.60ubuntu1) ...
 Processing triggers for udev (237-3ubuntu10.3) ...
 Processing triggers for libc-bin (2.27-3ubuntu1) ...
 [email]david@david-All-Series:~/Downloads/iscan-gt-f720-bundle-1.0.1.x64.deb[/email]$ 
```
I am now of the view that nothing will work on my scanner until the bug is fixed - in the meantime I'm having torely on my camera for any copying of paper that I need to do.......

---

### Post by davethesteam2 on 2018-11-02
One thing I would add:
The Epson downloads are specific about the order in which the 3 sections should be installed:
1) Data, 
2) Core
2)Plug-ins
When installing through the GUI installer, this order was adhered to.

---

### Post by daniell59 on 2018-11-02
I would think that an HP scanner would work out of the box. I am thinking of installing Windows XP on a different hard drive and when I need the scanner, I will go to that hard drive.

---

### Post by ajgreeny on 2018-11-02
> **daniell59 said:**
> I would think that an HP scanner would work out of the box. I am thinking of installing Windows XP on a different hard drive and when I need the scanner, I will go to that hard drive.
I think you're correct about HP printers/scanners; just about any HP machine will be installed and often work without any action on your part; it is usually detected and ready to use out of the box.

---

### Post by him610 on 2018-11-02
Could you please display, between code tags, the results of *scanimage -L*

---

### Post by Holger_Gehrke on 2018-11-02
@davethesteam2: Not very surprising. The driver at [https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz](https://download2.ebz.epson.net/iscan/plugin/gt-f720/deb/x64/iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz) is for the Epson Perfection **30**. If I search for the Perfection **370** at Epson's site, I get this URL: [https://download2.ebz.epson.net/iscan/plugin/perfection-v370/deb/x64/iscan-perfection-v370-bundle-1.0.1.x64.deb.tar.gz](https://download2.ebz.epson.net/iscan/plugin/perfection-v370/deb/x64/iscan-perfection-v370-bundle-1.0.1.x64.deb.tar.gz) Not just different URLs but actually different files (downloaded both and compared them). I don't know whether this one will make your scanner work (I have neither the 30 nor the 370), but you could try it.

Holger

---

### Post by him610 on 2018-11-02
After viewing the contents of your Downloads, I can see you have downloaded and unzipped the correct file three different times. You should be able to complete the installation with what you have on hand.

Open a terminal and navigate down to the directory where the installation will be performed.  <<==**IMPORTANT**
```
$cd ~/Downloads/iscan-bundle-1.0.1.x64.deb
```

Next, let's see what's in the directory.
```
$ls -l 
```

There should be a couple of directories and a couple of files, one which is install.sh
let's run that file now,
```
$ ./install.sh
```
Enter your password when prompted:

You should now see several pages of lines scrolling up the terminal window ending with a return to your prompt. Hopefully you will get no errors.

There are a couple of ways you can check the installation.

```
dpkg -l | grep iscan 
```
This is what mine looks like...
```
$ dpkg -l | grep iscan
ii  iscan                                 2.30.2-2                                    amd64        simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                            1.36.0-1                                    all          Image Scan! for Linux data files
 
```
or
```
 scanimage -L
```
Again, this is what mine looks like...
```
 scanimage -L
device `epson2:libusb:001:009' is a Epson Perfection1640 flatbed scanner

```
If both show similar results then try scanning a document

Note: I am running a system with Ubuntu 18.04.1 that I just installed a few days ago. Your post actually prodded me into installing the Epson scanner software for myself. Everything works, I only used the file downloaded from the Epson Scanner Driver Downloads webpage you referenced. All driver installations should be this easy.

By the way, you need to clean out your Downloads directory when finished. Too much clutter!

---

### Post by daniell59 on 2018-11-03
Thanks to all for your informative replies. I cleaned out the downloads directory and will start again after a brief rest. I only have one monitor for two computers. I put back the computer that has the 16.04 installed. I am sure that with this helpful forum, i will eventually succeed.

---

### Post by davethesteam2 on 2018-11-08
Hi again
Yes, mine looks exactly as your $ dpkg entry - still no scanne r though.......

However, using scan image I get:
  	 	 	 	   david@david-All-Series:~$ scanimage -L
 
 
 No scanners were identified. If you were expecting something different,
 check that the scanner is plugged in, turned on and detected by the
 sane-find-scanner tool (if appropriate). Please read the documentation
 which came with this software (README, FAQ, manpages).


My scanner is plugged in

Help!!!!

---

### Post by davethesteam2 on 2018-11-08
Thanks Holger
Still inable to get the scanner working

---

### Post by davethesteam2 on 2018-11-08
**I have done a basic set of look ups using lsusb and here are the results:**
  	 	 	 	   ```
david@david-All-Series:~$ lsusb
 Bus 002 Device 002: ID 8087:8000 Intel Corp.  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 002: ID 8087:8008 Intel Corp.  

 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 003 Device 004: ID 041e:4095 Creative Technology, Ltd Live! Cam Sync HD [VF0770]
 Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
 Bus 003 Device 002: ID 04a9:10d8 Canon, Inc.  
 [COLOR=#ce181e]Bus 003 Device 013: ID 04b8:014a Seiko Epson Corp. [/COLOR] 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
  	 	 	 	   
```
lsusb -v
 Bus 003 Device 013: ID 04b8:014a Seiko Epson Corp.  
 Couldn't open device, some information will be missing
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass          255 Vendor Specific Class
   bDeviceSubClass       255 Vendor Specific Subclass
   bDeviceProtocol       255 Vendor Specific Protocol
   bMaxPacketSize0        64
   idVendor           0x04b8 Seiko Epson Corp.
   idProduct          0x014a  
   bcdDevice            1.00
   iManufacturer           1  
   iProduct                2  
   iSerial                 0  
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           32
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0  
     bmAttributes         0xc0
       Self Powered
     MaxPower                2mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           2
       bInterfaceClass       255 Vendor Specific Class
       bInterfaceSubClass    255 Vendor Specific Subclass
       bInterfaceProtocol    255 Vendor Specific Protocol
       iInterface              0  
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes

         bInterval             255
  
  

**I have also checked software installation and this is the output:**
  	 	 	 	   david@david-All-Series:~$ dpkg -l | grep iscan
 ii  iscan                                         2.30.2-2                                    amd64        simple, easy to use scanner utility for EPSON scanners
 ii  iscan-data                                    1.36.0-1                                    all          Image Scan! for Linux data files
 ii  iscan-plugin-perfection-v370                  1.0.0-2                                     amd64        Plugin for the GT-F740/S640 and Perfection V37/V370 Photo
```
  
**and then the look up for the scanner through scanimage:**
   	 	 	 	   ```
david@david-All-Series:~$ scanimage -L
 
 
 No scanners were identified. If you were expecting something different,
 check that the scanner is plugged in, turned on and detected by the
 sane-find-scanner tool (if appropriate). Please read the documentation
 which came with this software (README, FAQ, manpages).
```

  
So, we have software installed correctly for the Epson V370 Photo, we have the scanner  identified on the USB system, but the 2 will not identify each other.
Could you please help to make the 2 talk to each other?
Many thanks

---

### Post by daniell59 on 2018-11-09
I am ashamed to say it, but I still cannot get it to work. It seemed like the drivers installed. I tried doing it numerous times. If anybody still has the patience to work with me, I will try again.

Thanks in advance

---

### Post by davethesteam2 on 2018-11-09
Hi Daniell59
We are both in the same boat I think. 
It is now clear to me that neither of us have made any errors in our attempts.
Quite early on in the posts, these problems were advised as being a 'bug' that only occurred with Ubuntu 17.10 and later.
Now that we have 18.04 LTS - which is the version most of us ordinary users will be moving to, I am afraid it looks as if we will need to rely on the specialists to sort it out for us - I have absolutely no idea how to do the job myself.
Are there any specialists / developers out there who know how to help us please?

---

### Post by daniell59 on 2018-11-09
Hi Dave,

i cannot tell you with any certainty whether it is a bug in the OS or my lack of knowledge. I may at some point reinstall Ubuntu 16.04 in another computer and see if I can get it to work. For the time being, if I need something scanned, I will go back to an old installation of Windows XP.

---

### Post by davethesteam2 on 2018-11-10
Hi again Daniell
See this link from elsewhere in Ubuntu help:

 "I fear that this is a known bug. See [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)

  Although they're referring to 18.04 that's the same version of  libsane1 as in 17.10 and the change to sane appears to have stopped  various Epson scanners from working."

This was found in slack exchange

---

### Post by daniell59 on 2018-11-10
> **davethesteam2 said:**
> Hi again Daniell
See this link from elsewhere in Ubuntu help:

 "I fear that this is a known bug. See [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012)

  Although they're referring to 18.04 that's the same version of  libsane1 as in 17.10 and the change to sane appears to have stopped  various Epson scanners from working."

This was found in slack exchange

Thanks Dave. Now at least I can stop trying and think of my options. I also have a DVD of Vista. I don't know whether I will be able to activate it again at this late date. My other option is to reinstall Ubuntu 16.04.

---

### Post by SeijiSensei on 2018-11-10
I have an unsupported HP scanner that works with VueScan. You could give that a try.

[https://www.hamrick.com](https://www.hamrick.com)

---

### Post by daniell59 on 2018-11-10
> **SeijiSensei said:**
> I have an unsupported HP scanner that works with VueScan. You could give that a try.

[https://www.hamrick.com](https://www.hamrick.com)



Thanks for the information.

---

### Post by daniell59 on 2018-11-16
On one of my computers, i just went back to Ubuntu 16.04. Hopefully I will be able to install the Epson drivers and make the scanner work. By the way, I like Ubuntu 16.04 better than 18.04.

---

### Post by daniell59 on 2018-11-18
I was able to install the Epson scanner drivers on Ubuntu 16.04. The scanner is now functioning. Thanks to all for your informative assistance.

---

### Post by marty777 on 2019-01-09
The ones, still struggling with the Epson scanner drivers:
I got it also running with Ubuntu Studio 18.10 (Xubuntu). 
Well, more or less. ;) Xsane and the scanimage program is working well.
(The imagescan (Epson) and simple-scan program do not work. I think there is still some permission problem going on.)
Here my description:
[https://ubuntuforums.org/showthread.php?t=2383646&page=3](https://ubuntuforums.org/showthread.php?t=2383646&page=3)

---

### Post by suzukawa on 2019-01-13
I also struggled some days ago with my EPSON V33 in Ubuntu 18.04.1. Going back to 16.04 was not really an option.
But I found a solution in the bugreport-lauchpad-forum that I followed and got the scanner to work (with SimpleScan without root).

[URL="https://bugs.launchpad.net/debian/+source/sane-backends/+bug/1707352/comments/108"]https://bugs.launchpad.net/debian/+source/sane-backends/+bug/1707352/comments/108
[/URL]
My scanner is connected via usb, not in a network.
In order to let Ubuntu detect your scanner instantly ("scanimage -L"), you may further have to comment out (#) all in the other epson backend-config-files (epson.conf, epson2.conf, epsonds.conf, ...) in the folder /etc/sane.d/ , because they seem to interfere each other making it to last minutes. Only uncommented "usb" in the epkowa.conf is necessary.

---

