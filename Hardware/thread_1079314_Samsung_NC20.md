---
title: "Samsung NC20"
date: 2009-02-24
forum: Hardware
---

### Post by lots_of_entropy on 2009-02-24
I have been digging around the web for a while now and did not find a single thread about running linux on the Samsung NC20 netbook. So this is it!

Please post your experience!

I am particular interested in the following questions:
- Are there linux drivers (maybe from via) that provide 3D and video acceleration. According to their web-page openchrome only has 2D support. 
- How is the battery life under linux
- Does the suspend to ram work
- Any glitches with the remaining hardware (sound, bt, wireless, etc.)

P.S.: Anyone who is planning on starting another discussion if 12" is still a netbook - please get a life.

Links:
[http://www.howtobemobile.com/index.p...y-samsung-nc20]("http://www.howtobemobile.com/index.p...y-samsung-nc20")
[http://forum.eeepcnews.de/viewtopic.php?f=86&t=6360&st=0&sk=t&sd=a]("http://forum.eeepcnews.de/viewtopic.php?f=86&t=6360&st=0&sk=t&sd=a") (in German)

---

### Post by lots_of_entropy on 2009-03-10
Update: A guy at [http://www.howtobemobile.com/index.php/how-2s/49-software/169-linpus-lite-on-my-samsung-nc20]("http://www.howtobemobile.com/index.php/how-2s/49-software/169-linpus-lite-on-my-samsung-nc20") runs Linpus linux on the NC20 however does not give any useful information regarding the questions above.

---

### Post by binbash on 2009-03-10
I was gonna buy that netbook.I read a lot of blogs , everything is working pretty well however you may need some work to get some stuff working.(Some parts were not out of the box)

---

### Post by lots_of_entropy on 2009-03-11
Do you have a few links?

---

### Post by r4idei on 2009-03-11
Ok here i am... Im going to be short beacuse i dont have much time, but im not going on the moon so i will follow this thread :)

I will describe my experience with intrepid and samsung nc20

-Xorg live doesnt start, alternate doesnt boot. Solution: downloading compiling and installing latest openchrome to boot xorg and start installation.

-Afeter installing xorg doesnt start again (obviously). SOlution: same of above (if you are smart put drivers in a persisten partition)

-NO CPU FREQUENCY SCALING! PANIC!! Solution: build module e_powersaver from kernel source
Strange things: loading module gives scaling from 850 to 1700.
loading, unloading, reloading gives from 800 to 1600 (same as windows)
BAD THINGS: compiling e_powersaver with 64bit kernel gave me a bunch of errors, im using 32 bit. I'it a shame but im optimistic for future kernels (maybe i was unlucky or/and not capable)

-restriced drivers manager says wifi module are loaded, i dont see any ifconfig device and i dint have time to seek out the problem. UPDATE: wifi works using these drivers [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros) Led doesnt'work, it is always ON

-sound seems to work UPDATE: sound works without doing anything. Speakers mute when you plug earphones

-openchrome works with no resolution problems, but REALLY slow. even with direct redering activated i get 80 fps with glxgears. Im gonna try via driver (im quite confused with via closed, via open, openchrome uargHH)

-suspend to ram works perfectly. I activated it via menu, the screen shuts down, the power led blinks, everything ok

-Special keyboard keys seems to work. Volume up and down works. I didnt try sleep button :\. Brightness buttons dont work (**** i hate this thing, it should be hardware embebbed like my old notebook) but luckily you can use applets in gnome and in kde4 (FIUU!)

Thats all, forgive my shortness (uh?) and my english.
If anybody wants to open a wiki, it would be wonderful and ill partecipate

BTW: the machine is WONDERFUL. Everything runs REALLY smooth, i can live with poor 2d-3d drawing having wifi and sound perfectly workin

---

### Post by lots_of_entropy on 2009-03-11
Yay - finally some hard info - thanks man. Did you time your battery life yet? Thanks for your time

---

### Post by r4idei on 2009-03-11
I havent still tested battery life cause i had hard times with freq scaling :D I will do it the near future

---

### Post by r4idei on 2009-03-13
Update: i made via's driver work :) Now i get more than 400 fps with glxgears. (this works just with intrepid)

With jaunty the e_powersaver module is compiled so you hust have to load it.
On the other side i cant get video driver working

---

### Post by lots_of_entropy on 2009-03-13
You could try
```
Option "AccelMethod" "EXA"
```
if it is not already enabled. Any news on the battery life? Need to know ... need to know .. :-)

---

### Post by thawn on 2009-03-17
first of all, thanks for to r4idei for his post it helped me a great deal!
I would like to add some details and experiences of my own
> **r4idei said:**
> Ok here i am... Im going to be short beacuse i dont have much time, but im not going on the moon so i will follow this thread :)

I will describe my experience with intrepid and samsung nc20

-Xorg live doesnt start, alternate doesnt boot. Solution: downloading compiling and installing latest openchrome to boot xorg and start installation.

-Afeter installing xorg doesnt start again (obviously). SOlution: same of above (if you are smart put drivers in a persisten partition)

a nice howto for the openchrome drivers can be found here:
[https://help.ubuntu.com/community/OpenChrome#Manual%20Installation]("https://help.ubuntu.com/community/OpenChrome#Manual%20Installation")

However with openchrome, I could not get an external monitor to work
If anyone has a solution for this, please post it here!

if you don't need an external monitor or 3d accelration, you are probably better off with the openchrome driver.  but if you plan to install the via drivers anyway, you might as well do that now: here is a quick step by step guide:

you first need some packages in order to be able to compile a kernel package (I am not sure if this list of packages is complete, since I had installed quite some packages before installing the via drivers please correct me, if anything is missing):
```
sudo apt-get install build-essential subversion autoconf automake1.9 libtool linux-headers-generic
```

get the drivers and the kernel module from [http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action"). select OS: ubuntu 8.10 and Platform: VX800.

download the "unified gfx driver" and the "chrome DRM source for kernel 2.6.27"

now install the gfx driver:
```
tar zxvf ./5.74.33.85a-44597.tar.gz
cd   ./5.74.33.85a-44597
sudo ./vinstall
sudo reboot

```

after this step, I had a running x system, but resolution and drm were not working.

to get drm working, I had to compile and install the DRM driver (this is from the readme):
```
2. For VIA CN896/VN896/VX800 chipset
(1) Copy drm-via_chrome9-2.6.27-85a-44411-src.tar.gz to your working directory
(2) Extract the package
    # tar -zxf drm-via_chrome9-2.6.27-85a-44411-src.tar.gz
(3) Enter the directory and build the source
    # cd drm-via_chrome9-2.6.27-85a-44411-src
    # make
    # sudo su -
(4) Backup the VIA chrome9 DRM module
    # cd /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9
    # mv via_chrome9.ko via_chrome9.ko.bak
(5) Replace VIA DRM module by the new one
    # cp ~/drm-via_chrome9-2.6.27-85a-44411-src/via_chrome9.ko /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9/
    # depmod -a
(6) Restart (not necessary just load the module)
    # modprobe via_chrome9
(7) Check whether VIA chrome9 DRM module is loaded
    # lsmod |grep via_chrome9
    If you get the output as:
      drm        86056  1 via_chrome9
    that means the VIA chrome9 DRM module is successfully loaded.
    Make sure the path of VIA DRM module is right.
    # modinfo via_chrome9
    The output should be like:
      filename:  /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9/via_chrome9.ko

```

now I had to make some adjustments to my xorg.conf:
```
Section "Monitor"
        Identifier "Monitor"
EndSection

Section "Screen"
        Monitor  "Monitor"
        DefaultDepth 16
        SubSection "Display"
                Modes  "1280x800"
                Virtual 1280 1824
                Depth  16
        EndSubSection
        Identifier      "Default Screen"
        Device          "Configured Video Device"
EndSection

Section "Module"
        Load  "glx"
        Load  "dri"
        Load  "extmod"
EndSection

Section "DRI"
        Group 0
        Mode 0666
EndSection

Section "Device"
        Driver "via"
        VendorName  "VIA Tech"
        BoardName   "via"
                #Option "PanelID" "0"    #640x480,    Single,    Dithering
        Identifier      "Configured Video Device"
        Option "SWCursor" "TRUE"
        Option "PanelID" "7"
EndSection

```
for some reason I needed to turn off the hardware cursor in order to be able to see the mouse cursor therefore the Option "SWCursor" "TRUE".

> -NO CPU FREQUENCY SCALING! PANIC!! Solution: build module e_powersaver from kernel source
Strange things: loading module gives scaling from 850 to 1700.
loading, unloading, reloading gives from 800 to 1600 (same as windows)
BAD THINGS: compiling e_powersaver with 64bit kernel gave me a bunch of errors, im using 32 bit. I'it a shame but im optimistic for future kernels (maybe i was unlucky or/and not capable)

Edit: this is how I got it working:
You could reconfigure and compile a whole new kernel version. However there is a way to compile and install just the module:
first we need the kernel sources
```
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
```
now switch to the new source directory and configure the kernel:
```
cd ~/linux-2.6.27
make oldconfig
gedit .config
```
change "# CONFIG_X86_E_POWERSAVER is not configured" to "CONFIG_X86_E_POWERSAVER=m"
now we need the Module.symvers file from the linux-headers and then we can compile and install the modules (note: I'm not sure if fakeroot is really necessary but that's how I did it and how it worked):
```
cp /usr/src/linux-headers-2.6.27-11-generic/Module.symvers ~/linux-2.6.27/
make clean
fakeroot make prepare
fakeroot make M=arch/x86/kernel/cpu/cpufreq/
sudo cp arch/x86/kernel/cpu/cpufreq/*.ko /lib/modules/2.6.27-11-generic/kernel/arch/x86/kernel/cpu/cpufreq/
sudo depmod -a
sudo modprobe e_pwersaver
```
now, after a reboot, your frequency switching should be working just fine

Update: I also experienced the weird frequencies, which get fixed upon reloading the module e_powersaver.
I suspect that the frequencies that really get set are correct and just the reported frequencies are wrong.
The evidence for this is that the reported frequencies were 1.6 to 3.2 GHz and the system was running fine and did not even run as hot as before I installed e_powersaver.
This probably has something to do with when the module gets loaded during boot. So the proper fix would be to delay loading e_powersaver. However, I went for a workaround:
add the following lines to /etc/rc.local :
```
modprobe -r e_powersaver
modprobe e_powersaver
```
now the frequencies should be displayed correctly.

> -restriced drivers manager says wifi module are loaded, i dont see any ifconfig device and i dint have time to seek out the problem. UPDATE: wifi works using these drivers [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros) Led doesnt'work, it is always ON

I deactivated the default drivers in System -> Administration -> Hardware
then I installed linux-backports-modules-intrepid.
```
sudo apt-get install linux-backports-modules-intrepid
```
activated the atheros 5xxxx drivers in System -> Administration -> Hardware
works like a charm!

> -sound seems to work UPDATE: sound works without doing anything. Speakers mute when you plug earphones

One caveat: I could not get the internal microphone to work! Connecting a mic to the microphone jack works, but not the internal one. However, I haven't ever tried under windows, if there is an inernal mic behind this little hole in the screen, or if it is just a mock-up. 
If anyone has gotten this to work, please let me know how (or if there is no mic built-in).

> -suspend to ram works perfectly. I activated it via menu, the screen shuts down, the power led blinks, everything ok

in principle works for me, too but occasionally, the computer won't wake up any more with the openchrome drivers. don't know if this occurs with the via drivers, since I just installed those.

edit: I have been using the via drivers for quite some time now and never had problems. Also, the video playback acceleration works.

Concerning the webcam: It works out of the box. luvcview shows a nice image albeit just with 3 
skype 2.0.0.79, seems to only use the top-right quarter of the image which is o.k. since my head fits in there, but it forces me to look at the screen from an angle. If anyone else has heard of this or knows a solution, please tell.

edit: for some reason, skype works fine now, not sure why (maybe just a reboot?)

Bluetooth works out of the box.

> -Special keyboard keys seems to work. Volume up and down works. I didnt try sleep button :\. Brightness buttons dont work (**** i hate this thing, it should be hardware embebbed like my old notebook) but luckily you can use applets in gnome and in kde4 (FIUU!)

Thats all, forgive my shortness (uh?) and my english.
If anybody wants to open a wiki, it would be wonderful and ill partecipate

BTW: the machine is WONDERFUL. Everything runs REALLY smooth, i can live with poor 2d-3d drawing having wifi and sound perfectly workin


same here, I the only thing I am missing is the microphone, but that can be worked around using a bluetooth headset

---

### Post by harenarius on 2009-03-19
Hello all,

Finally some signs that ubuntu can be successfully installed on the nc20. Thanks a lot for your info, without it I really wouldn't know where to start.

I were thinking maybe it is a good idea to create a descent howto or maybe even a wiki with instructions on how to install ubuntu on the nc20 and get the various hardware/software features to work. Starting with creating a bootable usb stick and than step by step instructions from there on. This, i think, would greatly help a lot of people, myself included, to get started.


Another thing: isn't it better to start of with jaunty as to have the latest kernel and openchrome etc? I tried installing it but got stuck on a flickering screen roughly the color of the default ubuntu background. No clue how to continue form there...


Thanks again!

---

### Post by thawn on 2009-03-20
> **harenarius said:**
> Another thing: isn't it better to start of with jaunty as to have the latest kernel and openchrome etc? I tried installing it but got stuck on a flickering screen roughly the color of the default ubuntu background. No clue how to continue form there.
There are two reasons that IMHO speak against Jaunty. The obvious one is that it is still beta and a lot of other (not kernel related) things might not work yet.
The other one is that the via graphic drivers do not work with Jaunty, yet.
The latter is of course no problem if you plan to use openchrome anyways. However openchrome does not support most of the features of the VX800 chipset (3D and video decoding acceleration) yet (see [http://www.openchrome.org/trac/wiki/SupportedHardware]("http://www.openchrome.org/trac/wiki/SupportedHardware") ). Therefore I used the via drivers and Intrepid.

However, I am going to try to upgrade to Jaunty as soon as the via drivers support it.

---

### Post by Bram-NL on 2009-03-22
> **thawn said:**
> [...]

same here, I the only thing I am missing is the microphone, but that can be worked around using a bluetooth headset

THANKS for your very useful post! you :guitar: :)

About the microphone, according to [this page]("http://www.samsung.com/nl/consumer/detail/spec.do?group=computersperipherals&type=notebook&subtype=mininotebooks&model_cd=NP-NC20-KA01NL&fullspec=F") (in dutch), there should be an internal mic.
It's listed as "Interne microfoon: Ja" which is literally "Internal microphone: Yes" in English.

And indeed, under Windows, using skype, I confirmed that that little hole on the right of the camera is the microphone.

---

### Post by Tobis87 on 2009-03-23
Hello,

I also have a NC20 netbook, the only problem, except the 3d hardware acceleration, with the amd64 kernel is that it doesn't currently support the padlock and the rng number generator. The e_powersaver kernel module for the cpu frequency is also not precompiled. 

Until I found a fresh patch for the padlock on the kernel mailing list. You will need the at least the 2.6.29rc8 kernel to apply the padlock patch. I also modified the via-rng.c file in order to get the rng number generator to work.

The patch doesn't get applied that well, so you will have to check the rej files in the linux-2.6.29-rc8/arch/x86 . For the rng number generator you will have to copy the via-rng.c file to linux-2.6.29rc8/drivers/char/hw_random and modify the Kconfig file inside that folder, to make the rng module not depended on X86_32. For the cpufreq module, you will also have to modify Kconfig inside linux-2.6.29-rc8/arch/x86/cpu/cpufreq.

After that, you can choose the padlock-aes, padlock-sha, e_powersaver and the via-rng module when you configure the kernel.:popcorn:

edit:
I also attached the patch for the vmware 6.5 modules for the 2.6.29 Kernel.
You may also want to enable the new ath5k module for the atheros card.

[ATTACH]107407[/ATTACH]

[ATTACH]107408[/ATTACH]

[ATTACH]107410[/ATTACH]

---

### Post by thawn on 2009-03-24
> **Bram-NL said:**
> THANKS for your very useful post! you :guitar: :)

About the microphone, according to [this page]("http://www.samsung.com/nl/consumer/detail/spec.do?group=computersperipherals&type=notebook&subtype=mininotebooks&model_cd=NP-NC20-KA01NL&fullspec=F") (in dutch), there should be an internal mic.
It's listed as "Interne microfoon: Ja" which is literally "Internal microphone: Yes" in English.

And indeed, under Windows, using skype, I confirmed that that little hole on the right of the camera is the microphone.

Thanks! :-D
(for the guitar and the info ;-) )

> **r4idei said:**
> I havent still tested battery life cause i had hard times with freq scaling :D I will do it the near future

I tested the battery life now:
Conditions: Intrepid generic kernel (2.6.27-11) with e_powersaver. Via graphics driver, W-lan and bluetooth enabled. Browsing the internet via w-lan (including some youtube) and listening to music. Display set to 70% brightness.

This gave me a battery life of 4h 30 min
This seems to be a lot less than the promised 6 hours.

However I am not sure under which conditions the 6h are reached. If that is without wlan and bluetooth and without load then I think we can reach this under linux as well (will test that sometime)

The youtube videos and occasional browser restarts caused 100% cpu-load (maybe 2% of the total time)

could anyone post his experiences using windows?

---

### Post by r4idei on 2009-03-24
Im quite disappointed with via drivers.... 32/24 bits doesnt work: you can see it watching some photos or even the ubuntu gdm screen (the brown one).
HWCursor doesnt work, and this makes compiz unusable :/

---

### Post by StephSD3 on 2009-03-25
wooow, mighty good info here :P
I'll be buying one next month, but first had to know if it would run Ubuntu (Offc). Now I know 8)

---

### Post by Bram-NL on 2009-03-28
I have a hard time getting Ubuntu 8.10 to work on the NC20. Jaunty/9.04 works fine, but I can't get the Via drivers to work there so I want to try 8.10 to get 3D.

I have tried 8.10 desktop and 8.10 alternate (using both the "Create USB startup disk" from Ubuntu and the "unetbootin-linux-319" tool) but it fails to boot at all (it becomes unusable after "Saving VESA state".

How should I do it right?

---

### Post by Tobis87 on 2009-03-28
> **Bram-NL said:**
> I have a hard time getting Ubuntu 8.10 to work on the NC20. Jaunty/9.04 works fine, but I can't get the Via drivers to work there so I want to try 8.10 to get 3D.

I have tried 8.10 desktop and 8.10 alternate (using both the "Create USB startup disk" from Ubuntu and the "unetbootin-linux-319" tool) but it fails to boot at all (it becomes unusable after "Saving VESA state".

How should I do it right?

Follow this guide and add fb=off to the syslinux.cfg.

[http://actualreality.wordpress.com/2008/12/27/installing-ubuntu-810-intrepid-ibex-with-a-usb-drive/](http://actualreality.wordpress.com/2008/12/27/installing-ubuntu-810-intrepid-ibex-with-a-usb-drive/)

```
default vmlinuz

append initrd=initrd.gz fb=off
```

---

### Post by Bram-NL on 2009-03-28
Sweet! I'll try, thanks!

[Edit]
Victory! :cool:

Now I will try to get 3D to work :)

---

### Post by r4idei on 2009-03-30
I tried the "2d only" drivers and they seem to work better than the latest! You can use Hwcursor and compiz runs better (they should ben just for 2d... boh!). The only problem is that i cant use 1280x800 res!

---

### Post by Barry Carroll on 2009-04-03
Hi All,

I followed the instructions here on both the Intrepid live CD and the Jaunty beta live CD.  Strangely the most recent build of the gutsy live cd works perfectly

Unfortunately I haven't been able to get a working X display.  When I follow the Openchrome installation instructions (compiling from svn) X will start but only in what looks like a test pattern.

The screen changes colour and then displays various gradient patterns only.  I can hear the Ubuntu start-up sound so I know GDM has managed to start.

Any ideas?

---

### Post by harenarius on 2009-04-06
I finally managed to install ubuntu on my nc20 using the instructions of thawn. Thanks!

There are a couple of things i'd like to share with you:
1) toggle bluetooth on/off
2) sound issue
3) compiz not working correctly

1)
I found it annoying that i had no option to turn of the bluetooth radio to save battery life. This script is a descent work around.
#!/bin/bash
if ps -A | grep -c bluetoothd
then
gksudo /etc/init.d/bluetooth stop
sudo hciconfig hci0 down
sudo rmmod bluetooth
else
sudo modprobe bluetooth reset=1
gksudo /etc/init.d/bluetooth start
fi

you could save it in /usr/bin and then create a launcher, on your desktop for instance.

2)
In contrary to experiences of others my sound didn't seem to work at first. I fixed it by selecting the top 3 default mixer tracks in system->preferences->sound 

3)
It turns out a lot of the compiz features aren't working such as Scale (like expose on a mac). I figured i had to select Normal or Extra in system->preferences->appearance - visual effects, but this is not possible. It says desktop effects could not be enabled. Does anyone know how to fix this? I really really like the Scale functionality. (i'm using the via drivers btw)

---

### Post by Barry Carroll on 2009-04-07
When I followed thawn's instructions to install the binary via driver I discovered that the resolution of the panel was 1024*768 which had been stretched to the size of the LCD panel.

This was obvious when I added the "center" option to the device section in xorg.conf.  Are you sure that you are getting the full 1280x800 resolution?

---

### Post by r4idei on 2009-04-07
> **harenarius said:**
> I finally managed to install ubuntu on my nc20 using the instructions of thawn. Thanks!

3)
It turns out a lot of the compiz features aren't working such as Scale (like expose on a mac). I figured i had to select Normal or Extra in system->preferences->appearance - visual effects, but this is not possible. It says desktop effects could not be enabled. Does anyone know how to fix this? I really really like the Scale functionality. (i'm using the via drivers btw)

Without "normal" effects you dont have compiz running at all... So you were trying to use compiz effects without compiz :D 
Just edit /usr/bin/compiz and add "via" in the withelist section and you can start compiz (it will not run smooth and you will get mouse artifacts, i warn you)

---

### Post by harenarius on 2009-04-08
ah that is it indeed, thx. however you are right, it is a big disappointment and not useable. maybe i'll find another way to get the "expose" functionality. Will let u know when i do. 

Do you happen to know how to get two finger scroll and two finger right click to work? I know that the hardware supports it one way or another because under windows it works perfectly with [http://code.google.com/p/two-finger-scroll/](http://code.google.com/p/two-finger-scroll/). I tried adding Option "VertTwoFingerScroll" "true" to my xorg.conf. And indeed synclient -l gives (among others) VertTwoFingerScroll=1. But synclient -m 100 never shows more then 1 finger on the touchpad (5th collumn). I'm clueless...

---

### Post by Barry Carroll on 2009-04-09
Did you guys get the full 1280*800 resolution with the openchrome driver? No matter what I did I got the 1024*786 stretched which made the gui look distinctly fuzzy.

---

### Post by Tobis87 on 2009-04-10
> **Barry Carroll said:**
> Did you guys get the full 1280*800 resolution with the openchrome driver? No matter what I did I got the 1024*786 stretched which made the gui look distinctly fuzzy.

I do get the full 1280*800 resolution. I followed this guide and compiled the opechrome drivers from source.

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

And this is my xorg.conf
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

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
	Option		"ActiveDevice" "LCD,CRT"
	Option		"NoDDCValue" "true"
#	Option		"XaaNoImageWriteRect" "true"
	Option		"SWCursor"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"PreferredMode" "1280x800"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
	InputDevice	"Synaptics Touchpad"
EndSection
```

note:
You won't need the "XaaNoImageWriteRect" "true" entry anymore, if you use the latest drivers.
You may want to change "XkbLayout" "de" to your keyboard layout.
I only tested the openchrome drivers on Intrepid Ibex.

---

### Post by Barry Carroll on 2009-04-10
Hi Tobis87,

Many thanks for posting your xorg conf, I can now get the full 1280*800 resolution and it looks great!  

I am running Jaunty beta myself and the svn trunk was at rev. 753 when I built the drivers.  I think it might have been 752 the last time I tried.

In any case I now have great 2D performance :)  Once again, many thanks for your help.

Edit: There was a new version from the 07/Apr/09 so perhaps this may have helped too

> r743 | schlobinux | 2009-04-07 22:08:45 +0100 (Tue, 07 Apr 2009) | 1 line

don't try to enable XvMC on VX800


---

### Post by r4idei on 2009-04-12
> **Barry Carroll said:**
> Hi Tobis87,

Many thanks for posting your xorg conf, I can now get the full 1280*800 resolution and it looks great!  

I am running Jaunty beta myself and the svn trunk was at rev. 753 when I built the drivers.  I think it might have been 752 the last time I tried.

In any case I now have great 2D performance :)  Once again, many thanks for your help.

Edit: There was a new version from the 07/Apr/09 so perhaps this may have helped too

You have better performance than with rev 752?

---

### Post by Barry Carroll on 2009-04-12
The 2D performance is good, but there are some slowdowns when there is intensive cpu usage.  I don't have to use the SW cursor either.  I haven't tried 3D yet as it isn't that important to me right now.

I've been working on the screen brightness keys mainly.  I filed a bug and submitted a patch for hal-info and I just tested a kernel that I compiled as the second part of the fix.

Fixing hal-info to recognise the keys allows you to change brightness but there is a bug where the keys for brightness up and brightness down are repeated.  
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/359814](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/359814)

To stop the repeating keys problem I had to add some code into the at keyboard driver in the kernel, and this was inspired by the same type of fix for the nc10.  I'll submit the patch to the kernel people soon.

---

### Post by Barry Carroll on 2009-04-12
Just filed the bug report and patch
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360247)

I can also upload the deb from my kernel build if you would like to test but you'll also need to add the nc20 info into the hal configuration files too:

Hal file is in:

```
/usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi
```

```
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix_ncase="samsung">
	<match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="NC10;**NC20**;SP55S;SQ45S70S;SX60P;SX30S;R59P/R60P/R61P;Q210;Q310;X05">
```

I hope hosting on rapidshare is allowed, if not I will remove the link.  The deb is available at the following address and is the same as the stock kernel with the keyboard patch.

**edit: this is a kernel that I compiled under Jaunty Beta, 2.6.28-11-generic**
[http://rapidshare.com/files/220609333/linux-image-2.6.28-11-generic_2.6.28-11.41_i386.deb](http://rapidshare.com/files/220609333/linux-image-2.6.28-11-generic_2.6.28-11.41_i386.deb)

---

### Post by Tobis87 on 2009-04-13
Hi Barry Carroll,

Thanks for the patch, I try it if Kernel 2.6.29.2 will be out.

Maybe this is only a amd64 issue, but did you get suspend to ram (standby) working with the openchrome driver?

---

### Post by Barry Carroll on 2009-04-13
Yes, suspend worked fine for me.

Edit: I was using the 32-bit distribution, and I have replaced the atheros card in my nc20 with an intel wifi link 5100.

---

### Post by r4idei on 2009-04-15
> **Barry Carroll said:**
> The 2D performance is good, but there are some slowdowns when there is intensive cpu usage.  I don't have to use the SW cursor either.  I haven't tried 3D yet as it isn't that important to me right now.

I've been working on the screen brightness keys mainly.  I filed a bug and submitted a patch for hal-info and I just tested a kernel that I compiled as the second part of the fix.

Fixing hal-info to recognise the keys allows you to change brightness but there is a bug where the keys for brightness up and brightness down are repeated.  
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/359814](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/359814)

To stop the repeating keys problem I had to add some code into the at keyboard driver in the kernel, and this was inspired by the same type of fix for the nc10.  I'll submit the patch to the kernel people soon.

Great! To be honest i don't miss keyboard brightness control too much thanks to the gnome brightness applet, but your work is very useful without any doubts!!

I hope via will release some good video drivers for jaunty!! Openchrome are good drivers (i can say via's drivers are ****... they dont even display real 24 bit color depth) but we need some official stuff :|

---

### Post by Barry Carroll on 2009-04-15
I found that with via's drivers too.  No matter what value I specified it was only displaying what looked like 16-bit and I couldn't get the right resolution either.

I have to admit that I love the fn keys on laptops and it usually drives me mad if they don't work or can't be made to work easily :)

I'll probably do a fresh install when Jaunty is released because I have tried so many things in the beta that I'm not sure what's what!  Hopefully openchrome will bring be updated in the meantime as well.

---

### Post by r4idei on 2009-04-15
> **Barry Carroll said:**
> I found that with via's drivers too.  No matter what value I specified it was only displaying what looked like 16-bit and I couldn't get the right resolution either.

I have to admit that I love the fn keys on laptops and it usually drives me mad if they don't work or can't be made to work easily :)

I'll probably do a fresh install when Jaunty is released because I have tried so many things in the beta that I'm not sure what's what!  Hopefully openchrome will bring be updated in the meantime as well.

Yes, it happens just with via drivers! Openchrome displays correct depth!
I just tried jaunty beta and the last rev of openchrome with no luck. All i can get when i start gdm are colured screens :\

---

### Post by Barry Carroll on 2009-04-15
That happened to me too but when I used Tobis' xorg.conf I got a usable display:

[http://ubuntuforums.org/showpost.php?p=7047627&postcount=28](http://ubuntuforums.org/showpost.php?p=7047627&postcount=28)

Mine is almost the same as his but I didn't need to enable SWCursor.  Before using his configuration I had nothing but coloured screens and test patterns but I could hear the login sound in the background which was very annoying!

---

### Post by r4idei on 2009-04-15
> **Barry Carroll said:**
> That happened to me too but when I used Tobis' xorg.conf I got a usable display:

[http://ubuntuforums.org/showpost.php?p=7047627&postcount=28](http://ubuntuforums.org/showpost.php?p=7047627&postcount=28)

Mine is almost the same as his but I didn't need to enable SWCursor.  Before using his configuration I had nothing but coloured screens and test patterns but I could hear the login sound in the background which was very annoying!

Ohh thanks :D This option did the work: 	

Option		"ActiveDevice" "LCD,CRT"

---

### Post by Barry Carroll on 2009-04-17
I think I'll try a fresh install of the RC over the weekend and see if there's a newer version of openchrome too.

---

### Post by Bram-NL on 2009-04-17
Hey Barry,

Installing Openchrome from SVN is very easy so no need to wait for a newer package.
Read this guide from "Manual Installation" and proceed with the steps for 8.10:

[https://help.ubuntu.com/community/OpenChrome#Manual%20Installation](https://help.ubuntu.com/community/OpenChrome#Manual%20Installation)


[edit] @vvv: I see. That's good then ;)

---

### Post by Barry Carroll on 2009-04-17
Cheers Bram ;)

I meant that I was going to check for a newer revision in SVN.  The packaged version doesn't work with the NC20 at the moment.

---

### Post by Tobis87 on 2009-04-28
I now got Openssl working with Padlock in Amd64 Intrepid.:popcorn:

Read this guide:
[http://www.a110wiki.de/wiki/VIA_Padlock](http://www.a110wiki.de/wiki/VIA_Padlock)

Download the attached new patch, apply it and recompile Openssl.
```
sudo apt-get install build-essential devscripts fakeroot
sudo apt-get build-dep openssl
apt-get source openssl
cd openssl-0.9.8g
wget -q -O - http://launchpadlibrarian.net/13798833/bug119295.patch | patch -p1
wget -q -O - http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff | patch -p1
cat ../centaur-openssl-padlock-x86_64.patch | patch -p1
debchange --nmu
#type if vi :wq else if nano ctrl-o ctrl-x
sudo dpkg-buildpackage
sudo dpkg -i ../openssl_0.9.8g-10.1ubuntu2.3_amd64.deb ../libssl0.9.8_0.9.8g-10.1ubuntu2.3_amd64.deb ../libssl-dev_0.9.8g-10.1ubuntu2.3_amd64.deb

```

Configure Openssl to always use the Padlock engine:
[http://ubuntuforums.org/showthread.php?t=710243](http://ubuntuforums.org/showthread.php?t=710243)

Note:
Openssh has already been fixed in interpid.

---

### Post by Barry Carroll on 2009-04-30
Did you look at getting the RNG working at all?  I tried to modprobe via-rng but it failed with a message about a device being missing.  I assumed that was /dev/hwrandom so I tried making a node there in /sys but still no joy.

Do you load the padlock-aes and padlock-sha modules at start-up now or is having OpenSSL working good enough?

---

### Post by Tobis87 on 2009-04-30
For the RNG, you will need to modify the via-rng.c in order to bypass the "unnecessary sanity check", the RNG does work without this check.
Just comment it out and recompile the kernel module:
```
/* perhaps-unnecessary sanity check; remove after testing if
   unneeded
   rdmsr(MSR_VIA_RNG, lo, hi);
   if ((lo & VIA_RNG_ENABLE) == 0) {
   printk(KERN_ERR PFX "cannot enable VIA C3 RNG, aborting\n");
   return -ENODEV;
   }*/
```
But for amd64 you need to patch the kernel (>=2.6.29), as I described here: [http://ubuntuforums.org/showpost.php?p=6944581&postcount=14](http://ubuntuforums.org/showpost.php?p=6944581&postcount=14)

The modules padlock-aes and padlock-sha are only used by dm-crypt (cryptsetup). You may still need to modify and recompile Openssl if you want to use it with Openssh, Openvpn and many more.

You can follow my guide above. It still runs on i386. But I don't know if that is necessary for jaunty anymore.

But I now also managed to port the in official sha patch for Openssl to intrepid and amd64. Because it is dependend on my last patch you will need to apply them both.
For i386 you'll need to change inside eng_padlock.c:
```
typedef unsigned int uint32_t;
-> typedef unsigned long uint32_t;
```

---

### Post by Barry Carroll on 2009-04-30
Cool, thanks!  I'm using the 32-bit install and openssl seems to support padlock out of the box:

```
barry@raptor:~/openchrome$ openssl engine
(padlock) VIA PadLock (no-RNG, ACE)
(dynamic) Dynamic engine loading support
```

I'll need to patch via-rng.c though so thanks for the tip!

---

### Post by Tobis87 on 2009-04-30
But for SHA1 and SHA256 hardware acceleration, you still need to recompile Openssl.

---

### Post by Barry Carroll on 2009-04-30
Ah ok, will do - thanks again.

---

### Post by Barry Carroll on 2009-05-01
I might try and get some of this info into a wiki page over the weekend, I think this thread is a great resource for the nc20 :popcorn:

---

### Post by Barry Carroll on 2009-05-05
I put up the startings of a a wiki entry here: [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20)

I swapped out my wirless card for an intel one before I installed ubuntu so I wasn't sure if the stock card works out of the box.  I also added what seems to me like a hacky way of getting the wifi button to work so if anyone knows a better way I'd be happy to learn.

---

### Post by Barry Carroll on 2009-05-07
Good news everyone!

The microphone is working with alsa 1.0.20, just select 'Mic' as opposed to 'Front Mic' and play with the 'digital' / 'capture' sliders in the recording tab - takes a bit of tweaking but it works!

---

### Post by pureblood on 2009-05-07
I have just installed Jaunty on my new NC20. I had a little bit of bad luck with the graphic display but I finally got it to work so I want to share this bit of information.
Long story short, the openchrome driver does not work out of the box. The version in Jaunty is svn713 and X will just not start properly. The vesa driver does not seem to work as well. To install the system I took the hard drive out and installed it from another machine.
The current version of the openchrome driver is svn749 which, apparently, does not work as well. I think it is broken or something like that. The system starts fine, but the screen is black or it alternates between red white and green. Very odd.
Luckily, the people at debian made a debian package with version svn741 which works great. Follow this link:
[http://packages.debian.org/search?keywords=xserver-xorg-video-openchrome](http://packages.debian.org/search?keywords=xserver-xorg-video-openchrome)
And download the package for sid (not the one for squeeze which has some dependency problems with ubuntu). Then install it on your system with 'dpkg -i' and voila, the graphic now works just fine.
If it wasn't for this glitch, Jaunty would support this laptop completely. Wireless and sound works just fine and I am pretty excited to know that the latest alsa driver supports the built-in microphone. Maybe the next release of ubuntu will be a piece of cake to install.

---

### Post by Barry Carroll on 2009-05-08
Hey Pureblood, I compiled the openchrome drivers from SVN myself but it's good to know there's a package out there as some people would much prefer to use that instead.  I started a wiki about the NC20 a short while ago: [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20) and there's a lot of good info in this thread if you read back through it too.

---

### Post by Tobis87 on 2009-05-08
Hey Barry,
It's nice to hear that the internal mic is now working with alsa 1.0.20.:guitar:
 Do you know whether the alsa-driver is depended on alsa-libs and alsa-utils? I don't have a problem compiling new kernel modules. But I don't like the idea of installing the rest of alsa by overwriting my old files.
Does the mic port actually work? I don't have a microphone here, so I couldn't tested it yet.

Regarding my problem with standby, this seems to be an issue by switching to the virtual console and back to x11. The strange thing is, that I can log out and log in again, which also restarts the x.org server. But I can't switch to a virtual console and back to x11. The screen than gets black and I have to hard reboot, even the SysRq keys won't work.

---

### Post by Barry Carroll on 2009-05-08
Hey Tobis87, I'm not sure about the dependencies as I upgraded all to 1.0.20.  I haven't tried the other mic port either as I don't have anything to plug in there but there are two options when selecting a mic so it looks like it is being *detected* at least.

You are using 64-bit, right?  I remember seeing this on the openchrome mailing list recently about someone with the same problem: [http://wiki.openchrome.org/pipermail/openchrome-users/2009-May/005534.html](http://wiki.openchrome.org/pipermail/openchrome-users/2009-May/005534.html)

---

### Post by pureblood on 2009-05-08
Thanks for the wiki Barry. It looks awesome and I look forward for more information about what I can do with the NC20. It will be a very useful tool for a lot of people.

I tried to get the via closed source driver working on my machine, but the only result I got was a black screen and X crashing. Does anybody have the same problem? If so and you get some progress, could you open a section on the wiki [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20)?

I don't care about 3D that much, but I wanted the external monitor to work, so I can use the laptop for presentations. Does the
> Option          "ActiveDevice"  "LCD,CRT"
option in the xorg.conf file allow you to use an external screen with the openchrome driver?

Does anybody know why the SD card does not work at all? Is there a driver supposed to take care of it which does not turn on or is there just no driver at all?

---

### Post by Barry Carroll on 2009-05-08
Hey, I saw your change on the wiki, awesome stuff :guitar:

I just added some headings and internal page links to tidy it up just now.  The card reader support is on the way.  I have been looking at some kernel mailing list archives and I think there is a patch available from via but it has not been incorporated into the kernel yet.  IIRC it is called ```
via-sdmmc
```.

The activedevice section is something that I and others needed to do just in order to get a display.  Without that setting X would be just like a test pattern for video although you could hear the start-up sounds in the background.

I think I'll stick with openchrome unless something drastic happens with the closed source driver.  That is not out of idealism though!  From what I have read the closed source driver is not very good and openchrome seems to have better performance.

I might try hooking up an external monitor this weekend although it's not something that would be that important to me as my desktop is set up with two large screens.

---

### Post by Tobis87 on 2009-05-08
> **Barry Carroll said:**
> The card reader support is on the way.  I have been looking at some kernel mailing list archives and I think there is a patch available from via but it has not been incorporated into the kernel yet.

Yeah, I read about this. But I don't want to do the bug testing for Via. The new Via Nano might be an innovation, but Via fails to write good drivers. The viafb and their chrome9 driver don't work and almost any driver we use is made by reverse engineering, e.g. the openchrome driver, e_powersave, padlock, via-rng and so forth. On the other side, the padlock engine is a great invention and I'm looking forward to see something like this implemented in the mainstream processors.

By the way, I tested the new alsa driver and I can confirm that they are not dependend on alsa libs/utils. You can follow the guide from the NC10:
[https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10) -> Audio - Alsa driver
```
cd Desktop/alsa-driver-1.0.20
./configure --with-cards=hda-intel --with-oss=yes --with-sequencer=yes
make
sudo make install
```

The microphone plug does also work.

---

### Post by pureblood on 2009-05-09
I can confirm that the external monitor works fine with the openchrome driver, at least in clone mode. That is awesome, I can use the laptop for presentations.

Although I have this weird problem. Everytime I boot the laptop it takes two reboots to work. The first time everything locks and the screen goes black. No idea why. Also, if I leave the laptop alone, the screen goes super black after a while and I have no means to turn it back on. Is there any way to fix that?

Anybody with the same problems? I am using openchrome svn741, which may be a bad idea. I tried the other day svn749 but it just wasn't working.

---

### Post by Barry Carroll on 2009-05-09
I'm running with the driver from svn rev. 747 and that appears for me to be the latest that is available at [http://svn.openchrome.org/svn/trunk/](http://svn.openchrome.org/svn/trunk/)

My install is 32-bit and I haven't had any issues with rebooting.  On the other hand sometimes the backlight does not come back on after a screensaver timeout or lid open after close.  It's not something that happens regularly so I'm assuming it's a small bug somewhere in the driver.  I have a feeling that the VX800 support is quite young compared to some of the other chipsets supported by openchrome but I have high hopes! :)

---

### Post by Barry Carroll on 2009-05-09
Another thing that I meant to ask you all about was the frequency scaling.  Mine goes up to 1.7GHz - is that something that you have noticed on your installations?  I don't know if it is normal or down to a tweak that I have done.  I'm using the e_powersaver module that came with the distribution and the generic gnome cpu frequency applet to report.

---

### Post by Barry Carroll on 2009-05-10
I was playing around the sd / mcc card reader this morning and got it to work with some source that was posted to the kernel mailing list.  I cobbled together a makefile too and it seems to work pretty well. 

I'll put the stuff up on the wiki later after I get some breakfast!

---

### Post by Barry Carroll on 2009-05-10
[https://help.ubuntu.com/community/NC20#SD%20/%20MMC%20Card%20Reader](https://help.ubuntu.com/community/NC20#SD%20/%20MMC%20Card%20Reader)

Works for me, hopefully it'll work for others too.

---

### Post by pureblood on 2009-05-10
Barry, in the past few days I got this laptop, you have become my little hero! Way to go and give it back to the community. Thanks for the SD post, I will try it immediately. It is a bless that there are people like you that do what VIA should have done.

I am still pissed at the screen light dimming problem. I do not understand what triggers it and how to avoid it from happening. The best workaround I have got is to put the laptop in sleep mode, through the Fn+Esc shortcut, and then turn it back on with the power button. That way the screen goes back bright.

---

### Post by Barry Carroll on 2009-05-10
Hehe, thanks although I wouldn't have been experimenting as much if the other folk in this thread had not helped me to get X working.  I should point out that the person who wrote the patch is a VIA employee - I just pulled the source out of a mailing list post and thankfully it worked.

---

### Post by KristinaK on 2009-05-10
maybe a dumb question, but I need to know. Should I use Ubuntu 9.04 Netbook Remix or Ubuntu 9.04 Desktop with my new nc20 ? I am new here and beg your pardon.
[B][B]
[/B][/B]

---

### Post by Barry Carroll on 2009-05-10
It's entirely up to you.  The netbook remix has a different interface by default designer for lower resolution screens but the NC20 has 1280*800 which is much more than most netbooks.

---

### Post by renesco on 2009-05-11
Hello. Thanks for the wiki and other posts. I have one serious problem. Wine don't work. When I start it's conf or start win apps using it - system is down. I have 9.04 with Xfce. Sorry my eng))

I have tried to set up Netbook-remix on NC20. It seems that version includes only specified Netbook-launcher with the large icons of apps and maximus package. I don't now why, but I have about 1 fps in this system. I set it up on Notebook with Core 2 and this problem repeats. Maybe it's optimized only for Atom CPU. Netbook-remix works propertly on NC10 with Atom.

---

### Post by Barry Carroll on 2009-05-11
I haven't used wine on the NC20 myself as I don't need access to any Windows binaries.

I think that the netbook remix might also rely on compiz now that I think more about it.  This would be a problem with openchrome as compiz doesn't work yet.

I think the NC20 is fine with the full Jaunty installer and I never had much interest in trying out the netbook remix because the NC20's screen has much more resolution than the 10" netbooks.

---

### Post by pureblood on 2009-05-11
Wine should not be able to crash the whole system. I think it is likely a problem with the graphic driver interacting with the drm module of your system when you use wine. Look online for "wine openchrome drm crash".

---

### Post by Tobis87 on 2009-05-11
Playing a video with totem will also crash the system. At least if totem-gstreamer is installed. This happens, because Xv is not yet supported for the XV800 and gstreamer does not detect this correctly. My workaround for this is to launch gstreamer-properties and set the video plugin to "no xv". Instead you could also install totem-xine which I think is even better than gstreamer.

---

### Post by dm666 on 2009-05-15
Hey there,

very helpful posts here, thanks a lot all of you, especially Barry for the great howto.

I've been digging around with my NC20 for 6 weeks now, tried almost every linux distribution (opensuse, ubuntu, sidux, linpus, fluxflux-sl) but I just can't get skype to work properly. even compiled various kernels from 2.6.28- 2-6.30.
Tried ALSA versions 1.0.18 - 1.0.20.

I always have the problem, that skype test calls are choppy, extream distorted with packet loss AND cpu sage of 100%. and that without webcam usage!
Windows on the same network works alright.Damn!

Why is skype eating my cpu? I had a 9 years old P3 laptop befor that could manage this tasks.

Any ideas?

Cheers
Dirk

---

### Post by Barry Carroll on 2009-05-15
Hey Dirk,

I found skype to be a bit lacklustre too.  I did get it to a good enough state by playing with the recording controls endlessly which included looking at input gain in the OSS mixer as well as tuning the recording options in the ALSA mixer.  I also disabled the setting in skype allowing it to automatically adjust the recoding levels as I thought it was getting it wrong a lot of the time.

edit: is your cpu scaling up when you are using skype?  I'm using the on demand governor but I should try performance to see if it helps.

---

### Post by Barry Carroll on 2009-05-15
> **Tobis87 said:**
> Playing a video with totem will also crash the system. At least if totem-gstreamer is installed. This happens, because Xv is not yet supported for the XV800 and gstreamer does not detect this correctly. My workaround for this is to launch gstreamer-properties and set the video plugin to "no xv". Instead you could also install totem-xine which I think is even better than gstreamer.

Nice, I'll try that too.  I'm going to see how it handles VLC if I have the time as well.  I'm selling my windows laptop soon so I'll need to get some workable video player on my nc20 soon :)

---

### Post by dm666 on 2009-05-15
Hey Barry,
thanks for your response!
I chacked the CPU skaling, it went up with the on demand governor.
ut also with the Performance setting cpu is at 100%, also whe i swith of skypes automatic settings.
Been playing with the mixer settings, but no success.
Could you have a look at your mixer, and tell me what level you use approx for the sliders eg. "digital", "capture".
my OSS mixer only has settings for playback, not for record??? what mixer do you mean?
The last skype test calls gave me a time stretching effect. Tried this here:

[http://forum.skype.com/index.php?showtopic=17384](http://forum.skype.com/index.php?showtopic=17384)

but I dont know how to reset this to default...


Cheers
Dirk

---

### Post by dm666 on 2009-05-15
Hello again,
and sorry for my typos.

What I really don't understand with the ALSA mixer settings of  the NC20s VIA VT82xx is the organisation of the sliders:

In the section "playback" theres a slider for "Front Mic Boost", but not in the section "record" shouldn't it be vice versa, so that I have a boost for recording, not for listening to the mic?
Another confusing thing is that the internal mic is refered as "mic",  and the mic-plug is for "front-mic". Thats how I could record with the build in mic anyway.
would be no problem, but the mic boost is only for the front mic, means the external plugged mic. 
so theres no boost for the buil-in mic.

All pretty weird. Or did I get it all wrong?

Cheers
Dirk

---

### Post by londonzombie on 2009-05-16
Hi guys, This is my first post here, I have been trying to get linux to run on the nc20 since the day I bought it and have still not found a great solution.
I would love to tun my attention to ubuntu now.
 
Could you tell me how I can get this installed?
 
I have tried using the alternate dvd iso using the text based installer and it just gives me a blank screen. (I have used amd x64 and i386 and they are both the same)
 
and as you all know the stardard install just goes straight to the fuzzy screen.....
 
Could anyone let me know what version you have used of jaunty and which option to use for the install?
 
Thanks so much in advance !!
 
Mark

---

### Post by nicxz on 2009-05-16
Hi,

Great thread (and documentation page) with lots of useful tips.

I've been using ubuntu jaunty on my new samsung nc20 for 2 days now, and I've run into a problem. Wifi drops off after a while, sometimes as soon as a few minutes after connecting. I haven't figured out what triggers it yet. 

syslog shows the following:
May 16 20:35:26 VIA kernel: [  291.994295] ath5k phy0: noise floor calibration timeout (2442MHz)
May 16 20:35:27 VIA NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
May 16 20:35:27 VIA kernel: [  293.229718] wlan0: No ProbeResp from current AP (my AP here) - assume out of range
May 16 20:35:28 VIA NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
May 16 20:35:28 VIA kernel: [  293.380920] ath5k phy0: failed to wakeup the MAC Chip
May 16 20:35:28 VIA kernel: [  293.380944] ath5k phy0: can't reset hardware (-5)

Access point used is a Fritzbox FON WLAN 7170 Annex A with WPA2 encryption.

I've verified that ath5k module is the only wifi module loaded. After a while, a prompt appears which says 'authentication required by access point' and I can enter my AP password again. That repeats untill the system gives up trying to connect. 

Has anyone else run into this, or have an idea where to look for debugging?

---

### Post by nicxz on 2009-05-16
Hi Londonzombie,

Information on the NC20 in combination with Ubuntu Jaunty can be found at [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20) .

What I did for installation is first follow the howto @ [http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?22973.0#post_22976](http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?22973.0#post_22976) which gets you a working but slow ubuntu installation. It's slow because of the video driver. To fix that, I then installed openchrome ( [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) 'manual install')

Good luck!

---

### Post by Barry Carroll on 2009-05-17
Hey dm666.  It does seem odd that the front mic boost is in the playback section alright.

I got to the input gain control that I was talking about by selecting realtek alc 272 as the device in the mixer and then clicking preferences.  In preferences you can check a box to show 'Input gain' in the mixer and that seems to control recording volume like a mic boost.

I tried to take some screenshots but I've found that GIMP is crashing horribly and taking the whole system with it and I can't find out why.  Does GIMP work for you by any chance?

Londomzombie, there are lots of ways to get your video working and two of them are detailed here: [https://help.ubuntu.com/community/NC20#Video%20/%20Graphics](https://help.ubuntu.com/community/NC20#Video%20/%20Graphics)

The problem is that you must do this to run the installer and then again when your machine reboots after installation.  It's not ideal but it works.  I wrote the standard jaunty iso to a usb stick with unetbootin and booted with the stick.  If you hit the escape key when you turn the nc20 on you will go to a boot selection screen where you can choose to boot from the usb stick.

---

### Post by Barry Carroll on 2009-05-17
> **nicxz said:**
> Hi,

Great thread (and documentation page) with lots of useful tips.

I've been using ubuntu jaunty on my new samsung nc20 for 2 days now, and I've run into a problem. Wifi drops off after a while, sometimes as soon as a few minutes after connecting. I haven't figured out what triggers it yet. 

syslog shows the following:
May 16 20:35:26 VIA kernel: [  291.994295] ath5k phy0: noise floor calibration timeout (2442MHz)
May 16 20:35:27 VIA NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
May 16 20:35:27 VIA kernel: [  293.229718] wlan0: No ProbeResp from current AP (my AP here) - assume out of range
May 16 20:35:28 VIA NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
May 16 20:35:28 VIA kernel: [  293.380920] ath5k phy0: failed to wakeup the MAC Chip
May 16 20:35:28 VIA kernel: [  293.380944] ath5k phy0: can't reset hardware (-5)

Access point used is a Fritzbox FON WLAN 7170 Annex A with WPA2 encryption.

I've verified that ath5k module is the only wifi module loaded. After a while, a prompt appears which says 'authentication required by access point' and I can enter my AP password again. That repeats untill the system gives up trying to connect. 

Has anyone else run into this, or have an idea where to look for debugging?

Unfortunately I can't confirm as I swapped out the atheros card for an intel one (wifi link 5100) but you don't appear to be alone with the problem which seems to be across multiple distros.  Do any of these threads apply?

[http://ubuntuforums.org/showpost.php?p=7168287&postcount=4](http://ubuntuforums.org/showpost.php?p=7168287&postcount=4)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341952)

and an apparent fix in the mainline kernel which is linked to the launchpad bug...

[http://bugzilla.kernel.org/show_bug.cgi?id=12647](http://bugzilla.kernel.org/show_bug.cgi?id=12647)

edit: The maintainer of the bug has developed a kernel with the fix for testing and needs it tested, perhaps worth a shot?

[http://people.ubuntu.com/~manjo/lp341952-jaunty/](http://people.ubuntu.com/~manjo/lp341952-jaunty/)

---

### Post by nicxz on 2009-05-17
Hi Barry,

Thanks for pointing me in the right direction. I'll try out the patched kernel tonight and post results.

---

### Post by pureblood on 2009-05-18
I am having the same ath5k problem. Is it actually fixed with kernel 2.6.28-13? This laptop is really linux unfriendly at the moment. Hey Barry, where did you get the wifi link 5100? Furthermore, how much did you pay it and how do you install it? Is it easy? If I keep getting the same problem with the ath5k I might consider making the change as well.

---

### Post by Barry Carroll on 2009-05-19
> **pureblood said:**
> I am having the same ath5k problem. Is it actually fixed with kernel 2.6.28-13? This laptop is really linux unfriendly at the moment. Hey Barry, where did you get the wifi link 5100? Furthermore, how much did you pay it and how do you install it? Is it easy? If I keep getting the same problem with the ath5k I might consider making the change as well.


Hey, I got it on ebay from this seller: [http://shop.ebay.ie/merchant/praesidee](http://shop.ebay.ie/merchant/praesidee)

[http://cgi.ebay.ie/Intel-5100-Wireless-N-802-11N-Mini-PCI-E-Card-300M_W0QQitemZ220401480356QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item220401480356&_trksid=p3286.c0.m14&_trkparms=72%3A1300|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50](http://cgi.ebay.ie/Intel-5100-Wireless-N-802-11N-Mini-PCI-E-Card-300M_W0QQitemZ220401480356QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item220401480356&_trksid=p3286.c0.m14&_trkparms=72%3A1300|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A0|293%3A1|294%3A50)

You can also get the 5300 which is like the 5100 but with an extra (third) connection for an antenna.

[http://cgi.ebay.ie/Intel-5300-Mini-PCI-E-Card-Wifi-802-11N-Wireless-N_W0QQitemZ320363352283QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item320363352283&_trksid=p3911.c0.m14&_trkparms=72%3A1301|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A1|293%3A1|294%3A50](http://cgi.ebay.ie/Intel-5300-Mini-PCI-E-Card-Wifi-802-11N-Wireless-N_W0QQitemZ320363352283QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item320363352283&_trksid=p3911.c0.m14&_trkparms=72%3A1301|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A1|293%3A1|294%3A50)

Some other stores sell the card plus antenna as a package.  I don't know if Wimax is also in your region but if you are interested there's a 5350 which is a 5300 plus wimax

edit: It did take some time to remove the bottom part of the nc20 to get at the wireless card but take it slowly and you'll be fine.  I'll have a look later and see what screws need to be taken out.  Once that is done replacing the card is easy.  You just need to unhook the two antennae, take out the fastening screw, the card will pop up at an angle, slide it out, put the new one in at an angle and press down and fasten with the screw.

---

### Post by nathan_k on 2009-05-19
Hey Barry.

I've been lurking on this thread for a while but finally created an account to ask you a question.

Why did you switch to the Intel wireless card so quickly? Did you expect driver problems, or is there something about the 5100 which makes it a lot better than the Atheros card?

I'm intrigued...

---

### Post by Barry Carroll on 2009-05-19
Hi Nathan,

I originally had a q210 with windows.  I upgraded the card in the q210 from a 2 antenna intel 5100 to a three antenna intel 5300.  Then I got the nc20 and sold the q210 so I had that intel 5100 lying around and I had known from previous machines that it worked very well.

I installed the 5100 before I even powered up the machine as I also had a spare 2GB dimm too so I upgraded the hardware and then installed Ubuntu.

---

### Post by nicxz on 2009-05-19
> **pureblood said:**
> I am having the same ath5k problem. Is it actually fixed with kernel 2.6.28-13? This laptop is really linux unfriendly at the moment. Hey Barry, where did you get the wifi link 5100? Furthermore, how much did you pay it and how do you install it? Is it easy? If I keep getting the same problem with the ath5k I might consider making the change as well.

The kernel which Barry linked to seems to have solved my problems, yes. I haven't been disconnected yet, since installing it. So with that (apparently) fixed, I'm really enjoying using this laptop again.

---

### Post by billy boy on 2009-05-19
Hi,
I'm coming up against a problem installing 9.04 (32bit) onto my NC20. 
I've booted it live from a USB stick, entered the command line when the screen goes haywire, installed the openchrome drivers according to the instructions on Barry's excellent community wiki, restarted GDM and everything seems fine (apart from the fact that certain programs (firefox, openoffice) don't run). 
When I try to install it (whilst in the live session) the install sequence always stalls after I've chosen the keyboard layout and pressed ok. The cursor churns, I wait and wait and nothing happens. Does anyone know what the problem might be? I've tested the integrity of the usb image and the iso from which it was created and they're both ok. 
Cheers
William

---

### Post by dm666 on 2009-05-19
Still got Skype not working properly with Linux on this machine.

CPU usage goes up most of the times to 100%, skype test calls give me a distorted or time stretched calls.
Played with the mixer settings a lot. 
Barry: the slider "In-gain" from the Realtek ALC272 OSSS Mixer section is the same as the "recording" slider in therecording section of HDA VIA VT82xxx Alsa Mixer, they slide synchronously. So theres no mic boost for the internal mix, right?

Anyways: has anybody had a successful and understandable conversation with skype on this machine? If yes, what are your settings, kernel versions, ALSA-versions...

Thank you
Dirk

---

### Post by Barry Carroll on 2009-05-20
I just installed jaunty 64-bit as I wanted to see how that ran after seeing some positive benchmark results on Phoronix.  It does appear to be more responsive except that I have encountered more problems.

* Does not power off after halt
* Gimp crashes on 32 and 64 bit when creating or opening an image
* e_powersaver needs to be built from source (as per earlier in this thread)

I'll download the kernel that fixes the keyboard stuff and I'll upgrade alsa and see if I can skype at good quality.  When I upgraded alsa I upgraded it all, not just the driver.

Anyone have the same issues with shutting down on 64-bit or problems with gimp?  ***warning***  On my machine gimp hard-locks the entire system and you must hold down the power button to power it off. If you do test it please don't have any unsaved work in the background :)

---

### Post by Barry Carroll on 2009-05-20
> **billy boy said:**
> Hi,
I'm coming up against a problem installing 9.04 (32bit) onto my NC20. 
I've booted it live from a USB stick, entered the command line when the screen goes haywire, installed the openchrome drivers according to the instructions on Barry's excellent community wiki, restarted GDM and everything seems fine (apart from the fact that certain programs (firefox, openoffice) don't run). 
When I try to install it (whilst in the live session) the install sequence always stalls after I've chosen the keyboard layout and pressed ok. The cursor churns, I wait and wait and nothing happens. Does anyone know what the problem might be? I've tested the integrity of the usb image and the iso from which it was created and they're both ok. 
Cheers
William

Hi William, I haven't experienced that and I have installed both the 32-bit and 64-bit versions at this stage.

Perhaps when it starts to churn you could switch to a VT and see if there are any error messages printed to the console.  Ctrl + Alt + F1 will go the first, then alt + f2 to f6 to check the others.  Alt + f7 will go back to the GUI.

---

### Post by nicxz on 2009-05-20
> **Barry Carroll said:**
> 
* Gimp crashes on 32 and 64 bit when creating or opening an image

Anyone have the same issues with shutting down on 64-bit or problems with gimp?  ***warning***  On my machine gimp hard-locks the entire system and you must hold down the power button to power it off. If you do test it please don't have any unsaved work in the background :)

Hi Barry,

I have the same problems with Gimp, using a 32-bit kernel. No solution found as of yet. Debugging is made difficult, because the whole system seems to freeze, and nothing shows up in logs (tried starting gimp from commmandline with verbose flag, and logging to file).

---

### Post by Barry Carroll on 2009-05-20
> **nicxz said:**
> Hi Barry,

I have the same problems with Gimp, using a 32-bit kernel. No solution found as of yet. Debugging is made difficult, because the whole system seems to freeze, and nothing shows up in logs (tried starting gimp from commmandline with verbose flag, and logging to file).

Cheers, at least I know I'm not the only one :)  The not powering off at the end of shutdown on 64-bit is annoying too although I haven't trouble-shooted it yet.

---

### Post by Tobis87 on 2009-05-20
> **Barry Carroll said:**
> The not powering off at the end of shutdown on 64-bit is annoying too although I haven't trouble-shooted it yet.

This must be jaunty specific, because I don't have that problem with intrepid amd64.

But do you also have the "vt switching freeze" with jaunty? If you switch to a VT and back to X.org?

The Gimp problem seems to be related with the problems in Wine and Totem. I think that all of these programs try to access opengl or xv which is not yet supported with the openchrome drivers.

---

### Post by IdealVithVodka on 2009-05-21
Has anyone tried the ubuntu 9.10 alpha 1 version on nc20 maybe ??

---

### Post by Barry Carroll on 2009-05-23
> **Tobis87 said:**
> This must be jaunty specific, because I don't have that problem with intrepid amd64.

But do you also have the "vt switching freeze" with jaunty? If you switch to a VT and back to X.org?

The Gimp problem seems to be related with the problems in Wine and Totem. I think that all of these programs try to access opengl or xv which is not yet supported with the openchrome drivers.

I do have the vt switching freeze :(  I tracked down the shutdown problem to an issue with the intel wireless drivers and 64-bit in general.  If I disable wireless and remove the modules before shutdown it works fine.

---

### Post by derlachendehans on 2009-05-24
> **nicxz said:**
> Hi Barry,

I have the same problems with Gimp, using a 32-bit kernel. No solution found as of yet. Debugging is made difficult, because the whole system seems to freeze, and nothing shows up in logs (tried starting gimp from commmandline with verbose flag, and logging to file).

try changing the color depth of the screen to 32 bit, that fixed the problem for me.

---

### Post by Barry Carroll on 2009-05-24
> **derlachendehans said:**
> try changing the color depth of the screen to 32 bit, that fixed the problem for me.

I think my colour depth is set to 32-bit already but I will double check, thanks.  Are you using the openchrome or via driver?

---

### Post by derlachendehans on 2009-05-24
i use the openchrome driver from the jaunty repositories.

i also have two questions for you

i know somone other already asked the question, when my display backlight turns off after some time idleing it does not wake up again.
is there a soultion for this problem?

i read some of you changed the wifi card to an intel card.
i've got an intel 3945ag which worked perfectly in my old eee but the nc20 completly ignores this card.
it does not even appear in the bios.
a bios update did not solve the problem.
so what is the trick with the other cards?

regards
derlachendehans

edit:
i just double checked it, i turned my color depth back to 24 bit and i had a the freeze again.

---

### Post by KristinaK on 2009-05-24
> **IdealVithVodka said:**
> Has anyone tried the ubuntu 9.10 alpha 1 version on nc20 maybe ??

you are brave one :popcorn: what is changed in alpha 1 ? I'll wait till 2.6.30-rc7

---

### Post by Barry Carroll on 2009-05-25
> **derlachendehans said:**
> i use the openchrome driver from the jaunty repositories.

i also have two questions for you

i know somone other already asked the question, when my display backlight turns off after some time idleing it does not wake up again.
is there a soultion for this problem?

i read some of you changed the wifi card to an intel card.
i've got an intel 3945ag which worked perfectly in my old eee but the nc20 completly ignores this card.
it does not even appear in the bios.
a bios update did not solve the problem.
so what is the trick with the other cards?

regards
derlachendehans

edit:
i just double checked it, i turned my color depth back to 24 bit and i had a the freeze again.

I haven't found a solution for the backlight issue but when that happens I usually suspend the laptop and then resume it and the backlight comes back.

I put in an intel 5100 and it was picked up straight away - I wasn't aware of any bios lockouts like you see on other laptops.  Are you 100% that it is seated firmly and correctly?

---

### Post by pureblood on 2009-05-25
I cannot manage to play videos on my laptop. I am trying to play a mov file (mjpeg for video and pcm_u8 for audio) and I either get bad audio with vlc, or I get really sloppy video with mplayer, both with the option '-vo xv' and with the option '-vo x11'. Other files work better though.
Does anybody know a solution for this?

---

### Post by thawn on 2009-05-27
Barry: Way to go. The wiki is great!

To everyone having video related problems with backlight, wakeup, console switching, external monitors or movie playback: It might be worthwhile to try intrepid (32-bit) with the via closed source drivers (see my post on page 1 of this thread for a howto).

I do not have any problems with these drivers. The backlight/wakeup/consoleswitch problems were my main prompt to use them instead of openchrome. They do also support movie playback acceleration.

With that installation I do not seem to have problems with skype, although that might be because I use alsa 1.0.18 and an external camera with a built-in microphone.

Barry: What problems did you have with the via drivers and what do you mean by openchrome performance being better? Certainly not 3d, since that is not supported by the driver yet afaik. Do you think it makes sense to include info for intrepid and the via drivers in the wiki (I could do that)?

---

### Post by Barry Carroll on 2009-05-27
Sounds good! 

I meant that the 2D performance was pretty good with openchrome but the issues with the backlight and other acceleration problems has been making me curious about your method so I might try that.

I think the alsa / mic problems are only for the built in microphone which simply isn't recognised before the update :)  The quality isn't the best though but that doesn't really bother me as I hardly use it.

---

### Post by pureblood on 2009-05-27
thawn, I think the wiki is only about Jaunty Jackalope, so it might be confusing to put information about Intrepid. Although, I would be curios to know why the closed source driver fail to work with Jaunty. Is that a problem with the new Xorg? Do you think they will update the closed source drivers and post them on VIA website? In that case it would be worth it to put a link on the wiki so that people can periodically check if the closed source drivers are now provided or not.

---

### Post by IdealVithVodka on 2009-05-28
I've just received my nc20 2day. I tried few distros on it (live CD) and it seems that debian handles it quite good as he detects the video mode without major problems (well, he makes it virtual so some parts of the desktop are outside the physical screen). Tried backtrack v3 and it did start using vesa mode in 1024x768 (very good to be honest). Didn't have much more time to test other stuff - will do that later in the evening.

---

### Post by thawn on 2009-05-28
> **pureblood said:**
> thawn, I think the wiki is only about Jaunty Jackalope, so it might be confusing to put information about Intrepid.

That's exactly why I asked first before making changes to the wiki.
The way I would suggest to do it is to set up the whole wiki so that it explains how to get it to work under jaunty and intrepid by adding different subsections specifically labeled for jaunty and intrepid. For example (just the headings):

[SIZE="4"]Video/Graphics[/SIZE]
[SIZE="3"]Openchrome driver (intrepid and jaunty)[/SIZE]
...
[SIZE="3"]Via Drivers (intrepid only)[/SIZE]
...

[SIZE="4"]Touchpad (intrepid and jaunty)[/SIZE]
...

etc...

edit: This is also how the [opencheome wiki]("https://help.ubuntu.com/community/OpenChrome") (and many others) does it, when explaining different ubuntu releases.

> Although, I would be curios to know why the closed source driver fail to work with Jaunty. Is that a problem with the new Xorg? 
The problems are probably mainly the new xorg and maybe also the newer kernel.

> Do you think they will update the closed source drivers and post them on VIA website? In that case it would be worth it to put a link on the wiki so that people can periodically check if the closed source drivers are now provided or not.
I sure hope so! However it might be a while until they support the new xorg. If I added the sections for intrepid, we would get the link automatically and could update the wiki accordingly, once the driver becomes available for jaunty, too.

---

### Post by pureblood on 2009-05-30
I have this annoying problem that every once in a while the wireless driver fails to connect to the access points and the network manager prompts me with a new password for the access point. Nothing seems to make it work at that point, other than restarting the driver. I wrote this alias:

> 
alias fixath5k='sudo modprobe -r ath5k && sudo modprobe ath5k'


to speed up things a little bit. The annoying problem comes up even after I installed the iw5100 intel wireless card. This is so annoying. So I wrote for that the following alias:

> 
alias fixiw5100='sudo modprobe -r iwlagn iwlcore mac80211 cfg80211 && sudo modprobe iwlagn'


Why is this problem so widespread among linux wireless drivers? Believe it or not, sometimes I have the same problem with my android phone, which uses the wlan driver. It seems something deep in the linux wireless stack or something. It is so annoying.

---

### Post by thawn on 2009-05-30
> **pureblood said:**
> I have this annoying problem that every once in a while the wireless driver fails to connect to the access points and the network manager prompts me with a new password for the access point. Nothing seems to make it work at that point, other than restarting the driver. 
Why is this problem so widespread among linux wireless drivers? Believe it or not, sometimes I have the same problem with my android phone, which uses the wlan driver. It seems something deep in the linux wireless stack or something. It is so annoying.
I am having the same problem with all my wireless linux systems. However the problem is not as pronounced recently. I found that it helps (for a while) to open the network manager and delete the wireless connection. afterwards it'll work for a couple of days...

---

### Post by thawn on 2009-05-30
> **dm666 said:**
> Still got Skype not working properly with Linux on this machine.

CPU usage goes up most of the times to 100%, skype test calls give me a distorted or time stretched calls.

I have the same problem trying to use alsa 1.0.20 and the internal microphone.

However, using another microphone (external, bluetooth or usb) and alsa 1.0.17 (the standard intrepid package) skype does work nicely.

Barry: you said earlier that skype works for you? is that with the internal mic? If yes, how did you do it?

---

### Post by thawn on 2009-05-30
I just patched intrepid's kernel to get the keyboard fn-keys fixed
I'll reference this file from [the wiki]("https://help.ubuntu.com/community/NC20")
I also added info on how to get intrepid working to the wiki.

---

### Post by pureblood on 2009-05-31
Barry, I installed the iw5100 card in the laptop, but now I discovered that there is a nasty bug that makes the card unable to work after putting the laptop on sleep mode, giving the message:
> 
iwlagn: MAC is in deep sleep!

How did you cope with that? It seems like there is no solution other than rebooting the machine. On top of that, when the backlight is off, putting the computer to sleep is the only solution to turning the backlight on again. Is there any way to turn the backlight on or to avoid that from happening? I cannot believe there are so many problems for something so stupid. I am starting to wish I did not buy this laptop. It is too annoying.

---

### Post by pureblood on 2009-06-03
I decided to say no to compromises. I downgraded in jaunty Xorg from version 1.6.0 to version 1.5.2 and after doing that, now both the openchrome driver and the proprietary via driver seem to work fine. It took sometime, since I had to collect a bunch of packages from the intrepid distribution. If anybody wants to dare the same, I created a tarball with all the packages and put some instructions on the wiki [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20).

---

### Post by Barry Carroll on 2009-06-03
> **pureblood said:**
> Barry, I installed the iw5100 card in the laptop, but now I discovered that there is a nasty bug that makes the card unable to work after putting the laptop on sleep mode, giving the message:

How did you cope with that? It seems like there is no solution other than rebooting the machine. On top of that, when the backlight is off, putting the computer to sleep is the only solution to turning the backlight on again. Is there any way to turn the backlight on or to avoid that from happening? I cannot believe there are so many problems for something so stupid. I am starting to wish I did not buy this laptop. It is too annoying.

Hey,  Yes I got the same when I was using 64-bit.  I got around it by doing a rmmod of iwlagn and iwlcore when I was shutting down.  IIRC disabling the wirless before shutdown using the fn-key method in the wiki also worked.  I went back to 32-bit in the meantime though as I experienced some problems with suspend and vt switching.

---

### Post by Barry Carroll on 2009-06-03
> **pureblood said:**
> I decided to say no to compromises. I downgraded in jaunty Xorg from version 1.6.0 to version 1.5.2 and after doing that, now both the openchrome driver and the proprietary via driver seem to work fine. It took sometime, since I had to collect a bunch of packages from the intrepid distribution. If anybody wants to dare the same, I created a tarball with all the packages and put some instructions on the wiki [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20).

Sounds interesting :) Can you get 24 bit colour with the proprietary drivers?  When I tried them before I only seemed to be able to get 16-bit.

---

### Post by pureblood on 2009-06-03
> **Barry Carroll said:**
> Sounds interesting :) Can you get 24 bit colour with the proprietary drivers?  When I tried them before I only seemed to be able to get 16-bit.

I copied the configuration that thawn gave me on the wiki, which is for 16 bit. Not sure why. But it looks good enough to me. I just had too many problems with openchrome. At this point if the proprietary driver is stable enough, I will just wait for a better openchrome driver or a better via driver. Although I tried to put 24 bit and it seems to work fine.

If you are going to try the same, be aware that I could not compile the via drm driver with kernel 2.6.30 but it luckily did compile fine with kernel 2.6.28 even if I think it was targeted for version 2.6.27.

---

### Post by thawn on 2009-06-04
> **pureblood said:**
> I copied the configuration that thawn gave me on the wiki, which is for 16 bit. Not sure why. But it looks good enough to me.
I did put in the 16 bit there because with that I actually seemed to get more colors that with a 24 bit setting (judging from how the color gradients look for the background image).

pureblood: it is good to see that you did not give up! Downgrading xorg on Jaunty - great idea.

I am hoping that openchrome will have improved by the time ubuntu 9.10 comes out.

---

### Post by thawn on 2009-06-04
> Hey, Yes I got the same when I was using 64-bit. I got around it by doing a rmmod of iwlagn and iwlcore when I was shutting down. IIRC disabling the wirless before shutdown using the fn-key method in the wiki also worked. I went back to 32-bit in the meantime though as I experienced some problems with suspend and vt switching.

While having 64 bit capabilities in the processor is nice, I don't quite get why anyone would want 64 bit with a netbook:

64 bit is good for memory above 3Gb and some programs that have been specifically optimized for it like 3d rendering and some video encoders.

However, the Samsung only supports up to 2GB of memory and IMHO, the processor is too slow for any of the 64 bit optimized programs anyways. While you might argue that especially with a slow processor you need every bit of speed, I would highly recommend to get a different machine for rendering and video encoding. AFAIK none of the programs most people use are sped up by 64 bit yet and some are even slowed down. So unless you want to develop 64 bit software, IMHO you are better off with 32 bit anyways - at least for now.

---

### Post by londonzombie on 2009-06-08
HI guys, DOes anyone have the drm-via_chrome9-2.6.27-85a-44411-src.tar.gz ?

The via linux site has been down all weekend and I'm stuck trying to get the graphics drivers loaded.

Thanks in advance!
Mark.

---

### Post by londonzombie on 2009-06-08
I just found it! [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=183](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=183)
the other linux part of the sie is still off line...

---

### Post by IdealVithVodka on 2009-06-09
The ubuntu daily-live build of 9.10 seems to work quite nice on the nc20. The vga was detected, wireless card detected and working (didn't work via network manager, but could configure it manually via ifconfig, iwconfig), most of the fn keys don't work apart from the sound volume control. its still an alpha version so hopefully when 9.10 will be released all the issues will be sorted out.

---

### Post by Barry Carroll on 2009-06-09
Sounds promising - I read that HAL is going to be deprecated in Karmic so we'll just have to figure out how to get the special keys working with the new system.

---

### Post by thawn on 2009-06-10
> **Barry Carroll said:**
> Sounds promising - I read that HAL is going to be deprecated in Karmic so we'll just have to figure out how to get the special keys working with the new system.

I think this could be a chance! If we report bugs with the samsung NC20 like the function keys, and power management problems we can help to significantly improve the nc20 support in karmic. So go on get testing :p

---

### Post by Milamber_Cubed on 2009-06-16
A quick question for you all:

It seems that the Via Nano CPU is 64-bit capable, but is there any advantages/disadvantages in choosing a 32-bit or 64-bit installation in terms of drivers etc?

Thanks for any input.

---

### Post by thawn on 2009-06-17
> **thawn said:**
> While having 64 bit capabilities in the processor is nice, I don't quite get why anyone would want 64 bit with a netbook:

64 bit is good for memory above 3Gb and some programs that have been specifically optimized for it like 3d rendering and some video encoders.

However, the Samsung only supports up to 2GB of memory and IMHO, the processor is too slow for any of the 64 bit optimized programs anyways. While you might argue that especially with a slow processor you need every bit of speed, I would highly recommend to get a different machine for rendering and video encoding. AFAIK none of the programs most people use are sped up by 64 bit yet and some are even slowed down. So unless you want to develop 64 bit software, IMHO you are better off with 32 bit anyways - at least for now.
I posted this just one page back - please use the search.

---

### Post by Milamber_Cubed on 2009-06-17
> **thawn said:**
> I posted this just one page back - please use the search.

Thanks... I did see that, but I was wondering more about the via drivers since they dont specify 32/64bit support and there's a binary blob involved. I tried 64 bit and it didn't seem to like the via drivers (X just wouldn't fire up) so went with 32-bit Intrepid instead.

Anyway, I was round at a friends house installing Ubuntu for them on their NC20 last night and this morning. The wiki page was massively helpful, so thanks to all involved in creating it, but there were some things which didn't go exactly as planned. I thought reporting back would be a good idea.

The major one was that the kernel patch and recompile (which I left running overnight) seemed to have failed when I checked it this morning with a " Previous or current ABI file missing!" message.

I managed to find from the blog posting linked to on the wiki that I needed to do the following:

```

cd ~/linux-2.6.27
cp debian/abi/2.6.27-XXX/i386/generic debian/abi/2.6.27-7.13/i386/nc20
cp debian/abi/2.6.27-XXX/i386/generic.modules debian/abi/2.6.27-7.13/i386/nc20.modules

```

After which the debs were created correctly and (most of) the Function keys proceded to work. 

The other thing that didn't work as planned was the wireless. There were no drivers listed in the System-->Hardware section either before or after the backports installation. Is is possible that the wireless hardware has changed between releases? Anyway, I found out the chipset from lspci and managed to find another page on the forums here that detailed how to install a version of the madwifi ath_pci driver that worked. 

Apart from that, there was a slight niggle with wireless not working correctly after waking from sleep, so I created a script based on the Bluetooth one posted earlier in the thread by harenarius:

```

#!/bin/bash
if lsmod | grep ath_pci
then
gksudo rmmod ath_pci
else
gksudo modprobe ath_pci
fi

```

Running this twice to disable and then re-enable the wireless fixes the post-sleep/wake issues. It would be nice if I could tie this script into the Fn key for the wireless, but I haven't had time to look into it. Any pointers for how to do this on Intrepid would be much appreciated. Maybe if I place those commands into the /etc/acpi/wireless.sh then the procedure for Jaunty will work? I'm not 100% sure if this is actually disabling the wireless radio or not, so maybe this isn't the solution to that problem. I ran out of time for this and just left a launcher link on the desktop for the wireless and bluetooth scripts.

The final comment is that one of the updates to the system after I did all the configuration caused the brightness keys to stop working so I had to re-do the edit to /usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi but this wasn't a huge problem.

I tried firing up compiz from the command line right before I had to leave but it failed complaining that there were no whitelisted drivers found. It's not a deal breaker by any means, I just thought it might be nice to see how well (if at all) it ran on the NC20. EDIT: just saw that you can add to the whitelist, but it sounds like it won't work well anyway... no huge loss!

I thought I would share my experiences in case they are useful to anyone else. All in all it went mostly as expected but the main point is that my friend has a working ubuntu install and they couldn't be happier. Thanks again for all the effort that went into this previously, it is seriously much appreciated!

---

### Post by Rainier Piqual on 2009-06-17
> **thawn said:**
> I think this could be a chance! If we report bugs with the samsung NC20 like the function keys, and power management problems we can help to significantly improve the nc20 support in karmic. So go on get testing :p

I have Karmic Alpha 2 on my nc20. the system freezes upon starting gimp and wine. after a hard reset the xserver fails to load. concerning the function keys, only the volume control works. brightness control seems to be somehow out of control, repeatingly dimming the display while running from battery. the wlan occasionally fails as well.

@idealwithvodka: did you manage to improve your setup somehow?

---

### Post by Rainier Piqual on 2009-06-18
A new Version of the BIOS is out:

[http://www.samsungpc.com/08/products/nc20/firmware.html](http://www.samsungpc.com/08/products/nc20/firmware.html)

"09MQ - Prevent system halt issue during idle"

Does this patch relieve us from any known misbehaviour? And how do I apply it under Ubuntu anyway? Wine?

---

### Post by pureblood on 2009-06-19
> brightness control seems to be somehow out of control, repeatingly dimming the display while running from battery.

Rainier Piqual, I also had a lot of problems with the installation of Jaunty. The brightness dimming of the display really drove me nuts. The openchrome driver was also too unstable. So I downgraded X to version 1.5.2 and installed the via proprietary driver. Truth is, this is unstable as well, but it is way better and I can watch most (not all) multimedia videos fine on the laptop. My suggestion is to do the same. I put some packages in the wiki to make the process easy, maybe it works with Karmic as well. In the meanwhile, I wait for the day either the openchrome or the via driver support well X 1.6.0. I am faithful but I would not bet on it. In the meanwhile, do not suggest anybody to buy VIA hardware.

---

### Post by Rainier Piqual on 2009-06-23
Thank you pureblood, I did as you recommended and I'm fine with my display now.

Another question, which wasn't answered in the wiki: Is it possible to scroll with two fingers? It is a multitouch touchpad, so it should be, right? How to achieve this without HAL ?

---

### Post by thawn on 2009-06-24
> **Rainier Piqual said:**
> Another question, which wasn't answered in the wiki: Is it possible to scroll with two fingers? It is a multitouch touchpad, so it should be, right? How to achieve this without HAL ?

I tried to get this to work using the synaptics driver.
have a look at [http://wiki.ubuntuusers.de/Touchpad]("http://wiki.ubuntuusers.de/Touchpad")
however I didn't manage to get the two finger scrolling to work but I didn't try very hard either since I mainly use the left vertical scrolling anyways.
The gsynaptics tool is very nice, too (helped me to deactivate tapping which can be very usful when writing texts ;-) ).
Edit: using gsynaptics, you probably still need to activate the driver in hal, though. Why do you want to get this working without hal? You are not talking about Karmic (which comes without hal) are you?

---

### Post by Rainier Piqual on 2009-06-24
Thank you for the hint, thawn. And yes, I am talking about karmic. 
But I installed gsynaptics anyway but it was no help concerning two-finger scrolling. There's just no option available in the menu. Is this because I have no (set up) HAL ? That's what I would guess.
Devicekit is the successor right? But I didn't find any insightful informations how to handle it.

---

### Post by Jartsuli on 2009-06-24
Thank you ALL!

I got my nc20 working quite nicely, first I tried most recent ubuntu with no success.. it was 'ok' exept lack of graphic performance.

..After that, I decided to try 8.10 (I read from here that it would be simple to make working).. And here I am :D

It works now quite nicely, installed ubuntu 8.10, patched by following [https://help.ubuntu.com/community/NC20#Full:](https://help.ubuntu.com/community/NC20#Full:) 'out of the box': (needed to make freq changing work) and updated alsa to 1.0.20 (so that I have working microphone) .. Only thing what wonders me, why I have low FPS when playing from youtube.. normal videofiles plays very nicely (mplayer playback). This problem seems to be only when playing in browser (?).


HUGE THANKS GOES TO THIS THREAD AND ITS ACTIVE MEMBERS !

--sorry about my english--

---

### Post by thawn on 2009-06-25
> **Jartsuli said:**
> 
Only thing what wonders me, why I have low FPS when playing from youtube.. normal videofiles plays very nicely (mplayer playback). This problem seems to be only when playing in browser (?).
--sorry about my english--

Yes, youtube videos will be a problem. That is because they are flash videos and adobe's flash player plugin is a huge performance sink. I think it doesn't even support hardware decoding acceleration (mplayer runs so smoothly because it uses the hardware acceleration provided by the via driver).

AFAIK youtube videos will also be slow under windows.

---

### Post by lunke on 2009-06-25
Note to everyone using the e_powersaver module for frequency scaling; it is considered dangerous on VIA C7 system since it it doesn't scale within the cpu spec. The acpi-cpufreq module should be used instead (needs patching though).

I also noticed the same problem using cpuidle instead of cpufreq, so the wiki should probably be updated so it doesn't recommend the e_powersaver module nor cpuidle.

Patches/discussion;
[http://patchwork.kernel.org/patch/28610/](http://patchwork.kernel.org/patch/28610/)
[http://patchwork.kernel.org/patch/28609/](http://patchwork.kernel.org/patch/28609/)

---

### Post by pureblood on 2009-06-26
I experience system freezes when I try to play videos on the external screen with the proprietary via driver. There does not seem to be any way to avoid it. Anybody with the same problem? I cannot play videos smoothly with the openchrome driver and I cannot play videos with the via driver. This is turning insane. I am seriously thinking about selling this laptop back on ebay. Via did not reply to my question about when they will update their drivers.

---

### Post by Scott Belden on 2009-06-26
I have installed xubuntu 9.10 alpha 2 on the samsung nc20.  Screen res, wireless, sound, all work.  The one bug that is driving a bit crazy is that after about 10-20 minutes the screen backlight shuts off.  Everthing is still there, I can see it with a flashlight to save and restart.  I would like to help debug for this machine, I love it, but I'm new to this. 
  Also, the func keys don't change brightness, but I'm sure most of you know this.
  If anyone knows a work around or fix for the screen shutoff it would be very welcome.
  All the best
  S

---

### Post by lyovushka on 2009-06-27
I want to say thank you to all of you and especially to Barry for the great howto. That was extremely helpful for installing ubuntu on my NC20. The only thing that went wrong is the binding of Fn+F9 key. For some reason the script /etc/acpi/wireless.sh refuses to turn off my wireless. Anyway, this is not a big issue.

---

### Post by lyovushka on 2009-06-27
> **Scott Belden said:**
> I have installed xubuntu 9.10 alpha 2 on the samsung nc20.  Screen res, wireless, sound, all work.  The one bug that is driving a bit crazy is that after about 10-20 minutes the screen backlight shuts off.  Everthing is still there, I can see it with a flashlight to save and restart.  I would like to help debug for this machine, I love it, but I'm new to this. 
  Also, the func keys don't change brightness, but I'm sure most of you know this.
  If anyone knows a work around or fix for the screen shutoff it would be very welcome.
  All the best
  S

There is a better workaround for the backlite issue. You may suspend the system by Fn+Esc and then resume it. Still annoying, but a little bit better :)

---

### Post by Jartsuli on 2009-06-27
> **lunke said:**
> Note to everyone using the e_powersaver module for frequency scaling; it is considered dangerous on VIA C7 system since it it doesn't scale within the cpu spec. The acpi-cpufreq module should be used instead (needs patching though).

I also noticed the same problem using cpuidle instead of cpufreq, so the wiki should probably be updated so it doesn't recommend the e_powersaver module nor cpuidle.

Hi. Could you explain to me, how you see problem with e-powersaver module? .. I dont understand so much about these, Im just happy that freq scaling works with e-powersaver module.

..Perhaps you could make a spep-by-step howto about this?

---

### Post by Jartsuli on 2009-06-27
Ok I've been playing with this for a few days now, and I've discovered that firefox3 when using gmail eats up all my CPU. Have anyone else see the same?

.. Good news though.. google chrome dev release is working quite nicely and it's alot lighter than firefox. .. as cons I must mention, that chrome doesnt support addblock feature by anyway (setting proxy is disabled in dev release)

-- discussion about firefox3 & gmail eating all cpu :confused:

---

### Post by thawn on 2009-06-27
> **lunke said:**
> Note to everyone using the e_powersaver module for frequency scaling; it is considered dangerous on VIA C7 system since it it doesn't scale within the cpu spec. The acpi-cpufreq module should be used instead (needs patching though).

I also noticed the same problem using cpuidle instead of cpufreq, so the wiki should probably be updated so it doesn't recommend the e_powersaver module nor cpuidle.

Patches/discussion;
[http://patchwork.kernel.org/patch/28610/](http://patchwork.kernel.org/patch/28610/)
[http://patchwork.kernel.org/patch/28609/](http://patchwork.kernel.org/patch/28609/)

Are you sure this affects the NC20? The Nano is NOT the C7, in fact, it is a complete redesign!!!

With e_powersaver my NC20 scales between 851 and 1700 MHz. Via specifies the nano used in the NC20 with 1600+MHz mentioning that the processor can do more than 1600MHz. So this does not seem too far off.

Has anybody noticed problems like crashes during extended periods of high cpu usage? I did recompile the kernel which took a few hours and did not have problems (at least not hardware related ones ;-) )

I will definitely stick with e_powersaver for now, until someone presents good evidence, that there actually are problems with that module.

---

### Post by lyovushka on 2009-06-27
I think the processor used in NC20 is 1300+ not 1600+

---

### Post by Jartsuli on 2009-06-27
> **thawn said:**
> Are you sure this affects the NC20? The Nano is NOT the C7, in fact, it is a complete redesign!!!

With e_powersaver my NC20 scales between 851 and 1700 MHz. Via specifies the nano used in the NC20 with 1600+MHz mentioning that the processor can do more than 1600MHz. So this does not seem too far off.

Has anybody noticed problems like crashes during extended periods of high cpu usage? I did recompile the kernel which took a few hours and did not have problems (at least not hardware related ones ;-) )

I will definitely stick with e_powersaver for now, until someone presents good evidence, that there actually are problems with that module.

I agree with you.. **"Building on the market-leading energy efficiency of the VIA C7® processor family, the VIA Nano processor family offers"** mentioned at [http://www.via.com.tw/en/products/processors/nano/]("http://www.via.com.tw/en/products/processors/nano/")

---

### Post by lunke on 2009-06-28
> **thawn said:**
> Are you sure this affects the NC20? The Nano is NOT the C7, in fact, it is a complete redesign!!!

With e_powersaver my NC20 scales between 851 and 1700 MHz. Via specifies the nano used in the NC20 with 1600+MHz mentioning that the processor can do more than 1600MHz. So this does not seem too far off.

Has anybody noticed problems like crashes during extended periods of high cpu usage? I did recompile the kernel which took a few hours and did not have problems (at least not hardware related ones ;-) )

I will definitely stick with e_powersaver for now, until someone presents good evidence, that there actually are problems with that module.
I believe the scaling is from 800MHz to 1.6Ghz or 1.5Ghz, some people have reported that unloading and then reloading the e_powersaver module acctually makes it scale correctly from 800 to 1600Mhz.
Haven't found anything other than the lkml emails though.

---

### Post by Sackley85 on 2009-06-29
> **nicxz said:**
> Hi Londonzombie,

Information on the NC20 in combination with Ubuntu Jaunty can be found at [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20) .

What I did for installation is first follow the howto @ [http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?22973.0#post_22976](http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?22973.0#post_22976) which gets you a working but slow ubuntu installation. It's slow because of the video driver. To fix that, I then installed openchrome ( [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) 'manual install')

Good luck!


Does anyone have any experience with this? The post at sammynetbook seemed too good to be true... And at this point, after reading as much as I can find on the topic, what version would be recommended to a newbie? It seems like Intrepid as far as I can tell from the posts here and the wiki.

Thanks for all the great info!

---

### Post by thawn on 2009-06-29
> **lunke said:**
> I believe the scaling is from 800MHz to 1.6Ghz or 1.5Ghz, some people have reported that unloading and then reloading the e_powersaver module acctually makes it scale correctly from 800 to 1600Mhz.
Haven't found anything other than the lkml emails though.
Yes, unloading and reloading the e_powersaver module helps (I describe how to do that on the first page of this thread). but even without reloading I did not have any problems despite the powersaver reporting roughly double frequencies (between 1.6 GHz and 3.2GHz) and even then the NC20 was stable even at high load, which leads me to believe, that the frequencies used are correct and just the reported frequencies are off. However as I said unloading and reloading the module helps and leaves a stable system.
also after reading the lkml email links you posted, I don't think that they actually affect the NC20, since they talk about problems with the C7 processors not the Nano. Since e_powersaver works without manual patching, I would recommend using that module (and reloading it at boot).

---

### Post by thawn on 2009-06-30
> **Sackley85 said:**
> Does anyone have any experience with this? The post at sammynetbook seemed too good to be true... And at this point, after reading as much as I can find on the topic, what version would be recommended to a newbie? It seems like Intrepid as far as I can tell from the posts here and the wiki.

Thanks for all the great info!

No version really works out of the box so far...
I do recommend intrepid and the via proprietary driver since that driver is a little bit more stable and supports video decoding acceleration for MPEG2 and 4.

The only difference between the wiki and the post at sammynetbook is that the wiki recommends to compile the openchrome driver to get the installation running. you might try to skip the compilation, change the video driver to fbdev in xorg.conf, and then continue with the installation...

good luck.

---

### Post by pureblood on 2009-07-01
I have read that to avoid the backlight of the LCD from not turning back on properly with the openchrome driver, it is enough to add to the xorg.conf file the option:
Option "VBEModes" "True"
Although this workaround should work only with 32 bit installations. Can anybody confirm this? I cannot since I downgraded my installation to Xorg 1.5.2 and I don't want to waste my time reinstalling all the packages. If it is indeed true, it should be added to the wiki.

---

### Post by lyovushka on 2009-07-01
I can deny that adding Option "VBEModes" "True" solves the backlite issue on 32 bit Ubuntu 9.04. Moreover the screen fails to load at all.

---

### Post by Jartsuli on 2009-07-02
I must ask, I've done so far installing 8.10 ubuntu, applied patch for cpu scaling, display adapter and compiled never alsa for working mikrophone.

.. Now aptitude wants to upgrade packages " linux-headers-2.6.27-14 linux-headers-2.6.27-14-generic linux-image-2.6.27-14-generic linux-libc-dev"

.. Im currently running 2.6.27-14-generic, if I install those updates, will it mess my system so that I must re-patch all ?

--I really dont understand so much about these--

big thanks :)

---

### Post by thawn on 2009-07-02
> **Jartsuli said:**
> I must ask, I've done so far installing 8.10 ubuntu, applied patch for cpu scaling, display adapter and compiled never alsa for working mikrophone.

.. Now aptitude wants to upgrade packages " linux-headers-2.6.27-14 linux-headers-2.6.27-14-generic linux-image-2.6.27-14-generic linux-libc-dev"

.. Im currently running 2.6.27-14-generic, if I install those updates, will it mess my system so that I must re-patch all ?

--I really dont understand so much about these--

big thanks :)
The problem is, that you patched and recompiled the kernel without installing it into a new slot. Therefore aptitude thinks you want the default kernel and does not recognize the one you compiled yourself. If you upgrade these packages, they will in fact undo your patching and mess up your system.

You would have to create a new kernel flavor as described in the wiki (caled nc20). but afterwards you would have to maintain that kernel yourself. which is a lot of hassle and requires hours of compilation time every time a security patch comes out...

I strongly recommend to follow the "shortcut to e_powersaver" in the wiki. That way, you only compile the one module and don't have to maintain your own kernel.

---

### Post by Jartsuli on 2009-07-02
> **thawn said:**
> The problem is, that you patched and recompiled the kernel without installing it into a new slot. Therefore aptitude thinks you want the default kernel and does not recognize the one you compiled yourself. If you upgrade these packages, they will in fact undo your patching and mess up your system.

You would have to create a new kernel flavor as described in the wiki (caled nc20). but afterwards you would have to maintain that kernel yourself. which is a lot of hassle and requires hours of compilation time every time a security patch comes out...

I strongly recommend to follow the "shortcut to e_powersaver" in the wiki. That way, you only compile the one module and don't have to maintain your own kernel.


Ok thanks, perhaps I just disable all updates, and wait for never release which hopefully supports this hardware fully out of box, some day soon :)

---

### Post by thawn on 2009-07-02
> **Milamber_Cubed said:**
> Thanks... I did see that, but I was wondering more about the via drivers since they dont specify 32/64bit support and there's a binary blob involved. I tried 64 bit and it didn't seem to like the via drivers (X just wouldn't fire up) so went with 32-bit Intrepid instead.
sorry, I didn't see that you were asking specifically for the drivers.
I don't think not having 64bit drivers is a big loss though, since I don't see a reason for 64 bit on the nc20 anyways (as explained before).

> Anyway, I was round at a friends house installing Ubuntu for them on their NC20 last night and this morning. The wiki page was massively helpful, so thanks to all involved in creating it, but there were some things which didn't go exactly as planned. I thought reporting back would be a good idea.

The major one was that the kernel patch and recompile (which I left running overnight) seemed to have failed when I checked it this morning with a " Previous or current ABI file missing!" message.

I managed to find from the blog posting linked to on the wiki that I needed to do the following:

```

cd ~/linux-2.6.27
cp debian/abi/2.6.27-XXX/i386/generic debian/abi/2.6.27-7.13/i386/nc20
cp debian/abi/2.6.27-XXX/i386/generic.modules debian/abi/2.6.27-7.13/i386/nc20.modules

```

After which the debs were created correctly and (most of) the Function keys proceded to work. 

Thanks, I included that in the wiki.

> 
The other thing that didn't work as planned was the wireless. There were no drivers listed in the System-->Hardware section either before or after the backports installation.

To be honest, the backports installation just was too much hassle for me, so I kissed the fn keys good bye and took the e_powersaver shortcut. therefore I never tested activating the wireless on a patched kernel. Have you tried manually loading the atheros ath5k driver, though?
you can find more info here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

It would be great, if you could test that and add your experience about wireless with a patched kernel to the wiki.

---

### Post by thawn on 2009-07-03
> **Jartsuli said:**
> Ok thanks, perhaps I just disable all updates, and wait for never release which hopefully supports this hardware fully out of box, some day soon :)
Actually, I strongly recommend against that because that way you would also miss the important security updates.
I would rather install the unpatched kernel and then compile the e_powersaver module manually, which works with the default kernel. That way you will miss out on the brightness keys but would still get frequency scaling and the automatic updates.
This is how you get the e_powersaver module to work:
[https://help.ubuntu.com/community/NC20#Compiling%20the%20e_powersaver%20module%20(Intrepid%20only)](https://help.ubuntu.com/community/NC20#Compiling%20the%20e_powersaver%20module%20(Intrepid%20only))

---

### Post by lyovushka on 2009-07-08
Some good news !!!!!!!!!!!!

I've been playing with the source code of openchrome driver and found the part responsible for turning back lite on. Also, I have downloaded the source of VIA's 2D driver and investigated it too. By the way, codes are very similar, though the openchrome code is cleaned up a lot, VIA's codes is really awful. I found out that in VIA's code back lite issues for VX800 are treated a little bit different. So I've bring them to the openchrome and bingo!!! the backlite comes back :)

The patch is attached, though it is quite dirty. Later on, I'll cleanup it and send to openchrome.

---

### Post by thawn on 2009-07-09
> **lyovushka said:**
> I've been playing with the source code of openchrome driver and found the part responsible for turning back lite on. 

You :guitar:

Keep up the great work!

---

### Post by Rainier Piqual on 2009-07-09
Thank you very much indeed.
But how to apply the patch?

---

### Post by lyovushka on 2009-07-09
cp patch.txt <your_openchrome_directory>
cd <your_openchrome_directory>
patch -p0 <patch.txt
make
sudo make install

---

### Post by Tarpoon on 2009-07-10
Hello,

I've been trying to get Ubuntu with compiz to run on a NC20 and have run into a wall.

I have managed to install 9.10 and openchrome, but as soon as I try to install the via drivers I get the following message during installing:
```
install the via driver!
........../usr/bin/install: reguläre Datei "/lib/modules/2.6.28-13-generic/kernel/ubuntu/via_chrome9/via_chrome9.ko" kann nicht angelegt werden: No such file or directory 
....... done!
```
I have tried to downgrade Xorg ( [https://help.ubuntu.com/community/NC20#Proprietary%20graphics%20driver%20(jaunty%20only](https://help.ubuntu.com/community/NC20#Proprietary%20graphics%20driver%20(jaunty%20only)) ), but get the same error message and now the desktop won't start at all.

Is there a way to get compiz to work with openchrome, or will I have to try to install 8.10 and hope the via drivers work there?

---

### Post by moldy on 2009-07-11
Hi Guys - firstly, thanks for the great write up and how-to.
But can someone give me an idea of how to start the process off.
I have my NC20, and have downloaded the 9.04 ISO.
I have made a USB stick using UNetbootin and it will bring up the bootloader.

However, when I try to go into a live session, I get the fuzzy screen.  It is obviously the NC20 (and it works on my other laptop).

But is there anyway to update the USB stick for these patches if it can't load?

I want to use the stick to boot from to test ubuntu out before i install it on its own partition.

Any help would be great?

Moldy.

---

### Post by thawn on 2009-07-11
> **Tarpoon said:**
> Hello,

I've been trying to get Ubuntu with compiz to run on a NC20 and have run into a wall.

I have managed to install 9.10 and openchrome, but as soon as I try to install the via drivers I get the following message during installing:
```
install the via driver!
........../usr/bin/install: reguläre Datei "/lib/modules/2.6.28-13-generic/kernel/ubuntu/via_chrome9/via_chrome9.ko" kann nicht angelegt werden: No such file or directory 
....... done!
```
I have tried to downgrade Xorg ( [https://help.ubuntu.com/community/NC20#Proprietary%20graphics%20driver%20(jaunty%20only](https://help.ubuntu.com/community/NC20#Proprietary%20graphics%20driver%20(jaunty%20only)) ), but get the same error message and now the desktop won't start at all.

Is there a way to get compiz to work with openchrome, or will I have to try to install 8.10 and hope the via drivers work there?

Firstly, you won't have much fun with compiz on the NC20 - It's just too slow (even with hardware acceleration)

To me it sounds like something went wrong in your xorg downgrading process...
also, from the via site you will need to download and install both the 3d driver and the kernel module source code

If you want hardware acceleration, I recommend using 8.10 and the via drivers for now...

If you follow the wiki, I recommend using the shortcut for e_powersaver and forget about the brightness keys.

edit: you might also want to have a look at my post on the first page of this thread for 8.10 installation instructions...

---

### Post by Rumpsteak on 2009-07-11
Hi guys and thanks a lot for the information!

I've got Xubuntu 9.04 running on my brand new NC20 now since yesterday. I chose 9.04 to avoid the hassle of kernel patching and some other stuff. 

I also wanted hardware acceleration though, so I chose to downgrade my xserver to 1.5.2. I downloaded the file collections from the wiki and tried downgrading but without success. I found another (easier?) way though (at [http://ubuntuforums.org/showthread.php?t=1171445](http://ubuntuforums.org/showthread.php?t=1171445)). You basically uninstall your xserver temporarily, change apt to point to intrepid instead of jaunty, install xserver (you will now get 1.5.2, and then revert sources.list back to jaunty again:

```

1) apt-get remove 'xserver-*'

2) apt-get remove libdrm2 libdrm-intel1 libgl1-mesa-dri

3) copy /etc/apt/sources.list /etc/apt/sources.list.jaunty

4) substitute 'jaunty' with 'intrepid' everywhere in /etc/apt/sources.list

5) apt-get update

6) apt-get install xserver-xorg-core

7) apt-get install libdrm2 libdrm-intel1 libgl1-mesa-dri

8) mv /etc/apt/sources.list.jaunty /etc/apt/sources.list

9) apt-get update

10) apt-get install <non_xserver_packages_eliminated_in_step_1>

```I think the only package I had to reinstall in 10) was x11-utils, x11-session-utils or x11-xserver-utils (can't really remember). Then I just followed the wiki instructions for installing the proprietary driver. So now I get 461 FPS in glxgears. Wohoo. (And there's no backlighting issue). 

I guess you just have to be aware not to upgrade your xserver packages, but apart from that I see no problems with the downgrade method. I would actually recommend this method as it was fairly easy to do. 

I also followed the wiki for the Fn Brightness keys (Adding NC20 to HAL). With the original kernel (2.6.28-11), the Fn keys repeat indefinitely. But with the newest kernel upgrade there was no problem. Brightness keys are now working perfectly.

The other Fn-hotkeys do not work out of the box in Xubuntu 9.04 though (because of Xfce). However, after adding NC20 to HAL, they do get recognized by xev as XF86WLAN, XF86AudioLowerVolume, XF86Launch3, so it should be pretty easy to tie them to their correct actions.

Using xev, I can also see that the Fn-F5 (Backlight on/off) gets recognized as XF86Launch1. Does anyone know a script to turn backlighting on/off? If so, it should be possible to tie that hotkey to have this working as well. 



[I]Re: Tarpoon
[/I]
You could try my method (but obviously changing back to karmic instead of jaunty sources).


Hope this helps!

---

### Post by Jartsuli on 2009-07-12
Hello, Im trying to find fix for total system halting when using mobile phone as an wlan-3G adapter (joikuspot premium software). After googling, I think that problem is in ubuntus Atheros wlan driver. 

Im using 8.10 ubuntu, with support for 5xxx series of Atheros 802.11 wireless lan cards.

Problem occures just in minutes when using WEP encryption, but if I disable all enclyption link may work for several hours.. but Its still unreliable, and when it crash youll need to make hard boot (nothing else works)

Another way to go, is to try using windows driver with ndiswrapper (XP works well with the same ad-hoc network)

[SIZE=7]?[/SIZE]

---

### Post by Tarpoon on 2009-07-12
> **Rumpsteak said:**
> 
[I]Re: Tarpoon
[/I]
You could try my method (but obviously changing back to karmic instead of jaunty sources).


Hope this helps!

Thanks, I will try it out. But why would I want to use karmic instead of jaunty when I install jaunty on the netbook?

---

### Post by Tarpoon on 2009-07-12
Ok, I believe I have found one of my problems:

I had copied the VIA drivers on my Desktop and tried to install them from there.
I guess this is was wrong... where do I need to copy them?
When I tried to mv them to / I was told that the bin folder could not be moved because the targed directory was not empty.

-edit-
Also when doing "1) apt-get remove 'xserver-*'" and later at "6) apt-get install xserver-xorg-core" the netbook seemed to freeze at restarting the hardware abstraction layer. Can I press CTRL + C, or do I just have to wait longer?

---

### Post by Rumpsteak on 2009-07-12
> Thanks, I will try it out. But why would I want to use karmic instead of jaunty when I install jaunty on the netbook? 	

You wrote that you were trying to install 9.10. But if you're trying to install 9.04, you should use jaunty obviously. 

> I had copied the VIA drivers on my Desktop and tried to install them from there.
I guess this is was wrong... where do I need to copy them?
When I tried to mv them to / I was told that the bin folder could not be moved because the targed directory was not empty.

-edit-
Also when doing "1) apt-get remove 'xserver-*'" and later at "6) apt-get install xserver-xorg-core" the netbook seemed to freeze at restarting the hardware abstraction layer. Can I press CTRL + C, or do I just have to wait longer?

It doesn't matter much where you put the files. But, are you trying to install while still in graphical mode perhaps? 

Hit Ctrl-Alt-F1 to use the shell instead. Also do ```
/etc/init.d/gdm stop
``` to stop the graphical interface.

---

### Post by billy boy on 2009-07-13
Has any one else got Rumpsteak's method of getting an older version of xserver on Jaunty to work?

I've tried a few times on a fresh install and have had no joy.

Step 7 seems to be an issue: when I try to reinstall the 3 packages i get a message saying that I already have the newest versions...not sure what i'm doing wrong. In any case, the GUI wont come back up on reboot.

I'm worried that the laptop seems to run very hot when using openchrome - much hotter than when I use the XP partition, and, I assume, when using the via drivers.

---

### Post by lyovushka on 2009-07-20
Hi guys,

During inaccurate cleanup of the keyboard, I have broken a pair of keys. Does anyone know from where I can order a black US keyboard.

Thanks in advance

---

### Post by lyovushka on 2009-07-21
Hi guys,

Already found a keyboard in Armenia. Hard to believe, but there is an official Samsung service center in Armenia :)

---

### Post by moldy on 2009-07-22
Just a query on Gimp.  Somebody mentioned a while back that their whole system freezes when Gimp loads.  Mine does the same.
Anybody know whether this is an NC20 problem or a Gimp problem?  If it is an NC20 problem, does anybody know a fix?
Thanks in advance, Moldy.

---

### Post by Simon_H on 2009-07-29
Hi,
is anyone of you using 802.11i? Is it working with the NC20 wireless card? Does the ath5k driver support it?

EDIT: After more googling I found out how to do it: You have to use wpa_supplicant with the nl80211 driver (I only tried wext and madwifi before, which both failed), e.g.:

wpa_supplicant -i wlan0 -D nl80211 -c your_config.conf [-B]



Simon

---

### Post by pureblood on 2009-08-01
Did anybody notice that with kernel 2.6.28-13 the system can suddenly freeze when performing intense hard drive tasks (like removing large files or copying a lot of files)? Do you know what causes the problem and if it has been fixed in the newest kernels?

---

### Post by Simon_H on 2009-08-02
A comment on the Wiki:
[https://help.ubuntu.com/community/NC20#Brightness](https://help.ubuntu.com/community/NC20#Brightness)

I'm not using Ubuntu, so I don't edit it myself, but if the same is true you might want to change that:

System upgrades usually overwrite files in  [FONT=monospace][/FONT]/usr/share/hal/fdi[FONT=monospace]/, so if the user edits files like [/FONT]/usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi it is generally a good idea to copy it to /etc/hal/fdi/ (in the appropriate subdirectory), where the will be safe from changes. On archlinux these files are then used automatically by hal.


Simon

---

### Post by lyovushka on 2009-08-05
Hi guys,

The problem with wireless annoyed me and I started to google for the solution.
In an article dedicated to NC10 I found that the guys suggests to blacklist ath_hal and ath_pci. So I added the line

blacklist ath_hal

to the file /etc/modprobe.d/blacklist-ath_pci.conf and its is about a week that my wireless work OK.
Simultaneously I've replaced NetworkManager with wicd, but I don't think this metters.

---

### Post by thawn on 2009-08-06
> **lyovushka said:**
> The problem with wireless annoyed me and I started to google for the solution.
In an article dedicated to NC10 I found that the guys suggests to blacklist ath_hal and ath_pci. So I added the line

blacklist ath_hal

to the file /etc/modprobe.d/blacklist-ath_pci.conf and its is about a week that my wireless work OK.
Simultaneously I've replaced NetworkManager with wicd, but I don't think this metters.

What problem with the wireless are you referring to?

---

### Post by lyovushka on 2009-08-10
> **thawn said:**
> What problem with the wireless are you referring to?

I refer to the problem of driver breaking. When the wireless driver fails to connect to the Access Point and NetworkManager prompts for the password. I thought this is the only problem with Atheros wireless on NC20

---

### Post by Sandrider on 2009-08-10
Hi guys,

for those who still don't have completely working function keys with their NC20 I made two bash scripts that provide access to display brightness control and toggling of wireless network...

Just put the scripts in a folder you like and set up links in Ubuntu settings - keyboard shortcuts (see attached screen shot). I used the "Windows-logo" key that I don't need anyway as a substitution of the fn-key that you don't have access to using this deamon.

Additionally you should add two lines to your sudoers file (/etc) to be able to start the scripts directly as root without being prompted for a password:
%admin ALL=NOPASSWD: /home/scripts/bright.sh
%admin ALL=NOPASSWD: /home/scripts/wireless.sh

I hope that's helpful for someone...

---

### Post by chortle on 2009-08-12
I have the same problems with graphics noted in this thread. I can't easily access the internet from Bangladesh, which makes the suggested work arounds a real pain.

What are the chacnes the next version of Ubuntu will support the Samsung NC20?

I managed to get Fedora Core 5 working. I'll live with that for now.

---

### Post by chrome9 on 2009-08-25
Yesterday **VIA** released the source for the 2d-driver for Ubuntu 9.04. I haven't  benn testing it yet. There were posts on a HP2133-Forum that they had issues with the autoconf-version of Jaunty. So fire up your compiler and go. If it works and brings significant advantages it shoud be added to the NC20-Howto. So far, good luck:guitar:
Edit: Compiling was no problem but X doesn't start. Doin' some error-searching now....

---

### Post by lyovushka on 2009-08-25
> **lyovushka said:**
> I refer to the problem of driver breaking. When the wireless driver fails to connect to the Access Point and NetworkManager prompts for the password. I thought this is the only problem with Atheros wireless on NC20

Oooops, had the problem again, which means that it is not fixed for now :(

---

### Post by pureblood on 2009-08-25
chrome9, I assume the forum you were talking about is this:
[http://www.hp2133guide.com/forums/viewtopic.php?t=2468](http://www.hp2133guide.com/forums/viewtopic.php?t=2468)
Have you had any luck making the driver work? I am a bit scared to try after you told us that X was not working. Although if it does work, that would be really good news.

---

### Post by pureblood on 2009-08-25
I confirm that the new driver does not work. I get the screen completely black and I cannot revert back to the console anymore. Do they even test the driver on their machines before releasing it?

---

### Post by thawn on 2009-08-26
> **lyovushka said:**
> Oooops, had the problem again, which means that it is not fixed for now :(

I myself haven't had any problems with my wireless for a long time and that is without any modifications that I can think of (atheros 5xxx drivers and the standard NetworkManager). However, yesterday the problems with networkmanager asking for a password repeatedly reappeared. Notably I have the problem with both my ubuntu notebooks (an old dell and the NC20), indicating that it is a more general problem.
I have the hunch, that everything works fine, as long as there is only one computer connected to the wireless. Can you confirm that?

---

### Post by chrome9 on 2009-08-26
@Pureblood: Compiling and loading of the modules via, via_chrome9 works but in the  Xorg.0.log I find one little thing I can´t explain. It might be interesting

(II) Loading sub module "viavideo"
(WW) Warning, couldn´t open module viavideo
(II) UnloadModule: "viavideo"
(EE) Failed to load module "viavideo" (module does not exist, 0)
(WW) Couldn´t open viavideo

Yesterday VIA also posted driver for the VX800-Chipset which contains support for cpufreq, the cardreader and so on:

[http://linux.via.com.tw/support/beginDownload.action?eleid=321&fid=621](http://linux.via.com.tw/support/beginDownload.action?eleid=321&fid=621)

 It´s availlable as debs or the source. The debs are compiled for 2.6.28-11 (I´m using 2.6.28-15) so I tried to compile them an ended up with errors. ](*,) 

After a little bit of research I managed to compile and install the new cpufreq-via module! \\:D/
Now I try the via-sdmmc card-reader-module. 

Stay tuned...:guitar:

---

### Post by chrome9 on 2009-08-26
Yeah, cardreader works! So please guys, get the graphics driver working. My favorite would be the openchrome with 3d-support...:popcorn:
Good night from germany (it's 3:14am local time)

---

### Post by pureblood on 2009-08-27
> (EE) Failed to load module "viavideo" (module does not exist, 0)

Try to run first 'sudo depmod -a'.

> The debs are compiled for 2.6.28-11 (I´m using 2.6.28-15) so I tried to compile them an ended up with errors.

That is a shame. I hate when they do that. It just reminds how not flexible proprietary software is.

> Now I try the via-sdmmc card-reader-module.

If you go to [https://help.ubuntu.com/community/NC20#SD / MMC Card Reader]("https://help.ubuntu.com/community/NC20#SD / MMC Card Reader") you will notice that there has been a solution for that for a long time. And you can use whatever kernel you like.

---

### Post by chrome9 on 2009-08-27
@pureblood: I ran depmod -a. My xserver is starting now, but I have a screen that changes the color after a few seconds. I had this problem before, I think with the old 3D-driver but I can´t remember how to fix it. It has something to do with the xorg.conf.

I knew the page about the NC20 and that there was a card-reader-module available, but I´m testing the new stuff that VIA posted on the official page. Maybe we can generate some kind of NC20-Package which fixes all the problems at one time...

---

### Post by ashwyn on 2009-08-27
I'm having the same problems after sucessfully compiling and installing the drivers.  I've pasted myxorg log below in case it helps anyone.  I'm trying to use the CN896/VN896 drivers on a .28-15 kernel.

Really baffled atm, below is my xorg.log

Something confusing.  It says that the X.Org X Server version is 1.6, when in synaptic it says 1.7, which is how it should be given that I'm running jaunty.

Really need help, have no idea what next.

> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux user-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 27 11:47:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] rev 1, Mem @ 0xc0000000/536870912, 0xfc000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 5.74.255
	Module class: X.Org Video Driver
(II) LoadModule: "via"
(II) Reloading /usr/lib/xorg/modules/drivers//via_drv.so
(II) UnloadModule: "via"
(II) Failed to load module "via" (already loaded, 156369760)
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 65536 kB
(II) VIA(0): VESA VBE OEM: VIA N3364


(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(**) VIA(0): Option "ActiveDevice" "LCD"
(==) VIA(0): Using XAA acceleration architecture.
(II) VIA(0): MergedFB mode forced off.
(**) VIA(0): Active Device is LCD.
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VGA BIOS Version is = 10.0
(II) VIA(0): VGA BIOS Release Date Is: 2007/4/25
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) VIA(0): DPI set to (96, 96)
(II) VIA(0): Output CRT using monitor section Monitor0
(II) VIA(0): Output DVI has no monitor section
(II) VIA(0): Output LCD has no monitor section
(EE) VIA(0): Unknown EDID version 0
(II) VIA(0): Output CRT disconnected
(WW) VIA(0): No outputs definitely connected, trying again...
(II) VIA(0): Output CRT disconnected
(WW) VIA(0): Unable to find initial modes
(EE) VIA(0): No valid initial configuration found
(II) VIA(0): VIAFreeScreen
(II) UnloadModule: "via"
(II) UnloadModule: "xaa"
(II) Unloading /usr/lib/xorg/modules//libxaa.so
(II) UnloadModule: "fb"
(II) Unloading /usr/lib/xorg/modules//libfb.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by thawn on 2009-08-28
> **chrome9 said:**
> @pureblood: I ran depmod -a. My xserver is starting now, but I have a screen that changes the color after a few seconds. I had this problem before, I think with the old 3D-driver but I can´t remember how to fix it. It has something to do with the xorg.conf.

I knew the page about the NC20 and that there was a card-reader-module available, but I´m testing the new stuff that VIA posted on the official page. Maybe we can generate some kind of NC20-Package which fixes all the problems at one time...

> **r4idei said:**
> Ohh thanks :D This option did the work: 	

Option		"ActiveDevice" "LCD,CRT"

Adding this option to my xorg.conf in the display section did work. good luck!

---

### Post by thawn on 2009-08-28
> **ashwyn said:**
> I'm having the same problems after sucessfully compiling and installing the drivers. 

Something confusing.  It says that the X.Org X Server version is 1.6, when in synaptic it says 1.7, which is how it should be given that I'm running jaunty.

Really need help, have no idea what next.

AFAIK there is no xorg server version 1.7 and jaounty does use 1.6 so this seems to be o.k.

to get the drivers working:

try to run "sudo depmod -a"
and add

Option "ActiveDevice" "LCD,CRT"

to your xorg.conf

good luck

---

### Post by luc765 on 2009-08-28
Hello,

 I have just installed jaunty on my PC NC20 recently bought while following your informations.
Could you tell me where I can find the package : drm-via_chrome9-2.6.27-85a-44411-src.tar.gz it is no more available on the Via site

Thank beforehand 

Lucien

---

### Post by lyovushka on 2009-08-28
> **thawn said:**
> I myself haven't had any problems with my wireless for a long time and that is without any modifications that I can think of (atheros 5xxx drivers and the standard NetworkManager). However, yesterday the problems with networkmanager asking for a password repeatedly reappeared. Notably I have the problem with both my ubuntu notebooks (an old dell and the NC20), indicating that it is a more general problem.
I have the hunch, that everything works fine, as long as there is only one computer connected to the wireless. Can you confirm that?

Well, for now I can't neither confirm nor reject that the source of the problem is the fact that multiple machines are connected to the same wireless. I've tried to experiment a little bit but with no luck. The reason is that it is a rare thing that my pc is alone connected to the access point. But it may well explain why I thought the problem is fixed: it seems like every one was in a vacation and I was the only person to use the Internet from my home for that period of time.

---

### Post by chrome9 on 2009-08-29
Sometimes the ability of reading helps a lot.... I compiled the wrong DRM module!You'll have to take th H5DRM_Independant_2.6.27_28 for the VX800-Chipset. I only whatched out for the right kernel version... Now I'm going to check out the performance of video acceleration. And in my dreams there's a working 3D-driver out next week...

---

### Post by tom09 on 2009-08-29
Just out of interest: Do you have messages like "PCIE init failed! Using PCI" and "*ERROR* Allocate memory error!" in your kernel log file after starting the X server? I get those with the new 2D driver (the old binary only one did not produce them) and neither EXA acceleration nor 3D acceleration is working anymore (Desktop icons are gone when enabling EXA).  Thanks in advance tom09

---

### Post by Simon_H on 2009-08-29
> 
and add

Option "ActiveDevice" "LCD,CRT"

to your xorg.conf


If you don't need the CRT output you can disable it. I think it gives a little more runtime (battery rate is down by about 30 mA, i.e. about 3%), but I didn't do detailed tests:

```

Option "ActiveDevice" "LCD"

```

---

### Post by lyovushka on 2009-08-30
> **thawn said:**
> I myself haven't had any problems with my wireless for a long time and that is without any modifications that I can think of (atheros 5xxx drivers and the standard NetworkManager). However, yesterday the problems with networkmanager asking for a password repeatedly reappeared. Notably I have the problem with both my ubuntu notebooks (an old dell and the NC20), indicating that it is a more general problem.
I have the hunch, that everything works fine, as long as there is only one computer connected to the wireless. Can you confirm that?

Today my wireless has gone even though my laptop was the only one to connect to wireless access point. Thus, your guess is not correct, at least for my case.

---

### Post by thawn on 2009-08-31
> **lyovushka said:**
> Today my wireless has gone even though my laptop was the only one to connect to wireless access point. Thus, your guess is not correct, at least for my case.
Same here, Maybe its the date ;-) - Just kidding...
In my case there are about 20 wireless networks that I see in my neighborhood. Maybe the problem is not caused by other people in our own networks but by too many other networks interfering with ours...
How many networks are in your neighborhood?

---

### Post by lyovushka on 2009-08-31
> **thawn said:**
> Same here, Maybe its the date ;-) - Just kidding...
In my case there are about 20 wireless networks that I see in my neighborhood. Maybe the problem is not caused by other people in our own networks but by too many other networks interfering with ours...
How many networks are in your neighborhood?

Not many, there is only one network beside mine.

---

### Post by lyovushka on 2009-08-31
Several days ago a new Skype was release and today ALSA 1.0.21. I've tried to update both but the problem with internal mic was not fixed. Then I started to play with Skype sound options. Instead of the default option for Microphone, I chose "HDA VIA VT82xx, ALC272 Analog Front speakers (front:CARD=VT82xx,DEV=0)" - the third one in the list. Then everything was working well. I'm not sure, but maybe the update of Skype and ALSA do not matter here :)

---

### Post by OpenFish on 2009-09-01
Ladies and Gentlemen Congratulations on a fantastic job well don this thread and the wiki u have all contributed to are supurbe!!

i was easly able 2 set up jaunty up with openchrome and despite much efort was unable to get the graphics to work well enough to wach dvds full screen!

so 2 day dispite some very stupide foul ups i have intrepid workin with 450+ fps from glxgears and all the network and many function keys working but i did it a way no one else seems 2 have tride if u have then sorry but i didnt notice and did it my own way!

fist used the alt 8.10 installer (noobs dont foget (i did) that u need 2 add vga=771 4 it 2 work!)

installed ssh

then from desktop (not necessary but my preference)

installed the driver the way the wiki says but it needs updating as the file names are diffrent on the download page !! ps if u cant open the file i had 2 mount them to decompres them (right click then second option)

add nc20 to /usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi like in wiki

then from the nc10 wiki

```
Alternatively one can use an actual 2.6.28 Ubuntu Jaunty kernel without recompiling a new one from scratch. This can be done easily with the apt-tools. To install a Jaunty kernel by the apt-tools first create an /etc/apt/preferences file with the following content:

Package: *
Pin: release o=ubuntu,a=jaunty
Pin-Priority: 60

The pin priority 60 avoids the automatic installation of Jaunty packages so Intrepid packages are still preferred..

For the apt-tools to find Jaunty packages the /etc/apt/sources.list needs some amendment or even better create a new file /etc/apt/sources.list.d/jaunty.list with the following content:

# Jaunty package repository
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted

Create the right key mappings as stated in the next section (update the file /usr/share/hotkey-setup/samsung.hk).

After that do a

sudo apt-get update

As at February 21st the actual 2.6.28 kernel package is linux-image-2.6.28-8-generic. To install it do a

sudo apt-get install linux-image-2.6.28-8-generic

In case you need the kernel header files (e.g. you use VirtualBox and the kernel module has to be rebuilded) do a

sudo apt-get -t jaunty install linux-headers-2.6.28-8-generic

After a reboot both brightness keys should work
```

now the wireless ethernet just works!!! (with out wiki fix!!)
but the fnk keys dont
so 
```
sudo nano /etc/apt/sources.list.d/jaunty.list
```
```
# Jaunty package repository
deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main


deb http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted

```
then
```
sudo apt-get update
sudo apt-get install linux-image-2.6.28-15-generic
sudo apt-get -t jaunty install linux-headers-2.6.28-15-generic

```
and fn keys work 
and u can load e_powersaver with out further kernal messing around!!
i will try jaunty again and try 2 use this methord to down grade xorg but ??
will finish of the wiki ie card reader etc and report back 2 morrow as i have bin at the computer 4 2 longe now!! (i messed up quite a few times!! as i was experimenting but noobs do not fear this isnt hard and recomend the laptop!!)

oh nearly fogot be very care full as i did 
```
sudo apt-get update
sudo apt-get install linux-image-2.6.28-15-generic
sudo apt-get -t jaunty install linux-headers-2.6.28-15-generic rhythmbox

```
and while every thing still seemed to work on reboot after the mouse appeared at start up gnome failed 2 mitirealise and this cost me hours trying 2 fix!!

so what do u think??

will

UPDATE: last night at party wireless was bit ropey and then this morning the wireless was poor  again so i got thinking about backport mods and opened synaptic (System>administration>synaptic package manager) and surched for 'backports' scrolled down passed the headers modles and applyed the juanty vertions of 'linux-backports-modules' and removed the intrepid versions and rebooted
now when i look at gnome network managers 'connection information' i get the driver ath5k instead of ath5k_pci and wireless seems 2 work much better

---

### Post by pureblood on 2009-09-01
> **thawn said:**
> Adding this option to my xorg.conf in the display section did work. good luck!

@thawn could you please share your whole xorg.conf with us? I am using Xorg 1.6.0 and the only result I got with the latest via driver, that is, version 86a, is a complete black screen, although KDE starts ok. It seems to me that the only problem is that the screen is off.

---

### Post by pureblood on 2009-09-01
Damn via, now I understand why the screen was completely black. Thanks via software engineers for your complete lack of documentation of the driver. I wish I will see the day companies will just not be able to sell hardware without providing decent support to linux, even for people that understand nothing about computers. Anyway, you need to add the following section to the xorg.conf file:
> Section "ServerLayout"
        Identifier      "X.org Configured"
        Option          "RandR"         "false"
EndSection
Also, for reasons that go beyond my understanding, you will also need to add this line to the Device section of the xorg.conf file:
>         Option          "ActiveDevice"  "LCD,CRT"
If you do not, the resolution will be set to 1024x768 instead of 1280x800, no clue why. There is also another option, after you unpack the file via-xserver-86a-50283_src.tgz, enter the directory via-xserver-86a-50283_src/XServer/Misc and run the following commands:
> chmod a+x vinstall_ubuntu
./vinstall_ubuntu
Then edit the file /etc/X11/xorg.conf and add the line
>         Option          "ActiveDevice"  "LCD,CRT"
to the Device Section as previously specified. I am going to add these instructions to the [wiki]("https://help.ubuntu.com/community/NC20") and remove the section about Intrepid, since I guess with this addition, there is no need to install Intrepid on this laptop anymore.

---

### Post by OpenFish on 2009-09-02
@pureblood with the setup u have after the new wiki what kind of fps do u get from glxgears and can u play dvds smothly and can u use gimp??

thnkx

will

---

### Post by lyovushka on 2009-09-02
> **pureblood said:**
> I am going to add these instructions to the [wiki]("https://help.ubuntu.com/community/NC20") and remove the section about Intrepid, since I guess with this addition, there is no need to install Intrepid on this laptop anymore.

I've tried to use your hints in the wiki but with a little luck.
First of all ./vinstall_ubuntu need to modify xorg.conf so it requires superuser privileges. When I run sudo ./vinstall_ubuntu I get

```
install the via driver!
.../usr/bin/install: cannot stat `./bin/via_drv.so': No such file or directory
.../usr/bin/install: cannot stat `./bin/libGL.so.1.2.via_chrome9': No such file or directory
/usr/bin/install: cannot stat `./bin/via_chrome9_dri.so': No such file or directory
.../usr/bin/install: cannot stat `./bin/via_chrome9.ko': No such file or directory
......done!
Original X config file was saved as /etc/X11/xorg.conf.viabak
Caution!!
Need add the Option "ActiveDevice" "XXX" into /etc/X11/xorg.conf and reboot the system!

```

And gdm fails to start.
I managed to find via_drv.so, created bin directory with it and rerun ./vinstall_ubuntu. After it gdm starts but applications (such as glxgears) fails to load complaining that libGl.so.1 not found.

---

### Post by lyovushka on 2009-09-02
found all these shared objects in the package chrome9.83-242-sl10.1 which was somewhy located under Ubuntu 9.04 (by the way, it is no longer there). Finally managed to get 360 FPS on glxgears, but most opengl applications such as google-earth and supertuxkart hang the system.

---

### Post by tom09 on 2009-09-02
> **lyovushka said:**
> found all these shared objects in the package chrome9.83-242-sl10.1 which was somewhy located under Ubuntu 9.04 (by the way, it is no longer there).
The most recent versions (v85a) of via_chrome9_dri.so and libGL.so.1.2.chrome9 can be found on linux.via.com.tw when "Ubuntu 8.10" and "VX800" are selected.
Btw, do not mix the latest via open source driver (v86a) with these DRI drivers, it will crash your system when starting an OpenGL program that uses textures.

bye, tom09

---

### Post by pureblood on 2009-09-03
> **OpenFish said:**
> with the setup u have after the new wiki what kind of fps do u get from glxgears and can u play dvds smothly and can u use gimp??

With glxgears I get about 490 fps, but I doubt that means much anyway. The driver is still buggy and pretty bad as it used to. I also don't have a dvd player, but I can play almost any video without any problem (other than the mov files generated by my camera with the mjpeg codec, but I had problem opening those even on a laptop with nvidia).

But I do realize now that libGL.so.1.2.chrome9 comes from the older driver in the 5.74.33.85a-44597.tar.gz package. I just did not notice since I had installed that previously. What a mess the people at via have done! I really do not understand. I will fix this in the wiki.

---

### Post by thawn on 2009-09-03
> **pureblood said:**
> @thawn could you please share your whole xorg.conf with us? I am using Xorg 1.6.0 and the only result I got with the latest via driver, that is, version 86a, is a complete black screen, although KDE starts ok. It seems to me that the only problem is that the screen is off.
I guess you fixed it already, but just in case, my xorg.conf is in [this post on the first page of this thread]("http://ubuntuforums.org/showpost.php?p=6911954&postcount=10"), I haven't changed it since...

---

### Post by OpenFish on 2009-09-03
@pureblood thank u very much 

i quite agree via really are doing a poor job but if people are finally able 2 get 9.04 working with half descant drivers then it seems they have finally got there act together and i thank them but am looking 4ward 2 an even better job in future :confused:

i am very happy with my quite easily setup 8.10 but wounder if i should take the plunge and try 9.04 again so my question is:

and gose out 2 u all could a few poeple kindly post what they have done and what results they have got thanks

i'll start

as of last sunday 30th Aug with 9.04 (before pureblood last update 2 wiki) i could only get openchrome drivers 2 work this ment

full X
gimp opens but will not load a pic (crash)
videos work but full screen quolity is 2 poor 
screen will not wake up with out suspend 2 ram then resume (so u can only have a blank screen if idle not good 4 battery life!)
all Fn keys and e_power are good
battery only seems 2 last 2 and a bit hours nearly 3 hours
(crashes with heave file movement eg 20GB of music )

but i then installed 8.10 and 3d driver installed very easy
but lots of kernal probs (eg Fn keys, e_power mod etc)
so added some 9.04 sources to apt and installed latest kernal 2.6.28-15-generic (as i said before... this is very doable.. if not easy) i now have 

full X
full screen dvds (from usb dvd or .iso's) good quality
google earth is usable and just found my house (but clames 2 be in software mode and is slow but usable)
gimp works with out hitch
if idle with out ac power screen turns completely off and wakes with a move of the mouse (this dont work in 9.04)
all Fn keys and e_power are good (in 9.04 the cpu freq applet sometimes says 2x the actual speed but not with 8.10)
but no compiz (i dont want any fancy stuff but the awn panel would be fab!)
flash vids are acceptable if kept no bigger than standered iplayer size not the biger iplayer window and full screen is a no no.. very poor for all flash (avrage utube size is fine tho)
battry seems 2 last well over 3 hours usually 3 and a half hours
(occasional crashes with ridiculously heave file movement eg 60GB of film over network and 8GB iso between partitions)

(ps if i say it dont work that is only with my last openchrome set up and may be out of date 4 new via drivers)

thanks 

will

---

### Post by harrykipper on 2009-09-04
what you guys are referring to are 32-bit installs, right?
because in Ubuntu 64 the via driver doesn't work at all...

---

### Post by thawn on 2009-09-04
> **harrykipper said:**
> what you guys are referring to are 32-bit installs, right?
because in Ubuntu 64 the via driver doesn't work at all...
But 64 bit doesn't make sense at all on a nc20 either...

---

### Post by harrykipper on 2009-09-06
> **thawn said:**
> But 64 bit doesn't make sense at all on a nc20 either...

well, the Nano is a 64bit processor. Via advertise their platform as 64bit capable, opposed to the 32-bit only atom. 
One would expect that their drivers *at least* load in a 64bit system...

---

### Post by luc765 on 2009-09-06
Just for informations (French speaking ubunteros)

1) - Installed jaunty 9.04 following the pureblood's wiki (many, many thanks, great job)
kernel 2.6.28-15-generic

2) - I have increase the memory to 2GB (Kingston M25664G60) and put in the Bios an allocation of 256MB for the graphic memory

3) Video-graphic driver : OpenChrome 
- sudo apt-get purge compiz* evolution xsane-common
- install VLC and mplayer
- Firefox plugin : mplayer
- The is absolutely no problem to read DVD or Divx fullscreen through USB DVD reader and VLC or Mplayer. Wonderful 100% 
- glxgears = 96i/s !!!! but except compiz everything works well 

4) Replace metacity by xfwm4 in order to have the store effect :
After having made all your preferences for metacity do :
sudo apt-get install xfwm4
sudo xfwm4 --replace

4) Mouse bluetooth :
- After recognition of the mouse by the system do :
sudo hidd --search

5) Sound-Microphone : install alsa1.020 via the script see :
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

6) SD/MMC card reader :
Download at : [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
- OS : 9.04 and Platform : VX800
- the pack : VX800 BSP
- choose SDMMC/source and :
$cd path/source 
$make
$sudo make install
Nothing else and it works perfectly

7) Skype :
- video : perfectly but I have change the resolution :
$gedit /home/yourname/.Skypeyouridentification/config.xml
Add :
<CaptureHeight>120</CaptureHeight>
      <CaptureWidth>160</CaptureWidth>
like that, just after </StatsSender>  :

 </StatsSender> 
    <Video> 
      <AutoSend>1</AutoSend> 
      <CaptureHeight>120</CaptureHeight>
      <CaptureWidth>160</CaptureWidth>
    </Video>
- sound : like everybody the microphone give a sound stretched 

8) Working keys : the 4 most important :
Sound (+ - and mute) and desable touchpad

All the other keys based on Fn do not work

9) Add a magnifier through keyboard shortcut (Preferences/keyboard shortcut/Add)
Ctrl + Top page : command : magnifier -z 1.5 -m -f
Ctrl + End page : command : pkill magnifier

10) Cryptkeeper do not work correctly on NC20 I replace this by TrueCryp

Lucien

---

### Post by thawn on 2009-09-07
> **harrykipper said:**
> well, the Nano is a 64bit processor. Via advertise their platform as 64bit capable, opposed to the 32-bit only atom. 
One would expect that their drivers *at least* load in a 64bit system...

of course, that would be nice, but unless you do any double precision calculations (e.g. a linpack benchmark) or spend copious amounts of money on >=4GB ram, 64bit does not make sense. Therefore I think it is o.k. to not have working 64 bit drivers. Which I abbreviated into:
64bit does not make sense on the nc20!

---

### Post by lyovushka on 2009-09-09
Seems like I've found a solution to the wireless problem. It is to ndiswrapper instead of native drivers.
ndiswrapper is program that allows to use windows drivers in Linux. First I used the drivers from the official website, but didn't manage to make them work. Then I came across the thread [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828). However the link to the driver provided there was broken. After intensive googling I found the driver here [http://repo.ugm.ac.id/ekstra/driver/wireless/](http://repo.ugm.ac.id/ekstra/driver/wireless/) . The driver is working well for now, hope all the problems in the past.

---

### Post by lyovushka on 2009-09-09
With ndiswrapper wireless hangs even more often :(.
Switched back to ath5k for now.

---

### Post by thawn on 2009-09-10
> **lyovushka said:**
> With ndiswrapper wireless hangs even more often :(.
Switched back to ath5k for now.
I heard that the problem might actually be with wpasupplicant (the manager for the wpa authentication). Does everybody having problems with the wireless use wpa encryption (I do)? Could someone try to update wpasupplicant and see if this helps? I don't have time myself atm but I'll try in October...

good luck everyone...

---

### Post by lyovushka on 2009-09-10
> **thawn said:**
> I heard that the problem might actually be with wpasupplicant (the manager for the wpa authentication). Does everybody having problems with the wireless use wpa encryption (I do)? Could someone try to update wpasupplicant and see if this helps? I don't have time myself atm but I'll try in October...

good luck everyone...

Actually I have problems in connecting to wpa2, wep and unsecured networks so I don't think the problem lies in wpasupplicant. Actually there are several bug reports concerning this issue. See for example [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356768](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356768) .

The last 2 weeks the wireless hangs very often - it hardly works about 30 minutes. I think this is because I updated the kernel to 2.6.28-14. So I decided to further update the kernel and update to 2.6.28-15. Unfortunately, the ath5k driver doesn't work out of the box with that kernel. Currently trying 2.6.28-15 with 1.55 version of ndiswrapper with 7.7 windows driver. Will further post if any of my configurations will be working

---

### Post by Simon_H on 2009-09-13
There is a solution to the freeze problem with openchrome and gimp [1], and as it turns out, mplayer with video output xv (probably also for other players).

Put the following in you xorg.conf:
```
[FONT=monospace]
[/FONT]Option "AccelMethod" "exa"[FONT=monospace]
[/FONT]Option "EnableAGPDMA" "true"[FONT=monospace]
[/FONT]Option "MigrationHeuristic" "greedy"[FONT=monospace]
[/FONT]Option "ExaScratchSize" "8192"[FONT=monospace]
[/FONT]Option "ExaNoComposite" "true"

```For me, together with svn 784 the freezes are gone. Mplayer plays now a 1280x720 video (without fancy compression) with a cpu load of 70% (@ 1.7 GHz). For a x264 with litte motion at 75-80%.


Simon


Source 
[1] [http://bbs.archlinux.org/viewtopic.php?pid=607667#p607667](http://bbs.archlinux.org/viewtopic.php?pid=607667#p607667)

---

### Post by ttosca on 2009-09-13
I was wondering if anyone know whether future versions of Ubuntu (either Desktop or UNR) will support the Samsung NC20 out of the box.  

Does anyone have any information about this?  Have you heard of any work being done in this area?

Surely the NC20 is a fairly popular netbook, and therefore deserves a high priority in getting it working?

Thanks in advance.

---

### Post by pureblood on 2009-09-15
I am being unable to use the openchrome driver. The problem is that I cannot even debug it to know why. As soon as X starts, the system freezes. Anybody experiencing the same problem? I do not understand though, openchrome used to work fine. Now I have no clue what is going on.

---

### Post by 2345 on 2009-09-16
Hello is there any linux distro which i can install "out of the box" on my Samsung nc20? It doesn't have to be fancy, i just want a working version "Out of the box" without all this extra work to make the notebook run.

THANKS!

Im going to try out Fedora now
See install instructions here

[http://rootatlocalhost.bouldernet.org/index.php?option=com_content&view=article&id=6:samsung-nc20-and-linux-dual-boot&catid=1:articles&Itemid=2](http://rootatlocalhost.bouldernet.org/index.php?option=com_content&view=article&id=6:samsung-nc20-and-linux-dual-boot&catid=1:articles&Itemid=2)

[http://en.wikipedia.org/wiki/Fedora_(operating_system](http://en.wikipedia.org/wiki/Fedora_(operating_system))

---

### Post by tom09 on 2009-09-16
@pureblood: I just checked todays SVN of openchrome, it works for me. If your notebook is hooked up to a network try to login via ssh and look at the logfiles for kernel and Xorg. Check if all drm modules are unloaded.

@2345: [quote=2345]is there any linux distro which i can install "out of the box"[/quote]
Depends on your definition of "box"... Support for some of the NC20 hardware (card reader, Wifi RFKILL feature) was added quite recently to the kernel so you need a distribution with really recent packages. You could use some rolling-release-distro like Archlinux, but setting this up means a *lot* more work than installing Ubuntu and doing "the extra work". so I'm afraid the answer to your question is: No, not at the moment.

---

### Post by lyovushka on 2009-09-16
> **pureblood said:**
> I am being unable to use the openchrome driver. The problem is that I cannot even debug it to know why. As soon as X starts, the system freezes. Anybody experiencing the same problem? I do not understand though, openchrome used to work fine. Now I have no clue what is going on.

I had the same problem with the following line in my xorg.conf
        Option          "ActiveDevice" "LCD,CRT"
The problem was fixed by deleting it :)

---

### Post by 2345 on 2009-09-16
> **tom09 said:**
> so I'm afraid the answer to your question is: No, not at the moment.
Fedora is just what i wanted, thx.

---

### Post by Uli_of on 2009-09-17
Hello, I found that the change in svn 764 freezes my NC20 with Opensuse 2.6.31.
If you comment out the changes of svn 764 in via_mode.c and compile it works until the latest svn.
Regards

---

### Post by Uli_of on 2009-09-17
> **Uli_of said:**
> Hello, I found that the change in svn 764 freezes my NC20 with Opensuse 2.6.31.
If you comment out the changes of svn 764 in via_mode.c and compile it works until the latest svn.
Regards
 Sorry, forgot to say it is regarding the openchrome driver from svn.
Regards

---

### Post by pureblood on 2009-09-17
> **lyovushka said:**
> I had the same problem with the following line in my xorg.conf
        Option          "ActiveDevice" "LCD,CRT"
The problem was fixed by deleting it :)

Yep, that fixed it for me too. Why is that though? It did not use to be that way. I removed that line from the wiki. How do I get the external monitor to work now? Also, as soon as I try to play a video with mplayer the screen back-light turns off. Does anybody have the same problem? Does anybody know why?

---

### Post by thawn on 2009-09-18
> **pureblood said:**
>  I removed that line from the wiki. How do I get the external monitor to work now? Also, as soon as I try to play a video with mplayer the screen back-light turns off. Does anybody have the same problem? Does anybody know why?
Sounds like the lates svn version (764) is buggy. Has anybody posted a bug with the openchrome crowd?
you can check out an earlyer revision (which hopefully does not contain the bug) with this command:
```
svn checkout -r 763 http://svn.openchrome.org/svn/trunk openchrome
```
It is really important to post a bug, though. That way you can help to make the driver more stable! (I cannot do it myself since I am using the via driver).

---

### Post by Uli_of on 2009-09-18
> **thawn said:**
> Sounds like the lates svn version (764) is buggy. Has anybody posted a bug with the openchrome crowd?
you can check out an earlyer revision (which hopefully does not contain the bug) with this command:
```
svn checkout -r 763 http://svn.openchrome.org/svn/trunk openchrome
```
It is really important to post a bug, though. That way you can help to make the driver more stable! (I cannot do it myself since I am using the via driver).
 The latest svn is 787. If you comment out the change svn 764 it does work.
It seems to be a VX800 specific bug. It was adressed in the openchrome user list.
I am currently using openchrome or  via .
If I use via with gnome it works fine, if I use kde via crashes my X-server.
Anyone having the same expirience ?
Regards
Uli

---

### Post by pureblood on 2009-09-18
@Uli_of I assume that the "change" you are talking about is the one of commenting the recently added lines
>     /* Enable MMIO & PCI burst (1 wait state) */
    ViaSeqMask(hwp, 0x1A, 0x06, 0x06);
in the function
> void ViaModeFirstCRTC(ScrnInfoPtr pScrn, DisplayModePtr mode)
in the file via_mode.c which is line 1632 in the current svn 787 (but which could probably change any time).

I have commented it and I am giving it a try right now.

---

### Post by Uli_of on 2009-09-18
Openchrome svn 790 is out.
Resolves freezing with Samsung NC20
Regards

---

### Post by pureblood on 2009-09-18
Well, svn790 solves the freezing because that line has been removed, I believe in svn788. Although, I am still unable to use the external screen. Any insights in that?

---

### Post by pureblood on 2009-09-21
Everyone, openchrome svn 791 is out, and it fixes the issues with the backlight, so, if you have that problem, I highly suggest to update to the latest version.

---

### Post by embeee on 2009-10-10
Thanks for a great and very helpful thread!

I recently bought a Samsung NC20 and loving it, but unfortunately I'm having a lot of problems with my wireless connection.

After I boot up Ubuntu the wireless works fine but then suddenly just dies after 5-30 minutes. The connection is completely lost and if I run ifdown wlan0 followed by ifup wlan0 it just says that the interface doesn't exist or isn't configured. It always comes back again if I reboot, but I would really like a better solution...

I've tried reloading and disabling various modules (ath5k, ath9k, ath_pci, ath_hal etc.) as well as restarting the network scripts in /etc/init.d but nothing helps. I also tried the backport and madwifi drivers with the same result.

I'm running Jaunty 9.04 and haven't done any major system changes other than the automatic updates which Ubuntu did automatically shortly after the installation. I've tried both the 2.6.28-11 and 2.6.28-15 kernels that are available in GRUB, but there's no difference.

It's the same problem at home and at school, and the wireless always works fine in Windows (which is really annoying), so the problem isn't hardware-related.

Has anyone had a similar problem or know how to fix it? I really don't want to be stuck with Windows. :(

/ Markus

---

### Post by tvijlbrief on 2009-10-13
> **embeee said:**
> Thanks for a great and very helpful thread!

I recently bought a Samsung NC20 and loving it, but unfortunately I'm having a lot of problems with my wireless connection.

After I boot up Ubuntu the wireless works fine but then suddenly just dies after 5-30 minutes. The connection is completely lost and if I run ifdown wlan0 followed by ifup wlan0 it just says that the interface doesn't exist or isn't configured. It always comes back again if I reboot, but I would really like a better solution...

I've tried reloading and disabling various modules (ath5k, ath9k, ath_pci, ath_hal etc.) as well as restarting the network scripts in /etc/init.d but nothing helps. I also tried the backport and madwifi drivers with the same result.

I'm running Jaunty 9.04 and haven't done any major system changes other than the automatic updates which Ubuntu did automatically shortly after the installation. I've tried both the 2.6.28-11 and 2.6.28-15 kernels that are available in GRUB, but there's no difference.

It's the same problem at home and at school, and the wireless always works fine in Windows (which is really annoying), so the problem isn't hardware-related.

Has anyone had a similar problem or know how to fix it? I really don't want to be stuck with Windows. :(

/ Markus

I installed the 9.10beta which seems to fix this issue, but you'll have to install a new videodriver because the one in 9.10beta has problems.

The best thing to do is just wait about two weeks till 9.10 is out or you could try installing just the wifi drivers from 9.10beta.

9.10 looks to work really good on the nc20.

See [https://bugs.launchpad.net/bugs/374090](https://bugs.launchpad.net/bugs/374090) for details if you want to install 9.10beta and compile the video driver.

---

### Post by embeee on 2009-10-13
> **tvijlbrief said:**
> I installed the 9.10beta which seems to fix this issue, but you'll have to install a new videodriver because the one in 9.10beta has problems.

The best thing to do is just wait about two weeks till 9.10 is out or you could try installing just the wifi drivers from 9.10beta.

9.10 looks to work really good on the nc20.

See [https://bugs.launchpad.net/bugs/374090](https://bugs.launchpad.net/bugs/374090) for details if you want to install 9.10beta and compile the video driver.

Thank you very much for your reply, that really does sound like a proper solution. I think I'll hold out until the official release and then do the upgrade.

Cheers!

---

### Post by Mal Bridgeman on 2009-10-13
> **tvijlbrief said:**
> I installed the 9.10beta which seems to fix this issue, but you'll have to install a new videodriver because the one in 9.10beta has problems.

The best thing to do is just wait about two weeks till 9.10 is out or you could try installing just the wifi drivers from 9.10beta.

9.10 looks to work really good on the nc20.

See [https://bugs.launchpad.net/bugs/374090](https://bugs.launchpad.net/bugs/374090) for details if you want to install 9.10beta and compile the video driver.
[COLOR=DarkRed]
Hiya

I am a bit of a noob (well, total Linux noob actually) but reasonably savvy pc wise.

I feel confident of following the instructions to download and compile the package .... but I am stumped at how to get to a point where I can start the process. 

If I install 9.04 netbook remix I get the fuzzy screen.
If I install 9.10 netbook remix beta I get flashing screens of different colours.

How do I get from that point to a terminal window where I can start the openchrome driver update, please?

Thanks in advance
Mal[/COLOR]

---

### Post by tvijlbrief on 2009-10-13
> **Mal Bridgeman said:**
> [COLOR=DarkRed]
Hiya

I am a bit of a noob (well, total Linux noob actually) but reasonably savvy pc wise.

I feel confident of following the instructions to download and compile the package .... but I am stumped at how to get to a point where I can start the process. 

If I install 9.04 netbook remix I get the fuzzy screen.
If I install 9.10 netbook remix beta I get flashing screens of different colours.

How do I get from that point to a terminal window where I can start the openchrome driver update, please?

Thanks in advance
Mal[/COLOR]

For some reason the F4 safe mode key from the live USB stick does not work. The way to get started without a flashing X display is hitting the F6 key and than ESC which leaves you with an editable boot options line.

Remove the "quiet splash --" at the end (this is optional but you'll see what is happening under the hood) and replace "only-ubiquity" with "single" and hit enter.

After a while you'll get the rescue menu options, you can choose netroot for a shell with networking...

I think wireless will not work in this early mode, so you should attach an UTP cable.

---

### Post by embeee on 2009-10-13
> **Mal Bridgeman said:**
> [COLOR=DarkRed]
Hiya

I am a bit of a noob (well, total Linux noob actually) but reasonably savvy pc wise.

I feel confident of following the instructions to download and compile the package .... but I am stumped at how to get to a point where I can start the process. 

If I install 9.04 netbook remix I get the fuzzy screen.
If I install 9.10 netbook remix beta I get flashing screens of different colours.

How do I get from that point to a terminal window where I can start the openchrome driver update, please?

Thanks in advance
Mal[/COLOR]

Ctrl+Alt+F1 should do the trick.

---

### Post by tvijlbrief on 2009-10-13
> **embeee said:**
> Ctrl+Alt+F1 should do the trick.

Normally it does, but that did not work for me in 9.10beta...

---

### Post by Mal Bridgeman on 2009-10-14
> **tvijlbrief said:**
> For some reason the F4 safe mode key from the live USB stick does not work. The way to get started without a flashing X display is hitting the F6 key and than ESC which leaves you with an editable boot options line.

Remove the "quiet splash --" at the end (this is optional but you'll see what is happening under the hood) and replace "only-ubiquity" with "single" and hit enter.

After a while you'll get the rescue menu options, you can choose netroot for a shell with networking...

I think wireless will not work in this early mode, so you should attach an UTP cable.

[COLOR=DarkRed]Firstly - thanks for the insight into how to break into the install.

I get the line you refer to but not the ubiquity piece ... so I just replaced the quiet splash -- bit with the word single

[COLOR=Black]     sudo apt-get install build-essential subversion autoconf automake1.9 libtool[/COLOR]

Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

So I went for the [COLOR=Black]apt-get update[/COLOR] option

then I did the next step

[COLOR=Black]  sudo apt-get build-dep xserver-xorg-video-openchrome[/COLOR]

which seemed to go ok

When I do the next step 

[COLOR=Black]  svn checkout [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk) openchrome[/COLOR]

I get an error [COLOR=Black]The program 'svn' is not currently installed. You can install it by typing:  apt-get install subversion[/COLOR]

so that's what I did. It ran ok so I redid the svn checkout step again and got a msg at the end about revision 811.

So I moved through the next steps with no problem

[COLOR=Black]  cd openchrome
  ./autogen.sh --prefix=/usr
  make
  sudo make install[/COLOR]

then edit and save the xorg.conf file ok

When I type the command 
[COLOR=Black]  sudo /etc/init.d/gdm restart[/COLOR]
to restart GDM, I get a message 
[COLOR=Black]Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm restart.

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the restart(8) utility, e.g. restart gdm
restart: Unknown instance:[/COLOR]

so I type

[COLOR=Black]service gdm restart[/COLOR]

and get the message 
[COLOR=Black]restart: Unknown instance:[/COLOR]

so I try[COLOR=Black] restart gdm[/COLOR] with the same result

Thinking I have messed up I go through the whole process again and of course, end up with the same result.

In frustration, I type [COLOR=Black]GDM[/COLOR] and the desktop starts ...... and I am able to complete the installation through the UBUNTU GUI!!!

It is very slow and clunky though and I am kind of wondering why I bothered now .... have I missed a performance tweak somewhere, perhaps?

..any ideas what I have missed or done wrong would be gratefully received. (I chose a 2gb swap file and a 23Gb area for the system ... is that enough perhaps?)

TIA
Mal[/COLOR]

---

### Post by Susp on 2009-10-14
Hey there. Let's see if I've found a *new* ultimate solution for all the NC20 owners.

[CENTER][FONT=System][SIZE=3][COLOR=Red]PAY ATTENTION: This is a highly experimental driver which may not work at all or may be unstable but in case you are lucky to setup everything properly you will have a decent speed (for such a graphic board) on kernels up to 2.6.30. Below comes the original message posted, nothing was edited, however you may want to check the file names due to recent changes.
[/COLOR][/SIZE][/FONT][/CENTER]
 
Well, as a preamble I'd love to say I've managed to grab an experimental driver for Chrome9 graphics directly from the developer. You won't find this one neither on [http://linux.via.com.tw](http://linux.via.com.tw) website, nor on the net.

Well, well. Just to get you in. That is an official driver for Chrome9 HC3 graphics in Linux, the driver is produced by Via tech., it is libre and completely legal. The driver is meant for Ubuntu Jaunty, but it is called
something experimental. Now lets get the good news. I've managed to successfully install and run it on my Lenovo S12, loaded with Jaunty.

For those of you, who haven't heard of this laptop before, I'd say it features Via Nano CPU, Via VX800 chipset, Chrome9 HC3 graphics. Sounds familiar, huh? That's it. The NC20 of yours is based on exactly
the same hardware, so you may use this guide.

Well, let's see. The driver I'm introducing is versioned 86a-50937,
so its version tag is higher than the one available at the official site.
But as I've said this one is experimental so you will have to trick around a bit.
I think it is a good price for having, ehm... All the stuff *I've personally managed to do* with this driver:


[LIST]
[*]       * Installs and starts on Ubuntu Jaunty with updates
[/LIST]

[LIST]
[*]   * Allows setting the required resolution
[/LIST]

[LIST]
[*]       * Allows plugging an external display
[/LIST]

[LIST]
[*]       * Accelerates 2D with XAA and EXA, depending on your choice
[/LIST]

[LIST]
[*]       * Accelerates Xvideo. This means that you will have a much smoother movies, decent 720p.
[/LIST]

[LIST]
[*]       * Accelerates 3D and openGL. Currently I'm gaming Quake Live full-screen. Brilliant!
[/LIST]

[LIST]
[*]       * Stated to accelerate Compiz, but I don't need it so I haven't tested it. Hope you do.
[/LIST]

[LIST]
[*]       * Works something like pretty stable
[/LIST]
 
Let's get set.
What you gonna need is the driver package itself, I'll put the links to grab it in the end of the message, also check the attachments.
Once you have the driver, I'm chatting about, it is time to unpack it and get to work.
**Important notice**: You are strongly recommended to switch off X and gdm, while you're installing.


[LIST]
[*]  * Prerequisite: switch off X server
[/LIST]

[LIST]
[*]  * Prerequisite: disable GDM (Not sure about KDM), while you are working:
[/LIST]
 
    ```
sudo /etc/init.d/gdm stop
```When you are all set you should be inside the console. I assume you get the shell basics, but I'll try to make things clear.


[LIST]
[*]       * You will have to unpack the driver you got.
[/LIST]

[LIST]
[*]       * Move it to some place as if it is your lab
[/LIST]
 
    ```
sudo mkdir /tmp/tempvia
    mv ./574-u904-f.tgz /tmp/tempvia
    cd /tmp/tempvia
    tar -xf ./574-u904-f.tgz
```
[LIST]
[*]* This will make a temporary place for tricking with the driver, move the file you've got there, unpack it, go there.
[/LIST]

[LIST]
[*]       * Now you should have all the required files in that place. You can get to install itself.
[/LIST]
**Important notice**: Install script will try to remove existing module via.ko. It is *required* in order to run. However, in
case this module is currently loaded, you may be unable to go through the installation smoothly, even in case you are
the root. To make sure everything installs clear, remove any existing Chrome9 graphic board drivers from your
system, both produced by Via, inc. and OpenChrome project. To ensure that module is not loaded when you
install the new driver, first perform

```
sudo rmmod via
```
```
sudo rmmod drm
```

**Important notice**: in case you are having errors on this step, claiming that the module doesn't exist in /proc/modules, please just ignore them, this means that the old modules are not loaded for some reason, so you can proceed normally.

Also note that you are strongly recommended not to install OpenChrome driver and Via, inc. drivers altogether. This is
sometimes reported to break both of them.

[LIST]
[*]       * Now simply run
[/LIST]
 
    ```
sudo ./vinstall
```
[LIST]
[*]* I've modified ./vinstall script in order to copy *all* the required files. See bundled readme for details
[/LIST]

[LIST]
[*]     * As asked, reboot and see if the new load works.
[/LIST]
 
Once you're in your desktop, congrats, looks like you're done. In order to test the whole stuff:

Open a terminal, perform
```
glxgears -info
```See if the spinning gears appear to be drawn correctly.
If you got errors, bring your error messages. See the terminal output as well.
Pay attention to the frame per se counter which appears in the terminal shortly.
Gears FPS value should be between 200 and 450, depending on Compiz etcetera.
Once you feel it is okay, try some games and HD videos.
**Important notice**: in case you are going to watch HD movies, I'll strongly recommend that you use mplayer as your media player. I'm not sure if the acceleration comes to players, such as xine and totem.
In case your output is still slow, try passing
```
vo=xv
```option to the mplayer config file. For more information on mplayer configuration please search forums.
Don't try to go for 1080i. Ashame, but you are unable to play such HD on this hardware. Basically it is technical hardware limitations so you can't do anything about it. Go for 720p movies. I've found them very smooth and cool-looking on this glossy screen. Well at least you are unable to go 720p with OpenChrome. Have fun.
**Important notice**: in case you see spinning gears okay, but 3D games lock your Ubuntu, I'd ask you to bring the output of:
```
dmesg | grep drm
```just before you launch the game, which causes problems.

Well, now when your patience is over, lets have some mirrors to grab the wanted archive from:

[CENTER][FONT=System][SIZE=3][COLOR=Red]PAY ATTENTION: Due to minor yet blocking misprints and mistakes in the scripts, the links below, pointing to the first edition of this driver are marked as unstable and unusable and you're strongly recommended to proceed to [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") in order to download updated and fixed files.[/COLOR][/SIZE][/FONT][FONT=System][SIZE=3][COLOR=Red] Do not use the links below please![/COLOR][/SIZE][/FONT]
[/CENTER]

**Download mirrors** (3.4Mb file):
[Mirror]("http://www9.zippyshare.com/v/63915701/file.html")
[Mirror]("http://upload.info/tu78c9t3t9xs/574-u904-f.tgz")

Good luck, have fun. Open for your questions.

---

### Post by Susp on 2009-10-14
Ehm, just in case I've messed up the installation script, here it is the default one (Attachment). Note that it won't install everything required, so you'll have to do it youself. Untar the attachment, you will see the original ./vinstall script.

**For your information**:
Files required to run via driver:


[LIST=1]
[*]_via_chrome9.ko_ : kernel module
[/LIST]

[LIST]
[*]Path /lib/modules/`uname -r`/kernel/drivers/gpu/drm/via/via_chrome9.ko
[/LIST]

[LIST=1]
[*]_via_drv.so_ : X driver
[/LIST]

[LIST]
[*]Path /usr/lib/xorg/modules/drivers/via_drv.so
[/LIST]

[LIST=1]
[*]_libGL.so.2.via_chrome9_ : 3D driver
[/LIST]

[LIST]
[*]Path /usr/lib/libGL.so.2.via_chrome9 (**May vary!** Depends on your configuration and requires additional symlinks of libGL.so)
[/LIST]

---

### Post by tvijlbrief on 2009-10-15
> **Mal Bridgeman said:**
> [COLOR=DarkRed]
In frustration, I type [COLOR=Black]GDM[/COLOR] and the desktop starts ...... and I am able to complete the installation through the UBUNTU GUI!!!

It is very slow and clunky though and I am kind of wondering why I bothered now .... have I missed a performance tweak somewhere, perhaps?

..any ideas what I have missed or done wrong would be gratefully received. (I chose a 2gb swap file and a 23Gb area for the system ... is that enough perhaps?)

TIA
Mal[/COLOR]

Hi Mal,

After installing the OpenChrome driver you better just reboot (type the command "reboot"), instead of running gdm.

Is it still slow after a normal boot? It should be quite fast, your swap and system dimensions are ok. Note that 3D is not accelerated, but 2D desktop and MPEG decoding (watching a DVD) should be accelerated if you use the xv output option for eg mplayer and it uses very little cpu.

---

### Post by Mal Bridgeman on 2009-10-15
> **tvijlbrief said:**
> Hi Mal,

After installing the OpenChrome driver you better just reboot (type the command "reboot"), instead of running gdm.

Is it still slow after a normal boot? It should be quite fast, your swap and system dimensions are ok. Note that 3D is not accelerated, but 2D desktop and MPEG decoding (watching a DVD) should be accelerated if you use the xv output option for eg mplayer and it uses very little cpu.
[COLOR=DarkRed]
The actual applications seem fine .... but navigating the interface and opening applications is just dreadfully slow. I have watched UTube videos of the interface which are near immediate .... my experience on the NC20 makes Vista look like a finely tuned OS :D

I previously had Fedora 11 on the m/c and it was sensationally quick.

I am not so sure why I want Ubuntu to work on the machine! I guess I started with Ubuntu on the desktop as a derivative of the RedHat I played with 10 years ago and have achieved some level of comfort with where things are.

The killer app for me is Remote Desktop and the Fedora version was not too good and kept loosing the cursor hence why I am sticking with Ubuntu for now.

I am going to try Xubuntu and see if it addresses the clunky interface.
Mal[/COLOR]

---

### Post by Mal Bridgeman on 2009-10-16
> **Mal Bridgeman said:**
> [COLOR=DarkRed]
I am going to try Xubuntu and see if it addresses the clunky interface.
Mal[/COLOR]

[COLOR=DarkRed]I know it's bad form to follow up your own posts ... but I tried to install Xubuntu and got the same error symptoms as when first installing Ubuntu.

So I tried to download and compile the openchrome driver but it ran out of space and errored badly....

I am now thinking it must be possible to compile the driver and conf file using an ubuntu install then cut that into the Xubuntu build but have no idea what I'd need to copy from where or to where ....any thoughts that could help me here?

Thanks
Mal[/COLOR]

---

### Post by Susp on 2009-10-16
I'd also kindly ask those who tried the way, described [here]("http://ubuntuforums.org/showpost.php?p=8103495&postcount=244") to tell me your experience, whether you have succeeded or not.

---

### Post by Mal Bridgeman on 2009-10-16
[COLOR=DarkRed]I have figured out my problem ... I switched from the UNR special Desktop (System>Preferences>Switch Desktop Mode) and chose Classic Desktop and it's now great ... a familiar and quick interface!!
Thanks for the help getting me this far.
Mal[/COLOR]

---

### Post by meso uug on 2009-10-19
> I'd also kindly ask those who tried the way, described here to tell me your experience, whether you have succeeded or not.

1. Sorry for my English.
2. This way is great.
3. Some problem's were present with xorg.conf. I've edited xorg.conf, now it works!
4. Compiz works and works good, but sometime's X hangs...

---

### Post by Susp on 2009-10-19
> **meso uug said:**
> 
4. Compiz works and works good, but sometime's X hangs...

[CENTER][FONT=System][SIZE=3][COLOR=YellowGreen][COLOR=Blue]Changes described below are incorporated in the updated and fixed 574-u904-n package, see [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") for details. Information below is now considered outdated. Below comes the original text:[/COLOR][/COLOR][/SIZE][/FONT]
[/CENTER]
 
Nice to see it works at least. Even though I've told that the driver is still experimental, I have an idea you may use along with your Compiz.

I've found _some recommendations_ regarding to hardware acceleration.
It is said that _switching to EXA acceleration on this card fixes problems_ with the GIMP.
Could it be that it will also help your Compiz? Why not to try?
The advice is to add the following to the **"Device" section** of xorg.conf:

```

Option "AccelMethod" "EXA"
Option      "ExaNoComposite" "True"
Option      "MigrationHeuristic" "greedy"
Option      "ExaScratchSize" "8192"

```And also you may try adding this to xorg.conf:

```

Section "Extensions"
Option "Composite" "enable"
EndSection

```Please check if your sections are not being repeated.
I hope that works. I dont experience X hangs with this drivers usually, probably because of neither using Fusion nor Emerald.
Good luck.

---

### Post by Ant. on 2009-10-21
First of all a big thanks to everyone who has contributed to this thread and the [NC20 Ubuntu Documentation]("https://help.ubuntu.com/community/NC20"), both have been extremely useful to me since I got my NC20.

So far I have installed Jaunty off USB, installed the openchrome driver following the instructions in the documentation and run system update. Despite only having 2D graphics support and being a bit unresponsive at times I'm really happy that I'm finally back on Ubuntu, using XP for a couple of months drove me insane. 

For me the main hurdle is to get full graphics functionality on this laptop, then I'll worry about the other minor things (FN keys, brightness adjust, frequency scaling, etc) which I'll deal with after.

I have tried the method posted by Susp in post [#244]("http://ubuntuforums.org/showpost.php?p=8103495&postcount=244") but have had some problems along the way. 

The first thing that happened (which I'm not sure whether its a problem or not) is when I followed the step about disabling graphics modules:
```
sudo rmmod via
```& 
```
sudo rmmod drm
```I get the messages:
```
ERROR: Module via does not exist in /proc/modules
``````
ERROR: Module drm does not exist in /proc/modules
```Susp also mentioned about removing any existing Chrome9 graphics drivers (via & openchrome) from the system, how do I go about doing that at this step because I skipped it?

Then when I install the driver:
```
sudo ./vinstall
```I'm pretty sure something has gone wrong because inbetween bits of text that had "ok" next to it was this:
```
cannot stat '/lib/modules/2.6.28-15-generic/kernel/drivers/gpu/drm/via/via.ko' : No such file or directory
```Upon restart or gdm or reboot I just get console with no GUI and have to reinstall openchrome and use my old xorg.conf (from when I was using openchrome) again. I also tried the alternate install script posted by Susp in post [#245]("http://ubuntuforums.org/showpost.php?p=8103629&postcount=245") with the same results.

I'd appreciate any help or guidance with this, please bear in mind I'm still a beginner when it comes to Ubuntu, I know how to do a few things but on my previous laptop evertything worked out of the box and everything else I done was easy enough with google's help.

---

### Post by Susp on 2009-10-21
[CENTER][FONT=System][SIZE=3][COLOR=YellowGreen][COLOR=Blue]Changes described below are incorporated in the updated and fixed 574-u904-n package, see [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") for details. Information below is now considered outdated. Below comes the original text:[/COLOR][/COLOR][/SIZE][/FONT]
[/CENTER]

Hello, Ant.
Excuse me, but unfortunately I was unable to cover everything within the subject post. Lets say that what you have posted above means that you have neither "via" module nor the "drm" loaded. That is simply the reason. The idea is that instruction says you have to remove them manually, however you *already* don't have them loaded. So there is no reason to worry about this. However, the only thing I'm worried about is the fact that since you don't have a file named via.ko in your modules folder, at least as said in your warning message, the vinstall script is reasonably unable to remove it. That shouldn't be a problem at all but this may have a bad consequences. Look, when installation script comes up to a minor error like this one, it may stop proceeding at all, therefore you wont have the driver installed completely just because some stupid thing has happened at the very beginning. I'm almost sure the reason is something like this, so I'd love you to make one thing to test it in case you are ready for another try.

First of all, on concern of OpenChrome project driver removal:
Go to the folder where you have compiled the OpenChrome driver and run
```
sudo make uninstall
```This action will clear openchrome installed, allowing you to proceed.
**Important notice**: for obvious reasons you will be unable to use openchrome driver since this action is performed. However, you can always reinstall it using the manual you used to install it previously.

[COLOR=Blue](Please check attachments and post additions first, information below may not be required anymore)[/COLOR]

> There is one more thing I'd suggest.
Just before you will do
```
sudo ./vinstall
```try doing a simple trick. Lets create a dummy of via.ko file, which the script tries to remove.
```
sudo touch /lib/modules/2.6.28-15-generic/kernel/drivers/gpu/drm/via/via.ko
```this will create a dummy for vinstall script to remove and let it continue operating normally.Also, I've noticed a typo in your message. It says "kernal". I wonder if it is my typo in script or it is simply your misprint? This thing as of major importance so please tell me if you see something like this inside the script or output messages.[B]
Addition[/B]:
I've decided it will be better if I'll update the install script in order to perform such routines for you. Now it also should indicate the progress.
Please take the updated vinstall file from the attachment.
unpack the attachment using
```
tar -xf vinstall.tar
```and put the vinstall file instead of the one you have previously used.
Please report as soon as you try this.

---

### Post by pureblood on 2009-10-21
Susp, is it possible to install the 574-u904-f.tgz driver in Karmic Koala? Did you just get binaries for the modules to work with 2.6.28-15 or did you also get the sources? Because I would much rather use the driver with the new upcoming edition of Ubuntu rather than the old one.

---

### Post by Susp on 2009-10-22
> **pureblood said:**
> Susp, is it possible to install the 574-u904-f.tgz driver in Karmic Koala? Did you just get binaries for the modules to work with 2.6.28-15 or did you also get the sources? Because I would much rather use the driver with the new upcoming edition of Ubuntu rather than the old one.
[COLOR=Blue]
[/COLOR]**[FONT=Fixedsys][SIZE=3][COLOR=Blue]This information applies to all users who want Via 574-u904 driver on kernels different from the Jaunty default 2.6.28, this includes custom kernel users. This driver is reported to work with kernels up to 2.6.30.9. However, there are certain problems within the kernel 2.6.31, which is used in Karmic, so its users will have to stay with OpenChrome drivers currently.[/COLOR][/SIZE][/FONT]**

[CENTER][FONT=System][SIZE=3][COLOR=YellowGreen][COLOR=Blue]These sources are also available within the 574-u904-n package, see [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") for details. Note that some information here may relate to 574-u904-f, originally posted at [n244]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=244"), however it is currently considered unstable and broken. Similar warnings are multiplied all across my posts related to this driver.[/COLOR]
[/COLOR][/SIZE][/FONT][/CENTER]
 
Ehm. You cannot install this driver directly into 9.10 or anything what differs from 9.04. The reason is simple. This archive contains a *precompiled* kernel module, via_chrome9.ko. And it is already done for 2.6.28, which 9.04 uses. So you may know that inserting it into any other kernel, like 2.6.31, featured in 9.10, will simply give you an error. However, since Via, inc. kindly makes moves towards libre software and open source community, as of January 2009, DRM kernel module for chrome9 and unichrome boards is made public and open source. That is the reason you may want to compile it against your kernel and insert. The rest of the driver content should stay exactly the same as given in the subject package, also see the post [n245]("http://ubuntuforums.org/showpost.php?p=8103629&postcount=245") for the list of driver contents that matters. The only thing you have to build yourself is via_chrome9.ko, the rest should do the trick. So you may want to do the following:


[LIST]
[*]Acquire the subject 574-u904-f package from post [n244]("http://ubuntuforums.org/showpost.php?p=8103495&postcount=244")
[*]Acquire the DRM module sources, see the links at the end of this message
[*]You will need the following packages in order to build the module:
[LIST]
[*] autoconf
[*] automake
[*] autotools-dev
[*] diffstat
[*] libdrm-dev
[*] libgl1-mesa-dev
[*] libltdl-dev
[*] libpciaccess-dev
[*] libpixman-1-dev
[*] libpthread-stubs0
[*] libpthread-stubs0-dev
[*] libtool
[*] libx11-dev
[*] libxau-dev
[*] libxcb1-dev
[*] libxdmcp-dev
[*] libxext-dev
[*] libxv-dev
[*] libxvmc-dev
[*] libxvmc1
[*] mesa-common-dev
[*] libdrm-dev
[*] x11proto-core-dev
[*] x11proto-dri2-dev
[*] x11proto-gl-dev
[*] x11proto-randr-dev
[*] x11proto-render-dev
[*] x11proto-video-dev
[*] x11proto-xext-dev
[*] x11proto-xf86dri-dev
[*] xserver-xorg-dev
[*] xtrans-dev
[*] build-essential
[/LIST]
 
[*]Probably it is way too much of them to install one by one, so to install most of the stuff you can do:
[/LIST]
```
sudo apt-get build-dep xserver-xorg-video-openchrome
```and then
```
sudo aptitude install libdrm-dev
```
[LIST]
[*]This should be just enough
[*]Now you can build the DRM module source you have downloaded
[*]At first move it to some place, let it be:
[/LIST]
```

sudo mv ./574-drm-src.tar.gz /tmp/tempvia
cd /tmp/tempvia
sudo tar -xf ./574-drm-src.tar.gz
cd ./drmsource

```
[LIST]
[*]Now when you have unpacked the driver lets set up for install
[/LIST]
**Important notice**: in case you want this (for some reason) on kernels prior to
2.6.28-rc3, you have to open the file via_chrome9_drv.c with a text editor and
navigate to line number 38, you will see additional instructions there.
This fact is none of concern for users of 2.6.28, the one present in Jaunty and
users of newer kernels shouldn't bother as well.

[LIST]
[*]To build the driver:
[/LIST]
```
sudo make
```**Important notice**: you have to install this along with the rest of the driver, the order does really matter. So I'd suggest you to modify the vinstall script you have got with the driver from [n244]("http://ubuntuforums.org/showpost.php?p=8103495&postcount=244") or the essential vinstall script replacement from [n254]("http://ubuntuforums.org/showpost.php?p=8142221&postcount=254") in order *not* to copy via_chrome9.ko at all or not to try inserting it. You can show your creativity in this, probably you will find the following acceptable:

[LIST]
[*]Open the vinstall script in text editor, locate the following line there:
[/LIST]
```
modprobe via_chrome9
```
[LIST]
[*]remove it so the module won't be loaded during the installation and so you can then install the module you've compiled yourself.
[*]Run the vinstall script so that it installs everything but kernel module
[*]Now simply install the new module you have compiled yourself  using:
[/LIST]
 ```

cd /tmp/tempvia/drmsource
sudo make install

```This should be okay.
I haven't really tested this to work neither with Karmic, nor with vanilla kernel 2.6.31, and no way I've tested 2.6.32-rc5, but people say that they are not always successful in compiling DRM module against recent kernels. I'd ask you to post any error output for that reason.

To make you feel a bit more comfortable: two days ago I've made the whole stuff described above within half an hour while using custom kernel 2.6.30.9 with Jaunty. Everything works like a charm.

---

### Post by Exatic on 2009-10-22
Hello Susp. I've also tried your method but have gotten into some problems. 

When i try to install the vinstall file i get this "ERROR: MOdule via does not exist in /proc/modules", and when i reboot the system after the installation, gde won't start and i get stuck in the terminal. I also tried  your lastest vinstall file but it doesent output anything, so im not sure if its working. I would appericate all suggestion to my problem :)

---

### Post by pureblood on 2009-10-22
Susp, the kernel modules do not compile properly under kernel 2.6.31, since the function drm_alloc, drm_calloc, and drm_free are not declared anymore in the header file drmP.h. I tried to make the obvious modifications myself, got the driver compiled, installed libGL and the X driver.

But it was a monumental waste of time. The given xorg.conf file does not work (other than the fact that it is missing a line at the end). When X starts I see the screen cycling between black, green, and other colors, which reminds of a problem I had already noticed in the past. If I switch to console and then back to X, the system hangs. I tried my own xorg.conf file and I got at least X to start. But the desktop was far from responsive. I tried to change the settings from XRender to openGL but then the whole screen became white. On top of that, why does RandR need to be turned off? It is pretty annoying.

I am a bit confused, but what is the goal of the via drivers? They have more bugs than holes in a colander. I hope this to be related with the fact that what you are giving away is a beta driver. Also, if via wants to have open source drivers, why doesn't via adopt a release process with svn and forums like openchrome? Are they really trying to pursue something that works under linux or what?

---

### Post by meso uug on 2009-10-23
> **pureblood said:**
> Susp, the kernel modules do not compile properly under kernel 2.6.31, since the function drm_alloc, drm_calloc, and drm_free are not declared anymore in the header file drmP.h. I tried to make the obvious modifications myself, got the driver compiled, installed libGL and the X driver.

But it was a monumental waste of time. The given xorg.conf file does not work (other than the fact that it is missing a line at the end). When X starts I see the screen cycling between black, green, and other colors, which reminds of a problem I had already noticed in the past. If I switch to console and then back to X, the system hangs. I tried my own xorg.conf file and I got at least X to start. But the desktop was far from responsive. I tried to change the settings from XRender to openGL but then the whole screen became white. On top of that, why does RandR need to be turned off? It is pretty annoying.

I am a bit confused, but what is the goal of the via drivers? They have more bugs than holes in a colander. I hope this to be related with the fact that what you are giving away is a beta driver. Also, if via wants to have open source drivers, why doesn't via adopt a release process with svn and forums like openchrome? Are they really trying to pursue something that works under linux or what?

I had problem's like this.
Try to use my xorg.conf it shoud fix it:
```
Section "ServerLayout"
Identifier "ConfiguredLayout"
Option "RandR" "false"
EndSection

Section "Device"
        #BusID "PCI:00:01:0"
        #BusID "PCI:00:01:0"
        BusID "PCI:00:01:0"
Identifier "Card0"
Driver "via"
Option "ActiveDevice" "LCD,CRT"
#Option "PanelSize" "1280x800"
#Option "LCDPort" "LVDS0"
Option "AccelMethod" "EXA"
Option "ExaNoComposite" "True"
Option "MigrationHeuristic" "greedy"
Option "ExaScratchSize" "8192"
VendorName "VIA Technologies, Inc."
BoardName "VIA Chrome9 HC3 IGP"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
Depth 24
EndSubSection
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection


```

P.S. After last string must be empty string.

---

### Post by Susp on 2009-10-23
First of all, let me apologize for the inconveniences brought to you by that highly experimental stuff. But I insist on not blaming me directly for any software faults, because that wasn't actually I, who wrote the driver. :)
Please ask Via, inc. on concern of what actually is going on.
I'll retell you briefly. Recently I've discussed this driver with the developer and what have been exactly told is that they are currently not ready to release any Karmic driver. That is reasonable though, because we'll see the Karmic to fallout in a week. So this may not be a good idea to cry for the drivers beforehand. This should close issues concerning 9.10 and Kernels 31+.

Now let's get to the current. I've decided to put all the suggested fixes altogether and packed a driver with fixed scripts, updated xorg.conf (My apologies once again) and kernel module sources included for those who use Kernels 2.6.29 and 2.6.30.
The new driver package is named 574-u904-n.tar.gz just in order not to mess everything. I'll strongly recommend that you use it now since it contains fixes.

The installation instructions remain the same except you will have to check the file names. could be found at posts [n244]("http://ubuntuforums.org/showpost.php?p=8103495&postcount=244"), [n256]("http://ubuntuforums.org/showpost.php?p=8145144&postcount=256").

Package includes:

[LIST]
[*]Precompiled X driver (via_drv.so)
[*]Precompiled 3D parts (libGL.so)
[*]Precompiled kernel module (via_chrome9.ko) - Kernel 2.6.28
[*]Configured xorg.conf file
[*]Installation script (vinstall)
[*]Uninstallation script (vuninstall)
[*]Kernel module sources - Kernels 2.6.29, 2.6.30, any patchlevel
[/LIST]
Mirrors (3.5 Mb archive):
[Mirror - 574-u904-n]("http://www21.zippyshare.com/v/2940272/file.html")
[Mirror - 574-u904-n]("http://www.filedropper.com/574-u904-ntar")

---

### Post by Exatic on 2009-10-23
The last driver combined with meso uug's xorg.conf did the magic. Thank you very much!

EDIT: How do i get compiz to work?
Ive tried compiz from terminal and then start avant-window-manager but everytime ig et "Warning: Screen isnt composited. Please run compiz (-fusion) or another compositing manager"

---

### Post by Rainier Piqual on 2009-10-23
I just tried to install Xubuntu Karmic RC, but to no avail. I got the flashing screen, did the steps indicated above, but my lan would not connect to the internet, despite setting up /etc/network/interfaces etc.
As I am not willing to invest too much time, I think I'll have to wait until the graphic driver is fixed. Hopefully, this happens until next week's release, but I don't think it will.

Just to give you a short mission statement...keep up the good work!

---

### Post by Exatic on 2009-10-23
I've fially managed the compiz to work too (thanks to #compiz)!

Afer you have installed the driver simply run this command in a terminal:

mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by oscrp on 2009-10-23
Susp, did you asked him if they are going to publish a karmic 3d driver in a near future?. Hope they are not thinking on doing the same as on the jaunty release, no official driver from them...
BTW, I'm using your leaked-driver on an hp2133 (via c7-m+cn896) and it runs very good with compiz. The 720p videos lag a  bit but i think is more an issue of the weak power of the processor. Quake live also runs fairly good.. The only problem I had was with world of goo. I'm getting a black screen when I try to launch it. Can anyone test the demo or complete game to determinate that it isn't a hp2133-only issue? 
Thanks in advance!

---

### Post by Tobis87 on 2009-10-24
Susp, could you please ask the developers, how long I have to wait until amd64 precompiled modules and libraries are available!? 

It would also be nice if the new drivers are also back ported to older Ubuntu Versions, not everybody has the time to update their system every year.

I would need the X and 3D parts compiled against an amd64 intrepid ubuntu and the precompiled via_chrome9.ko compiled against 2.26.9.2 SMP PREEMPT x86_64.

Something like the Nvidia binary driver would be nice to see which does not care about which distribution you have.

---

### Post by Susp on 2009-10-24
I'm glad to see some of you guys have succeeded with this as did I. I'm not surprised this works with CN896 due to hardware similarity. Good news HP2133 runs this fine or something like this. On concern of World of Goo. I've already completed this game a long time ago so I simply don't have a reason to install it. However, I've tried the native Google Earth with this drivers. Due to its 3D functionality it utilizes OpenGL. However at first it behaved something like strange, giving graphical glitches. Accidentally I have found out that you have to disable fancy "Atmosphere" effects within Google Earth. This may help you when using this software. Also I guess it may be reasonable to disable high graphics settings within World of Goo (Not sure if it is possible). Try googling on concern of lowering the graphics quality in World of Goo. Please report in case you are good with this.
Now about my chitchat with the developer. As I've been pretty much of interested in Karmic support, I've asked about it and what have been told is "When it is done". Basically says nothing. However, something interesting on this concern has turned up today. Accidentally I saw some Linux news site to publish info that a new S3 Chrome driver for Linux was released today. As you may know, S3 has something to do with Via, inc. in graphic boards and the latest [release notes]("http://drivers.s3graphics.com/en/download/drivers/chrome5x-Linux/RN_Chrome5x_Linux_EN_26.htm") claim that it officially supports a number of recent distros and Ubuntu Karmic is among them. I'm sincerely hoping that Chrome9 from Via, inc. will shortly gain official Karmic support as well. We will have to wait for a while, I guess. No updates on this yet. I'll inform you as soon as anything interesting turns up. To conclude, currently you can't do the whole stuff with Karmic, however, one post from an anonymous user appeared and it looks something like worth looking at. Look at [this]("http://www.linux.org.ru/jump-message.jsp?msgid=4090641&cid=4148770"). It is in Russian language, so I'll give you a translation:

> I've patched the Kernel ( had to do some hard work, basically because of "drm_free" absence, I've replaced it with "kfree" and various stuff, it took me something like twenty minutes to do this. Works like a charm, I was happy to get 600 fps (*Translation note: I guess it is about glxgears*), but then I've upgraded X and the bad things had turned up - glxgears won't start anymore, so I've switched to OpenChrome, which works ( 120-160 fps ). It is okay (*Translation note: to my opinion it is not* ) . I'm using Samsung NC20. Here it is a kernel patch: [http://mirror.ls-home.org/distfiles/genpatches-2.6.31-4.lastrix.tar.bz2](http://mirror.ls-home.org/distfiles/genpatches-2.6.31-4.lastrix.tar.bz2)  But if you want 3D, you will have to stay at a previous version of X.org ( 1.5.3-r6 ). 

(*Translation note: in this case "old" is something special. Usual Ubuntu users shouldn't care about this*)


I'm not sure if you should use this because this solution includes patching the vanilla kernel which requires you to be pretty much of skilled and I cannot guarantee the stability of such a kernel. I won't test this anyway simply for the reason I do not want this. I'm okay with 2.6.30.9.

Just a few words about amd64: I wonder why would you need this? Do you know that gcc won't compile when Via Nano CPU runs in 64-bit mode? Currently it is so. No ideas what is the reason to use 64-Bit system on a consumer medium-low laptop.

---

### Post by Ant. on 2009-10-24
**@Susp** - Tried the method you outlined in post [_#254_]("http://ubuntuforums.org/showpost.php?p=8142221&postcount=254") but still couldn't get to a working desktop for some reason. I even tried formatting the HDD and resinatlling Ubuntu Jaunty again, but still encoutered the same problems. Also I did make a couple of typos in my post before mispelling kernel, that was a mistake of my own when posting, sorry for creating any confusion.

However since then I have managed to get the driver working following **Exatic**'s suggestion in post [_#261_]("http://ubuntuforums.org/showpost.php?p=8152894&postcount=261"), using 574-u904-n.tar.gz from post [_#260_]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") and **meso uug**'s xorg.conf from post #259, as the xorg.conf with 574-u904-n.tar.gz didn't work for me.

Thanks a lot for taking the time helping me and others with this driver, I really appreciate it. I am pleased with the driver as it seems to be so much faster and more responsive than openchrome, and with glxgears I was getting 380fps compared to 80-90fps with openchrome. 

But it seems as if the driver is stuck in 16bit colour, despite the defaultdepth and depth being set at 24 in meso uug's xorf.conf. I tried changing the value but that didn't seem to work either. And when I go to System > Preferences > Display I get an error message "Could not get screen information. RandR extension is not present." Anyway I can change this? I don't particularly like using 16bit colour :(

---

### Post by Susp on 2009-10-24
Ooow. That is really strange, Ant. You see, I had no idea at all to check the bit depth. I wonder if it really is 16 bit? Let's say I'm surprised. Because I run games and HD-movies normally, watch quality photos etcetera. I really had no idea on bit depth, because it seemed okay even on maximum brightness level enabled. You are making me something like anxious with this. I'm not sure about this, really. I'm really confused but I have no idea on how to test it (I'm using neither Gnome nor KDE) and despite all applications run and feel normally I'd prefer not to care about this currently. Lets see what brings us the updated driver, pointed at Karmic, I'd love to see improvements in it.
BTW: in case you need help on your built-in media card reader, cpu frequency scaling and so on, you're free to ask. I've gone through all of this and got all of these to work.

To all of those who have succeeded: you are welcome.

---

### Post by Tobis87 on 2009-10-25
> **Susp said:**
> Just a few words about amd64: I wonder why would you need this? Do you know that gcc won't compile when Via Nano CPU runs in 64-bit mode? Currently it is so. No ideas what is the reason to use 64-Bit system on a consumer medium-low laptop.

Which version of gcc does not compile in 64-bit mode? I use the standard gcc in intrepid amd64 on my samsung nc20 and even compiled a custom kernel. Or do you mean the via opensource 2D driver? If so, this is what I ask myself. How can they promote the via nano with amd64 support, when they drivers only support i386. The amd64 architecture is not that different.

I can only speculate that they don't have a amd64 version of the driver, because they think like you do, that there is no reason that a consumer wants to run a 64-bit linux on their machine.

This dictation of how I have to use a product, is one reason why I switched to linux.

Anyway, I want to take full advantage of the latest developments. I even recompiled openssl and patched it to support the padlock sha1 acceleration in amd64 mode. And because my other machines run on amd64, it is easier to exchange compiled debs like scummvm, because it would take ages to compile on the nc20.

Finally, you even get more security, by using the NX-Bit flag and more performence, because of the default usage of sse and sse2 registers.

**Edit:**
Maybe only gcc 4.3.x compiles on the Via Nano.

---

### Post by Susp on 2009-10-26
Hey, Tobis.
You see, fella, I understand your disappointment about 64 bit support. If only the whole stuff was okay, I'd probably switch, however... The idea was about gcc self-compilation, not an ordinary building. That's the idea. Probably, meaningless in case you are an Ubuntu user, though it may be reasonable to stay at i386 for Gentoo users for obvious reasons.
Basically I'll agree with you about freedom of usage... Even though Nano is a full-featured CPU, it includes ssse3 as far as I remember, I'd say you won't receive a performance boost. That is it. If only there were fine 64-bit drivers, I'd switch in a moment, guess you do the same. But it is not, sorry.

---

### Post by Uli_of on 2009-10-26
Hello all,
I, as a opensuse  and NC20 user, am very interested in this forum.

Not beeing able to get  the via drm  driver to compile with kernel 2.6.32 R5
any advice would be helpful. 
Can anyone explain to me the diffrence in performance
between the 32-bit and the 64-bit driver version in glxgears,
if there is some?
My glxgears with the 32-bit version and kernel 2.6.27 are ~ 420.
Regards
Uli

---

### Post by Susp on 2009-10-27
> Not beeing able to get  the via drm  driver to compile with kernel 2.6.32 R5
any advice would be helpful.

Hey, man, just forget this. It wont compile fine against 2.6.31 and I guess you will have the same stuff up there.
You will probably have to wait for Karmic driver to show up. All of us will probably have to.

By the way, an _update_ turned up.

The driver I've introduced a week ago or something is now available at the Via, inc. [website]("http://linux.via.com.tw")
Therefore the driver posted in [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") is not something special anymore, I guess it is reasonable to leave the manual there.

---

### Post by Tobis87 on 2009-10-27
> **Uli_of said:**
> Can anyone explain to me the diffrence in performance
between the 32-bit and the 64-bit driver version in glxgears,
if there is some?
My glxgears with the 32-bit version and kernel 2.6.27 are ~ 420.
Regards
Uli

Glxgears will not run in 64-bit mode, this is because there are no 3d-drivers out yet. Until there will be some, you will have to stick to 2d only driver called openchrome. And even this driver only runs on kernel < 2.6.30.

> **Susp said:**
> If only there were fine 64-bit drivers.

When I started to use the nc20 (2.6.29.2), there were almost none drivers for 64-bit mode. And I had to do a lot of patching, but now I think most of them have been merged in the kernel. Anyway I will attach them including my kernel config.

Everything works, except the viafb framebuffer driver and the via 3d driver. If you compile your kernel you will have to select padlock-aes, padlock-sha, e_powersaver (safe on the nc20) and the via-rng module.

How to use the openssl patches:
aes 64bit-support:
[http://ubuntuforums.org/showpost.php?p=7167334&postcount=43](http://ubuntuforums.org/showpost.php?p=7167334&postcount=43)
sha1 64bit-support:
[http://ubuntuforums.org/showpost.php?p=7186693&postcount=45](http://ubuntuforums.org/showpost.php?p=7186693&postcount=45)

I could not include these drivers, because they are to big, you will have to google for them:

Alsa-driver-1.0.20
openchrome

---

### Post by Susp on 2009-10-27
Cmon man, I am already using a custom kernel with Via HW RNG and Padlock incorporated. It is okay. Not sure about amd64 though. :)

---

### Post by tom09 on 2009-10-27
Hello all,

I've ported the drm kernel module to kernels 2.6.31 and above (didn't check with 2.6.32rc though). The archive contains the chrome9 module sources modified with some patches I found in this thread and on the dri-devel mailing list. It works on my NC20 (tested with: kernel 2.6.31.4, X.org 7.4, xorg-server 1.6.4, 32bit only) in combination with the new binary drivers for Ubuntu 9.04. Feel free to test it.

Regards, tom09

---

### Post by Rainier Piqual on 2009-10-27
> **tom09 said:**
> Hello all,

I've ported the drm kernel module to kernels 2.6.31 and above (didn't check with 2.6.32rc though). The archive contains the chrome9 module sources modified with some patches I found in this thread and on the dri-devel mailing list. It works on my NC20 (tested with: kernel 2.6.31.4, X.org 7.4, xorg-server 1.6.4, 32bit only) in combination with the new binary drivers for Ubuntu 9.04. Feel free to test it.

Regards, tom09

Is there a way to include this patch in the ubuntu iso? Or more generally asked, what options do I have to apply your patch?

Regards,
Rainier

---

### Post by moldy on 2009-10-27
Does anyone here know whether the new 9.10 will be installable "out of the box" or whether the methods described earlier in the thread will still be required?

Also, is anyone aware whether any of the fixes we've had to use have been included in the new release?

Moldy.

---

### Post by Uli_of on 2009-10-28
> **tom09 said:**
> Hello all,
 
I've ported the drm kernel module to kernels 2.6.31 and above (didn't check with 2.6.32rc though). The archive contains the chrome9 module sources modified with some patches I found in this thread and on the dri-devel mailing list. It works on my NC20 (tested with: kernel 2.6.31.4, X.org 7.4, xorg-server 1.6.4, 32bit only) in combination with the new binary drivers for Ubuntu 9.04. Feel free to test it.
 
Regards, tom09
Thank for your help.
I got it compiled with 2.6.32 R5.
Glxgears works, but googleearth freezes my system.
Anyone having the same experience ?
Regards
Uli

---

### Post by tom09 on 2009-10-28
> Glxgears works, but googleearth freezes my system.
Anyone having the same experience ?Googleearth works here, slow but usable. Did you try some other OpenGL apps (tuxracer, foobillard,...) beside glxgears?
What does dmesg say? Anything with [drm] in it may provide some clue...

---

### Post by Uli_of on 2009-10-28
> **tom09 said:**
> Googleearth works here, slow but usable. Did you try some other OpenGL apps (tuxracer, foobillard,...) beside glxgears?
What does dmesg say? Anything with [drm] in it may provide some clue...
Got it working. Compiled the via_chrome9 drm  modul.
Recompiled the GFX-betadriver from August 2009 for the via_drv.so, took the libGL.so.1.2.chrome9 and the via_via_chrome9_dri.so libraries from the new Oktober driver package.
All works  with kernel 2.6.32 R5 and 420 fps in glxgears.
Regards
:grin: Uli

---

### Post by ChrisUK on 2009-10-28
Hi all.

I don't often give up on things but after hours of trying to install Ubuntu Netbook Remix 9.10 onto my Samsung NC20 I'm on the verge of giving up.

Basically, here is what I have done so far.

I've downloaded the "karmic-netbook-remix-i386.iso" file from this location;
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

I then installed Unetbootin onto my Windows machine and followed the instructions to make the above .iso file into a bootable USB key.
It all worked successfully and I could see all the files on my USB flash drive.
Next I put the USB flash drive into my NC20, booted it up from the flash drive and I was prompted by UNetbootin to select one of the following options within 10 secs (Default, Help or OEM-install). I let the counter run and it automatically started to boot into Ubuntu.
It got passed the Ubuntu loading icon and then it displayed some loading text, then the screen goes a solid white/grey colour and it keeps changing colours from white, to red, to green, to blue, etc and I can hear the Ubuntu login sound in the background but the screen is just a solid colour constantly changing.
I made a video of it below to explain it better - if you have your sound on you'll hear the Ubuntu login sound.

[http://www.youtube.com/watch?v=FLxCUYSBan0](http://www.youtube.com/watch?v=FLxCUYSBan0)

Does anyone know why that is happening?
I've tried 3 different Ubuntu .iso files now and formatted my USB flash drive several times to FAT32. It's definitely not a corrupt download so I have no idea why this is happening!

Any help would be appreciated.

---

### Post by pureblood on 2009-10-29
tom09, I used your via_chrome9 code to compile the driver and I installed the X drivers from the via website ([http://linux.via.com.tw/](http://linux.via.com.tw/)). Although, I cannot get it to work properly. I think the xorg.conf from via is screwed up. To begin with, the server does not start because the LCD is enabled while the DVI should be enabled (I discovered this by trying, but I don't know why). Then X starts but the screen is all black. I tried to add the line 'Option "RandR" "false"' to the ServerLayout section of the xorg.conf and now the server starts but the resolution is 1024x768 instead of 1280x800 and I am not sure hot to fix that since with RandR disabled I cannot use xrandr to change the resolution. What a mess, again.

---

### Post by Tobis87 on 2009-10-29
ChrisUK, the problem is the framebuffer.
Do what I posted earlier:
[http://ubuntuforums.org/showpost.php?p=6972302&postcount=19](http://ubuntuforums.org/showpost.php?p=6972302&postcount=19)

But insead use the boot files for 9.10:
i386
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/)

amd64
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/)

---

### Post by tom09 on 2009-10-29
pureblood, these are the xorg.conf device and monitor sections I use:

```

Section "Monitor"
    Identifier    "CRT"
    HorizSync   31.5 - 64.3
    VertRefresh 50-70
EndSection

Section "Monitor"
    Identifier    "DVI"
    Option        "Ignore"    "true"
EndSection    

Section "Monitor"
    Identifier    "LCD"
    Option       "PanelSize"        "1280x800"
EndSection    

Section "Device"
    Identifier  "chrome"
    Driver      "via"
    BusID    "PCI:00:01:0"
    Option "SWCursor" "false"
#    Option "AccelMethod" "XAA"
    Option "AccelMethod" "EXA"
    Option "LCDPort" "LVDS0"
    Option "ExaNoComposite" "True"
    Option "MigrationHeuristic" "greedy"
    Option "ExaScratchSize" "8192"
    Option  "ActiveDevice"     "LCD"
    Option  "PanelSize"        "1280x800"
    VendorName  "VIA Technologies, Inc."
EndSection

```I think it is important to add a monitor section for LCD, CRT and DVI and to define a panel size. I had a similar problem with the NC20 but I cannot remember which setting actually solved it.
Regards, tom09

---

### Post by pureblood on 2009-10-29
Thanks tom09, I will try that when I get home. Although this brings me again to the same question. Why do via releases a driver which is supposed to contain a user guide which is missing and with an xorg.conf which clearly is not going to work on the laptop? How sloppier can they be?

---

### Post by Sackley85 on 2009-10-29
Hey everyone,

I am an admitted linux newbie... so bear with me. I'm absolutely sick of Microsoft and I really want to get 9.10 working on my nc20. I'm about to try the "windows installer", although I expect to get the screen issues, in which case I'll be back trying to decipher what the hell the solution to that is (as previously posted). I'm probably going to post some pretty basic questions, and apologize for such in advance, but any direction as to the answers will be much appreciated.

Scott

---

### Post by Tobis87 on 2009-10-29
Hi Sackley85,

I understand that this is not the easiest way to get started with linux. 

But the screen issue is caused by the buggy viafb framebuffer driver, which gets loaded on boot time. My solution to this is to tell linux on boot, that it shouldn't try to load any framebuffer driver.

My earlier post described a way how to install ubuntu alternate from a bootable usb stick. I had to do this the manual way, because there was no automatic usb creator application for the alternate version of ubuntu. Anyway you probably won't need the alternate installer.

To create the bootable usb stick, download UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) run it and select your prefered ubuntu version. After that open the file syslinux.cfg on the usb stick and append fb=off.```
default vmlinuz
append initrd=initrd.gz fb=off
```

---

### Post by abovo on 2009-10-29
> **Tobis87 said:**
> 
To create the bootable usb stick, download UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) run it and select your prefered ubuntu version. After that open the file syslinux.cfg on the usb stick and append fb=off.```
default vmlinuz
append initrd=initrd.gz fb=off
```

I created a USB stick on another 9.10 system - only one syslinux.cfg file is in the syslinux directory. Created the file in the root with your two lines and the menu changes to a live disk and then continues to the flashing colors again!  Added just the last line of yours to the syslinux.cfg (content below) file in the syslinux directory and I still get the cycling colors.

What did I not understand??

Thank you Vic

```
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
```

---

### Post by --dtk on 2009-10-29
Hey guys,

spent the last two days getting via's october binary to run on my HP Mini 2133. Kinda plotted the progress here[0]

Currently the new driver is being used, afaics:
```

(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 5.74.86
	Module class: X.Org Video Driver
(II) via driver subversion: V86a-50937
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 01@00:00:0

```

Rest of the config _seems_ to be ok
```

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX

(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2

(**) VIA(0): Using EXA acceleration architecture.
(==) VIA(0): EXA composite acceleration enabled.

(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0

(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0

(II) VIA(0): [drm] Detect H5s1 chipset: 0005  chipid: 3371
   ...
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
   ...
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [drm] drmAgpEnabled succeeded

(II) VIA(0): H5 3D Engine has been initilized.

(II) VIA(0): Enable EXA Now
(II) VIA(0): [EXA] Trying to enable EXA acceleration.
(II) VIA(0): [dri] frame buffer initialized done.
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): DPMS enabled
(II) VIA(0): [DRI] installation complete
(II) VIA(0): Map agp/pcie texture memory successfully and branch buffer will work for H6 chipset! 
(II) VIA(0): [dri] kernel data initilized.
(II) VIA(0): direct rendering enabled

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: Loaded and initialized /usr/lib/dri/via_chrome9_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

```


The only thing that's definitely b0rken is the viavideo module:
```

(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(==) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor

```

X does start, though. Seems to use another submodule :|

What gets me is the fact that I can only get software acceleration:
```

dtk@minibox:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_MESA_copy_sub_buffer, 
    GLX_SGI_make_current_read, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_SGIX_fbconfig
OpenGL vendor string: S3/VIA Graphics, Incorporated
OpenGL renderer string: S3/VIA Graphics Chrome9 HC IGP
OpenGL version string: 1.4 15.13.18.01
OpenGL extensions:
   ...

```


Maybe I'm getting something wrong, but the driver *should* enable the card's hardware acceleration, shouldn't it?

Right now I can't quite see what's the point if the driver neither gives me performance nor works with xrandr to give me vga out :/

Maybe someone enlighten me (in one way or another ;))

tia
dtk


__________
[0]http://ubuntuforums.org/showthread.php?t=1303965

---

### Post by Tobis87 on 2009-10-30
abovo,

I have not tested the latest version yet, do you have a menu if you start from the usb stick? If so press F6 (other options), ESC, append the fb=off and press ENTER.
```
(...) quiet splash fb=off
```

**Edit:**
Try this first, everything else would be speculation.

---

### Post by Rainier Piqual on 2009-10-30
> **Tobis87 said:**
> ChrisUK, the problem is the framebuffer.
Do what I posted earlier:
[http://ubuntuforums.org/showpost.php?p=6972302&postcount=19](http://ubuntuforums.org/showpost.php?p=6972302&postcount=19)

But insead use the boot files for 9.10:
i386
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/)

amd64
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/current/images/hd-media/)


Thank you Tobis, this worked fine for me. I successfully installed Xubuntu 9.10 :)

---

### Post by TITO_RU on 2009-10-30
Hi all. I have the problem with my Samsung NC20. As shown in this video [http://www.youtube.com/watch?v=FLxCUYSBan0](http://www.youtube.com/watch?v=FLxCUYSBan0). 
I installed video driver for this instrucction [http://ubuntuforums.org/showpost.php?p=8151398&postcount=260](http://ubuntuforums.org/showpost.php?p=8151398&postcount=260).
I use Ubuntu 9.04.
who may be can help me?

---

### Post by abovo on 2009-10-30
Hi Tobis87,

Tried as you suggested - press F6 (other options), ESC, append the fb=off and press ENTER - but it boots to a shell screen that is flashing all the text. This is more than screen problem as I can only type when the text is visible. Tried with safe graphics on and off...

This happens (Lang=English) for both Try and Install. 

It is the screen, but why your suggestion fails I have no clue, any new ideas?

Many thanks

Victor

---

### Post by pureblood on 2009-10-31
tom09, thanks for your help. With your patch ([http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424](http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424)), your xorg.conf, and the latest Xorg driver from via I finally got everything to work fine on my machine with the latest Ubuntu Karmic. I get about 340fps with glxgears and google earth seems to work as well. The desktop experience is much better now. I only get a weird message in the Xorg.0.log file:

(EE) VIA(0): DRM initjudge==1

and I have no clue what it means. Also, I cannot "Enable desktop effects" from the KDE's "System Settings", not sure for what reasons. Do you know if it is possible to use a second monitor with 1920x1200 resolution with the VX800 chipset?

---

### Post by tom09 on 2009-10-31
pureblood, glad to hear that it works. Ignore the "initjudge==1" error, it's harmless. I get this too when I switch to a text console and back to X. The driver seems to stop the 3D chip and checks if it is already initialized when going back to the X desktop. Don't know why the driver emits an error, though.
About the 2nd monitor: I already have used a projector connected to the VGA port as a secondary display, it has to be enabled via xrandr or the gnome screen properties. But I do not know whether theVX800 can do the 1920x1200. 
Make sure that you set the compositing type to XRENDER in KDE. If it still doesn't work, try disabling some effects (shadows, animations,..). I crashed the X server once playing with the desktop effects, but it works now. It is not blindingly fast, though.

---

### Post by tom09 on 2009-10-31
Sorry, I forgot this: Remove the "ExaNoComposite" line from xorg.conf, otherwise compositing does not work at all.

---

### Post by john363 on 2009-10-31
Hi,

I just put Jaunty on my nc20 and I'm trying out the new graphics drivers, I hear the login sound but just see the changing colours.

I'm using the 574-u904-n.tar.gz file but when i run the vinstall i noticed i get one error but the script still finishes. I cant figure out what I've missed:

```

./vinstall: line 70: [ : mv: binary operator expected

```
Thanks!

---

### Post by Sackley85 on 2009-10-31
> **Rainier Piqual said:**
> Thank you Tobis, this worked fine for me. I successfully installed Xubuntu 9.10 :)

I tried this also (ubuntu 9.10 though, not xubuntu) and just get an error:

Cannot find kernel: linux

Am I missing something?

---

### Post by azzert on 2009-10-31
Hello.
I've patched, installed drivers, reconfigured xorg.conf and still got black screen ( LCD turn off ) .  I dont have more ideas what to do .. maybe someone helps :)

Xorg:
> Section "ServerLayout"
    Identifier     "X.org Configured"
    option        "RandR" "false"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc/"
    FontPath     "/usr/share/fonts/X11/TTF/"
    FontPath     "/usr/share/fonts/X11/OTF"
    FontPath     "/usr/share/fonts/X11/Type1/"
    FontPath     "/usr/share/fonts/X11/100dpi/"
    FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Module"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "record"
    Load  "glx"
    Load  "xtrap"
    Load  "freetype"
EndSection

Section "Device"
    BusID "PCI:01:00:0"
    Identifier  "Card0"
    Driver      "via"
    VendorName  "VIA Technologies, Inc."
    Option      "ActiveDevice"      "LCD"
    Option        "AccelMethod"        "EXA"
    Option        "MigrationHeuristic" "greedy"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
	Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
      SubSection "Display"
        Depth      24
        Modes      "1280x800"
      EndSubSection
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

#Section "Extensions"
#    Option    "Composite"            "Enable"
#EndSection


and Xlog.0.log :
> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 30 01:49:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "RandR" "false"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] rev 1, Mem @ 0xa0000000/536870912, 0xc8000000/16777216
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "xtrap"
(WW) Warning, couldn't open module xtrap
(II) UnloadModule: "xtrap"
(EE) Failed to load module "xtrap" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 5.74.86
	Module class: X.Org Video Driver
(II) via driver subversion: V86a-50937
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(==) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 262144 kB
(II) VIA(0): VESA VBE OEM: VIA N3364

(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(**) VIA(0): Option "AccelMethod" "EXA"
(**) VIA(0): Option "ActiveDevice" "LCD"
(**) VIA(0): Option "LCDPort" "DFP_HIGH"
(**) VIA(0): Using EXA acceleration architecture.
(==) VIA(0): EXA composite acceleration enabled.
(II) VIA(0): MergedFB mode forced off.
(**) VIA(0): Active Device is LCD.
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VGA BIOS Version is = 9.0
(II) VIA(0): VGA BIOS Release Date Is: 2007/1/12
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  262144k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VIA(0): Manufacturer: LPL  Model: e600  Serial#: 0
(II) VIA(0): Year: 2006  Week: 0
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Digital Display Input
(II) VIA(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) VIA(0): Gamma: 2.20
(II) VIA(0): No DPMS capabilities specified
(II) VIA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) VIA(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) VIA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VIA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) VIA(0): Unknown vendor-specific block 0
(II) VIA(0):  LGPhilipsLCD
(II) VIA(0):  LP154WX4-TLA3
(II) VIA(0): EDID (in hex):
(II) VIA(0): 	b8054e0930293a20556e6b6e6f776e20
(II) VIA(0): 	76656e646f722d737065636966696320
(II) VIA(0): 	626c6f636b202568780a006420256920
(II) VIA(0): 	765f626c390000000000000020564941
(II) VIA(0): 	2830293a20556e6b6e6f776e2076656e
(II) VIA(0): 	646f722d737065636966696320626c6f
(II) VIA(0): 	636b202568780a002020536519000000
(II) VIA(0): 	8011c1b78011c1b7342d544c4133003b
(II) VIA(0): EDID vendor "LPL", prod id 58880
(II) VIA(0): Printing DDC gathered Modelines:
(II) VIA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(--) VIA(0): Max Monitor H Size =  1280
(--) VIA(0): Max Monitor V Size =  800
(II) VIA(0): Monitor0: Using hsync value of 49.31 kHz
(II) VIA(0): Monitor0: Using vrefresh value of 59.91 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
	(..........................................................)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "480x640" (hsync out of range)
	(..........................................................)
(II) VIA(0): Not using default mode "2048x1536" (vertical timing out of range)
(II) VIA(0): Not using mode "1280x768" (no mode of this name)
(--) VIA(0): Virtual size is 1280x800 (pitch 1280)
(**) VIA(0):  Driver mode "1280x800": 71.0 MHz, 49.3 kHz, 59.9 Hz
(II) VIA(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(**) VIA(0): Display dimensions: (330, 210) mm
(**) VIA(0): DPI set to (98, 96)
(II) VIA(0): VIASetDisplayPath is Single
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): [drm] Detect H5s1 chipset: 0005  chipid: 3371
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) VIA(0): [drm] Using the DRM lock SAREA also for drawables.
(II) VIA(0): [drm] framebuffer handle = 0xa0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [drm] drmAgpEnabled succeeded
(II) VIA(0): [dri] use agp.
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] mmio Registers = 0x3355443200
(II) VIA(0): [dri] mmio maped.
(II) VIA(0): VIAModeInit
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): -----CRT TIMING-----
(II) VIA(0): IGA1 timing
HActive=640, HSyncStart=656, HSyncEnd=752, HTotal=800 
VActive=480, VSyncStart=490, VSyncEnd=492, VTotal=525
(II) VIA(0):  PixelClock=25175000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1328, HSyncEnd=1360, HTotal=1440 
VActive=800, VSyncStart=803, VSyncEnd=809, VTotal=823
(II) VIA(0):  PixelClock=71000000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): -----LCD TIMING-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1328, HSyncEnd=1360, HTotal=1440 
VActive=800, VSyncStart=803, VSyncEnd=809, VTotal=823
(II) VIA(0):  PixelClock=71000000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): into 3D initial...3Dinitial? 0
(II) VIA(0): H5 3D Engine has been initilized.
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) VIA(0): VIAInternalScreenInit
(**) VIA(0): Option "MigrationHeuristic" "greedy"
(II) EXA(0): Offscreen pixmap area of 12288000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) VIA(0): Enable EXA Now
(II) VIA(0): [EXA] Trying to enable EXA acceleration.
(II) VIA(0): [dri] frame buffer initialized done.
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): DPMS enabled
(II) VIA(0): [DRI] installation complete
(II) VIA(0): Map agp/pcie texture memory successfully and branch buffer will work for H6 chipset! 
(II) VIA(0): [dri] kernel data initilized.
(II) VIA(0): direct rendering enabled
(**) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: Loaded and initialized /usr/lib/dri/via_chrome9_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**) Video Bus: xkb_layout: "pl"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pl"
(**) AT Translated Set 2 keyboard: xkb_layout: "pl"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2+USB Mouse
(**) PS/2+USB Mouse: always reports core events
(**) PS/2+USB Mouse: Device: "/dev/input/event5"
(II) PS/2+USB Mouse: Found 3 mouse buttons
(II) PS/2+USB Mouse: Found x and y relative axes
(II) PS/2+USB Mouse: Configuring as mouse
(**) PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE)
(**) PS/2+USB Mouse: (accel) keeping acceleration scheme 1
(**) PS/2+USB Mouse: (accel) filter chain progression: 2.00
(**) PS/2+USB Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2+USB Mouse: (accel) set acceleration profile 0
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) VIA(0): Hqv0Saved.hqv_ctl:a678046e
(II) VIA(0): Hqv1Saved.hqv_ctl:0
(II) VIA(0): [drm] Cleaning up DMA ring-buffer.
(II) PS/2+USB Mouse: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) VIA(0): [drm] removed 1 reserved context for kernel
(II) VIA(0): [drm] unmapping 8192 bytes of SAREA 0xf7d46000 at 0xb7ee4000
(II) VIA(0): [drm] Closed DRM master.
(II) VIA(0): [drm] Freeing agp memory
(II) VIA(0): [drm] Releasing agp module
(II) VIA(0): VIACloseScreen
 ddxSigGiveUp: Closing log


Thanks for help :)

---

### Post by john363 on 2009-10-31
> **john363 said:**
> Hi,

I just put Jaunty on my nc20 and I'm trying out the new graphics drivers, I hear the login sound but just see the changing colours.

I'm using the 574-u904-n.tar.gz file but when i run the vinstall i noticed i get one error but the script still finishes. I cant figure out what I've missed:

```

./vinstall: line 70: [ : mv: binary operator expected

```Thanks!

Figured out it was just a problem with the xorg.conf. Changed to to be the exact same as meso ugg has in post 259.

Thanks Again!

---

### Post by Tobis87 on 2009-11-01
TITO_RU, I described a solution for the frambuffer issue on page 28, [B]the video shows the framebuffer (text console driver) not working,
the driver you installed is for Xorg (2D/3D driver).[/B]

abovo, please try it with the **alternate installer**. With this at least some managed to install ubuntu 9.10.

Sackley85, have you used **initrd.gz and vmlinuz** from the **9.10** Ubuntu archive?

**ChrisUK and Rainier Piqual** seem to have managed to install Ubuntu 9.10, I have not even tried it. So I am not a great help here, try to contact them or open up a new thread.

---

### Post by Rainier Piqual on 2009-11-02
> **Sackley85 said:**
> I tried this also (ubuntu 9.10 though, not xubuntu) and just get an error:

Cannot find kernel: linux

Am I missing something?

Did you use the alternate Installer? This is what I did wrong first.

---

### Post by Sackley85 on 2009-11-02
> **Rainier Piqual said:**
> Did you use the alternate Installer? This is what I did wrong first.

Yep, just tried it with the alternate (Ubuntu, not xubuntu) and it still went to the changing colors/gray scales.... hmm.

---

### Post by 0d3 on 2009-11-03
I just got 9.10 installed with openchrome without any big problems.

Here's how you do it:
1. download [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) for Windows
2. use a USB stick of 1Gb or more (I used a 1Gb stick)
3. run LinuxLiveUSB, select to download Ubuntu 9.10
4. in LinuxLiveUSB deselect 'Enable launching LinuxLive in Windows'
5. select maximum persistant space (on a 1Gb stick about 300Mb)
6. create the bootable stick
7. plug an ethernet cable to you NC20 for network access
8. boot NC20 with the USB stick
9. the screen will cycle through colors - press CTRL-ALT-F1
10. follow 'Build from SVN' instructions from [http://help.ubuntu.com/community/NC20](http://help.ubuntu.com/community/NC20)
11. when you get to the desktop you can play with the system or install to the hard disk

---

### Post by lyovushka on 2009-11-03
> **0d3 said:**
> I just got 9.10 installed with openchrome without any big problems.

Here's how you do it:
1. download [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) for Windows
2. use a USB stick of 1Gb or more (I used a 1Gb stick)
3. run LinuxLiveUSB, select to download Ubuntu 9.10
4. in LinuxLiveUSB deselect 'Enable launching LinuxLive in Windows'
5. select maximum persistant space (on a 1Gb stick about 300Mb)
6. create the bootable stick
7. plug an ethernet cable to you NC20 for network access
8. boot NC20 with the USB stick
9. the screen will cycle through colors - press CTRL-ALT-F1
10. follow 'Build from SVN' instructions from [http://help.ubuntu.com/community/NC20](http://help.ubuntu.com/community/NC20)
11. when you get to the desktop you can play with the system or install to the hard disk

That did the job, thank you very much!!!

I managed to make skype work on 9.04, but that involved removing pulseaudio. The same trick works for 9.10, but the half of programs in 9.10 won't work :(. Currently looking on how to overcome this issue.

---

### Post by Sackley85 on 2009-11-03
Just tried that method with Xubuntu and still no luck! :confused:

Guess it's time for another method...

Edit: I guess I should specify the alternate installer/hd media/syslinux method is what still didn't work for me.

---

### Post by pureblood on 2009-11-04
Do you get wireless lock-ups which require reboot to have the wireless working again? I still get those with 2.6.31-4, with the usual dmesg output:

> 
ath5k phy0: failed to wakeup the MAC Chip
ath5k phy0: can't reset hardware (-5)


Does anybody have any insight on this? Is this:

[http://lkml.indiana.edu/hypermail/linux/kernel/0905.2/02453.html](http://lkml.indiana.edu/hypermail/linux/kernel/0905.2/02453.html)

the same exact problem?

---

### Post by Mal Bridgeman on 2009-11-04
> **ChrisUK said:**
> Hi all.

I don't often give up on things but after hours of trying to install Ubuntu Netbook Remix 9.10 onto my Samsung NC20 I'm on the verge of giving up.

Basically, here is what I have done so far.

I've downloaded the "karmic-netbook-remix-i386.iso" file from this location;
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

I then installed Unetbootin onto my Windows machine and followed the instructions to make the above .iso file into a bootable USB key.
It all worked successfully and I could see all the files on my USB flash drive.
Next I put the USB flash drive into my NC20, booted it up from the flash drive and I was prompted by UNetbootin to select one of the following options within 10 secs (Default, Help or OEM-install). I let the counter run and it automatically started to boot into Ubuntu.
It got passed the Ubuntu loading icon and then it displayed some loading text, then the screen goes a solid white/grey colour and it keeps changing colours from white, to red, to green, to blue, etc and I can hear the Ubuntu login sound in the background but the screen is just a solid colour constantly changing.
I made a video of it below to explain it better - if you have your sound on you'll hear the Ubuntu login sound.

[http://www.youtube.com/watch?v=FLxCUYSBan0](http://www.youtube.com/watch?v=FLxCUYSBan0)

Does anyone know why that is happening?
I've tried 3 different Ubuntu .iso files now and formatted my USB flash drive several times to FAT32. It's definitely not a corrupt download so I have no idea why this is happening!

Any help would be appreciated.

[COLOR="DarkRed"]Chris - Did you figure this out in the end?

I am happily running the desktop version on my NC20.

The netbook remix will load but is so slow it defeats the object of the simple menu I think....hence why I just went for the Desktop version.

Both require a bit of fiddling in the install process but easily doable ... if you read back through this thread you will see I am a total noob and I managed it. When creating the USB stick I chose to reduce the "free file space" from 128Mb (default) to zero else it ran out of room on my 1GB USB stick.

My current view is it's worth the effort.

HTH
Mal[/COLOR]

---

### Post by bendabla on 2009-11-05
Hi,

With the help of this Forum I got it working aswell.
I basically used the same method as 0d3 but took the **official release** of openchrome, so after step

> 9. the screen will cycle through colors - press CTRL-ALT-F1I used a combination of [https://help.ubuntu.com/community/NC20#Build%20from%20SVN]("https://help.ubuntu.com/community/NC20#Build%20from%20SVN")
```

sudo apt-get install build-essential subversion autoconf automake1.9 libtool
sudo apt-get build-dep xserver-xorg-video-openchrome
```and the method described in the openchrome documentation.

```

wget http://www.openchrome.org/releases/xf86-video-openchrome-0.2.904.tar.gz
tar xvzf xf86-video-openchrome-0.2.904.tar.gz
cd xf86-video-openchrome-0.2.904
./configure --prefix=/usr
make
sudo make install
```I think I didn't even have to edit the xorg.conf...

---

### Post by luc765 on 2009-11-06
Hello,

As the new pilot 904 is published in the form of a package. deb, I describe but in french the procedure for karmic here:  

[http://users.skynet.be/linux-rixensart/samsung_nc20.html](http://users.skynet.be/linux-rixensart/samsung_nc20.html)

In summary :

- download the the 2 .deb packages here :
[https://launchpad.net/%7Exorg-edgers/+archive/drivers-only/+build/1307486](https://launchpad.net/%7Exorg-edgers/+archive/drivers-only/+build/1307486)
- put the packages on USB key
- install karmic with alternate version to avoid the graphic problems
- reboot the PC and Ctrl+Alt+F1 to open a terrminal and then :
- sudo mkdir /media/cle
- sudo mount -t ext4 /dev/sdb1 /media/cle ## ext4 depending of the key
- sudo dpkg -i /media/cle/.....via_0.2.904~svn814-0ubuntu0tormod_i386.deb
- sudo dpkg -i /media/cle/.....openchrome_0.2.904~svn814-0ubuntu0tormod_i386.deb
- Reboot and everything is OK 

Lucien

---

### Post by yoshiki2 on 2009-11-06
> **Susp said:**
> Hey there. Let's see if I've found a *new* ultimate solution for all the NC20 owners.

[CENTER][FONT=System][SIZE=3][COLOR=Red]PAY ATTENTION: This is a highly experimental driver which may not work at all or may be unstable but in case you are lucky to setup everything properly you will have a decent speed (for such a graphic board) on kernels up to 2.6.30. Below comes the original message posted, nothing was edited, however you may want to check the file names due to recent changes.
[/COLOR][/SIZE][/FONT][/CENTER]
 
Well, as a preamble I'd love to say I've managed to grab an experimental driver for Chrome9 graphics directly from the developer. You won't find this one neither on [http://linux.via.com.tw](http://linux.via.com.tw) website, nor on the net.

Well, well. Just to get you in. That is an official driver for Chrome9 HC3 graphics in Linux, the driver is produced by Via tech., it is libre and completely legal. The driver is meant for Ubuntu Jaunty, but it is called
something experimental. Now lets get the good news. I've managed to successfully install and run it on my Lenovo S12, loaded with Jaunty.

For those of you, who haven't heard of this laptop before, I'd say it features Via Nano CPU, Via VX800 chipset, Chrome9 HC3 graphics. Sounds familiar, huh? That's it. The NC20 of yours is based on exactly
the same hardware, so you may use this guide.

Well, let's see. The driver I'm introducing is versioned 86a-50937,
so its version tag is higher than the one available at the official site.
But as I've said this one is experimental so you will have to trick around a bit.
I think it is a good price for having, ehm... All the stuff *I've personally managed to do* with this driver:


[LIST]
[*]       * Installs and starts on Ubuntu Jaunty with updates
[/LIST]

[LIST]
[*]   * Allows setting the required resolution
[/LIST]

[LIST]
[*]       * Allows plugging an external display
[/LIST]

[LIST]
[*]       * Accelerates 2D with XAA and EXA, depending on your choice
[/LIST]

[LIST]
[*]       * Accelerates Xvideo. This means that you will have a much smoother movies, decent 720p.
[/LIST]

[LIST]
[*]       * Accelerates 3D and openGL. Currently I'm gaming Quake Live full-screen. Brilliant!
[/LIST]

[LIST]
[*]       * Stated to accelerate Compiz, but I don't need it so I haven't tested it. Hope you do.
[/LIST]

[LIST]
[*]       * Works something like pretty stable
[/LIST]
 
Let's get set.
What you gonna need is the driver package itself, I'll put the links to grab it in the end of the message, also check the attachments.
Once you have the driver, I'm chatting about, it is time to unpack it and get to work.
**Important notice**: You are strongly recommended to switch off X and gdm, while you're installing.


[LIST]
[*]  * Prerequisite: switch off X server
[/LIST]

[LIST]
[*]  * Prerequisite: disable GDM (Not sure about KDM), while you are working:
[/LIST]
 
    ```
sudo /etc/init.d/gdm stop
```When you are all set you should be inside the console. I assume you get the shell basics, but I'll try to make things clear.


[LIST]
[*]       * You will have to unpack the driver you got.
[/LIST]

[LIST]
[*]       * Move it to some place as if it is your lab
[/LIST]
 
    ```
sudo mkdir /tmp/tempvia
    mv ./574-u904-f.tgz /tmp/tempvia
    cd /tmp/tempvia
    tar -xf ./574-u904-f.tgz
```
[LIST]
[*]* This will make a temporary place for tricking with the driver, move the file you've got there, unpack it, go there.
[/LIST]

[LIST]
[*]       * Now you should have all the required files in that place. You can get to install itself.
[/LIST]
**Important notice**: Install script will try to remove existing module via.ko. It is *required* in order to run. However, in
case this module is currently loaded, you may be unable to go through the installation smoothly, even in case you are
the root. To make sure everything installs clear, remove any existing Chrome9 graphic board drivers from your
system, both produced by Via, inc. and OpenChrome project. To ensure that module is not loaded when you
install the new driver, first perform

```
sudo rmmod via
``````
sudo rmmod drm
```**Important notice**: in case you are having errors on this step, claiming that the module doesn't exist in /proc/modules, please just ignore them, this means that the old modules are not loaded for some reason, so you can proceed normally.

Also note that you are strongly recommended not to install OpenChrome driver and Via, inc. drivers altogether. This is
sometimes reported to break both of them.

[LIST]
[*]       * Now simply run
[/LIST]
 
    ```
sudo ./vinstall
```
[LIST]
[*]* I've modified ./vinstall script in order to copy *all* the required files. See bundled readme for details
[/LIST]

[LIST]
[*]     * As asked, reboot and see if the new load works.
[/LIST]
 
Once you're in your desktop, congrats, looks like you're done. In order to test the whole stuff:

Open a terminal, perform
```
glxgears -info
```See if the spinning gears appear to be drawn correctly.
If you got errors, bring your error messages. See the terminal output as well.
Pay attention to the frame per se counter which appears in the terminal shortly.
Gears FPS value should be between 200 and 450, depending on Compiz etcetera.
Once you feel it is okay, try some games and HD videos.
**Important notice**: in case you are going to watch HD movies, I'll strongly recommend that you use mplayer as your media player. I'm not sure if the acceleration comes to players, such as xine and totem.
In case your output is still slow, try passing
```
vo=xv
```option to the mplayer config file. For more information on mplayer configuration please search forums.
Don't try to go for 1080i. Ashame, but you are unable to play such HD on this hardware. Basically it is technical hardware limitations so you can't do anything about it. Go for 720p movies. I've found them very smooth and cool-looking on this glossy screen. Well at least you are unable to go 720p with OpenChrome. Have fun.
**Important notice**: in case you see spinning gears okay, but 3D games lock your Ubuntu, I'd ask you to bring the output of:
```
dmesg | grep drm
```just before you launch the game, which causes problems.

Well, now when your patience is over, lets have some mirrors to grab the wanted archive from:

[CENTER][FONT=System][SIZE=3][COLOR=Red]PAY ATTENTION: Due to minor yet blocking misprints and mistakes in the scripts, the links below, pointing to the first edition of this driver are marked as unstable and unusable and you're strongly recommended to proceed to [n260]("http://ubuntuforums.org/showpost.php?p=8151398&postcount=260") in order to download updated and fixed files.[/COLOR][/SIZE][/FONT][FONT=System][SIZE=3][COLOR=Red] Do not use the links below please![/COLOR][/SIZE][/FONT]
[/CENTER]

**Download mirrors** (3.4Mb file):
[Mirror]("http://www9.zippyshare.com/v/63915701/file.html")
[Mirror]("http://upload.info/tu78c9t3t9xs/574-u904-f.tgz")

Good luck, have fun. Open for your questions.
I own a lenovo s12 via nano edition. It's basically the same as Samsung nc20.
I've tried live cds 9.04 9.10. Even Wubi.. All I get is a Black Screen if I install ubuntu and load it. Any Idea how can I fix it.. thanks

---

### Post by Sackley85 on 2009-11-06
> **0d3 said:**
> I just got 9.10 installed with openchrome without any big problems.

Here's how you do it:
1. download [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) for Windows
2. use a USB stick of 1Gb or more (I used a 1Gb stick)
3. run LinuxLiveUSB, select to download Ubuntu 9.10
4. in LinuxLiveUSB deselect 'Enable launching LinuxLive in Windows'
5. select maximum persistant space (on a 1Gb stick about 300Mb)
6. create the bootable stick
7. plug an ethernet cable to you NC20 for network access
8. boot NC20 with the USB stick
9. the screen will cycle through colors - press CTRL-ALT-F1
10. follow 'Build from SVN' instructions from [http://help.ubuntu.com/community/NC20](http://help.ubuntu.com/community/NC20)
11. when you get to the desktop you can play with the system or install to the hard disk

Ok, so I tried this out. I got the live version working and it seemed great! So I installed and when I rebooted it went back to the changing colors.

Ok, no big deal. I got it working before so I'll just 'Build from SVN' again on the installed version.

Now everytime I enter the first command
```
sudo apt-get install build-essential subversion autoconf automake1.9 libtool
```

I get an error that build-essential is not available. 

??

---

### Post by abovo on 2009-11-07
Thank you [lyovushka]("http://ubuntuforums.org/member.php?u=863759") this worked for me, so I now have a working system, lets hope this is gets included in the next build.

---

### Post by luc765 on 2009-11-08
Hello Pureblood and/or tom09,

It seems that you succed installed Via drivers in ubuntu 9.10. I and I'm sure others will appraciate very muchif you could explain the procedure with some details.
I tried but without any success.
There is no problem with openchrome but really too slow

Thanh you in advance,

Lucien, a french speaking man

---

### Post by pureblood on 2009-11-08
Ok, you will have first to download the GFX driver for Ubuntu 9.04 for VX800 from the via website:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
Install the Xorg driver and the libGL libraries. I believe you should be able to do this with the vinstall program.
Then download the patch from tom09:
[http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424](http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424)
compile and copy the file via_chrome9.ko in the right place, that is
/lib/modules/`uname -r`/kernel/drivers/gpu/drm/via/
Make sure the kernel will not try to load the via_chrome9.ko from GFX tarball downloaded from the via website, since it is compiled for kernel 2.6.28-11.
Last step, replace your /etc/X11/xorg.conf file with something like the following one:

> 
Section "Monitor"                                                       
    Identifier    "CRT"                                                 
    HorizSync   31.5 - 64.3                                             
    VertRefresh 50-70                                                   
EndSection                                                              

Section "Monitor"
    Identifier    "DVI"
    Option        "Ignore"    "true"
EndSection

Section "Monitor"
    Identifier    "LCD"
    Option       "PanelSize"        "1280x800"
EndSection

Section "Device"
    Identifier  "chrome"
    Driver      "via"
    BusID    "PCI:00:01:0"
    Option "SWCursor" "false"
#    Option "AccelMethod" "XAA"
    Option "AccelMethod" "EXA"
    Option "LCDPort" "LVDS0"
#    Option "ExaNoComposite" "True"
    Option "MigrationHeuristic" "greedy"
    Option "ExaScratchSize" "8192"
    Option  "ActiveDevice"     "LCD"
    Option  "PanelSize"        "1280x800"
    VendorName  "VIA Technologies, Inc."
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Module"
        Load    "glx"
        Load    "dri"
        Load    "extmod"
EndSection

Section "DRI"
        Group 0
        Mode 0666
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection


You should now be able to restart X with the via driver (or just reboot). For some reasons, when kde starts, the screen starts showing a lot of garbage. If the same happens with you try to switch to the console with ctrl+alt+f1 and back to X with ctrl+alt+f7. You should now be able to use your laptop with dri acceleration. Although I warn you. Via drivers are nothing short of really bad and buggy drivers. It is very easy to crash the machine if you start using 3D applications, so I just don't. If openchrome supported dri, then I would not even think of using via's unreliable drivers.

I would have never bought this laptop if I knew about this but, sadly, there is no company selling 12 inches netbook with linux preinstalled, so I am not sure what other options there are out there.

---

### Post by luc765 on 2009-11-08
@pureblood

Manny thanks, i'm going to do that tomorrow and will inform you 

Thanks again

Lucien

;)

---

### Post by bilakispa on 2009-11-08
Hi! I have ubuntu 9.04 nbr (2.6.28-16) installed on a netbook and i have via CX700.
I've downloaded and installed the [package at n260](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8151398&postcount=260). It's working ok but when i run .mp4 or programs with opengl it freezes. Maybe i haven't 3d support. Here is my $glxgears -info:
> AllocateDmaBuffer fail
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  32
  Current serial number in output stream:  34

At Xorg.0.log there are two errors and couple of warnings:
> (EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(EE) VIA(0): Unknown EDID version 0

Can you help me?

---

### Post by Ant. on 2009-11-09
> **pureblood said:**
> 
I would have never bought this laptop if I knew about this but, sadly, there is no company selling 12 inches netbook with linux preinstalled, so I am not sure what other options there are out there.

Same with me, after reading reviews this seemed to be one of the best netbooks to buy but it fails in the Linux department due to the lack of support with the VIA hardware. Haven't installed Karmic yet, been messing around on Jaunty for a few weeks now, not very impressed with these graphics drivers, they are good but not perfect, had a few crashes and times when the laptop has locked up and been unresponsive. 

I'm actually considering selling this NC20 and getting a Samsung N510 or maybe a Dell 11z in the new year, both look good and should support Ubuntu or any distro a lot better than the NC20 does. Fortunately I got a really good deal on this NC20 so I should get at least 90% of what I paid back when I sell it. Maybe I'll do a fresh install of Karmic or reinstall Jaunty, not sure yet.

---

### Post by luc765 on 2009-11-09
OK Pureblood 

It works but as you said the the screen show a lot of garbage at the start very strange.
The result is better but it is not a miracle around 600 frames per 5 seconde. Is it the same with you ??

Lucien

---

### Post by Uli_of on 2009-11-10
> **luc765 said:**
> OK Pureblood 
 
It works but as you said the the screen show a lot of garbage at the start very strange.
The result is better but it is not a miracle around 600 frames per 5 seconde. Is it the same with you ??
 
Lucien
I got now the VIA driver with the August beta GFX driver and the modified drm driver working with kerne 2.6.31. 
Glxgears shows max. 420 fps.
Can I improve this or is this the maximum performance of the hardware ?
 Regards
Uli

---

### Post by thawn on 2009-11-10
I'm giving up. After one of the occasional crashes, I lost data on the filesystem (ext3). Fortunately I had backups and only lost 2 Days of work but this was the straw that broke the camels back. Going to sell the thing on ebay. I am NEVER buying via hardware again and I'm going to tell everyone who asks to stay away from their products. Good hardware requires good drivers and they are obviously not able to write proper drivers. Even their windows drivers are quite unstable and their linux support is unbelievable!

This is really a pity, because I think Samsung did a great job with this netbook: Long battery life, great display, just the right keyboard size and a good touchpad.

Maybe I'll try the N510. Seems to be just like the NC20 but with Intel processor and Nvidia Graphics - sounds great doesn't it?

Good luck to everyone!

---

### Post by lastrick on 2009-11-13
> **thawn said:**
> I'm giving up. After one of the occasional crashes, I lost data on the filesystem (ext3). Fortunately I had backups and only lost 2 Days of work but this was the straw that broke the camels back. Going to sell the thing on ebay. I am NEVER buying via hardware again and I'm going to tell everyone who asks to stay away from their products. Good hardware requires good drivers and they are obviously not able to write proper drivers. Even their windows drivers are quite unstable and their linux support is unbelievable!

This is really a pity, because I think Samsung did a great job with this netbook: Long battery life, great display, just the right keyboard size and a good touchpad.

Maybe I'll try the N510. Seems to be just like the NC20 but with Intel processor and Nvidia Graphics - sounds great doesn't it?

Good luck to everyone!

what have you done with your system? I cann't crash my anyhow... Dunno, what i doing wrong? ( i'm not using 3d, cos ADoM isn't use it %) )

Sorry for bad english.

---

### Post by thawn on 2009-11-14
> **lastrick said:**
> what have you done with your system? I cann't crash my anyhow... Dunno, what i doing wrong? ( i'm not using 3d, cos ADoM isn't use it %) )

Sorry for bad english.
I'm not using 3d either, but with high cpu load and especially with high i/o load (copying large files over the network) I and others in this forum get occasional system lockups.

---

### Post by mäki on 2009-11-14
Hello everyone. I got ubuntu working okay on my samsung nc20, i get 500fps / 5sek on glxgears and seems to be stable. 

I got one problem thou - Video playback. No mather what i try to watch it lags.. do anyone know what i should do?

Mplayer with X11 video output works, and stuff is watchable, but you cant watch fullscreen with X11... 

Any ideas?

---

### Post by bendabla on 2009-11-14
Thanks to this Forum I got the via driver working aswell :)

@luc765 I don't get any garbage at the beginning, but I remember getting some at first and then added
```
Option  "Ignore" "true" 
```
for the CRT in the xorg.conf  (don't know if that solved it but the rest is the same as pureblood's xorg.conf)

Some people previously mentioned having the problems with only 16 bit like colour display. I've got the same problem and couldn't find a solution. Did anyone?

---

### Post by ja2z on 2009-11-15
Ubuntu on Samsung NC20 running Windows XP 1GB RAM 160GB HD

I've tried to install 9.04 Jaunty Jackalope alongside Windows XP (need sketchup which won't work on my PC using WINE unfortunately).

All goes well until the main screen which then just rolls and breaks up so I can't get into a terminal or the system at all.

BUT I can run Ubuntu 9.04 in a Sun VirtualBox with no problems.
As the graphics card etc are the same for both systems what can be the problem?

NB I am a very NEWBIE so don't get too technical please.

Many thanks for your help.
John

---

### Post by pureblood on 2009-11-15
@ja2z the problem with the video is that Ubuntu Jaunty does not come with a working video driver for the VX800 chipset (and neither Karmic does). So you need to work on that. I rewrote parts of the wiki at this website:
[https://help.ubuntu.com/community/NC20/](https://help.ubuntu.com/community/NC20/)
to reflect what needs to be done with Ubuntu Karmic. My suggestion is to avoid Jaunty at this point, since everything that works for Jaunty works also for Karmic and you will have to fix many less nuances, while the nuances you won't be able to fix you wouldn't have been able to fix anyway. If you have problems with it, let me know.

---

### Post by pureblood on 2009-11-15
> I got one problem thou - Video playback. No mather what i try to watch it lags.. do anyone know what i should do?

I have got the same problem, not sure how to deal with it though.

---

### Post by Rainier Piqual on 2009-11-15
Did anyone try the new Mint RC1? Or doesn't this distro make any difference, as it is based upon Ubuntu?

---

### Post by luc765 on 2009-11-15
Hello Pureblood,

Many thanks for the update of your wiki but there is something wrong in the address to download the .deb packages. The correct address is :

[https://launchpad.net/~xorg-edgers/+archive/drivers-only/+build/1307486](https://launchpad.net/~xorg-edgers/+archive/drivers-only/+build/1307486) 

Lucien

---

### Post by lyovushka on 2009-11-16
> **thawn said:**
> I'm not using 3d either, but with high cpu load and especially with high i/o load (copying large files over the network) I and others in this forum get occasional system lockups.

This used to happen to me with 9.04 very often. The problem is not, at least, reproducible in Ubuntu 9.10. I think it might be because of incorrect cpu frequency scaling in 9.04 (it was up to 1.7 GHz, now it is up to 1.6 GHz)

---

### Post by mäki on 2009-11-16
> **pureblood said:**
> I have got the same problem, not sure how to deal with it though.

I got it working decently now. I removed mplayer ( with gui ), then downloaded the mplayer without gui, and it playback everything expect 720p+ ok. I even tried to download the gui and use it, same problem again, slow playback... i dont have a clue why? 

And i guess it would work fine playing 720p x264 if i could get CoreAVC work with mplayer. I found a pretty good guide, but since i dont have a serial and it wont work with the 30-days-trail (atleast thats what the guide told me).

Any1 tried MPlayer with CoreAVC on a NC20? Or any other experience of 720p+ playback on nc20?

---

### Post by yoshiki2 on 2009-11-17
What to do if I have openchrome drivers, but I want to change to via drivers. heard those allow 3d) thx
Ubuntu 9.10

---

### Post by pureblood on 2009-11-18
@yoshiki2 just follow the steps described on the wiki:
[https://help.ubuntu.com/community/NC20/](https://help.ubuntu.com/community/NC20/)
And if you have problems let me know.

---

### Post by Sackley85 on 2009-11-22
> **pureblood said:**
> @yoshiki2 just follow the steps described on the wiki:
[https://help.ubuntu.com/community/NC20/](https://help.ubuntu.com/community/NC20/)
And if you have problems let me know.

This feels like a dumb question, but....

Can I put the 2 .deb packages on the usb stick that the os is booting from?

I'm assuming no.

I don't understand why I can't get this to work. I get the liveusb version running with the build from svn, but I can't save the file it says to type up at the end of the process. When I ^O to write out and attempt to save to the default location/filename it gives an error that the location/file doesn't exist.

I'm a total noob so sorry for any ignorance.

Thanks

---

### Post by pureblood on 2009-11-22
> Can I put the 2 .deb packages on the usb stick that the os is booting from?

I'm assuming no.

Actually yes, you can. That is what I have done. I used unetbootin to install Ubuntu Karmic on a USB stick and then I copied the two deb files on the same USB stick. Why would that be not allowed?

---

### Post by Exatic on 2009-11-25
It looks like Karmic has support for a bunch of functions out of box. Right now I'm using Jaunty and its stable except frequently freezes where reboot is needed. I can't make the mic work either (for Skype usage). Should i upgrade? if it's not going to fix my problems, i would prefer not, because i have done a lot of configuration to make all this work.

---

### Post by Susp on 2009-11-25
Hello guys, I've updated the wiki pages with an easy manual on how to install the Via driver
instead of the openchrome in Karmic. It works well and doesn't require compiling and any sort of tricks.
Should be a real deal for newbies.
[Wiki pages]("https://help.ubuntu.com/community/NC20")

Find the "Proprietary graphics driver" there and then the "Easy way" heading.
The manual describes the things pretty clearly.

Addition: changes were made to the wiki page above and now it contains the essential system clean-up script as well. If you have failed the first time for some reason, I suggest you would try it again. Because actually what I did in order to test this was to use the instructions directly on Xubuntu 9.10 LiveUSB and everything worked just fine.

---

### Post by Rainier Piqual on 2009-11-26
> **Susp said:**
> Hello guys, I've updated the wiki pages with an easy manual on how to install the Via driver
instead of the openchrome in Karmic. It works well and doesn't require compiling and any sort of tricks.
Should be a real deal for newbies.
[Wiki pages]("https://help.ubuntu.com/community/NC20")

Find the "Proprietary graphics driver" there and then the "Easy way" heading.
The manual describes the things pretty clearly.

That did not work for me, Susp. I got the colour switching screen, so I went back to openchrome. Perhaps it's because I'm using Xubuntu. I appreciate your effort!

---

### Post by Susp on 2009-11-26
That is really strange, Rainier. I've tried it with Xubuntu 9.10 as well.
Did you got any errors or warnings when installing? What is your notebook model?
Probably you had Via drivers installed previously? If so, it is a good idea to remove them first.

I would also like somebody to try this with Live CD or Live USB.

---

### Post by Susp on 2009-11-26
That is really strange, Rainier.
I've tried it with Xubuntu 9.10 as well. And it works like a charm.
Did you got any errors or warnings when installing?
What is your notebook model?
Probably you had Via drivers installed previously?
If so, it is a good idea to remove them first.

I would also like somebody to try this with Live CD or Live USB.

---

### Post by cuttersblade on 2009-11-26
I cant get this to work either, im trying on a fresh ubuntu 9.10 install and still get the coloured test screens. Any ideas?

---

### Post by Susp on 2009-11-26
Would you be so kind to post any errors and warnings you met during the installation process?

---

### Post by cuttersblade on 2009-11-26
after doing 'sudo sh ./cleanup.sh' i get a message saying 'it is recommended to purge openchrome driver package as well to do this you should run as root: aptitude purge xserver-xorg-video-openchrome.

after 'sudo sh ./install.sh' 'pay attention a non-RandR version of xorg.conf is copied! RandR seems to be working bad with this driver, so it is. just in case you want to try something, use another xorg.conf. A RandR-enabled xorg.conf is shipped with this package as well.

After it has attempted to restart GDM 'rather than invoking init scripts through /etc/init.d, use the service(8 ) utility, eg service gdm resart
Since the script you are attempting to invoke has been converted to an upstart job, you may also use the restart(8 ) utility, eg. restart GDM start/running, process 1736'

That help?

---

### Post by Rainier Piqual on 2009-11-26
> **Susp said:**
> That is really strange, Rainier.
I've tried it with Xubuntu 9.10 as well. And it works like a charm.
Did you got any errors or warnings when installing?
What is your notebook model?
Probably you had Via drivers installed previously?
If so, it is a good idea to remove them first.

I would also like somebody to try this with Live CD or Live USB.

Hej Susp.
Sorry, I could not make out any error messages, however, the last few messages suggested a successful installation.
Before, I had openchrome installed on my NC20. But as I read now cuttersblade post, I should purge the openchrome driver before? Can anyone confirm that this then works?

---

### Post by cuttersblade on 2009-11-27
I have tried running the 'aptitude purge xserver-xorg-video-openchrome' before trying the install but it hasn't helped, still get the cycling colour screens after running through the installation.

---

### Post by Susp on 2009-11-27
Uh. I'm really sorry that doesn't work for you guys. I would call such behavior nothing but weird.
Because... Damn, it worked for me!
Well, if you still don't give up, try using the xorg.conf from "The hard way" on the wiki pages.
I bet this helps you because basically the trouble is about refresh rates etcetera, I'm almost sure.
Please kindly do another try. I suggest you abort the auto-restarting of GDM just after the installation process, replace the /etc/X11/xorg.conf file with the one posted there and restart GDM manually, or simply reboot your computer. I am almost sure this is going to cause changes.
In order to restart GDM:
```
sudo service gdm start
```
Thank you.

---

### Post by cuttersblade on 2009-11-29
Copying the xorg.conf from the wiki has worked, i have a working desktop, many thanks

---

### Post by Rainier Piqual on 2009-11-29
> **cuttersblade said:**
> Copying the xorg.conf from the wiki has worked, i have a working desktop, many thanks

Uhm, how did you copy it while still in console? By hand?
If this only hinges upon the correct xorg.conf I will surely try it out in the next few days, but please be so kind as to answer my question first :)

---

### Post by cuttersblade on 2009-11-29
Yea i did it by hand, had the wiki open on my desktop and then just copied it over to my NC20 by hand.

---

### Post by Tubu78 on 2009-11-30
Hi,
thanks for "the easy way", it made my day. great work!

had the same probs with the "disco screen" in the beginning, copying the xorg.conf did the trick for me, too.

dont know if its the easiest way, cause im still a noob, but i did it like this.

1. copied the xorg.conf from the wiki to gedit, and safed it :) ( i allways put stuff i am going to work with on the desktop, dont ask me why, i dont know either )

2. changed to console ( Ctrl Alt F1 ) and followed the instructions "the easy way"

3. after installation pressed Ctrl C

4. then i just renamed the old xorg.confg and copied the one from the wiki to the folder

     sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
     sudo cp Desktop/xorg.conf /etc/X11/

5. rebooted


many thanks again for the great wiki

---

### Post by Susp on 2009-12-02
Hey there.
I'm glad you finally made it work, even though it seems to me that it is strange the whole party won't work with the included xorg config file. Even though, nice to see you have finally figured out what is wrong.
For those of you who is still not, I have updated the wiki pages once again, now they include the xorg.conf replacement notes. In order to make it easier, I have uploaded its copy to some host and it is supposed that you would copy it just after the installation. I am probably too lazy (or too busy) to re-pack the package with fixed xorg config. But I guess this little inconvenience won't turn up as a show-stopper for those who want responsive and feature-rich NC20. After all, the whole process is still much more clear and obvious and surely consumes lesser time for setting everything up.
You are welcome.

---

### Post by yoshiki2 on 2009-12-03
Any idea how to report this, so it can work out of the box in lucid lynx?
(openchrome is open software, right)?

---

### Post by Uli_of on 2009-12-04
Hello all,
is there anyone able to communicate
the processor tempereature running an idle KDE4.3 desptop ?
Thanks in advance.
Uli

---

### Post by Susp on 2009-12-04
Hello again, guys.

yoshki2:

Man, I guess you got the right idea. I'm interested in including the driver in Ubuntu base as well. To my opinion we should begin with creating the .deb package for this driver because the driver source is GNU GPL so I guess there is nothing blocking this. I wonder who we should contact on concern of building packages. I'll try to study this process, because I have a PPA with some software, but no drivers. I'm unsure if it is hard to use things like module-assistant.

Uli:

Never thought of something like that, I think Via Nano is pretty cold guy generally so it is not reasonable to watch its temperature. However, I've tried running lm-sensors and it told me the temperature. I guess there will be no problem for KDE temperature widget to detect it as well. Didn't tried though.

---

### Post by Uli_of on 2009-12-04
> **Susp said:**
> Hello again, guys.

yoshki2:

Man, I guess you got the right idea. I'm interested in including the driver in Ubuntu base as well. To my opinion we should begin with creating the .deb package for this driver because the driver source is GNU GPL so I guess there is nothing blocking this. I wonder who we should contact on concern of building packages. I'll try to study this process, because I have a PPA with some software, but no drivers. I'm unsure if it is hard to use things like module-assistant.

Uli:

Never thought of something like that, I think Via Nano is pretty cold guy generally so it is not reasonable to watch its temperature. However, I've tried running lm-sensors and it told me the temperature. I guess there will be no problem for KDE temperature widget to detect it as well. Didn't tried though.
My temperature is ~ 62°C idle and  up to 75°C under load.
I do not know wether this is standard or too high

---

### Post by Rainier Piqual on 2009-12-04
Thanks to the wiki and your contribution, susp, I have now a more responsive and smooth video playback. Great! Keep up the good work!

---

### Post by luc765 on 2009-12-05
To Pureblood and Susp


I tried the propriatory driver with Karmic about a month ago and the PC works more or less correctly but as mentioned by Pureblood it starts showing a lot of grabage and I have to switch to the console ctrl+alt+F1 and back to F7.

Please could you tell me if now with your method and xorg.cont this problem disepear and the machine do not crash for any reason.

Thanks in advance

Lucien

---

### Post by Susp on 2009-12-05
luc765:
Oh, is it so? In case it has been a month since you last tried it - it surely was a previous version of DRM module, because it was the only one available at that time. I bet it was a 86a-50937 series module. Well, it won't operate with Karmic normally as far as I know. I suggest you would kindly consider to try this. Simply because I'd like to collect the proofs of the good package state in order to recommend it to maintainers later.
*Addition: Ah, one more thing. I wonder why would everybody call this driver proprietary? Via had kindly opened the sources with GPL+AR licensing so that we could have all this, uh... fun. To my opinion, the driver is open-source.* :)

Uli:
Mine is dangling around 47 deg. C. when I'm doing some office work (PDFs, documents, Thunderbird mail, jabber on the background)

Rainier:
I'm glad you've found it useful.

---

### Post by luc765 on 2009-12-06
Susp, Pureblood your are the kings.......

I applied what you call the "easy way" as describe in your document  

[https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20)

My PC runs now like a racing car.... 1730i/5sec in place of 360i/5sec, no grabage no crashes.....

Manny thanks

Lucien

[http://users.skynet.be/linux-rixensart](http://users.skynet.be/linux-rixensart)

---

### Post by Joersch on 2009-12-11
Ja wir können / Yes, we can

**VIA Grafik Treiber**

Danke / Thanks

Glxgears ca.1710  :D:D:D:D

Grüße aus Germany

---

### Post by yoshiki2 on 2009-12-12
I've reported this bug..
[https://bugs.launchpad.net/hundredpapercuts/+bug/495901](https://bugs.launchpad.net/hundredpapercuts/+bug/495901)
follow that link and mark that you guys are being affected 2... So maybe it can work out of the bos in 10.04

---

### Post by Susp on 2009-12-12
yoshiki,

I think your bug report is completely invalid for the following reasons:
1. There *are* openchrome drivers included in a Live CD. The version may be some kind of outdated, but they are there.
2. OpenChrome drivers is not the stuff posted in easy way. OpenChrome is a standalone project, they have almost no relation to the official Via's graphics drivers. If you want an easy way packages included in base distribution, I suggest you would create another bug rep.
3. Graphics drivers are not meant for processors as you wrote there.

---

### Post by harrykipper on 2009-12-12
> **Joersch said:**
> 

Glxgears ca.1710  :D:D:D:D

could you post your xorg.conf? 
i can't get further then 320fps in glxgears :-(((

---

### Post by Susp on 2009-12-12
Hello, Harry.

You can't achieve this results with OpenChrome, no matter what sort of configuration file you are using.
Joersch must have used the "Easy way" as some other users already did.
To find out more on this, have a look at what I have posted [here]("http://ubuntuforums.org/showpost.php?p=8385916&postcount=338").

---

### Post by harrykipper on 2009-12-12
> **Susp said:**
> Hello, Harry.

You can't achieve this results with OpenChrome, no matter what sort of configuration file you are using.
Joersch must have used the "Easy way" as some other users already did.

i'm using VIA's binary driver + patched chrome9 compiled from source, here's my xorg.log. I have drm acceleration, but still glxgears gives me no more than 320fps
```
X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Slackware 13.0 Slackware Linux Project
Current Operating System: Linux schwarz 2.6.32 #2 PREEMPT Thu Dec 3 23:21:13 CET 2009 i686
Build Date: 03 August 2009  06:51:50PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 12 12:16:44 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "ConfiguredLayout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Card0"
(==) No monitor specified for screen "Screen0".
	Using a default monitor configuration.
(**) Option "RandR" "false"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/local" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/CID" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/TTF,
	/usr/share/fonts/Type1,
	/usr/share/fonts/misc,
	/usr/share/fonts/75dpi/:unscaled,
	/usr/share/fonts/100dpi/:unscaled,
	/usr/share/fonts/75dpi,
	/usr/share/fonts/100dpi,
	/usr/share/fonts/cyrillic,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1de0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:1:0) 1106:1122:144d:c04e rev 17, Mem @ 0xd0000000/268435456, 0xf4000000/16777216, 0xf0000000/67108864, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 5.74.86
	Module class: X.Org Video Driver
(II) via driver subversion: V86a-50937
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 00@00:01:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "VX800"
(--) VIA(0): Chipset Rev.: 0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 32768 kB
(II) VIA(0): VESA VBE OEM: VIA VX800


(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(**) VIA(0): Option "AccelMethod" "EXA"
(**) VIA(0): Option "ExaScratchSize" "8192"
(**) VIA(0): Option "ActiveDevice" "LCD"
(**) VIA(0): Option "PanelSize" "1280x800"
(**) VIA(0): Using EXA acceleration architecture.
(==) VIA(0): EXA composite acceleration enabled.
(II) VIA(0): MergedFB mode forced off.
(**) VIA(0): Active Device is LCD.
(**) VIA(0): LCD Panel Size is 1280x800.
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VGA BIOS Version is = 5.0
(II) VIA(0): VGA BIOS Release Date Is: 2008/12/1
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  262144k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VIA(0): Manufacturer: CMO  Model: 1233  Serial#: 0
(II) VIA(0): Year: 2008  Week: 45
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Digital Display Input
(II) VIA(0): Max Image Size [cm]: horiz.: 26  vert.: 17
(II) VIA(0): Gamma: 2.20
(II) VIA(0): No DPMS capabilities specified
(II) VIA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.560 redY: 0.350   greenX: 0.340 greenY: 0.560
(II) VIA(0): blueX: 0.159 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported detailed timing:
(II) VIA(0): clock: 69.3 MHz   Image Size:  260 x 170 mm
(II) VIA(0): h_active: 1280  h_sync: 1320  h_sync_end 1346 h_blank_end 1412 h_border: 0
(II) VIA(0): v_active: 800  v_sync: 803  v_sync_end 807 v_blanking: 818 v_border: 0
(II) VIA(0):  N121IB-L06
(II) VIA(0):  CMO
(II) VIA(0):  N121IB-L06
(II) VIA(0): EDID (in hex):
(II) VIA(0): 	70e15cb770e15cb7765f616374697665
(II) VIA(0): 	3a2025692020765f73796e633a202569
(II) VIA(0): 	2020765f73796e635f656e6420256920
(II) VIA(0): 	765f626c616e6b696e673a2025692000
(II) VIA(0): 	340004aa10000018000000fe39000000
(II) VIA(0): 	70e15cb770e15cb72020000000fe0043
(II) VIA(0): 	4d4f0a202020202020202020000000fe
(II) VIA(0): 	004e31323149422d4c30360a202000c4
(II) VIA(0): EDID vendor "CMO", prod id 4659
(II) VIA(0): Printing DDC gathered Modelines:
(II) VIA(0): Modeline "1280x800"x0.0   69.30  1280 1320 1346 1412  800 803 807 818 -hsync -vsync (49.1 kHz)
(--) VIA(0): Max Monitor H Size =  1280
(--) VIA(0): Max Monitor V Size =  800
(II) VIA(0): <default monitor>: Using hsync value of 49.08 kHz
(II) VIA(0): <default monitor>: Using vrefresh value of 60.00 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (hsync out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (hsync out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (hsync out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (vertical timing out of range)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (vertical timing out of range)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (vertical timing out of range)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (vertical timing out of range)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (vertical timing out of range)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (vertical timing out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (vertical timing out of range)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (vertical timing out of range)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "480x640" (hsync out of range)
(II) VIA(0): Not using default mode "720x480" (hsync out of range)
(II) VIA(0): Not using default mode "720x576" (hsync out of range)
(II) VIA(0): Not using default mode "800x480" (hsync out of range)
(II) VIA(0): Not using default mode "848x480" (hsync out of range)
(II) VIA(0): Not using default mode "852x480" (hsync out of range)
(II) VIA(0): Not using default mode "856x480" (hsync out of range)
(II) VIA(0): Not using default mode "960x600" (hsync out of range)
(II) VIA(0): Not using default mode "1000x600" (hsync out of range)
(II) VIA(0): Not using default mode "1024x512" (hsync out of range)
(II) VIA(0): Not using default mode "1024x576" (hsync out of range)
(II) VIA(0): Not using default mode "1024x600" (hsync out of range)
(II) VIA(0): Not using default mode "1088x612" (hsync out of range)
(II) VIA(0): Not using default mode "1152x720" (hsync out of range)
(II) VIA(0): Not using default mode "1152x864" (vertical timing out of range)
(II) VIA(0): Not using default mode "1200x720" (hsync out of range)
(II) VIA(0): Not using default mode "1280x600" (hsync out of range)
(II) VIA(0): Not using default mode "1280x720" (hsync out of range)
(II) VIA(0): Not using default mode "1280x768" (hsync out of range)
(II) VIA(0): Not using default mode "1280x800" (hsync out of range)
(II) VIA(0): Not using default mode "1280x960" (vertical timing out of range)
(II) VIA(0): Not using default mode "1360x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "1366x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "1368x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "1440x900" (vertical timing out of range)
(II) VIA(0): Not using default mode "1440x1050" (vertical timing out of range)
(II) VIA(0): Not using default mode "1600x900" (vertical timing out of range)
(II) VIA(0): Not using default mode "1600x1024" (vertical timing out of range)
(II) VIA(0): Not using default mode "1680x1050" (vertical timing out of range)
(II) VIA(0): Not using default mode "1792x1344" (vertical timing out of range)
(II) VIA(0): Not using default mode "1856x1392" (vertical timing out of range)
(II) VIA(0): Not using default mode "1920x1080" (vertical timing out of range)
(II) VIA(0): Not using default mode "1920x1200" (vertical timing out of range)
(II) VIA(0): Not using default mode "2048x1536" (vertical timing out of range)
(--) VIA(0): Virtual size is 1280x800 (pitch 1280)
(**) VIA(0): *Driver mode "1280x800": 69.3 MHz, 49.1 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x800"x60.0   69.30  1280 1320 1346 1412  800 803 807 818 -hsync -vsync (49.1 kHz)
(**) VIA(0): Display dimensions: (260, 170) mm
(**) VIA(0): DPI set to (125, 119)
(II) VIA(0): VIASetDisplayPath is Single
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): [drm] Detect H6 chipset: 0006  chipid: 1122
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:0:1:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:0:1:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) VIA(0): [drm] Using the DRM lock SAREA also for drawables.
(II) VIA(0): [drm] framebuffer handle = 0xd0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] mmio Registers = 0x4093640704
(II) VIA(0): [dri] mmio maped.
(II) VIA(0): VIAModeInit
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): -----CRT TIMING-----
(II) VIA(0): IGA1 timing
HActive=640, HSyncStart=656, HSyncEnd=752, HTotal=800 
VActive=480, VSyncStart=490, VSyncEnd=492, VTotal=525
(II) VIA(0):  PixelClock=25175000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1320, HSyncEnd=1346, HTotal=1412 
VActive=800, VSyncStart=803, VSyncEnd=807, VTotal=818
(II) VIA(0):  PixelClock=69300000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): -----LCD TIMING-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1328, HSyncEnd=1360, HTotal=1440 
VActive=800, VSyncStart=803, VSyncEnd=809, VTotal=823
(II) VIA(0):  PixelClock=69300000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): into 3D initial...3Dinitial? 0
(II) VIA(0): H6 3D Engine has been initilized.
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) VIA(0): VIAInternalScreenInit
(**) VIA(0): Option "MigrationHeuristic" "greedy"
(II) EXA(0): Offscreen pixmap area of 12288000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) VIA(0): Enable EXA Now
(II) VIA(0): [EXA] Trying to enable EXA acceleration.
(II) VIA(0): [dri] frame buffer initialized done.
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): DPMS enabled
(II) VIA(0): [DRI] installation complete
(II) VIA(0): [drm] use pcie
(II) VIA(0): Map agp/pcie texture memory successfully and branch buffer will work for H6 chipset! 
(II) VIA(0): [dri] kernel data initilized.
(II) VIA(0): direct rendering enabled
(**) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:0:1:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: Loaded and initialized /usr/lib/xorg/modules/dri/via_chrome9_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.3
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) VIA(0): Hqv0Saved.hqv_ctl:c4000008
(II) VIA(0): Hqv1Saved.hqv_ctl:5388006e
(II) VIA(0): [drm] Cleaning up DMA ring-buffer.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) VIA(0): VIAModeInit
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): -----CRT TIMING-----
(II) VIA(0): IGA1 timing
HActive=640, HSyncStart=656, HSyncEnd=752, HTotal=800 
VActive=480, VSyncStart=490, VSyncEnd=492, VTotal=525
(II) VIA(0):  PixelClock=25175000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1320, HSyncEnd=1346, HTotal=1412 
VActive=800, VSyncStart=803, VSyncEnd=807, VTotal=818
(II) VIA(0):  PixelClock=69300000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): -----LCD TIMING-----
(II) VIA(0): IGA2 timing
HActive=1280, HSyncStart=1328, HSyncEnd=1360, HTotal=1440 
VActive=800, VSyncStart=803, VSyncEnd=809, VTotal=823
(II) VIA(0):  PixelClock=69300000 Hz
(II) VIA(0): -----TIMING END-----
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) VIA(0): Hqv0 hqv_ctl:c400000e
(II) VIA(0): Hqv1 hqv_ctl:5388006e
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
```

no, i'm not using ubuntu :-)

---

### Post by yoshiki2 on 2009-12-12
Just check the link:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/495901](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/495901)
It's in this category:                                  [xserver-xorg-video-via (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via")                                        Edit                              
                                 [New]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/495901/+editstatus")         [           [IMG]https://bugs.launchpad.net/@@/edit[/IMG]         ]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/495901/+editstatus")       

     Maybe you can mark: this bug affects me 2. So it will work out of the box on 10.04. Via is releasing a new chipset that draws 6 watts and play 1024p, blu ray, decode h264... It'll be useful for the new generation dual nano. Sadly intel is just worried about reducing power consumption while Via is going for power and consumption.

---

### Post by lyovushka on 2009-12-12
I also get around 1700 fps with glxgears using easy way.
I'm a little bit surprised as previously I couldn't get more than 400 with proprietary drivers. I'm going to use it for a while and compare the experience with openchrome.

Thanks guys.

---

### Post by Exatic on 2009-12-14
Finally i decided to install Ubuntu 9.10 (fresh installation). Till now my experience with Karmic Koala has been unpleasant but maybe you guys can help me out. 

Things that don't work:
- Compiz.
- Audio playback. The sound rasps all the way through. Impossible to hear anything.
- CPU frequency is stuck at 800 mhz. I know this is a common bug. But does my CPU still work on 3.2GHZ, though?

I have looked trough the wiki without getting any further. On the bright side the regular freezups dont happen anymore.

---

### Post by Joersch on 2009-12-14
> **lyovushka said:**
> I also get around 1700 fps with glxgears using easy way.
I'm a little bit surprised as previously I couldn't get more than 400 with proprietary drivers. I'm going to use it for a while and compare the experience with openchrome.

Thanks guys.

:popcorn::popcorn::popcorn:**   Proprietary graphics driver (****The easy way)**

---

### Post by lyovushka on 2009-12-14
> **Exatic said:**
> Finally i decided to install Ubuntu 9.10 (fresh installation). Till now my experience with Karmic Koala has been unpleasant but maybe you guys can help me out. 

Things that don't work:
- Compiz.
- Audio playback. The sound rasps all the way through. Impossible to hear anything.
- CPU frequency is stuck at 800 mhz. I know this is a common bug. But does my CPU still work on 3.2GHZ, though?

I have looked trough the wiki without getting any further. On the bright side the regular freezups dont happen anymore.

3.2GHZ? :o No it definitely doesn't work on 3.2GHZ and it never had before

---

### Post by Susp on 2009-12-15
Hello, Exatic.

> CPU frequency is stuck at 800 mhz. I know this is a common bug. But does my CPU still work on 3.2GHZ, though?
Sadly it is not so.
FYI, the installed Via Nano processor is capable of 1.6Ghz, but not 3.2Ghz, you may check the Wikipedia on this.
As you can see, the wiki contains a link to the bug I have started: [LP488792]("https://bugs.launchpad.net/ubuntu/+bug/488792"). It does describe the situation around the cpu frequency scaling it Karmic, in case you are familiar to kernel building, I guess you would fix this one easily, but for yourself. If we want this into the basic Karmic distribution, the best idea out there is subscribe to this bug altogether and hope that maintainers would notice this. The bug entry above clarifies the situation with scaling, you could find everything there.

> Compiz
Strange it is, I thought it would work with this driver. Furthermore, somebody confirmed that it worked. I bet that is all about the X configuration you are using.

> Audio playback. The sound rasps all the way through
I suggest you would update your Alsa packages. The audio is reported to work nicely since alsa v.20.
You may also try turning off pulseaudio.

---

### Post by lyovushka on 2009-12-17
7 kernel panics in 4 days made the decision easy. I'm switching back to openchrome :(

---

### Post by Uli_of on 2009-12-20
> **Susp said:**
> Hello, Exatic.


Sadly it is not so.
FYI, the installed Via Nano processor is capable of 1.6Ghz, but not 3.2Ghz, you may check the Wikipedia on this.
As you can see, the wiki contains a link to the bug I have started: [LP488792]("https://bugs.launchpad.net/ubuntu/+bug/488792"). It does describe the situation around the cpu frequency scaling it Karmic, in case you are familiar to kernel building, I guess you would fix this one easily, but for yourself. If we want this into the basic Karmic distribution, the best idea out there is subscribe to this bug altogether and hope that maintainers would notice this. The bug entry above clarifies the situation with scaling, you could find everything there.


Strange it is, I thought it would work with this driver. Furthermore, somebody confirmed that it worked. I bet that is all about the X configuration you are using.


I suggest you would update your Alsa packages. The audio is reported to work nicely since alsa v.20.
You may also try turning off pulseaudio.
Hello all,
Has anyone compiled the "cpufreq-via" module from VIA driver homepage with
kernel version 2.6.32.
Any help would be welcome.
Uli

---

### Post by tom09 on 2009-12-20
Change line 869 in cpufreq-via.c from
```
data->acpi_data = percpu_ptr(acpi_perf_data, cpu);
```to
```
data->acpi_data = per_cpu_ptr(acpi_perf_data, cpu);
```

---

### Post by Uli_of on 2009-12-20
> **tom09 said:**
> Change line 869 in cpufreq-via.c from
```
data->acpi_data = percpu_ptr(acpi_perf_data, cpu);
```to
```
data->acpi_data = per_cpu_ptr(acpi_perf_data, cpu);
```

Thank you.
It worked.
Regards

---

### Post by nthroot on 2009-12-22
Hi everybody,

I'm running Karmic with 2.6.32.2 ([kernel-ppa]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.2/")) and the via proprietary driver ([ubuntu community doc]("https://help.ubuntu.com/community/NC20#The%20hard%20way")).

No kernel panics, no freezes, no crashes and stable wifi so far :P Everything else seems to be pretty stable and works out of the box.

Glxgears gives 2400-2500 fps :guitar:

---

### Post by lyovushka on 2009-12-23
> **nthroot said:**
> Hi everybody,

I'm running Karmic with 2.6.32.2 ([kernel-ppa]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.2/")) and the via proprietary driver ([ubuntu community doc]("https://help.ubuntu.com/community/NC20#The%20hard%20way")).

No kernel panics, no freezes, no crashes and stable wifi so far :P Everything else seems to be pretty stable and works out of the box.

Glxgears gives 2400-2500 fps :guitar:
Most of my kernel panics happened while reading documents in evince. Unfortunately I use evince a lot.

2400 fps sounds too good to be true. I don't even know what to think. But can you use google-earth, because when I tried to do so with proprietary drivers the speed was normal but it didn't show maps properly?

---

### Post by nthroot on 2009-12-23
> **lyovushka said:**
> Most of my kernel panics happened while reading documents in evince. Unfortunately I use evince a lot.

2400 fps sounds too good to be true. I don't even know what to think. But can you use google-earth, because when I tried to do so with proprietary drivers the speed was normal but it didn't show maps properly?

Just read a few PDFs in the last days, but I'll keep an eye on possible crashes.

Google Earth performance is good. After switching off texture compression, textures indeed appear, but they have a strong green cast :(

EDIT: To fix the green cast, simply turn off the atmosphere under view preferences. Then everything in Google Earth runs smooth an looks great.

---

### Post by lyovushka on 2009-12-25
> **nthroot said:**
> Just read a few PDFs in the last days, but I'll keep an eye on possible crashes.

Google Earth performance is good. After switching off texture compression, textures indeed appear, but they have a strong green cast :(

EDIT: To fix the green cast, simply turn off the atmosphere under view preferences. Then everything in Google Earth runs smooth an looks great.

Thank you, I've switched off texture compress and not it works good. Mine works good both with or without atmosphere.

---

### Post by luc765 on 2009-12-26
> **lyovushka said:**
> Most of my kernel panics happened while reading documents in evince. Unfortunately I use evince a lot.

2400 fps sounds too good to be true. I don't even know what to think. But can you use google-earth, because when I tried to do so with proprietary drivers the speed was normal but it didn't show maps properly?
As you mentioned, the 2.6.32 kernel gives better results. 
However I have a problem at startup. Whenever I get the message "Unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to overide" and then I have to reboot a second time in selecting the kernel 2.6.32 for it to work
.
How did you do to avoid or to solve this problem

Thanks in advance

Lucien

---

### Post by LodeRunner on 2009-12-27
> **Sackley85 said:**
> Just tried that method with Xubuntu and still no 

I haven't tried Xubuntu, but "OpenFish" mentioned somewhere that adding the line "vga=771" fixes the alternate installer, and it does. Press f6, escape, type that and then hit enter.  After it's installed, you won't have video but you will be able to access the console by pressing control + alt + [F1 - F6]. You can install whatever video drivers you wish from there. (I'm using the openchrome drivers from [here]("https://launchpad.net/~xorg-edgers/+archive/drivers-only/+build/1307486"). They're slow, but they work just fine for everything other than gaming and fullscreen / HD video.)

By the way, if you are going the alt installer route you might want to consider full AES disk encryption, or at the very least home encryption.  Via's chipset includes their Padlock AES / SHA acceleration, and it's really simple to add support for dm-crypt (unfortunately, it's somewhat less easy for OpenSSL.) Just edit /etc/initramfs-tools/modules, add new lines "padlock-aes" and "padlock-sha", save, run "sudo update-initramfs -u" (unless you are using compcache; see below), reboot, and enjoy triple-speed hard disk reads (non-cached).

One final note: if you're doing full disk encryption you probably don't want to create a swap partition. Instead, use compcache. This creates a compressed, virtual swap space in ram. Ignore the warning the text installer gives you, edit etc/initramfs-tools/initramfs.conf , do a control-f search for compcache and insert a percentage in the quotes "". (I did "10%", but people have widely differing opinions about the magnitude and necessity of swap. I personally wouldn't recommend putting more than 15% here unless you've upgraded your ram.) Do this, then add the padlock lines to modules as shown above, then run update-initramfs but this time use "sudo update-initramfs -k all -c".

---

### Post by nthroot on 2009-12-27
> **luc765 said:**
> However I have a problem at startup. Whenever I get the message "Unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to overide" and then I have to reboot a second time in selecting the kernel 2.6.32 for it to work

Hi Lucien,

I see this message as well while my System loads fine every time.

The message is related to AppArmor. It didn't make it into vanilla 2.6.32. Ubuntu's stock 2.6.31 seems to have AppArmor patches applied, while the 2.6.32-packages posted above don't have them.

This wiki page mentions several ways to disable it: [https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework](https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework)

I disabled it via:
```
sudo apt-get remove apparmor
sudo update-initramfs -u
```Cheers,
Matthias

---

### Post by 2345 on 2009-12-27
[https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20)
> [http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424](http://ubuntuforums.org/attachment.php?attachmentid=133328&d=1256670424) 
Main thread: [http://ubuntuforums.org/showthread.php?t=1079314](http://ubuntuforums.org/showthread.php?t=1079314) 
[B]compile it and then move the via_chrome9.ko file to 
/lib/modules/uname -r/kernel/ubuntu/via_chrome9/via_chrome9.ko[/B] How do i "move" the file and use this command? "sudo mv" and than this command line is not working.

Using UNR 9.10 and 2.6.31 kernel, openchrome or via (easy way) works - but extremly slow.

Gets faster with this trick
[http://ubuntuforums.org/showpost.php?p=8232024&postcount=6]("http://ubuntuforums.org/showthread.php?t=1308792")

Thanks

---

### Post by nthroot on 2009-12-28
> **2345 said:**
> [https://help.ubuntu.com/community/NC20](https://help.ubuntu.com/community/NC20)
How do i "move" the file and use this command? "sudo mv" and than this command line is not working.

Try this one:
```
sudo mv via_chrome9.ko /lib/modules/`uname -r`/kernel/ubuntu/via_chrome9/via_chrome9.ko
```Take care of the backticks and don't use single quotes instead. This is a shell feature called "command substitution". The output of the command replaces the command itself.

On my system [FONT=Courier New]uname -r[/FONT] produces:
```
2.6.32-02063202-generic
```Thus the shell would do the command substitution and would execute the following command instead:
```
sudo mv via_chrome9.ko /lib/modules/2.6.32-02063202-generic/kernel/ubuntu/via_chrome9/via_chrome9.ko
```

---

### Post by 2345 on 2009-12-28
Thank you nthroot, 
but i tried

sudo mv via_chrome9.ko /lib/modules/`uname -r`/kernel/ubuntu/via_chrome9/via_chrome9.ko

But everytime i got a error about directory not existing. And even trying manual copy would not work, as the folder structure is diffrent.

/uname -r/build/kernel   no ubuntu folder.


Anway besides i was able to setup UNR 9.10 with 2.6.31 i was not satisfied with the performance (around 500 fps glxgears).

So i go back and install fedora 12, which is pretty straight forward ... installing took approx (download iso and fedora USB iso tool - creating/installing/booting) 40 mins only. With fedora 12 i get around 57.000 fps ... LOL

I find it pretty sad that ubuntu offers netbook remix for liek almost the year, which is not working on nc20 without this hazzle of terminal use, downloading, reading 4 diffrent ways of installing and all this ...

On the positive site i learned a few new terminal commands and that UNR target are touch screen mainstream netbooks.:)

---

### Post by wasteinc on 2009-12-30
results so far:popcorn:

openchrome is stable, but no compiz and extremely slow
VIA **** driver is quite unstable, compiz works quite good, but system locks up every now and then. (5-8 times during a full work day).

any other people experiencing locks with via's driver?? (not even ctrl-alt-backspace working)

For movies , I still use windows and MDC ;-)

and considering some general stuff

Samsung is about to drop nc20, in favor of the n510 atom/ion based setup. In germany there is a sell off at 300 euro and less.

Via apart from some big talk concerning open-source, will do[ small stuff]("http://www.phoronix.com/scan.php?page=article&item=via_2010_roadmap&num=1") during the whole 2010, so Im not quite optimistic that we will definitely see tha nc20 shine on ubuntu. Which is quite a shame because its a very nice laptop and a very nice platform. all stuff considered

kudos to all the people giving advice and solutions to this very grumpy laptop, and made ubuntu happen

PS I havnt managed to make fn-f9 work (wireless on-off) dispite the workaround in the manual. Is it just me?

---

### Post by pureblood on 2009-12-30
> Has anyone compiled the "cpufreq-via" module from VIA driver homepage with
kernel version 2.6.32.

@Uli_of, where can I find the cpufreq-via source code? Also, did you have to recompile the whole 2.6.32 kernel to make it work?

---

### Post by luc765 on 2009-12-30
> **nthroot said:**
> Hi Lucien,

I see this message as well while my System loads fine every time.

The message is related to AppArmor. It didn't make it into vanilla 2.6.32. Ubuntu's stock 2.6.31 seems to have AppArmor patches applied, while the 2.6.32-packages posted above don't have them.

This wiki page mentions several ways to disable it: [https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework](https://help.ubuntu.com/community/AppArmor#Disable%20AppArmor%20framework)

I disabled it via:
```
sudo apt-get remove apparmor
sudo update-initramfs -u
```Cheers,
Matthias
Thank you for tour advice Mathias,


The problem apparmor is solve.
The last problem is that at the boot the system takes more than 2 minutes. Have you an idea of that problem ??

Lucien

---

### Post by Uli_of on 2009-12-30
> **pureblood said:**
> @Uli_of, where can I find the cpufreq-via source code? Also, did you have to recompile the whole 2.6.32 kernel to make it work?
The VIA sourcefile is on the VIA downloadpage.
I think it is the BSP source file
You can take the CPUFREQ part and compile it seperatly with kernel 2.6.32.
Move the modul to lib/modules/`uname -r`/arch/x86/kernel/cpu/cpufreq/
Regards
Uli

---

### Post by nthroot on 2009-12-31
> **luc765 said:**
> The last problem is that at the boot the system takes more than 2 minutes. Have you an idea of that problem ??


I've seen this long boot times aswell (not every time, but up to 4-5 minutes) The log says something about auto-probing... it might be sound chip related. Got no solution so far :(

---

### Post by lyovushka on 2010-01-02
> **wasteinc said:**
> 
PS I havnt managed to make fn-f9 work (wireless on-off) dispite the workaround in the manual. Is it just me?

Neither have I, but this is a small problem. My wireless hangs often and this is a real problem. Luckily I mostly use Ethernet nowadays, but sometimes I use a wifi and it's really annoying when it hangs and I have to reboot the laptop.

---

### Post by Tobis87 on 2010-01-09
> **nthroot said:**
> [QUOTE=luc765;8583729]The last problem is that at the boot the system takes more than 2 minutes. Have you an idea of that problem ??
I've seen this long boot times aswell (not every time, but up to 4-5 minutes) The log says something about auto-probing... it might be sound chip related. Got no solution so far :([/QUOTE]
Add clocksource=hpet to the kernel command line, this will speedup the boot process a little bit.
The kernel also resets the harddisk from time to time, during the boot process. I have not yet found a solution for that.

---

### Post by luc765 on 2010-01-11
> **Tobis87 said:**
> Add clocksource=hpet to the kernel command line, this will speedup the boot process a little bit.
The kernel also resets the harddisk from time to time, during the boot process. I have not yet found a solution for that.

You'r right but a very little bit

Thanks

Lucien

---

### Post by chrome9 on 2010-01-13
Has anybody managed to get DualScreens working? I dont't mean cloning the desktop, but spanning it over 2 monitors. I use the latest VIA drivers. If anybody has a solution, please post it! I'm using the NC20 for 8 months now and linux support has improved a lot. So this is one last lack of feature for me. Thanks to all the contributors in this thread. It feel like a family in the family (NC20-user who use ubuntu...)
:guitar:

---

### Post by lyovushka on 2010-01-22
Has anybody managed to make new Skype 2.1 beta 2 work?

---

### Post by Uli_of on 2010-01-24
> **lyovushka said:**
> Has anybody managed to make new Skype 2.1 beta 2 work?
Skype 2.1 beta2 works for my partially.
Im am struggeling with my microphon.
That is not working properly with all applications.
regards

---

### Post by sickenmcsluggets on 2010-01-31
Anybody try Lucid Lynx with the NC20 yet? I booted with it from usb persistent and it seems to be pretty working pretty well so far...well at least graphically, and the wifi works great. So far so good.

---

### Post by mdragt on 2010-02-02
Hi all,
Thanks for the great work to get linux running smoothly on a NC20. Unlike most of you, I'm running Fedora 12 with the following details:

# uname -r
2.6.31.12-174.2.3.fc12.i686
# X -version

X.Org X Server 1.7.4
Release Date: 2010-01-08
X Protocol Version 11, Revision 0
Build Operating System: x86-04 2.6.18-164.6.1.el5 
Current Operating System: Linux lynx.ssc.kalliance.nl 2.6.31.12-174.2.3.fc12.i686 #1 SMP Mon Jan 18 20:22:46 UTC 2010 i686
Kernel command line: ro root=/dev/mapper/vg_lynx-lv_root rhgb quiet vga=792 SYSFONT=latarcyrheb-sun16 LANG=nl_NL.UTF-8 KEYTABLE=us-acentos
Build Date: 08 January 2010  04:30:00AM
Build ID: xorg-x11-server 1.7.4-1.fc12 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://bodhi.fedoraproject.org/](http://bodhi.fedoraproject.org/)
	to make sure that you have the latest version.

I've used Susp.'s 574-u904-n.tar.gz with the enclosed xorg.conf (#260) and tom09's drm-chrome9_2.6.31.tar.gz (#275). I restarted KDM/rebooted, but I get an error in my /var/log/Xorg.0.log:

(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
**dlopen: /usr/lib/xorg/modules/drivers/via_drv.so: undefined symbol: resVgaShared**
(EE) Failed to load /usr/lib/xorg/modules/drivers/via_drv.so
(II) UnloadModule: "via"
(EE) Failed to load module "via" (loader failed, 7)
(EE) No drivers available 

Also tried the xorg.conf from pureblood (#315), without luck. Please help, as I look forward to joining the "successful!" team...

Martin

---

### Post by tom09 on 2010-02-02
The via driver is incompatible with all X servers version 1.7.0 and above. You'll have to downgrade the xorg-server to 1.6.5.

---

### Post by mdragt on 2010-02-05
Will the via driver be made available for X 1.7.0 and up any day soon?  Can we influnce that...?

Edit: where should I be looking for an older X-version? All I can find is on [http://www.x.org/wiki/Releases?action=show&redirect=XorgReleases]("http://www.x.org/wiki/Releases?action=show&redirect=XorgReleases");. This tells me:

The last release of X.Org was 7.4, on September 23, 2008.
X.Org 7.0 (Released: 2005-12-21)

---

### Post by mdragt on 2010-02-14
Regarding the issue:
ath5k phy0: failed to wakeup the MAC Chip
ath5k phy0: can't reset hardware (-5)

This appears to be gone if you're NOT using WPA or WPA2 for your wireless securtity. I use MAC-address filtering and a 128 bit WEP key, and that appears to be stable the last few hours.

Regards
Martin

---

### Post by lyovushka on 2010-02-14
Hi guys,

I decided to try opensound on NC20, but found out that skype_static_oss is no longer available from skype's webpage. Does anyone have the old binary for oss or knows where to get it?

---

### Post by luc765 on 2010-02-14
> **lyovushka said:**
> Hi guys,

I decided to try opensound on NC20, but found out that skype_static_oss is no longer available from skype's webpage. Does anyone have the old binary for oss or knows where to get it?
I have and I use effectively an old version of Skype for my NC20 PC runing Karmic.
With that old version internal micro and HP work fine.
The version is skype-debian_2.0.0.63-1_i386.deb 14,7MB
The problem is how to send you this SW ??? Have you an idea ??

Lucien

---

### Post by lyovushka on 2010-02-14
> **luc765 said:**
> I have and I use effectively an old version of Skype for my NC20 PC runing Karmic.
With that old version internal micro and HP work fine.
The version is skype-debian_2.0.0.63-1_i386.deb 14,7MB
The problem is how to send you this SW ??? Have you an idea ??

Lucien

Thanks you very much, but your version is the ordinary version of skype, not the one for oss. Anyway, I have already found it here
[http://www.fileupyours.com/view/77985/skype_static-2.0.0.72-oss.tar.bz2](http://www.fileupyours.com/view/77985/skype_static-2.0.0.72-oss.tar.bz2)
Thanks again

---

### Post by Rainier Piqual on 2010-02-18
by the way, can we expect any improvements concerning nc20 support to be made with the upcoming ubuntu release?
did anyone of you already give it a try?

---

### Post by Uli_of on 2010-03-02
Hello all,
The VIA driver is not working anylonger with the latest Xorg version.
It does not compile.
I also use kernel 2.6.33. Is there anyone who has resolved this issue ?

---

### Post by tom09 on 2010-03-02
Hello everybody,
here is a new version for the VIA drm kernel module, which restores compatibility with kernel 2.6.33. I also attached a *very preliminary* and *experimental* (!!!) version of a patched X.Org 2D driver for the xorg-server 1.7 series, based on the open source 2D driver from linux.via.com.tw.

Things that work (at least for me...):
- 2D XAA acceleration
- 3D acceleration (with via_chrome9_dri.so)
- RandR 1.2
- XVideo
- suspend-to-ram (well, sometimes...)

Things that do NOT work (but did with xorg-server 1.6):
- EXA acceleration (use AccelMethod "XAA" in xorg.conf instead)
- DPMS
I could use some help here, especially with EXA, I am not really an experienced programmer...

Hopefully this stuff is of some use for you, feel free to comment and post your experience.

tom09

Edit1: Fixed DRM driver to work with kernels < 2.6.33 as well

---

### Post by Uli_of on 2010-03-03
Thanks for the files,
I compiled them, but I get only coloured and black an white screens
after installation.
My via_chrome9_dri.so is dated 2009-09-02.
Is there a newer version available?
Thanks in advance
Uli

---

### Post by tom09 on 2010-03-04
No problem here on 10.04 Alpha3. I had to disable all those framebuffer boot splash things, though. As for the DRI driver: There is no updated version available, but the old version still works.

---

### Post by Tobis87 on 2010-03-08
> **mdragt said:**
> Regarding the issue:
ath5k phy0: failed to wakeup the MAC Chip
ath5k phy0: can't reset hardware (-5)

Try the following patch, this fixed the issue with the ath5k driver for me.

```
diff --git a/drivers/net/wireless/ath5k/base.c b/drivers/net/wireless/ath5k/base.c
index 5ef3229..248a34f 100644
--- a/drivers/net/wireless/ath5k/base.c
+++ b/drivers/net/wireless/ath5k/base.c
@@ -526,6 +526,7 @@ ath5k_pci_probe(struct pci_dev *pdev,
 	sc->cachelsz = csz * sizeof(u32); /* convert to bytes */
 	sc->opmode = NL80211_IFTYPE_STATION;
 	mutex_init(&sc->lock);
+	spin_lock_init(&sc->restlock);
 	spin_lock_init(&sc->rxbuflock);
 	spin_lock_init(&sc->txbuflock);
 	spin_lock_init(&sc->block);
@@ -2685,6 +2686,7 @@ ath5k_reset(struct ath5k_softc *sc, bool stop, bool change_channel)
 {
 	struct ath5k_hw *ah = sc->ah;
 	int ret;
+	unsigned long flags;
 
 	ATH5K_DBG(sc, ATH5K_DEBUG_RESET, "resetting\n");
 
@@ -2693,7 +2695,11 @@ ath5k_reset(struct ath5k_softc *sc, bool stop, bool change_channel)
 		ath5k_txq_cleanup(sc);
 		ath5k_rx_stop(sc);
 	}
+
+	spin_lock_irqsave(&sc->restlock, flags);
 	ret = ath5k_hw_reset(ah, sc->opmode, sc->curchan, true);
+	spin_unlock_irqrestore(&sc->restlock, flags);
+
 	if (ret) {
 		ATH5K_ERR(sc, "can't reset hardware (%d)\n", ret);
 		goto err;
diff --git a/drivers/net/wireless/ath5k/base.h b/drivers/net/wireless/ath5k/base.h
index facc60d..bd08aae 100644
--- a/drivers/net/wireless/ath5k/base.h
+++ b/drivers/net/wireless/ath5k/base.h
@@ -152,6 +152,7 @@ struct ath5k_softc {
 				led_off;	/* off time for current blink */
 
 	struct tasklet_struct	restq;		/* reset tasklet */
+	spinlock_t		restlock;	/* protects reset state */
 
 	unsigned int		rxbufsize;	/* rx size based on mtu */
 	struct list_head	rxbuf;		/* receive buffer */
diff --git a/drivers/net/wireless/ath5k/phy.c b/drivers/net/wireless/ath5k/phy.c
index 7ba18e0..fe45a2f 100644
--- a/drivers/net/wireless/ath5k/phy.c
+++ b/drivers/net/wireless/ath5k/phy.c
@@ -1621,7 +1621,7 @@ int ath5k_hw_rfregs(struct ath5k_hw *ah, struct ieee80211_channel *channel,
 
 	if (ah->ah_rf_banks == NULL) {
 		/* XXX do extra checks? */
-		ah->ah_rf_banks = kmalloc(ah->ah_rf_banks_size, GFP_KERNEL);
+		ah->ah_rf_banks = kmalloc(ah->ah_rf_banks_size, GFP_ATOMIC);
 		if (ah->ah_rf_banks == NULL) {
 			ATH5K_ERR(ah->ah_sc, "out of memory\n");
 			return -ENOMEM;

```

---

### Post by Uli_of on 2010-03-21
Hello all,
I am running moovida as a videoplayer and internet-video-viewer.
The output of the videos is only black and white. 
The program itself and the previews are ok.
I belive this is a VIA driver issue
with GL. Has anyone this program running properly ?

---

### Post by synkrox on 2010-04-02
Hi everyone.

I havent tried ubuntu netbook before, have just installed the lucid beta 1 on my nc20. wow, everything looks slick. loving it. 
now... if only the video acceleration worked so the likes of youtube was useable..

I have tried the "easy method" posted before, but seems to just make the screen go blank when the OS loads up. 

I dont mind editing conf files and the like, but I dont have any experience compiling stuff from scratch. 

Could anyone help me out with getting a better driver loaded up?

Cheers

Chris

---

### Post by moldy on 2010-04-15
Just been testing 10.04 on my NC20. I've no experience as anything other than a user, and this might not be the right place to put this post - but here are my observations.

Out of the box installation seems to work fine. The following things do not seem to work correctly out of the box:

- no microphone
- brightness control
- VERY short battery time
- scrambled screen on loading and shutting down
- no special effects (not sure if these will ever work)

But, a few issues that I had with 9.10 are fixed. For example, no more gimp freezing, video and audio seems to work fine.

Just my observations (and by no means complete). Please move to appropriate place if necessary.

Moldy.

---

### Post by Rainier Piqual on 2010-04-16
> **moldy said:**
> Just been testing 10.04 on my NC20. I've no experience as anything other than a user, and this might not be the right place to put this post - but here are my observations.

Out of the box installation seems to work fine. The following things do not seem to work correctly out of the box:

- no microphone
- brightness control
- VERY short battery time
- scrambled screen on loading and shutting down
- no special effects (not sure if these will ever work)

But, a few issues that I had with 9.10 are fixed. For example, no more gimp freezing, video and audio seems to work fine.

Just my observations (and by no means complete). Please move to appropriate place if necessary.

Moldy.

Thank you for your insights Moldy! Sounds promising. (except for the battery time)
Report back if you gain any additional observations :)

---

### Post by moldy on 2010-04-19
> **moldy said:**
> Just been testing 10.04 on my NC20. I've no experience as anything other than a user, and this might not be the right place to put this post - but here are my observations.

Out of the box installation seems to work fine. The following things do not seem to work correctly out of the box:

- no microphone
- brightness control
- VERY short battery time
- scrambled screen on loading and shutting down
- no special effects (not sure if these will ever work)

But, a few issues that I had with 9.10 are fixed. For example, no more gimp freezing, video and audio seems to work fine.

Just my observations (and by no means complete). Please move to appropriate place if necessary.

Moldy.

Just reporting that battery issue seems to have been fixed. In my experience, the rest of the issues still remain.

Also, the webcam seems to be pointing in a strange direction. Only the top-left quartile of the webcam's view is in shot. This happens in both skype and other webcam programs.

---

### Post by lyovushka on 2010-04-21
> **moldy said:**
> Just reporting that battery issue seems to have been fixed. In my experience, the rest of the issues still remain.

Also, the webcam seems to be pointing in a strange direction. Only the top-left quartile of the webcam's view is in shot. This happens in both skype and other webcam programs.

I also had the issue with webcam with openchrome driver. However this is just an issue from your side, i.e. people I am talking with can see me normally, not just the top left quartie.

---

### Post by stanger192 on 2010-04-24
tom09: thanks for your work with the via video drivers. is there any chance you could explain how to install the 3d drivers as im somewhat confused as how to go about it...

---

### Post by tom09 on 2010-04-26
The 3D driver consists of two files: via_chrome9_dri.so and libGL.so.1.2.via_chrome9. Both are part of the binary driver package for Ubuntu 9.04 from VIA's website. It needs the kernel driver compiled for the kernel running your Ubuntu system and successfully loaded.
So, to use the 3D driver, the two files must be copied into the correct directories. via_chrome9_dri.so goes into /usr/lib/dri, and libGL.so.1.2.via_chrome9 goes into /usr/lib as libGL.so.1.2. The existing libGL.so.1.2 that comes with Ubuntu must be replaced, so make a backup copy of the original file. When all is set, restart Ubuntu and open a terminal window. Type "glxinfo | grep direct" (without the quotes), it should return "direct renderding: Yes". If everything works, try running glxgears from terminal, you should get about 2100 fps.
If glxinfo says that direct rendering is not enabled, you can check the following things:
- Is the kernel module loaded ? ("lsmod | grep via_chrome9")
- Is Ubuntu using the VIA Xorg driver ? (look into /var/log/Xorg.0.log)
- Error and warning messages in /var/log/Xorg.0.log

Good luck,
tom09

---

### Post by peter27 on 2010-04-30
I have just installed ubuntu 10.4 on a nc20. The problems we had with graphics after a 9.10 installation are gone. 

But I can't get compiz to work. When I try to enable visual effects it says that "Desktop effects could not be enabled". Any ideas ? Thanks in advance.

---

### Post by moldy on 2010-05-02
Dammit - after using Gimp in 10.04 without issue since the beta phase, all of a sudden today I am back with the system freezing solid whenever an image is opened. I have no clue as to what is different between this morning and this afternoon - but it is so frustrating to nearly get to a stage where I can do everything I need, and then in an instant I am back into Windows again because it works with my machine.

---

### Post by sickenmcsluggets on 2010-05-02
> **moldy said:**
> Also, the webcam seems to be pointing in a strange direction. Only the top-left quartile of the webcam's view is in shot. This happens in both skype and other webcam programs.

I noticed that in the Cheese program as well, but if you actually take your pic in that program, it shows that the webcam is picking up everything normally. It seems to show you the odd quarter-view even though it is actually picking everything up normally.

---

### Post by lyovushka on 2010-05-03
Hi guys,

Today installed Lubuntu 10.04 (Ubuntu with LXDE). When I try to enable e_powersaver, I get

sudo modprobe e_powersaver 
FATAL: Error inserting e_powersaver (/lib/modules/2.6.32-21-generic/kernel/arch/x86/kernel/cpu/cpufreq/e_powersaver.ko): Invalid argument

Any ideas?

---

### Post by tom09 on 2010-05-03
U10.04 uses the acpi-cpufreq kernel driver for CPU frequency scaling, so you cannot load e_powersaver. Unfortunately, acpi-cpufreq is built into the kernel, so you also cannot simply unload it and use e_powersaver instead. But the bug within this driver resulting in a permanent 800Mhz frequency was fixed, so e_powersaver is not necessary anymore.

---

### Post by lyovushka on 2010-05-03
> **tom09 said:**
> U10.04 uses the acpi-cpufreq kernel driver for CPU frequency scaling, so you cannot load e_powersaver. Unfortunately, acpi-cpufreq is built into the kernel, so you also cannot simply unload it and use e_powersaver instead. But the bug within this driver resulting in a permanent 800Mhz frequency was fixed, so e_powersaver is not necessary anymore.

Yes it really uses acpi-cpufreq, but for some reason this doesn't quite work. Here is the output of cpufreq-info

pufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1.10 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  [B]current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 1.60 GHz.
  cpufreq stats: 1.60 GHz:56.96%, 1.40 GHz:0.09%, 1.30 GHz:0.08%, 1.20 GHz:0.12%, 1.10 GHz:0.11%, 1000 MHz:0.12%, 900 MHz:0.15%, 800 MHz:42.38%  (21822)

---

### Post by tom09 on 2010-05-04
Ubuntu seems to have some strange default settings for CPU frequency contol: It uses the maximum frequency permanently while the power cord is connected and pulls it down to 1.3 GHz when in battery mode.
However, there is a GNOME panel applet which controls the frequencies and the policy used for clock control. I installed the gnome-applets package and added the CPU Frequency control applet to the panel, then selected "ondemand". Now the processor is clocked with low frequency (800MHz) when idle and with higher frequencies up to 1.6GHz if needed.

---

### Post by lyovushka on 2010-05-04
Hm, now it also works for me, but I didn't do anything, except rebooting machine once :confused:

---

### Post by moldy on 2010-05-04
I would be very glad if any of you guys with proper technical knowledge could provide some comment when you are able on the new 10.04. As a user with no technical experience, I find the issues frustrating - but look forward to any solutions you kind people may be able to offer. Cheers, Moldy.

---

### Post by stenosis on 2010-05-05
could somebody please write a proper instruction down how to integrate this via hack into the 10.4 system?

---

### Post by Mal Bridgeman on 2010-05-05
[COLOR=DarkRed]I initially tried to install the 64bit desktop version of 10.04 but had lots of problems with the suspend, or more precisely, resume from suspend.

I had the 32bit Netbook remix on a stick for one of my other machines so I tried that out and it installed really well with most features enabled "out of the box".

I booted into Gnome Desktop rather than UNR which looks better System>Administration>Login Screen>Unlock>Select Gnome 

I then installed the Samsung NC20 specific fixes from [http://www.voria.org/forum/viewtopic.php?f=3&t=296](http://www.voria.org/forum/viewtopic.php?f=3&t=296) and seem to have a "fully" [1] functioning machine (no compiz effects but I don't need them on here) 

HTH
Mal

[1] For what I need at least.[/COLOR]

---

### Post by tom09 on 2010-05-10
Hello everybody,

I finally managed to build some installable binary packages of the VIA driver for U10.04. I also (hopefully) fixed/found a workaround for the DPMS and EXA bug I encountered with xserver 1.7.
So, here are two packages in the zip file:
chrome9-drm: contains the kernel module, requires the 'dkms' package. The module should now be rebuilt automatically when a kernel update is installed. I did not test this, because there have not been any kernel updates yet...
xserver-xorg-video-chrome9: contains the X.Org DDX driver, fixed and compiled for Ubuntu 10.04. It does, however, not contain the 3D driver, you'll have to install it manually (see README in /usr/share/doc/xserver-xorg-video-chrome9).
You can install both packages as root or via 'sudo' from console (CTRL-ALT-F1):
'sudo dpkg install <package_file_name>'. You should shut down the X-Server first by 'sudo service gdm stop' and restart it afterwards by 'sudo service gdm start'.
Some final remarks:
- Although I did some tests with it, I would not consider this driver a "stable", so use it at your own risk!
- EXA acceleration is fixed in this release, but ssssllllllooooowww...use XAA instead (Option "AccelMethod" "XAA" in xorg.conf).
- There is a sample xorg.conf file for the NC20 in /etc/X11/xorg.conf.nc20
- This is my first "published" binary package, so please be careful when testing it, I cannot guarantee for it being 100% error-free...

Have fun with it
tom09

---

### Post by moldy on 2010-05-11
> **tom09 said:**
> Hello everybody,

I finally managed to build some installable binary packages of the VIA driver for U10.04. I also (hopefully) fixed/found a workaround for the DPMS and EXA bug I encountered with xserver 1.7.
So, here are two packages in the zip file:
chrome9-drm: contains the kernel module, requires the 'dkms' package. The module should now be rebuilt automatically when a kernel update is installed. I did not test this, because there have not been any kernel updates yet...
xserver-xorg-video-chrome9: contains the X.Org DDX driver, fixed and compiled for Ubuntu 10.04. It does, however, not contain the 3D driver, you'll have to install it manually (see README in /usr/share/doc/xserver-xorg-video-chrome9).
You can install both packages as root or via 'sudo' from console (CTRL-ALT-F1):
'sudo dpkg install <package_file_name>'. You should shut down the X-Server first by 'sudo service gdm stop' and restart it afterwards by 'sudo service gdm start'.
Some final remarks:
- Although I did some tests with it, I would not consider this driver a "stable", so use it at your own risk!
- EXA acceleration is fixed in this release, but ssssllllllooooowww...use XAA instead (Option "AccelMethod" "XAA" in xorg.conf).
- There is a sample xorg.conf file for the NC20 in /etc/X11/xorg.conf.nc20
- This is my first "published" binary package, so please be careful when testing it, I cannot guarantee for it being 100% error-free...

Have fun with it
tom09

Hey Tom

Thanks for all your work on this. If you get a free moment, can you please write a short note about what this is exactly and what it does? I'm sure that not-so-technical people like me would be very grateful, especially if it fixes some of the bugs with the default drivers.

Many thanks

Richard

---

### Post by ashwyn on 2010-05-13
Another thanks from me too.

I'm trying to get this working for me, just did a fresh install of lucid, and have a few problems.

First, two symlinks that you mentioned should be deleted:
4. Remove the files (symlinks) /usr/lib/libGL.so and /usr/lib/libGL.so.1
I do no have on my system, there are however files named:
/usr/lib/libGLU.so and /usr/lib/libGLU.so.1
I have not deleted these.

Second, I am guessing that this line:
[myname]# sudo ln -s /usr/lib/libGL.1 /usr/lib/libGL.so
should really read like this
[myname]# sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
to refer to one of the files deleted in the last step...
...or am I wrong?

I haven't managed to get it working yet.  Under 9.04, and 9.10, I needed to use the following xorg.conf file (attached)  I am actually using a MSI VR321 laptop, quite obscure, and uses a N3362 LCD panel, that doesn't properly report an EDID.  As far as I can tell, this was the reason that other xorg.conf files didn't work for me.

However, this configuration has ceased to work for me, providing the errors:
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(EE) VIA(0): Unknown EDID version 0
(EE) VIA(0): No valid initial configuration found
(EE) Screen(s) found, but none have a usable configuration.
(full error log attached...)

and the new xorg that you provided simple reports that no screens were found.

Still looking into things, but just thought I'd post an update to let you know where I'm at.

---

### Post by gvlists on 2010-05-13
I upgraded my Samsung NC20 to Lucid  before the release. It working OK with latest openchrome. But after the Lucid release, I did an update/upgrade the packages (sudu apt-get update/upgrade. This updated my kernel to 2.6.32-22 among other things. Now after the boot I get the black screen. I get Grub. But no splash, X or login screen. Just a blank black screen with a cursor on the left top corner. I do not get a terminal window by pressing ctrl+alt+Fx. If I remove the boot options splash/quiet from grub I get to see the text messages scrolling up which finally shows something like

Ext3-fs mounted
Begin /scripts/init-bottom 
DONE

Now the screen goes blank with a green flash once. Has anyone experienced this? There are many references to blank screen problem in Lucid. Most of them suggest using nomodeset, xforcevesa, acpi=off etc but none of these or their combinations worked for me. Not even to give a terminal window. Recovery option is also not useful. Only thing that worked for me was init=/bin/bash option in grub. This gave me rudimentary console. But it will not allow me to change files as the filesystem is read only. Could it be a problem with the display driver? Is there any other boot switch that I may try? Thanks for the help?

---

### Post by ashwyn on 2010-05-13
hi gvlists,

not sure if this will help, as I do not have a permanent black screen, but on upgrading to lucid, I did start getting a black screen when trying to ctrl-alt-fx to another tty.  This was fixed by an option in grub detailed here:
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

> 3. VGA console modes: At the moment of writing, for the console, we can only keep the resolution we set for the GRUB 2 menu. This is due by the instruction set gfxpayload=keep, that, in order to be inserted into our /boot/grub/grub.cfg configuration file we have to hardcode to the 00_header script, in this way:

/etc/grub.d/00_header excerpt :

set gfxmode=${GRUB_GFXMODE} <-- FIND THIS LINE
(as you note GRUB_GFXMODE is the variable we set before through /etc/default/grub)
set gfxpayload=keep <-- THIS IS FOR THE VGA CONSOLE!
(as you note the statement keep, obviously, keeps, what?, the resolution we set before through GRUB_GFXMODE variable set into /etc/default/grub)
insmod gfxterm
insmod ${GRUB_VIDEO_BACKEND}

setting the GRUB_GFXMODE variable near the top to 800x600, and putting in the set gfxpayload=keep worked for me to bring back my tty's, of course, after editing the file, be sure to run sudo update-grub.

---

### Post by tom09 on 2010-05-13
@moldy
[QUOTE=moldy] If you get a free moment, can you please write a short note about what this is exactly and what it does?[/QUOTE]

It is a video driver package that provides better performance on the NC20 than the openchrome driver. It is still buggy, though.

@ashwyn
[QUOTE=ashwyn]
First, two symlinks that you mentioned should be deleted:
4. Remove the files (symlinks) /usr/lib/libGL.so and /usr/lib/libGL.so.1
I do no have on my system, there are however files named:
/usr/lib/libGLU.so and /usr/lib/libGLU.so.1
I have not deleted these.
[/QUOTE]
If the symlinks do not exist, skip this step. It seems that Ubuntu keeps these under /usr/lib/mesa for some reason. I had symlinks into /usr/lib/mesa after installation so I wrote this step.

[QUOTE=ashwyn]
Second, I am guessing that this line:
[myname]# sudo ln -s /usr/lib/libGL.1 /usr/lib/libGL.so
should really read like this
[myname]# sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
to refer to one of the files deleted in the last step...
...or am I wrong?
[/QUOTE]
No, you're right, it is a stupid typo I made...sorry.

Concerning your "No screens found" problem, did you try the sample xorg.conf.nc20 file that comes with the driver (under /etc/X11)? It is written for the NC20 netbook, but maybe it works on your laptop as well.

tom09

---

### Post by ashwyn on 2010-05-13
Thanks for a speedy response!  Yes, I did try the provided nc20 xorg first off, but unfortunately no luck, slightly different error message, can't find the logs for it though.  Was more blunt about 'no devices found' or something like that.

Was wondering if there was any way of checking if the driver install went well?  via is listed as a loaded module when I run lsmod, but that's about all I know how to do...

---

### Post by gvlists on 2010-05-13
@Ashwyn,

Thanks, but I am not able to get console or X. Therefore I can not edit the files you suggested. I have xubuntu installed in another partition which installed for browsing when Lucid Lynx stopped booting. From this xubuntu console I made the modifications you suggested which I hoped should be fine. That broke my working Xubuntu partition also :(. I might be able to install it again. Any other suggestions?

---

### Post by ashwyn on 2010-05-13
That sounds horrible!

Can you tell me exactly what you edited, and in what way things are broken?

If I were you I would get a live cd or usb, of whatever distro you choose (ubuntu, puppy, etc...) and restore the files that you edited (or at least change the 800*600 to 640*480.)

If you need any help just ask...

---

### Post by tom09 on 2010-05-14
@ashwyn:
If you use xorg.conf.nc20 as your xorg.conf, you could try and remove the BusID line from the device section. If it still does not work, please add the line
```
Option "ModeDebug" "true"
```to the device sections of your own xorg.conf file and post the Xorg.0.log file. Maybe we can then find out why the driver doesn't detect your display correctly.

---

### Post by moldy on 2010-05-14
[QUOTE=tom09;9295247]@moldy


It is a video driver package that provides better performance on the NC20 than the openchrome driver. It is still buggy, though.

@tom09

Thanks mate. You and the people like you are champs. I assure you that all this work is much appreciated by those who cannot contribute but will be better off with the updates. I can't wait until it is usable. Thanks again for all your work. Moldy.

---

### Post by wasteinc on 2010-05-18
Gvlists, did you find a solution for your blank screens? I upgraded to 10.04 from 09.10 and it seems I cant even boot to recovery console, the same problem with you with the green flash.

the only keystroke that works was ctrl-alt-del that rebooted the computer

is it a xorg problem or a video driver problem?
I have a samsung nc20 here

---

### Post by tom09 on 2010-05-18
The problem with the green flash and blank console is caused by one of the framebuffer video drivers, vga16fb. Ubuntu seems to load it by default on boot, so you must tell Ubuntu not to use it. You need to change a configuration file by hand for this and you need root privileges.
1. Boot your Ubuntu or some rescue CD/DVD or whatnot, you'll need to access (mount) your installation partition.
2. Open /etc/modprobe.d/blacklist-framebuffer.conf on your installed Ubuntu in a text editor
3. Add a new line:
```
blacklist vga16fb
```OPTIONAL: Comment out (add a # at beginning) the line 
```
blacklist viafb
```
4. Save the file and exit the editor.
5. Reboot
Chances are that the normal text console will work now, but maybe you'll lose the boot splash screen...

tom09

---

### Post by Mark XIII on 2010-05-18
> **tom09 said:**
> The problem with the green flash and blank console is caused by one of the framebuffer video drivers, vga16fb. Ubuntu seems to load it by default on boot, so you must tell Ubuntu not to use it. You need to change a configuration file by hand for this and you need root privileges.
1. Boot your Ubuntu or some rescue CD/DVD or whatnot, you'll need to access (mount) your installation partition.
2. Open /etc/modprobe.d/blacklist-framebuffer.conf on your installed Ubuntu in a text editor
3. Add a new line:
```
blacklist vga16fb
```OPTIONAL: Comment out (add a # at beginning) the line 
```
blacklist viafb
```4. Save the file and exit the editor.
5. Reboot
Chances are that the normal text console will work now, but maybe you'll lose the boot splash screen...

tom09

Thanks Tom! 
Works!

I used only ```
blacklist vga16fb
```P.S. Sorry my English.
Hello from Russia :)

---

### Post by wasteinc on 2010-05-19
thanks a million Tom, it worked. Now I ll get down with the 3D acceleration :)

PS personal mental note, dont ever upgrade again on samsung nc20, there are quite many things that need fixing again :)

---

### Post by Mark XIII on 2010-05-20
A have got a problem with Wine.
Can anybody help me?  [http://ubuntuforums.org/showthread.php?p=9331981#post9331981](http://ubuntuforums.org/showthread.php?p=9331981#post9331981)

---

### Post by wasteinc on 2010-05-28
after the upgrade to 10.04 the brightness fn-keys dont work. the bad thing is that even the brightness applet doesnt work. Has anyone else the same problem, and have you found a way to fix it ? 

(oooh I hate it when I have to deal with last year's problems)

---

### Post by entsyymi on 2010-05-29
> **wasteinc said:**
> after the upgrade to 10.04 the brightness fn-keys dont work. the bad thing is that even the brightness applet doesnt work. Has anyone else the same problem, and have you found a way to fix it ? 

(oooh I hate it when I have to deal with last year's problems)

Yep having the same problem here. :( Not that it's that big of a deal, the default brightness settings are quite suitable for me. Still, would be nice to find a fix for that.

---

### Post by tom09 on 2010-05-29
Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

---

### Post by Morvie on 2010-05-29
> **tom09 said:**
> Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

This does not  work for me.
I also tried to install samsung backlight package from this source : [http://www.voria.org/forum/viewtopic.php?f=3&t=296&sid=7c3fc4e0d5cccd37574c7d9e39c387c3](http://www.voria.org/forum/viewtopic.php?f=3&t=296&sid=7c3fc4e0d5cccd37574c7d9e39c387c3)

Which seemed to work, but as soon as i work a little(on battery)  the backlight starts flicker at random.


Also is there a way to get the mic working properly ?
options snd_hda_intel position_fix=1
fixed the mic problem for me



And does anyone else has problems with the grub boot loader screen split in half ?

---

### Post by wasteinc on 2010-05-31
it worked for me... :popcorn:

thanks again, 10.04 begins to be viable again.




> **tom09 said:**
> Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

---

### Post by gang65 on 2010-05-31
Hi tom09.
Thanks for your great work!

Where I could find the source code of this driver.

I would love to try to fix the remaining bugs


> **tom09 said:**
> Hello everybody,

I finally managed to build some installable binary packages of the VIA driver for U10.04. I also (hopefully) fixed/found a workaround for the DPMS and EXA bug I encountered with xserver 1.7.
So, here are two packages in the zip file:
chrome9-drm: contains the kernel module, requires the 'dkms' package. The module should now be rebuilt automatically when a kernel update is installed. I did not test this, because there have not been any kernel updates yet...
xserver-xorg-video-chrome9: contains the X.Org DDX driver, fixed and compiled for Ubuntu 10.04. It does, however, not contain the 3D driver, you'll have to install it manually (see README in /usr/share/doc/xserver-xorg-video-chrome9).
You can install both packages as root or via 'sudo' from console (CTRL-ALT-F1):
'sudo dpkg install <package_file_name>'. You should shut down the X-Server first by 'sudo service gdm stop' and restart it afterwards by 'sudo service gdm start'.
Some final remarks:
- Although I did some tests with it, I would not consider this driver a "stable", so use it at your own risk!
- EXA acceleration is fixed in this release, but ssssllllllooooowww...use XAA instead (Option "AccelMethod" "XAA" in xorg.conf).
- There is a sample xorg.conf file for the NC20 in /etc/X11/xorg.conf.nc20
- This is my first "published" binary package, so please be careful when testing it, I cannot guarantee for it being 100% error-free...

Have fun with it
tom09

---

### Post by ibuclaw on 2010-05-31
What is the difference between the Samsung N110 and NC20 ?

Just curious... :)

---

### Post by tom09 on 2010-05-31
> **gang65 said:**
> Hi tom09.
Thanks for your great work!

Where I could find the source code of this driver.

I would love to try to fix the remaining bugs

I have attached the source code packages I used to build the packages. Happy hacking.

tom09

---

### Post by moldy on 2010-06-01
> **tom09 said:**
> Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

Thanks Tom - you are a NC20 God-send!! As someone else said, fixes like this start to make Ubuntu more viable on our netbooks. 

As far as I can tell, it's just the microphone and graphics driver that cause trouble now.

Thank you again Tom.

---

### Post by djkofi on 2010-06-01
> **tom09 said:**
> I have attached the source code packages I used to build the packages. Happy hacking.

tom09


thanx tom!!!

---

### Post by p07 on 2010-06-02
> **tom09 said:**
> I have attached the source code packages I used to build the packages. Happy hacking.

tom09

Thanks Tom09 for your work! On my NC20 it works very good: compiz works quite fine, i can see the Ubuntu upsplash at start (after configuration with "startupmanager") and i've no more gimp's bug freezing

But i've some problemes since i use your driver because my computer is now warming a lot (maybe the spanish summer is helping it too) and this causes unexpected shutdown and freezing of the computer... i hope some one can fixe it soon... or it is normal?

Good job again Tom09!

---

### Post by Mark XIII on 2010-06-03
> **tom09 said:**
> @ashwyn:
If you use xorg.conf.nc20 as your xorg.conf, you could try and remove the BusID line from the device section. If it still does not work, please add the line
```
Option "ModeDebug" "true"
```to the device sections of your own xorg.conf file and post the Xorg.0.log file. Maybe we can then find out why the driver doesn't detect your display correctly.

Lenovo S12. Black Screen. 

Kernel 2.6.32-22 generic (i686)

Option "ModeDebug" 

> (II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0) 


---

### Post by tom09 on 2010-06-04
```

(II) VIA(0): Output CRT disconnected
(II) VIA(0): Output DVI connected
(II) VIA(0): Output LCD disconnected

```This is probably not correct. Try adding this:
```

Section "Monitor"
    Identifier  "CRT"
    HorizSync   31.5 - 74
    VertRefresh 50-70
EndSection
Section "Monitor"
        Identifier      "DVI"
        Option          "Ignore"        "true"
EndSection      
Section "Monitor"
        Identifier      "LCD"
        Option          "Enable"                "true"
EndSection      

```to your xorg.conf and change the line 
```
Monitor         "Configured Monitor"
``` in the "Screen" section to
```
Monitor         "LCD"
``` You might need to uncomment the "ActiveDevice" statement in the "Device" section.

tom09

---

### Post by Mark XIII on 2010-06-04
> **tom09 said:**
> ```

(II) VIA(0): Output CRT disconnected
(II) VIA(0): Output DVI connected
(II) VIA(0): Output LCD disconnected

```This is probably not correct. Try adding this:
```

Section "Monitor"
    Identifier  "CRT"
    HorizSync   31.5 - 74
    VertRefresh 50-70
EndSection
Section "Monitor"
        Identifier      "DVI"
        Option          "Ignore"        "true"
EndSection      
Section "Monitor"
        Identifier      "LCD"
        Option          "Enable"                "true"
EndSection      

```to your xorg.conf and change the line 
```
Monitor         "Configured Monitor"
``` in the "Screen" section to
```
Monitor         "LCD"
``` You might need to uncomment the "ActiveDevice" statement in the "Device" section.

tom09

Not work.

---

### Post by tom09 on 2010-06-04
No idea then, sorry.

---

### Post by moldy on 2010-06-05
Hey Tom09

Are you able to provide an update on your work for some of us non-technical people?
- are your drivers quite usable yet (very buggy, is overheating a common problem)? 
- what additional functionality do they provide (special effects, HD playback)?
- how does one go about installing the files you have posted (can you point me to some instructions)?

Thanks in advance, Richard

---

### Post by tom09 on 2010-06-06
> **moldy said:**
> 
- are your drivers quite usable yet (very buggy, is overheating a common problem)?

The standard 2D drivers (package xserver-xorg-video-chrome9) seem to work fine for me, the 3D drivers from VIA's homepage are definitely buggy, I have some 3D related crashes now and then. I did not encounter the overheating problem so far, processor temperature stays at about 70°C under load.
> **moldy said:**
> 
- what additional functionality do they provide (special effects, HD playback)?

- some sort of "2D desktop acceleration"
- If you install the 3D driver part: hardware-accelerated OpenGL (of course...) and desktop effects (normal and "advanced")
- energy saving features concerning the LCD backlight (DPMS)
- Dual-head output (VGA and LCD simultaneously), also called XRandR sometimes
- very basic video acceleration (called XVideo), no special acceleration features for HD videos! DVD video plays fluently.
> **moldy said:**
> 
- how does one go about installing the files you have posted (can you point me to some instructions)?

You only need the binary packages from post #431. Some install instructions are also there. There is no easy "non-technical" install procedure atm, sorry. You can safely ignore all my posted source code packages (unless you'd like to start to hack on the driver yourself...)

tom09

---

### Post by moldy on 2010-06-06
Thanks Tom! I'll set about installing it and see how I go!

---

### Post by TV Stands on 2010-06-06
Apologies for my ignorance but why would you even want to run Linux as opposed to windows on the Samsung? What are the benefits?

---

### Post by chrome9 on 2010-06-07
´cause Linux is not only an OS for us. Windows works fine. I use Win 7 on my NC20. But I also use Ubuntu 9.10. It´s mostly open-source, my workflow under Linux is definetly better. It´s free (you don´t have to pay for it). I know configuring Linux on the NC20 is a pain in the a**, but trust me it´s worth it. Thanx VIA for the poor support. Many of us are dissapointed, ´cause VIA made us think, there´ll be good Linux-support.:---)I love my NC20, but I won´t buy anything from VIA in the near future. I would prefer an Intel with nvidia ION with an high resolution-display.:guitar:
PS: Thanx to all, who contribute workarounds and solutions to us!=D>

---

### Post by wasteinc on 2010-06-07
yes, nc20 is definitely a no no for a linux newbie. So please guys and occasional girls, If you want to try linux, to do it with VIA hardware.

I have my NC20 for a year now and Im pretty happy with it, but linux support would surely be  a no-go zone if all those savvy people wouldnt help. VIA's support is nearly not existent.

So definitely If you want to try linux go with nvidia and Atom

thanx again tom your help is invaluable for all of us stuck with this via hardware :)

 

> **chrome9 said:**
> ´cause Linux is not only an OS for us. Windows works fine. I use Win 7 on my NC20. But I also use Ubuntu 9.10. It´s mostly open-source, my workflow under Linux is definetly better. It´s free (you don´t have to pay for it). I know configuring Linux on the NC20 is a pain in the a**, but trust me it´s worth it. Thanx VIA for the poor support. Many of us are dissapointed, ´cause VIA made us think, there´ll be good Linux-support.:---)I love my NC20, but I won´t buy anything from VIA in the near future. I would prefer an Intel with nvidia ION with an high resolution-display.:guitar:
PS: Thanx to all, who contribute workarounds and solutions to us!=D>

---

### Post by moldy on 2010-06-18
Thanks Tom09 and P07 - I have managed to get 3D graphics working. Yes, there are a few bugs - and I get a few crashes - but it just makes the whole Ubuntu experience a bit more enjoyable.

Thanks again for your hard work Tom09 - it is really appreciated. Hopefully Via come to the party and can work out some more of the bugs in the driver.

Moldy.

---

### Post by Big_Philly on 2010-06-23
> **r4idei said:**
> Brightness buttons dont work (**** i hate this thing, it should be hardware embebbed like my old notebook) but luckily you can use applets in gnome and in kde4 (FIUU!)

Can you tell me more about these applets? I have the same problem; brightness keys don't work. I am using Ubuntu Netbook Remix

Edit: 

> **tom09 said:**
> Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it  to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

This worked. Occasionally the brightness gets turned down automatically (at least for a few minutes after startup) but at least it works. 
As for the battery life, it should be around 4 hours.

---

### Post by jarnik on 2010-06-27
I tried VIA drivers update by tom90 ([#431]("http://ubuntuforums.org/showpost.php?p=9275836&postcount=431")), but after starting X, LCD screen shows no picture (switching to console screen works fine).

Running Ubuntu Netbook Edition 10.04 on Lenovo S12 VIA Nano, VX800/VX820 Chrome 9 HC3. xorg.conf and Xorg.0.log attached.

Anyone having similar experience or a possible solution?

Thanks to everyone for putting your time and effort into fixing what VIA couldn't deliver!

---

### Post by tom09 on 2010-06-27
xorg.log and xorg.conf both look fine to me. Does adding
```
Modeline  "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
```to the "Monitor" Sections for LCD and LCD-2 change anything?

---

### Post by jarnik on 2010-06-29
Thanks, for a quick response, tom09!

Unfortunately, adding the Modeline did not change anything (log and conf attached).
But as logs show no error, LCD mode seems to be the problem (setting a correct clock frequency?).

Should I be concerned with a following message in Xorg.0.log?
```
(II) VIA(0): LCD Max Resolution 0x0, set virtual desktop!!
```

---

### Post by tom09 on 2010-06-29
Looks like X.Org did not accept the new modeline for 1280x800, according to log file it's still using the built-in one. What happens if you select another mode in the "Screen" section, i.e.
```
Modes        "1024x768"
```You can also try and rename the Modeline for "1280x800" to "1280x800_new" and change "Modes" in the "Screen" section to
```
Modes        "1280x800_new"
```Cheers
tom09

---

### Post by jarnik on 2010-06-29
Setting the Modeline 
```
	Modeline  "1280x800_new" 83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync 
```

X now seems to accept it
```
(II) VIA(0): Output LCD using initial mode 1280x800_new 
```
but still no luck, LCD screen remains blank :/

I'll try to mess with the modes a bit more. Thanks for advice, tom09!

---

### Post by Big_Philly on 2010-06-29
> **moldy said:**
> Dammit - after using Gimp in 10.04 without issue since the beta phase, all of a sudden today I am back with the system freezing solid whenever an image is opened. I have no clue as to what is different between this morning and this afternoon - but it is so frustrating to nearly get to a stage where I can do everything I need, and then in an instant I am back into Windows again because it works with my machine.

I have this same issue with GIMP: anything that I do causes the entire system to freeze. The same thing happened with Xara. Does anyone know what the problem could be? Am I missing some drivers? 
I can start up the program with no trouble, but the minute I load an image the computer just freezes.
I saw someone mention the problem had been resolved somewhere but I could not find how he / she actually did it. Any help would be awesome!

---

### Post by jarnik on 2010-06-29
For everyone interested in running Ubuntu NRE 10.04 on Lenovo S12 with VIA drivers:

I managed to compile tom09's X module for VIA with "DEBUG_PRINT" enabled to get more precise Xorg logs (attached).
I'm quite suspicious about the part
```
(II) VIA(0): pBIOSInfo: offsetWidthByQWord=640,countWidthByQWord=640
(II) VIA(0): pBIOSInfo:,frameX1=-1,frameY1=-1,HDisplay=0,VDisplay=0
(II) VIA(0): pBIOSInfo:,ActualDesktopSizeX=1280,ActualDesktopSizeY=1280
```
Is there anyone skilled enough having a clue what might be the problem?
Thanks a lot!

---

### Post by Big_Philly on 2010-07-05
> **Big_Philly said:**
> I have this same issue with GIMP: anything that I do causes the entire system to freeze. The same thing happened with Xara. Does anyone know what the problem could be? Am I missing some drivers? 
I can start up the program with no trouble, but the minute I load an image the computer just freezes.
I saw someone mention the problem had been resolved somewhere but I could not find how he / she actually did it. Any help would be awesome!

I went to a friend of mine who is good with linux; we suspect it's a driver issue. Atom-based netbooks don't appear to have this problem, so it's a VIA driver issue. 
Hopefully someone will figure something out - I know I can't :(

---

### Post by tom09 on 2010-07-05
Try adding
```
Option "AccelMethod" "EXA"
```to the "Device" Section of your xorg.conf file (file is in /etc/X11) containing the line 

```
"Driver" "openchrome"
```The freezes should go away (at least they did for me when using the openchrome driver)

tom09

---

### Post by Big_Philly on 2010-07-06
> **tom09 said:**
> Try adding
```
Option "AccelMethod" "EXA"
```to the "Device" Section of your xorg.conf file (file is in /etc/X11) containing the line 

```
"Driver" "openchrome"
```The freezes should go away (at least they did for me when using the openchrome driver)

tom09

Thanks Tom! I'll try it soon and report back in.

---

### Post by ashwyn on 2010-07-13
Hi all, unfortunately I got lazy about trying more to get the via drivers to work, as every time I got it wrong I had to boot into a liveCD and fix my xorg.conf.  So I waited a few days, and then found the blissful experience of never having m computer freeze was more attractive than being able to play video without jerkiness.

So anyway, just thought I'd explain why I never got around to posting the xorg logs.  It's just more pleasant to live without via's buggy drivers for the meanwhile.

Maybe I'll wait until (if) via ever releases a new driver, but even then I'd be suspicious of it.

---

### Post by Big_Philly on 2010-07-16
> **tom09 said:**
> Try adding
```
Option "AccelMethod" "EXA"
```to the "Device" Section of your xorg.conf file (file is in /etc/X11) containing the line 

```
"Driver" "openchrome"
```The freezes should go away (at least they did for me when using the openchrome driver)

tom09

This failed, but I may have done it wrong. What I did was add
```
Section "Device"
option "AccelMethod" "EXA"
Driver "openchrome"
EndSection
```to the xorg.conf file. Did I go wrong somewhere? The xorg.conf file was empty when I opened it with gedit. 


Edit: *facepalm*, I think I see where it went wrong... ("Driver"). Is that all, or is there more?

---

### Post by tom09 on 2010-07-16
> **Big_Philly said:**
> 
Edit: *facepalm*, I think I see where it went wrong... ("Driver"). Is that all, or is there more?

Uhh, there are two mistakes here: First, my xorg.conf code is wrong, 
```

Driver "openchrome"

```without the quotation marks around Driver is correct. Sorry for that.
Second, the keyword Option must start with a capital letter.

cheers
tom09

---

### Post by Big_Philly on 2010-07-16
Thanks again Tom, but once again it did not work. I am pretty sure the openchrome drivers are installed correctly. However, apparently my laptop still runs a driver called Mesa. 
I'll give up for now - I have alternatives to GIMP on my windows installation. Maybe one day the issue can be resolved with the click of a button :) 

Cheers,
Philly

---

### Post by tom09 on 2010-07-17
For everybody trying to use the openchrome driver on the NC20, I have attached a (hopefully) working xorg.conf file. The infamous GIMP crash should not occur with it. If there are any problems, posting the file /var/log/Xorg.0.log can be helpful.
The attached file must be decompressed and goes into /etc/X11 as xorg.conf (as ususal).

tom09

---

### Post by 0d3 on 2010-07-17
> **ashwyn said:**
> hi gvlists,

not sure if this will help, as I do not have a permanent black screen, but on upgrading to lucid, I did start getting a black screen when trying to ctrl-alt-fx to another tty.  This was fixed by an option in grub detailed here:
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

setting the GRUB_GFXMODE variable near the top to 800x600, and putting in the set gfxpayload=keep worked for me to bring back my tty's, of course, after editing the file, be sure to run sudo update-grub.


I did a clean install of Lucid and the boot splash didn't work and tty's are just corrupted graphics and therefore unusable.

I finally got everything working by modifying [these instructions]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") a bit.

First install V86D which is needed for uvesafb (which is already installed):
```
sudo apt-get install v86d
```Edit the following lines in /etc/default/grub (remove # from infront of GLUB_GFXMODE):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"

GRUB_GFXMODE=800x600
```Add this line to /etc/initramfs-tools/modules:
```
uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap
```Force use of uvesafb:
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```And finally:
```
sudo update-grub2
sudo update-initramfs -u
```Hope this helps!

---

### Post by wasteinc on 2010-07-23
I have used toms drivers with 3D for a month or so, but got fed up with the freezing and disabled the desktop effects. I now have a quite stable system, but I m not sure if 2D accelaration works.

glxgears is around 600-700 and tom said that it should be around 2100. maybe with one of those kernel updates something got stuck behind. 

 how do I check what works in my system and what not?

---

### Post by Tobis87 on 2010-07-26
> **0d3 said:**
> I did a clean install of Lucid and the boot splash didn't work and tty's are just corrupted graphics and therefore unusable.
You might want to blacklist the viafb framebuffer driver or even delete the viafb.ko inside /lib/modules.

> **0d3 said:**
> 
I finally got everything working by modifying [these instructions]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") a bit.
Is it only me or is the uvesafb driver very slow, switching to a vt and back?
You don't need to add the line to the kernel command line, adding it inside modules should be sufficant.


I would change the line to
```
uvesafb mode_option=1280x800-32 mtrr=0
```

since 1280x800 is  the native resolution of the nc20 and the mtrr will be set by xorg.


I found out that adding
```
options snd_hda_intel enable_msi=1
```

to /etc/modprobe.d/options will enable the use of MSI-X interrupts for the soundcard.


Using the latest svn (>=854) of openchrome, fullscreen xv acceleration does not crash anymore (e.g. fullscreen mplayer).
And with the appended patch it is now even possible to use gimp and wine without crashing.
Playing Diable II and Myst 3 Exile is now even possible without the crappy via driver.

**Edit:**
You can check the current mtrrs with:
```
cat /proc/mtrr
```

This is not needed with the patch, it makes the driver only more unstable.
e.g. launching OpenOffice will crash Xorg.
```
option "AccelMethod" "EXA"
```

And I also can confirm that the latest harddrive from WD, a WD5000BEKT does work inside the nc20.
You just need to go the bios, and press FN-F11, FN-F12, left.
Then go to VIA_ADV, Advanced Chipset Control, SATA GenI/II Control and set it to Gen2.

---

### Post by Tobis87 on 2010-07-28
:KSBig News!:KS

Openssl does now support partital hashing on the Via Nano with the following patch.

These patches:
-support ONESHOT Mode and partital hashing for SHA-1, SHA-224 and SHA-256
-support SHA1 acceleration of DSS (DSA with SHA-1)
-have limited backward compatibility with Eden
-work with i386 and x86_64 openssl
-also include aes support for x86_64.
-are based against 0.9.8g and 0.9.8k

Partital mode means that every application that uses openssl's sha routines will use hardware acceleration without any modification.

Openssl >= 0.9.8k has full HMAC support. Therefore only the patch against 0.9.8k also include support for HMAC(SHA1).

Huge thanks goes to Timo Teräs for hacking this stuff and even discovering that the Via Nano cannot do hardware finalization if the messages is longer than 2^29 bytes and writing a software workaround for it.

I have verified multiple hashes of files larger than 4gb and they were always correct.

Howto Openssl 0.9.8g
```
sudo apt-get build-dep openssl
apt-get source openssl
cd openssl-0.9.8g
wget -q -O - http://launchpadlibrarian.net/13798833/bug119295.patch | patch -p1
wget -q -O - http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff | patch -p1
cat ../openssl-0.9.8g-padlock.patch | patch -p1
debchange --nmu
#type if vi :wq else if nano ctrl-o ctrl-x
sudo dpkg-buildpackage
sudo dpkg -i ../openssl_0.9.8g-10.1ubuntu2.7_amd64.deb ../libssl0.9.8_0.9.8g-10.1ubuntu2.7_amd64.deb ../libssl-dev_0.9.8g-10.1ubuntu2.7_amd64.deb
```

Howto Openssl 0.9.8k
```
sudo apt-get build-dep openssl
apt-get source openssl
cd openssl-0.9.8k
wget -q -O - http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff | patch -p1
cat ../openssl-0.9.8k-padlock.patch | patch -p1
debchange --nmu
#type if vi :wq else if nano ctrl-o ctrl-x
sudo dpkg-buildpackage
sudo dpkg -i ../openssl_0.9.8k-7ubuntu9_amd64.deb ../libssl0.9.8_0.9.8k-7ubuntu9_amd64.deb ../libssl-dev_0.9.8k-7ubuntu9_amd64.deb
```

Configure Openssl to always use the Padlock engine:
[http://ubuntuforums.org/showthread.php?t=710243](http://ubuntuforums.org/showthread.php?t=710243)

---

### Post by Rainier Piqual on 2010-07-30
> **Tobis87 said:**
> :KSBig News!:KS

Openssl does now support partital hashing on the Via Nano with the following patch.

These patches:
-support ONESHOT Mode and partital hashing for SHA-1, SHA-224 and SHA-256
-support SHA1 acceleration of DSS (DSA with SHA-1)
-have limited backward compatibility with Eden
-work with i386 and x86_64 openssl
-also include aes support for x86_64.
-are based against 0.9.8g and 0.9.8k

Partital mode means that every application that uses openssl's sha routines will use hardware acceleration without any modification.

Openssl >= 0.9.8k has full HMAC support. Therefore only the patch against 0.9.8k also include support for HMAC(SHA1).

Huge thanks goes to Timo Teräs for hacking this stuff and even discovering that the Via Nano cannot do hardware finalization if the messages is longer than 2^29 bytes and writing a software workaround for it.

I have verified multiple hashes of files larger than 4gb and they were always correct.

Howto Openssl 0.9.8g
```
sudo apt-get build-dep openssl
apt-get source openssl
cd openssl-0.9.8g
wget -q -O - http://launchpadlibrarian.net/13798833/bug119295.patch | patch -p1
wget -q -O - http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff | patch -p1
cat ../openssl-0.9.8g-padlock.patch | patch -p1
debchange --nmu
#type if vi :wq else if nano ctrl-o ctrl-x
sudo dpkg-buildpackage
sudo dpkg -i ../openssl_0.9.8g-10.1ubuntu2.7_amd64.deb ../libssl0.9.8_0.9.8g-10.1ubuntu2.7_amd64.deb ../libssl-dev_0.9.8g-10.1ubuntu2.7_amd64.deb
```

Howto Openssl 0.9.8k
```
sudo apt-get build-dep openssl
apt-get source openssl
cd openssl-0.9.8k
wget -q -O - http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff | patch -p1
cat ../openssl-0.9.8k-padlock.patch | patch -p1
debchange --nmu
#type if vi :wq else if nano ctrl-o ctrl-x
sudo dpkg-buildpackage
sudo dpkg -i ../openssl_0.9.8k-7ubuntu9_amd64.deb ../libssl0.9.8_0.9.8k-7ubuntu9_amd64.deb ../libssl-dev_0.9.8k-7ubuntu9_amd64.deb
```

Configure Openssl to always use the Padlock engine:
[http://ubuntuforums.org/showthread.php?t=710243](http://ubuntuforums.org/showthread.php?t=710243)

Please explain how the average user profit from this. Just so that everyone knows what to make of this. 
Great effort!

---

### Post by Tobis87 on 2010-07-30
> **Rainier Piqual said:**
> Please explain how the average user profit from this. Just so that everyone knows what to make of this. 
Great effort!
**Background Information:**
This patch "basically" enables Openssl to move cryptographic Operations outside of the CPU. This is done by specific Opcodes which the Via Nano CPU has (xcryptecb, xcryptcbc, xcryptcfb, xcryptofb, xsha1, xsha256). These Operations are calculated inside the Cryptographic Co-Processor (Padlock) and the results are send back to the CPU. This is somehow similar to the numeric Co-Processor (x87) which early CPUs until the first Pentium needed in order to do floating point Operations in a certain time. And as Intel had a problems with the floating point hardware (Pentium FDIV bug), VIA seems to have forgotten to connect the three highest bits in 32-bit eax/ecx to the padding generator.

**Why is this useful?:**
It's useful, because it decreases the time needed for the CPU to do calculations. Especially Openvpn needs to do a lot of SHA calculations and as longer the CPU needs to compute a hash as longer it will take in total to transfer a file. It should, through it will be hardly noticeable, also increase battery life, because operations will need less clock cycles to be finished.

**Or to put it simple (Openssl 0.9.8k):**
```
$ openssl speed -engine padlock
The 'numbers' are in 1000s of bytes per second processed.
type       16 bytes     64 bytes    256 bytes   1024 bytes   8192 bytes
sha1       56420.63k   158718.23k   330674.07k   450498.63k   503601.81k
sha256     49462.70k   132886.71k   275400.24k   389601.14k   433312.67k
hmac(sha1) 15763.47k    55789.43k   165528.48k   325655.26k   454531.88k
```

**Reference:**
[http://en.wikipedia.org/wiki/Opcode](http://en.wikipedia.org/wiki/Opcode)
[http://en.wikipedia.org/wiki/Coprocessor](http://en.wikipedia.org/wiki/Coprocessor)
[http://www.via.com.tw/en/initiatives/padlock/features.jsp](http://www.via.com.tw/en/initiatives/padlock/features.jsp)
[http://www.via.com.tw/en/downloads/whitepapers/initiatives/padlock/VIAPadLockSecurityEngine.pdf](http://www.via.com.tw/en/downloads/whitepapers/initiatives/padlock/VIAPadLockSecurityEngine.pdf)
[http://en.wikipedia.org/wiki/X87](http://en.wikipedia.org/wiki/X87)
[http://en.wikipedia.org/wiki/Pentium_FDIV_bug](http://en.wikipedia.org/wiki/Pentium_FDIV_bug)
[http://www.hermann-uwe.de/blog/speed-up-linux-crypto-operations-on-the-one-a110-laptop-with-via-padlock](http://www.hermann-uwe.de/blog/speed-up-linux-crypto-operations-on-the-one-a110-laptop-with-via-padlock)

---

### Post by Uli_of on 2010-08-08
Hello all,
there is a new version of the VIA driver at the VIA Linux portal
available. [Unified GFX driver Ver 87a-55689 for Ubuntu 10.04(04Aug10) (2.1M)]("http://linux.via.com.tw/support/beginDownload.action?eleid=405&fid=705")
I tried to compile it, but got only coloured screens.
Has anyone got it running with kernel 2.6.34 and Xorg 7.5 ?
Thanks for help in advance.
Uli

---

### Post by tom09 on 2010-08-08
Yes, I've got it working. I didn't get the coloured screens, though. However, the new driver did not improve things, switching to console and back is broken here and all OpenGL games and applications started to hang for a moment every five seconds or so. VIA seems to have fixed the problems with 2D acceleration and ported the driver to Xorg 7.5, but 3D is still slow...
So I took the updated kernel driver and 3D drivers from the new package and switched back to my "hacked" driver...It works better for me. I really hope that VIA releases the source code for this driver.

tom09

---

### Post by ultix on 2010-08-12
> **Uli_of said:**
> Hello all,
there is a new version of the VIA driver at the VIA Linux portal
available. [Unified GFX driver Ver 87a-55689 for Ubuntu 10.04(04Aug10) (2.1M)]("http://linux.via.com.tw/support/beginDownload.action?eleid=405&fid=705")
I tried to compile it, but got only coloured screens.
Has anyone got it running with kernel 2.6.34 and Xorg 7.5 ?
Thanks for help in advance.
Uli

I have found simple instruction:
**Unpack an install drivers:**
**tar -zxf 5.75.32.87a-u1004-55689.tar.gz**
[B]cd 5.75.32.87a-u1004-55689
sudo ./vinstall

Compile 3D driver:
[/B] **[B]cd** VIA_Chrome9_2.6.33[/B]
[B] sudo make
sudo make install

Unload old modules and load our new module:
[/B][B]sudo depmod -a
sudo rmmod via
sudo modprobe via_chrome9

Download and unpack new xorg.conf from following archive:
[http://narod.ru/disk/18889512000/9.10.zip.html](http://narod.ru/disk/18889512000/9.10.zip.html)

Reboot
[/B]
It is works fine for me, but 3D is too slow.

---

### Post by peter27 on 2010-08-21
> **ultix said:**
> I have found simple instruction:
**Unpack an install drivers:**
**tar -zxf 5.75.32.87a-u1004-55689.tar.gz**
[B]cd 5.75.32.87a-u1004-55689
sudo ./vinstall

Compile 3D driver:
[/B] **[B]cd** VIA_Chrome9_2.6.33[/B]
[B] sudo make
sudo make install

Unload old modules and load our new module:
[/B][B]sudo depmod -a
sudo rmmod via
sudo modprobe via_chrome9

Download and unpack new xorg.conf from following archive:
[http://narod.ru/disk/18889512000/9.10.zip.html](http://narod.ru/disk/18889512000/9.10.zip.html)

Reboot
[/B]
It is works fine for me, but 3D is too slow.

I tried it. I get the red-blue-green screen.

---

### Post by ednat on 2010-08-21
didnt worked for me too.
after installing the driver (sudo vinstall) the console said i have to restart. After restart the screen leaves black, nothing happens.
Now i reinstalled ubuntu and dont know if i should try again, i HATE setup a new OS :P

edit:
system is/was ubnutu 10.4 fully patched

---

### Post by ashwyn on 2010-08-23
Thought I'd live life on the edge, got the new via drivers and installed them on my (fully updated) fresh install of 10.04, with great results.

Has not frozen, as the old drivers did frequently on the old installs, worked out of the box, with the same xorg.conf that I used to use (not the one linked to above.)

Now even compiz works!  Though with some strange behaviour.  When I shut down, it only logs me out, and then when I start up again, I have to reenable compiz manually.  Probably something easy to fix though.

It is a dream to finally be able to watch videos and things without restarting into a crash prone 9.10 install.

But I am not using an NC20, I have an MSI VR321, another computer with the same graphics card.

---

### Post by peter27 on 2010-08-23
ashwyn if you could give a detailed description of how you installed the driver it would be great :-).

Thanks in advance.

---

### Post by peter27 on 2010-08-23
As I wrote earlier I get the red-blue-screen every time when I try to install the new driver. Afterwards I can't boot into console (not even from grub). 

Instead of reinstalling ubuntu each time  I use an usb stick with ubuntu on. I boot it up and from there I mount my drive and delete the xorg.conf. Then ubuntu works again.

---

### Post by ashwyn on 2010-08-24
Sure, I'll post the parts that I think are relevant, and if you need more explanation let me know!

First I followed ultix's instructions earlier in this thread to the letter, only varying in one point, I used the xorg.conf that I have attached to this message.  Unfortunately, it is something that I found to work for my brand of laptop MSI VR321, when I couldn't get the one that other people were using for the NC20 to work.

I'm not really sure about all the stuff in it, so anyway, proceed with caution I guess...

---

### Post by ultix on 2010-08-24
> **peter27 said:**
> I tried it. I get the red-blue-green screen.

You should replace xorg.conf before reboot)

---

### Post by peter27 on 2010-08-24
Thanks a lot guys :-). It's working! compiz works fine. I followed ultix's guide  and it worked.I don't know why it did not work the first 4 times I tried.

Maybe we should build an ubuntu image for nc20 :).

---

### Post by ednat on 2010-08-27
how could i delete the old xorf.conf and insert the new one?
in the nautilus it dont work because of permission rights, and in console i dont know how to delete and copy files.
i tried with:
sudo cp '/.../.../new xorg.conf' '/etc/X11'

but it didnt work, so i did anything wrong :D

and compile the 3d driver make an error too:

> patricknet@patrick:~/via driver/5.75.32.87a-u1004-55689/VIA_Chrome9_2.6.33$ sudo make
make -C /lib/modules/2.6.32-24-generic/build M=/home/patricknet/via driver/5.75.32.87a-u1004-55689/VIA_Chrome9_2.6.33 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** Keine Regel, um »driver/5.75.32.87a-u1004-55689/VIA_Chrome9_2.6.33« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Fehler 2


anyone could help?

---

### Post by mss_omsk on 2010-09-01
1) from directory with new xorg.conf: 'sudo cp ./xorg.conf /etc/X11'
2) Possible you don't have installed kernel headers. To install: 'apt-get install linux-headers-generic'

---

### Post by ednat on 2010-09-03
Anyone know if the official driver is added to the Ubuntu 10.10 Beta?

---

### Post by youngtrotsky on 2010-09-10
> **tom09 said:**
> Fixing the brightness problem:
 1. Copy the attached file into /etc/hal/fdi/information and rename it to 99-nc20-panel.fdi
(must be done as root or via sudo)
2. Reboot the system
Brightness keys should work again.

First, apologies for being new to linux. I cannot find a 'hal' directory inside the 'etc' directory in my file system. Searching for hal brings up 2 folders, one in usr/lib, one in usr/share. I think I'm logged in as root but I don't know how to use sudo. Thought maybe someone could take 10 seconds to help me out rather than me spend another several hours trying to figure it out for myself... :( Thanks.

---

### Post by yura1 on 2010-09-12
> **ultix said:**
> I have found simple instruction:
**..**.
Thank you! I have Ubuntu for netbooks 10.04.1 2.6.32-24-generic. It works fine for me :D

But the only desktop for netbook lacks of smoothing. What should I do?

---

### Post by ultix on 2010-09-20
> **yura1 said:**
> Thank you! I have Ubuntu for netbooks 10.04.1 2.6.32-24-generic. It works fine for me :D

But the only desktop for netbook lacks of smoothing. What should I do?

Try to use desktop version without any effects (compiz etc...) :)

PS &#1050;&#1072;&#1082;-&#1090;&#1086; &#1090;&#1091;&#1090; &#1084;&#1085;&#1086;&#1075;&#1086; &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1093; &#1089;&#1090;&#1072;&#1083;&#1086;)

---

### Post by mäki on 2010-09-22
Hi,

Some weeks ago i started to get problems with sound on my Nc20, when i start up the computer sound is gone, and alsa tells me that it can't find my soundcard. When i reinstall alsa and alsa-utils it finds my soundcard and it worked fine for some days. But now again when i booted up my nc20 i got no sound. 

Anyone got any ideas or got the same problems? Running 10.04.

Edit: Alsaconf fins my soundcard, but when i try to use alsamixer i get: Cannot open mixer

---

### Post by Uli_of on 2010-09-26
Hallo Tom,
in the past I used your VIA_driver until kernelversion 2.6.33.
Now Iam using kernel 2.6.36-rc5-23 and the latest
xorg version on an Opensuse system.
Can you modify your driver to this kernelversion and xorg version?
Kind regards
Uli

---

### Post by tom09 on 2010-09-29
> **Uli_of said:**
> Hallo Tom,
in the past I used your VIA_driver until kernelversion 2.6.33.
Now Iam using kernel 2.6.36-rc5-23 and the latest
xorg version on an Opensuse system.
Can you modify your driver to this kernelversion and xorg version?
Kind regards
Uli
Updated kernel driver source attached. It works with kernels 2.6.34 - .36-rc. The xorg part from one of my earlier posts should still work, but you will have to recompile it for use with newer versions.

tom09

---

### Post by Uli_of on 2010-09-30
> **tom09 said:**
> Updated kernel driver source attached. It works with kernels 2.6.34 - .36-rc. The xorg part from one of my earlier posts should still work, but you will have to recompile it for use with newer versions.

tom09
Thanks for your help.
I will test it and report the result.
Regards
Uli

---

### Post by Rainier Piqual on 2010-09-30
Did anyone of you had a chance to test 10.10 Maverick on the NC20?

---

### Post by Uli_of on 2010-10-02
> **Uli_of said:**
> Thanks for your help.
I will test it and report the result.
Regards
Uli
Hello Tom_9,
got the driver working.

---

### Post by chrome9 on 2010-10-11
I'll try it asap. First as a live-system. Later with the via drivers. I hope that xorg hasn't changed since 10.04.
I will post my experiences with 10.10 later. I've upgraded my working-laptop right now. Everything works here (DELL Latitude E5400)

---

### Post by chrome9 on 2010-10-14
So, first impressions with the perfect 10. Very responsive, no problems so far. Next stept will be installing the 3d-drivers. So wish me good luck... Wow, no problems with the brightness keys! ;-)

---

### Post by Rainier Piqual on 2010-10-15
> **chrome9 said:**
> So, first impressions with the perfect 10. Very responsive, no problems so far. Next stept will be installing the 3d-drivers. So wish me good luck... Wow, no problems with the brightness keys! ;-)

Sounds great! Did the install go easy-peasy? Could you provide what does not work? Any improvements on functions to prior versions? Best NC20 Ubuntu so far?

---

### Post by chrome9 on 2010-10-17
I did only a run from usb-stick. I'll install it this week. But so far I think it&#347; the best Ubuntu for the NC20 so far. If the VIA-Driver works...  One thing would be great: A working Skype with the buildin microphone! So stay tuned.:popcorn:

---

### Post by Uli_of on 2010-10-18
> **chrome9 said:**
> I did only a run from usb-stick. I'll install it this week. But so far I think it&#347; the best Ubuntu for the NC20 so far. If the VIA-Driver works...  One thing would be great: A working Skype with the buildin microphone! So stay tuned.:popcorn:
If anyone can advise how to get skype with the buildinngmicrophone workig
would be great. I mostly get a lot of noise while recording and low volume.

---

### Post by Celoxocis on 2010-10-19
I just installed Ubuntu Netbook version 10.10 on my Samsung NC20.  I cant use the "Netbook Edition" Desktop its saying  ```
No required driver detected for unity.
```  Im pretty new to the whole linux with desktop and UI (been working on servers without an x-server for a about a year) and decided to give the "desktop" a try.  Anyone know what i have to do, do get the "Netbook Edition" Desktop working?

---

### Post by p07 on 2010-10-20
> **ednat said:**
> how could i delete the old xorf.conf and insert the new one?
in the nautilus it dont work because of permission rights, and in console i dont know how to delete and copy files.
i tried with:
sudo cp '/.../.../new xorg.conf' '/etc/X11'

but it didnt work, so i did anything wrong :D

and compile the 3d driver make an error too:



anyone could help?
for 3D driver: you have a space in the name of the file (ex "/via driver" instead of "/via_driver")

---

### Post by vkarazija on 2010-10-22
> **tom09 said:**
> Updated kernel driver source attached. It works with kernels 2.6.34 - .36-rc. The xorg part from one of my earlier posts should still work, but you will have to recompile it for use with newer versions.

tom09

Hi,

I am trying to get X working in Ubuntu 10.10 on VIA Pico-ITX board P820-12L that has the same chipset VX855 but cannot figure it out what driver should I use.

I red whole topic about this I find it very usefull but also confusing.....do I use openchrome driver or via_chrome9 driver to get X working on Ubuntu 10.10 ....

I see tom09 that you are quite an expert so if you will be so kind to explain what source driver should I use to try to compile against 2.6.35-22 kernel that is default in Ubuntu 10.10?

Any help would be appreciated....
regards, Vladimir

---

### Post by tom09 on 2010-10-22
The driver source from post #510 (you already found it, I suppose...) should be fine for U10.10. But you have to compile it for yourself, I don't have any U10.10 installable binary package ready yet. You will only need this kernel driver if you intend to use the VIA Xorg driver. It is not needed for the openchrome Xorg driver.
I didn't do the update to U10.10 yet, so I cannot tell whether the Xorg driver available at linux.via.com.tw for U10.04 works for you. You will at least need to replace the kernel driver in that package with the one mentioned above.
So, to answer your question which driver to use: Try the openchrome driver, if you don't need desktop effects or 3D/Video playback acceleration. If you feel adventurous, try VIA's driver but be prepared for any kind of problems.

I'll look into U10.10 for updated driver packages as soon as I have some free time...

tom09

---

### Post by vkarazija on 2010-10-22
Wierd stuff....

I tried several approaches....

1. Tried to install driver from 10.04 ---> NO SUCCESS
2. Tried install from svn openchrome  ---> NO SUCCESS
3. Tried to install  xf86-video-chrome9-86a.50290.tar.bz2 + chrome9_drm-87a-55690.tar.gz          ---> SUCCESS

I have changed Driver to "via" in xorg.conf and it works, but the picture flickers....not to much but has some interference that I cannot figure why.
I tried HDMI, and it works without the problem :)

I am attaching the xorg.conf file.

thnx for the help...

V.

---

### Post by roizcorp on 2010-10-27
> **vkarazija said:**
> Wierd stuff....

I tried several approaches....

1. Tried to install driver from 10.04 ---> NO SUCCESS
2. Tried install from svn openchrome  ---> NO SUCCESS
3. Tried to install  xf86-video-chrome9-86a.50290.tar.bz2 + chrome9_drm-87a-55690.tar.gz          ---> SUCCESS

I have changed Driver to "via" in xorg.conf and it works, but the picture flickers....not to much but has some interference that I cannot figure why.
I tried HDMI, and it works without the problem :)

I am attaching the xorg.conf file.

thnx for the help...

V.

have you done it with acceleration? i'm breaking my balls with 10.04, still can't make the vx855 show hd fluenlty,
any advice?

---

### Post by yura1 on 2010-11-02
> **tom09 said:**
> I'll look into U10.10 for updated driver packages as soon as I have some free time...

Hello, tom09! I've tried Ubuntu 10.10 on Samsung NC20. It works fine except 3D  driver. I used post #494 procedure. After rebooting I'd got Xorg crashed  with error:

```
[    14.856] (II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
[    14.856] dlopen: /usr/lib/xorg/modules/drivers/via_drv.so: undefined symbol: miEmptyData
[    14.856] (EE) Failed to load /usr/lib/xorg/modules/drivers/via_drv.so
[    14.856] (II) UnloadModule: "via"
[    14.856] (EE) Failed to load module "via" (loader failed, 7)
[    14.856] (EE) No drivers available.
[    14.856] 

```
Full log attached.

May be it caused by switching to xorg 1.9.0. I found similar problem with legacy nvidia driver: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

---

### Post by yura1 on 2010-11-02
> **yura1 said:**
> I've tried Ubuntu 10.10 on Samsung NC20. It works fine[]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974")

Oh, it means even Skype works fine :)

---

### Post by eundas on 2010-11-02
I did a fresh install of Ubuntu 10.10. It works fine except:

- Gimp freezes the computer anytime I want to open an image (it loads fine, but then, when the image is opened and I move th mouse, it freezes).

- The webcam in Cheese looks superzoomed, I mean, instead of being able to see my face on the webcam, I just see an eye, an ear, but it is impossible to see the whole face unless I stand far away from the computer (which is not ideal to chat...).

I haven't tested the mic yet.

Any ideas about how to solve the problems I detected?

Eduardo

---

### Post by eundas on 2010-11-02
Ah, I forgot to mention that when using Cheese or mplayer (the console-based version) the video is on top of everything. If I want to open a menu on the window border, the menu becomes hidden by the video. 

Eduardo

---

### Post by tom09 on 2010-11-02
Hi all,

I have updated the Xorg+kernel drivers to work with U10.10. As before, unpack the attached zip archive and install the two .deb packages with
```
dpkg -i <package file name>
```A few notes on the drivers:
1. These drivers are for U10.10 *only* and won't work with earlier versions of Ubuntu.
2. People upgrading from U10.04 should uninstall older versions of this driver.
3. 3D acceleration (OpenGL) will NOT work correctly in U10.10. I cannot do anything about that atm, VIA needs to release an updated 3D driver for maverick first.

I hope they'll work for you. If not, just come back here and I'll try to help.
tom09


Edit: Uploaded a new version of the Xorg driver, which contains a fix for the "GIMP freeze" bug.

---

### Post by eundas on 2010-11-02
Wow, the new drivers did the trick! Thanks tom09 :-)

Eduardo

---

### Post by Vincey37 on 2010-11-02
It works!  Thanks tom09!!

---

### Post by himtosh on 2010-11-03
Has anyone could get it work on lenovo s12?

---

### Post by eundas on 2010-11-03
Hmmm... I spoke too soon. Regarding graphics, everything is fine except gimp, which still freezes the whole system whenever I start it. Is this a driver problem or a gimp bug?

Also, just after the fresh install, the wireless card was working fine; I was even able to use Transmission over the wireless card the whole day with no issues. Then I applied the latest ubuntu updates and guess what... now the wifi connection is dropped randomly when I fire up Transmission. This was an old problem and one of the main reasons I had for doing a fresh install of ubuntu... Any ideas? :-/

Eduardo

---

### Post by tom09 on 2010-11-03
> 
Hmmm... I spoke too soon. Regarding graphics, everything is fine except  gimp, which still freezes the whole system whenever I start it. Is this a  driver problem or a gimp bug?
Driver bug. As a quick workaround, change "AccelMethod" from "XAA" to "EXA" in /etc/X11/xorg.conf. I'll fix the driver as soon as I can.

tom09

Edit: Driver package in post #529 updated.

---

### Post by eundas on 2010-11-04
Thanks a lot! This fixed the gimp issue.

Eduardo

---

### Post by aramiss on 2010-11-05
I have installed with no errors [via_chrome9_drv_u1010_v2.zip]("http://translate.googleusercontent.com/translate_c?hl=en&sl=ru&u=http://ubuntuforums.org/attachment.php%3Fattachmentid%3D174559%26d%3D1288896702&prev=/search%3Fq%3Dlenovo%2Bs12%2Bchrome9%2Bubuntu%26hl%3Den%26rlz%3D1B5_____enUS335US335&rurl=translate.google.com&usg=ALkJrhiotokm7q6JglbW_ltI7qPaqAjmxA") but nothing happened. What can I do more. I have the 10.10 version installed.

---

### Post by tom09 on 2010-11-05
Update your /etc/X11/xorg.conf to use the VIA driver. Use /etc/X11/xorg.conf.nc20 as an example.

---

### Post by aramiss on 2010-11-05
Where can i find the xorg.conf.nc20 file? I have attached my xorg.conf if it makes any help(just installed openchrome with no use either)

---

### Post by tom09 on 2010-11-05
> **aramiss said:**
> Where can i find the xorg.conf.nc20 file?

/etc/X11/xorg.conf.nc20

Remove the line 
```
BusID       "PCI:00:01:0"
```if you don't have a NC20 netbook.

---

### Post by Maltizzle on 2010-11-05
hey, can i use the old instructions in post #493, or is there another way to install the driver?

can someone post a simple step-by-step plan, how to get the driver working?

it would be very kind of you, because i'm still new to the ubuntu-world :)


greetings

---

### Post by aramiss on 2010-11-05
I don't have a NC20, but neither can i find /etc/X11/xorg.conf.nc20

Anyway, i have installed the two debs from the archive, and after that i have renamed the word "openchrome" with "via" in the Device section in xorg.conf. After reboot: compiz, the cube and other effects started to work, and my monitor was recognised too. So, this means that the drivers where installed ?:)

---

### Post by tom09 on 2010-11-05
Ok, here are some step-by-step installation instructions for driver installation on Ubuntu 10.10 *only*

1. Download the zip file from post #529 and unzip it somewhere (f.e. in your home directory)
2. open a terminal window and change into that directory ("cd ~" for home dir)
3. Install the "dkms" package from Ubuntu package repository
```
$ sudo apt-get install dkms
```4. Install the kernel driver:
```
$ sudo dpkg -i chrome9-drm_87a.55689-maverick1_all.deb
```5. Install the X.org driver:
```
$ sudo dpkg -i --force-confmiss --force-confnew xserver-xorg-video-chrome9_87a.55729-maverick1_i386.deb
```6. Update /etc/X11/xorg.conf file
For NC20 owners only:
6a. Copy the provided xorg.conf.nc20 file to xorg.conf
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo cp /etc/X11/xorg.conf.nc20 /etc/X11/xorg.conf
```For all other users:
6b. Modify /etc/X11/xorg.conf to use the via driver
Open /etc/X11/xorg.conf in a text editor
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo gedit /etc/X11/xorg.conf
```and look for a line in the section "Device" beginning with "Driver". Change it to read:
```
Driver    "via"
```and save the file. You might need to change other settings in this file depending on your hardware, but I cannot help you there (I only have a NC20)
7. Reboot Ubuntu
8. Check if it's working: Open /var/log/Xorg.0.log in a text editor. If you see several lines containing "VIA(0)", then the new driver is being used.

Some final notes:
1. The sample xorg.conf.nc20 is only installed if you add the "--force-confmiss --force-confnew" options to dpkg.
2. Although VIA marks the source code this hacked driver is based on as stable, I cannot guarantee it to be bug-free. Use with caution.

Happy installing
tom09

PS: Could someone with an Ubuntu wiki account verify these instructions and add them to the NC20 community documentation, please? So people do not have to crawl through a 500+ posts thread every time...

---

### Post by Maltizzle on 2010-11-05
thank you very much, it works fine, now.

---

### Post by Uli_of on 2010-11-06
> **tom09 said:**
> Ok, here are some step-by-step installation instructions for driver installation on Ubuntu 10.10 *only*

1. Download the zip file from post #529 and unzip it somewhere (f.e. in your home directory)
2. open a terminal window and change into that directory ("cd ~" for home dir)
3. Install the "dkms" package from Ubuntu package repository
```
$ sudo apt-get install dkms
```4. Install the kernel driver:
```
$ sudo dpkg -i chrome9-drm_87a.55689-maverick1_all.deb
```5. Install the X.org driver:
```
$ sudo dpkg -i --force-confmiss --force-confnew xserver-xorg-video-chrome9_87a.55729-maverick1_i386.deb
```6. Update /etc/X11/xorg.conf file
For NC20 owners only:
6a. Copy the provided xorg.conf.nc20 file to xorg.conf
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo cp /etc/X11/xorg.conf.nc20 /etc/X11/xorg.conf
```For all other users:
6b. Modify /etc/X11/xorg.conf to use the via driver
Open /etc/X11/xorg.conf in a text editor
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo gedit /etc/X11/xorg.conf
```and look for a line in the section "Device" beginning with "Driver". Change it to read:
```
Driver    "via"
```and save the file. You might need to change other settings in this file depending on your hardware, but I cannot help you there (I only have a NC20)
7. Reboot Ubuntu
8. Check if it's working: Open /var/log/Xorg.0.log in a text editor. If you see several lines containing "VIA(0)", then the new driver is being used.

Some final notes:
1. The sample xorg.conf.nc20 is only installed if you add the "--force-confmiss --force-confnew" options to dpkg.
2. Although VIA marks the source code this hacked driver is based on as stable, I cannot guarantee it to be bug-free. Use with caution.

Happy installing
tom09

PS: Could someone with an Ubuntu wiki account verify these instructions and add them to the NC20 community documentation, please? So people do not have to crawl through a 500+ posts thread every time...

Hello Tom09,
I aways are keen to use your work on an opensuse s sytsem.
Can you please, as a benefit for other linux user,
release your work in source code as before ?
Thanks in advance.
Uli_of

---

### Post by tom09 on 2010-11-06
Latest source code attached.

---

### Post by aramiss on 2010-11-07
Ok, so here's a short guide for those who don't have an NC20. This was tested on 2 different Intel's with via chrome9 hc igp,P4M900/VN896/CN896, ubuntu version 10.10. :

0. download and unzip the drivers from post #529
1. Fresh install of ubuntu 10.10
2. apt-get install dkms
3. dpkg -i chrome9-drm_87a.55689-maverick1_all.deb
4. check if xorg.conf DOES EXIST in /etc/X11/

comment: don't know why but alot of sistems don't have xorg.conf from the beggining of a fresh install

4a. if the file is not there, you can download the one i have attached here
4b. if the file is there, open it and add "via" at the Device Driver
5. dpkg -i xserver-xorg-video-chrome9_87a.55729-maverick1_i386.deb
6. reboot
7. drivers should be working and monitor recognised

---

### Post by Tarpoon on 2010-11-09
I followed the instructions from post 542 and everything seems to work fine.

I have plenty "VIA(0)" in the /var/log/Xorg.0.log and glxinfo tells me direct rendering is enabled.
```
glxinfo |grep rendering
direct rendering: Yes
```
However I cannot enable compiz
```
compiz
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

Did I miss anything during installation?

Also I would like to know if I can test somehow if the video acceleration works.

---

### Post by tom09 on 2010-11-09
> **Tarpoon said:**
> 
Did I miss anything during installation?

You are using U10.10, right? Did you upgrade it from U10.04? If so, please check if the files /usr/lib/libGL.so and /usr/lib/libGL.so.1 (these are symlinks) point to /usr/lib/libGL.so.1.2.via_chrome9 and that this file is present. Also keep in mind that the 3D driver (via_chrome9_dri.so) is not compatible with U10.10 and has some problems (Xorg crashes, 3D apps hang or crash,...).
> 
Also I would like to know if I can test somehow if the video acceleration works.Depends on what you mean by "video acceleration". The actual video "drawing" on your screen is accelerated by the driver (XVideo extension), but there's no hw accelerated video decoding like VDPAU or XvBA or such things...and it probably will never be supported.

cheers, tom09

---

### Post by ultix on 2010-11-11
The incredible thing :)
I have frequent wi-fi disconnection when chromium browser is opened.
Does anyone have any similar issue? Any solution?

---

### Post by HansHansen on 2010-11-11
Hello there,

I am trying to get the via driver working on my Ideapad S12 for a while now. It installs fine, but after i set the driver up with the xorg.conf I can only get a working external monitor, the internal never works. I tried to disable RandR but this doesn't help. RandR identifies the internal monitor but can't activate it anyway. I hope someone got an idea how to get this fixed because this seems to be the only thread about via graphics drivers on the whole internet.

Thanks in advance!

---

### Post by lepetit on 2010-11-11
HI 

des fois qu'une personne parlerai français 
j'aimerai savoir au final comment ça se passe, si tout fonctionne bien sur ce laptop a base de via nano

acceleration 3d ? compiz ? 
acceleration video ? 
bug ? 

thanks

---

### Post by Maltizzle on 2010-11-19
> **tom09 said:**
> You are using U10.10, right? Did you upgrade it from U10.04? If so, please check if the files /usr/lib/libGL.so and /usr/lib/libGL.so.1 (these are symlinks) point to /usr/libGL.so.1.2.via_chrome9 and that this file is present. Also keep in mind that the 3D driver (via_chrome9_dri.so) is not compatible with U10.10 and has some problems (Xorg crashes, 3D apps hang or crash,...).
Depends on what you mean by "video acceleration". The actual video "drawing" on your screen is accelerated by the driver (XVideo extension), but there's no hw accelerated video decoding like VDPAU or XvBA or such things...and it probably will never be supported.

cheers, tom09


if the file /usr/libGL.so.1.2.via_chrome9 doesn't exist, what should i do?

---

### Post by tom09 on 2010-11-19
Whoops, typo, should have been /usr/**lib**/libGL.so.1.2.via_chrome9.
libGL.so.1.2.via_chrome9 is in the driver package available on linux.via.com.tw.

---

### Post by Maltizzle on 2010-11-19
okay, i neither have /usr/lib/libGL.so or /usr/lib/libGL.so.1 
or /usr/lib/libGL.so.1.2.via_chrome9

what to do?

download the libGl.so.1.2.via_chrome9 into url/lib, then copy it and save it as libGL.so, or am i getting it totally wrong?


oh,1st problem:
downloaded libGL.so.1.2.via_chrome9, but can't copy it in /usr/lib...

---

### Post by Crackerjack79 on 2010-11-21
Hey Guys,

i also would like to use the window effects with my NC20. The "installation " of the VIA driver worked fine. But there are still no window effects accessable. :-(

---

### Post by Uli_of on 2010-11-22
> **tom09 said:**
> Whoops, typo, should have been /usr/**lib**/libGL.so.1.2.via_chrome9.
libGL.so.1.2.via_chrome9 is in the driver package available on linux.via.com.tw.
 
 
Hello Tom09,
again I am ahead,
can you tell where to look into the via module source  to adjust the kernel version
from 2.6.36 to 2.6.37 ?

---

### Post by tom09 on 2010-11-22
> **Uli_of said:**
> 
can you tell where to look into the via module source  to adjust the kernel version
from 2.6.36 to 2.6.37 ?


Edit via_chrome9_drv.c:
Comment out the two lines beginning with
.get_map_ofs = ...
.get_reg_ofs = ...
(around line 273), save and recompile. Works for me.

Ok, now for the 3D drivers and desktop effects:
There are no VIA 3D drivers for U10.10 and the ones for U10.04 are partly incompatible. I encountered some strange behaviour while using them including complete system freezes, crashes when starting a 3D application and "hanging" of apps every few seconds. So I do not recommend using the 3D drivers on U10.10. 
If you are really,really sure you want to try this, here are some instructions on how to install the necessary files. BUT: 
- You need some experience with linux console commands. 
- You can seriously screw up your system by doing this.
- You have been warned.

Installing the 3D driver (This must be done as root or via sudo):
1. Get the binary driver package for Ubuntu 10.04 (VX800) from linux.via.com.tw and unpack it somewhere. Look for the files via_chrome9_dri.so and libGL.so.1.2.via_chrome9 and remember where they are.
2. Log out from Ubuntu, switch to console (Ctrl+Alt+F1), log in and stop the
   GUI: [myname]# sudo service gdm stop
3. Copy the file 'via_chrome9_dri.so to /usr/lib/dri
4. Remove the files (symlinks) /usr/lib/libGL.so and /usr/lib/libGL.so.1
5. copy the file libGL.so.1.2.via_chrome9 from the driver package into /usr/lib
6. Create the symlinks for libGL.so and libGL.so.1:
    [myname]# sudo ln -s /usr/lib/libGL.so.1.2.via_chrome9 /usr/lib/libGL.so.1
    [myname]# sudo ln -s /usr/lib/libGL.1 /usr/lib/libGL.so
7. Check that the kernel module is loaded properly
8. restart the GUI: [myname]# sudo service gdm start

Good luck
tom09

---

### Post by Crackerjack79 on 2010-11-24
> there's no hw accelerated video decodingHi again!

Does this statement mean, that there probably never will be a hardware accleration for the Samsung NC20?:icon_frown:

@tom09

Thanks for the above mentionend instructions!!! :)

Can you propose some other  "manual" workaround for 10.10 to get  at least the 3D effects working without the possibility of screwing the whole system? Maybe by using Ndiswrapper or sth.???

---

### Post by Uli_of on 2010-11-24
> **tom09 said:**
> Edit via_chrome9_drv.c:
Comment out the two lines beginning with
.get_map_ofs = ...
.get_reg_ofs = ...
(around line 273), save and recompile. Works for me.

Ok, now for the 3D drivers and desktop effects:
There are no VIA 3D drivers for U10.10 and the ones for U10.04 are partly incompatible. I encountered some strange behaviour while using them including complete system freezes, crashes when starting a 3D application and "hanging" of apps every few seconds. So I do not recommend using the 3D drivers on U10.10. 
If you are really,really sure you want to try this, here are some instructions on how to install the necessary files. BUT: 
- You need some experience with linux console commands. 
- You can seriously screw up your system by doing this.
- You have been warned.

Installing the 3D driver (This must be done as root or via sudo):
1. Get the binary driver package for Ubuntu 10.04 (VX800) from linux.via.com.tw and unpack it somewhere. Look for the files via_chrome9_dri.so and libGL.so.1.2.via_chrome9 and remember where they are.
2. Log out from Ubuntu, switch to console (Ctrl+Alt+F1), log in and stop the
   GUI: [myname]# sudo service gdm stop
3. Copy the file 'via_chrome9_dri.so to /usr/lib/dri
4. Remove the files (symlinks) /usr/lib/libGL.so and /usr/lib/libGL.so.1
5. copy the file libGL.so.1.2.via_chrome9 from the driver package into /usr/lib
6. Create the symlinks for libGL.so and libGL.so.1:
    [myname]# sudo ln -s /usr/lib/libGL.so.1.2.via_chrome9 /usr/lib/libGL.so.1
    [myname]# sudo ln -s /usr/lib/libGL.1 /usr/lib/libGL.so
7. Check that the kernel module is loaded properly
8. restart the GUI: [myname]# sudo service gdm start

Good luck
tom09
Thanks Tom09,
it workes for me.
Regards
Uli

---

### Post by tom09 on 2010-11-26
> **Crackerjack79 said:**
> 
Can you propose some other  "manual" workaround for 10.10 to get  at least the 3D effects working without the possibility of screwing the whole system? Maybe by using Ndiswrapper or sth.???

Sorry, but no, I can't. As long as VIA doesn't update the 3D driver there is no clean and proper way of getting 3D on U10.10.

---

### Post by Throne777 on 2010-11-27
> **Celoxocis said:**
> I just installed Ubuntu Netbook version 10.10 on my Samsung NC20.  I cant use the "Netbook Edition" Desktop its saying  ```
No required driver detected for unity.
```  Im pretty new to the whole linux with desktop and UI (been working on servers without an x-server for a about a year) and decided to give the "desktop" a try.  Anyone know what i have to do, do get the "Netbook Edition" Desktop working?

Same problem here. Fresh install and it doesn't work. Help?

---

### Post by Zephael on 2010-11-28
Thank you Tom09! 
 
Notebook: Fujitsu Amilo LI 1705
 
Downloaded drivers from #[**[COLOR=#000000]529[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10062021&postcount=529") 
generated xorg.conf file (recovery mode root console: "X -configure")
followed instructions in #[**[COLOR=#000000]542[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10077432&postcount=542") 
replaced symlink #[**[COLOR=#000000]557[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=10149610&postcount=557") 
 
glxgears give me 215-227 FPS for normal screen, and 12-13 FPS for fullscreen.
 
2D video playback works fine (~10-15% CPU use instead of openchrome ~70%)
 
How can I test advanced 3D features? I tried to enable compiz with fusionicon but no luck. But it's not so important for me...
 
I requested also an Ubuntu 10.10 driver from viaarena. Maybe they will compile one.

---

### Post by seimonas on 2010-12-01
Hello guys.
I have got Samsung nc20 with ubuntu 10.10
just installed chrome drivers and it works great.
But there is one problem about Adobe flash player.
like example on youtube i cant watch anything on fullscreen it's freezing...
any solutions ?

---

### Post by jarnik on 2010-12-02
Anyone with **Lenovo S12 (VIA Nano, VX800 GPU)** on Ubuntu **10.04** having luck with official and/or tom09's mod drivers? Would you care to share your xorg.conf? All I'm getting is a blank screen.

---

### Post by himtosh on 2010-12-02
> **jarnik said:**
> Anyone with **Lenovo S12 (VIA Nano, VX800 GPU)** on Ubuntu **10.04** having luck with official and/or tom09's mod drivers? Would you care to share your xorg.conf? All I'm getting is a blank screen.

I had success just with external monitor.
Internal LCD worked only with old driver for Ubuntu 9.10, but I can't use it for 10.10, because it incompatable with new kernel and xorg.
I'll be glad to get any useful information.

---

### Post by jarnik on 2010-12-02
Thanks, himtosh, it seems to be the case :/

I managed to get the official drivers working (5.75.32.87a-u1004-55689), but only without RandR.
Now I'm getting 260+FPS with glxgears (135+ with openchrome), also some bug from openchrome are gone: screen doesn't get stuck while switching videos from fullscreen, videos can be overlayed with window menus. Which is fine for me, rebooting after every quicker switch from fullscreen was really annoying.

The downside is a bit jaggy netbook-launcher screen - there seems to be a problem with alpha channel. Screenshots (openchrome and via, both without RandR) and xorg.conf (for via) attached.
OpenGL apps also seem to misbehave (attached Celestia screenshot - blue orb is supposed to be covered with a texture).

---

### Post by zz887878zz on 2010-12-03
Hi guys~
Anybody succeeded in compiling and installing this on Natty (2.6.37-7 kernel) ?
I downloaded from             #[**545 **]("http://ubuntuforums.org/showpost.php?p=10080999&postcount=545")and followed instructions from                            #[**557**]("http://ubuntuforums.org/showpost.php?p=10149610&postcount=557")  and                            #[**542**]("http://ubuntuforums.org/showpost.php?p=10077432&postcount=542")                      
but encountered buld error.

make.log attached, can anybody help ?

---

### Post by himtosh on 2010-12-03
> **jarnik said:**
> Thanks, himtosh, it seems to be the case :/

I managed to get the official drivers working (5.75.32.87a-u1004-55689), but only without RandR.
Now I'm getting 260+FPS with glxgears (135+ with openchrome), also some bug from openchrome are gone: screen doesn't get stuck while switching videos from fullscreen, videos can be overlayed with window menus. Which is fine for me, rebooting after every quicker switch from fullscreen was really annoying.

The downside is a bit jaggy netbook-launcher screen - there seems to be a problem with alpha channel. Screenshots (openchrome and via, both without RandR) and xorg.conf (for via) attached.
OpenGL apps also seem to misbehave (attached Celestia screenshot - blue orb is supposed to be covered with a texture).

I tried to use official drivers + your xorg.conf, it didn't work (maybe it incompatable with new kernel or xorg). 

I could get it work with tom09's patched drivers + your xorg.conf, but all blinks like CRT at 60Hz. Xorg.0.log attached.

---

### Post by Zephael on 2010-12-15
Hello!
 
I'll post it here, maybe someone will find it usefull.
 
I asked for CN896+VT8251 (VN896) via driver for Amilo 1705 Ubuntu 10.10 from viaarena support.
I've got this message:
 
 
Since the official driver package is not available yet, I would like to support our dear users by email.
For Ubuntu 10.10 on CN896, attached file is the driver that I used on the HP2133. You can have a try if you like.
Please be informed that the attached driver is built based on the following procedure:
1. Download the X driver source from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729](http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729).
2. Download the latest GFX driver package from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728](http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728).
3. Rebuild the X driver source
4. Replace the X driver in the driver packaged downloaded at step 2.
5. Install the driver from the driver package integrated in step 4.
6. If you are using external monitor, such as LCD monitor or CRT, reboot
7. If you are using Laptop with internal LCD panel, you need to follow the xorg.conf tuning document in the driver package to adjust the /etc/X11/xorg.conf.
 
 
 
Attached file name is: 5.75.32.87a-u1010-55689.tar.bz2
I split-ed it for smaller files, and renamed the splited files to bz2.
(Sorry for complications)
 
Use: [FONT=Courier New]cat *.bz2* | (cd path-to-destination; tar jxv)[/FONT]

[FONT=Courier New]Used attached driver, and ./vinstaller.[/FONT]
[FONT=Courier New]Replaced Driver "openchrome" with Driver "via" in xorg.conf.[/FONT]

[FONT=Courier New]After this, I needed to tweak my screen resolution, because the auto recognition didn't work.[/FONT]

[FONT=Courier New]Used a "modeline" parameter in xorg.conf, and it's working now! [/FONT]

[FONT=Courier New]I get ~940 FPS from glxgears in standard window, and ~84 FPS in full screen. Compiz works.[/FONT]

[FONT=Courier New]Best regards![/FONT]

---

### Post by Maltizzle on 2010-12-17
step by step, copy paste, tutorial, pleeeease!!

---

### Post by teeedubb on 2010-12-19
> **Zephael said:**
> Hello!
 
I'll post it here, maybe someone will find it usefull.
 
I asked for CN896+VT8251 (VN896) via driver for Amilo 1705 Ubuntu 10.10 from viaarena support.
I've got this message:
 
 
Since the official driver package is not available yet, I would like to support our dear users by email.
For Ubuntu 10.10 on CN896, attached file is the driver that I used on the HP2133. You can have a try if you like.
Please be informed that the attached driver is built based on the following procedure:
1. Download the X driver source from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729](http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729).
2. Download the latest GFX driver package from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728](http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728).
3. Rebuild the X driver source
4. Replace the X driver in the driver packaged downloaded at step 2.
5. Install the driver from the driver package integrated in step 4.
6. If you are using external monitor, such as LCD monitor or CRT, reboot
7. If you are using Laptop with internal LCD panel, you need to follow the xorg.conf tuning document in the driver package to adjust the /etc/X11/xorg.conf.
 
 
 
Attached file name is: 5.75.32.87a-u1010-55689.tar.bz2
I split-ed it for smaller files, and renamed the splited files to bz2.
(Sorry for complications)
 
Use: [FONT=Courier New]cat *.bz2* | (cd path-to-destination; tar jxv)[/FONT]

[FONT=Courier New]Used attached driver, and ./vinstaller.[/FONT]
[FONT=Courier New]Replaced Driver "openchrome" with Driver "via" in xorg.conf.[/FONT]

[FONT=Courier New]After this, I needed to tweak my screen resolution, because the auto recognition didn't work.[/FONT]

[FONT=Courier New]Used a "modeline" parameter in xorg.conf, and it's working now! [/FONT]

[FONT=Courier New]I get ~940 FPS from glxgears in standard window, and ~84 FPS in full screen. Compiz works.[/FONT]

[FONT=Courier New]Best regards![/FONT]


Hmmmm... I was thinking about giving ubuntu a whirl on my NC20... this post has made it a done deal... the only other thing im not to sure about is the multi touch trackpad, but ill have to look into that...

---

### Post by Ant. on 2010-12-19
> **Zephael said:**
> Hello!
 
I'll post it here, maybe someone will find it usefull.
 
I asked for CN896+VT8251 (VN896) via driver for Amilo 1705 Ubuntu 10.10 from viaarena support.
I've got this message:
 
 
Since the official driver package is not available yet, I would like to support our dear users by email.
For Ubuntu 10.10 on CN896, attached file is the driver that I used on the HP2133. You can have a try if you like.
Please be informed that the attached driver is built based on the following procedure:
1. Download the X driver source from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729](http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729).
2. Download the latest GFX driver package from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728](http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728).
3. Rebuild the X driver source
4. Replace the X driver in the driver packaged downloaded at step 2.
5. Install the driver from the driver package integrated in step 4.
6. If you are using external monitor, such as LCD monitor or CRT, reboot
7. If you are using Laptop with internal LCD panel, you need to follow the xorg.conf tuning document in the driver package to adjust the /etc/X11/xorg.conf.
 
 
 
Attached file name is: 5.75.32.87a-u1010-55689.tar.bz2
I split-ed it for smaller files, and renamed the splited files to bz2.
(Sorry for complications)
 
Use: [FONT=Courier New]cat *.bz2* | (cd path-to-destination; tar jxv)[/FONT]

[FONT=Courier New]Used attached driver, and ./vinstaller.[/FONT]
[FONT=Courier New]Replaced Driver "openchrome" with Driver "via" in xorg.conf.[/FONT]

[FONT=Courier New]After this, I needed to tweak my screen resolution, because the auto recognition didn't work.[/FONT]

[FONT=Courier New]Used a "modeline" parameter in xorg.conf, and it's working now! [/FONT]

[FONT=Courier New]I get ~940 FPS from glxgears in standard window, and ~84 FPS in full screen. Compiz works.[/FONT]

[FONT=Courier New]Best regards![/FONT]

For those of us who are not the most competent with Ubuntu or linux in general...

> **Maltizzle said:**
> step by step, copy paste, tutorial, pleeeease!!

^ This. Would be very much appreciated by myself and most likely many others :)

While I have XP set up very nicely on my NC20 I'd love to have Ubuntu running on here perfectly and have stayed away from it for months because of poor graphics driver support.

---

### Post by ultix on 2010-12-19
> **Zephael said:**
> Hello!
 
I'll post it here, maybe someone will find it usefull.
 
I asked for CN896+VT8251 (VN896) via driver for Amilo 1705 Ubuntu 10.10 from viaarena support.
I've got this message:
 
 
Since the official driver package is not available yet, I would like to support our dear users by email.
For Ubuntu 10.10 on CN896, attached file is the driver that I used on the HP2133. You can have a try if you like.
Please be informed that the attached driver is built based on the following procedure:
1. Download the X driver source from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729](http://linux.via.com.tw/support/beginDownload.action?eleid=422&fid=729).
2. Download the latest GFX driver package from the link of [http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728](http://linux.via.com.tw/support/beginDownload.action?eleid=421&fid=728).
3. Rebuild the X driver source
4. Replace the X driver in the driver packaged downloaded at step 2.
5. Install the driver from the driver package integrated in step 4.
6. If you are using external monitor, such as LCD monitor or CRT, reboot
7. If you are using Laptop with internal LCD panel, you need to follow the xorg.conf tuning document in the driver package to adjust the /etc/X11/xorg.conf.
 
 
 
Attached file name is: 5.75.32.87a-u1010-55689.tar.bz2
I split-ed it for smaller files, and renamed the splited files to bz2.
(Sorry for complications)
 
Use: [FONT=Courier New]cat *.bz2* | (cd path-to-destination; tar jxv)[/FONT]

[FONT=Courier New]Used attached driver, and ./vinstaller.[/FONT]
[FONT=Courier New]Replaced Driver "openchrome" with Driver "via" in xorg.conf.[/FONT]

[FONT=Courier New]After this, I needed to tweak my screen resolution, because the auto recognition didn't work.[/FONT]

[FONT=Courier New]Used a "modeline" parameter in xorg.conf, and it's working now! [/FONT]

[FONT=Courier New]I get ~940 FPS from glxgears in standard window, and ~84 FPS in full screen. Compiz works.[/FONT]

[FONT=Courier New]Best regards![/FONT]

Many thanks! It's works!
I just install driver from your post and update xorg.conf from xorg.conf.nc20 (I have found it in this thread).
Compiz works (just Normal Effects).

---

### Post by aramiss on 2010-12-20
We are still waiting for that tutorial[-o<

---

### Post by Ant. on 2010-12-22
> **aramiss said:**
> We are still waiting for that tutorial[-o<

Shameless bump :p;)

---

### Post by wasteinc on 2010-12-31
shameless bump and happy new year :)

PS even some feedback on the new drivers will be welcome :)

---

### Post by eundas on 2011-01-03
Just adding my voice to the chorus of people asking for a tutorial... or at least some rough instructions...

---

### Post by wasteinc on 2011-01-05
> **Zephael said:**
> Hello!
 

[FONT=Courier New]I get ~940 FPS from glxgears in standard window, and ~84 FPS in full screen. Compiz works.[/FONT]

[FONT=Courier New]Best regards![/FONT]

yes even rough instruction would be great...

when he says 940 FPS, does he really mean FPSecond or does he mean the "828 frames in 5.0 seconds" that glxgears counts??


also when you use your ubuntu desktop for internet browsing and other everyday stuff, dont you find it a little bit sluggish on nc20? I mean, a fullscrean video on VLC (ubuntu) tops near 80-100% of CPU (no post processing), while in windows XP VLC it is around 50%

Xorg is also more or less constantly high (15-25%), internet browsing (no videos, no flash) consumes more or less another 40-50% of CPU even with less than a dozen windows.
 and I dont know if it is a ubuntu thing, a NC20 thing , or my installation thing...

---

### Post by meso uug on 2011-01-10
Hi everybody.
I've finally installed Ubuntu 10.04 on my NC20. Openchrome drivers works out of the box and that is good :D. I'm trying to install drivers from linux.via.com.tw [COLOR=#ff0000]Stable[/COLOR] [Unified GFX driver Ver 87a-55689 for Ubuntu 10.04(29Sep10) (3.3M)]("http://linux.via.com.tw/support/beginDownload.action?eleid=402&fid=732") and everything seems to be OK except one thing. This drivers are using only external monitor. I've tried a lot of combinations of xorg.conf file, but I've only reached "rainbow" on LCD, when LCD is flashing with different colors.
Has anybody idea how to fix this? I want to test drivers without external monitor.
Also could anybody provide me with stable working xorg.conf for openchrome driver?

P.S. I've searched whole this thread for solution but with no success. Help page is also outdated.

---

### Post by mäki on 2011-01-17
> **aramiss said:**
> We are still waiting for that tutorial[-o<

+1 . Got some problems gettin' it working :S

---

### Post by Meister17 on 2011-01-22
Thank you! I have successfully installed Ubuntu 10.10 on my HP 2133 just following your instructions. Everything is working and produces 275+ FPS in the window mode now. It is cool! Thank you once more.

---

### Post by Riley84 on 2011-01-26
Probably no use but I have a Samsung N148 Plus notebook and run Ubuntu 10.10 on it, works like a dream! No need to install anything, it just works.

---

### Post by StephJ on 2011-01-30
Thank you Tom09!

Your driver combined with the installation example has fixed my problems with Ubuntu 10.10 and my Samsung NC20 laptop!

Much kudo's!

Thanks!

Steph

---

### Post by Morvie on 2011-02-02
Hello, 
can someone please explain how to compile the  Xdriver mentioned in Step 3.
Or does this also work if I only install the via driver without recompiling anything?

Regards
Marvin

---

### Post by Morvie on 2011-02-03
OK I got the driver installed.
But i cannt get a working xorg.conf

Can someone please provide a config thast working with a NC20?

Regards
Marvin

---

### Post by okoman on 2011-02-06
Hi!

Around September I installed Ubuntu 10.10 on my NC20 and did not notice any crashes. But since December or so I am experiencing frequent crashes when copying large files or installing something. As it is mentioned on the [NC20 wiki page]("https://help.ubuntu.com/community/NC20") it seems to be a known problem.
Therefore I'm wondering if anyone has an idea what to do in order to avoid those crashes?
Unfortunately I haven't found any log entries which could give a clue.

The problem is that I'm not able to install anything in the last time because the netbook crashes. As already said this didn't use to be like that in September so maybe it has to to with a certain package update.

---

### Post by okoman on 2011-02-08
In case it might help someone else: After endless testing and resinstalling I have finally found out that the current kernel was the problem. Using 2.6.35-22 everything works just fine.

---

### Post by lepetit on 2011-02-08
avez vous testez le driver openvia sur le netbook ? 
[http://www.phoronix.com/scan.php?page=news_item&px=OTA4MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTA4MQ)

---

### Post by moldy on 2011-02-18
Hi all - for someone who is not all that tech competent - can somebody please summarise where we are at with tom09 vs zephael's drivers etc. That is, which is the most up to date method for 10.10 - and which gets the better results.

Also, for any of those that have upgraded as a result of one of these methods - can you please draft a short tutorial for all the noobs out there.

Many thanks in advance.

Moldy.

---

### Post by taidoka on 2011-02-21
Hi there,
I'm glad to tell you I managed Zephaels desription of installing the VIA driver for Linux Mint 10 / Ubuntu 10.10 (#[569]("http://ubuntuforums.org/showpost.php?p=10242822&postcount=569")[]("http://ubuntuforums.org/showpost.php?p=10242822&postcount=569"), pg. 57).
My computer is a AMILO PRO V3515, so I couldn't handle his attached xorg.conf.4HP2133. I had to configure some lines on my own.
First you have to download the files attached in his thread. Then open a Terminal and move to the folder you downloaded them. Use: cat *.bz2 | tar jxv. This command creates a new folder (5.75.32.87a-u1010-55689). Move to that folder (inside there are two more) choose the one named: 5.75.32.87a-u1010-55689 and type ./vinstall.
After that you have to reconfigure his attached xorg.conf.
In my case I had to enable both CRT and LCD screen. Insert a [Modeline]("http://wiki.ubuntuusers.de/XServer_Modelines") in both sections. In my case I used: Modeline "1280x800@60"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
Then scroll down to section "Screen" and add Modes "1280x800@60" in subsection "Display".
That's it. Compiz is working now.
Thank you Zephael.

Regards taidoka

Edit: The reason why I had to enable both, LCD and CRT was that in my BIOS both screens where enabled by default.
So if this configuration is not running, just check your BIOS and change the lines according to your needs...

---

### Post by moldy on 2011-03-04
Hi there

With Taidoka's help, I have managed to get Zephael's drivers working on the NC20 with 10.10. This is largely a duplicate of Taidoka's post, but here are the steps I followed:

1. Download each of the files attached to Zephael's post: (#[http://ubuntuforums.org/showpost.php...&postcount=569](http://ubuntuforums.org/showpost.php...&postcount=569), pg. 57).

2. Open the terminal, and move (using the "cd" command) to the folder which contains the downloaded files (e.g., "cd Downloads" - without quotation marks).

3. Type the command "cat *.bz2 | tar jxv" (without quotation marks). This compiles the 5 files, and unpacks the driver files from the archive to the current directory.

4. Type the command "cd 5.75.32.87a-u1010-55689" (without quotation marks).

5. Type the command "cd 5.75.32.87a-u1010-55689" (without quotation marks). Again.

6. Type the command "sudo ./vinstall" (without quotation marks). 

The new drivers are now installed. The xorg.conf file now needs to be updated. This may differ from computer to computer - but the following is what I had to do:

7. Type the command "sudo gedit /etc/X11/xorg.conf" (without quotation marks) to open xorg.conf in a text editor.

8. Ensure that the following sections are as follows:

[I][INDENT]Section "Monitor"
Identifier "CRT"
**Option "Enable" "true" # check these lines!**
**Modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync # check these lines!**
EndSection

Section "Monitor"
Identifier "LCD"
**Option "Enable" "true" # check these lines!**
**Modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync # check these lines!**
EndSection
...
Section "Device"
Driver "via"
[B]VendorName "VIA Tech" # check these lines!
BoardName "via" # check these lines![/B]
Identifier "Configured Video Device"
Option "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
DefaultDepth 24
SubSection "Display"
# Virtual 2000 2000
Depth 24
**Modes "1280x800@60" # check these lines!**
EndSubSection
Identifier "Default Screen"
Device "Configured Video Device"
EndSection[/INDENT][/I]

9. Reboot

But a disclaimer: I have no real idea what I'm doing. So am not really placed to offer any additional assistance if things go wrong. I have to rely on the generosity of others myself. But thought I'd post this in case it helps someone.

A big thanks from me to Taidoka for his help - and to Tom09 and Zaphael for all their work for us NC20 users.

Moldy

---

### Post by peter27 on 2011-03-05
Thank you very much Moldy and others for sharing.Compiz works now on my nc20.

Sometimes my nc20 freezes. It always happens when the fan is running max. This started  before I installed the 3d-driver. Anyone having the same issues ?

Thanks in advance.
Peter

---

### Post by Maltizzle on 2011-03-06
thank you very much.

---

### Post by lepetit on 2011-03-07
[http://dev.laptop.org/git/users/jnettlet/xf86-video-chrome/](http://dev.laptop.org/git/users/jnettlet/xf86-video-chrome/)

test this driver on your netbook
this driver is based on a via driver official

---

### Post by konigx on 2011-03-07
I am a bit lost with my Hp 2133 10.10, can someaone tell me which drivers and xorg.conf work the best?

---

### Post by MWaddams on 2011-03-08
> **konigx said:**
> I am a bit lost with my Hp 2133 10.10, can someaone tell me which drivers and xorg.conf work the best?

[http://ubuntuforums.org/showthread.php?p=10532707&highlight=2133#post10532707](http://ubuntuforums.org/showthread.php?p=10532707&highlight=2133#post10532707)

The driver from the link in my last post works fine.
I use the following xorg.conf (for 1024x600):

Section "ServerLayout"
       Identifier	"Default Layout"
       Screen		"Default Screen"
       InputDevice	"Mouse"
       InputDevice	"Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier	"Keyboard"
       Driver		"kbd"
       Option		"XkbRules"	"xorg"
       Option		"XkbModel"	"pc105"
       Option		"XkbLayout"	"cn"
EndSection

Section "InputDevice"
       Identifier	"Mouse"
       Driver		"mouse"
       Option		"CorePointer"
EndSection

Section "Monitor"
       Identifier	"CRT"
       Option	"Enable"	"true"            
EndSection

Section "Monitor"
       Identifier	"LCD"
       Option    "Enable"       "true"
        Option  "Type"          "HardWired"
        Option  "PanelSize"     "1024x600"
	Option	"PreferredMode"	"1024x600"
        Option  "DIPort"        "DFP_LOW"
EndSection	

Section "Monitor"
       Identifier	"DVI"
       Option	 "Enable"	"false"
EndSection	

Section "Monitor"
       Identifier	"TV"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"HDMI"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"CRT-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"LCD-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"DVI-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"TV-2"
       Option	  "Ignore"	"true"
EndSection

Section "Device"
	#BusID "PCI:01:00:0"
	Driver 	"via"
	VendorName  	"VIA Tech"
	BoardName   	"via"
	Identifier	"Configured Video Device"
	Option		"MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
#              Modes "1024x600"
              Depth  24
       EndSubSection
       Identifier	"Default Screen"
       Device		"Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
	Option	"Composite"			"Enable"
EndSection

---

### Post by taidoka on 2011-03-09
> **moldy said:**
> Hi there

With Taidoka's help, I have managed to get Zephael's drivers working on the NC20 with 10.10. This is largely a duplicate of Taidoka's post, but here are the steps I followed:

1. Download each of the files attached to Zephael's post: (#[http://ubuntuforums.org/showpost.php...&postcount=569](http://ubuntuforums.org/showpost.php...&postcount=569), pg. 57).

2. Open the terminal, and move (using the "cd" command) to the folder which contains the downloaded files (e.g., "cd Downloads" - without quotation marks).

3. Type the command "cat *.bz2 | tar jxv" (without quotation marks). This compiles the 5 files, and unpacks the driver files from the archive to the current directory.

4. Type the command "cd 5.75.32.87a-u1010-55689" (without quotation marks).

5. Type the command "cd 5.75.32.87a-u1010-55689" (without quotation marks). Again.

6. Type the command "sudo ./vinstall" (without quotation marks). 

The new drivers are now installed. The xorg.conf file now needs to be updated. This may differ from computer to computer - but the following is what I had to do:

7. Type the command "sudo gedit /etc/X11/xorg.conf" (without quotation marks) to open xorg.conf in a text editor.

8. Ensure that the following sections are as follows:

[I][INDENT]Section "Monitor"
Identifier "CRT"
**Option "Enable" "true" # check these lines!**
**Modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync # check these lines!**
EndSection

Section "Monitor"
Identifier "LCD"
**Option "Enable" "true" # check these lines!**
**Modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync # check these lines!**
EndSection
...
Section "Device"
Driver "via"
[B]VendorName "VIA Tech" # check these lines!
BoardName "via" # check these lines![/B]
Identifier "Configured Video Device"
Option "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
DefaultDepth 24
SubSection "Display"
# Virtual 2000 2000
Depth 24
**Modes "1280x800@60" # check these lines!**
EndSubSection
Identifier "Default Screen"
Device "Configured Video Device"
EndSection[/INDENT][/I]

9. Reboot

But a disclaimer: I have no real idea what I'm doing. So am not really placed to offer any additional assistance if things go wrong. I have to rely on the generosity of others myself. But thought I'd post this in case it helps someone.

A big thanks from me to Taidoka for his help - and to Tom09 and Zaphael for all their work for us NC20 users.

Moldy
Hi Moldy,

nice to read your lines.
I want to add that you should check your BIOS which monitor (LCD, CRT) is enabled. This monitor should be enabled ("true") as well in the xorg.conf. The other needs to be disabled ("false"). 
If both are enabled you will have to enable both in your xorg.conf.

---

### Post by peter27 on 2011-03-12
Hi guys,

My nc20 with ubuntu 10.10 freezes quite often. It happens with both via and openchrome drivers. Do you have these problems too ?

Thanks in advance.

---

### Post by wasteinc on 2011-03-26
try disabling Compiz, it helps alot usually

> **peter27 said:**
> Hi guys,

My nc20 with ubuntu 10.10 freezes quite often. It happens with both via and openchrome drivers. Do you have these problems too ?

Thanks in advance.

---

### Post by Uli_of on 2011-03-30
Hello all,
I changed my linux from 32 bit to 64 bit.
Now i am struggling with the via deriver and the openchrome driver
with my 64 bit opensuse 11.4 and the latest version of X11.
Has anyone got one of this drivers running on a 64 bit NC20 ?
Which X11 version ?
Any help is welcome.
Regards
Uli

---

### Post by tom09 on 2011-04-01
VIA finally has released an updated driver for Ubuntu 10.10. It seems to have been partly rewritten by VIA, the kernel driver contains much more code now. It also almost doubles the 3D (OpenGL) performance on my NC20. On the downside, it's broken...again. The login screen is completely garbled, the console only partly visible. I had to restart the X Server by
# service gdm restart
as root in order to get a decent image.
Is there anybody at VIA who can fix this driver *without* breaking at least two other things at the same time? I really don't want to fix this code again and again every six months...

tom09

Edit: O.K. found the reason for the distorted login screen, now I need to find out how to fix it...

---

### Post by the waiter on 2011-04-02
Hello everyone

After some days of struggling I have to put some questions here but at first some info:
My PC: Lenovo S12 Ideapad
My OS: Bodhi Linux
My problem: VGA VIA of course

I can see, some of you succeded in installing VIA driver. I am now on Openchrome driver with modificated xorg.conf and I got cca 900fps instead of 500 without xorg.conf and working Wine. Its great but I have to forget fluent Fullscreen video on Youtube etc. But I saw someone got more than 1700fps with proprietary driver with "the easy way" of installation. I did it exactly according to the manual and my screen stopped black. So I wanted to try "hard way" but I stuck in these lines after sudo ./vinstall:
make -C /lib/modules/2.6.35-28-generic/build M=/home/stefan/5.75.32.87a-u1004-55689/5.75.32.87a-u1004-55689/VIA_Chrome9 modules
make: *** /lib/modules/2.6.35-28-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2

I can add info about kernel : 2.6.35.28
What to do now? What will create build directory? I am new on this platform...

Thanx for quick reply

---

### Post by Uli_of on 2011-04-03
> **tom09 said:**
> VIA finally has released an updated driver for Ubuntu 10.10. It seems to have been partly rewritten by VIA, the kernel driver contains much more code now. It also almost doubles the 3D (OpenGL) performance on my NC20. On the downside, it's broken...again. The login screen is completely garbled, the console only partly visible. I had to restart the X Server by
# service gdm restart
as root in order to get a decent image.
Is there anybody at VIA who can fix this driver *without* breaking at least two other things at the same time? I really don't want to fix this code again and again every six months...

tom09

Edit: O.K. found the reason for the distorted login screen, now I need to find out how to fix it...
Hello Tom09,
which kernel version did you use for compiling,
32 or 64 bit ?
I could not compile it with 2.6.38-4-default.
Can you, as before, release your modified version to all of us?
Cant believe the doubled fps so far.
Thanks in advance
Uli

---

### Post by tom09 on 2011-04-03
> **Uli_of said:**
> Hello Tom09,
which kernel version did you use for compiling,
32 or 64 bit ?
I could not compile it with 2.6.38-4-default.
Can you, as before, release your modified version to all of us?
Cant believe the doubled fps so far.
Thanks in advance
Uli
I'm using a 32bit system, as there are no OpenGL drivers for 64bit from VIA. The new driver that VIA released a couple of days ago is for kernel 2.6.35 only (the stock kernel for U10.10). It does *not* compile on 2.6.38, porting it is not as easy as it has been with the older releases, the kernel driver is far more complex now.
As for the X.Org driver part: AFAICS it's broken in several ways on my NC20 and I have the suspicion that VIA only develops this driver for its OEM systems and mainboards, not for anything beyond that (i.e. notebooks and netbooks).
I have some ideas on how to get this blob working on newer kernel versions, but I'm not finished yet. Please be patient.
In the meantime, it could be helpful if anybody running U10.10 with a stock kernel (2.6.35) could test the new driver from the VIA homepage (Select Ubuntu 10.10 and VX900) and report any problems, crashes, weirdness that occur. I'll try and collect the bugs you find and hopefully fix them. Thanks in advance.

tom09

---

### Post by the waiter on 2011-04-07
Good news (maybe not only for Lenovo S12 users)

After 3 week of trying and sleepless nights (as a newbie in Linux) I finally got VIA chrome9 work with proprietary driver. Glxgears shows 2500fp in 5 s. 500 fp in fullscreen. I am going to make clean Bodhi Linux instalation again and try to do it once again. I have only problem with flashplayer in Youtube which crashes if I demaximize watch screen. So if it works properly after clean reinstall, I'll put that method here in forum.  

Bye

---

### Post by Uli_of on 2011-04-07
> **tom09 said:**
> I'm using a 32bit system, as there are no OpenGL drivers for 64bit from VIA. The new driver that VIA released a couple of days ago is for kernel 2.6.35 only (the stock kernel for U10.10). It does *not* compile on 2.6.38, porting it is not as easy as it has been with the older releases, the kernel driver is far more complex now.
As for the X.Org driver part: AFAICS it's broken in several ways on my NC20 and I have the suspicion that VIA only develops this driver for its OEM systems and mainboards, not for anything beyond that (i.e. notebooks and netbooks).
I have some ideas on how to get this blob working on newer kernel versions, but I'm not finished yet. Please be patient.
In the meantime, it could be helpful if anybody running U10.10 with a stock kernel (2.6.35) could test the new driver from the VIA homepage (Select Ubuntu 10.10 and VX900) and report any problems, crashes, weirdness that occur. I'll try and collect the bugs you find and hopefully fix them. Thanks in advance.
 
tom09
 Tried to install the driver on a clean 10.10 32 bit Ubuntu on a stick.
Get it installed witout problem.
After a reboot the system freezes after starting the X-server.
Regards

---

### Post by Vincey37 on 2011-04-12
> **tom09 said:**
> I'm using a 32bit system, as there are no OpenGL drivers for 64bit from VIA. The new driver that VIA released a couple of days ago is for kernel 2.6.35 only (the stock kernel for U10.10). It does *not* compile on 2.6.38, porting it is not as easy as it has been with the older releases, the kernel driver is far more complex now.
As for the X.Org driver part: AFAICS it's broken in several ways on my NC20 and I have the suspicion that VIA only develops this driver for its OEM systems and mainboards, not for anything beyond that (i.e. notebooks and netbooks).
I have some ideas on how to get this blob working on newer kernel versions, but I'm not finished yet. Please be patient.
In the meantime, it could be helpful if anybody running U10.10 with a stock kernel (2.6.35) could test the new driver from the VIA homepage (Select Ubuntu 10.10 and VX900) and report any problems, crashes, weirdness that occur. I'll try and collect the bugs you find and hopefully fix them. Thanks in advance.

tom09
The new driver does not work for me on 10.10, but the one from page 57 does.  I am using the same installation method and xorg.conf for both.  Thanks for keeping up the work on this.

---

### Post by Happy Seagull on 2011-04-13
I've added Windows 7 and Ubuntu 10.10 to XP on my NC20.  Though I'm still a newbie, Ubuntu does everything just the way I want  it, except for one big thing - it doesn't seem to recognise/open/display  USB devices such as my Samsung external DVD drive or USB pen drives.

These show up fine on my Ubuntu desktop PC, and also under Windows on my  NC20. The only USB device that works (in all three USB sockets) is my  mouse. A bit odd, as I installed Ubuntu from a USB pen drive in the  first place!

However, if I look in Device Manager or Sysinfo, they ARE recognised and  listed with the correct device name - I just can't do anything with  them. Am I missing some drivers or other software? Thanks in advance.

---

### Post by Uli_of on 2011-04-27
> **tom09 said:**
> I'm using a 32bit system, as there are no OpenGL drivers for 64bit from VIA. The new driver that VIA released a couple of days ago is for kernel 2.6.35 only (the stock kernel for U10.10). It does *not* compile on 2.6.38, porting it is not as easy as it has been with the older releases, the kernel driver is far more complex now.
As for the X.Org driver part: AFAICS it's broken in several ways on my NC20 and I have the suspicion that VIA only develops this driver for its OEM systems and mainboards, not for anything beyond that (i.e. notebooks and netbooks).
I have some ideas on how to get this blob working on newer kernel versions, but I'm not finished yet. Please be patient.
In the meantime, it could be helpful if anybody running U10.10 with a stock kernel (2.6.35) could test the new driver from the VIA homepage (Select Ubuntu 10.10 and VX900) and report any problems, crashes, weirdness that occur. I'll try and collect the bugs you find and hopefully fix them. Thanks in advance.
 
tom09
 Hello tom09,
got the new driver working with Ubuntu 10.10.
Any news about later Ubuntu beta version or later kernel versions ?
Regards
Uli

---

### Post by lepetit on 2011-04-27
anyone has tested this ? 
[http://dev.laptop.org/git/users/jnettlet/xf86-video-chrome/](http://dev.laptop.org/git/users/jnettlet/xf86-video-chrome/)

---

### Post by chrome9 on 2011-05-01
Has anyone tried 11.04 on the NC20? Is it possible to use the VIA drivers? 11.04 is incredibly fast. I upgraded my laptop i use at work (Dell Latitude e5400). LibreOffice and Firefox are starting much faster now! But I fear I'll mess up my system when upgrading to 11.04 on my NC20. [-X
I don't need 3d, I only need good video performance (youtube, flash) Has the openchrome-driver now enough performance for that?:confused:

---

### Post by Rainier Piqual on 2011-05-01
> **chrome9 said:**
> Has anyone tried 11.04 on the NC20? Is it possible to use the VIA drivers? 11.04 is incredibly fast. I upgraded my laptop i use at work (Dell Latitude e5400). LibreOffice and Firefox are starting much faster now! But I fear I'll mess up my system when upgrading to 11.04 on my NC20. [-X
I don't need 3d, I only need good video performance (youtube, flash) Has the openchrome-driver now enough performance for that?:confused:

I second that enquiry. Still running 9.10 and would like to upgrade asap.

---

### Post by mäki on 2011-05-03
> **chrome9 said:**
> Has anyone tried 11.04 on the NC20? Is it possible to use the VIA drivers? 11.04 is incredibly fast. I upgraded my laptop i use at work (Dell Latitude e5400). LibreOffice and Firefox are starting much faster now! But I fear I'll mess up my system when upgrading to 11.04 on my NC20. [-X
I don't need 3d, I only need good video performance (youtube, flash) Has the openchrome-driver now enough performance for that?:confused:


Same here, i would like to upgrade to 11.04, but i'm busy this week so i aint got time to mess around with drivers n stuff if the upgrade messes it up. So i hope if someone have upgraded that they can post and tell us others if it went well or horrible :D

---

### Post by eundas on 2011-05-06
This is just to report that I upgraded my NC20 to Ubuntu Natty and it works fine. Nothing broken until now! :-) However, I have still not bothered trying to install the new VIA drivers. I'm using the ones installed by default and the system seems to be quite usable so far.

---

### Post by Rainier Piqual on 2011-05-07
> **eundas said:**
> This is just to report that I upgraded my NC20 to Ubuntu Natty and it works fine. Nothing broken until now! :-) However, I have still not bothered trying to install the new VIA drivers. I'm using the ones installed by default and the system seems to be quite usable so far.

Thanks eundas!

Which version of Ubuntu did you run before? And what are the differences in terms of performance for instance?

Would be cool if you could expand your report a bit :)

---

### Post by eundas on 2011-05-08
I don't perceive any change in performance but I had not been using much this machine during the last months, so I'm not sure. I upgraded from 10.10, having regularly upgraded the system with each new version of Ubuntu. 

Now that I have been using the system for a couple of days I can report the following:

Audio -> Works fine.

Video -> Works fine, but no 3D acceleration. I have not attempted to install the VIA drivers.

Webcam -> Not sure whether the problem is the webcam or Cheese, but I open Cheese, I can see the camera working for some seconds, and then X restarts. 

Wireles -> Works fine. I'm using the ath5k driver and it is stable. No need to use the madwifi drivers (which were a must in previous versions of Ubuntu).

Suspend -> I didn't mean to use it but I selected this by mistake and I could see that it works. 

Login screen, grub, mounting NTFS partitions, mounting USB sticks -> No problems.

Not tested: Microphone, earphones, wired network, hibernation.

---

### Post by eundas on 2011-05-08
> **chrome9 said:**
> 
I don't need 3d, I only need good video performance (youtube, flash) Has the openchrome-driver now enough performance for that?:confused:

I have been watching several YoutTube videos and websites with Flash and I have found no problems.

---

### Post by Rainier Piqual on 2011-05-08
Much appreciated eundas! Seems that there has been a considerable improvement over past versions, so great news that you bring!

Could you confirm wether the webcam works fine with skype? 

I'm running 9.10 with openchrome and cheese does not work either, so I'd guess your difficulties are rather cheese-related.

---

### Post by eundas on 2011-05-09
Yep, Skype works fine with the webcam.

---

### Post by markosjal on 2011-05-11
I recently walked into a local variety store and got an unbelievable deal on a floor model of a VIA mm3500 based desktop system. I also have an Atom 510 system and was surprised that the performance in mint was so much worse with the VIA than the Atom. The bundled "5 minute" Windows Vista Starter that was included was useless. 

The default mint video drivers were clunky on the Via with Linux, with slow redraws, etc.

I installed this driver as explained on about page 59 , and viola, the via system now feels comparable to the atom system

I only have a few annoyances .....

Mint (splash?) logo at boot is text only. (This is the logo over black)

My favorite resolution that was available on the standard VIA driver is not available on this new driver. I tried editing xorg.conf, and no luck.

The embossed looking Mint logo over grey while the GUI loads seems to be distorted, as if formatted for 16x9 on my 4x3 display


Good news is....
Overall system speeded up,
XBMC is now usable, and it appears hardware acceleration can now be used
Many video resolutions were available by default 
Compiz 3D Cube and all other effects I tested work.

I highly recommend this on Mint 10, and wonder why it is not the default driver for this video chip in Mint, or at least available as a driver.

Mark

UPDATE______________________
Upon further use I have discovered that I can not leave XBMC in "auto" rendering or I get weird color output. I will "software" does work and I seem to get decent SD playback. Also the hardware Acceleration seems to work but I think video is choppier than with software. 

XBMC seems to freeze when exiting. I must hit the power button an invisible menu appears then I hit return and I am logged out




Still at least I have a usable XBMC install with this driver , unlike before

---

### Post by mäki on 2011-05-16
> **eundas said:**
> This is just to report that I upgraded my NC20 to Ubuntu Natty and it works fine. Nothing broken until now! :-) However, I have still not bothered trying to install the new VIA drivers. I'm using the ones installed by default and the system seems to be quite usable so far.

Same thing here, usable, but drivers for 10.10 was faster. Hope Via release some drivers for 11.04 soon.

---

### Post by Rainier Piqual on 2011-06-04
> **mäki said:**
> Same thing here, usable, but drivers for 10.10 was faster. Hope Via release some drivers for 11.04 soon.

Thanks for the feedback on this!

---

### Post by mäki on 2011-06-22
bump, anyone have any news of drivers?

---

### Post by Rainier Piqual on 2011-06-24
I've just updated to Linux Mint 11 LXDE and its running quite well so far.

However activating the camera reverts me instantly back to the login screen. Also the video driver is not too smooth with glitches every now and then.
So same experience as eundas already reported. Any help?

Keep it coming guys.

---

### Post by Uli_of on 2011-07-29
> **tom09 said:**
> I'm using a 32bit system, as there are no OpenGL drivers for 64bit from VIA. The new driver that VIA released a couple of days ago is for kernel 2.6.35 only (the stock kernel for U10.10). It does *not* compile on 2.6.38, porting it is not as easy as it has been with the older releases, the kernel driver is far more complex now.
As for the X.Org driver part: AFAICS it's broken in several ways on my NC20 and I have the suspicion that VIA only develops this driver for its OEM systems and mainboards, not for anything beyond that (i.e. notebooks and netbooks).
I have some ideas on how to get this blob working on newer kernel versions, but I'm not finished yet. Please be patient.
In the meantime, it could be helpful if anybody running U10.10 with a stock kernel (2.6.35) could test the new driver from the VIA homepage (Select Ubuntu 10.10 and VX900) and report any problems, crashes, weirdness that occur. I'll try and collect the bugs you find and hopefully fix them. Thanks in advance.

tom09

Hello Tom09,
is there any news about the
good work you are doing for the
communty.
I am on kernel 3.0.4 and still have the problem that the DRM-driver is
not compiling.
The xserver 87a.55727 does only compile with gcc45.
gcc46 gives errors for duplicate variables.
Regards
Uli

---

### Post by Blackleker on 2011-07-29
I sent an email and this has been the response

My email:
Hello Alberto Jovito:
> Hello 
> I am a somewhat unsatisfied user by dr via driver and support for linux drivers. The drivers that you find here [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) 
> do not have specified for that platform are if are for 64-bit or 32-bit ubuntu obviously I have downloaded the driver for ubuntu 10.10 to a vx800 graphics card and driver 
> are for ubuntu 32-bit and the the page is not specified and not this available the source code to compile it and so would be a solution but the real solution is to have 
> two versions of the driver for 64-bit ubuntu one and one for ubuntu 32-bit otherwise have not been able to use the driver via even because the install shows me an 
> effect Tin of tv static in these two directions [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/665463](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/665463) 
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/665460](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/665460) , There is more information about the problem I like that they solved this 
> the most rapid possible Also another thing is that they have not opened a website to report the bugs and even the Forum works please open these pages would be
> very helpful to solve the problems that cause these drivers It would be good that freed all the source code and in some way help the development of the driver 
> openchrome and table to get 3d acceleration I wait your answers 

22/03/2011 response:
 
Thank you very much for your suggestion. Currently, the bin GFX package available at linux.via.com.tw is all 32bit Ubuntu. For 64 bit driver, it's still under internal verification. And hope can be released at linux portal at about Q3 this year.
Regarding open source 3D support, the source code of the DRM ( the module which is highly dependent with 3D) is in VIA linux portal. And the graphic programer's manual has been released too. The developer should be able to base on the document we release to develop the driver.
 
Regards
=================================================
Bruce C. Chang(&#24373;&#31062;&#26126;)
VIA Technologies, Inc.
Address: 1F, 531, Chung-Cheng Road, Hsin-Tien, 231 Taipei
Tel: +886-2-22185452 Ext 7323
Mobile: +886-968343824
Fax: +886-2-22186282
Skype: Bruce.C.Chang
Email: [email]BruceChang@via.com.tw[/email]

---

### Post by tom09 on 2011-08-06
> **Uli_of said:**
> Hello Tom09,
is there any news about the
good work you are doing for the
communty.
I am on kernel 3.0.4 and still have the problem that the DRM-driver is
not compiling.
The xserver 87a.55727 does only compile with gcc45.
gcc46 gives errors for duplicate variables.
Regards
Uli

Hello Uli_of,

sorry for the late reply, I have been quite busy during the last weeks. I  looked into the latest VIA driver (v89) and (hopefully) fixed most of  the issues that occur on the NC20. I also made the driver work on U11.04  but it's slow as hell...and Unity doesn't work either (only Unity2D  does).
Packages for Ubuntu 11.04 are attached, please remove the old packages  of the driver first. If you need hw-accelerated OpenGL, the matching  files (libGL.so.1.2.via_chrome9 and via_chrome9_dri.so) are available on  linux.via.com.tw -> Ubuntu 10.10 -> VX900. I have attached the  source code as well, the kernel driver now works with linux 3.0.1.
As I intend to replace my NC20 with something newer and faster, I won't  be able to hack on the VIA drivers anymore (the new laptop definitely  won't have any VIA-made part in it!). So unfortunately this is the last  driver package from my side. There are some efforts going on to  modernize the openchrome driver, so maybe there will be a properly written  driver for modern VIA hardware in the near future.

Regards
tom09

---

### Post by mäki on 2011-08-07
> **tom09 said:**
> Hello Uli_of,

sorry for the late reply, I have been quite busy during the last weeks. I  looked into the latest VIA driver (v89) and (hopefully) fixed most of  the issues that occur on the NC20. I also made the driver work on U11.04  but it's slow as hell...and Unity doesn't work either (only Unity2D  does).
Packages for Ubuntu 11.04 are attached, please remove the old packages  of the driver first. If you need hw-accelerated OpenGL, the matching  files (libGL.so.1.2.via_chrome9 and via_chrome9_dri.so) are available on  linux.via.com.tw -> Ubuntu 10.10 -> VX900. I have attached the  source code as well, the kernel driver now works with linux 3.0.1.
As I intend to replace my NC20 with something newer and faster, I won't  be able to hack on the VIA drivers anymore (the new laptop definitely  won't have any VIA-made part in it!). So unfortunately this is the last  driver package from my side. There are some efforts going on to  modernize the openchrome driver, so maybe there will be a properly written  driver for modern VIA hardware in the near future.

Regards
tom09

Thank you tom09, the new drivers for 11.04 works much better than it have been working for me without them. 
I also bought a new notebook without any VIA-made parts. I think i'll reinstall this nc20 with long term release and just use it for surfning. It was atleast much faster than with 11.04.

---

### Post by mäki on 2011-10-16
I updated this NC20 just to see if 11.10 works, and i would say it works better than 11.04, abit slow on startup, but otherwise it's faster. Some problems with Java, but i dont think it have anything to do with the computer.

---

### Post by Rainier Piqual on 2011-10-16
> **mäki said:**
> I updated this NC20 just to see if 11.10 works, and i would say it works better than 11.04, abit slow on startup, but otherwise it's faster. Some problems with Java, but i dont think it have anything to do with the computer.

Appreciate your update Mäki! How about webcam etc any problems with specific devices?

---

### Post by chrome9 on 2011-10-18
@mäki: Are you using the 3d via drivers or the openchrome ones. I would love to update to 11.10 but only if 3d works so that I can use the gnome3-shell.

---

### Post by Rainier Piqual on 2011-10-22
Did anyone of you try out this rep:

[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

?

Any experiences doing that? Probably worth a try!

---

### Post by chrome9 on 2011-10-23
> **Rainier Piqual said:**
> Did anyone of you try out this rep:

[https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa")

?

Any experiences doing that? Probably worth a try!

I don't think it helps a lot. The only problem with the NC20 is hunting for working 3d-drivers.

---

### Post by MWaddams on 2011-10-25
> **chrome9 said:**
> I don't think it helps a lot. The only problem with the NC20 is hunting for working 3d-drivers.

At least the entry (Ubuntu 11.04) has shown up on [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
Maybe they will still deliver...

---

### Post by chrome9 on 2011-10-25
> **MWaddams said:**
> At least the entry (Ubuntu 11.04) has shown up on [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
Maybe they will still deliver...

This entry ist existing for quite a few days now, but it's only for Ubuntu 11.04. I've already upgraded to 11.10 yesterday. Openchrome works well. But I want to use Gnome 3 and Google Earth and so on. I'll try to get something running. :D

---

### Post by mäki on 2011-10-25
> **chrome9 said:**
> @mäki: Are you using the 3d via drivers or the openchrome ones. I would love to update to 11.10 but only if 3d works so that I can use the gnome3-shell.

I use the openchrome, since i only use it for webbrowsing + writing. I tried via 3d driver in 11.04, but i didnt manage to get the nc20 running smoothly, alot of problems and freezes. So i changed back to openchrome.

---

### Post by chrome9 on 2011-12-20
Knock,knock... VIA recently updated there website [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) 
Now there are drivers for 10.10 and 11.04 for 32 and 64 Bit. If I'm right you should be able to use these drivers on 11.10 too, because 11.04 and 11.10 use the same major versions of Xorg and mesa. So I'll give it a try. I'm using 11.10 on the NC20 for a while now, but it's pretty unstable. The readme'sof the drivers are promising. It seems that there was happening a lot. :KS

---

### Post by Rainier Piqual on 2011-12-20
> **chrome9 said:**
> Knock,knock... VIA recently updated there website [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) 
Now there are drivers for 10.10 and 11.04 for 32 and 64 Bit. If I'm right you should be able to use these drivers on 11.10 too, because 11.04 and 11.10 use the same major versions of Xorg and mesa. So I'll give it a try. I'm using 11.10 on the NC20 for a while now, but it's pretty unstable. The readme'sof the drivers are promising. It seems that there was happening a lot. :KS

good stuff mate. let us know how this goes! 
i'm keen on using these as 11.04 (Mint LXDE) is not very stable either

---

### Post by chrome9 on 2012-01-09
The 3D-Driver doesn't work in 11.10! The installer quits with an compile error in the DRM-Module! Sorry, compile warnings are in german. The new drivers from December work in 11.04, but they are pretty unstable and slow. Gnome 3 works but it's very unstable with the VIA-Drivers.

make -C /lib/modules/3.0.0-14-generic/build M=/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.0.0-14-generic'
  CC [M]  /home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.o
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.0.0-14-generic'
9_drv.c:519:2: Fehler: unbekanntes Feld »pci_driver« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:520:4: Fehler: unbekanntes Feld »name« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:520:4: Warnung: Initialisierung von inkompatiblem Zeigertyp [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:520:4: Warnung: (nahe der Initialisierung für »driver.kdriver.pci«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:521:4: Fehler: unbekanntes Feld »id_table« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:521:4: Warnung: Elementüberschreitung in union-Initialisierung [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:521:4: Warnung: (nahe der Initialisierung für »driver.kdriver«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:523:4: Fehler: unbekanntes Feld »probe« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:523:4: Warnung: Elementüberschreitung in union-Initialisierung [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:523:4: Warnung: (nahe der Initialisierung für »driver.kdriver«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:524:4: Fehler: unbekanntes Feld »remove« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:524:4: Warnung: Elementüberschreitung in union-Initialisierung [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:524:4: Warnung: (nahe der Initialisierung für »driver.kdriver«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:525:4: Fehler: unbekanntes Feld »suspend« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:525:4: Warnung: Elementüberschreitung in union-Initialisierung [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:525:4: Warnung: (nahe der Initialisierung für »driver.kdriver«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:526:4: Fehler: unbekanntes Feld »resume« in Initialisierung angegeben
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:526:4: Warnung: Elementüberschreitung in union-Initialisierung [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:526:4: Warnung: (nahe der Initialisierung für »driver.kdriver«) [standardmäßig aktiviert]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c: In Funktion »via_chrome9_init«:
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:544:2: Fehler: Implizite Deklaration der Funktion »drm_init« [-Werror=implicit-function-declaration]
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c: In Funktion »via_chrome9_exit«:
/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.c:549:2: Fehler: Implizite Deklaration der Funktion »drm_exit« [-Werror=implicit-function-declaration]
cc1: Einige Warnungen werden als Fehler behandelt

make[2]: *** [/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9/via_chrome9_drv.o] Fehler 1
make[1]: *** [_module_/home/user/Downloads/5.76.42.90-u1104_32bit-61690/VIA_Chrome9] Fehler 2
make: *** [default] Fehler 2

:(

So let's wait for the next driver release or the first open 3D-Driver...

---

### Post by wasteinc on 2012-02-08
After so much time with ubuntu 10.04 I took the plunge of trying lubuntu.

well lubuntu is quite faster on the nc20 than gnome 2 and I recommend it to anyone still using nc20

I have installed 11.04 as it is the last thing Via and Tom supports and trying to install Toms driver. 

I have installed both .deb files TOM provided but Im not sure of I have succeeded anything. is installinh both deb files enough for the drivers and 3d acceleration to work??

---

### Post by yura1 on 2012-02-23
have tried new 32-bit VIA Chrome driver on the nc20 with ubuntu 11.04

I get with kernel 2.6.38-13-generic:
```

# modprobe via_chrome9
FATAL: Error inserting via_chrome9 (/lib/modules/2.6.38-13-generic/updates/dkms/via_chrome9.ko): Invalid module format

# dmesg | tail
...
[  168.797431] via_chrome9: disagrees about version of symbol module_layout
```

But driver seems to work with old kernel 2.6.35 from Ubuntu 10.10 but Xorg crashes with SEGFAULT when it used

---

### Post by lepetit on 2012-03-31
for testing, new snapshoot of openchrome

mailling list

"Hello
 
	Today is another snapshot release. Now the xorg driver supports 
resizing for UMS mode. You will be able to attach a HD monitor to your 
laptop and using randr be able to use it. This fix also makes the NC20 and 
XO usable again. The problem on both devices is the screen limits in 
virtual size is wrong. The problem is not really fixed but with resizing 
the screen is reset to the proper size. With the advent of KMS this will
eventually just go away. So as it stands the kms branch is usable across
the present devices supported in the master branch.
	The last set of the bugs left is Xv on the CLE266 and VX900. I 
plan to add RandR properties to the xorg driver as well. Currently the KMS 
part of the xorg driver is being hit by the fbfill pixman bug. I haven't 
tracked down what is causing this problem yet. Also it has been observed
EXA corruption bugs that happen randomly. The EXA needs a massive over 
haul but that will be saved for after the release. Give it a try and let 
me know how ti works for you."
 
[http://www.infradead.org/~jsimmons/xf86-video-openchrome-0.2.999-pre20120329.tbz](http://www.infradead.org/~jsimmons/xf86-video-openchrome-0.2.999-pre20120329.tbz)

---

### Post by Rainier Piqual on 2012-04-11
> **lepetit said:**
> for testing, new snapshoot of openchrome

mailling list

"Hello
 
	Today is another snapshot release. Now the xorg driver supports 
resizing for UMS mode. You will be able to attach a HD monitor to your 
laptop and using randr be able to use it. This fix also makes the NC20 and 
XO usable again. The problem on both devices is the screen limits in 
virtual size is wrong. The problem is not really fixed but with resizing 
the screen is reset to the proper size. With the advent of KMS this will
eventually just go away. So as it stands the kms branch is usable across
the present devices supported in the master branch.
	The last set of the bugs left is Xv on the CLE266 and VX900. I 
plan to add RandR properties to the xorg driver as well. Currently the KMS 
part of the xorg driver is being hit by the fbfill pixman bug. I haven't 
tracked down what is causing this problem yet. Also it has been observed
EXA corruption bugs that happen randomly. The EXA needs a massive over 
haul but that will be saved for after the release. Give it a try and let 
me know how ti works for you."
 
[http://www.infradead.org/~jsimmons/xf86-video-openchrome-0.2.999-pre20120329.tbz](http://www.infradead.org/~jsimmons/xf86-video-openchrome-0.2.999-pre20120329.tbz)

Did you test it? :)

---

### Post by lepetit on 2012-05-18
new release of openchrome 
[http://www.phoronix.com/scan.php?page=news_item&px=MTEwMzU](http://www.phoronix.com/scan.php?page=news_item&px=MTEwMzU)

---

### Post by Rainier Piqual on 2012-08-21
Hi guys,

did anyone ever try a 64bit linux on the nc20? any notable performance improvements?

cheers,

Rainier

---

### Post by yura1 on 2012-09-09
> **Rainier Piqual said:**
> Hi guys,

did anyone ever try a 64bit linux on the nc20? any notable performance improvements?

cheers,

Rainier

I've tried on Ubuntu 11.04. Firstly it lead to SEGFAULT. any way.
Then I reinstalled Ubuntu (to SSD) and tried again. It shows monocolour blinking screen when module is loaded

So I'm trying to upgrade up to 11.10 and test again

---

### Post by chrome9 on 2012-09-17
There seems to be a new driver for 12.04. Any hardcore NC20-user who tried this one?:guitar:

---

### Post by Diskdoc on 2012-09-17
I installed Ubuntu 12.04.1 on a friends NC-20. I checked xorg.0.log and saw it used the Openchrome driver. Seemed to work like a charm except Youtube stuttered terribly in fullscreen mode but that is more likely a Flash problem. I have recommended her some possible solutions to try.

---

### Post by MarBas on 2012-11-12
Have tried the new VIA drivers for 12.04 on Ubuntu 12.04.1 LTS. After Grub menu, the screen shows somthing like snow effect on the old cathode tube TVs. I'm not so expert as tom09 at Linux but I followed the step by step readme instructions and terminal gave me no errors. So maybe there's nothing good from VIA yet.

---

### Post by lepetit on 2013-03-31
hi, update for openchrome : [http://www.phoronix.com/scan.php?page=news_item&px=MTMzNzI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzNzI)
and update of official via driver for ubuntu 12.10
[http://linux.via.com.tw/support/beginDownload.action?eleid=704&fid=1004](http://linux.via.com.tw/support/beginDownload.action?eleid=704&fid=1004)

---

### Post by lepetit on 2013-04-04
\o/ try this for ubuntu 12.10
gallium3d driver for chipset Via
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0MTI](http://www.phoronix.com/scan.php?page=news_item&px=MTM0MTI)

---

### Post by johsv448 on 2013-07-14
> **lepetit said:**
> \o/ try this for ubuntu 12.10
gallium3d driver for chipset Via
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0MTI](http://www.phoronix.com/scan.php?page=news_item&px=MTM0MTI)

Has anyone managed to get these drivers to work?

I can't seem to compile the DRM driver, as gcc gives an error in file via_chrome9_cbios.c; in function     via_chrome9_connector_get_edid: struct drm_display_info has no     member named 'raw_edid'.

---

