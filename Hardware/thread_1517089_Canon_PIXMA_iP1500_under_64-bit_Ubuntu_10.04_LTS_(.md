---
title: "Canon PIXMA iP1500 under 64-bit Ubuntu 10.04 LTS (Lucid)"
date: 2010-06-24
forum: Hardware
---

### Post by RobDonovan on 2010-06-24
This HowTo will describe how to get a Canon PIXMA iP1500 printer working under 64-bit Ubuntu 10.04 LTS (Lucid). At the end of this HowTo you should be able to print from applications, from the command line using lpr, and from Canon's bjcups utility.

Before I start I should say that I have root enabled on my system.  Some of the steps below must be done as root, but others not.  I've tried to type sudo everywhere where it would have been required.  If you get "permission denied" at any point, I may have slipped up.

0) I'll start by saying that I saw a comment somewhere that people were having trouble with CUPS under Ubuntu 10.04, but that these problems were fixed by doing a simple reinstall of CUPS.  I'd done this already before I tried to attach this printer.  I can't say that this was necessary, but since I'd done it, I'll mention it.  If you continue without doing this, and everything works, perhaps you could post a note below to this effect.

1) Download the Canon PIXMA ip1500 printer drivers for Linux from

[http://www.canon-europe.com/Support/Software/Linux/2005/download.asp?ComponentID=369142&SourcePageID=312227#1](http://www.canon-europe.com/Support/Software/Linux/2005/download.asp?ComponentID=369142&SourcePageID=312227#1)

   Save the package to a directory in your home, say ~/sysadmin/
   These are rpms and can't be installed under Ubuntu directly.

2) Unpack the Canon tarball

cd ~/sysadmin/canon/
tar -xzf iP1500Linux.tar.gz

3) You can look at the documentation that came with the rpms from Canon by pointing your browser at  ~/sysadmin/iP1500/guide_index.htm
         This can be pretty useful.

4) Get alien for installing the rpms

sudo apt-get update
sudo apt-get install alien

5) The next step is to convert the rpms into debs for installation under Ubuntu.  This is complicated by the fact that the rpms are 32 bit.

    The command "sudo alien *i386.rpm" will barf with complaints about amd64 not appearing in the packages architecture list (i386).  I tried to get around this using alien -g but there were other failures.

    I got around this problem by running sudo alien *i386.rpm on an old 32 bit machine on which I have installed 32 bit Ubuntu 10.04, then copying the .deb files over.
    An alternative solution for those without a spare 32 bit machine may be to boot your 64bit machine from a 32 bit Live CD version of Ubuntu (I would suggest using 10.04).
   
   Since both the above steps are a pain and since my interpretation of Canon's copyright is that I'm allowed to do so, I will also attempt to post the Ubuntu 10.04 .debs as attachments to the post following this one.  If that works you can just download them directly from here.

   However you get them I'll assume the .debs are now in ~/sysadmin/debs/

6) To install i386 debs under amd64 run this in the ~/sysadmin/debs/ directory:

sudo dpkg --force-architecture -i *.deb

7) Put in sym links

cd /usr/lib32
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libpng12.so.0 libpng.so.2
sudo ln -s libxml2.so.2 libxml.so.1

   Note that the xml link will be overwritten below if you choose to get bjcups working.

8) The above installation installed quite a few libraries in /usr/lib instead of /usr/lib32
     We'll move them to the correct directory:

cd /usr/lib32
sudo mv /usr/lib/libcnbpcmcm214.so* .
sudo mv /usr/lib/libcnbpcnclapi214.so* .
sudo mv /usr/lib/libcnbpcnclbjcmd214.so* .
sudo mv /usr/lib/libcnbpcnclui214.so* .
sudo mv /usr/lib/libcnbpess214.so* .
sudo mv /usr/lib/libcnbpo214.so* .

    Note that the directory

/usr/lib/bjlib/

    contains conf files, not libraries.  It MUST remain in /usr/lib/.  lpr will not print if this is moved to /usr/lib32/

9) Tip for people trying to get this printer running under future versions of Ubuntu:
    The installation puts the following binaries into /usr/local/bin/

bjcmdpixmaip1500
bjcups
bjcupsmon
bjfilterpixmaip1500
lgmonpixmaip1500
pixmaip1500_ps
pixmaip1500_raw
printuipixmaip1500
stsmonpixmaip1500

    You can determine which libraries are missing/required by running these commands from the command line - they will complain about what is missing.  Alternatively, using

