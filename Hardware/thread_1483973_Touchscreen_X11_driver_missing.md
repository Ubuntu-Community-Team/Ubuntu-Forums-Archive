---
title: "Touchscreen X11 driver missing"
date: 2010-05-15
forum: Hardware
---

### Post by lixy on 2010-05-15
Hey folks,

Just acquired an Acer Aspire 1825PTZ tablet and loaded 10.04 on it. Not only does the touchscreen not work, but it's not even properly recognized as an input device.

"xinput list" does not list the touchscreen as a pointer device:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF9011                                 	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

The relevant section from a "cat /proc/bus/input/devices".

```
I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b00000000 0 0 0

```


The relevant section from dmesg:

```

[12.901155] USB Video Class driver (v0.1.0)
[13.980995] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[13.981061] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)

```

This is bad. Very bad. It requires somebody skilled in the obscure art of kernel drivers to solve.

---

### Post by lixy on 2010-05-15
Ok. So I had to load Win7 to check the touchscreen model. Turns out the touchscreen driver is from ST Microelectronics. I'm clueless about how to find the model, but there shouldn't be many 11.6" multitouch capacitive touchscreen from them.

---

### Post by lixy on 2010-05-15
So...it looks like there's a bug filed for this already.

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/511747](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/511747)

Guessing that it's the same model, since it's a 11.6" multitouch capacitive touchscreen in an Acer.

---

### Post by lixy on 2010-05-15
.

---

### Post by lixy on 2010-05-15
So there's a patch in the wild.

[https://patchwork.kernel.org/patch/94542/](https://patchwork.kernel.org/patch/94542/)

I spent two hours looking for a newer kernel that included that patch in vain. So I tried it the hard way, but no success on that front either. I downloaded Steph's patch from the link above. The error message from running the patch is listed below.

```
ali@ali-tablet:/usr/src/linux-headers-2.6.32-21$ sudo patch p0 < Support-for-the-11.6-Cando-panel-found-on-the-Acer-1825PTZ.patch 
patching file p0
Hunk #1 FAILED at 235.
1 out of 1 hunk FAILED -- saving rejects to file p0.rej
patching file p0
Hunk #1 FAILED at 1274.
1 out of 1 hunk FAILED -- saving rejects to file p0.rej
patching file p0
Hunk #1 FAILED at 118.
1 out of 1 hunk FAILED -- saving rejects to file p0.rej

```

Anyone who can apply patches care to chime in?

---

### Post by StCh on 2010-05-15
This patch is really simple and nearly human readable (basically, it is the addition of a couple of lines in three different files). I was going to suggest that you apply it by hand.

But actually, your issue is worse than I thought: if you have a vanilla Lucid kernel, then:
 1) there's no hid-cando.c file at all
 2) you need a patch to {linux}/include/linux/hid.h

I *believe* the following patches should be enough:

