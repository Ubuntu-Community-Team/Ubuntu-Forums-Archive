---
title: "XFX Radeon HD 5670 Won't work on ubuntu (not supported?)"
date: 2010-03-02
forum: Hardware
---

### Post by Dungdae on 2010-03-02
I have just purchased a new graphic card to spice up things a bit.. 

I decided to start all over and make a clean Ubuntu install, so i reinstalled just after inserting the hardware.. At startup after updating packages and latest version (9.10) i let the ristricted drivers take care of installing the driver.

That didn't work very well.. when rebooting after the ubuntu icon shows up the first time, the screen goes black and the loading  stops tottaly nothing even happened when pressing ctrl-alt-F1.

I overwrited the old xorg.conf with the xorg.conf-backup file and tried to download the driver through ATI's website. I installed their driver, now after rebooting Ubuntu finishes the startup (i can hear the log in sound in the background) while the screen still displays af black screen (now with a "Out of range" message)

After installation of the ati-driver but before i reboot for the first time, i'm not able to enter the ati catalyst center.. i get this message

> Initialization error: 
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Does this mean that there are no support for that card yet? 
Is there anything I can do to get install a working driver??

Hope someone can help..

---

### Post by gordintoronto on 2010-03-02
Here's an extract from a review on Newegg:
"Cons: Isn't supported in Linux yet (at least not by the open source xorg-ati-radeon or radeonhd drivers), not surprised...Too new, but I was aware of this going in and anticipate this being resolved possibly within the year. At least I get a desktop with a tolerable resolution, but no 3D and I don't get my panel's native resolution just yet. I might be able to work something out though. And since I was aware of the fact it was likely to not work in Linux yet, I am not taking any eggs off for it."

The user reviews for this product are among the worst I have seen.

---

### Post by Dungdae on 2010-03-02
Darn.. I saw that comming.. It's quite ironic though, cause the box claimes to be supported by windows, mac and linux!! Well thank you for the help!

---

### Post by patrickjlbyrne on 2010-04-10
Yeah me too. I am very happy with the card on windows, it is low power and runs Doom3 just fine.

If anyone finds a distro that does support it I would like to hear about it.

---

### Post by zzhao on 2010-05-04
I have seen people pointing to the link on this page for the driver. Maybe this would help?
[http://www.ati-forum.de/general/downloads/driver/2470-treiber-f%C3%BCr-hd5400-serie/?68ff7617]("http://www.ati-forum.de/general/downloads/driver/2470-treiber-f%C3%BCr-hd5400-serie/?68ff7617")
BTW, does any one already tried ubuntu 10.4 with this card?

---

### Post by patrickjlbyrne on 2010-05-04
I don't know about that driver. It seems to me that if the driver that comes by default with a distribution's install disk won't work then it is kind of hard to install the distribution in the first place even before you can get hold of an appropriate driver.

Yesterday I managed to get Ubuntu 10.04 installed without too much trouble. I downloaded the alternate install disk and did a text-only install. This worked fine but when I rebooted after installation it failed to start X-Windows. There is a fallback menu though which lets you start X with a basic driver configuration. From there I installed the ATI Catalyst driver and control centre. This is shown in the hardware drivers applet - I think it pops up an icon on the status bar as soon as you start. Everything worked fine after that.

So, it is still a problem that boot disks won't boot with this card, but installing using the alternate disk is still quite do-able.

---

### Post by jasonbauer on 2010-05-15
I just made the same mistake. CRAP!!:(

---

### Post by Ste3f on 2010-05-29
Had the same problems. Started up using low graphic stuff and waited for the driver prompt to come up and installed it. After that is was fine.

That was the 32 bit story. Tried to upgrade, via fresh install using USB stick, to 64 bit. Couldn't get it to work. 

Anyone any idea how to get it to work?

---

### Post by mschira on 2010-06-02
Yea I got a Saphire 5670. I bought it because it has one DVI and two HDMI connectors, and doesn't waste space with VGA.

I just installed Ubuntu 10.4x64 and found that right now the card only works using VGA. So put the DVI2VGA adapter on then connect the screen via VGA and it works.

Of course that is not ideal, I haven't figured yet out how to switch the card to use the DVI connector...
Right now I hope switching to the generic AMD driver will solve this - but I have yet to try 
So any help appreciated...
best

---

### Post by yozgoesdigital on 2010-06-03
Got here also the Sapphire 5670 and DVI worked without any problem with the propietary drivers. I gues it is the version which comes with 10.4 (so not the newer 10.5)

---

### Post by - Mikael - on 2010-08-30
I have XFX HD 5670, and it works fine with ubuntu 10.10 beta :) no problem at all, no drivers to be installed first :)