ldd binary

will give you a full list of the libraries used by each binary, noting any that are missing.
I suggest starting with bjfilterpixmaip1500 - that seems to be pretty central.

10) Restart cups:

sudo /etc/init.d/cups restart

11) Connect your printer and switch it on

12) You can add the printer to your system using either:

A) System->Admin->Printing under Gnome Desktop, or
B) The CUPS system admin page at [http://localhost:631](http://localhost:631)

     The latter is worth a look even if you use the Gnome App - there's lots of documentation on CUPS, print queues, etc.  All very useful.

     Choose Canon iP1500 as the printer.

     When you choose/confim names, note that the first line is the one you'll be typing after lpr -P if you need to specify, so you might like to make it something short.

     At this point you can either select the Driver from the list, or specify the ppd file in
/usr/share/cups/model/canonpixmaip1500.ppd  I think both methods worked for me.

13) With all the above steps done correctly, I successfully printed a test page.
      There are test page options under both the Gnome and CUPS interfaces.

      At this point you can successfully print from applications and using lpr from the
      command line.  To get bjcups going and for customization, read on...

14) bjcups provides a graphical interface that allows you to do everything you can
      under windows.

     The bjcups and bjcupsmon utilities have lib dependencies of their own.
     These programs will not work if you just link to newer versions of the libraries.
     You have to get the original versions.
     Luckily they can be downloaded from here (under the 386 link of course):
     Save them into ~/sysadmin/libs/

[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)
[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)
[http://packages.ubuntu.com/hardy/libxml1](http://packages.ubuntu.com/hardy/libxml1)

     As yourself:

cd ~/sysadmin/libs/
dpkg-deb -x libgtk1.2_1.2.10-18.1build2_i386.deb .
dpkg-deb -x libglib1.2ldbl_1.2.10-19build1_i386.deb .
dpkg-deb -x libxml1_1.8.17-14.1_i386.deb .

cd ~/sysadmin/libs/usr/lib/

sudo cp -d libgtk-1.2.so.0* /usr/lib32
sudo cp -d libgdk-1.2.so.0* /usr/lib32
sudo cp -d libglib-1.2.so.0* /usr/lib32
sudo cp -d libgmodule-1.2.so.0* /usr/lib32
sudo cp -d libxml.so.* /usr/lib32

     bjcups will now run. 

15) The standard ppd file is just fine, but you can add a lot more options if you want.
     
      The following options give you much of the control of bjcups, but can be used to set defaults under the CUPS Set Default Options page, under the Gnome interface Printer->Properties->Printer Options page and, perhaps most usefully, to control printing output directly from applications like Firefox, in which particular case they show up under the Image Quality and Advanced tabs. 

    First backup the ppd file :

cd /usr/share/cups/model/
sudo cp canonpixmaip1500.ppd canonpixmaip1500.ppd.install

    Edit the ppd file

gksudo gedit canonpixmaip1500.ppd

   Note that the Nickname field is the one used to list the driver in driver lists.
   When your edits are done and you add the modified driver to CUPS the previous
   version of the driver will not be removed.  It can therefore be a good idea to change
   the Nickname slightly so you can distinguish between the two in the list if you need to.
   Eg. If you end up adding this printer via NX.  I added the letters "mod" to mine:

*NickName: "Canon PIXMA iP1500 Ver.2.50 mod"

    Remove the following lines from your ppd file :

* OpenUI *Resolution/Output Resolution: PickOne
* DefaultResolution: 600
* Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
* CloseUI: *Resolution

    Add the following:

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*CloseUI: *Resolution

*OpenGroup: Color Adjustment

*OpenUI *CNGrayscale/Grayscale: PickOne
*DefaultCNGrayscale: true
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale

