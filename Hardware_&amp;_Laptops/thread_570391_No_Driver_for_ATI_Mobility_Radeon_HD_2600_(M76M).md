---
title: "No Driver for ATI Mobility Radeon HD 2600 (M76M)"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by kriebgui on 2007-10-08
Hello,

i have a ASUS F3KA Notebook with the Graphic Chip/Card ATI Mobility Radeon HD 2600 (M76M).
I can't install Ubuntu. Not in a smaller Resolution (VGA-Mode) or any other Resolution.
Have anyone a idea?

---

### Post by Joe325 on 2007-10-08
What version of Ubuntu are you trying to install

---

### Post by Xenaco on 2007-10-08
ATI website has Linux Radeon HD2600 drivers under the Radeon chipset.

[http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html]("http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html")

This is ATI Proprietary Linux x86 Display Driver 8.41.7

It works for all Radeon HD2xxx family.

---

### Post by kriebgui on 2007-10-09
@XENACO

Many thanks for the information. I will test the driver.

---

### Post by kriebgui on 2007-10-09
@Joe325

I will install Unbuntu Desktop Version 7.04.
If you have no other information for me, i will test the Driver that post me from Xenaco

---

### Post by isnake on 2007-10-14
I tried installing Ubuntu 7.10 Beta.
I have a wide screen monitor (1680*1050) but trying to work in that resolution seems not possible.
Installing the ATI driver kind of means screwing up the whole video part.
I get 3 screwed up same desktops in the top part of my monitor and it's unworkable.
That is if I do not get an error that it is not working at all with an error (blue screen asking to show input and output).... (although that might have been Ubuntu 7.04)

I got an Asus EAH2600PRO video card.
Any way how I can get a workable situation on my computer or will I have to have patience before I can actually run Ubuntu (or Linux at all) properly on my computer ?

---

### Post by war@rsb.at on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/152179](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/152179) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Xenaco said:**
> ATI website has Linux Radeon HD2600 drivers under the Radeon chipset.

[http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html]("http://ati.amd.com/support/drivers/linux/linux-radeonhdd.html")

This is ATI Proprietary Linux x86 Display Driver 8.41.7

It works for all Radeon HD2xxx family.

Have you tried this? If so, on which machine did you try?

I found these drivers did not work on mobile radeon 2600HD

Wolf

---

### Post by FlamingGooch on 2007-10-19
I'm having this same problem with my ATI X1400 card on my Dell 9400 inspiron notebook. I'm trying to install 7.10 and I get to a point where my screen just starts to flicker and displays bits of color all over the screen.

---

### Post by Maxime2323 on 2007-10-19
i'd like to have some help on this i'm also trying to instal my ati hd2600 mobility on my laptop

---

### Post by deffcon on 2007-10-22
Hi all,

I have an Hewlet Packard 8510P notebook with an hd2600 mobility videocard in it, but tried everything under gutsy to get it working, but no luck anyone ideas?

Thnx in advance,

Dave

---

### Post by Manoliitto on 2007-10-25
> **deffcon said:**
> Hi all,

I have an Hewlet Packard 8510P notebook with an hd2600 mobility videocard in it, but tried everything under gutsy to get it working, but no luck anyone ideas?

Thnx in advance,

Dave

I have a 8510P as well and I get it work only with VESA. Am I right that ATI drivers are not supporting Mobility Radeon HD 2600 yet?

Manoliitto

---

### Post by dZoniiiii on 2007-11-08
unfortunately it seems that they just don't have a solution for mobility radeonhd cards yet.. hope that it's just a matter of time when we will find them in restricted drivers section.

Oh, almost forgot - I have toshiba A210-16f notebook with mob. radeon hd 2600 - it doesn't work! :(

---

### Post by rafar on 2007-11-08
I got mine working after installing the driver somebody provided on these forums.
I have asus F3KA with ATI HD 2600. Had to tweak the xorg.conf and setup the Compiz properly. All works ok, my video card is identified properly. I'm running gutsy 7.10

---

### Post by dZoniiiii on 2007-11-08
omg omg, pleeeaaaaseee give me the link to that topic where that was explained! :) pls pls pls pls pls!! :)

