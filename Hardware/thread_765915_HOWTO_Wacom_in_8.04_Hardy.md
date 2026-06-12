---
title: "HOWTO: Wacom in 8.04 Hardy"
date: 2008-04-24
forum: Hardware
---

### Post by neko18 on 2008-04-24
**[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

These are the steps I took to make my Wacom Bamboo Fun work in Ubuntu 8.04 Hardy. These instructions should work for most Wacom tablets.

**0.** Make sure you have a couple hours available. This will take a while. Also, print off a copy of this post because you will need to restart your computer a couple of times. If something goes wrong, see the troubleshooting section at the end of this post.

**1.** Plug in your tablet and open a terminal (Applications > Accessories > Terminal). Enter the commands in the following steps line by line into the terminal, pressing enter after each command. If you are prompted for a password, type your password then press enter.

**2.** ```
lsusb | grep -i wacom
```
Mine is a "056a:0017". Most models beginning with "056a" should work.

**3.** ```
mkdir wacom
cd wacom
```

**4.** ```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev -y
```

**5.** ```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.0-3.tar.bz2
tar xjf linuxwacom-0.8.0-3.tar.bz2
cd linuxwacom-0.8.0-3
```

**6.** ```
sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
sudo ln -s /usr/include/pixman-1/pixman-version.h /usr/include/pixman-version.h
```

**7.** ```
./configure --enable-wacom
make
sudo make install
```

**8.** ```
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf
```

**9.** Place the following lines near the beginning of the file. If you have a touchpad, make sure you place these lines before the "Synaptics Touchpad" Section.
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```

**10.** Find the section that looks somewhat like this. It will be near the end of the file.
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

**11.** Add these lines within the section you found in step 10.
```
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
```

**12.** Save (Ctrl-S) and quit (Ctrl-Q).

**13.** ```
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
You may get an error on this step. If you do, please write down the error. If your tablet does not work when you finish this HOWTO, please post this error so I (or someone else) can work through it with you.

**14.** ```
sudo depmod -e
```

**15.** ```
cd linuxwacom-0.8.0-3/prebuilt
sudo ./uninstall
sudo ./install
```

**16.** ```
wget 'http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master' -O wacom.udev
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules wacom.udev.backup
sudo cp wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```

**17.** ```
sudo apt-get remove wacom-tools xserver-xorg-input-wacom -y
sudo apt-get install wacom-tools xserver-xorg-input-wacom -y
```

**18.** ```
sudo ./uninstall
cd ..
sudo make install
```

**19.** Reboot your computer.

**20.** At this point, my tablet began working. If yours still is not, please post in this thread if you need help. Be sure to include any errors you received from the terminal. Also, include the ouput of the following two commands *as an attachment* (text file):
```
cat /etc/X11/xorg.conf
ls -l /dev/input
```


**[SIZE="3"]Troubleshooting[/SIZE]**

**1.**
Problem: X.org does not start after restarting your computer the first time.
Solution:
1. Restart your computer. You can do this either by pressing your power button or by pressing Ctrl-Alt-Delete.
2. When you see "GRUB Loading... Please Wait" on your screen, press the Escape key.
3. Scroll down to the "Recovery mode" entry with the arrow keys and press Enter. It is usually the second one.
4. Once the messages stop scrolling on the screen, enter the following commands. Press enter after each line. Remember to replace "USERNAME" with your actual username. If you do not remember your username, see the troubleshooting #2 entry.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.wacom_modified
cp /home/USERNAME/wacom/xorg.conf /etc/X11/xorg.conf
reboot
```

**2.**
Problem: You do not remember your username.
Solution: Run the following command. It will output a list of users. You will probably be able to recognize your username from this list.
```
cat /etc/passwd | grep "/home" | cut -d: -f1
```

**3.**
Problem: It didn't work.
Solution: Read though the posts in this topic. If you do not find a solution that applies to you, post a new reply asking for help.

---

### Post by arelis on 2008-04-25
Thanks! That was fast :)

There is a little error in your guide. "make install" should be "sudo make install" because without permissions make install doesn't work.

Also, if you bold out "correctly" where it says "If your tablet works correctly, stop now" and put this in the sentence: "(That is, if your tablet does seem to work, but not like it normally would, for example if it functions like a touchpad)", that might help. I got my tablet to work using your guide, but on first reboot (before i did apt-get remove wacom-tools xserver-xorg-input-wacom, and installed those back), it functioned like a touchpad. **_When i followed those final instructions, however, my tablet functions normally_**. How do i customize my tablet now? And, for example, the pad? I ran wacomcpl but the list which normally has the components of the tablet, is empty. Also, how do i reset the settings of the tablet to the settings you get when first installing it?? I screwed up the settings once, when on Ubuntu Gutsy, and the 'defaults' button in wacomcpl didn't do much good.

---

### Post by Nesmontu on 2008-04-25
Thanks, worked liked a charm for me! Maybe this should go on the wiki? :)

---

### Post by jazzroy on 2008-04-25
it worked for me too. thanks!!

---

### Post by Eastisle on 2008-04-25
Wow thanks Neko. Works better than ever. It got my Bamboo working right after step 19. :)

---

### Post by ChromeKaldra on 2008-04-25
i don't know if by "working" you mean "is more than a mouse". If so then no, it's only acting like a mouse. [w/o box selection too...] 

But if by working you mean 'responsive' then yes! 

i thank you for this as well, as it has gotten my tablet responsive. :D

Now i just gotta get Gimp to recognize it...any links anyone? :)

---

### Post by SnakeArtworX on 2008-04-25
Hi.
I have a problem with my Bamboo One tablet. However, I'm using 7.10 and I wonder if my tablet will finally start to "cooperate" under 8.04?
I've did everything to make it work, but there's no /dev/input/wacom, no event in /dev/input/ is responding after cat eventx (where x is the number of event). So if there's anyone with Bamboo One, please share your experience with that model and Ubuntu 7.10 or 8.04.

---

### Post by Eastisle on 2008-04-25
Hi Snake, 

The Bamboo is automatically recognized in 8.04 but it has to be configured through the use of this guide. Otherwise, the stylus moves the cursor on the screen but very slowly and the tablet basically behaves like a touchpad.

In 7.10 the Bamboo didn't function at all through plug and play. It can be made to work though. There's a guide on this forum that worked for me 100%.

I'm using the Bamboo in 8.04 as I write this, works super smooth thanks to this guide.

Edit: 
Didn't notice you were referring to the Bamboo One. In that case, this might help:

[http://ubuntuforums.org/showpost.php?p=3728205&postcount=4](http://ubuntuforums.org/showpost.php?p=3728205&postcount=4)

---

### Post by adamsad1 on 2008-04-26
This works perfectly on my X61 tablet!

Thanks a lot!

---

### Post by neko18 on 2008-04-26
**@arelis**
Thank you for the suggestions. I modified the howto accordingly.

To get `wacomcpl` working correctly, open a terminal and enter the following commands. I updated the howto to include them.
```
cd wacom/linuxwacom-0.7.9-11/prebuilt
sudo ./uninstall
cd ..
sudo make install
wacomcpl
```

**@Nesmontu**
Thanks for the suggestion. I posted a link to this thread on the wiki.

**@jazzroy, @Eastile**
I'm glad you got your tablet working.

**@ChromeKaldra**
Please reboot your computer with the tablet plugged in, then run the following command. Reply to this thread with its output.
```
ls -l /dev/input
```

**@SnakeArtworX**
The link Eastile gave in his edit should work.

**@adamsad1**
I didn't realize this worked for serial tablets as well as USB tablets. Thanks for pointing that out.

---

### Post by mykes on 2008-04-26
Doesn't work for me on my HP Tx2110 laptop - tablet / touch screen

A few issues.

mykes@mykes-laptop:~$ lsusb | grep -i wacom
Bus 002 Device 006: ID 056a:0093 Wacom Co., Ltd

Both the linuxwacom-0.7.9-11.tar.bz and the 0.8 version do not compile in step 6 for me.  I had to hack the Makefile to add a -I for the compiler to find pixman.h

I never had a /dev/input/wacom device, and still don't after following this how-to.

From the Xorg.0.log file:
```

(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "pad"
(**) |-->Input Device "Synaptics Touchpad"
... (later on)
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) pad: always reports core events
(**) pad device is /dev/input/wacom
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) pad: reading USB link
(**) Option "BaudRate" "9600"
... and later on again
(II) evaluating device (pad)
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

```

The xf86OpenSerial errors repeat about 100 times :)

Thanks for your help!

---

### Post by neko18 on 2008-04-26
**@mykes**
Open a terminal and make sure you have a scrollback of at least 500 lines (Edit > Current Profile, Scrolling tab). Run the following commands. Copy the entire terminal session into a text file and attach it.
```
cd wacom/linuxwacom-0.7.9-11
./configure --enable-wacom
make clean > /dev/null
make | tail -n 300
```

---

### Post by welldone101 on 2008-04-26
Hey thanks for the big setup here.  I'm working my way through it and ran into my first problem.

First, a preamble, When I did step 4 I got the ouput "Reading package lists... done; Building dependence tree; Reading state info... done; E: Couldn't find package linux-headers-uname -r

Then when I got to step 6 and type "make" it says:
make: *** No targets specified and no makefile found.  Stop.
I tried the next line "sudo make install" and got:
make: *** No rule to make target `install'.  Stop.

Since my first time ever using linux was this morning I'm not sure exactly what this means >.<  Any advice?

---

### Post by rajivnavada on 2008-04-26
Hi. I went through all the commands in this post without any error messages. However, the touchscreen still does not work. I am using an HP Pavilion tx2000 laptop with Ubuntu 8.04. Does the nvidia driver have anything to do with this? Also, does compiz work with the touchscreen? Can you please help me resolve this? I have attached the outputs you requested as text files. Thanks a lot!

---

### Post by Brown Betty on 2008-04-27
I've followed the instructions here to the end without getting any errors, but my tablet is behaving just as it was before; it seems be unable to reach the edges of the screen, and the buttons on the stylus are not working like they ought.  Anyway, I've attached my output files, and would be grateful for any suggestions you have.

---

### Post by neko18 on 2008-04-27
**@welldone101**
It looks like you missed the backticks (the ` character) on the package name. It should be ```
linux-headers-`uname -r`
``` instead of ```
linux-headers-uname -r
```

**@Brown Betty**
Your driver appears to be installed and working correctly. I suggest you file a bug at the Linux Wacom bug tracker: [http://sourceforge.net/tracker/?atid=525124&group_id=69596&func=browse](http://sourceforge.net/tracker/?atid=525124&group_id=69596&func=browse)

**@rajivnavada**
What is the output of this command?
```
lsusb | grep -i wacom
```

---

### Post by pommattski on 2008-04-27
Great howto, neko18...

I feel I must point out that that procedure is not necessary for **all** Wacom tablets.

I have a Graphire3 and have it working in a new installation of Hardy (64 bit) based on information in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=747500") - thanks to twisted_steel.
In summary:
I installed wacom-tools.  I then backed-up /etc/X11/xorg.conf and edited it as follows, adding:
```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection
```... and adding the 3 InputDevice lines to the ServerLayout section:```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 		"Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"

EndSection
```
... Rebooted and was able to "configure extended input devices" in Preferences of the GIMP - no problems. Just confirmed ok in Inkscape also.
Pressure sensitivity working just fine.

---

### Post by Kiongku on 2008-04-27
Do I have to always reboot my pc to use the wacom tablet?
Seems if I unplug it and plug it again while the computer is on, the tablet reverts to its old behavior. Not as a tablet.

Just making sure if everyone has the same issue. Thanks.

---

### Post by rajivnavada on 2008-04-27
Hi neko18. Thanks for replying to my post earlier and also thanks for the entire "How-To". I have attached the output of lsusb | grep -i wacom in the attached txt file. Thanks for your help.

---

### Post by neko18 on 2008-04-27
**@pommattski**
From what I've read, 64 bit users seem to be having better luck with Wacom tablets. I may just be seeint a false correlation though. In any case, it won't hurt to follow all the instructions.

**@Kiongku**
There are three ways to get Ubuntu to detect your tablet if it is plugged back in:
**1.** Restart your computer. This should always work.

**2.** Log out and log back in. This almost always works.

**3.** 
Switch to a different virtual terminal, then back to the one running X.org. To do this, press Ctrl-Alt-F1, wait a couple seconds, then press Ctrl-Alt-F7, then wait a couple seconds.

Yours may not be F7 (though the majority seem to be), so try some other higher numbers if it isn't. The only other one I've personally seen is F9.

**@rajivnavada**
**1.** Follow steps 1, 2, 3, 4, and 5 of the original guide

**2.** ```
wget http://linuxwacom.pastebin.com/pastebin.php?dl=f3d5b9e73 -O ../zappacky_tabletpc.patch
patch -p1 < ../zappacky_tabletpc.patch
```

**3.** Follow step 6.

**4.** If you haven't done 8, 9, 10, and 11 before, do them. They only need to be done once.

**5.** ```
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.normal_build.`uname -r`
sudo cp linuxwacom-0.7.9-11/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

**6.** Follow steps 13, 14, 15, 16, 17, 18, 19, and 20.

I've read reports that the tablet calibration may be off with this patched driver. This can be fixed. If you have this problem, I can step you through calibrating it.

---

### Post by ChromeKaldra on 2008-04-27
[QUOTE=neko18;4797903]**@ChromeKaldra**
Please reboot your computer with the tablet plugged in, then run the following command. Reply to this thread with its output.
```
ls -l /dev/input
```

i get this: 

```
jason@JX:~/wacom/linuxwacom-0.7.9-11$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    140 2008-04-27 12:11 by-id
drwxr-xr-x 2 root root    180 2008-04-27 12:11 by-path
crw-rw---- 1 root root 13, 64 2008-04-27 12:07 event0
crw-rw---- 1 root root 13, 65 2008-04-27 12:07 event1
crw-rw---- 1 root root 13, 66 2008-04-27 12:07 event2
crw-rw---- 1 root root 13, 67 2008-04-27 12:07 event3
crw-rw---- 1 root root 13, 68 2008-04-27 12:07 event4
crw-rw---- 1 root root 13, 69 2008-04-27 12:07 event5
crw-rw---- 1 root root 13, 70 2008-04-27 12:07 event6
crw-rw---- 1 root root 13, 71 2008-04-27 12:11 event7
crw-rw---- 1 root root 13, 63 2008-04-27 12:06 mice
crw-rw---- 1 root root 13, 32 2008-04-27 12:06 mouse0
crw-rw---- 1 root root 13, 33 2008-04-27 12:06 mouse1
crw-rw---- 1 root root 13, 34 2008-04-27 12:11 mouse2
lrwxrwxrwx 1 root root      6 2008-04-27 12:11 tablet-bamboo -> event7
lrwxrwxrwx 1 root root      6 2008-04-27 12:11 wacom -> event7

```

---

### Post by Tecra on 2008-04-27
1.I have run the following command,bu can't get any output.
```
lsusb | grep -i wacom
```
```
luke@luke-laptop:~$ lsusb | grep -i wacom 
luke@luke-laptop:~$ lsusb | grep -i wacom
luke@luke-laptop:~$ 

```
2.when running wacomcpl,I get below error.
```
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libwacomcfg.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1691)

```

Thinkpad X61t multitouch,ubuntu 8.04,linuxwacom 0.80,
Any advice? thanks.

---

### Post by neko18 on 2008-04-27
**@Tecra**
The tablet is not connected via USB. If you haven't already, you can try just continuing through the tutorial (it's worth a try). If that doesn't work, try searching the forums for "wacom tabletpc" or "wacom serial".

**@ChromeKaldra**
It appears to be set up correctly. Did you configure it in GIMP yet? If you haven't, there's information available on that topic on the wiki: [https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e](https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e)

---

### Post by Bleatlessness on 2008-04-27
After following the guide with the extra patch ([http://ubuntuforums.org/showpost.php?p=4811746&postcount=20]("http://ubuntuforums.org/showpost.php?p=4811746&postcount=20")) my Bamboo Fun works perfectly, pressure sensitive and all.

Seriously, I love you. Thank you so much!

---

### Post by rajivnavada on 2008-04-27
Neko18, You are great!!!!!!

The patch you asked me to apply and the line you asked me to add to *.udev worked. I can get the pointer to respond to the stylus etc... It is not calibrated though. When I run wacomcpl, a dialog box pops-up but there is nothing I can do inside the dialog box.

I have attached a screenshot of the dialog box. Whenever you get the chance let me know what I can do to fix this. Thanks for all your help.

---

### Post by arelis on 2008-04-27
> **rajivnavada said:**
> Neko18, You are great!!!!!!

The patch you asked me to apply and the line you asked me to add to *.udev worked. I can get the pointer to respond to the stylus etc... It is not calibrated though. When I run wacomcpl, a dialog box pops-up but there is nothing I can do inside the dialog box.

I have attached a screenshot of the dialog box. Whenever you get the chance let me know what I can do to fix this. Thanks for all your help.
Look on the first page at the far bottom. It has information on how to get wacomcpl to work. Also, the guide has been updated.

---

### Post by StefanA on 2008-04-27
I've followed this 'howto' to the bone, and can't get my intuos3 to work at all.
I've pasted below all the input that I can think of that you might need. I hope anyone can shed some light over this. The rest of the hardware is a Mac Pro with a nVidia card.

regards
stefan 


```
sanders@sanders3d:~$ uname -a
Linux sanders3d 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```


```
sanders@sanders3d:~$ lsusb | grep -i wacom
Bus 001 Device 004: ID 056a:00b1 Wacom Co., Ltd 

```
```

sanders@sanders3d:~$ ls -l /dev/input
total 0
drwxr-xr-x  2 root root     140 2008-04-27 22:10 by-id
drwxr-xr-x  2 root root     180 2008-04-27 22:10 by-path
crw-rw----  1 root root 13,  64 2008-04-27 22:10 event0
crw-rw----  1 root root 13,  65 2008-04-27 22:10 event1
crw-rw----  1 root root 13,  66 2008-04-27 22:10 event2
crw-rw----  1 root root 13,  67 2008-04-27 22:10 event3
crw-rw----  1 root root 13,  68 2008-04-27 22:10 event4
crw-rw----  1 root root 13,  69 2008-04-27 22:10 event5
crw-rw----  1 root root 13,  70 2008-04-27 22:10 event6
crw-rw----  1 root root 13,  71 2008-04-27 22:10 event7
crw-rw----  1 root root 13,  72 2008-04-27 22:10 event8
crw-rw----  1 root root 13,  73 2008-04-27 22:10 event9
crw-rw----  1 root root 13,  63 2008-04-27 22:10 mice
crw-rw----  1 root root 13,  32 2008-04-27 22:10 mouse0
crw-rw----  1 root root 13,  33 2008-04-27 22:10 mouse1
crw-rw----  1 root root 13,  34 2008-04-27 22:10 mouse2
crw-rw----  1 root root 13,  35 2008-04-27 22:10 mouse3
lrwxrwxrwx  1 root root       6 2008-04-27 22:10 tablet-intuos3-6x8 -> event7
crw-rw----+ 1 root root 10, 223 2008-04-27 22:10 uinput
lrwxrwxrwx  1 root root       6 2008-04-27 22:10 wacom -> event7
```




```

sanders@sanders3d:~$ cat /etc/X11/xorg.conf
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by rajivnavada on 2008-04-27
Hi Arelis,

Thanks for the reply. When I go into wacom/linux*/prebuilt and type sudo ./uninstall, the uninstall works fine. Then I do cd .. (go out one directory, so now I am in linuxwacom*). Now when I type in sudo make install and then wacomcpl, I get an error message saying command not found. I don't get the idea here. We uninstall the wacom X driver related utility and then try to invoke a command that we just uninstalled?? Maybe I'm reading this wrong. I might be missing a few steps. Could you please help?

Thanks a lot.

---

### Post by mykes on 2008-04-27
> **neko18 said:**
> **@mykes**
Open a terminal and make sure you have a scrollback of at least 500 lines (Edit > Current Profile, Scrolling tab). Run the following commands. Copy the entire terminal session into a text file and attach it.
```
cd wacom/linuxwacom-0.7.9-11
./configure --enable-wacom
make clean > /dev/null
make | tail -n 300
```

See attached files.  

out3.txt is the output of the ./configure
out4.txt is the output of the make | tail...

When this is over, you going to help me figure out how to make the "rotate screen" button work, too?  The button is on the frame around the LCD.  When you rotate the screen and close the laptop up as a tablet (LCD facing out), the rotate button lets you change from landscape -> portrate -> landscape -> portrait in 90 degree increments.  VERY neat feature.

---

### Post by rajivnavada on 2008-04-27
Hi Neko18 & Arelis,

I figured out why I wasn't able to run wacomcpl when I followed the updated instructions on page 1. I didn't have the tcl-dev and tk-dev packages and so libwacomxi wasn't getting compiled. Anyway, I installed these packages and repeated all the steps in the HOW-TO again. Now atleast I can run wacomcpl after doing sudo ./unistall >> cd .. >> sudo make install as mentioned in step 19. 

But I still have the same problem. I don't see anything on the "wacom control panel" dialog. Is there anything else I can do to get this to work? Can we calibrate the touchscreen using wacdump???? Also, which file would wacomcpl write to? The Linux Wacom Project says that the calibration info will be stored in ~/.xinitrc. Is this true even for Ubuntu?

Thanks for your help.

---

### Post by neko18 on 2008-04-27
**@Bleatlessness**
I'm glad your tablet's working.

**@rajivnavada**
The `sudo ./uninstall` command is removing the currently installed version of `wacomcpl`. The `sudo make install` is installing it from the source version you compiled earlier.

Yes, the calibration info is stored in "~/.xinitrc". You can edit the file manually by placing commands in the form of `xsetwacom set DEVICE PARAM VALUE`.

Please send me the output of ```
xsetwacom list dev
xidump -l
```

**@mykes**
Those look fine. Try the instructions I gave to **rajivnavada** in [http://ubuntuforums.org/showpost.php?p=4811746&postcount=20](http://ubuntuforums.org/showpost.php?p=4811746&postcount=20)

---

### Post by rajivnavada on 2008-04-27
Thanks for your reply Neko18. Here is the output from the 2 commands you requested. It seems like I might have done something wrong but I can't figure out what.

When I follow step 19) of the How-To, and then issue the command wacomcpl, I get the blank dialog box like in the screenshot I attached in post #25. At this time if I try "sudo wacdump /dev/input/wacom" I get a nice terminal screen where everything seems to be working great. It seems like wacdump detects everything from the stylus in pen-mode or eraser mode and also I get the line at the top where wacdump shows the input streams etc... 

However, when I restart the computer and then issue the command (wacomcpl), I get the dialog box with "pad" listed. Clicking on pad is no use and I can't really do much except exit. Now when I try wacdump, the input stream line does not show and also the different modes of the stylus are not recognized. Almost seems like there is some driver that is conflicting with the wacom driver. Another note here: after running these 2 commands when I make an error in typing in the terminal (anything that normally results in a system beep), X shuts down and I need to re-login.

Sorry for all this rambling but maybe this extra info might help you debug this problem.

Thanks.

---

### Post by not_surt on 2008-04-28
Still no change for me come step 17 (relative positioning only when touching surface).
Come step 21 it's better, with absolute positioning above the surface, but no pressure sensitivity and an empty wacomcpl.

I've got a Bamboo MTE-450.

Result of "lsusb | grep -i wacom":
```
Bus 001 Device 008: ID 056a:0065 Wacom Co., Ltd
```

Other info attached.

---

### Post by mykes on 2008-04-28
> **neko18 said:**
> **@Bleatlessness**
I'm glad your tablet's working.

**@rajivnavada**
The `sudo ./uninstall` command is removing the currently installed version of `wacomcpl`. The `sudo make install` is installing it from the source version you compiled earlier.

Yes, the calibration info is stored in "~/.xinitrc". You can edit the file manually by placing commands in the form of `xsetwacom set DEVICE PARAM VALUE`.

Please send me the output of ```
xsetwacom list dev
xidump -l
```

**@mykes**
Those look fine. Try the instructions I gave to **rajivnavada** in [http://ubuntuforums.org/showpost.php?p=4811746&postcount=20](http://ubuntuforums.org/showpost.php?p=4811746&postcount=20)

Awesome.  The pen/tablet is now working, but:

> 
I've read reports that the tablet calibration may be off with this patched driver. This can be fixed. If you have this problem, I can step you through calibrating it.

(the calibration is way off - maybe 200 pixels to the right and too low)

xsetwacom list dev:
Synaptics Touch Pad

xidump -l
xidump: error while loading shared libraries: libtinfo.so.5: cannot open shared object file: no such file or directory.

wacomcpl gives me an empty dialog (no devices to choose)

---

### Post by mykes on 2008-04-28
not sure what to make of this, but xidump suddenly started working.  All I did was a find / -name command, and the library wasn't there.

xidump:
virtual core keyboard keyboard
virtual core pointer disabled
generic keyboard unknown
configured mouse unknown
synaptics touchpad unknown
pad unknown
eraser unknown
cursor unknown
stylus unknown

After reboot...  wacomcpl shows "select the device" with just "pad" in the list.

It doesn't let me do anything but check the "turn help on" checkbox and quit :)

---

### Post by MikLSP on 2008-04-28
Hi, thanks for the guide however it isn't working for me so far...

At stage 6 I get the following:
bash: cd: linuxwacom-0.7.9-11./configure: No such file or directory

I am totally new to Ubuntu and Linux so apploogies if I'm missing something simple

---

### Post by mykes on 2008-04-28
> **MikLSP said:**
> Hi, thanks for the guide however it isn't working for me so far...

At stage 6 I get the following:
bash: cd: linuxwacom-0.7.9-11./configure: No such file or directory

I am totally new to Ubuntu and Linux so apploogies if I'm missing something simple

It seems you have joined two commands together.

cd linuxwacom-0.7.9-11

and

./configure

should be typed on separate lines

---

### Post by rospo84 on 2008-04-28
> **rajivnavada said:**
> Thanks for your reply Neko18. Here is the output from the 2 commands you requested. It seems like I might have done something wrong but I can't figure out what.

When I follow step 19) of the How-To, and then issue the command wacomcpl, I get the blank dialog box like in the screenshot I attached in post #25. At this time if I try "sudo wacdump /dev/input/wacom" I get a nice terminal screen where everything seems to be working great. It seems like wacdump detects everything from the stylus in pen-mode or eraser mode and also I get the line at the top where wacdump shows the input streams etc... 

However, when I restart the computer and then issue the command (wacomcpl), I get the dialog box with "pad" listed. Clicking on pad is no use and I can't really do much except exit. Now when I try wacdump, the input stream line does not show and also the different modes of the stylus are not recognized. Almost seems like there is some driver that is conflicting with the wacom driver. Another note here: after running these 2 commands when I make an error in typing in the terminal (anything that normally results in a system beep), X shuts down and I need to re-login.

Sorry for all this rambling but maybe this extra info might help you debug this problem.

Thanks.
Also for me there are the same problems. Wacomcpl does,'t show the orptions and also the xidump-out is the same but the xsetwacom-out is empty. Any suggestions? PS The tablet works fine.

---

### Post by btnelson on 2008-04-28
So I've finally managed to setup my Asus R1F tablet using the guide below and zappacky's patch which recognises the USB Tablet PC interface used by Asus.  Unfortunately I can't get the offset right.  I've tried putting in the minimum and maximum X:Y values I get from wacdump without success and wacomcpl doesn't show any devices.

Thanks to everyone for their useful posts and guides. 

> **neko18 said:**
> **@pommattski**
From what I've read, 64 bit users seem to be having better luck with Wacom tablets. I may just be seeint a false correlation though. In any case, it won't hurt to follow all the instructions.

**@Kiongku**
There are three ways to get Ubuntu to detect your tablet if it is plugged back in:
**1.** Restart your computer. This should always work.

**2.** Log out and log back in. This almost always works.

**3.** 
Switch to a different virtual terminal, then back to the one running X.org. To do this, press Ctrl-Alt-F1, wait a couple seconds, then press Ctrl-Alt-F7, then wait a couple seconds.

Yours may not be F7 (though the majority seem to be), so try some other higher numbers if it isn't. The only other one I've personally seen is F9.

**@rajivnavada**
**1.** Follow steps 1, 2, 3, 4, and 5 of the original guide

**2.** ```
wget http://linuxwacom.pastebin.com/pastebin.php?dl=f3d5b9e73 -O ../zappacky_tabletpc.patch
patch -p1 < ../zappacky_tabletpc.patch
```

**3.** Follow step 6.

**4.** If you haven't done 8, 9, 10, and 11 before, do them. They only need to be done once.

**5.** ```
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.normal_build.`uname -r`
sudo cp linuxwacom-0.7.9-11/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

**6.** Follow steps 13, 14, 15, 16, 17, 18, 19, and 20.

I've read reports that the tablet calibration may be off with this patched driver. This can be fixed. If you have this problem, I can step you through calibrating it.

---

### Post by Icemanyurt on 2008-04-28
I am running a fresh install of 8.04 (64 bit) on a Dell Inspiron 1521.  I am using the hardware driver for the ATI graphics card.

I followed all of the steps for my Wacom Bamboo Fun and it tossed me into low graphics mode and the tablet only works if I drag the pen across it.  The mouse is unresponsive.

---

### Post by MikLSP on 2008-04-28
> **mykes said:**
> It seems you have joined two commands together.

cd linuxwacom-0.7.9-11

and

./configure

should be typed on separate lines

Yes, it was my bad. I didn't realise I had to press enter more than once during Step 5 so I still had a command left to enter when I added the next one.

I have now got the tablet working though had to follow the extra step in order to have hover sensing working.

Big thanks for this guide =D>

I've no idea why these things need to be so complicated, Ubuntu is supposed to be easy to use :confused: ](*,)

---

### Post by louishr on 2008-04-28
worked great no problems, and i'm brand new to linux, just installed ubuntu today :)

---

### Post by donGoGo on 2008-04-29
It works perfectly by step 16
Thank you very much

---

### Post by r32inc on 2008-04-29
> **rajivnavada said:**
> Thanks for your reply Neko18. Here is the output from the 2 commands you requested. It seems like I might have done something wrong but I can't figure out what.

When I follow step 19) of the How-To, and then issue the command wacomcpl, I get the blank dialog box like in the screenshot I attached in post #25. At this time if I try "sudo wacdump /dev/input/wacom" I get a nice terminal screen where everything seems to be working great. It seems like wacdump detects everything from the stylus in pen-mode or eraser mode and also I get the line at the top where wacdump shows the input streams etc... 

However, when I restart the computer and then issue the command (wacomcpl), I get the dialog box with "pad" listed. Clicking on pad is no use and I can't really do much except exit. Now when I try wacdump, the input stream line does not show and also the different modes of the stylus are not recognized. Almost seems like there is some driver that is conflicting with the wacom driver. Another note here: after running these 2 commands when I make an error in typing in the terminal (anything that normally results in a system beep), X shuts down and I need to re-login.

Sorry for all this rambling but maybe this extra info might help you debug this problem.

Thanks.


hi guys, just like to thank neko and the others for all there help and patience. anyways i've been following rajivnavada's post and i get the same problem on my HP tx2000 with the exact same outputs that he posted and same goes for problem wacomcpl. As for my tablet it works fine with the pen eraser and side button but the touchscreen with my fingers is really off.

sorry if this post is unspecific i'm very new to ubuntu.

---

### Post by provide on 2008-04-29
> **mykes said:**
> 

Both the linuxwacom-0.7.9-11.tar.bz and the 0.8 version do not compile in step 6 for me.  I had to hack the Makefile to add a -I for the compiler to find pixman.h


I'm having the same issue whereas "make" kicks out this error:

```

/usr/include/xorg/miscstruct.h:54:20: error: pixman.h: No such file or directory

```

What exactly did you do to the Makefile for it to work? Thanks in advance.

---

### Post by pmosher on 2008-04-29
I've had **almost** complete success getting my Intuos 3 working on Hardy with the OP's instructions in post #1.  Thanks a TON to neko for posting this and for all the subsequent guidance.

Two little quibbles remain: the command 'wacomcpl' shows no devices at all, just a basically blank dialog box except for the "exit" command; and the mouse itself is insensitive/inconsistent with respect to the normal left-button click -- sometimes I have to click two or three times before it is recognized.

If someone could suggest ways to address the above, I'd be very grateful!

Thanks -- pmosher

---

### Post by nitricacid on 2008-04-29
Anyone try this [http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main) ?

---

### Post by neko18 on 2008-04-29
**@rajivnavada**
Follow my instructions for **mykes** later in this post.

**@not_surt**
Try running through the guide again. If that doesn't work, you can try installing the new 0.8.0 driver (if you don't know how, ask and I'll post instructions when I get a chance).

**@mykes**
**1.** Open a terminal

**2.** ```
xidump stylus
```

**3.** Move the pen to the upper left corner of the screen and record the "x-axis" and "y-axis" values from the "data" row.

**4.** Repeat step 3 with the upper right, lower left, and lower right corner.

**5.** Record the "min"/"x-axis", "max"/"x-axis", "min"/"x-axis", and "max"/"x-axis" values.

**6.** Reply with those values in your post. Make sure you label which value is which.

**@rospo84**
Try running through the guide again.

**@btnelson**
Follow my instructions for **mykes** from this post.

**@Icemanyurt**
You missed a line while copying the text into xorg.conf. Here's how to fix it:
**1.** Open a terminal

**2.** ```
gksudo gedit /etc/X11/xorg.conf
```

**3.** Find the text that looks like this:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
```


**4.** Replace it with this
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```

**5.** Save (Ctrl-S) and quit (Ctrl-Q)

**6.** Log out then log back in *or* reboot your computer

**@MikLSP**
I agree, I think Canonical should make Wacom tablets work by default.

**@louishr and @donGoGo**
I'm glad it worked for you

**@r32inc**
Follow my instructions for **mykes** earlier in this post.

**@provide**
I'm not sure what the problem is with the Makefile. **mykes** should be able to help you though.

**@pmosher**
First issue: Don't use `wacomcpl`. It doesn't really have anything useful anyway.

Second issue: It's the same for me. I think it's the hardware though, since I experience the same behavior in multiple operating systems. I use the pen as my primary pointing device and only switch to the mouse if my friends are using my computer (since they're not used to a tablet).

**@nitricacid**
That's what this guide explains how to install ;)

---

### Post by not_surt on 2008-04-30
I had already run though a second time with linuxwacom-0.7.9-11 in case I missed anything.

After going through the process with linuxwacom-0.8.0 the only change is that wacomcpl now lists the devices, though it shows an error message when selecting a device after the first selection.

Still no pressure sensitivity.

Thanks for all your help anyway.

---

### Post by pmosher on 2008-04-30
Thanks for the speedy reply, neko18.  I won't bother with wacomcpl.  Everything's working fine anyway with the exception of the click issue I mentioned earlier.  Pressure sensitivity is fine, even within WinXP and Photoshop under vmware.

pmosher

P.S.  For those who are struggling with a tablet within VirtualBox without success -- i.e. no pressure sensitivity -- try vmware server instead. I know it's a more heavyweight solution than you may otherwise require, but at least the tablet works completely within the wirtual machine.

---

### Post by provide on 2008-04-30
This is more of a follow-up to my previous post. I tried compiling linuxwacom 8.0 and got the same result when I went to "make":

```

/usr/include/xorg/miscstruct.h:54:20: error: pixman.h: No such file or directory
make[2]: *** [xf86Wacom.o] Error 1
make[2]: Leaving directory `/home/user/wacom/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/wacom/src'
make: *** [all-recursive] Error 1

```

I'm using Kubuntu 8.04. Thanks in advance for any advice.

EDIT:

Should I take this issue to linuxwacom instead of posting it here?

---

### Post by arelis on 2008-04-30
> **neko18 said:**
> **[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**
**17.** If your tablet works correctly, stop now. The mouse cursor should move when you hover over the tablet, and you should not have to touch the tablet with the stylus to move the mouse cursor. If it is no functioning correctly, open a terminal and continue to the next step.

**18.** ```
sudo apt-get remove wacom-tools xserver-xorg-input-wacom -y
sudo apt-get install wacom-tools xserver-xorg-input-wacom -y
```

**19.** ```
cd wacom/linuxwacom-0.7.9-11/prebuilt
sudo ./uninstall
cd ..
sudo make install
```

**20.** Reboot your computer.

What is the equivalent of this on Arch Linux? I managed to get it to work on Arch, but it acts like a touchpad, like it does on Ubuntu before i do these steps

---

### Post by ChromeKaldra on 2008-04-30
> **neko18 said:**
> **@ChromeKaldra**
It appears to be set up correctly. Did you configure it in GIMP yet? If you haven't, there's information available on that topic on the wiki: [https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e](https://help.ubuntu.com/community/Wacom#head-929f7242507f9630c22bacd764264465a7a3f59e)

It works now,[the tablet] i think i forgot to restart or something. But GIMP still doesn't recognize it. Gimp also run INCREDIBLY slowly for some reason...

Is it possible to have Photoshop recognize it through my VM? That'd be a dream. Atm it functions like a mouse which i can live with in the meantime.

thank you very much for getting it to work!

---

### Post by ruetheday on 2008-04-30
arrrggggg!!!  i'll never get this thing to work,

---

### Post by r32inc on 2008-04-30
> **neko18 said:**
> **@rajivnavada**
Follow my instructions for **mykes** later in this post.

**@mykes**
**1.** Open a terminal

**2.** ```
xidump stylus
```

**3.** Move the pen to the upper left corner of the screen and record the "x-axis" and "y-axis" values from the "data" row.

**4.** Repeat step 3 with the upper right, lower left, and lower right corner.

**5.** Record the "min"/"x-axis", "max"/"x-axis", "min"/"x-axis", and "max"/"x-axis" values.

**6.** Reply with those values in your post. Make sure you label which value is which.

**@r32inc**
Follow my instructions for **mykes** earlier in this post.


@neko18

Thanks again for the reply neko18

Once I run,
```
xidump stylus
```
I get the following:

InputDevice: stylus
Valuators: Absolute   ID: Undefined  Serial Number: Undefined

             x-axis    y-axis   pressure   x-tilt    y-tilt     wheel
     data:
      min:  +00000    +00000    +00000    -00064    -00064    +00000
      max:  +01280    +00800    +00255    +00063    +00063    +01023
      res:  +00050    +00050    +00001    +00001    +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:

But once I touch (upper / lower right and left corners) the LCD no data inputs show up on the data row like you mentioned. But in anycase my Pen "Stylus" is working correctly its when I touch the screen with my fingers when its really off.

---

### Post by Jest_of_EVE on 2008-04-30
This is a fine guide, thanks Neko.

I had everything working a few days ago then started to try and get wacomcpl to work....I killed everything and couldn't get it back.

This was my last resort this morning and it worked a charm using 0.8.0 release.


BTW, is there a way to get the Intuos3 mouse side buttons to do something other than emulate the scroll wheel?
Pointers from anyone would be much appreciated.

Thanks again Neko! :)

---

### Post by Nikobelia on 2008-04-30
Hey, thanks for the howto! I'd have no hope of getting anything to work via the terminal without the help of these lovely forums :D

I've run into an error on step 4, and it doesn't seem to have come up so far in the thread:

```
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r

``` 

My tablet's a Wacom Bamboo Fun, and I did use it with Gutsy Gibbon (with the help of a tutorial). My computer's partitioned, and the tablet works fine in Windows XP.

---

### Post by _Narcisse_ on 2008-04-30
Wow, You know what you're talking about. Absolutely no errors for me. You saved me from artistic despair, haha, my Intuos3 6x8 Tablet works like a charm. The only thing that bother me a little is that the ink tool in Gimp seems to go less smoothly than in Gutsy, but I didn't install it this way anyway. I'll try to mess around with it. Thanks a lot neko.

---

### Post by neko18 on 2008-04-30
**@not_surt**
I may have asked you this before, but did you configure the pressure-sensitive application to use the tablet? To configure it in Gimp or Inkscape, follow these directions: [https://help.ubuntu.com/community/Wacom#head-e6be1b063169fbd7ef35aa6c1e9e57a538f466f8](https://help.ubuntu.com/community/Wacom#head-e6be1b063169fbd7ef35aa6c1e9e57a538f466f8)

**@provide**
Yes, you may want to take that to Linux Wacom. I don't really understand what is causing the pixman.h error.

**@arelis**
APT is Ubuntu/Debian specific. Try simply skipping step 18.

**@ChromeKaldra**
Someone suggested earlier in the thread to use VMWare Server. Wine also supports tablet pressure.

**@r32inc**
I see. You may want to take that to the Linux Wacom Project since they'll know far more about tablet PCs than I do. I use an external USB tablet (which doesn't even have the option of sensing fingers).

**@Jest_of_EVE**
To configure the buttons, use the `xsetwacom` command. The general syntax for setting button commands is:
```
xsetwacom set DEVICE PARAM VALUE
```

**1.** DEVICE can be "stylus", "erasor", or "pad".

**2.** PARAM can be "Button1", "Button2", ... "Button32", "RelWUp", "RelWDn", etc. You can get a full list with this command:
```
xsetwacom list param
```

**3.** VALUE can be any X11 event. Some examples are "core key alt f2", "button 1", "dblclick 2", "button 2", etc. For examples, look through the output of:
```
xsetwacom list param
```

**@Nikobelia**
You made a mistake while copying or typing the command into the terminal. Make sure you enter the commands *exactly* as shown. I suggest copying and pasting (to paste into the terminal you'll have to go to Edit > Paste or use Ctrl-Shift-V).

Good luck with the guide.

**@_Narcisse_**
I also noticed the problem with the ink tool. I'm not sure what is wrong with it, but I'll post in this thread if I ever get it working smoothly.

---

### Post by not_surt on 2008-04-30
Argh! Stupid me. That did the trick.

xidump wasn't reporting any change in pressure so I presumed it wasn't working.

Thanks heaps!

---

### Post by anemptygun on 2008-04-30
Props to neko! worked perfect. Linked to this thread on my blog.

---

### Post by Nikobelia on 2008-05-01
Thankyou neko! It worked after I did the extra step (and I've now learnt to use copy-paste better, :)).

---

### Post by s.toonen on 2008-05-01
Great! I just followed the steps and my Wacom Bamboo works perfectly!
When is start the wacomcpl tool it is empty too, but i don't know why i should need it since i configured all the actions with xsetwacom.
There is only one thing i can't get going. In windows i can configure my Wacom such that it goes into scroll mode when clicking a button. Just like clicking on a mouse wheel. How should i do this in Ubuntu?

---

### Post by zvadinov on 2008-05-01
Awsome neko,it worked perfect!
thank you!

---

### Post by _Narcisse_ on 2008-05-01
Well, I spoke too fast. Today, at the moment my stylus touched the tablet, X badly crashed, everything froze, keyboard included, so no terminal. After a forced reboot, it works almost normally again... 
Crashes like this one used to be rare, any suggestions ?

(Still reading the Net for a way to smooth the ink tool in Gimp like it was under Gutsy...)

EDIT : The not-smooth lines problem with the ink tool in Gimp seems to be a (known...) old bug with the "zoom factor", even if I did not experienced this problem with Gimp under Gutsy...

[http://bugzilla.gnome.org/show_bug.cgi?id=55366](http://bugzilla.gnome.org/show_bug.cgi?id=55366)

As described here, if you draw a line zooming in at 200% or more and then zoom back to normal level, the line is perfectly smooth, as like it was when I used to draw in Gutsy. 

And the problem is the same with the mouse, so obviously it's not the tablet's fault.

Thanks again for the howto.

---

### Post by ilpiero on 2008-05-02
Thanks a lot for this guide , my bamboo fun works perfectly except for the wacomcpl.
(btw, is there a graphical interface in kubuntu for making programs/scripts start with the system?)

i post to answer a questio  that was done by **provide** in the thread.

if the compiler doesn't find pixman.h is because it was moved from 
/usr/include/ to /usr/include/pixman-1/ (or something like that, i'm at work now i can't check).

to solve the problem i made a linked both the files in the /pixman-1/ folder to the /usr/include/

i'm not an expert user so tell me if there is a better solution.

I hope in the next ubuntu there will be native support for our tablets.

Thanks again ;)

---

### Post by chriscast on 2008-05-02
I get this in my 'Xorg.0.log' file. I'm not really sure what to do at this point, total n00b here. Any help is greatly appreciated :-)

```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(EE) module ABI major version (0) doesn't match the server's version (2)
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input//wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)
```

---

### Post by mooosebag on 2008-05-02
Hi,

foa : Thanks for the howto, it's really bulky :)

So, if I go step-by-step through it, it won't really work at all, there are two things I found, so, now it works fine - at last with linuxwacom 0.8.0

First : 
> 
Yes, you may want to take that to Linux Wacom. I don't really understand what is causing the pixman.h error.


I had this error too and found a solution in :

(This is for hardy heron / 8.04)

```

cd /usr/include
sudo ln -s /usr/include/pixman-1/pixman.h
sudo ln -s /usr/include/pixman-1/pixman-version.h

```

After this symbolic link the 'make / make install' works fine and wacom.ko is built, so you could do the following steps.

After all I had to do one step more to get wacom full functionally :

```

cd [path to linuxwacom...version...]/src/2.6.24 (or other kernel-version)
sudo rmmod wacom
sudo insmod ./wacom.ko

```

After this I'm able to use my wacom bamboo full featured :)

SoLong

---

### Post by provide on 2008-05-02
Thanks to **ilpiero** and **mooosebag** for their replies; I wave linuxwacom compiled now. I am truly grateful!

I ended up typing the first command wrong, though (sudo ln -s /usr/include/pixman-**l**/pixman.h), thus making a bad link. To correct his error, I did this:

```
sudo unlink pixman.h
```

Then I repeated the correct command. Thanks again!

---

### Post by lauter on 2008-05-02
Hi
I got a error message by running "make"

/usr/include/xorg/miscstruct.h:54:20: error: pixman.h: No such file or directory
make[2]: *** [xf86Wacom.o] Error 1
make[2]: Leaving directory `/home/imre/linuxwacom-0.8.0/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/imre/linuxwacom-0.8.0/src'
make: *** [all-recursive] Error 1

Any suggestion?
Thanks.

---

### Post by provide on 2008-05-02
**lauter,**

See mooosebag's post #68.

---

### Post by eel on 2008-05-02
thanks, ever since the beta release i have been waiting for this tutorial!
Worked perfectly. One small problem is that the control panel is sort of eeehm... minimalistic to say the least. There's a little box i can check to turn on help features (which does nothing if i check it) and a scroll menu where there is only one item visible which i can select, 'pad' Oh and i can click ok in the bottom right corner which is also nice to do. But controlwise it doesn't add that much to my wacom experience (:
Thanks again for the very clear tutorial!

---

### Post by vboblinux on 2008-05-02
Thank you very much...!!! :-) 
It worked for me (Wacom Graphire). :-)

---

### Post by lauter on 2008-05-02
> **provide said:**
> **lauter,**

See mooosebag's post #68.

 Thanks, it's solved, but I got the next error:

imre@Kubuntu:~/wacom/linuxwacom-0.8.0/src/2.6.24$ sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules

---

### Post by neko18 on 2008-05-02
**@not_surt, @Nikobelia, @zvadinov, @vboblinux**
I'm glad it's working.

**@anemptygun**
Thanks for the link! Hopefully it will lead more stranded Wacom users to this thread :)

**@s.toonen**
I'm not sure how to do that. Most applications support scrolling or panning by clicking and holding the middle mouse button, though. On my stylus and configuration, the middle mouse button translates to the side button closest to the top of the pen.

**@_Narcisse_**
That's strange. Does it crash every time you touch the stylus to the tablet, most of the times, or just occasionally?

Thanks for the info on the ink tool.

**@ilpiero**
Thank you for that fix. I integrated it into the howto.

I'm not sure how to modify the startup session in Kubuntu.

I suggest not worrying about `wacomcpl` because it's generally not a very useful program anyway.

**@chriscast**
Try following through the instructions again from the beginning. If it still doesn't work, send me the output of step 6 as an attachment.

**@mooosebag**
Thank you for that fix. I integrated it into the howto.

I'm just trying to account for the most possible people by making it bulky.

**@lauter**
If your tablet works fine now (after a reboot), don't worry about the rest of the steps from **moosebag**'s post.

If your tablet does not work, repeat the howto from the beginning. With the help of **moosebag** and **ilpiero**, I added step 5.5 to fix that error.

**@eel**
It's unlikely you will find a use for `wacomcpl`, so don't worry about trying to make it work (unless you need it for a specific purpose).

---

### Post by msar24 on 2008-05-02
I have a graphire 4 and when I get to step 6 and run:

./configure --enable-wacom

I get the following response:

msar24@engraving:~/linuxwacom-0.7.9-11$ ./configure --enable-wacom
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
msar24@engraving:~/linuxwacom-0.7.9-11$ 

I'm a newbie so I'm lost at this point!

Thanks

---

### Post by MastaBullz on 2008-05-03
Thank you very much for this excellent tutorial, even me after I managed French no problem installed my Bamboo!

I was forced to go to the stage 20 and everything works to perfection apart from the "wacomcpl" which runs but does nothing visible (see screen attached)

[[img]http://apu.mabul.org/up-mini/apu/2008/05/03/img-060912vrq18.png[/img]](http://apu.mabul.org/up/apu/2008/05/03/img-060912vrq18.png.html)

One last little question, do I install Expresskeys (available here [http://freshmeat.net/projects/wacomexpresskeys/](http://freshmeat.net/projects/wacomexpresskeys/)) to make my staff configuration buttons pad and stylus or is that "xsetwacom" enough?

---

### Post by neko18 on 2008-05-03
**@msar24**
That is strange. Please send me the output of the following command:
```
gcc
```

**@MastaBullz**
I'm glad your tablet is working now.

`xsetwacom` should work for any configuration, since it is the official Linux Wacom configuration tool.

---

### Post by MastaBullz on 2008-05-03
yes but the problem is that I do not know how to create a roster of autostart to find my personal configuration each restart my Hardy heron, could you help me please? 
 
 I know it is done with a file. Bash but I've never set up, how do I return parameters please? 
 
 I returned this 
 ```

 xsetwacom set stylus button2 3 
 xsetwacom set stylus button3 2 
 xsetwacom set pad button1 "core key ctrl" 
 xsetwacom set pad button2 "core alt key f2" 
 xsetwacom set pad button3 "core key shift" 
 xsetwacom set pad button4 "core alt key shift f3" 

```
 
 and then I save the file with the extension .bash and I place it in the folder .Autostart ?

---

### Post by msar24 on 2008-05-03
neko18,

when I enter gcc i get:

gcc: no input files

---

### Post by valmont27 on 2008-05-03
great guide, mate!

---

### Post by neko18 on 2008-05-03
**@MastaBullz**
You can place the commands in the file "~/.xinitrc"

**@msar24**
I'm not sure why that is happening. Please attach the file "~/linuxwacom-0.7.9-11/config.log".

**@valmont27**
Thanks

---

### Post by msar24 on 2008-05-03
neko18,

Attached is my config.log file.  I changed the name to config.txt so it would upload.



Thanks

msar24

---

### Post by MastaBullz on 2008-05-03
sorry I can not find xinitrc file, do I have? and if so should I put the root or in my personal folders? 

EDIT: my problem is fixed, Im new on linux and im learn little by little!
  
 big thankz for your help NEKO and for the quality of this tutorial ;)

PS: 
What is this tutorial can also be used to install a wacom tablet under Ubuntu 6.06 (Dapper Drake), Ubuntu 6.10 (Edgy Eft), Ubuntu 7.04 (Feisty Fawn) and Ubuntu 7.10 (The Gutsy Gibbon)?

---

### Post by neko18 on 2008-05-04
**@msar24**
I think it has something to do with your processor architecture, i686. I'm not sure how to fix it though. Sorry.

**@MastaBullz**
For 7.10 (Gutsy), you can follow this guide: [http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

---

### Post by marian99us on 2008-05-04
hello hello,
day before yesterday i installed ubuntu on my toshiba R25 tablet pc.
i have never used a linux machine before and am completely ignorant! 
could someone please help me resolve some of my problems with my pc?

first and foremost, my stylus wouldn't trigger nothin' no matter how hard i hit the screen with it :( the cursor just won't budge! 

second: my trackpad really really sucks! 
i am used to highly sensitive trackpads, and now my trackpad hardly responses! 
i mean it works fine and all, but even at its maximum trackspeed and maximum sensitivity it just doesn't meet my need! 
plus, tapping is also slow, there is a certain delay between the physical tap and the software event! 
please please help me!

---

### Post by _Narcisse_ on 2008-05-04
**@neko18**
It just did it once, the day after the install, after boot. Strange as you say but not so important, it's working well now, never did it again. I've tried to look for a clue in the logs but found nothing. Now, I'm only in trouble with the ink lines in Gimp, but seems to be Gimp's fault. :-s

---

### Post by msar24 on 2008-05-04
neko18,

Thanks for looking at it.  I'll keep trying and if I figure it out I'll post.

---

### Post by WasMeHere on 2008-05-04
I'm a newcomer in the Ubuntu world, and it works much better than I expected. I did not expect to get our Bamboo Fun to work, but after the instructions above, it actually works better with the GIMP than in Windows XP  :KS
thank you/olle

---

### Post by sbranam on 2008-05-04
:KS BIG thanks! I just loaded Ubuntu 8.04 under Windows on my wife's laptop and set up our new Bamboo Fun verbatim per your instructions, mostly just cut-n-pasting into the terminal (except that I used the 0.8.0 drivers). Note that the default Hardy install doesn't include tcl-dev or tk-dev, so you have to get them first via Synaptic, which will trip up neophytes.

We just got the Bamboo Fun for my daughter, and there was so much junk running in background under Windows that GIMP would simply lose touch with the stylus as she was drawing, then jump to the current position (this system is infested despite my attempts at cleaning it, hence the drive to move to Linux). However, seeing that GIMP preferences need to be configured for it, that may have been the problem. Anyway, works great under Ubuntu. I love the pressure-sensitivity, that is cool!

---

### Post by chris-chan on 2008-05-04
hi :)
after getting my tablet to work under kubuntu feisty with the old guide i tried this one out after reinstalling with hardy yesterday.
i followed the steps  1-16 closely (except that i used version 0.8.0 of linuxwacom) and there were no errors at all.
Problem is, all my pen does is act like a mouse. I tried editing the device info in gimp but the eraser, pen etc. devices are missing, only thing  gimp shows there is a configured mouse. Also, when i start wacomcpl there is nothing in there at all.
i even installed krita, the pen works, but without pressure. 
in krita>preferences, if i go to the tablet tab it says no device found :/

hobe you can help me with that problem
dont want to use win

ps: this is my second try after i had to reinstall hardy the other day.Sadly it had the same outcome

---

### Post by neko18 on 2008-05-04
**@marian99us**
Did you try following the guide I made? It's the first post in this thread and it should make your tablet work.

I'm not sure about the trackpad. I suggest opening a new thread and asking for help there.

**@Olle Wiklund, @sbranam**
I'm glad you got your tablet working.

**@chris-chan**
Do steps 17-21.

---

### Post by alisiacam on 2008-05-04
Wow, I have no idea who you are, but I love you. THANKS!!!!!!!
thinkpad x61 up and running!

---

### Post by flaviusxvii on 2008-05-04
Thanks for the guide...
Just one problem. I have a Wacom Bamboo and a dual monitor setup. The stylus only works in the "outer halves" of the two screens (and that's with a two or three hundred horizontal pixel offset). And when I move the stylus across the screen it jumps from outer half to outer half.

Any ideas on how to fix this?

---

### Post by neko18 on 2008-05-04
**@alisiacam**
That was an overreaction :)
I'm glad your tablet is working.

**@flaviusxvii**
I just updated the guide to use Linux Wacom 0.8.0. Follow these instructions:

**0.** Follow steps 0, 1, and 2 of the new guide.

**1.** ```
mv wacom wacom.0.7.9-11
```

**2.** Follow steps 3, 4, 5, 6, and 7.

**3.** ```
cd ..
```

**4.** Follow steps 13, 14, 15, 16, 17, 18, and 19.

---

### Post by msar24 on 2008-05-04
neko18,

I figured out why I could not get past step 6.  For some reason I did not have a C compiler installed.  Once I did that crusied right on through to the step where you reboot.  After reboot X broke and I got low res video.  If I comment out all of lines that I added in xorg.conf and restart X then the video goes right back to where it should be.  Now I have to figure out the video issue.  I'm running a Dell Optiplex 745, Pentium D, 3 GHz with the Intel Q963/Q965 video.

If you have any ideas let me know.  If I figure it out I'll post.

msar24

---

### Post by flaviusxvii on 2008-05-04
@neko

That all went smoothly, but the horizontal offset and the 'outer halves' problem still remains.

Does anyone else have this working on a dual monitor Xinerama setup?

---

### Post by chris-chan on 2008-05-05
ok,  its working now, big thanks, and sorry^^

---

### Post by tmray on 2008-05-05
My graphire2 tablet worked without doing anything after I installed 8.04. 

The problem I had was that pressure didn't work and it would not match the screen. When I used the stylus, the cursor would move from where it was on the screen, not where I put the stylus on the pad. So i would move the cursor to the corner on the screen with the stylus but on the pad I could be anywhere.

And in gimp and other programs the input device properties didn't even have tablet choices in the configuration the only choice was "configured mouse". The tablet works with these programs but no pressure settings.

So to try and fix this, I followed the instructions as writen in the first post. I also noticed that when I opened my xorg.conf file it didn't even have any of the wacom input devices info on it to begin with so I added it. Still the results were the same after following all the instructions on the first post.

I tried switching the /dev/input settings to event6 as well because that's where it said the wacom was located and the results were still the same.

Any ideas how I can get screen detection and pressure to work on my system?

Thanks.

---

### Post by neko18 on 2008-05-05
**@msar24**
Please attach the output of:
```
cat /etc/X11/xorg.conf
```

**@flaviusxvii**
You may want to ask the Linux Wacom Project ( [http://linuxwacom.sf.net](http://linuxwacom.sf.net) ) directly. I doubt this is an Ubuntu-specific issue.

**@chris-chan**
I'm glad your tablet works now

**@tmray**
Do you have to press down on the tablet to move your mouse cursor or can you simply hover over the tablet to move the cursor?

Also, please send the output of these two commands:
```
ls -l /dev/input
xidump -l
```

---

### Post by tss101 on 2008-05-05
Many thanks for the guide and help neko18

I managed to get the tablet screen working as a mouse (and it's calibrated nicely too!) on my hp tx2110. I used the instructions you gave to rajivnanda on page 2 (the numbers are a little out of sync after the updated 0.8.0 instructions). Although wacomcpl doesn't seem to work - it gives me an unknown device error for all four wacom components in the list

There's also a nasty side effect. Every time I now press tab in a bash terminal window (with a system beep) X restarts. It only happens after using the patched instructions. I was wondering if anyone else has seen this or has any ideas why it might be.

---

### Post by tss101 on 2008-05-05
Seems the tab issue is fixed by using the xorg.conf file entries in [here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=708726&page=3") (post #27). 

wacomcpl kind of works now too, though this may be unrelated to the changes to xorg.conf

---

### Post by rospo84 on 2008-05-05
How can disinstall the wacom driver for retring to install wacom driver

---

### Post by rospo84 on 2008-05-05
> @rospo84
Try running through the guide again.

i tried to run through the guide but now it give me error at the step 7.
> 7.
Code:

./configure --enable-wacom
make
sudo make install

 It didn't make the "sudo make install". I tried to go ahed but at the step 12 when i write ```
sudo cp linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
it returned:
> cp: impossibile fare stat di `linuxwacom-0.8.0/src/2.6.24/wacom.ko': Nessun file o directory
that means that there are no file or directory and that it was impossible make the stat of `linuxwacom-0.8.0/src/2.6.24/wacom.ko'.
So, can anybody help me.
Sorry for my worst english!!!

---

### Post by Papadzulinux on 2008-05-05
I tried all steps and it worked just fine...After I tweaked the xorg.conf.. this because my tablet is an old ArtPad II Serial tablet and not a USB model...After playing with  wacdump and xsetwacom I managed to get my old tablet working and with ```
 xsetwacom set stylus button2 3
``` I mapped the middle button to mouse-right.

Thank you so much

---

### Post by Papadzulinux on 2008-05-05
> **rospo84 said:**
> i tried to run through the guide but now it give me error at the step 7.
 It didn't make the "sudo make install". I tried to go ahed but at the step 12 when i write ```
sudo cp linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
it returned:
that means that there are no file or directory and that it was impossible make the stat of `linuxwacom-0.8.0/src/2.6.24/wacom.ko'.
So, can anybody help me.
Sorry for my worst english!!!

You can't find it possibly because you are on "/home/whomeveryoure/linuxwacom-0.8.0/",it happened to me, so try instead:
```
sudo cp src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
``` or

```
sudo cp /home/'usrname'/wacom/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by neko18 on 2008-05-05
**@tss101**
I'm glad your tablet is working. I'm guessing the 'Option "ForceDevice" "ISDV4"' line fixed it.

**@rospo84**
Please open a terminal and run the following commands. Attach their output.
```
cd ~/wacom/linuxwacom-0.8.0
./configure --enable-wacom
make | tail -n 300
sudo make install
```

**@Papadzulinux**
Noting the current directory is a good tip. I'll try to integrate it into the guide somehow.

---

### Post by rospo84 on 2008-05-05
> **Papadzulinux said:**
> You can't find it possibly because you are on "/home/whomeveryoure/linuxwacom-0.8.0/",it happened to me, so try instead:
```
sudo cp src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
``` or

```
sudo cp /home/'usrname'/wacom/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

doesn't work!!! :sad::sad::sad:

---

### Post by rospo84 on 2008-05-05
> **neko18 said:**
> **@tss101**
I'm glad your tablet is working. I'm guessing the 'Option "ForceDevice" "ISDV4"' line fixed it.

**@rospo84**
Please open a terminal and run the following commands. Attach their output.
```
cd ~/wacom/linuxwacom-0.8.0
./configure --enable-wacom
make | tail -n 300
sudo make install
```

**@Papadzulinux**
Noting the current directory is a good tip. I'll try to integrate it into the guide somehow.
make | tail -n 300 give me:

```
Making all in src
make[1]: Entering directory `/home/neararo/linuxwacom-0.8.0/src'
Making all in .
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src'
Making all in wacomxi
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src/wacomxi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src/util'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src/util'
Making all in xdrv
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src/xdrv'
gcc -MM -g -O2 -I/usr/include/tcl  -I../include -I/usr/include/xorg  ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c > .depend
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src/xdrv'
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src/xdrv'
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o -Bstatic -lgcc
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src/xdrv'
Making all in 2.6.24
make[2]: Entering directory `/home/neararo/linuxwacom-0.8.0/src/2.6.24'
cp -f ../2.6.19/wacom_wac.c .
cp -f ../2.6.19/wacom.h .
cp -f ../2.6.22/wacom_wac.h .
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.24-16-generic/build M=/home/neararo/linuxwacom-0.8.0/src/2.6.24
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom_wac.o
  CC [M]  /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom_sys.o
  LD [M]  /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[2]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src/2.6.24'
make[1]: Leaving directory `/home/neararo/linuxwacom-0.8.0/src'
make[1]: Entering directory `/home/neararo/linuxwacom-0.8.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/neararo/linuxwacom-0.8.0'

```

---

### Post by MastaBullz on 2008-05-05
Hello everyone, I can not run the file. Xinitrc to boot my PC to restart my setup, I am French, starting on Linux and I have a little difficulty to understand or do I put this file. Xinitrc I has a wacom bamboo and the beta version 0.7.9-11 driver because I encounter some difficulties with version 0.8.0! 

I would like to know if there is a special code to enter the file. Xinitrc or if he just returned my staff like this: 
```
xsetwacom set stylus button2 3 
xsetwacom set stylus button3 2 
xsetwacom set pad button1 "core key shift" 
xsetwacom set pad button1 "core key shift super" 
xsetwacom set pad button1 "core key ctrl" 
xsetwacom set pad button1 "core alt key super tab" 

```

and I wanted to know whether this file requires absolutely wacomcpl and if it depends on him because I have some problems with him,GUI displays, but show nothing !!! :(


Be indulgent with me and my English, I am not an expert ;) ! 

Another possibility, with a file. sh, but because I try my knowledge are limited, and when my system restarts execute it in the file, but Kate

For those interested I send you my Xorg.0.log together with the results of diagnostic USB my machine: 
```

(II) LoadModule: "wacom" 
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so 
(II) Module wacom: vendor="X.Org Foundation" 
(II) Wacom driver level: 47-0.7.9-11 $ 
(**) stylus device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) cursor device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) eraser device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(**) pad device is /dev/input/wacom 
(**) WACOM: suppress value is 2 
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad) 
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser) 
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor) 
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus) 
(**) Option "Device" "/dev/input/wacom" 
pad Wacom X driver grabbed event device 
(==) Wacom using pressure threshold of 30 for button 1 
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled 
(==) Wacom device "pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540 

```

and lsusb result : 

```
Bus 005 Device 004: ID 0930:6545 Toshiba Corp. 
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 004: ID 1241:1503 Belkin 
Bus 004 Device 003: ID 15ca:00c3 
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 002: ID 056a:0065 Wacom Co., Ltd 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by mishathegoat on 2008-05-06
Followed your steps with no errors displayed but my Wacom Graphire4 Tablet still acts like a mouse :-( Any suggestions? Thanks a bunch

---

### Post by MastaBullz on 2008-05-06
Could you be more specific about how it works please, I do not understand very well what you mean by "works like a mouse"? ;)

---

### Post by tmray on 2008-05-06
> **neko18 said:**
> **@msar24**
Please attach the output of:
```
cat /etc/X11/xorg.conf
```

**@flaviusxvii**
You may want to ask the Linux Wacom Project ( [http://linuxwacom.sf.net](http://linuxwacom.sf.net) ) directly. I doubt this is an Ubuntu-specific issue.

**@chris-chan**
I'm glad your tablet works now

**@tmray**
Do you have to press down on the tablet to move your mouse cursor or can you simply hover over the tablet to move the cursor?

Also, please send the output of these two commands:
```
ls -l /dev/input
xidump -l
```
The tablet functions normally in every other sense. I can move the cursor by hovering and can make it work when I press down. It just doesn't match tablet to screen when I switch from mouse to stylus. The the cursor starts from where it was on the screen originally, not where I have the stylus on the pad relative to the screen. And no pressure sensitivity.

Here is the output of the two commands you requested.

ls -l /dev/input
total 0
drwxr-xr-x 2 root root     80 2008-05-05 21:05 by-id
drwxr-xr-x 2 root root    160 2008-05-05 21:05 by-path
crw-rw---- 1 root root 13, 64 2008-05-05 21:05 event0
crw-rw---- 1 root root 13, 65 2008-05-05 21:05 event1
crw-rw---- 1 root root 13, 66 2008-05-05 21:05 event2
crw-rw---- 1 root root 13, 67 2008-05-05 21:05 event3
crw-rw---- 1 root root 13, 68 2008-05-05 21:05 event4
crw-rw---- 1 root root 13, 69 2008-05-05 21:05 event5
crw-rw---- 1 root root 13, 70 2008-05-05 21:05 event6
crw-rw---- 1 root root 13, 63 2008-05-05 16:04 mice
crw-rw---- 1 root root 13, 32 2008-05-05 16:04 mouse0
crw-rw---- 1 root root 13, 33 2008-05-05 21:05 mouse1
crw-rw---- 1 root root 13, 34 2008-05-05 21:05 mouse2
lrwxrwxrwx 1 root root      6 2008-05-05 21:05 tablet-graphire2-4x5 -> event6
lrwxrwxrwx 1 root root      6 2008-05-05 21:05 wacom -> event6


and

xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               unknown
Configured Mouse               unknown

Thanks for the help in this matter.

---

### Post by mishathegoat on 2008-05-06
> **MastaBullz said:**
> Could you be more specific about how it works please, I do not understand very well what you mean by "works like a mouse"? ;)

Sorry.. I mean..

My pen has to be pressed onto the tablet for ubuntu (hardy) to read where I'm moving it. Whereas usually my pen could hoover over the tablet freely and ubuntu (gutsy) would pick it up. There's no pressure sensitivity or eraser or anything.. It pretty much only functions like a mouse

```
misha@misha-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root     80 2008-05-06 00:03 by-id
drwxr-xr-x 2 root root    160 2008-05-06 00:03 by-path
crw-rw---- 1 root root 13, 64 2008-05-06 00:03 event0
crw-rw---- 1 root root 13, 65 2008-05-06 00:03 event1
crw-rw---- 1 root root 13, 66 2008-05-06 00:03 event2
crw-rw---- 1 root root 13, 67 2008-05-06 00:03 event3
crw-rw---- 1 root root 13, 68 2008-05-06 00:03 event4
crw-rw---- 1 root root 13, 69 2008-05-06 00:03 event5
crw-rw---- 1 root root 13, 70 2008-05-06 00:03 event6
crw-rw---- 1 root root 13, 71 2008-05-06 00:03 event7
crw-rw---- 1 root root 13, 72 2008-05-06 00:03 event8
crw-rw---- 1 root root 13, 63 2008-05-06 00:03 mice
crw-rw---- 1 root root 13, 32 2008-05-06 00:03 mouse0
crw-rw---- 1 root root 13, 33 2008-05-06 00:03 mouse1
crw-rw---- 1 root root 13, 34 2008-05-06 00:03 mouse2
lrwxrwxrwx 1 root root      6 2008-05-06 00:03 tablet-graphire4-4x5 -> event6
lrwxrwxrwx 1 root root      6 2008-05-06 00:03 wacom -> event6
```


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"

EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by MastaBullz on 2008-05-06
> My pen has to be pressed onto the tablet for ubuntu (hardy) to read where I'm moving it. Whereas usually my pen could hoover over the tablet freely and ubuntu (gutsy) would pick it up. There's no pressure sensitivity or eraser or anything.. It pretty much only functions like a mouse


thank you for all precision, I am not an expert but as you try to change the "/ dev / input / wacom" by "/ dev/input/event6" in your xorg.conf?

---

### Post by mishathegoat on 2008-05-06
> **MastaBullz said:**
> thank you for all precision, I am not an expert but as you try to change the "/ dev / input / wacom" by "/ dev/input/event6" in your xorg.conf?

I switched it back to /dev/input/wacom heh I was trying another tutorial after this one which had me switch it to that. Here is my xorg.conf now:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"

EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by MastaBullz on 2008-05-06
Personally, after much reading on the subject I think it comes from a conflict with the TouchPad synaptic, but I am not sure! 
 If you are not against some tests, trying first to put InputDevices on the shelves below the touchpad and keyboard. 
In the second I recall having a problem almost similar with my graphire4 under fiesty, and I had just to see uncomment the line on ISDV4 and it had run. I know that ca may seem barbaric, but the moment that does it work;)

---

### Post by mishathegoat on 2008-05-06
Ah sorry just tried it and it's stiiill not workin'

---

### Post by neko18 on 2008-05-06
**@rospo84**
Your `make` output doesn't have any problems.

**0.** Run this:
```
sudo cp /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

**1.** Reboot and hope your tablet works.

**@MastaBullz**
".xinitrc" does not depend on `wacomcpl`.

To edit ".xinitrc", open a terminal and run the following command:
```
gedit ~/.xinitrc
```

**@mishathegoat**
Try this:

**0.** Open a terminal

**1.** Run these commands:
```
cp /etc/X11/xorg.conf wacom/xorg.conf.before_reorder
gksudo gedit /etc/X11/xorg.conf
```

**2.** Replace the contents of the file with this:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"

EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

**3.** Save (Ctrl-S) and quit (Ctrl-Q)

**4.** Reboot your computer

**@tmray**
That is strange. The tablet device is registered, but it is not being recognized as an extended input device.

When you ran `xidump -l`, had you already used the mouse or was it still functioning properly as a stylus?

If you had already used the mouse, try rebooting, then running these commands (and sending me their output) before using the mouse:
```
xidump -l
xsetwacom list dev
```

---

### Post by mishathegoat on 2008-05-06
Dang, still doesn't work..

---

### Post by neko18 on 2008-05-06
**@mishathegoat**
Just to verify, did you follow through all of the steps? A couple people skipped the last few steps and got the same symptom as you have.

---

### Post by mishathegoat on 2008-05-06
Yup did steps 1 - 20 twice :cry: Sucks because I really need to finish some drawings.. I mean the tablet is working.. I just have to press down with the pen to move the cursor anywhere. So it only functions as a mouse.. there's no pressure sensitivity, erasor, or anything..

---

### Post by tmray on 2008-05-07
> **neko18 said:**
> **@rospo84**
Your `make` output doesn't have any problems.

**0.** Run this:
```
sudo cp /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

**1.** Reboot and hope your tablet works.

**@MastaBullz**
".xinitrc" does not depend on `wacomcpl`.

To edit ".xinitrc", open a terminal and run the following command:
```
gedit ~/.xinitrc
```

**@mishathegoat**
Try this:

**0.** Open a terminal

**1.** Run these commands:
```
cp /etc/X11/xorg.conf wacom/xorg.conf.before_reorder
gksudo gedit /etc/X11/xorg.conf
```

**2.** Replace the contents of the file with this:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"

EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:5:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

**3.** Save (Ctrl-S) and quit (Ctrl-Q)

**4.** Reboot your computer

**@tmray**
That is strange. The tablet device is registered, but it is not being recognized as an extended input device.

When you ran `xidump -l`, had you already used the mouse or was it still functioning properly as a stylus?

If you had already used the mouse, try rebooting, then running these commands (and sending me their output) before using the mouse:
```
xidump -l
xsetwacom list dev
```

I rebooted and didn't touch the mouse. Just used the keyboard and after typing xidump -l this is what I got

xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               unknown
Configured Mouse               unknown

and after typing xsetwacom list dev nothing happened. It just started a new line.

Also just so we can see if I missed anything, here is the xorg.conf readout.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "Module"
        Load            "glx"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/event6"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/event6"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/event6"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/event6"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection


I've tried many different things ready this is just where it is at now. 

I added the info that was mentioned to the "ServerLayout" section before and that didn't work. I've tried /dev/input/wacom as well. And I added the "InputDevice" for wacom pad before too. Same results.

But as I mentioned before, the tablet was working as it is now even before I entered the "InputDevice" wacom settings. Those weren't even in the xorg.conf file when I started I put them there after installing wacom-tools didn't add them.

Thanks again for your help.

---

### Post by hobie1024 on 2008-05-07
I follow the 20 steps twice on my Thinkpad x61t computer. the pen just  does not work. some output of commands are list as follows, some commands does not have any output. I add "NOTE" to soem commands.


usrname@hobie:~$ xsetwacom list dev
usrname@hobie:~$ xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Keyboard0                      unknown
Mouse0                         unknown
usrname@hobie:~$ ls -l /dev/input
total 0
drwxr-xr-x  2 root root     100 2008-05-06 23:48 by-id
drwxr-xr-x  2 root root     180 2008-05-06 23:48 by-path
crw-rw----  1 root root 13,  64 2008-05-06 23:48 event0
crw-rw----  1 root root 13,  65 2008-05-06 23:48 event1
crw-rw----  1 root root 13,  74 2008-05-06 23:48 event10
crw-rw----  1 root root 13,  75 2008-05-06 23:48 event11
crw-rw----  1 root root 13,  76 2008-05-06 23:48 event12
crw-rw----  1 root root 13,  66 2008-05-06 23:48 event2
crw-rw----  1 root root 13,  67 2008-05-06 23:48 event3
crw-rw----  1 root root 13,  68 2008-05-06 23:48 event4
crw-rw----  1 root root 13,  69 2008-05-06 23:48 event5
crw-rw----  1 root root 13,  70 2008-05-06 23:48 event6
crw-rw----  1 root root 13,  71 2008-05-06 23:48 event7
crw-rw----  1 root root 13,  72 2008-05-06 23:48 event8
crw-rw----  1 root root 13,  73 2008-05-06 23:48 event9
crw-rw----  1 root root 13,  63 2008-05-06 16:48 mice
crw-rw----  1 root root 13,  32 2008-05-06 16:48 mouse0
crw-rw----  1 root root 13,  33 2008-05-06 16:48 mouse1
crw-rw----  1 root root 13,  34 2008-05-06 23:48 mouse2
crw-rw----+ 1 root root 10, 223 2008-05-06 23:48 uinput
lrwxrwxrwx  1 root root      10 2008-05-06 23:48 wacom -> /dev/ttyS0
usrname@hobie:~$ xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Keyboard0                      unknown
Mouse0                         unknown
usrname@hobie:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
NOTE: nothing in the opened window.

strange ouput during the procedure of the 20 steps:
usrname@hobie:~$ lsusb | grep -i wacom
NOTE: nothing listed
usrname@hobie:~$ sudo ln -s /usr/include/pixman-1/pixman-version.h /usr/include/pixman-version.h
ln: creating symbolic link `/usr/include/pixman-version.h': File exists


the file xorg.conf is attached.
I just use linux, do not know much on system administration. I spend a lot of time on time. I appreciate your help very much!

hobie

---

### Post by rospo84 on 2008-05-07
> @rospo84
Your `make` output doesn't have any problems.

0. Run this:
Code:

sudo cp /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

1. Reboot and hope your tablet works.
```
neararo@neararo-desktop:~/wacom/linuxwacom-0.8.0$ sudo cp /home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: impossibile fare stat di `/home/neararo/linuxwacom-0.8.0/src/2.6.24/wacom.ko': Nessun file o directory

```
doesn't work!!!
ah, tnx for all till now!!! ( if means something )

---

### Post by mirosol on 2008-05-07
Hi. I'm experiencing some hard time with this. After several hours of trying with this tutorial i've had no luck whatsoever. My laptop is HP Pavillion tx 2020, which is same as all the others in tx2000 series.

I tried with original howto-post and even with that other driver that came from pastebin.

So.. Here's the files... If someone would be able to tell me what i'm doing wrong..

lsusb gives me this - Bus 002 Device 006: ID 056a:0093 Wacom Co., Ltd 

[http://mirosol.kapsi.fi/varasto/wacomproblems/devinput.txt]("http://mirosol.kapsi.fi/varasto/wacomproblems/devinput.txt")
[http://mirosol.kapsi.fi/varasto/wacomproblems/xorg.conf.txt]("http://mirosol.kapsi.fi/varasto/wacomproblems/xorg.conf.txt")
[http://mirosol.kapsi.fi/varasto/wacomproblems/xorg.log.txt]("http://mirosol.kapsi.fi/varasto/wacomproblems/xorg.log.txt")
[http://mirosol.kapsi.fi/varasto/wacomproblems/xsetwacom_xidump.txt]("http://mirosol.kapsi.fi/varasto/wacomproblems/xsetwacom_xidump.txt")

It seems that what ever i do, i can't get ubuntu to recognize the device.

All help is welcome.
+m

---

### Post by jbatalha on 2008-05-07
I'm using a Wacom Graphire 3 on the 8.04 Hardy and i follow all the steps place in this HowTo. The wacom is working fine but time to time the X server restarts itself. 
This only happens when using the Wacom. Any ideas?
Thanks

---

### Post by Fir3chi3f on 2008-05-07
I couldn't have done it without your nice tutorial! :D

Nothing big but, I have to mention, I had to edit some of the directories to get some of the commands to work.

---

### Post by Fir3chi3f on 2008-05-07
I have a suggestion, its not really necessary as the tutorial proves. Adding some pressure sensitivity:

```
Option "PressCurve" "50,0,100,50"
```

Added to the bottom of the stylus section in xorg

---

### Post by BobtheBlueBerry on 2008-05-07
Thank you! :)

---

### Post by Xfcn on 2008-05-07
Not sure if this works for me, yet, but I would recommend tossing the following on the front of the instructions:

sudo apt-get update

I couldn't find the repositories my first time, since this was the VERY first thing I've tried to install since installing 8.04.

**EDIT**

Okay, this worked just fine for me, using instructions 1-20.

Dell Inspiron E1505 -- Intel Core Duo 1.83Ghz

I'd tell you more about my system and specs, but Hardware Information keeps crashing hard on me... ...

---

### Post by MastaBullz on 2008-05-08
> **neko18 said:**
> 

**@MastaBullz**
".xinitrc" does not depend on `wacomcpl`.

To edit ".xinitrc", open a terminal and run the following command:
```
gedit ~/.xinitrc
```[B]
[/B]

I did exactly that, but my setup still does not load when you start the computer, how to fix this problem please? 
 
 Here is my file ".xinitrc" :


```

xsetwacom set cursor Accel "4"
xsetwacom set cursor SpeedLevel "6"
xsetwacom set stylus button2 3
xsetwacom set stylus button3 2
xsetwacom set pad AbsWDn "Button 4"
xsetwacom set pad AbsWUp "Button 5"
xsetwacom set pad Button4 "core key  ALT  SUPER  Tab "
xsetwacom set pad Button3 "core key  CTRL "
xsetwacom set pad Button2 "core key  SHIFT  SUPER "
xsetwacom set pad Button1 "core key  SHIFT "
$ more .xinitrc

```


Thankz for your help ;)

---

### Post by andyrue304 on 2008-05-08
Hi guys,

I'm thinking of getting one of these for my Hardy laptop.

I have a few questions, but to save poluting this threat, I've created my own [here]("http://ubuntuforums.org/showthread.php?p=4901971").

Would be grateful for your opinions!

Cheers:)

---

### Post by mamaar on 2008-05-08
I got a problem after installing this. When I pressed tab in gnome-terminal, X restarted. Now I have commented out the line with
```
InputDevice	"pad"		"SendCoreEvents"
```
And everything seems to work fine now. Am I missing out on something without this line?

---

### Post by neko18 on 2008-05-08
**@tmray**
I'm not sure if the order of the sections in xorg.conf matters, but try replacing yours with this:
```
Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "USB" "on"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Device" "/dev/input/wacom"
	Option "Type" "eraser"
	Option "USB" "on"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "cursor"
	Option "Device" "/dev/input/wacom"
	Option "Type" "cursor"
	Option "USB" "on"
EndSection

Section "Device"
	Identifier "Configured Video Device"
	Driver "nvidia"
	Option "NoLogo" "True"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	Defaultdepth 24
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
EndSection

Section "Module"
	Load "glx"
EndSection
```
I reordered them so the InputDevices came before ServerLayout. I also changed it back to /dev/input/wacom and added the devices to ServerLayout.

**@hobie1024**
You're using a serial tablet. I'm not sure how to set those up, but I suggest searching around the forums some more. You may want to try this:

**0.** ```
gksudo gedit /etc/X11/xorg.conf
```

**1.** Replace the contents of the file with this:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"pad"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
	Load  "GLcore"
	Load  "xtrap"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen		   0  "Screen0" 0 0
	InputDevice    "Mouse0" 	"CorePointer"
	InputDevice    "Keyboard0" 	"CoreKeyboard"
    InputDevice    "stylus" 	"SendCoreEvents"
    InputDevice    "cursor"		"SendCoreEvents"
    InputDevice    "eraser"		"SendCoreEvents"
    InputDevice		"pad"		"SendCoreEvents"
EndSection

```

**2.** Save (Ctrl-S) and quit (Ctrl-Q)

**@rospo84**
Sorry, I must have misread one of your earlier posts. Try this instead.

**0.** Open a terminal and run:
```
sudo cp /home/neararo/wacom/linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

**@mirosol**
I'm not sure, sorry.

**@jbatalha**
This helped fix a similar issue with **mamaar**, so maybe it will work for you.

**0.** Open a terminal and run this:
```
gksudo gedit /etc/X11/xorg.conf
```

**1.** Look for the line that looks like this:
```
	InputDevice	"pad"	"SendCoreEvents"
```

**2.** Replace the line you found in step 1 with this (note the hash mark at the beginning of the line):
```
#	InputDevice	"pad"	"SendCoreEvents"
```

**3.** Save (Ctrl-S) and quit (Ctrl-Q)

**4.** Restart your computer

**@Fir3chi3f**
Thanks for telling me the directories are wrong. I'll run through the instructions again and fix it.

**@BobtheBlueBerry**
I'm glad to help

**@Xfcn**
I added `sudo apt-get update` to the instructions; thanks for the suggestion.

Don't worry about the hardware information, most of the trouble of getting these things working is because of software.

**@MastaBulls**
I'll post instructions for you in a couple minutes

**@mamaar**
Removing that line will disable support for the tablet-specific buttons (on my Bamboo Fun, these are "<", ">", "FN1", and "FN2"). I never use those buttons anyway.

---

### Post by Xfcn on 2008-05-08
No trouble. :)

---

### Post by neko18 on 2008-05-08
**@MastaBulls**
Try this:

**0.** ```
gedit ~/.xinitrc
```

**1.** Replace the file with this:
```
#!/bin/sh
xsetwacom set cursor Accel "4"
xsetwacom set cursor SpeedLevel "6"
xsetwacom set stylus button2 3
xsetwacom set stylus button3 2
xsetwacom set pad AbsWDn "Button 4"
xsetwacom set pad AbsWUp "Button 5"
xsetwacom set pad Button4 "core key  ALT  SUPER  Tab "
xsetwacom set pad Button3 "core key  CTRL "
xsetwacom set pad Button2 "core key  SHIFT  SUPER "
xsetwacom set pad Button1 "core key  SHIFT "

```

**2.** Save and quit gedit

**3.** ```
chmod +x ~/.xinitrc
```

**4.** Send me the output of the following command. Also, are you using Ubuntu or Kubuntu?
```
whoami
```

---

### Post by MastaBullz on 2008-05-08
>  ***Neko 18 Says***

Try this:

**0.**      Code:
     gedit ~/.xinitrc 
**1.** Replace the file with this:
     Code:
     #!/bin/sh
xsetwacom set cursor Accel "4"
xsetwacom set cursor SpeedLevel "6"
xsetwacom set stylus button2 3
xsetwacom set stylus button3 2
xsetwacom set pad AbsWDn "Button 4"
xsetwacom set pad AbsWUp "Button 5"
xsetwacom set pad Button4 "core key  ALT  SUPER  Tab "
xsetwacom set pad Button3 "core key  CTRL "
xsetwacom set pad Button2 "core key  SHIFT  SUPER "
xsetwacom set pad Button1 "core key  SHIFT " 
**2.** Save and quit gedit

**3.**      Code:
     chmod +x ~/.xinitrc 
**4.** Send me the output of the following command. Also, are you using Ubuntu or Kubuntu?
     Code:
     whoami 
                                                                              
Neko18 Thank you! 
 
 This procedure does not work, you have another idea s'il vous plait 
 
 When I send whoami in the terminal return me my username.

PS: 
 I Kubuntu, I replace gedit by kate!

---

### Post by ShelJ on 2008-05-09
Well, it happen again!!  My tablet has been working for a while, and worked great when I upgraded to Hardy.  However, once again an update went and blew the whole deal ...  My tablet stopped working again after updating last week.

Unfortunately, I don't have the time to go through this tutorial today, but I'm glad that you are on top of it for us neko18.  I'll come back later and give it a try.

---

### Post by msar24 on 2008-05-09
I finally got mine working.  Turns out I had some issues with the video adapter and monitor not wanting to play nice with the tablet.

Dell Optiplex 745
Dual Pentium D 3.0GHz
Intel 965 graphics
Westinhouse 19 widescreen LCD (1440 x 900)

I reloaded 8.04 from the CD and installed all the updates.  Once that was done I turned on the app for monitor and video settings and set the monitor to a generic LCD (wide screen) with a resolution of 1024 x 768 and set the graphics adapter to the intel 965.  I can't get the full resolution of the monitor but I reallly do not need it anyway.  I made sure all of the Wacom packages were installed and then followed Neko18's instructions and my Graphire 4 kicked right in.  Stylus, mouse and pressure all work.

Now I just need to find out how to get the buttons on the pad and stylus programmed for what I want.

:KS

---

### Post by ShelJ on 2008-05-09
Hey neko18, thanks again for your help with this, it works great.

---

### Post by msar24 on 2008-05-09
neko18,

How do I specify functions for each button on the pad and on the stylus?

msar24

---

### Post by Xfcn on 2008-05-10
Anyone else having a problem with GUI errors on wacomcpl? I get issues if I try to click into more than one setting. And I was having issues where after adjusting some of the stylus settings, the same issue would crop up when I tried to adjust the settings later.

@msar - In terminal, type: wacomcpl

---

### Post by prokoudine on 2008-05-10
Whenever I create ServerLayout section with all that stuff inside, X server doens't manage to start in full mode, it goes for failsafe mode. Any ideas?

**Edit**: never mind, I removed the synaptics part and it works :)

---

### Post by alecfkayak on 2008-05-10
Cheers for this, worked perfectly with my Wacom Bamboo one

The driver and that needs to be changed to 0.8.0-1 though

---

### Post by piobair on 2008-05-10
Failure report: Wacom tablet does not respond at all

I have a Thinkpad X41. The Wacom worked prior to Hardy.
I followed the above instructions, as excepted: 
The wget from prdownloads.sourceforge.net in Step 5 did not work, so I downloaded the tar manually.
Step 6 required that I apt-get install the pixman package.

more /proc/bus/input/devices does not report a wacom device
However, /var/log/kern.log reports:
May 10 18:27:48 harold kernel: [   35.621535] usbcore: registered new interface driver wacom
May 10 18:27:48 harold kernel: [   35.621947] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver

Suggestions?

---

### Post by Loïc2 on 2008-05-11
Hi neko18,

Thank you for the help you provide to other wacom users.

You edited the wiki at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) (I'm the original creator of the page, and I try to maintain it for each release if there's any changes) by adding at the beginning :

>Ubuntu 8.04 Hardy Heron
>
>To set up your tablet, follow the instructions at [WWW] >[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915) 

I still haven't been able to install Hardy on my computer (CD reader broke and I won't be able to fix that before June), so I might be mistaken (and if so please excuse me - I usually don't like talking without having tried it first, but in this case I can't).

However, I'm under the impression that the fix you suggest in this thread is mostly for Bamboo tablets, not for other Wacom tablets (i.e. all the Intuos models).

Unless Ubuntu developers really botched the job in Hardy (which is still plausible considering other previous regressions), Wacom tablet users (except Bamboo and a few other ones) should see now change from Gutsy (i.e. just plug the tablet in and it works).

If this is the case, your description at the beginning of the wiki might be misleading a lot of users (Bamboo tablets are only a small percentage of the linuxwacom supported tablets), and creating for them some unnecessary troubles.

In case your fix only address Bamboo users, could you please edit the description you gave in the wiki? I don't want to do it myself, because I don't have Hardy yet.

In case linuxwacom is really botched in Hardy, I'd be happy if someone could point me to a bug report in Launchpad though ;)

Thanks,
Loïc

---

### Post by Loïc2 on 2008-05-11
Note : I'll probably do a big clean up of the wiki after June* but it would be nice if Ubuntu Hardy users weren't mislead to think they HAVE to compile the drivers to get it work (during that time) when they could just edit their xorg.conf for that.

I actually created the wiki because I didn't want Ubuntu users to think getting Wacom tablets to work in Ubuntu required to compile your own driver - it's sad if it has now evolved like that (and even for Wacom tablets that are unsupported, it would be far better to provide the compiled driver - in a debian package if possible ;) ).


* I don't plan to delete any information, but since the page got so complicated with each user experience, it has lost most of its purpose, so I plan to either put all the special cases (i.e. special Wacom tablets) AT THE FREAKIN' BOTTOM where it should always have been, or in links to a special page (I already did that for a special configuration, so sad nobody else thought it's worth the trouble to keep the page as simple as possible)

Thanks

---

### Post by neko18 on 2008-05-11
**@Loïc2**
Sorry about my misleading edit.

**@anyone else**
I'm leaving this thread. I no longer have time to reply to everyone. Good luck to you all.

---

### Post by ueman on 2008-05-11
hi, i hava a Intuos 3 wacom, it worked well with gutsy, i just had to configure my xorg.conf, and then downloaded expresskeys to map Gimp shortcuts, to the wacom's pad, and worked perfectly, but then i upgrated to ubuntu hardy, i did the same, configuire my xorg.con, and wacom starts to work but when i try to use expresskeys to map the pad buttons in Gimp, it didnt compile, shearching in internet, i found how to compile it, but, doesnt work. when i open my gimp, and try tu use the pad, to scale my brush or some, Gimp Flicks like it was trying to do something but nothing happens., every thing its well configurated in Gimp, xorg.conf and expresskeys, but now, the pad buttons and scrolls doesnt work anymore in GIMP.

Please some body help me, i'll paste my xorg.conf, and esxpress config files

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option       	"USB"          "on"  
	Option		"Type"	"stylus"
	Option        	"Mode"         "Absolute"
	Option		"Vendor" 	"WACOM"
	Option       	"tilt"         "on"  # add this if your tablet supports tilt
	Option        	"Threshold"    "5"   # the official linuxwacom howto advises this line
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option       	"USB"          "on"  
	Option		"Type"	"eraser"
	Option        	"Mode"         "Absolute"
	Option		"Vendor"	"WACOM"
	Option       	"tilt"         "on"  # add this if your tablet supports tilt
	Option        	"Threshold"    "5"   # the official linuxwacom howto advises this line
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option       	"USB"          "on"  
	Option		"Type"	"cursor"
	Option		"Vendor"	"WACOM"
	Option        	"Mode"         "Absolute"
	#Option		"SpeedLavel"	"3"
	#Option		"Accel"		"0"
	#Option		"Button1"	"Button 1"
	#Option		"Button2"	"Button 2"
	#Option		"Button3"	"Button 3"
	Option		"RelWDn"	"Button 5"
	Option		"RelWUp"	"Button 4"
	#Option		"Button6"	"Button 6"
	#Option		"Button7"	"Button 7"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "pad"
	Driver      "wacom"
	Option      "Type" "pad"
	Option      "Device" "/dev/input/wacom"
	Option      "ButtonsOnly" "off"
	Option      "USB" "on"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Option		"RenderAccel"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
		InputDevice     "pad"		#"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection



the Expresskeys Config is this.

	# <---  ******** BEGIN NEW PROGRAM RECORD ********

ProgramName		"default" # Name must be within double quotes ""

Stylus1PressCurve "0 0 100 100" # PressCurve must be within double quotes ""
Stylus2PressCurve "0 0 100 100" # PressCurve must be within double quotes ""

DelayEachKeycode	0.0	# Seconds (Max 10 - Min 0.01 - Or no delay)

ButtonRepeatAfter	0.5	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayButtonRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

TouchRepeatAfter	0.6	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayTouchRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

HandleTouchStrips	1	# Switch 1/0 (Enable/Disable Touch Strips)

LeftPadTouchUp		994 0	# Keycodes (Max number of keys to send is 32)
LeftPadTouchDown	995 0	# Keycodes (Max number of keys to send is 32)

RepeatLeftUp		1	# Switch 1/0 (Finger held at top repeat keys)
RepeatLeftDown		1	# Switch 1/0 (Finger held at bottom repeat keys)

RightPadTouchUp		98 0	# Keycodes (Max number of keys to send is 32)
RightPadTouchDown	104 0	# Keycodes (Max number of keys to send is 32)

RepeatRightUp		1	# Switch 1/0 (Finger held at top repeat keys)
RepeatRightDown		1	# Switch 1/0 (Finger held at bottom repeat keys)

LeftPadButton9		113 104	# Keycodes (Max number of keys to send is 32)
LeftPadButton10		113 102	# Keycodes (Max number of keys to send is 32)
LeftPadButton11		113 97	# Keycodes (Max number of keys to send is 32)
LeftPadButton12		37 45	# Keycodes (Max number of keys to send is 32)

RepeatButton9		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton10		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton11		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton12		0	# Switch 1/0 (Press and hold button repeat keys)

RightPadButton13	113 104	# Keycodes (Max number of keys to send is 32)
RightPadButton14	113 102	# Keycodes (Max number of keys to send is 32)
RightPadButton15	113 97	# Keycodes (Max number of keys to send is 32)
RightPadButton16	37 45	# Keycodes (Max number of keys to send is 32)

RepeatButton13		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton14		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton15		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton16		0	# Switch 1/0 (Press and hold button repeat keys)

%%			# <---  ******** BEGIN NEW PROGRAM RECORD ********

ProgramName		"Gimp" # Name must be within double quotes ""

Stylus1PressCurve "0 0 100 100" # PressCurve must be within double quotes ""
Stylus2PressCurve "0 0 100 100" # PressCurve must be within double quotes ""

DelayEachKeycode	0.0	# Seconds (Max 10 - Min 0.01 - Or no delay)

ButtonRepeatAfter	0.5	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayButtonRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

TouchRepeatAfter	0.6	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayTouchRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

HandleTouchStrips	1	# Switch 1/0 (Enable/Disable Touch Strips)

LeftPadTouchUp		50 98	# Keycodes (Max number of keys to send is 32)
LeftPadTouchDown	50 104	# Keycodes (Max number of keys to send is 32)

RepeatLeftUp		0	# Switch 1/0 (Finger held at top repeat keys)
RepeatLeftDown		0	# Switch 1/0 (Finger held at bottom repeat keys)

RightPadTouchUp		86	# Keycodes (Max number of keys to send is 32)
RightPadTouchDown	82	# Keycodes (Max number of keys to send is 32)

RepeatRightUp		0	# Switch 1/0 (Finger held at top repeat keys)
RepeatRightDown		0	# Switch 1/0 (Finger held at bottom repeat keys)

LeftPadButton9		37 29	# Keycodes (Max number of keys to send is 32)
LeftPadButton10		37 52	# Keycodes (Max number of keys to send is 32)
LeftPadButton11		37 56	# Keycodes (Max number of keys to send is 32)
LeftPadButton12		95 0	# Keycodes (Max number of keys to send is 32)

RepeatButton9		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton10		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton11		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton12		0	# Switch 1/0 (Press and hold button repeat keys)

RightPadButton13	33 	# Keycodes (Max number of keys to send is 32)
RightPadButton14	39 	# Keycodes (Max number of keys to send is 32)
RightPadButton15	50	# Keycodes (Max number of keys to send is 32)
RightPadButton16	37 46	# Keycodes (Max number of keys to send is 32)

RepeatButton13		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton14		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton15		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton16		0	# Switch 1/0 (Press and hold button repeat keys)

%%			# <---  ******** BEGIN NEW PROGRAM RECORD ********

ProgramName		"Blender" # Name must be within double quotes ""

Stylus1PressCurve "0 0 100 100" # PressCurve must be within double quotes ""
Stylus2PressCurve "0 0 100 100" # PressCurve must be within double quotes ""

DelayEachKeycode	0.0	# Seconds (Max 10 - Min 0.01 - Or no delay)

ButtonRepeatAfter	0.5	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayButtonRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

TouchRepeatAfter	0.6	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayTouchRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

HandleTouchStrips	1	# Switch 1/0 (Enable/Disable Touch Strips)

LeftPadTouchUp		102 0	# Keycodes (Max number of keys to send is 32)
LeftPadTouchDown	100 0	# Keycodes (Max number of keys to send is 32)

RepeatLeftUp		1	# Switch 1/0 (Finger held at top repeat keys)
RepeatLeftDown		1	# Switch 1/0 (Finger held at bottom repeat keys)

RightPadTouchUp		86	# Keycodes (Max number of keys to send is 32)
RightPadTouchDown	82	# Keycodes (Max number of keys to send is 32)

RepeatRightUp		1	# Switch 1/0 (Finger held at top repeat keys)
RepeatRightDown		1	# Switch 1/0 (Finger held at bottom repeat keys)

LeftPadButton9		37 98	# Keycodes (Max number of keys to send is 32)
LeftPadButton10		37 104	# Keycodes (Max number of keys to send is 32)
LeftPadButton11		65	# Keycodes (Max number of keys to send is 32)
LeftPadButton12		23	# Keycodes (Max number of keys to send is 32)

RepeatButton9		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton10		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton11		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton12		0	# Switch 1/0 (Press and hold button repeat keys)

RightPadButton13	38	# Keycodes (Max number of keys to send is 32)
RightPadButton14	9	# Keycodes (Max number of keys to send is 32)
RightPadButton15	37	# Keycodes (Max number of keys to send is 32)
RightPadButton16	50	# Keycodes (Max number of keys to send is 32)

RepeatButton13		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton14		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton15		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton16		0	# Switch 1/0 (Press and hold button repeat keys)

%%			# <---  ******** BEGIN NEW PROGRAM RECORD ********

ProgramName		"XTerm" # Name must be within double quotes ""

Stylus1PressCurve "0 0 100 100" # PressCurve must be within double quotes ""
Stylus2PressCurve "0 0 100 100" # PressCurve must be within double quotes ""

DelayEachKeycode	0.0	# Seconds (Max 10 - Min 0.01 - Or no delay)

ButtonRepeatAfter	0.5	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayButtonRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

TouchRepeatAfter	0.6	# Seconds (Max 10 - Min 0.01 - Or no delay)
DelayTouchRepeat	0.1	# Seconds (Max 10 - Min 0.01 - Or no delay)

HandleTouchStrips	0	# Switch 1/0 (Enable/Disable Touch Strips)

LeftPadTouchUp		0 0	# Keycodes (Max number of keys to send is 32)
LeftPadTouchDown	0 0	# Keycodes (Max number of keys to send is 32)

RepeatLeftUp		0	# Switch 1/0 (Finger held at top repeat keys)
RepeatLeftDown		0	# Switch 1/0 (Finger held at bottom repeat keys)

RightPadTouchUp		0 0	# Keycodes (Max number of keys to send is 32)
RightPadTouchDown	0 0	# Keycodes (Max number of keys to send is 32)

RepeatRightUp		0	# Switch 1/0 (Finger held at top repeat keys)
RepeatRightDown		0	# Switch 1/0 (Finger held at bottom repeat keys)

LeftPadButton9		0 0	# Keycodes (Max number of keys to send is 32)
LeftPadButton10		0 0	# Keycodes (Max number of keys to send is 32)
LeftPadButton11		0 0	# Keycodes (Max number of keys to send is 32)
LeftPadButton12		0 0	# Keycodes (Max number of keys to send is 32)

RepeatButton9		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton10		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton11		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton12		0	# Switch 1/0 (Press and hold button repeat keys)

RightPadButton13	0 0	# Keycodes (Max number of keys to send is 32)
RightPadButton14	0 0	# Keycodes (Max number of keys to send is 32)
RightPadButton15	999 0	# Keycodes (Max number of keys to send is 32)
RightPadButton16	0 0	# Keycodes (Max number of keys to send is 32)

RepeatButton13		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton14		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton15		0	# Switch 1/0 (Press and hold button repeat keys)
RepeatButton16		0	# Switch 1/0 (Press and hold button repeat keys)

plese help me to fix expresskeys, or if thereis other way to map the pad buttons for gimp

Thanks

---

### Post by making on 2008-05-11
Neko, thanks for this excellent piece of work, much more direct, clear, and effective than the LinuxWacom HowTo I wasted more than 2 whole days on.  This was the hardest piece of hardware I've had to set up yet in Linux, and I was ready to give up before finding your HowTo.  Yours may be a general solution for other Debians, as it worked for my Graphire4 on 2 different Sidux machines exactly as described, after only about 30 minutes of work.  _Much_ appreciated.

---

### Post by arelis on 2008-05-12
> *neko18 said:*
@anyone else
I'm leaving this thread. I no longer have time to reply to everyone. Good luck to you all.
.

---

### Post by nazg00l on 2008-05-12
I recently upgraded from Gutsy - where everything was configured OK - to Hardy. My tablet (Bamboo) did work out of the box, but in some weird mouse-like fashion (e.g. no devices were visible in wacomcpl, but pressure sensitivity worked...), so I did the full compilation procedure using driver 0.8.0-1 from Linuxwacom. Now it works... almost.

What I am aiming at is mapping the tablet to a GIMP window (not the whole display - I am using a dual-head setup and the Bamboo is small enough). I can't do it, though. If I configure the xorg.conf file as suggested, in GIMP I get two cursors, one mouse-like moving around the whole display, the other - painting tool - constrained to the window. (When I tell GIMP to map the tablet to Screen instead of Window, I get a single cursor working as expected, but mapped to all the display area.) Playing with "Mode Absolute|Relative and/or SendCoreEvents does not change anything.

The best I could do was to contrain the tablet to a single screen, which makes it usable, while still somewhat wasteful. Does anybody have any idea how to configure the tablet so that GIMP is able to contrain it to picture window? (I think the problem lies in the tablet still sending core events, as the all-screen cursor is the same mouse uses, but removing SendCoreEvents does nothing...)

---

### Post by pamplepoo on 2008-05-12
I don't know if this has been covered, but by page 13 I was getting a headache and I hadn't seen this, SO

Step 8:
gksudo gedit /etc/X11/xorg.conf

didn't do anything. My brother told me to change gedit to nano since i'm using Kubuntu, and that brings up:

[IMG]http://www.ppss.silversorcerer.com/art/temp/xorg_stuck.jpg[/IMG]

He told me to flip through pages until what i saw matched what was in step 9, but nothing i do will make that screen change! up/down/left/right, ctrl+v, page up/down, ctrl+shift+6+V... I dunno. 

so.. any assistance appreciated, please forgive my newbishness :x

---

### Post by moaxey on 2008-05-13
> **Loïc2 said:**
> 
Unless Ubuntu developers really botched the job in Hardy (which is still plausible considering other previous regressions), Wacom tablet users (except Bamboo and a few other ones) should see now change from Gutsy (i.e. just plug the tablet in and it works).

If this is the case, your description at the beginning of the wiki might be misleading a lot of users (Bamboo tablets are only a small percentage of the linuxwacom supported tablets), and creating for them some unnecessary troubles.


Thats certainly the case for me - I've always been able to get my Intuos 2 tablet working - and I've been using since Breezy.

Hardy is the first ubuntu where its completely f#&#WEd and i really hate to follow compiling instructions like this and fail, cos its so impossible to undo whatever damage is done...

---

### Post by munchy on 2008-05-15
works absolutely perfectly with my Bamboo Fun...thankyou thankyou thankyou!
:)

---

### Post by DonQuichote on 2008-05-15
Thanks for the great howto.

I wanted to share that after following the instructions on page 1, my computers tried 3 times to fire up gdm and then failed. If you have the same problem:

Log in with a text terminal: type the key combination [CTRL][ALT][F1] and log in with your normal user name.

Type:
```
ps -eF | grep gdm
```

You will now see a list of processes containing the hanging gdm instances. Kill them with "sudo kill <processnumber>" (except for the last one, because that is grep which has already finished).

Then, type:
```
startx
```

In my case, that fired up a working desktop situation. Looking at /var/crash, I saw that it was a pressure applet I downloaded that was giving the problems.

Hope this is of any help...

Edit:
Looks like I cheered too early. My PC still repeatedly crashes gdm. I uninstalled and reinstalled the packaged wacom tools and the linuxwacom-tools more than enough. It seems that gdm can work and my Bamboo One can work, but not both with Hardy. I never had a problem with Gutsy...

---

### Post by provide on 2008-05-16
> **pamplepoo said:**
> I don't know if this has been covered, but by page 13 I was getting a headache and I hadn't seen this, SO

Step 8:
gksudo gedit /etc/X11/xorg.conf

didn't do anything. My brother told me to change gedit to nano since i'm using Kubuntu, and that brings up:

[IMG]http://www.ppss.silversorcerer.com/art/temp/xorg_stuck.jpg[/IMG]

He told me to flip through pages until what i saw matched what was in step 9, but nothing i do will make that screen change! up/down/left/right, ctrl+v, page up/down, ctrl+shift+6+V... I dunno. 

so.. any assistance appreciated, please forgive my newbishness :x
Try the following instead:

```

kdesu kate /etc/X11/xorg.conf

```

---

### Post by ChameleonDave on 2008-05-17
This guide (modified slightly, to use the latest drivers) worked great for me, but I have one problem.  I configure the buttons to do specific things (e.g. the buttons on the pad open up the GIMP and Inkscape), but they are forgotten at the next reboot.  Why?

Also, the GIMP distinguishes between the two ends of the stylus, but Inkscape doesn't.  Why not?

I'm using a Graphire CTE-440 on Hardy Heron.

---

### Post by priegog on 2008-05-17
Hi guys. 
Just wanted to let you know I finally got my Motion computing M1300 to work, mainly thanks to the instructions given here. I even did a How-to and all. :D So, thanks!

---

### Post by nroussi on 2008-05-19
Thank you for the guide. It worked on my ubuntu 8.04 with the edubuntu LTSP addon package but it only works on the server (when I log on the console) when I log on the thin clients it does not work. I tried to follow the guide by getting into the chroot but it  there are a lot of errors. Do you have any idea of how to get this to work on the thin client environment?

thanks again.

---

### Post by Llewellyn01 on 2008-05-19
Thank you very much, you are a star!

I got my Fujitsu T3010 tablet working thanks to your instructions. Can I just add a slight modification that I did to help others who might have the same device.

In step 9 you have the "ISDV4" fields commented out. If I removed the comment out field i.e. "#" It than works after a reboot.

Thanks again!

Rich

---

### Post by kalphitte on 2008-05-20
I have a lenovo/ibm thinkpad X41 tablet PC...  I followed all of the steps and did not receive any error messages on any steps but the stylus will still not work with my tablet.  I have tried commenting out the tablet pc lines from the xorg.conf and rebooting, then uncommenting them and rebooting and still no go.  I have attached the requested information.  

thank you in advance for your help.

---

### Post by kalphitte on 2008-05-20
> **kalphitte said:**
> I have a lenovo/ibm thinkpad X41 tablet PC...  I followed all of the steps and did not receive any error messages on any steps but the stylus will still not work with my tablet.  I have tried commenting out the tablet pc lines from the xorg.conf and rebooting, then uncommenting them and rebooting and still no go.  I have attached the requested information.  

thank you in advance for your help.

Ok not sure what changed besides htis one thing.

I downloaded linuxwacom-0.8.0-2.tar.bz2 instead of linuxwacom-0.8.0.tar.bz2 and extracted linuxwacom-0.8.0-2 then renamed it to linuxwacom-0.8.0

After that I followed step for step and everything worked fine.

Thanks for the tutorial!

:guitar:

---

### Post by stainsby on 2008-05-20
Worked on my AMD64 machine.

Thanks, you're a champion! :razz:

---

### Post by digital19 on 2008-05-21
I have a Cintiq 12WX, following your instructions the cursor now responds to the pen perfectly!

My only problem is this.. the cursor stays on the primary monitor, not on the cintiq. 

In windows, you can assign a button to shift the cursor from the cintiq to your monitor, and back.

Does anyone know how this works? 

I noticed in the xorg.conf file this line under screen:
 
Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1440+0" 

I'm guessing that means that the cintiq is 1440 pixels over from the primary monitor.  Would there be some way of just adjusting the cintiq pen and adding 1440 pixels to its position?

---

### Post by lklk on 2008-05-22
I can't get it to work on my x61 Thinkpad under the 64-bit version. The x61 has a serial Wacom tablet not a usb one if that helps.

---

### Post by Wokm4n on 2008-05-23
That was easy, thanks a lot it finnaly works :)

---

### Post by nroussi on 2008-05-23
OK, I had a major problem with this because I am using the edubuntu addon. I installed Ubuntu 8.04 AMD64 with and LTSP server. Then I build the thin client image for i386. Out of the box nothing was working. On the server the tablets (Bamboo, BambooFun, Steel Blue) were not even moving the mouse. So I follow this guide and Steel blue starts working but the Bamboos do not. After a lot of searching I found out that there if you change the file wacom_wac.c there might be a chance of this to actually work. In wacom_wac.c there are two C structures towards the end. In one of the structures you will see the definitions of the bamboo tablets and the driver they are supposed to use (WACOM_MO). I changed that to GRAPHIRE and re-compiled and reinstalled again. That got the BambooFun working on the server which is AMD64.


I turned on the thin client and tried, but only the steel blue was working. So, I chroot into the i386 environment, I made sure that the environment was updated and upgraded and followed this guide again. After the third time the bambooFun is working.

If anyone is using LTSP hopefully can use this for some help cause there is not a lot of help on this for thin clients.

---

### Post by leperisland on 2008-05-23
Thanks for this guide, it certainly tool alot less than 2 hours which was a relief!

I have an x61s with a Wacom bamboo & it moves the cursor unbearably slow in Gimp and in Xara the line kind of carries on for a second after you lift the pen off te table. 

Any ideas?

Thanks,

Caroline

---

### Post by Mr. Deutsch on 2008-05-25
Hi

     Thank you for posting help but I have encountered a problem. I followed the instructions as posted in the beginning of this thread and crossed my fingers. I really want the Tablet function of my HP TC4200 to work. Unfortunately it didn't.

     I even made the changes to it as suggested by a fellow user of Ubuntuforums (dolorose wrote: Change the driver to linuxwacom-0.8.0-2.tar.bz2 instead of linuxwacom-0.8.0.tar.bz2 and the instructions work for the tc4200.) and that didn't work either.

     Could you tell me what it is I'm doing that is wrong. I'm very new to being un-windows'ed :-)

I've attached the two text files as specified:

"20. At this point, my tablet began working. If yours still is not, please post in this thread if you need help. Be sure to include any errors you received from the terminal. Also, include the ouput of the following two commands as an attachment (text file):
Code:

cat /etc/X11/xorg.conf
ls -l /dev/input"

Regards,

Daniel

---

### Post by Ted D. on 2008-05-25
I followed the instructions posted by Neko18, but haven't succeded. Did get an error messages as was warned in the instructions at step 13.

error message was: " cp:cannot stat 'linuxwacom-0.8.0/src/2.6.24/ waccom.ko: no such file or directory exists.

please advise & thanks

---

### Post by MacUntu on 2008-05-26
Thanks for the howto but I stick to Windows with my Bamboo... this is really awful. Let's praise plug'n'play.

---

### Post by fsando on 2008-05-26
Thanks for this howto.

I followed the instructions and am now having a weird problem:
In a terminal (gnome-terminal), when I press backspace and it is placed leftmost (ie. deleting every character on the command line) gnome crashes immediately. Ubuntu crashes randomly in other programs, mostly when windows or dialogs are closed.

On the other hand the tablet seems to work perfectly.

A few days a go I updated to 8.04 (clean install) I had this same problem, couldn't figure out where it came from, ended up reinstalling and had a great system running.

Now I just installed the wacom driver and this problem returned - so it is reliably related to the wacom driver installation.

```
cat /etc/X11/xorg.conf

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
Section "Module"
	Load		"glx"
EndSection

ls -l /dev/input

total 0
drwxr-xr-x 2 root root    120 2008-05-26 22:10 by-id
drwxr-xr-x 2 root root    200 2008-05-26 22:10 by-path
crw-rw---- 1 root root 13, 64 2008-05-26 22:10 event0
crw-rw---- 1 root root 13, 65 2008-05-26 22:10 event1
crw-rw---- 1 root root 13, 74 2008-05-26 22:10 event10
crw-rw---- 1 root root 13, 66 2008-05-26 22:10 event2
crw-rw---- 1 root root 13, 67 2008-05-26 22:10 event3
crw-rw---- 1 root root 13, 68 2008-05-26 22:10 event4
crw-rw---- 1 root root 13, 69 2008-05-26 22:10 event5
crw-rw---- 1 root root 13, 70 2008-05-26 22:10 event6
crw-rw---- 1 root root 13, 71 2008-05-26 22:10 event7
crw-rw---- 1 root root 13, 72 2008-05-26 22:10 event8
crw-rw---- 1 root root 13, 73 2008-05-26 22:10 event9
crw-rw---- 1 root root 13, 63 2008-05-27 00:10 mice
crw-rw---- 1 root root 13, 32 2008-05-27 00:10 mouse0
crw-rw---- 1 root root 13, 33 2008-05-26 22:10 mouse1
crw-rw---- 1 root root 13, 34 2008-05-26 22:10 mouse2
crw-rw---- 1 root root 13, 35 2008-05-26 22:10 mouse3

lrwxrwxrwx 1 root root      6 2008-05-26 22:10 tablet-intuos-4x5 -> event9
lrwxrwxrwx 1 root root      6 2008-05-26 22:10 wacom -> event9
```

UPDATE
Apparently I've also lost desktop effects, trying to apply them results in an error.

UPDATE 2
Apparently what happened was that the non-free fglrx driver was replaced with the free one.
What I did was 
1) reinstall the generic kernel (don't know if this was needed or did anything)
2) re-enabled the non-free fglrx
Now have destop effects but the wacom's functioning is faulty

UPDATE 3
Installed xserver-xorg-input-wacom (1:0.7.9.8-0ubuntu3) through synaptic
Added the all the recommended stuff to xorg.conf again
Now I have a good system again: wacom is working, desktop is ok, system is working nicely

---

### Post by fsando on 2008-05-26
> **Ted D. said:**
> I followed the instructions posted by Neko18, but haven't succeded. Did get an error messages as was warned in the instructions at step 13.

error message was: " cp:cannot stat 'linuxwacom-0.8.0/src/2.6.24/ waccom.ko: no such file or directory exists.

please advise & thanks

Your problem is most likely that you downloaded the linuxwacom-0.8.0-2 version and that you should adjust the path accordingly.

---

### Post by fsando on 2008-05-27
> **MacUntu said:**
> Thanks for the howto but I stick to Windows with my Bamboo... this is really awful. Let's praise plug'n'play.

This used to be called 'plug and pray' it took a few years before it was actually working well, probably too many unknowns. Vista is seeing the same kind of problems today.

---

### Post by JimmyI on 2008-05-27
Thanks alot, your guide worked a treat for me. (First attempt failed miserably for some reason though!).

Quick question, is there a way to change the ative area on the pad? I have a Bambo 4X5, widescreen, but a square 19" monitor. My brain can't cope with having to move further horizontaly than vertical.

Many thanks
James

---

### Post by mallow on 2008-05-27
Hi. I`ve got a problem. Under Ubuntu 7.10 my Intuos tablet worked great. Since upgrade to Hardy Heron using it is a pain. At first all the tablet`s express keys didn`t work. Thanks to [this tip]("http://ubuntuforums.org/showpost.php?p=4784464&postcount=2") express keys do work, but only until I use a touchstrip. Then the expresskeys deamon is killed. If running in terminal, it gives: "Segmentation fault". I`ve upgraded to latest linux wacom driver following this tutorial, but it still doesn`t work.
Please help. I really need this tablet working. I wouldn`t like to downgrade to Gutsy Gibbon or worse - install Windows.

At least tell me something. Does anyone`s Intuos touchstrips work under Hardy Heron. If so, I would go clean reinstall and try everything again. But if not, if noone managed to make the touchstrips work, then I really don`t know what to do next :(

---

### Post by munchy on 2008-05-27
Had my Bamboo Fun tablet working after following this guide however I did a software update recently which disabled my tablet, I'm guessing it was due to one of the kernel related updates that were in there. Anyway, I followed through the guide again which worked perfectly and my tablet sprung back into life.
Just wondering if there is any need to follow ALL the steps again? Or if it's just a case of typing 1 or 2 commands to get my tablet operational after a kernel upgrade?
Fantastic How-to by the way!!!

---

### Post by Pauan on 2008-05-27
This how-to worked flawlessly when I followed it by the letter, but did not work when using the latest 0.8.0-3 drivers. Neko, I know you are busy, but perhaps you could put a notice on the first post that this only works with the 0.8.0 drivers?

---

### Post by LordKonti on 2008-05-28
Lenovo x61t with a MultiView + MultiTouch WVA XGA TFT, dual booting Vista32 biz & Hardy Heron 32bit (Installed with Wubi)

@Neko18- Your post has been invaluable in getting the tablet functionality working on my Lenovo x61t multi touch tablet!  Thank you so much.

I was able to get the latest Wacom drivers (at time of post) to work for the stylus input by adding a "-3" to the end of any and all references to the driver, for instance this line from step 5:

tar xjf linuxwacom-0.8.0.tar.bz2

Gets Changed to:

tar xjf linuxwacom-0.8.0-3.tar.bz2

I continued this where necessary; which was steps 5, 13, and 15 I believe.

Through farther research and multiple other great walk-throughs I was able to get the "Touch" functionality working with a slight change to the xorg.conf, what I used is posted below.

The only thing that I could really use some help with now is calibrating the touch sensor (the stylus is calibrated perfectly, I'm also not sure that I needed the "pad" input device entry).

If anyone could help me with this it would be greatly appreciated!

---

### Post by LordKonti on 2008-05-28
Sorry bout the long post (first one), maybe i shouldn't have put the entire xorg.conf in there!  I just made the change to having it there as an attachment.

---

### Post by mallow on 2008-05-29
Thanks neko18. It finally works for me. I`ve done few more things, don`t know what exactly helped. For example, I`ve installed tcl-dev and tk-dev and done again all the steps from your HOWTO. Success for me this time :)
ExpressKeys deamon still doesn`t work right, but I reassigned shortcuts with wacomcpl. Unfortunatelly I don`t know how to set different sorts of shortcuts depending on on specific applications, but at least expresskeys work fine.

> **MastaBullz said:**
> I did exactly that, but my setup still does not load when you start the computer, how to fix this problem please?

run gnome-session-properties:
```
username@ubuntu:~$ gnome-session-properties
```

now just add .xinitrc as a starting app. type these for example:

name: ExpressKeys
command: /home/username/.xinitrc
comment: sets my preferences of WACOM ExpressKeys

It should work. It works for me. The .xinitrc file should run everytime you login to Gnome.

O, and here`s my .xinitrc file at the attathements. Unzip it first.

---

### Post by ivan malo on 2008-05-29
Hi my baboo fun works great, except it is not recognized as an extended device neither in gimp or inkscape and i cant use pressure sensitive, could anyone help me get it recognized as an extended devicee?

---

### Post by kjones on 2008-05-30
That worked great!Thanks for the information. Now my Wacom mouse finally works and the pen buttons do what they're supposed to do. :)

How difficult would it be to put all of these steps in to a "package" file of some type? I'm planning a project for a local school using Ubuntu and wacom tablets and having the ability to easily install the proper drivers and software would make it so much easier. 

Kevin

---

### Post by Ted D. on 2008-05-30
> **fsando said:**
> Your problem is most likely that you downloaded the linuxwacom-0.8.0-2 version and that you should adjust the path accordingly.

How do I do this? Thanks. Ted D.

---

### Post by geobiker on 2008-05-30
> **ivan malo said:**
> Hi my baboo fun works great, except it is not recognized as an extended device neither in gimp or inkscape and i cant use pressure sensitive, could anyone help me get it recognized as an extended devicee?

I'm having the same problem--using the 8.0 driver and Gutsy 7.10.  The Bamboo tablet installs fine but is not recognized as an extended input device in GIMP. I've combed the Linux Wacom pages as well as the Ubuntu forums and can't seem to figure out a solution.  I've posted messages several places elsewhere and so far have not heard back.  Please help us with this-- I would like to get my Bamboo working in GIMP.

---

### Post by FOBoi1122 on 2008-05-31
I got my wacom pen to work for my Fujitsu T4220 tablet PC yesturday, but due to me messing around with trying to install files from the wacomproject, I messed it up again. In desperation, I tried to follow your instructions on installing the wacom pen with no success. here's a copy of my xorg.conf

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom" # "/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom" # "/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom" # "/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by arm-c on 2008-06-02
Well,

I would like to thank all for the post.  Especially for the EXCELLENT build instructions in the start of this post.  Through no fault of the post, it didn't work for me for a while... and after the 8.0 and 7x driver run... I was able to dig in and find a clue in my Xorg.0.log file...

** I was reported that the device was timing out.  I copied the line and Googled (love google) for it and eventually turned up the solution for me.

The new driver 8.0-3 worked fine, and supplented by your instructions, the build and install went great.

I am using an ACER C300 tablet PC.

When the creator gets a chance, the lead entry needs to be updated to the new driver... apparently the ones you are using weren't good for my serial TabletPC.

NOW A QUESTION:
When I use the wacomcpl, what should I see?  I just have a blank screen and three entries on the left.  Clicking them gives me an error box, so I don't know what this is supposed to help me CONTROL or give me a clue about it.  Are the errors normal????

---

### Post by moogstork on 2008-06-02
I have tried and failed to do this so many times with my Wacom Bamboo. I have followed every step to the letter, before and after the kernel upgrades. I get no errors. Everything seems to be going fine! ...till I reboot. GDM starts, but then decides against it. It informs me,

"The greeter application appears to be crashing. Attempting to use a different one."

It does that and fails. The only cure is to comment out the bit in the xorg conf that tells you not to comment it out:

```
# Uncomment if you have a wacom tablet
#        InputDevice     "stylus"
#        InputDevice     "cursor"
#        InputDevice     "eraser"
#        InputDevice     "pad"

```

Interestingly enough, whilst that error message comes up, the tablet works beautifully. Mapped to the corners properly and EVERYTHING. But I can't do anything. Of course after I comment out the lines in the conf file I can get to the log-in window, but the tablet returns to its crappy self if I do.

Help me please! I am pulling my hair out over this.

Edit: Just out curiosity, I tried other display managers (XDM, KDM &c), but neither do any good. Humph.

---

### Post by arm-c on 2008-06-04
While my system is a tablet PC, I recommend that you repeat the initial steps, however, use the latest release 0.8.0-3 (or something like that.).  It may solve your issues. It worked for me when the 0.8.0 and 0.7.x didn't work.

For your information (and others), my tablet worked out of the box initially when I installed 7.04 last year, but 7.10 and 8.04 it was broken in.

---

### Post by geobiker on 2008-06-05
I got my Bamboo working in GIMP and extend my hearty thanks to **andrevanzuydam** and **andguent** for their postings in this thread: [http://ubuntuforums.org/showthread.php?p=4804392]("http://ubuntuforums.org/showthread.php?p=4804392")

The trick is to disable xgl by creating a file called "disable" in the hidden folder called .config/xserver-xgl/disable.

I came across this by realizing that the Wacom driver was installing and running fine, but that the Desktop Effects had compiz and xgl running, which was preventing xinput (and hence, GIMP) from seeing the tablet.  This is apparently a known bug-- at least there's a workaround.

---

### Post by WasMeHere on 2008-06-05
Thanks Neko18,
 It worked fine to use your instructions to make my daughter's Bamboo Fun work with version 16, but after updating to 17 (and 18) recently, it stopped working. How can I reactivate the driver for her tablet? (Is it necessary to redo the whole list of instructions, or is it enough with one or a few of them?) 
 It still works if she starts version 16 from the grub menu.
looking forward to your answer
Best regards/Olle

---

### Post by Strash on 2008-06-05
I followed this tutorial and didn't get my Wacom Bamboo working. Can you help me ?

It used to work well 1 month ago but now it didn't work :cry:

Here is some informations :

```
~$ uname -a
Linux oripi-164 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

~$ lsusb | grep -i wacom
Bus 002 Device 003: ID 056a:0065 Wacom Co., Ltd

~$ cat /var/log/Xorg.0.log | grep -i wacom
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.9-11 $
(II) LoadModule: "wacom"
(II) Reloading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Wacom driver level: 47-0.7.9-11 $
(**) stylus device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) cursor device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) eraser device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) pad device is /dev/input/wacom
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
pad Wacom X driver can't grab event device, errno=1022
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Bamboo tablet speed=9600 maxX=14760 maxY=9225 maxZ=511 resX=2540 resY=2540  tilt=enabled
(==) Wacom device "pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540

~$ lsmod | grep -i wacom
wacom                  18816  0 
usbcore               146028  5 wacom,usbhid,ehci_hcd,uhci_hcd

~$ cat /etc/X11/xorg.conf

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	
	Inputdevice "stylus" "SendCoreEvents"
	Inputdevice "cursor" "SendCoreEvents"
	Inputdevice "eraser" "SendCoreEvents"
	Inputdevice "pad"
EndSection

Section "Files"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
  	Load "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
	Load  "wacom"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
	Identifier	"pad"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"pad"
	Option		"USB"	"on"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fr"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option      "ShmConfig" "true"
EndSection

Section "Monitor"
	Identifier   "LCD"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"

	Option	    "OverlayOnCRTC2" "1"
	Option	    "UseInternalAGPGART" "no"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "DRI" "true"
	Option      "XAANoOffscreenPixmaps" "true"

	Option      "ForceMonitors" "lvds, tv"
	Option      "Mode2" "1024x768, 800x600, 640x480"
	Option      "TVFormat" "PAL-N"
	Option      "DesktopSetup" "c"

	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "enable"
	Option      "DAMAGE" "true"
EndSection

Section "ServerFlags"
	Option       "AIGLX" "true"
EndSection

```

If someone can help me !

Thanks

---

### Post by Trivia89 on 2008-06-05
I've tried lots of different drivers versions for my HP Pavilion tx2000... 0.7.9-11, 0.8.0, 0.8.0-3... 
I got the same output as one guy on the second page, so i tried patching the driver (0.8.0-3 and 0.7.9-11) and reinstalling... but i've got nothing!
I neither have got a "wacom" dev in /dev/input...

Hope somebody can help me fixing this!

```
alberto@alberto-laptop:~$ cat /var/log/Xorg.0.log | grep -i wacom
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.9-11 $
(**) stylus device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) cursor device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) eraser device is /dev/input/wacom
(**) WACOM: suppress value is 2
(**) pad device is /dev/input/wacom
(**) WACOM: suppress value is 2
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
Error opening /dev/input/wacom : Success
```

---

### Post by arm-c on 2008-06-05
Trivia89, check to see if you have serial port mapped correctly.  My tablet has a "weird" mapping for the serial device and I have to place it in the config file.  See if you can find out what the serial settings are for your device.  I am just taking a stab at the problem.  

In /etc there is a file called "serial.conf"

MY SERIAL.COF File
**********
#Stylus pen
/dev/ttyS0 port 0x06f8 irq 6 uart 16550A
**** End of file ****

Again, you will need to find out the settings... and this is just a hunch on my part.

Good luck

---

### Post by Trivia89 on 2008-06-06
> **arm-c said:**
> Trivia89, check to see if you have serial port mapped correctly.  My tablet has a "weird" mapping for the serial device and I have to place it in the config file.  See if you can find out what the serial settings are for your device.  I am just taking a stab at the problem.  

In /etc there is a file called "serial.conf"

MY SERIAL.COF File
**********
#Stylus pen
/dev/ttyS0 port 0x06f8 irq 6 uart 16550A
**** End of file ****

Again, you will need to find out the settings... and this is just a hunch on my part.

Good luck

I still don't seem to be able to make the /dev/input/wacom appear... :(

I get this output from dmesg:
```
alberto@alberto-laptop:~$ dmesg | grep tty
[   43.479381] console [tty0] enabled
[   66.843799] audit(1212734990.216:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5249 profile="/usr/sbin/cupsd" namespace="default"
```

The Xorg log is the same as above... is there anybody with my same tablet pc? (hp tx2000) I did not find a way to figure out my serial settings... any suggestions?

---

### Post by labwizard on 2008-06-06
hello i am a new at Linux and ubuntu, hopefully i can transfer completly from windows, i have a Cintiq 20wsx, and i installed the driver for wacom. My now the screen acts like a tablet, i mean usually hovering over the screen (not touching it) will make the mouse move exactly at where the stylus is. now i have to click and drag on the screen surface to make the cursor move and the offset is huge depending on where i click. plus it is so slow...
can anybody please help... i am an artist and moving to Linux depends on this. thank you

---

### Post by M42 on 2008-06-06
> **Trivia89 said:**
> 

The Xorg log is the same as above... is there anybody with my same tablet pc? (hp tx2000) I did not find a way to figure out my serial settings... any suggestions?

I have a HP tx2000 series (tx2113cl) laptop and follow a guide on another thread.  TomtheWombat's guide near the bottom of the page worked for me.

[http://ubuntuforums.org/showthread.php?t=708726&highlight=tx2000&page=3](http://ubuntuforums.org/showthread.php?t=708726&highlight=tx2000&page=3)

You will need to change the kernel numbers to the one you are using .  Also when the kernel changes you need to re-run with the new kernel numbers.

Good luck.

---

### Post by JoelP on 2008-06-07
The link provided in step 16 no longer works.

Thanks.

---

### Post by wire604 on 2008-06-08
Hi I might have join this thread late...
I recently got a Tx2000  or close enough that reports

lsusb | grep -i wacom:
Bus 002 Device 004: ID 056a:0093 Wacom Co., Ltd 

So its still not working after the 1 post tutorial. Now i noticed that Mykes had the same device than I and process all information that was sent to both Mykes and rajivnavada. But its still not working.

Im providing all file requested to them for your support.

alto I can say that I had issues with some part of the process let me put them here
From:[http://ubuntuforums.org/showpost.php?p=4811746&postcount=20](http://ubuntuforums.org/showpost.php?p=4811746&postcount=20)

5.
Code:
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.normal_build.`uname -r`
sudo cp linuxwacom-0.7.9-11/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

6. Follow steps 13,

and from the step 13 
[http://ubuntuforums.org/showpost.php?p=4785779&postcount=1](http://ubuntuforums.org/showpost.php?p=4785779&postcount=1)
13.
Code:
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
ot found.. so i change the command and my position to be in location of wacom.co

aint those steps override each other?

I still went tru them i had some problem, i was getting a file not found.. so i change the command and my position to be in location of wacom.ko and putted the request it went fine...

is this where i did soething wrong?

this may help
kernel 2.6.22.17
gnome with compiz fusion...
im pretty new to linux but im getting it pretty quickly

Let me know please !

---

### Post by CITguy on 2008-06-10
Thank you so much for this post. I've been looking everywhere for instructions on getting my Bamboo Tablet to work. It works perfectly!

---

### Post by SebbyT on 2008-06-10
This was a really helpful - my old Wacom Intuos2 now works properly in Hardy 8.04. (running on a Dell Latitude D630, w/ nVidia) - all I had to do was modify my xorg.conf file:

Understanding that Hardy was supposed to support Wacom tablets right out of the box, I searched for wacom-related items ("locate wacom" in the terminal) and saw that I had the wacom specific drivers, files, etc. already installed by default. So before assuming the worst and going through all the complexity of downloading, compiling, etc. I thought I'd try simply modifying xorg.conf first (steps 8-12 in the original post), and what do you know? It worked!

---

### Post by ChameleonDave on 2008-06-12
Linuxwacom-0.8.0-3 is now out.  Perhaps you should update this guide.

---

### Post by aleb on 2008-06-12
> **SebbyT said:**
> This was a really helpful - my old Wacom Intuos2 now works properly in Hardy 8.04. (running on a Dell Latitude D630, w/ nVidia) - all I had to do was modify my xorg.conf file
SebbyT, in case you have an USB Intuos2, please tell me what happens if you unplug and then plug back the tablet; does it work as expected?
Is your screen aspect ratio 4:3?
Thanks!

---

### Post by alex34567 on 2008-06-13
I just wanted to say thank you. I'm fairly new to Linux and still don't have a good grasp of things. There is no way I could have gotten things working without this step-by-step guide.

---

### Post by Ollec on 2008-06-13
I am trying to get my Fujitsu T4220 working it is Penabled by wacom. I am running 8.04. I thought this should work seeing he has the tablet PC part of the xorg.conf I uncommented that and was hoping that would do the trick. It still isn't working.

I didn't really experience any errors while following this guide but I did have one problem, on step 2 when I enter this code,
lsusb | grep -i wacom

Nothing is returned. I kept going hoping it would still work. It isn't. Please find the desired files attached. Any help would be greatly appreciated. =)


Thanks!

~Ted


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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
  

drwxr-xr-x 2 root root    140 2008-06-13 12:33 by-path
crw-rw---- 1 root root 13, 64 2008-06-13 12:33 event0
crw-rw---- 1 root root 13, 65 2008-06-13 12:33 event1
crw-rw---- 1 root root 13, 66 2008-06-13 12:33 event2
crw-rw---- 1 root root 13, 67 2008-06-13 12:33 event3
crw-rw---- 1 root root 13, 68 2008-06-13 12:33 event4
crw-rw---- 1 root root 13, 69 2008-06-13 12:33 event5
crw-rw---- 1 root root 13, 70 2008-06-13 12:33 event6
crw-rw---- 1 root root 13, 71 2008-06-13 12:33 event7
crw-rw---- 1 root root 13, 72 2008-06-13 12:33 event8
crw-rw---- 1 root root 13, 63 2008-06-13 05:32 mice
crw-rw---- 1 root root 13, 32 2008-06-13 05:32 mouse0
crw-rw---- 1 root root 13, 33 2008-06-13 12:33 mouse1

---

### Post by the dsc on 2008-06-14
> **mooosebag said:**
> Hi,

foa : Thanks for the howto, it's really bulky :)

So, if I go step-by-step through it, it won't really work at all, there are two things I found, so, now it works fine - at last with linuxwacom 0.8.0

First : 


I had this error too and found a solution in :

(This is for hardy heron / 8.04)

```

cd /usr/include
sudo ln -s /usr/include/pixman-1/pixman.h
sudo ln -s /usr/include/pixman-1/pixman-version.h

```

After this symbolic link the 'make / make install' works fine and wacom.ko is built, so you could do the following steps.

After all I had to do one step more to get wacom full functionally :

```

cd [path to linuxwacom...version...]/src/2.6.24 (or other kernel-version)
sudo rmmod wacom
sudo insmod ./wacom.ko

```

After this I'm able to use my wacom bamboo full featured :)

SoLong

Don't think that I'm in any way blaming you, but look how complicated things can be... I'm using debian Lenny, I just did that and my bamboo stoped working completely... previously it was at least in a "mouse mode", with no hovering and quite slow movement... :(


**Edit:** after reboot (rather than just restart X), and perhaps some other attemps of just having it working back, the tablet is working again, but still only in "relative" mode and with no hovernig...

---

### Post by cwillip on 2008-06-15
> **LordKonti said:**
> Lenovo x61t with a MultiView + MultiTouch WVA XGA TFT, dual booting Vista32 biz & Hardy Heron 32bit (Installed with Wubi)

@Neko18- Your post has been invaluable in getting the tablet functionality working on my Lenovo x61t multi touch tablet!  Thank you so much.

I was able to get the latest Wacom drivers (at time of post) to work for the stylus input by adding a "-3" to the end of any and all references to the driver, for instance this line from step 5:

tar xjf linuxwacom-0.8.0.tar.bz2

Gets Changed to:

tar xjf linuxwacom-0.8.0-3.tar.bz2

I continued this where necessary; which was steps 5, 13, and 15 I believe.

Through farther research and multiple other great walk-throughs I was able to get the "Touch" functionality working with a slight change to the xorg.conf, what I used is posted below.

The only thing that I could really use some help with now is calibrating the touch sensor (the stylus is calibrated perfectly, I'm also not sure that I needed the "pad" input device entry).

If anyone could help me with this it would be greatly appreciated!


LordKonti,
I commented out the pad section with no adverse effect. Have you found a way to calibrate multitouch on your x61t? It seems i'm at the same stage on mine.

Good luck!

---

### Post by wire604 on 2008-06-15
> **wire604 said:**
> Hi I might have join this thread late...
I recently got a Tx2000  or close enough that reports

lsusb | grep -i wacom:
Bus 002 Device 004: ID 056a:0093 Wacom Co., Ltd 

So its still not working after the 1 post tutorial. Now i noticed that Mykes had the same device than I and process all information that was sent to both Mykes and rajivnavada. But its still not working.

Im providing all file requested to them for your support.

alto I can say that I had issues with some part of the process let me put them here
From:[http://ubuntuforums.org/showpost.php?p=4811746&postcount=20](http://ubuntuforums.org/showpost.php?p=4811746&postcount=20)

5.
Code:
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.normal_build.`uname -r`
sudo cp linuxwacom-0.7.9-11/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

6. Follow steps 13,

and from the step 13 
[http://ubuntuforums.org/showpost.php?p=4785779&postcount=1](http://ubuntuforums.org/showpost.php?p=4785779&postcount=1)
13.
Code:
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
ot found.. so i change the command and my position to be in location of wacom.co

aint those steps override each other?

I still went tru them i had some problem, i was getting a file not found.. so i change the command and my position to be in location of wacom.ko and putted the request it went fine...

is this where i did soething wrong?

this may help
kernel 2.6.22.17
gnome with compiz fusion...
im pretty new to linux but im getting it pretty quickly

Let me know please !

Yay i got it working !
manage to understand what i was doing and modified some stuff to make it work
im so happy

---

### Post by ortwein on 2008-06-17
I have a Lenovo x61 tablet.  I followed the directions to the letter, and nothing happened.  My tablet doesn't do anything at all. here are the results:

tigre@tigre-laptop:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

---

### Post by Ollec on 2008-06-17
> **ortwein said:**
> I have a Lenovo x61 tablet.  I followed the directions to the letter, and nothing happened.  My tablet doesn't do anything at all. here are the results:

 

I am having the same Problem. Two suggestions though, When you do step two : "lsusb | grep -i wacom"

Does it report anything? I think I should reply with what kind of Wacom it detects. When I type it on my Fujitsu It reports nothing, which is part of my problem I think. 

Second I think you are supposed to uncomment the "For tablet PC" lines, so try deleting the # at the begging of the line. so it looks like this

> Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection


Just my guesses, I hope it works. I would like to get mine working as well. Best of luck.

~Ted

---

### Post by goggle5 on 2008-06-18
I finally got my Wacom Graphire 4 to work in 7.10 ...  but one problem I am having, particularly in GIMP in that the cursor/stylus position is not exactly calibrated to pad.  The positions are off by several centimeters.  I tried changing some of the input device settings in GIMP - but it didn't help any.  I looked in my xorg.conf file but I did not see anything for calibration (X,Y?) Any suggestions or fixes would be most appreciated.

---

### Post by transkinetic on 2008-06-20
I have a graphire 3 that worked fine in previous installations. I followed the step by step at the beginning of this thread but it still doesn't work.

Woot, figured it out! It had to do with forgetting some sendcoreevents entries and the system crashing do to references to pad.

See my thread for details...

[http://ubuntuforums.org/showthread.php?p=5227418#post5227418](http://ubuntuforums.org/showthread.php?p=5227418#post5227418)

---

### Post by sarah.fauzia on 2008-06-20
> **ortwein said:**
> I have a Lenovo x61 tablet.  I followed the directions to the letter, and nothing happened.  My tablet doesn't do anything at all. here are the results:

tigre@tigre-laptop:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

I followed the instructions with a different tutorial--because of it my Wacom pen works perfectly! I just had to add another code to my xorg.conf to also enable the eraser (if you end up needing it, you can see the the thread I posted [when my eraser wasn't working]("http://ph.ubuntuforums.com/showthread.php?t=830496") properly). Try this [link]("http://ph.ubuntuforums.com/showthread.php?t=796359"), and see if it works for you!

---

### Post by troseph on 2008-06-21
Neko18, you are my new personal hero!

---

### Post by willyboy666 on 2008-06-21
i have been fighting since ubuntu6 ,
i have a gateway c120x tablet .

my problem is the Bus 001 Device 004: ID 056a:0093
none of the driver worked for me .

any suggestions...???????

10x

---

### Post by Kalibur on 2008-06-22
> **willyboy666 said:**
> i have been fighting since ubuntu6 ,
i have a gateway c120x tablet .

my problem is the Bus 001 Device 004: ID 056a:0093
none of the driver worked for me .

any suggestions...???????

10x

Same issue with me

---

### Post by siennalizard on 2008-06-22
Do these instructions apply also to Tablet PCs, like my HP TX2130? It has a USB Wacom touchscreen.

Many thanks,
J.

---

### Post by unsapiens on 2008-06-23
thanks too much

---

### Post by ozbluenose on 2008-06-24
Hello everyone.

I had some problems with my first attempt at this where I was copy-typing the codes from Neko18 manually.  I only got to point 13 before encountering an error.  This turned out to be a typographical error by me.  By the time I discovered this and tried again, I had rebooted a couple of times and had also downloaded some automatic updates in ubuntu.  For whatever reason, my subsequent attempt to finish off and then completely redo the code from Neko18 didn't work.  I have since reinstalled ubuntu, as it was a new installation for me anyway, so not much loss, except for several days of my life.  From a clean install, I have just re-entered Neko18's code by copying and pasting the text into Terminal to avoid my typo's and it has worked first time.  My WACOM CTE-440 is working beautifully.  So a big thanks to Neko18 for his/her time and work.

So to those that did encounter a problem and haven't been able to fix it, somehow either reverting to the previous state before entering any of Neko18's code or reinstalling ubuntu might be in order before trying again perhaps by copying and pasting to avoid any mistakes.

Bye the way, I have been determined to leave Windows XP, primarily because I'm fed up with my system getting slower and slower even immediately after boot-up, and so I tried several other Linux distributions in the past couple of days.  OpenSUSE v11 has a nice WACOM GUI control tool, but it didn't work and I lost all mouse control, including my touchpad on my laptop.  That was a shame as I liked the look of OpenSUSE, but I need my tablet to work.  But Mandriva One Spring 2008 had my tablet working first time from the live CD without any modification; very nice.  I'd already installed ubuntu to my hard drive, so before overwriting it with Mandriva, I gave it one last try as I liked the look of ubuntu a bit more than Mandriva.  Close call.  It would be nice if the ubuntu programmers were able to do the same with the tablet installation and setup, though.

Regards.

---

### Post by Methuselah on 2008-06-24
The instructions worked for me!
Thanks for putting this guide up.

---

### Post by Thomaseov on 2008-06-24
Hi,  I just followed the instructions through (but substituted 8.0-3 for 8.0 throughout for the latest driver) and the good news is that my bamboo is working beautifully for the first time.

The bad news is though that my system is now buggered...I can't launch an x-session except for failsafe gnome, and even then I get an error that HAL has failed to initialize...leaving me with no wireless, no compiz, no shutdown...

I found an old post about this error with NVIDIA so I purged my invidia install and reinstalled fresh, but still the same.

Anybody?  Help.
Thomas

---

### Post by eddb0t on 2008-06-24
> **neko18 said:**
> **[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**


Worked like a charm, thanks.

---

### Post by Thomaseov on 2008-06-25
> **Thomaseov said:**
> Hi,  I just followed the instructions through (but substituted 8.0-3 for 8.0 throughout for the latest driver) and the good news is that my bamboo is working beautifully for the first time.

The bad news is though that my system is now buggered...I can't launch an x-session except for failsafe gnome, and even then I get an error that HAL has failed to initialize...leaving me with no wireless, no compiz, no shutdown...

I found an old post about this error with NVIDIA so I purged my invidia install and reinstalled fresh, but still the same.

Anybody?  Help.
Thomas


UPDATE:
System is fine when tablet is unplugged.  So to recap the bamboo works but only when started in failsafe, but still conflicts with HAL stopping HAL from initializing.  Has anyone else had this problem?  Any ideas?

It seems obvious that the tablet is conflicting with HAL for some resource.  Also, when I plug the tablet in when already booted, it does act like a mouse, but is misaligned with screen and jumps around alot.  But if I reboot with tablet attached, fails to launch regular x-session.

It is edubuntu 8.04  on a pundit p1-AH1 running on a generic kernel with onboard NVIDIA 6150 graphics.  

Thanks
Thomas

---

### Post by Cruce on 2008-06-26
This is my second week of Ubuntu, i`m kinda newb at it, this howto was so comprehensive i actually managed to set up my Wacom Bamboo A6 Wide, works like a charm and i just wanned to say thanx A LOT! :D

---

### Post by Kalibur on 2008-06-26
I have gone through several how tos and still no break thru to get touch screen working.  I am using an HP TX2000 running hardy heron 8.04 with the latest everything I just updated. I got my sound (no mic and headphone sound) and wireless working perfecting (ndiswrapper).  The result from lsusb terminal command are:

kalibur@kal-tx2000:~$ lsusb
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd 
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. 
Bus 001 Device 004: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000 

May the guys that go the touchscreen working paste the results from command lsusb at terminal please.  Thank you in advance

---

### Post by setdosa on 2008-06-29
Can you please please tell me how you got it working. I tried everything i can but I still dont see the /dev/input/wacom. I used linux 0.8.0, 0.7.9.11 devel version. the driver seems to work fine and it looks like the udev doesnt have 0093 listed. which is what lsusb gives 056a:0093. I tried adding the line manually after the neko version in the beginning to the 50-xser.. file which went like this 

```
KERNEL=="event[0-9]*", DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="00", SYMLINK="input/wacom0"
KERNEL=="event[0-9]*", DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="01", SYMLINK="input/wacom1"
```

based on [http://www.nabble.com/Re:-Slightly-modified-wacom.rules-td17449264.html]("http://www.nabble.com/Re:-Slightly-modified-wacom.rules-td17449264.html")
which didnt work either.

I tried wacdump with all the /dev/input/eventX but none of them are saying the Model is wacom.


Thanks a lot for helping me

---

### Post by mlsandahl on 2008-06-29
neko18,
Yesterday I bought a Bamboo Fun.  I've started doing some wallpapers in GIMP, but until now I've done everything with a mouse.  I followed your guide, and within 30 minutes I have a working tablet, pressure sensitivity and all! Many thanks! 

It would be great to have these tablets automatically working out of the box, but luckily we have people like you writing how-to's like this.

I'm running Linux Mint 5, and I'll be posting a link to your post on their forums if there isn't one already.  Great work!

Michael

---

### Post by Momof9Blessings on 2008-06-29
Hi all,

I went thru and did not have any error messages.  I have a Compaq Presario V5000 and Wacom ET-0405-R.

lori@lori-laptop:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
lori@lori-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    100 2008-06-29 18:54 by-id
drwxr-xr-x 2 root root    180 2008-06-29 18:54 by-path
crw-rw---- 1 root root 13, 64 2008-06-29 18:54 event0
crw-rw---- 1 root root 13, 65 2008-06-29 18:54 event1
crw-rw---- 1 root root 13, 74 2008-06-29 18:54 event10
crw-rw---- 1 root root 13, 66 2008-06-29 18:54 event2
crw-rw---- 1 root root 13, 67 2008-06-29 18:54 event3
crw-rw---- 1 root root 13, 68 2008-06-29 18:54 event4
crw-rw---- 1 root root 13, 69 2008-06-29 18:54 event5
crw-rw---- 1 root root 13, 70 2008-06-29 18:54 event6
crw-rw---- 1 root root 13, 71 2008-06-29 18:54 event7
crw-rw---- 1 root root 13, 72 2008-06-29 18:54 event8
crw-rw---- 1 root root 13, 73 2008-06-29 18:54 event9
crw-rw---- 1 root root 13, 63 2008-06-29 18:54 mice
crw-rw---- 1 root root 13, 32 2008-06-29 18:54 mouse0
crw-rw---- 1 root root 13, 33 2008-06-29 18:54 mouse1
crw-rw---- 1 root root 13, 34 2008-06-29 18:54 mouse2

Thank you,
Lori

---

### Post by dusty ghost on 2008-06-30
Hey buddy! Great tutorial! My intous3 is working much better.
Any clues on how to get the pressure sensitivity working in GIMP?

Again great tutorial thanks! :D

---

### Post by koosfoto.hu on 2008-07-01
Well, Neko18! GREAT! It worked as it might ever do!
THANKS a lot!!!!

I have a CTE-440 (silver).
On the tablet there are two buttons, as well. How can I make them programed and used, as well?

Thanks a lot, again, and again!

Tamas

---

### Post by asafk88 on 2008-07-03
Hello!
I switched to Ubuntu some time ago and until now everything's great.
Except... I have a problem with Expresskeys.
when I type ./configure I get this message:
 
.....
"
/usr/lib/libX11.so OK
/usr/lib/libXext.so OK
/usr/lib/libXi.so OK
Can not link with Xtst /usr/lib/libXtst.so library!
/usr/include/X11/Xlib.h OK
/usr/include/X11/Xutil.h OK
/usr/include/X11/extensions/XInput.h OK
/usr/include/X11/extensions/XIproto.h OK
/usr/include/X11/extensions/XTest.h OK

The X compiling environment is NOT complete!
Some linux distributions omit parts of, or sometimes
the whole, X development environment. Based on the
error message(s) above you should be able to hunt down
which package(s) you need to install. For example, one
distribution call their xinput and xtest packages
libxi-dev and libxtst-dev
"

help pls...

---

### Post by johnnylavah on 2008-07-04
> **arm-c said:**
> Well,

I would like to thank all for the post.  Especially for the EXCELLENT build instructions in the start of this post.  Through no fault of the post, it didn't work for me for a while... and after the 8.0 and 7x driver run... I was able to dig in and find a clue in my Xorg.0.log file...

** I was reported that the device was timing out.  I copied the line and Googled (love google) for it and eventually turned up the solution for me.

The new driver 8.0-3 worked fine, and supplented by your instructions, the build and install went great.

I am using an ACER C300 tablet PC.

When the creator gets a chance, the lead entry needs to be updated to the new driver... apparently the ones you are using weren't good for my serial TabletPC.

NOW A QUESTION:
When I use the wacomcpl, what should I see?  I just have a blank screen and three entries on the left.  Clicking them gives me an error box, so I don't know what this is supposed to help me CONTROL or give me a clue about it.  Are the errors normal????

did you ever get it working on your Acer?  i cannot get the stylus to work for the life of me.  i had it working fine in gusty, and it still worked when i upgraded to hardy, but last night i did a fresh install of hardy and i cannot get the stylus to work.

i run the command sudo xxd /dev/ttyS0 and the screen reacts to the pen, but that is the 
only time the screen recognizes/reacts to the pen.

any ideas?  i am on an acer c310 (very similar to the c300).

thank you!

---

### Post by asafk88 on 2008-07-05
> Hello!
I switched to Ubuntu some time ago and until now everything's great.
Except... I have a problem with Expresskeys.
when I type ./configure I get this message:

.....
"
/usr/lib/libX11.so OK
/usr/lib/libXext.so OK
/usr/lib/libXi.so OK
Can not link with Xtst /usr/lib/libXtst.so library!
/usr/include/X11/Xlib.h OK
/usr/include/X11/Xutil.h OK
/usr/include/X11/extensions/XInput.h OK
/usr/include/X11/extensions/XIproto.h OK
/usr/include/X11/extensions/XTest.h OK

The X compiling environment is NOT complete!
Some linux distributions omit parts of, or sometimes
the whole, X development environment. Based on the
error message(s) above you should be able to hunt down
which package(s) you need to install. For example, one
distribution call their xinput and xtest packages
libxi-dev and libxtst-dev
"

help pls... 



Ok... I solved it by installing the xtst package..
But now, i get this error:
>  expresskeys ERROR: Tablet not attached, OR (in case of Cintiq 21UX, Intuos3
and Graphire4) the 'pad' device has not been specified in xorg.conf, OR is
lacking on the command line when using "named devices".
 

The xorg.conf is edited correctly...
So I searched in google, and I saw a suggestion to change a couple of lines in the source..
But I dont know how to remove or recompile expresskeys...
pls help me :rolleyes:

---

### Post by johnnylavah on 2008-07-07
> **johnnylavah said:**
> did you ever get it working on your Acer?  i cannot get the stylus to work for the life of me.  i had it working fine in gusty, and it still worked when i upgraded to hardy, but last night i did a fresh install of hardy and i cannot get the stylus to work.

i run the command sudo xxd /dev/ttyS0 and the screen reacts to the pen, but that is the 
only time the screen recognizes/reacts to the pen.

any ideas?  i am on an acer c310 (very similar to the c300).

thank you!


ok, i finally got the stylus working, but it is allover the place.  the cursor is up and to the right of everyplace i touch on the screen and selects everything i highlight.  anyone else experience this?

---

### Post by ProsaicPatch on 2008-07-08
Hi, I just went through all your guide, but the tablet still isnt pressure sensetive... it's a wacom graphire, now a bamboo, but the guide said it should have worked anyways...  Anywho, I read through a few of the responses, and dug up this, if it helps.
fireseed@fireseed-desktop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-07-08 13:04 by-id
drwxr-xr-x 2 root root    160 2008-07-08 13:04 by-path
crw-rw---- 1 root root 13, 64 2008-07-08 13:04 event0
crw-rw---- 1 root root 13, 65 2008-07-08 13:04 event1
crw-rw---- 1 root root 13, 66 2008-07-08 13:04 event2
crw-rw---- 1 root root 13, 67 2008-07-08 13:04 event3
crw-rw---- 1 root root 13, 68 2008-07-08 13:04 event4
crw-rw---- 1 root root 13, 69 2008-07-08 13:04 event5
crw-rw---- 1 root root 13, 70 2008-07-08 13:04 event6
crw-rw---- 1 root root 13, 71 2008-07-08 13:04 event7
crw-rw---- 1 root root 13, 63 2008-07-08 13:04 mice
crw-rw---- 1 root root 13, 32 2008-07-08 13:04 mouse0
crw-rw---- 1 root root 13, 33 2008-07-08 13:04 mouse1
crw-rw---- 1 root root 13, 34 2008-07-08 13:04 mouse2
lrwxrwxrwx 1 root root      6 2008-07-08 13:04 tablet-graphire4-6x8 -> event7
lrwxrwxrwx 1 root root      6 2008-07-08 13:04 wacom -> event7
fireseed@fireseed-desktop:~$ 


help. pleeease

---

### Post by bonfire89 on 2008-07-09
any tips on getting a tabletPC to work with an external monitor?

---

### Post by tpradeep369 on 2008-07-09
Hi
Thanks for all the info 
I am trying to enable the tablet features in ubuntu. 8.04 on an x61 
and i have followed all the steps that were mentioned 
but it did not work. i did not see any errors either 

attached are the out puts of those two commands 

thanks, 
pradeep

---

### Post by guy87 on 2008-07-10
Hi! I'm a very very NOOB, i'm using Ubuntu 8.04 with a Wacom Volito 1 tablet that now works as a normale mouse (no pressure, no tablet's pad limits).
I'd like to have it working better so i tried to follow the how-to and at step 7 when i write:

./configure --enable-wacom
make
sudo make install

i get this:

damiano@dam:~$ ./configure --enable-wacom
bash: ./configure: Nessun file o directory
damiano@dam:~$ make
make: *** No targets specified and no makefile found. 
damiano@dam:~$ sudo make install
make: *** No rule to make target `install'. 

Please tell me what to do... Thanks!!!

---

### Post by provide on 2008-07-10
@guy87:

In step 5, did you "cd" into the wacom directory?

---

### Post by SuperGrouper on 2008-07-10
Thank you so much for making this thread!  Your method is far easier than manually downloading and extracting the files, and while the old method worked when I first installed Hardy, it wouldn't work after the first time I updated the OS.

Now, my tablet works well.  Thank you! :)

---

### Post by SuperGrouper on 2008-07-10
Um, I know this may sound dumb, but I don't have much experience here yet- how do I "thank" you for this post?  I can't find the button to click anywhere around your post. ^^;  I know that such a thing exists, because I've seen it before on other posts.  Why isn't it showing on yours?  Is it an issue with my account somehow, do you think? :(

---

### Post by Ed J on 2008-07-12
Thanks,  
Getting the pad and stylus to work under ubuntu has almost convinced my daughter to migrate from vista to ubuntu.

WTG

Ed

---

### Post by fsando on 2008-07-13
Thanks for the howto my wacom pad work.

But I now experience consistently predictable crashes:

In a console whenever the cursor hit a limit gnome crashes immediately - no questions asked (so to speak). I am suddenly in a full screen terminal in which some process is running. Wen I tap the keyboard I can see strange character sequences but it doesn't react to what I'm typing.

I can go to another terminal (ie. alt + F1) login and reboot (sudo shutdown -r now)

To reproduce:
Open a console, use the arrow keys to move the cursor. If the cursor is to its leftmost position try to move it further left (click left arrow) or likewise to the right or downwards - same result.

When I installed the driver I first allowed myself to use the newest driver, after experiencing the crashes I followed howto verbatim which didn't change anything.

This does not happen in kde's konsole. It happens in gnomes default console, in xterm, xterm unicode

My guess is that the driver affects what is sent from the keyboard in some way.

Any suggestions?

Just discovered that an important app also crashes because of this so now I really need to uninstall the driver until I can get it fixed.

---

### Post by MHmr on 2008-07-13
This worked great. My only problem now is getting the calibration working. wacompl & wacdump refuse to work.

A note for Tx2000 users, I couldn't get this guide to work until I made absolutely sure my graphics card had been installed properly. As soon as I had done that it worked perfectly.

---

### Post by larry19l on 2008-07-14
Trouble in step 7 line 1: "./configure --enable-wacom"
the error? : "configure:2441: error: C compiler cannot create executables"
also, what is the output of the next 2 cmds in step 7 supposed to be ?

./
It's been years since I ran a make on anything! (are you old enough to remember CP/M ? and ASM and lint and linkers and ISO Pascal and Borland C ?
How about an original first edition of K&R ! :lolflag: )
./

Ok,so now what ?
Attached config.log file (renamed: configlog.txt)

---

### Post by opendesigner on 2008-07-17
Hey Super thanks for this guide!

Just worked perfectly for me.

Just two questions: There is something like a control panel to change settings for the tablet?

How can I change button funcions of my pen?

Again great guide and big thanks!

MrMax

---

### Post by nacodbera on 2008-07-18
> **adamsad1 said:**
> This works perfectly on my X61 tablet!

I am running Linux Mint Elyssa on my x61 Tablet and followed your procedures. I didn't get any error messages however the stylus still is nonfunctional. Please help when you have a sec.. thanks!

---

### Post by fsando on 2008-07-18
> **fsando said:**
> Thanks for the howto my wacom pad work.

But I now experience consistently predictable crashes:

In a console whenever the cursor hit a limit gnome crashes immediately - no questions asked (so to speak). I am suddenly in a full screen terminal in which some process is running. Wen I tap the keyboard I can see strange character sequences but it doesn't react to what I'm typing.

I can go to another terminal (ie. alt + F1) login and reboot (sudo shutdown -r now)

To reproduce:
Open a console, use the arrow keys to move the cursor. If the cursor is to its leftmost position try to move it further left (click left arrow) or likewise to the right or downwards - same result.

When I installed the driver I first allowed myself to use the newest driver, after experiencing the crashes I followed howto verbatim which didn't change anything.

This does not happen in kde's konsole. It happens in gnomes default console, in xterm, xterm unicode

My guess is that the driver affects what is sent from the keyboard in some way.

Any suggestions?

Just discovered that an important app also crashes because of this so now I really need to uninstall the driver until I can get it fixed.

I'd like to repeat my posting.

It did not work for me in the following sense:
After installing the wacom pen worked absolutely perfect for the first time since I installed Hardy BUT:

1) gnome-terminal would lock up so that I'd have to force a reboot - mostly I could go to another shell other times I couldn't.

2) One very important applications would constantly crash.

I'd like to give much more info, I'm willing to reinstall the driver to get as much info as possible if someone can tell me what kind of info to provide and what to do te get it.

---

### Post by megadeus on 2008-07-18
Just wanted to say thanks for this post! The forum-based thanking feature seems to have expired, but I just wanted to let you know that it worked perfectly on the second try!

The first try, I didn't type the apt-get install commands correctly and misspelled a few critical compiling components. If possible, you might want to edit the post to encourage users to copy and paste your commands directly! :-)

The only minor config issue was solved with xsetwacom and a startup shell script copied from my Gutsy install, but those were easily fixed. Cheers!

---

### Post by susanzsx on 2008-07-19
Hi, I've just switched over to Ubuntu recently and I have had some trouble installing my Intuos 3 Wacom tablet. It works when I plug it in like a mouse (no pressure sensitivity, positioning only available on direct contact). I've gone through the tutorial step by step but nothing seemed to have changed. 

The tablet is: 
Bus 002 Device 002: ID 056a:00b1 Wacom Co., Ltd 

I am on a Compaq Presario with Nvidia graphics. 

Thanks!

---

### Post by Repus on 2008-07-20
Thanks for the great guide. I am curious about something though. After a kernel patch where should I start on the guide to get my bamboo working again? It seems every couple of months I have to go through the process again and I know I'm putting more effort into it then is required, so anyone have a recommendation where to start on the guide after a kernel patch kills your tablet?

---

### Post by neko18 on 2008-07-20
**@Repus**
Whenever there's a kernel upgrade I refer back to my post (I'm the creator of this thread) and go through the guide. It only takes about 10 minutes, which isn't a significant amount of time.

However, you should be able to avoid repeating all of this by saving your ~/wacom directory. Whenever there is a kernel upgrade, simply run these commands to fix your tablet (if you know how and are motivated enough, you could make this into a shell script):
```
cd ~/wacom
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

I'm not positive that will work, but it doesn't hurt to give it a try next time you upgrade your kernel.

---

### Post by larry19l on 2008-07-22
Sounds good2me, thankx
So where can I find a good tutorial on writing (and naming) shell scripts ? Is this for the bash shell and where do I find a list of it's commands & syntax ?

---

### Post by larry19l on 2008-07-22
> **megadeus said:**
> 
The only minor config issue was solved with xsetwacom and a startup shell script copied from my Gutsy install, but those were easily fixed. Cheers!

Hi, What is xsetwacom and could you post that shell script ?
Right now I've loaded linuxwacom.0.8.1.tar but when I boot, the tablet is not properly detected until I hit some of the buttons on the tablet or take the mouse off and use the pen. Any idea as to the cause ? Does it make any difference where in the /etc/X11/xorg.conf file the wacom sections are ? I put them after the keyboard and mouse. Maybe I should remove the non-Wacom mouse section ? Also, wacom mouse clicks are hit-and-miss, mostly miss, gotta click 2,3, sometimes 4 times to do something ? Don't know yet about tilt, rotation or pressure. I'm waiting delivery on a 6D pen. Then I'll do some real testing. After I re-read wacom docs, I'll see if I have time to make a QC chart for the 8.1 driver.
---
L8r...

---

### Post by willyboy666 on 2008-07-22
hi every body and thanks for the great guide.

here is my success story:

first i have a c-120x 12 inch widescreen tablet pc.
i have been trying to get the touch screen working for months and today i got  99% of the wacom touchscren to work .

first my tablet get this with lsusb:

root@walid-Tablet:/home/walid# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000

i installed the 0.8.1-1 driver (thanks to the guide in the beginning of the thread) so i got the tablet to work partially ,(i edited the xorg in this way so i got the 99%) 
my xorg 

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
# Option        "Device"        "/dev/input/event10"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option "TopX" "225"
  Option "TopY" "122"
  Option "BottomX" "26365"
  Option "BottomY" "16488"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
# Option        "Device"        "/dev/input/event10"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
# Option        "Device"        "/dev/input/event10"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "touch"
# Option "Device" "/dev/input/by-id/usb-Tablet_ISD-V4-event-mouse"
  Option        "Device"        "/dev/input/event10"   # USB ONLY
  Option        "Type"          "touch"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option        "USB"           "on"                  # USB ONLY

EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"
	InputDevice    "touch"     "SendCoreEvents"
EndSection 


After trying 1000 of possibilities with xorg,i found
the only way to get the touch and the stylus to work together and to be calibrated ,is to put the touch at event10 or event11 (crazy ,every restart the wacom changes from event10 to event11 and opposite ,bug ),and all others at /dev/input/by-id/usb-Tablet_ISD-V4-event-mouse.

and now i 1%that is bugging me, is evey time i restart the tablet i have to run wacomcpl to change the key function.

if somebody know how to save it ,please tell me .

thanks for everybody for the great work.

---

### Post by Dave M G on 2008-07-25
Thank you for creating this how-to.

I have been using a Wacom tablet since Edgy Eft, and it was working fine. I am not sure of my tablet's exact model number, but this is the output of lsusb | grep -i wacom:

Bus 002 Device 004: ID 056a:0016 Wacom Co., Ltd

Since upgrading to Hardy, I get the offset problem reported by many around the web. In GIMP and Inkscape, the mouse cursor and where the line is drawn are two different places. I have two monitors, and can not seem to get the stylus to draw in Window mode without the offset problem making it impossible to draw.

I followed the instructions provided in the very first post to this thread, and was able to complete the entire set of instructions without a single error. On reboot, my Wacom tablet works.

However, I still have the offset problem. Is there something additional I need to do to get rid of this offset problem?

I have attached my xorg.conf file for reference.

Thank you for any assistance.

---

### Post by RocksThatFloat on 2008-07-25
Hi,

I have a bamboo fun tablet and a macbook running hardy.
I ran through the steps 3 times now, once with the patch, never with any errors, same id(056a:0017).

My bamboo works for a few seconds immediately after I plug it in but only on contact.

I attached both the commands and their outputs.

Any help appreciated, thanks.

---

### Post by zalun on 2008-07-27
Thank you for the Howto - it's great.

I have a multiple screens setup (2 to be exact), no compiz. Is it possible to setup the wacom area to work only on one of these?

---

### Post by AKnightintheDesert on 2008-07-27
Ok maybe i am just slow but I went threw this entire thing and still have nothing when I try to use the pen on my Lenovo X61 Tablet PC.  It was a Wacom tablet installed. Please help :(

---

### Post by juanpecan on 2008-07-28
I did what you said Niko and my intuos3 seemed to be working fine.  However upon restart my computer insists on being in 800x600 low graphics mode. When I try to change the resolution back up to 1920x1200 the option doesn't exist. I'm at a loss for what to do from here.  Help please!  Docs attached, much thanks for help fixing this.

John

---

### Post by juanpecan on 2008-07-28
also, now the wacom tablet isnt working either.

---

### Post by ellkae on 2008-07-31
I didn't look through the entire thread to check if anyone is experiencing the same problems I'm having, but I have two that I immediately noticed.

1) Pressure sensitivity doesn't work in gimp (I saw people getting help with this problem) Also, do I need to configure the pen for the stylus and eraser to be separate?

2) X crashes while I'm using terminal. Specifically when I'm using tab completion or when I'm using my arrow keys to scroll through my bash history and I go past the head or the tail entries (like if I open the terminal and just press down).

Can someone help me with the problems? More my second than the first. Thanks.

---

### Post by queseuq on 2008-07-31
Went through all the steps and my Bamboo still acts like a touchpad.  Pretty sure I didn't get any error messages. Here are the results from the terminal.

PS. Thanks for taking the time to create such a detailed how-to, and for helping out when it doesn't work :)

---

### Post by juanpecan on 2008-08-01
Nevermind, I worked it out.  I renamed my xorg.conf and restarted the comp.  Ubuntu automatically made a fresh new basic one.  I then set up my graphics card/monitor then followed this setup specifically for the Intuos3: 

[http://cgi.feureau.com/2008/02/how-to-get-wacom-tablet-fully-working.html](http://cgi.feureau.com/2008/02/how-to-get-wacom-tablet-fully-working.html)

---

### Post by ronaldogg on 2008-08-01
I followed your procedure I got no errors, but nothing happens.

I have a tablet PC Lenovo X61, with Vista/Hardy.
Vista tablets works OK.
I'd like to use my tablet pen in Ubuntu and other software related to the tablet PC.

Thanks.

$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

#original starts here
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
rgarcia@RGG-tablet-pc:~$ ls -l /dev/input
total 0
drwxr-xr-x  2 root root      80 2008-08-01 12:01 by-id
drwxr-xr-x  2 root root     160 2008-08-01 12:01 by-path
crw-rw----  1 root root 13,  64 2008-08-01 11:56 event0
crw-rw----  1 root root 13,  65 2008-08-01 11:56 event1
crw-rw----  1 root root 13,  74 2008-08-01 11:56 event10
crw-rw----  1 root root 13,  66 2008-08-01 12:01 event2
crw-rw----  1 root root 13,  67 2008-08-01 11:56 event3
crw-rw----  1 root root 13,  68 2008-08-01 11:56 event4
crw-rw----  1 root root 13,  69 2008-08-01 11:56 event5
crw-rw----  1 root root 13,  70 2008-08-01 11:56 event6
crw-rw----  1 root root 13,  71 2008-08-01 11:56 event7
crw-rw----  1 root root 13,  72 2008-08-01 11:56 event8
crw-rw----  1 root root 13,  73 2008-08-01 11:56 event9
crw-rw----  1 root root 13,  63 2008-08-01 07:55 mice
crw-rw----  1 root root 13,  32 2008-08-01 07:55 mouse0
crw-rw----  1 root root 13,  33 2008-08-01 12:01 mouse1
crw-rw----  1 root root 13,  34 2008-08-01 11:56 mouse2
crw-rw----+ 1 root root 10, 223 2008-08-01 11:56 uinput
lrwxrwxrwx  1 root root      10 2008-08-01 11:56 wacom -> /dev/ttyS1
rgarcia@RGG-tablet-pc:~$

---

### Post by rusty spork on 2008-08-01
I got through all of the code without any problems, but I rebooted and my touch pad wasn't working.  I have a hp tx2000 tablet with ubuntu hardy heron.  Here is what I got after I entered the two commands:

First one:
```

joe@joe-tablet:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		 "RandRRotation"  "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```




Second one:

```
joe@joe-tablet:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-08-01 21:14 by-path
crw-rw---- 1 root root 13, 64 2008-08-01 21:14 event0
crw-rw---- 1 root root 13, 65 2008-08-01 21:14 event1
crw-rw---- 1 root root 13, 66 2008-08-01 21:14 event2
crw-rw---- 1 root root 13, 67 2008-08-01 21:14 event3
crw-rw---- 1 root root 13, 68 2008-08-01 21:14 event4
crw-rw---- 1 root root 13, 69 2008-08-01 21:14 event5
crw-rw---- 1 root root 13, 70 2008-08-01 21:14 event6
crw-rw---- 1 root root 13, 71 2008-08-01 21:14 event7
crw-rw---- 1 root root 13, 72 2008-08-01 21:14 event8
crw-rw---- 1 root root 13, 73 2008-08-01 21:14 event9
crw-rw---- 1 root root 13, 63 2008-08-01 16:13 mice
crw-rw---- 1 root root 13, 32 2008-08-01 16:13 mouse0
crw-rw---- 1 root root 13, 33 2008-08-01 21:14 mouse1

```

Thanks for any help you might be able to offer.

---

### Post by Denis Clijsters on 2008-08-02
Making doesn't work here. This is what I get (i only added the last part of the output)

......... -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl   -o libwacomcfg.la -rpath /usr/local/lib -no-undefined -version-info 0:1:0 wacomcfg.lo -L/usr/lib -lX11 -lXi -lxf86config -lm 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi -lxf86config -lm  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
/usr/bin/ld: cannot find -lxf86config
collect2: ld returned 1 exit status
make[2]: *** [libwacomcfg.la] Fout 1
make[2]: Map '/home/dclijste/svn/linuxwacom-0.8.1-2/src/util' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/dclijste/svn/linuxwacom-0.8.1-2/src' wordt verlaten
make: *** [all-recursive] Fout 1

It seems to be that I don't have lxf86config, what is this?

I have a HP TC1100 Tablet PC. The pen always worked till ubuntu hardy due to the xorg 7.3 update..

Thanks in advance

---

### Post by apjone on 2008-08-03
> **ellkae said:**
> I didn't look through the entire thread to check if anyone is experiencing the same problems I'm having, but I have two that I immediately noticed.

1) Pressure sensitivity doesn't work in gimp (I saw people getting help with this problem) Also, do I need to configure the pen for the stylus and eraser to be separate?

2) X crashes while I'm using terminal. Specifically when I'm using tab completion or when I'm using my arrow keys to scroll through my bash history and I go past the head or the tail entries (like if I open the terminal and just press down).

Can someone help me with the problems? More my second than the first. Thanks.

I also get the problem with the terminal, nothing in logs that i can find. Also notice i have no ttys on any ctrl+alt+function keys.

Any help would be greatly accepted!!:confused::confused::confused:

---

### Post by weegie on 2008-08-03
Welldone Necko18. 
Everything works as expected on my Bamboo - including pressure sensitivity in GIMP.

Only issue was that most commands had to be executed as sudo.

Many thanks

---

### Post by apjone on 2008-08-03
@necko18

I have the same machine as r32inc, it comes up as "configured mouse" and here is my output. the pen needs training.

```

InputDevice: Configured Mouse
Valuators: Relative   ID: Unreported  Serial Number: Unreported

             x-axis    y-axis
     data:  +01218    +00154
      min:  -00001    -00001
      max:  -00001    -00001
      res:  +00001    +00001

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
Proximity:
    Focus:
  Buttons:  1-UP  
     Keys:



```

> 
**@r32inc**
I see. You may want to take that to the Linux Wacom Project since they'll know far more about tablet PCs than I do. I use an external USB tablet (which doesn't even have the option of sensing fingers).


---

### Post by gma-murphy on 2008-08-04
This is probably a stupid question about something simple i've overlooked, but i'm a complete noob with linux. (though i think i've already learnt quite a bit about the system just from messing around trying to get this tablet working)

The tablet is a wacom graphire4 6x8 and is working at the moment like a laptop touch pad. 
When i type #ls -1 /dev/input the terminal returns:
> by-id
by-path
event0
event1
event2
event3
event4
event5
event6
event7
event8
mice
mouse0
mouse1
mouse2
tablet-graphire4-6x8
wacom


From what i can figure from these forums, the next step to get it working properly is:
> 
sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko

which returns:
> 
cp: cannot stat 'linux-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

I've looked  in the directory and the only files there seem to be:
> Makefile.in
wacom_sys.c

when i run #locate wacom.ko the terminal returns:
> /lib/moduels/2.6.24-16-generic/kernel/drivers/input/tablet/wacom.ko
/lib/moduels/2.6.24-19-generic/kernel/drivers/input/tablet/wacom.ko

As best i can figure, the file just doesn't exist.

Can anybody help me out?

---

### Post by willyboy666 on 2008-08-04
> **Denis Clijsters said:**
> Making doesn't work here. This is what I get (i only added the last part of the output)

......... -I/usr/include/tcl -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl   -o libwacomcfg.la -rpath /usr/local/lib -no-undefined -version-info 0:1:0 wacomcfg.lo -L/usr/lib -lX11 -lXi -lxf86config -lm 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi -lxf86config -lm  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
/usr/bin/ld: cannot find -lxf86config
collect2: ld returned 1 exit status
make[2]: *** [libwacomcfg.la] Fout 1
make[2]: Map '/home/dclijste/svn/linuxwacom-0.8.1-2/src/util' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/dclijste/svn/linuxwacom-0.8.1-2/src' wordt verlaten
make: *** [all-recursive] Fout 1

It seems to be that I don't have lxf86config, what is this?

I have a HP TC1100 Tablet PC. The pen always worked till ubuntu hardy due to the xorg 7.3 update..

Thanks in advance

same here 
unable to make

help

---

### Post by wasme on 2008-08-04
I finally found the solution to my problem with a wacom tablet on hardy, and figured it may help one or two others here:

I did all the various stuff (edit xorg.conf, compile wacom drivers from source, etc. etc.) and it still didn't work. It came down to this line in the Xorg.0.log file:

pad Wacom X driver can't grab event device, errno=1022

Seems something else was occupying the wacom device. I plugged the tablet into a different computer were it worked right away, and after doing a process-by-process comparison of what was running on the two I eventually tracked down the offender to a daemon called 'mouseemu'. After I uninstalled mouseemu my tablet worked perfectly.

So anyone who's tried everything and their tablet still doesn't work should maybe look to see if mouseemu is running and try disabling it and restarting X.

---

### Post by cherok on 2008-08-05
Hi folks, 

I'm a desperate WACOM wannabe like everyone else.  I made it to step 13 where the code below was to be inserted.

```
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

And received this message:
```
No such file or directory
```

I continued throughout, rebooted and noticed no difference in my WACOM.  Initially it operated as the touch pad would.

I have a Bamboo (original) and a HP Pavilion DV2000 (DV2404ca)

Thanks in advance!

---

### Post by carloslosgrande on 2008-08-06
[FONT="Comic Sans MS"][COLOR="Blue"]Hi Necko, great job. Thanks.

I just got a Wacom Intuos3.

Step 13 gave me the same error as others are getting.
I also got an error at step 18
*sudo ./uninstall - command not found*
and
[I]sudo make install - ***no rule to make target 'install'.  stop.
[/I]
Lost all sound during the xorg setup.

Everything seems fine after reboot.

Now I need to setup the pen and tablet buttons. Any ideas on how I can do this?[/COLOR][/FONT]

---

### Post by Skimmer on 2008-08-08
**@Ronalddog**: See instructions below

**@Rusty Spork**:
For your xorg.conf file, on each of the three lines that read:
```

#       Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

```
  try uncommenting each by removing the front hash so it looks like:
```

        Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY

```
Hope this helps!
-SK

---

### Post by cainmark on 2008-08-10
[QUOTE=neko18;4785779]**[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

These are the steps I took to make my Wacom Bamboo Fun work in Ubuntu 8.04 Hardy. These instructions should work for most Wacom tablets.


Thank you!  Mine had been halfway working until I got an update that affected my nvidia video card and all the wacom stuff in my xorg.conf dissapeared.  Your post finally helped me to get both working correctly!

---

### Post by Pokkulompus on 2008-08-14
Hi,

I'm an graphic artist, just got an Ubuntu, and since my Wacom hasnt worked. So, yesterday i followed these steps and it did not help, the pencil only moves when i press it against tablet, so i cant click or draw with pen.

ls -l /dev/input returned me:

```
drwxr-xr-x 2 root root    140 2008-08-14 16:19 by-id
drwxr-xr-x 2 root root    200 2008-08-14 16:19 by-path
crw-rw---- 1 root root 13, 64 2008-08-14 16:19 event0
crw-rw---- 1 root root 13, 65 2008-08-14 16:19 event1
crw-rw---- 1 root root 13, 66 2008-08-14 16:19 event2
crw-rw---- 1 root root 13, 67 2008-08-14 16:19 event3
crw-rw---- 1 root root 13, 68 2008-08-14 16:19 event4
crw-rw---- 1 root root 13, 69 2008-08-14 16:19 event5
crw-rw---- 1 root root 13, 70 2008-08-14 16:19 event6
crw-rw---- 1 root root 13, 71 2008-08-14 16:19 event7
crw-rw---- 1 root root 13, 72 2008-08-14 16:19 event8
crw-rw---- 1 root root 13, 63 2008-08-14 16:19 mice
crw-rw---- 1 root root 13, 32 2008-08-14 16:19 mouse0
crw-rw---- 1 root root 13, 33 2008-08-14 16:19 mouse1
crw-rw---- 1 root root 13, 34 2008-08-14 16:19 mouse2
lrwxrwxrwx 1 root root      6 2008-08-14 16:19 tablet-intuos3-6x8 -> event8
lrwxrwxrwx 1 root root      6 2008-08-14 16:19 wacom -> event8
```

I would be glad if someone helped me with this, i would not like to return to using Windows! :(

---

### Post by viou on 2008-08-14
hi everyone, like a lot of people, i had ubuntu a week ago, and i've been trying to configure my wacom tablet for 3 days, nothing works at all, the tablet has been recognize at once, but i can't have pressure, i've been looking in the thread and nothing i tried worked, i'm sorry if didn't see something in the thread that was my solution!

well, here is my xorg.conf, i'm pretty sure it's okey, if it isn't i'm the biggest moron on earth because i've been modifying it for days:
```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg


Section "Module"
    Load           "glx"
    Load           "wacom"
EndSection



Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbVariant"    "oss"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  #Option        "Device"        "/dev/ttyS0"          # Tablette SERIE
  Option        "Device"        "/dev/input/event7"    # Tablette USB
  Option        "Type"          "stylus"              # Stylet pointe ecriture
  Option        "USB"           "on"                  # Tablette USB
  Option        "Mode"          "absolute"            # Position sur la tablette
  Option        "ForceDevice"  "ISDV4"                # Tablet PC ONLY
  #Option        "HistorySize"  "64"                   # Taille buffer
  Option         "Tilt"         "on"                  # Inclinaison
  #Option         "TiltInvert"   "on"                  # Invertion de l'inclinaison
  Option         "Threshold"     "10"                   # sensibilité à la pression
  
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  #Option        "Device"        "/dev/ttyS0"           # Tablette SERIE
  Option        "Device"        "/dev/input/event7"    # Tablette USB
  Option        "Type"          "eraser"              # stylet pointe gomme
  Option        "USB"           "on"                  # Tablette USB
  Option        "Mode"          "absolute"            # Position sur la tablette
  Option        "ForceDevice"  "ISDV4"                # Tablet PC ONLY
  #Option        "HistorySize"  "64"                   # Taille buffer
  Option         "Tilt"         "on"                  # Inclinaison
  #Option         "TiltInvert"   "on"                  # Invertion de l'inclinaison
  Option         "Threshold"     "5"                   # sensibilité à la pression
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  #Option        "Device"        "/dev/ttyS0"           # Tablette SERIE
  Option        "Device"        "/dev/input/event7"    # Tablette USB
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # Tablette USB
  Option        "Mode"          "absolute"            # Position sur la tablette
  Option        "ForceDevice"  "ISDV4"               # Tablet PC ONLY
  #Option        "HistorySize"  "64"                  # Taille buffer
EndSection



Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "NVIDIA GeForce 7 Series"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
    Vendorname    "NVIDIA"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic CRT Display"
    Modelname    "Monitor 1600x1200"
    Horizsync    31.5-107.5
    Vertrefresh    50-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    2048    1536
        Modes        "1600x1200@85"    "1792x1344@75"    "1600x1200@70"    "1792x1344@60"    "1600x1200@75"    "1856x1392@60"    "1600x1200@60"    "1920x1440@60"    "1600x1200@65"    "2048x1536@60"    "1400x1050@75"    "1400x1050@60"    "1280x960@75"    "1280x1024@60"    "1280x1024@85"    "1280x960@85"    "1280x960@60"    "1280x1024@75"    "1152x864@75"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection
Section "device" #  
    Identifier    "device1"
    Boardname    "NVIDIA GeForce 7 Series"
    Busid        "PCI:1:0:0"
    Driver        "nv"
    Screen    1
    Vendorname    "NVIDIA"
EndSection
Section "screen" #  
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
    SubSection "Display"
        Depth    24
        Modes        "1600x1200@65"    "1600x1200@60"    "1400x1050@60"    "1280x960@75"    "1280x1024@60"    "1280x960@60"    "1280x1024@75"    "1152x864@75"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection
Section "monitor" #  
    Identifier    "monitor1"
    Vendorname    "Generic CRT Display"
    Modelname    "Monitor 1280x1024"
    Horizsync    31.5-81.0
    Vertrefresh    50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection



Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice   "Generic Keyboard"
    InputDevice   "Configured Mouse"
    InputDevice   "stylus" "SendCoreEvents"
    InputDevice   "eraser" "SendCoreEvents"
    InputDevice   "cursor" "SendCoreEvents"

        
EndSection


Section "Files"
EndSection



```

then i noticed that the stylus eraser was totally missing from the devices:

```
vio@ubuntu:~$ xsetwacom list dev
vio@ubuntu:~$ xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               extension
Configured Mouse               extension

```

i have a graphire2 and ubuntu hardy heron
...i don't think i have to say something much, tell me, hope you'll have a clue and that i did a stupid thing ^___^

ps:: i'm french, it would be the reason why i say things that means nothing

---

### Post by markkupaakkonen on 2008-08-14
Ijust installed my new Wacom intuos3! 
Thanks a lot! Works fine.

---

### Post by mariapilar on 2008-08-14
Please help! i have my brand new wacom bamboo fun and only works in windows!!:(
I updated my hardy and followed your instructions...nooo way, i can't make it work, i got this error message:

aripi@lamaquinola:~$ sudo make install 
make: *** No hay ninguna regla para construir el objetivo `install'.  Alto. 
maripi@lamaquinola:~$ cd .. 
maripi@lamaquinola:/home$ cp /etc/X11/xorg.conf . 
cp: no se puede crear el fichero regular «./xorg.conf»: Permiso denegado 
maripi@lamaquinola:/home$ gksudo gedit /etc/X11/xorg.conf 
maripi@lamaquinola:/home$ cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r` 
cp: no se puede crear el fichero regular «wacom.ko.2.6.24-19-generic»: Permiso denegado 
maripi@lamaquinola:/home$ sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 


What is going on???

TKS:(

---

### Post by umor on 2008-08-15
Hi, we got "Bamboo One" working at the first attempt within 15 mins without understanding what we were doing thanks to your outstanding guide!! Cheers from Austria, U&L

---

### Post by Maduroutmb on 2008-08-15
It worked for me.  However, this took quite a while because I had the Wacom drivers installed via Snyaptic.  I finally tried the guide again after removing these pakcages (5th time's the charm, eh?).  This leads me to the following point, which will probably help the people who are as thick-headed as I am:

Word of Warning:

The Xorg.conf modifications will screw up your X server if you have these packages installed.  Remove them before you follow this guide.

Great guide and thanks again for posting it/ following up on questions.  This sort of work allows Linux to overcome the initial obstacles to becoming a real market player.  People who understand technical stuff  (Neko) helping non-technical early adopters (me) is a huge step for the FOSS movement.  Sorry for a paragraph of gratitude, but I really feel that what you're doing matters.

---

### Post by quinnten83 on 2008-08-16
> **mariapilar said:**
> Please help! i have my brand new wacom bamboo fun and only works in windows!!:(
I updated my hardy and followed your instructions...nooo way, i can't make it work, i got this error message:

aripi@lamaquinola:~$ sudo make install 
make: *** No hay ninguna regla para construir el objetivo `install'.  Alto. 
maripi@lamaquinola:~$ cd .. 
maripi@lamaquinola:/home$ cp /etc/X11/xorg.conf . 
cp: no se puede crear el fichero regular «./xorg.conf»: Permiso denegado 
maripi@lamaquinola:/home$ gksudo gedit /etc/X11/xorg.conf 
maripi@lamaquinola:/home$ cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r` 
cp: no se puede crear el fichero regular «wacom.ko.2.6.24-19-generic»: Permiso denegado 
maripi@lamaquinola:/home$ sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 


What is going on???

TKS:(

There is a lot of permiso denegado in there. I think you should use sudo when performing the tasks.

---

### Post by quinnten83 on 2008-08-16
I hate the fact though that with every new kernel update, I have to perform the installation again. When is Ubuntu going to build support for these tablets into the kernel?

---

### Post by gaussian on 2008-08-16
> **quinnten83 said:**
> I hate the fact though that with every new kernel update, I have to perform the installation again. When is Ubuntu going to build support for these tablets into the kernel?

In Intrepid Alpha 8.10 Bamboo Fun at least works almost out of the box. Only thing I had to do was to edit xorg.conf

---

### Post by Minipalmer on 2008-08-17
Excellent guide! Just installed Ubuntu and this *almost* got my Bamboo working.

I hope I haven't missed this in the thread, but I've tried searching all I could.

The guide does not allow the buttons on the stylus of my bamboo to work. Has anyone solved this? Or a way to configure the actions of the buttons on top of the touch pad?

Thanks for all the work put into this thread.

---

### Post by johnnyart on 2008-08-17
I love you
No, seriously, I can't thank you enough

---

### Post by carloslosgrande on 2008-08-17
[FONT="Comic Sans MS"]Is anyone else having problems with the cursor movement and panels?
eg. I use the stylus all the time but my cursor sometimes gets stuck, the only thing which will move it is the mouse.
And, the panels have begun behaving oddly - Current apps don't show, cancelled apps do. Active panel highlight gets stuck on a single panel square.
OpenOffice doesn't like the copy and paste from a browser using the stylus, it often shuts during this action and the auto recover has a fit too - shuts down.

These problems have begun since installing wacom. I know these are minor but my experience is that minor becomes major.[/FONT]

---

### Post by mella2000 on 2008-08-18
It doesn't work for me. Whic is the error?

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
        InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
	InputDevice	"Synaptics Touchpad"
EndSection

ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-08-18 08:27 by-path
crw-rw---- 1 root root 13, 64 2008-08-18 08:27 event0
crw-rw---- 1 root root 13, 65 2008-08-18 08:27 event1
crw-rw---- 1 root root 13, 66 2008-08-18 08:27 event2
crw-rw---- 1 root root 13, 67 2008-08-18 08:27 event3
crw-rw---- 1 root root 13, 68 2008-08-18 08:27 event4
crw-rw---- 1 root root 13, 69 2008-08-18 08:27 event5
crw-rw---- 1 root root 13, 70 2008-08-18 08:27 event6
crw-rw---- 1 root root 13, 71 2008-08-18 08:27 event7
crw-rw---- 1 root root 13, 72 2008-08-18 08:27 event8
crw-rw---- 1 root root 13, 63 2008-08-18 10:26 mice
crw-rw---- 1 root root 13, 32 2008-08-18 10:26 mouse0
crw-rw---- 1 root root 13, 33 2008-08-18 08:27 mouse1

---

### Post by Lometari on 2008-08-18
Thank you SO much Neko!!!! I set up my new Bamboo in no time on my Hp nx6325, a VERY problematic laptop. The only downside is I have to restart X to  make it work whenever I unplug it, but I don't think it's a problem. I'll go configure GIMP now. Again thanks a lot.

---

### Post by Eastisle on 2008-08-18
> **mella2000 said:**
> 

ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-08-18 08:27 by-path
crw-rw---- 1 root root 13, 64 2008-08-18 08:27 event0
crw-rw---- 1 root root 13, 65 2008-08-18 08:27 event1
crw-rw---- 1 root root 13, 66 2008-08-18 08:27 event2
crw-rw---- 1 root root 13, 67 2008-08-18 08:27 event3
crw-rw---- 1 root root 13, 68 2008-08-18 08:27 event4
crw-rw---- 1 root root 13, 69 2008-08-18 08:27 event5
crw-rw---- 1 root root 13, 70 2008-08-18 08:27 event6
crw-rw---- 1 root root 13, 71 2008-08-18 08:27 event7
crw-rw---- 1 root root 13, 72 2008-08-18 08:27 event8
crw-rw---- 1 root root 13, 63 2008-08-18 10:26 mice
crw-rw---- 1 root root 13, 32 2008-08-18 10:26 mouse0
crw-rw---- 1 root root 13, 33 2008-08-18 08:27 mouse1

The xorg.conf that you posted looks the same as mine.
My ls -l /dev/input shows this: 

```
ls -l /dev/input
total 0
drwxr-xr-x 2 root root    100 2008-08-18 15:24 by-id
drwxr-xr-x 2 root root    120 2008-08-18 15:24 by-path
crw-rw---- 1 root root 13, 64 2008-08-18 15:24 event0
crw-rw---- 1 root root 13, 65 2008-08-18 15:24 event1
crw-rw---- 1 root root 13, 66 2008-08-18 15:24 event2
crw-rw---- 1 root root 13, 67 2008-08-18 15:24 event3
crw-rw---- 1 root root 13, 68 2008-08-18 15:24 event4
crw-rw---- 1 root root 13, 69 2008-08-18 15:24 event5
crw-rw---- 1 root root 13, 63 2008-08-18 15:23 mice
crw-rw---- 1 root root 13, 32 2008-08-18 15:23 mouse0
crw-rw---- 1 root root 13, 33 2008-08-18 15:24 mouse1
lrwxrwxrwx 1 root root      6 2008-08-18 15:24 tablet-bamboo -> event5
lrwxrwxrwx 1 root root      6 2008-08-18 15:24 wacom -> event5

``` 
Maybe this can give you a hint in the right direction?

---

### Post by shameless on 2008-08-20
Hey, I tried installing my tablet using your first tutorial, but when that didn't work, I tried using the patch install, which gave me an error at step 13 the second time around, which was 

philip@RINGWORLD-DOCK9:~/wacom/linuxwacom-0.8.0-3$ sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory


The output of the two commands you asked for are attached. 

You are a hero for posting this in the first place, you'll be my savior from Vista if you can help me get mine working too. This tablet is a USB (I think) connection screen, and this is my last hope before having to downgrade from Linux again, I need it for classes. 

Also, I should note that I'm rather new to Linux, so a lot of this is flying over my head, but I can follow the directions I'm given.

Thanks in advance

---

### Post by Loaded.len on 2008-08-20
I can confirm that "cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory" I just followed the steps and got the same thing.

I'm trying to install my ancient Wacom serial PenPartner.  Tablet's getting power and sees the stylus, but no cursor movement.

After that error, I continued, but to no avail.  So I backtracked to square one.

---

### Post by Loaded.len on 2008-08-20
Ok, I got mine working.  Minor oversight on my part. 

I downlaoded the latest package from the Linux Wacom Project and compiled it.  It all went fine, but when I ran ```
wacdump /dev/ttyS0
``` I got nothing.  Looked in /etc/X11/xorg.conf and found that the default entries that the build put there all said **"Device"    "/dev/input/wacom"**  But ```
ls -l /dev/input
``` didn't show wacom.  I changed all the Devices to **/dev/ttyS0** in xorg.conf then restarted X and it works now.  Just have to fine tune it.

---

### Post by Draw2much on 2008-08-22
I just wanted to say thanks for getting my medium Bamboo tablet to work. The first time I rebooted it acted just like a mouse and I admit I was a bit worried. However, the second reboot mysteriously fixed this and now my Wacom works just like it did in Windows. Hurrah! You're a genius! :KS

---

### Post by SkippoGuangiacomo on 2008-08-24
Hello, my Bamboo tablet works very fine. However I get a very funny error due to the installation of it ( see this link for the whole story: [http://ubuntuforums.org/showthread.php?p=5656852#post5656852](http://ubuntuforums.org/showthread.php?p=5656852#post5656852) )
which is that when I'm using a command line (not just the console though, but the command line in matlab or kate) I get logged out anytime i make a mistake (i.e., if I open kate, i click on the terminal window and push the arrow pointing downward i get logged out of kubuntu).

Any clues about what could be going on?
Thx in advance

p.s.: if i make the same mistake in the console I do not get logged out.

---

### Post by shameless on 2008-08-24
Ok, after I deleted the whole folder and started over from step one, it works! The problem is that the calibration is wrong, it's varible depending on where it is on the screen (upper left corner is dead on, but moving down causes it to get off by going down too much, going right causes it to get off to the right too much, etc) I tried doing the xidump stylus to get the data, but when I did the command, I got:

InputDevice: stylus
Valuators: Absolute   ID: Unreported  Serial Number: Unreported

             x-axis    y-axis   pressure   x-tilt    y-tilt     wheel
     data:
      min:  +00000    +00000    +00000    -00064    -00064    +00000
      max:  +01280    +00800    +00255    +00063    +00063    +01023
      res:  +00050    +00050    +00001    +00001    +00001    +00001


Proximity:
    Focus:
  Buttons:
     Keys:

I can't get anything for the data line, and I'm not sure how to manually calibrate the stylus. From the output, it seems like the pressure sensitivity works properly, but I havne't anything to test with (yet). Help, please? This is saving me from vista if this works

---

### Post by petertheclock on 2008-08-25
A sincere thanks for a clear and concise set of instructions which do exactly what it says on the tin.  I now have a working Wacom - Gimp here I come !:)

Peter

---

### Post by Jack1989 on 2008-08-25
Hi, after the reboot the screen driver was gone and the resolution was 800 x 600, which is wrong. How ever I fixed it with your instructions so the screen is working again now. But the touch screen is not working. I didn't got any errors but maybe it is a command that doesn't executed.

The outputs is the backup file, I think, but maybe you can see whats wrong or tell me to repeat some of the steps.

Thank you for a great guide and all support!

EDIT:
I repeated all the steps again without any errors and rebooted the laptop (Hp tx 2020). Everything worked but not the Wacom. I used this command to check if it's initialized: ls -l /dev/input but it isn't there, only mice, mouse, and event0...

I've changing the xorg.conf file a couple of times and then rebooted but nothing happens.

What can be wrong? How can I troubleshoot by my self?

// Jack

---

### Post by ceti331 on 2008-08-27
Anyone get this to work with a cintiq 12wx ?
lsusb is recognizing that i've got a wacom thing plugged in, but i get no cursor movement. nothing wacom related shows up on ls -l /dev/input
A regular intuous pad *does* work though.

---

### Post by Ictinike on 2008-08-28
> **ceti331 said:**
> Anyone get this to work with a cintiq 12wx ?
lsusb is recognizing that i've got a wacom thing plugged in, but i get no cursor movement. nothing wacom related shows up on ls -l /dev/input
A regular intuous pad *does* work though.

Having an identical problem with the Bamboo. It was working 2 weeks ago.

---

### Post by robnolten on 2008-08-30
happy happy joy joy.

I say: thank you, mister! works like a charm!

---

### Post by Neo2.0 on 2008-08-30
Thanks for the great guide!

On Hardy, I got my Graphire4 working almost completely. The only thing that keeps bothering me is the following behaviour:

When I do 1 click with any of the 2 pad buttons OR move the scroll wheel by one step in one of the two directions, the expected reaction happens. BUT: when I do any more of these actions, the mouse pointer jumps to the top left corner.

This renders the scroll-wheel unusable for scrolling.

Has anyone bumped into this kind of problem?
Thanks for any comments!

René

---

### Post by BinaryDigit on 2008-08-31
This is fantastic!!! I'm so excited!  I have the Bamboo Fun as well and it works great :) Thank you so much for posting this!

---

### Post by yoma819 on 2008-09-01
i have a toshiba m200 tablet does anyone know of any guides for that?
thanks 
--yoma

---

### Post by TRON84 on 2008-09-01
THANK YOU!

Good guide, easy and straight forward! worked after step 19!

/TRON84

---

### Post by tempo500 on 2008-09-03
i got myself a cintiq 20wsx vers5, compiled latest wacom driver with success, buttons on pen and screen seem to work but no cursor movement.  sudo wacdump -v /dev/input/wacom gives me full feedback - tooltype, x and y position, pressure etc...
xidump does not give me any feedback, - as far as i understand this prog, it reads the data out of the xorg...? which would tell me that something in the xorg is wrong...

[http://linuxwacom.sourceforge.net/index.php/howto/mouse1]("http://linuxwacom.sourceforge.net/index.php/howto/mouse1")

can someone translate this? does this apply to me? i am running ubuntu 8.04. thanks! phil

update:
i found out that the intuos3(another machine) and my tabletPC (wacom inside hp tx2000) don't report anything through wacdump just through xidump. - which is the exact opposite to the cintiq.... any ideas?

tail /var/log/messages
```
Sep  4 00:59:49 render kernel: [ 3166.157825] input: Wacom Cintiq 20WSX as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input20

```

more /proc/bus/input/devices
```
I: Bus=0003 Vendor=056a Product=00c5 Version=0108
N: Name="Wacom Cintiq 20WSX"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input20
U: Uniq=
H: Handlers=mouse1 event3 js0 
B: EV=1f
B: KEY=18ff 1f03ff 0 0 0 0
B: REL=100
B: ABS=1000f00017f
B: MSC=1

```

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Thu Jun  5 09:27:12 UTC 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice     "stylus"        "SendCoreEvents"
    InputDevice     "cursor"        "SendCoreEvents"
    InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "WAC Cintiq 20WSX"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1500"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60_0 +0+0"
    SubSection     "Display"
    Depth          24
    EndSubSection
EndSection

```

---

### Post by dorame on 2008-09-04
Thanks you for your advice.Good bye!

---

### Post by ridnout on 2008-09-05
Why aren't MOST listing their machines manufacturer and model?

I need help; this thread has jumped about without any real direction.  What gives?

I have a post and a rant.  No kinda freaking reply, link, or whatever.

Crap.

On to Debian Proper and learning again to do it yourself.

Ubuntu--Debian for dummies and no control offered by a real Debian System built from scratch.

Heck, I don't even know what alls inside this Quasi Distro!

It's Knoppix folks.  The stuff doesn't work to tough either!

Yup ranting, cause I got no help, and I aint gonna beg, just bash and rant!

A lack of aid is the best impetous for doing it your f'n self.

---

### Post by concord on 2008-09-05
> **neko18 said:**
> **[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

These are the steps I took to make my Wacom Bamboo Fun work in Ubuntu 8.04 Hardy. These instructions should work for most Wacom tablets.


I just got my Wacom Bamboo (MTE 450) today and had it up and running in less than 20 minutes using your handy "HOWTO".  Thank you so much!

I'm not an artist but this is how your help has affected me:

[http://www.concordsystems.com/images/before_ike.png]("http://www.concordsystems.com/images/before_ike.png")

Thanks again! \\:D/

---

### Post by tempo500 on 2008-09-06
cintiq 20wsx update

still no pleasure, ive been talking to wacom linux mailinglist, but up untill now, no solution came up. i dont know where to search for problems anymore. i started out with a fresh install, package update and wacom 8.0.3 compile. wacom gets recoginzed but i have to touch the monitor with the pen to move the cursor wacdump reports everything fine, pressure position etc. xidump does not work

```
 BUILD ENVIRONMENT:
>>>        architecture - x86_64-linux-gnu
>>>        linux kernel - yes 2.6.24
>>>   module versioning - no
>>>       kernel source - yes /lib/modules/2.6.24-19-generic/build
>>>      XFree86 source - no
>>>            Xorg SDK - yes /usr/include/xorg
>>>           XSERVER64 - yes
>>>            dlloader - yes
>>>                XLib - yes /usr/lib
>>>                 TCL - yes /usr/include/tcl
>>>                  TK - yes /usr/include/tcl
>>>             ncurses - yes
>>>
>>>   BUILD OPTIONS:
>>>             wacom.o - yes
>>>             wacdump - yes
>>>              xidump - yes
>>>         libwacomcfg - yes
>>>          libwacomxi - yes
>>>           xsetwacom - yes
>>>               hid.o - no
>>>          usbmouse.o - no
>>>             evdev.o - no
>>>          mousedev.o - no
>>>             input.o - no
>>>        wacom_drv.so - yes /usr/lib/xorg/modules/input
>>>         wacom_drv.o - no
>>>   wacom*_drv quirks - libc-wrapper tablet-screen-scaling 
>>> IsXExtensionPointer key-events dixScreenOrigins
>>> ----------------------------------------
>>>
>>> I: Bus=0003 Vendor=056a Product=00c5 Version=0108
>>> N: Name="Wacom Cintiq 20WSX"
>>> P: Phys=
>>> S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input8
>>> U: Uniq=
>>> H: Handlers=mouse2 event7
>>> B: EV=1f
>>> B: KEY=1cff 1f03ff 0 0 0 0
>>> B: REL=100
>>> B: ABS=1000f00017f
>>> B: MSC=1
```
```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/event7"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/event7"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/event7"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection

     InputDevice     "stylus"        "SendCoreEvents"
    InputDevice     "cursor"        "SendCoreEvents"
    InputDevice     "eraser"        "SendCoreEvents"

```

---

### Post by Jack the R on 2008-09-07
I'm trying to get the driver to work on an Asus R1e tablet pc.

Here's what I did - 

[Link](http://www.extinctionlevelevent.com/misc/linux/tablet/1st_try_.8.1-4.odt)

and the results of the commands neko18 requested at the end of his write up - 

[Link](http://www.extinctionlevelevent.com/misc/linux/tablet/1st_try_.8.1-4_output.odt)

---

### Post by bogamol on 2008-09-08
> **ridnout said:**
> Why aren't MOST listing their machines manufacturer and model?

I need help; this thread has jumped about without any real direction.  What gives?

I have a post and a rant.  No kinda freaking reply, link, or whatever.

Crap.

On to Debian Proper and learning again to do it yourself.

Ubuntu--Debian for dummies and no control offered by a real Debian System built from scratch.

Heck, I don't even know what alls inside this Quasi Distro!

It's Knoppix folks.  The stuff doesn't work to tough either!

Yup ranting, cause I got no help, and I aint gonna beg, just bash and rant!

**A lack of aid is the best impetous for doing it your f'n self.**

Hold on there, guy... Forgive me if I completely misunderstood your post, it is very chaotic, but as I understand, you are ranting at/about the people who don't understand Linux that are asking how to get it to work... If a person can't figure it out himself, he is likely to go back to what he knows works...Windows. With the device in question, the wacom bamboo, it works better in Windows anyway. The biggest thing that makes Linux better than the other 2 big OS is that it is community supported, and can be community edited. Don't be a jerk, because by doing so, you ruin the best part of Linux and continue to make it esoteric and unusable by the casual user.

---

### Post by Jack the R on 2008-09-08
Another try using an earlier driver with the Zappacky patch - 

[What I did](http://www.extinctionlevelevent.com/misc/linux/tablet/2nd_try_.8.1-4.odt)


and the results of the commands neko18 requested at the end of his write up - 

[Link](http://www.extinctionlevelevent.com/misc/linux/tablet/2nd_try_.8.1-4_output.odt)

I also don't have a /dev/input/wacom device. Should I?

---

### Post by jsherwood on 2008-09-09
THANKS, your method worked

---

### Post by beejunk on 2008-09-09
Well, I've been working on this for half the day now, but I don't seem to be getting anywhere.

I've run through the How To three times now, with no errors (or at least, nothing I recognize as errors) and still nothing, EXCEPT that, for whatever reason, the click-wheel on my tablet's mouse works.  And that's it, nothing else.  No stylus at all.  From what I can tell, I've set everything up correctly in GIMP and Inkscape, but I'm still getting no response (except for the mysterious wheel).  Here's my info:

Graphire 2 Tablet
Macbook Dual Core 2.0 ghz
Ubuntu 8.04

I've attached the two text files that the How To requests in order to identify problems.  If any of you can help, I'd be eternally greatful!  I have high hopes for using Ubuntu for graphic design, but I've got to get this working (and Gimp needs to get CMYK support one of these days, but that's another topic)

Also, I am very new at this, and all this command line stuff makes my head hurt.  I wish they could figure a way to do this through gnome.  Anyway, thanks again in advance.

---

### Post by Zatzum on 2008-09-12
Okay, I'm trying to install a brand-new Bamboo Fun. At step 19, when I rebooted, Ubuntu couldn't recognize my display anymore! I wasn't sure why it was so, and opened a terminal and put these in:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.wacom_modified
cp /home/USERNAME/wacom/xorg.conf /etc/X11/xorg.conf
reboot
```

I bet it wasn't the right thing to do... Anyway, now I'm stuck with 800x600 resolution - but tablet works, although only if you press it hard. The buttons work also.

There was a "configure" - option at the startup screen, when it told about problems with graphics, and I chose my lg flatron l1715s from the list, but still the resolution is small.

Any help would be appreciated. Sorry for not reading the 32 pages through, but with this resolution it's just... painful... I tried to use search at least.

Okay, I had a backup of my old xorg.conf file and returned to that one. Now the tablet works and resolution is fine, and I'm fine. I'll get back to this thing tomorrow, as it has taken me whole evening. I'm sure I can manage to find solution now that I can read without getting frustrated :)

Edit: Now it's working perfectly, after several hours of messing with my xorg.conf file and multiple reboots :) I'm happy :D

---

### Post by DuckDodgers on 2008-09-15
Hello,
     I'm still new to Ubuntu and linux, so I'm not sure if this is where this post should go.  Anyway I finally Got my Wacom Bamboo working perfectly with the help of this list... for a few hours.  Then randomly while I was using Gimp the tablet acted like my stylus was touching the pad when I was at hovering distance.  In other words I couldn't move the cursor around without functioning like I was clicking the mouse button.  It still has pressure sensitivity and everything like that, but it makes drawing nearly impossible.  Dose anybody know what's going on?

---

### Post by gerudobombshell on 2008-09-16
The mouse buttons work, but the mouse tracking is messed up!!! Help Please!!

[btw, is this thread too old?...]

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```


```
total 0
drwxr-xr-x 2 root root     80 2008-09-16 01:37 by-id
drwxr-xr-x 2 root root    160 2008-09-16 01:37 by-path
crw-rw---- 1 root root 13, 64 2008-09-16 01:35 event0
crw-rw---- 1 root root 13, 65 2008-09-16 01:35 event1
crw-rw---- 1 root root 13, 66 2008-09-16 01:37 event2
crw-rw---- 1 root root 13, 67 2008-09-16 01:35 event3
crw-rw---- 1 root root 13, 68 2008-09-16 01:35 event4
crw-rw---- 1 root root 13, 69 2008-09-16 01:37 event5
crw-rw---- 1 root root 13, 70 2008-09-16 01:35 event6
crw-rw---- 1 root root 13, 63 2008-09-15 18:34 mice
crw-rw---- 1 root root 13, 32 2008-09-15 18:34 mouse0
crw-rw---- 1 root root 13, 33 2008-09-16 01:37 mouse1
crw-rw---- 1 root root 13, 34 2008-09-16 01:37 mouse2
lrwxrwxrwx 1 root root      6 2008-09-16 01:37 tablet-intuos3-9x12 -> event2
lrwxrwxrwx 1 root root      6 2008-09-16 01:37 wacom -> event2
```

---

### Post by Kimbo66 on 2008-09-16
> **neko18 said:**
> **[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

These are the steps I took to make my Wacom Bamboo Fun work in Ubuntu 8.04 Hardy. 

Just wanted to say Thank You for this great How-To. Got my brand new Bamboo MTE-450 to work perfectly on my ASUS M51Sn Laptop after following your post.

---

### Post by EhrinJ on 2008-09-18
I'm stuck on the fourth step :( I feel like such a noob right now.

Anyway, I'm unable to install the package 'build-essential' due to a whole mess of dependency errors. Mostly related to G++ (>= 4:4.2.1.1)

Any other way I could handle the tablet fix without that package? Like an alternate package with the same uses?

---

### Post by brandon88tube on 2008-09-20
Ok, I have scoured the forums and google, but cannot figure out how to run wacomcpl. I don't even know if its installed. If anyone could help I would greatly appreciate it.

---

### Post by neoanderthal on 2008-09-20
I'm reporting success with this setup - Lenovo Thinkpad T61, Kubuntu 8.04 (x86), KDE 4.1, Bamboo Fun (larger bamboo). Works fine as a pointer, etc. My induction mouse works fine as well. I need to fiddle with the config tools a bit to get the eraser to actually 'erase', but it works fine.

Very nice, detailed step-by-step. Thank you so much :) Now I can go forward with my planned purchase of a TZ25xx :)

---

### Post by neoanderthal on 2008-09-20
> **brandon88tube said:**
> Ok, I have scoured the forums and google, but cannot figure out how to run wacomcpl. I don't even know if its installed. If anyone could help I would greatly appreciate it.

have you tried the instructions for building the tool that were on the first page of this thread? [http://ubuntuforums.org/showpost.php?p=4797903&postcount=10]("http://ubuntuforums.org/showpost.php?p=4797903&postcount=10")

my copy of wacomcpl was installed under /usr/local/bin

did you get an error message when you did the 'sudo make install'?

---

### Post by brandon88tube on 2008-09-21
When I type in sudo make install I get this error make: *** No rule to make target `install'.  Stop. Then if I try wacomcpl, it says command not found probably because the above happened.

---

### Post by impact on 2008-09-22
What is needed to get the FORWARD and BACK buttons on the Bamboo pad working as FORWARD and BACK in Firefox? I tried to set them up as ALT+LEFT ARROW, ALT+RIGHT ARROW, but that did not work.

---

### Post by larsgj on 2008-09-23
Thanks everyone for this tutorial :)

Now the Wacom Bamboo is working flawless in GIMP , and I got a crash course in app. building - nice.

Hopefully native support for tablets will improve in coming releases.

Setting up GIMP: preferences->input devices->configure extended input devices->  all tablet functions set to "screen".

Wacom Bamboo standard edition
GIMP 2.4.5
Ubuntu 8.04 (x86)

edit:  yehaaa  Inkscape (0.46) also works perfectly :)  -still haven't gotten this one to behave in windoze

---

### Post by beejunk on 2008-09-23
Well, just to follow up on my previous post concerning Wacom and Ubuntu on the Macbook (which, sadly, got no responses):

I looked through the Apple Users forum for a bit, and it looks like the linux Wacom drivers are well and truly broke on the Macbook.  Hopefully one day this will get fixed.  This does, for the moment, destroy my dreams of designing entirely in open-source, but what can you do?

However, I did get the tablet to work perfectly on my girlfriend's computer (running Ubuntu 8.04) using this How-To, so I do want to say thank you for that!  

If anyone has any more info on Wacom drivers and Ubuntu on Macbooks, let me know.

---

### Post by EhrinJ on 2008-09-24
All it took to get it working was a complete re-install. Yay.

My tablet's working, calibration is dead-on

Although there's no pressure sensetivity, I'm pretty sure I've seen others in this threat with the same problem, so I'll try the fixes that neko provided them.

Thanks, big time.

---

### Post by beejunk on 2008-09-24
Success!  As it turns out, for whatever reason, mouseemu was screwing with the Wacom installation.  So, for you Macbooks users with problems with wacom:

Use synaptic to remove mouseemu.  I did this, and after logging out and then back in, the tablet worked great!

---

### Post by positron469 on 2008-09-25
Hi! My wacom volito2 is not working. I followed all steps. It works as a mouse after replugging, but is not detected when system starts.

---

### Post by positron469 on 2008-09-25
And this is output from my comp.

---

### Post by brandon88tube on 2008-09-28
Ok, I posted on here a week ago about a problem and no one really replied. Now for some reason my Wacom Graphire4 is not working again. This is really annoying because I don't know how to fix it. If anyone could help, please do so.

---

### Post by jcm1979 on 2008-09-28
Hi.  I'm a linux newbies and I'm running into a problem in step #7.  After I run "./configure --enable-wacom" I receive a warning in the string of text that appears after I run the command.  

*** WARNING:
*** Unable to guess kernel source directory
***   Looked at /lib/modules/2.6.24-21-generic/source, /lib/modules/2.6.24-21-generic/build,
***     /usr/src/linux, /usr/src/linux-2.6.24-21-generic, /usr/src/linux-2.4, and
***     /usr/src/linux-2.6
*** Kernel modules will not be built
***

Once "./configure --enable-wacom" is done running I don't end up with the file "wacom.ko" in any of the src directories.  Can someone please help me work through this issue?

This tutorial worked once before, but being a linux newbie I had to reinstall 8.04 and it doesn't seem to work this time around

Thanks

---

### Post by asdfoo on 2008-09-29
I'm using 8.04 - I did not follow this tutorial, but installed the two wacom packages using apt-get and my tablet seems to work.  Only it appears to not be configured properly?  I can only use part of the tablet, maybe a config issue?

*edit* maybe something to do with twinview, using one monitor it works fine.


Maybe this tutorial should be retired as old and unnecessary to avoid people breaking their setup or doing things unnecessarily?

---

### Post by lukyluke on 2008-09-30
just wanted to point you out to a post that seems to indicate that there is a bug in the wacom driver...
Maybe this is not the case but please take a look at 
[http://ubuntuforums.org/showthread.php?p=5798711]("http://ubuntuforums.org/showthread.php?p=5798711").

I made some testing and the bug is only present with the tablet attached and configured as you   describe in this HOWTO.

Regards

---

### Post by JoeLosco on 2008-09-30
For some reason, I'm thinking that Nvidia Twinview and Wacom are having issues with each other..  At least I am finding that to be a common thread for those having trouble in their xorg file as well as my own.  

I have the same issue in that it shows up in wacdump completely fine but does not show up in xidump -l or xsetwacom at all or in programs such as Gimp in the Extended devices area (no cursor, stylus, or erasor available)

Also the pad works in that I can move the cursor around while hovering and clicking works in Part of the screen.  What I mean by that is while using the stylus on full extents of the pad it only moves on parts of the screen, even with the relative statement.  

My xorg.conf file is listed below in case I'm doing something stupid.  Also I've tried with both the ForceDevice "ISDV4" remmed out as well as not.  

If anyone has a solution, I'd be very appreciative.  Thanks

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier	"stylus"
    Driver		"wacom"
    Option		"Device"	"/dev/input/wacom"
    Option		"Type"		"stylus"
    Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
    Option		"USB"		"on"
    Option		"PressCurve"	"50,0,100,50"
EndSection

Section "InputDevice"
    Identifier	"eraser"
    Driver		"wacom"
    Option		"Device"	"/dev/input/wacom"
    Option		"Type"		"eraser"
    Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
    Option		"USB"		"on"
EndSection

Section "InputDevice"
    Identifier	"cursor"
    Driver		"wacom"
    Option		"Device"	"/dev/input/wacom"
    Option		"Type"		"cursor"
    Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
    Option		"Mode"		"relative"
    Option		"USB"		"on"
EndSection

Section "InputDevice"
    Identifier	"pad"
    Driver		"wacom"
    Option		"Device"	"/dev/input/wacom"
    Option		"Type"		"pad"
    Option		"USB"		"on"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
EndSection


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "cursor"	"SendCoreEvents"
    InputDevice     "stylus"	"SendCoreEvents"
    InputDevice     "eraser"	"SendCoreEvents"
    InputDevice	"pad"
EndSection

Section "Module"
    Load           "glx"
EndSection


```

---

### Post by jonspringall on 2008-09-30
Joe's issue, and the one described in the thread that he has linked to, sound very much like my own. However, my laptop uses an integrated intel graphics chip.

I have described my problems, in replying to another thread, at [http://ubuntuforums.org/showthread.php?t=923486]("http://ubuntuforums.org/showthread.php?t=923486") 

I would love to get my Bamboo One working without feeling like I've reverted to Windows 95! With the Wacom tablet disabled Ubuntu is certainly my favourite operating system.

---

### Post by juanfran27 on 2008-10-01
I have just one question. Will the tablet work as it does on Windows? You know, not needing to touch the tablet with the pen in order to make the cursor move (hovering it's called, i beleive) and personalizing buttons.

---

### Post by Pauan on 2008-10-01
> **juanfran27 said:**
> I have just one question. Will the tablet work as it does on Windows? You know, not needing to touch the tablet with the pen in order to make the cursor move (hovering it's called, i beleive) and personalizing buttons.
Yes (it does for me), though I have not tried personalizing the buttons, the hovering and round touch-scroll both work fine for me. It seems to work just as in Windows, albeit with some extra tweaks to get it working.

---

### Post by juanfran27 on 2008-10-01
Excelent, thanks. Are those tweks in this thread? I haven't gone through it all.

---

### Post by Pauan on 2008-10-01
> **juanfran27 said:**
> Excelent, thanks. Are those tweks in this thread? I haven't gone through it all.
They are. I got mine working by following the directions in the first post. You may not be as lucky, in which case additional tweaks are required.

---

### Post by shaft350x on 2008-10-01
So for some odd reason I can't thank you for this.  So Thanks!  Followed the instructions, worked great.

---

### Post by whizbaby on 2008-10-02
I didnt read the whole thread (though its not like I didnt read it at all :)), so I dont know if someone else experienced the same problems. Anyways, heres the solution, too.

After setting up a bamboo one tablet on hardy 8.04.1 I did not get to the login screen, only giving me a weird popup window I've never seen before, saying 'having problems with the login manager, trying another..' or similar. So I
1)switched to console (ctrl-alt-f1) and stopped gdm
```
sudo /etc/init.d/gdm stop
```
this seemed to hang somehow (after 2 minutes it was still saying '***stopping gnome display manager')
, so I went back to ctrl-alt-f7 and clicked the 'OK' button on the weird popup. Then going back to ctrl-alt-f1 I could see gdm was stopped now.
2)make your ```
Inputdevice "pad"
``` line in /etc/X11/xorg.conf look like this
```
Inputdevice "pad"  "AlwaysCore"
```
(the others, stylus cursor and eraser, have "SendCoreEvents").
I fiddled around for a few hours until I found what to do.
3)```
sudo /etc/init.d/gdm start
```
should take you back to a working login manager.
p.s.:
The guide worked flawless for bamboo one in gutsy. Only thing is(every version), one line cant be copy-pasted because you are in the wrong directory at that time, but I guess nobody is having a problem with that. I am talking about this line 
```
sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
Because one cd's to linuxwacom directory before it says 'file not found' when you copy-paste the line.
(for all those blind-copy-pasters like me :))

---

### Post by ninothedog on 2008-10-02
Thank you very much. The instructions didn't work for me the first time but looking to see what I did wrong I found it. I needed to uncomment the lines for tablet PC only in the xorg.conf lines - you might want to spell this out explicitly in the instructions in case another dummy like me comes along. I only needed to remove the comments and restart. Didn't need to follow the remaining steps again. - Pad working great now on Lenovo ThinkPad X61. Thanks.

---

### Post by jgoppert on 2008-10-04
Using Bamboo MTE-450 on Ubuntu Hardy 8.04, Lenovo X61t.
Had a 3 hour glitch that I finally resolved with the help of another forum.I suggest you add this to the step by step instructions.

Quoting from: [http://www.feigetech.com/?page_id=4](http://www.feigetech.com/?page_id=4)
h
Make SURE to change the following line to your specific pointer device. Failure to do so will cause hair loss and dementia, as it’s impossible to get the Bamboo to work without this change. Trust me, I had a friend who…

Change from:

Option         "Device" "/dev/input/mice"

To:

Option         "Device" "/dev/input/mouse0"

---

### Post by pooyaplus on 2008-10-04
Hi all,
I finally managed to get the things working. It was not that easy, to tell the truth, most of the packages recommended in the instructions are old. I, personally suggest to download the packages manually and not from the links. 

Anyways, have you guys managed to get the right click working? I just can hover around and work with a single object with no right click option at all; i.e. I can not move objects when I select multiple objects on my desktop.

It seems that the wacom can not be used in full features under linux.

---

### Post by psmaster on 2008-10-04
Excellent! Thank you very much! My Bamboo Fun is now working perfectly!

---

### Post by HanaD on 2008-10-14
Hi!
after doing all this i am grateful that at least somethings started working, though i wanted to ask if it was possible to right click with that stylus?
I mean i can use the stylus to move the cursor around the screen but cannot right click anything, 
is it that i am missing something ?



I do not have the touchpad and below is the output of /etc/X11/xorg.conf & ls -l /dev/input. Also in my tablet the command lsusb | grep -i wacom does not show anything, it just returns me ot prompt again.

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

hana@hana-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x  2 root root     120 2008-10-14 13:29 by-path
crw-rw----  1 root root 13,  64 2008-10-14 13:29 event0
crw-rw----  1 root root 13,  65 2008-10-14 13:29 event1
crw-rw----  1 root root 13,  74 2008-10-14 13:30 event10
crw-rw----  1 root root 13,  66 2008-10-14 13:29 event2
crw-rw----  1 root root 13,  67 2008-10-14 13:29 event3
crw-rw----  1 root root 13,  68 2008-10-14 13:29 event4
crw-rw----  1 root root 13,  69 2008-10-14 13:29 event5
crw-rw----  1 root root 13,  70 2008-10-14 13:29 event6
crw-rw----  1 root root 13,  71 2008-10-14 13:29 event7
crw-rw----  1 root root 13,  72 2008-10-14 13:29 event8
crw-rw----  1 root root 13,  73 2008-10-14 13:29 event9
crw-rw----  1 root root 13,  63 2008-10-14 07:29 mice
crw-rw----  1 root root 13,  32 2008-10-14 07:29 mouse0
crw-rw----  1 root root 13,  33 2008-10-14 13:29 mouse1
crw-rw----+ 1 root root 10, 223 2008-10-14 13:30 uinput
lrwxrwxrwx  1 root root      10 2008-10-14 13:30 wacom -> /dev/ttyS0

---

### Post by falsadoo on 2008-10-15
Hi, I am a new in Ubuntu... I have HP tx2000 tablet and I trid the step on my laptop they all work but when I restart my laptop nothing happened this what you asked for.I hope you can  help me fix this problem 

:confused:

---

### Post by pooyaplus on 2008-10-16
falsadoo,
I followed another tutorial and that worked for me. If you are on Hardy here are the steps then you need to configure your xorg.conf:

```

cd ¬/Desktop
wget -c http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-5.tar.bz2
sudo apr-get update
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
sudo apt-get upgrade
sudo apt-get remove wacom-tools xserver-xorg-input-wacom
sudo apt-get install linux-headers-generic
tar xjvf linuxwacom-0.8.1-4.tar.bz2
cd linuxwacom-0.8.1-4
./configure --enable-wacom
make
sudo make install
sudo rmmod wacom
sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -e
sudo modprobe wacom

```

Then restart your x server: ```
ctrl+alt+backspace
```
See if the touchscreen works and if it needs calibration, then we need to take a look at your xorg.conf file. 

Post back if you encountered a problem.

---

### Post by pooyaplus on 2008-10-16
Another thing to mention, we are not using a usb tablet or a bamboo fun, so it is better not to bother these guys here:popcorn:

Here is where our tx2000 thread is located:
[http://ubuntuforums.org/showthread.php?t=708726&page=1](http://ubuntuforums.org/showthread.php?t=708726&page=1)
Post your problems there plz.

---

### Post by jetbbal on 2008-10-16
Just picked up a bamboo fun, followed the directions, and it's unresponsive

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

```
total 0
drwxr-xr-x 2 root root    100 2008-10-16 12:15 by-id
drwxr-xr-x 2 root root    120 2008-10-16 12:15 by-path
crw-rw---- 1 root root 13, 64 2008-10-16 12:15 event0
crw-rw---- 1 root root 13, 65 2008-10-16 12:15 event1
crw-rw---- 1 root root 13, 66 2008-10-16 12:15 event2
crw-rw---- 1 root root 13, 67 2008-10-16 12:15 event3
crw-rw---- 1 root root 13, 68 2008-10-16 12:15 event4
crw-rw---- 1 root root 13, 69 2008-10-16 12:15 event5
crw-rw---- 1 root root 13, 70 2008-10-16 12:15 event6
crw-rw---- 1 root root 13, 63 2008-10-16 12:15 mice
crw-rw---- 1 root root 13, 32 2008-10-16 12:15 mouse0
crw-rw---- 1 root root 13, 33 2008-10-16 12:15 mouse1

```

any help is appreciated

---

### Post by falsadoo on 2008-10-16
I try the new way but it didn't work too... I have Ubuntu hardy heron 8.04. I hope there is a way to make it work.:confused:

---

### Post by Loïc2 on 2008-10-20
I've just updated the wiki ( [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) ) for Intrepid, and cleaned up the rest of the page. I also updated [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting) , I just didn't add entries for the "pad" since it's not supported in old versions.

I was forced to use Intrepid for quite a while (new hardware), and, during its development, only recently has Wacom support been newbie friendly enough to warrant updating the wiki ;)

For Hardy users (actually for any version of Ubuntu, previous or future ones) remember that you can check on [The Linux Wacom Project]("http://linuxwacom.sourceforge.net/") if the version of the linux wacom driver you have in your distribution (check with System>Administration>Synaptic Package Manager or ```
dpkg -p wacom-tools  | grep Version
``` ) supports your model of tablet. If it supports it, you only need to edit your /etc/X11/xorg.conf as in the wiki - you save time and run less risks to mess up your configuration.

Since this thread is dedicated to tablets unsupported in Hardy (and those tablets are now supported by the wacom driver in Intrepid), I've opened a thread at [http://ubuntuforums.org/showthread.php?t=953818](http://ubuntuforums.org/showthread.php?t=953818) as a forum side of the Community documentation.

---

### Post by pspace on 2008-10-20
Worked as expected after step 19. Now to the fine-tuning. Lots of thanks!

---

### Post by Carl72 on 2008-10-20
Worked great on my Toshiba Satilite R20!  Thanks for the easy tut.  Only took a few min.  Now I have no excuse to stick to Linux this time...

Thanks!

---

### Post by Macktownjoe on 2008-10-21
Neko,

Thanks. I'm pretty new to Ubuntu, but your directions worked (after one **little** :confused: mistake on my part. Tablet works in Inkscape and Gimp - all except pressure-sensitive. I can live with that until some genius shows me what to do to make it work.

My hat is off to you, my friend!

Macktownjoe

---

### Post by sekibun on 2008-10-21
thx it works! but when i did this tutorial my X serwer restarts when i for example use 'search' tool. it also restarts when i do nothing. my tablet works but i can't work normally :/ 
could somebody help me?

sorry for my english.

---

### Post by manilandragon on 2008-10-25
Hi there. Having some problems.here's one thing that pops up in the terminal whilst following your tutorial.

cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

also,...
manilandragon@manilanpad:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"	
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
manilandragon@manilanpad:~$ ls -l /dev/input

_________________________________________________
Hope someone could help me out,...I'm pretty new to this stuff
Thanks

---

### Post by Aero_Rising on 2008-10-26
Mine doesn't work and it won't let me attach a file but here is the output.

```
jacob@jacob-laptop:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
jacob@jacob-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-10-26 11:39 by-path
crw-rw---- 1 root root 13, 64 2008-10-26 11:39 event0
crw-rw---- 1 root root 13, 65 2008-10-26 11:39 event1
crw-rw---- 1 root root 13, 66 2008-10-26 11:39 event2
crw-rw---- 1 root root 13, 67 2008-10-26 11:39 event3
crw-rw---- 1 root root 13, 68 2008-10-26 11:39 event4
crw-rw---- 1 root root 13, 69 2008-10-26 11:39 event5
crw-rw---- 1 root root 13, 70 2008-10-26 11:39 event6
crw-rw---- 1 root root 13, 63 2008-10-26 11:37 mice
crw-rw---- 1 root root 13, 32 2008-10-26 11:37 mouse0
crw-rw---- 1 root root 13, 33 2008-10-26 11:39 mouse1

```

---

### Post by Nephila on 2008-10-30
Hi. Um. I'm very Ubuntu-illiterate. And I need help. Err.

I input everything up to direction number seven: 

> ./configure --enable-wacom
make
sudo make install

And now I'm kind of stuck. I don't think I did anything wrong, but, it is entirely possible. Maybe I should be using the CD at the same time? I feel really.. dumb.

I just can't get past seven. When I input those commands, I get a message saying:

> ./configure: no such file or directory

Which kind of um, sucks. And I don't know what to do.
(If its a simple fix I'll feel really dumb. Arg.)

Thanks for any help. :]

EDIT:

Wait a minute, I got it to work. If I have any other trouble I'll post again. : D

---

### Post by kloyde on 2008-10-30
it worked for me at first, everything exept the scroll part of the stylus, but now nothing works. i want to uninstall everything that i did here and try again, but i dont know how. ive attached the results of the two commands at the end of the page.

---

### Post by Nephila on 2008-10-30
Nevermind. I'm not going to bother.

---

### Post by oth8man on 2008-10-31
Hello everybody,I followed the steps until step 13 I have problem that when I write this this line :

sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

but then it show this :

cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

I don't know why the terminal can't find the directory, and by the way after I finished step 12 I had to shut-Down the laptop, and then start again from step 13 .

Thanks:)

---

### Post by priegog on 2008-10-31
Intrepid is out soooo...
Are these instructions usable for intrepid? I tried them on a late beta and they didn't work AT ALL (I had gotten them to work on hardy, mind you, so that's not the issue).
Also there's this new xorg deal and I have no idea on how to proceed. 
I have a tablet pc, so there's really no option to "plug&play" for me.

---

### Post by revidnus on 2008-11-01
Thanks, neko18 ... nice post. Im running 64 bit Hardy on a Hp pavillion dv 9610us and the Bamboo Fun tablet installed nicely with your codes. No problems a smoooooth setup. Thanks again,
Philip

---

### Post by small_sammy on 2008-11-05
Hi there,

I followed the steps, with no errors at all.
I came to the point to restart and the X server kept crashing with message, cannot start greeter application..... I just realized that the tutorial is for Ubuntu, I am running Xubuntu...

I logged in from the console and attempted to start the X server manually by "startx"... 
It started, but with the Ubuntu Desktop, not Xfce.. lol (several errors kept appearing about applets that couldnt load)

So i copied my original xorg.conf back to etc and rebooted and everything came back to normal... even the Wacom is working... hehe.. No pressure sensing though, but i think i can live with that.

Thanx.

---

### Post by gnocci on 2008-11-06
Just a quick note, for the point 2 of the troubleshoting ("Problem: You do not remember your username."), it's wnough to run:

```
whoami
```

---

### Post by dalebert on 2008-11-07
This worked for me on my Intuos3 tablet. Thank you!

---

### Post by lpagola on 2008-11-09
Thanks neko18. I have a Wacom Bamboo running on a dell 1330 with Ubuntu 8.04 and everything is working after following your howto. Now I just have to find out how to configure Gimp and other drawing software to recognize pressure function.

Thanks again,

---

### Post by Puzzlenoise on 2008-11-11
Yay, the installation went perfect. It wasn't complicated and everything works just fine. :D

---

### Post by Thorn Striff on 2008-11-15
Hey,

i have a HP TX2075 and this tutorial didnt worked to me.
I got no error but at end my tablet still didnt working.

Can someone help me?

```
pedro@pedro-laptop:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
pedro@pedro-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    120 2008-11-16 01:51 by-path
crw-rw---- 1 root root 13, 64 2008-11-16 01:51 event0
crw-rw---- 1 root root 13, 65 2008-11-16 01:51 event1
crw-rw---- 1 root root 13, 66 2008-11-16 01:51 event2
crw-rw---- 1 root root 13, 67 2008-11-16 01:51 event3
crw-rw---- 1 root root 13, 68 2008-11-16 01:51 event4
crw-rw---- 1 root root 13, 69 2008-11-16 01:51 event5
crw-rw---- 1 root root 13, 70 2008-11-16 01:51 event6
crw-rw---- 1 root root 13, 71 2008-11-16 01:51 event7
crw-rw---- 1 root root 13, 72 2008-11-16 01:51 event8
crw-rw---- 1 root root 13, 73 2008-11-16 01:51 event9
crw-rw---- 1 root root 13, 63 2008-11-15 23:51 mice
crw-rw---- 1 root root 13, 32 2008-11-15 23:51 mouse0
crw-rw---- 1 root root 13, 33 2008-11-16 01:51 mouse1
pedro@pedro-laptop:~$ 

```

---

### Post by umor on 2008-11-16
Hello Neko18,
what follows is my (sucsessful) experience  with installing a wacom bamboo on a lenovo T400 laptop with ubuntu 8.10.
 
I followed your excellent description how to install a wacom bamboo step by step. 
But, instead of Ubuntu 8.04 I had Ubuntu 8.10 on the Lenovo T400 Laptop. Never the less, everything worked out without error. Only at point 10 of your description I saw that there was no Section called "ServerLayout" in the xorg.conf file. Hence I just copied your lines from step 10, added them at the end of the "xorg.conf" file and included those of step 11. As I had no clue what I was doing, it was not very surprising that what I was doing, was not the correct thing to do. Still I had no error messages until renbooting after point 19. While rebooting, Ubuntu told me, the graphic was broken. I didn't care and decided to use it anyway, but Ubuntu was right: the screen was just a weired mixture of colors... After rebooting again, Ubuntu asked me again to switch back to the default values and this time I agreed. Everything worked again. 
Even the wacom was working!! 
Now I can only speculate that it is not necessary to manimulate your xorg.conf if there is no "ServerLayout" entry. But this speculation comes from someone who has almost no expericene with Linux. Still I hope it might be helpful for those who find themeself in the same situation as I was.

umor

---

### Post by Malvazar on 2008-11-16
Umm... Okay this is weird! I ran through all the steps and every thing worked fine until I pick up my mouse and tried to use it, nothing happened! I don't know what is going on because I can use my pen just fine. I am running on Ubuntu 8.10 need some help!:confused:

---

### Post by Malvazar on 2008-11-17
> **Malvazar said:**
> Umm... Okay this is weird! I ran through all the steps and every thing worked fine until I pick up my mouse and tried to use it, nothing happened! I don't know what is going on because I can use my pen just fine. I am running on Ubuntu 8.10 need some help!:confused:
I found some thing quite interesting out just now!
When I go to change the xorg file and add in the new lines not only is the file not as big as it was in the older versions of ubuntu but if I go ahead and add the lines the files  screws up ad causes the boot process not to work properly  and I have to reset everything thought the recovery mode.
Any ideas on what to do would be very much appreciated, other wise I will have to go back to windows. (And I really don't want to do that):(

---

### Post by ipburbank on 2008-11-18
I tried this, and got an error. The problem is that my Xorg is only nvidia stuff, no input sections. I'm running ubuntu studio 8.10, any ideas? Should there be something else there? and if so, how am I supposed to do the last few steps? help would defiantly be appreciated!

---

### Post by cseberino on 2008-11-26
If one's USB Wacom tablet works out of the box, must they go through all the work of this HOWTO?

My *ONLY* problem is I want absolute positioning so my USB Wacom tablet doesn't just act like a mouse?

Do I have to do the ENTIRE HOWTO just for that? 

Is there a piece I can focus on only?

Thanks,

cs

---

### Post by Favux on 2008-11-28
Thorn Striff,

Unfortunately lots of stuff not right with your xorg.conf.  Since I have a TX 2110us you could probably cut and paste mine to replace yours.  Be sure to back yours up first!  But I'd go over it a section at a time to familiarize yourself with it.
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
# if it has not been modified since the last upgrade of the xserver-xorggksudo gedit /etc/X11/xorg.conf &
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
# uncommented out 11-27-08 as test for key bindings
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Pad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
Option "Button2" "3" # make side-switch a right button
Option "TopX" "225"
Option "TopY" "225"
Option "BottomX" "26300"
Option "BottomY" "16375"
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-event-"
Option "TopX" "200"
Option "TopY" "225"
Option "BottomX" "4000"
Option "BottomY" "3875"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Type" "eraser"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse"
Option "USB" "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option "RandRRotation"  "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Pad"
	Inputdevice "stylus"	"SendCoreEvents"
	Inputdevice "touch"	"SendCoreEvents"
	Inputdevice "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection
```
Notice how there are actual usb input paths and position information.  Also to get touch working "Synaptics Touchpad" needs to be renamed to "Synaptics Pad".  Note how I had to uncomment out the keyboard section so it would reactivate through xorg.conf rather than HAL.  This is because HAL breaks single key key-bindings.  So if you want to use your "Q" key to rotate your screen you need this.

Speaking of rotation, you do have the nVidia card, right?  Have you enabled the proprietary driver?  Also to do screen rotation you need to add to your video section:
```
	Option 		"RandRRotation"  "on"
```
Like I have in my xorg.conf.  I'd suggest you also check out other threads for tablet pc's and TX2000's.  Some of the folks there like gali98 are very helpful.

Hope this helps some.

---

### Post by Favux on 2008-11-28
Oops!  Thorn Striff,

Rereading your post I realized you and I may be talking about two different tutorials.  I strongly recommend you check out gali98's tutorial dated 11-3-08 for TX2000's.  You can find it here:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")
Notice for the TX2000 we're using the Wacom development driver 0.8.1-6, not the Ubuntu repository driver.  It will take you some time to read through and study it but if you follow it exactly you'll be up and running.  And since every time Ubuntu updates the kernel it breaks Wacom you'll have to repeat it.  But by then it'll only take you about 10 minutes.

Good luck.

---

### Post by djframes on 2008-11-29
BRILLIANT! --- worked a dream. Tablet covers the whole screen now and everything works except The Gimp Dialogue will not recognize the damned thing even though it all works. I'll Google this if I need to. THANK YOU VERY MUCH I have spent hours of fruitless effort before finding you.

---

### Post by Favux on 2008-11-29
I'm glad I could be of help djframes.  Not sure of the problem you're having with Gimp.  As far as I can tell Gimp works fine for me, but I'm not a Gimp jockey.

By the way I posted a tutorial on screen rotation to Tips & Tutorials this morning.  Now the wait while the moderators decide if it's worth posting.  If not I'll post it elsewhere.

---

### Post by Favux on 2008-11-30
Hi djframes,

Like I said I'm not sure what problem you're having with Gimp but here's a few sources I used to set it up.  First I'd suggest you go to the Linux Wacom Project's _Using Xsetwacom_ HOWTO at:

   [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom")

if you haven't already.  Lots of good info., esp. on using terminal to check your pressure sensitivity, etc.  Remember the tool names are case sensitive so stylus is not the same as Stylus.  Check your xorg.conf if you don't remember.  This gives you access to settings that aren't necessarily in wacomcpl.

Now to Gimp.  You probably want to check out Drawing Tablets-Wilber's Wiki at:
   
   [http://wiki.gimp.org/gimp/DrawingTablets]("http://wiki.gimp.org/gimp/DrawingTablets") 

Lots of good info. but to set up Gimp you want the hotlink Pressure Sensitivity under Enabling Gimp Pressure Sensitivity.  When it says File>Preferences it means Edit>Preferences.  Also the Device Status dialog is located in Windows>Dockable Dialogs>Device Status.  Just follow the steps and you should have your stylus, eraser, and pressure working in short order.  Hope this helps.

---

### Post by djframes on 2008-12-01
Thanks for the answer. Everything works fine in Gimp but the Preferences/Input controllers/Linux input/ Looks like this:

Wacom Graphire 2.4 Linux input Device not available Permission denied.

Which doesn't make a lot of sense as in the dialogues it shows the Stylus,Cursor, Eraser and Pad.

I'll probably put up with it as it doesn't seem to matter a lot.

---

### Post by Puzzlenoise on 2008-12-01
Hi

I already installed my Bamboo One once, but a few days ago it stopped working. Now I installed it again and my screen resolution is extremely low (800*600). I feel ill, I am not used to it. :(

Thats not everything. My keyboard changed some functions...
Does it have something to do with the xorg.conf?
Can I reset it anyhow?

---

### Post by Puzzlenoise on 2008-12-02
Finally, I solved the problems with my screen resolution and the keyboard.

Back to my Bamboo One:
It doesn't work properly. Usually this board acted as a "screen". If I pointed the pen in the middle of the board, the cursor was in the middle of the screen. Now it isn't!

Instead, my pen is taking the funktion as a "mouse". If I wield the pen fast, the cursor goes a longer way than if I would wield the pen slow.
I cannot draw like that. :(

Did anyone hear from a problem like this already? 
Should I just install the board again?
Or is there another solution?

I'd be thankful for getting answers. :)

EDIT: Reinstalling it worked just fine. Everything is perfect now~

---

### Post by oc666 on 2008-12-04
Hello,
I've got a tx2510us tablet a few months ago, i installed ubuntu 8.10 a few days ago, got the sound to work and wireless runs fine, but i havent managed to get the tablet function to work at all, ive installed wacom without even seeing these posts but it didnt help and the cpl is empty.
seems that the device isnt recokgnized by the xorg at all...
i would also appriciate some help regarding the video card and rotation if possible.
thanks.

---

### Post by Favux on 2008-12-04
Hi oc666,

I'm afraid you're lost.  This thread seems more for folks who have wacom drawing tablets, not people who have tablet pc's.  I was reading through the thread for useful information when I happened onto Thorn Striff, who also seemed lost and now seems to have disappeared.

First to get the tablet part of your tablet pc working I suggest
doing gali98's wacom tutorial for tablet pc's found here:
[http://ubuntuforums.org/showthread.p...47#post5469447](http://ubuntuforums.org/showthread.p...47#post5469447)
or follow the shortened version posted on this thread:
[http://ubuntuforums.org/showthread.php?t=845911&page=39](http://ubuntuforums.org/showthread.php?t=845911&page=39)
and follow the instructions exactly using the latest linuxwacom development driver 0.8.1-6 since you're using Intrepid (8.10).

Try to find TX2500 and TX2000 threads to follow.  For instance:
   [http://ubuntuforums.org/showthread.php?t=845911]("http://ubuntuforums.org/showthread.php?t=845911")
where on the last few pages I have been trying to walk tah123 through my rotation how to at:
   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

I hope this helps some.

---

### Post by riccardhino on 2008-12-05
hi everyone!

I followed this guide and it worked just fine right from the beginning. I installed a bamboo one and I had a lot of fun drawing for some weeks, then, I stopped using the tablet for a couple of weeks and today I took it up again to draw, but it doesn't work. 

Now, the cursor only moves when I use the mouse, whereas just after the installation I could use both mouse and pen at the same time.
the problem is I never touched anything in the wacom setting since the installation, more to it I merely did the basic security updates on Hardy and nothing more on this pc!

just as a first check today I rebooted the pc and I saw that the tablet is recognized as a USB input device. I also checked xorg.conf, but the settings are the same as when I set them during the installation.


Is it a problem about the configuration?
How can I have my pen working again? what else can I do?
Please, help me, because I am totally at a loss with the console!

---

### Post by Sawer on 2008-12-07
I can only get this far   cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

I all ready had xorg.conf done  so I skipped it don't know if this makes a difference.
Thanks for the How To

---

### Post by Sawer on 2008-12-10
Thanks neko18 I finally got my tablet working. It took a couple of tries, but it is working now.

---

### Post by anantyk on 2008-12-11
neko18

many thanks for the HOWTO on wacom tablets. For me it worked like magic. I now have my Graphire4 running as smooth as butter.

Have yet to get GIMP to understand the eraser & pen buttons.

kanwarjit


[QUOTE=neko18;4785779]**[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

---

### Post by Sawer on 2008-12-12
Is there someway to get new settings in waconcpl to stick? Every time I do either restatX or switch users the settings  revert to default.
I've noticed that you can't set new settings for the cursor, eraser or stylus I get  an error message that they are core devices no changes can be made. It worked fine in Gusty but not in Hardy.
Thanks

---

### Post by MGaddict2000 on 2008-12-23
**@welldone101**

I had the same error, the problem is the entire line doesn't print. If your trying to print out this thing and then type it in, your not going to be able to. You have to copy and paist it.  The line scolls over quite a bit, when you paist it its like 3 lines long. You will have that problem again later.  I hit my head against the same wall for 10 minutes.

---

### Post by MGaddict2000 on 2008-12-23
Well, this thread has gotten wildly out of hand it looks like, its very hard to find what I'm looking for. From what I see, a lot of people have complained about wacomcpl not working and just brushing it off. I'm getting a different error from other people. But a lot are having a lot of different errors, which leads e to believe there is an inherent problem with wacomcpl all together. I have a Tablet PC and have been trying to get wacomcpl to work for a while, at least now its listing my stylus. although the calibration pops up an error 

> unknown device "stylus" or it is currently a core device
unknown device "stylus" or it is currently a core device
    while executing
"wacomxi::bindevent .topleft.m $device <ButtonRelease>  {calibrationSequence 0 %0 %1}"
    (procedure "startCalibration" line 20)
    invoked from within
"startCalibration"
    (procedure "Calibration" line 22)
    invoked from within
"Calibration"
    invoked from within
".panel.calibrate invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .panel.calibrate"
    (command bound to event)

So I'm moving in the right direction just still not there. If somebody can suggest a solution here great, otherwise I'm going to repost this on a new thread. The solution may be in this thread already but its imposible to follow any of them because its just to huge. Mabey I'm viewing it wrong. I don't know.

---

### Post by Doctor Mapache on 2008-12-29
I just follow the steps and my wacom Bamboo doesn't work at all.

I have the following error:

doctormapache@Skydine:~/wacom$ sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: no se puede efectuar `stat' sobre «linuxwacom-0.8.0-3/src/2.6.24/wacom.ko»: No existe el fichero ó directorio

I attached the file with the outputs that you asked for.

Thnaks beforehand:
DM

---

### Post by RevBingo on 2008-12-31
neko18, thanks, worked first time for me with a Bamboo One

---

### Post by Christopherius on 2009-01-01
My Wacom Bamboo tablet doesn't respond at all after I followed this How-To.

Heres my xorg.conf:

```
Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Option         "AIGLX" "true"
    InputDevice	   "Wiimote" "AlwaysCore"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
    InputDevice    "pad"      
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL S199WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "XAANoOffscreenPixmaps"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1440x900 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

And my /dev/input:

```
chrism@chris-desktop:~$ ls -l /dev/input
total 0
drwxr-xr-x  2 root root        120 2009-01-01 01:10 by-id
drwxr-xr-x  2 root root        200 2009-01-01 01:10 by-path
crw-rw----  1 root root    13,  64 2009-01-01 01:10 event0
crw-rw----  1 root root    13,  65 2009-01-01 01:10 event1
crw-rw----  1 root root    13,  74 2009-01-01 01:10 event10
crw-rw----  1 root root    13,  66 2009-01-01 01:10 event2
crw-rw----  1 root root    13,  67 2009-01-01 01:10 event3
crw-rw----  1 root root    13,  68 2009-01-01 01:10 event4
crw-rw----  1 root root    13,  69 2009-01-01 01:10 event5
crw-rw----  1 root root    13,  70 2009-01-01 01:10 event6
crw-rw----  1 root root    13,  71 2009-01-01 01:10 event7
crw-rw----  1 root root    13,  72 2009-01-01 01:10 event8
crw-rw----  1 root root    13,  73 2009-01-01 01:10 event9
crw-rw----  1 root plugdev 13,   0 2009-01-01 01:10 js0
crw-rw----  1 root root    13,  63 2009-01-01 01:10 mice
crw-rw----  1 root root    13,  32 2009-01-01 01:10 mouse0
crw-rw----  1 root root    13,  33 2009-01-01 01:10 mouse1
crw-rw----  1 root root    13,  34 2009-01-01 01:10 mouse2
crw-rw----  1 root root    13,  35 2009-01-01 01:10 mouse3
lrwxrwxrwx  1 root root          6 2009-01-01 01:10 tablet-bamboo -> event6
crw-rw----+ 1 root root    10, 223 2009-01-01 01:10 uinput
lrwxrwxrwx  1 root root          6 2009-01-01 01:10 wacom -> event6

```

I gotta be missing something simple here. Maybe a fresh set of eyes will help. I've been at this for a few hours. Thanks for any help.

Almost forgot my xsetpointer output:

```
xsetpointer -l
0: "Virtual core keyboard"	[XKeyboard]
1: "Virtual core pointer"	[XPointer]
2: "Generic Keyboard"	[XExtensionKeyboard]
3: "Configured Mouse"	[XExtensionPointer]
4: "pad"	[XExtensionKeyboard]
5: "cursor"	[XExtensionKeyboard]
6: "eraser"	[XExtensionKeyboard]
7: "stylus"	[XExtensionKeyboard]
```

Shouldn't pad, cursor, eraser and stylus be XPointer instead of XExtensionKeyboard?

---

### Post by nashmage on 2009-01-01
I have an hp tx2000 tablet pc and i was redirected to this post in order to get my touchscreen to work i tried this but after the restart my laptop went into graphics safe mode and wouldnt let me log back in until i went back to my previous graphics setup. i made the text file like was mentioned and hopefully someone can help it would be greatly appreciated! :D

---

### Post by Favux on 2009-01-01
Hi nashmage,

Did you install Ubuntu 8.10 Intrepid?  It looks like you did because there is almost nothing in your xorg.conf.  If your stylus is working, it is through HAL (hardware abstraction layer).  But HAL won't let the rest of your tablet work so you have to go back to xorg.conf.

Also you do not have the nVidia proprietary driver installed.  Go to System>Administration>Hardware Drivers.  Select nVidia driver v. 177 and make active.

Then go to:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

At the bottom of the rotation HOW TO select the TX2000 xorg.conf.  You should just replace you xorg.conf with it (if you're on Intrepid, otherwise it needs some editing).  Be sure to back up your xorg.conf first.  It would be a good idea to study them side by side so you can see what your current xorg.conf is missing.

If after a reboot with the new xorg.conf you still don't have a working tablet we can deal with the linuxwacom drivers.

Good luck.

---

### Post by Christopherius on 2009-01-01
I got my tablet working now. The mouseemu package was conflicting with the wacom drivers. I uninstalled mousemu and restarted X and all is well!

---

### Post by Mr. Turtle on 2009-01-02
I ran into a problem in step 4,
after I enter the second command (sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev -y) (even when I copy and paste) it responds:

Reading state information... Done
Package linux-headers-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.22-14-generic has no installation candidate

any help would be wonderful, thank you.

---

### Post by Applegeek on 2009-01-03
These instructions worked perfectly for me on Ubu Hardy amd64.

Thanks!!!!

---

### Post by Deeno on 2009-01-06
Fantastic Post, the steps worked for my Wacom Bamboo.

My only issue is getting the FN1 FN2 < > buttons to work as they did for me in XP

So Far the little circle on the pad acts as a scroll up down in Firefox

I really like the < > buttons to function as back and forward buttons in Firefox. Any help on how to do this, please?

Also How would you configure the two buttons on the pen to be, for instance : upper button centre mouse click, so I can use it to scroll up and down the page?

Thanks for any help in advance.

Deeno

---

### Post by Deeno on 2009-01-06
> **Deeno said:**
> Fantastic Post, the steps worked for my Wacom Bamboo.

My only issue is getting the FN1 FN2 < > buttons to work as they did for me in XP

So Far the little circle on the pad acts as a scroll up down in Firefox

I really like the < > buttons to function as back and forward buttons in Firefox. Any help on how to do this, please?

Also How would you configure the two buttons on the pen to be, for instance : upper button centre mouse click, so I can use it to scroll up and down the page?

Thanks for any help in advance.

Deeno

[COLOR="Red"]UPDATE[/COLOR]  On the Firefox Scroll on Pen Button.
I found a solution for this. It was not in fact the button that was not working, for some reason the Feisty Fawn install of Firefox disables the us of middle button scroll as default.
FIX: Open Firefox Type about:config in the address bar and look for the line general.autoScroll and set the value to True. 
Now my pen scrolls just as it did in XP :)

Any help on the stting of the FN1 FN2 < > buttons would still be appreciated :)

Deeno

---

### Post by GixGidea on 2009-01-11
First, thank you to everyone in this community for being so helpful.
I'm just starting to try and figure our ubuntu, and there are a lot of things that I don't understand.  I've read through the previous pages and now my eyes are crossing... I may have read the answer to my question, but I couldn't tell you if I did.

I've followed all the directions:  
When I get to step 8:
gksudo gedit /etc/X11/xorg.conf
The system pauses like it wants to do something, or it asks me for my password (I've tried this a couple of times).  However, I just get the prompt again and am not given anything to edit.

Here is the information I get from the output of cat /etc/X11/xorg.conf
 and ls -l /dev/input.

Any help would be greatly appreciated.
Thank you so much in advance.

[edit]: In case this helps with anything, I'm using xubuntu, on an older Dell Latitude (I don't know the specs off hand

---

### Post by alcyon7 on 2009-01-12
I neko18
I follow the how to, no error message but the bambou fun doesn't work
here is after my xorg.conf
could you help me ?
thanks
marc@marc-dell:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Dougpol1 on 2009-01-21
Hello Neko 18,  Thanks to all for this help this is great stuff.  Ran into this problem and ignored it.   Could not connect to repository.akirad.net:80 (78.47.64.240), connection timed out
Err [http://repository.akirad.net](http://repository.akirad.net) akirad-hardy/main Translation-en_US           
  Unable to connect to repository.akirad.net http:
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy Release.gpg                            
  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Translation-en_US                 
  Unable to connect to akirad.hfbk.net http:
Err [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy Release.gpg                       
  Could not connect to akirad.cinelerra.org:80 (78.47.64.240), connection timed out
Err [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy/main Translation-en_US
  Unable to connect to akirad.cinelerra.org http:
Reading package lists... Done                          
W: Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/Release.gpg](http://repository.akirad.net/dists/akirad-hardy/Release.gpg)  Could not connect to repository.akirad.net:80 (78.47.64.240), connection timed out

W: Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2](http://repository.akirad.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to repository.akirad.net http:

W: Failed to fetch [http://akirad.cinelerra.org/dists/akirad-hardy/Release.gpg](http://akirad.cinelerra.org/dists/akirad-hardy/Release.gpg)  Could not connect to akirad.cinelerra.org:80 (78.47.64.240), connection timed out

W: Failed to fetch [http://akirad.cinelerra.org/dists/akirad-hardy/main/i18n/Translation-en_US.bz2](http://akirad.cinelerra.org/dists/akirad-hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to akirad.cinelerra.org http:

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg](http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg)  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2](http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to akirad.hfbk.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Got this  cp:cannot sat "linux wacom-0-30-3/sac/2.6.24/wacom.kono such file or directory help please  Doug

---

### Post by SnakeArtworX on 2009-02-03
Big thanks for this How-To. I'd like to know, why everytime I do an actualization of my system, I need to recompile the wacom driver? It happened even when X.org is not updated during actualization.

---

### Post by satangos_w on 2009-02-05
It works for me! 
For some days i think that i never can configure my bamboo fun.
So, thank you for this how to!

:popcorn:

---

### Post by Kyosys on 2009-02-07
I did this, and now my PC keeps crashing (goes to black screens)

---

### Post by arm-c on 2009-02-07
SUBJECT:  Users of Acer Tablet PCs or other users that use the acerhk driver to control their wireless and bluetooth adapters.

I have written a small GUI program to provide interface to control the ACERHK driver.  A link to my post on the ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=1059704](http://ubuntuforums.org/showthread.php?t=1059704)

I really hope this is helpful. I know that it is a little off topic here, but I post because I use with my Acer Travelmate C300 Tablet PC and provides for a nice PEN interface in tablet mode because buttons that control that are on the keyboard surface (hidden) when in tablet mode.

I just ask that users let me know if it is helpful to them. :)  The POLL is a good place to start.

Warm Regards
ARM-C

---

### Post by M.Erde on 2009-02-07
Hello, I am new to forums so forgive any errors.
Trying to do installation of Bamboo fun above.
Step 7 I get several errors. finished out anyway and no luck. tablet doesn't work at all.

**I upgraded to 8.10 and now my bamboo works although not all functions keys work yet.

---

### Post by qxz9p on 2009-02-09
I too am new to the forums and am just posting for this help.

Im on an HP Compaq tc4200 running 8.04

I have followed the guide and not gotten any error messages except:
"ldconfig deferred processing now taking place" while "Processing triggers for libc6" during step 17.

for the docs you request I get
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

```

and 

```

steven@steven-laptop:~$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root    160 2009-02-09 22:46 by-path
crw-rw---- 1 root root 13, 64 2009-02-09 22:45 event0
crw-rw---- 1 root root 13, 65 2009-02-09 22:45 event1
crw-rw---- 1 root root 13, 66 2009-02-09 22:45 event2
crw-rw---- 1 root root 13, 67 2009-02-09 22:45 event3
crw-rw---- 1 root root 13, 68 2009-02-09 22:45 event4
crw-rw---- 1 root root 13, 69 2009-02-09 22:45 event5
crw-rw---- 1 root root 13, 70 2009-02-09 22:45 event6
crw-rw---- 1 root root 13, 71 2009-02-09 22:45 event7
crw-rw---- 1 root root 13, 72 2009-02-09 22:46 event8
crw-rw---- 1 root root 13, 63 2009-02-09 22:45 mice
crw-rw---- 1 root root 13, 32 2009-02-09 22:45 mouse0
crw-rw---- 1 root root 13, 33 2009-02-09 22:45 mouse1
crw-rw---- 1 root root 13, 34 2009-02-09 22:46 mouse2
lrwxrwxrwx 1 root root     10 2009-02-09 22:46 wacom -> /dev/ttyS0

```

and typing "lsusb | grep -i wacom" doesnt return me with any information.

I am really quite lost and would appreciate any help.

Thanks!

---

### Post by Favux on 2009-02-10
Hi qxz9p,

Please check out the following thread:

[http://ubuntuforums.org/showthread.php?t=1027808&highlight=tablet+pc]("http://ubuntuforums.org/showthread.php?t=1027808&highlight=tablet+pc")

It should help you get set up.  You probably should post any further questions there.

Good luck!

PS:  You do not need the cursor or pad InputDevice sections or in ServerLayout in your xorg.conf.  Those are for external graphics tablets.

---

### Post by ktwbug on 2009-02-14
MANY THANKS!!!  I looked everywhere and tried a million different fixes but this one worked flawless start to finish!!!  You give great directions!!!  Thank you sooo much.  My tablet is working and I can't wait to get back to drawing!!!  This should definitely go on the wiki!

thanks again!!):P

---

### Post by Mr. Turtle on 2009-03-02
Ive tried this tutorial about three times in the past two days (I kept retrying because there would be problems like power outages coming up) The last time i did it i went through the tutorial exactly as it is posted, ( I copy and pasted the commands) but then my computer booted in low graphics mode. It did this last time also, but i attributed that to the power outage. I copied and saved everything in the terminal from the last time i went through the the terminal and could post it if it is necessary, but it is really long. I would appreciate any help that anyone could provide.
I would really like to get my wacom tablet working soon as it is the only thing that i now use my windows computer for.
thank you in advance for any help.

---

### Post by Sciamano on 2009-03-02
First of all, thanks a lot for this tutorial.
I followed it for both my Linux Mint desktop and my Kubuntu 8.04 installations and it worked like a charm!

I've a question though, because my monitor is still a 4:3 one, and therefore using the tablet as it is I draw ovals instead of circles...

I've found the solution in the community documents, which is to add a few lines to the xorg.conf, in the stylus and eraser sections, to limit the size of the pad that's being used, so to maintain the 4:3 proportion of the monitor.

This is the example provided:

```
Section "InputDevice"
        ...     
        Option          "TopX"        "100"     
        Option          "TopY"        "200"      
        Option          "BottomX"     "14000"
        Option          "BottomY"     "6000"
        ...
    EndSection
```

There's not much explanation, although I guess that TopX is the first value (in lines) where the pad should become active on the X-axis, while BottomX is the last active line.
Same of course, with TopY/BottomY, but for the Y-axis.

Now, considering that the resolution of the Bamboo tablet is 2540 lines/inch (1000 lines/centimeter) and that the active portion is 9.4 centimeters tall, to maintain the 4:3 proportion, the active portion should then be (9.4/3*4) = 12.54 cms wide, or 12540 lines (12.54 x 1000).

I therefore added this code to my xorg.conf:

```

        Option          "TopX"        "0"
        Option          "TopY"        "0"
        Option          "BottomX"     "12540"
        Option          "BottomY"     "9400"
```

But, even though the active pad is now limited in its size, I still draw ovals instead of circles...
What did I do wrong in my calculations? Anyone able to calculate the exact numbers to punch in the Top/Bottom couples?
Or maybe I misinterpreted the meaning of TopX/Y and BottomX/Y?

Any help appreciated.
Thanks!

---

### Post by Tobias-sama on 2009-03-07
[COLOR="Indigo"]okay.. okay.. seriously.. I'm really sick of having to configure everything, and really sick of having to spend a couple hours doing so; I'm almost at my wits end with all this crap, it seems that if it doesn't plug and play with linux I've just obtained about 7-8 hours of painstaking work

>.> everything in the tutorial works fine after much tweaking, pain and frustration on my part due to my own stupid human error and the like, except when I reboot, my graphical interface evaporates ... don't worry I figured out how to roll back my xorg.conf file, and then it works fine, but I'm sick of doing the same thing over and over again, please someone just show my what my xorg file is supposed to look like so I can just use the tablet, I'm so sick of working on this >.> it's been four hours already and I have better things to do with my time -.-

this is what my xorg file looks like now 

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

I'm sorry if this topic has been addressed already, but I'm really not in the mood to be looking through 45 pages of posts, again, this is already taking forever and I'm just thoroughly sick of this whole process 

if applicable, computer is a couple-years-old dell laptop
tablet is a wacom bamboo

help would be greatly, greatly appreciated >.<[/COLOR]

---

### Post by Favux on 2009-03-07
Hi Tobias-sama,

Sorry I don't know the xorg.conf for a bamboo.  It's usb, correct?  Because you don't have the Wacom entries in I can't help.  My guess, from looking at the first page of this thread, is that you're confusing the usb and/or serial tablet setups or you do not have the "ServerLayout" correctly configured.  Probably the latter.

Check out Loic2's wiki (and associated thread):

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

It should help.

---

### Post by lordi1980 on 2009-03-18
Hi,

I did steps 1 - 20, but gimp and inkscape don't detect my bamboo.

My xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbVariant"	"multi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"		"SendCoreEvents"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option "NoLogo" "True"

	Screen	0
EndSection



Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```
and did:
ls -l /dev/input
```
total 0
drwxr-xr-x 2 root root    120 2009-03-18 14:39 by-id
drwxr-xr-x 2 root root    160 2009-03-18 14:39 by-path
crw-rw---- 1 root root 13, 64 2009-03-18 14:39 event0
crw-rw---- 1 root root 13, 65 2009-03-18 14:39 event1
crw-rw---- 1 root root 13, 66 2009-03-18 14:39 event2
crw-rw---- 1 root root 13, 67 2009-03-18 14:39 event3
crw-rw---- 1 root root 13, 68 2009-03-18 14:39 event4
crw-rw---- 1 root root 13, 69 2009-03-18 14:39 event5
crw-rw---- 1 root root 13, 70 2009-03-18 14:39 event6
crw-rw---- 1 root root 13, 63 2009-03-18 10:39 mice
crw-rw---- 1 root root 13, 32 2009-03-18 10:39 mouse0
crw-rw---- 1 root root 13, 33 2009-03-18 10:39 mouse1
crw-rw---- 1 root root 13, 34 2009-03-18 14:39 mouse2
lrwxrwxrwx 1 root root      6 2009-03-18 14:39 tablet-bamboo -> event6
lrwxrwxrwx 1 root root      6 2009-03-18 14:39 wacom -> event6

```
xidump -l
```
pointer                        disabled
keyboard                       keyboard

```

---

### Post by justin_c18 on 2009-03-19
> **neko18 said:**
> **[SIZE="3"]Wacom on 8.04 Hardy[/SIZE]**

These are the steps I took to make my Wacom Bamboo Fun work in Ubuntu 8.04 Hardy. These instructions should work for most Wacom tablets.

**0.** Make sure you have a couple hours available. This will take a while. Also, print off a copy of this post because you will need to restart your computer a couple of times. If something goes wrong, see the troubleshooting section at the end of this post.

**1.** Plug in your tablet and open a terminal (Applications > Accessories > Terminal). Enter the commands in the following steps line by line into the terminal, pressing enter after each command. If you are prompted for a password, type your password then press enter.

**2.** ```
lsusb | grep -i wacom
```
Mine is a "056a:0017". Most models beginning with "056a" should work.

**3.** ```
mkdir wacom
cd wacom
```

**4.** ```
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk-dev tcl-dev -y
```

**5.** ```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.0-3.tar.bz2
tar xjf linuxwacom-0.8.0-3.tar.bz2
cd linuxwacom-0.8.0-3
```

**6.** ```
sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
sudo ln -s /usr/include/pixman-1/pixman-version.h /usr/include/pixman-version.h
```

**7.** ```
./configure --enable-wacom
make
sudo make install
```

**8.** ```
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf
```

**9.** Place the following lines near the beginning of the file. If you have a touchpad, make sure you place these lines before the "Synaptics Touchpad" Section.
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```

**10.** Find the section that looks somewhat like this. It will be near the end of the file.
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

**11.** Add these lines within the section you found in step 10.
```
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
```

**12.** Save (Ctrl-S) and quit (Ctrl-Q).

**13.** ```
cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
You may get an error on this step. If you do, please write down the error. If your tablet does not work when you finish this HOWTO, please post this error so I (or someone else) can work through it with you.

**14.** ```
sudo depmod -e
```

**15.** ```
cd linuxwacom-0.8.0-3/prebuilt
sudo ./uninstall
sudo ./install
```

**16.** ```
wget 'http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master' -O wacom.udev
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules wacom.udev.backup
sudo cp wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```

**17.** ```
sudo apt-get remove wacom-tools xserver-xorg-input-wacom -y
sudo apt-get install wacom-tools xserver-xorg-input-wacom -y
```

**18.** ```
sudo ./uninstall
cd ..
sudo make install
```

**19.** Reboot your computer.

**20.** At this point, my tablet began working. If yours still is not, please post in this thread if you need help. Be sure to include any errors you received from the terminal. Also, include the ouput of the following two commands *as an attachment* (text file):
```
cat /etc/X11/xorg.conf
ls -l /dev/input
```


**[SIZE="3"]Troubleshooting[/SIZE]**

**1.**
Problem: X.org does not start after restarting your computer the first time.
Solution:
1. Restart your computer. You can do this either by pressing your power button or by pressing Ctrl-Alt-Delete.
2. When you see "GRUB Loading... Please Wait" on your screen, press the Escape key.
3. Scroll down to the "Recovery mode" entry with the arrow keys and press Enter. It is usually the second one.
4. Once the messages stop scrolling on the screen, enter the following commands. Press enter after each line. Remember to replace "USERNAME" with your actual username. If you do not remember your username, see the troubleshooting #2 entry.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.wacom_modified
cp /home/USERNAME/wacom/xorg.conf /etc/X11/xorg.conf
reboot
```

**2.**
Problem: You do not remember your username.
Solution: Run the following command. It will output a list of users. You will probably be able to recognize your username from this list.
```
cat /etc/passwd | grep "/home" | cut -d: -f1
```

**3.**
Problem: It didn't work.
Solution: Read though the posts in this topic. If you do not find a solution that applies to you, post a new reply asking for help.

Hello, 

Can I follow these instructions to install in Jaunty, too? If not, could provide instruction so I can use Jaunty and my wacom tablet?

Thanks a lot. I've used this tutorial multiple times in Hardy, and it works perfect every time.

Thanks a lot, appreciate the effort and I'm sure many others do too.
Justin

---

### Post by Sciamano on 2009-03-23
> **lordi1980 said:**
> Hi,

I did steps 1 - 20, but gimp and inkscape don't detect my bamboo.

Have you enabled it?
In GIMP: Preferences -> Input Devices -> Configure Extended Input Devices

---

### Post by lordi1980 on 2009-03-23
> **Sciamano said:**
> Have you enabled it?
In GIMP: Preferences -> Input Devices -> Configure Extended Input Devices

Yes, many time, always  "No extended input devices".

---

### Post by Sciamano on 2009-03-23
> **lordi1980 said:**
> Yes, many time, always  "No extended input devices".

In your xorg.conf, have you already tried substituting /dev/input/wacom with /dev/input/tablet-bamboo?
Also, does the tablet work outside GIMP/Inkscape?

---

### Post by lordi1980 on 2009-03-23
> **Sciamano said:**
> In your xorg.conf, have you already tried substituting /dev/input/wacom with /dev/input/tablet-bamboo?

It didn't work. 

> **Sciamano said:**
> 
Also, does the tablet work outside GIMP/Inkscape?
I can move le cursor, wihtout touching the tablet.

---

### Post by Sciamano on 2009-03-24
> **lordi1980 said:**
> I can move le cursor, wihtout touching the tablet.

But does it move as a tablet or as a mouse (if you point the pen on the top left, does the cursor appear immediately to the top left part of the screen?)

---

### Post by lordi1980 on 2009-03-24
> **Sciamano said:**
> But does it move as a tablet or as a mouse (if you point the pen on the top left, does the cursor appear immediately to the top left part of the screen?)

Yes

---

### Post by Sciamano on 2009-03-24
Yes what? It moves like a pen tablet?
In this case I have no idea why GIMP does not recognize it.

---

### Post by albesan on 2009-05-13
Hello team, 

Thanks for the howto.

I've just done  a quick translation for my brother and I thought I'd post it here in case it is useful to someone else.

Regards

a.

---

### Post by padeco on 2009-06-08
hi there!
many thanks for the guide. i had no issues with the installation as i followed the steps. i am running hardy (8.04) and just bought the bamboo fun tablet. it works nicely, although, i have not had a chance to try out everything yet.

cheers,
padeco.

---

### Post by Halberd on 2009-06-17
My Wacom bamboo tablet works fine, thanks to this guide, when I reboot my computer (although I did have to do some messing around with pixman.h).  However, if I unplug the tablet and plug it back in, or simply don't have it plugged in when I boot, it doesn't work properly, only registering mouse motion when the stylus is pressed against the tablet.

How can I get the computer to recognize the tablet again, without rebooting?  I've heard that switching to a different tty with ctrl-alt-f1 will work, but that key combination doesn't seem to do anything on my computer.  Is there another way to recognize the tablet without a reboot?

---

### Post by Halberd on 2009-06-18
Edit:  I'm getting a strange problem when I try to paste my messages here, everything looks fine in my editing box but all the newlines get removed when my post shows up.  Here is my post on pastebin: 
[http://pastebin.com/m28ef581a](http://pastebin.com/m28ef581a)

---

### Post by padeco on 2009-07-05
hi there,

my tablet was working fine (see post #434) now i have no response at all. i attempted to go through the post again and follow step by step. no luck. how do you advise i go about this problem. is there any info you recommend i should post? any help would be much appreciated.

system - hardy 8.04
kernel - 2.6.24-24 generic

many thanks,
padeco

---

### Post by Favux on 2009-07-05
Hi padeco,

If there was a kernel and/or kernel header update that may have knocked out your install.  I don't know why you can't get it to reinstall.

But 0.8.0-3 linuxwacom is an old version to be using for a Wacom Bamboo.  You would be better off installing the 0.8.1-6 deb.s on Loic2's Wacom wiki.  They are near the top listed under "Ubuntu 8.10 (Intrepid Ibex)" but I think they will work on Hardy.  The Deb installer shouldn't let them load if there is a problem.  Find them here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

You have to be careful not to mix driver and wacom-tools versions, otherwise bad things can happen.  So you probably should uninstall the current drivers.  First type these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then change directory into the unpacked 0.8.0-3 linuxwacom tar you used.  Then change directory into the "prebuilt" folder.  Then in a terminal:
```
sudo ./uninstall
```
The 0.8.1-6 deb.s should copy over your current wacom.ko with the new wacom.ko so you shouldn't have to worry about it.

---

### Post by padeco on 2009-07-05
hi favux,

thanks for that info. i had another go at it and it is working now. yes, there was a linux header update, and i was not aware that the installation is specific with each update.

however, i installed LinuxWacom Kernel Driver ...0.8.2-2.tar.bz2, is this ok or should i revert to the .deb one that you recommended. once again, thanks for your attention.

cheers,
padeco

---

### Post by Favux on 2009-07-05
Hi padeco,

No that should be good.  Just remember if you compile to a kernel an update will "break" the wacom.ko (usb kernel driver specific to the kernel) and you need to recompile.  With the deb or an install through Synaptics you don't have to do that.  Since I can do a compile in about 5 minutes and the updates don't come through that often it just isn't that big a deal for me.

---

### Post by padeco on 2009-07-09
hi favux,

is there a way to make the tablet a permanent install that will work when you turn the system on, first time. some times, most times, i have to restart the system so that the tablet becomes active.

do you know if the wacom bamboo tablet offers pen sensitivity? 

many thanks,
padeco

---

### Post by Favux on 2009-07-09
Hi padeco,

You're on Hardy right?  Then you should use the hotplug commands:  ctrl-alt-F1 followed by ctrl-alt-F7.  That should get your usb tablet recognized.

As far as I know all Wacom tablet's have pressure, including the Bamboo.

---

### Post by padeco on 2009-07-09
hi favux,

i tried the short keys that you recommended and it does not work, so i have to restart the system.

with regards to the pressure sensor, where do you recommend i go to find out further info, i don't think my system is responding to any pressure variation. once again, thanks for all your help.

cheers,
padeco

---

### Post by Favux on 2009-07-10
Hi padeco,

Sorry to hear that.  Those commands still work for me in Intrepid.  Occasionally when I come out of suspend my digitizer isn't recognized and I just do that.

Have you calibrated your tablet through wacomcpl?  That generates a PressCurve in the .xinitrc where it stores settings.  The .xinitrc is a hidden file in "/home/username/" that stores the xsetwacom commands to configure your tablet.

To set it up see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
More on xsetwacom stuff here:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

Or maybe you're not setting Gimp or Inkscape up right.  See near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by padeco on 2009-07-10
hi favux,

thanks for the hint, i did not set up gimp properly! now it is all good. i will have a look at the table calibration later, it seems to be quite well tuned as it is.

cheers,
padeco

---

### Post by Estroyer on 2009-07-12
My Wacom Tablet Bamboo works perfect with the newest Ubuntu install. But what I can't find out is how I can assign the button commands, the speed of the pen and how to make the pointer drag from the same place where I left it after I lift the pen so I don't have to drag it all along the pad but instead move it in a few motions.
Is there a tab somewhere where I can adjust these settings?
Or do I have to go onto the codes?

---

### Post by Favux on 2009-07-12
Hi Estroyer,

Well the Wacom configuration and calibration gui (wacomcpl) is the closest to what you're talking about.  There are some older Wacom configuration programs out there, I don't know how well they work with Jaunty.  They seem to want to do things through xorg.conf still.

So you are probably have to get a little down and dirty to get things the way you want them.  To find out if you can use wacomcpl in a terminal enter:
```
xsetwacom list
```
that should return you linuxwacom names like stylus, eraser, cursor (if you have the Wacom mouse), and pad.  Then you can use wacomcpl.  If blank then to see what HAL is calling your Wacom input devices try:
```
xinput --list
```

---

### Post by Estroyer on 2009-07-12
I&#7743; a fast learner and not afraid to get dirty! I'm right on it and report back here :-)
Where can I get to the codes? I imagine it's something like the old DOS screen?

---

### Post by Favux on 2009-07-12
Hi Estroyer,

Right, using the terminal is very similar to a DOS box.  The terminal is in Applications>Accessories.

---

### Post by Estroyer on 2009-07-12
I don't want to spam this thread so if needed I am willing to figure it out through pm, just let me know, but maybe it can be of help to any other newbee?

I typed in the xsetwacom command and then I get this:

The program 'xsetwacom' is currently not installed.  You can install it by typing:
sudo apt-get install wacom-tools
bash: xsetwacom: command not found

When I type the command it askes me to ( to install it), it asks me for a password, but my regular Ubuntu password doesn't work here.

EDIT: it works now!
I'll get right back after I'm finished snooping about the codes!

I got the codings in front of me and it's not as bad as I expected it!
There is a logic in it so I expect to figure it out somehow.
As a newbe it's hard for me how to interpret some commands or what the counter command is in some cases.
First I'll experiment a bit with the number values in order to change the movements of the pen so I know what I'm looking at and it seems the most easiest thing to figure out at first.
Oh just a question: when I change a value, will it work immediately or do I have to save/reboot the laptop for changes to take place?

---

### Post by Favux on 2009-07-12
Hi Estroyer,

We aren't "suppose" to PM.  The idea is to post so others can see how we solved whatever we're trying to solve.  You could start a new thread if you wanted to.

The following assumes you're on a fresh Jaunty install and haven't compiled and installed linuxwacom drivers.  If you have tell me.  Go to Synaptic Package Manager (System>Administration>Synaptic).  Search "wacom".  You should see the two default Jaunty 0.8.2-2 linuxwacom packages.  The drivers xserver-xorg-input-wacom should be installed.  If not install them.  The other wacom-tools sounds like it isn't installed.  Tell Synaptic to install it.

---

### Post by Estroyer on 2009-07-12
I have started a new thread here as not to pirate this one :-)

[http://ubuntuforums.org/showthread.php?p=7605214#post7605214](http://ubuntuforums.org/showthread.php?p=7605214#post7605214)

---

### Post by deepesh on 2009-08-15
> **padeco said:**
> hi there,

my tablet was working fine (see post #434) now i have no response at all. i attempted to go through the post again and follow step by step. no luck. how do you advise i go about this problem. is there any info you recommend i should post? any help would be much appreciated.

system - hardy 8.04
kernel - 2.6.24-24 generic

many thanks,
padeco

Hi,
My Wacom bamboo is not working on kernel - 2.6.24-24 generic, but it works great on 2.6.24-22 generic. 

I do have to restart X if I plug the tablet after login. Otherwise it doesn't map to full screen (on 2.6.24-22).

Thanks,
Deepesh

---

### Post by deepesh on 2009-08-15
> **deepesh said:**
> Hi,
My Wacom bamboo is not working on kernel - 2.6.24-24 generic, but it works great on 2.6.24-22 generic. 

I do have to restart X if I plug the tablet after login. Otherwise it doesn't map to full screen (on 2.6.24-22).

Thanks,
Deepesh

Sorry to generate unnecessary noise. It is now working on 2.6.24-24 after I replaced the wacom.ko file in /lib/modules/2.6.24-24/kernel/input/tablet from the one in 2.6.24-22. I think that one was compiled using instructions found somewhere in this helpful forum :-).

Deepesh

---

### Post by mistyj on 2009-09-03
Hello,

The reason for my Bamboo Fun being unresponsive is beyond me at present. Any imput will be highly appreciated. 

[INDENT]misty@La:~$ lsusb | grep -i wacom
Bus 003 Device 002: ID 056a:0017 Wacom Co., Ltd 
[/INDENT]
The output after each step identified is as follows:

step4 :
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

step6: 
11:52:40 (214.95 KB/s) - `linuxwacom-0.8.0-3.tar.bz2' saved [977383/977383]

misty@La:~/wacom$ tar xjf linuxwacom-0.8.0-3.tar.bz2
misty@La:~/wacom$ cd linuxwacom-0.8.0-3sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
bash: cd: linuxwacom-0.8.0-3sudo: No such file or directory
misty@La:~/wacom$ sudo ln -s /usr/include/pixman-1/pixman-version.h /usr/include/pixman-version.h
misty@La:~/wacom$ bash: cd: linuxwacom-0.8.0-3sudo: No such file or directory
bash: bash:: command not found
misty@La:~/wacom$ ./configure --enable-wacom
bash: ./configure: No such file or directory
misty@La:~/wacom$ make
make: *** No targets specified and no makefile found.  Stop.
misty@La:~/wacom$ sudo make install

step 7: 
misty@La:~/wacom$ ./configure --enable-wacom
bash: ./configure: No such file or directory
misty@La:~/wacom$ make
make: *** No targets specified and no makefile found.  Stop.
misty@La:~/wacom$ sudo make install
make: *** No rule to make target `install'.  Stop.
misty@La:~/wacom$ 

step 13:
cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

step 15:
bash: cd: linuxwacom-0.8.0-3/prebuilt: No such file or directory
misty@La:~$ sudo ./uninstall
sudo: ./uninstall: command not found
misty@La:~$ sudo ./install
sudo: ./install: command not found

Step 17:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
misty@La:~$ sudo apt-get install wacom-tools xserver-xorg-input-wacom -y
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

step 18:
misty@La:~$ sudo ./uninstall
sudo: ./uninstall: command not found
misty@La:~$ cd ..
misty@La:/home$ sudo make install
make: *** No rule to make target `install'.  Stop.

Thank you for your consideration.

---

### Post by Favux on 2009-09-03
Hi mistyj,

Welcome to Ubuntu Forums!

It appears you are using Hardy, correct?

One problem may be:
```
cd linuxwacom-0.8.0-3sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
```
That's actually two lines.
```
cd linuxwacom-0.8.0-3
```
Enter (copy & paste) into the terminal and then hit enter.  Next line is:
```
sudo ln -s /usr/include/pixman-1/pixman.h /usr/include/pixman.h
```
And again hit enter or return.  You follow?  The lines are all like that.

Hope this helps.

---

### Post by mistyj on 2009-09-03
Hello Favux,

Thank you, I did just retry steps starting from 4 without the previous replies, but at step 7: install and uninstall this was the terminal's output:

[INDENT]misty@La:~/wacom$ ./configure --enable-wacom
bash: ./configure: No such file or directory
misty@La:~/wacom$ make
make: *** No targets specified and no makefile found.  Stop.
misty@La:~/wacom$ sudo make install
make: *** No rule to make target `install'.  Stop.
[/INDENT]Also, step 13:
[INDENT]misty@La:~/wacom$ cp /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko wacom.ko.`uname -r`
misty@La:~/wacom$ 
misty@La:~/wacom$ sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `linuxwacom-0.8.0-3/src/2.6.24/wacom.ko': No such file or directory

[/INDENT]Is there something I am simply not doing that is necessary? Perhaps a shut down is in order.

Thank you.
[U]


[/U]

---

### Post by Favux on 2009-09-03
Hi mistyj,

A reboot probably wouldn't hurt.  You're using Hardy (8.04), correct?

For that line I use:
```
./configure --enable-wacom --prefix=/usr
```
In my HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

When you encounter an error like:
```
misty@La:~/wacom$ ./configure --enable-wacom
bash: ./configure: No such file or directory
```
There isn't any point in continuing with commands.  That's why the next one says:
```
misty@La:~/wacom$ make
make: *** No targets specified and no makefile found. Stop.
```

---

### Post by tik-tik on 2009-09-11
Hello, 

 I have a problem with my Intuos 3 ... 
 after several test configuration (with your procedure too), I got to the point where my pen opens the basket every time. I tried to delete xorg.conf and again reinstall but without success. 

 Help - Thanks

---

### Post by grimace on 2009-09-12
My Wacom Bamboo tablet works well with one monitor (with 8.04).  As soon as I add my DipslayLink USB device and attach a second monitor things go wrong.  The tablet's left side now controls the cursor on the left side of my left monitor, and as I drag the pen across the tablet's center the cursor jumps across to the right side of my right monitor!

Does anyone have any suggestions on how to correct this?

---

### Post by Favux on 2009-09-12
Hi tik-tik,

Welcome to Ubuntu Forums!

I don't understand your question.  You are in Hardy (8.04) and using a xorg.conf with Wacom sections.  What does:
> my pen opens the basket every time
mean?  What did you delete?  The Wacom sections in xorg.conf?  What did you reinstall?


Hi grimace,

Did you put the lines to configure the Bamboo to the right screen in xorg.conf?   For an explanation see:  [http://linuxwacom.sourceforge.net/index.php/howto/multimonitor](http://linuxwacom.sourceforge.net/index.php/howto/multimonitor)  which links to:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

And to see some folks applying it (with cintiqs) see:  [http://ubuntuforums.org/showthread.php?t=1035029&&page=8](http://ubuntuforums.org/showthread.php?t=1035029&&page=8)  and the last page:  [http://ubuntuforums.org/showthread.php?t=1035029&page=10](http://ubuntuforums.org/showthread.php?t=1035029&page=10)

There are some bugs in linuxwacom and it also depends on the video card, which also have bugs.  So mileage varies.

Hope this helps.

---

### Post by uterrorista on 2009-09-17
```
make[2]: Entering directory `/home/qaz/.wacom/linuxwacom-0.8.0-3/src/xdrv'
gcc -g -O2 -I/usr/include/tcl  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \
		 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.c:79:
./xf86Wacom.h:26:25: error: xf86Version.h: No such file or directory
./xf86Wacom.c: In function ‘xf86WcmRegisterX11Devices’:
./xf86Wacom.c:582: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes integer from pointer without a cast
./xf86Wacom.c:582: error: too many arguments to function ‘InitValuatorClassDeviceStruct’
make[2]: *** [xf86Wacom.o] Error 1
make[2]: Leaving directory `/home/qaz/.wacom/linuxwacom-0.8.0-3/src/xdrv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/qaz/.wacom/linuxwacom-0.8.0-3/src'
make: *** [all-recursive] Error 1

```

How can i work around this?
@ step7: make

---

### Post by Favux on 2009-09-17
Hi uterrorista,

Linuxwacom 0.8.0-3 won't compile on Xserver 1.6 which Jaunty has.  The first version to compile on Jaunty would be 0.8.3-2.

What tablet are you trying to support?  The 0.8.2-2 linuxwacom (specially patched to support Xserver 1.6 and HAL) that comes with Jaunty works for every tablet but the Intous4.

---

### Post by grimace on 2009-09-18
> **Favux said:**
> 
Did you put the lines to configure the Bamboo to the right screen in xorg.conf? 


Thanks Favux! 

I was able to get my bamboo functioning well on either the left or right monitor, but not both at the same time.  Has anyone had any luck setting up the xorg.conf so that when you move the tablet's pen/cursor to the right of screen 0, it skips over to the left side of screen 1?

Also, I can only get my additional monitor to match the resolution of my laptop display.  The GUI on the added monitor states "RESOLUTION: OFF" and no amount of tweaking the xorg.conf file has given me a high resolution alternative.  arrrrrg...

here's my xorg.conf file... any suggestions would be much appreciated!

[HTML]
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"ScreenNo"	"1"
	Option		"MMonitor"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"		"on"
	Option		"ScreenNo"	"1"
	Option		"MMonitor"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"		"on"
	Option		"ScreenNo"	"1"
	Option		"MMonitor"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
	Option		"ScreenNo"	"1"
	Option		"MMonitor"	"on"
EndSection                                                                

Section "Files"
	ModulePath      "/dev/input/wacom"
	ModulePath      "/usr/lib/xorg/modules"
	ModulePath      "/usr/local/lib/xorg/modules"
EndSection

Section "Monitor"
	Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
	Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
	Monitor         "DisplayLinkMonitor"
	SubSection "Display"
		Virtual	0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier      "Server Layout"
	Screen  0       "Default Screen" 0 0
	Screen  1       "DisplayLinkScreen" RightOf "Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

Section "Device"
	Identifier      "DisplayLinkDevice"
	driver          "displaylink"
	Option  "fbdev" "/dev/fb0"
EndSection
[/HTML]

---

### Post by Favux on 2009-09-18
Hi grimace,

I'm far from an expert.  Do you have Intel video?
```
lspci | grep VGA
```

I think Intel has a virtual memory limit (add resolutions up) of 2048 x 2048 (but not a hundred percent sure) so for max. you're suppose to:
```
Subsection Display
     Virtual 2048x2048
EndSubsection
```
And is it right to have two "Device" sections?  Isn't that the video card?

---

### Post by grimace on 2009-09-18
This is my Intel Video Card....

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

According to the Intel site, the Graphics Media Accelerator 950 Graphics Core has a maximum resolution of 2048x1536 at 75 Hz.  So, if I add this ...

```
Subsection Display
     Virtual 2048x1536
EndSubsection
```

...where exactly would it be inserted?


> And is it right to have two "Device" sections?  Isn't that the video card?

My understanding is that one is for the laptop display, and the other for my DiskplayLink USB Multi-monitor adapter.  Should they be combined?

---

### Post by uterrorista on 2009-09-18
> **Favux said:**
> Hi uterrorista,

Linuxwacom 0.8.0-3 won't compile on Xserver 1.6 which Jaunty has.  The first version to compile on Jaunty would be 0.8.3-2.

What tablet are you trying to support?  The 0.8.2-2 linuxwacom (specially patched to support Xserver 1.6 and HAL) that comes with Jaunty works for every tablet but the Intous4.

```
qaz@blue:~/.wacom/linuxwacom-0.8.0-2$ lsusb | grep -i wacom
Bus 005 Device 002: ID 056a:0017 Wacom Co., Ltd 
```

I only want to configure the buttons that still aren't working!
Thank you.

---

### Post by Favux on 2009-09-18
Hi uterrorista,

Are you asking about setting up your tablet buttons, in other words the pad?  See post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  And it tells you about shatterblast's post #188 on the next page.  If instead you want to set things up through the wacom.fdi there's some posts on that page and the page before that should help.


Hi grimace,

Could we take a step back?

After reading back over your posts and looking at the xorg.conf I'm confused about what you're trying to do.  And you are only showing the relevant parts of the xorg.conf, correct?

You are in Hardy (8.04) with a Wacom Bamboo tablet.  You have a laptop (resolution?) and are setting a monitor (resolution?) up to the right of the laptop LCD using the usb device.

Are you setting up one big screen/desktop?  Or two separate screens?  Or are you trying to clone the laptop display to the monitor?

Do you want the stylus/eraser and Wacom mouse (cursor) to stay just on the right screen/monitor?  Or cross freely over both screens?

---

### Post by Favux on 2009-09-19
Hi grimace,

The first xorg.conf here:  [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen)  shows you where to put the 2048 x 2048.  And another Intel 945GM user in Hardy discusses it here:  [http://ubuntuforums.org/showthread.php?t=1140104](http://ubuntuforums.org/showthread.php?t=1140104)

---

### Post by grimace on 2009-09-21
Sorry, I should have been much more detailed in my explanation right from the beginning.

> **Favux said:**
> 

...you are only showing the relevant parts of the xorg.conf, correct?

My prior post shows the complete xorg.conf minus the ### sections at the head of the document.

> **Favux said:**
> You are in Hardy (8.04) with a Wacom Bamboo tablet.  You have a laptop (resolution?) and are setting a monitor (resolution?) up to the right of the laptop LCD using the usb device. Are you setting up one big screen/desktop?  Or two separate screens?  Or are you trying to clone the laptop display to the monitor?  Do you want the stylus/eraser and Wacom mouse (cursor) to stay just on the right screen/monitor?  Or cross freely over both screens?

I'm actually using 8.10 with the Bamboo tablet.  My I.O.DATA 22" display is attached via a Buffalo USB Multi-monitor adapter with a DisplayLink Chipset.  It is currently running as a second workspace to the right of my laptop, and not as a clone of my laptop's display.  It is now almost perfect.  My only unresolved issues are:

1) I am unable to change the resolution on the 22" monitor.  It is currently displaying the same resolution as the laptop's display (1280x800)  Ideally I'd like the 22" to be set to 1680x1050.

2) I'd like stylus/eraser and Wacom mouse (cursor) to cross freely over both screens.  At the moment the Bamboo works fine but is set to only function on 22" display.  I'm not sure what to tweak in the xorg.conf file to get the cursor to cross the screens freely.

---

### Post by Favux on 2009-09-21
Hi grimace,

OK, Intrepid with the Buffalo USB Multi-monitor adapter with a DisplayLink Chipset.  So the Buffalo amounts to a second video card?  And that's why you need a second "Device" section.

So you actually have two separate video cards each with their own monitor.  With one video card the default with Wacom is to cover both.  Most people want to confine the tablet to one monitor.

I'm definitely out of my depth.  It would be nice if someone would rescue us.  You may need to post on the Multimedia & Video forum.

I'm not sure, but you may need two instances of X11, both configured for linuxwacom, to do what you want.

Here's some links:

Good general one:  [http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors](http://en.gentoo-wiki.com/wiki/HOWTO_Dual_Monitors)

Klaus Knopper covers two video adaptors and two monitors:  [http://www.linuxpromagazine.com/Issues/2007/83/ASK-KLAUS/(kategorie)/0](http://www.linuxpromagazine.com/Issues/2007/83/ASK-KLAUS/(kategorie)/0)  and:  [http://www.linuxpromagazine.com/Issues/2008/95/ASK-KLAUS/(kategorie)/0](http://www.linuxpromagazine.com/Issues/2008/95/ASK-KLAUS/(kategorie)/0)  You download the pdf's.

If you figure it out I'd appreciate you filling me in.

---

### Post by grimace on 2009-09-23
Thanks for all the help and suggested reading.  I'm actually at a point where I can live with the dual monitor set up that I've currently got running.  Having the tablet only on one monitor is not that big a drawback, but the resolution on the 22" would be nice to set properly.  For anyone looking to run two monitors with a DisplayLink USB video device, I highly recommend this HOWTO...

[http://mulchman.org/blog/?p=21]("http://mulchman.org/blog/?p=21")


I'll post again here if I get any further with my resolution/tablet issues...

---

### Post by shnurui on 2009-09-25
Error in four?

what do I replace 'uname -r' with?

---

### Post by Favux on 2009-09-25
Hi shnurui,

`uname -r` just puts in your current kernel version.  You can see this by entering "uname -r" (without the quotes) into a terminal.

---

### Post by shnurui on 2009-09-25
> **Favux said:**
> Hi shnurui,

`uname -r` just puts in your current kernel version.  You can see this by entering "uname -r" (without the quotes) into a terminal.

Thanks.  It actually ran when I replaced that manually, for some reason it wasn't replacing it automatically.

---

### Post by shnurui on 2009-09-25
13 error =NSD or NSF

16 error 403, first line of code.

new version linuxwacom-0.8.4-2.tar.bz2 found at [http://prdownloads.sourceforge.net/linuxwacom/0.8.4-2/linuxwacom-0.8.4-2.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/0.8.4-2/linuxwacom-0.8.4-2.tar.bz2)

---

### Post by Favux on 2009-09-25
Hi shnurui,

I've been able to compile and install 0.8.4-2 in Intrepid using:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)  Does 0.8.4-2 install on Hardy?

---

### Post by shnurui on 2009-09-25
yes.

---

### Post by Favux on 2009-09-25
Hi shnurui,

Thanks.

Hardy uses 2.6.24 correct?  Maybe I should add:
```
sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
for Hardy to my HOW TO?

---

### Post by shnurui on 2009-09-26
> **Favux said:**
> Hi shnurui,

Thanks.

Hardy uses 2.6.24 correct?  Maybe I should add:
```
sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
for Hardy to my HOW TO?

I'm not sure, I'm a fairly novice, I just noticed that the new wacom was out, 9/18 and before vista decided it din't like my hd, the update made my pressure work in gimp.

I'm just hoping my pascal training will make it like moving from a 4 wheeler to a 2 wheeler:/:lolflag:

PS,

Where's the wiki for this thing?  Last time I tried, I screwed my video thuroughput and had to re-Reinstall, fortuneately, other than the restricted nvidia this is the only thing I tried to install.

---

### Post by shnurui on 2009-09-26
> **Favux said:**
> Hi shnurui,

Thanks.

Hardy uses 2.6.24 correct?  Maybe I should add:
```
sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
for Hardy to my HOW TO?

from my directory list it looks like it should be ./src/wacom.ko/2.6.24-24-generic
:confused:

Did you want me to try that? I'm using a fun, not a tablet screen.

no visible out put, no change, didn't redo everything, wouldn't know where it would go, in the sequence.

PS From inside the linuxwacom-0.8.4-2 directory it runs fine, no visible output though.

---

### Post by shnurui on 2009-09-26
File 403 forbidden on 16, is there a new location to get this file from, a new file to get?

:

All the info that goes in the "ServerLayout" section causes my computer to freeze on boot.

Recovery method removes the stuff from 9.

Result=  Pen works in limited area, mouse block doesn't work at all.

skipped step ten, ten is for tablet pc only-warning should be on it.

Result=Pen works like mouse block, mouse block doesn't work.[Lift and drag]

---

### Post by shnurui on 2009-10-05
So, throughout the thread, the real answer was missed.

Upgrade to 9.04+ Everything works, except the pressure is still wonky.

Will work on this next.

---

### Post by gerhard83 on 2009-10-06
Has anybody got a serial wacom tablet got to work in karmic64?

I have an Wacom Artpad II, which works fine in Windows on the same machine.
Wacdump works fine, but I can't get to work the tablet anywhere else.
I tried to compile the new linuxwacom driver myself, but that didn't help. Also I replaced the 10-wacom.fdi file with this one: [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)
The wacom module is loaded during startup, but no device seems to be accounted for.

xinput list shows:
virtual core pointer + keyboard
Logitech USB stuff
Power Button
Macintosh mouse button emulation

Any ideas?

Any help is appreciated!
Gerhard

---

### Post by gerhard83 on 2009-10-06
It works!

I found out, that according to: [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting), "newer" serial devices use the pnpbios to signal their presence to the system. Older ones, like my ArtPad II don't and therefore need extra info in the xorg.conf
Using the xorg.conf provided in the example on that page and changing "Default Screen" to "Configured Screen Device" I got my device to work.

It still doesn't do exactly as I want to, but hey, one step at a time.

---

### Post by osarusan on 2009-10-16
I have a new question that I think hasn't been asked here yet... I have two pens -- one is the standard stylus that came with my Cintiq, the other is the Felt-tipped pen style one. Right now they both work using the same parameters, but I'd like to be able to give the felt tipped pen a softer touch.

Looking at the linuxwacom page, I think it's possible if I use the "serial number" information in my configuration. However, I don't know how to find the serial number for the pens, and the manual for xsetwacom is too confusing for me.

I'm using xorg.conf to configure my wacom because it's difficult in TwinView otherwise. Is there a way I can add a second stylus through xorg?

---

### Post by Favux on 2009-10-16
Hi osarusan,

I think the command is:
```
xsetwacom get stylus ToolSerial
```
Which returns 0 for me.  But if I try:
```
xsetwacom getdefault stylus ToolSerial
```
I get -1.  I think the first one is right.

To use multiple styli try this wiki:  [http://cblfs.cross-lfs.org/index.php/Wacom](http://cblfs.cross-lfs.org/index.php/Wacom)

---

### Post by 10hp on 2009-10-16
in my pc does not work...

notebook hp 550
 wacom bamboo fun
release ubuntu 9.04
kernel 2.6.28-15-generic

at  7 stepl make install..return error..:

make[2]: *** [xf86Wacom.o] Error 1
make[2]: Leaving directory `/home/tony/wacom/linuxwacom-0.8.0-3/src/xdrv'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tony/wacom/linuxwacom-0.8.0-3/src'
make: *** [install-recursive] Error 1

at the step 6 to.. gksudo gedit /etc/X11/xorg.conf 
and at 8..the file is totelly different missing piece
.

last error... at 13 point..   sudo cp linuxwacom-0.8.0-3/src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 
the file do not exist

uff.. please give me help...

---

### Post by Favux on 2009-10-16
Hi 10hp,

Welcome to Ubuntu Forums!

You're using a Hardy HOW TO for Jaunty.  And the linuxwacom is pretty old.  You could try this HOW TO if you need to compile linuxwacom for some reason:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

But likely the Jaunty default linuxwacom packages should work fine for you  and it's newer.  You don't use xorg.conf in Jaunty, you use the HAL/.fdi method.  So it's probably a good thing you weren't able to compile and install.

A modified wacom.fdi and some explanation is at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Hope this helps.

---

### Post by 10hp on 2009-10-17
excuse me...:(:(
*thank's very much*. **...**we're the best!!!

---

### Post by osarusan on 2009-10-17
> **Favux said:**
> Hi osarusan,

I think the command is:
```
xsetwacom get stylus ToolSerial
```
Which returns 0 for me.  But if I try:
```
xsetwacom getdefault stylus ToolSerial
```
I get -1.  I think the first one is right.

To use multiple styli try this wiki:  [http://cblfs.cross-lfs.org/index.php/Wacom](http://cblfs.cross-lfs.org/index.php/Wacom)

Hi Favux,

Thanks for the reply!

```
xsetwacom get stylus ToolSerial
```
returned 94379391 for me... which is actually different from the serial number listed in wacomcpl... Hmmm. But it appears to work when I tell xorg to use that number for stylus0. Do you think this is correct?

However, for stylus1, I'm having less luck. Using the method described at the site you sent me, I thought I discovered the serial number of my art pen to be 90178677. However, after entering it into xorg and relogging in, it seems my computer can find stylus0 but not stylus1. Wacomcpl also returns stylus0 but not stylus1... Mysterious. Any ideas?




--Edit--

I figured it out. I had to set stylus1 to sendcoreevents. Now it shows up in wacomcpl with a separate serial number. I'm still clueless as to why the serial numbers displayed in wacomcpl are different than the ones in xsetwacom, but it appears to be working correctly. I haven't tested it in GIMP yet, but I'll do that in a few minutes, and if there are any problems I'll come back here and post them.

---

### Post by Favux on 2009-10-17
Hi 10hp,

Great!  It sounds like you're set up.  You're welcome.


Hi osarusan,

Good deal.  If you get it working in Gimp etc., could you expand on how you set things up a little?  You're the first person who's asked that question (as you noted) that I'm aware of.  :)

---

### Post by osarusan on 2009-10-20
> **Favux said:**
> Hi osarusan,

Good deal.  If you get it working in Gimp etc., could you expand on how you set things up a little?  You're the first person who's asked that question (as you noted) that I'm aware of.  :)

Sure, it was really easy actually. Once I had stylus0 and stylus1 defined in my xorg.conf, I was able to see both of them in Gimp, and set them both up normally.

I use the basic wacom pen for drawing, and I set it to have a stronger presscurve setting, while the art pen I use for painting, and it has a lighter presscurve setting. Gimp remembers each pen separately, including the color they last used, the brush they last used, and so on. Quite nice, actually.

---

### Post by Favux on 2009-10-20
Hi osarusan,

That does sound nice!

---

### Post by osarusan on 2009-10-25
Hey Favux, here's another question. I think there was a discussion on this a long while back, but I can't seem to find it.

Since my tablet is also a monitor, if I happen to turn off the monitor, the tablet turns off as well. When I turn the monitor back on, the tablet acts like it was just re-plugged in. Unfortunately this means it "forgets" the settings in my xorg.conf and acts like a new tablet, stretching across both my monitors and forgetting my customized pressure settings, etc.

Aside from "just don't turn off my monitor," is there any way that you know of to keep my tablet active? Or to have the computer remember the tablet's settings when it's reconnected, instead of treating it as a new device?

---

### Post by Favux on 2009-10-25
Hi osarusan,

Seems like a hardware shortcoming.  Why didn't they make it so you could turn off the LCD without turning off the digitizer?

Well, as you know that's what the .fdi is supposedly for.

I don't really know.  A quick google didn't turn up much, but I probably don't know the right key words.

You can't really do it through xorg.conf.  The manual I use for writing udev rules talks about being able to call a program from a udev rule so I guess you could.  The program you'd call would be a script that duplicates the xorg.conf with xsetwacom rules.  You could pattern it on the old wdaemon.  That's the old hot plug daemon that they made for wacom tablets to use before Xorg supported hot plugging in Intrepid/Jaunty.  Seems pretty complicated.  Or maybe if you got lucky it would be just a simple symlink rule in udev that could intercept the Cintiq hot plug with a callout to the xsetwacom script, but still.

---

### Post by mortamus on 2009-10-28
Followed the instructions substituting 0.8.5 for the version (the latest as of today) but was unable to get the system to recognize the Bamboo. The Wacom Bamboo model number is CTL-460. There is no wacom in /dev/input.

$ ls /dev/input/
by-id    event1   event12  event2  event5  event8  mouse0  mouse3
by-path  event10  event13  event3  event6  event9  mouse1  mouse4
event0   event11  event14  event4  event7  mice    mouse2  uinput

but it does appear in the USB list:

$ lsusb | grep Wacom
Bus 005 Device 004: ID 056a:00d4 Wacom Co., Ltd 

And there is no /dev/ttyUSB0.

---

### Post by Favux on 2009-10-28
Hi mortamus,

Two problems.

To compile 0.8.5 you might want to try this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

The second is your Bamboo Pen is not yet supported by linuxwacom.  We are working on adding support in this thread [here]("http://ubuntuforums.org/showthread.php?t=1290251").  Ayuthia has basic stylus working (which is what you need) with the wcm_working_patch [here]("http://ubuntuforums.org/showpost.php?p=8129913&postcount=144").  He gives instructions on applying the patches to linuxwacom 0.8.4-3 there to.  And you can find a .fdi or xorg.conf [here]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384").

Hope this helps.

---

### Post by osarusan on 2009-11-04
Woot! I've got hotplugging working now. Favux, you were a big help. I had previously beed quite afraid of the wacom.fdi, but it wasn't too tricky. It took some trial-and-error, but I've got dual-monitor hot plugging supporting working *almost* perfectly using this custom fdi file:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">5,0,100,95</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
        <merge key="input.x11_options.Serial" type="string">94379391</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">0,5,95,100</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
      </match>
    </match>
  </device>

  <!--device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">0,5,95,100</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
        <merge key="input.x11_options.Serial" type="string">90178677</merge>
      </match>
    </match>
  </device-->

</deviceinfo>
```

I say *almst* perfectly because it only works for the first stylus. As you can see, I have an entry commented out for the second stylus there. When it's not commented out, HAL overrules the first stylus with the rules for the second one, meaning that *only* my second stylus is usable. So for now, I have it set so only my first stylus is usable.

I know that I have to give them separate names somehow... but I'm not sure how to do that. Back in xorg is was easy enough to do with the Identifier tag, but in with the fdi I can't seem to figure out where to do that.

I'm pretty sure it has something to do with the differences between the *match* and *merge* entries, but at this point, it's Greek to me.

I'm also not sure if I need to enter anything for the "pad" entry that I had in xorg... that's for the custom buttons on the tablet. Also, do I need to do anything to replace the "SendCoreEvents" entries that used to be in xorg?

---

### Post by Favux on 2009-11-04
Hi osarusan,

You're in Jaunty right?  Can you attach the working xorg.conf where you had both styli working?

> Also, do I need to do anything to replace the "SendCoreEvents" entries that used to be in xorg? 
No.  Everything Wacom related can/should be removed from the xorg.conf.

---

### Post by Favux on 2009-11-04
And looking at the .fdi I think we need to look at your "lshal>lshal.txt" with at least one stylus identified by serial number in the .fdi.  That may give us a line(s) to match to.

It would be cool if we get this to work.

---

### Post by osarusan on 2009-11-04
Actually I'm in Karmic now.

The wacom parts of my old xorg setup are as follows (I've since commented them out):

```
Section "InputDevice"
	Identifier	"stylus0"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option          "USB"   "on"
  	Option         	"MMonitor" "off"
	Option 		"TwinView" "horizontal"
	Option 		"TVResolution" "1600x1200,1680x1050"
	Option 		"ScreenNo" "0"
	Option  	"Serial"        "94379391"
EndSection

Section "InputDevice"
	Identifier	"eraser0"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option          "USB"   "on"
  	Option         	"MMonitor" "off"
	Option 		"TwinView" "horizontal"
	Option 		"TVResolution" "1600x1200,1680x1050"
	Option 		"ScreenNo" "0"
EndSection

Section "InputDevice"
	Identifier	"stylus1"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option          "USB"   "on"
  	Option         	"MMonitor" "off"
	Option 		"TwinView" "horizontal"
	Option 		"TVResolution" "1600x1200,1680x1050"
	Option 		"ScreenNo" "0"
	Option  	"Serial"        "90178677"
EndSection

Section "InputDevice"
	Identifier	"pad"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"pad"
	Option          "USB"           "on"
   	Option         	"MMonitor" "off"
	Option 		"TwinView" "horizontal"
	Option 		"TVResolution" "1600x1200,1680x1050"
	Option 		"ScreenNo" "0"
EndSection
```
and of course
```
Section "ServerLayout"
   InputDevice    "stylus0"	"SendCoreEvents"
   InputDevice    "eraser0"	"SendCoreEvents"
   InputDevice    "stylus1"	"SendCoreEvents"
   InputDevice    "pad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection
```

stylus1, being the felt-tipped marker style pen, had no eraser, which is why there is no eraser1 item.

And for lshal, here's the parts that show up when I search for "wacom":

```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'DTZ-2100'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 260  (0x104)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'DTZ-2100'  (string)
  usb_device.product_id = 63  (0x3f)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 260  (0x104)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 63  (0x3f)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  input.product = 'Wacom Cintiq 21UX'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '5,0,100,95'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.Serial = '94379391'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.x11_options.USB = 'on'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6/event6'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '0,5,95,100'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'eraser'  (string)
  input.x11_options.USB = 'on'  (string)
```

The first two entries, I don't know what they are.

Then comes my stylus, next is my "pad" -- the touch strips and buttons, next is the "cursor" which my tablet doesn't actually use, and finally comes the eraser.

There doesn't seem to be anything for the additional pen, and likewise, it doesn't respond when I touch it to the screen. However it does respond if I enter its serial number instead of my main stylus' serial number in the stylus entry (but then my main stylus becomes likewise unusable).

---

### Post by Favux on 2009-11-04
Hi osarusan,

Parent and first daughter.

Ok, I have a .fdi roughed out.  But I don't see anything to match to, to separate out the styli.  Could you do the "lshal>lshal.txt" with both styli active in the .fdi so we can see if there's anything.

The other thing is to make it work we have to do multiple info.callouts.  I don't know if that's allowed.

---

### Post by osarusan on 2009-11-04
This is a bit tricky, because I don't know where the best place to put the device is -- within the device tags as a new match, or within a new set of device tags.

First, I uncommented-out the device as it was written in the previous post, so the second stylus appears as a separate device. This is the output:

```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'DTZ-2100'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/004/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 260  (0x104)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'DTZ-2100'  (string)
  usb_device.product_id = 63  (0x3f)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.product = 'Wacom Cintiq 21UX'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  input.product = 'Wacom Cintiq 21UX'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '0,5,95,100'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.Serial = '90178677'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.x11_options.USB = 'on'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input10/event6'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '0,5,95,100'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'eraser'  (string)
  input.x11_options.USB = 'on'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 260  (0x104)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 63  (0x3f)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 1.1 (1.1) (double)
```

Now I'll try it again, putting the 2nd stylus just after the 1st stylus, within the same device tags:

```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'  (string)
  info.product = 'DTZ-2100'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/004/007'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 260  (0x104)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 7  (0x7)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'DTZ-2100'  (string)
  usb_device.product_id = 63  (0x3f)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 260  (0x104)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 7  (0x7)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 63  (0x3f)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  info.product = 'Wacom Cintiq 21UX'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0'  (string)
  input.product = 'Wacom Cintiq 21UX'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '0,5,95,100'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.Serial = '90178677'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.x11_options.USB = 'on'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input11/event6'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom Cintiq 21UX eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_3f_noserial_if0_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.KeepShape = 'off'  (string)
  input.x11_options.MMonitor = 'off'  (string)
  input.x11_options.PressCurve = '0,5,95,100'  (string)
  input.x11_options.ScreenNo = '0'  (string)
  input.x11_options.TPCButton = 'off'  (string)
  input.x11_options.TVResolution = '1600x1200,1680x1050'  (string)
  input.x11_options.Threshold = '1'  (string)
  input.x11_options.TwinView = 'horizontal'  (string)
  input.x11_options.Type = 'eraser'  (string)
  input.x11_options.USB = 'on'  (string)
```

As you can see, it's recognizing the Serial number that I entered in the options, and there's a very slight difference between the two lshal outputs, though I can't tell which one is better.

There seem to be a lot of variables when deciding upon where to enter the 2nd pen... I wonder where the correct location is?

Edit:
I also tried it like this:
```
<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">5,0,100,95</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
        <merge key="input.x11_options.Serial" type="string">94379391</merge>
      </match>
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">0,5,95,100</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
        <merge key="input.x11_options.Serial" type="string">90178677</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.USB" type="string">on</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">0,5,95,100</merge>
        <merge key="input.x11_options.MMonitor" type="string">off</merge>
        <merge key="input.x11_options.TwinView" type="string">horizontal</merge>
        <merge key="input.x11_options.TVResolution" type="string">1600x1200,1680x1050</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
      </match>
    </match>
  </device>


</deviceinfo>
```

And there was no change -- the 2nd device listed takes priority, regardless of where in the file it's entered... curious...

---

### Post by Favux on 2009-11-04
Hi osarusan,

Still don't see anything to match.  It would be nice if both styli could be active at the same time so lshal might show something.

To be sure I have the physical situation straight.  The stylus doesn't attach to the Cintiq with a physical data cord, does it?  Instead when you bring the stylus close enough to be "in proximity" the Cintiq reads the serial number for that stylus.  So you can only use one at a time.

The .fdi I've come up with is patterned on the one I gave you a long time ago from [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  But I don't think the match lines I used for the serial numbers are right and will work.  I don't think it works that way.  So it will probably break X.  Plus I don't know about the multiple info.callouts.  They might break X too.  If you want to try it be prepared to fix things from the command line.

But at least you can see what I'm thinking.  The other way would be to duplicate the stylus and eraser sections.  But then I don't know if we could get pad set up for both.  Does your Cintiq come with a Wacom mouse?  I can't remember.  I took it out to simplify the .fdi.

---

### Post by osarusan on 2009-11-04
Hey, it works! I tried both hotplugging and rebooting, and neither broke X.

Looking at the file, I expected the eraser would screw up, and it did (which is a good thing, because it worked how I expected). So all I have to do now is edit the line for the eraser to re-enable its TwinView settings.

Actually, I'm not sure if it's actually working correctly or not. Right now, both styluses are responding properly, but the same thing happens if I simply delete the serial number info from my original custom fdi. Also, wacomcpl still only shows 1 stylus, so I can't be sure that it's actually detecting 2 styluses, or if it's ignoring the lines relating to their serial numbers and custom pressure.

My styluses don't have cords -- the tablet detects them as they come close. And there's no mouse which comes with this tablet, so I don't need to cursor function. As for the pad, I think if we list it as a separate device rather than a subsection of the stylus, there should be no problem, right?

Also, is there a logic behind whether the eraser and pad are listed as separate devices?

*Edit:*
Actually, I'm sure it's not detecting two separate devices, because GIMP is only detecting one stylus, and both pressures feel identical.

*Edit again:*
This is very puzzling. The serial number is key here... but I'm totally stumped.
In xorg this was pretty easy because of the Identifier entry... is there any equivalent of that in HAL?

---

### Post by Favux on 2009-11-04
Hi osarusan,

Darn.  Well just the fact that it didn't break X I count as a triumph.  That's one of the things I was looking for in lshal:
```
Identifier	"stylus0"
```
or the equivalent to match to.

It seems like there should be a way.  You're suppose to be able to translate xorg.conf into a .fdi.  Maybe we're again getting to where the .fdi needs to call out a program or script to pick up the stylus.  Let's think on it.  Since that .fdi booted, maybe there is something to it.

Maybe the post #176 modified with your entries and the appropriate xsetwacom commands in a script would work.

---

### Post by osarusan on 2009-11-05
Yeah, we're definitely getting close.

I originally simply translated my xorg into the custom fdi file as it was explained in [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi) -- pretty straightforward.

Is there another place with any documentation on the custom fdi file? If we can just figure out how to name the separate devices, I think it would work.

---

### Post by Favux on 2009-11-05
Hi osarusan,

My links to the HAL 5.11 and 5.2 spec.s are broken.  Rearranging the site?

Anyway here you go:

[http://www.redhat.com/magazine/003jan05/features/hal/](http://www.redhat.com/magazine/003jan05/features/hal/)

[http://www.marcuscom.com/hal-spec/hal-spec.html](http://www.marcuscom.com/hal-spec/hal-spec.html)

[http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL)

---

### Post by osarusan on 2009-11-05
Thanks a lot for those links. I've been fooling around with it for a few hours and it's starting to become clearer to me.

It looks like there's no way to get it to work the way you were trying -- Serial is something that has to be manually entered, so it won't be able to detect the string, and any strings entered in the same device will overwrite the previous strings in that device.

I think we need to focus on the USB HID Interface section right above the stylus, rather than the stylus section. The objects pad, cursor, and eraser look to be children of the stylus, and the stylus is a child of the USB HID Interface.

There's a section called usb.num_interfaces set to 1... I don't know if that's what we're looking for or what, but I'm 90% sure that our answer lies in the parent of the stylus entry rather than the stylus entry itself.

---

### Post by Favux on 2009-11-05
Hi osarusan,

> It looks like there's no way to get it to work the way you were trying -- Serial is something that has to be manually entered, so it won't be able to detect the string, and any strings entered in the same device will overwrite the previous strings in that device.
That seems right and that's basically what I was trying to say.

You're probably right, but I seem to be leaning the other way.  If we're going to crawl out on the device tree branch to split the styli they have to be defined as wacom devices somehow, don't they?  I wonder if what we need is to append them as sub-devices like pad or eraser to the "main" stylus.  But I doubt hal-setup-wacom is setup to do that.

So maybe duplicate stylus and eraser sections paired (like the xorg.conf) and we try to use something in the parent to segregate them.  Hmmm.

---

### Post by Favux on 2009-11-05
Hi osarusan,

This one feels like it's more in the ballpark to me.  See what you think.

---

### Post by osarusan on 2009-11-05
It's close, but still not quite there. Splitting them into stylus0 and stylus1 only works if we can name them stylus0 and stylus1, but we can't do that without the product info.tag. I tried using the x11_identifier but it seems to have no effect.

Unless -- did you mean I should add stylus0 and stylus1 back into the xorg.conf and try it from there?

As for going up the device tree, I can't honestly say I know what I'm talking about here, but there are still two other wacom devices listed in lshal, "DTZ-2100," the base Wacom device, and "USB HID Interface," which is a child of DTZ-2100. Perhaps one of those holds the key?

For the time, it works fine enough with one stylus set up, so it's nothing I'm in a rush to accomplish. It would be cool, but it looks like it might be impossible to do... At least until HAL can detect the two styluses by their serial numbers.

---

### Post by Slancher on 2009-12-01
Thanks very much.  I've got a wacom ID 056a:0015 Wacom Co., Ltd and this tutorial worked perfectly.

---

### Post by thecec on 2010-02-18
I stumbled upon this tutorial just now and I can't wait to try it.

I believe that the best use for a tablet is Photoshop, which is not for Linux.

I tried using VirtualBox, but it was still not usable due to some lag when moving layers around (3D is still experimental), but I got a reply by *jefro* on this thread:

[Adobe CS4 on Ubuntu 8.10 or any Gnome capable Linux]("http://www.linuxquestions.org/questions/linux-software-2/adobe-cs4-on-ubuntu-8.10-or-any-gnome-capable-linux-692819/")

which gave me a very interesting thing to try: install CS4 on VBox, then copy the appropriate directories to your wine installation.
As last step import some registry keys and you should be ready to go. 

See the detailed instructions [_here_]("http://maketecheasier.com/how-to-install-dreamweaver-cs3-in-ubuntu-hardy/2008/06/20")

---

### Post by Sciamano on 2010-02-18
I don't see why limiting this to Gnome-based linux installation.
It should work fine on KDE and other DE's too.

---

### Post by thecec on 2010-02-18
@Sciamano

Yes, I definitely agree with you. In fact I'm using KDE :p 
I just wanted to keep the original title to give the credits.

But you are right, I should have said that it was not limited to Gnome, I'm sorry for being misleading and thanks for making me notice that!

---

### Post by Sciamano on 2010-02-18
@thecec: I know it was the title of the thread you were referring to. BTW, I was not criticizing you, but just pointing out that it was somewhat a silly title! :)

---

### Post by thecec on 2010-02-18
@Sciamano
;) yes it was a silly title :p

---

### Post by breutsen on 2010-05-22
Hi all,

first, excuse my english spoken, i'm a french student.
I'm on ubuntu 8.04 hardy heron, I spent several hours trying to install my bamboo pen CTL-460.
I finally found a solution for me. I don't know if this message could help anyone, but here is the solution i found : 

  - install the linux header 2.6.24-27 (i really don't know why, but it don't work with any previous version).
 - get the lastest version of the driver  :  linuxwacom-0.8.7-1.tar.bz2  instead of linuxwacom-0.8.0-3.tar.bz2.

 - Follow exactly the first post of this topic , by replacing the folder name  linuxwacom-0.8.0-3 by linuxwacom-0.8.7-1 .

It works !

have fun


god is not real unless it is explicitly declared

---

### Post by manussa on 2010-10-23
Hello, all
How could i install  linuxwacom-0.8.8-10 instead my  linuxwacom 0.7.9.8-0? I try  to do it like in the first post and falure :(

  
I couldn't  do it with 
sudo apt-get update
a lot of Warning mistakes 

and a t that step also have something like
 
/usr/include/pixman-version.h./configure --enable-wacom
ln: unrecognized option `--enable-wacom'
&#1055;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1081;&#1090;&#1077; `ln --help' &#1076;&#1083;&#1103; &#1087;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1080;&#1103; &#1073;&#1086;&#1083;&#1077;&#1077; &#1087;&#1086;&#1076;&#1088;&#1086;&#1073;&#1085;&#1086;&#1075;&#1086; &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1103;.
udhacha@udhacha-laptop:~/wacom$ make
bash: make: &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1072; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;&#1072;
udhacha@udhacha-laptop:~/wacom$ sudo make install
sudo: make: command not found
udhacha@udhacha-laptop:~/wacom$

thank you for answer and sorry for my mistakes i am russian speaking

---

### Post by Favux on 2010-10-23
Hi manussa,

Welcome to Ubuntu forums!

Please see the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Hope this helps.

---

### Post by manussa on 2010-10-24
Hi Favux
I'll try your recipe  
I have a bamboo cth-661
is it a **serial tablet or usb tablet?**
Thank you

---

### Post by Favux on 2010-10-24
That is a usb Bamboo Pen and Touch tablet called the Bamboo Fun.  If you are in Lucid or Maverick please use the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by manussa on 2010-10-24
Hi Favux
I'll try your recipe  
I have a bamboo cth-661
is it a **serial tablet or usb tablet?**
as I understand its usb 

I have done the intallation according  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

I thnink everything was ok  but at the step 5

./configure --enable-wacom 

make

I have that:

udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ ./configure --enable-wacom 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ make

is it correct?
after that    sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 


Ihave that 
bash: makesudo: &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1072; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;&#1072; (command not found)
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
something wrong i think 
 
I checked folders I have all that path from src to wacom.ko
What went wrong?
I am on Hardy Heron 8.04     (Runtu LXDE )
Thank you

---

### Post by Favux on 2010-10-24
Hi manussa,

> configure: error: no acceptable C compiler found in $PATH
Seems to indicate you don't have gcc (gnome C compiler) installed or it is on the wrong path.

It should have been installed by:
```
sudo apt-get install build-essential
```
in
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```

---

### Post by manussa on 2010-10-25
Hi Favus!
glad to hear from you
 after I use   the code you give ( here a lot of in Russian sorry)
but it said that I should  use the CD Runtu Office Pro ( its my distribute< but I cant cause my CDrom is not reading well)  do you have any recipe how to get that compiler from internet not from CD?
 
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1041;&#1091;&#1076;&#1091;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1076;&#1086;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;:
  binutils dpkg-dev g++ g++-4.2 gcc gcc-4.2 libc6-dev libgomp1
  libstdc++6-4.2-dev libtimedate-perl linux-libc-dev make patch
&#1055;&#1088;&#1077;&#1076;&#1083;&#1072;&#1075;&#1072;&#1077;&#1084;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;:
  binutils-doc debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc
  libstdc++6-4.2-dbg autoconf automake1.9 bison flex gcc-doc gcc-multilib gdb
  libtool manpages-dev gcc-4.2-locales gcc-4.2-multilib libgcc1-dbg
  libgomp1-dbg libmudflap0-4.2-dev libmudflap0-dbg glibc-doc
  libstdc++6-4.2-doc make-doc ed diff-doc
&#1053;&#1054;&#1042;&#1067;&#1045; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099;:
  binutils build-essential dpkg-dev g++ g++-4.2 gcc gcc-4.2 libc6-dev libgomp1
  libstdc++6-4.2-dev libtimedate-perl linux-libc-dev make patch
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 14 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1089;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; 0B/11,0MB &#1072;&#1088;&#1093;&#1080;&#1074;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1077;&#1085;&#1080;&#1103; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080; &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 44,7MB.
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1044;/&#1085;]? &#1076;
&#1057;&#1084;&#1077;&#1085;&#1072; &#1085;&#1086;&#1089;&#1080;&#1090;&#1077;&#1083;&#1103;: &#1074;&#1089;&#1090;&#1072;&#1074;&#1100;&#1090;&#1077; &#1076;&#1080;&#1089;&#1082; &#1089; &#1084;&#1077;&#1090;&#1082;&#1086;&#1081; 'Runtu Office Pro - Release i386' &#1074; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; '/cdrom/' &#1080; &#1085;&#1072;&#1078;&#1084;&#1080;&#1090;&#1077; &#1074;&#1074;&#1086;&#1076;

Thank you for helping me

---

### Post by willyboy666 on 2010-10-25
hi everybody,

how to calibrate Wacom touchscreen (p.s with the out of box driver)

I installed Ubuntu 10.10 om my Gateway an the touch screen works perfectly ( just need a small calibration).

should i install the newest driver to be able to calibrate??? 

thanks

---

### Post by Favux on 2010-10-25
Hi manussa,

You should be able to use:
```
sudo apt-get install gcc
```


Hi willyboy666,

Which Gateway tablet pc do you have?  In addition to the stylus does it have touch also?

You can use xinput_calibrator:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)  Then place the coordinates you get into a xsetwacom script.

---

### Post by manussa on 2010-10-25
Hi Favux
I ve used the command  sudo aptget install gcc

and the result was 

udhacha@udhacha-laptop:~$ sudo apt-get install gcc
[sudo] password for udhacha: 
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1076;&#1083;&#1103; &#1080;&#1089;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103; &#1101;&#1090;&#1080;&#1093; &#1086;&#1096;&#1080;&#1073;&#1086;&#1082; &#1074;&#1099; &#1079;&#1072;&#1093;&#1086;&#1090;&#1080;&#1090;&#1077; &#1074;&#1086;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100;&#1089;&#1103; `apt-get -f install':
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1080;&#1084;&#1077;&#1102;&#1097;&#1080;&#1077; &#1085;&#1077;&#1091;&#1076;&#1086;&#1074;&#1083;&#1077;&#1090;&#1074;&#1086;&#1088;&#1105;&#1085;&#1085;&#1099;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;:
  dpkg-dev: &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: binutils &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
            &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libtimedate-perl &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
            &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: patch (>= 2.2-1) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
  gcc: &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: gcc-4.2 (>= 4.2.3-1) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
E: &#1053;&#1077;&#1091;&#1076;&#1086;&#1074;&#1083;&#1077;&#1090;&#1074;&#1086;&#1088;&#1105;&#1085;&#1085;&#1099;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;. &#1055;&#1086;&#1087;&#1099;&#1090;&#1072;&#1081;&#1090;&#1077;&#1089;&#1100; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; 'apt-get -f install', &#1085;&#1077; &#1091;&#1082;&#1072;&#1079;&#1099;&#1074;&#1072;&#1103; &#1080;&#1084;&#1077;&#1085;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;, (&#1080;&#1083;&#1080; &#1085;&#1072;&#1081;&#1076;&#1080;&#1090;&#1077; &#1076;&#1088;&#1091;&#1075;&#1086;&#1077; &#1088;&#1077;&#1096;&#1077;&#1085;&#1080;&#1077;).
udhacha@udhacha-laptop:~$ 


as I understand  &#1085;&#1077;&#1091;&#1076;&#1086;&#1074;&#1083;&#1077;&#1090;&#1074;&#1086;&#1088;&#1105;&#1085;&#1085;&#1099;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080; means  unmet dependencies ( if my translation is good)

What should  I do?

---

### Post by Favux on 2010-10-25
It's starting to sound as if your version of Ubuntu, Runtu Office Pro, is very non-standard.  Maybe it deliberately does not have standard package support?  Or else your package support is broken.

-f means --fix-broken
>            Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8 ) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.

Have you tried 'apt-get -f install gcc' yet?

---

### Post by willyboy666 on 2010-10-26
> **Favux said:**
> Hi manussa,

You should be able to use:
```
sudo apt-get install gcc
```


Hi willyboy666,

Which Gateway tablet pc do you have?  In addition to the stylus does it have touch also?

You can use xinput_calibrator:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)  Then place the coordinates you get into a xsetwacom script.

Gateway 120x wacom touch ,pen and eraser ,
which xsetwacom script do you mean?
thanks

---

### Post by manussa on 2010-10-26
> **Favux said:**
> It's starting to sound as if your version of Ubuntu, Runtu Office Pro, is very non-standard.  Maybe it deliberately does not have standard package support?  Or else your package support is broken.

-f means --fix-broken

Have you tried 'apt-get -f install gcc' yet?

I ve just done and ist ok  thank you  what should i do next? :) I am a little bit  mess up in all that

---

### Post by manussa on 2010-10-26
[http://ubuntuforums.org/showpost.php?p=7093065&postcount=104](http://ubuntuforums.org/showpost.php?p=7093065&postcount=104)
I am using that recipe for my bamboo is it right? 
til the point 6 was  everything ok  in my installation
but when i use    6 from section 1) Next we copy the module to the appropriate directory:  I ve got the next

udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; `./src/2.6.28/wacom.ko': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 

its said that there is no such file or folder :( But I check it EXIST ????!!!!! ( I mean wacom.ko)
  
     my path to wacom.ko is :  /lib/modules/2.6.24-28-generic/kernel/drivers/input/tablet/wacom.ko
and there is no /src/2.6.28/wacom.ko   at the beginning of this path

---

### Post by Favux on 2010-10-26
Hi willyboy666,
> Gateway 120x wacom touch ,pen and eraser ,
which xsetwacom script do you mean?
Except the xsetwacom coordinates the one for the TX2000 should basically work for you.  We can fine tune it as needed.  It's attached to the bottom of post #2 on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  See step IV. for installation instructions.


Hi manussa,
> I ve just done and ist ok thank you what should i do next?
Great!  It worked.  :)
> [http://ubuntuforums.org/showpost.php...&postcount=104](http://ubuntuforums.org/showpost.php...&postcount=104)
I am using that recipe for my bamboo is it right?
No.  That is for tablet pc's in Jaunty or Karmic.  You have Hardy, you use:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)  Section 1.  Especially since you're using linuxwacom 0.8.8-10.  The dependency line isn't complete for 0.8.8-10 and you need to do a 'sudo make install'.

The copy (cp) line is wrong for Hardy.  You will use:
```
sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by manussa on 2010-10-26
Hi Favux 
Thank you for great help
Ok, now I m using  that  recipe
[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

I begin with **section 1**


1) Its ok I ve got it in my desktop
2)Here I have a lot of W errors (  I think this is not bad)

```
Ign http://ppa.launchpad.net hardy/main Translation-ru                         
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release.gpg                              
&#1042; &#1082;&#1077;&#1096;&#1077; http://packages.medibuntu.org hardy/non-free Packages                   
Ign http://download.virtualbox.org hardy/non-free Translation-ru               
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.infralinux.org hardy-backports/main Packages             
Ign http://ppa.launchpad.net hardy/main Translation-ru                         
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/restricted Packages                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/restricted Sources                      
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/main Sources                            
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/multiverse Sources                      
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/universe Sources                        
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:2 http://ppa.launchpad.net hardy Release [27,6kB]                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/universe Packages                       
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy/multiverse Packages                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/main Packages                   
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/restricted Packages             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/restricted Sources              
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/main Sources                    
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/multiverse Sources              
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/universe Sources                
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/universe Packages               
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-updates/multiverse Packages             
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/main Packages                 
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/restricted Packages           
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/universe Packages             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/multiverse Packages           
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/main Sources                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/restricted Sources            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:3 http://ppa.launchpad.net hardy Release [27,6kB]                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/universe Sources              
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-backports/multiverse Sources            
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:4 http://ppa.launchpad.net hardy Release [27,6kB]                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy Release                                  
Ign http://ppa.launchpad.net hardy/main Packages                               
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:5 http://download.virtualbox.org hardy Release [3457B]                
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/main Packages                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/restricted Packages            
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/restricted Sources             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/main Sources                   
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/multiverse Sources             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/universe Sources               
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/universe Packages              
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-security/multiverse Packages            
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/restricted Packages            
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/main Packages                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/multiverse Packages            
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/universe Packages              
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/restricted Sources             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/main Sources                   
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/multiverse Sources             
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.ubuntu.com hardy-proposed/universe Sources               
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Packages                
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages             
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
Err http://download.virtualbox.org hardy Release                 
  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages              
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086; 201B &#1079;&#1072; 2s (70B/c)                
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
W: &#1055;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1072; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1082;&#1077; &#1087;&#1086;&#1076;&#1087;&#1080;&#1089;&#1077;&#1081;. &#1048;&#1085;&#1076;&#1077;&#1082;&#1089;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099;, &#1073;&#1091;&#1076;&#1091;&#1090; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100;&#1089;&#1103; &#1080;&#1093; &#1089;&#1090;&#1072;&#1088;&#1099;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080;. &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; GPG: http://download.virtualbox.org hardy Release: &#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1086;&#1076;&#1087;&#1080;&#1089;&#1080; &#1085;&#1077; &#1084;&#1086;&#1075;&#1091;&#1090; &#1073;&#1099;&#1090;&#1100; &#1087;&#1088;&#1086;&#1074;&#1077;&#1088;&#1077;&#1085;&#1099;, &#1090;&#1072;&#1082; &#1082;&#1072;&#1082; &#1085;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;&#1085; &#1086;&#1073;&#1097;&#1080;&#1081; &#1082;&#1083;&#1102;&#1095;:
W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; http://apt.wicd.net/dists/hardy/Release.gpg  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; apt.wicd.net

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; http://apt.wicd.net/dists/hardy/extras/i18n/Translation-ru.bz2  &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1085;&#1072;&#1081;&#1090;&#1080; IP &#1072;&#1076;&#1088;&#1077;&#1089; &#1076;&#1083;&#1103; apt.wicd.net

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz  404 Not Found

W: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; http://download.virtualbox.org/virtualbox/debian/dists/hardy/Release  

W: &#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1080;&#1085;&#1076;&#1077;&#1082;&#1089;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099; &#1085;&#1077; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1083;&#1080;&#1089;&#1100;, &#1086;&#1085;&#1080; &#1073;&#1099;&#1083;&#1080; &#1087;&#1088;&#1086;&#1080;&#1075;&#1085;&#1086;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1099; &#1080;&#1083;&#1080; &#1074;&#1084;&#1077;&#1089;&#1090;&#1086; &#1085;&#1080;&#1093; &#1073;&#1099;&#1083;&#1080; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1099; &#1089;&#1090;&#1072;&#1088;&#1099;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080;
W: &#1042;&#1099; &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1079;&#1072;&#1087;&#1091;&#1089;&#1090;&#1080;&#1090;&#1100; 'apt-get update' &#1076;&#1083;&#1103; &#1080;&#1089;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103; &#1101;&#1090;&#1080;&#1093; &#1086;&#1096;&#1080;&#1073;&#1086;&#1082;
udhacha@udhacha-laptop:~/Desktop$ 
```> **Note**:  Starting with 0.8.5-11 add **libxrandr-dev** to the libraries/dependency line above because a wacom XRandR daemon was added.should I do that? where? and how?

> If you are **changing linuxwacom versions** the following is needed to clear the previous version (do not do in **Karmic**)Its ok I think

3) I have 2.6.24-28-generic
a) new version installed

b) is that all for Karmic? ( I skipped it)
4) Its ok I got unpacked linuxwacom on my desktop
5) I v got the next :
```
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.24-28-generic/build
checking kernel version... 2.6.24-28-generic
checking for kernel module support... yes
checking for Xlib... checking for X lib directory... found, /usr/lib
checking for XSERVER... checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg, and /usr/xc/include
checking for X... no
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... configure: WARNING: not found; tried /usr/include, tcl, and tcl8.4; 
***
*** The tcl development environment can not be found.
*** The header file tcl.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking for tk header files... configure: WARNING: not found; tried /tk.h and /usr/include/tk.h
***
*** The tk development environment can not be found.
*** The header file tk.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking ncurses/ncurses.h usability... no
checking ncurses/ncurses.h presence... no
checking for ncurses/ncurses.h... no
configure: WARNING: ncurses not available, ncurses UI disabled
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... configure: WARNING: tcl environment missing, libwacomxi not built
checking if wacdump should/can be built... configure: WARNING: ncurses environment missing, wacdump not built
checking if xidump should/can be built... yes, no ncurses
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... no
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... configure: WARNING: requires Xorg SDK or XFree86 build environment, wacom_drv not built
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.24
      kernel source - yes /lib/modules/2.6.24-28-generic/build
     XFree86 source - no 
           Xorg SDK - no 
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - no 
                 TK - no 
            ncurses - no

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - yes (no ncurses)
        libwacomcfg - yes
         libwacomxi - no
          xsetwacom - yes
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks -
----------------------------------------


Your wacom.ko will be available under 
    /home/udhacha/Desktop/linuxwacom-0.8.8-10/src/2.6.24

udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```after 
make

sudo make install

I have  

```
wacomcfg.c:83: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XListInputDevices&#8217;
wacomcfg.c:83: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:84: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;nDevCnt&#8217;
wacomcfg.c:86: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c: &#1053;&#1072; &#1074;&#1077;&#1088;&#1093;&#1085;&#1077;&#1084; &#1091;&#1088;&#1086;&#1074;&#1085;&#1077;:
wacomcfg.c:96: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected &#8216;)&#8217; before &#8216;*&#8217; token
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigTerm&#8217;
wacomcfg.c:127: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c:129: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XFreeDeviceList&#8217;
wacomcfg.c:129: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigListDevices&#8217;
wacomcfg.c:140: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceInfo&#8217; undeclared (first use in this function)
wacomcfg.c:140: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: (Each undeclared identifier is reported only once
wacomcfg.c:140: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: for each function it appears in.)
wacomcfg.c:140: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;info&#8217; undeclared (first use in this function)
wacomcfg.c:144: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: ISO C90 forbids mixed declarations and code
wacomcfg.c:150: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c:164: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;nDevCnt&#8217;
wacomcfg.c:166: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c:168: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;IsXExtensionDevice&#8217; undeclared (first use in this function)
wacomcfg.c:190: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;nDevCnt&#8217;
wacomcfg.c:192: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigOpenDevice&#8217;
wacomcfg.c:300: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDevice&#8217; undeclared (first use in this function)
wacomcfg.c:300: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;pDev&#8217; undeclared (first use in this function)
wacomcfg.c:301: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceInfo&#8217; undeclared (first use in this function)
wacomcfg.c:301: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;pDevInfo&#8217; undeclared (first use in this function)
wacomcfg.c:301: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;info&#8217; undeclared (first use in this function)
wacomcfg.c:301: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: &#1083;&#1077;&#1074;&#1099;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1085;&#1076; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080; `&#1079;&#1072;&#1087;&#1103;&#1090;&#1072;&#1103;' &#1085;&#1077; &#1080;&#1084;&#1077;&#1077;&#1090; &#1087;&#1086;&#1073;&#1086;&#1095;&#1085;&#1099;&#1093; &#1101;&#1092;&#1092;&#1077;&#1082;&#1090;&#1086;&#1074;
wacomcfg.c:302: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: ISO C90 forbids mixed declarations and code
wacomcfg.c:308: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c:312: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;nDevCnt&#8217;
wacomcfg.c:314: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDevs&#8217;
wacomcfg.c:338: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XOpenDevice&#8217;
wacomcfg.c:338: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:350: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigCloseDevice&#8217;
wacomcfg.c:359: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:360: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XFree&#8217;
wacomcfg.c:360: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigSetRawParam&#8217;
wacomcfg.c:369: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceResolutionControl&#8217; undeclared (first use in this function)
wacomcfg.c:369: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected &#8216;;&#8217; before &#8216;c&#8217;
wacomcfg.c:370: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceControl&#8217; undeclared (first use in this function)
wacomcfg.c:370: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;dc&#8217; undeclared (first use in this function)
wacomcfg.c:370: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:370: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;c&#8217; undeclared (first use in this function)
wacomcfg.c:376: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;DEVICE_RESOLUTION&#8217; undeclared (first use in this function)
wacomcfg.c:382: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XChangeDeviceControl&#8217;
wacomcfg.c:382: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:382: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:387: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;BadValue&#8217; undeclared (first use in this function)
wacomcfg.c:387: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;BadRequest&#8217; undeclared (first use in this function)
wacomcfg.c:396: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:396: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:408: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XSetDeviceMode&#8217;
wacomcfg.c:408: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:408: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; &#8216;WacomConfigGetRawParam&#8217;
wacomcfg.c:416: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceResolutionControl&#8217; undeclared (first use in this function)
wacomcfg.c:416: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected &#8216;;&#8217; before &#8216;c&#8217;
wacomcfg.c:417: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceResolutionState&#8217; undeclared (first use in this function)
wacomcfg.c:417: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;ds&#8217; undeclared (first use in this function)
wacomcfg.c:418: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: ISO C90 forbids mixed declarations and code
wacomcfg.c:424: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;c&#8217; undeclared (first use in this function)
wacomcfg.c:424: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;DEVICE_RESOLUTION&#8217; undeclared (first use in this function)
wacomcfg.c:430: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:430: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:431: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;XDeviceControl&#8217; undeclared (first use in this function)
wacomcfg.c:431: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:433: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;BadValue&#8217; undeclared (first use in this function)
wacomcfg.c:433: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;BadRequest&#8217; undeclared (first use in this function)
wacomcfg.c:439: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:454: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:455: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:456: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:464: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:476: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMCONFIG&#8217; has no member named &#8216;pDisp&#8217;
wacomcfg.c:476: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: &#8216;WACOMDEVICE&#8217; has no member named &#8216;pDev&#8217;
wacomcfg.c:477: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
wacomcfg.c:479: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: implicit declaration of function &#8216;XFreeDeviceControl&#8217;
wacomcfg.c:479: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: expected expression before &#8216;)&#8217; token
make[2]: *** [wacomcfg.lo] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/udhacha/Desktop/linuxwacom-0.8.8-10/src/util'
make[1]: *** [install-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/udhacha/Desktop/linuxwacom-0.8.8-10/src'
make: *** [install-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```&#1086;&#1096;&#1080;&#1073;&#1082;&#1072; means error          And here are a lot of errors :(
How could I correct them? or maybe  (Don't worry if this returns an error saying "wacom" is not loaded.  It just means you've never installed wacom before.)

after  that 

sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko 
I have that again :(

```
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; stat &#1076;&#1083;&#1103; `./src/2.6.24/wacom.ko': &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```there is now such  file or folder they say :( 

but > The bottom line is if the copy command doesn't work you need to locate the folder the compiled wacom.ko has appeared in and modify the copy (cp) command accordingly.what does it mean ?  What should I do?


sudo depmod -a
something was done but I don't see what

7) should I restart my computer here several times? or "restart" means start  from the begining of the step 6?  
after 
modinfo -n wacom
I v got that  
```
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ modinfo -n wacom
/lib/modules/2.6.24-28-generic/kernel/drivers/input/tablet/wacom.ko
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```modinfo -d wacom
I v got ```
 udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ modinfo -d wacom
USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```but I have Bamboo FUn?



8)     
lsmod
or
lsmod | grep wacom
 I have ```
 udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ lsmod
Module                  Size  Used by
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            74432  2 
libusual               20772  1 usb_storage
pppoe                  14528  2 
pppox                   4876  1 pppoe
wacom                  18048  0 
binfmt_misc            12808  1 
ppdev                  10372  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
video                  19856  0 
output                  4736  1 video
ppp_generic            29588  6 pppoe,pppox
slhc                    7040  1 ppp_generic
ipv6                  268164  12 
nls_iso8859_1           4992  3 
nls_cp437               6656  3 
vfat                   14464  3 
fat                    54556  1 vfat
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
container               5632  0 
af_packet              23812  4 
snd_es1968             30592  1 
gameport               16008  1 snd_es1968
snd_ac97_codec        101028  1 snd_es1968
serio_raw               7940  0 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm                78724  2 snd_es1968,snd_ac97_codec
snd_timer              24836  1 snd_pcm
snd_page_alloc         11400  2 snd_es1968,snd_pcm
snd_mpu401_uart         9728  1 snd_es1968
snd_rawmidi            25760  1 snd_mpu401_uart
snd_seq_device          9612  1 snd_rawmidi
snd                    56996  9 snd_es1968,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8800  1 snd
irtty_sir               9728  0 
radio_maestro           8960  0 
battery                14212  0 
sir_dev                17412  1 irtty_sir
ac                      6916  0 
button                  9232  0 
videodev               29440  1 radio_maestro
v4l2_common            18304  1 videodev
i2c_piix4               9612  0 
v4l1_compat            15492  1 videodev
intel_agp              25492  1 
i2c_core               24832  1 i2c_piix4
compat_ioctl32          2304  1 radio_maestro
yenta_socket           27276  2 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport_pc             36260  1 
agpgart                34760  1 intel_agp
evdev                  13056  5 
irda                  203196  2 irtty_sir,sir_dev
parport                37832  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  8 
ata_generic             8324  0 
ata_piix               19588  3 
uhci_hcd               27024  0 
pata_acpi               8320  0 
floppy                 59588  0 
e100                   37388  0 
mii                     6400  1 e100
usbcore               146412  6 usbhid,usb_storage,libusual,wacom,uhci_hcd
libata                159728  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151692  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36616  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ or
bash: or: &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1072; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;&#1072;
udhacha@udhacha-laptop:~/Desktop/linuxwacom-0.8.8-10$ lsmod | grep wacom 
wacom                  18048  0 
usbcore               146412  6 usbhid,usb_storage,libusual,wacom,uhci_hcd

```gksudo gedit /etc/modules
```
(gksudo:16985): Gtk-WARNING **: &#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100; &#1090;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; &#1074; module_path: «thinice»,
```it means that downloading  module  not foud in ....


Thats all i n section 1

---

### Post by Favux on 2010-10-26
```
sudo apt-get install libxrandr-dev
```
What is happening after you do?:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```
The line is long.  Get the entire line.

Are you running your "Hardy", Hardy Heron (8.04 LTS), in Virtual Box?

---

### Post by manussa on 2010-10-27
Hi Favux  I think something wrong here :
```
udhacha@udhacha-laptop:~$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
[sudo] password for udhacha: 
Sorry, try again.
[sudo] password for udhacha: 
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1059;&#1078;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072; &#1089;&#1072;&#1084;&#1072;&#1103; &#1085;&#1086;&#1074;&#1072;&#1103; &#1074;&#1077;&#1088;&#1089;&#1080;&#1103; build-essential.
&#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100;. &#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1074;&#1099; &#1087;&#1088;&#1086;&#1089;&#1080;&#1090;&#1077; &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1075;&#1086;,
&#1080;&#1083;&#1080; &#1078;&#1077; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1077; &#1085;&#1077;&#1089;&#1090;&#1072;&#1073;&#1080;&#1083;&#1100;&#1085;&#1091;&#1102; &#1074;&#1077;&#1088;&#1089;&#1080;&#1102; &#1076;&#1080;&#1089;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1080;&#1074;&#1072;, &#1075;&#1076;&#1077; &#1079;&#1072;&#1087;&#1088;&#1086;&#1096;&#1077;&#1085;&#1085;&#1099;&#1077; &#1074;&#1072;&#1084;&#1080;
&#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1077;&#1097;&#1105; &#1085;&#1077; &#1089;&#1086;&#1079;&#1076;&#1072;&#1085;&#1099; &#1080;&#1083;&#1080; &#1073;&#1099;&#1083;&#1080; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1099; &#1080;&#1079; Incoming.
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1072;&#1103; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;, &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1087;&#1086;&#1084;&#1086;&#1078;&#1077;&#1090; &#1074;&#1072;&#1084;:

&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1080;&#1084;&#1077;&#1102;&#1097;&#1080;&#1077; &#1085;&#1077;&#1091;&#1076;&#1086;&#1074;&#1083;&#1077;&#1090;&#1074;&#1086;&#1088;&#1105;&#1085;&#1085;&#1099;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;:
  libx11-dev: &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libxcb-xlib0-dev &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
E: &#1057;&#1083;&#1086;&#1084;&#1072;&#1085;&#1085;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;
udhacha@udhacha-laptop:~$ 
```

that's translation :

Reading package lists ... Finish
Building dependency tree
Reading state information ... Finish
Is already the newest version of the build-essential.
Some packages can not be installed. Perhaps you are asking for the impossible,
or using the unstable distribution that some required you
packages have not yet been created or been moved out of Incoming.
The following information may help you:

The following packages have unmet dependencies:
  libx11-dev: Depends: libxcb-xlib0-dev but it will not be installed
E: Broken packages
udhacha @ udhacha-laptop: ~ $&#1055;&#1088;&#1086;&#1089;&#1083;&#1091;&#1096;&#1072;&#1090;&#1100;
&#1053;&#1072; &#1083;&#1072;&#1090;&#1080;&#1085;&#1080;&#1094;&#1077;
 

I am using LXDE ( at the moment)  also have Open Box

---

### Post by TirxSg3ng on 2010-11-20
Content of xorg.conf

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice   "stylus"  "SendCoreEvents"
   InputDevice   "eraser"  "SendCoreEvents"
   InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
   InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
#  InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection
```

Devices List:

```

drwxr-xr-x 2 root root    120 2010-11-20 18:47 by-path
crw-rw---- 1 root root 13, 64 2010-11-20 18:47 event0
crw-rw---- 1 root root 13, 65 2010-11-20 18:47 event1
crw-rw---- 1 root root 13, 66 2010-11-20 18:47 event2
crw-rw---- 1 root root 13, 67 2010-11-20 18:47 event3
crw-rw---- 1 root root 13, 68 2010-11-20 18:47 event4
crw-rw---- 1 root root 13, 69 2010-11-20 18:47 event5
crw-rw---- 1 root root 13, 70 2010-11-20 18:47 event6
crw-rw---- 1 root root 13, 71 2010-11-20 18:47 event7
crw-rw---- 1 root root 13, 72 2010-11-20 18:47 event8
crw-rw---- 1 root root 13, 63 2010-11-20 18:47 mice
crw-rw---- 1 root root 13, 32 2010-11-20 18:47 mouse0
crw-rw---- 1 root root 13, 33 2010-11-20 18:47 mouse1

```

Doesn't Work. Basically, the device doesn't appear. Why? Can you help me?

---

### Post by Favux on 2010-11-20
Hi TirxSg3ng,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?  Which Wacom usb tablet do you have?

My first guess is the symlinks aren't working because you do not have the wacom.rules in udev.

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> Hi TirxSg3ng,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?  Which Wacom usb tablet do you have?

My first guess is the symlinks aren't working because you do not have the wacom.rules in udev.


Thank you for the welcome. My replies are:

- Ubuntu 8.40
- Bamboo Pen. ( "056a" so it should work ).

This is the content of udev:

```

10-wacom.rules
50-xserver-xorg-input-wacom.rules            
50-xserver-xorg-input-wacom.rules.dpkg-dist

```

Are you referring to this, is it right?

---

### Post by Favux on 2010-11-21
Hi TirxSg3ng,

OK.  By Bamboo Pen do you mean the CTL460 (Product ID = 0xd4) stylus only?  I'm going to assume so.  If so I have my Bamboo Pen and Touch CTH460 (Product ID = 0xd1) working in Hardy (8.04).

I don't recognize '10-wacom.rules'.  What's in it and where is it?  '50-xserver-xorg-input-wacom.rules' is where a symlink udev rule for your tablet should go.  Since Hardy still uses the old syntax I haven't tried to construct a symlink for my tablet because I would also have to include touch.  So I use the pci usb by-paths instead.  With the Pen we probably could construct a symlink for you if needed or wanted.

So for you the xorg.conf should look something like:
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
#	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option "Device" "/dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse
	Option		"Type"          "stylus"
	Option		"USB"           "on"               # USB ONLY
	Option		"Button2"	"2"  # make first button a middle click
	Option		"Button3"	"3"  # make second button a R click
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"stylus"	"SendCoreEvents"
EndSection
```
If that pci usb by-path doesn't work for you we'll have to determine what yours is.

The other issue is you have to compile and install a more recent linuxwacom than the default in Hardy.  Have you done this yet?  Which version of linuxwacom did you use?  In Hardy I used the latest linuxwacom 0.8.8-10 and I used the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> Hi TirxSg3ng,

OK.  By Bamboo Pen do you mean the CTL460 (Product ID = 0xd4) stylus only?  I'm going to assume so.  If so I have my Bamboo Pen and Touch CTH460 (Product ID = 0xd1) working in Hardy (8.04).

I don't recognize '10-wacom.rules'.  What's in it and where is it?  '50-xserver-xorg-input-wacom.rules' is where a symlink udev rule for your tablet should go.  Since Hardy still uses the old syntax I haven't tried to construct a symlink for my tablet because I would also have to include touch.  So I use the pci usb by-paths instead.  With the Pen we probably could construct a symlink for you if needed or wanted.

So for you the xorg.conf should look something like:
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
#	Option        "Device"        "/dev/input/wacom" # USB ONLY?
	Option "Device" "/dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse
	Option		"Type"          "stylus"
	Option		"USB"           "on"               # USB ONLY
	Option		"Button2"	"2"  # make first button a middle click
	Option		"Button3"	"3"  # make second button a R click
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"stylus"	"SendCoreEvents"
EndSection
```
If that pci usb by-path doesn't work for you we'll have to determine what yours is.

The other issue is you have to compile and install a more recent linuxwacom than the default in Hardy.  Have you done this yet?  Which version of linuxwacom did you use?  In Hardy I used the latest linuxwacom 0.8.8-10 and I used the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Thank you very much, because now it works! :) Can you help me to calibrate it? When I launch "wacomcpl" nothing appear in the devices list. Why?

---

### Post by Favux on 2010-11-21
Stylus should show up in wacomcpl because that's the identifier on the Wacom section in xorg.conf.  Are you seeing any error messages?  You may have not compiled with a needed dependency or dependencies.  Did you see any errors when you compiled?

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> Stylus should show up in wacomcpl because that's the identifier on the Wacom section in xorg.conf.  Are you seeing any error messages?  You may have not compiled with a needed dependency or dependencies.  Did you see any errors when you compiled?

This is what I see when I launch wacomcpl:

```

tir@tir-486:~/wacom/linuxwacom-0.8.8-10$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"

```

I did not see any error during the compiling... but I cannot say for sure :) The config.log file says that there were two errors, but due to the Xorg version. But I think it was only a check, because configure ended happily.

Instead maybe it's important to you to know that I am using the kernel 2.6.34-020634-generic, so not a "hardy-one".

I also tried that versions of modified fdi that you put online, but nothing changed.

---

### Post by Favux on 2010-11-21
What Xorg version are you using?

Let's see what the output of:
```
xinput --list
```
is.  And:
```
xsetwacom list
```

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> What Xorg version are you using?

Let's see what the output of:
```
xinput --list
```
is.  And:
```
xsetwacom list
```

This is the output of xinput --xlist:

```


tir@tir-486:~$ xinput --list
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Generic Keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Configured Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 9
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Synaptics Touchpad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 3
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"stylus"	id=4	[XExtensionDevice]

```

The output of the other command, instead, is empty :)

```

tir@tir-486:~$ xsetwacom list
tir@tir-486:~$ 

```

---

### Post by Favux on 2010-11-21
It looks like something is wrong with your install of the linuxwacom driver.  I think stylus should say [XExtensionKeyboard] in xinput list.  That may be why it's not showing up in xsetwacom list.

Let's take a look at your Xorg.0.log in /var/log.

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> It looks like something is wrong with your install of the linuxwacom driver.  I think stylus should say [XExtensionKeyboard] in xinput list.  That may be why it's not showing up in xsetwacom list.

Let's take a look at your Xorg.0.log in /var/log.

Here it is Xorg.0.log :

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux tir-486 2.6.34-020634-generic #020634 SMP Mon May 17 20:34:55 UTC 2010 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 21 23:48:56 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(**) |-->Input Device "stylus"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27ac card 1025,015b rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27ae card 1025,015b rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1025,015b rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1025,015b rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1025,015b rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1025,015b rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1025,015b rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1025,015b rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1025,015b rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1025,015b rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1025,015b rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1025,015b rev 02 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 10ec,8136 card 1025,015b rev 02 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 168c,001c card 105b,e008 rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 197b,2382 card 1025,015b rev 00 class 08,80,00 hdr 80
(II) PCI: 04:00:2: chip 197b,2381 card 1025,015b rev 00 class 08,05,01 hdr 80
(II) PCI: 04:00:3: chip 197b,2383 card 1025,015b rev 00 class 08,80,00 hdr 80
(II) PCI: 04:00:4: chip 197b,2384 card 1025,015b rev 00 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00005000 - 0x00005fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x77300000 - 0x783fffff (0x1100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x70000000 - 0x70ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x00004fff (0x2000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x76300000 - 0x772fffff (0x1000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x71000000 - 0x720fffff (0x1100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x75200000 - 0x762fffff (0x1100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x72100000 - 0x730fffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x74100000 - 0x751fffff (0x1100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x73100000 - 0x740fffff (0x1000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0x78480000/19, 0x60000000/28, 0x78500000/18, I/O @ 0x60c0/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x78400000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[1] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[2] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[3] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[4] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[5] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[6] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[7] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[8] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[9] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[10] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[11] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[12] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[13] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[14] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[15] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[21] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[22] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[23] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[24] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[1] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[2] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[3] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[4] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[5] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[6] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[7] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[8] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[9] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[10] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[11] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[12] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[13] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[14] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[15] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[21] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[22] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[23] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[24] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[5] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[6] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[7] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[8] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[9] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[10] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[11] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[12] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[13] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[14] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[15] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[21] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[27] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[28] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[29] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[30] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.8.8-9 $
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GME found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[5] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[6] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[7] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[8] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[9] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[10] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[11] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[12] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[13] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[14] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[15] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[20] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[21] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[27] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[28] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[29] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[30] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[5] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[6] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[7] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[8] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[9] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[10] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[11] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[12] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[13] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[14] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[15] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[16] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[23] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[24] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[30] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[31] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[32] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[33] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(--) intel(0): Linear framebuffer at 0x60000000
(--) intel(0): IO registers at addr 0x78480000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1024x600
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000400
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000203
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x00000010 to 0x000c0010
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x78500000 - 0x7853ffff (0x40000) MS[B]
	[1] 0	0	0x60000000 - 0x6fffffff (0x10000000) MS[B]
	[2] 0	0	0x78480000 - 0x784fffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x74100000 - 0x741000ff (0x100) MX[B]
	[8] -1	0	0x74100100 - 0x741001ff (0x100) MX[B]
	[9] -1	0	0x74100200 - 0x741002ff (0x100) MX[B]
	[10] -1	0	0x74100300 - 0x741003ff (0x100) MX[B]
	[11] -1	0	0x75200000 - 0x7520ffff (0x10000) MX[B]
	[12] -1	0	0x71000000 - 0x7100ffff (0x10000) MX[B]
	[13] -1	0	0x71010000 - 0x71010fff (0x1000) MX[B]
	[14] -1	0	0x78544400 - 0x785447ff (0x400) MX[B]
	[15] -1	0	0x78540000 - 0x78543fff (0x4000) MX[B]
	[16] -1	0	0x78400000 - 0x7847ffff (0x80000) MX[B](B)
	[17] -1	0	0x78500000 - 0x7853ffff (0x40000) MX[B](B)
	[18] -1	0	0x60000000 - 0x6fffffff (0x10000000) MX[B](B)
	[19] -1	0	0x78480000 - 0x784fffff (0x80000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] 0	0	0x000060c0 - 0x000060c7 (0x8) IS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[27] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[28] -1	0	0x000060a0 - 0x000060af (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00006020 - 0x0000603f (0x20) IX[B]
	[34] -1	0	0x00006040 - 0x0000605f (0x20) IX[B]
	[35] -1	0	0x00006060 - 0x0000607f (0x20) IX[B]
	[36] -1	0	0x00006080 - 0x0000609f (0x20) IX[B]
	[37] -1	0	0x000060c0 - 0x000060c7 (0x8) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 356096 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1424380 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0x78480000
(II) intel(0): [drm] ring buffer = 0x60000000
(EE) intel(0): I830 Dma Initialization Failed
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8071000 at 0xb73df000
(II) intel(0): [drm] Closed DRM master.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): Page Flipping disabled
(WW) intel(0): Failed to set up write-combining range (0x60000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 12582912 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x00c00000 (pgoffset 3072)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000005f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000005fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000005fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000005fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00c00000-0x017fffff: exa offscreen (12288 kB)
(II) intel(0): 0x10000000:            end of aperture
(WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(WW) intel(0): fbc already enabled on plane a, not enabling on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Failed
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) intel(0): Setting screen physical size to 195 x 113
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(**) Option "Device" "/dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse"
(WW) stylus: failed to open /dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse in wcmDeviceTypeKeys.
(EE) stylus: stat failed (No such file or directory). cannot check for duplicates.
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "Button2" "2"
(**) Option "Button3" "3"
(**) Option "BaudRate" "9600"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(EE) xf86OpenSerial: Cannot open device /dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse
	No such file or directory.
Error opening /dev/input/by-path/pci-0000:00:13.0-usb-0:2:1.0-event-mouse : No such file or directory
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
(WW) intel(0): fbc already enabled on plane a, not enabling on plane a
(EE) stylus: No type or invalid type specified.
Must be one of stylus, touch, cursor, eraser, or pad
(EE) PreInit returned NULL for "stylus"
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a

```

---

### Post by Favux on 2010-11-21
Alright you have X.Org X Server 1.4.0.90.  I think that's too early for a .fdi to work for you.

It looks like maybe the by-path isn't quite right for you.  Let's see if we can find it:
```
dmesg | grep Wacom
```
and
```
ls -l /dev/input/by-path
```
Let's also check for your product ID:
```
lsusb | grep [Ww]acom
```

---

### Post by TirxSg3ng on 2010-11-21
> **Favux said:**
> Alright you have X.Org X Server 1.4.0.90.  I think that's too early for a .fdi to work for you.

It looks like maybe the by-path isn't quite right for you.  Let's see if we can find it:
```
dmesg | grep Wacom
```
and
```
ls -l /dev/input/by-path
```
Let's also check for your product ID:
```
lsusb | grep [Ww]acom
```

dmesg | grep Wacom

```

tir@tir-486:/dev/input/by-path$ dmesg | grep Wacom
[   23.476238] input: Wacom Bamboo 4x5 Pen as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input8
[   23.510633] input: Wacom Bamboo 4x5 Finger as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input9
[   23.520513] wacom: v1.52-pc-0.3:USB Wacom tablet driver

```

This is the content of by-path: 

```


tir@tir-486:/dev/input/by-path$ ls -l
totale 0
lrwxrwxrwx 1 root root 10 2010-11-21 23:48 pci-0000:00:1b.0--event- -> ../event10
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 pci-0000:00:1d.1-usb-0:1:1.0-event-mouse -> ../event8
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 pci-0000:00:1d.1-usb-0:1:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 pci-0000:00:1d.1-usb-0:1:1.1- -> ../mouse2
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 pci-0000:00:1d.1-usb-0:1:1.1-event- -> ../event9
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 platform-i8042-serio-0-event-kbd -> ../event4
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 platform-i8042-serio-2-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 platform-i8042-serio-2-mouse -> ../mouse0
lrwxrwxrwx 1 root root  9 2010-11-21 23:48 platform-pcspkr-event-spkr -> ../event6

```

And my product id:

```

Bus 003 Device 002: ID 056a:00d4 Wacom Co., Ltd 

```

:)

---

### Post by Favux on 2010-11-21
Good, it's definitely a Bamboo Pen, product ID 00d4.

Try this by-path:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
```

For some more stuff see:  [http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)  The [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") is for Lucid and Maverick, so it doesn't really apply to you.  But has some information that may be of use.

---

### Post by TirxSg3ng on 2010-11-22
> **Favux said:**
> Good, it's definitely a Bamboo Pen, product ID 00d4.

Try this by-path:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
```

For some more stuff see:  [http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)  The [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") is for Lucid and Maverick, so it doesn't really apply to you.  But has some information that may be of use.

Good, now it works. Thank you very much for your help :)

---

### Post by cevin7 on 2011-02-17
i know this thread is a bit old but i have a problem 
 
the only thing that works on my wacom are the mouse buttons. i got an error with the ./install for the drivers.

i got this error

Error:  Failed to get system architecture Reason: uname, with options -i, -p, and -m, doesn't work properly 

this is the powerpc version of hardy.

i have attached the requested files

*edit never mind just had to uninstall mouse emu

---