*OpenUI *CNDensity/Density: PickOne
*DefaultCNDensity: 0
*CNDensity -50/-50: "<</CNDensity(-50)>>setpagedevice"
*CNDensity -40/-40: "<</CNDensity(-40)>>setpagedevice"
*CNDensity -30/-30: "<</CNDensity(-30)>>setpagedevice"
*CNDensity -20/-20: "<</CNDensity(-20)>>setpagedevice"
*CNDensity -10/-10: "<</CNDensity(-10)>>setpagedevice"
*CNDensity 0/0: "<</CNDensity(0)>>setpagedevice"
*CNDensity 10/10: "<</CNDensity(10)>>setpagedevice"
*CNDensity 20/20: "<</CNDensity(20)>>setpagedevice"
*CNDensity 30/30: "<</CNDensity(30)>>setpagedevice"
*CNDensity 40/40: "<</CNDensity(40)>>setpagedevice"
*CNDensity 50/50: "<</CNDensity(50)>>setpagedevice"
*CloseUI: *CNDensity

*OpenUI *CNGamma/Gamma Adjustment: PickOne
*DefaultCNGamma: 1.8
*CNGamma 1.4/1.4: "<</CNGamma(1.4)>>setpagedevice"
*CNGamma 1.8/1.8: "<</CNGamma(1.8)>>setpagedevice"
*CNGamma 2.2/2.2: "<</CNGamma(2.2)>>setpagedevice"
*CloseUI: *CNRenderIntent

*OpenUI *CNBalanceC/Balance Cyan: PickOne
*DefaultCNBalanceC: 0
*CNBalanceC -50/-50: "<</CNBalanceC(-50)>>setpagedevice"
*CNBalanceC -40/-40: "<</CNBalanceC(-40)>>setpagedevice"
*CNBalanceC -30/-30: "<</CNBalanceC(-30)>>setpagedevice"
*CNBalanceC -20/-20: "<</CNBalanceC(-20)>>setpagedevice"
*CNBalanceC -10/-10: "<</CNBalanceC(-10)>>setpagedevice"
*CNBalanceC 0/0: "<</CNBalanceC(0)>>setpagedevice"
*CNBalanceC 10/10: "<</CNBalanceC(10)>>setpagedevice"
*CNBalanceC 20/20: "<</CNBalanceC(20)>>setpagedevice"
*CNBalanceC 30/30: "<</CNBalanceC(30)>>setpagedevice"
*CNBalanceC 40/40: "<</CNBalanceC(40)>>setpagedevice"
*CNBalanceC 50/50: "<</CNBalanceC(50)>>setpagedevice"
*CloseUI: *CNBalanceC

*OpenUI *CNBalanceM/Balance Magenta: PickOne
*DefaultCNBalanceM: 0
*CNBalanceM -50/-50: "<</CNBalanceM(-50)>>setpagedevice"
*CNBalanceM -40/-40: "<</CNBalanceM(-40)>>setpagedevice"
*CNBalanceM -30/-30: "<</CNBalanceM(-30)>>setpagedevice"
*CNBalanceM -20/-20: "<</CNBalanceM(-20)>>setpagedevice"
*CNBalanceM -10/-10: "<</CNBalanceM(-10)>>setpagedevice"
*CNBalanceM 0/0: "<</CNBalanceM(0)>>setpagedevice"
*CNBalanceM 10/10: "<</CNBalanceM(10)>>setpagedevice"
*CNBalanceM 20/20: "<</CNBalanceM(20)>>setpagedevice"
*CNBalanceM 30/30: "<</CNBalanceM(30)>>setpagedevice"
*CNBalanceM 40/40: "<</CNBalanceM(40)>>setpagedevice"
*CNBalanceM 50/50: "<</CNBalanceM(50)>>setpagedevice"
*CloseUI: *CNBalanceM

*OpenUI *CNBalanceY/Balance Yellow: PickOne
*DefaultCNBalanceY: 0
*CNBalanceY -50/-50: "<</CNBalanceY(-50)>>setpagedevice"
*CNBalanceY -40/-40: "<</CNBalanceY(-40)>>setpagedevice"
*CNBalanceY -30/-30: "<</CNBalanceY(-30)>>setpagedevice"
*CNBalanceY -20/-20: "<</CNBalanceY(-20)>>setpagedevice"
*CNBalanceY -10/-10: "<</CNBalanceY(-10)>>setpagedevice"
*CNBalanceY 0/0: "<</CNBalanceY(0)>>setpagedevice"
*CNBalanceY 10/10: "<</CNBalanceY(10)>>setpagedevice"
*CNBalanceY 20/20: "<</CNBalanceY(20)>>setpagedevice"
*CNBalanceY 30/30: "<</CNBalanceY(30)>>setpagedevice"
*CNBalanceY 40/40: "<</CNBalanceY(40)>>setpagedevice"
*CNBalanceY 50/50: "<</CNBalanceY(50)>>setpagedevice"
*CloseUI: *CNBalanceY