- 8b0e58a70a7a41443c779de074288035b014cb94, which I can't find in patchwork
- [https://patchwork.kernel.org/patch/92471/](https://patchwork.kernel.org/patch/92471/)
- [https://patchwork.kernel.org/patch/93203/](https://patchwork.kernel.org/patch/93203/)
- [https://patchwork.kernel.org/patch/94542/](https://patchwork.kernel.org/patch/94542/)

St.

---

### Post by lixy on 2010-05-16
I hunted down the patch 8b0e58a70a7a41443c779de074288035b014cb94 and attached it here.

Then, I applied all four patches and compiled a new kernel. Upon rebooting, I get the following error:

```
Kernel panic - not syncing: VFS Unable to mount root fs on unknown-block(0,0)
```

Probably more related to my lack of expertise in the area than to the patches. 

Oh well...I gave it a shot anyway. Will have to patiently wait for this to be fixed upstream. I hope the kernel crew will not leave us hanging for too long.

---

### Post by StCh on 2010-05-16
Wow! I suspect that the boot problem does not come from the driver :-)

In theory you don't need to re-compile the whole kernel. You just need to go to drivers/hid and (re)build the hid and hid-cando modules. The command is "make -C ../.. SUBDIRS=`pwd`modules". Then you need to copy hid.ko and hid-cando.ko to /lib/modules/{your-kernel}/kernel/drivers/hid, and use rmmod/modprobe/insmod (plus a touch of depmod).

What might happen though is that you get warnings at compile time about missing files (such as Module.symvers). As far as I remember you can find them for your kernel somewhere in /lib/modules or in /boot. Or you can rebuild the whole kernel to produce them, but you don't need to install the resulting kernel.

---

### Post by nearo on 2010-05-16
does everything else work out of the box? webcam, wifi, screen rotation etc?

---

### Post by lixy on 2010-05-17
> **nearo said:**
> does everything else work out of the box? webcam, wifi, screen rotation etc?

You'll need a tiny script for the touchpad to be multitouch. But other than that, it works fine.

I don't know what "screen rotation" means though. I can rotate the screen through system > preferences > display if that's what you mean.

---

### Post by arobase40 on 2010-05-22
> **nearo said:**
> does everything else work out of the box? webcam, wifi, screen rotation etc?

If you're talking about the 1825PTZ and Ubuntu 10.04 lucid, as far as I know everything is working out of the box except the touchscreen and screen auto-rotation.
I have not tested HDMI and Bluetooth, but they might work...

I have compiled the touchscreen drivers and got the hid.ko and hid-cando.ko installed and loaded with modprobe but it does not work yet... :(

Edit : at least I got the touchscreen working (I have to play with rmmod and modprobe) but the pointer is completly out of sync with my finger and the mouse is not working anymore (mouse is moving but I can't click on anything... ^^
I have to unload hid-cando to get my mouse back.

Anyone knows what the coordinates in the xorg.conf should be ???

---

### Post by arobase40 on 2010-05-26
> **StCh said:**
> This patch is really simple and nearly human readable (basically, it is the addition of a couple of lines in three different files). I was going to suggest that you apply it by hand.

But actually, your issue is worse than I thought: if you have a vanilla Lucid kernel, then:
 1) there's no hid-cando.c file at all
 2) you need a patch to {linux}/include/linux/hid.h

I *believe* the following patches should be enough:

- 8b0e58a70a7a41443c779de074288035b014cb94, which I can't find in patchwork
- [https://patchwork.kernel.org/patch/92471/](https://patchwork.kernel.org/patch/92471/)
- [https://patchwork.kernel.org/patch/93203/](https://patchwork.kernel.org/patch/93203/)
- [https://patchwork.kernel.org/patch/94542/](https://patchwork.kernel.org/patch/94542/)

St.

Did you get the touchscreen working easyly and well integrated to  Xorg ?

I have tried the way the owner of the LenoVo S10-3T did as they have the same touchscreen, but it seems not to work the same way as the 1825PTZ : I added some informations in hal (which gives much more informations about the panel), I compiled xf86-input-hidtouch and loaded it through xorg.conf but I have not visble actions on screen (no mouse pointer moving), but I have some feedback with hidDeviceDump...:confused:

---

### Post by Castor456 on 2010-06-12
It's work !! But I'm an Gentoo/Debian user.

I use the latest RC of kernel Linux 2.6.35 with the Canda hid touchscreen module, then I upgrade xf86-input-evdev to 2.4.0 (2.3.2 dont work). I have just configure my xorg.conf like that :
```
Section "InputDevice"
        Identifier "Touchscreen"
        Driver          "evdev"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event9"
EndSection
```
It's done, no calibrate needed :)

---

### Post by arobase40 on 2010-06-14
Got it working too, but it was a little bit more difficult due to a compatibility problem with xorg-input server and library causing a calibration issue.
):P

Even if this works with any events, the true event that handles the touchscreen is event5...
:guitar:

---

### Post by nearo on 2010-06-15
So everything works with an up-to-date version of Debian?
How is the battery life when running Linux? Acer claims a battery life of 8+ hours.

---

### Post by lixy on 2010-06-16
I installed Kernel 2.6.35-rc3 on a fresh Maverick alpha1 install, and I'm able to move the cursor on the touch screen. Out of the box! Which is pretty neat. 

The left mouse click doesn't work though (not just upon tapping the screen, but also when clicking on the touchpad or with an external mouse). This is probably an issue in Maverick, as I noticed erratic left mouse behavior during the 10.10 installation process. 

Battery life varies between 4 and 6 hours depending on usage. I'm surprised at how loud the machine is - the fan seems to be running non-stop (under Windows 7 as well). Despite that, I'll say it's good value for the money (or it could be [post-purchase rationalization]("http://en.wikipedia.org/wiki/Post-purchase_rationalization")).

---

### Post by arobase40 on 2010-06-16
> **nearo said:**
> So everything works with an up-to-date version of Debian?
How is the battery life when running Linux? Acer claims a battery life of 8+ hours.

As much as I know with Debian and Gentoo you have to do most of the work by hands whilst this works out of the box with Ubuntu except the touchscreen... ^^

I don't know much about battery life as I work most of the time with the power supply for the moment. :p

---

### Post by arobase40 on 2010-06-16
> **lixy said:**
> I installed Kernel 2.6.35-rc3 on a fresh Maverick alpha1 install, and I'm able to move the cursor on the touch screen. Out of the box! Which is pretty neat. 

The left mouse click doesn't work though (not just upon tapping the screen, but also when clicking on the touchpad or with an external mouse). This is probably an issue in Maverick, as I noticed erratic left mouse behavior during the 10.10 installation process. 

Battery life varies between 4 and 6 hours depending on usage. I'm surprised at how loud the machine is - the fan seems to be running non-stop (under Windows 7 as well). Despite that, I'll say it's good value for the money (or it could be [post-purchase rationalization]("http://en.wikipedia.org/wiki/Post-purchase_rationalization")).

I really don't like Maverick, so I stopped the try after Alpha1.

My 1825ptz is very silent, so I guess there is a problem with your machine... ^^

---

### Post by arobase40 on 2010-06-19
> **Castor456 said:**
> It's work !! But I'm an Gentoo/Debian user.

I use the latest RC of kernel Linux 2.6.35 with the Canda hid touchscreen module, then I upgrade xf86-input-evdev to 2.4.0 (2.3.2 dont work). I have just configure my xorg.conf like that :
```
Section "InputDevice"
        Identifier "Touchscreen"
        Driver          "evdev"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event9"
EndSection
```
It's done, no calibrate needed :)

Beware, looks like the xf86-input-evdev 2.4.0 is only a monotouch driver and another result is very slow scrolling in softwares like Okular or Acrobat Reader, no scrolling in Google Chrome, and some other problems... :-k[-X

---

### Post by rizzly on 2010-07-25
So I just installed Maverick alpha 2, and just like lixy I can move the cursor as if the screen was a touchpad, no more, no less. 

Unfortunetly it doesn't seem to recognize the touchscreen as a cando panel, alpha 2 should have the necessarry cando-patch for our screen to work, no? My idea behind the screen not being registered as a cando-panel is that when type lsmod in the terminal it says that hid_cando is used by 0.

So, I tried to just add the lines to xorg.conf described earlier, wich didn't work. Right now I'm trying to install xf86-input-evdev-2.4, but am stuck on this when trying to autoconf it:

```
./configure: line 11714: syntax error near unexpected token `XINPUT,'
./configure: line 11714: `XORG_DRIVER_CHECK_EXT(XINPUT, inputproto)'

```Any ideas?

EDIT:

Nevermind, all solved by doing this: [http://ubuntuforums.org/showpost.php?p=9538094&postcount=2](http://ubuntuforums.org/showpost.php?p=9538094&postcount=2)

---

### Post by arobase40 on 2010-07-31
I'd like to add a new solution for those who would like to activate the touchscreen of the Acer 1825pt(z) but have problem to compile the xf86-input-evdev 2.4.0 drivers, on a (K)ubuntu 10.04 Lucid basis. It might work on a Maverick version even tough I have'nt tested it...

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

Here you have all the instructions to both upgrade your intel drivers (for hardware of h264 video acceleration) and activate the touchscreen using a 2.6.35-rc(n) kernel. Kernel 2.6.35-rc1 does not contain any cando drivers (drivers for the touchscreen). So the latest version you installed, the better it is.
The latest version from this day now is 2.6.35.rc6...

If you follow all the instructions from above your system should also upgrade with the xf86-input-evdev 2.4 drivers with no need to compile anything and the touchscreen will work with no need of calibration, and even no need to generate a xorg.conf file.

BUT... the monotouch drawback remains the same... for now... ^^

Regarding the screen rotation, Tomfrancart wrote a script which does the job.
It is not a auto rotate way yet, but still it is an elegant way as he uses the P-button which exists on the 1825pt(z) panel and some other Acer laptops.

to do so, just follow the link given by rizzly just above this message...

For the auto-rotate screen, i'll try to find a solution based on what exists on my Fujitsu P1610, but I guess it will take some time...

Just in case anyone has more time or is smarter than me... ^^ ;)
here is the start point :

[http://fjbtndrv.git.sourceforge.net/git/gitweb.cgi?p=fjbtndrv/fjbtndrv;a=summary](http://fjbtndrv.git.sourceforge.net/git/gitweb.cgi?p=fjbtndrv/fjbtndrv;a=summary)

EDIT: for those who need to compile xf86-input-evdev 2.4.0 for a reason or another and encounter problems such dependencies problems, just pm me as I come here once a while and I may miss some messages such the one from rizzly...

---

### Post by Aidenairel on 2010-08-01
Thanks arobase, I just got my 1825PTZ a couple of weeks ago, and have been trawling the internet to get my touchscreen working. Would it be alright on my Netbook edition flavour of Lucid? I have never done a separate kernel install, etc, before, so I would like to knwo what I'm getting myself into..

---

### Post by arobase40 on 2010-08-02
I use myself a Ubuntu Netbook Lucid edition  and all work really fine, except the mutitouch (or at least dual touch) and auto-rotate screen.

---

### Post by arobase40 on 2010-08-25
Hi,

I think I have found some informations about the G sensor for this 1825(ptz)...

I first watch at the Acer drivers for Windows and found a reference :  SMO8800. I poke around google but found nothing useful except this is a  sensor made by ST Micro... :(
But I watch again in the drivers located in the  "C:\OEM\Preload\Autorun\DRV\MISC G sensor LIS33DETR" directory and found  another reference LIS33DETR, which looks like to be the real reference  of the ScreenDetection device for autoscreen rotation.
There is no source code reference at all in any versions of linux kernel  (I watched at 2.6.36-rc1), but after a deep search with google, I found  2 things : a script which was supposed to read informations about a 3D  Accelerator on Palo35 device and using a LIS33DE with i2c-dev module...  But this script does not work as it could even not read the registers...  May be I missed something... ??? Some differences between the lis33DE  and lis33DETR ??? ^^

[http://permalink.gmane.org/gmane.linux.distributions.gumstix.general/49727](http://permalink.gmane.org/gmane.linux.distributions.gumstix.general/49727)

At least, I then found all the C source code for the list33DE driver in the Android-kernel trunk... ^^ :)
I have not integrated this code in a linux kernel nor have I tested it, yet !

[http://code.google.com/p/m8-android-kernel/source/browse/trunk/drivers/i2c/chips/lis302dl.c](http://code.google.com/p/m8-android-kernel/source/browse/trunk/drivers/i2c/chips/lis302dl.c)

I will try to compile it and see if I can get if work, but if you are quicker than me, you can use it at your own risk... ^^

Best regards,

---

### Post by arobase40 on 2010-08-27
Some new informations about the accelerometor used by the Acer 1825ptz...

I found out a few 2 years old codes used by a other model : lis3lv02DL (in HTC Shift) but closed to the one use by the 1825pt(z).

[http://pof.eslack.org/blog/2008/06/03/i2c-gsensor-lis3lv02dl-accelerometer-on-htc-shift-g-sensor/](http://pof.eslack.org/blog/2008/06/03/i2c-gsensor-lis3lv02dl-accelerometer-on-htc-shift-g-sensor/)

Just download i2c-gsensor file, edit the i2c-gsensor.c file and change the line :

#define WHO_AM_I    0x3a

by 

#define WHO_AM_I    0x3b

Compile and play with it under Terminal ! :p

As you will notice, this is a 3 axis only accelerometor. That means you  won't be able to make difference between Left and Right... ^^ :(

After a deep search in  the linux source code, I finally found the same reference (lis3lv02DL) in driver/hwmon and probably the magic number under lis3lv02d.h . That means that the code and modules are already there, but I don't know how to use them yet... ^^
I will let you know as soon I have more informations.

regards

---

### Post by arobase40 on 2010-09-02
Hi again,

I forgot to mention you need to load i2c-i801 and i2c-dev modules first before you can use the i2c-gsensor util... ^^

I'm surprised about nobody's reactions about this...

---

### Post by arobase40 on 2010-09-23
Here is a new version of the manual rotation script.

Rename rotate.sh to rotate and rotate-screen.sh to rotate-screen
It is written in 2 parts and both files are to be placed in the same dir (part of your env variables).
Only the rotate script is to be binded to the P-button.

If someone can propose better optimization...

I "may" post a first version of an auto-rotate script soon... Hopefully... ^^

---

### Post by sadcruel on 2010-09-24
Ok, Ok, resuming, in the Acer 1825PTZ, to get the touchscreen (in mono-touch mode and without G-rotation) you need to do this:

[SIZE=3]1) Install the new Intel drivers[/SIZE]

1a) _On a updated Ubuntu 10.04_ the first thing we have to do is install the latest Intel drivers.  In a terminal type:

[FONT=Courier New]sudo gedit /etc/apt/sources.list[/FONT]

1b) At the end of the file add the following 2 lines:

[FONT=Courier New]deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main #xorg-edgers PPA
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main #xorg-edgers PPA[/FONT]

1c) Now type in a terminal the following command:

[FONT=Courier New]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542[/FONT]

1d) Update the distro from the repository to search the new packages:

[FONT=Courier New]sudo apt-get update[/FONT]

1e) And make the upgrade

[FONT=Courier New]sudo apt-get dist-upgrade[/FONT]

[SIZE=3]
1) Install the new 2.6.35 kernel[/SIZE]

2a) Now we are going to upgrade to the 2.6.35 kernel.  First add the kernel repository:
[FONT=Courier New]
[/FONT] [FONT=Courier New]sudo add-apt-repository ppa:kernel-ppa/ppa
[FONT=Arial]
[/FONT][/FONT]2b) Update so the kernel can be availables:
[FONT=Courier New][FONT=Arial]
[/FONT]sudo apt-get-update

