---
title: "Quick ATI Radeon HD 4870 (RV770) 3D setup guide"
date: 2008-08-03
forum: Hardware
---

### Post by kgk on 2008-08-03
The fglrx drivers give you 2D and all resolutions, but no 3D acceleration.  here's how I managed to get mine working.



Open Synaptic Package Manager, search for 'fglrx'


The only packages I have installed are "fglrx-controll", "jockey-common", "jockey-gtk", "xorg-driver-fglrx" and "xserver-xorg-video-ati"



Download the 8.7 ATI drivers: [http://www2.ati.com/drivers/linux/ati-driver-installer-8-7-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-8-7-x86.x86_64.run")

Run that file

> sudo sh ati-driver-installer-8-7-x86.x86_64.run

Do auto install.


Open the xorg config file:

> sudo gedit /etc/X11/xorg.conf

Scroll down to:
> 
EndSection
Section "Extensions"
Option "Composite" "**X**"
EndSection

Replace whatever the X value is ("off", "0", whatever) with "1"

Save and close.

> sudo aticonfig --initial

Ctrl-Alt-Backspace to restart x


Go to _System-Preferences->Appearance Preferences->Visual Effects_, and enable the custom settings

Voila, 3D acceleration should be enabled and compiz should work.


To check, mess with the compiz effects, or click _Applications->ATI Catalyst Control Center_.  If it loads, it's working.


This is after being up all night setting up various different things and finally stumbling across something that worked for me with my 4870.  I don't think I left anything out, but I am half asleep.  ](*,)

So if these instructions give you any trouble post something here and I'll likely be able to help.  


And for the love of god,

_Do not install xgl_ after installing the 8.7 driver, it'll turn your desktop into monstrous glitchy mess and you'll have to boot into recovery or exit xorg and use terminal to uninstall it.  I only say this because the instructions I've seen when you google for 4870 instructions tell you to do this because of the older models needing it to work.

---

### Post by Grimmwolf on 2008-08-03
I wonder if you can display videos without flickering while compiz is activated. It is quite annoying on my computer.

---

### Post by kgk on 2008-08-03
> **Grimmwolf said:**
> I wonder if you can display videos without flickering while compiz is activated. It is quite annoying on my computer.

Ah, I hadn't tried to play an avi file yet.  Yea I see that problem now.

Same with the default and with VLC player.  Going to try a few solutions and report back.  ](*,)](*,)

Note: this only affects video played in the movie player or VLC (i.e. avi files, wmv files), and not Flash video embedded in Firefox as Youtube works fine.


Of the top of my head I'm guessing it has something to do with refresh rate, but I thought that the whole screen would be flickering and not just the small VLC window when video is playing.

Weird.

---

### Post by kgk on 2008-08-03
FOUND IT!  :guitar::guitar::guitar:


This thread: [http://ubuntuforums.org/showthread.php?t=763649]("http://ubuntuforums.org/showthread.php?t=763649") discusses the problem relating to compiz + video flickering on 8.4 Catalyst drivers and newer.  The solution applies to 4870 cards as well.

The solution is as follows:

> If you want to fix the flickering widowed video problem you can edit the appropriate sections of your xorg.conf to look like this:

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
Option "AIGLX" "on"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "XAANoOffscreenPixmaps" "on"
Option "TexturedVideo" "off"
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "Textured2D" "on"
Option "UseFastTLS" "1"
Option "BackingStore" "on"
EndSection

Section "Module"
Load "glx"
EndSection

Section "DRI"
Group "Video"
Mode 0666
EndSection

Section "Extensions"
Option "RENDER" "Enable"
Option "DAMAGE" "Enable"
Option "Composite" "Enable"
EndSection

Then either save and close it or,

Run, in a terminal:

sudo aticonfig --input=/etc/X11/xorg.conf

Then Ctrl-Alt-Backspace to restart x.  You'll have compiz and video won't flicker.

---

### Post by NeoGreen on 2008-08-03
Quick question, did you add the configuration you posted on to X11 config?

---

### Post by kgk on 2008-08-05
> **NeoGreen said:**
> Quick question, did you add the configuration you posted on to X11 config?

No, only xorg.

---

### Post by Ubuntiac on 2008-08-08
Hi KGK,

Whatever I try with this I keep having it fall back to VESA. I've got the full details over at:
[http://ubuntuforums.org/showthread.php?t=883594](http://ubuntuforums.org/showthread.php?t=883594)

---

### Post by Ubuntiac on 2008-08-10
I finally got this to work on a vanilla install of 8.04 *however* it borks rather nastily the moment the kernel / restricted modules are updated.

I would *strongly* recommend that rather than doing the auto install that people follow the "Manual Method" part of the guide here instead:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29)

Just make sure that you do the "finishing the install" part at the end and you'll have a far more stable install that doesn't conflict with ubuntu packages and survives upgrades.

Happy days. Wobbly windows and Nexuiz fragging ahoy!

Oh, and thanks for the composite tip.  :D

---

### Post by Grimmwolf on 2008-08-11
Thanks for the solutions, I will test them when I get home. I totally forgot about this thread. :)

