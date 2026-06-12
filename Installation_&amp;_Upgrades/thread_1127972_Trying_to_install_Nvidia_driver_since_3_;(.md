---
title: "Trying to install Nvidia driver since 3 ;("
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by T_1000 on 2009-04-17
I am trying to install nvidia graphic driver since 3 days. i have gone through many suggestions but didnt work. when i try to install manually by downloading driver from nvidia.com , it gives me some kernel error like" No Matching Precompiled kernel found" and then another error comes"no nvidia.ko found" and installation failes. when i try to install automatically  using Envy download manager, it install perfectly but my screen resolutions stucks at 600X480 and doesnt increases.

what should i do, please help me out?:(

---

### Post by inobe on 2009-04-17
hi and welcome :)

we are missing important information !

1) what version of ubuntu do you have.

2) tell us about your hardware, the model of your graphics card will do.

you can also open terminal and type

```
lspci
```

then hit enter, copy and past the output on your next post.

---

### Post by T_1000 on 2009-04-17
I have installed latest ubuntu 8.10. this is overall my pc config. its old.
Intel 845 motherboard
1.9ghz pentium 4
Nvidia Gforce 400MX 64Mb Graphic card
512 ddr2 ram
160 gb ata harddisk
15" microtek lcd monitor

This is what you requested. please help me out

> 
root@deepak-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0b.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



---

### Post by inobe on 2009-04-17
> please help me out

i will try my best.

tell me about the driver you tried to install, what version was it ?

i suggest installing version 96, in synaptic select these packages to install.

nvidia-glx-96-dev
nvidia-96-kernel-source
nvidia-96-modealiases
nvidia-glx-96
jockey-gtk
jockey-common 

install those, you should then restart and check "hardware drivers"

---

### Post by zeex on 2009-04-17
hey!

[**_check this link out_**]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") , It should help. 

Explains pre-compiled kernel requirement in nvidia driver installation. 

Good luck :)

---

### Post by willpower232 on 2009-04-17
Envy or EnvyNG does a cracking job with my nvidia cards and is a lot less confusing!

See:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

for more information.

If I remember correctly, I had to install not the most recent one but the one before that to get it working properly but that might just be because the card in question was a couple of years old.

---

### Post by T_1000 on 2009-04-17
> hey!

check this link out , It should help.

Explains pre-compiled kernel requirement in nvidia driver installation.

Good luck 

after going through that , i restarted pc. but before login screen it cameup with error, Nvidia cannot be loaded and kept the same resolution again i.e low graphics ones.

---

### Post by zeex on 2009-04-17
> **T_1000 said:**
> after going through that , i restarted pc. but before login screen it cameup with error, Nvidia cannot be loaded and kept the same resolution again i.e low graphics ones.

It worked fine for me :| . couple of questions.

Did you remove X-org display driver before or after nVIDIA driver installation?

When you started nvidia driver file. It asks for kernel source before compiling right? It'll notify if linux source is not available.

At the end it asks for modifying Xorg.conf. Did you updated Xorg.conf right there?  

:: Check if the kernel-source you 've downloaded is of the same kernel that you are using. If it's a different kernel-image then it doesn't work. _**Kernel-image and kernel-source should be same.**_

For nVIDIA everytime you update kernel-image you need to recompile the nvidia driver for that version of kernel-image

---

### Post by T_1000 on 2009-04-17
i had removed the xorg as per instructions. and yes after following step it gave same kernel error. but still installation completed successfully. rebooted the system and then weird happened. after ubuntu loading screen my monitor goes off. even if I tries to off/on monitor. it goes off. 

so I chose the recovery mode and repaired the x server and then it placed my original resolutions again.ie. 600 X... 

so i am really couldnt figure out wheres the problem is.. is it kernel problems or monitors problem or graphic card problem.

one thing i want to mention is that same thing had happened when i had tried installing graphic drivers On Linux Debian distro. so what i think.. the problem may be with kernel or it could be with monitor... i have microtek 15" monitor which is 7 yrs old i guess.. but it runs perfectly with windows xp and other windows versions.

**check this**
> root@deepak-desktop:~# lsmod | grep nv
nvidia               4713492  0 
i2c_core               31892  4 saa7134,v4l2_common,tveeprom,nvidia
agpgart                42184  2 nvidia,intel_agp

so what shall be my further steps?

---

### Post by upchucky on 2009-04-17
the following is the proper way to get nvidia working when all the other workarounds fail. including Envy.


Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

---

### Post by kforum on 2009-04-17
im curious did the standard method of using the hardware manager not work for you? it downloads AND installs proprietary drivers, its quite simple.
what went wrong when using this method?