[/FONT]2c) Install the latest 2.6.35 linux:
[FONT=Courier New]
sudo apt-get install linux-headers-2.6.35-22  linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic  linux-maverick-source-2.6.35[/FONT]

2d) Restart your computer. you will see the 2.6.35-22 kernel is now in you boot screen, select them. Once started, you will notice that the left button mouse doen't work (in touchpad or external mouse).  Pulse with your finger in the touch screen and the mouse must go to that point int the screen.  Now the left button in the touchpad/external mouse will be ok.

[SIZE=3]3) Aditional notes[/SIZE]

3a) In theory, you can install the 2.6.35 kernel and then install the Intel drivers.  The problem with this is that if you install 2.6.35 kernel and restart, you won't have the new intel drivers yet.  This causes that the touchscreen is recognized like a touchpad, and the left button die.  In any case, remember that you can install the intel drivers in any kernel (for example in the 2.6.32-24) and the drivers will be used by all kernels installed after or before.

3b) In the Ubuntu 10.10 Maverick beta the default kernel is the 2.6.35, so you will notice something like the 3a) behaviour (touchscreen detected like a touchpad and no left button mouse).

----

And it's all.  All is perfect except the manual rotation (throught the System->Preferences).  For example if you rotate 180º the screen and touch the screen in the bottom-right corner, the cursor go to the upper-left corner and so on.