---

### Post by Grimmwolf on 2008-08-11
The manual installation had the bug:
xorg-driver-fglrx (--configure):
ErrorMessage: subprocess pre-installation script returned error exit status 2

I was unable to complete the guide because of that error.


The xorgconf change worked fine however, thank you very much. :)

---

### Post by Torqumada286 on 2008-08-19
Not quite working for me.  I followed the instructions, but I still don't have 3D effects.  I wonder if this has something do with with the fact that I can't get any kernel higher than 14 to work on my system for some strange reason?  Any ideas?

Torqumada

---

### Post by illmortal on 2008-08-25
Nice write up!

I have a question though. Supposedly the 4870 runs really high/hot during IDLE and there's an .ini file that could be modified to lower the idle. Has anyone by any chance taken the time to modify this file?

---

### Post by dokuro on 2009-04-28
has any of you had any problem in trying the ubuntu 9.04 with this video card, mine allways hangs on start up, i blame ati's driver because after installing it, is when i got the problem.

the driver i intalled was the lattest 9.4; i need to try older versions to see if it helps, but we could lend a had to Xorg development team.

---

### Post by ropsu on 2009-08-14
> **dokuro said:**
> has any of you had any problem in trying the ubuntu 9.04 with this video card, mine allways hangs on start up, i blame ati's driver because after installing it, is when i got the problem.

I'm having this issue with fresh install of Kubuntu Jaunty (9.04). Trying to update drives through shell.