also, can you please show the `card0` section of your /etc/X11/xorg.conf
or if you dont know what i mean, simply paste the whole file.

---

### Post by T_1000 on 2009-04-17
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

---

### Post by T_1000 on 2009-04-17
i went through all the steps provided by Upchucky. but it didn't work out. after restartig the x server and i got this screen.

Ubuntu is Running in Low Graphics Mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) Unable to find a valid frame buffer device.
(EE) NV(0): Failed to open framebuffer device, consult waif this doesn't work from synaptic than we can alert launchpad of this bug and get it fixed !if this doesn't work from synaptic than we can alert launchpad of this bug and get it fixed !rinng and/or errors above for possible reasons
(EE) Screen(s) Found, But none have a usable configurations.

Then after pressing it showed another screen 

What would you like to do?
o Run Ubuntu in low-graphics mode for just this session
o Reconfigure graphics
o Troubleshoot error

and set back my original resolutions again. :( :(
i am ****** tired.. trying to figure out this piece of ****... :p

whats further suggestion?

---

### Post by inobe on 2009-04-17
i haven't quoted me or provided any update information for this 

> Re: Trying to install Nvidia driver since 3 ;(
Quote:
[QUOTE]please help me out
i will try my best.

tell me about the driver you tried to install, what version was it ?

i suggest installing version 96, in synaptic select these packages to install.

nvidia-glx-96-dev
nvidia-96-kernel-source
nvidia-96-modealiases
nvidia-glx-96
jockey-gtk
jockey-common

install those, you should then restart and check "hardware drivers" [/QUOTE]


have you tried my suggestion, if so' what went wrong ?


noticed some suggestions to manually install the kernel module, i think that would be great but you must consider having to reinstall the nvidia driver each and every time you update the linux image.

lets try to use synaptic, at least this way you will not need to reinstall your nvidia driver after an image update.

if this doesn't work from synaptic than we can alert launchpad of this bug and get it fixed !


note: nvidia drivers are not supported by Canonical

---

### Post by T_1000 on 2009-04-17
> have you tried my suggestion, if so' what went wrong ?


noticed some suggestions to manually install the kernel module, i think that would be great but you must consider having to reinstall the nvidia driver each and every time you update the linux image.

lets try to use synaptic, at least this way you will not need to reinstall your nvidia driver after an image update.

if this doesn't work from synaptic than we can alert launchpad of this bug and get it fixed !

yeah.. tried that way too.. i rebooted the system and now my monitor was getting off.. so i went to recovery mode and fix the x server and now its back to same resolutions again.. :(

> 
if this doesn't work from synaptic than we can alert launchpad of this bug and get it fixed !

sure.. i wandered around net and seen some similar problems with nvidia drivers which are unsolved...

---

### Post by kforum on 2009-04-17
> **T_1000 said:**
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

ok first and foremost the tool hardware drivers, that manages restricted drivers should install nvidia proprietary drivers flawlessly, as it does for me(nvidia 8600m gt).

second, a user a few posts back told you to purge and destroy the nv drivers... in my view thats a bad idea. there was also a series of fixer-uppers instructions that are not unusual in the ubuntu world, but people form the linux front are scared by it.

now, what you NEED to have the proprietary running is:
to have it loaded on the modules list, as the other post described.
in your /etc/X11/xorg.con you NEED something like ->
Section "Device"
    Identifier     "Video Card"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
	Option		   "NoLogo"	"true"
EndSection

and then up ahead:
Section "Screen"
    Identifier     "LCD Screen"
    Device         "Video Card"
    Monitor        "LCD Monitor"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

these are examples from MY xorg.conf... so adapting your xorg.conf we would have...

Section "Device"
	#Identifier	"Configured Video Device"
	#Option		"UseFBDev"		"true"
    Identifier     "card0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce XXX your card name here"
	Option		   "NoLogo"	"true"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"card0"
EndSection

and you may also need to add:
Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection
 
anywhere in that file, just to make sure...
now, ubuntu relies on auto detection, and thus gdm and friends to do things, while that works... what im describing to you is what you would need if you where on ANY linux, so its a fail-safe instruction.

if you already have installed the nvidia drivers then it all should work...
now if not, generally if everything fails when trying to install the proprietary drivers, 
you should dl the installer form the main site,
press alt+ctrl+fx(where x= 2 through 4) so you`ll get another tty, 
then type init 2 return.
then run the installer, it should all work, provided you have the source version of you kernel(downloadable through synaptics).
then you can reboot, or type init3 and go back.
at any rate, this works on pretty much any linux also, as far as im aware.

load the modules, fix the xorg.conf, and everything WILL work.
if you need monitor configs for you xorg.conf(in case it complains about that), post me a msg.

ALSO, if you run nvidia-settings, after you got the `driver` set to `nvidia`, then you can tell it to `write the settings to xorg.conf`, and it will write a more or less perfect xorg for you.

the only thing you might need to remove from the auto-nvidia-conf are the mouse and keyboard configs it will have added(if you use xorg 1.5~), or it may bork your keyboard when using X(gui interface), until you fix that.

i think that is probably ALL you need to know, msg me if anything else is needed.

cheers.

---

### Post by inobe on 2009-04-17
i would report the problem if it hasn't been already !

from the last post till now i have searched, even been to the nvidia forums then back here again.

i found this [http://ubuntuforums.org/showpost.php?p=6106745&postcount=1](http://ubuntuforums.org/showpost.php?p=6106745&postcount=1)

for step #1 don't use that beta, instead get the driver here
[http://www.nvidia.com/object/linux_display_x86_96.43.11.html](http://www.nvidia.com/object/linux_display_x86_96.43.11.html)

personally **i would skip #2** and do everything else assuming you already have the headers and the newer kernel source.


you should follow the other steps, good luck

---

### Post by T_1000 on 2009-04-17
everything here is messedup now.. i am really not getting what to do.. just feelin like helpless even having it. can anyone of you come to online chat on any messenger and guide me right from start... step by step..my ids are
[email]supreme_champion7@yahoo.co.in[/email]
[email]supremechampion7@gmail.com[/email]
[email]supreme_champion7@hotmail.com[/email]
bye goodnight.. c u tommrow..

---

### Post by T_1000 on 2009-04-18
I am now facing even more problems... i was installing 96 glx but it gives these error. 
>  apt-get install nvidia-glx-96

Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-glx-96
0 upgraded, 1 newly installed, 0 to remove and 271 not upgraded.
1 not fully installed or removed.
Need to get 0B/4473kB of archives.
After this operation, 13.9MB of additional disk space will be used.
(Reading database ... 119296 files and directories currently installed.)
Unpacking nvidia-glx-96 (from .../nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-96' clashes with `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-71'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


When i open add-remove application, there also i get error

> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


and when i try to install nvidia glx 96 from synaptic manager, it tells
> 
E: /var/cache/apt/archives/nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb: subprocess pre-installation script returned error exit status 2


why this is happening.. instead of problems getting sloved they are growing. 
:(  :(  :(

---

### Post by T_1000 on 2009-04-18
one good news. i can see nvidia in System-->administration--> Hardware Drivers profile now
but when i activates it, it starts a downloader, and then nothing happens.. it stays as it is,, 

and i still get this error when installing nvidia-glx-96
> root@deepak-desktop:~# apt-get install nvidia-glx-96
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-96
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4473kB of archives.
After this operation, 13.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvidia-glx-96
Install these packages without verification [y/N]? y
(Reading database ... 132797 files and directories currently installed.)
Unpacking nvidia-glx-96 (from .../nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-96' clashes with `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-71'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-96_96.43.09-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


i think we are very near to our target... what should be my next step?

---

### Post by kforum on 2009-04-18
i`ve seen a similar bug on ubuntu, if the hardware drivers shows up then your gtg, but it starts downloading and `seems` to freeze.
usually if you wait it out and then after its done downloading restart the pc it should be working...

are you using kubuntu, kubuntu had that problem...
to be honest though... if things brake too much you might consider a reinstall, this time around(if you havent yet) set you /home folder to a different partition.
(i`ve always done that, ever since i used computers... specially on my windows era)

anyways, after re-installing simply use the hardware drivers method i`ve yet to see it -not- work.

or you can try what i described in my other post, now or whenever...

if you havent understood a certain part of what i described, please ask.

cheers

---

### Post by T_1000 on 2009-04-18
yeah that would be my last option.. reinstalling.. if that didnt work too then.. i would consider my way too ol.. monitor to be a culprit..
:p
if you have any more suggestion, please let me konw.. i will try every possible action.

---

### Post by inobe on 2009-04-18
> **T_1000 said:**
> yeah that would be my last option.. reinstalling.. if that didnt work too then.. i would consider my way too ol.. monitor to be a culprit..
:p
if you have any more suggestion, please let me konw.. i will try every possible action.

there were so many things recommended i am uncertain to which you have followed and in what order !

stick with the first person that replies and provide as much information that you can, then if that person decides they have no other solution' you can then follow the third to reply on your topic.

T_1000 usually you would want to follow the first person that replies to your new topics, this eliminates mass confusion, you must also quote to each post that you are following......

simply said' i don't know what you did to get drivers in hardware drivers......

i am still willing to help' just tell me what you did.

EDIT: i hope you understand. also and out of respect to the forums' lets not use a messenger, if this gets solved i can clear up the confusion and it would benefit others.

---

### Post by T_1000 on 2009-04-19
> there were so many things recommended i am uncertain to which you have followed and in what order !

stick with the first person that replies and provide as much information that you can, then if that person decides they have no other solution' you can then follow the third to reply on your topic.

T_1000 usually you would want to follow the first person that replies to your new topics, this eliminates mass confusion, you must also quote to each post that you are following......

simply said' i don't know what you did to get drivers in hardware drivers......

i am still willing to help' just tell me what you did.

EDIT: i hope you understand. also and out of respect to the forums' lets not use a messenger, if this gets solved i can clear up the confusion and it would benefit others.

Yeah, i know we shoudn't use messengers. But this is the almost 6thday , trying to figure out the single problem.  My hands really paining, i can see unvidia,drivers n all those things in my dreams.. wandering all through my dreams . and this post had gone way to far, onthe 4th page yesterday. thats why i thought to call someone on messenger.

I have tried every suggestions that is listed here and in proper steps. Even i dont know how come it listed nvidia in hardware driver there. I got guy on messenger yesterday.. he is guiding me.. lets see what happenes. If its get solved, i will immediately post the solution.

---

### Post by T_1000 on 2009-04-19
ok, now i have reinstalled the unbutu 8.10 and directly started downloading of envyng. it downloaded something 52mb of packages. then run the envyng and enabled the most suitable & recommended version. after enbling it installed driver and restarted the system. take a look at my envyng.

[IMG]http://i39.tinypic.com/2h37m9d.png[/IMG]

after rebooting what has happened is, i can see nvidia driver information in system tools--> nvidia x server setting but i CANT see any driver information in system-->administration--> hardware drivers.

also it changed down my 800X resolutino to 640X480. but i can enable visual effects from change background--> visual effects.

this is where i am now, what should i do further?

---

### Post by zeex on 2009-04-19
> **T_1000 said:**
> ok, now i have reinstalled the unbutu 8.10 and directly started downloading of envyng. it downloaded something 52mb of packages. then run the envyng and enabled the most suitable & recommended version. after enbling it installed driver and restarted the system. take a look at my envyng.

[IMG]http://i39.tinypic.com/2h37m9d.png[/IMG]

after rebooting what has happened is, i can see nvidia driver information in system tools--> nvidia x server setting but i CANT see any driver information in system-->administration--> hardware drivers.

also it changed down my 800X resolutino to 640X480. but i can enable visual effects from change background--> visual effects.

this is where i am now, what should i do further?

Hi,

I hope you have nvidia-settings package installed. Open it from System -> Administration -> NVIDIA X server settings

[IMG]http://i39.tinypic.com/2k0rhu.jpg[/IMG]

Try this to change the resolution instead of System -> Preferences -> Screen resolution 

I am assuming you haven't tried this way. Since the effects are working so i guess the driver is working (almost). I think this might work cuz I am also out of ideas now. So do post the solution whenever you get it done.

Good luck :)

---

### Post by nealaustin on 2009-04-19
I just happened to come across a resolve for a Nvidia problem that I was having. I bought a new wide monitor and could only get it to work in 4:3 mode stretched. A while afterwardsI had tried to delete a partition (3rd boot Kubuntu) and totally screwed my HD. I recovered the original Compaq configuration and started all over :( . I originally started with XP added Ubuntu 7.10 and had upgraded every 6 months until 8.10.  Now I was forced to do a brand new install, pulled the Nvidia driver 180 out of the synaptic. Every quirky little problem that I had is gone and the 16:10 resolution is right there. Now please nobody flame me, but you know how Apple says that their Macs just work? That describes Ubuntu to a T.:D:D:D:D:D:D

---

### Post by T_1000 on 2009-04-20
> Try this to change the resolution instead of System -> Preferences -> Screen resolution 

I am assuming you haven't tried this way. Since the effects are working so i guess the driver is working (almost). I think this might work cuz I am also out of ideas now. So do post the solution whenever you get it done.

Good luck
nope it dosent show 1024 X resolutions. it displays only 640X and 320X resolutions.

---

### Post by zeex on 2009-04-20
> **T_1000 said:**
> nope it dosent show 1024 X resolutions. it displays only 640X and 320X resolutions.

Sorry I made a mistake. I didn't mean to write System -> Preferences -> Screen resolution . I wanted to write System -> Administration -> NVIDIA X server settings.

sorry I don't know where my head was .

---

### Post by upchucky on 2009-04-20
the following is an old xorg.conf that was generated by Envy before i used the method of setting up my nvidia that i posted for you earlier.

when I used Envy, it also only allowed a resolution of 640x480

I manually added the extra resolutions and modes that you see here to make it work with other resolutions.

back up your xorg, then you could try to use this as a template for yours, but remember to edit out the extra button settings for the mouse, i use a 7 button programmable mouse, and remember to change the entries and substitute the appropriate devices for your card and screen.

You must realize that the editing of this is done at the command line, and you must be able to switch back and forth from command line and gdm for each test. 





```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#    SubSection     "Display"
#        Depth       4
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       8
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       15
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       16
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       16
#        Modes      "1024x678"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "960x600"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "840x525"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "800x600"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1024x768"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x800"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1400x1050"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "640x480"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x1024"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x960"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x960"
#    EndSubSection
#Endsection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
#    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.9 [GeForce Go 6800 Ultra]"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.9 [GeForce Go 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "TripleBuffer" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1024x678" "960x600" "840x600" "1280x960" "800x600"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

---

### Post by T_1000 on 2009-04-20
Well well well.. well well well..well well well... well well well

Its DONE.. D..... O...... N...... E...... not completely. i would say 90%. The problem is itself with the monitor. now,, you must be thinking how is it working... well

After ubuntu loading screen(which has a bar),monitor flicks and goes off, which was happeneing earlier too with some driver installations. but i can enter my login information blindly and guess what.. it automatically turns On the monitor again with 1024 Resolutions. this is what happenening and when it happened first time.. when the first time i blindly logged, monitor turned On.. resolutions were 1024 which i wanted and for which i was strugling since 7 days.. but my desktop was wayyyyyyyyy to streched horizontly like rubber.. so somehow i reset the screen as per monitor width n height. I thnk, due to its corrupted on board settings, created the problems

Actually my monitor has been repaired several times and last time it was behaving so badly i was going to buy new one. but still i wasted some bugs and got it repaired. but even after repairing it has some width and clarity problems at some points. Even on Xp it dosent show entire screen, dosent fit to monitor & it dosent move its screen to right side.


So i think my monitor is the main culprit. :) Actually i didnt go through proper steps at start due to which driver wasnt getting installed properly. the next mistake was from my monitor itself.the only bad feeling is couldnt see my login screen. 

Also i can enable my visual effects,, normal and extra too. 

In nutshell my advice/step to install drivers for newcomers is this
1 - Install Ubuntu
2 - Directly Install Envyng if you have some legacy graphic card with this command.

# sudo apt-get install envyng-qt
3 - Run the envyng

4 - Finally install the suitable/recommended driver
Note: Do not install any other driver and do not execute any commands unless your professional

:)

And thanks to all of you for helping me out. but i still need you all as i am new to linux. so get ready for my wierd queries 

:) :) :) :) :)