I've reading the solution from arobase40 (it seem good for me) but i really don't understand that.

---

### Post by arobase40 on 2010-09-24
> **sadcruel said:**
> Ok, Ok, resuming, in the Acer 1825PTZ, to get the touchscreen (in mono-touch mode and without G-rotation) you need to do this:

...

And it's all.  All is perfect except the manual rotation (throught the System->Preferences).  For example if you rotate 180º the screen and touch the screen in the bottom-right corner, the cursor go to the upper-left corner and so on.

I've reading the solution from arobase40 (it seem good for me) but i really don't understand that.

I don't understand what you don't understand ? :P

Did you install xf86-input-evdev 2.4 or above ?
If this is the problem, then you have to download the tar ball, uncompress, ./configure --prefix=/usr, then make and make install. Just reboot and it should be fine.

By 180°, you mean inverted, is that right ?
If so, you sould'nt have any problem with the manual rotate script.

The sole problem you should encouter is with the xorg-intel 2.12 driver... When you rotate the panel, the system may dim the brightness. So you will have to fn+right dir to recover full brightness.
This is a bug with the Intel driver I can't solve by script yet. I have tried to recover the brightness state and to apply it back after the rotation, but it does not work. I don't know why... ^^

---

### Post by arobase40 on 2010-11-14
If you need informations about the way to handle the G-sensor (for automatic display rotation), watch at this link :