---

### Post by Manoliitto on 2007-11-09
This sounds very interesting. I would be interested too. Where is that document?

-Manoliitto-

---

### Post by Sivik on 2007-11-11
> **rafar said:**
> I got mine working after installing the driver somebody provided on these forums.
I have asus F3KA with ATI HD 2600. Had to tweak the xorg.conf and setup the Compiz properly. All works ok, my video card is identified properly. I'm running gutsy 7.10

Ok,  how did you get it all working.   I am thinking about buying a toshiba laptop with the ati 2600 HD but I have heard alot of rumors in regards to problems with the drivers.  Any advice would be helpful.  Thanks.

---

### Post by sandstig on 2007-11-15
Try using _[Envy](http://albertomilone.com/nvidia_scripts1.html)_, then when it says your card isn't recognized, select "Manual Install" and choose the latest ATI binaries. Make sure to click the button for removing your ATI drivers first (in Envy) before installing.

---

### Post by NeverM$4Me on 2007-11-15
> **rafar said:**
> I got mine working after installing the driver somebody provided on these forums.
I have asus F3KA with ATI HD 2600. Had to tweak the xorg.conf and setup the Compiz properly. All works ok, my video card is identified properly. I'm running gutsy 7.10

Hi rafar,

A couple of questions here.

First, when you said you got it working with "the driver somebody provided on these forums", can you please kindly post their links here so we can give a shot? Are they open-source one or ati's resctricted fglrx? Which version?

Second, you said you had to tweak the /etc/X11/xorg.conf for it to work, can you kindly copy/paste your working xorg.conf file for us?

Third, you said your card was identified properly, can you do a "fglrxinfo" in the terminal and copy/paste the result here?

As now the rest of Mobility HD 2600 owners are all scratching our heads going nuts trying to figure this whole thing out.

Thanks in advance!

---

### Post by colonelk on 2007-11-16
I'm in the same boat as you guys.  HP 8510p brand new with Vista x64 and Ubuntu Gutsy.  The gutsy install went fine but I can't select the right resolution for this laptop screen.  The highest I can select is 1400 which frankly looks pap!

HELP !!! :D

---

### Post by Tom Rolfson on 2007-11-17
Hi, i also got the HP8510p, I tried to run Vista and Ubuntu dual, but manage to delete all the hp files and Vista, How do i get it back?

---

### Post by macmus on 2007-11-21
> **Tom Rolfson said:**
> Hi, i also got the HP8510p, I tried to run Vista and Ubuntu dual, but manage to delete all the hp files and Vista, How do i get it back?

lol u are screwd :D

depending how many partition u deleted u are in a deep **** or not.

good luck

---

### Post by Manoliitto on 2007-11-21
> **sandstig said:**
> Try using _[Envy](http://albertomilone.com/nvidia_scripts1.html)_, then when it says your card isn't recognized, select "Manual Install" and choose the latest ATI binaries. Make sure to click the button for removing your ATI drivers first (in Envy) before installing.

Thanks for the effort to help. But this time, no help. :(

I made fresh install for 7.10 with live CD. I installed Envy by envy_0.9.8-0ubuntu13_all.deb.
I first removed ATI drivers before installing newer. So far looks good, but after reboot and logging in all goes white except mouse pointer.

Here are parts of my _not_working_ xorg.conf

[B]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection


[/B]

Any new ideas are welcome.

-Manoliitto-

---

### Post by Jojoba86 on 2007-11-22
I've got the same problem... used envy to install latest ati drivers manually. Login screen in seems good, proper 1440 x 900 resolution, but then just a white screen and a pointer?!

I hope someone has a suggestion, it's horrible having to use a low non-widescreen resolution.

My setup is a Toshiba P100-123 laptop with a HD2600 graphics card.

Jj.

---

### Post by Clancy_s on 2007-11-22
Hi all,

I too have the Radeon HD 2600 and would like to get it working under ubuntu 7.10

It looks like rafar's not been around for a bit.  After searching on envy+radeon+2600 I came up with 5 threads: one was this one ](*,)  one of the others may have been the one rafar referred to:

[http://ubuntuforums.org/showthread.php?t=606859](http://ubuntuforums.org/showthread.php?t=606859)

I'm very new to ubuntu (been using Xandros for 3 years), do the suggestions in that post look doable to anyone?  I fail at the first hurdle: the restricted driver manager tells me there are no restricted drivers for my system :rolleyes:

I'm still pudding around in ubuntu basics and getting non video things set up the way I want them.  Once I've done that, backed up my xorg conf files and imaged my install I might get up the courage to try proprietary video drivers.

I gather ATI released a new set yesterday, maybe they'll work...

Tohsiba Satellite A200/S01
Intel Core 2 Duo 2.2 Ghz T7500
4096Mb DDR2 RAM (667 Mhz)
2 x 160 Gb SATA HDD
ATI Radeon 2600 HD graphics card with 512Mb RAM
15.4" WXGA (1280 x 800) BrightView Screen
HD DVD-ROM DVD SuperMulti Double/Dual Layer Drive
Intel 4965 agn Wireless LAN 802.11 a/g/n

---

### Post by Clancy_s on 2007-11-22
> **Tom Rolfson said:**
> Hi, i also got the HP8510p, I tried to run Vista and Ubuntu dual, but manage to delete all the hp files and Vista, How do i get it back?

That really isn't a video card issue, I'd suggest looking / asking in the beginner's forum.

As macmus implied if your ubuntu install took over your whole hard disk you'll have completely wiped all your Vista stuff, OS and data.

Do you have install / rescue disks for your system?  If not I think your only chance is to get disks from HP, I'd expect them to charge you for them.  You could then resinstall Vista, that'd give you a 'virgin' system, you'd  have to reinstall all your apps and data seperately.

If you didn't overwrite your Vista partition just lost it off the boot menu you should be able to see the partition in Nautilus.  I believe in that case you can use the Vista rescue disk to redo your MBR (which will break Grub), but I've never tried it.

---

### Post by Jojoba86 on 2007-11-24
I've made some progress getting the card working, here are the steps I took so far;
[LIST=1]
[*]Install the latest ATi drivers using envy, needs to be done using the manual option as officially the drivers don't support the HD2X00 laptop cards (this is why Ubuntu doesn't install them automatically). At this stage I got a white screen after I logged in...
[*]Next step was to login using the failsafe gnome option at the login screen, which worked fine for me.
[*]Finally I disabled the desktop graphical effects by editing /etc/X11/xorg.conf changing "Enable" to "Disable" in the following section
```
Section "Extensions"
	Option "Composite" "Enable"
EndSection
```
[/LIST]
So this leaves everything working except the 3D effects (also scrolling/dragging doesn't work well). If anyone knows how to get the 3D effects working please share!

Jj

---

### Post by jstableford on 2007-11-25
I too am having a lot of trouble with this. I've been able to install the driver, but not the effects without getting the 'white screen of death.'

I'm going to keep working on this, but any help would be much appreciated. I'll post what I find.

J

---

### Post by milanp on 2007-11-25
Help


I tried to manually install the latest driver from ATI website (7.11) and when I try to boot
the system the display is out of sync with lots of horizontal lines.
I had the same problem using envy.
I read somewhere that ATI's latest drivers for radeon don't support the mobility HD2600.
Can someone post the xorg.conf file where you can actually boot in X, please....

HP 8510p with ATI 2600
Intel Core 2 Duo 2.2 Ghz T7500
2048 DDR2 RAM (667 Mhz)
160 Gb SATA HDD
ATI Radeon 2600 HD graphics card with 256 MB RAM
15.4" WXGA (1280 x 800) Screen
DVD recorder
Intel 4965 802.11 a/g/n + bluetooth.

---

### Post by Yellow Pasque on 2007-11-25
For basic 2D support, you could always try one of the open-source drivers.
[http://www.phoronix.com/scan.php?page=article&item=921&num=1](http://www.phoronix.com/scan.php?page=article&item=921&num=1)
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

---

### Post by Jojoba86 on 2007-11-25
> **Temüjin said:**
> For basic 2D support, you could always try one of the open-source drivers.
[http://www.phoronix.com/scan.php?page=article&item=921&num=1](http://www.phoronix.com/scan.php?page=article&item=921&num=1)
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

Thanks Temüjin, I tried this driver and things work better now, and getting it running was easier than expected. This gets 2D acceleration working, so scrolling/dragging is smooth now. I guess those of us with the HD2600 card will have to wait until one of the drivers out there supports 3D for the Compiz Fusion stuff. Hopefully won't be too far off in the future...

---

### Post by Yellow Pasque on 2007-11-25
Awesome! Which driver did you use, the radeon or RadeonHD driver? (i.e. which link did you follow?)

---

### Post by Jojoba86 on 2007-11-25
I used the RadeonHD driver (but used the instructions found on the other link's website). I'm not sure if one would be better than the other, but as neither support 3D I guess it doesn't really matter too much.

---

### Post by jstableford on 2007-11-25
> **Temüjin said:**
> For basic 2D support, you could always try one of the open-source drivers.
[http://www.phoronix.com/scan.php?page=article&item=921&num=1](http://www.phoronix.com/scan.php?page=article&item=921&num=1)
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

Thanks - I got the 'raedon' driver to work for me. I'm running a VisionTek Radeon HD2600 512mb (I should say "running") in an old Athlon 2800 system. Now I have no acceleration whatsoever, but at least I'm not getting white or black screens like before.

I will be watching this form like a hawk for updates to this driver.

J

---

### Post by dmf86 on 2007-11-28
Same problem here, any solution in the horizont?

---

### Post by Jojoba86 on 2007-11-28
Illubaba posted on how he got it working (in German but you get the idea) [http://ubuntuforums.org/showthread.php?t=623258](http://ubuntuforums.org/showthread.php?t=623258). I don't know if anyone else tried this and got it working? Some of the instructions are a little unclear and I'm not in the experimenting mood at the moment.

Otherwise the RadeonHD driver, using the guide at [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1) worked for me.

Jj

---

### Post by Clancy_s on 2007-11-28
The radeonhd install worked for me.  Phoronix have a page for that too (see Jojoba86's link), which is convenient, all I had to do was copy and paste the commands. :)

I chose radeonhd over radeon because it looks like radeon doesn't fully support the hd cards yet, but since radeon provides 2d acceleration and full 3d support with acceleration to those cards it does fully support I'll be keeping an eye on it.  It'll be interesting to see whether the radeon project comes up with a driver before ATI does.

I also sent an enquiry to ATI re linux drivers for the Mobility Radeon HD2600, all I got was an automated reply to some links that apply to other cards. :rolleyes:  I pressed the "No I still need help" button and will keep at it until I get a sign that a real person received my request.

eta: I had a reply from an actual tech support person at ATI.  Not actually helpful as such but I wasn't expecting that, just letting them know I wanted linux drivers for the Mobility Radeon HD 2600.

[quote=ATI tech support]Dear customer,

Thank you for contacting AMD.

Since the equipment manufacturer that uses AMD technology in their mobile (laptop/notebook) products has many other implementations that might affect the general performance of the equipment, we redirect our customer to contact the equipment manufacturer for technical service.

You also have available our Knowledge Base for technical research.

For more information about this issue, please access the link below:
[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=23433](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=23433)

For more information about Linux driver support, please access [http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)

For more information about technical support for Linux OS, please access [http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=28027](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=28027)

Any other questions, please contact us again.

Regards,
Pier Bottero
AMD Technical Support Center [/quote]

---

### Post by mthn on 2007-12-16
i m still looking for any solution, however couldnt find it, everybody still waiting for new drivers ?
or somebody have solution for mobility hd 2600
regards.

---

### Post by peterpan168 on 2007-12-18
I have mobility hd 2600 too, anyone found a solution?

---

### Post by slwk on 2008-01-04
Hi, i have installed ATI mobility Radeon HD 2600 on my toshiba by [[THIS]](http://www.cyberarmy.net/forum/art_public/messages/316396.html) method. Resolution change to proper (1200x800), it's much better now than it was ealier, but the graphic is still worse than on windows, just check out like google looks [[SCREEN]](http://www.imagic.pl/public/102006/zrzutekranu.png) Note that i'm new linux user (I've been using ubuntu 7.10 only for 1 week) and i don't know how to configure this ATI graphic card to work properly. If sb can help me i would be grateful :)
Here's my xorg file:
```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

and this is what i get after i put fglrxinfo and glxinfo | grep "direct" in terminal:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600
OpenGL version string: 2.1.7059 Release

direct rendering: Yes

```
i also tested glxgears:
```
15368 frames in 5.0 seconds = 3073.465 FPS
16799 frames in 5.0 seconds = 3359.755 FPS
16796 frames in 5.0 seconds = 3359.080 FPS
16797 frames in 5.0 seconds = 3359.298 FPS
18932 frames in 5.0 seconds = 3786.378 FPS
25699 frames in 5.0 seconds = 5139.654 FPS
21165 frames in 5.0 seconds = 4232.876 FPS
21153 frames in 5.0 seconds = 4230.546 FPS
28359 frames in 5.0 seconds = 5666.005 FPS
27807 frames in 5.0 seconds = 5561.291 FPS
20980 frames in 5.0 seconds = 4195.959 FPS
30070 frames in 5.0 seconds = 6013.876 FPS
28783 frames in 5.0 seconds = 5756.410 FPS
30555 frames in 5.0 seconds = 6110.958 FPS
29488 frames in 5.0 seconds = 5897.554 FPS
29951 frames in 5.0 seconds = 5990.103 FPS
29520 frames in 5.0 seconds = 5903.865 FPS

```
and fgl_glxgears
```
Using GLX_SGIX_pbuffer
4005 frames in 5.0 seconds = 801.000 FPS
6006 frames in 5.0 seconds = 1201.200 FPS
7165 frames in 5.0 seconds = 1433.000 FPS
5081 frames in 5.0 seconds = 1016.200 FPS
4954 frames in 5.0 seconds = 990.800 FPS
4955 frames in 5.0 seconds = 991.000 FPS
4959 frames in 5.0 seconds = 991.800 FPS
4959 frames in 5.0 seconds = 991.800 FPS
4957 frames in 5.0 seconds = 991.400 FPS
4961 frames in 5.0 seconds = 992.200 FPS
4958 frames in 5.0 seconds = 991.600 FPS
4965 frames in 5.0 seconds = 993.000 FPS
4957 frames in 5.0 seconds = 991.400 FPS
4957 frames in 5.0 seconds = 991.400 FPS
4955 frames in 5.0 seconds = 991.000 FPS
4960 frames in 5.0 seconds = 992.000 FPS
4933 frames in 5.0 seconds = 986.600 FPS
4841 frames in 5.0 seconds = 968.200 FPS
4524 frames in 5.0 seconds = 904.800 FPS

```
Can sb tell if those results are ok? :)

---

### Post by sercal7 on 2008-01-15
To install and work an HD2600 mobility on ubuntu 7.10 is quite easy, just un "envy" search it in google and is a .deb package, and when it starts select automated ati istallation driver... it works, even for 3D acceleration... it only has some issues with compizfusion in accelerated aplication, so when you start a divx or a game just disable compiz... bye

---

### Post by cknight91 on 2008-02-06
Hey guys,

I came across this forum seeking help with my Radeon HD 2600 on my ASUS F3ka laptop. Except I am running Vista 32-bit. I have noticed that there are not any drivers for this card at the moment?

I am having probelms playing World in Crisis. The game isn't running at full graphics and randomly freezes. Sound will continue to work and it will still say the game is "running" under task manager so it isn't technically crashing. The freeze can happen after 5 minutes or an hour.

I feel like there is something I need to do to tweak the graphics card to get this to work correctly, however I can play WoW fine. Any help would be appreciated, thanks!

---

### Post by Yellow Pasque on 2008-02-06
> **cknight91 said:**
> Hey guys,

I came across this forum seeking help with my Radeon HD 2600 on my ASUS F3ka laptop. Except I am running Vista 32-bit. I have noticed that there are not any drivers for this card at the moment?

I am having probelms playing World in Crisis. The game isn't running at full graphics and randomly freezes. Sound will continue to work and it will still say the game is "running" under task manager so it isn't technically crashing. The freeze can happen after 5 minutes or an hour.

I feel like there is something I need to do to tweak the graphics card to get this to work correctly, however I can play WoW fine. Any help would be appreciated, thanks!
This is the wrong forum for that kind of thing. We don't support Windoze here.

---

### Post by dnzz on 2008-02-09
I have been using ubuntu for 1 year. I used to have Nvidia 6200go and I have changed my laptop to Toshiba A210-1AH with Ati Radeon Mobility HD2600.

When I install Ubuntu Gui does not start.

I have tried official drivers and Envy. Both way I see that "Your hardware does not need any restricted drivers"

Envy enabled compiz but when I try to run any 3D app Ubuntu fails.

fglrxinfo
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600
OpenGL version string: 2.1.7276 Release

```

```
$ glxgears
22370 frames in 5.0 seconds = 4473.837 FPS
22797 frames in 5.0 seconds = 4559.374 FPS
22805 frames in 5.0 seconds = 4560.860 FPS
22804 frames in 5.0 seconds = 4560.663 FPS

```

```
$ fgl_glxgears
Using GLX_SGIX_pbuffer
4575 frames in 5.0 seconds = 915.000 FPS
5455 frames in 5.0 seconds = 1091.000 FPS
5646 frames in 5.0 seconds = 1129.200 FPS
5653 frames in 5.0 seconds = 1130.600 FPS

```

any ideas to enable 3D support?

---

### Post by dbwalsh on 2008-02-19
Envy worked a treat, running compiz and full resolution for the first time on my Compaq 8510p (mobility radeon HD2600)

Not sure of stability yet, had one glitch but definitely working

D

---

### Post by kml.krk on 2008-02-21
> **sandstig said:**
> Try using _[Envy](http://albertomilone.com/nvidia_scripts1.html)_, then when it says your card isn't recognized, select "Manual Install" and choose the latest ATI binaries. Make sure to click the button for removing your ATI drivers first (in Envy) before installing.

Thank You for your help! This method allowed me to install Radeon HD 2600 in my ASUS F3SA. The only thing I did differently is: I downloaded the newest version of envy and actually chose the automatic installation of ATI drivers - it installs the newest drivers from AMD website - the driver version is 8.4xxx. Envy automaticly configured my XORG file. Everything works like a charm now. I was able to play games and turn on the visual effects ON!

Cheers
KaMeL

---

### Post by sercal7 on 2008-03-07
do you have to disable compiz to play games or watching divx? with compiz enabled i always have black splashes in divx and 3d apps... and also without compiz I have some glitches in divx... even i got it in windows, only GOM media playes works right, vlc and others don't xp or ubuntu it's the same, any suggestion?

---

### Post by Clancy_s on 2008-05-17
As I said earlier I have a Mobility Radeon HD2600 in a Toshiba Satellite A200/S01.  Under Gutsy I was running the radeon HD driver.  The upgrade to Hardy borked that so I decided to give Envy a try (using the new packages in the Universe repository so it'd update auotmatically hereafter.

I used synaptic to do the install then ran Envy from the graphical install: it thought everything went well.  Unfortunately on reboot I had a 640 x 480 res with no option to increase it.  I took a look at my xorg.conf file which reported that I was using the fglrx driver ???

At the beginning of the file it said:

> # This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Since I'd seen it recommended elsewhere and didn't have much to lose I tried running the 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

logged out then back in again: lo, I now have the correct video resolution.

Screen movement is fine, I've not done any other testing yet.

---

### Post by Jorin on 2008-06-03
I've been having some issues with the new proprietary ATI driver (version 8.5 according to the website) on my Toshiba A200 as well.

Originally I thought it was working, but video playback looked grainy and pixelated. I read that this means my drivers weren't configured properly, so I tried Envy.

When I check my restricted drivers menu the driver says it is "in use" but not "enabled" (ie. the checkbox is blank).

I tried to install the driver through terminal with an sh command. It appeared to install correctly, but I got a black screen when I restart and I had to use xfix to recover my desktop.

---

