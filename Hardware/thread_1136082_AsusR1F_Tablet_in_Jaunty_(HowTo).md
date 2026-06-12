---
title: "AsusR1F Tablet in Jaunty (HowTo)"
date: 2009-04-24
forum: Hardware
---

### Post by kleinric on 2009-04-24
Hi this is my first howto, and I'm certainly no expert so please bare with me(I'm not even sure if this is posted in the right place?), or if there are better ways to do this feel free to shoot me down. This is what I did to get the Tablet Features working on my AsusR1F tablet pc. I understand that this procedure would be the same for the AsusR1E I don't know about any other models.

The beginning section of this howto is based on the discussions and answers from this forum particularly kshepherd1's response on 2008-04-26 22:29.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127). The latter parts from the callibration onwards art what I've figured out over a while, and is probably a lot less fool proof.

Before doing this make sure that you have all the necessary tools to build the source, to be honest I'm not sure 100% what they are, although I have added these:


[LIST]
[*]build-essential
[*] libncurses5 and libncurses5-dev
[*]tcl8.5 and tcl8.5-dev
[*]tk8.5 and tk8.5-dec
[*]xorg-dev
[/LIST]
 
There may be more, but this is all I added to my current (fairly new) setup.
You'll also want to install the wacom-tools:```
sudo apt-get install wacom-tools
```[SIZE=5]_**Setup Wacom Driver**_[/SIZE]
1. Download this version of the linux wacom drivers: linuxwacom-0.8.3-2.tar.bz2

[LIST]
[*] For some reason the current stable release (0.8.2-2) wouldn't compile on my system, although these are working well so far.
[/LIST]
 2. Change to the download directory and extract the files ```
cd download_directory/
tar -xf ./linuxwacom-0.8.3-2.tar.bz2
```3. Enter the source codes directory and configure the compile making sure to add the '--enable-wacom at the end' ```
cd ./linuxwacom-0.8.3-2/
./configure --enable-wacom
```The output should look like this, if it doesn't search synaptic to add the needed packages:
> ----------------------------------------
BUILD ENVIRONMENT:
architecture - i486-linux-gnu
linux kernel - yes 2.6.28
module versioning - no
kernel source - yes /lib/modules/2.6.28-11-generic/build
XFree86 source - no
Xorg SDK - yes /usr/include/xorg
XSERVER64 - no
dlloader - yes
XLib - yes /usr/lib
xf86config - no
TCL - yes /usr/include/tcl8.4
TK - yes /usr/include/tcl8.4
ncurses - yes

BUILD OPTIONS:
wacom.o - yes
wacdump - yes
xidump - yes
libwacomcfg - yes
libwacomxi - yes
xsetwacom - yes
hid.o - no
wacom_drv.so - yes /usr/lib/xorg/modules/input
wacom_drv.o - no
wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------4. At this point it should compile without any errors: ```
make
```5. Make sure that the current wacom module is removed:```
ric@richardtablet:~/Desktop/linuxwacom-0.8.3-2$ sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules
```6. Test the newly compiled module:```
ric@richardtablet:~/Desktop/linuxwacom-0.8.3-2$ cd src/2.6.28
ric@richardtablet:~/Desktop/linuxwacom-0.8.3-2/src/2.6.28$ sudo insmod ./wacom.ko
```     If you're not bombarded by error messages at this point, try using the pen to check that the driver is working. The cursor etc probably won't be aligned properly just yet, don't worry. As long as the pen is now being picked up.

7. You can check whats happening here:```
ric@richardtablet:~/Desktop/linuxwacom-0.8.3-2/src/2.6.28$ tail /var/log/messages
      Apr 25 00:08:23 richardtablet kernel: [ 3817.051494] usbcore: deregistering interface driver wacom
      Apr 25 00:11:12 richardtablet kernel: [ 3985.909808] input: Wacom ISDv4 90 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input10
      Apr 25 00:11:12 richardtablet kernel: [ 3985.914224] usbcore: registered new interface driver wacom
      Apr 25 00:11:12 richardtablet kernel: [ 3985.914231] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver
      Apr 25 00:11:12 richardtablet logger: device input10 is bound to the driver
      Apr 25 00:11:12 richardtablet logger: must rebind
      
```8. Install the driver, "sudo make install" did nothing for me so rather add the driver manually:```

ric@richardtablet:~/Desktop/linuxwacom-0.8.3-2$ cd /src/2.6.28
$ locate wacom.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/input/tablet/wacom.ko
$ sudo rmmod wacom.ko
$ sudo mv /lib/modules/2.6.28-11-generic/kernel/drivers/input/tablet/wacom.ko ../../../wacom.origional.ko
$ sudo cp ./wacom.ko /lib/modules/2.6.28-11-generic/kernel/drivers/input/tablet/wacom.ko
$ sudo depmod -e
$ sudo modprobe wacom