---

### Post by Claus7 on 2010-09-25
Hello,

with or without xfx does this make any difference?

*EDIT1: XFX and Sapphire (in my case) are different company suppliers-card manufacturers of the same amd/ati/radeon gpus or motherboards since AMD no longer sells Radeon cards directly at the retail level. *

No matter what I have been trying since a week now, I cannot make this card working with 10.10 beta as it should.

Initially, since alpha releases, without fglrx things installed from synaptic, the card was working really nice crisp and clear without compiz working though. That was not a big deal.

Since some last updates my resolution was ruined and no matter what I tried:
i) aticonfig --initial 
ii) install fglrx package 2:8.780
iii) write manually the xorg.conf file

I was not able to make it work.

The best thing I can get is having removed xorg.conf (as initially), yet now with available resolution options which in their entirety are not supported by my card.

Every effort except the one described, was giving me either a black screen after the ubuntu logo or a  black screen with terminal access. On the latter after typing startx I got the message: no screens found.

From system->administration->additional drivers ati fire gl is activated and currently in use, whereas the ati drivers catalyst control center (from system->preferences) gives me errors like those expressed already.

Some questions I have about ati drivers are:

1) what is the difference between ati and radeon? (I'm pretty new to this...)

[I]EDIT1: ATI technologies is a company that produced gp units and motherboard chipsets. In 2006, the company was acquired by Advanced Micro Devices (AMD) and was renamed to its present name, yet with changes to come.

ATI Radeon is the brand behind the gpus.[/I]

2) installing fglrx installs also fglrx-amdcccle package. Is this enough?

[I]EDIT2: That would need also fglrx-modaliases and jockey-gtk packages installed. The kernel source fglrx package does not seem necessary. 

Not sure about the fglrx dev files and the xserver ones.[/I]
 
3) there are some radeon and fglrx xserver video files. Which of these should be installed without causing conflicts? Maybe all of them?

[I]EDIT: Think this has to do whether fglrx is enabled or not, as that package does not have a direct xserver file, with the latter corresponding to the open source drivers.

Also this gives an insight of how to avoid it in case there is one:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)[/I]

4) Someone can either have installed the drivers from ati's (radeon's?) website. These are the proprietary drivers?

*EDIT1: Yup they are! They can be installed either from synaptic which correspond to the name fglrx or manually via the amd's website. Both of them refer to the proprietary drivers. *

5) The open source ones are those comprised in the fglrx package?

[I]EDIT2: No, these are the proprietary drivers. The open source ones, are those find in synaptic with names as xserver-xorg-ati and xserver-xorg-radeon.

Both of them do not seem to offer the 3D acceleration effects the newer cards can produce.[/I]

6) If the answer in q5 is negative, which are the open source drivers for this card?
...

Hope it is a problem on beta maverick only and that my questions are pretty basic for people using these cards.

Thank you,
Regards!

ps: edit1 -> source wikipedia
ps: edit2 -> ati unofficial linux driver wiki

---

### Post by Claus7 on 2010-09-28
Hello,

I can confirm that this card is supported from ubuntu maverick 10.10 using the proprietary drivers from synaptic package manager (fglrx) and adjusting accordingly the xorg.conf file. 