[http://www.uluga.ubuntuforums.org/showthread.php?t=1486671&page=5](http://www.uluga.ubuntuforums.org/showthread.php?t=1486671&page=5)

Regards,

---

### Post by drnessie on 2011-02-13
Can someone please send me their patched kernel? I'm a noob, can't get touchscreen working...

It is working as a touchpad as described above... maybe if I could have the source file or something... idk... tried downloading it through apt-get... cant access evdev.c... PLEASE!

Oh, and I accidently wiped Win7 in doing this so no touchscreen for me!

---

### Post by 2deadpool2 on 2011-02-13
> **drnessie said:**
> Can someone please send me their patched kernel? I'm a noob, can't get touchscreen working...

It is working as a touchpad as described above... maybe if I could have the source file or something... idk... tried downloading it through apt-get... cant access evdev.c... PLEASE!

Oh, and I accidently wiped Win7 in doing this so no touchscreen for me!

go here:[http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html") and follow the instructions to have touchscreen work, this is to have multitouch, but it only work in monotouch. this an easy method don't need to patch the kernel just install driver for the screen.

after that install grab and drag add-on for firefox or chrometouch for chromium

---

### Post by drnessie on 2011-02-13
Thankyou Thankyou Thankyou! *bookmarked*

May I suggest google chrome with chromeTouch extension for all yous who want to have finger scrolling? It's what I had installed on my Win7.

Such a shame I wiped it, it really was beautiful, and quite fast - even though it was made by microsoft..

---

### Post by 2deadpool2 on 2011-02-13
here: [http://www.ceh-photo.de/blog/?tag=acer-1825]("http://www.ceh-photo.de/blog/?tag=acer-1825")
everyone can find informations for configuring the 1825 ptz
the author (ceh-photo.de) list differents methods to enable features of this laptop (gyro-sensor, specials keys, etc...)
there is also a method for the touchscreen but i prefer the method from lii-enac.fr which is more stable for me

enjoy ;)

---

### Post by RRoel on 2011-02-27
Hey everyone, I'm trying to get my touch screen working as well, for now I have:
Linux kernel 2.6.36 (64 bit)
Ubuntu 10.10
My touchscreen is recognised as a touchpad, and on startup I have to tap my monitor to get my left mouse button working (so far I've read more people got that behaviour)
I also read it might be good to update my bios, but as long as it's not strictly necessary, I'd rather not..

I tried to install the driver as mentioned on lii-enac.fr, but when I try to compile, first everything seems fine untill:

[...]
  CC [M]  /home/roel/liitouch/enac-drivers/drivers/hid/hid-zpff.o
  CC [M]  /home/roel/liitouch/enac-drivers/drivers/hid/hid-zydacron.o
  CC [M]  /home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.o
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c: In function &#8216;wacom_raw_event&#8217;:
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c:233: error: &#8216;struct input_dev&#8217; has no member named &#8216;absmax&#8217;
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c: In function &#8216;wacom_probe&#8217;:
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c:409: error: &#8216;struct input_dev&#8217; has no member named &#8216;absmax&#8217;
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c:410: error: &#8216;struct input_dev&#8217; has no member named &#8216;absmax&#8217;
/home/roel/liitouch/enac-drivers/drivers/hid/hid-wacom.c:412: error: &#8216;struct input_dev&#8217; has no member named &#8216;absmax&#8217;
[... more in the attachment]

From there on it's loads of errors, and my touch screen is still a touch pad.
Could anyone tell me what more I could try?

(Also this os my first post on this forum, any constructiove comments (more/less info needed?) are appreciated)

Cheers!
Roel

---

### Post by RRoel on 2011-02-27
Fixed: [http://lii-enac.fr/en/architecture/l...ntu-howto.html]("http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html") is about kernel 2.6.35, booting in this kernel and then installing the drivers works for me, now let's see if i can get screen rotation working...

---