*OpenUI *CNBalanceK/Balance Black: PickOne
*DefaultCNBalanceK: 0
*CNBalanceK -50/-50: "<</CNBalanceK(-50)>>setpagedevice"
*CNBalanceK -40/-40: "<</CNBalanceK(-40)>>setpagedevice"
*CNBalanceK -30/-30: "<</CNBalanceK(-30)>>setpagedevice"
*CNBalanceK -20/-20: "<</CNBalanceK(-20)>>setpagedevice"
*CNBalanceK -10/-10: "<</CNBalanceK(-10)>>setpagedevice"
*CNBalanceK 0/0: "<</CNBalanceK(0)>>setpagedevice"
*CNBalanceK 10/10: "<</CNBalanceK(10)>>setpagedevice"
*CNBalanceK 20/20: "<</CNBalanceK(20)>>setpagedevice"
*CNBalanceK 30/30: "<</CNBalanceK(30)>>setpagedevice"
*CNBalanceK 40/40: "<</CNBalanceK(40)>>setpagedevice"
*CNBalanceK 50/50: "<</CNBalanceK(50)>>setpagedevice"
*CloseUI: *CNBalanceK

*CloseGroup: Color Adjustment

16) Save the ppd file.  Use the Modify Printer option under the CUPS interface to manually specify the modified ppd file.  It appears that the Printer->Properties->Settings "Make and Model" Change button under Gnome can be used to do the same thing.

17) You can specify that the printer becomes the default printer in the CUPs web interface.  I found this didn't seem to be recognised by the lpr command though.
   
lpoptions -d your-printer-short-name

    Fixes that.

18) The following threads were useful in putting all this together:

[https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500)
[http://ubuntuforums.org/showthread.php?t=1497702](http://ubuntuforums.org/showthread.php?t=1497702)
[http://ubuntuforums.org/showthread.php?t=593414](http://ubuntuforums.org/showthread.php?t=593414)
[http://www.uluga.ubuntuforums.org/showthread.php?p=9261604](http://www.uluga.ubuntuforums.org/showthread.php?p=9261604)

---

### Post by RobDonovan on 2010-06-24
The bad news is that the Forum software wouldn't let me upload any of the debs.
I can see that it would be a security risk to install debs posted on a forum.

---

### Post by RobDonovan on 2010-06-24
If you do try to use the printer attached to an NX Nomachine client machine you may find that print jobs submitted to the printer via the NX session wont print.  If you look at the print queue using the Cups web interface and see the error message

/usr/lib/cups/backend/nx failed

 and the same message repeated in /var/log/cups/error_log where you also find 

/usr/lib/cups/backend/nx: Permission denied

  then the problem is that apparmor is preventing Cups from running the NX backend.  This can be fixed by editing the following config file

gksudo gedit /etc/apparmor.d/usr.sbin.cupsd

   and modifying it (by adding just the NX line) to read

# third party backends get no restrictions as they often need high
# privileges and this is beyond our control
/usr/lib/cups/backend/* Ux,
/usr/NX/bin/nxspool Ux,

   Save the file then restart apparmor using

sudo /etc/init.d/apparmor restart

   The problem is/was that NX places a symlink at /usr/lib/cups/backend/nx that points to the binary at /usr/NX/bin/nxspool which apparmour then prevents cups from running.

   Thanks to John A Sullivan III on this thread [http://ubuntuforums.org/showthread.php?t=809922](http://ubuntuforums.org/showthread.php?t=809922) for this fix.

---

### Post by Gianpiero Piccolo on 2013-04-05
Great! You have been the Man who saved all new Ubuntu / Linux 64bit users with an old Canon PIXMA iP1500!!!!
I didn't have to restart cups at the step 0: I didn't do it and I reached anyway the right solution.

Now I can say "I never won't return to M$ Windows!!!": with my Ubuntu 12.10 I can reuse my old printer. However, as soon as the ink cartrige has run out, I'll buy a new Laser Monocromatic Printer! Any suggestions on what kind of printer to buy are welcome!

The Last thanks for the steps 15 and 16: they helped me to save ink, respect the envirnoment and print in grayscale!! Great man!

Bye!

Gianpiero

---