[ Found updated installation guide for Jaunty here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start").

---

### Post by ropsu on 2009-08-14
[B][COLOR="Red"]EDIT: may not work (did not solve my problems), see nex post!
[/COLOR][/B]
> **ropsu said:**
> I'm having this issue with fresh install of Kubuntu Jaunty (9.04). Trying to update drives through shell.

[ Found updated installation guide for Jaunty here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start").

It worked, but installing driver manually gave some errors - flgrx-installation seems to require kernel source, which it at first did not find. I just needed to find out what source-folder existed in my hd:
-->see what subfolder of /lib/modules/ has kernel-subfolder
for example in my computer there were two possibilities 
/lib/modules/**2.6.28-11-generic**  and
/lib/modules/**2.6.28-14-generic** 
and only first one had subfolder **kernel**

So, I rebooted pc, chose in grub **2.6.28-11 (recovery mode)**, selected later on to boot without desktop environment and did everything again from the beginning. Done - working.

---

### Post by ropsu on 2009-08-14
> **ropsu said:**
> It worked

...for a while. I may have more than just one problem, kwin is crashing all the time. 

Before installing drivers ubuntu used to hang during bootup or login, now it just hangs a few minutes later.

---

### Post by markbuntu on 2009-08-14
You should use the latest driver from ati and just run the installer. If you do not remove old fglrx drivers before installing new ones you will have problems, guaranteed.

---

### Post by ropsu on 2009-08-18
> **markbuntu said:**
> If you do not remove old fglrx drivers before installing new ones you will have problems, guaranteed.

Okay, I see. Well, I'm trying once again. I've been installing Kubuntu now for quite a few times, and the problems exists with a clean Kubuntu Jaunty alternative and also with a live-cd -installation. Running Kubuntu on Live-cd and from local hd installation are both hanging pretty soon after first graphical stuff shows up. Screen hangs always sooner or later, dispite whatever I try. Mandrake and Windows 7 RC are running fine on the same pc, so harware is not broken. 

If guess my mistake is **not to uninstall** drivers which came with installation disk. It is a bit confusing, since [ATI guide]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf") talks about
[LIST]
[*]Uninstalling the ATI **Linux Proprietary** Driver and 
[*]Installing the ATI **Proprietary Linux** Driver with their ATI Proprietary Linux Installer
[/LIST]
I'd say this could be a bit clearer and I think this is where I should have been more focused. I'll see it in a moment...

---

### Post by markbuntu on 2009-08-18
Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

This includes the driver offered by hardware manager and any driver aquired with Envy.

---

### Post by ropsu on 2009-08-18
Nope, I did not succeed. 

1) installed again Kubuntu 9.04 (alternative install cd)
2) booted to shell (no graphical environment)
3) removed all fglrx-related packages that were present
```
apt-cache search fglrx
```
and repeatedly removed all listed packages (some of them were not there, though)
```
apt-get remove XXX

```
Downloaded and executed ATI driver ([most recent one]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English"))
```
mkdir /usr/share/ati
cd /usr/shar/ati
wget http://www2.ati.com/drivers/linux/ati-driver-installer-9-7-x86.x86_64.run
sh ./ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty
```
which did download and install some more packages (no errors, but it took a lot longer this time with all package downloading and all). Script generated some installation packages in */usr/share/ati*. 
These packages I installed as guided in [Ubuntu Jaunty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Before_you_start"), since ATI's own Installation guide is for installing stuff through gnome/kde-environment (which I can't get into before I manage to install working drivers correctly). 

And after all this... [COLOR="DarkRed"]**it hangs again**[/COLOR], right after graphical login screen. 

If I try fglrxinfo, I get:
```
fglrxinfo
Error: unable to open display (null)
```
lspci says something like this abut ATI (I can't copy-paste stuff, I'm writing this on another mac):
```
lspci | grep ATI
01:00.0 VGA compatible controller: ATI Tehcnologies Inc RV770 [Radeon HD 4870]
01:00.1 Audio devide: ATI Technologies Inc HD48X0 audio
```

I'm stuck and I've been doing this for 10 days/evenings now and I have no idea what's wrong. Basically I just want to have a fresh Kubuntu installation on brand new pc which does not hang everytime I boot it. Every other problem I've had with Ubuntu have been pretty easy compared to this.

(I'm sorry if it sounds like I'm wining, I'm kind of, well, tired at the moment for this...)

---

### Post by markbuntu on 2009-08-18
Did you do

sudo aticonfig --initial

You really need to do that. Or try

sudo aticonfig --initial -f

If you have a HD4870x2 you need to do

sudo aticonfig --adapters=all --initial -f

---

### Post by AldenIsZen on 2009-08-18
> **ropsu said:**
> Nope, I did not succeed. 

...

```
mkdir /usr/share/ati
cd /usr/shar/ati
wget http://www2.ati.com/drivers/linux/ati-driver-installer-9-7-x86.x86_64.run
sh ./ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty
```
...


 Well, I uninstalled the Nvidia driver through the hardware manager, and the uninstalled from Windows 7. Rebooted, installed ATI driver in Windows 7, rebooted again. Came back next night and booted Ubuntu, got white screen after logging in (I would see the gnome panels briefly, maybe up to ten seconds or so) and then I could rotate the Compiz cube, even see the top and bottom pictures, reflection, etc. But it was very choppy.

 I followed these instructionas and am in like flint! Thanks! Forgot how to use wget, etc. Still a nub although been using Ubuntu since Breezy Badger. (5.10)

---

### Post by ropsu on 2009-08-20
> **markbuntu said:**
> Did you do

sudo aticonfig --initial

You really need to do that. Or try

sudo aticonfig --initial -f


Yes I did, both of them. I'm quite sure I followed all instructions but I guess my hardware is just not what ATI driver can handle (or maybe I'm just missing required packages which I can't find in any repositories). I'll give it a try again in a few months with a live-cd. 

Thanks anyway, markbuntu!

---

### Post by bultsaxnicke on 2009-08-25
I don´t get this, ive done exactly as you said, but Catalyst Center won't load, it says my drivers isnt working, and also i don't have the commands in my xorg.conf that you have, to make it all simple...

> # xorg.conf (X.Org X Window System server configuration file)
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
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


---

### Post by Yellow Pasque on 2009-08-25
The information in this thread is a bit outdated. Use this for proprietary driver install: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