---

### Post by inobe on 2009-04-20
after a fresh install i would recommend running system updates **first** then restarting the computer !

then check in **hardware drivers.**

if there are no drivers in use' install the drivers for your card in synaptic, if the driver is already pre installed and doesn't appear in "hardware drivers" there is a problem !

i would then suggest starting a topic in [multimedia and video]("http://ubuntuforums.org/forumdisplay.php?f=334") part of the forums.

that's important because it's the correct forum, scattering valuable information all over the forums only confuses things when users search for valid information.

provide all changes you made to your system in your initial post, this way the first to reply has enough information to provide a solution, this saves time for you and me otherwise the thread will turn into an ask and tell circus, that is totally unproductive and a waste of forum space :)

most importantly, follow the steps of the first person that replies to your topic, if that person runs out of solutions you may follow the next persons solutions, this will eliminate confusion at a mass scale and the next person would know what has changed in your system and know how to reverse the affects from the prior solutions.

when having system problems it's always best practice to start with the basics and if they fail' take it one step at a time "no multitasking" 

it's a procedure "a process" many of us religiously stick with at these forums or in our own homes, even in our workplace, it's not blind trial and error, it's call "troubleshooting" and many of us here are knowledgeable in that field within the proper forum.


> And thanks to all of you for helping me out. but i still need you all as i am new to linux. **so get ready for my wierd queries** 

if you follow the above information we can avoid weirdness :lol:


also congratulations :D

---