In order to make it work I had to do a lot of tampering with either the installation of the drivers or the tweaking of xorg.conf. My computer has not a fresh installation of maverick on it, so this might have caused more headaches on achieving a good result. 

I faced many problems during the process which I do not remember with much detail. Here, I will try to gather as much as I remember...

So, the packages from synaptic which are needed are:
> fgrlx
fgrlx-dev
fgrlx-amdcccle
fglrx-modaliases
jockey-common
jockey-gtk

It might be that not all of these are needed, yet up to know they to not impose any problem and seem to be necessary.

What I uninstalled in order to avoid conflicts was:
xserver-....(vesa, nouveau, nv, ati, radeon) and whatever had to do with nvidia (before there was nvidia there :(, had nice memories...).

Commands like:
fglrxinfo
fgl_glxgears

were producing segmentation fault.

The command (find driver in use):
```
perl -n0077 -e 'print "Using driver $1 v$3 by $2.\n" while /Module (radeon|fglrx|intel|nvidia|nv|vesa): vendor="([^"]+)"\n.*version = (\S+)/img;' /var/log/Xorg.${DISPLAY:1:1}.log
```

produced either vesa and radeon (both) or nothing.

The command glxinfo... I do not remember... Either nothing or something about sgi...something...

Finally:
> fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.0.10237 Compatibility Profile Context

I got also errors about no screen found, that the resolution was out of range (pressed the button source/exit on my monitor to check it sometimes, while the screen was dark black!). In order to avoid black screen and rebooting I had to press Ctrl+Alt+F2, change the contents of xorg.conf or whatever I thought necessary and then something like startx to bring back the screen.

I attach the xorg.conf file, which seems (I'm writing from such a configuration) to be a descent one. I can also see 1080p videos without any problem full screen! I have not tested extensively, yet things seem to work ok. With the error: no screens found, I tampered a little with old xorg files and new ones resulted from the command aticonfig --initial. 

Hope it helps in similar cases.
Over and out for the time being.

Regards!

PS: The third line about the resolution was a combination from older files and the result of the command xandr ([http://ubuntuforums.org/showthread.php?t=1321224&page=2](http://ubuntuforums.org/showthread.php?t=1321224&page=2))

---

### Post by Claus7 on 2010-09-29
Hello,

with some more tweaking I came up to this attachment.

Regards!

---

### Post by Claus7 on 2010-10-08
Hello,

and...this.

Regards!

---

### Post by mcclurec on 2010-11-08
Confirmed - was able to get my system working with this setup. Purged all Nvidia packages.

QUOTE=Claus7;9901012]Hello,

I can confirm that this card is supported from ubuntu maverick 10.10 using the proprietary drivers from synaptic package manager (fglrx) and adjusting accordingly the xorg.conf file. 

In order to make it work I had to do a lot of tampering with either the installation of the drivers or the tweaking of xorg.conf. My computer has not a fresh installation of maverick on it, so this might have caused more headaches on achieving a good result. 

I faced many problems during the process which I do not remember with much detail. Here, I will try to gather as much as I remember...

So, the packages from synaptic which are needed are:


It might be that not all of these are needed, yet up to know they to not impose any problem and seem to be necessary.

What I uninstalled in order to avoid conflicts was:
xserver-....(vesa, nouveau, nv, ati, radeon) and whatever had to do with nvidia (before there was nvidia there :(, had nice memories...).

Commands like:
fglrxinfo
fgl_glxgears

were producing segmentation fault.

The command (find driver in use):
```
perl -n0077 -e 'print "Using driver $1 v$3 by $2.\n" while /Module (radeon|fglrx|intel|nvidia|nv|vesa): vendor="([^"]+)"\n.*version = (\S+)/img;' /var/log/Xorg.${DISPLAY:1:1}.log
```produced either vesa and radeon (both) or nothing.

The command glxinfo... I do not remember... Either nothing or something about sgi...something...

Finally:


I got also errors about no screen found, that the resolution was out of range (pressed the button source/exit on my monitor to check it sometimes, while the screen was dark black!). In order to avoid black screen and rebooting I had to press Ctrl+Alt+F2, change the contents of xorg.conf or whatever I thought necessary and then something like startx to bring back the screen.

I attach the xorg.conf file, which seems (I'm writing from such a configuration) to be a descent one. I can also see 1080p videos without any problem full screen! I have not tested extensively, yet things seem to work ok. With the error: no screens found, I tampered a little with old xorg files and new ones resulted from the command aticonfig --initial. 

Hope it helps in similar cases.
Over and out for the time being.

Regards!

PS: The third line about the resolution was a combination from older files and the result of the command xandr ([http://ubuntuforums.org/showthread.php?t=1321224&page=2](http://ubuntuforums.org/showthread.php?t=1321224&page=2))[/QUOTE]

---

### Post by Kopasakis on 2011-03-09
so i just picked up a xfx radeon hd 5670... and when i go to boot i get absolutely nothing. when i go to boot into the into the fail safe driver... i get nothing, it works in my windows partition, but nothing in ubuntu :( help

---

### Post by Yellow Pasque on 2011-03-10
Boot to recovery console. Choose root prompt with networking. Install driver like so: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by Kopasakis on 2011-03-10
i'm good until i type ```
$ sh ati-driver-installer-[11-2]("http://wiki.cchtml.com/index.php?title=11-2&action=edit&redlink=1")-x86.x86_64.run --buildpkg Ubuntu/maverick

```

then i get an error 

```
Error: The distribution ubuntu is not supported 
Removing temporary directory: fglrx-install.0ecexd
```

any ideas?

---

### Post by Yellow Pasque on 2011-03-10
Capitalize the 'U'
LiNUX iS cASe SeNSItivE

---

### Post by Kopasakis on 2011-03-10
lol thanks now i have another problem 

i entered (no cheating this time;p) ```
sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/mavrick
```

 and got:

```
Error: Distro Version Entered Incorrectly or not supported, use --listpkg to indentify valid distro versions
Error: Distro Version Entered Incorrectly or not supported, use --listpkg to indentify valid distro versions 
Removing temporary directory:fglrx-install.NHveyG 
```

when i enter ```
--listpkg
```

I get 

```
--listpkg: command not found 
```

---

### Post by Yellow Pasque on 2011-03-10
you spelled 'maverick' incorrectly and the command for listing packages is:
```
sh ati-driver-installer-11-2-x86.x86_64.run --listpkg
```

---

### Post by Kopasakis on 2011-03-10
i could kiss you, now one questiondo i have to do aticonfig --initial -f? because i get the error aticonfig: command not found and of course the black screen

---

### Post by Yellow Pasque on 2011-03-11
So you installed the fglrx packages and no aticonfig? DId you try to install the ATI driver previously? If so, see: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot)

> i could kiss you
Unless you're a cute girl, I would prefer if you didn't. Gifts of money, bourbon, and/or other recreational drugs are highly encouraged though.

---

### Post by Kopasakis on 2011-03-11
ok i type in

```
update-alternatives --get-selections |grep gl_conf
```

and in response i get 

```
gl_conf                                   auto                      /usr/lib/nvidia-current/ld.so.conf
```

the board is an m2n-mx se and has, at lease in windows a nvidia chip set, plus before this card i had an nvidia card, so... any ideas?

---

### Post by Yellow Pasque on 2011-03-11
Go into synaptic and purge/completely remove nvidia packages.

---

### Post by Kopasakis on 2011-03-11
you are a good man, if you ever find yourself in cleveland let me know, and i'll get you a drink

---

### Post by Yellow Pasque on 2011-03-11
Cheers. I assume you're up and running? Mark thread solved then, and enjoy your computing ):P

---

### Post by MondoTofu on 2011-04-05
Very Simple Solution... use vesa.

No need to install ATI proprietary drivers.

Please look at this bug report.

[https://bugs.launchpad.net/ubuntu/+bug/569037](https://bugs.launchpad.net/ubuntu/+bug/569037)
[https://bugs.launchpad.net/ubuntu/+bug/569037]("https://bugs.launchpad.net/ubuntu/+bug/569037")

---

### Post by Claus7 on 2011-10-07
Hello,

I would like to report, that after a long time, I'm now using the same card mentioned here, with Catalyst 11.9 (proprietary fglrx driver), from amd's website, for 64bit ubuntu maverick and is working really nice.

I unistalled my previous proprietary driver by:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.move
```

and installed the new one:
```
chmod 755 ati-driver-installer-11-9-x86.x86_64.run
sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/maverick
sudo dpkg -i fglrx*.deb

```
created a new xorg.conf file:
```
sudo aticonfig --initial -f
```

forced the driver to adopt changes from xorg.conf file:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

and rebooted.

The final xorg.conf file looked like:
> Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "UseFastTLS" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

and the result of the commands to verify installation:
```
fglrxinfo

```

resulted in:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.1.11079 Compatibility Profile Context

and fgl_glxgears works as well.

Regards!

---

### Post by Claus7 on 2011-11-02
Hello,

same thing with amd's catalyst 11.10 for linux 64 bit. In ubuntu maverick that is.

Regards!

---

### Post by Claus7 on 2011-12-17
Hello,

even if 11.11 and on versions of ati drivers have opencl support in the same package, my humble experience shows that 11.10 was their best driver to date (11.12).

I have some glitches with cairo clock and more flickering when opening vmd via ssh. Other things as usual I guess.

Regards!

---

### Post by SeePU on 2011-12-17
Over a year and ATI drivers are still crap including the flaky open source drivers.   The FOSS drivers aren't all encompassing all features including almost zero support with power control.    So, your fans are going 100% and this is important if you have a newer laptop with AMD graphics.

But, even with a desktop card, you will have tons of glitches and bugs.

When will ppl learn that AMD has no intention of EVER supporting Linux with their graphics (ATI) division?!?

Why do people buy amd graphics cards if they use Linux.  Unless, you intend to experiment or have loads of cash to throw away, what's the point?   The support is shoddy, worse than Nvidia who doesn't open source their drivers but at least you don't have as many issues.

---

### Post by MoreOrLess on 2011-12-17
@SeePU: please do not bump threads to posts rants. The radeon driver and the open-source graphics stack in general work fine in a lot of usage scenarios.

---

### Post by Claus7 on 2012-01-25
Hello,

with amd catalyst 12.1 I can see slight nice improvements.
Just to mention that during installation it proposes (from the options) compilation for ubuntu maverick specifically (64 bit that is) and it gives a window environment. Procedure exactly the same as before.

Regards!

---

### Post by Claus7 on 2012-01-25
Hello,

some tweaking so as for FPS (frames per second) to work nicely:

1) System->Preferences->Amd Catalyst Control Center (Administrative)
[LIST]Display Options->Tear Free (disable)
[*]3D->More Settings->Wait for vertical refresh (far left : off)

if you enable tear free, then you have to adjust anew the vrefresh option
[/LIST]
2) System->Preferences->CompizConfig Settings Manager-> go to General Tab -> then to General Options->Display Settings and there:
**UN**check: Sync To VBlank

Then by typing:
 ```
glxgears
```
you get:
> 14276 frames in 5.0 seconds = 2854.993 FPS
13066 frames in 5.0 seconds = 2613.034 FPS
12087 frames in 5.0 seconds = 2417.233 FPS
11652 frames in 5.0 seconds = 2330.253 FPS
11791 frames in 5.0 seconds = 2358.199 FPS
13825 frames in 5.0 seconds = 2764.801 FPS
12227 frames in 5.0 seconds = 2445.337 FPS
12787 frames in 5.0 seconds = 2557.273 FPS
14086 frames in 5.0 seconds = 2817.100 FPS
12683 frames in 5.0 seconds = 2536.442 FPS
12859 frames in 5.0 seconds = 2571.610 FPS
13067 frames in 5.0 seconds = 2613.340 FPS
13135 frames in 5.0 seconds = 2624.147 FPS
13117 frames in 5.0 seconds = 2623.370 FPS
12629 frames in 5.0 seconds = 2525.729 FPS
13910 frames in 5.0 seconds = 2781.882 FPS

and by typing:
```
fgl_glxgears
```
you get:
> 4956 frames in 5.0 seconds = 991.200 FPS
4973 frames in 5.0 seconds = 994.600 FPS
5154 frames in 5.0 seconds = 1030.800 FPS
4881 frames in 5.0 seconds = 976.200 FPS
5203 frames in 5.0 seconds = 1040.600 FPS
6006 frames in 5.0 seconds = 1201.200 FPS
5829 frames in 5.0 seconds = 1165.800 FPS
5032 frames in 5.0 seconds = 1006.400 FPS
5448 frames in 5.0 seconds = 1089.600 FPS
5150 frames in 5.0 seconds = 1030.000 FPS
5081 frames in 5.0 seconds = 1016.200 FPS
5452 frames in 5.0 seconds = 1090.400 FPS
4855 frames in 5.0 seconds = 971.000 FPS
5058 frames in 5.0 seconds = 1011.600 FPS
5487 frames in 5.0 seconds = 1097.400 FPS
4887 frames in 5.0 seconds = 977.400 FPS
4903 frames in 5.0 seconds = 980.600 FPS
5199 frames in 5.0 seconds = 1039.800 FPS

Hope it helps,
Regards!

---

### Post by Claus7 on 2012-02-26
Hello,

> **Claus7 said:**
> Hello,

...
I have some glitches with cairo clock and more flickering when opening vmd via ssh. Other things as usual I guess.

Regards!

my cairo-clock was not working as it should, so I followed this here:
[http://osnovice.blogspot.com/2007/04/nice-desktop-analogue-clock.html](http://osnovice.blogspot.com/2007/04/nice-desktop-analogue-clock.html)

and with the command:
```
sudo apt-get install cairo-clock
```

I installed cairo-clock which appeared under:
Applications->Accessories->MacSlow's Cairo-Clock.

The result is really amazing with the smoothness and nice quality of colours of the clock.

I would like it to be placed on top left corner of my screen. I can either execute the command:
```
cairo-clock --width 200 --height 200 --xposition 970 --yposition 30 --seconds --date --taskbar
```

(don't forget the & sign if you would like it to stay if you close the terminal)

or just click it from Applications and Accessories menu (and make its size 150).

I do not know if I can implement it under cairo-clock though, which would have been nice...

The flickering with vmd via ssh in the latest version is not so annoying (tear free option is off).

Regards!

---

### Post by Claus7 on 2012-03-10
Hello,

with amd catalyst 12.2 I can see slight nice improvements.
No window environment this time. Procedure exactly the same as before.

EDIT: 12.3 slightly more improved...

Regards!

---

### Post by Claus7 on 2012-08-22
Hello,

it seems that catalyst 12.8 on ubuntu maverick using this card is the best solution so far for my system.

Problem with cairo clock showing seconds is almost gone (some minor trembling every 3 seconds or so) and using vmd via ssh is unhindered. 

So far so good then. :KS

Regards!

edit: trying the catalyst 13.4 at the time, I was able to see that wine was whining for missing directx 9. I tried to install directx, yet to no avail.
The moment I tried to invert back to 12.10 catalyst driver, I faced some errors as well, mostly because the previous tricks of removing the driver did not work. In case someone installs 13.4 and wants to revert back to older drivers then try the command:
sudo sh /usr/share/ati/fglrx-uninstall.sh
All the rest are working as mentioned in this post. My system is working as before using catalyst 12.10.

---