```9. Now you need to add these sections to your '/etc/X11/xorg.conf' file.
First backup:```
cd /etc/X11/
sudo cp ./xorg.conf ./xorg.conf.backup
```Open the file in your favourite text editor:```
sudo gedit ./xorg.conf
```Add these 3 sections:
> Section "InputDevice"
    Identifier    "TabletStylus1"
    Driver    "wacom"
#    Option    "ForceDevice" "ISDV4"
    Option    "Type" "stylus"
    Option    "SendCoreEvents" "true"
    Option    "Device" "/dev/input/wacom"
    Option    "TopX" "141"
    Option    "TopY" "94"
    Option    "BottomX" "28388"
    Option    "BottomY" "17807"
EndSection

Section "InputDevice"
    Identifier    "TabletStylus2"
    Driver    "wacom"
#    Option    "ForceDevice" "ISDV4"
    Option    "Type" "cursor"
    Option    "SendCoreEvents" "true"
    Option    "Device" "/dev/input/wacom"
    Option    "TopX" "141"
    Option    "TopY" "94"
    Option    "BottomX" "28388"
    Option    "BottomY" "17807"
EndSection


Section "InputDevice"
    Identifier    "TabletStylus3"
    Driver    "wacom"
#    Option    "ForceDevice" "ISDV4"
    Option    "Type" "eraser"
    Option    "SendCoreEvents" "true"
    Option    "Device" "/dev/input/wacom"
    Option    "TopX" "141"
    Option    "TopY" "94"
    Option    "BottomX" "28388"
    Option    "BottomY" "17807"
EndSectionAdd these 3 lines to SeverLayout:> Section "ServerLayout"
  ...
  InputDevice   "TabletStylus1" 
  InputDevice   "TabletStylus2" 
  InputDevice   "TabletStylus3"  
  ...
EndSectionIf it doesn't exist mine looks like this:> Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "TabletStylus1" 
  InputDevice   "TabletStylus2" 
  InputDevice   "TabletStylus3"  
EndSection10. Then reboot.

[SIZE=5]**_Calibrate Screen_**[/SIZE]
The numbers in the xorg.conf file are correct for my system, if you need to re-callibrate run:```
wacomcpl
```The only problem with this method is that it doesn't seem to save these settings after i reboot/logout as they are reloaded from xorg.conf. You can read the numbers out afterwards with:> ric@richardtablet:~$ xsetwacom get TabletStylus1 TopX
141
I had quite a few settings that I like changed so I wrote a script that runs at startup that calls xsetwacom to change all the settings. This seemed easiest to me. Here is my script, its quite simple feel free to change it. Just set it to run at startup to easily apply your settings.
> [ATTACH]110883[/ATTACH][SIZE=5]**_Fix Screen Rotation Problems_**[/SIZE]
There are problems with the rotation. If you turn the screen the picture is rotated, but the wacom driver isn't. I've written some scripts for those too. Just place all 3 files in a folder together. The 'screenRotation' file has 0 after 'norm' has run, and 1 after 'right' has run.
> [ATTACH]110886[/ATTACH]Here is one more batch of scripts that does some trickery with automatically deciding which way to rotate, depending on the value of 'screenRotation'.
'rotateScreen.sh' will:
> screenRotation=0   -> Currently Normal, will rotate right
screenRotation=1   -> Currently Right, will rotate Normal
screenRotation=2   -> Currently Normal, will not rotate
screenRotation=3   -> Currently Right, will not rotateRunning 'screenRotateIgnore.sh' will toggle between ignoring a rotate command and accepting a rotate command.
Running 'Forcerotatescreen.sh' will force the rotation no matter what is in screenRotation.
> [ATTACH]110892[/ATTACH]PS. these aren't brilliantly coded, the path of screenRotation is hard coded in some of the scripts, just change it to be where-ever you decide to put them all. Sorry about that.

If you want, you can change the acpi scripts so that rotateScreen is automatically called when you turn the lid over.
> sudo cp /etc/acpi/rotatescreen.sh ~/Desktop/rotatescreen.sh.origional
sudo gedit /etc/acpi/rotatescreen.sh
And then comment out every line (put a # in front) and copy my code from 'rotateScreen.sh' above it. Save it. In future when the lid is rotated it'll use that code instead. Its a bit of a dirty fix, but it works for me :)

Hope this all helps, please let me know how to do better with writing howto's in the future,
Thanks,
ric

---

