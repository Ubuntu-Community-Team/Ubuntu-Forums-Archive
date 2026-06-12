---
title: "Ubuntu 8.04LTS Gvision J5PX Touchscreen Help"
date: 2008-11-08
forum: General Help
---

### Post by ihitf13anddied on 2008-11-08
Hello all,

I have a Gvision J5PX SERIAL touchscreen and I am attempting to install drivers so that I can use it with Ubuntu. The drivers I am referencing can be found here:

[http://www.gvision-usa.com/s-drivers.htm](http://www.gvision-usa.com/s-drivers.htm)

When i run the setup that comes with the driver (after making it executable) by typing "sudo ./tscom_setup" and click Next (its GUI), I get the following error:



X WINDOW SYSTEM


**********************************************
FAIL TO GET XOrg/XF86 VERSION! (2)/(7)
**********************************************

Click Cancel to exit Setup.


And thats all I get. Any ideas? It seems to come with many tar.gz files, but I am not sure what to do with them short of having the setup program run them for me.

Any help would be greatly appreciated!

---

### Post by ihitf13anddied on 2008-11-08
I was blind to the documentation...there is an included file (PDF) as well as one on the site. I'll give it a shot and post results...

---

### Post by ihitf13anddied on 2008-11-08
```
Installation          manually (for expert)
We recommand that you using the Setup Wizard to complete the install, refer to                                Installation using
Setup Wizard           section for detail.
The followings describe how to complete the install manully:
1. Login as root.
2. Checking the X Window System Version.
To get the X Window System Version by running the following:
X -version
Write down the X Window System Version that you using, it's required when installing the Driver
Package later.
3. Removing the Previous Installed Version.
remove the previous installed directory and files by running the followings:
rm -vfr /etc/TSCOM
rm -vf /usr/X11R6/lib/modules/input/tscom_drv.o
rm -vf /usr/X11R6/lib/modules/input/tscomxp_drv.o
4. Creating the Install Directory.
Make a new directory named                 TSCOM          in the      /etc      directory and set correspond access permissions
to it, we recommand that you set permissions mode 0755 to the Install Directory.
Create Install Directory by running the following:
mkdir -m 0755 /etc/TSCOM
5. Installing Common Package.
The Common Package is a file named                     tscom-2.0.0-common.tar.gz , it's required to install for all X
Window System version.
Extra the the Common Package file by running the followings (replace the sourcePath to the path of
the Common Package file):
cd /etc/TSCOM
gzip -d < sourcePath/tscom-2.0.0-common.tar.gz | tar vxf -
6. Installing Driver Package.
The Driver Package is all of file named                 tscom-2.0.0-driver-xxx.tar.gz , where xxx indicates that it
supported what X Window System Version. Refer to the following table to choose a Driver Package
Filename correspond with the X Window System Version that you using:
------------------------------------------------------------ ------------------------------------------------
Using X Window System Driver Package Filename
------------------------------------------------------------ ------------------------------------------------
XOrg Version 6.4.x / XFree86 Version 4.1 tscom-2.0.0-driver-410.tar.gz
XOrg Version 6.5.x / XFree86 Version 4.2 tscom-2.0.0-driver-420.tar.gz
XOrg Version 6.5.x / XFree86 Version 4.2.1 tscom-2.0.0-driver-421.tar.gz
XOrg Version 6.6.x / XFree86 Version 4.3.x tscom-2.0.0-driver-430.tar.gz
XOrg Version 6.7.x / XFree86 Version 4.4.x tscom-2.0.0-driver-440.tar.gz
XOrg Version 6.8.x / XFree86 Version 4.5.x tscom-2.0.0-driver-450.tar.gz

Extra the the Driver Package file by running the followings (replace the sourcePath to the path of
the Driver Package file, and replace the xxx to set the filename to the Driver Package Filename that
you want to install):
cd /etc/TSCOM
gzip -d < sourcePath/tscom-2.0.0-driver-xxx.tar.gz | tar vxf -
7. Setting Correspond Access Permissions to Installed Files.
We recommand that you set correspond access permissions to each file in the Install Directory,
Set permissions to each file in the Install Directory by running followings:
cd /etc/TSCOM
chmod 0444 tscom_drv.o
chmod 0444 tscomxp_drv.o
chmod 0666 tscom-config
chmod 0755 tscom_calibrate
chmod 0666 tscom_calibrate.log
chmod 0755 tscom_rightbutton
chmod 0666 tscom_rightbutton.log
8. Installing the TSCOM XInput Device Drivers.
For loading the TSCOM XInput Device Drivers when the X Window System booting, All of TSCOM
drivers must present in the XInput Drivers Directory ( /usr/X11R6/lib/modules/input ), you can use
   Copy File     or    Create Symbolic File     command to install TSCOM drivers, from the Install Directory to
the XInput Drivers Directory.
We recommand that you Install TSCOM drivers by running the followings:
cd /usr/X11R6/lib/modules/input
ln -s /etc/TSCOM/tscom_drv.o tscom_drv.o
ln -s /etc/TSCOM/tscomxp_drv.o tscomxp_drv.o
9. Configurating the X Window System.
In order to use TSCOM Touchscreen with the X Window System, you need to configurate the X
Window System by editting the X Config File, the followings describe how to do that.
· Opening the X Config File.
Use any text editer to open the X Config File in edit mode. The path and filename of the X Config
File is depended on the Linux Distribution that you using, locate to the     /var/log   directory, open
the file named      XFree86.0.log    or    Xorg.0.log , search in the file with     Using config file: string,
the path and filename of the X Config File shows following the string.
· Add two InputDevice Section.
Section "InputDevice"
Identifier "TSCOM_Touchscreen
Driver "tscom"
Option      "Device" "/dev/ttyS0"
Option "DeviceModel" "TS"

Option "ScreenNo" "0"
Option "SendCoreEvents" "yes"
EndSection
Section "InputDevice"
Identifier "TSCOM_Calibration
Driver "tscomxp"
EndSection
Note:
(1) The instructions above are case-sensitive.
(2) The instructions above are for a touchscreen connected to COM1, the Option      Device
specifies the COM port the touchscreen is connected to. The following describe how to use:
Use Option      Device       /dev/ttyS0   for COM1.
Use Option      Device       /dev/ttyS1   for COM2.
Use Option      Device       /dev/ttyS2   for COM3.
Use Option      Device       /dev/ttyS3   for COM4.
· Add two InputDevice lines to the ServerLayout Section.
Section "ServerLayout"
InputDevice "TSCOM_Touchscreen" "SendCoreEvents"
InputDevice "TSCOM_Calibration"
EndSection
Note:
(1) The instructions above are case-sensitive.
(2) If no pointer device configed to "CorePointer", you can change the "SendCoreEvents" to
"CorePointer" in the InputDevice "TSCOM_Touchscreen" line.
· Save changes to the X Config File.
10.Restarting the X Window System.
After you complete the install, you must reboot your computer or restart the X Server for the new
settings to take effect, and make the TSCOM Touchscreen start to working.

```

This is what I followed, except where it said to make the symbolic links, i ALSO made symbolic links in "/usr/lib/xorg/modules/drivers".

I also used the 450 driver pack, figuring that Ubuntu had the latest xorg stuff ( my X-version command displayed nothing relevant to the listed version numbers in driver pack).


Unfortunately, cat /dev/ttyS0 and ttyS1 (i have 2 ports) do not yield any output when I touch my screen.

Any ideas?

---

### Post by ihitf13anddied on 2008-11-08
UPDATE: had a faulty serial cable. Now i can cat ttyS1 and when i touch the screen, sure enough i get garbled stuff which means it is communicating. Only problem is that even after following driver procedures, my touchscreen STILL does not work (although i can still see the activity on ttyS1).

---

### Post by rjgii on 2008-11-09
I'm experiencing the same issues described here, also with a GVision.

Tried both the TSCOM drivers included and the ELO drivers. The ELO drivers crased X, and the TSCOM drivers are doing nothing. 

X seems to not be able to locate the TSCOM drivers, Xorg.0.log section:

(EE) Failed to load module "tscom" (module does not exist, 0)
(EE) Failed to load module "tscomxp" (module does not exist, 0)
(EE) No Input driver matching `tscom'
(EE) No Input driver matching `tscomxp'

Still trying...

---

### Post by rjgii on 2008-11-09
I got it working perfectly, and can run both the configuration program and the right-mouse click program.

I don't have time right now, but hopefully tomorrow I'll be able to type up the whole process for anyone else experiencing this issue.

---

### Post by ihitf13anddied on 2008-11-09
I would be absolutely DELIGHTED if you could post the howto on this one...it certainly threw me for a loop!!

TIA,
Chris

---

### Post by rjgii on 2008-11-10
I actually did all this using Ubuntu 8.10, but the steps should be the same for 8.04.

First of all, we'll be compiling the driver from source.

The GTouch driver is actually maintained by a company called HiggsTec, as a nice Newegg reviewer pointed out, and can be downloaded here: [http://www.higgstec.com/download.htm](http://www.higgstec.com/download.htm) (Higgstec RS-232 Port - Linux series driver 2.0.2).

Before we get to compiling the touch screen drivers, set up your environment for building:

Open a teminal and run the following commands to get some required build packages:

```
sudo apt-get install build-essential checkinstall
```

If you look at the **tscom-source-2.0.2-readme.pdf** that came in the download archive for the driver source, you'll see that is says you need the Xorg sources for building. Run this command in the terminal to get the xorg dev packages, which should have all you need:

```
sudo apt-get install xserver-xorg-dev
```

Now we can get the tscom touchscreen drivers compiled. Most of this is covered in the **tscom-source-2.0.2-readme.pdf** document, but it's a bit too generic. The following steps are more specific to Ubuntu (like the addition of the needed sudo call before the make install commands).

Create a directory to hold your source files (I use **/home/username/Sources**).

Extract the contents of the **TS-COM-Linux.rar** archive downloaded from HiggsTec to this folder.

In a terminal change to the directory you extracted the sources to.

Extract the source files from the .tar.gz archive:

```
tar xfvz tscom-source-2.0.2.tar.gz

```
Change to the newly extracted driver source directory (we want **xorg-7.3**):

```
cd tscom-2.0.2/drivers/xorg-7.3
```

There are two drivers here we need to compile.

Run the following to compile the tscom driver:

```
cd tscom
./configure --prefix=/usr
make clean
make
sudo make install
```

That should do it for the tscom driver, now the tscomxp driver (used for the calibration tool):

```
cd ../tscomxp
./configure --prefix=/usr
make clean
make
sudo make install

```

Your touchscreen drivers should now be installed, but that won't do you much good without calibrating it, and you probably wouldn't mind the right-click feature as well. So lets compile those apps as well, before rebooting X and testing it out.

From the **tscom-2.0.2** directory, change to the programs directory:

```
cd programs
```

Now compile the calibrate app (no configuring to be done):

```
cd calibrate
make clean
make
sudo make install

```

Now for the right-click button program (again, no configuring needed):

```
cd ../rightbutton
make clean
make
sudo make install

```

Now that you have everything you need install, lets edit the xorg.conf to reflect the new drivers:

```
sudo gedit /etc/xorg.conf
```

Remove anything you have from previous attempts, and then add the following input device sections:

```
Section "InputDevice"
         Identifier "TSCOM_Touchscreen"
         Driver     "tscom"
         Option     "Device"           "/dev/ttyS1"
         Option     "DeviceModel"      "TS&#8221;
         Option     "ScreenNo"         "0"
         Option     "SendCoreEvents"   "yes"
EndSection
Section  "InputDevice"
         Identifier "TSCOM_Calibration"
         Driver     "tscomxp"
EndSection
```

Note that the Device section should contain the serial port the monitor is connected to.

Now add the following to the ServerLayout section:

```
InputDevice "TSCOM_Touchscreen" "SendCoreEvents"
InputDevice "TSCOM_Calibration"
```

Almost done. Time to calibrate and test all this work.

Restart X by pressing **ctrl+alt+backspace**.

Log in, and touch the screen, hopefully you'll get a response, even if it's a bad one.

Time to run the calibration program, open a terminal and run the calibrate command:

```
/etc/TSCOM/tscom_calibrate

```
Follow the instructions, and touch the 4 crosshairs.

If you want to have a right-click button on your desktop, run the following command (I made a launcher for it):

```
/etc/TSCOM/tscom_rightbutton
```


Hopefully, that should do it. Hopefully I'll have time to polish this up and post it in a more official format, so let me know if you run into any problems, I'd like to sort them out before I post an all-inclusive walk-through.

---

### Post by ihitf13anddied on 2008-11-10
So I recently went to 8.10. Fresh install, then I followed your directions and the driver installs seemed fine.

However, my /etc/X11/xorg.conf file did not contain a "ServerLayout" section so I just tried creating one and adding those two lines you told me to add.

Unfortunately, this messed up X (caused it to start in low graphics mode) but I was lucky to see the issue in error logs. The "ServerLayout" section, according to the logs, must have an 'Identifier' named. None of the other Ubuntu boxes here in the house have a ServerLayout section to compare to, so I'm not sure what to put in there.

Would you mind posting your xorg.conf for comparison?

Thanks again,
Chris

---

### Post by ihitf13anddied on 2008-11-10
Here is a copy of MY current working /etc/X11/xorg.conf file that does not cause errors on boot.

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I'm using an MX420 WITHOUT the Nvidia (96) drivers that Ubuntu recommends. When I use them, my max res is 640x480, but without i can go higher.

---

### Post by rjgii on 2008-11-11
I'm at work at the moment, but I'll post it when I'm out.

I'll also post what I think yours should look like as well. You shouldn't have to add too much.

---

### Post by ihitf13anddied on 2008-11-11
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
         Identifier "TSCOM_Touchscreen"
         Driver     "tscom"
         Option     "Device"           "/dev/ttyS1"
         Option     "DeviceModel"      "TS”
         Option     "ScreenNo"         "0"
         Option     "SendCoreEvents"   "yes"
EndSection
Section  "InputDevice"
         Identifier "TSCOM_Calibration"
         Driver     "tscomxp"
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice "TSCOM_Touchscreen" "SendCoreEvents"
	InputDevice "TSCOM_Calibration"
EndSection

```

I can boot with this config, no errors. I am using the default driver, which is perfectly fine since I do not need 3d acceleration on this machine.

The touch screen does not work with this config, although ttyS1 still has output when I touch the screen. At least I know it's talking.

I can also run the calibration tool without flaws (I was getting a segmentation fault on the old drivers/old install) but of course I cannot press the center of the cross since the TS driver isn't working yet.

I wouldn't be able to RUN the calibrate program unless the calibration driver was getting properly loaded in my xorg.conf, correct?

I'm certainly learning a LOT through this whole process :)


Truly grateful,
Chris

---

### Post by rjgii on 2008-11-11
Hmmm, check your input modules directory to make sure the drivers are there:

/usr/lib/xorg/modules/input

If the original compile went smoothly, you should see both of the tscom drivers in there.

There's not much more I can do right now without it in front of me.

---

### Post by ihitf13anddied on 2008-11-11
```

/usr/lib/xorg/modules/input$ ls
evdev_drv.so  mouse_drv.so      tscom_drv.la  tscomxp_drv.la  vmmouse_drv.so
kbd_drv.so    synaptics_drv.so  tscom_drv.so  tscomxp_drv.so  wacom_drv.so

```

Fantastic, it looks like they are installed. Don't worry I am in no kind of rush here...I have learned that with all things Linux you need time and patience ;)

---

### Post by ihitf13anddied on 2008-11-12
Also, are you using the same monitor as I am? I did a bunch of research and with my current config file plus the drivers being installed my monitor touch should work as far as I can tell, but the drivers dont show up under the currently loaded drivers list. I'm hoping that theres just something small that I am missing here.

---

### Post by rjgii on 2008-11-13
I'm away on business for a couple days, but I did notice a few options that I have in my xorg.conf that you do not, and may make the difference.

When I'm back in town I'll post my configuration file, and you can try a couple more things first.

---

### Post by ihitf13anddied on 2008-11-13
Good luck on your trip, and I will be looking forward to your reply. :D

Thanks,
Chris

---

### Post by donnied on 2008-11-28
Thank you for this thread.  I've been reading and rereading it.  The problem I'm having (now) is compiling the calibrate and rightthumb utils.  I get the error message

********* CHECKOUT THE GLIBC VERSION! MUST BELOW 2.3
GLIBC_2.4
GLIBC_2.1
GLIBC_2.0
*********

In order to get a sufficiently new Xorg my glibc is too advanced.  How did you work around this?

ihitf13anddied, have you gotten your gvision working yet?

---

### Post by ihitf13anddied on 2008-11-28
i have not gotten mine to work yet. I would recommend searching for and manually installing glib2.3 and anything else it asks for. sometimes, it just isnt installed in Ubuntu by default but is available in the Package manager. Let me know how it works out, and please send me any input you might have on how to make mine work.

---

### Post by donnied on 2008-11-28
What's wrong with your installation? The low resolution? 

The problem is that the version of glibc I have is 2.8 which was installed before or when I install the development headers for xserver-xorg.   I'm not sure on how to install / choose a different version of glibc.

---

### Post by donnied on 2008-11-28
Ohh.. I see your problem...  I missed that.  Now, I have the same problem.  I can 
```

make
make install

```
the calibrate function and it doesn't crash.  It was segfaulting.  I am now using Ubuntu 8.04 as you are and the input device seems to be recognized.  There aren't any 'device not found' messages in the calibrate.log.  I also notice that the input when catting /dev/ttyS1 is qualitatively different.  

I think I'll try the 8.10 version tomorrow.

---

### Post by donnied on 2008-11-29
> **ihitf13anddied said:**
> ```

/usr/lib/xorg/modules/input$ ls
evdev_drv.so  mouse_drv.so      tscom_drv.la  tscomxp_drv.la  vmmouse_drv.so
kbd_drv.so    synaptics_drv.so  tscom_drv.so  tscomxp_drv.so  wacom_drv.so

```


We see the drivers are there, but how do we know the right modules are being loaded?  Should I see anything tscom when I lsmod or in /proc/modules?

---

### Post by ihitf13anddied on 2008-11-29
Yes, I do believe you should see the modules loading. This is where I am at. There is something I am missing in my xorg config file that I cannot seem to figure out. So now I have the drivers installed, I'm getting output on ttyS1, but i cannot use it as a touchscreen yet. I am glad you were able to get the right glibc, i assume through package manager? If you have any ideas on the config please share them. I'm not sure what happened to rjgii, last time he posted he said he was on business for a few days, which if I am not mistaken was approx two weeks ago. He thought he had an answer for the config file, so we may need to wait for him to return.

---

### Post by donnied on 2008-11-30
Well, I just tried Fedora 9 because there was a walk through for it.  The same results: when I go to calibrate it goes to the calibrate screen and nothing happens.  Maybe you could send rjgii a message? (I haven't been on long enough to.)  

He said he had messed around with the elo drivers.  Maybe he found some configuration tips there that helped?

---

### Post by ihitf13anddied on 2008-12-29
any word on this yet? My touchscreen still stands untouchable...

---

