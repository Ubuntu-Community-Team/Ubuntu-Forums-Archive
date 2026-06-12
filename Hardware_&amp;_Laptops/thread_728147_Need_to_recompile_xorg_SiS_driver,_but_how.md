---
title: "Need to recompile xorg SiS driver, but how?"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by dvh on 2008-03-18
I have Intel D201GLY2 motherboard which doesn't work well with native ubuntu drivers (7.10 nor 8.04alpha6). It is well known problem (vertical stripes across the screen, missing xv and 3d acceleration). All theese problems solve patched version of SiS xorg driver. I've downloaded patched version of SiS video driver from [http://www.winischhofer.net/sis/sisp.tar.gz](http://www.winischhofer.net/sis/sisp.tar.gz).

But it is for xorg 7.1. However it is know to work with 7.2 version too, it only need to disable version checking in this driver source. So I need to recompile this driver for my current xorg (Ubuntu 7.10). I uncomment all deb-src from sources list, but what to do now? I compile a lot, I'm experienced user, but not via apt-src so I need some quick start. I could download "some" xorg source from x.org, but God knows what it will do with ubuntu's xorg, so I preffer ubuntu-native solution. thanks.

The reason why I need xorg source is that ./configure in that modified SiS driver said:

```
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto fontsproto xf86dgaproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found
No package 'xf86dgaproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by gameame on 2008-03-21
I had your same problem. I managed to compile the driver after having installed:
x11proto-core-dev
x11proto-fonts-dev
x11proto-gl-dev
x11proto-input-dev
x11proto-randr-dev
x11proto-render-dev
x11proto-video-dev
x11proto-xext-dev
x11proto-xf86dga-dev
x11proto-xf86dri-dev
x11proto-xf86misc-dev
x11proto-xinerama-dev
mesa-common-lib

I hava a SiS Mirage integrated video driver on a Foxconn n15235 motherboard with Ubuntu 8.04 alpha6.

---

### Post by pulsifier on 2008-03-30
maybe you could give us a hand?

[http://ubuntuforums.org/showthread.php?t=615094&highlight=M671&page=6](http://ubuntuforums.org/showthread.php?t=615094&highlight=M671&page=6)

---

### Post by ottod on 2008-04-11
Patched source and binaries for D201GLY2 compiled for Hardy. Originals taken from [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2873&DwnldID=15443&strOSs=39&OSFullName=Linux*&lang=eng"). 2D only. Capable of playing videos with included xorg.conf.
Binaries only for the interested. I know enough C only to make a sophisticated Hello World. I just forced some ifdef's that were not working well and replaced one deprecated constant called SecurityWriteAccess with DixWriteAccess.
Binaries compiled and working in Hardy Heron beta. Place sis_drv.* in /usr/lib/xorg/modules/drivers and xorg.conf in /etc/X11. xorg.conf is configured for a generic 60hz 1024x768 CRT. Do a dpkg-reconfigure -phigh xserver-xorg if not good for you and after first boot, try to check available screen resolutions in System/Preferences. Important lines for video playback are
	Option		"EnableSiSCtrl"		"yes"
	Option		"XvDefaultAdaptor"	"Blitter"
Remove not wanted screen resolutions and virtual desktop settings from xorg.conf to taste. Use included as sample.
If successful, have a toast with some :popcorn:!

---

### Post by Master One on 2008-04-11
Wouldn't it be great, if someone could manage a binary package for 64bit Hardy as well? Would save a lot of hassle, and prevent ppl wasting time on one and the same task (inventing the wheel multiple times).

---

### Post by Master One on 2008-04-18
> **dvh said:**
> The reason why I need xorg source is that ./configure in that modified SiS driver said
How about the debian way, instead of installing all the needed dev-packages according to the ./configure error-messages:```
sudo apt-get build-dep xserver-xorg-video-sis
```

---

### Post by tuneable on 2008-04-19
> Wouldn't it be great, if someone could manage a binary package for 64bit Hardy as well?

:D That would really be great! 

A binary was produced compiling the source from Intel, but it did not seem to work.

---

### Post by Master One on 2008-04-20
Thanks to ottod, using the src-package from [here](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4) it was no problem compiling the driver on Hardy amd64.

But now I am fiddling with the rebuild of the kernel to inlude the iMedia-patch for sis-agp, because without it, no AGP support. I already did it, and it was working great, but with my rebuilt kernel there seemed to be some modules missing (likt snd-intel8x0), although I took the .config from /boot. I think I open a new thread concerning this issue.

---

### Post by tuneable on 2008-04-21
Thanks Master One, I compiled the binary using the "ottod" modified source and things went like a breeze on Hardy 64bit running on an Intel d201gly2 motherboard. 

After compilation, I manually moved the binary to **/usr/lib/xorg/modules/drivers/** (not to the default **/usr_/local_/lib/xorg/modules/drivers/** location). Not sure if it makes a difference, but I thought I'd better mention it.

Thumbs up to ottod!  \\:D/

---

### Post by Master One on 2008-04-21
No manual moving of files requires, just do it this way:```
sudo apt-get purge xserver-xorg-video-sis
./configure --prefix=/usr
make
sudo make install
```
I am still on the matter of patching the kernel, which is far less of a problem, than expected before (this time I just followed the CustomKernel guide in the Ubuntu wiki, using the git-method), but I am unsure how to measure the difference between having AGP support and not.

With just the driver, but no patched kernel, you will find a line in /var/log/Xorg.0.log, that just says something like "No AGP found, aborting". With the patched kernel it finds AGP and says something about 32MB assigned to AGP or so. With normal use in Gnome, I could not see any real difference so far, that's why I would like to know, how to measure graphics performance with and without AGP support.

---

### Post by PaulHuygen on 2008-04-28
[QUOTE=ottod;4697207]Patched source and binaries for D201GLY2 compiled for Hardy. 
[..]
Binaries compiled and working in Hardy Heron beta. Place sis_drv.* in /usr/lib/xorg/modules/drivers and xorg.conf in /etc/X11. xorg.conf is configured for a generic 60hz 1024x768 CRT.
[..]

Thanks! It worked rightaway and I am glad to have the high resolution back.

Only problem was, that I just moved your xorg.conf at the right place without editing. As a result, the keyboard was set to spanish and I could not type my password to login. So, other people should not do as clumsy as I did.

Paul Huygen.

---

### Post by nitrousoxide82 on 2008-04-30
Worked "out of the box" on Kubuntu Hardy for my laptop with a SiS 671 (I'm typing this message from the Live CD, I'm running a test with it right now). Now I can upgrade to Hardy without fear. Thanks, thanks, thanks!!

PS: Just ran a test with an AMD64 live CD. Compiled it on a machine (running NVIDIA so I couldn't "make install" it, not that it matters), grabbed the binaries and loaded them on the live CD. Worked on first try as well. It was sort of a hassle to compile it (which I'm a bit used to though), so to save people this hassle I'm adding the binaries for 64-bit Hardy I built. I'm using these to post here from my laptop. To install:

- Copy the files to "/usr/lib/xorg/modules/drivers" (use sudo).
- Edit your "/etc/X11/xorg.conf" file, and add the following lines under the "Device" section:
```

Section "Device"
    Identifier "Configured Video Device"
    Driver    "sis"                    # <-- Add this line
    Option    "EnableSiSCtrl" "yes"    # <-- Add this line
(rest of file contents follow)

```

Once again, thanks!!

---

### Post by alicemoon on 2008-05-01
I have a sis mirage graphics card and have worked out that this is what is causing the wavy lines on my screen. I have no idea how to do anything complicated but have read the forums - will the vesa driver just make my screen bearable and if so how do I load it - or do I need to do what is suggested in this thread. Very simple step by step instructions would be good as I only have a vague idea of what you are talking about. Thanks in advance for help

---

### Post by nitrousoxide82 on 2008-05-02
alicemoon,

I think you should use the drivers posted in this thread. They are for Ubuntu 8.04, if you're using another version you can find them elsewhere (I used to have them archived here but I think I lost them after I reorganized my files).

The files you need are [font="Monospace"]sis_drv.la[/font] and [font="Monospace"]sis_drv.so[/font]. If you're using a 32-bit system, get ottod's "intelbin.tar.bz2" package. The files you need will be in the [font="Monospace"]usr/lib/xorg/modules/drivers[/font] subfolder of where you extracted the package. If you are on 64-bit (like me) get my "sis_drv-hardy-amd64.tar.bz2" package. The files will be right where you extract the package.

I'll try to detail the installation procedure as well as I can. I will describe a command-line driven procedure, done in the "raw Linux console" (as I like to call it). That's how I did it. It can also be done via the graphical interface but is prone to fail because you may already be running another version of the drivers, so it is ideal that the X server is not running when you do this.

**Using the raw Linux console**
- Log out of the graphical environment.
- When you're sent back to the login screen, press Ctrl+Alt+F1. That'll take you to the raw Linux console.
- Type your username and password to log into the console.
- Enter [font="Monospace"]sudo /etc/init.d/gdm stop[/font] (or [font="Monospace"]sudo /etc/init.d/kdm stop[/font] if you are in Kubuntu) to stop the display manager. That will stop the X server as well.


**Going back to the graphical interface**
- Restart the display manager, using the same command you used to stop it with "restart" as the argument instead of "stop". That'll bring back your graphical login screen.
- Press Ctrl+Alt+F1 to go back to the raw console, and log out of it (by typing "logout"). 
- Then, press Ctrl+Alt+F7 to go back to the graphical login screen.


**Installation instructions**

1. Go into the raw Linux console (procedure above). 

2. Go into the directory where the [font="Monospace"]sis_drv.la[/font] and [font="Monospace"]sis_drv.so[/font] files are (see note above).

3. Copy those files to [font="Monospace"]/usr/lib/xorg/modules/drivers[/font]). You'll need root privileges to do this. 

4. Open the file [font="Monospace"]/etc/X11/xorg.conf[/font] in a text editor (I recommend [font="Monospace"]nano[/font] in the command line). You'll also need root privileges for this operation. You may also want to make a backup copy of the file so you can restore it in case anything goes wrong.

5. Edit the contents of the file. Find the "Device" section and add the following lines:
```

Driver  "sis"
Option  "EnableSiSCtrl"  "yes"

```
then, find the "Screen" section and add the following line:
```

DefaultDepth  24

```
If any of the lines are already present, change them to have values to reflect those above. After you're done, save the file and quit the editor.

6. Restart the graphical interface and go out of the raw console (see above).


I have done this and had success. My graphics chip is the SiS Mirage 3 (a.k.a. SiS 671).

NOTE: Some of the operations described need root privileges. To obtain them, use [font="Monospace"]sudo[/font] before the command. [font="Monospace"]sudo[/font] will ask for your password, supply it. The characters are not echoed on screen. 

Here's what your screen would look like, with your input in [color="red"]red[/color], and my comments in [color="blue"]blue[/color]. I assume the needed files are in a folder called "sis-driver" in your home folder here.

[font="Monospace"]
Ubuntu 8.04 computer tty1

computer login: [color="red"]alicemoon[/color]
Password:

alicemoon@computer:~$ [color="red"]cd sis-driver[/color]
alicemoon@computer:~/sis-driver$ [color="red"]sudo cp sis_drv.* /usr/lib/xorg/modules/drivers[/color]
[sudo] password for alicemoon:
alicemoon@computer:~/sis-driver$ [color="red"]sudo nano /etc/X11/xorg.conf[/color]
[color="blue"]After you finish editing the file...[/color]
alicemoon@computer:~/sis-driver$ [color="red"]sudo /etc/init.d/gdm restart[/color]
* Restarting GNOME Display Manager...
[color="blue"]A little while after this you should see the graphical login screen. When you do, press Ctrl+Alt+F1 to go back to the console.[/color]
alicemoon@computer:~/sis-driver$ [color="red"]logout[/color]

Ubuntu 8.04 computer tty1

computer login:
[/font]

I also attach a copy of my [font="Monospace"]/etc/X11/xorg.conf[/font] file, to serve as an example.

Hope this helps.

---

### Post by alicemoon on 2008-05-05
thanks for taking the time to give me a detailed reply - i will give this a go and hope it solves my problems

---

### Post by pr144tue on 2008-05-26
Hello, 

I used the package intelsrc.tar.bz2 from ottod. But - to tell the truth I am using
slackware - I always receive an error if I try to complile der sis-2d-driver:

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/pixman-1 -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT sis_mergedfb.lo -MD -MP -MF .deps/sis_mergedfb.Tpo -c sis_mergedfb.c  -fPIC -DPIC -o .libs/sis_mergedfb.o
sis_mergedfb.c: In function 'SiSProcXineramaSelectInput':
sis_mergedfb.c:2640: error: 'DixWriteAccess' undeclared (first use in this function)
sis_mergedfb.c:2640: error: (Each undeclared identifier is reported only once
sis_mergedfb.c:2640: error: for each function it appears in.)
make[2]: *** [sis_mergedfb.lo] Fehler 1
make[2]: Leaving directory `/home/work/hardware/notebookesprimoV5355/sis/ottod/2d-driver/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Leaving directory `/home/work/hardware/notebookesprimoV5355/sis/ottod/2d-driver'
make: *** [all] Fehler 2

But someone please give me an advice to avoid this error?

Best regards
Peter

---

### Post by v314m on 2008-06-05
I have a problem after upgrading to Hardy from Festy. I installed the binaries posted by ottod in #4 ([http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)). Everything works, except one important thing: all movies are displayed only in original resolution; any resizing is not possible. So no full screen movies... In Festy, I had the driver compiled by skisevel; that worked ok ([http://ubuntuforums.org/showthread.php?t=463077](http://ubuntuforums.org/showthread.php?t=463077)).

---

### Post by SebMKd on 2008-06-07
Hello Everyone. 
I've just installed 8.04 Desktop 64bits on D201GLY2A (Celeron 220 1.2GHz, 1GB DDR2 533MHz, MiniPSU PW-200-M, Acer 22") and had the same problem.
I've fooled around with Linux for a few years, however, I've never 'compiled' anything. So step by step instructions are crucial to me!
So I've followed nitrousoxide82 welcomed instructions (with 64b drivers) and got a huge surprise: my VGA wouldn't be recognized by my screen, "Out of range". I was stuck without display. Fortunately, I tried a bunch of CRTL+ALT+ something and was back to the console. 
In order to fix my problem I had to remove "DepthDefault  24" in my Xorg!!!
Now I'm all set. Thanks a bunch!

---

### Post by flaugher on 2008-06-10
I am Mr. Noob.
I do parties, anniversaries, birthdays and other special occasions.

I have also just killed my mother-in-law's new computer which I built using Hardy. I downloaded and copied the sis_drv.* successfully, then edited xorg.conf. Now all I get is "INPUT NOT SUPPORTED".

Who should I blame? Intel? Ubuntu 8.04? Myself? My mother-in-law? (Nah, she's 84 years old and only wants her email back).

How do I get the screen with the noise lines back???? :confused:

---

### Post by SebMKd on 2008-06-10
So you have the same problem as I just had. Scary isn't it! You use Sis661?

While the computer was still running, I either pressed CRTL+ALT+F1 or F7 which through me back to the raw console (I believe it's F1).

Then restarted the whole nitrousoxide82 procedure, whithout copying the files and the Defaultdepth:

- Enter [FONT="Courier New"]sudo /etc/init.d/gdm stop [/FONT]to stop the display manager.
- Open xorg.conf: [FONT="Courier New"]sudo nano /etc/X11/xorg.conf [/FONT]
- Edit the contents of the file. Find the [ section "Device" ] and add the following lines:
Code:
[FONT="Courier New"]Driver  "sis"
Option  "EnableSiSCtrl"  "yes"[/FONT]
- Now, restart the display manager, using [FONT="Courier New"]sudo /etc/init.d/gdm restart[/FONT]. That'll bring back your graphical login screen.
- Press Ctrl+Alt+F1 to go back to the raw console, and log out of it by typing "logout". 
- Then, press Ctrl+Alt+F7 to go back to the graphical login screen.

That did it in my case. If you powered down the computer in the meantime I think you should still be able to go into the raw console mode with CRTL+ALT+F1 whenever you estimate that the computer has rebooted and should be showing you the login screen. Even if you don't see it.

Hope this'll help.

---

### Post by flaugher on 2008-06-10
No joy. Still get "Input Not Supported". May have to reinstall video drivers ... uh ... somehow since I can't get to the package manager.

I cut my teeth on DOS, Pascal, and Fortran (before 77), but this is just too ... wierd. :confused:

---

### Post by SebMKd on 2008-06-19
Well, well, well. 

My goal was to use this mobo (D201GLY2A) for a file server. Therefore, I've installed Hardy Server 64 on a new hard drive and repeated my steps to get rid of the vertical lines. And to my utmost exasperation it didn't work!!

So I'm booting back on my Hardy Desktop 64 drive and to my surprise all the changes I've made to my xorg file are gone and I have no display! ("Input not supported")

Damn...

I go back to my Hardy Server drive, fool around some more (try displayconfig-gtk which tells me "Could not open display", then dpkp-reconfigure -phigh xerver-xorg, which revert my xorg to a virgin state...), without any luck.
Upon manual shutdown I end up several times to the recovery console.
So I finally decide to try a few things... I click on "Repair package" (I think or Repair PKG) and watch the process. At some point it seems to install or reinstall a kernel (2.6.24-19)...
Then system reboots, flickers during login and brings up a graphic interface, out of nowhere, with that precious Display Configurator, where you can select your monitor and graphic card. I select my display (Acer AL2223wd) and a Generic Sis driver (as the 662 is not listed). And miraculously, I have a clear desktop. However, I currently can't get above 800x600.

Well to me this would be enough, as I just want to use this system as file server, and thus a low resolution is acceptable.

In consequence, this Repair package in the Recovery console did the trick.

Hope this helps.

---

### Post by peanut80 on 2008-06-21
> **SebMKd said:**
> Hello Everyone. 
I've just installed 8.04 Desktop 64bits on D201GLY2A (Celeron 220 1.2GHz, 1GB DDR2 533MHz, MiniPSU PW-200-M, Acer 22") and had the same problem.
I've fooled around with Linux for a few years, however, I've never 'compiled' anything. So step by step instructions are crucial to me!
So I've followed nitrousoxide82 welcomed instructions (with 64b drivers) and got a huge surprise: my VGA wouldn't be recognized by my screen, "Out of range". I was stuck without display. Fortunately, I tried a bunch of CRTL+ALT+ something and was back to the console. 
In order to fix my problem I had to remove "DepthDefault  24" in my Xorg!!!
Now I'm all set. Thanks a bunch!

I'm having similar issues trying to use the solution posted by nitrousoxide with my LCD TV. After replacing the drivers and changing my xorg.conf I restart the graphics manager, but receive a "Mode not supported" message. Removing or changing the DefaultDepth line didn't work either, unfortunately.

The nitrousoxide solution actually works on my CRT monitor, and interestingly the original sis driver supports 1366x768@60 hertz with the screen tearing issue, so it must be something to do with the output using the new driver, perhaps the resolution is not supported.

Any help would be greatly appreciated.

---

### Post by Braveheart1980 on 2008-06-28
Well I just ordered the intel d20 mobo with Sis 662 graphic driver
As I am about to install ubuntu I was wondering if there is any way Sis662 can run properly under hardy , or if I should install gutsy intead.
Thanx in advance

PS I am talking about the 32bit versions of either gutsy or hardy

---

### Post by lajthabalazs on 2008-06-29
I wasn't woried until the D201GLY2 arrived, and even if a Windows installed for an other config worked well with this mobo out of the box, after installing Ubuntu, I got the stripes and vibration. Ubuntu updates didn't solve the problem, but the #4 post in this thread did. I posted my experiences in an other thred:

[http://ubuntuforums.org/showthread.php?t=463077&highlight=D201GLY2&page=14](http://ubuntuforums.org/showthread.php?t=463077&highlight=D201GLY2&page=14)

Thx ottod, your post was realy useful. For all the others, don't get discouraged, if you wait long enough sooner or later your problem will be solved by someone else.

---

### Post by baharia on 2008-07-21
> **ottod said:**
> Patched source and binaries for D201GLY2 compiled for Hardy. Originals taken from [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2873&DwnldID=15443&strOSs=39&OSFullName=Linux*&lang=eng"). 2D only. Capable of playing videos with included xorg.conf.
Binaries only for the interested. I know enough C only to make a sophisticated Hello World. I just forced some ifdef's that were not working well and replaced one deprecated constant called SecurityWriteAccess with DixWriteAccess.
Binaries compiled and working in Hardy Heron beta. Place sis_drv.* in /usr/lib/xorg/modules/drivers and xorg.conf in /etc/X11. xorg.conf is configured for a generic 60hz 1024x768 CRT. Do a dpkg-reconfigure -phigh xserver-xorg if not good for you and after first boot, try to check available screen resolutions in System/Preferences. Important lines for video playback are
	Option		"EnableSiSCtrl"		"yes"
	Option		"XvDefaultAdaptor"	"Blitter"
Remove not wanted screen resolutions and virtual desktop settings from xorg.conf to taste. Use included as sample.
If successful, have a toast with some :popcorn:!
Thanks al lot...

---

### Post by zorglups on 2008-07-22
> **ottod said:**
> Important lines for video playback are
	Option		"EnableSiSCtrl"		"yes"
	Option		"XvDefaultAdaptor"	"Blitter"


Thank a lot to Ottod and everyone else in this forum who made this little motherboard usable with Mythbuntu.

For information, in order to be able to play video fullscreen, I had to remove the following option from the xorg.conf :

Option "XvDefaultAdaptor" "Blitter"

Have a nice day.

Pierre

---

### Post by brons2 on 2008-07-24
I got it working finally after much pulling out of hair.  I had to play with the xorg.conf a lot.  my monitor resolutions still aren't what I want but the current res is ok.  I am loath to play with it anymore.

---

