---
title: "AMD/Intel Hybrid Graphics works"
date: 2012-02-23
forum: Hardware
---

### Post by Alexislavie on 2012-02-23
[FONT=Arial][SIZE=2]If you do want to make the switch possible between your Intel and your AMD graphics cards, then this post is for you. If you do not own a AMD hybrid graphic card, please leave this thread, and post your problems in a thread made for AMD single graphic or Intel single graphic.

[B]Edit: The solution seems not to work with ATI 5xxx graphic cards, try at your own risk.
Warning: Works only for muxless systems.
Warning 2: Check if your BIOS is updated, if not update it ! (You will need Windows). This is your computer manufacturer that "implements the switch on your mother card, and modify the video drivers for Windows to work on your computer". If an AMD 6630m (for example) works on a HP computer, this doesn't mean the same video card will work for sure (for example) on a ASUS computer.
[/B] 
**Edit bodhi.zazen**: [COLOR=darkred]**Best check hardware compatibility before following this tutorial. If your hardware is not listed as supported, this tutorial will not help you. See [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) **[/COLOR]

The following solution has been tested on a DELL Vostro 3550, with an AMD 6630m card and an Intel HD 3000 (Sandybridge) card (integrated into a Intel core i5). The version of Ubuntu used is 12.04 LTS (further versions should works too). **The system is very stable, and everything works well.**
This tutorial requires the use of the terminal, but still is simple if you're a beginner, you will just have to past some commands on it and press "Enter".
*(Tip for beginners : to past a command on a terminal, just press CTRL+SHIFT+V, it is the same shorcut as usual just don't forget to press SHIFT when pasting).*

Before beginning this tutorial, we will suppose you are following it on a fresh install (i.e. You did not install vgaswitchroo or flgrx (via jockey-gtk : The proprietary driver installer application from Ubuntu). Please also install all updates available for your computer before starting (and reboot if you're proposed to).
[B][COLOR=red]
STEP 1 - Installing latest AMD catalyst drivers :[/COLOR][/B]

As I'm writing this the latest version is 12.4, please check this page to know if there is a new version : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)[/SIZE][/FONT][FONT=Arial][SIZE=2] (this also includes the guide to install them).

First we're going to download all the prerequisite packages :
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
```If you're using Ubuntu 64bits please run those two commands (32bits users don't have to) :
```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
```We can now download the AMD catalyst 12.4 driver :
```
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
```And create Ubuntu packages of it :[/SIZE][/FONT][FONT=Arial][SIZE=2]
```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```Now let's install them :
```
sudo dpkg -i fglrx*.deb
```and configure the Xserver (xorg.conf file) for the first time :
```
sudo aticonfig --initial -f
```Now reboot your computer.

Test the switch to the discrete card :
```
sudo aticonfig --px-dgpu
```Then reboot again your computer.
[B] 
[COLOR=red]STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :[/COLOR][/B]
*Thanks to **[Niccola]("http://ubuntuforums.org/showpost.php?p=11819555&postcount=107")** for finding the actual fix.*[/SIZE][/FONT][FONT=Arial][SIZE=2]

_[COLOR=darkorange]If you ever apply an fglrx update, or your system automatically update fglrx, YOU WILL HAVE to repeat STEP 2, otherwise direct rendering will be missing on integrated gpu (i.e. No Unity 3D or Gnome Shell or Gnome Classic + Compiz on the Intel graphic). If you have an other solution (like loading a script on startup) please post it.[/COLOR]_

Open the /etc/X11/Xsession.d/10fglrx file with root rights :
```
gksu gedit /etc/X11/Xsession.d/10fglrx
```If you're using a 32bits system add at the end of 4th line this text : *"/usr/lib32/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```If you're using a 64bits system add at the end of 4th line this text : *"/usr/lib/x86_64-linux-gnu/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```Now save the file.

**[COLOR=red]STEP 3 - Enjoy your hybrid graphic system ! :[/COLOR]**

Reboot your computer to see the changes, it should boot up with the discrete card.[COLOR=black]

[/COLOR]**[COLOR=red]Useful informations, commands :[/COLOR]**

Power consumption is a lot better now, it seems that my battery last 4 times more with the integrated card, but this isn't still good as in Windows. If someone find or know tricks to decrease power consumption a little more please post it !

I do not recommend to update the catalyst driver once it's installed (if it works), if you really want to upgrade then check this page to find instructions : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)[/SIZE][/FONT][FONT=Arial][SIZE=2]

The AMD driver GUI application doesn't provide settings for screen configuration, but only 3d settings. This is a missing feature.

[I]Switching commands :
[/I]```
aticonfig --pxl # List current activated GPU
sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect
sudo aticonfig --px-igpu # Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```Verify the Open GL's libraries used :
```
fglrxinfo
```Verify if the direct rendering is used :
```
glxinfo | egrep render
```Install mesa-utils, and test the card 3d power (compare the fps) :
```
sudo apt-get install mesa-utils
glxgears
```[COLOR=Red]If something goes wrong and your[/COLOR][COLOR=black][COLOR=Red] computer doesn't boot (i.e. black screen), press CTRL+ALT+F3, log yourself into your account and enter those commands :[/COLOR]
[/COLOR]```
sudo rm /etc/X11/xorg.conf
sudo startx
```And you should be able to see your desktop.
[COLOR=red]
[/COLOR]**[COLOR=red]List of fully supported computers :   [/COLOR]**[COLOR=DarkOrange]// Updated 05/16/2012 (American date format).[/COLOR]
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]**ACER      7750g**, Intel HD 3000, AMD 6650m, HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL Inspiron 14R (N4110)**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL      Vostro 3550**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Envy 14t-2000 CTO**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP ENVY 15-3090CA**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dm4-2160sf**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavillion dm4-2110sp**,[/SIZE][/FONT][FONT=Arial][SIZE=2] Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6102sg**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6169sl**, Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6178sl**, Intel HD 3000, AMD 6770m, HDMI Intel/AMD: working/working, VGA      Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6192sf**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv7-6070ef**, Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/working,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion g4-1001tx**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Probook 4530s**, Intel HD 3000, [/SIZE][/FONT][FONT=Arial][SIZE=2]AMD 6490m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo e520**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6630m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo G-770**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6650m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SB1S1E**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SC1AFM/S**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=2]
If you want to add your computer, please do want it (this will help other users), **_make a post and indicate your configuration [COLOR=Red]like those above[/COLOR]_**. 
[/SIZE][/FONT][FONT=Arial][SIZE=2]I will then add it to the working list.
[/SIZE][/FONT][FONT=Arial][SIZE=2]_I repeat as many people do not get it : "[COLOR=Red]like those above[/COLOR]" ! It take you two minutes to write it, this saves me time, and I can update more frequently this thread._ Also posts like "It works on HP Pavilion dm4" are USELESS, I won't add a computer with an incomplete computer model number. Exception for computers without a precise model name (example : DELL Vostro 3550, Lenovo e520).
[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black]


_Useful links :_
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://forums.gentoo.org/viewtopic-p-6936730.html](http://forums.gentoo.org/viewtopic-p-6936730.html)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can thanks that guy because his post really helped me to understand how the ati hybrid graphics works.
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics](http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can also check this Gentoo wiki about hybrid graphics, this is some Gentoo's users that actually found first a solution on how to make AMD hybrid cards to work on Linux.[/COLOR][/SIZE][/FONT]

---

### Post by Sda1986 on 2012-02-23
Hi, can I ask how many Watts are you saving with this? thanks!

---

### Post by aeronutt on 2012-02-23
"Dell Vostro 3550 computer with a Intel HD 3000 integrated video device and a ATI/AMD 6630M video card"

This is my exact setup, I WILL be trying this...have never gotten it to work prior.

---

### Post by Alexislavie on 2012-02-23
I will post an update about the progress of the package and ppa creation tomorrow.

For now here are outputs from some commands :

With Dedicated GPU :

> 
alexis@Alexis-Vostro:~$ sudo aticonfig --px-dgpu
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: avertissement: création de  /etc/OpenCL/vendors/amdocl32.icd abandonnée car le fichier associé  /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (du groupe de liens  x86_64-linux-gnu_gl_conf) n'existe pas.

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!> 
alexis@Alexis-Vostro:~$ sudo aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).> alexis@Alexis-Vostro:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon 6600M and 6700M Series
OpenGL version string: 4.2.11399 Compatibility Profile ContextWith Integrated GPU :

> alexis@Alexis-Vostro:~$ sudo aticonfig --px-igpu
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: avertissement: création de /etc/OpenCL/vendors/amdocl32.icd abandonnée car le fichier associé /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (du groupe de liens x86_64-linux-gnu_gl_conf) n'existe pas.> alexis@Alexis-Vostro:~$ sudo aticonfig --pxl
PowerXpress: Integrated GPU is active (Power-Saving mode).

PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!> alexis@Alexis-Vostro:~$ fglrxinfo
display: :2.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0)
And here is my xorg.conf :

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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

---

### Post by Alexislavie on 2012-02-23
> **Sda1986 said:**
> Hi, can I ask how many Watts are you saving with this? thanks!

I didn't test this for the moment, I will do it when the PPA will be ready.
A thing is obvious it can't be worse than without fglrx and sna because by default the kernel gives power to the two cards but only the Intel one can be used by Xorg.

---

### Post by Alexislavie on 2012-02-24
I have been trying, 4 hours this afternoon to make it work, but sadly xserver-xorg-video-intel version 2.15.901 doesn't work with the latest Catalyst 12.1. Intel's driver 2.17 version works but needs a more recent Xorg version to be installed or compiled.
I think we will have to wait the release of Ubuntu 12.04 to have a compatible and stable Xorg version.

Although if you are impatient there is a way to install the latest Xorg version on Ubuntu 11.10 by adding those ppas but there are considered as unstable:
> [B]sudo add-apt-repository ppa:xorg-edgers/ppa
[/B]**sudo add-apt-repository ppa:sarvatt/intel-sna**
sudo apt-get update
sudo apt-get upgrade Then install the latest fglrx driver following this guide : [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide) and you will get Hybrid Graphics on Ubuntu 11.10

I'm sorry, but because the Xorg version used in Ubuntu 11.10 isn't enoughly recent, I can't do anything at that time.

---

### Post by aeronutt on 2012-02-24
Unfortunately, the above didn't work for me. I'll keep trying, but it's extremely frustrating that Ubuntu can't support dual graphics for this common hardware.  Hopefully, in 12.04.

---

### Post by Alexislavie on 2012-02-25
> **aeronutt said:**
> Unfortunately, the above didn't work for me. I'll keep trying, but it's extremely frustrating that Ubuntu can't support dual graphics for this common hardware.  Hopefully, in 12.04.

Did you run aticonfig --initial -f after installing the latest Catalyst driver, you should also have uninstalled fglrx if it was alrready installed on your computer.

---

### Post by aeronutt on 2012-02-25
> **Alexislavie said:**
> Did you run aticonfig --initial -f after installing the latest Catalyst driver, you should also have uninstalled fglrx if it was alrready installed on your computer.

Yes, I ran aticonfig --initial -f, and fglrx had never been installed previously.  I tried this on my 'test' load of Ubuntu, and now that load will not boot.

---

### Post by Alexislavie on 2012-02-25
> **aeronutt said:**
> Yes, I ran aticonfig --initial -f, and fglrx had never been installed previously.  I tried this on my 'test' load of Ubuntu, and now that load will not boot.

Go to a tty console example: CTRL+Alt+F3
Enter your login information.
sudo rm /etc/X11/xorg.conf
startx

It should boot as before.

---

### Post by pinguinhood on 2012-02-25
Hi! ):P
I'll get my new notebook next week. It's a Samsung Np700Z5A notebbok with Intel® HD Graphics 3000 + AMD Radeon™ HD6750M graphics. I want to install Ubuntu 12.04 (I know the risks of alpha versions). Should it work with xserver-xorg-video-intel of your ppa?
Thanks for your work!

---

### Post by zapo on 2012-02-25
Hello, first thank you for putting up these ppas and for your work.
Here is my experience so far.
I have a HP dv6 laptop with snd HD3000 / Radeon 6700M with an up to date ubuntu precise installed and the last version of catalyst drivers (12.1).

Xserver & direct rendering works well using Discrete GPU but I can't get direct rendering to work using Integrated GPU with xf86-video-intel from ubuntu repos (xserver runs though).

I tried using the packages from xorg-edgers and your ppa but it ended up crashing xserver.
I also tried compiling and installing xf86-video-intel with the --enable-sna flag against precise xorg but it gave me the same results than with your ppas.

I cant wait to see some progresses !

---

### Post by Starks on 2012-02-25
Is there any dynamic switching available?

---

### Post by pinguinhood on 2012-02-26
I found this article:
[http://www.phoronix.com/scan.php?page=news_item&px=MTA2MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTA2MTc)
Will SNA support be enabled by default in new 2.18 version or i'm I wrong?

---

### Post by Joe76000 on 2012-02-26
Hello Alexis,

Further to your post on the French Ubuntu forum, I am coming here where you originally posted your interesting **AMD/Intel Hybrid Graphics works !** subject.
I will give a try and keep you aware about my results.

Currently, I am using the **acpi_call** procedure which is working fine: iGPU=ON and dGPU=OFF with NO AMD drivers at all as it was just nightmares !
Roughly, my DV7 is running 10 to 15°C lower and the battery time is about double ! 
On one of my laptops: HP Pavilion DV7-6070ef CPU i7-2630QM + Switchable Graphics dGPU HD6490M / iGPU HD3000: W7 + Ubuntu 11.10 both in 64-bits.

ADD: On the HP Pavilion DV6-6000 or DV7-6000 (only Fixed Mode) and DV6-6100 or DV7-6100 series (Fixed or Dynamic Mode setup in BIOS) both with the AMD/INTEL Switchable Graphics, you cannot disable neither iGPU nor dGPU in BIOS which would have been much easier.

Keep going on and don't give up as a lot of people are more than interested by this hot topic.
Thanks. Joe

---

### Post by Starks on 2012-02-26
Just to confirm, this is for both muxed and muxless?

---

### Post by Alexislavie on 2012-02-26
> **zapo said:**
> Hello, first thank you for putting up these ppas and for your work.
Here is my experience so far.
I have a HP dv6 laptop with snd HD3000 / Radeon 6700M with an up to date ubuntu precise installed and the last version of catalyst drivers (12.1).

Xserver & direct rendering works well using Discrete GPU but I can't get direct rendering to work using Integrated GPU with xf86-video-intel from ubuntu repos (xserver runs though).

I tried using the packages from xorg-edgers and your ppa but it ended up crashing xserver.
I also tried compiling and installing xf86-video-intel with the --enable-sna flag against precise xorg but it gave me the same results than with your ppas.

I cant wait to see some progresses !

I didn't make any ppa for the moment, I'm waiting 12.04 to be out. The ppa I gave are for testing, they might be unstable, **and they aren't mine.**

---

### Post by Alexislavie on 2012-02-26
> **pinguinhood said:**
> Hi! ):P
I'll get my new notebook next week. It's a Samsung Np700Z5A notebbok with Intel® HD Graphics 3000 + AMD Radeon™ HD6750M graphics. I want to install Ubuntu 12.04 (I know the risks of alpha versions). Should it work with xserver-xorg-video-intel of your ppa?
Thanks for your work!

It depends if Catalyst 12.1 recognize your card. Check on the internet the compatibility.

---

### Post by Alexislavie on 2012-02-26
> **Starks said:**
> Is there any dynamic switching available?
X.org can't do this. Wayland will someday.

---

### Post by Alexislavie on 2012-02-26
> **pinguinhood said:**
> I found this article:
[http://www.phoronix.com/scan.php?page=news_item&px=MTA2MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTA2MTc)
Will SNA support be enabled by default in new 2.18 version or i'm I wrong?
This is the Ubuntu packager of that driver who will decide to either compile it with --enable-sna or not.

---

### Post by Alexislavie on 2012-02-26
> **Starks said:**
> Just to confirm, this is for both muxed and muxless?
Only muxless system.
Muxed system have a switch in the BIOS, this is why muxless system are a problem, because they do not have this option.

---

### Post by Alexislavie on 2012-02-26
For those who want to try the unstable ppas, after running aticonfig --initial -f
please check the result of this command :
> echo "PCI:$(lspci | grep VGA | grep ATI | awk '{print $1}' | sed 's/\./:/')"
with the pci adress in /etc/X11/xorg.conf if they aren't the same please replace the one in the xorg.conf by the one the previous command gave you.

I recommend to all of you to read this : [http://forums.gentoo.org/viewtopic-p-6936730.html](http://forums.gentoo.org/viewtopic-p-6936730.html)

---

### Post by hebetude on 2012-02-26
This could use some more information.  For instance, the fglrx version does match the deb package.  Also, the deb package is difficult to determine the deb version.  930 ubuntu2 seems to match up with 12.1. 

Not sure on intel

---

### Post by Starks on 2012-02-26
> **Alexislavie said:**
> X.org can't do this. Wayland will someday.

dma-buf, not Wayland.

---

### Post by wegah on 2012-02-27
Already there is a sna enable ppa. Using the last intel drivers.
[https://launchpad.net/~sarvatt/+archive/intel-sna](https://launchpad.net/~sarvatt/+archive/intel-sna)


The ppa drive work. no idea for how long the owner will maintain or update.


You need to use to.
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

---

### Post by wegah on 2012-02-27
not working. ATI Radeon HD 6850M envy 17 3d

[http://www.amd.com/us/products/notebook/graphics/amd-radeon-6000m/amd-radeon-6800m/Pages/amd-radeon-6800m.aspx#2](http://www.amd.com/us/products/notebook/graphics/amd-radeon-6000m/amd-radeon-6800m/Pages/amd-radeon-6800m.aspx#2)

Same problem before;

PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver

The 6850m from what i know is a muxless ( at last inside windows).





[    41.939] (--) Chipset Supported AMD Graphics Processor (0x68A8) found
[    41.940] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    41.940] (II) fglrx: intel VGA device detected, load intel driver.
[    41.940] (II) LoadModule: "intel"
[    41.940] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    41.940] (II) Module intel: vendor="X.Org Foundation"
[    41.940]    compiled for 1.11.2.902, module version = 2.17.0
[    41.940]    Module class: X.Org Video Driver
[    41.940]    ABI class: X.Org Video Driver, version 11.0
[    41.941] ukiDynamicMajor: found major device number 250
[    41.941] ukiDynamicMajor: found major device number 250
[    41.941] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    41.941] ukiOpenDevice: node name is /dev/ati/card0
[    41.941] ukiOpenDevice: open result is 8, (OK)
[    41.941] ukiOpenByBusid: ukiOpenMinor returns 8
[    41.941] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    41.942] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    41.942] (EE) No devices detected.
[    41.942]
Fatal server error:
[    41.942] no screens found
[    41.942]
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[    41.942] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    41.942]

---

### Post by LinoLinux on 2012-02-27
Doesn't work on my Dv6-6030el either (Intel HD3000 + ATI HD6470M).

added both PPAs, updated packages, installed catalyst12.1, ran "aticonfig --initial -f" (which created a xorg.conf file exactly like yours) but on reboot X segfaults.

Xorg.0.log is not very helpful:

```
(EE) Screen 1 deleted because of no matching config section
``` 

and backtrace:
```
0: /usr/bin/X (xorg_backtrace+0x26) [0x567006]
1: /usr/bin/X (0x400000+0x16ac6a) [0x56ac6a]
2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fa59b32f000+0x10060) [0x7fa59b33f060]
3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fa597300000+0x631c5) [0x7fa5973631c5]
4: /usr/bin/X (xf86DeleteScreen+0x7c) [0x47cdbc]
5: /usr/bin/X (xf86BusConfig+0x1cb) [0x46459b]
6: /usr/bin/X (InitOutput+0x903) [0x470c03]
7: /usr/bin/X (0x400000+0x22dfd) [0x422dfd]
8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fa59a25830d]
9: /usr/bin/X (0x400000+0x232bd) [0x4232bd]
Segmentation fault at address 0x4
```

Other commands you tried in #4 work fine (apparently I can switch graphics, and that's a great step forward) except "fglrxinfo" which gives "Error: unable to open display (null)"

I blacklisted radeon and added "nomodeset" at boot (as found via google) but nothing changed. Any other ideas?

---

### Post by Andy_9000 on 2012-02-27
I made a thread for this but seeing as it's not getting much attention I'll post it here also

I recently installed the AMD drivers on a DV6 with hybrid graphics using the SMXI script, I installed the intel driver first, then the AMD one. It worked until I logged out, after which I got this error:
(EE) Screen 1 deleted because of no matching config selection
(EE) fglrx(0): PowerXpress: usr/lib64/fglrx/switchlibGL failed with exit status 1
(EE) fglrx(0): PowerXpress: Failed to switch libGL link files.
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error: No screens found.


I'd like to see hybrid graphics work as well. The open source ati drivers are very energy hungry and inefficient

---

### Post by wegah on 2012-02-27
The "No screens found" relies in the fact at last for our AMd muxless card. There is in fact just one REAL HARDWARE VIDEO CARD. The INTEL GPU one. 
The intel GPU ones that controls the hardware, videos ports and everything. The AMD is more like a TURBO PROCESSOR. When we switch to AMd under windows. The hardware structure still being the intel but the system disable the logic from GPU intel and start to use the logic of AMD processor  ( In mine understand no MUX mean that)

The amd driver try to find an output for screen to control But this doesn't exist. who control is the gpu intel one.

Now come the fact of A+I question. 
The driver already have or at last seems to have a background for muxles at some level.

OR this messages are a kind of wrong identification of the card by the side of amd driver ( a+i are the muxed ones? or i'm wrong). 

OR the drive compatibility we saw in pictures are for MUXED ONES.

OR there is a blacklist for non use the drivers in predefined cards same if work ( by the amd driver).

OR there is 2 kinds of AMD MUXLESS devices.
The ones in mine case amd 8550m that use the HARDWARE structure from GPU acting just like an advanced TURBO and other one that are muxless but both cards (GPU AND DISCRETE) have a full hardware control of video ports.

So.. Is is. Because this the solution seems little magical to me. At last for mine devices.

Still on wait.

---

### Post by wegah on 2012-02-27
From [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03048374](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03048374)


At last seems the option in linux drivers to switch the cards. Are made for the ATI + ATI ( muxed ones) and not the GPU + ATI ( or muxless).

---

### Post by SamBam77 on 2012-02-27
I tried installing the drivers for the AMD video card using instructions found here:
[http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html)
for my HP dv6t Quad 6000 series notebook with an AMD 7470M discrete graphics card.

However, after rebooting X fails to load and I cannot get anything graphical to work on the computer.  I can boot into recovery mode, but I cannot load X or any graphical programs.  If I boot normally it will just hang indefinitely at a screen with a list of tasks that it is trying to do with “[OK]” next to most of them, though it “[fail]”s on “Starting automatic crash report generation”.

How can I reverse the damage I have done (uninstall the drivers, etc…) so that I can get the computer back to a useable state?

---

### Post by pinguinhood on 2012-02-29
> **SamBam77 said:**
> I tried installing the drivers for the AMD video card using instructions found here:
[http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html)
for my HP dv6t Quad 6000 series notebook with an AMD 7470M discrete graphics card.

However, after rebooting X fails to load and I cannot get anything graphical to work on the computer.  I can boot into recovery mode, but I cannot load X or any graphical programs.  If I boot normally it will just hang indefinitely at a screen with a list of tasks that it is trying to do with “[OK]” next to most of them, though it “[fail]”s on “Starting automatic crash report generation”.

How can I reverse the damage I have done (uninstall the drivers, etc…) so that I can get the computer back to a useable state?
Did you try the command on the post #10?
sudo rm /etc/X11/xorg.conf
startx

---

### Post by pinguinhood on 2012-02-29
> **Alexislavie said:**
> This is the Ubuntu packager of that driver who will decide to either compile it with --enable-sna or not.
Ok, I'll wait the pc to try!
Thank you!

---

### Post by Sj3 on 2012-02-29
Well... but how to check if a notebook is muxless or muxed?(before i buy it, ofc)

---

### Post by SamBam77 on 2012-02-29
> **pinguinhood said:**
> Did you try the command on the post #10?
sudo rm /etc/X11/xorg.conf
startx
That worked.  I did not think to do that before because I only had read-only access through the command prompt.  But I was able to access it through a boot disk and delete this file, which allowed me to boot into the GUI, and then I could purge the drivers myself to get everything back to normal (since those drivers also prevented some of my programs from loading).

I guess I will need to wait a bit longer to make use of my video card in linux.

---

### Post by wegah on 2012-02-29
Sj3

By definition. When you are using windows. If your card change from gpu to discrete card in a transparent way ( both, nvidia and amd).
You are using a muxless card.

IF you need to restart or logoff/login your computer to turn the effect on when using windows. Then Is a muxed one.


Both, Muxless or MUXED ones. CAN  have in BIOS the option to use the GPU or DISCRETE only/PRIMARY.



The problem resides the companies like HP. That use secured bios ( YES the same secured bios everyone listen and read microsoft will use and **** with linux. they do it for ages). Disable this option on bios and doesn't let us to enable this by our-self ( they use cryptography keys that doesn't allows to open all hidden and useful bios options), sometimes that does't let just use a usb or change our RAM memory if not their ones ( but this kind of **** they do with us, are another discussion).

The problem between AMD and NVIDIA. Besides both being muxless they works different. 

In resume. NVIDIA when disable the gpu or discrete card. ALREADY UNLOAD the modules and disable the pcie channel/card. ( because this NVIDIA are not ALL 100% transparent when switching one from other). And the AMD. disable the pcie card. But maintain the states of card/pcie and drivers loaded ( faking the card is on) Then when you ALREADY RESTART the card. all become 100% transparent and perfect.


Apple are muxless but use a special processor/chip that work with all this. almost turning the muxless cards in a muxed one.

And last in AMD side. Seems some supposed muxless cards  special from 66xxM that besides SEEMS be muxless act like a muxed one.


Under linux is simple to know if you use a muxed one or muxless one. Try to switch the discrete card using the vgaswitcheroo. IF you receive a ERROR when switching in dmesg. Then yu are muxless. Probable the metodo of this post ( 99% of chance) will not work.

---

### Post by Yellow Pasque on 2012-02-29
> **Sj3 said:**
> Well... but how to check if a notebook is muxless or muxed?(before i buy it, ofc)
It would be better to avoid hybrid graphics completely. If all you need is video acceleration and enough 3D for desktop effects and light gaming, go intel.

---

### Post by Sj3 on 2012-03-01
Well... i'm going for a new AMD A6 processor with only the integrated card, looks like a good entry-level gaming card(and it's all i need), i have seen this in action on a debian, over 5k fps with glxgears(i know it's not a real benchmark but still it's a good result).

Btw i know how to check if there is mux or not... but i'm buying the computer online so... that's why i asked how to know BEFORE i buy it... ehehe

p.s. sorry for the poor english, it's not my mother language.

---

### Post by Yellow Pasque on 2012-03-01
> **Sj3 said:**
> Well... i'm going for a new AMD A6 processor with only the integrated card, looks like a good entry-level gaming card(and it's all i need), i have seen this in action on a debian, over 5k fps with glxgears(i know it's not a real benchmark but still it's a good result).

Btw i know how to check if there is mux or not... but i'm buying the computer online so... that's why i asked how to know BEFORE i buy it... ehehe

p.s. sorry for the poor english, it's not my mother language.
The mux/less distinction only applies to systems with two GPU's. You're in the wrong thread...

---

### Post by Sj3 on 2012-03-02
> **Temüjin said:**
> The mux/less distinction only applies to systems with two GPU's. You're in the wrong thread...

I'm not in the wrong thread, just since it's impossible to know if it's muxless or not(before you try it, that's why i asked about it) i'm going for an integrated GPU to avoid the problem, it's simple.

---

### Post by jonnyboysmithy on 2012-03-02
> **Joe76000 said:**
> Hello Alexis,
[B]
Keep going on and don't give up as a lot of people are more than interested by this hot topic.[/B]
Thanks. Joe
Yes thats me! I'm also stuck with these problems I would be very grateful+happy if it all worked properly.

> Roughly, my DV7 is running 10 to 15°C lower and the battery time is about double !  Yea I'm still stuck with that issue. I'm getting about half battery life of what I would get in windows. :/

---

### Post by wegah on 2012-03-02
Sj3, by the view point of FUNCTIONALITY. If you buy a muxless card with gpu and discrete. The notebook will have full work. The only drawback is, the non use of the discrete one.

By the investment side.
Muxed ones, are PAST. MUXLESS are the present and future.

We can't forgives that one of the problems with muxless cards are the fact of XORG/KERNEL and some EGOS cant be touched. Not only the fact of AMd or NVIDIA didn't release drivers for this cards..

The facts is. This will be the future.
Linux today, next 6 months, or next 2 years at last. will have full support for this.

Then, If you buy a notebook with a intel gpu. will work well a lot. ( pity sandy bridge not be discernible). Just the discrete will have troubles. ( easy do disable ) and save battery.

Of course. If you buy a WHITEBOOK kind like MSI ones that are NOT LOCKED at HELL LEVEL. You probably will have use of discrete card.

By definition. All amd 60xx mobile and up are muxless.
Want know if will work or not?
Look at BIOS.IF you HAVE the option to choose discrete or GPU? ( YES WITH MUXLESS CARDS)
Then, 90% of chance your notebook work well with discrete card, same being a muxless one under linux.

Or buy one with just a discrete card...

The option is your.

---

### Post by Kakitus on 2012-03-04
Thank you very much for your effort, OP. I have also been dealing with this problem for some time now. In fact, the lack of switchable graphics on my Ubuntu laptop is the only thing holding me back from fully enjoying having switched over to Linux.

What I would like to ask you is whether your solution would also work with an AMD 5xxx / Intel configuration. (Acer 3820TG, AMD HD5650 and Intel Core i5-450m).

Thanks again.

---

### Post by Alexislavie on 2012-03-05
I forgot to mention :
Please check the PCI adress in the xorg.conf generated (the line in red) and replace it if necessary by the adress this command outputs :
> 
echo "PCI:$(lspci | grep VGA | grep ATI | awk '{print $1}' | sed 's/\./:/')"Then switch to discrete GPU and reboot.

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    [COLOR=Red]BusID       "PCI:1:0:0"[/COLOR]
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

If the PCI adress isn't exact, then it is normal Xorg fails at start.
I've seen many of you tried this on HP computers, did someone else than me tried it on a Dell ?

---

### Post by Alexislavie on 2012-03-05
Please don't forget to tell your computer model, and the two drivers version. I used 2.17 for Intel and 12.1 for Catalyst. The actual version in the ppa is 2.18, so if it doesn't work with that one install 2.17 to give it a try : [https://launchpad.net/~sarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra](https://launchpad.net/~sarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra)
Download the i386 or amd64 package and install it manually.

---

### Post by pinguinhood on 2012-03-06
Did anyone try it on Precise? :confused:

---

### Post by cmeng on 2012-03-07
> **pinguinhood said:**
> Did anyone try it on Precise? :confused:

I have tried with precise for the pass few days but with no luck.
System: HP Pavilion dm4 i5 HD54xx with Ubuntu Precise-64bit

Added the following repositories and do "sudo apt-get update"

sudo add-apt-repository ppa: org-edgers/ppa
sudo add-apt-repository ppa:sarvatt/intel-sna
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates  (no precise repository)

The system installed with
xserver-xorg-video-intel 2.18
amd-driver-installer-12-1-x86.x86_64.run (installed with direct .run or convert to .deb packages - give the same results

After the installationtion, have tried all the tests given in the link below and every things seems to work.
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

But always get the following when check with fglrxinfo, I suppose it is correct since need to reboot to enable dgpu(but never success to boot properly)
$ fglrxinfo
display: :2.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0)                      

Also facing problem whenever I do "sudo aticonfig --px-dgpu, as it is looking for 
"/etc/OpenCL/vendors/amdocl32.icd' instead of "/etc/OpenCL/vendors/amdocl64.icd'

Ignore the warning, and reboot system. System always hang. Has to go into recovery mode to
remove the /etc/X11/xorg.conf

Note: Recovery mode always set the mounted dev/sdax as read-only file system. so has  to perform the following to find out the boot disk then remount it as rw:
sudo fdisk -l                      
sudo mount -o remount,rw /dev/sda8
sudo rm /etc/X11/xorg.conf

Right now without the ATI driver, xbmc Eden cannot work as it needs openGL. IGPU driver is no good for xbmc.

Looking forward to Alexislavie to provide a solution.

---

### Post by clean31 on 2012-03-07
> **Alexislavie said:**
> Please don't forget to tell your computer model, and the two drivers version. I used 2.17 for Intel and 12.1 for Catalyst. The actual version in the ppa is 2.18, so if it doesn't work with that one install 2.17 to give it a try : [https://launchpad.net/~sarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra]("https://launchpad.net/%7Esarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra")
Download the i386 or amd64 package and install it manually.

Hi Alexislavie,

I'm a french user too, and i'm sorry for my bad language in english.

I posted too on your french **[topic]("http://forum.ubuntu-fr.org/viewtopic.php?id=831941")**, just in case.

My laptop is a Sony Vaio SA2Z9E with this HW :

Corei7
Sandy Bridge
Hybrid Integrated Intel Graphics HD 3000 + ATI Radeon HD6630M

Ubuntu 11.10 Oneiric
xserver-xorg-video-intel with -sna 2.17 from archives of ppa:sarvatt/intel-sna
amd-ati-driver proprietary 12.1 compiled in .deb via this [B][URL="http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Download_the_latest_Catalyst_package."]wiki
[/URL][/B]

So, i follow your guide step by step with no error until reboot my laptop at the end.

Ubuntu start normaly with the boot animation and stop on a black screen, the series of ctrl+alt+f1 or ctrl+alt+backspace keys combinations doesn't work.

i'm stuck on this black screen until i press on the power button, so the sequence to shutdown the laptop start and i see the ubuntu shutdown animation.

If i start in recovery mode and look the logs :

xorg.log --> no errors (EE)
syslog --> "[Firmware Bug] : Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1" if the current driver doesn't work."

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213841&stc=1&d=1331111974[/IMG]


After install of xserver-xorg-video-intel & ati driver proprietary, i generated the xorg.conf with "aticonfig --initial -f", no error.
The BusID match with my HW "PCI:01:00:0"

If i use fglrxinfo it's working and i see my sandy bridge HW
I can switch between igpu and dgpu with aticonfig --px-igpu or aticonfig --px-dgpu

but if i reboot after the end, i'm stuck on a black screen.

Any idea ?

Thx a lot


EDIT :

New : With the two command "sudo aticonfig --px-dgpu" or "sudo aticonfig --px-igpu" i have the same result for the commande "fglrxinfo"


> sudo aticonfig --px-dgpu
PowerXpress: Discrete GPU is active (High-Performance Mode)

fglrxinfo
display: :0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
OpenGL version string: 1.4 (2.1 Mesa 7.11)

> sudo aticonfig --px-igpu
PowerXpress info : Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alernatives: avertissement: création de /etc/OpenCL/vendors/amdocl32.icd abandonnée car le fichier associé /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (du groupe de liens x86_64-linux-gnu_gl_conf) n'existe pas.

PowerXpress : Integrated GPU is selected (Power-saving mode), please restart XServer for changes to take effect!



fglrxinfo
display: :0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
OpenGL version string: 1.4 (2.1 Mesa 7.11)

---

### Post by pinguinhood on 2012-03-08
[New Catalyst 12.2]("http://ubuntuforums.org/showthread.php?t=1937297")!

Who's going to try it with hybrid graphics?! (I'm still waiting for new notebook, sigh :frown:)

---

### Post by zapo on 2012-03-11
> **pinguinhood said:**
> [New Catalyst 12.2]("http://ubuntuforums.org/showthread.php?t=1937297")!

Who's going to try it with hybrid graphics?! (I'm still waiting for new notebook, sigh :frown:)

12.2 works good for me. HD3000/HD6770m using linux 3.3.0-rc7 and latest precise updates.
I've tried to use xorg-edgers ppa without success (12.2 still doesnt support xserver 1.12). Haven't tried xf86-video-intel 2.18 yet but ubuntu's 2.17 works quite well and direct rendering now works.
The only remaining problems I have are:

- gnome-shell not starting automatically (from lightdm) on intel gpu, I have to manually start it from tty with : 
```
DISPLAY=:0.0 gnome-shell --replace
```

- random hard lockup when shutting down on ati gpu (most of the time after having played a bit): [https://bugs.launchpad.net/ubuntu/+bug/750437](https://bugs.launchpad.net/ubuntu/+bug/750437)

---

### Post by jonnyboysmithy on 2012-03-12
> **pinguinhood said:**
> [New Catalyst 12.2]("http://ubuntuforums.org/showthread.php?t=1937297")!

Who's going to try it with hybrid graphics?! (I'm still waiting for new notebook, sigh :frown:)
Just installed 12.2 on the new precise 12.04 beta1. ran sudo aticonfig --initial rebooted and it all works out of the box!!!:KS:D:KS:D

this is on hp pavilion dv6 6023TX with ATI HD6770m.
EDIT: Ok only the ATI works DONT try switching to the intel integrated, it just crashes.

---

### Post by Alexislavie on 2012-03-12
> **jonnyboysmithy said:**
> Just installed 12.2 on the new precise 12.04 beta1. ran sudo aticonfig --initial rebooted and it all works out of the box!!!:KS:D:KS:D

this is on hp pavilion dv6 6023TX with ATI HD6770m.
EDIT: Ok only the ATI works DONT try switching to the intel integrated, it just crashes.

Did you use a sna version of the intel driver or not ? Don't forget to mention that.

---

### Post by jonnyboysmithy on 2012-03-12
> **Alexislavie said:**
> Did you use a sna version of the intel driver or not ? Don't forget to mention that.
No idea. I justed clicked switch graphics and rebooted.

---

### Post by xrend on 2012-03-12
I'm running HP G62-a70sm (intel + ati hd5470) with no bios switching options.

Will give this all a shot tomorrow and update.


@Alexslavie: Thank you for all the time you invested. Writing a walk-trough for this would be awesome. I know at least 3 other guys in my country that could use it. 
If you need an extra hand for writing it, i want to help.

---

### Post by htrex on 2012-03-13
Works without major modifications but with some relevant defects on ubuntu 12.04 beta + Catalyst 12.2 (.deb packages created with AMD installer ).

My laptop is an HP DV6-6169sl (Intel HD Graphics 3000 + AMD 6770M).

* Unity 3D doesn't work with integrated GPU:
X starts but there's no menu bar and no unity bar.
When using just the laptop display I can't see any file, and right click has no effect.
When using multiple monitors I can see and open files on the desktop but windows are without any decoration, right click shows context menu.

In either case CTRL+ALT+CANC shows a dialog to logout, so I can login again with Unity 2D.

* Unity 2D with integrated GPU is almost perfect:
Using multiple monitors with different resolution you need to top align theme, otherwise the shortest monitor doesn't show the menu bar.
glxgears works 

```

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
347 frames in 5.0 seconds = 69.030 FPS
320 frames in 5.3 seconds = 60.008 FPS
300 frames in 5.0 seconds = 60.000 FPS
300 frames in 5.0 seconds = 59.993 FPS

```

* Unity 2D with discrete GPU:

With a single display seems ok.
With a second external HDMI display I can get the menubar on the FULLHD secondary monitor only if is right aligned in respect to the laptop monitor (no menu bar on top, but unity bar is ok).

```

glxgears
1851 frames in 5.0 seconds = 370.177 FPS
3362 frames in 5.0 seconds = 672.191 FPS
2165 frames in 5.0 seconds = 432.971 FPS
2221 frames in 5.0 seconds = 444.170 FPS

```

* Unity 3D with discrete GPU:
With a single display, either internal or external seems ok.
With a second display sort of works if the secondary external FullHD monitor is on right of the laptop monitor, in this case I'm seeing 2 Unity launch bars, one for each monitor, but when widows are maximized they span across both monitors.

```

glxgears
2608 frames in 5.0 seconds = 521.010 FPS
2595 frames in 5.0 seconds = 518.740 FPS
2602 frames in 5.0 seconds = 519.889 FPS
2601 frames in 5.0 seconds = 519.312 FPS

```

Are you seeing this kind of defects?
Do you know of a relevant bug where to report, or do we need to open a new one?

---

### Post by zapo on 2012-03-13
> **htrex said:**
> 
* Unity 3D doesn't work with integrated GPU:
X starts but there's no menu bar and no unity bar.
When using just the laptop display I can't see any file, and right click has no effect.
Have you tried restarting it from tty ? I have the exact same hardware and problem with gnome-shell (which use compositing as well) on the integrated GPU.
```
DISPLAY=:0.0 unity --replace
```

---

### Post by htrex on 2012-03-13
> **zapo said:**
> Have you tried restarting it from tty ? I have the exact same hardware and problem with gnome-shell (which use compositing as well) on the integrated GPU.
```
DISPLAY=:0.0 unity --replace
```

Yeah, it works and seems perfect with dual monitor.

Think all this info would be usefull for devs, I'll search for a relevant bug to report, please point me to one if you know about it. 

Thanks

Edit:
Some stuff is broken, eg. right click on the desktop or unity launcher has no effect...

---

### Post by zapo on 2012-03-13
> **htrex said:**
> Yeah, it works and seems perfect with dual monitor.

Think all this info would be usefull for devs, I'll search for a relevant bug to report, please point me to one if you know about it. 

Thanks
I just created a new one : [https://bugs.launchpad.net/ubuntu/+bug/954021](https://bugs.launchpad.net/ubuntu/+bug/954021)

---

### Post by htrex on 2012-03-14
> **zapo said:**
> I just created a new one : [https://bugs.launchpad.net/ubuntu/+bug/954021](https://bugs.launchpad.net/ubuntu/+bug/954021)

Ok, so I've tried to use PPAs suggested at post #6 on a 11.10 64 bit install with catalyst 12.2 (.deb packages self generated from AMD installer) and it works quite well in any configuration, seems only with a minor problem.

The glitch with 11.10 is just that pressing the left mouse button on menu bar indicators opens the relative submenus, but releasing it closes the menu instead of leaving it open until clicking outside it, not a big problem, just need to keep the left mouse button pressed while moving on the necessary menu entry to open it.

To summarize so far, 11.10 works for me while 12.04 beta1 seems badly broken with this hw/sw configuration, but there's definitelly a huge progress with AMD multi GPU switching and may be 12.04 final of both ubuntu and catalyst will nicelly work togheter.

---

### Post by jonnyboysmithy on 2012-03-14
I got tired of it all so I turned of the ATI card all together. I don't need processing power or power consumption of the ati card. Here it explains how to disable and turn it of altogether. 
If you get the problem of "vgaswitcheroo not found" then try it on a fresh install. worked for me!

[http://ubuntuforums.org/showthread.php?t=1917897](http://ubuntuforums.org/showthread.php?t=1917897)

SO, finaly its sorted..:guitar:

EDIT: Also checkout: [http://ubuntuforums.org/showthread.php?t=1859945](http://ubuntuforums.org/showthread.php?t=1859945)

---

### Post by miatawnt2b on 2012-03-18
I just bought a Samsung series 7 with Hybrid Intel/AMD graphics. 
AMD 6750M
Intel HD3000

There doesn't seem to be a solid solution for this at the moment if I'm not mistaken. Could you folks let me know if I'm headed in the right direction...

Ubuntu Precise is the only version with the correct xorg-intel driver but we aren't sure if the maintainer of the stock package has the -sna option enabled.

Does anyone have a ppa to get this thing working in Oneiric or Precise?  What would be my best option?

Thanks,
-J

---

### Post by Startacus on 2012-03-19
I'm also trying to get this to work. I followed the steps that were posted by the OP but when I switch to my Integrated chip and reboot it fails to start up by saying LightDM fails and then it just hangs. I have to reboot into recovery and rerun "aticonfig --initial -f" to force it back to discrete. I would really like to fix this because the fans aren't running properly and my laptop runs very hot. I'm running a Sony VPCSC1AFM which has a 6470M and I believe an Intel 3000 HD.

---

### Post by pinguinhood on 2012-03-19
> **miatawnt2b said:**
> I just bought a Samsung series 7 with Hybrid Intel/AMD graphics. 
AMD 6750M
Intel HD3000

There doesn't seem to be a solid solution for this at the moment if I'm not mistaken. Could you folks let me know if I'm headed in the right direction...

Ubuntu Precise is the only version with the correct xorg-intel driver but we aren't sure if the maintainer of the stock package has the -sna option enabled.

Does anyone have a ppa to get this thing working in Oneiric or Precise?  What would be my best option?

Thanks,
-J
Hi miatawnt2b, could you post xserver-xorg-video-intel and fglrx version number?

There is a xserver-xorg-video-intel sna enable ppa (post #25)
[https://launchpad.net/~sarvatt/+archive/intel-sna]("https://launchpad.net/~sarvatt/+archive/intel-sna")
Or you can download the version you want from here
[https://launchpad.net/~sarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra]("https://launchpad.net/~sarvatt/+archive/intel-sna/+sourcepub/2245651/+listing-archive-extra")

What about "aticonfig --initial -f"? Did it run properly?

---

### Post by miatawnt2b on 2012-03-19
xserver-xorg-video-intel 2:2.17.0-1ubuntu4

fglrx is not installed under synaptic.  I purged all instances of radeon/ati/fglrx in synaptic before installing the catalyst 12.2 package.

After this, my ATI graphics seems to work, but selecting the intel chipset under the catalyst administrative options prompts for a reboot, then upon reboot, x refuses to start.  I haven't been able to recover from this. I tried enabling vesa and intel in the xorg.conf, tried reinstalling the catalyst package from command line, tried 'aticonfig --initial' (forgot the -f option)

I was able somehow (cant remember exactly how) to get the login screen back which told me something was working, but upon logon all I got was a black screen.  I ended up reinstalling 12.04 from scratch since it was a new build anyhow.

I thought the ppa was just for onieric, not for the 12.04 beta so I never installed anything from the ppa.

---

### Post by pinguinhood on 2012-03-19
The ppa seems to be for Precise too. If you open the link with your browser you should be able to select "Precise" as filter (default version).

Do you use ubuntu (unity) mode? Did you try with ubuntu classic mode?

---

### Post by miatawnt2b on 2012-03-19
> **pinguinhood said:**
> The ppa seems to be for Precise too. If you open the link with your browser you should be able to select "Precise" as filter (default version).

Do you use ubuntu (unity) mode? Did you try with ubuntu classic mode?

I didn't think to try unity(hate it so first thing I do is install gnome-session)... only classic with compiz.

so I just installed the ppa, and it grabbed the xserver-xorg-video-intel - 2:2.18.0+git20120317.e31d9dac-0ubuntu0sarvatt2~sna 

I'm afraid to enable the intel and reboot though given what happened yesterday. :)

---

### Post by pinguinhood on 2012-03-19
> **miatawnt2b said:**
> I didn't think to try unity(hate it so first thing I do is install gnome-session)... only classic with compiz.

so I just installed the ppa, and it grabbed the xserver-xorg-video-intel - 2:2.18.0+git20120317.e31d9dac-0ubuntu0sarvatt2~sna 

I'm afraid to enable the intel and reboot though given what happened yesterday. :)

=D> Go for it(and good luck!):KS

---

### Post by delsus on 2012-03-19
This didn't work for me using an ATI mobility radeon HD 5470 and a first generation i5 CPU with integrated graphics controller. I issue aticonfig --initial -f and get a black screen on boot, and have to restore my original xorg.conf file to boot into Ubuntu.

Whats curious is after I have updated xorg it shows both graphics adapters switched on, and if I do an aticonfig --pxl after the aticonfig --initial it shows the discreet GPU active but still will not boot unless I use recovery to restore my original xorg.conf.

Any additional help would be appreciated, I really want my discreet GPU working to game on Ubuntu

---

### Post by kmas on 2012-03-20
so I Downloaded
[http://www2.ati.com/drivers/linux/am...x86.x86_64.run](http://www2.ati.com/drivers/linux/am...x86.x86_64.run)

As normal, I run:
```

$ chmod +x amd-driver-installer-12-2-x86.x86_64.run
$ ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb
```copied the .debs somewhere for safekeeping.

Builds OK, installs OK.

rebooted. 

when it came up, 

```
sudo aticonfig --initial -f
```then rebooted again

I added the ppa ppa:sarvatt/intel-sna

upgraded, and made sure xserver-xorg-video-intel was installed to the latest ppa version, then I rebooted again. 

```
sudo aticonfig --initial -f 
```then I reboot again. 

Now on the terminal 

tried
```
sudo aticonfig --pxl
```It told me I was using the AMD GPU. 

To switch to the Intel gpu I entered this command in a terminal :
```
sudo aticonfig --px-igpu
```I rebooted. as soon as the machine booted, it told me that ubuntu graphics settings wasn't configured properly. It didn't even let me revert from that window. 

I then did ctr alt f1 to get to the command line. 
To switch back to the AMD/ATI gpu I entered this command in a terminal :

```
sudo aticonfig --px-dgpu
```Here is my hardware info
```

makezan@700Z3A:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760]

```here is my xorg.conf
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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

```

Questions: I'm I missing something, I'm I supposed to do aticonfig --initial before my reboots?? or after my reboots? 
```
makezan@700Z3A:~$ sudo aticonfig --initial -f 
Warning: you are intending to clear the configuration infomation which you need to recover to High Performance mode, please reboot your machine to aviod inconsistency 
```
I already anwered this question for myself. It makes sense. you need to swtich the drivers first before trying to initialize it. 


Is there a way to quickly reboot xserver without rebooting, before it was ctrl alt del, and that service gdm restart isn't relevant because now its unity.

How can I get this to Work.

---

### Post by miatawnt2b on 2012-03-20
actually I guess xserver-xorg-video-intel didn't install from the PPA.

xserver-xorg-video-intel:
 Depends: xorg-video-abi-12  but it is not installable
  Depends: xserver-xorg-core (>=2:1.11.99) but 2:1.11.4-0ubuntu6 is to be installed

Running 12.04

took a quick look for the depend, but didn't find one for AMD64
-J

---

### Post by Startacus on 2012-03-21
After a frusturating two days trying to figure this problem out and being unable to install Catalyst because it kept detecting a previous fglrx driver when I had already removed and purged it I decided to reformat (it was a new install anyway) and start from scratch. Before even installing a driver I followed the instructions to install the sna driver and then I installed the latest catalyst and everything now works. The only thing is that I have to run Unity 2D when on the integrated chip. I can definitely live with this as long as it solves my overheating issue.

---

### Post by jonnyboysmithy on 2012-03-21
> **Startacus said:**
> After a frusturating two days trying to figure this problem out and being unable to install Catalyst because it kept detecting a previous fglrx driver when I had already removed and purged it I decided to reformat (it was a new install anyway) and start from scratch. Before even installing a driver I followed the instructions to install the sna driver and then I installed the latest catalyst and everything now works. The only thing is that I have to run Unity 2D when on the integrated chip. I can definitely live with this as long as it solves my overheating issue.
I have an hp dv6-6023TX with i5-2410m intel HD3000 and AMD Radeon HD 6700M Series.
I screwed around for a looong time with the catalyst driver.
My experience is that it is buggy and that I didn't need all that  performance. 
I just wanted to get rid of the overheating and the fans running fast.
Now I just use the intel HD3000. It runs really cool (fan just running @51celsius).
As far as I can tell everything seem to work as it should (effects hd videos no artifacts).
I can get about 5-6hours battery time (usually about 12-18watts consumption, the lowest I got it was 9.4watts) 
Anyway I suggest you give this a go: [http://ubuntuforums.org/showthread.php?t=1917897](http://ubuntuforums.org/showthread.php?t=1917897)

---

### Post by onefthemany on 2012-03-21
try post#9 in this thread:

[http://ubuntuforums.org/showthread.php?p=11780425#post11780425](http://ubuntuforums.org/showthread.php?p=11780425#post11780425)

i have bastardised a script that allows you to switch between integrated and discrete, if you want to use the discrete for gaming.

good luck

---

### Post by Startacus on 2012-03-21
> **jonnyboysmithy said:**
> I have an hp dv6-6023TX with i5-2410m intel HD3000 and AMD Radeon HD 6700M Series.
I screwed around for a looong time with the catalyst driver.
My experience is that it is buggy and that I didn't need all that  performance. 
I just wanted to get rid of the overheating and the fans running fast.
Now I just use the intel HD3000. It runs really cool (fan just running @51celsius).
As far as I can tell everything seem to work as it should (effects hd videos no artifacts).
I can get about 5-6hours battery time (usually about 12-18watts consumption, the lowest I got it was 9.4watts) 
Anyway I suggest you give this a go: [http://ubuntuforums.org/showthread.php?t=1917897](http://ubuntuforums.org/showthread.php?t=1917897)

Is there a benefit to doing this as opposed to just running the Integrated Chip with Catalyst? I really have no need for the discrete chip. Any gaming or heavy duty computing I do on my powerful desktop. I just use this laptop to develop and get a little work done.

---

### Post by delsus on 2012-03-21
I posted this in another thread and I don't like posting multiple times, but I hit the wrong prefix, so I don't know if it is getting the right people to see, so I thought I would post it here to see if anyone can help because it seems like I am getting somewhere. (warning wall of text inc)

After failing to get my discreet GPU working in ubuntu 11.10 I decided  to install 12.04 to see if it was working and I believe I am getting  somewhere with it.

I installed the fglrx drivers through jockey and ran ```
aticonfig  --initial -f
```However it came up with this powerXpress error:

```
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
```I however ignored  this and rebooted, and rather than completely failing to boot it boots  to low graphics mode (which is progress) but I cannot configure my  graphics adapter and screen,

Here are my xorg.conf and my xorg.0.log files:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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

``````
[    15.420] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.420] X Protocol Version 11, Revision 0
[    15.420] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    15.420] Current Operating System: Linux mike-ubuntu 3.2.0-17-generic #27-Ubuntu SMP Fri Feb 24 15:37:36 UTC 2012 x86_64
[    15.420] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic  root=UUID=ff081b73-4bb3-4c52-8153-e789022d6a06 ro quiet splash  vt.handoff=7
[    15.420] Build Date: 22 February 2012  03:16:54AM
[    15.420] xorg-server 2:1.11.4-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    15.420] Current version of pixman: 0.24.4
[    15.420]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.420] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.420] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 21 20:44:20 2012
[    15.420] (==) Using config file: "/etc/X11/xorg.conf"
[    15.420] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.421] (==) ServerLayout "aticonfig Layout"
[    15.421] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    15.421] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    15.421] (**) |   |-->Device "aticonfig-Device[0]-0"
[    15.421] (==) Automatically adding devices
[    15.421] (==) Automatically enabling devices
[    15.421] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.429] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    15.429]     Entry deleted from font path.
[    15.429]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    15.429] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.429] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.429] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.429] (II) Loader magic: 0x7f40d6b22b00
[    15.429] (II) Module ABI versions:
[    15.429]     X.Org ANSI C Emulation: 0.4
[    15.429]     X.Org Video Driver: 11.0
[    15.429]     X.Org XInput driver : 16.0
[    15.429]     X.Org Server Extension : 6.0
[    15.431] (--) PCI:*(0:0:2:0) 8086:0046:103c:144a rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005050/8
[    15.431] (--) PCI: (0:1:0:0) 1002:68e0:103c:144a rev 0, Mem @  0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00004000/256, BIOS @  0x????????/131072
[    15.431] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.431] (II) "extmod" will be loaded by default.
[    15.431] (II) "dbe" will be loaded by default.
[    15.431] (II) "glx" will be loaded by default.
[    15.431] (II) "record" will be loaded by default.
[    15.431] (II) "dri" will be loaded by default.
[    15.431] (II) "dri2" will be loaded by default.
[    15.431] (II) LoadModule: "extmod"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.448] (II) Module extmod: vendor="X.Org Foundation"
[    15.448]     compiled for 1.11.3, module version = 1.0.0
[    15.448]     Module class: X.Org Server Extension
[    15.448]     ABI class: X.Org Server Extension, version 6.0
[    15.448] (II) Loading extension MIT-SCREEN-SAVER
[    15.448] (II) Loading extension XFree86-VidModeExtension
[    15.448] (II) Loading extension XFree86-DGA
[    15.448] (II) Loading extension DPMS
[    15.448] (II) Loading extension XVideo
[    15.448] (II) Loading extension XVideo-MotionCompensation
[    15.448] (II) Loading extension X-Resource
[    15.448] (II) LoadModule: "dbe"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.448] (II) Module dbe: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension DOUBLE-BUFFER
[    15.449] (II) LoadModule: "glx"
[    15.449] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    15.449] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    15.449]     compiled for 6.9.0, module version = 1.0.0
[    15.449] (II) Loading extension GLX
[    15.449] (II) LoadModule: "record"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.449] (II) Module record: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.13.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension RECORD
[    15.449] (II) LoadModule: "dri"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.449] (II) Module dri: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension XFree86-DRI
[    15.449] (II) LoadModule: "dri2"
[    15.450] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.450] (II) Module dri2: vendor="X.Org Foundation"
[    15.450]     compiled for 1.11.3, module version = 1.2.0
[    15.450]     ABI class: X.Org Server Extension, version 6.0
[    15.450] (II) Loading extension DRI2
[    15.450] (II) LoadModule: "fglrx"
[    15.450] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    15.728] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    15.740]     compiled for 1.4.99.906, module version = 8.91.4
[    15.740]     Module class: X.Org Video Driver
[    15.826] (II) Loading sub module "fglrxdrm"
[    15.826] (II) LoadModule: "fglrxdrm"
[    15.826] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    15.850] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    15.850]     compiled for 1.4.99.906, module version = 8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.850] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.850] (++) using VT number 7

[    15.851] (WW) Falling back to old probe method for fglrx
[    15.931] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.952] (--) Chipset Supported AMD Graphics Processor (0x68E0) found
[    15.958] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    15.958] (II) fglrx: intel VGA device detected, load intel driver.
[    15.958] (II) LoadModule: "intel"
[    15.958] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.958] (II) Module intel: vendor="X.Org Foundation"
[    15.958]     compiled for 1.11.3, module version = 2.17.0
[    15.958]     Module class: X.Org Video Driver
[    15.958]     ABI class: X.Org Video Driver, version 11.0
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.960] ukiOpenDevice: node name is /dev/ati/card0
[    15.960] ukiOpenDevice: open result is 11, (OK)
[    15.960] ukiOpenByBusid: ukiOpenMinor returns 11
[    15.960] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.971] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    15.971] (EE) No devices detected.
[    15.971] (==) Matched intel as autoconfigured driver 0
[    15.971] (==) Matched vesa as autoconfigured driver 1
[    15.971] (==) Matched fbdev as autoconfigured driver 2
[    15.971] (==) Assigned the driver to the xf86ConfigLayout
[    15.971] (II) LoadModule: "intel"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.971] (II) Module intel: vendor="X.Org Foundation"
[    15.971]     compiled for 1.11.3, module version = 2.17.0
[    15.971]     Module class: X.Org Video Driver
[    15.971]     ABI class: X.Org Video Driver, version 11.0
[    15.971] (II) UnloadModule: "intel"
[    15.971] (II) Unloading intel
[    15.971] (II) Failed to load module "intel" (already loaded, 32576)
[    15.971] (II) LoadModule: "vesa"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.972] (II) Module vesa: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 2.3.0
[    15.972]     Module class: X.Org Video Driver
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) LoadModule: "fbdev"
[    15.972] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.972] (II) Module fbdev: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 0.4.2
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.972] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.972] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.972] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.972] (II) VESA: driver for VESA chipsets: vesa
[    15.972] (II) FBDEV: driver for framebuffer: fbdev
[    15.972] (++) using VT number 7

[    15.972] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    15.972] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    15.972] (WW) Falling back to old probe method for fglrx
[    15.972] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.972] (WW) Falling back to old probe method for vesa
[    15.972] (WW) Falling back to old probe method for fbdev
[    15.972] (EE) No devices detected.
[    15.972] 
Fatal server error:
[    15.972] no screens found
[    15.972] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    15.972] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.972] 
```Also here is my lshw -C -video output

```
*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5400 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

```Any help to get this working will be appreciated.

---

### Post by Deradon on 2012-03-22
Running on a fresh 12.04 Daily Build.
PPAs added.

Won't boot X with the following settings.

xorg.conf
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	#BusID       "PCI:1:0:0"
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

```

xorg.log.0
```

[     5.767] 
X.Org X Server 1.12.0
Release Date: 2012-03-04
[     5.767] X Protocol Version 11, Revision 0
[     5.767] Build Operating System: Linux 2.6.24-30-xen i686 Ubuntu
[     5.767] Current Operating System: Linux werbeboten-HP-Pavilion-g6-Notebook-PC 3.2.0-20-generic-pae #32-Ubuntu SMP Thu Mar 22 02:43:40 UTC 2012 i686
[     5.767] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-20-generic-pae root=UUID=cd51926a-213f-455e-bed3-9e4a2e522a22 ro quiet splash vt.handoff=7
[     5.767] Build Date: 08 March 2012  07:07:08AM
[     5.767] xorg-server 2:1.12.0+git20120308+server-1.12-branch.b1be72c5-0ubuntu0ricotz (For technical support please see http://www.ubuntu.com/support) 
[     5.767] Current version of pixman: 0.25.2
[     5.767] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     5.767] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.767] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 23 01:43:49 2012
[     5.768] (==) Using config file: "/etc/X11/xorg.conf"
[     5.768] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.768] (==) ServerLayout "aticonfig Layout"
[     5.768] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     5.768] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     5.769] (**) |   |-->Device "aticonfig-Device[0]-0"
[     5.769] (==) Automatically adding devices
[     5.769] (==) Automatically enabling devices
[     5.769] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.769] 	Entry deleted from font path.
[     5.769] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.769] 	Entry deleted from font path.
[     5.769] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.769] 	Entry deleted from font path.
[     5.769] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.769] 	Entry deleted from font path.
[     5.769] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.769] 	Entry deleted from font path.
[     5.773] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[     5.773] 	Entry deleted from font path.
[     5.773] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[     5.773] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     5.773] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.773] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.773] (II) Loader magic: 0xb778d5a0
[     5.773] (II) Module ABI versions:
[     5.773] 	X.Org ANSI C Emulation: 0.4
[     5.773] 	X.Org Video Driver: 12.0
[     5.773] 	X.Org XInput driver : 16.0
[     5.773] 	X.Org Server Extension : 6.0
[     5.775] (--) PCI:*(0:0:2:0) 8086:0046:103c:1669 rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00006050/8
[     5.775] (--) PCI: (0:1:0:0) 1002:6760:103c:1669 rev 0, Mem @ 0xa0000000/268435456, 0xc6400000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[     5.775] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.775] (II) "extmod" will be loaded by default.
[     5.775] (II) "dbe" will be loaded by default.
[     5.775] (II) "glx" will be loaded by default.
[     5.775] (II) "record" will be loaded by default.
[     5.775] (II) "dri" will be loaded by default.
[     5.775] (II) "dri2" will be loaded by default.
[     5.775] (II) LoadModule: "extmod"
[     5.779] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     5.779] (II) Module extmod: vendor="X.Org Foundation"
[     5.779] 	compiled for 1.12.0, module version = 1.0.0
[     5.779] 	Module class: X.Org Server Extension
[     5.779] 	ABI class: X.Org Server Extension, version 6.0
[     5.779] (II) Loading extension MIT-SCREEN-SAVER
[     5.779] (II) Loading extension XFree86-VidModeExtension
[     5.779] (II) Loading extension XFree86-DGA
[     5.779] (II) Loading extension DPMS
[     5.779] (II) Loading extension XVideo
[     5.779] (II) Loading extension XVideo-MotionCompensation
[     5.779] (II) Loading extension X-Resource
[     5.779] (II) LoadModule: "dbe"
[     5.780] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     5.780] (II) Module dbe: vendor="X.Org Foundation"
[     5.780] 	compiled for 1.12.0, module version = 1.0.0
[     5.780] 	Module class: X.Org Server Extension
[     5.780] 	ABI class: X.Org Server Extension, version 6.0
[     5.780] (II) Loading extension DOUBLE-BUFFER
[     5.780] (II) LoadModule: "glx"
[     5.780] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     5.781] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     5.781] 	compiled for 6.9.0, module version = 1.0.0
[     5.781] (II) Loading extension GLX
[     5.781] (II) LoadModule: "record"
[     5.788] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     5.788] (II) Module record: vendor="X.Org Foundation"
[     5.788] 	compiled for 1.12.0, module version = 1.13.0
[     5.788] 	Module class: X.Org Server Extension
[     5.788] 	ABI class: X.Org Server Extension, version 6.0
[     5.788] (II) Loading extension RECORD
[     5.788] (II) LoadModule: "dri"
[     5.789] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     5.789] (II) Module dri: vendor="X.Org Foundation"
[     5.789] 	compiled for 1.12.0, module version = 1.0.0
[     5.789] 	ABI class: X.Org Server Extension, version 6.0
[     5.789] (II) Loading extension XFree86-DRI
[     5.789] (II) LoadModule: "dri2"
[     5.790] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     5.790] (II) Module dri2: vendor="X.Org Foundation"
[     5.790] 	compiled for 1.12.0, module version = 1.2.0
[     5.790] 	ABI class: X.Org Server Extension, version 6.0
[     5.790] (II) Loading extension DRI2
[     5.790] (II) LoadModule: "fglrx"
[     5.790] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     5.857] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     5.858] 	compiled for 1.4.99.906, module version = 8.95.3
[     5.858] 	Module class: X.Org Video Driver
[     5.859] (II) Loading sub module "fglrxdrm"
[     5.859] (II) LoadModule: "fglrxdrm"
[     5.860] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.861] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     5.861] 	compiled for 1.4.99.906, module version = 8.95.3
[     5.861] (II) ATI Proprietary Linux Driver Version Identifier:8.95.3
[     5.862] (II) ATI Proprietary Linux Driver Release Identifier: 8.95                                 
[     5.862] (II) ATI Proprietary Linux Driver Build Date: Feb 14 2012 21:04:52
[     5.862] (++) using VT number 7

[     5.862] (WW) Falling back to old probe method for fglrx
[     5.902] (II) Loading PCS database from /etc/ati/amdpcsdb
[     5.905] (--) Chipset Supported AMD Graphics Processor (0x6760) found
[     5.905] (II) fglrx: intel VGA device detected, load intel driver.
[     5.905] (II) LoadModule: "intel"
[     5.906] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.906] (II) Module intel: vendor="X.Org Foundation"
[     5.906] 	compiled for 1.12.0, module version = 2.18.0
[     5.906] 	Module class: X.Org Video Driver
[     5.906] 	ABI class: X.Org Video Driver, version 12.0
[     5.909] ukiDynamicMajor: failed to open /proc/ati/major
[     5.909] ukiDynamicMajor: failed to open /proc/ati/major
[     5.910] (WW) PowerXpress feature is not supported
[     5.910] (EE) No devices detected.
[     5.910] (==) Matched intel as autoconfigured driver 0
[     5.910] (==) Matched vesa as autoconfigured driver 1
[     5.910] (==) Matched fbdev as autoconfigured driver 2
[     5.910] (==) Assigned the driver to the xf86ConfigLayout
[     5.910] (II) LoadModule: "intel"
[     5.911] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.911] (II) Module intel: vendor="X.Org Foundation"
[     5.911] 	compiled for 1.12.0, module version = 2.18.0
[     5.911] 	Module class: X.Org Video Driver
[     5.911] 	ABI class: X.Org Video Driver, version 12.0
[     5.911] (II) UnloadModule: "intel"
[     5.911] (II) Unloading intel
[     5.911] (II) Failed to load module "intel" (already loaded, -1217056484)
[     5.911] (II) LoadModule: "vesa"
[     5.912] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.912] (II) Module vesa: vendor="X.Org Foundation"
[     5.912] 	compiled for 1.11.99.901, module version = 2.3.0
[     5.912] 	Module class: X.Org Video Driver
[     5.912] 	ABI class: X.Org Video Driver, version 12.0
[     5.912] (II) LoadModule: "fbdev"
[     5.912] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.913] (II) Module fbdev: vendor="X.Org Foundation"
[     5.913] 	compiled for 1.11.99.901, module version = 0.4.2
[     5.913] 	Module class: X.Org Video Driver
[     5.913] 	ABI class: X.Org Video Driver, version 12.0
[     5.913] (II) ATI Proprietary Linux Driver Version Identifier:8.95.3
[     5.913] (II) ATI Proprietary Linux Driver Release Identifier: 8.95                                 
[     5.913] (II) ATI Proprietary Linux Driver Build Date: Feb 14 2012 21:04:52
[     5.913] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     5.914] (II) VESA: driver for VESA chipsets: vesa
[     5.914] (II) FBDEV: driver for framebuffer: fbdev
[     5.914] (++) using VT number 7

[     5.914] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     5.914] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     5.914] (WW) Falling back to old probe method for fglrx
[     5.914] (II) Loading PCS database from /etc/ati/amdpcsdb
[     5.914] (WW) Falling back to old probe method for vesa
[     5.914] (WW) Falling back to old probe method for fbdev
[     5.914] (EE) No devices detected.
[     5.914] 
Fatal server error:
[     5.914] no screens found
[     5.914] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     5.914] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     5.914] 

```


lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

```


Somehow, this looks strange in log:

```

[     5.859] (II) LoadModule: "fglrxdrm"
[     5.860] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.861] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     5.861] 	compiled for 1.4.99.906, module version = 8.95.3
[     5.861] (II) ATI Proprietary Linux Driver Version Identifier:8.95.3
[     5.862] (II) ATI Proprietary Linux Driver Release Identifier: 8.95                                 
[     5.862] (II) ATI Proprietary Linux Driver Build Date: Feb 14 2012 21:04:52
[     5.862] (++) using VT number 7

[     5.862] (WW) Falling back to old probe method for fglrx

```

Any ideas?

UPDATE:
[http://forums.fedoraforum.org/showthread.php?p=1564578](http://forums.fedoraforum.org/showthread.php?p=1564578)

uname -r
```

3.2.0-20-generic-pae

```

Got this warning too.
Will try a fresh install on 11.10 for testing purposes tomorrow.

---

### Post by pinguinhood on 2012-03-24
Hi people! I'm trying to get my new notebook working. I have a Intel hd3000 + amd radeon 6750M and I installed ubuntu precise. I added sarvatt ppa (xserver-xorg-video-intel 2.18) than I tried installing ati driver. Here is the problem, because with jokey-gtk I can install only the non-post-release driver,if I try installing the post release version it creashes (I found the bug also in launchpad). I tried compiling the driver downloaded from amd site, but when I try to install them through dpkg I give dependency error referred to the other packages I want to install.
Then I tried installing fglrx-updates through synaptic and terminal. I can install the driver, give the aticonfig --install -f command but when I reboot (without any switch) a window appear saying me that ubuntu is running in low-graphic mode. After reconfiguring lightdm starts again.
Furthermore I can't get Catalyst Control Center working. Any suggestion for the ati driver installation?

---

### Post by delsus on 2012-03-24
> **pinguinhood said:**
> Hi people! I'm trying to get my new notebook working. I have a Intel hd3000 + amd radeon 6750M and I installed ubuntu precise. I added sarvatt ppa (xserver-xorg-video-intel 2.18) than I tried installing ati driver. Here is the problem, because with jokey-gtk I can install only the non-post-release driver,if I try installing the post release version it creashes (I found the bug also in launchpad). I tried compiling the driver downloaded from amd site, but when I try to install them through dpkg I give dependency error referred to the other packages I want to install.
Then I tried installing fglrx-updates through synaptic and terminal. I can install the driver, give the aticonfig --install -f command but when I reboot (without any switch) a window appear saying me that ubuntu is running in low-graphic mode. After reconfiguring lightdm starts again.
Furthermore I can't get Catalyst Control Center working. Any suggestion for the ati driver installation?

Its what we are trying to work out right now, from what I have seen even the Linux gurus are having problems with Intel/ATI hybrid graphics.

---

### Post by sarathsnair on 2012-03-24
is the hybrid graphics problem is over ?
when it complete ? id their any changes in the new ubuntu 12.04

---

### Post by mrvoxel on 2012-03-25
I can confirm that following these instructions I was able to get Hybrid graphics on my Sony S VPCSA!  Excellent!  Of course, ATI graphics card gobbles up over TWICE the power than the integrated (~24-26k mW vs ~8-12k mW.)

I was able to follow the same procedure on Linux Mint and got very good results, in fact faster and smoother than those that I got in Ubuntu 12.04 (which, granted is in Beta.)

One problem I notice, at least with my linux Mint build (haven't confirmed on Ubuntu 12.04) if I try to switch to integrated graphics and restart X, it logs in fine, but doesn't bring up my gnome 3 panels, it seems something hangs up around then.  I change back to dedicated and restart and it works fine again :-\.

delsus:  Not sure if you're still having this problem... I had a very similar problem.  I had to follow Alexislavie's post on installing the newest drivers here:  [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)  after installing the PPAs and that seemed to work.

---

### Post by Alexislavie on 2012-03-25
> **kmas said:**
> so I Downloaded
[http://www2.ati.com/drivers/linux/am...x86.x86_64.run](http://www2.ati.com/drivers/linux/am...x86.x86_64.run)

As normal, I run:
```

$ chmod +x amd-driver-installer-12-2-x86.x86_64.run
$ ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb
```copied the .debs somewhere for safekeeping.

Builds OK, installs OK.

rebooted. 

when it came up, 

```
sudo aticonfig --initial -f
```then rebooted again

I added the ppa ppa:sarvatt/intel-sna

upgraded, and made sure xserver-xorg-video-intel was installed to the latest ppa version, then I rebooted again. 

```
sudo aticonfig --initial -f 
```then I reboot again. 

Now on the terminal 

tried
```
sudo aticonfig --pxl
```It told me I was using the AMD GPU. 

To switch to the Intel gpu I entered this command in a terminal :
```
sudo aticonfig --px-igpu
```I rebooted. as soon as the machine booted, it told me that ubuntu graphics settings wasn't configured properly. It didn't even let me revert from that window. 

I then did ctr alt f1 to get to the command line. 
To switch back to the AMD/ATI gpu I entered this command in a terminal :

```
sudo aticonfig --px-dgpu
```Here is my hardware info
```

makezan@700Z3A:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760]

```here is my xorg.conf
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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

```Questions: I'm I missing something, I'm I supposed to do aticonfig --initial before my reboots?? or after my reboots? 
```
makezan@700Z3A:~$ sudo aticonfig --initial -f 
Warning: you are intending to clear the configuration infomation which you need to recover to High Performance mode, please reboot your machine to aviod inconsistency 
```I already anwered this question for myself. It makes sense. you need to swtich the drivers first before trying to initialize it. 


Is there a way to quickly reboot xserver without rebooting, before it was ctrl alt del, and that service gdm restart isn't relevant because now its unity.

How can I get this to Work.

PLEASE DO INSTALL INTEL DRIVERS BEFORE COMPILING AND INSTALLING ATI DRIVERS !
Otherwise it obviously should not work.

---

### Post by Alexislavie on 2012-03-25
> **delsus said:**
> I posted this in another thread and I don't like posting multiple times, but I hit the wrong prefix, so I don't know if it is getting the right people to see, so I thought I would post it here to see if anyone can help because it seems like I am getting somewhere. (warning wall of text inc)

After failing to get my discreet GPU working in ubuntu 11.10 I decided  to install 12.04 to see if it was working and I believe I am getting  somewhere with it.

I installed the fglrx drivers through jockey and ran ```
aticonfig  --initial -f
```However it came up with this powerXpress error:

```
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
```I however ignored  this and rebooted, and rather than completely failing to boot it boots  to low graphics mode (which is progress) but I cannot configure my  graphics adapter and screen,

Here are my xorg.conf and my xorg.0.log files:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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

``````
[    15.420] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.420] X Protocol Version 11, Revision 0
[    15.420] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    15.420] Current Operating System: Linux mike-ubuntu 3.2.0-17-generic #27-Ubuntu SMP Fri Feb 24 15:37:36 UTC 2012 x86_64
[    15.420] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic  root=UUID=ff081b73-4bb3-4c52-8153-e789022d6a06 ro quiet splash  vt.handoff=7
[    15.420] Build Date: 22 February 2012  03:16:54AM
[    15.420] xorg-server 2:1.11.4-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    15.420] Current version of pixman: 0.24.4
[    15.420]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.420] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.420] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 21 20:44:20 2012
[    15.420] (==) Using config file: "/etc/X11/xorg.conf"
[    15.420] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.421] (==) ServerLayout "aticonfig Layout"
[    15.421] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    15.421] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    15.421] (**) |   |-->Device "aticonfig-Device[0]-0"
[    15.421] (==) Automatically adding devices
[    15.421] (==) Automatically enabling devices
[    15.421] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.429] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    15.429]     Entry deleted from font path.
[    15.429]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    15.429] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.429] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.429] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.429] (II) Loader magic: 0x7f40d6b22b00
[    15.429] (II) Module ABI versions:
[    15.429]     X.Org ANSI C Emulation: 0.4
[    15.429]     X.Org Video Driver: 11.0
[    15.429]     X.Org XInput driver : 16.0
[    15.429]     X.Org Server Extension : 6.0
[    15.431] (--) PCI:*(0:0:2:0) 8086:0046:103c:144a rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005050/8
[    15.431] (--) PCI: (0:1:0:0) 1002:68e0:103c:144a rev 0, Mem @  0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00004000/256, BIOS @  0x????????/131072
[    15.431] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.431] (II) "extmod" will be loaded by default.
[    15.431] (II) "dbe" will be loaded by default.
[    15.431] (II) "glx" will be loaded by default.
[    15.431] (II) "record" will be loaded by default.
[    15.431] (II) "dri" will be loaded by default.
[    15.431] (II) "dri2" will be loaded by default.
[    15.431] (II) LoadModule: "extmod"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.448] (II) Module extmod: vendor="X.Org Foundation"
[    15.448]     compiled for 1.11.3, module version = 1.0.0
[    15.448]     Module class: X.Org Server Extension
[    15.448]     ABI class: X.Org Server Extension, version 6.0
[    15.448] (II) Loading extension MIT-SCREEN-SAVER
[    15.448] (II) Loading extension XFree86-VidModeExtension
[    15.448] (II) Loading extension XFree86-DGA
[    15.448] (II) Loading extension DPMS
[    15.448] (II) Loading extension XVideo
[    15.448] (II) Loading extension XVideo-MotionCompensation
[    15.448] (II) Loading extension X-Resource
[    15.448] (II) LoadModule: "dbe"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.448] (II) Module dbe: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension DOUBLE-BUFFER
[    15.449] (II) LoadModule: "glx"
[    15.449] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    15.449] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    15.449]     compiled for 6.9.0, module version = 1.0.0
[    15.449] (II) Loading extension GLX
[    15.449] (II) LoadModule: "record"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.449] (II) Module record: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.13.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension RECORD
[    15.449] (II) LoadModule: "dri"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.449] (II) Module dri: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension XFree86-DRI
[    15.449] (II) LoadModule: "dri2"
[    15.450] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.450] (II) Module dri2: vendor="X.Org Foundation"
[    15.450]     compiled for 1.11.3, module version = 1.2.0
[    15.450]     ABI class: X.Org Server Extension, version 6.0
[    15.450] (II) Loading extension DRI2
[    15.450] (II) LoadModule: "fglrx"
[    15.450] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    15.728] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    15.740]     compiled for 1.4.99.906, module version = 8.91.4
[    15.740]     Module class: X.Org Video Driver
[    15.826] (II) Loading sub module "fglrxdrm"
[    15.826] (II) LoadModule: "fglrxdrm"
[    15.826] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    15.850] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    15.850]     compiled for 1.4.99.906, module version = 8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.850] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.850] (++) using VT number 7

[    15.851] (WW) Falling back to old probe method for fglrx
[    15.931] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.952] (--) Chipset Supported AMD Graphics Processor (0x68E0) found
[    15.958] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    15.958] (II) fglrx: intel VGA device detected, load intel driver.
[    15.958] (II) LoadModule: "intel"
[    15.958] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.958] (II) Module intel: vendor="X.Org Foundation"
[    15.958]     compiled for 1.11.3, module version = 2.17.0
[    15.958]     Module class: X.Org Video Driver
[    15.958]     ABI class: X.Org Video Driver, version 11.0
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.960] ukiOpenDevice: node name is /dev/ati/card0
[    15.960] ukiOpenDevice: open result is 11, (OK)
[    15.960] ukiOpenByBusid: ukiOpenMinor returns 11
[    15.960] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.971] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    15.971] (EE) No devices detected.
[    15.971] (==) Matched intel as autoconfigured driver 0
[    15.971] (==) Matched vesa as autoconfigured driver 1
[    15.971] (==) Matched fbdev as autoconfigured driver 2
[    15.971] (==) Assigned the driver to the xf86ConfigLayout
[    15.971] (II) LoadModule: "intel"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.971] (II) Module intel: vendor="X.Org Foundation"
[    15.971]     compiled for 1.11.3, module version = 2.17.0
[    15.971]     Module class: X.Org Video Driver
[    15.971]     ABI class: X.Org Video Driver, version 11.0
[    15.971] (II) UnloadModule: "intel"
[    15.971] (II) Unloading intel
[    15.971] (II) Failed to load module "intel" (already loaded, 32576)
[    15.971] (II) LoadModule: "vesa"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.972] (II) Module vesa: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 2.3.0
[    15.972]     Module class: X.Org Video Driver
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) LoadModule: "fbdev"
[    15.972] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.972] (II) Module fbdev: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 0.4.2
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.972] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.972] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.972] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.972] (II) VESA: driver for VESA chipsets: vesa
[    15.972] (II) FBDEV: driver for framebuffer: fbdev
[    15.972] (++) using VT number 7

[    15.972] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    15.972] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    15.972] (WW) Falling back to old probe method for fglrx
[    15.972] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.972] (WW) Falling back to old probe method for vesa
[    15.972] (WW) Falling back to old probe method for fbdev
[    15.972] (EE) No devices detected.
[    15.972] 
Fatal server error:
[    15.972] no screens found
[    15.972] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    15.972] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.972] 
```Also here is my lshw -C -video output

```
*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5400 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

```Any help to get this working will be appreciated.

Do not install fglrx via jockey but compile the packages and install it manually.

---

### Post by Alexislavie on 2012-03-25
To all people having trouble while testing, please remember to verify the PCI adress in the xorg, aticonfig -f --initial only need to be run once, if the generated xorg.conf doesn't work delete it via a tty : sudo rm /etc/X11/xorg.conf and enter startx , to relaunch the X server.

Please do try this on 12.04, not 11.10 ! The xorg version in it is too old.

---

### Post by PerlJedi on 2012-03-27
Wooo Hooo! :guitar:

Thank you to everyone putting their knowledge in this thread!

I now have Ubuntu 11.10 running with switchable graphics on my HP Envy 15. Following the instructions in post #6, and things are running beautifully.

**Update:** The check described in post #22 was also needed to make it work.  My first time around I didn't notice that it was PCI:1:0:0 in xorg.xonf and PCI:01:00:0 in the output from that command, which resulted in failure.

---

### Post by Niccola on 2012-03-27
I'm in a hard work to put the Display Manager working in catalyst center. I dont know what to do anymore.

Simply, the catalyst 12.2 (also 12.1) doesn't appear the Display Manager Option (to switch displays or monitors, change resolution or aspect ratio, etc...) as you can see in the image below:

[IMG]http://dl.dropbox.com/u/13977411/Screenshot2012-03-2723%3A34%3A10.png[/IMG]

So, somebody help me solving this problem, its driving me crazy! I only can manage the Displays using the native ubuntu 11.10 monitor manager and this is a crap, for me!

Thanks

---

### Post by wegah on 2012-03-27
Who write this guide need to put a warning at start.

1- This guide work in MUXED CARDS.
2- This guide WORK in MUXLESS cards that have bios choice for primary card (most of ones here that work have this and doesn't know it).
3- THIS GUIDE will WORK for who DOESN't HAVE BIOS CHOICe, But the manufacturer made the AMD the primary card. 
4- This GUIDE WILL NOT work for who have MUXLESS CARD AND NO BIOS CHOICE TO CHANGE the PRIMARY CARD AND THE BIOS WAS NOT SET BY THE MANUFACTURER HAVING THE AMD CARD BEING THE PRIMARY. 

There is a lot of users that just become in troubles when doing this and being with a black screen after.

vgaswitcheroo is the standard test. that will not harm your install.

If vgaswitcheroo doesn't work for you. This guide will not work to. There is no MAGIC here. The X developers, THE VIDEO CARDS developers are aware this.

It's not a cheat  that will solve this.

---

### Post by wegah on 2012-03-29
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)



--------------------
### STATUS
--------------------

--------------
## ATI hybrid:
--------------

The PowerXpress pre-4.0 models have a mux solution to switch between
discrete and integrated card. For most ATI/Intel hybrid
configurations:

a) try the latest closed-source Catalyst Driver for login/logout card switching,
 or
b) try vga_switcheroo and open-source graphics drivers (kernel 2.6.35 or newer).

The PowerXpress 4.0+ models have a muxless solution to use both cards
and switch on/off the discrete card.
For Muxless PowerXpress 4.0+ models, please submit your DSDT tables
information as described later in this document.

--------------
## NVIDIA hybrid:
--------------

Support is growing quite well in both Bumblebee and IronHide.

There is ongoing work to support for Nvidia Optimus/Intel hybrid
offloading for nouveau drivers:
    [http://thread.gmane.org/gmane.comp.freedesktop.xorg.devel/29140](http://thread.gmane.org/gmane.comp.freedesktop.xorg.devel/29140)
    [http://cgit.freedesktop.org/~airlied/linux/log/?h=drm-prime-dmabuf](http://cgit.freedesktop.org/~airlied/linux/log/?h=drm-prime-dmabuf)
    [http://airlied.livejournal.com/74176.html](http://airlied.livejournal.com/74176.html)
    [http://airlied.livejournal.com/75405.html](http://airlied.livejournal.com/75405.html)

--------------

):P AND THE MOST IMPORTANT..... 
):P DO THIS IF YOUR CARD DOES NOT WORK..

### ACPI Calls
--------------

For a list of DSDT ON/OFF methods, subscribe to the mailing list at
the bottom of the Launchpad page
    [http://launchpad.net/~hybrid-graphics-linux](http://launchpad.net/~hybrid-graphics-linux)
and also follow the blogspot page
    [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
You should also look at this Wiki :
    [http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls)

We are gathering technical information to improve Linux support for
hybrid graphics systems. If you have a switchable graphics laptop,
please submit your laptop's DSDT.dsl and SSDT tables as an attachment
by "adding a comment" at the bottom of this bug report:

    [http://bugs.launchpad.net/bugs/752542](http://bugs.launchpad.net/bugs/752542)

To compile your DSDT and SSDTs information, install if you haven't
already the acpidump and iasl tools:

Ubuntu:
    sudo apt-get install acpidump iasl
Fedora:
    sudo yum install pmtools iasl

Then download the information collector script and run it:

    wget [http://lekensteyn.nl/files/get-acpi-info.sh](http://lekensteyn.nl/files/get-acpi-info.sh)
    sh get-acpi-info.sh

This will create a tar.gz file that you can attach to the bug report.

There is another more complete ACPI dump handles that might be useful
for some models. Details on how to produce it are below:

    git clone git://github.com/Lekensteyn/acpi-stuff.git
    cd acpi-stuff/acpi_dump_info
    make
    sudo make load
    cat /proc/acpi/dump_info > handles.txt

Attach the file in a comment on [http://bugs.launchpad.net/lpbugreporter/+bug/752542/+addcomment](http://bugs.launchpad.net/lpbugreporter/+bug/752542/+addcomment)

This information will allow the full development of hybrid graphics
features for Linux. Thanks for your help!

---

### Post by miatawnt2b on 2012-03-30
Can someone guide me with dependency problems?  I am running 12.04, and installed the sarvatt PPA.  I can't upgrade tehxserver-xorg-intel package because of dependancy issues.

xserver-xorg-video-intel:
 Depends: xorg-video-abi-12  but it is not installable
  Depends: xserver-xorg-core (>=2:1.11.99) but 2:1.11.4-0ubuntu8 is to be installed

---

### Post by kfk2 on 2012-03-31
Got it working with 12.04 Precise! Didn't need any ppa, so all that trying xorg-edgers was not needed. Simply install the fglrx driver and then run:
 sudo aticonfig --initial

Then to switch to integrated gpu, run
 sudo aticonfig --px-igpu
and restart X.

To Switch to discrete gpu: 
 sudo aticonfig --px-dgpu
and restart X.


Laptop is HP dv6-6100 (i7 Quad with Radeon HD 6700M and i915)


fglrx version 2:8.960-0ubuntu1
xserver-xorg-video-intel version 2:2.17.0-1ubuntu4

---

### Post by aeronutt on 2012-04-01
Wow...I just tried this on Precise Beta2, and it works...almost.
Loaded fglrx from the repositories, ran "sudo aticonfig --initial", and now catalyst runs!! (Never successful before), and switching between Intel integrated graphics and ATI grapics is as simple as:

Then to switch to integrated gpu, run
sudo aticonfig --px-igpu
and restart X.

To Switch to discrete gpu:
sudo aticonfig --px-dgpu
and restart X.

...BUT...and the only but.
**When using integrated graphics, only Ubuntu2D works. (3D works fine with ATI GPU is selected).**

Anyone have a fix for this?

---

### Post by pinguinhood on 2012-04-02
Finally works for me too!!! (Samsung serie 7 chronos, ubuntu 12.04)
I had to remove the ppa and reinstall the driver. All seems to work well, I can switch to intel graphic (simple with catalyst control center).

It is normal that only unity 2d works, unity 3d require more resource that integrated graphic doesn't have. (IMHO Unity 2D looks very good in this version of Ubuntu!)

Thank you very much!!!

---

### Post by aeronutt on 2012-04-02
> **pinguinhood said:**
> ....
It is normal that only unity 2d works, unity 3d require more resource that integrated graphic doesn't have. ...

On other loads (eg 11.04, Mint12) Unity3D works fine using my Intel i3 integrated graphics using open drivers (with my AMD discrete GPU turned off).

---

### Post by kmas on 2012-04-02
any one gets this warning? 

```
makezan@700Z3A:~$ sudo aticonfig --px-igpu
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

```

I haven't restarted the x server just yet. 

> **aeronutt said:**
> Wow...I just tried this on Precise Beta2, and it works...almost.
Loaded fglrx from the repositories, ran "sudo aticonfig --initial", and now catalyst runs!! (Never successful before), and switching between Intel integrated graphics and ATI grapics is as simple as:

Then to switch to integrated gpu, run
sudo aticonfig --px-igpu
and restart X.

To Switch to discrete gpu:
sudo aticonfig --px-dgpu
and restart X.

...BUT...and the only but.
**When using integrated graphics, only Ubuntu2D works. (3D works fine with ATI GPU is selected).**

Anyone have a fix for this?

---

### Post by pinguinhood on 2012-04-02
> **aeronutt said:**
> On other loads (eg 11.04, Mint12) Unity3D works fine using my Intel i3 integrated graphics using open drivers (with my AMD discrete GPU turned off).
Sorry, I didn't know that.

---

### Post by aeronutt on 2012-04-02
> **pinguinhood said:**
> Sorry, I didn't know that.

No worries...it does take a few tweaks to get it to work in 3D mode!

---

### Post by onefthemany on 2012-04-03
> **aeronutt said:**
> Wow...I just tried this on Precise Beta2, and it works...almost.
Loaded fglrx from the repositories, ran "sudo aticonfig --initial", and now catalyst runs!! (Never successful before), and switching between Intel integrated graphics and ATI grapics is as simple as:

Then to switch to integrated gpu, run
sudo aticonfig --px-igpu
and restart X.

To Switch to discrete gpu:
sudo aticonfig --px-dgpu
and restart X.

...BUT...and the only but.
**When using integrated graphics, only Ubuntu2D works. (3D works fine with ATI GPU is selected).**

Anyone have a fix for this?

You don't have to use fglrx or reboot. I can switch between integrated and discreet by doing the following on another thread:

[http://ubuntuforums.org/showthread.php?p=11780425#post11780425](http://ubuntuforums.org/showthread.php?p=11780425#post11780425)

all you have to do is make sure you have gxmessage installed to make the script work.

I have this running on 2 different laptops with switchable graphics and it works great without requiring a reboot.

---

### Post by aeronutt on 2012-04-03
> **onefthemany said:**
> You don't have to use fglrx or reboot. I can switch between integrated and discreet by doing the following on another thread:

[http://ubuntuforums.org/showthread.php?p=11780425#post11780425](http://ubuntuforums.org/showthread.php?p=11780425#post11780425)

all you have to do is make sure you have gxmessage installed to make the script work.

I have this running on 2 different laptops with switchable graphics and it works great without requiring a reboot.

Thanks for the link. Just FYI, here's what I think I know about fglrx vs the method in the script you pointed to:
- fglrx includes proprietary drivers which should perform better than the open drivers. Loaded fglrx is needed if you want to run the proprietary drivers. Certainly if you don't like using proprietary drivers, your method is great.
- I do not need to reboot to use fglrx,simply restart X (eg alt-printscrn-k).
- Just browsing the script, I saw a misspelling of a command, so I'm reluctant to depend on it. ( gnome-session-quit is spelled as gnome-sesseion-quit on one of the lines, didn't look any further at the script.)
- I've tried vgaswitcheroo before, with no luck. Maybe it'll work for me in 12.04, but no need to use that with proprietary drivers and s/w fglrx/catalyst working.

---

### Post by delsus on 2012-04-03
> **kfk2 said:**
> Got it working with 12.04 Precise! Didn't need any ppa, so all that trying xorg-edgers was not needed. Simply install the fglrx driver and then run:
 sudo aticonfig --initial

Then to switch to integrated gpu, run
 sudo aticonfig --px-igpu
and restart X.

To Switch to discrete gpu: 
 sudo aticonfig --px-dgpu
and restart X.


Laptop is HP dv6-6100 (i7 Quad with Radeon HD 6700M and i915)


fglrx version 2:8.960-0ubuntu1
xserver-xorg-video-intel version 2:2.17.0-1ubuntu4

Has anyone tried this on 12.4 with an ati radeon HD 5400 series laptop yet? I can only ever get low graphics mode and I have to restore the default xorg.conf so fglrx will not work, I use the fglrx driver from jokey. or perhaps link me to a compatible version for my graphics card if that is the problem.

---

### Post by kmas on 2012-04-04
I'm going to ask a silly question. So the intel graphics was so that we could have our laptops not discharge as fast as it does under the high power settings correct?? can anyone tell me how much their battery lives improved because mine went from 2:30 to 2:45. 

second silly question, was anyone able to make this work for unity 3d. 

last question how do you restart your xserver without reboot in 12.04.

---

### Post by bidget on 2012-04-04
I can't seem to get my intel graphics to work properly. My AMD graphics will load up just fine, but if I use catalyst to switch to intel, or if I do it via the command line with 'aticonfig --px-igpu' after I restart and login, nothing will display, it is simply the desktop wallpaper. There's no bar along the lefthand side or along the top. To fix it I just restart into the recovery mode and use 'aticonfig --px-dgpu' and then after I restart again everything is working ok.

I'm using 12.04 and have a Lenovo y470p which has a ati 7690m/intel 3000. I would really like to get the intel chip working because my battery life with the 7690m on is HORRIBLE!

I've attached a screenshot of what my catalyst shows as I'm not entirely sure what I have to type to get all of the version numbers etc. to display. I haven't used ubuntu since 7.10, so I am a bit rusty!

Also it should be noted that it is detecting that I have a 7670m, instead of 7690. Not too sure why it's doing that.[IMG]http://i.imgur.com/2Ekfl.png[/IMG]

---

### Post by aeronutt on 2012-04-04
> **bidget said:**
> I can't seem to get my intel graphics to work properly. My AMD graphics will load up just fine, but if I use catalyst to switch to intel, or if I do it via the command line with 'aticonfig --px-igpu' after I restart and login, nothing will display, it is simply the desktop wallpaper. There's no bar along the lefthand side or along the top. To fix it I just restart into the recovery mode and use 'aticonfig --px-dgpu' and then after I restart again everything is working ok.

I'm using 12.04 and have a Lenovo y470p which has a ati 7690m/intel 3000. I would really like to get the intel chip working because my battery life with the 7690m on is HORRIBLE!

I've attached a screenshot of what my catalyst shows as I'm not entirely sure what I have to type to get all of the version numbers etc. to display. I haven't used ubuntu since 7.10, so I am a bit rusty!

Also it should be noted that it is detecting that I have a 7670m, instead of 7690. Not too sure why it's doing that.[IMG]http://i.imgur.com/2Ekfl.png[/IMG]


This sounds like the exact same problem I have. When you switch to integreated (intel) graphics, try using Unity 2D instead of Unity 3D. 

For me, before I loaded fgrlx, intel integrated graphics and Unity3D worked fine.  After loading fglrx, whoooohooo, I can now switch between integrated and discrete graphics, BUT, in integrated graphics mode, only Unity2D works.

---

### Post by Niccola on 2012-04-04
> **aeronutt said:**
> This sounds like the exact same problem I have. When you switch to integreated (intel) graphics, try using Unity 2D instead of Unity 3D. 

For me, before I loaded fgrlx, intel integrated graphics and Unity3D worked fine.  After loading fglrx, whoooohooo, I can now switch between integrated and discrete graphics, BUT, in integrated graphics mode, only Unity2D works.

aeronutt, can you tell me if you have direct rendering when you're using Intel iGP?
just show the output of:

```

$ glxinfo | egrep render

```thanks

---

### Post by bidget on 2012-04-05
Alright! So I figured out how to get 2d to work (click the little ubuntu logo, very clever...) and the intel graphics seems to work just fine. I tried the glxinfo | egrep render and it spit out the following:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile

Any idea why catalyst would still be recognizing my graphics as 7670 instead of 7690 though? Maybe just because it's so new?



Also... Is it just me or do unity 2d/3d look exactly the same...?

---

### Post by sarathsnair on 2012-04-05
i also have this problem

---

### Post by Niccola on 2012-04-05
> **bidget said:**
> Alright! So I figured out how to get 2d to work (click the little ubuntu logo, very clever...) and the intel graphics seems to work just fine. I tried the glxinfo | egrep render and it spit out the following:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile

Any idea why catalyst would still be recognizing my graphics as 7670 instead of 7690 though? Maybe just because it's so new?



Also... Is it just me or do unity 2d/3d look exactly the same...?

bidget,
try to remove the file amdpcsdb in /etc/ati/ as root with the following command:

```
$ sudo rm /etc/ati/amdpcsdb 
```then reboot and check it out again.

if it does not work, I think you have to wait for newer versions of Catalyst. You Graphic Card could too recent to this driver (for linux users) OR you card has the same chipset or identifier that the 7670

----------------------------------------------

Ok, I've figured out this problem (about no rendering at Intel iGP) when switching to iGP the direct render isn't working on intel.

So, I think that's the problem about Unity3D and also Gnome-shell error loading using iGP

When using a fresh installation, the direct render works successfully but, without any switch method.

I'm trying to fix iGP no direct rendering (I think it'll solve most of  performance and hardware problem), but I have no so much time to put on  it so if any of you want to help me just send me an email or lets  talking in this thread.

:!: just some knowledge:
this error occurred with me in older version and just installing  mesa-dri-experimental has solved the problem. However, this was solved  on an old computer without Hybrid Graphics,  I've installed it yesterday  but without success (but no errors). If one of you want to test, be  knowing that it doesn't causes any error for me and feel free to try the  same.

:arrow: Are you using 12.04? :?:

Could you tell me what version of this packages you have?
xserver-xorg-core
xserver-xorg-common
xserver-xorg-video-all 
and 
xserver-xorg-video-intel

thanks

---

### Post by bidget on 2012-04-05
I'll try installing mesa-dri-experimental when I get home from work tonight and see if that changes anything. I'll post all my other info as well. I definitely don't mind helping, it's a fresh installation that I'm working with on a new computer, so I really have nothing to lose.

What commands would I use to find out which versions of those packages/drivers I have?

---

### Post by Niccola on 2012-04-05
I've found the solution!!!!!!
 

 It's not necessary  the mesa-dri-experimental package to solve the problem.
 I've found a weird thing done by AMD fglrx driver during installation, but to make sure it'll work, let's verify if you have the same diagnostic:
 First thing is about glxinfo, if it show no direct rendering, just execute this command:
 ```
 LIBGL_DEBUG=verbose; glxinfo 
``` the first output lines, if appears a lot of 'libGL errors' like below:
 
*libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed*
 *libGL error*: *dlopen* /*usr/lib32/fglrx/dri/i915_dri.so failed*
 
 *if you saw, there's an i915 dri driver that couldn't be loaded for some reason. As you can see, the directory is /usr/lib32/fglrx/dri/ but, if you ls this directory you will not see more than one driver named*
 *fglrx_dri.so*
 *So, I've figured out that when fglrx driver installs it changes the LIBGL_DRIVERS_PATH to its own particular path, such that is: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you write the command below you'll see the output like above:*
 *```
 echo $LIBGL_DRIVERS_PATH 
```*[I]
the output will be something like that: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri[/I]
* if you have the same output as above you just have to add the directory where is the intel dri drivers, lets do that!*
[I]
as you can see in this file : /etc/X11/Xsession.d/10fglrx[/I]
 *```
$ gksu gedit /etc/X11/Xsession.d/10fglrx 
```*
 ```
 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH *
```
*in the fourth line you have the LIBGL_DRIVERS_PATH defined as: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you have the same as above, just add the following path in that fourth line:*
 
*for x86_64 (64 bits): /usr/lib/x86_64-linux-gnu/dri/*
 
*for x86 (32 bits) linux: /usr/lib32/dri/*
 
*just add is with a &#8220;:&#8221; (without quotes) in the end of 4**th** line and put the path above of your respective system to get the direct render working!*
 *The file will be like this:*
 *File /etc/X11/Xsession.d/10fglrx for 64 bits (x86_64) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri * 
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
```*File /etc/X11/Xsession.d/10fglrx for 32 bits (x86) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri://usr/lib32/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
``` *then save the /etc/X11/Xsession.d/10fglrx (must have root privileges) and reboot your system*
 
*then glxinfo | egrep render*
 *and check it out if you'll have direct rendering!*
 *Voilà! Shaazaam! Works*
 
*I've got gnome-shell loading and working sweeeeeeeeeetly without video tearing!!! XBMC also are working sweeeeetly and without video tearing! Good bye cruel World!!!!*
 
*Can someone tell me if Unity 3D works?*

---

### Post by bidget on 2012-04-05
Alright so what I take from that is I just have to edit the /etc/X11/Xsession.d/10fglrx file and add in the proper path to the drivers?

Would my path be the same or would it be something different? Can't wait to try this when I get home!

---

### Post by Niccola on 2012-04-05
> **bidget said:**
> Alright so what I take from that is I just have to edit the /etc/X11/Xsession.d/10fglrx file and add in the proper path to the drivers?

Would my path be the same or would it be something different? Can't wait to try this when I get home!

Yes! You just have to edit it! BUT, make sure about the prognostic explained above

Good luck! ;D

---

### Post by Alexislavie on 2012-04-05
> **bidget said:**
> Alright! So I figured out how to get 2d to work (click the little ubuntu logo, very clever...) and the intel graphics seems to work just fine. I tried the glxinfo | egrep render and it spit out the following:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile

Any idea why catalyst would still be recognizing my graphics as 7670 instead of 7690 though? Maybe just because it's so new?



Also... Is it just me or do unity 2d/3d look exactly the same...?

I think your graphic card isn't supported for the moment, this is why the driver use it as an 7670 instead of a 7690, and because this is not a 7670 you can't change the settings.

---

### Post by eug89 on 2012-04-05
> **Niccola said:**
> I've found the solution!!!!!!
 

 It's not necessary  the mesa-dri-experimental package to solve the problem.
 I've found a weird thing done by AMD fglrx driver during installation, but to make sure it'll work, let's verify if you have the same diagnostic:
 First thing is about glxinfo, if it show no direct rendering, just execute this command:
 ```
 LIBGL_DEBUG=verbose; glxinfo 
``` the first output lines, if appears a lot of 'libGL errors' like below:
 
*libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed*
 *libGL error*: *dlopen* /*usr/lib32/fglrx/dri/i915_dri.so failed*
 
 *if you saw, there's an i915 dri driver that couldn't be loaded for some reason. As you can see, the directory is /usr/lib32/fglrx/dri/ but, if you ls this directory you will not see more than one driver named*
 *fglrx_dri.so*
 *So, I've figured out that when fglrx driver installs it changes the LIBGL_DRIVERS_PATH to its own particular path, such that is: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you write the command below you'll see the output like above:*
 *```
 echo $LIBGL_DRIVERS_PATH 
```*[I]
the output will be something like that: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri[/I]
* if you have the same output as above you just have to add the directory where is the intel dri drivers, lets do that!*
[I]
as you can see in this file : /etc/X11/Xsession.d/10fglrx[/I]
 *```
$ gksu gedit /etc/X11/Xsession.d/10fglrx 
```*
 ```
 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH *
```
*in the fourth line you have the LIBGL_DRIVERS_PATH defined as: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you have the same as above, just add the following path in that fourth line:*
 
*for x86_64 (64 bits): /usr/lib/x86_64-linux-gnu/dri/*
 
*for x86 (32 bits) linux: /usr/lib32/dri/*
 
*just add is with a “:” (without quotes) in the end of 4**th** line and put the path above of your respective system to get the direct render working!*
 *The file will be like this:*
 *File /etc/X11/Xsession.d/10fglrx for 64 bits (x86_64) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri * 
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
```*File /etc/X11/Xsession.d/10fglrx for 32 bits (x86) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri://usr/lib32/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
``` *then save the /etc/X11/Xsession.d/10fglrx (must have root privileges) and reboot your system*
 
*then glxinfo | egrep render*
 *and check it out if you'll have direct rendering!*
 *Voilà! Shaazaam! Works*
 
*I've got gnome-shell loading and working sweeeeeeeeeetly without video tearing!!! XBMC also are working sweeeeetly and without video tearing! Good bye cruel World!!!!*
 
*Can someone tell me if Unity 3D works?*

You're great!!!!:guitar:
I have a dv6 6178sl with radeon 6770m and I was struggling with this problem since I installed ubuntu on this laptop. I can confirm that by doing what you've described I'm able to run unity3d with the integrated graphic using catalyst 12.3 on ubuntu 12.04 beta2.
Thanks again:p

---

### Post by bidget on 2012-04-05
so, here's the output I got. Don't see any errors here...

```
dan@derp:~$ LIBGL_DEBUG=verbose; glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


```

Also I looked into the 7670/7690 issue and they are they exact same chip, only the 7690 is clocked at 725mhz instead of 600. My catalyst shows a 7670m clocked at 725mhz, so everything appears to be fine it's just displaying the wrong model number. I'm not too worried about it.

Where do I proceed from here though? I don't see any problems like you were explaining.

Should I just try adding the driver path to the file anyway...?

---

### Post by Niccola on 2012-04-06
> **eug89 said:**
> You're great!!!!:guitar:
I have a dv6 6178sl with radeon 6770m and I was struggling with this problem since I installed ubuntu on this laptop. I can confirm that by doing what you've described I'm able to run unity3d with the integrated graphic using catalyst 12.3 on ubuntu 12.04 beta2.
Thanks again:p

nice to hear that my solution works for you! ;D

---

### Post by Niccola on 2012-04-06
> **bidget said:**
> so, here's the output I got. Don't see any errors here...

```
dan@derp:~$ LIBGL_DEBUG=verbose; glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


```Also I looked into the 7670/7690 issue and they are they exact same chip, only the 7690 is clocked at 725mhz instead of 600. My catalyst shows a 7670m clocked at 725mhz, so everything appears to be fine it's just displaying the wrong model number. I'm not too worried about it.

Where do I proceed from here though? I don't see any problems like you were explaining.

Should I just try adding the driver path to the file anyway...?

You can continue adding path anyway, but I know whats happens in your case:
I think you've installed liggl1-mesa-dri-experimental because your vendor on glxinfo shows SGI, and not Tungsten. That's why the errors doesn't appear. Remove it, it's not necessary as I said.

Can you please show the following outputs:
```
$ echo $LIBGL_DRIVERS_PATH
```

remove the libgl1-mesa-dri-experimental
reboot your machine
edit adding the path in 10fglrx file
reboot

---

### Post by l0o0 on 2012-04-06
I am in 12.04 with xserver-xorg-video-intel version 2.17. but when i install the catalyst 12.3, do sudo aticonfig --initial -f and reboot. Ubuntu* *is running in *low graphic* mode. how can i solve this problem.
my laptop is acer 4745, ati radeon5650 ande intel HD graphic(inside i5).
i really appreciate someone help me:p

---

### Post by bidget on 2012-04-06
Alright, so I've removed the libgl1-mesa-dri-experimental package. I think in 12.04 it comes already installed, as I don't remember installing it... I also added the path to the intel driver.

```
dan@derp:~$ echo $LIBGL_DRIVERS_PATH
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu
dan@derp:~$ 

```

But I still don't have the direct rendering working!

```
dan@derp:~$ glxinfo | egrep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
dan@derp:~$ 

```

When I check the glxinfo with the verbose option, I still get the following:

```
dan@derp:~$ LIBGL_DEBUG=verbose; glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


```

:(

---

### Post by Niccola on 2012-04-06
> **bidget said:**
> Alright, so I've removed the libgl1-mesa-dri-experimental package. I think in 12.04 it comes already installed, as I don't remember installing it... I also added the path to the intel driver.

```
dan@derp:~$ echo $LIBGL_DRIVERS_PATH
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu
dan@derp:~$ 

```But I still don't have the direct rendering working!

```
dan@derp:~$ glxinfo | egrep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
dan@derp:~$ 

```When I check the glxinfo with the verbose option, I still get the following:

```
dan@derp:~$ LIBGL_DEBUG=verbose; glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 1.4 (3.0 Mesa 8.0.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_packed_pixels, GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_depth_clamp, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x065  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x071 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x078  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x089 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


```:(


sorry but I think your path is wrong!
You said your path as
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu
when it should be
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri

I think you forgot the "dri" subdirectory that contains dri drivers

---

### Post by Niccola on 2012-04-06
> **l0o0 said:**
> I am in 12.04 with xserver-xorg-video-intel version 2.17. but when i install the catalyst 12.3, do sudo aticonfig --initial -f and reboot. Ubuntuis running in *low graphic* mode. how can i solve this problem.
my laptop is acer 4745, ati radeon5650 ande intel HD graphic(inside i5).
i really appreciate someone help me:p

You should remove the installed driver and try again following the steps below: (to remove correctly, check this [link]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx"))

before installing Catalyst 12.3 you should do the following things:

1- install packages dependencies of Catalyst:
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic 
```2-install 32-bit library:
```
sudo apt-get install ia32-libs
```3- Create symlink between 64 and 32 libraries:
```
cd /usr ; sudo ln -svT lib /usr/lib64
```then install the driver 12.3
and sudo aticonfig --initial -f

reboot and check

Instructions can be read [here]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")

---

### Post by sarathsnair on 2012-04-06
i am new in this topic. i have dv6 6121tx from HP. it has 2 graphics processors 

1. Integrated Intel GPU ( my processor is Core i7-2630QM)
2. Dedicated ATI 6770m

i want to use Ubuntu as my primary OS , but the Hybrid graphics problem will not permit me to use Ubuntu, because of the heating problem and less battery backup. 
i came here this thread to resolve my problem. I heared that from 12.04 this problem will be resolved. Is that information is correct ?
i cant understand the solutions given in above posts such as intel ppa, sna, package and editing files , mesa,xorg etc. these are confusing me. I am new in linux. but once i used in my desktop i really love it.
can any one help give a step by step guide to resole this problem?  Remember i am a beginner. At this moment i installed the ubuntu 12.04 beta and i have downloaded catalyst 12.3 driver. what is the next steps ?? thannks in advance

---

### Post by eug89 on 2012-04-06
> **sarathsnair said:**
> i am new in this topic. i have dv6 6121tx from HP. it has 2 graphics processors 

1. Integrated Intel GPU ( my processor is Core i7-2630QM)
2. Dedicated ATI 6770m

i want to use Ubuntu as my primary OS , but the Hybrid graphics problem will not permit me to use Ubuntu, because of the heating problem and less battery backup. 
i came here this thread to resolve my problem. I heared that from 12.04 this problem will be resolved. Is that information is correct ?
i cant understand the solutions given in above posts such as intel ppa, sna, package and editing files , mesa,xorg etc. these are confusing me. I am new in linux. but once i used in my desktop i really love it.
can any one help give a step by step guide to resole this problem?  Remember i am a beginner. At this moment i installed the ubuntu 12.04 beta and i have downloaded catalyst 12.3 driver. what is the next steps ?? thannks in advance
Hi, I basically have your same hardware. In order to install correctly the 12.3 driver I followed this guide [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29) up to the ```
sudo aticonfig --initial -f
``` comand. Then I followed the steps Niccola posted yesterday [http://ubuntuforums.org/showpost.php?p=11819555&postcount=107](http://ubuntuforums.org/showpost.php?p=11819555&postcount=107). This allows you to use Unity3d or gnome shell with the integrated graphic card (intel). 
Lastly, if you want to achieve better battery consumption and working backlight comands you can follow this guide [http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html) only the first part though, where he describes how to edit the etc/default/grub file. Hope this helps solve your problems how it did for me.

---

### Post by bidget on 2012-04-06
```
dan@derp:~$ glxinfo | egrep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, 
dan@derp:~$ 

```

Woohoo!!! I'm also able to use Unity3D and gnome without issues on the integrated graphics.

Now all I have to do is figure out why alt+tab doesn't work and everything will be perfect!

Also I realize this is probably the wrong thread for this, but now that the rendering is working I have noticed a very significant hit to battery life. Before on integrated graphics I was getting about 4.5-5 hours of battery, and now I'm down to 2-3. Still a lot better than running off the ati graphics, but definitely an issue I wouldn't mind working on. Any recommendations?

---

### Post by sarathsnair on 2012-04-06
> **eug89 said:**
> Hi, I basically have your same hardware. In order to install correctly the 12.3 driver I followed this guide [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29) up to the ```
sudo aticonfig --initial -f
``` comand. Then I followed the steps Niccola posted yesterday [http://ubuntuforums.org/showpost.php?p=11819555&postcount=107](http://ubuntuforums.org/showpost.php?p=11819555&postcount=107). This allows you to use Unity3d or gnome shell with the integrated graphic card (intel). 
Lastly, if you want to achieve better battery consumption and working backlight comands you can follow this guide [http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html) only the first part though, where he describes how to edit the etc/default/grub file. Hope this helps solve your problems how it did for me.

So i first install catalyst 12.3 ? Any steps before that ?

---

### Post by eug89 on 2012-04-07
> **sarathsnair said:**
> So i first install catalyst 12.3 ? Any steps before that ?

Yes, you have nothing to do before installing catalyst 12.3. If you want you can try to edit the etc/default/grub file as described in the last link I've posted, it's not related with the graphic cards. 
When you're installing the 12.3 drivers be sure to change the comand ```
sudo sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/oneiric
``` in ```
sudo sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/precise
``` since you have ubuntu 12.04 installed.

---

### Post by sarathsnair on 2012-04-07
> **eug89 said:**
> Yes, you have nothing to do before installing catalyst 12.3. If you want you can try to edit the etc/default/grub file as described in the last link I've posted, it's not related with the graphic cards. 
When you're installing the 12.3 drivers be sure to change the comand ```
sudo sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/oneiric
``` in ```
sudo sh ./amd-driver-installer-12-3-x86.x86_64.run --buildpkg Ubuntu/precise
``` since you have ubuntu 12.04 installed.

i done all the steps u mentioned. but i have no luck. still the fan running noisly and the laptop heats much more. i knw that i cant do anything with ubuntu. First of alli didnt understand the commands and such terms used. i just copy and paste in terminal. Now i want to know that is this problem will completely resolve in new ubuntu 12.04 ? so that i can run without any problem. or is their any development regarding this issue by canonocal developers ?

---

### Post by Genero on 2012-04-07
Salut Alexis,

Merci beaucoup de ta contribution pour ce sujet qui doit concerner de plus en plus de monde ;) Je vais essayer de suivre ta procédure avec une installation fraîche de 12.04. Je t'ai envoyé un message privé, j'espère que tu y répondra.

Bonne journée

-----------

Hi Alexis,

Thanks a lot for your involvement  in this very interesting topic ! More and more users seem concerned these days. I will try to follow the different steps that you have described before, with a fresh installation of Precise 12.04 64bits. I sent you a private message at your hotmail's, I hope you will reply soon.

Bye.

---

### Post by pinguinhood on 2012-04-07
> **Niccola said:**
> sorry but I think your path is wrong!
You said your path as
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu
when it should be
/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri

I think you forgot the "dri" subdirectory that contains dri drivers

I had the same output of Niccola and the trick works to me!
Now my notebook is 100% working(and absolutely noiseless!)!!!

Notebook: Samsung Series 7 Chronos NP700Z5A-S02IT
Graphics: INTEL HD Graphics 3000 + AMD Radeon HD 6750M
OS: Ubuntu 12.04 + kernel 3.2.0-22-generic
xserver-xorg-video-intel + fglrx: from Ubuntu's repository
/etc/X11/Xsession.d/10fglrx: modify as above

Thanks to all!!!

---

### Post by aeronutt on 2012-04-07
Darn, this didn't work for me. I could get to login screen but nothing else, is now hanging after entering password. I've tried to change file back to previous, but looks like something got corrupted. Might need to re-install 12.04 and try again.  This is worth messing with to get it right . :)

---

### Post by aeronutt on 2012-04-08
Got it working, awesome!!  Reinstalled 12.04 beta, installed fglrx from the repositories, edited the one line in the file as described above, and all is good!!  I can now run gnome-shell and unity3d with either AMD gpu or intel imbedded gpu.

---

### Post by Novak on 2012-04-09
Is current beta 12.04 includes compatible Xorg version?I installed it but I havn't tried to do this because last time I tried this caused the same problems as  in the case of [aeronutt]("http://ubuntuforums.org/member.php?u=761978").And how can I see which version of Intel drivers is using?This problem has frustrated me quite a while...

---

### Post by redhat24 on 2012-04-13
Hey!

I have a Dell Vostro 3350 with AMD video card. I've installed ubuntu 12.04 and the latest driver from amd.com (12.3).

Starting with discrete (```
aticonfig --px-dgpu
```) it works fine with default Gnome (I think this is what you are referring as unity 3d), but my laptop gets warm really quick and the fan is really loud. (Though I get a good FPS in fgl_glxgears). When I switch to integrated (```
aticonfig --px-igpu
```), if I start default Gnome it hangs up after login (no unity 3d), but with Gnome 2D option it starts, but flickers heavily (the cursor, the windows etc, it is really annoying).

I would prefer that AMD would be turn off (only integrated) by default and sometimes when I would need some 3D accel, I would turn it on, but integrated would have the primary usage.

Is anybody experiencing this aswell? I can provide any output I can get from commands you need.

Thanks for any guidance!

EDIT:
When I switch I get this in console:
```
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: figyelj!: forcing reinstallation of alternative /usr/lib/pxpress/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: figyelj!: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: figyelj!: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.

PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!

```
I am using 64-bit version of Ubuntu 12.04. Maybe this is the one of the problems?

---

### Post by Alexislavie on 2012-04-14
I'm going to update the 1st post, I installed Ubuntu 12.04 beta 2 today with fglrx (catalyst) 12.3 and it works very well. It seems that the new AMD driver doesn't need the intel driver to have been compiled with the sna option. Which really simplify all the installation.

Just one thing : with the integrated gpu (intel) my cursors blinks a few times everytime I move it, and this doesn't happen with the discrete gpu. Does anyone has an idea to fix this ?

EDIT: This may be because it's a beta version of Ubuntu. I hope it is because of this.

---

### Post by Alexislavie on 2012-04-14
This is an history of the 1st post published. [COLOR=Red]PLEASE DO NOT FOLLOW IT[/COLOR]. GO TO THE FIRST POST TO GET THE INSTRUCTIONS.

> As the title says there is way to get AMD/Intel Hybrid Graphics to work on Ubuntu   and other Linux's distros. I'm actually writing this post under Ubuntu   11.10 and Gnome Shell on a Dell Vostro 3550 computer with a Intel HD   3000 integrated video device and a ATI/AMD 6630M video card, and the video device used right now is the AMD one.

So before, I tell you how did I do and what to know about how the   AMD/Intel Switchable Graphics works, I believe it would be better to   show you a screenshot, so here it is : 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213167&stc=1&d=1330035570[/IMG]
*As you can notice my computer is in French, but I think this isn't a problem for a global understanding of the text.

I - How to make fglrx (the catalyst ATI/AMD driver) communicate with the intel driver ?

1 - Sandy Bridge New Acceleration -SNA

First of all, the major problem that   users are faced when trying to install fglrx is that fglrx to   communicate with the Intel driver and take control of the Xorg server   need the Intel driver package : xserver-xorg-video-intel to have been compiled with the --enable-sna option. Otherwise without that option fglrx doesn't work at all and may not detect any AMD device on your computer. In fact the Sandy Bridge New Acceleration wasn't included into the xserver-xorg-video-intel package   by Ubuntu because that option was known to be too much recent and was   consequently a risk of many bugs for people who actually have a Intel   video device.

2 - Version compatibility between fglrx and xserver-xorg-video-intel

In order to make fglrx properly   works, the intel driver installed must be supported by the actual fglrx   driver installed on your computer.

Here is what I know :
[INDENT]- flgrx (version < 12.1 && version >= 11.6) supports only as most recent the 2.15 Intel's driver version.
[/INDENT][INDENT]- fglrx (version = 12.1) now works with the latest Intel's driver version which is 2.17.
[/INDENT]The conclusion is that no matter if xserver-xorg-video-intel has been compiled with the --enable option if it's version is not compatible with fglrx.

II - Xorg.conf and switching between the two graphics cards.

Supposing you just installed the proper drivers (fglrx + xserver-xorg-video-intel with SNA), you first need to create a xorg.conf, this can be simply done by entering this command :
[QUOTE]sudo aticonfig --initial   -fThis command outputs a valid Xorg.conf that indicate to the   Xserver to give control of the display to the fglrx driver, nothing is   mentioned about the Intel's driver in it.
A thing to note before you continue the reading is that when you   actually switch between the graphics cards you will need to reboot your   system in order to apply the changes.

To know what gpu is used enter this command in a terminal :
> sudo aticonfig --pxlTo switch to the Intel gpu enter this command in a terminal :
> sudo aticonfig --px-igpuTo switch to the AMD/ATI gpu enter this command in a terminal :
> sudo aticonfig --px-dgpuNote : This can also be easily done with the catalyst gui as seen on my screenshot.

The two commands that switch the gpu secondarily calls two scripts   installed automatically by fglrx. Those scripts contains command (mainly   update-alternatives) to indicate to the system which GL's librairies   the Xserver will have to use at next boot. Those two scripts are   developed to work on any Debian based distros, so it totally works out   of the box on Ubuntu.

III - How to install a correct version of xserver-xorg-video-intel and fglrx on Ubuntu to get AMD/Intel Hybrid Graphics to work. [TODO]

Sadly, there is actually no easy way to install a sna version of the xserver-xorg-video-intel   driver, I plan to do a ppa containing it, so you better check this   thread frequently. I hope I will be able to make it before the end of   the week (26 February), if you want to help, please tell me. I suscribed   to this thread, I will receive an email if anybody create a new post.
The Oneiric version of the package is 2.15.901 I will only compile that   one and not the most recent to avoid bugs with Oneiric's Xorg version.

To install the latest AMD/ATI driver an easy way exists just check this page : [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)
But do not install it ! Before I release the Intel driver compiled with sna.

IV - AMD/Intel Hybrid Graphics in the Linux future.

As I said in the first part, by default there is actually no Linux   distribution that provides the xserver-xorg-video-intel package compiled   with --enable-sna. But recently Chris Wilson the main developper of   this driver has released the 2.17 version of it (this is the version   that will be included in Ubuntu 12.04), which according to him brings   many bug fixes and performance improvements. What I hope is that Ubuntu   and other distros will in the future provides by default the Intel   driver compiled with sna, this would make our AMD hybrid card work out   of the box after installation (if the package maintainer also check the  compatibility with  fglrx).

Sadly I don't think this will be available for Ubuntu 12.04 (I think   it's too late to integrate new functionnality into the drivers that  will  be provided).
I'm asking every person reading this post, to create a post, to proove that we are many that depends on this sna option,   to gain the attention of Ubuntu employees. An attention which I hope   will lead to the adoption of the New Sandy Bridge Acceleration before   the release of Ubuntu 12.10.

[CENTER]Any kind of help is welcome, and you can contact me at [EMAIL="dev-lavie.alexis@gmail.com"]dev.lavie.alexis@gmail.com[/EMAIL]

[/CENTER]
 
Useful links :
[http://forums.gentoo.org/viewtopic-p-6936730.html](http://forums.gentoo.org/viewtopic-p-6936730.html) You can thanks that guy because his post really helped me to understand how the ati hybrid graphics works.
[http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics](http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics)   You can also check this Gentoo wiki about hybrid graphics, this is  some  Gentoo's users that actually found first a solution on how to make  AMD  hybrid cards to work on Linux.[/QUOTE]

---

### Post by carlocb on 2012-04-14
Hello everyone! This is my first posts in this forum. In fact I'm not even a ubuntu user (arch actually), but I'm following this as it seems the most updated thread in getting switchable graphics to work with linux in the whole www! :P
So...I have an HP pavilion dv6 6169sl with an intel i7 and radeon 6770hd I guess. I set the bios option to "fixed graphics" opposed to "dynamic" mode. I tried both however.
I tried with fedora 16, installed the fglrx drivers from directly from amd website and it worked. That is: the fglrx got the radeon card working BUT highly unstable. And by that I mean gnome was crashing like 2-3 times an hour. That is NOT usable and/or acceptable for me, so if your achievements are that the discrete graphic runs Xorg but it crashes every 10 minutes just tell me please. The switching feature provided by ccc did not work, so the discrete (buggy) card was the only available.

Then I installed arch linux (my favorite distro) and got running the intel card without heat issues (switching OFF the vgaswitcheroo on boot). The gnome-experience is exceptional: NO crashes ever. The vgaswitcheroo is not able to switch to the discrete card however, it just hangs even if doing it with init runlevel 3 (no X running).

I tried uninstalling the opensource ati drivers and recompiling the intel ones with --enable-sna feature (because with arch that is easy to do), then installing the ati drivers 12.3 from amd website.
NO LUCK this time.
What I mean is: (Xorg.0.log) ---
(EE) Screen 1 deleted because of no matching config section.
Backtrace:
0: /usr/bin/Xorg (xorg_backtrace+0x36) [0x55f646]
1: /usr/bin/Xorg (0x400000+0x163379) [0x563379]
[...] CUT
Segmentation fault at address 0x4
-----
Of course I tried googling the logs but with no luck (except this thread, which I tried reading whole: happened to some, but no answers for this issue).
So I'm here begging for help, because I know it has to work in some way...we need to get a better picture of it so it can be applied to every linux distro.
I'd like to ask to the ones that have this working (like the OP):
- what version of Xorg are you running?
- what version of intel xf86 drivers?
- kernel version?
- is kms or framebuffer working? do you get a nice splash screen?
And, most importantly: is everything really running smoothly? As in...no crashes with discrete, no crashes with internal? Flash player, virtualbox, opening java software like eclipse, mplayer...all running well with either cards?? I don't care about power consumption, as I am on ac like 99% of the times...hell...I wouldn't even care about the integrated if the discrete for which I payed lots of money worked as requested...I wasn't using integrated even on windows...
I just need my laptop to run with linux with no major issues...so if it means switching to ubuntu because we can't figure out how to adapt it I'll go with it...but I'd like to better understand everything...please! ;)

---

### Post by godofcrows on 2012-04-14
Thanks so much been trying to get my gpu to work well with ubuntu for a while. Got it running on my acer 7750g-6444 with an amd 6650m. Ubuntu looks so beautiful now!! :guitar:

---

### Post by Alexislavie on 2012-04-15
> **godofcrows said:**
> Thanks so much been trying to get my gpu to work well with ubuntu for a while. Got it running on my acer 7750g-6444 with an amd 6650m. Ubuntu looks so beautiful now!! :guitar:
Can you more describe your configuration ? Did you test HDMI out and VGA out ? Test them with the integrated and discrete card.

---

### Post by Alexislavie on 2012-04-15
Please try this on a fresh install, AND DO NOT USE VGASWITCHEROO.
I never used Arch Linux, but it should works too if you follow the guide here: [http://wiki.cchtml.com/index.php/Arch_Linux](http://wiki.cchtml.com/index.php/Arch_Linux) for the catalyst installation.
I encourage you to make a post on the Arch Linux forums, and post a link to the ubuntu thread, Arch Linux users may better help you.
As you asked, the system is very stable, with both cards. And power consumption is 4x lower now with the integrated gpu active.

*linux-generic version :* linux-meta (3.2.0.23.25) precise-proposed;
*xorg version :* xorg (1:7.6+12ubuntu1) precise;
*xorg-server version :* xorg-server (2:1.11.4-0ubuntu10) precise;
*xserver-xorg-video-intel version : *xserver-xorg-video-intel (2:2.17.0-1ubuntu4) precise;

---

### Post by carlocb on 2012-04-15
> **Alexislavie said:**
> Please try this on a fresh install, AND DO NOT USE VGASWITCHEROO.
I never used Arch Linux, but it should works too if you follow the guide here: [http://wiki.cchtml.com/index.php/Arch_Linux](http://wiki.cchtml.com/index.php/Arch_Linux) for the catalyst installation.
I encourage you to make a post on the Arch Linux forums, and post a link to the ubuntu thread, Arch Linux users may better help you.
As you asked, the system is very stable, with both cards. And power consumption is 4x lower now with the integrated gpu active.

*linux-generic version :* linux-meta (3.2.0.23.25) precise-proposed;
*xorg version :* xorg (1:7.6+12ubuntu1) precise;
*xorg-server version :* xorg-server (2:1.11.4-0ubuntu10) precise;
*xserver-xorg-video-intel version : *xserver-xorg-video-intel (2:2.17.0-1ubuntu4) precise;
So...first of all thank you very very much for your answer! ;) The fact that it's stable is very reassuring for me. In fact I guess I'll try your method on ubuntu as soon as possible.
The strange thing is that I'm now in your same position, meaning that I have installed the same exact version of xorg-server, the intel driver and the catalyst driver. Strange thing is I'm still getting the same crash of the xorg-server...I thought it was related to the xorg version (was on 1.12 and it's said to not be compatible with catalyst...now I don't know what to think anymore... :(

---

### Post by carlocb on 2012-04-15
Ok...soooo...things are starting to get weirder and weirder...but I'm actually understanding something maybe! I'm sure we can find a solution to get this working in every linux distro!!
So...first of all...I reinstalled the xserver (correct version). The libgl, intel-dri and intel xf86 drivers. Then I reinstalled the catalyst downloaded from amd's website and it is WORKING! What I mean is that discrete graphic card gets recognized and is usable (with direct rendering enabled).
I noted that, if you compile the xf86 intel drivers with --enable-sna (as suggested before) DOES NOT work! I have to omit it (--enable-dri only option).

Things are getting weird when trying to switch to the integrated card!! 
aticonfig --px-igp tells me it can't do the switch (but it actually does it, if you do aticonfig --pxl afterwards you see that integrated is enabled).

-- INTERESTING OBSERVATION:
How does it do that (the switch)? It is my observation that it actually changes a symlink in /usr/lib/xorg/modules/extensions. That folder in my system looks like this:

1. BEFORE installing fglrx (but with intel driver installed) the libglx.so is a symlink to libglx.xorg in the very same folder.

2. WHEN you install fglrx it creates another symlink in that folder: FGL.renamed.libglx.so which points to libglx.xorg. It then makes the libglx.so symlink point to fglrx/fglrx-libglx.so --> this is with DISCRETE graphics selected.

3. SWITCHING means simply changing the libglx.so to point to FGL.renamed.libglx.so...which is nothing more than a pointer to libglx.xorg THEREFORE the situation will be the same as when you were using simply the intel driver, even without fglrx installed.

NOW...what happens is that the aticonfig --px-igp changes that symlink BUT it leaves the xorg.conf which states that Xorg server should use as graphic card the PCI id 1:0:0 (ati card) with the fglrx driver...Xorg crashes!!
I found two equal solutions to this issue:
1. moving /etc/X11/xorg.conf to xorg.conf.old for example
2. editing xorg.conf to have PCI id 0:2:0 (intel card) with the intel driver
Now X starts fine on the intel graphic BUT direct rendering is NOT working. Why? Because of the variables you talked about: if I cat $LIBGL_DRIVERS_PATH in my system it points to /usr/lib32/dri:/usr/lib/dri
folder which contains only the fglrx_dri.so
The correct folder (after intel switching) would be /usr/lib/xorg/modules/dri which contains i915_dri.so and such...

Now the answer is: since I don't have the /etc/X11/xorg.conf.d/10-fglrx file you are talking about...how can I have that variable properly set up when I make the switch?? If I get that right, then I could write a little scripts which does the switch:
1. change the libglx.so symlink to intel one
2. move the xorg.conf out of the way (or maybe not)
3. use the proper $LIBGL_DRIVERS_PATH
4. start gdm

I also have a little concern about the fglrx driver actually switching off the intel card when using the discrete and viceversa. Why?? Because the i915 module gets loaded on boot and it provides the kms, so I doubt it can be shut off. 

Other little concern...try doing the following:
1. start X on the discrete card
2. switch to integrated
3. start X on the integrated
4. switch back to the discrete
5. start X again on the discrete
Do you get a KERNEL PANIC doing this?? That is the case for me. It seems it can't switch again to the discrete card (reproducible error for me). Hard-rebooting however gets the discrete loaded again first an with no issues...

---

### Post by carlocb on 2012-04-15
Ok...I tried changing the $LIBGL_DRIVERS_PATH to the correct one after switching to integrated card but still no luck :(

Thing is REALLY weird, because the single drivers alone are working well. I can use intel drivers correctly if i uninstall fglrx and I can use fglrx right now (with intel drivers installed). But intel drivers don't work anymore...I can't make the switch!! WTF???

---

### Post by delsus on 2012-04-15
Still can't get this working properly with my ATI 5470 card, here is my current xorg.conf, I'm not sure if its been setup properly

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
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

```What seems off to me is under the Device subsection it says Identifier  "aticonfig-Device[0]-0" rather than naming my card, aticonfig --list-adapters shows it as a ```
 0. 01:00.0 ATI Mobility Radeon HD 5000 Series 
```Most of what I am seeing in here is 6000 series cards getting it working and anyone that uses a 5000 series is having problems (on 12.4) of it booting into low graphics mode, I have installed all prereqs with the following commands from the terminal.

```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1  
``````

sudo apt-get install ia32-libs lib32gcc1 libc6-i386
```[FONT=Arial]```
cd /usr ; sudo ln -svT lib /usr/lib64
```[/FONT]
[FONT=Arial]
Any help will be appreciated, this is really annoying me now nothing seems to work for my card everything 
I do to solve it makes it boot into low graphics mode using the fglrx driver, also curiously after I have run 
aticonfig --initial I cannot use fglrxinfo I get the error:

[/FONT]```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12

```[FONT=Arial]

I don't mind editing xorg.conf manually if someone can provide one that should work with my card to try it.

Which does make me think I am missing something, please help.
[/FONT][FONT=Arial]
[/FONT]

---

### Post by carlocb on 2012-04-15
I'm decided to understand this better that I can: I'll try installing ubuntu precise now and see how it works with OP instructions...

---

### Post by eug89 on 2012-04-15
Couple of days ago I did exactly what you described on the first post thanks to Niccola's help, now everything's working fine on my hp dv6 6178sl.
You can add this to the first page:
HP DV6-6178sl, i7 2670QM, Intel HD 3000, AMD 6770m, igpu<->dgpu switch: working, Unity3D/Gnome shell on Intel: working, HDMI Intel/AMD: working/working, VGA Intel/AMD: working/working
Ubuntu 12.04 beta 2 + catalyst 12.3 + 3.3.1-030301-generic
To improve power consumption I added these lines 
```
pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```
On GRUB_CMDLINE_LINUX_DEFAULT in the /etc/default/grub file as described in this article [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)(I also added acpi_backlight=vendor in order to get the backlight controls to work on this laptop).
Thanks again for this useful thread!

---

### Post by carlocb on 2012-04-15
Ok...ubuntu 12.04 beta2 definitely works as written by the OP. This is great! Still can't figure out why is this, but I will...I hope!
Interesting thing to note (don't know if it's the same for you)...when I'm using discrete graphics if I go under "System Settings" > "Details" > "Overview" or "Graphics" show "unknown driver". Intel one is correctly recognized when using discrete instead.
All the other non-working distros I tried (fedora, linux mint 12, archlinux) all showed correctly the fglrx driver when using discrete graphics...it was impossible however to switch to discrete...so this is definitely the best solution so far! ;)

EDIT: Actually now (after reboot which keeps the integrated enabled...WOW!) I tried switching to discrete...it's very nice and flawless and radeon hd6700 series gets correctly recognized in unity "system settings"...

EDIT: Been testing a little more...with java, vbox (things I had real troubles using with ati&fglrx in other distros)...it is working WONDERFULLY!! XD 
So far no crashes _whatsoever_ of the Xorg server or gnome...of course I'm using unity (which I hate)...I would like to try out gnome-shell to see if something changes (like the crashes)...but I'm a little reluctant now that everything is finally working properly (been trying for a week to get this working).
OK...did that...gnome-shell 3.4 WORKS and is STABLE with both cards! ;)

EDIT --- IMPORTANT!!!
Have you tried suspend / hibernate using the fglrx driver on both cards??
This is what I'm observing: using the "suspend" from gnome (or unity) results in a system freeze or kernel panic (visible) *before* the actual suspension takes place and with *both* cards (fglrx is supposed to have problems with suspend from what I've read).
Using pm-suspend command from a root terminal (inside X) works fine on the intel, I'll try the discrete tomorrow I guess. 
It is interesting if this means that gnome "suspend" feature doesn't use the well-tested and stable pm-utils (since using pm-suspend directly doesn't result in a crash). It should be possible to bypass gnome controls completely (like closing lid, pressing button, etc.) and just write the appropriate acpid script calling pm-utils (which provide also the hibernate, that is not available in my ubuntu for some misterious reasons)...

---

### Post by sarathsnair on 2012-04-16
Is the hybrid graphics problem is over ?? !!! Can i install ubuntu 12.04 beta 2 in my laptop with switchable graphics intel hd3000/ati redeon 6770m ? unuty 3d/gnome 3 shel works well with Integrated gpu ?

---

### Post by Tinek on 2012-04-16
Hi all!

I'm a french Ubuntu user trying to fix these switching problems too :D
('scuse for the poor english level)
First of all thanks for your work (I mean all of you trying and trying, and other www contributors).

I found this thread yesterday and I hoped I could add my config in the hardware supported list today. I hoped!.. But something went wrong. I'm always stuck with a "running on low graphic mode" at the beginning. And this time any way to choose reconfigure graphics or anything, I'm sent on tty1. So I think I'll wait a little more (still waiting and trying since 10.04lts ;)).
But I'd like to help a little if I can!

I also have a few questions about Mux(ed/less) :

-I read that muxless cards are powerXpress >=4.0 ati cards (so then all cards newer than HD6xxx series) can we conclude that every card under hd6xxx is muxed?!  That could explain the fact I didn't see that any HD 5xxx/4xxx user was able to run Catalyst drivers properly 
-Could Catalysts Drivers can run on muxed configs? In the page 3 it's told that no, but later on the topic someone say that it works.

One more last thing : while trying to solve my problems I tried a "dsmeg | grep VGA" and then found a 
"[Firmware Bug] : Duplicate ACPI video bus devices for the same VGA controller, plesae try module parameter "video.allow_duplicates=1" if the current driver doesn't work"
Maybe it can help ;)

Keep it up!
Tinek

---

### Post by aeronutt on 2012-04-16
> **sarathsnair said:**
> Is the hybrid graphics problem is over ?? !!! Can i install ubuntu 12.04 beta 2 in my laptop with switchable graphics intel hd3000/ati redeon 6770m ? unuty 3d/gnome 3 shel works well with Integrated gpu ?

I'd say you have a good chance of it working with your configuration. But, there's only one way to know for sure. And remember, this IS still beta.

---

### Post by Alexislavie on 2012-04-16
> **carlocb said:**
> Ok...ubuntu 12.04 beta2 definitely works as written by the OP. This is great! Still can't figure out why is this, but I will...I hope!
Interesting thing to note (don't know if it's the same for you)...when I'm using discrete graphics if I go under "System Settings" > "Details" > "Overview" or "Graphics" show "unknown driver". Intel one is correctly recognized when using discrete instead.
All the other non-working distros I tried (fedora, linux mint 12, archlinux) all showed correctly the fglrx driver when using discrete graphics...it was impossible however to switch to discrete...so this is definitely the best solution so far! ;)

EDIT: Actually now (after reboot which keeps the integrated enabled...WOW!) I tried switching to discrete...it's very nice and flawless and radeon hd6700 series gets correctly recognized in unity "system settings"...

EDIT: Been testing a little more...with java, vbox (things I had real troubles using with ati&fglrx in other distros)...it is working WONDERFULLY!! XD 
So far no crashes _whatsoever_ of the Xorg server or gnome...of course I'm using unity (which I hate)...I would like to try out gnome-shell to see if something changes (like the crashes)...but I'm a little reluctant now that everything is finally working properly (been trying for a week to get this working).
OK...did that...gnome-shell 3.4 WORKS and is STABLE with both cards! ;)

EDIT --- IMPORTANT!!!
Have you tried suspend / hibernate using the fglrx driver on both cards??
This is what I'm observing: using the "suspend" from gnome (or unity) results in a system freeze or kernel panic (visible) *before* the actual suspension takes place and with *both* cards (fglrx is supposed to have problems with suspend from what I've read).
Using pm-suspend command from a root terminal (inside X) works fine on the intel, I'll try the discrete tomorrow I guess. 
It is interesting if this means that gnome "suspend" feature doesn't use the well-tested and stable pm-utils (since using pm-suspend directly doesn't result in a crash). It should be possible to bypass gnome controls completely (like closing lid, pressing button, etc.) and just write the appropriate acpid script calling pm-utils (which provide also the hibernate, that is not available in my ubuntu for some misterious reasons)...

Hibernation doesn't work yes, I didn't test suspend.

---

### Post by sarathsnair on 2012-04-16
> **aeronutt said:**
> I'd say you have a good chance of it working with your configuration. But, there's only one way to know for sure. And remember, this IS still beta.

i just want to know that is the switchable graphics work well on bete 2 ?

---

### Post by Alexislavie on 2012-04-16
Well I discovered some little bugs, they are not related with my solution. If someone has any idea how to correct them, please tell me.
 - On Gnome Classic (gnome-panel), when playing fullscreen flash videos on the AMD graphic, the top and bottom defaults panels doesn't hide, this do not happen when using the Intel graphic. This may be an aticonfig or compiz problem.
 - I experience screen tearing when playing fullscreen videos (Unity, Gnome Classic or Gnome Shell), I tried many settings, nothing worked. In Catalyst Control Center on my precedent computer they were a "Tear Free Desktop" option, I had to tick it, and deactivate Sync to VBlank on compiz and screen tearing disappeared. Problem : there is no such option in Catalyst Control Center for hybrid graphics cards. Do someone knows the aticonfig equivalent command ? Maybe it can be activated via command line ?

Can someone help me and confirm those two bugs ?

---

### Post by Alexislavie on 2012-04-16
> **sarathsnair said:**
> i just want to know that is the switchable graphics work well on bete 2 ?
Yep it works well, just a few screen tearing problems when playing fullscreen videos.
What is your configuration ?

---

### Post by Alexislavie on 2012-04-16
> **Tinek said:**
> Hi all!

I'm a french Ubuntu user trying to fix these switching problems too :D
('scuse for the poor english level)
First of all thanks for your work (I mean all of you trying and trying, and other www contributors).

I found this thread yesterday and I hoped I could add my config in the hardware supported list today. I hoped!.. But something went wrong. I'm always stuck with a "running on low graphic mode" at the beginning. And this time any way to choose reconfigure graphics or anything, I'm sent on tty1. So I think I'll wait a little more (still waiting and trying since 10.04lts ;)).
But I'd like to help a little if I can!

I also have a few questions about Mux(ed/less) :

-I read that muxless cards are powerXpress >=4.0 ati cards (so then all cards newer than HD6xxx series) can we conclude that every card under hd6xxx is muxed?!  That could explain the fact I didn't see that any HD 5xxx/4xxx user was able to run Catalyst drivers properly 
-Could Catalysts Drivers can run on muxed configs? In the page 3 it's told that no, but later on the topic someone say that it works.

One more last thing : while trying to solve my problems I tried a "dsmeg | grep VGA" and then found a 
"[Firmware Bug] : Duplicate ACPI video bus devices for the same VGA controller, plesae try module parameter "video.allow_duplicates=1" if the current driver doesn't work"
Maybe it can help ;)

Keep it up!
Tinek

That thread is for muxless systems only.

---

### Post by sarathsnair on 2012-04-16
> **Alexislavie said:**
> Yep it works well, just a few screen tearing problems when playing fullscreen videos.
What is your configuration ?

I have dv6 6121tx. Intel core i7-2630QM , Intel HD 3000 / HD radeon 6770m  gpu. 4gb ram. Now i am downloading ubuntu 12.04 beta 2 and catalyst 12.3 fglrx driver. Is their any additional requirements ? I am going to install both. will it work ?

---

### Post by Alexislavie on 2012-04-16
> **sarathsnair said:**
> I have dv6 6121tx. Intel core i7-2630QM , Intel HD 3000 / HD radeon 6770m  gpu. 4gb ram. Now i am downloading ubuntu 12.04 beta 2 and catalyst 12.3 fglrx driver. Is their any additional requirements ? I am going to install both. will it work ?

I think it should work with your amd card.

---

### Post by Tinek on 2012-04-16
> **Alexislavie said:**
> That thread is for muxless systems only.

Ok, huum so then I don't understand something :

> **wegah said:**
> 
(...)
1- This guide work in MUXED CARDS.
2- This guide WORK in MUXLESS cards that have bios choice for primary card (most of ones here that work have this and doesn't know it).
(...)


Is there a mistake in the wegah post? The Launchpad page let me think that muxed systems are ok with this method...

I suggest you adding a little part a the beginning of the post.
EDIT: oooops, you did it !

thanks,

---

### Post by carlocb on 2012-04-16
You can write my configuration as fully working however!
HP Pavilion DV6 6169sl - ATI radeon HD6770M + Intel i7. Everything works with this tutorial...tried also using my external monitor (when on integrated graphics)...no issues whatsoever! ;) Great work!!

---

### Post by htrex on 2012-04-16
> **Niccola said:**
> I've found the solution!!!!!!
 

 It's not necessary  the mesa-dri-experimental package to solve the problem.
 I've found a weird thing done by AMD fglrx driver during installation, but to make sure it'll work, let's verify if you have the same diagnostic:
 First thing is about glxinfo, if it show no direct rendering, just execute this command:
 ```
 LIBGL_DEBUG=verbose; glxinfo 
``` the first output lines, if appears a lot of 'libGL errors' like below:
 
*libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed*
 *libGL error*: *dlopen* /*usr/lib32/fglrx/dri/i915_dri.so failed*
 
 *if you saw, there's an i915 dri driver that couldn't be loaded for some reason. As you can see, the directory is /usr/lib32/fglrx/dri/ but, if you ls this directory you will not see more than one driver named*
 *fglrx_dri.so*
 *So, I've figured out that when fglrx driver installs it changes the LIBGL_DRIVERS_PATH to its own particular path, such that is: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you write the command below you'll see the output like above:*
 *```
 echo $LIBGL_DRIVERS_PATH 
```*[I]
the output will be something like that: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri[/I]
* if you have the same output as above you just have to add the directory where is the intel dri drivers, lets do that!*
[I]
as you can see in this file : /etc/X11/Xsession.d/10fglrx[/I]
 *```
$ gksu gedit /etc/X11/Xsession.d/10fglrx 
```*
 ```
 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH *
```
*in the fourth line you have the LIBGL_DRIVERS_PATH defined as: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you have the same as above, just add the following path in that fourth line:*
 
*for x86_64 (64 bits): /usr/lib/x86_64-linux-gnu/dri/*
 
*for x86 (32 bits) linux: /usr/lib32/dri/*
 
*just add is with a “:” (without quotes) in the end of 4**th** line and put the path above of your respective system to get the direct render working!*
 *The file will be like this:*
 *File /etc/X11/Xsession.d/10fglrx for 64 bits (x86_64) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri * 
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
```*File /etc/X11/Xsession.d/10fglrx for 32 bits (x86) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri://usr/lib32/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
``` *then save the /etc/X11/Xsession.d/10fglrx (must have root privileges) and reboot your system*
 
*then glxinfo | egrep render*
 *and check it out if you'll have direct rendering!*
 *Voilà! Shaazaam! Works*
 
*I've got gnome-shell loading and working sweeeeeeeeeetly without video tearing!!! XBMC also are working sweeeeetly and without video tearing! Good bye cruel World!!!!*
 
*Can someone tell me if Unity 3D works?*

It works like a charm,
Thank you Niccola!

---

### Post by sarathsnair on 2012-04-17
I installed ubuntu 12.04 and catalyst 12.3 then run 
sudo aticonfig --initial -f then i restarted. But ubuntu running in low graphics mode message appears. I dont know what to do. One thing is that i didnt run "sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic" before installing catalyst 12.3. Is this is the problem ? how can i uninstall catalyst 12.3 drivers ? And also i cant decrease brightness using function keys ( F3 to increase F2 to decrease ). So it is very hard to look into the screen. Tell me how to resolve this problem also

---

### Post by Unclean009 on 2012-04-17
I can confirm the methods listed in the OP working on my system. 
I have an HP Probook 4530s running AMD Radeon HD 6490M w/ Intel HD 3000

---

### Post by offnix on 2012-04-17
Hi all,
my configuration is: 
ACER 7750g, Intel HD 3000, AMD 6650m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not [COLOR="red"]tested[/COLOR]/not [COLOR="Red"]tested[/COLOR]

you can mark this as tested and working.

thanks for the support.

OffNix :-)

---

### Post by Alexislavie on 2012-04-17
> **sarathsnair said:**
> I installed ubuntu 12.04 and catalyst 12.3 then run 
sudo aticonfig --initial -f then i restarted. But ubuntu running in low graphics mode message appears. I dont know what to do. One thing is that i didnt run "sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic" before installing catalyst 12.3. Is this is the problem ? how can i uninstall catalyst 12.3 drivers ? And also i cant decrease brightness using function keys ( F3 to increase F2 to decrease ). So it is very hard to look into the screen. Tell me how to resolve this problem also

Just reinstall ubuntu it will be simpler than trying to fix your system. Don't forget anything this time while reading the tutorial.

---

### Post by Alexislavie on 2012-04-17
> **carlocb said:**
> You can write my configuration as fully working however!
HP Pavilion DV6 6169sl - ATI radeon HD6770M + Intel i7. Everything works with this tutorial...tried also using my external monitor (when on integrated graphics)...no issues whatsoever! ;) Great work!!

Please don't forget to mention VGA and HDMI, "external monitor working" isn't enough.
Intel HD 3000 ?

---

### Post by sarathsnair on 2012-04-17
> **Alexislavie said:**
> Just reinstall ubuntu it will be simpler than trying to fix your system. Don't forget anything this time while reading the tutorial.

can u explain little more ? Which guide i follow ?

---

### Post by iowabeakster on 2012-04-17
I followed the new instructions in the first post, exactly. 

OS is an up-to-date 12.04.

Computer is a new Asus B43S-X51, intel i5- 2520, with an ATI 6470 card.

I also got the low graphics graphics warning.  Removing the xorg.conf file did not bring back the 2D desktop either.  I have made a few attempts of installing Catalyst driver prior to today, and I used to be able to get the desktop back after removing the xorg.conf file.  So, I had to reinstall the OS (now done 3 times trying to get this working).

Is it possible to get the direct rendering on the integrated chip, without installing fglrx first?

---

### Post by carlocb on 2012-04-17
> **iowabeakster said:**
> I followed the new instructions in the first post, exactly. 

OS is an up-to-date 12.04.

Computer is a new Asus B43S-X51, intel i5- 2520, with an ATI 6470 card.

I also got the low graphics graphics warning.  Removing the xorg.conf file did not bring back the 2D desktop either.  I have made a few attempts of installing Catalyst driver prior to today, and I used to be able to get the desktop back after removing the xorg.conf file.  So, I had to reinstall the OS (now done 3 times trying to get this working).

Is it possible to get the direct rendering on the integrated chip, without installing fglrx first?

Of course you can...that is the "easy" thing! ;) Just make sure you have the i915 and radeon modules, then 
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
Don't make an xorg.conf, the intel card will be recognized by default...
Of course if you would like to install the fglrx afterwards, you'll need to blacklist the radeon module.

---

### Post by nico@nc on 2012-04-17
Hello,

I tried these instructions with the following configuration, and it almost works.

 * Computer: Sony VAIO VPC SE series.
 * Graphic cards: AMD Radeon HD 6470M 512Mo + Intel HD 3000

The problem is that even though direct rendering is said to be enabled:
```
nicolas@nico-ubuntu:~$ glxinfo | egrep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render,
```
...Unity "3D" interface doesn't appear after login. I only get a functional desktop, but no sidebar nor "top bar". And the problem is the same using any of the two GPUs.

It however works when choosing "Ubuntu 2D" (ie. no desktop effect) at login.

What could be wrong?

Thank you!

**edit:** I am using Ubuntu 11.10 (apparently, I can't change my profile as I have less than 50 posts)

---

### Post by ubik89 on 2012-04-17
It works!

I've got a Lenovo G-770 and my graphic cards are Intel HD 3000 and Radeon HD 6650M.

But there is a problem.

When activating the radeon card, there is tearing. Anybody knows how to fix it?

Using the intel one, there is no tearing.

---

### Post by carlocb on 2012-04-17
> **Alexislavie said:**
> Please don't forget to mention VGA and HDMI, "external monitor working" isn't enough.
Intel HD 3000 ?

Sorry...tried VGA, no money for the hdmi cable, lol! ;)

---

### Post by Goronok on 2012-04-17
Does anyone know if an Envy 13 is considered a muxed or muxless setup?  I have an intel GMA4500HD and an ATI HD 4330 which does not switch automatically, but also does not have an option in BIOS to switch.  Everything is done within software on the windows side of things.

Any chance the directions in the OP will work for me?  The intel card works fine off of a fresh install, but it's also the only option. Installing the Radeon or FGLRX drivers brings me to a non-booting system, forcing a full OS re-install.  

I'm on 11.10 - any help that you guys can provide would be greatly appreciated!

---

### Post by carlocb on 2012-04-17
Ok guys...I did a little more testing, so here are my findings...

1. Tried again to get this working on archlinux, but with no success. Discrete works fine, intel doesn't as before. The --px-igpu says it can't switch to the integrated, while in fact it does (changing the symlink libglx.so to the intel one)...but there surely is more than that. 
What I mean is that managing the symlink is one thing, and is probably all switchlibGL and switchlibglx do.
This is confirmed by the fact that if you look at those script on ubuntu (installing with the ati installer, not via apt!!) they are written in python and with a VERY INTERESTING "Copyright 2011 Canonical Ltd."!! Interesting because this could be the reason why I couldn't get this f*** driver to work on *any* distro I tried, *but* ubuntu, lol! ;) Those scripts are different on different distros, where the "official" amd ones use the symlinking, debian uses update-alternatives and the gentoo hack (on the wiki) uses eselect opengl. It is basically the same thing and those scripts should work (and I bet they do).
It is also confirmed by the fact that the error message I see when I try the --px-igpu is not present in those script. 
Soooo the error could be in the part (which is yet to find) where the fglrx actually "tells" our cards something like "power off discrete, switch to integrated". In fact the laptop fans spin a lot, as if both the cards were active...
Now...how could this part be distro-dependent is really strange because I figure this is the "driver" or "kernel-module" part as I see it, and that should be unaffected by things as xorg version, xf86 intel drivers, etc. It could however depend on a kernel version or config?? O_o But that would be really strange...I don't know, I'm open to your ideas as well...

2. (On Ubuntu) Since now I always used the integrated graphics and it works flawlessly so far. I tried to better test the discrete this evening.
Happy to say pm-suspend WORKS on this one too! :D So that's a problem of the gnome sleep management which is easily corrected if you do use suspend function a lot like me.
The card does indeed show tearing issues with fullscreen vids, and that's sad! :( 
There is a REALLY strange bug I noticed just now: the battery icon in the statusbar doesn't get drawn when using the ati card: it's a clickable black spot. Doing "alt+F2 - r" resulted in a gnome crash, "ctrl+alt+F1 - killall Xorg" and that battery icon still isn't showing up, so it could really be related somehow to the driver. 

In the end, amd should *really* be doing something for their lame ****** driver. It sucked years ago, in the ati-era. It continues to suck now. Their catalyst control center is something horrible and a pain-in-the-*** also on windows. The whole thing is basically rubbish. We are their customers, not beta-testers or whatsoever...I'll NEVER EVER EVER buy a f**** ati card again!! :(
(sorry for the swearing against amd but I'm so tired of trying to get to work something that should just work at least at a *DECENT* level and for which I payed for)

---

### Post by Niccola on 2012-04-18
It's always a pleasure for me help the linux community. A lot of bugs in AMD/Intel Hybrid graphics in the linux world were fixed in the past days, any contributions is always welcome.

However, there's still people who don't read everything and do not follow the post as they have to. So, who still have problems should uninstall completely the fglrx driver and remove the Xorg.conf file and of course reboot the machine.

After that, should read the [first post]("http://ubuntuforums.org/showpost.php?p=11712748&postcount=1") that was created by our friend [Alexislavie]("http://ubuntuforums.org/member.php?u=1138228") and have worldwide contributions.

Remember: RTFM!!! ):P

---

### Post by sarathsnair on 2012-04-18
I done all the steps mentioned in the first post. But after i run sudo aticonfig --initial -f and then restart, the "Ubuntu running in Low graphics mode" message appear. What should i do ?

---

### Post by carlocb on 2012-04-18
Ok...tested also the radeon is working with the external monitor (in vga). Thing is, the behavior is very strange:

- with the intel you have your normal gnome-shell on the laptop monitor and an "added desktop" on the external one. What I mean is if you switch virtual desktops, the laptop monitor switches fine, while the external stays "fixed" on the same workspace.

- with the ati it basically "extends" everything on the external monitor, meaning that if you have a fullscreen window, that window becomes "huge" extending also on the other monitor. So - if you press your windows key - you will see the application launcher on the left of your laptop's lcd and the workspaces on the right of the external monitor. The windows in the middle are basically splitted between the twos. I don't know if I made myself clear...sorry but english is not my mother tongue.

There are also other observations:

1. Suspend works with the pm-suspend command (as I said)...so how would you leave your computer on sleep on the office table when you're going away and don't want anyone wandering with your laptop?
```
sudo pm-suspend; gnome-screensaver-command -l
```
So that when you open it up, the lockscreen comes over asking for your password. Well...if you do that a nice kernel panic greets you!! And that is very strange to me. And it could be the reason why pm-suspend alone works, while the gnome "suspend" feature doesn't: it seems that the fglrx driver, when you wake your laptop, takes a little bit of time before being "reactivated". You can see this also because after opening the lid you see a console (no X) for a little while. Will try adding a little sleep between the two commands to see if that fixes it...
[EDIT] It doesn't...it seems you just can't put another command after the pm-suspend, even if it's a sleep. :( 

2. There's more to the battery icon bug I told you yesterday: it seems that some icons are "evil" in some way and disliked by the f*** fglrx driver!! The virtualbox icon in the app drawer is blank too when using the ati...and maybe some other...WHY???

---

### Post by phoenix6434 on 2012-04-19
For all pangolin (32 bit) users with an AMD/Intel Hybrid Graphic Solution. It's possible to use the installation via apt. There's also a direct rendering bug on the integrated card. Here is my solution

You can install the fglrx driver via apt.

```
sudo apt-get install fglrx
```

after installation let's configure the Xserver (xorg.conf file) for the first time:

```
sudo aticonfig --initial -f
```

There is also the bug for direct rendering on the integrated card. To fix it you have to edit the following file (it's nearly the same fix like the one from Niccola):

```
gksu gedit /etc/X11/Xsession.d/10fglrx
```

If you're using a 32bit system add at the end of 1th line this text : ":/usr/lib/i386-linux-gnu/dri" without the quotes. The file should now look like this :


```


LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/i386-linux-gnu/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH

```

If you have the integrated card activated reboot your system.

You can check the result after the reboot with glxinfo. If direct rendering is activated, it shows "direct rendering: yes".

```
glxinfo | grep rendering
```

You can also test it with the glxgears command.

Unity 3d should work now in integrated mode.

---

### Post by sarathsnair on 2012-04-19
i have hp pavilion dv6 6121tx. Intel 3000/ATI 6770m hybrid graphics. How can i decrease my brightness using the function keys ? the brightness is always high and i can't also control it via settings menu

---

### Post by wegah on 2012-04-22
> **Tinek said:**
> Ok, huum so then I don't understand something :



Is there a mistake in the wegah post? The Launchpad page let me think that muxed systems are ok with this method...

I suggest you adding a little part a the beginning of the post.
EDIT: oooops, you did it !

thanks,


Tinek..

This method WORK in MUXED cards. Like series 5000. But of course. You do the choice in your bios and then when you boot you install the catalyst driver like the one default. 
Your computer will act being or having a default discrete card. no mastery. 

Until now, Just in one MSI computer with series 5000 muxed I saw you change the integrated to discrete just by Catalyst control center.


The other side. Everyone that use the supposed muxless cards serie 6000 up and this method work.

How I write. 

1- They have some exotic muxless system, like MAC OS. That have the own mux chip inside computer or some DELL/LENOVO/PINGPONG CHINESE BRANDS. That ACT like a MUXED one same being muxless.
2- They have in bios the choice of primary card output, same when using muxless card ( most of dv6, dv7 hp ones, and do not do a choice of THE CARD  being used, But the path where the default monitor will be out by default).
3- If no choice. And your notebook have the integrate GPU being the default one most of ASUS, DELL, ACER ones. 

But if you are a owner of a EXPENSIVE computer like me using a ENVY second generation with 6850m. and the bios locked and setup to use the GPU bein the primary output card.

YOU ARE ****...

Until now, there is no MAMBOJAMBO or ABRACADABRA we can do. Just because the CATALYST driver find out your card, load modules, everything well. BUT does not find the default OUTPUT device ( monitor) to render. If you use an HDMI external monitor you will find will work most of time. but not the default monitor from our devices. Because the default monitor seems some way trigged in bios to primary gpu and then we have all messages of muxless not being working or not output device found.

Some point in a not near future. What developers will do , or try to do. to find out how to use this TRIGGER to turn the default output monitor to AMD cards and bypass the intel one.

Until this not come under light.

CRY like me... A BEAST. we cant use..

OR..

HP and any computer WITH LOCKED BIOS NEVER MORE.

---

### Post by wegah on 2012-04-22
> **sarathsnair said:**
> i have hp pavilion dv6 6121tx. Intel 3000/ATI 6770m hybrid graphics. How can i decrease my brightness using the function keys ? the brightness is always high and i can't also control it via settings menu

Try to do it.

under /etc/default/grub

Put this

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"

then save

and use the comand

update-grub2


Will work

---

### Post by wegah on 2012-04-22
> **Goronok said:**
> Does anyone know if an Envy 13 is considered a muxed or muxless setup?  I have an intel GMA4500HD and an ATI HD 4330 which does not switch automatically, but also does not have an option in BIOS to switch.  Everything is done within software on the windows side of things.

Any chance the directions in the OP will work for me?  The intel card works fine off of a fresh install, but it's also the only option. Installing the Radeon or FGLRX drivers brings me to a non-booting system, forcing a full OS re-install.  

I'm on 11.10 - any help that you guys can provide would be greatly appreciated!

Goronok

Muxed one. And you have the ADVANCE BIOS mode. Just look around how to enter.
Envy 13 first and second generation do have this advanced bios.

there you can change to  discrete graphics card and install catalyst like a standard computer.

---

### Post by ddonn on 2012-04-25
You may add this configuration to your list of "fully supported computers"
HP Envy15 (Kubuntu), Intel HD 3000, AMD HD 7670M, HDMI Intel/AMD: not tested/not tested, VGA na/na, DisplayPort Intel/AMD: not tested/not tested. 

And a big "thank you" to you and the other contributors for sorting all this out!

---

### Post by eug89 on 2012-04-26
Just installed catalyst 12.4 on precise following the same steps as with 12.3. Everything seems to work, I still need to test vga/hdmi though.

---

### Post by iowabeakster on 2012-04-26
I also followed the instructions on page one, completely, except I substituted these four lines for catalyst 12.4. 

```

cd ~/; mkdir catalyst[12.4]("http://wiki.cchtml.com/index.php/12.4"); cd catalyst[12.4]("http://wiki.cchtml.com/index.php/12.4")/
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-](http://www2.ati.com/drivers/linux/amd-driver-installer-)[12-4]("http://wiki.cchtml.com/index.php/12-4")-x86.x86_64.run
chmod +x amd-driver-installer-[12-4]("http://wiki.cchtml.com/index.php/12-4")-x86.x86_64.run

sudo sh ./amd-driver-installer-[12-4]("http://wiki.cchtml.com/index.php/12-4")-x86.x86_64.run --buildpkg Ubuntu/precise
```Everything downloads, builds, and installs perfectly fine.  No errors... nothing

I run the "aticonfig --initial -f" command and it spits out my xorg.conf file. I give the command to switch to the discrete card, and it responds that it is in high performance mode and using the discrete card. 

and on reboot... low graphics mode

I remove the xorg.conf file and default graphics work again.

I believe that the xorg.conf file generated is the problem (experienced but ignorant linux user guesswork here).  I tried manually messing with the xorg.conf file... and managed to do nothing good.  More screwing around led to total re-installation of Precise.  I have previously tried building the .deb files with catalyst 12.3... tried with jockey... and "sh" ing the blob without manually building and installing the .deb files...  

All with the same results... low graphics on reboot... screw around with it until eventually I screw it up... and reinstall the OS fresh again.  I've reinstalled Precise four times now.

Asus B43S-XH51 
Intel i5-2520
ATI 6470M HD

Anybody gotten a 6470M card working?

---

### Post by SonnyBegood on 2012-04-27
Don't know too much about my hardware details, but...

Got it running on a Sony Vaio VPCSA, with a AMD radeon HD 6600M and some integrated Intel graphics and as well with the amd-fglrx 12-4 version. works a treat. thanks.

---

### Post by brshadow on 2012-04-27
After following the guide here what i get when i try to log in 

[IMG]http://i49.tinypic.com/2z4woyc.jpg[/IMG]

After i Press ok

[IMG]http://i49.tinypic.com/2aep1t.jpg[/IMG]

After I choose "Just for this session"

[IMG]http://i50.tinypic.com/30n858i.jpg[/IMG]

Please help me I don't know how to fix this.

-------------------------------------------------

Computer-----> Laptop HP Pavillion g7-1205ev
CPU---> Intel® Core™ i5-2430M CPU @ 2.40GHz × 4 
Graphics ------------> VESA: Intel®Sandybridge Mobile Graphics 
Card 1: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
Card 2: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
OS --------- > Ubuntu 12.04 Precise Pangolin 64bit

---

### Post by miatawnt2b on 2012-04-27
login as you
sudo -s
cd /path_to_amd-driver-installer
./amd-driver-installer-12-xxx.run
keep pressing enter through the installer
when installer exits, type 'amdconfig -i'
shutdown -r now

---

### Post by carocco on 2012-04-27
Yeeeeeeeaaaahhh! It finally works!!!

For me:

[FONT=Arial][SIZE=2]SONY Vaio VPC-SB1S1E, Intel HD 3000, AMD 6470M, HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]

---

### Post by yoyo007 on 2012-04-27
Followed the instructions just used the 12.4 driver everything seems good except a message I get when I use the switch command. Haven't yet put time into looking for the issue.

```
sudo aticonfig --px-dgpu
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect
```


I do not see any negative effects from it in the short time I have been using it. I used the 12.04 final release of ubuntu and the amd 12.4 driver. I did the beta2 with the 12.3 and did not have the message. 

I am able to use both graphics battery life seems better then before 2 hours to about 4 hours on the intel. I get about 2.5 with the amd. 

I have gone from sad with this laptop to extremely happy now that I can get 4 hours of battery life and now can make use of the amd card.


HP ENVY 14t-2000 CTO, Intel HD 3000, AMD 6630M, HDMI Intel/AMD: not tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested

---

### Post by razorxpress on 2012-04-27
Works for dell N4110 (Sandy bridge/Radeon HD 6400M)

---

### Post by Ikith on 2012-04-27
Can't get this working, I've read everything in this thread and tried all of the methods and aside from wiping out xorg.conf which makes it so I can't do anything, I keep getting kicked in to low graphics mode. Running a AMD Radeon 6700M Series.

---

### Post by analyzer123 on 2012-04-28
Got it working on my Sony VAIO SC series. Specs:

Vaio VPC-SC1AFM/S Intel HD 3000, AMD 6470m
Ubuntu 12.04, AMD driver 12.4

I did get a few warnings as described by yoyo007 above, but thats fine. (Note: to all those who already have ubuntu 11.xx or higher installed alongwith the default amd fglrx driver through jockey - please remove it completely. The instructions are at: 
[http://askubuntu.com/questions/68306/how-do-i-restore-default-video-drivers](http://askubuntu.com/questions/68306/how-do-i-restore-default-video-drivers)

also remove 'jockey' from Ubuntu software center)

Switching works with command line or by opening the catalyst control center app and selecting the appropriate option in switchable graphics.

Note: This notebook (like all Vaio S-series 2010, 2011) have a physical switch to switch between intel/ATI. However that only works in windows where you dont have to restart any "x-server"

for now, that switch is meaningless in linux. Switch using the methods described above.

temperatures are much less, fan is gentle. But yes, the temperatures (esp. with integrated intel gpu) are much lesser in windows. I guess the windows drivers are much more optimized (which is not surprising!)

Thanks Alexi for the perfect instructions! (Do you know if anyone has written a utility to detect the change of switch to perform switching?)

I finally have usable ubuntu alongwith windows on my Vaio!

HDMI Intel/AMD: not tested/not tested
VGA Intel/AMD: not tested/not tested

---

### Post by Ikith on 2012-04-28
Could me not having luck have anything to do with the fact that I updated the kernel as well using dist-upgrade?

---

### Post by iowabeakster on 2012-04-28
Wow, two folks with 6470 cards working!  Both with Sonys... anybody with an Asus?

Could one of you that recently got your 6470 cards working on your Sonys please post the contents of your xorg.conf file?  I would like to see it.

---

### Post by Ikith on 2012-04-28
Anyone get this working with a 7690M XT still having issues with mine even after reinstalling without the kernel update.

---

### Post by Eastsun on 2012-04-28
Hi,[Alexislavie]("http://ubuntuforums.org/member.php?u=1138228").

I have followed your steps bug got some error.

In 
[COLOR=#0000FF]sudo dpkg -i fglrx*.deb

I got messages as:

[/COLOR]Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
[COLOR=#FF0000]Error! Bad return status for module build on kernel: 3.2.0-24-generic-pae (i686)[/COLOR]
Consult /var/lib/dkms/fglrx/8.961/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...

My computer inf: Thinkpad E420, ATI Radeon HD 6630M, with Ubuntu 12.04 x86 alternate.

**[*Any help would* be much appreciated]("http://us.battle.net/sc2/en/forum/topic/4768478313")!**

---

### Post by Joe76000 on 2012-04-28
Bonjour Alexis,

Long time ago... My previous message was on February 26th ! This year of course.

I am running my tests on one of my laptops: **[HP Pavilion DV7-6070ef]("http://h10025.www1.hp.com/ewfrf/wc/product?product=5085483&lc=fr&cc=fr&dlc=fr&lang=fr&cc=fr")**
CPU INTEL Core i7-2630QM with Switchable Graphics dGPU AMD HD6490M / iGPU INTEL HD3000, BIOS version F.1B and 1600 x 900 screen resolution.

** NB:** Switchable Graphics AMD+INTEL... On the HP Pavilion DV6-6000 or DV7-6000 series (only Fixed Mode in the BIOS) and  on DV6-6100 or DV7-6100 series (Fixed or Dynamic Mode setup in BIOS available starting with version F.1A). Users of HP series DV6 and DV7-6100 Series must set Fixed Mode in their BIOS.  But it's impossible to disable neither iGPU  nor dGPU in the BIOS.
We have to keep in mind that the BIOS update can only be done under Windows !

HP explanations about Switchable Graphics under Windows for these above HP Pavilion Series which could help understanding how this works and could be more or less extrapolated to Linux... 
```
[FONT=Courier New]- [Overview of Switchable Graphics or Dual GPUs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02731962&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_usen")
HP notebook PCs with switchable graphics provide the following benefits to mobile
computing:
. The notebook conserves power for longer battery life when handling less demanding
applications.
. When using graphics-intense applications such as games, the discrete graphics
processor enables high performance.
- [Switchable Graphics on Notebooks Configured with Intel and ATI GPUs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03048374&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_usen")
This document contains information pertaining to specific HP notebook PCs configured
with dual Intel and AMD graphics adapters.
- [OpenGL Applications Cannot Be Configured to Use the Discrete GPU]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02948560&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_usen")
This  document pertains to HP Envy 14-2000 series, HP Pavilion dv6-6100 series
and HP Pavilion dv7-6100 Series Entertainment Notebook PCs.[/FONT]
```Some other links:
- [URL="http://www.amd.com/us/products/technologies/switchable-graphics/Pages/dynamic-switchable-graphics.aspx"]AMD Dynamic Switchable Graphics Technology
[/URL]- [AMD Switchable Graphics Technology]("http://www.amd.com/us/products/technologies/switchable-graphics/Pages/switchable-graphics.aspx")
- [AMD PowerXpress 4.0 & Interview with AMD's Asif Rehman]("http://www.rage3d.com/articles/amd_powerxpress4_asif_rehman_interview/")

**=> So now, let's enter into the race...**
After a fresh installation of Ubuntu 12.04 LTS RTM, I have tried both proprietary AMD drivers proposed by Ubuntu. And of course there were not successful at all, a real nightmare. :(

[B]=> So, as I said it previously, I have made a second full and fresh installation of Ubuntu 12.04 LTS 64-bits on my DV7 applying your updated solution *VERSION 2 *in the first post of this subject.
*[FONT=Arial][SIZE=2]-> HP DV7-6070ef [/SIZE][/FONT]with Switchable Graphics and both WLan and Bluetooth on:*[/B]
- iGPU INTEL HD3000: Working both on AC and on Battery (last +/- 2H45mn with full screen light as not managed by Ubuntu)
- dGPU AMD HD6490M: Working both on AC and on Battery (last +/- 1H30mn with full screen light as not managed by Ubuntu)
- [FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested / working (A/V on Sony LCD TV with 1920 x 1080 screen resolution)
- VGA      Intel/AMD: not tested / not tested.[/SIZE][/FONT]
 [SIZE=2][COLOR=Blue]_**And guess what ? It's working great like a charm for the time being !**_[/COLOR][/SIZE]   8-)  \\:D/

[SIZE=2][COLOR=Red]**=> May 1st - WARNING:**[/COLOR][/SIZE] Further comments to Alexis's 1st post FGLRX update !
I was obliged to make a 3rd fresh installation as bloody Ubuntu updated automatically my working graphic drivers.
For avoiding that, I am now disabling "Additional proprietary drivers (restricted)" in Software sources - Ubuntu Softwares. I hope it will be fine...

**=> AFTER the 1st reboot (initial Ubuntu installation)** - Some comments in French as my Ubuntu is...
```
[FONT=Courier New]UBUNTU Version 12.04 (precise) 64 bits
Noyau Linux 3.2.0-24-generic
GNOME 3.4.1
Mémoire : 5,8 Gio
Processeur : Intel® Core™ i7-2630QM CPU @ 2.00GHz × 8
Espace disque disponible : 34,0 Gio[/FONT]
```
```
[FONT=Courier New]joehp@ubuntu:~$ **glxinfo**
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI[/FONT] [FONT=Courier New]
client glx version string: 1.4
GLX version: 1.4[/FONT] [FONT=Courier New]
OpenGL vendor string: Tungsten Graphics, Inc[/FONT] [FONT=Courier New]
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2
OpenGL shading language version string: 1.30

joehp@ubuntu:~$ **glxgears**[/FONT] [FONT=Courier New]
Running synchronized to the vertical refresh. The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.312 FPS
301 frames in 5.0 seconds = 60.122 FPS
301 frames in 5.0 seconds = 60.125 FPS

**Carte graphique**: Intel® Sandybridge Mobile / Expérience standard[/FONT] [FONT=Courier New]

**[Firefox's Hardware Acceleration Stress Test]("http://hacks.mozilla.org/2010/09/hardware-acceleration/")**[/FONT]  [FONT=Courier New]
How fast is your browser? 60+ FPS[/FONT]
[FONT=Courier New] What is hardware acceleration?
"Hardware acceleration" is basically using the GPU when it’s possible
(instead of the CPU). This makes page-drawing operations faster.[/FONT]
```[B]
=> Screen shoots of ACCC v.12.3:[/B] [IMG]http://ubuntuforums.org/%3Ca%20href=http://imageshack.us/photo/my-images/824/hpdv76070efu1204accc123.jpg/%20target=_blank%3E[IMG]http://img824.imageshack.us/img824/8605/hpdv76070efu1204accc123.jpg[/IMG][IMG]http://img36.imageshack.us/img36/5903/dv76070efu1204accc123.jpg[/IMG]

** => After applying your STEPS 1-2-3 / dGPU AMD Radeon HD6490M**
```
[FONT=Courier New]joehp@ubuntu:~$ **glxinfo**
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
client glx vendor string: ATI[/FONT] [FONT=Courier New]
client glx version string: 1.4
GLX version: 1.4[/FONT] [FONT=Courier New]
OpenGL vendor string: Advanced Micro Devices, Inc.[/FONT] [FONT=Courier New]
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11566 Compatibility Profile Context
OpenGL shading language version string: 4.20

joehp@ubuntu:~$ **glxgears**[/FONT] [FONT=Courier New]
6224 frames in 5.0 seconds = 1244.746 FPS
6211 frames in 5.0 seconds = 1242.163 FPS
6212 frames in 5.0 seconds = 1242.354 FPS

joehp@ubuntu:~$ **fgl_glxgears** (added)
Using GLX_SGIX_pbuffer
3340 frames in 5.0 seconds = 668.000 FPS
3298 frames in 5.0 seconds = 659.600 FPS
3349 frames in 5.0 seconds = 669.800 FPS

**Carte graphique**: AMD Radeon HD 6400M Series / Expérience standard[/FONT] [FONT=Courier New]

**Firefox's Hardware Acceleration Stress Test**[/FONT] [FONT=Courier New]
***How fast is your browser? 30 FPS ! THERE IS A PROBLEM HERE !***[/FONT] [FONT=Courier New]

**ACCC INFORMATIONS**:[/FONT] [FONT=Courier New]
Version Catalyst™                    12.3
Version du package du pilote         8.951-120308a-135854C-ATI
Version du pilote 2D                 8.95.3
Version de Catalyst™ Control Center  2.13
Version de RandR                     1.3
Fournisseur OpenGL         Advanced Micro Devices, Inc.
Moteur de rendu OpenGL     AMD Radeon HD 6400M Series
Version de OpenGL          4.2.11566 Compatibility Profile Context

joehp@ubuntu:~$ **aticonfig --pxl # List current activated GPU**[/FONT][FONT=Courier New]
PowerXpress: Discrete GPU is active (High-Performance mode).

joehp@ubuntu:~$ **fglrxinfo**[/FONT][FONT=Courier New]
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11566 Compatibility Profile Context

joehp@ubuntu:~$ **glxinfo | egrep render**[/FONT] [FONT=Courier New]
direct rendering: Yes
OpenGL renderer string: AMD Radeon HD 6400M Series
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render[/FONT]
```[B]
=> After applying your STEPS 1-2-3 / iGPU INTEL HD3000[/B]
```
[FONT=Courier New]joehp@ubuntu:~$ **glxinfo**
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
GLX version: 1.4
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2
OpenGL shading language version string: 1.30

joehp@ubuntu:~$ **glxgears**
Running synchronized to the vertical refresh. The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.357 FPS
301 frames in 5.0 seconds = 60.100 FPS
301 frames in 5.0 seconds = 60.077 FPS

joehp@ubuntu:~$ **fgl_glxgears** (added - but ratio is strange vs glxgears and dGPU !)
Using GLX_SGIX_pbuffer
300 frames in 5.0 seconds = 60.000 FPS
301 frames in 5.0 seconds = 60.200 FPS
300 frames in 5.0 seconds = 60.000 FPS

**Carte graphique**: Intel® Sandybridge Mobile / Expérience standard

**Firefox's Hardware Acceleration Stress Test**
How fast is your browser? 60+ FPS

**ACCC INFORMATIONS**:
Version Catalyst™                    12.3
Version du package du pilote         8.951-120308a-135854C-ATI
Version du pilote 2D                 8.95.3
Version de Catalyst™ Control Center  2.13
Version de RandR                     1.1
Fournisseur OpenGL         Tungsten Graphics, Inc
Moteur de rendu OpenGL     Mesa DRI Intel(R) Sandybridge Mobile
Version de OpenGL          3.0 Mesa 8.0.2

joehp@ubuntu:~$ **aticonfig --pxl # List current activated GPU**
PowerXpress: Integrated GPU is active (Power-Saving mode).

joehp@ubuntu:~$ **fglrxinfo**
display: :0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2

joehp@ubuntu:~$ **glxinfo | egrep render**
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility,[/FONT]
```You are making the life of lot of users of Switchable Graphics under Ubuntu really easier ! :guitar:
Thanks a lot and much more to YOU (and the folks you have mentioned) for your GREAT solution and contribution to the community... =D>

JOE from France  ):P

---

### Post by brshadow on 2012-04-29
> **miatawnt2b said:**
> login as you
sudo -s
cd /path_to_amd-driver-installer
./amd-driver-installer-12-xxx.run
keep pressing enter through the installer
when installer exits, type 'amdconfig -i'
shutdown -r now

I dont know how to find the path to amd driver... Anyone help ?

---

### Post by brshadow on 2012-04-29
> **wegah said:**
> Who write this guide need to put a warning at start.

1- This guide work in MUXED CARDS.
2- This guide WORK in MUXLESS cards that have bios choice for primary card (most of ones here that work have this and doesn't know it).
3- THIS GUIDE will WORK for who DOESN't HAVE BIOS CHOICe, But the manufacturer made the AMD the primary card. 
4- This GUIDE WILL NOT work for who have MUXLESS CARD AND NO BIOS CHOICE TO CHANGE the PRIMARY CARD AND THE BIOS WAS NOT SET BY THE MANUFACTURER HAVING THE AMD CARD BEING THE PRIMARY. 

There is a lot of users that just become in troubles when doing this and being with a black screen after.

vgaswitcheroo is the standard test. that will not harm your install.

If vgaswitcheroo doesn't work for you. This guide will not work to. There is no MAGIC here. The X developers, THE VIDEO CARDS developers are aware this.

It's not a cheat  that will solve this.

And please explain me what is MUXED cards and how do i find out if i have one ? 

-------------------------------------------------

Computer-----> Laptop HP Pavillion g7-1205ev
CPU---> Intel® Core™ i5-2430M CPU @ 2.40GHz × 4 
Graphics ------------> VESA: Intel®Sandybridge Mobile Graphics 
Card 1: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
Card 2: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
OS --------- > Ubuntu 12.04 Precise Pangolin 64bit

---

### Post by analyzer123 on 2012-04-29
I don't think you're completely correct. vgaswitcheroo does not work in Sony VAIO S-series laptops but the steps mentioned here do make the switchable graphics work correctly.

the 'magic' is really in AMD writing excellent drivers to support their version of switchable graphics in linux.


> **wegah said:**
> Who write this guide need to put a warning at start.

1- This guide work in MUXED CARDS.
2- This guide WORK in MUXLESS cards that have bios choice for primary card (most of ones here that work have this and doesn't know it).
3- THIS GUIDE will WORK for who DOESN't HAVE BIOS CHOICe, But the manufacturer made the AMD the primary card. 
4- This GUIDE WILL NOT work for who have MUXLESS CARD AND NO BIOS CHOICE TO CHANGE the PRIMARY CARD AND THE BIOS WAS NOT SET BY THE MANUFACTURER HAVING THE AMD CARD BEING THE PRIMARY. 

There is a lot of users that just become in troubles when doing this and being with a black screen after.

vgaswitcheroo is the standard test. that will not harm your install.

If vgaswitcheroo doesn't work for you. This guide will not work to. There is no MAGIC here. The X developers, THE VIDEO CARDS developers are aware this.

It's not a cheat  that will solve this.

---

### Post by clement.analogue on 2012-04-29
It doesn't work on my laptop with an ATI Radeon Mobility HD 5400.

---

### Post by electromattic on 2012-04-29
I can report that the solution on Page 1 works successfully on the HP ENVY 15-3090CA.   Logging in using integrated graphics works perfectly in Ubuntu-2D.  When logging in with Ubuntu-3D, I have to manually restart unity (desktop background comes up, but no window manager).
  To do this, I log into tty 1 (ctrl+alt+F1, enter username/pw), then type 'unity <enter>'.  Ctrl+Alt+F7 brings me back to the desktop and everything is fine from there.

---

### Post by dagnachewl on 2012-04-29
Everything went well as per the instruction on page 1. I now have a working ATI driver version 12.4 switchable with Intel on:

Ubuntu 12.04 64-bit

Samsung Chronos 7 series, Intel® Core&#8482; i7-2675QM CPU @ 2.20GHz × 8, AMD Radeon HD 6400M, Tested both -igpu and -dgpu and it works.

But I get the following error while running:
sudo aticonfig --px-igpu or sudo aticonfig --px-dgpu


PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!

restarting X does apply the change. What may be wrong?

Another issue: When on battery, battery life is double with the integrated option. However, the fan often kick starts every now and then and the system is unusable in that fraction of second. This is same on both options. When on power, no issue at all.

Thank you for this useful and clearly written tutorial.

---

### Post by analyzer123 on 2012-04-29
Nothing is wrong:) it is working as it is. logout and login again to see the change.

btw, its a 'warning' and not an error.

> **dagnachewl said:**
> Everything went well as per the instruction on page 1. I now have a working ATI driver version 12.4 switchable with Intel on:

Ubuntu 12.04 64-bit

Samsung Chronos 7 series, Intel® Core™ i7-2675QM CPU @ 2.20GHz × 8, AMD Radeon HD 6400M, Tested both -igpu and -dgpu and it works.

But I get the following error while running:
sudo aticonfig --px-igpu or sudo aticonfig --px-dgpu


PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!

restarting X does apply the change. What may be wrong?

Another issue: When on battery, battery life is double with the integrated option. However, the fan often kick starts every now and then and the system is unusable in that fraction of second. This is same on both options. When on power, no issue at all.

Thank you for this useful and clearly written tutorial.

---

### Post by analyzer123 on 2012-04-29
.

---

### Post by dagnachewl on 2012-04-30
Thank you for the reply above. My other problem is in fact related to a known problem, helas, of hdparm, which causes the hard disk to spin up and down every few seconds. It is not only annoying but potentially dangerous for the hard disk. Apparently, there has been a 'fix' but in vein. Still waiting for a fix from Ubuntu or Linus Torvalds (it is a kernel issue).

Cheers

---

### Post by xtrasyn on 2012-04-30
I just tried this on my ThinkPad EDGE e520, and it worked like a charm :) I didn't need to reinstall from scratch or anything, I just did a web-update from ubuntu 11.10, and then followed the howto in the first post. 3D acceleration works with both integrated and discrete GPU, VGA output works as well (I haven't tried HDMI yet). And, most importantly for me, OpenCL works when the discrete GPU is selected.
Thanks very much for this thread :) Without it, I probably would have spent countless hours trying to make this work ;)

---

### Post by shinylenin on 2012-04-30
Hello!

I have this problem and I hope someone can help me out here. 

I have an ATI 6770m and an Intel chip. The installation for the driver went smoothly and without any problems. The thing is Unity3D doesn't work with the integrated Intel chip. I truely did it the same way as it was explained. Here is my configuration:

[HTML]LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH[/HTML]

What could have went wrong? Tell me if you need any further information!

I would be glad if someone could help me  :)

---

### Post by analyzer123 on 2012-04-30
are you sure you installed ubuntu 64-bit?

> **shinylenin said:**
> Hello!

I have this problem and I hope someone can help me out here. 

I have an ATI 6770m and an Intel chip. The installation for the driver went smoothly and without any problems. The thing is Unity3D doesn't work with the integrated Intel chip. I truely did it the same way as it was explained. Here is my configuration:

[HTML]LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH[/HTML]

What could have went wrong? Tell me if you need any further information!

I would be glad if someone could help me  :)

---

### Post by wegah on 2012-04-30
[QUOTE=brshadow;11886416]And please explain me what is MUXED cards and how do i find out if i have one ? 


MUXED the "MUX" is a kind of SWITH, key, you have in your computer.
Where you can change the cards. Is almost like to change your computer card.
You in fact do have 2 complete video cards inside computer. DIS and IGD.

Because this you need to restart your computer.
when you are with your IGD card. You can install the IGD program/driver like a standard and unique card.

When you are with DIS card ( in case Catalyst ) your system behave like have a standard and single amd card.

Because this you can install catalyst the standard way. Just when switch back to DIS card and using xorg.conf need to change/remove this to.

BUT in most cases if you are not using xorg.conf. with muxed cards. The ubuntu will identify and work well since for the system, seems just one card working. 


The muxles card. By other side. The computer have only one video card output where the 2 CPUS are plugged ( Ok, the more technical will write in case, just exist the IGD card where the DIS are plugged, but no need this technical here to explain).

There is the trouble.
the linux identify both cards processors  and load the modules and turn on both. But we ( in amd case) don't have the TRIGGER that speak the system WHAT CPU is using the output card to monitor.

Some computers, like hp, envy 13, 14, dv4, dv5, dv6, dv7 and others do have the OUTPUT set-up by default using the DIS card. OR. they have an advanced bios menu where they can switch this output ( similar the muxed ones). 

This ones are lucky. Because the CATALYST driver LOAD the module and know the output to monitor.

But who are not lucky in have this bios option or the bios by default are set-up to be the IGD. When we load our graphics. Everything is well. Until the driver module request the output and didn't find it ( what we have in xorg.log  of no EDP found). 

By default. All, 6xxx series from AMD are muxless and old ones no.

BUT.....

Some cards in some brands are exotic. Muxles act like muxed ones and muxed ones act like muxles. 

EXAMPLE are APPLE ones. That muxless or muxed. They use a specific mux chip inside computer. APPLE SPECIFIC.
And some dell ones. Seems have something similar.

---

### Post by wegah on 2012-04-30
> **analyzer123 said:**
> I don't think you're completely correct. vgaswitcheroo does not work in Sony VAIO S-series laptops but the steps mentioned here do make the switchable graphics work correctly.

the 'magic' is really in AMD writing excellent drivers to support their version of switchable graphics in linux.

I'm not 100% correct because I never tested all computers.
but until now, all tests i do with computers ( and was a lot). All ones that work with vgaswitcheroo worked with catalyst. All one that worked with catalyst worked with standard amd drivers. All ones that have troubles with vgaswitcheroo didn't work with catalyst. 

I'm 100% correct? no. There is crazy hardware's with crazy set-ups around there.

one point vgaswitcheroo does not work if you have the catalyst working.

second point, if not work, try to load the standard amd driver in ubuntu using xorg.conf.

The point is. 
AMD is not DOING MAGIc to suport this.

AGAIN.

Who are lucky of do this work. Or have the bios option to switch the card output in BIOS, or the bios option are set-up by default to DIS. 

All others ones that the BIOS come locked and set-up by default to IGD ( the default by the technical papers), Catalyst just doesn't know how to trigger this. Like the same driver in windows do very well.  

now AMD release a new kind of MUXLESS cards. Our only hope are the open source driver. Because I doubt AMd will maintain for long the old muxles cards.

---

### Post by shinylenin on 2012-05-01
I was working on my system but I couldn't find a solution. Therefore I made a new install and now everything works perfectly. :) 

Thanks anyway!

---

### Post by analyzer123 on 2012-05-01
dude, its AMD's driver which is working here to support switchable graphics! so the magic is from AMD's side, no body else. Even with windows drivers - its AMD's graphics drivers which implement the switching, not Intel.

BIOS option to switch is old tech. Most of the new laptops have dynamic switching, where you dont have to do any kind of reboot or login/logout to switch. So there is no 'default' card.

> **wegah said:**
> I'm not 100% correct because I never tested all computers.
but until now, all tests i do with computers ( and was a lot). All ones that work with vgaswitcheroo worked with catalyst. All one that worked with catalyst worked with standard amd drivers. All ones that have troubles with vgaswitcheroo didn't work with catalyst. 

I'm 100% correct? no. There is crazy hardware's with crazy set-ups around there.

one point vgaswitcheroo does not work if you have the catalyst working.

second point, if not work, try to load the standard amd driver in ubuntu using xorg.conf.

The point is. 
AMD is not DOING MAGIc to suport this.

AGAIN.

Who are lucky of do this work. Or have the bios option to switch the card output in BIOS, or the bios option are set-up by default to DIS. 

All others ones that the BIOS come locked and set-up by default to IGD ( the default by the technical papers), Catalyst just doesn't know how to trigger this. Like the same driver in windows do very well.  

now AMD release a new kind of MUXLESS cards. Our only hope are the open source driver. Because I doubt AMd will maintain for long the old muxles cards.

---

### Post by wegah on 2012-05-01
> **analyzer123 said:**
> dude, its AMD's driver which is working here to support switchable graphics! so the magic is from AMD's side, no body else. Even with windows drivers - its AMD's graphics drivers which implement the switching, not Intel.

BIOS option to switch is old tech. Most of the new laptops have dynamic switching, where you dont have to do any kind of reboot n/logout to switch. So there is no 'default' card.


YET there is a lot about INTEL and how the BIOS are set-up.

 
Here you have a fast understand of HOW a muxless from AMD work ( not being more technical to become easy).

[http://www.rage3d.com/articles/amd_powerxpress4_asif_rehman_interview//pics/r3dbaco08.jpg](http://www.rage3d.com/articles/amd_powerxpress4_asif_rehman_interview//pics/r3dbaco08.jpg)

There you understand that in THEORY we have just one complete VIDEO CARD Hardware, The INTEL ONE ( in our case of IGD are intel, because exist a  muxless not use intel, but ati + ati).

The amd in practice just have the acceleration PROCESSOR. That use all HARDWARE from IGD card.

The switch from one to another. Is done in a very easy way of understand. Bridging the output hardware and disabling one or other card.

This default use of OUTPUT HARDWARE is a logic things not a PHYSIC one. 

Then when the manufacturer BUILD your computer and write the BIOS. they decide "WHAT CARD WILL HAVE THE HARDWARE OUTPUT TRIGGERED by default"

And all BIOSES already have this switch of the default OUTPUT. But some manufacturers just crypt the bios and do not allow us to change this. This bios switch is not to do the CARD CHOICE. Like MUXED ones. But what one have the logic enabled by default.

Easy to test this. ( i'm to use HP or MSI example, because is more easy to me).

Go there in Bios.. enter in ADVANCED MENU. If you are lucky of HP allow you do it. ( this is for muxless ones, another brands of computers do have another keys for advanced menu).

almost all dv5, dv6, dv7, envy 13, 14, 15m 17 first generation work with this)
1. Shutdown your computer completely
2. Power on and hit 'esc' to enter the boot menu.
3. Now press F10 immediately followed by the key "A". you have to press "A" after you press F10 and before you are in bios setup screen. 
4. You are now in advanced bios setup. You should see additional tabs and new options.

Now turn by default logic output the AMD card. And use this metod from forum. Will work like a charm. 

Now with your card working under linux. Got to advanced menu again and turn the advanced logic output to integrate one.

BANG. Your computer do not start anymore with AMD.

WHY?

Because your hardware are LOGICALLY SET-UP to make the discrete card use the default monitor output patch. Then the AMD didn't find this "HARDWARE" output and halt ( and the message of

**[COLOR="red"]"[/COLOR]**
No devices detected.
Fatal server error:
no screens found
**[COLOR="red"]"[/COLOR]**
)

this message is exactly this. The KERNEL was loaded. The driver was loaded and working. BUT the card do not have a output to monitor and crash.

Actually, The AMD kernel driver do not work the same way in windows.
Under windows. The AMD catalyst do this swith being your bios setup to default output patch DIS or IGD. Linux no, who have this working are [COLOR="Red"]LUCKY[/COLOR].


Now AMd is changing the PowerXpress/Bacon muxless system to a new one called AMD Enduro. So we will be more in trouble. We need to wait until the open source ones start to support this muxless cards because is obvious AMD will soon treat us like a OLD CARD.

Here we can have a little more about.
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-hybrid-graphics](https://blueprints.launchpad.net/ubuntu/+spec/desktop-p-hybrid-graphics)

[COLOR="red"][SIZE="4"]**"**[/SIZE][/COLOR]
MUXed (with multiplexers, “switchable graphics”)
Every output has a multiplexer that both the integrated (IGP) and discrete GPU’s are connected to and depending on the workload the GPU is switched to the more appropriate GPU.
There are several downsides to this method of implementation [1]:
    * Manual mode changes - the user is required to make the change herself.
    * Transition time - mode change can take several seconds.
    * User Experience - The GPU switch results in screen flicker.
    * Increased cost - due to the need of hardware multiplexers.
The user experience of this method of Hybrid Graphics is not that great even on Windows, due to aforementioned issues in addition to “blocking apps” which reserve the hardware and prevent switching until closed.
[COLOR="red"][SIZE="4"][B]"

"[/B][/SIZE][/COLOR]
 MUXless
**[COLOR="Red"][SIZE="3"]In this implementation the video output is routed via the integrated (IGP) chipset and the more intense graphics work is offloaded to the discrete GPU.[/SIZE][/COLOR]**
The benefits of this implementation are:
    * Possible to automatically enable/disable the discrete GPU
    * Near-instant transition time
    * No screen flicker
    * Less complex/expensive hardware support
[B][SIZE="4"][COLOR="red"]"

"[/COLOR][/SIZE][/B]
**[COLOR="red"][SIZE="3"]Some machines allow selecting between the integrated graphics (IGP) and the discrete GPU from the BIOS, however most ‘low-cost’ implementations do not.[/SIZE][/COLOR]**
"

THEN MY POINT, SOME EXPENSIVE ONES LIKE HP ENVY O NOT TO, TO HELL HP
[B][SIZE="4"][COLOR="red"]"

"[/COLOR][/SIZE][/B]
MUXed Configurations
For **[SIZE="3"]Intel and Radeon open-source drivers[/SIZE]** there is an interface available [SIZE="3"]**called “vga_switcheroo” which does provide the ability to “switch”between integrated and discrete GPUs**[/SIZE]. This does still require a restart of the X server, resulting in a flawed user-experience. Lastly there has been mention of forthcoming Nouveau support within vga_switcheroo [3].
The AMD Catalyst driver has no official support, though scripts have been provided to perform the switching and mucking with the mesa/fglrx libGL flavors. This implementation similarly requires a X server restart.
[COLOR="red"][SIZE="4"][B]"

"[/B][/SIZE][/COLOR]
NOTES:
Problems:
 - binary drivers do not coexist with builtin graphics well
 - installing the binary drivers commits you to the discrete graphics
 - [COLOR="red"]**[SIZE="4"]sometimes outputs are only available via the discrete grahics (which may not be in use)[/SIZE]**[/COLOR] - would like the Displays GUI to indicate possibly *why* they are not available (or at least that any but the suppored outputs ones are not available). Also, the GUI should show pictures of the socket types to help less techincal users.
[COLOR="red"][SIZE="4"]**"**[/SIZE][/COLOR]

The fault is not just from AMD.
There is more under all this troubles. There is a problem with EGO's from X developers, AMD developers, OPEN SOURCE driver developers, KERNEL developers. 

There is to, troubles with how the kernel work with binaries and licenses and HOW the drivers can be integrated.

---

### Post by miatawnt2b on 2012-05-02
Using the howto from post 1, I have hybrid graphics on my Samsung Chronos7 working perfectly. Thanks!

A couple of quick questions...

Is anyone running the 3.4 kernel with Catalyst 12.4 packages? I am currently running the precise latest 3.2.0-24, butI have a need to run 3.4.  Do I need to install 3.4 and rebuild the deb's and install fglrx again?

Second... I am seeing a 29W power draw with the discerete gpu and about 19W with the integrated. I would really like to get this even lower, especially when in descrete mode on battery power.  I saw somewhere someone had wrote some updated config scripts to help with the power savings when on battery for the catalyst, but I can't find it again. I don't believe it was in this thread.  Anyone else come across it, or can help with tweaking the power usage on battery?

Thanks!
-J

---

### Post by Ikith on 2012-05-03
This does not work on HP Envy 17 3070NR with 7690M XT.

---

### Post by wegah on 2012-05-03
> **Ikith said:**
> This does not work on HP Envy 17 3070NR with 7690M XT.

Welcome to the club. Not the envy 17 3d second generation with 6850m.

If you HEX the bios to change the option work at first boot. but the second bood your computer lock in bios start. 

Welcome the brave new world of locked bios. Welcome to the new windows 8 world.

---

### Post by Przedzmirski on 2012-05-03
My configuration is:

"Dell Inspiron 14R (N4110) computer with a Intel HD 3000 integrated video device and a  AMD Radeon  HD 6470M video card"

Haven't tried yet.. :P

Does someone already tried with this configuration???

---

### Post by Ikith on 2012-05-03
> **wegah said:**
> welcome to the club. Not the envy 17 3d second generation with 6850m.

If you hex the bios to change the option work at first boot. But the second bood your computer lock in bios start. 

Welcome the brave new world of locked bios. Welcome to the new windows 8 world.

awesome!

---

### Post by Przedzmirski on 2012-05-04
Im glad to say that i tested and its working!!!!!!!! Just the fan that is getting crazy sometimes, but the temperature isn't so high.
:guitar:

---

### Post by Betonius on 2012-05-05
Hello everyone.

First, thanks you all of you, your posts helped me to finally solve this problem. I'm really new into Ubuntu. Is nice to know that you have the support of a big big community.

Second. I have a Lenovo e520, i5 with sandybridge. Ati HD 6630 and Intel HD graphics. I did all the things in the first post. Everything worked out!:P:KS

Third. :confused:I have questions about the check part: How to i perform the checks?

After i perform the checks. then you can put my laptop model in the "all works" list
Thx in advance

---

### Post by melser.anton on 2012-05-05
Seems to work for a:
HP Pavilion dm4-2160sf (Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz with AMD Radeon HD 6470M, maybe this card is not the exact one, it's 64?0M anyway).

---

### Post by Przedzmirski on 2012-05-06
Btw, the performance of the discrete card in windows is a lot better... I assume that this is caused by the fact that the "switchable graphics" in windows doesn't really switches the cards, just force the discrete when needed, but it is always like : DIS: default for processing and IGD : default for displaying. Here in Ubuntu, we have OR the DIS working OR the IGD. Am I wrong? Sometimes, just for surfing on the net or programming, etc, its better to use the IGD one...

---

### Post by Rabenschwinge on 2012-05-07
Thanks for the guide. At least it works for now. I am using an HP Pavilion dv6-6102sg with Intel Core I5 2430 CPU (including intel HD 3000 graphics) and an AMD Radeon HD 6770M graphics adapter.

**I would strongly discourage anyone with such a computer who depends on using external screens from using Ubuntu 12.04!**

I am still having massive problems using an external screen - any change in the screen setting my cause a crash. And while I managed to use the external VGA screen at work at its native resolution of 1280x1024, it doesn't work for my HDMI screen at home at 1920x1080. A part of the screen remains black, even though the mouse cursor is rendered if I move it into it. Even pulling the HDMI cable or connecting it after XServer started causes the system to hang up.

But I can use the the built in screen without complication and with full 3D support, which is a great thing.

I updated to 12.4 which didn't fix my problems but seems to work fine otherwise earlier today.

---

### Post by o xavi on 2012-05-07
Hi thanks for the post, it did work fine with my laptop:

HP Pavillion dm4 - 2110,  VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller , AMD HD 6470, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: OK / OK

---

### Post by rotten777 on 2012-05-08
Asus B43S - Doesn't work as of May 8 2012. Radeon 6400 series.

---

### Post by debashishone on 2012-05-09
Hey,

It dint worked for me too...I am using generic-pae kernel Ubuntu 12.04 LTS on HP Pavilion dv-6 laptop. The command worked right up until creating of debs (debian package); but the package compiled won't install and it always gave an error. :(

For the time being this is what worked for me:

[COLOR=Red]Uninstall all the drivers suggested by **jokey-gtk**, if you have tried installing it. And restart.[/COLOR]

Now install the drivers using this command
> sudo apt-get install fglrx-updates fglrx-amdcccle-updates

Initialise aticonfiguration
> sudo aticonfig --initial --input=/etc/X11/xorg.conf

Restart the system

Verify installation by using **fgl_glxgears **or **fglrxinfo **

Hope someone find it useful! ENJOY!!!

---

### Post by iowabeakster on 2012-05-09
> **rotten777 said:**
> Asus B43S - Doesn't work as of May 8 2012. Radeon 6400 series.

at least i am not the only one... i have tried and tried on my wife's new B43S.

---

### Post by maraschin on 2012-05-09
I've a HP Envy 17 3D and there is no way I can make the ATI drive to work with it! It is really frustrating! (Radeon HD 6850)

---

### Post by rotten777 on 2012-05-09
> **iowabeakster said:**
> at least i am not the only one... i have tried and tried on my wife's new B43S.

Yeah I'm not even sure who to complain to. The forums ignore the cries for help and Asus doesn't care... neither does ATI/AMD or Intel.

---

### Post by iowabeakster on 2012-05-10
my plan is to wait for some updates... try again in few weeks/months

then wait and try again... then....give up

---

### Post by delsus on 2012-05-11
> **rotten777 said:**
> Yeah I'm not even sure who to complain to. The forums ignore the cries for help and Asus doesn't care... neither does ATI/AMD or Intel.

No laptop vendors care, contacted HP about it on my laptop and all they would say is "we are unable to support software that was not preinstalled" even when I was only asking if there were plans to update the bios to allow us to completly disable the intel GPU before the laptop boots, which would enable me to use the fglrx driver.

What ever happened to good customer service?

---

### Post by polyrhythmic on 2012-05-11
This would be working great for Catalyst 12.4 on my Samsung Series 7 Chronos (NP700Z5B-S01UB) with Radeon HD 6490M (512MB) if I was running Xorg 1.11 ... but I like xorg-edgers PPA and Xorg 1.12 segfaults with fglrx.  The integrated graphics still work great for gnome-shell though.  Really digging this laptop with linux.

---

### Post by eloydark on 2012-05-11
Although this guide does show how to switch the two graphics cards (A6 6775G2 on an HP DV6) this does nothing for OpenCL.
OpenCL only recognises the onboard graphics of the A6 (Turks) with 6 processors.
Is there any advice on that matter?

---

### Post by rompelstompel on 2012-05-12
Why don't the fglrx-update packages work as well (jockey)? It isn't that much older than the current release (8.960 vs 8.961).

Is there a way to make the repository packages work in the same way as the bundle from AMD?

---

### Post by doktoreas on 2012-05-12
I tried the procedure but, once I reboot, I have got a black screen with you are running in low graphic mode :(

LSPCI:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

Thx
L.

---

### Post by jamesmuga on 2012-05-13
Thanks, it does work with my 

HP g4-1001tx, Intel HD 3000, AMD 6470m

---

### Post by hani270 on 2012-05-14
i have 512MB ATI Card -- Mobility Radeon HD **5430** Series (laptop: dell inpiron n4030)

what can i do ?

---

### Post by willis on 2012-05-14
This works on a sony vaio VPCSA:

lspci:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]

Have to be careful with updates though, and fglrx update breaks the whole system and I have to redo the steps.

---

### Post by Niccola on 2012-05-15
I've uploaded to YouTube a video for tearing test. This video was originally [posted in launchpad]("http://youtu.be/ceX18O9pvLs") and now it is available in YouTube by me.

If you can't see the white line moving smoothly in the screen, you have video tearing in your system.

OBS: It is Highly recommended the download of the video in High resolution. YouTube flash executing don't reproduces this test very well. So, use some tools to download it in High definition or click in the link above to download the original video file source.

[YouTube Video Tearing Test link]("http://youtu.be/ceX18O9pvLs")

I'm running I've tested the fglrx driver and opensource intel HD driver as described in this thread in a lot of linux systems and it works very well in all of them. The computer used for testing is a laptop HP Pavilion dv6-6192sf Core i7 + AMD Radeon HD6770M and tested in:

Ubuntu 11.10 / Ubuntu 12.04 LTS
Kubuntu 11.10 and Kubuntu 12.04 LTS
Lubuntu 11.10 and Lubuntu 11.10
also tested in Debian squeeze

---

### Post by shinylenin on 2012-05-16
Guys, you are seriously my last hope.

I already posted this in other forums, but no one could help me.

Here it is: I have a HP dv6-6180eg i5, an Intel iGPU and an ATI HD 6770M dGPU. I seriously followed every step from your tutorial but still I have this big problem: The dGPU is burning hot. I barely can't lie my left hand on the laptop. 

Only the iGPU is activated:

```
$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.2

```

Here is the output of sensors:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +99.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +52.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +53.0°C  (high = +86.0°C, crit = +100.0°C)

```

I already switched to "Dynamic" and not "Fixed" in BIOS but I still can't lower the temperatur. I mean, around 50° is not too bad for this kind of machine, but as I said, the dGPU is extremely hot.

When I activate the dGPU, the temperature is the following:

```

~$ aticonfig --adapter=0 --od-gettemperatur

Adapter 0 - AMD Radeon HD 6700M Series
            Sensor 0: Temperature - 54.00 C

```

I am seriously hopeless right now. I don't know what else I can do. I made a fresh install of Kubuntu (there is no Win anymore on my HDD) but the problem still remains.

I really hope that you guys can help me out! 

Thanks in advance!

---

### Post by tminhdn on 2012-05-16
> **debashishone said:**
> Hey,

It dint worked for me too...I am using generic-pae kernel Ubuntu 12.04 LTS on HP Pavilion dv-6 laptop. The command worked right up until creating of debs (debian package); but the package compiled won't install and it always gave an error. :(

For the time being this is what worked for me:

[COLOR=Red]Uninstall all the drivers suggested by **jokey-gtk**, if you have tried installing it. And restart.[/COLOR]

Now install the drivers using this command


Initialise aticonfiguration


Restart the system

Verify installation by using **fgl_glxgears **or **fglrxinfo **

Hope someone find it useful! ENJOY!!!

Thanks. This works for me. But whenever I switch to intergrated gpu, I can't load gnome-shell (desktop and icon on desktop show, but nothing more). How can I solve this? I tried the way in first post to enable direct rendering in intergrated gpu but it doesnt work. Or how can I revert to original driver when install ubuntu? I'm using Dell Inspiron N4110R, core-i3, intel hd 3000 + ati radeon 6630m

---

### Post by apochry on 2012-05-17
Hi guys,

very helpful thread!

I am using a Dell Vostro 3450 Laptop with Hybrid AMD 6630M/Intel HD300 graphics. The discrete card works fine, but I can't get Unity 3D with the integrated. 

Google doesn't help me a lot to figure out, if Unity 3D is supported by the Intel HD3000 integrated cards.
Here is what ```
/usr/lib/nux/unity_support_test -p

``` says:

```
penGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  1.4 (3.0 Mesa 8.0.2)

Not software rendered:    **[COLOR=DarkGreen]yes[/COLOR]**
Not blacklisted:          [COLOR=DarkGreen]**yes**[/COLOR]
GLX fbconfig:             [COLOR=DarkGreen]**yes**[/COLOR]
GLX texture from pixmap:  **[COLOR=DarkGreen]yes[/COLOR]**
GL npot or rect textures: [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex program:        [COLOR=DarkGreen]**yes**[/COLOR]
GL fragment program:      [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex buffer object:  **[COLOR=Red]no[/COLOR]**
GL framebuffer object:    [COLOR=DarkGreen]**yes**[/COLOR]
GL version is 1.4+:       [COLOR=DarkGreen]**yes**[/COLOR]

Unity 3D supported:       **[COLOR=Red]no[/COLOR]**


```Is there any way to have Unity3D with the integrated card?
You, guys, should know this for sure...

Thanks,
   Christo

---

### Post by tminhdn on 2012-05-17
> **apochry said:**
> Hi guys,

very helpful thread!

I am using a Dell Vostro 3450 Laptop with Hybrid AMD 6630M/Intel HD300 graphics. The discrete card works fine, but I can't get Unity 3D with the integrated. 

Google doesn't help me a lot to figure out, if Unity 3D is supported by the Intel HD3000 integrated cards.
Here is what ```
/usr/lib/nux/unity_support_test -p

``` says:

```
penGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  1.4 (3.0 Mesa 8.0.2)

Not software rendered:    **[COLOR=DarkGreen]yes[/COLOR]**
Not blacklisted:          [COLOR=DarkGreen]**yes**[/COLOR]
GLX fbconfig:             [COLOR=DarkGreen]**yes**[/COLOR]
GLX texture from pixmap:  **[COLOR=DarkGreen]yes[/COLOR]**
GL npot or rect textures: [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex program:        [COLOR=DarkGreen]**yes**[/COLOR]
GL fragment program:      [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex buffer object:  **[COLOR=Red]no[/COLOR]**
GL framebuffer object:    [COLOR=DarkGreen]**yes**[/COLOR]
GL version is 1.4+:       [COLOR=DarkGreen]**yes**[/COLOR]

Unity 3D supported:       **[COLOR=Red]no[/COLOR]**


```Is there any way to have Unity3D with the integrated card?
You, guys, should know this for sure...

Thanks,
   Christo

Intel HD3000 supports Unity 3D if you dont install Catalyst. After you install Catalyst, when switch to intergrated gpu (intel hd3000), it can't run Unity 3D anymore until you remove Catalyst and revert to original driver. That's what happened to me.

---

### Post by Alexislavie on 2012-05-18
> **apochry said:**
> Hi guys,

very helpful thread!

I am using a Dell Vostro 3450 Laptop with Hybrid AMD 6630M/Intel HD300 graphics. The discrete card works fine, but I can't get Unity 3D with the integrated. 

Google doesn't help me a lot to figure out, if Unity 3D is supported by the Intel HD3000 integrated cards.
Here is what ```
/usr/lib/nux/unity_support_test -p

``` says:

```
penGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  1.4 (3.0 Mesa 8.0.2)

Not software rendered:    **[COLOR=DarkGreen]yes[/COLOR]**
Not blacklisted:          [COLOR=DarkGreen]**yes**[/COLOR]
GLX fbconfig:             [COLOR=DarkGreen]**yes**[/COLOR]
GLX texture from pixmap:  **[COLOR=DarkGreen]yes[/COLOR]**
GL npot or rect textures: [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex program:        [COLOR=DarkGreen]**yes**[/COLOR]
GL fragment program:      [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex buffer object:  **[COLOR=Red]no[/COLOR]**
GL framebuffer object:    [COLOR=DarkGreen]**yes**[/COLOR]
GL version is 1.4+:       [COLOR=DarkGreen]**yes**[/COLOR]

Unity 3D supported:       **[COLOR=Red]no[/COLOR]**


```Is there any way to have Unity3D with the integrated card?
You, guys, should know this for sure...

Thanks,
   Christo

Check if you do have direct rendering enabled.

---

### Post by aeronutt on 2012-05-18
> **apochry said:**
> Hi guys,

very helpful thread!

I am using a Dell Vostro 3450 Laptop with Hybrid AMD 6630M/Intel HD300 graphics. The discrete card works fine, but I can't get Unity 3D with the integrated. 

Google doesn't help me a lot to figure out, if Unity 3D is supported by the Intel HD3000 integrated cards.
Here is what ```
/usr/lib/nux/unity_support_test -p

``` says:

```
penGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  1.4 (3.0 Mesa 8.0.2)

Not software rendered:    **[COLOR=DarkGreen]yes[/COLOR]**
Not blacklisted:          [COLOR=DarkGreen]**yes**[/COLOR]
GLX fbconfig:             [COLOR=DarkGreen]**yes**[/COLOR]
GLX texture from pixmap:  **[COLOR=DarkGreen]yes[/COLOR]**
GL npot or rect textures: [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex program:        [COLOR=DarkGreen]**yes**[/COLOR]
GL fragment program:      [COLOR=DarkGreen]**yes**[/COLOR]
GL vertex buffer object:  **[COLOR=Red]no[/COLOR]**
GL framebuffer object:    [COLOR=DarkGreen]**yes**[/COLOR]
GL version is 1.4+:       [COLOR=DarkGreen]**yes**[/COLOR]

Unity 3D supported:       **[COLOR=Red]no[/COLOR]**


```Is there any way to have Unity3D with the integrated card?
You, guys, should know this for sure...

Thanks,
   Christo

Did you do step #2 as outlined in the first post?  Unity 3D didn't work for me until I did step #2.

---

### Post by apochry on 2012-05-18
> **aeronutt said:**
> Did you do step #2 as outlined in the first post?  Unity 3D didn't work for me until I did step #2.

Yes, I did exactly as described.

My */etc/X11/Xsession.d/10fglrx* says:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```

When try I log in to Unity 3D using the integrated video, I get in, but I don't have Launcher and Panel on my desktop and the  start-up applications start without window decorations.  I can't do anything else but press ctrl+alt+del and log out. 

Thanks!

---

### Post by Aidamir on 2012-05-21
Hi, all. Thank's! It is very helpful thread. But I still cannot run unity-3d on **HP ProBook 4350s**  intel HD3000/Radeon 6400M   intergated card it show's likely the same as described in many  posts here. No unity appear and all windows are headless (due compiz fail to start). There is only these lines I found in the /var/log/syslog.log  
May 20 23:30:52 yellow gnome-session[2090]: WARNING: App 'compiz.desktop' respawning too quickly
May 20 23:30:52 yellow gnome-session[2090]: CRITICAL: We failed, but the fail whale is dead. Sorry....
However I notice - when I tried to start compiz manually, it started successfully from console and windows start's looking normal (but still missing unity panel).  

I also want to share my experience of installing latest AMD catalyst driver's. It does not build kernel driver without patch. 
I found also this post complain to the same problem 
[http://ubuntuforums.org/showpost.php?p=11885405&postcount=192]("http://ubuntuforums.org/showpost.php?p=11885405&postcount=192")

When installing catalyst Dirver I got these error:

Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
[COLOR="Red"]**Error! Bad return status for module build on kernel: 3.2.0-24-generic-pae (i686)**[/COLOR]
Consult /var/lib/dkms/fglrx/8.961/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...

/var/lib/dkms/fglrx/8.961/build/make.log - says the following:

 MD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-24-generic-pae/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/linux-headers-3.2.0-24-generic-pae'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; «KCL_fpu_begin»:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:5812:28: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: «TS_USEDFPU» undeclared (first use in this fun
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:5812:28: &#1079;&#1072;&#1084;&#1077;&#1095;&#1072;&#1085;&#1080;&#1077;: each undeclared identifier is reported only
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/linux-headers-3.2.0-24-generic-pae'
make: *** [kmod_build] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

I found fix for that on these thread of AMD site forum:[http://ati.cchtml.com/show_bug.cgi?id=444]("http://ati.cchtml.com/show_bug.cgi?id=444")

These patch I copied from that site and attached here. It does only simple thing you can do using any text editor. 
So to replace string "if (cur_task->status & TS_USEDFPU)" with 
"if (__thread_has_fpu(cur_task))" in  /usr/src/fglrx-8.961/firegl_public.c file after unpacking fglrx package.

**How to fix:**

The following guide assumes that you are running all commands from the directory containing fglrx_8.961-0ubuntu1_i386.deb package (built by --buildpkg option of AMD catalyst package) and patch file ts_usedfpu.txt attached here.


1) Firstly you have to build packages using the Alexislavie steps, or if you have already built and installed them no reinstallation requered the procedure should replace fglrx package.
2) Then we need unpack deb package to let us apply patches before running kernel module build:
**  sudo dpkg --unpack ./fglrx_8.961-0ubuntu1_i386.deb**
[INDENT]Output expected to be something like:
(Reading database ... 194533 files and directories currently installed.)
Preparing to replace fglrx 2:8.961-0ubuntu1 (using fglrx_8.961-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx ...
Processing triggers for ureadahead ...[/INDENT]

3) Apply patch:
 ** sudo patch -d /usr/src/fglrx-8.961 -p0 < ts_usedfpu.txt** 
Output expected to be something like:
[INDENT]patching file firegl_public.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 5809 with fuzz 1 (offset 10 lines).
[/INDENT]

Or you can simply open /usr/src/fglrx-8.961/firegl_public.c, go to 5812 line and replace the string "if (cur_task->status & TS_USEDFPU)" with "if (__thread_has_fpu(cur_task))" 

4) Build DMKS and finish package istallation 
  **sudo dpkg --configure fglrx** 
[INDENT]At the end of output you should see something like:
Loading new fglrx-8.961 DKMS files...
Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
[/INDENT] 

Now you are ready to proceed with configure if neccesary.

---

### Post by jjiggens on 2012-05-22
Works fine on an HP Elietebook 8560p [FONT=Arial][SIZE=2]Intel: HD 3000, AMD 6470m did not test display port or vga. i will tomorrow. 
[/SIZE][/FONT]

---

### Post by Aidamir on 2012-05-22
Hi, has anybody solved missing launcher and panel with integrated adatper running? 
The only information I have is 2 lines from syslog:

May 20 23:30:52 yellow gnome-session[2090]: WARNING: App 'compiz.desktop' respawning too quickly
May 20 23:30:52 yellow gnome-session[2090]: CRITICAL: We failed, but the fail whale is dead. Sorry....

I did try to run session by startx script. Decorator did start. Then I did run unity from console. It start to show launcher and panel but with horrible blinking and glitches. May be somebody can comment that?

unity log: 

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600004

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:3709): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
ERROR 2012-05-21 17:15:24 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x100009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.

WARN  2012-05-21 17:15:25 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-21 17:15:25 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
....................................several lines of the same content.......................
ERROR 2012-05-21 17:15:25 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-21 17:15:25 unity.launcher Launcher.cpp:3012 Object registration failed. Won't get dynamic launcher addition.
Initializing staticswitcher options...done
Setting Update "launcher_hide_mode"
Setting Update "icon_size"
Setting Update "edge_responsiveness"
Setting Update "launcher_capture_mouse"
Setting Update "main_menu_key"
Setting Update "run_key"

---

### Post by mimmozzo on 2012-05-22
All works for me except for Unity 3D with Intel (I am forced to use discrete gpu), even after applying the fix in step 2.
Notebook: HP Pavilion dv6 6169sl

```
cat /etc/X11/Xsession.d/10fglrx
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```

**EDIT: **I took a deeper look at the script and, since "uname -m" gives "i686" as output (I have 32 bit Ubuntu), none of the instructions above are executed but these two:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
export LIBGL_DRIVERS_PATH
```
Guess we need something like:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/dri
export LIBGL_DRIVERS_PATH
```
I'll try it and let you know :)

**EDIT2: **No luck, even tried creating symlink /usr/lib32 to /usr/lib (the aticonfig util wants the lib32 directory).

**EDIT3: **This is Xorg.0.log when Unity does not start correctly after selecting igpu:
```

[    17.679] (II) fglrx(0): pEnt->device->identifier=0xb8828108
[    17.680] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.680] (II) intel(1): pEnt->device->identifier=**(nil)**
[    17.680] (EE) Screen 1 deleted because of no matching config section.
[    17.680] (II) UnloadModule: "intel"
[    17.680] (II) Unloading intel

```

---

### Post by jasonwyz98 on 2012-05-22
> **mimmozzo said:**
> All works for me except for Unity 3D with Intel (I am forced to use discrete gpu), even after applying the fix in step 2.
Notebook: HP Pavilion dv6 6169sl

```
cat /etc/X11/Xsession.d/10fglrx
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```

**EDIT: **I took a deeper look at the script and, since "uname -m" gives "i686" as output (I have 32 bit Ubuntu), none of the instructions above are executed but these two:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
export LIBGL_DRIVERS_PATH
```
Guess we need something like:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/dri
export LIBGL_DRIVERS_PATH
```
I'll try it and let you know :)

**EDIT2: **No luck, even tried creating symlink /usr/lib32 to /usr/lib (the aticonfig util wants the lib32 directory).

**EDIT3: **This is Xorg.0.log when Unity does not start correctly after selecting igpu:
```

[    17.679] (II) fglrx(0): pEnt->device->identifier=0xb8828108
[    17.680] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.680] (II) intel(1): pEnt->device->identifier=**(nil)**
[    17.680] (EE) Screen 1 deleted because of no matching config section.
[    17.680] (II) UnloadModule: "intel"
[    17.680] (II) Unloading intel

```

1. Remove ":/usr/lib/dri" from 4th line

2. Append this ":/usr/lib32/dri" ( 32bit systems ) without quotes to: LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri

so the first line should be: LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib32/dri

Let us know if works :)

---

### Post by rotten777 on 2012-05-23
> **rotten777 said:**
> Asus B43S - Doesn't work as of May 8 2012. Radeon 6400 series.

> **iowabeakster said:**
> at least i am not the only one... i have tried and tried on my wife's new B43S.



I got 3D to work. Not with ATI card I don't believe though.


> **rotten777 said:**
> To anyone that runs across this, I've ended up getting 3D to work. I don't believe it is the ATI card doing it though. If you just want your B43S-X51 to work in Unity 3D, do this:

```
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```

---

### Post by mimmozzo on 2012-05-23
It didn't work sorry.

---

### Post by jjiggens on 2012-05-23
hmmm scratch my previous post as working. 

although the HP elietebook can switch between intel and AMD GFX in windows it does not seem to work on ubuntu 12.04, even though aticonfig says it has switched. getting the gfx info on reboot shows its still using the amd gpu.

not sure what else i can try to get it to work.

---

### Post by dpacmittal on 2012-05-24
Works awesome on HP DV6-6121tx. Has also reduced power consumption from ~30W to ~13-15W. Also, overheating has reduced a lot.

Thanks a lot for the tutorial.

---

### Post by p3rry on 2012-05-24
Hi,

I've tried the solution for a [FONT=Arial][SIZE=2]DELL Vostro 3550, with an AMD 6630m card and Ubuntu 12.04 LTS. I tried it on a fresh install (keeping my old home directory anyway).

I experience some issue with X and I think it's related to the driver. 
When I try for ex. to move the cursor by nonstop arrow pressing it stops after a while, while the display blinks slightly. 

It turned out that each time it happens on Xorg.0.log I get
[/SIZE][/FONT]```
 873.634] (II) fglrx(0): EDID vendor "SEC", prod id 21569
[   873.634] (II) fglrx(0): Printing DDC gathered Modelines:
[   873.635] (II) fglrx(0): Modeline "1366x768"x0.0   76.69  1366 1414 1446 1618  768 770 775 790 +hsync -vsync (47.4 kHz)
[   873.635] (II) fglrx(0): Modeline "1366x768"x0.0   48.22  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (31.6 kHz)
```

It is happening also with unity2D...

---

### Post by Joe76000 on 2012-05-25
Hello All,

Ref. my previous post [# 193]("http://ubuntuforums.org/showpost.php?p=11885742&postcount=193") regarding ACCC v.12.3, I have moved successfully to v.12.4 accordingly to Alexis post # 1 update dated one week ago on my HP DV7-6070ef under Ubuntu 12.04 LTS 64-bits.
I just made sure I removed all ACCC v.12.3 installed components before updating to v.12.4.
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
```And then rebooted.
Then I continued the installation of v.12.4 from "[FONT=Arial][SIZE=2]We can now download the AMD catalyst 12.4 driver :[/SIZE][/FONT]" and when finished I rebooted again.
Test of the installed graphic cards:
```
joehp@ubuntu:~$ lspci | grep "VGA"
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
```Test of the activated graphic card:
```
joehp@ubuntu:~$ aticonfig --pxl # List current activated GPU
PowerXpress: Discrete GPU is active (High-Performance mode).
```Test of direct rendering:
```
joehp@ubuntu:~$ glxinfo | egrep render
direct rendering: Yes OpenGL renderer string: AMD Radeon HD 6400M Series
     GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render,
```Test of the used OpenGL library:
```
joehp@ubuntu:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11631 Compatibility Profile Context
```The choice between AMD dGPU and INTEL iGPU is simply done into ACCC in Admin mode then rebooting either my session or notebook for finalizing the switch of the graphic card. :guitar:

Many thanks again to Alexis. =D> 
Cheers. JOE from France ):P

---

### Post by Cristobal92 on 2012-05-28
HP G6-1122ss Intel HD 3000, AMD 6470m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working

---

### Post by NirvashType0 on 2012-05-30
Well.....i had been trying to make this work on my inspiron N5110 (pls tell me everything u can, im new in the use of linux distros in this case ubuntu 12.04) well the think is..................i already be reading this:
-------------------------------------------------------------------------------------------------
***Check installation***

 *This is important!* Sometimes the driver installer will NOT move all the executables into  the correct folders. Copy the switchlibGL and switchlibglx into the  /usr/lib64/fglrx folder. You may have to check in /usr/lib32/ or  /usr/lib/, and move the files accordingly, depending on if you are on a  x64 or x86 system. 
 sudo cp /usr/lib64/switchlib* /usr/lib64/fglrx/  If you do not do this, and the executables are not already in  /usr/lib64/fglrx/ or /usr/lib32/fglrx, depending on your distro version,  the X server will likely NOT START when you reboot. 
--------------------------------------------------------------------------------------------------
And well efectivly thats both files arent in that location, so can someone give me the twice files pls??? i only need put the both files in that folder right?????

---

### Post by NirvashType0 on 2012-05-31
> **NirvashType0 said:**
> Well.....i had been trying to make this work on my inspiron N5110 (pls tell me everything u can, im new in the use of linux distros in this case ubuntu 12.04) well the think is..................i already be reading this:
-------------------------------------------------------------------------------------------------
***Check installation***

 *This is important!* Sometimes the driver installer will NOT move all the executables into  the correct folders. Copy the switchlibGL and switchlibglx into the  /usr/lib64/fglrx folder. You may have to check in /usr/lib32/ or  /usr/lib/, and move the files accordingly, depending on if you are on a  x64 or x86 system. 
 sudo cp /usr/lib64/switchlib* /usr/lib64/fglrx/  If you do not do this, and the executables are not already in  /usr/lib64/fglrx/ or /usr/lib32/fglrx, depending on your distro version,  the X server will likely NOT START when you reboot. 
--------------------------------------------------------------------------------------------------
And well efectivly thats both files arent in that location, so can someone give me the twice files pls??? i only need put the both files in that folder right?????

well.............nobody gave me an answer but........i make it work on my INSPIRON N5110, i tryed many times on the 32 bits system but it never work, so i tryed only one time in the 64 bits sytem and like magic it works in the first try, so thx for the tutorial, if some of u are trying on the INSPIRON 5110(15R) I STRONGLY RECOMMEND YOU!!!! TRY WITH THE 64 BITS SYSTEM!!!!!! so i guess you can add this model to the compatibility list but of course with 64 bits system, Thanks again!!!!

---

### Post by freon777 on 2012-06-02
Thanks!
Work for me.

Notebook and system details:

Model:
HP ProBook 4330s (A6D83EA)

```
 cat /etc/issue
Ubuntu 10.04.4 LTS \n \l

```

```
uname -a
Linux comp 2.6.38-15-generic-pae #59~lucid1-Ubuntu SMP Mon Apr 30 20:06:20 UTC 2012 i686 GNU/Linux

```

```
lspci  | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6760

```
but, specification and Catalyst show 6400 series adapter
and glxinfo doesn't show renderer:

```
 glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

Also, I updated Intel driver from this PPA:
[B]ppa:glasen/intel-driver

[/B]UPDATE:
glxinfo from NOT root user show:
```
glxinfo  | grep rend
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: AMD Radeon HD 6400M Series

```

---

### Post by OGOOGO on 2012-06-03
Lenovo e520 (1143R24),Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working

Ubuntu 10.04 32-bit

I follow instruction except:
- dh-modaliases isn't in ubuntu 10.04 repo, found .deb
- I can't install ati drivers from created packages (install it from .run)
- direct rendering work without file "/etc/X11/Xsession.d/10fglrx" 

Thanks for guide!

---

### Post by ysNoi on 2012-06-03
Has anyone here tried installing this on HP G4-1335TX with Precise 64Bits?

It has AMD 7450M (according to specs), other info like HD xxxx is I don't know. (How to get it?)

Any advice before I start the install?

TYIA...

---

### Post by clement.analogue on 2012-06-04
> **ysNoi said:**
> It has AMD 7450M (according to specs), other info like HD xxxx is I don't know. (How to get it?)

lspci  | grep VGA

---

### Post by delsus on 2012-06-04
Anyone managed to get it working with ATI Mobility Radeon 5000 yet, specifically 5400 series?
 
Also I noticed on the ATI website there is a new beta driver released 12.6 and it says it allows support for multiple GPUs with some 7000 series cards in case anyone wanted to look.

Seems like this is the relevent part of the changelog:

> [B]Dual Graphics enhancements &#8211; new application profiles
[/B] 
[LIST]
[*]Supported Dual Graphics configurations:
**AMD Accelerated Processors for Desktop PCs**
[LIST]
[*]AMD Radeon HD 7660D (A10-5700)
[*]AMD Radeon HD 7560D (A8-5500
[/LIST]
**Notebooks with AMD Accelerated Processors **
[LIST]
[*]AMD Radeon HD 7660D (A10-4600)
[*]AMD Radeon HD 7640G (A8-4500M)
[*]AMD Radeon HD 7520G (A6-4400M)
[/LIST]
[/LIST]


[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx)

---

### Post by clement.analogue on 2012-06-04
> **delsus said:**
> Anyone managed to get it working with ATI Mobility Radeon 5000 yet, specifically 5400 series?

I've got a ATI Mobility Radeon HD 5400 but I still don't find any solution :(

---

### Post by delsus on 2012-06-04
> **clement.analogue said:**
> I've got a ATI Mobility Radeon HD 5400 but I still don't find any solution :(

I want to try Final Fantasy XIV out through wine, but I need the catalyst drivers working to even run the game :(

---

### Post by ysNoi on 2012-06-04
> **clement.analogue said:**
> lspci  | grep VGA

Thanks Bro...

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
```I wonder I have HD 7450M but it appears HD 6400M on lspci  | grep VGA test... :(

Edit : Any idea..? I want also to test activate my Radeon HD 7450M...

TYIA...

---

### Post by RayVad on 2012-06-05
Confirmed working on my HP Pavillion G7-1270sd:

HP Pavilion G7-1270sd, Intel HD 3000, AMD 6470M, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] (rev ff)
04:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

Ubuntu Precise 12.04 LTS LiveCD had to start with boot options nomodeset and acpi=off.
After installation i had to boot only with the nomodeset. 
After following your instructions, all worked without these boot options.
(Ubuntu Mint 13 Maya is working out of the box, no need to add these boot options at all!)

(This step below was also not needed on Ubuntu Mint 13 Maya, its working out of the box)
Screen was dark though, but seemed brightness after every reboot.
So i added this line to /etc/rc.local before exit 0:

echo 8 > /sys/class/backlight/acpi_video0/brightness
exit 0

All is working now, thanks!

---

### Post by Niccola on 2012-06-05
Somebody having problems surfing with browser and suddenly it freezes (only browser)?

When I using lot flash websites it freezes a lot just using Intel HD iGP!!!

---

### Post by drimchik on 2012-06-07
I managed to run ATI graphics on my Sony VPC SA3 yesterday
Note: it works if slider is set to STAMINA
Thanks a lot for you help
**SONY Vaio VPC-SA3S9R, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working**

---

### Post by ubik89 on 2012-06-07
Is there a possibility to turn tear-free desktop on?

I can't find it in the Catalyst Control Center.

On others non-switchable graphic cards, there is an option to do this in Catalyst Control Center.

---

### Post by N0oki3 on 2012-06-07
**HP Pavilion g6-1190sm** Intel HD 3000, AMD 6470m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: **working**/**not working**

**igpu** works while **dgpu** doesn't

---

### Post by arazour on 2012-06-07
With Vostro 3350 and Radeon HD 6400M Series my problem is that when I enable integrated gpu I get these warnings:

```

sudo aticonfig --px-igpu
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.

PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!

```

and when I restart my laptop or X gnome will start in fallback mode or unity in 2D. 
anyone with similar experience here?

---

### Post by N0oki3 on 2012-06-08
Hello there. When  I do
> sudo dpkg -i fglrx*.deb

I get this 
edit: i have fixed this error by editing etc/kernel/postinst.d/zz-update-grub and commenting 
>  */postinst.d/*:|*/postinst.d/*:configure|*/postrm.d/*:|*/postrm.d/*:remove)
#       exec update-grub
        ;;
> update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.



and this error is still that I get. As I have currently installed (quite gave up after formating multiple times) windows 7 and trying to fix this driver problems via persistent usb ubuntu
> cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
I got this error with installed on laptop or USB. 

When ever I want to open amd catalyst center it pops error that I don't have installed drivers / not detecting graphic card. 

With >  sudo aticonfig --px-dgpu 
It does say  Activate discrete GPU (High-Performance mode), must re-start X to take effect

But under system it always shows that I am running sandy bridges graphic card. So after rebooting i get error that i am running in low graphic mode and i have to delete xorg.conf so i can get back to desktop. Also i always need to run in nomodeset otherwise I have black screen. So only thing I wonder still (but I belive that it wouldn't change anything) to install drivers in Ubuntu(3D) instead of Ubuntu 2D

My gpu is : Radeon HD 6470m

---

### Post by Niccola on 2012-06-08
Iam with a little impression that Ubuntu 11.10 works better than 12.04!

Mine 12.04 always show a error log message to report and it is freezing sometimes...

> **ubik89 said:**
> Is there a possibility to turn tear-free desktop on?
  
  I can't find it in the Catalyst Control Center.
  
  On others non-switchable graphic cards, there is an option to do this in Catalyst Control Center.
  
  There are no Tear free option in Hybrid Graphics ATI/AMD with intel igp as framebuffer due to igp display managing.

> **N0oki3 said:**
> **HP Pavilion g6-1190sm** Intel HD 3000, AMD 6470m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: **working**/**not working**

**igpu** works while **dgpu** doesn't

Have you followed the post #1 correctly? Can you repeat the steps? What ubuntu version are you using?

---

### Post by N0oki3 on 2012-06-08
Hello there Niccola. I have tried to install it on Ubuntu 12.04 precise pangolin (32 bit) and also i have tried to install on ubuntu 11.10 oneiric. As I couldn't fix unity 3D I have back installed windows 7, and[B] atm I have ubuntu on persistent USB so i can install stuff on usb as it is primary HDD.
[/B] 
So how I did it. First I had to change grub to nomodeset so I could get into desktop otherwise i have black screen.
Than I have installed > [FONT=Arial][SIZE=2]sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1[/SIZE][/FONT]Afterward I have downloaded drivers > [FONT=Arial][SIZE=2]cd ~/; mkdir catalyst12.4; cd catalyst12.4/ wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run) chmod +x amd-driver-installer-12-4-x86.x86_64.run[/SIZE][/FONT]and build them.
> 
[FONT=Arial][SIZE=2]sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
[/SIZE][/FONT]=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/precise
Package /home/ubuntu/Downloads/fglrx_8.961-0ubuntu1_i386.deb has been successfully generated
Package /home/ubuntu/Downloads/fglrx-dev_8.961-0ubuntu1_i386.deb has been successfully generated
Package /home/ubuntu/Downloads/fglrx-amdcccle_8.961-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.L2e2JS
[/QUOTE]

than i do > sudo dpkg -i fglrx*.debAnd i get this:
> 
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 135500 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.961-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.961-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from fglrx_8.961-0ubuntu1_i386.deb) ...
Setting up fglrx (2:8.961-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
[B]update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.[/B]
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.961 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture i686
Building initial module for 3.0.0-12-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.961-0ubuntu1) ...
Setting up fglrx-dev (2:8.961-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
[B]cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab[/B]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
than i do sudo aticonfig --initial -f

> 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
I switch to dgpu 

> PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!
afterward I edit [FONT=Arial][SIZE=2]etc/X11/Xsession.d/10fglrx
to 
[/SIZE][/FONT]> 
[FONT=Arial][SIZE=2]LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri[/SIZE][/FONT]I save file, reboot system, set it to nomodeset(otherwise black screen) and it says that im running in low graphic mode

my xorg config 
> 
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
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
my lspci 
> 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

also my pc spec is:
intel i3,
igpu: intel sandy bridge
dgpu: radeon hd 6470m

Bios is locked (cannot switch or set default graphic there), in windows 7 it works well

**edit:** i have also tried with patch 
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
./amd-driver-installer-12-4-x86.x86_64.run --extract driver
cd driver/common/lib/modules/fglrx/build_mod/
wget -O fglrx.patch http://ubuntuone.com/5gNgEmVfzs3ytD5QZ2YGCi
patch -p1 < fglrx.patch
cd ~/catalyst12.4/driver/
./ati-installer.sh 8.961 --buildpkg Ubuntu/precise
cd ../
```

---

### Post by mrhat1988 on 2012-06-09
Does not work for me (hp dv6 amd 6700 m) either, unfortunately. (I followed the instructions on p.1 step-by-step, u know your way around these things if you've down this like for the 99th time :) )

One problem, that i encountered with this method (AND other methods for fglrx in the past) is the following:

If you do the ole' > sudo aticonfig --initial -f
you get > Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0 BUT BUT BUT if you open this file /etc/X11/xorg.conf with gedit it STILL is completely EMPTY and thus, i suppose, NOT configured, in contrary to what you see on terminal. And thus, most likely, your GUI will crash after reboot.

I looked around if there are some write-rights or anything in the way but could not find any - I'm not too hot at those things.

Maybe this helps a little.

Anyway, this seems not so much be an issue of the driver itself as of bad package dependencies and configuration processes as it seems to actually work for some lucky ones.

---

### Post by N0oki3 on 2012-06-09
> **mrhat1988 said:**
> BUT BUT BUT if you open this file /etc/X11/xorg.conf with gedit it STILL is completely EMPTY and thus, i suppose, NOT configured, in contrary to what you see on terminal.

hmm...In my case:
cat etc/X11/xorg.conf and gksu gedit etc/x11/xorg.conf is exactly same

---

### Post by Niccola on 2012-06-09
You guys need to do the steps easily and without speed. Try to  understand whats happening in the installation. You should put the fglrx  driver working FIRST and after you try to solve the Integrated Graphic  Direct Rendering Problem.

> **mrhat1988 said:**
> Does not work for me (hp dv6 amd 6700 m)  either, unfortunately. (I followed the instructions on p.1 step-by-step,  u know your way around these things if you've down this like for the  99th time :smile: )

One problem, that i encountered with this method (AND other methods for fglrx in the past) is the following:

If you do the ole' 
you get  BUT BUT BUT if you open this file /etc/X11/xorg.conf with gedit  it STILL is completely EMPTY and thus, i suppose, NOT configured, in  contrary to what you see on terminal. And thus, most likely, your GUI  will crash after reboot.

I looked around if there are some write-rights or anything in the way but could not find any - I'm not too hot at those things.

Maybe this helps a little.

Anyway, this seems not so much be an issue of the driver itself as of  bad package dependencies and configuration processes as it seems to  actually work for some lucky ones.

By default, Xorg.conf is an empty file. But after fglrx installation, it  get filled by ```
sudo aticonfig --initial -f
``` command.
 
  I suggest you to reboot the computer AFTER sudo aticonfig --initial -f  command and THEN, you modify the 10fglrx file, THEN reboot again!

> **N0oki3 said:**
> hmm...In my case:
cat etc/X11/xorg.conf and gksu gedit etc/x11/xorg.conf is exactly same


   Hey N0oki3,
   look, you don't need to worry about WARNINGS. At least you're the  software developer and want to do everything out of Warnings. Usually,  anyone care with Warnings, but ERRORS. So, don't worry about this  Warnings.
   
   I think you SHOULD REBOOT the computer after the ```
sudo aticonfig --initial -f
``` command.
   
   And AFTER this reboot, you will be able to succeed with 10fglrx file modification, try it!
   
And make a LAST reboot BEFORE using the command:[FONT=Arial][SIZE=2]sudo aticonfig --px-dgpu[/SIZE][/FONT]

   And why are you using nomodeset? Try to remove this and just add it at kernel parameters after succeed with driver installation.

---

### Post by N0oki3 on 2012-06-09
> **Niccola said:**
> And why are you using nomodeset?
I am using nomodeset becouse otherwise I have black screen all the time. 

> **Niccola said:**
> Try to remove this and just add it at kernel parameters after succeed with driver installation.

What do you mean ?

---

### Post by Niccola on 2012-06-09
> **N0oki3 said:**
> I am using nomodeset becouse otherwise I have black screen all the time. 


What do you mean ?

Im wonder to you, remove Xorg.conf file (yes! Delete it and restart your system) after, remove fglrx driver and remove nomodeset parameter. Reboot your system and reinstall the driver again (as post 1) and after sudo aticonfig --initial -f command, restart the system and then you modify the 10fglrx file, reboot the system and THEN change to the GPU that you want to use. Last thing is add nomodeset as parameter IF NEEDED!!

Blackscreen alltime? Ohh Man, your BIOS is updated? Check it out and update it!

Another thing is, how is Hybrid mode Setting in your BIOS Setup?

Cheers

---

### Post by N0oki3 on 2012-06-09
> **Niccola said:**
> Blackscreen alltime? Ohh Man, your BIOS is updated?
BIOS is updated from the same day I bought this laptop. It is still version F.63
edit: Funny thing is, before I have updated BIOS I didn't had to use nomodeset but instead everytime I have booted PC (from linux(live cd) not windows) I got errror that system went into hibernate becouse of overheating. Which is actually a lie

> **Niccola said:**
> Another thing is, how is Hybrid mode Setting in your BIOS Setup?
Like I've mentioned in post above 
Only thing I can change in BIOS is clock and boot order LOL! I am really dissapointed with HP and thinking to throw it through balcony

---

### Post by Niccola on 2012-06-09
> **N0oki3 said:**
> BIOS is updated from the same day I bought this laptop. It is still version F.63
edit: Funny thing is, before I have updated BIOS I didn't had to use nomodeset but instead everytime I have booted PC (from linux(live cd) not windows) I got errror that system went into hibernate becouse of overheating. Which is actually a lie


Like I've mentioned in post above 
Only thing I can change in BIOS is clock and boot order LOL! I am really disappointed with HP and thinking to throw it through balcony

I'll tell you something,
Was really hard to install Ubuntu 12.04 LTS in my HP dv6-6192sf. I had to put a lot of kernel parameters but still having hangs, freezing and a lot lot of reports. And this wasn't happening in 11.10, such was running wonderfully in my PC.

I recommend you to try 11.10 instead 12.04 and check if everything run fine (better than 12.04) and check again if there are another BIOS update and update it!

What's your HP model?

It isn't HP fault, but the Hybrid technology is quite "new" in the market and the software are fitting on it just now. Calm down, take it easy that everything will gonna be ok (I'm like relationship advisor, but I am not! rsrsrsrs).

Try to reinstall system (using 11.10 to test then 12.04) then install fglrx, after sudo aticonfig --initial -f reboot the system

then change the 10fglrx file add the driver path and then reboot again!

Then Change to the desired GPU and reboot last time!

Have fun!

(What I want you to know is how important is all of this reboots)

---

### Post by N0oki3 on 2012-06-09
> **Niccola said:**
> 
I recommend you to try 11.10 instead

I'm downloading it now, will reply later how it went
> **Niccola said:**
> 
and check again if there are another BIOS update and update it!

I have back in the morning and there is no new update

> **"Niccola said:**
> 
What's your HP model?

It is HP pavilion g6 1190sm


> **"Niccola said:**
> It isn't HP fault
Well they could give us at least more freedom in BIOS
> **"Niccola said:**
> but the Hybrid technology is quite "new" in the market and the software are fitting on it just now.

Yeah, I hope that it will work properly and without any problems on linux.

> **Niccola said:**
>  I had to put a lot of kernel parameters
which ? Perhaps they might help me

**UPDATE: using ubuntu 11.10 oneiric: **Installing drivers -> rebooting PC 
```
 aticonfig --initial -f 
```
reboot 
And at reboot it fails :
> 
[ 32.456929] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 65325

[ 32.461106] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 65322

[ 32.461137] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 65325

[ 32.497119] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 65322

[ 32.499075] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 260769

[ 32.510801] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 260769

[ 35.512346] init: lightdm main process (5716) terminated with status 1



Looks like untill HP won't update BIOS with option to switch graphics or there will be fix for us from developers. I guess we cannot run unity 3D

---

### Post by miatawnt2b on 2012-06-10
Has anyone beenhaving issues with suspend?  I am running a samsung series 7, and 12.6 beta fglrx. If I close the lid on the laptop, the backlight stays on (its either the backlight or keyboard light) and the system will get very hot and drain the battery in about 30 min.

opening the lid will not bring the laptop back, it's simply frozen and I need to hold down the power button.

-J

---

### Post by Niccola on 2012-06-11
> **N0oki3 said:**
> I'm downloading it now, will reply later how it went
...
run unity 3D

Are you running with some kernel parameters, another which isn't nomodeset? Did you tried some acpi parameters? If not, google it and look for acpi (nolapic, acpi=off, etc...) parameters.
I am using this parameters:
```
GRUB_CMDLINE_LINUX_DEFAULT="pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 acpi_osi=Linux acpi_backlight=vendor quiet splash"
```

The 3 first are to overheating problem and power-saving parameters. The last one is to work the backlight screen buttons.

It is quite weird this error is happening with you. I hope you succeed with 11.10 installation.

Try to send an email/message or report to HP asking to a new BIOS release to solve linux kernel problems. I did it a long time ago and they send me a new BIOS release in 2 weeks. Report the problem easily and nice-speaking.

Otherwise, Have you tried to google this errors? Everything works fine without the fglrx driver? I mean, with a fresh ubuntu installation (out-of-box)?

Wait a minute...
this errors that you show us "EXT2-fs (loop1): error" stand for persistent file system problem (damaged, corrupted, etc...) Are running in an USB flash driver, right? How much space there is in this flash drive? Why don't you try to INSTALL it on your HD? Dual Boot or External HDD?? Try it.


> **miatawnt2b said:**
> Has anyone beenhaving issues with suspend?  I am running a samsung series 7, and 12.6 beta fglrx. If I close the lid on the laptop, the backlight stays on (its either the backlight or keyboard light) and the system will get very hot and drain the battery in about 30 min.

opening the lid will not bring the laptop back, it's simply frozen and I need to hold down the power button.

-J

First, make some search in google/ubuntuforums and you'll find solutions. This thread is just for Intel/AMD Hybrid Graphics

---

### Post by miatawnt2b on 2012-06-11
My machine is a hybrid graphics model which is why I posted here. The google searching I've done only returns results that deal with resuming from suspend. My laptop never gets that far. If you've found something different, please let me know.
-J


> **Niccola said:**
> 




First, make some search in google/ubuntuforums and you'll find solutions. This thread is just for Intel/AMD Hybrid Graphics

---

### Post by N0oki3 on 2012-06-11
[quote="Niccola"]Try to send an email/message or report to HP asking to a new BIOS release to solve linux kernel problems. I did it a long time ago and they send me a new BIOS release in 2 weeks. Report the problem easily and nice-speaking[/quote]
I'll try that again

[quote="Niccola"]Otherwise, Have you tried to google this errors? Everything works fine without the fglrx driver? I mean, with a fresh ubuntu installation (out-of-box)?[/quote]
Ubuntu without any fglrx drivers works perfectly fine with Unity 2D and Sandy Bridge graphic card

[quote="Niccola"]this errors that you show us "EXT2-fs (loop1): error" stand for persistent file system problem (damaged, corrupted, etc...) [/quote]
This error happened after installing fglrx drivers with aticonfig --initial -f 

[quote="Niccola"]Are running in an USB flash driver, right? How much space there is in this flash drive? Why don't you try to INSTALL it on your HD? Dual Boot or External HDD?? Try it.[/quote]
Usb has 8GB so there is no way that I have ran out of space. Also it is maybe 2 weeks old and it cannot be damaged as everything works properly before driver update.

---

### Post by Niccola on 2012-06-11
> **N0oki3 said:**
> Hm...where exactly I have contacted live support and they couldn't help me. I'll check again and send them e-mail


Ubuntu without any fglrx drivers works perfectly fine with Unity 2D and Sandy Bridge graphic card


This error happened after installing fglrx drivers with aticonfig --initial -f 


Usb has 8GB so there is no way that I have ran out of space. Also it is maybe 2 weeks old and it cannot be damaged as everything works properly before driver update.

Did you configure the persistent space in your USB flash drive with Ubuntu?

I think the problem is the persistent space. Im not talking about your flash drive been damaged, but the fact of the Filesystem been damaged. Try to create again the USB with persistent space (at least 2GB). But, I really recommend you to install it on a HDD.

Without persistent configuration setted, everytime you reboot the system in your flash drive, the default configuration will be reloaded. So, you won't have any programs, configuration or personal files saved in each boot.
Read more at: [http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/)

technical information from canonical: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

and how to create a linux persistent live USB:
[http://www.howtogeek.com/65888/create-a-persistent-bootable-and-virtualized-linux-usb-drive-with-lili/](http://www.howtogeek.com/65888/create-a-persistent-bootable-and-virtualized-linux-usb-drive-with-lili/)

---

### Post by N0oki3 on 2012-06-11
Yes, I have created persistent USB properly with 7GB.

Also as I cannot send e-mail to HP into USA only into my country which only is about services. I have to find the e-mail to ask them if they can create/send me fix for switchable graphic cards.

I have had installed 4 times ubuntu on my hdd and it was same thing (no kernel error) but after aticonfig --initial -f, reboot, it said low graphic mode.

**update:** Pavilion G6 serie doesn't have support for switchable graphics and it won't have. On live support they can't give me e-mail nor I cannot contact HP via telephone (due to not living in USA). So I guess untill there won't be a fix in linux like in windows that it switches graphic card manually or maybe once upon a time new version of bios, I cannot use unity 3D.

---

### Post by ciesla.tomasz on 2012-06-13
it won't work on dell vostro 3350 with radeon 6470
but there there is a way to install catalyst control center - just simply type:
```
sudo apt-get install fglrx
```and after instalation you have to configure xorg with command:
```
sudo aticonfig --initial - f
```or
```
sudo amdconfig --initial - f
``` and reboot
unfortunately driver will recognize radeon 6470 as radeon 7000 family so you gonna endup wtih really poor performance... up side is that you can switch off radeon via catalyst control center but you will loose hardware acceleration on intel 3000 and still have silly performance

so the best way to live with radeon 6470 is to simply switch it off:
```
sudo gedit /etc/rc.local
```and add there before exit line
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```and reboot
some plp are recomending adding to rc.local additional line
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```and blacklisting radeon
```
sudo gedit /etc/modprobe.d/blacklist.conf
```and add there:
```
blacklist radeon
```after that you can turn on/off radeon with vgaswitcheroo
```
sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
or
sudo echo ON > /sys/kernel/debug/vgaswitcheroo/switch
```but it won't affect computer performance, only heating and battery life....

if you'll get comunicate "premission denied" do that:
```
sudo chmod -R 705 /sys/kernel/debug
sudo chown -R **aaa**:**aaa** /sys/kernel/debug/vgaswitcheroo
```where **aaa** is your username

I'm still waiting for the support of the radeon 6470 for linux os's from amd....

ps to thest 3d graphics performance install glmark2:
```
sudo apt-get install glmark2
```and to run it type:
```
glmark2
```after installing fglrx you will wave 10 times worsed performance than after switching off radeon in rc.local

---

### Post by Alexislavie on 2012-06-13
> **ciesla.tomasz said:**
> it won't work on dell vostro 3350 with radeon 6470
but there there is a way to install catalyst control center - just simply type:
```
sudo apt-get install fglrx
```and after instalation you have to configure xorg with command:
```
sudo aticonfig --initial - f
```or
```
sudo amdconfig --initial - f
``` and reboot
unfortunately driver will recognize radeon 6470 as radeon 7000 family so you gonna endup wtih really poor performance... up side is that you can switch off radeon via catalyst control center but you will loose hardware acceleration on intel 3000 and still have silly performance


Seriously, THIS IS TOTALLY USELESS !
Do you think we manually create the deb of fglrx for fun ?! I know we can just install fglrx via the repository but the version provided by Ubuntu is already outdated. YOU DO NEED TO USE THE LATEST VERSION !

---

### Post by ciesla.tomasz on 2012-06-14
This walkaroud ([http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)) wroks properly on dell vostro 3350 with radeon hd6470m but only on 64-bit system (i've tested it on ubuntu 12.04 dvd edition 64 bits with updates). It won't work on Ubuntu desktop 32 bit (tested). Catalyst Control Center recognizes discrete graphics properly (radeon 6400 series) but there are two or three issues:
1. You can't switch to the integrated graphich via catalyst control center - it'll only hang you system, you have to do it via command line:
[FONT=Arial][SIZE=2]```
aticonfig --pxl # List current activated GPU
sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect
sudo aticonfig --px-igpu # Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```[/SIZE][/FONT]
It switches gpu but i'm getting error with it:
```
PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
```
2. Open gl performance on dgpu is only 10% better than on igpu... (results from glmark2)
3. On igpu you cant run some 3d benchmarks like Unigine heaven - they just hang up

---

### Post by rompelstompel on 2012-06-15
[FONT=Arial][SIZE=2]**HP Pavilion dv7-6051ei**, Intel HD 3000, AMD 6770m, HDMI Intel/AMD: working/working, VGA      Intel/AMD: working/working[/SIZE][/FONT]

---

### Post by Holger D on 2012-06-15
**SONY Vaio VPC-SA3BGX**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working

---

### Post by Thrashrokz33 on 2012-06-16
My card falls into the Radeon HD 7xxx (7690m) series listed as "Catalyst only". Forgive me for not understanding, but does that mean this fix won't be possible for me?

---

### Post by N0oki3 on 2012-06-16
> **Thrashrokz33 said:**
> My card falls into the Radeon HD 7xxx (7690m) series listed as "Catalyst only". Forgive me for not understanding, but does that mean this fix won't be possible for me?

What is your laptop (full name), do you have latest bios update, have you option to set "fixed hybrid graphics" in bios ? which system do you run? is it 32 or 64 bit ? more info please.

---

### Post by daniaix on 2012-06-16
Hi, 

If you ever come to Paris, I'll offer you a beer! It works well on a :[SIZE=2][FONT=Arial][B]
Dell Vostro 3450, [/B][/FONT][/SIZE][FONT=Arial][SIZE=2]Intel HD 3000, AMD Radeon HD 6630m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]

---

### Post by Thrashrokz33 on 2012-06-16
> **N0oki3 said:**
> What is your laptop (full name), do you have latest bios update, have you option to set "fixed hybrid graphics" in bios ? which system do you run? is it 32 or 64 bit ? more info please.

I have a Lenovo Y470. I'll have to install the latest BIOS update I think, as I've checked for the "fixed" option inside of it and didn't find anything.

I also don't have an Ubuntu installation on this machine yet, but I planned on making it a 64bit.

---

### Post by markackerman8@gmail.com on 2012-06-17
OK I am new to this thread but NOT new to this problem - PLEASE help!!

HP Envy17-3195 intel hd3000/amd-ATI 6850m graphics cards
any way here is what i did from a fresh Ubuntu install tonight - if it helps anyone with troubleshooting this - PLEASE respond

- installed fresh 12.04 Ubuntu 64 bit
- downloaded and installed amd's driver 12.4 according to the wicki
[http://wiki.cchtml.com/index.php/Ubu...TI.27s_site.29](http://wiki.cchtml.com/index.php/Ubu...TI.27s_site.29)
- after sudo amdconfig --initial -f, used switch_between_cards script seemed to work BUT logout or reboot X fails and only cntgrl+alt+F1 works, so I had to remove /etc/X11/xorg.conf, to get back in (and no discrete card function) - arghhhhhhh
- additionally there is no switcharoo file
  - ati CCC won't load no matter how install the AMD graphics driver (proprietary or open source or ubuntu proposed in add'l drivers)

PLEASE can anyone suggest any other troubleshooting tips - now 5 months without a functional Ubuntu

p.s. still NO success using my ATI/AMD 6850m graphics card - 5 months later - please help - I Like games and Hate Windows - Thanks

---

### Post by N0oki3 on 2012-06-17
DO not install drivers from jockey-gtm (additional drivers) remove and purge fglrx, do not use switcheero. Check for latest bios update, set fixed hybrid graphics (dgpu) in BIOS and do as the OP (post #1) did. It should work! If it doesn't, than you're notebook only have dynamic graphics and you have to wait for fix like the rest of us

---

### Post by markackerman8@gmail.com on 2012-06-17
> **N0oki3 said:**
> DO not install drivers from jockey-gtm (additional drivers) remove and purge fglrx, do not use switcheero. Check for latest bios update, set fixed hybrid graphics (dgpu) in BIOS and do as the OP (post #1) did. It should work! If it doesn't, than you're notebook only have dynamic graphics and you have to wait for fix like the rest of us

I installed the amd drivers from their website 12.4 (LATEST STABLE)on a clean Ubuntu 12.04 64bit (notrhing from add'l drivers - unless during the install I said it could install 3rd party software - hmmmm? should I not allow it to install 3rd party software during the install and try again after a new install? or just a purge?

though i am not optimistic as it seems I have tried EVERYTHING.

and my bios is updated and hp has nothing in it to adjust video cards at all - stupid when they know it causes problems and many may just want one or the other to use.  Oh well - thank you for your post and look forward to your responses.

---

### Post by N0oki3 on 2012-06-17
[quote=markackerman8@gmail.com]I installed the amd drivers from their website 12.4 (LATEST STABLE)on a clean Ubuntu 12.04 64bit[/quote]
Install it from step 1 to last step from OP (post #1) If it won't work, than you have to wait for dynamic hybrid graphic cards fix (We do not know **when and if** there is going to be fix for dynamic graphic cards)

---

### Post by Alexislavie on 2012-06-18
> **daniaix said:**
> Hi, 

If you ever come to Paris, I'll offer you a beer! It works well on a :[SIZE=2][FONT=Arial][B]
Dell Vostro 3450, [/B][/FONT][/SIZE][FONT=Arial][SIZE=2]Intel HD 3000, AMD Radeon HD 6630m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]

As I live In Orléans, I hope to attend the next Ubuntu Party in Paris. I will see you there in November, maybe ;).

---

### Post by Alexislavie on 2012-06-18
> **N0oki3 said:**
> DO not install drivers from jockey-gtm (additional drivers) remove and purge fglrx, do not use switcheero. Check for latest bios update, set fixed hybrid graphics (dgpu) in BIOS and do as the OP (post #1) did. It should work! If it doesn't, than you're notebook only have dynamic graphics and you have to wait for fix like the rest of us

I think you misunderstood this thread, this thread is for people who doesn't have any gpu setting in their BIOS. The default parameter is locked to dynamic : both card are powered at start and you can change it. Then this must be catalyst (the driver) that can only control the dgpu and his energy consumption.

---

### Post by Alexislavie on 2012-06-18
> **markackerman8@gmail.com said:**
> I installed the amd drivers from their website 12.4 (LATEST STABLE)on a clean Ubuntu 12.04 64bit (notrhing from add'l drivers - unless during the install I said it could install 3rd party software - hmmmm? should I not allow it to install 3rd party software during the install and try again after a new install? or just a purge?

though i am not optimistic as it seems I have tried EVERYTHING.

and my bios is updated and hp has nothing in it to adjust video cards at all - stupid when they know it causes problems and many may just want one or the other to use.  Oh well - thank you for your post and look forward to your responses.

Can you describe "3d party software" ?

---

### Post by Alexislavie on 2012-06-18
> **N0oki3 said:**
> Install it from step 1 to last step from OP (post #1) If it won't work, than you have to wait for dynamic hybrid graphic cards fix (We do not know **when and if** there is going to be fix for dynamic graphic cards)

Not before 2 years for sure !
Wayland will be able to switch gpus without reboot as in Windows. It will be the replacement of Xorg. But it still need a lot of dev.

---

### Post by Alexislavie on 2012-06-18
> **Thrashrokz33 said:**
> I have a Lenovo Y470. I'll have to install the latest BIOS update I think, as I've checked for the "fixed" option inside of it and didn't find anything.

I also don't have an Ubuntu installation on this machine yet, but I planned on making it a 64bit.

It should work... normally, but I can't promise anything.
I don't have gpu option in my BIOS too.

---

### Post by Alexislavie on 2012-06-18
I will add some troubleshooting help tonight to my first post tonight (UTC +02:00 France), this may help some of you.

And don't give up !

You know it's worst with nvidia as they don't official support, they have bumblebee which use open source drivers, this is great but they also have poorest performance than if they had the propietary driver working.

And for fun go here : [http://www.youtube.com/watch?v=MShbP3OpASA&feature=player_embedded](http://www.youtube.com/watch?v=MShbP3OpASA&feature=player_embedded) to 49'00 :).

Catalyst isn't working out of the box, but at least they're trying to make it.

---

### Post by N0oki3 on 2012-06-18
> **Alexislavie said:**
> I think you misunderstood this thread, this thread is for people who doesn't have any gpu setting in their BIOS. The default parameter is locked to dynamic : both card are powered at start and you can change it. Then this must be catalyst (the driver) that can only control the dgpu and his energy consumption.

I don't have this option in BIOS and when I want to use my radeon HD 6470m it fails into low graphic mode

---

### Post by Alexislavie on 2012-06-18
> **Alexislavie said:**
> I think you misunderstood this thread, this thread is for people who doesn't have any gpu setting in their BIOS. The default parameter is locked to dynamic : both card are powered at start and you can change it. Then this must be catalyst (the driver) that can only control the dgpu and his energy consumption.
" can change it"
I'm sorry I meant "can't change it", I just saw my mistake.

---

### Post by Niccola on 2012-06-19
I saw a lot of people getting trouble after reboot and getting low graphic mode or X failure.

I DO NOT recommend to execute the command 'sudo aticonfig --px-dgpu' before reboot!

Seems that AMD make post-processing changes after driver installation in first reboot. So, reboot the machine after driver installation to fglrx be loaded with default settings. I really recommend everybody that's having problem to follow the post #1 until the following command:

```
sudo aticonfig --initial -f
```

after that, make sure that your /etc/X11/xorg.conf file isn't empty.

Then reboot your machine. DO NOT run 'sudo aticonfig --px-dgpu' before reboot!

After this first boot with AMD drivers with default settings, you be able to continue the POST #1 and get success in driver installation.

TIP:
Instead using 'sudo aticonfig --px-dgpu' to switch to Discrete GPU, use amdcccle.

---

### Post by Thrashrokz33 on 2012-06-19
Ok quick question. I checked my BIOS and found the options:

**Graphics Mode:** 
-Switchable Graphics
-UMA graphics

I'm not sure, but is this basically the dynamic and fixed settings people are talking about, where UMA will only run the Intel card and not the discrete GPU? 

If so, I don't plan on even using the discrete GPU inside of Ubuntu to save battery life, so **can I just enable the UMA graphics setting, and avoid installing any Catalyst drivers inside Ubuntu completely? **

I want to take this path because the HD 7xxx series cards have terrible Catalyst support even inside Windows, where the 12.4 Catalyst isn't even supported, so I imagine it would only be more nightmarish to work with this card's drivers in Ubuntu, ignoring the fact that I have no use for high graphics processing in Linux anyway.

---

### Post by Alexislavie on 2012-06-20
> **Thrashrokz33 said:**
> Ok quick question. I checked my BIOS and found the options:

**Graphics Mode:** 
-Switchable Graphics
-UMA graphics

I'm not sure, but is this basically the dynamic and fixed settings people are talking about, where UMA will only run the Intel card and not the discrete GPU? 

If so, I don't plan on even using the discrete GPU inside of Ubuntu to save battery life, so **can I just enable the UMA graphics setting, and avoid installing any Catalyst drivers inside Ubuntu completely? **

I want to take this path because the HD 7xxx series cards have terrible Catalyst support even inside Windows, where the 12.4 Catalyst isn't even supported, so I imagine it would only be more nightmarish to work with this card's drivers in Ubuntu, ignoring the fact that I have no use for high graphics processing in Linux anyway.

Yes, you could do this, if you have no use of the AMD gpu.

---

### Post by Niccola on 2012-06-20
> **Thrashrokz33 said:**
> Ok quick question. I checked my BIOS and found the options:

**Graphics Mode:** 
-Switchable Graphics
-UMA graphics

I'm not sure, but is this basically the dynamic and fixed settings people are talking about, where UMA will only run the Intel card and not the discrete GPU? 

If so, I don't plan on even using the discrete GPU inside of Ubuntu to save battery life, so **can I just enable the UMA graphics setting, and avoid installing any Catalyst drivers inside Ubuntu completely? **

I want to take this path because the HD 7xxx series cards have terrible Catalyst support even inside Windows, where the 12.4 Catalyst isn't even supported, so I imagine it would only be more nightmarish to work with this card's drivers in Ubuntu, ignoring the fact that I have no use for high graphics processing in Linux anyway.

Have you tried driver 12.6 beta? I heard that it is working nice under gnome (I don't know about another windows manager, but you can try it out and tell us). Don't forget to report to AMD if you find bugs or driver-related problems.

According with AMD ([in this link]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx")) they solved a lot of issues in  7xxx series.

What's your laptop brand/model?

You can keep the ***'Switchable Graphics'*** BIOS options and turn off your Discrete Graphic Card by software (using Catalyst, for example). I think this option more flexible. Ok, it depends of your wish or utilization way.

I can't install Catalyst 12.6 beta because I'm developing OpenCL programs and I need the version 12.4 until official release of 12.6 and AMD APP SDK v2.7 support get confirmed! So, check it out ;)

---

### Post by Thrashrokz33 on 2012-06-20
> **Niccola said:**
> Have you tried driver 12.6 beta? I heard that it is working nice under gnome (I don't know about another windows manager, but you can try it out and tell us). Don't forget to report to AMD if you find bugs or driver-related problems.

According with AMD ([in this link]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst126beta.aspx")) they solved a lot of issues in  7xxx series.

What's your laptop brand/model?

You can keep the ***'Switchable Graphics'*** BIOS options and turn off your Discrete Graphic Card by software (using Catalyst, for example). I think this option more flexible. Ok, it depends of your wish or utilization way.

I can't install Catalyst 12.6 beta because I'm developing OpenCL programs and I need the version 12.4 until official release of 12.6 and AMD APP SDK v2.7 support get confirmed! So, check it out ;)

Thanks for the link to that 12.6 beta driver. I read through it and didn't see any support for my card though, the 7690m. I may try to install these drivers after I get Ubuntu installed and making sure it works fine with the Intel card. I do have very limited experience with installing drivers though, so if it broke something I'd have no idea how to fix it.

And laptop brand/model is Lenovo Y470.

---

### Post by cyanide911 on 2012-06-22
Okay I'm trying to do these steps in Linux Mint 13, I have a quesiton. 

Will this step cause any issues in Mint? I ask because of the Ubuntu/precise at the end.
[FONT=Arial][SIZE=2]sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise

Also more importantly, 

My HP 6121tx has an option of setting graphics to 'Dynamic' or 'Static' in the Bios. In dynamic, (In windows) CCC chooses which card to run on per application basis, and in Static, we've to manually select a card via CCC. If I want to use only the Integrated card in Linux, and I'm following the steps in post 1, which mode should I select?
[/SIZE][/FONT]

---

### Post by Alexislavie on 2012-06-22
> **cyanide911 said:**
> Okay I'm trying to do these steps in Linux Mint 13, I have a quesiton. 

Will this step cause any issues in Mint? I ask because of the Ubuntu/precise at the end.
[FONT=Arial][SIZE=2]sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise

Also more importantly, 

My HP 6121tx has an option of setting graphics to 'Dynamic' or 'Static' in the Bios. In dynamic, (In windows) CCC chooses which card to run on per application basis, and in Static, we've to manually select a card via CCC. If I want to use only the Integrated card in Linux, and I'm following the steps in post 1, which mode should I select?
[/SIZE][/FONT]

Dynamic switching is not supported in Linux, use the static setting (I call it manual switching). But I'm not sure so try static and if it doesn't work try dynamic. (I have doubt because my computer BIOS setting is set to dynamic, and I can't change it).

If Linux Mint is based on Ubuntu 12.04 I think it will works.

---

### Post by Alexislavie on 2012-06-22
> **Thrashrokz33 said:**
> Thanks for the link to that 12.6 beta driver. I read through it and didn't see any support for my card though, the 7690m. I may try to install these drivers after I get Ubuntu installed and making sure it works fine with the Intel card. I do have very limited experience with installing drivers though, so if it broke something I'd have no idea how to fix it.

And laptop brand/model is Lenovo Y470.

Mine wasn't listed with 12.3 but it still worked.

---

### Post by cyanide911 on 2012-06-22
I'm getting this error when running [FONT=Arial][SIZE=2]sudo apt-get install ia32-libs lib32gcc1 libc6-i386[/SIZE][/FONT]

```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Ignoring this causes an issue later on.

---

### Post by Alexislavie on 2012-06-22
> **cyanide911 said:**
> I'm getting this error when running [FONT=Arial][SIZE=2]sudo apt-get install ia32-libs lib32gcc1 libc6-i386[/SIZE][/FONT]

```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```Ignoring this causes an issue later on.

Try "sudo apt-get install ia32-libs-multiarch"

---

### Post by Niccola on 2012-06-22
Today appears a new update here and I've updated.
One of package was Xorg xserver video. Now video is flickering (tearing) a lot!!! Be careful! Do not update xorg xserver video.

---

### Post by Alexislavie on 2012-06-22
> **Niccola said:**
> Today appears a new update here and I've updated.
One of package was Xorg xserver video. Now video is flickering (tearing) a lot!!! Be careful! Do not update xorg xserver video.

No problem for me.
On  igpu or dgpu ?

---

### Post by Niccola on 2012-06-22
> **Alexislavie said:**
> No problem for me.
On  igpu or dgpu ?

both of them. Possible fix after re-installing driver. I will check it tomorrow

---

### Post by Pay87 on 2012-06-23
Hi! First of all thank your for this guide!
I only have one problem..

When I switch the gpu I get the following error:

PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: Warning: /etc/OpenCL/vendors/amdocl32.icd skipped because /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (link group x86_64-linux-gnu_gl_conf) does not exist.

Any idea how to fix this?

---

### Post by Gelai on 2012-06-23
Is this Method Works Perfectly on 12.04 Kernel-PAE ..?
i've just have fresh installed of 12.04 on my Notebook.
wondered if this method doesnt mess-up with the system 
like what i've experienced on 11.10-Oneiric. that I
always get my VGA Not-Working after PAE installed.

Thanks so much :)

---

### Post by Niccola on 2012-06-23
> **Pay87 said:**
> Hi! First of all thank your for this guide!
I only have one problem..

When I switch the gpu I get the following error:

PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: Warning: /etc/OpenCL/vendors/amdocl32.icd skipped because /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (link group x86_64-linux-gnu_gl_conf) does not exist.

Any idea how to fix this?

I've got the same error after update the system. But it was solved reinstalling the driver again.
So, Try to reinstall the driver!

---

### Post by Alexislavie on 2012-06-24
> **Niccola said:**
> I've got the same error after update the system. But it was solved reinstalling the driver again.
So, Try to reinstall the driver!

This is a warning, not an error, I've got the same and I do not care about it.

---

### Post by balta on 2012-06-24
**HP Pavillion G6 1356el**, Intel HD 3000, AMD 7450M*, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

*It **is** a 7450M but it's detected as a 6400 under Ubuntu (don't know why, still everything seems to work fine)

Will update as soon as I can do a proper battery test.

Big thanks!

---

### Post by Gelai on 2012-06-24
Have Tried it and followed your instructions and also here [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file) still got the same Problem. it boot with saying "Low Graphics" then to Terminal. i tried also the step 2 on the terminal using nano editor. still no luck. My machine is HP Pavillion G6 1045SX Core i5 AMD 6470M hybrid. 
i also did uninstall the drivers and update my machine via Software Update and on terminal. and Tried to do it again, and still don't work.

any idea.?

---

### Post by Entomologist on 2012-06-24
What-oh, what-oh!!
First of all, let me compliment you on that tutorial of yours, great stuff.
However, if i may ask you an advice:
I'm using an ACER aspire timeline X 5820 TG with Ubuntu first installed as 11.04, and then upgraded to 12.04 .
> lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Robson CE [AMD Radeon HD 6300 Series] (rev ff)

The problem was that, with fglrx installed, any program looking for OPENGL would exit saying:
> ...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13
 
Therefore, I looked for a solution via [HTML]http://askubuntu.com/questions/81344/how-to-fix-error-with-ati-driver-error-of-failed-request[/HTML]Though I found out that the radeon card was blacklisted but fglrx wasn't.
>  more /etc/modprobe.d/fglrx.conf
# This file was installed by fglrx
# Do not edit this file manually

blacklist radeon
alias fglrx fglrx
alias radeon off
alias lbm-radeon off
 Still I tried to reinstall completely fglrx, by >  sudo /usr/share/ati/fglrx-uninstall.sh
 sudo apt-get remove --purge xorg-driver-fglrx fglrx*
 sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx
It still wouldn't work. Now coming to the particular problem, while trying your solution, I found that,while accomplishing the first step installing-the-fglrx*.deb-part, the following problem was happening:

> sudo dpkg -i fglrx*.deb
Selecting previously unselected package fglrx.
(Lecture de la base de données... 457071 fichiers et répertoires déjà installés.)
Dépaquetage de fglrx (à partir de fglrx_8.961-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Dépaquetage de fglrx-amdcccle (à partir de fglrx-amdcccle_8.961-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-dev.
Dépaquetage de fglrx-dev (à partir de fglrx-dev_8.961-0ubuntu1_amd64.deb) ...
Paramétrage de fglrx (2:8.961-0ubuntu1) ...
update-alternatives: utilisation de «*/usr/lib/fglrx/ld.so.conf*» pour fournir «*/etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf*» (x86_64-linux-gnu_gl_conf) en mode automatique.
update-alternatives: ***avertissement: création de /etc/OpenCL/vendors/amdocl32.icd abandonnée car le fichier associé /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (du groupe de liens x86_64-linux-gnu_gl_conf) n'existe pas.***
update-alternatives: ***avertissement: forçage de la réinstallation de l'alternative /usr/lib/fglrx/ld.so.conf car le groupe de liens x86_64-linux-gnu_gl_conf est cassé***
update-alternatives: ***avertissement: création de /etc/OpenCL/vendors/amdocl32.icd abandonnée car le fichier associé /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (du groupe de liens x86_64-linux-gnu_gl_conf) n'existe pas.***
update-alternatives: utilisation de «*/usr/lib/fglrx/alt_ld.so.conf*» pour fournir «*/etc/ld.so.conf.d/i386-linux-gnu_GL.conf*» (i386-linux-gnu_gl_conf) en mode automatique.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.961 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Traitement des actions différées («*triggers*») pour «*ureadahead*»...
Traitement des actions différées («*triggers*») pour «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Paramétrage de fglrx-amdcccle (2:8.961-0ubuntu1) ...
Paramétrage de fglrx-dev (2:8.961-0ubuntu1) ...
Traitement des actions différées («*triggers*») pour «*initramfs-tools*»...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Traitement des actions différées («*triggers*») pour «*libc-bin*»...
ldconfig deferred processing now taking place......
Done.
And so this is where it finally caught up with me:
> aticonfig --initial -f
aticonfig: No supported adapters detected
BTW FYI, those following links do not exist anymore >.<
> 
/usr/lib/pxpress/ld.so.conf
/usr/bin/amdupdaterandrconfig
/usr/lib/pxpress/alt_ld.so.conf
/usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
"update-alternatives: avertissement: /usr/lib/x86_64-linux-gnu/xorg/extra-modules ne sera pas remplacé par un lien."


So feeling like I shoot myself in the foot big time, I'm humbly asking you what should I do in order to repair those broken links, and try your solution with my particular configuration.
I do thank you very much in advance for an kind of answer you might give me(or anyone else for that matter).
Cheers

---

### Post by cyanide911 on 2012-06-25
I got the above fix working properly on my HP DV6 6121tx, Mint 13. 

But one thing I'm noticing, on integrated graphics, if I plug my laptop to the charger, it starts to heat up in the area where it heated up if I ran it on discrete graphics. Using the command in OP's post, I checked which GPU I was running. It still said integrated, but I'm skeptical about why it's getting heated so much.

---

### Post by Gelai on 2012-06-26
I think, i had enough to all the stuff regarding with ATI/AMD RADEON 6470M driver to get it work in UBUNTU 12.04 w/ kernel Pae, and 11.10 w/ kernel PAE, I did so many attempts of installing 11.10 w/ PAE and 12.04 and searching for an answer on how to get this VGA work on it to my HP Pavilion G6 i5 AMD Hybrid Graphic Card. but still i didn't get any answer and worst is no-one Replying to my concerns and even on a thread.

But anyway I just done reformatting my machine and use the Ubuntu 11.10 x86 as it is, with 2.4GB used only (without PAE) with AMD RADEON HD 6470M Hybrid Graphic Cards Fully working, and stuffs....

I know Developers and working very hard on this Project. We believed in you! ;) we know you can do much better than we expect, ;) we will just wait for your Next Great and Wonderful Deployment.

Cheers! :guitar:

---

### Post by cyanide911 on 2012-06-26
> **wegah said:**
> Try to do it.

under /etc/default/grub

Put this

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"

then save

and use the comand

update-grub2


Will work

I'm having the same problem, and this didn't work for me. I can't adjust my brightness via any method. Be it FN keys, be it System brightness settings, be it xbrightness etc.

---

### Post by srsrus on 2012-06-26
&#1044;&#1086;&#1073;&#1088;&#1099;&#1081; &#1076;&#1077;&#1085;&#1100;!
&#1048;&#1079;&#1074;&#1080;&#1085;&#1080;&#1090;&#1077; &#1095;&#1090;&#1086; &#1087;&#1080;&#1096;&#1091; &#1085;&#1072; &#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1084;, &#1090;.&#1082;. &#1089; &#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080;&#1084; &#1091; &#1084;&#1077;&#1085;&#1103; &#1087;&#1086;&#1082;&#1072; &#1087;&#1083;&#1086;&#1093;&#1086;&#1074;&#1072;&#1090;&#1086;. 
&#1059; &#1084;&#1077;&#1085;&#1103; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099; &#1089; &#1087;&#1077;&#1088;&#1077;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1077;&#1084; &#1084;&#1077;&#1078;&#1076;&#1091; &#1074;&#1080;&#1076;&#1077;&#1086;&#1082;&#1072;&#1088;&#1090;&#1072;&#1084;&#1080;. &#1053;&#1086;&#1091;&#1090; Lenovo E425 A4. 

```
~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9648]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series [1002:6760]
```

```
~$ cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:01.0
1:DIS: :Pwr:0000:01:00.0
```

&#1087;&#1099;&#1090;&#1072;&#1083;&#1089;&#1103; &#1086;&#1090;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1100; &#1076;&#1080;&#1089;&#1082;&#1088;&#1077;&#1090;&#1085;&#1091;&#1102; &#1074;&#1080;&#1076;&#1077;&#1086;&#1082;&#1072;&#1088;&#1090;&#1091; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1086;&#1081;
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
&#1074;&#1089;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1072;&#1077;&#1090; &#1085;&#1072;&#1087;&#1088;&#1086;&#1095;&#1100;.

&#1055;&#1086;&#1084;&#1086;&#1075;&#1080;&#1090;&#1077; &#1087;&#1086;&#1078;&#1072;&#1083;&#1091;&#1081;&#1089;&#1090;&#1072;!!!

---

### Post by AndrewX192 on 2012-06-27
I am looking to purchase a NP9150 (Clevo P150EM), with Intel HD Graphics 4000, and a Radeon HD 7970M. The external video outputs are attached to the Radeon HD 79790M, but the laptop LCD is attached to the Intel HD graphics. There is no switch in the BIOS to switch graphics cards.

1) Will I be able to use the AMD card to power additional monitors?

2) Will I be able to use the AMD card for enhanced graphics power?

---

### Post by Alexislavie on 2012-06-27
> **AndrewX192 said:**
> I am looking to purchase a NP9150 (Clevo P150EM), with Intel HD Graphics 4000, and a Radeon HD 7970M. The external video outputs are attached to the Radeon HD 79790M, but the laptop LCD is attached to the Intel HD graphics. There is no switch in the BIOS to switch graphics cards.

1) Will I be able to use the AMD card to power additional monitors?

2) Will I be able to use the AMD card for enhanced graphics power?

No idea. I think no for the moment.

---

### Post by gh1234 on 2012-06-28
Thanks for this tutorial! It works very good at my Vostro 3350 (from 2h up to 5h).

But I found out, that the time decreases again after suspend to ram.
Had >5h before going to suspend and now <4h afterwards.
When I kill Xorg and log in again I have the <5h back again.
Powertop reports ~14W before and ~21W after suspend.

Any suggestions here? If I would get this fixed I would have values equal to Windows.
I suspect the discrete graphics card to enable somehow in the background without being used. But I am not sure about this. Can anyone reproduce this?

---

### Post by Z4CHARiAS on 2012-06-29
hey there
first of all many thanks on this huge effort of yours, to make things work on linux, and to your senseis as well.
secondly: i own  an hp pavillion dv3-4160ep with a mobility radeon hd 5470 wich is not on the supportted graphic list.
any chance or do you know when/if it will be supported?
kudos

---

### Post by clement.analogue on 2012-06-30
> **Z4CHARiAS said:**
> i own  an hp pavillion dv3-4160ep with a mobility radeon hd 5470 wich is not on the supportted graphic list.
any chance or do you know when/if it will be supported?

I've got the same graphic card on my laptop. It worked only at the release of Ubuntu 11.04 (not before), then an update in this version broke everything.

---

### Post by Z4CHARiAS on 2012-06-30
> **clement.analogue said:**
> I've got the same graphic card on my laptop. It worked only at the release of Ubuntu 11.04 (not before), then an update in this version broke everything.
so how u manage to use it? i mean, i just want to use the intel crd all the time, since its a laptop and i like to carry it around wth no worries of battery life. and the kind of use i hv, does not require gpu hardcore activity.
kudos

---

### Post by clement.analogue on 2012-06-30
That's the all point of installing catalyst drivers. You can't disable any of the graphic cards with the free drivers. The both working at the same time, that's why battery dies so quickly. On my laptop, having both cards running together warm the laptop until the wifi card stop working due to heat.
So I don't manage it, I just hope it'll work eventually.

---

### Post by gh1234 on 2012-07-01
> **clement.analogue said:**
> That's the all point of installing catalyst drivers. You can't disable any of the graphic cards with the free drivers. The both working at the same time, that's why battery dies so quickly. On my laptop, having both cards running together warm the laptop until the wifi card stop working due to heat.
So I don't manage it, I just hope it'll work eventually.

With the free driver there is still vga switcheroo which worked quite well until I found this. The problem is that the catalyst driver fails to run in low power mode after S2RAM.

---

### Post by clement.analogue on 2012-07-01
How do you switch from one graphic card to another ? And, more important, how do you turn off the card unused with the free drivers ?

---

### Post by gh1234 on 2012-07-01
> **clement.analogue said:**
> How do you switch from one graphic card to another ? And, more important, how do you turn off the card unused with the free drivers ?

I used vgaswitcheroo:
```
echo "OFF"|sudo tee /sys/kernel/debug/vgaswitcheroo/switch

```does the trick with the free driver. The problem with this solution was, that:
a) it still consumed more power than this one (dunno why) it might be the same issue that occurs for me after S2RAM because the reported discharge rate was nearly the same :/
b) it was impossible to get the discrete graphics to work for some reason, so gaming was impossible thought.

---

### Post by AshenShugar on 2012-07-02
This worked to get graphics working. My only caveat is that it slowed my boot time by about 5-6 seconds, not a huge deal, except that I think it doesn't need to. At a certain point in my boot, xorg goes into uninterruptible sleep waiting for the Radeon GPU, which should be disabled as I'm in igpu mode. There is a six-second jump in the X.org log file which corresponds exactly to the sleep and which always occurs between the same two lines in the fglrx calls.

Computer: Samsung 700Z5B
OS: Ubuntu 12.04 LTS
Kernel Version: 3.2.0-26
Catalyst Version 12.6, but 12.4 had the same issue
Radeon HD 6400M

---

### Post by clement.analogue on 2012-07-04
If I understand, if I use this command, the intel graphics will be used instead of the ATI, but the energy consumes will be the same ?
So, I guess the ATI graphics still power on but not used, am I right ?

---

### Post by codeguru11 on 2012-07-05
> **Niccola said:**
> I've found the solution!!!!!!
 

 It's not necessary  the mesa-dri-experimental package to solve the problem.
 I've found a weird thing done by AMD fglrx driver during installation, but to make sure it'll work, let's verify if you have the same diagnostic:
 First thing is about glxinfo, if it show no direct rendering, just execute this command:
 ```
 LIBGL_DEBUG=verbose; glxinfo 
``` the first output lines, if appears a lot of 'libGL errors' like below:
 
*libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed*
 *libGL error*: *dlopen* /*usr/lib32/fglrx/dri/i915_dri.so failed*
 
 *if you saw, there's an i915 dri driver that couldn't be loaded for some reason. As you can see, the directory is /usr/lib32/fglrx/dri/ but, if you ls this directory you will not see more than one driver named*
 *fglrx_dri.so*
 *So, I've figured out that when fglrx driver installs it changes the LIBGL_DRIVERS_PATH to its own particular path, such that is: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you write the command below you'll see the output like above:*
 *```
 echo $LIBGL_DRIVERS_PATH 
```*[I]
the output will be something like that: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri[/I]
* if you have the same output as above you just have to add the directory where is the intel dri drivers, lets do that!*
[I]
as you can see in this file : /etc/X11/Xsession.d/10fglrx[/I]
 *```
$ gksu gedit /etc/X11/Xsession.d/10fglrx 
```*
 ```
 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH *
```
*in the fourth line you have the LIBGL_DRIVERS_PATH defined as: /usr/lib/fglrx/dri:/usr/lib32/fglrx/dri*
 *if you have the same as above, just add the following path in that fourth line:*
 
*for x86_64 (64 bits): /usr/lib/x86_64-linux-gnu/dri/*
 
*for x86 (32 bits) linux: /usr/lib32/dri/*
 
*just add is with a “:” (without quotes) in the end of 4**th** line and put the path above of your respective system to get the direct render working!*
 *The file will be like this:*
 *File /etc/X11/Xsession.d/10fglrx for 64 bits (x86_64) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri * 
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
```*File /etc/X11/Xsession.d/10fglrx for 32 bits (x86) linux:*
 ```

 *LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri * 
 *if [ `uname -m` = 'x86_64' ]; then * 
 *  if [ -d /usr/lib32/fglrx/dri ]; then * 
 *    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri://usr/lib32/dri*
 *    if [ ! -z $LD_LIBRARY_PATH ]; then * 
 *    LD_LIBRARY_PATH=$LD_LIBRARY_PATH: * 
 *    fi * 
 *    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 * 
 *    export LD_LIBRARY_PATH * 
 *  fi * 
 *fi * 
 *export LIBGL_DRIVERS_PATH*
 
``` *then save the /etc/X11/Xsession.d/10fglrx (must have root privileges) and reboot your system*
 
*then glxinfo | egrep render*
 *and check it out if you'll have direct rendering!*
 *Voilà! Shaazaam! Works*
 
*I've got gnome-shell loading and working sweeeeeeeeeetly without video tearing!!! XBMC also are working sweeeeetly and without video tearing! Good bye cruel World!!!!*
 
*Can someone tell me if Unity 3D works?*

I would like to add few things here. 
First, in a 32 bit system, the command "uname -m" will give i686, so your hack will not work. 
Second I use Ubuntu/Precise, and there is no package like ia32-libs. I couldn't find any directory named /usr/lib32. 
But I found this directory though, "/usr/lib/i386-linux-gnu/". The solution for 32 bits system is that, edit the 1st line of "/etc/X11/Xsession.d/10fglrx" with proper destination which contains "swrast_dri.so" and "i915_dri.so". Use "locate" command to find these libraries.
So in my case "/etc/X11/Xsession.d/10fglrx" was edited as:
[I]LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/i386-linux-gnu/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
        LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH[/I]

After this I was able to run unity-3d. Hope this would save someone's time.

---

### Post by ubik89 on 2012-07-06
I'm an owner of Intel HD 3000/Radeon HD 6450M.

Switchable graphics works fine.

But how to get rid of tearing with the radeon card?

Anybody has an idea?

There is no "tear-free" option in Catalyst Control Manager.

---

### Post by Niccola on 2012-07-06
> **codeguru11 said:**
> I would like to add few things here. 
First, in a 32 bit system, the command "uname -m" will give i686, so your hack will not work. 
Second I use Ubuntu/Precise, and there is no package like ia32-libs. I couldn't find any directory named /usr/lib32. 
But I found this directory though, "/usr/lib/i386-linux-gnu/". The solution for 32 bits system is that, edit the 1st line of "/etc/X11/Xsession.d/10fglrx" with proper destination which contains "swrast_dri.so" and "i915_dri.so". Use "locate" command to find these libraries.
So in my case "/etc/X11/Xsession.d/10fglrx" was edited as:
[I]LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/i386-linux-gnu/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
        LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH[/I]

After this I was able to run unity-3d. Hope this would save someone's time.

You're absolutely right! But let me point some things in your observation:
1 - In 32bits Operating System you don't need to install ia32-libs. This package just provide a "multi-arch" support to 32bits libraries for a 64bits OS libraries.

2 - About the directory it's weird, because when I was in ubuntu 11.10 (when I posted it) the default path was /usr/lib/dri/i915_dri.so
As you can see in both packages.ubuntu.com (from 10.04, 11.10 and 12.04):
[10.04 LTS dri path]("http://packages.ubuntu.com/search?suite=lucid&section=all&arch=any&searchon=contents&keywords=i915_dri.so")
[11.10 dri path]("http://packages.ubuntu.com/search?suite=oneiric&arch=any&searchon=contents&keywords=i915_dri.so")
[12.04 LTS dri path]("http://packages.ubuntu.com/search?suite=precise&arch=any&searchon=contents&keywords=i915_dri.so")

As you can see in the links above, the dri path in 32 bits its the same as described in my first post. But seems that things changed in 11.10 (as you can see in second link).
First, it was installed by ia32-libs but after, in 11.10 it was ported to libgl1-mesa-dri package

My fault to don't see it! Sorry!

---

### Post by Niccola on 2012-07-06
New 12.6 driver released! Somebody tried it?

I'm with 12.6 beta and facing with a lot of problems! It's freaking me out!

I've read that 12.6 final release is worst than beta version.

Is somebody having problems with final release of 12.6 driver?

---

### Post by ubik89 on 2012-07-06
No problems with 12.6 final and Intel HD 3000/Radeon HD 6450M.

But I have to use this commands to switch:

```
sudo amdconfig --px-dgpu
```
(switch to discrete)

```
amdconfig --px-igpu
```
(switch to integrated)

---

### Post by Niccola on 2012-07-06
> **ubik89 said:**
> No problems with 12.6 final and Intel HD 3000/Radeon HD 6450M.

But I have to use this commands to switch:

```
sudo amdconfig --px-dgpu
```
(switch to discrete)

```
amdconfig --px-igpu
```
(switch to integrated)

You can't switch using amdcccle? Because I can't switch with 12.6 beta. I can't believe that this problem wasn't fixed!

---

### Post by ubik89 on 2012-07-06
No, switching with amdcccle doesn't work. It's freezing my system.

---

### Post by Niccola on 2012-07-08
> **ubik89 said:**
> No, switching with amdcccle doesn't work. It's freezing my system.

This is really strange. Coz I can switch from iGPU to dGPU but I cannot switch from dGPU to iGPU... probably something easy to figure out...

I'll get some time to find this problem

---

### Post by mohgabr on 2012-07-09
First, Thanks very much for the great tutorial and you efforts here in the thread
Second , I have a laptop hp probook 4530s with amd 6490 and intel 3000 I tried this tutorial and did it all step by step
my problem is after running 

> sudo aticonfig --initial -f
then restart Ubuntu runs in the low graphics mode and i must reconfigure the grahpics

also

> fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


---

### Post by Niccola on 2012-07-11
> **mohgabr said:**
> First, Thanks very much for the great tutorial and you efforts here in the thread
Second , I have a laptop hp probook 4530s with amd 6490 and intel 3000 I tried this tutorial and did it all step by step
my problem is after running 


then restart Ubuntu runs in the low graphics mode and i must reconfigure the grahpics

also

Who's having low graphics mode problem, please follow this steps:

1 - Post the following command output:
```
uname -a
```

2 - follow the [post #1]("http://ubuntuforums.org/showpost.php?p=12092664&postcount=1"), AND before install fglrx .deb files, execute the following command (must be executed inside fglrx .deb directory):
```
sudo dpkg -i fglrx*.deb >> fglrx_install.log 2>&1
```
OBS: The command above will create a file fglrx_install.log logging all std output and error output occurred during fglrx installation.

3 - post here the fglrx_install.log file content

IMPORTANT TIP: To post something in this thread and be clear to everyone read it, use CODE /CODE declaration inside brackets.
You can also use [pastebin]("http://pastebin.com/") to paste your code, output or command stuff there and just put your stuff pastebin URL here. like that:
uname -a output: [http://pastebin.com/eaLcXUGV](http://pastebin.com/eaLcXUGV)

Cheers

---

### Post by Niccola on 2012-07-13
Guys,
sorry but there's an error in my post [***_#107_***]("http://ubuntuforums.org/showpost.php?p=11819555&postcount=107"). Which, probably, will not work on 32-bits Linux. :oops:

The 32-bits dri driver path is wrong. However, now I'll post an 10fglrx fix that will work to 32 or 64 bits.

Before, make sure you have libgl1-mesa-dri installed. Without this package, you cannot have Intel direct rendering on 32 bits systems.

```
sudo apt-get install libgl1-mesa-dri
```

Now, just edit /etc/X11/Xsession.d/10fglrx (with super user permission)

```
sudo gedit /etc/X11/Xsession.d/10fglrx
```

REPLACE LINE 4 with code below:
```
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
```

AND ADD the code below between lines 11 and 12. (before export LIBGL_DRIVERS_PATH)
```
if [ `uname -m` = 'i686' ] | [ `uname -m` != 'x86_64' ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib/i386-linux-gnu/dri
fi
```

:!: VERIFY YOUR CHANGES BEFORE SAVING
Your file should looks like this:

```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
if [ `uname -m` = 'i686' ] | [ `uname -m` != 'x86_64' ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib/i386-linux-gnu/dri
fi
export LIBGL_DRIVERS_PATH
```

:!: VERIFY YOUR CHANGES BEFORE SAVING
Verify your changes, save and enjoy Direct Rendering in 32/64 bits OSs

voila!

You can download here all .deb files from amd Catalyst 12.6 final with 10fglrx fixed (ready to install).
 - This .deb files only works with 12.04 LTS Precise Ubuntu
 - I've add Kernel 3.4 support in this .deb files (for Ubuntu 12.04 LTS precise)
 - Fixed Intel direct rendering

Download:
for Ubuntu 12.04 LTS 64 bits: [amd-12-6-fixed-Niccola-amd64.tar.gz]("http://dl.dropbox.com/u/13977411/amd-driver/amd-12-6-fixed-Niccola-amd64.tar.gz")
for Ubuntu 12.04 LTS 32 bits: [amd-12-6-fixed-Niccola-i386.tar.gz]("http://dl.dropbox.com/u/13977411/amd-driver/amd-12-6-fixed-Niccola-i386.tar.gz")

Instructions:
1 - Extract inside a new and empty directory
```
tar -xvf amd-12-6-fixed-Niccola.tar.gz
```

2 - Install:
```
sudo dpkg -i fglrx*.deb
```

3 - Run automatic configuration for xorg.conf file:
```
sudo amdconfig --initial -f
```
Reboot your machine

4 - Switch to Intel Integrated Graphic Card:
```
sudo amdconfig --px-igpu
```
reboot your machine

5 - test Intel Direct Rendering:
```
glxinfo | egrep render
```

---

### Post by mohgabr on 2012-07-14
> **Niccola said:**
> Who's having low graphics mode problem, please follow this steps:

1 - Post the following command output:
```
uname -a
```

2 - follow the [post #1]("http://ubuntuforums.org/showpost.php?p=12092664&postcount=1"), AND before install fglrx .deb files, execute the following command (must be executed inside fglrx .deb directory):
```
sudo dpkg -i fglrx*.deb >> fglrx_install.log 2>&1
```
OBS: The command above will create a file fglrx_install.log logging all std output and error output occurred during fglrx installation.

3 - post here the fglrx_install.log file content

IMPORTANT TIP: To post something in this thread and be clear to everyone read it, use CODE /CODE declaration inside brackets.
You can also use [pastebin]("http://pastebin.com/") to paste your code, output or command stuff there and just put your stuff pastebin URL here. like that:
uname -a output: [http://pastebin.com/eaLcXUGV](http://pastebin.com/eaLcXUGV)

Cheers

Hi , thanks for your efforts
And here is my output:

```

$ uname -a
Linux MohGabr-Ubuntu 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

```

about the other thing I removed the old packages and can't generate them again using :
```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```
it gives me this error
```

.
.
.
.
.
.
.
.
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.dL7xtG

```

I will try to rebuild the packages again

---

### Post by Niccola on 2012-07-14
> **mohgabr said:**
> Hi , thanks for your efforts
And here is my output:

```

$ uname -a
Linux MohGabr-Ubuntu 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

```

about the other thing I removed the old packages and can't generate them again using :
```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```
it gives me this error
```

.
.
.
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.dL7xtG

```

I will try to rebuild the packages again

I don't know what's happen with this information you give me. But in this step you probably miss some packages installation.

try it:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4 libgl1-mesa-dri
```

and after, download it to an empty directory:
[amd-12-6-fixed-Niccola-i386.tar.gz](http://dl.dropbox.com/u/13977411/amd-driver/amd-12-6-fixed-Niccola-i386.tar.gz)

then execute following command, such that is post [***_#357_***]("http://ubuntuforums.org/showpost.php?p=12101640&postcount=359"):
Instructions:
1 - Extract inside a new and empty directory
```
tar -xvf amd-12-6-fixed-Niccola.tar.gz
```
2 - Install:
```
sudo dpkg -i fglrx*.deb
```
3 - Run automatic configuration for xorg.conf file:
```
sudo amdconfig --initial -f
```
Reboot your machine

4 - Switch to Intel Integrated Graphic Card:
```
sudo amdconfig --px-igpu
```
reboot your machine

5 - test Intel Direct Rendering:
```
glxinfo | egrep render
```

---

### Post by roudy1989 on 2012-07-14
First of all I have to say thanks. I am following this thread since a long time and it was helping me a lot to get the switchable graphics working for my Samsung.

**Samsung Series 7 Chronos 700Z3A-SO2de**, Intel HD 3000, AMD 6490m, HDMI Intel/AMD not tested/not tested, Mini DisplayPort Intel/AMD not testes/not tested

Nevertheless there are still issues to fix. The laptop has been under linux always a little bit hotter than under windows. I had activated the integrated graphics card. But the dedicated seems to be online thought. Today I activated the dedicated and now the used power seems to be dropped by 0.5 to 1W and the temperature of the air coming out of the laptop seems to be lower.

Does anyone made the same observation? Maybe the fglrx driver does'nt set the dedicated graphics card into a very low power mode when the integrated graphics card is chosen.

---

### Post by mohgabr on 2012-07-14
> **Niccola said:**
> 
Instructions:
1 - Extract inside a new and empty directory
```
tar -xvf amd-12-6-fixed-Niccola.tar.gz
```
2 - Install:
```
sudo dpkg -i fglrx*.deb
```
3 - Run automatic configuration for xorg.conf file:
```
sudo amdconfig --initial -f
```
Reboot your machine

4 - Switch to Intel Integrated Graphic Card:
```
sudo amdconfig --px-igpu
```
reboot your machine

5 - test Intel Direct Rendering:
```
glxinfo | egrep render
```

Thanks for your great efforts I think it worked now
I have downloaded your fixed packages
and here is the output :
1- The installation log file fglrx_install.log : [http://pastebin.com/r8dipgCA](http://pastebin.com/r8dipgCA)

2- ```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11733 Compatibility Profile Context

```

3- ```
$ glxinfo | egrep render
direct rendering: Yes
OpenGL renderer string: AMD Radeon HD 6400M Series
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 

```

But the switching not working
```

$ sudo amdconfig --px-igpu
No layout section was found in the file: 'xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
amdconfig: parsing the command-line failed.

```

---

### Post by slowtrain on 2012-07-14
I tried to use these instructions to install the new Catalyst 12.6, which should be appropriate for my Radeon HD 6700M graphics processor.  

On a first run-through, X11 fails to work and I need to replace my xorg.conf file with a backup to get a graphic desktop again.

Looking through the installation output, I see lines such as the following with warnings:

update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

So, I tried installing opencl by adding the packages opencl-headers and python-pyopencl.

I now see a file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd .  I'm not sure whether this file was there before my attempted addition of OpenCL because I hadn't checked.

Anyway, I was going to test the new setup, so I uninstalled fglrx and then reinstalled. but when I try the line "sudo amdconfig --initial -f", I get "amdconfig: command not found".  

Looks like I scrambled something badly when I uninstalled fglrx earlier.  According to my locate database, there was previously an amdconfig command in /usr/bin.  It's no longer there.  There's also one under /user/lib/fglrx/bin.  I've tried running that by going to the directory and using sudo ./amdconfig --initial -f .  I get "Unable to open /etc/ati/control, please reinstall the driver."  I've reinstalled the driver 3 times and still get that error.  Have also tried the directions at the following link for fixing the problem, but it doesn't help:  [http://phoronix.com/forums/showthread.php?25866-Catalyst-10-8-fails-to-install-completely-on-lucid](http://phoronix.com/forums/showthread.php?25866-Catalyst-10-8-fails-to-install-completely-on-lucid) .

Anyway, looks like I can't test the new installation.  The dpkg command still gives a warning:  "update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-current/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken."

---

### Post by Niccola on 2012-07-15
> **mohgabr said:**
> Thanks for your great efforts I think it worked now
I have downloaded your fixed packages
and here is the output :
1- The installation log file fglrx_install.log : [http://pastebin.com/r8dipgCA](http://pastebin.com/r8dipgCA)

2- ```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11733 Compatibility Profile Context

```

3- ```
$ glxinfo | egrep render
direct rendering: Yes
OpenGL renderer string: AMD Radeon HD 6400M Series
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 

```

But the switching not working
```

$ sudo amdconfig --px-igpu
No layout section was found in the file: 'xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
amdconfig: parsing the command-line failed.

```

Ok, nice to know. No errors were found in your fglrx installation. 

you can solve last error running the command below:
```
sudo aticonfig --initial -f
```
and post it's output

then try to switch between graphic cards


> **slowtrain said:**
> I tried to use these instructions to install the new Catalyst 12.6, which should be appropriate for my Radeon HD 6700M graphics processor.  

On a first run-through, X11 fails to work and I need to replace my xorg.conf file with a backup to get a graphic desktop again.

Looking through the installation output, I see lines such as the following with warnings:

update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.

So, I tried installing opencl by adding the packages opencl-headers and python-pyopencl.

I now see a file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd .  I'm not sure whether this file was there before my attempted addition of OpenCL because I hadn't checked.

Anyway, I was going to test the new setup, so I uninstalled fglrx and then reinstalled. but when I try the line "sudo amdconfig --initial -f", I get "amdconfig: command not found".  

Looks like I scrambled something badly when I uninstalled fglrx earlier.  According to my locate database, there was previously an amdconfig command in /usr/bin.  It's no longer there.  There's also one under /user/lib/fglrx/bin.  I've tried running that by going to the directory and using sudo ./amdconfig --initial -f .  I get "Unable to open /etc/ati/control, please reinstall the driver."  I've reinstalled the driver 3 times and still get that error.  Have also tried the directions at the following link for fixing the problem, but it doesn't help:  [http://phoronix.com/forums/showthread.php?25866-Catalyst-10-8-fails-to-install-completely-on-lucid](http://phoronix.com/forums/showthread.php?25866-Catalyst-10-8-fails-to-install-completely-on-lucid) .

Anyway, looks like I can't test the new installation.  The dpkg command still gives a warning:  "update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-current/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken."

First of all...
Don't need to worry about update-alternatives warnings, it's not errors... just warnings. It's happens with everybody.

You just have to install OpenCL if you'll use your card for OpenCL purposes. It's not really necessary

I have same card than you 6700M series (mine is an 6770M)
however...

You probably corrupted files or pissed off in fglrx-system files and also your environment variables. I really recommend you to try again the first post #1 executing all commands again.

I really recommend, also, to uninstall OpenCL if you'll not use it. It's not necessary. But you can keep if you want to...

seems like amdconfig was added in last updates, so you can try to run aticonfig rather than amdconfig.

---

### Post by Niccola on 2012-07-15
> **roudy1989 said:**
> First of all I have to say thanks. I am following this thread since a long time and it was helping me a lot to get the switchable graphics working for my Samsung.

**Samsung Series 7 Chronos 700Z3A-SO2de**, Intel HD 3000, AMD 6490m, HDMI Intel/AMD not tested/not tested, Mini DisplayPort Intel/AMD not testes/not tested

Nevertheless there are still issues to fix. The laptop has been under linux always a little bit hotter than under windows. I had activated the integrated graphics card. But the dedicated seems to be online thought. Today I activated the dedicated and now the used power seems to be dropped by 0.5 to 1W and the temperature of the air coming out of the laptop seems to be lower.

Does anyone made the same observation? Maybe the fglrx driver does'nt set the dedicated graphics card into a very low power mode when the integrated graphics card is chosen.

I am experiencing the opposite than you. The fglrx driver really cool down my temperatures and computer noise. Before fglrx the opensource driver makes my laptop scream as crazy and temperatures goes higher than 90°C

You should verify if your laptop is muxless or muxed. It really makes differences in this case.

---

### Post by roudy1989 on 2012-07-15
> **Niccola said:**
> I am experiencing the opposite than you. The fglrx driver really cool down my temperatures and computer noise. Before fglrx the opensource driver makes my laptop scream as crazy and temperatures goes higher than 90°C

You should verify if your laptop is muxless or muxed. It really makes differences in this case.

It does cool down my laptop, too. I have now 56°C on CPU and GPU.
When I switch to integrated graphics card I cannot see the temperature of the dedicated graphics card anymore (aticonfig --odgt) but the temperature of the integrated card is slightly higher at ~60°C.

This laptop is muxless. I think every laptop which use PowerXPress 4.0 (or higher) is muxless, if I am informed right.

---

### Post by slowtrain on 2012-07-15
Hi Niccola:  Thanks for letting me know that the OpenCL software isn't needed.  Best not to have useless software clogging my system.  I've removed it (it did create some problems by installing nvidia-current, which seems to block any access to the GPU).

I did a clean install of the first additional driver that Ubuntu wants to add (not the post-release one).  This added the /usr/bin/amdconfig cmd back into my system.  Am guessing I can now use that command (or aticonfig).

Not really sure that repeating the instructions will make a difference--I've already gone through them at least 3 times, always with the effect of making X11 inaccessible.  If the problem isn't in the warnings, then I don't know what else to do to make this work.  Oddly, AMD seems to think that the 12.6 Catalyst driver should do the trick.  Maybe I'll give it one more try.

Thanks!

---

### Post by slowtrain on 2012-07-15
Well, tickle me pink, this time going through the instructions, Catalyst seems to have installed properly!

Powertop reports, at times, lower wattage used than I've ever seen before, but the power use is more variable, with rather high rates periodically.  So am not sure this is overall a power saving--will have to test some more.  

One thing that would be handy would be a way to switch between dual graphics and just the low-power intel chip.  The Catalyst Control Center (sudoed) allows such a switch, but the last time I used it, graphics simply wouldn't work on the system and I had to reinstall the system.  Maybe that's because Catalyst wasn't properly installed, but it would be nice if there were some way to use the command line to switch the original configuration file back if graphics get nuked.  

Problem is, I can't seem to find a config file for the Control Center.  Anyone have any ideas how to find that?

---

### Post by Niccola on 2012-07-15
> **roudy1989 said:**
> It does cool down my laptop, too. I have now 56°C on CPU and GPU.
When I switch to integrated graphics card I cannot see the temperature of the dedicated graphics card anymore (aticonfig --odgt) but the temperature of the integrated card is slightly higher at ~60°C.

This laptop is muxless. I think every laptop which use PowerXPress 4.0 (or higher) is muxless, if I am informed right.

Of course you can't see temperature when using integrated graphics: because de discrete one is "turned off"!

So, I put quotes in turned off by purposely, because in a muxless system, the switch is controlled by software in higher level. So, you can turn on again your discrete just running amdconfig command and restart your X server, and voila, the discrete graphic card is on again.

You can interpret it like the graphic card is not totally turned off, because your command send a signal to turn on the discrete GPU, and it turn on without reboot your operating system.

I really disagree with you saying that GPU in windows is colder than linux, because on Windows you have a software which manage applications that will use your dGPU. In linux, or you use dGPU or iGPU in each session, in this way, you have a colder system.

But, I've figured out that if you run amdconfig command you turn on your dGPU again for a while. Doesn't matter if you use it or not. That's the proof that you switch by high-level software in OS. If you kill the amdconfig command running, after a while the dGPU is turned off again (if you're using iGPU and just execute amdconfig to do anything).

In fact, the driver runs over Xorg management, if you want to run fglrx driver just change xorg.conf driver statement to "fglrx", if you want to use intel just change statement to "intel" and, of course, restart X. We can conclude that both graphic cards doesn't turn off completely, but, it draws little energy (just like in stand by mode)

So, I don't know whats your point or what you mean. Just clarify your question, please.

---

### Post by Niccola on 2012-07-15
> **slowtrain said:**
> Hi Niccola:  Thanks for letting me know that the OpenCL software isn't needed.  Best not to have useless software clogging my system.  I've removed it (it did create some problems by installing nvidia-current, which seems to block any access to the GPU).

I did a clean install of the first additional driver that Ubuntu wants to add (not the post-release one).  This added the /usr/bin/amdconfig cmd back into my system.  Am guessing I can now use that command (or aticonfig).

Not really sure that repeating the instructions will make a difference--I've already gone through them at least 3 times, always with the effect of making X11 inaccessible.  If the problem isn't in the warnings, then I don't know what else to do to make this work.  Oddly, AMD seems to think that the 12.6 Catalyst driver should do the trick.  Maybe I'll give it one more try.

Thanks!

What the hell! Why did you install nvidia-settings in your system? It increase the possibility to you clogging your system

after uninstall some driver or program I really recommend to execute sudo apt-get autoremove to clean old (not needded) dependencies. So you could execute this command and after repeat post #1 over again. (forcing reinstallation of each package)

> **slowtrain said:**
> Well, tickle me pink, this time going through the instructions, Catalyst seems to have installed properly!

Powertop reports, at times, lower wattage used than I've ever seen before, but the power use is more variable, with rather high rates periodically.  So am not sure this is overall a power saving--will have to test some more.  

One thing that would be handy would be a way to switch between dual graphics and just the low-power intel chip.  The Catalyst Control Center (sudoed) allows such a switch, but the last time I used it, graphics simply wouldn't work on the system and I had to reinstall the system.  Maybe that's because Catalyst wasn't properly installed, but it would be nice if there were some way to use the command line to switch the original configuration file back if graphics get nuked.  

Problem is, I can't seem to find a config file for the Control Center.  Anyone have any ideas how to find that?

Good to know you take back amdconfig. But, what you mean about Powertop?

Do you know that catalyst control center (amdcccle) it's not working properly to switch between graphic cards? System is hanging on and crashing for a while. To switch between dgpu and igpu graphic cards you must run by command line:

```
sudo amdconfig --px-igpu
```
to switch to integrated GPU
or

```
sudo amdconfig --px-dgpu
```
to switch to discrete GPU

can you post the specification of your computer?

---

### Post by slowtrain on 2012-07-15
Hi Niccola:

Again, thanks for the info, though that had some adverse effects for me (see below).

Some info I acquired on power usage with Catalyst.  I had run a test earlier without Catalyst in which I turned on only Chrome and ran a particular Hulu flash video for 30 minutes, collecting information on percent of battery power left at 15 minutes and every 5 minutes thereafter to 30 minutes.  Using a simple linear regression, I can predict, likely with good accuracy given the neat linear fit of the data, how many minutes of total battery life I could expect.  Without Catalyst, I could expect 153 minutes, but with Catalyst (in dual graphics mode) I could expect 138 minutes.  That's comparable to Win 7 (on the same machine), which had a predicted value of 132 minutes.  I guess it shouldn't be surprising that having something that occasionally checks in with a more power-consuming chip will use more power.  Of course, running a flash video in Hulu is not to be compared with, e.g., trying to run something more graphics-intensive.  It's just that I fairly rarely use more graphics intensive software.  Also, from what I saw in powertop (a program that calculates wattage used), the wattage used by the machine when Catalyst is switched to integrated graphics only seems lower than what I've seen without Catalyst (but with a bad install of fglrx from Additional Drivers that seems to block the GPU from running continuously at maximum).

Ok, so to more harrowing info.  I can't clearly remember if I've ever, in the past couple months of my Ubuntu install, had the system hang on suspend.  After installing Catalyst using the instructions here (both Steps 1 & 2), the system hung on the first suspect (the screen froze, I couldn't switch to a terminal, power consumption went to max, I had to hard shut down the computer).  I then undid Step 2 in the instructions above because it's not clear to me what this accomplishes and I was hoping the suspend problem would clear up.  That worked for about 3 suspends, after which that hung.

I nevertheless held out hope that perhaps the problem would go away if I had Catalyst switched to integrated graphics using sudo amdconfig --px-igpu, as you suggested.  This worked for a few minutes, then the system hung without even a suspend.  I subsequently could boot into neither the GUI or a command line.  Had to use Win 7 (on another partition) to swap to my original xorg.conf file so I could boot into Ubuntu.  Maybe this setup is stable now--it does seem to be using somewhat less power than my system w/o Catalyst.

Anyway, it does seem that Catalyst makes my system unstable, and that may be helpful to know for others out there experimenting with this.  My hardware is:

HP Pavilion dv6t
Intel Core i7-2720QM CPU @ 2.2GHz
Graphics:  Radeon HD 6770M

---

### Post by jkn83 on 2012-07-15
hey guys i am having trouble setting up my switchable graphics card for my hp dv6-3143us i am running 12.04 and everytime i do a manual update with teh ati 12-6.x86 driver i reboot only to find im in low graphics mode!  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834157466](http://www.newegg.com/Product/Product.aspx?Item=N82E16834157466)

I have switchable intel with ati 5650 mobility radeon...

what i am trying to do is get startx running because i am trying to do android development within eclipse...i cant create AVD device without my video driver being correctly installed...or at least startx being able to run under either intel or AMD...i get the badrequest error whenever i try to start my AVD device...really annoying 

i have tried the guide posted and i end up restarting getting low graphic mode and having to reinstall my whole linux after several re-installs i realized i could just rm /etc/R11/xorg.conf 

i am about to try this method...
[http://forums.gentoo.org/viewtopic-t-881115.html?sid=f0f64d4f635cf5fa1bef8b54d1dc9b70](http://forums.gentoo.org/viewtopic-t-881115.html?sid=f0f64d4f635cf5fa1bef8b54d1dc9b70)
but really unsure on what the hell i should do

i dont know if you guys can recommend anything i have tried the wikilinux guide and this guide and still end up getting into low graphics mode after removing fglrx and manually installing the new 12-6.x86 drivers

when i do a clean install of ubuntu 12.04 /etc/X11/xorg.conf doesnt even exist. Xorg.conf is created when 12-6.x86 ati driver installed but when I reboot i enter low graphics mode and end up pissed that I wasted another hour of my life trying to get this to work

when i do a clean install everyhting loads up fine i have video - i go to additional drivers and install fglrx now just because it is the safest way for me to get the driver installed...however as you all know this is not switchable... i still get the bad request error whenever i try to start my AVD device within eclipse because my video driver is not set up correctly and i believe startx doesnt start propertly


i have a clean install of 12.04 ubuntu and fglrx drivers installed through additional drivers
below is some info about my system

ME# startx
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 1.4 (2.1 Mesa 8.0.2)

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

/etc/X11$ dir
app-defaults         rgb.txt  xorg.conf   Xsession cursors             X      Xreset      Xsession.d
default-display-manager  xinit      Xreset.d    Xsession.options fonts             xkb      Xresources  Xwrapper.config

i have tried a couple methods to get it to work and keep failing on my install
so going to post here -  Keep in mind i have gone through the manual install multiple times for the 12-6.x86 driver and then get to the end where i sudo aticonfig -whatever and then i reboot in low graphics mode everytime! <=hate to see this
i have a clean install of 12.04 ubuntu and fglrx drivers installed through additional drivers

what method should i use to get startx to work

---

### Post by roudy1989 on 2012-07-16
> **Niccola said:**
> Of course you can't see temperature when using integrated graphics: because de discrete one is "turned off"!

So, I put quotes in turned off by purposely, because in a muxless system, the switch is controlled by software in higher level. So, you can turn on again your discrete just running amdconfig command and restart your X server, and voila, the discrete graphic card is on again.

You can interpret it like the graphic card is not totally turned off, because your command send a signal to turn on the discrete GPU, and it turn on without reboot your operating system.

I really disagree with you saying that GPU in windows is colder than linux, because on Windows you have a software which manage applications that will use your dGPU. In linux, or you use dGPU or iGPU in each session, in this way, you have a colder system.

But, I've figured out that if you run amdconfig command you turn on your dGPU again for a while. Doesn't matter if you use it or not. That's the proof that you switch by high-level software in OS. If you kill the amdconfig command running, after a while the dGPU is turned off again (if you're using iGPU and just execute amdconfig to do anything).

In fact, the driver runs over Xorg management, if you want to run fglrx driver just change xorg.conf driver statement to "fglrx", if you want to use intel just change statement to "intel" and, of course, restart X. We can conclude that both graphic cards doesn't turn off completely, but, it draws little energy (just like in stand by mode)

So, I don't know whats your point or what you mean. Just clarify your question, please.

Okay. The system is muxless. As you said, the GPU switching is controlled by software and either one is used while the other one is set into low power mode.
Thus, it should be following:
* Using the integrated graphics card, the consumed power should be less then using the dedicated graphics card.
* Using the integrated graphics card should make the system being cooler than using the dedicated graphics card.

But that is not the point. Actually (under normal load), the system uses same amount of power independent to which graphics card is used. This implies, that using the integrated graphics card, the dedicated graphics card is **NOT** set into very low power mode properly (aticonfig --odgc shows the core is in 100Mhz and the memory is in 150Mhz current clock speed, using the dedicated graphics card). So there are power states in which the dedicated graphics card can be set. But since it has now - using the dedicated graphics card - a lower temperature I can imply nothing than it does not work properly when using the integrated graphics card.

While under Windows, where both cards are active, there is much lesser heat (it is actually no real heat - more "warmer" than Windows ;) ) coming out of the laptop while idling / normal load.

I hope it is now clear enough what I wanted to tell you.

Cheers.

---

### Post by Niccola on 2012-07-16
> **slowtrain said:**
> Hi Niccola:

Again, thanks for the info, though that had some adverse effects for me (see below).

Some info I acquired on power usage with Catalyst.  I had run a test earlier without Catalyst in which I turned on only Chrome and ran a particular Hulu flash video for 30 minutes, collecting information on percent of battery power left at 15 minutes and every 5 minutes thereafter to 30 minutes.  Using a simple linear regression, I can predict, likely with good accuracy given the neat linear fit of the data, how many minutes of total battery life I could expect.  Without Catalyst, I could expect 153 minutes, but with Catalyst (in dual graphics mode) I could expect 138 minutes.  That's comparable to Win 7 (on the same machine), which had a predicted value of 132 minutes.  I guess it shouldn't be surprising that having something that occasionally checks in with a more power-consuming chip will use more power.  Of course, running a flash video in Hulu is not to be compared with, e.g., trying to run something more graphics-intensive.  It's just that I fairly rarely use more graphics intensive software.  Also, from what I saw in powertop (a program that calculates wattage used), the wattage used by the machine when Catalyst is switched to integrated graphics only seems lower than what I've seen without Catalyst (but with a bad install of fglrx from Additional Drivers that seems to block the GPU from running continuously at maximum).

Ok, so to more harrowing info.  I can't clearly remember if I've ever, in the past couple months of my Ubuntu install, had the system hang on suspend.  After installing Catalyst using the instructions here (both Steps 1 & 2), the system hung on the first suspect (the screen froze, I couldn't switch to a terminal, power consumption went to max, I had to hard shut down the computer).  I then undid Step 2 in the instructions above because it's not clear to me what this accomplishes and I was hoping the suspend problem would clear up.  That worked for about 3 suspends, after which that hung.

I nevertheless held out hope that perhaps the problem would go away if I had Catalyst switched to integrated graphics using sudo amdconfig --px-igpu, as you suggested.  This worked for a few minutes, then the system hung without even a suspend.  I subsequently could boot into neither the GUI or a command line.  Had to use Win 7 (on another partition) to swap to my original xorg.conf file so I could boot into Ubuntu.  Maybe this setup is stable now--it does seem to be using somewhat less power than my system w/o Catalyst.

Anyway, it does seem that Catalyst makes my system unstable, and that may be helpful to know for others out there experimenting with this.  My hardware is:

HP Pavilion dv6t
Intel Core i7-2720QM CPU @ 2.2GHz
Graphics:  Radeon HD 6770M

That's weird because I have the same system than you (an HP pavilion, but mine is dv6 with i7-2670QM and we have the same video dard) and I am not experiencing anything like this.

Actually I was experiencing something like you described using Ubuntu 12.04 with gnome-shell days ago, are you using gnome-shell? if yes, post the following commands output:
```
gnome-shell --version
```

and:
```
uname -a
```

---

### Post by Niccola on 2012-07-16
jkn83 and roudy1989,
following things will be recommended for both of you. Particular things you should read individually quote scope:

Well,
I think both of you should first update your BIOS to latest version. After that, check the Dynamic Video Option in BIOS Setup. If present, you should put in Dynamic mode (to switch between cards) and NOT in FIXED mode (to keep always discrete GPU on)

sure that you made it completely, read your particular things:

> **jkn83 said:**
> hey guys i am having trouble setting up my switchable graphics card for my hp dv6-3143us i am running 12.04 and everytime i do a manual update with teh ati 12-6.x86 driver i reboot only to find im in low graphics mode!  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834157466](http://www.newegg.com/Product/Product.aspx?Item=N82E16834157466)

I have switchable intel with ati 5650 mobility radeon...

what i am trying to do is get startx running because i am trying to do android development within eclipse...i cant create AVD device without my video driver being correctly installed...or at least startx being able to run under either intel or AMD...i get the badrequest error whenever i try to start my AVD device...really annoying 

i have tried the guide posted and i end up restarting getting low graphic mode and having to reinstall my whole linux after several re-installs i realized i could just rm /etc/R11/xorg.conf 

i am about to try this method...
[http://forums.gentoo.org/viewtopic-t-881115.html?sid=f0f64d4f635cf5fa1bef8b54d1dc9b70](http://forums.gentoo.org/viewtopic-t-881115.html?sid=f0f64d4f635cf5fa1bef8b54d1dc9b70)
but really unsure on what the hell i should do

i dont know if you guys can recommend anything i have tried the wikilinux guide and this guide and still end up getting into low graphics mode after removing fglrx and manually installing the new 12-6.x86 drivers

when i do a clean install of ubuntu 12.04 /etc/X11/xorg.conf doesnt even exist. Xorg.conf is created when 12-6.x86 ati driver installed but when I reboot i enter low graphics mode and end up pissed that I wasted another hour of my life trying to get this to work

when i do a clean install everyhting loads up fine i have video - i go to additional drivers and install fglrx now just because it is the safest way for me to get the driver installed...however as you all know this is not switchable... i still get the bad request error whenever i try to start my AVD device within eclipse because my video driver is not set up correctly and i believe startx doesnt start propertly


i have a clean install of 12.04 ubuntu and fglrx drivers installed through additional drivers
below is some info about my system

ME# startx
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 1.4 (2.1 Mesa 8.0.2)

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

/etc/X11$ dir
app-defaults         rgb.txt  xorg.conf   Xsession cursors             X      Xreset      Xsession.d
default-display-manager  xinit      Xreset.d    Xsession.options fonts             xkb      Xresources  Xwrapper.config

i have tried a couple methods to get it to work and keep failing on my install
so going to post here -  Keep in mind i have gone through the manual install multiple times for the 12-6.x86 driver and then get to the end where i sudo aticonfig -whatever and then i reboot in low graphics mode everytime! <=hate to see this
i have a clean install of 12.04 ubuntu and fglrx drivers installed through additional drivers

what method should i use to get startx to work

First of all, to solve your android stuff you should ask for it in another topic, not in a GPU topic. Ok? Could it be related? Yes! But there are also more people with low graphic mode that already solved this problem, so, if you look for this solution in this topic, you'll probably find it!

and about this topic from gentoo: forget it! Just follow faithfully this thread (mainly the #1 post) and you get your graphic cards switch working.

Appears that you didn't read this topic. So stop looking to another forums and go to post #1, follow instructions at first post carefully and you'll get your graphic card working.

If not, read my post #357 and follow instructions there. There are instructions to get information about your system related with GPU. Your Android Virtual Device will not solve your GPU problem.

What **** me off is guys that want quick answer before (or without) understand what's going on. So, RTFM post #1

> **roudy1989 said:**
> Okay. The system is muxless. As you said, the GPU switching is controlled by software and either one is used while the other one is set into low power mode.
Thus, it should be following:
* Using the integrated graphics card, the consumed power should be less then using the dedicated graphics card.
* Using the integrated graphics card should make the system being cooler than using the dedicated graphics card.

But that is not the point. Actually (under normal load), the system uses same amount of power independent to which graphics card is used. This implies, that using the integrated graphics card, the dedicated graphics card is **NOT** set into very low power mode properly (aticonfig --odgc shows the core is in 100Mhz and the memory is in 150Mhz current clock speed, using the dedicated graphics card). So there are power states in which the dedicated graphics card can be set. But since it has now - using the dedicated graphics card - a lower temperature I can imply nothing than it does not work properly when using the integrated graphics card.

While under Windows, where both cards are active, there is much lesser heat (it is actually no real heat - more "warmer" than Windows ;) ) coming out of the laptop while idling / normal load.

I hope it is now clear enough what I wanted to tell you.

Cheers.

I'ts really weird that but I'm sure that if you update your BIOS, and set DYNAMIC mode in BIOS setup you'll make it works properly.

after that, test if work switching between graphic cards

---

### Post by roudy1989 on 2012-07-16
> **Niccola said:**
> I'ts really weird that but I'm sure that if you update your BIOS, and set DYNAMIC mode in BIOS setup you'll make it works properly.

after that, test if work switching between graphic cards
My BIOS is at the latest version. I cannot set anything related to the graphics card in my BIOS.

But I think at the moment it is okay as it is. I got 40 minutes less working time now than in Windows. That is quite okay. It is still at 5 hours and more.

Hopefully the driver will be getting better in the future. And then, when the Sandy Bridge CPUs will have better support either (with Ubuntu 12.10 and Linux 3.5/3.6) there will be everything fine ;)

---

### Post by jkn83 on 2012-07-16
Niccola I tried rverything in post 1 then reboot into low graphics mode.  i found this topic to be the most related to my problem so i posted here...there are 38 pages in this thread so i am trying to go back and dig through everything everybody posted but it takes time...so i just posted my issue here...

I am going to try to update my BIOS when I get home today...I thought i had updated too all the latest windows drivers when i was running windows 7 a couple months ago...if i already do have an up-to-date bios i guess i would beable to change the settings in my bios...so i am going to start there

if i dont have an updated bios i am going to try this when i get home from work today...
[http://www.ehow.com/how_7256759_update-bios-ubuntu.html](http://www.ehow.com/how_7256759_update-bios-ubuntu.html)
[http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/](http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/)

---

### Post by Niccola on 2012-07-16
> **roudy1989 said:**
> My BIOS is at the latest version. I cannot set anything related to the graphics card in my BIOS.

But I think at the moment it is okay as it is. I got 40 minutes less working time now than in Windows. That is quite okay. It is still at 5 hours and more.

Hopefully the driver will be getting better in the future. And then, when the Sandy Bridge CPUs will have better support either (with Ubuntu 12.10 and Linux 3.5/3.6) there will be everything fine ;)

I've figured out that people owning Samsung Series 7 Chronos are facing with switch problem both on Windows and Linux. That's bad! Seems a samsung design problem. What you can do is contact support and ask for a new bios release with Switchable Graphic option, and wait.

but you can have more try to improve your experience installing newer versions of ubuntu 12.04 kernel (I know that the last stable kernel release is 3.4.0 I am using right now and for me is the best one...) if you want to try this out send me an MP and I can send you a tutorial step by step

> **jkn83 said:**
> Niccola I tried rverything in post 1 then reboot into low graphics mode.  i found this topic to be the most related to my problem so i posted here...there are 38 pages in this thread so i am trying to go back and dig through everything everybody posted but it takes time...so i just posted my issue here...

I am going to try to update my BIOS when I get home today...I thought i had updated too all the latest windows drivers when i was running windows 7 a couple months ago...if i already do have an up-to-date bios i guess i would beable to change the settings in my bios...so i am going to start there

if i dont have an updated bios i am going to try this when i get home from work today...
[http://www.ehow.com/how_7256759_update-bios-ubuntu.html](http://www.ehow.com/how_7256759_update-bios-ubuntu.html)
[http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/](http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/)

You have same brand and series laptop than me, I am absolutely sure that you have latest BIOS update to install. And after update, you'll be able to select DYNAMIC mode in Switchable Graphic Mode in BIOS.

TIP: DYNAMIC mode means that you will switch between Cards constantly, if you want to use your iGPU and/or GPU or switch between them, you have to select DYNAMIC option. Dynamic option you have better low-power consumption, but dGPU performance for OpenGL features aren't max as in FIXED mode:

FIXED option means that you want to use just GPU with its full feature. This option provides better and full OpenGL features in linux (I dont know about windows) for HP, and it improves dGPU performance (but I think just for OpenGL features).
**** FIXED method is very dangerous in linux if you forgot or don't set the driver as fglrx (selecting your dGPU) and may cause system instability, hangs and crashes (seg. faults, etc...) and also increase power usage.
You should select FIXED just if you will use dGPU and have previously switched to it by amdconfig command.

I always keep my BIOS configuration in DYNAMIC, because I don't game. If you are a game guy and you are playing a heavy game, you should switch to dGPU, reboot your system into BIOS and select FIXED mode. Of course it will drain more power and your battery will ends fast. So, you have to make the choice depending your usage

Don't try to update your bios by linux. It's not safety and I don't recommend this. Just do it if your manufacturer have BIOS update tools for linux. Otherwise, don't follow not trusted tutorial. If you don't have Windows available to update your BIOS, read [this thread]("http://askubuntu.com/questions/25129/updating-hp-pavilion-bios-from-linux").

But, trust me, this not work for every hardware. BE careful updating your BIOS, you can kill your pc

---

### Post by slowtrain on 2012-07-17
My system seems stable with Catalyst installed but the original xorg.conf in place.  This is a good setup for me because it seems to be using somewhat less power (no idea why) and, when I want to use something more graphics intensive without the processor running full-blast, I can just swap in the xorg.conf file for Catalyst & reboot.  I do have to avoid suspend in the latter case because it has that 'freezing' problem.

---

### Post by Niccola on 2012-07-18
> **slowtrain said:**
> My system seems stable with Catalyst installed but the original xorg.conf in place.  This is a good setup for me because it seems to be using somewhat less power (no idea why) and, when I want to use something more graphics intensive without the processor running full-blast, I can just swap in the xorg.conf file for Catalyst & reboot.  I do have to avoid suspend in the latter case because it has that 'freezing' problem.

What did you changed in xorg.conf versions you have?

I'm also using original xorg.conf file generated by amdconfig --initial -f command

But just it, I didn't change it to another xorg.conf file. I'll check if suspend problem happens with me...

---

### Post by mohgabr on 2012-07-18
```

$ sudo amdconfig --px-igpu
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.

PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!


```

now I have this result
I don't know how to restart the X server so i will try to reboot

After rebooting

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 3.0 Mesa 8.0.2


```
I think it is working well now

---

### Post by jkn83 on 2012-07-18
Finally updated my BIOS.  I do not see a dynamic mode in the BIOS options where are you guys seeing this option?  

i am running a dv6-3143us and hit esc on boot

Please help! =)

---

### Post by streetdaddy on 2012-07-19
Thanks Alexislavie, worked for me!

**Sony VAIO VPCSE2C5E** Intel HD 3000, AMD 6600m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working

A few notes:

[LIST=1]
[*]The first time I tried the step ```
sudo aticonfig --initial -f
``` I received the message ```
aticonfig: No supported adapters detected
```_However, after a reboot it worked_.


[*]Regarding *HDMI Intel/AMD: not tested/not tested* ... I'm using a second 27" monitor connected via the HDMI port, and it's working for both Discrete and Integrated, so perhaps that means it is in fact *working/working*?
[/LIST]

Thanks again ... very happy I can now play Urban Terror with my work mates :)

---

### Post by Niccola on 2012-07-19
> **jkn83 said:**
> Finally updated my BIOS.  I do not see a dynamic mode in the BIOS options where are you guys seeing this option?  

i am running a dv6-3143us and hit esc on boot

Please help! =)

Seems like your laptop doesn't have support to change graphic cards mode in BIOS. However, you have BIOS updated, so, let's figure it out if will work now.

Just install Ubuntu 12.04 normally,
*** DO NOT INSTALL ADDITIONAL DRIVERS ***
Apply updates (sudo apt-get update && sudo apt-get upgrade)
reboot
then follow post #1 from this thread due to install AMD driver

Then show us the result
Good Luck

---

### Post by jkn83 on 2012-07-19
Nicolla

I updated my bios and last night with a fresh install of ubuntu 12.04 i attempted follow post 1.  during the install i selected the option to download the updates and 3rd party stuff the two buttons...

i checked additional drivers and the AMD driver was not installed and did not install it 

So i started with no fglrx

before doing post 1 i did apt-get update and apt-get upgrade

i followed all steps and did the last step

[FONT=Arial][SIZE=2]sudo aticonfig --initial -f[/SIZE][/FONT]
i then rebooted into low graphics mode

i then tried [miatawnt2b]("http://ubuntuforums.org/member.php?u=263498") solution

[http://ubuntuforums.org/showthread.php?t=1930450&page=19](http://ubuntuforums.org/showthread.php?t=1930450&page=19)
                                  **Re: AMD/Intel Hybrid Graphics works !**             
                                                                login as you
sudo -s
cd /path_to_amd-driver-installer
./amd-driver-installer-12-xxx.run
keep pressing enter through the installer

this did not work as well i ran the installer and it said i would have to force to install

i forced the install and could reboot into ubuntu but then had system problems left and right 

i did an clean install last night and did apt get update and upgrade

any suggestions? ubuntu boots fine after install but i cant switch graphics and i need to try reinstalling eclipse with the AVD manager see if i can start the emulator because all i am trying to do is program android in a linux enviornment with eclipse...but it said that my video device isnt set up properly last time...thats why i initially came here

---

### Post by bugabuga on 2012-07-19
Hi everyone,

I hope you guys might give a helping hand on the following:

Mint 13 64-bit, based on Ubuntu installed on Macbookpro 8.3 early 2011.
Dual boot rEFIt with osX snow leopard updated.


Mint works good with amd catalyst control center user and administrative.  

I have downloaded the latest amd-driver-installer-12-6--x86.x86_64.run
yet did not install it yet.  I wanted to verify with you guys since a apple machine wither muxed / or -less.

Finally the questions: first, the backlight swith works so that I reduce the brightness with f1 and f2, however is there a way that I could adjust it to automatic?
second, what would be the process to have both graphics in Mint to work as flawlessly as possible?

Any help is greatly appreciated.  Thanks.[-o<

---

### Post by N0oki3 on 2012-07-19
> **jkn83 said:**
> 

i  followed all steps and did the last step

sudo aticonfig --initial -f
i then rebooted into low graphics mode

Hello there. I'm afraid I have to dissapoint you. Us, HP users that with latest BIOS update don't have the option to select fixed graphic card to use, cannot run unity 3D. I have tried a lot of times to contact HP via live support chat also on forums I have created topic and nicely asked HP administrators to configure the BIOS for my notebook and also alot of people with other HP notebook have replied with the same issue, but HP just doesn't give a damn about us. So you can either wait for BIOS update (ETA: unknown) or get a new laptop...acer or dell

---

### Post by jkn83 on 2012-07-19
Alot of people in here with HP laptops saying they got it to work though.  Thats why I kept at it :/ 

I guess I will reinstall java and eclipse and see if i can find a work around 

i dont plan on gaming so i have no need for my ati card right now

---

### Post by Mamoodoo on 2012-07-20
i tried what you said but the reboot i had to after installing the latest amd catalyst drivers before i can log in to my computer theres a window that pops up saying that "your pc is running on low graphics would you like to reconfigure" but even if i try to reconfigure when i reboot it the windows pops up again.So everytime i tried reconvigure the only option that works is to run it back to default graphics mode.So i really dont know what to do its not working the steps you gave.

---

### Post by Mamoodoo on 2012-07-20
> **Alexislavie said:**
> [FONT=Arial][SIZE=2]If you do want to make the switch possible between your Intel and your AMD graphics cards, then this post is for you. If you do not own a AMD hybrid graphic card, please leave this thread, and post your problems in a thread made for AMD single graphic or Intel single graphic.

[B]Edit: The solution seems not to work with ATI 5xxx graphic cards, try at your own risk.
Warning: Works only for muxless systems.
Warning 2: Check if your BIOS is updated, if not update it ! (You will need Windows). This is your computer manufacturer that "implements the switch on your mother card, and modify the video drivers for Windows to work on your computer". If an AMD 6630m (for example) works on a HP computer, this doesn't mean the same video card will work for sure (for example) on a ASUS computer.
[/B] 
**Edit bodhi.zazen**: [COLOR=darkred]**Best check hardware compatibility before following this tutorial. If your hardware is not listed as supported, this tutorial will not help you. See [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) **[/COLOR]

The following solution has been tested on a DELL Vostro 3550, with an AMD 6630m card and an Intel HD 3000 (Sandybridge) card (integrated into a Intel core i5). The version of Ubuntu used is 12.04 LTS (further versions should works too). **The system is very stable, and everything works well.**
This tutorial requires the use of the terminal, but still is simple if you're a beginner, you will just have to past some commands on it and press "Enter".
*(Tip for beginners : to past a command on a terminal, just press CTRL+SHIFT+V, it is the same shorcut as usual just don't forget to press SHIFT when pasting).*

Before beginning this tutorial, we will suppose you are following it on a fresh install (i.e. You did not install vgaswitchroo or flgrx (via jockey-gtk : The proprietary driver installer application from Ubuntu). Please also install all updates available for your computer before starting (and reboot if you're proposed to).
[B][COLOR=red]
STEP 1 - Installing latest AMD catalyst drivers :[/COLOR][/B]

As I'm writing this the latest version is 12.4, please check this page to know if there is a new version : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)[/SIZE][/FONT][FONT=Arial][SIZE=2] (this also includes the guide to install them).

First we're going to download all the prerequisite packages :
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
```If you're using Ubuntu 64bits please run those two commands (32bits users don't have to) :
```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
```We can now download the AMD catalyst 12.4 driver :
```
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
```And create Ubuntu packages of it :[/SIZE][/FONT][FONT=Arial][SIZE=2]
```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```Now let's install them :
```
sudo dpkg -i fglrx*.deb
```and configure the Xserver (xorg.conf file) for the first time :
```
sudo aticonfig --initial -f
```Now reboot your computer.

Test the switch to the discrete card :
```
sudo aticonfig --px-dgpu
```Then reboot again your computer.
[B] 
[COLOR=red]STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :[/COLOR][/B]
*Thanks to **[Niccola]("http://ubuntuforums.org/showpost.php?p=11819555&postcount=107")** for finding the actual fix.*[/SIZE][/FONT][FONT=Arial][SIZE=2]

_[COLOR=darkorange]If you ever apply an fglrx update, or your system automatically update fglrx, YOU WILL HAVE to repeat STEP 2, otherwise direct rendering will be missing on integrated gpu (i.e. No Unity 3D or Gnome Shell or Gnome Classic + Compiz on the Intel graphic). If you have an other solution (like loading a script on startup) please post it.[/COLOR]_

Open the /etc/X11/Xsession.d/10fglrx file with root rights :
```
gksu gedit /etc/X11/Xsession.d/10fglrx
```If you're using a 32bits system add at the end of 4th line this text : *"/usr/lib32/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```If you're using a 64bits system add at the end of 4th line this text : *"/usr/lib/x86_64-linux-gnu/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```Now save the file.

**[COLOR=red]STEP 3 - Enjoy your hybrid graphic system ! :[/COLOR]**

Reboot your computer to see the changes, it should boot up with the discrete card.[COLOR=black]

[/COLOR]**[COLOR=red]Useful informations, commands :[/COLOR]**

Power consumption is a lot better now, it seems that my battery last 4 times more with the integrated card, but this isn't still good as in Windows. If someone find or know tricks to decrease power consumption a little more please post it !

I do not recommend to update the catalyst driver once it's installed (if it works), if you really want to upgrade then check this page to find instructions : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)[/SIZE][/FONT][FONT=Arial][SIZE=2]

The AMD driver GUI application doesn't provide settings for screen configuration, but only 3d settings. This is a missing feature.

[I]Switching commands :
[/I]```
aticonfig --pxl # List current activated GPU
sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect
sudo aticonfig --px-igpu # Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```Verify the Open GL's libraries used :
```
fglrxinfo
```Verify if the direct rendering is used :
```
glxinfo | egrep render
```Install mesa-utils, and test the card 3d power (compare the fps) :
```
sudo apt-get install mesa-utils
glxgears
```[COLOR=Red]If something goes wrong and your[/COLOR][COLOR=black][COLOR=Red] computer doesn't boot (i.e. black screen), press CTRL+ALT+F3, log yourself into your account and enter those commands :[/COLOR]
[/COLOR]```
sudo rm /etc/X11/xorg.conf
sudo startx
```And you should be able to see your desktop.
[COLOR=red]
[/COLOR]**[COLOR=red]List of fully supported computers :   [/COLOR]**[COLOR=DarkOrange]// Updated 05/16/2012 (American date format).[/COLOR]
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]**ACER      7750g**, Intel HD 3000, AMD 6650m, HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL Inspiron 14R (N4110)**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL      Vostro 3550**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Envy 14t-2000 CTO**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP ENVY 15-3090CA**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dm4-2160sf**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavillion dm4-2110sp**,[/SIZE][/FONT][FONT=Arial][SIZE=2] Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6102sg**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6169sl**, Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6178sl**, Intel HD 3000, AMD 6770m, HDMI Intel/AMD: working/working, VGA      Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6192sf**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv7-6070ef**, Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/working,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion g4-1001tx**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Probook 4530s**, Intel HD 3000, [/SIZE][/FONT][FONT=Arial][SIZE=2]AMD 6490m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo e520**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6630m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo G-770**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6650m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SB1S1E**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SC1AFM/S**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=2]
If you want to add your computer, please do want it (this will help other users), **_make a post and indicate your configuration [COLOR=Red]like those above[/COLOR]_**. 
[/SIZE][/FONT][FONT=Arial][SIZE=2]I will then add it to the working list.
[/SIZE][/FONT][FONT=Arial][SIZE=2]_I repeat as many people do not get it : "[COLOR=Red]like those above[/COLOR]" ! It take you two minutes to write it, this saves me time, and I can update more frequently this thread._ Also posts like "It works on HP Pavilion dm4" are USELESS, I won't add a computer with an incomplete computer model number. Exception for computers without a precise model name (example : DELL Vostro 3550, Lenovo e520).
[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black]


_Useful links :_
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://forums.gentoo.org/viewtopic-p-6936730.html](http://forums.gentoo.org/viewtopic-p-6936730.html)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can thanks that guy because his post really helped me to understand how the ati hybrid graphics works.
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics](http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can also check this Gentoo wiki about hybrid graphics, this is some Gentoo's users that actually found first a solution on how to make AMD hybrid cards to work on Linux.[/COLOR][/SIZE][/FONT]

i tried what you said but the reboot i had to after installing the latest amd catalyst drivers before i can log in to my computer theres a window that pops up saying that "your pc is running on low graphics would you like to reconfigure" but even if i try to reconfigure when i reboot it the windows pops up again.So everytime i tried reconvigure the only option that works is to run it back to default graphics mode.So i really dont know what to do its not working the steps you gave.

---

### Post by N0oki3 on 2012-07-20
> **jkn83 said:**
> Alot of people in here with HP laptops saying they got it to work though.  Thats why I kept at it :/ 


Yes, as they have BIOS support for changing graphic default graphic card on boot.

---

### Post by jkn83 on 2012-07-20
thanks n0oki3 i ended up posting in the useless hp forums here [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567)

if you want to chime in just go ahead lol

---

### Post by N0oki3 on 2012-07-20
> **jkn83 said:**
> thanks n0oki3 i ended up posting in the useless hp forums here [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567)

if you want to chime in just go ahead lol

Indeed, most useless forums I have ever seen. Especially it irritates me, when they say: You are most valuable customers

---

### Post by ceejatec on 2012-07-24
**HP Pavilion dv6t Quad Ed**, Intel HD 3000, AMD 7470m, HDMI Intel/AMD: working/working, VGA Intel/AMD: not tested/not tested

I don't have a specific model number since this was a customized laptop from their website.

Also, I actually did not have to build fglrx from source; I installed fglrx and fglrx-amdcccle (v8.960) from the Ubuntu restricted archives, then proceeded with the instructions in the original post starting from "configure the X server for the first time". All worked fine; I can switch modes as described, and the outputs from fglrxinfo and others makes sense.

However, I will note that my graphics - or, possibly, my decoding - performance is far *worse* with the discrete driver. With the discrete GPU, I cannot play a medium-bitrate 1080p .mp4 without massive stuttering (tried totem, vlc, and mplayer). With the integrated Intel graphics, it plays just fine, although I do get annoying tearing when the video pans. So I can't really win there.

---

### Post by helgatheviking on 2012-07-24
I'm running Mint 13, but since that is ubuntu-based i followed these instructions, except that I used the latest ATI driver: version 12.6

i actually just ran the catalyst GUI and you can do the switching right from there if you can't remember the command line prompts.  this makes me think that editing the file in the Xsessions folder is no longer neccessary?    

i hit one major snag in the install process: not sure how but i had a file /etc/modprobe.b/blacklist-local.conf that said:

blacklist fglrx 

so after i ran your instructions and rebooted, X wouldn't start b/c xorg.conf was looking for fglrx, but this other file was blacklisting it.  followed the instructions to reset xorg.conf and then deleted that file since that 1 line was its only contents.  then i was able to switch between the 2!  

so this works for me with:
Samsung Series 7 NP700Z5A, Intel Core i7 267SQM, AMD Radeon HD 6750M 

(i'm not sure what the rest of that line is about HDMI/VGA.. i've only tested the laptop and not any external displays)

one caveat though, is that running the integrated graphics card breaks Cinnamon since the Cinnamon desktop requires 3d acceleration.

---

### Post by xalatar on 2012-07-24
Hi all :), 
I've just finished installing Catalyst as described in first post this thread. Sadly, something is wrong with integrated GPU mode -  I'm getting only wallpaper, no Unity panel and other apps. I use Vostro 3550 with Radeon 6630M, Ubuntu 12.04 x86 and installed newest Catalyst 12.6. 

Any help is greatly appreciated.  Thanks.

-----------------

I read few posts from this topic and found solution. The problem was traditionally with direct rendering. I made some changes in /etc/X11/Xsession.d/10fglrx. Now it looks:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = '**i686**' ]; then
  if [ -d /usr/**lib**/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:**/dri:/usr/lib/i386-linux-gnu/dri**
    if [ ! -z $LD_LIBRARY_PATH ]; then
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```
And direct rendering works fine. If you still have this problem just check what gives "uname -m" and locate file *915_dri.so.*

---

### Post by northar on 2012-07-24
I just tried the suggested tricks in the first post on my relatives new hp g6 1300 which uses intel/amd hybrid graphics.
No luck:( Too bad, my relative wanted to try unity 3d, but after messing around his now back to his win7 again (altough i saved the dualboot until later:)
Anyone knows if someone is working on a real solution for this? More and more notebooks seems to use the hybrid cards-

---

### Post by Glutanimate on 2012-07-24
Hi there,

I am about to do a complete reinstall on my notebook including a Precise/Win7 dualboot and wondered: If the driver installation were to fail, which in my case is likely due to the fact that I am running an Acer 3820TG with a HD5650, would I have to completely reinstall Ubuntu to revert the changes and go back to the initial state? And even though this might not be directly related to the topic at hand: Can I reinstall Ubuntu without compromising my Windows installation?

Thank you very much in advance.

P.S.: First post on the Ubuntu forums, yay. (albeit not my very first one, to tell the truth; just forgot the login details on another account)

---

### Post by rohan koranga on 2012-07-25
hey i tried to install that package every thing went right till installing the package ..it said the version ubuntu is not supported ,,,i have hd6770m gpu and i7 processor in my hp laptop and using ubuntu version 12.04

---

### Post by rohan koranga on 2012-07-25
ny1 there please help me with this i am very new to linux ..so want all ur help

---

### Post by serialpipoca on 2012-07-25
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-30-server x86_64 Ubuntu
Current Operating System: Linux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.6 root=UUID=ae22b898-77c4-417b-91cd-c4a0e07ecaa8 ro quiet splash pcie_aspm=force radeon.nomodeset=0
Build Date: 25 February 2012  06:57:33AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 25 20:55:25 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0116:1028:04ca Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
(--) PCI: (0:1:0:0) 1002:6760:1028:04ca ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] rev 0, Mem @ 0xe0000000/268435456, 0xf7b20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="Advanced Micro Devices, Inc."
	compiled for 6.9.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
	compiled for 1.4.99.906, module version = 8.98.2
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
	compiled for 1.4.99.906, module version = 8.98.2
(II) AMD Proprietary Linux Driver Version Identifier:8.98.2
(II) AMD Proprietary Linux Driver Release Identifier: 8.98                                 
(II) AMD Proprietary Linux Driver Build Date: Jun 11 2012 11:57:59
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x6760) found
(II) fglrx: intel VGA device detected, load intel driver.
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
ukiDynamicMajor: found major device number 249
ukiDynamicMajor: found major device number 249
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 7, (OK)
ukiOpenByBusid: ukiOpenMinor returns 7
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0xc095f0
(EE) fglrx(0): Unspported by intel driver! vendor id 0x8086, device id 0x116
(II) pEnt->device->identifier=(nil)
(II) fglrx(0): === [xdl_x750_atiddxPreInit] === begin
(II) fglrx(0): PowerXpress: Discrete GPU is selected.

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45fcc8]
1: /usr/bin/X (0x400000+0x5dfbd) [0x45dfbd]
2: /lib/libpthread.so.0 (0x7f5d8bf23000+0xf8f0) [0x7f5d8bf328f0]
3: /lib/libc.so.6 (0x7f5d8abfd000+0x37f328) [0x7f5d8af7c328]
Segmentation fault at address 0x7f5d8af7c328

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Thats my /var/log/Xorg.0.log ..... my notebook is a Dell N5110 with VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) and GA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

As seen... both drivers are been loaded... but the EE line says that fglrx doesnt support intel driver... i guess its not recognin' the fglrx as the main board, as i wanted =]... even PowerXpress its ok... but... does not seem to be working when the X is started..... Anyone have new ideas to get the Radeon working... The distribution is Backtrack R2 (Based on Lucid).

Ty!

---

### Post by jkn83 on 2012-07-26
the guys at hp finally responded to my thread in the hp forums 
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/DV6-3143-F29-BIOS-Update-No-Video-option-to-change-into-Dynamic/td-p/1681567)

thats the post and here is the link they referred me too - how to switch graphics while fixed mode is set in bios.....IN WINDOWS through CCC  (bah)

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03048374&lc=en&cc=us&dlc=en#N218](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03048374&lc=en&cc=us&dlc=en#N218)
go to very bottom of the page and click how to switch into fixed mode...anyways it got me thinking...

how come after a clean install of ubuntu and no updated drivers i cant install CCC and just switch to the ATI chipset?

The reason why is because i will just reboot into low graphics mode after the install of the 12-6 drivers

So it begs the question are there any open source control centers for video cards to utilize the ATI chipset?

Also what type of errors are thrown after the install of the 12-6 drivers for people that can't switch to dynamic in the BIOS.  Where would you find this information? 

For instance if I install the AMD 12-6 drivers with an up to date BIOS and cant switch to dynamic.  i  re-boot into low graphics mode.

I am interested to see the source of the problem or don't know if it has already been posted in the 40 page thread...

i still dont have the internet set up at my house and could re-install ubuntu one last time to get the correct log up in the thread if somebody could give me directions lol

Also, people on [http://askubuntu.com/questions/19897/getting-vga-switcheroo-with-ati-mobility-radeon-5650-hd-to-work](http://askubuntu.com/questions/19897/getting-vga-switcheroo-with-ati-mobility-radeon-5650-hd-to-work)
talk about something called Ubuntu Control Center.  i go to the website though and its half in spanish and i dont know where the hell is the download they are talking about
[https://sites.google.com/site/ubuntucontrolcenter/](https://sites.google.com/site/ubuntucontrolcenter/)

One last noob question why wont  vgaswitcharoo work for us in 12.04? thanks

---

### Post by Niccola on 2012-07-27
> **xalatar said:**
> Hi all :), 
I've just finished installing Catalyst as described in first post this thread. Sadly, something is wrong with integrated GPU mode -  I'm getting only wallpaper, no Unity panel and other apps. I use Vostro 3550 with Radeon 6630M, Ubuntu 12.04 x86 and installed newest Catalyst 12.6. 

Any help is greatly appreciated.  Thanks.

-----------------

I read few posts from this topic and found solution. The problem was traditionally with direct rendering. I made some changes in /etc/X11/Xsession.d/10fglrx. Now it looks:
```
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = '**i686**' ]; then
  if [ -d /usr/**lib**/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:**/dri:/usr/lib/i386-linux-gnu/dri**
    if [ ! -z $LD_LIBRARY_PATH ]; then
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```
And direct rendering works fine. If you still have this problem just check what gives "uname -m" and locate file *915_dri.so.*

Please, read my post [#356]("http://ubuntuforums.org/showpost.php?p=12098495&postcount=356"). Your changes can work, but isn't the best method.

> **Glutanimate said:**
> Hi there,

I am about to do a complete reinstall on my notebook including a Precise/Win7 dualboot and wondered: If the driver installation were to fail, which in my case is likely due to the fact that I am running an Acer 3820TG with a HD5650, would I have to completely reinstall Ubuntu to revert the changes and go back to the initial state? And even though this might not be directly related to the topic at hand: Can I reinstall Ubuntu without compromising my Windows installation?

Thank you very much in advance.

P.S.: First post on the Ubuntu forums, yay. (albeit not my very first one, to tell the truth; just forgot the login details on another account)
If something got wrong in video driver installation, you just need to delete xorg.conf file in /etc/X11/ and reboot
so, run this command:
```
sudo rm -f /etc/X11/xorg.conf
```

> **rohan koranga said:**
> hey i tried to install that package every thing went right till installing the package ..it said the version ubuntu is not supported ,,,i have hd6770m gpu and i7 processor in my hp laptop and using ubuntu version 12.04

You probably is using wrong package for your architecture. If you are using Ubuntu 64 bits you should download 64bits packages (amd64, even for intel processors). If you are using Ubuntu x86 you must download x86 packages. Just try again fixing it.

---

### Post by Glutanimate on 2012-07-27
> **Niccola said:**
> 
If something got wrong in video driver installation, you just need to delete xorg.conf file in /etc/X11/ and reboot
so, run this command:
```
sudo rm -f /etc/X11/xorg.conf
```

Thanks, I'll go ahead and test it then. I'll report back with the results later on.

---

### Post by vedovatti on 2012-07-28
Lenovo e420s,Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

---

### Post by clement.analogue on 2012-07-28
Apparently, no one opened a bug on launchpad for ATI Mobility Radeon HD 5xxx Series. So I did:

[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024)

---

### Post by D4mn17 on 2012-07-29
Hi I followed the instructions and they worked perfectly but the performance of the discrete graphics is rather under-whelming. I only get 2 fps in heaven benchmark while getting 18 fps in windows with directx11. Is there a way to improve this? or are the amd drivers just plain ****.

---

### Post by QIII on 2012-07-29
The fglrx driver works just fine or ATI and ATI/ATI hybrids.

Neither Intel/ATI hybrids nor Intel/nVIDIA hybrids seem to have a high success rate.

---

### Post by mlux on 2012-07-29
[LIST]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SE2L9E/B**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6630m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[/LIST]
It works!!

---

### Post by AbbasKhalil on 2012-08-01
The Steps mentioned in the first post in this thread helped me get my hybrid setup working.
My Laptop Specs are
HP G6-2020SE 
AMD Radeon HD 7670M
Intel Integrated Graphics.

I am using the official drivers from AMD's website for my laptop and everything is working smoothly.

Thanks a million!

---

### Post by Obscurus86 on 2012-08-02
Did someone got this working with an Intel HD 4000 (3rd gen i7) and AMD 7730m? Or any other recent hardware combo? :)

---

### Post by sajid.bd on 2012-08-04
HP Pavilion dv6-6186nr Entertainment Notebook PC with intel 3000 and amd radeon hd 6770 switchable cards. working fine :)

thanks

---

### Post by sarntam on 2012-08-05
I got the graphics working with this guide. (I did need to apply the patch to get direct rendering working for the integrated graphics though)

Samsung 700Z3A-S02, Intel HD 3000, AMD Radeon 6490M, VGA: working/working, HDMI: working/working

You need the adapter for Samsung's proprietary connector to plug in a VGA monitor, it is supported out of the box though.

Other recommendations for this laptop:

[LIST]
[*] Install samsung-tools and samsung-laptop from the [Linux on my Samsung PPA]("https://launchpad.net/%7Evoria/+archive/ppa/"). (enables backlight when you use the Grub kernel switch acpi_backlight=vendor, also check the Voria forums instructions on how to add backlight support to xorg.conf. Still didn't work for me, I used xbindkey and xbacklight in the end)
[*] Install Jupiter (CPU power saving tool)
[*] Enable power saving (see thread at [CrunchBang forums]("http://crunchbanglinux.org/forums/topic/11954"))
[*] Add kernel switches for better performance of CPU / integrated graphics (see Phoronix [#1]("http://www.phoronix.com/scan.php?page=news_item&px=OTYwNA") [#2]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1"))
[*]Install the proprietary WiFi Card driver offered in the "additional drivers" dialogue of Ubuntu to enable power saving for the WiFi card.
[/LIST]

---

### Post by sanukcm on 2012-08-06
OP's original instructions work perfectly on a Lenovo G570 with a AMD Radeon HD 6300M series 1gb hybrid card. 

Able to switch easily back and forth between power saving and high performance mode. 

Thanks _so_ much to the OP for helping me _finally_ get the most out of my machine!!):P

Results: 

Lenovo G-570,Intel HD 3000, AMD 6370m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

---

### Post by ejunior on 2012-08-07
Thanks!

I have a DELL Vostro 3550 with Intel HD 3000 and AMD Radeon HD 6630 working fine with the Ubuntu Precise Pangolin (12.04) 64bit
I'm able to switch easily back and forth between power saving and high performance mode.

The new Catalyst 12.6 have a GUI to switch between Power Saving and High Performance.

Thanks for the post!

---

### Post by orbus on 2012-08-08
Hello,

I have a Dell Vostro 3550 (i3, AMD 6630). This method works perfectly, the CPU temperature during average usage is between 49-54 celsius:P 

BUT compare to Windows 7, the keyboard is more hotter under Linux than Windows 7:confused:
I use Mint 13 with E17, powertop, jupiter to reduce powerusage. I turn off AMD card, but the cover around the "qwertasdfyxcv" keys's are very hot.

If someone have Dell Vostro 3550 whith same configuration, can check this with his/her machine?

---

### Post by ubik89 on 2012-08-09
complement:

Lenovo G-770,Intel HD 3000, AMD 6650m, HDMI Intel/AMD: working/working, VGA Intel/AMD: working/working

---

### Post by Chrishas on 2012-08-09
Hi,

I have an HP Pavillion dv3-2310 laptop with a Mobility Radeon HD 4300/4500 Series card. I have followed this guide and many alternatives, such as using jockey-gtk/amd driver without converting into .deb packages, none have worked. X crashes with the message 

(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:00:1) found

and then:

Fatal server error: no screens found.

Note that the PCI id is in the log (0@1:00:1)is wrong, it should report 01:00:0. The xorg.conf file has the correct id. The driver definitely support the HD 4xxx series with the latest update unlike the previous 12.6 one. Any help is appreciated.

Cheers,
Chris

---

### Post by lachoneus on 2012-08-14
Hi,

I am running a HP Envy 15 3033cl with the AMD Radeon 7690m. Linux 3.2.0-29-generic under Kubuntu.  Catalyst Version 12.6

I have been able to get the driver to install, via the first post, without any noticeable problems during installation. And I am also able to switch between the Intel and discrete GPU's without a problem, except for one thing.

When I switch to the discrete graphics, I run the gears demo

```
fgl_glxgears
```

and it doesn't redraw every frame, when the window is sitting there.  But if I begin to drag the window around, I can see the cube and gears moving.  As soon as I stop moving the window around, it immediately stops redrawing the window.

Here i a desktop recording of my problem 
[http://www.youtube.com/watch?v=kfUVg8WEjkU&feature=youtu.be](http://www.youtube.com/watch?v=kfUVg8WEjkU&feature=youtu.be)

There gear demo works fine when I switch over to the intel GPU.

I also notice the same thing when I use Blender 3D.  I open the program, and nothing.  Not until I move the window around anyways.

But if I switch back to the Intel GPU, Blender works fine, as it has in the past.

I thought it had something to do with direct rendering.  So when I run this command.

```
glxinfo | egrep render
```

It says that I have direct rendering.  Both for the Intel and discrete GPU's.

Here is my xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "0"
	BusID       "PCI:01:00:0"
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
```


I have looked around for a fix for this, but can't seem to find anything.  If someone could point me in the right direction, I would appreciate it.  It would be nice to have graphic acceleration for my 3D work.

---

### Post by lachoneus on 2012-08-14
Never mind. Figured it out.

When I was trying to install the divers 4 or 5 months ago, and failed, I had lost my desktop effects after reverting back to a no drivers situation.  So I discovered that under kwin>desktop effects>advanced tab there is an option to turn off opengl to XRender.  I did this to restore the nice desktop effects that Kubuntu has.

After doing some more searching around today, [here]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#kwin"), I discovered that you can turn on vsync in the same place.  Desktop Effects> Advanced tab.  But only if openGL is on.  Naturally it wasn't, because I had switched it to XRender before.

So, I switched it back to openGL, and now everything is behaving properly.  The gears demo and blender.  I even ran my system through some opengl benchmarks.  Works great.

If I had installed these drivers, according to the first post, with a clean install of Kubuntu, everything would have worked fine.

I will have to try it from a clean install sometime.

---

### Post by doktoreas on 2012-08-17
Hello everybody,
first of all thx for your help. Thanks to your suggestions, I could install AMD Driver and start Ubuntu without black screen.

My problem is that I have direct rendering:no

```
glxinfo | egrep direct
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/i965_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/i965_dri.so failed (/usr/lib/fglrx/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/i965_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/i965_dri.so failed (/usr/lib32/fglrx/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

```
aticonfig --pxl
PowerXpress: Discrete GPU is active (High-Performance mode).

```

With this problem I can run Unity only in 2D mode and it's very slow.

Any idea?

Thx!

---

### Post by bearlord on 2012-08-17
Hello :)

I am new to ubuntu... and I have a laptop HP dv6-6185la

Intel Core i7-2630QM
Radeon HD 6770M
Ubuntu 12.04 LTS 64 bits

I really don't have much experience with Linux... so I asked a friend to help me install ubuntu in my laptop. He installed it and everything seemed okay and I have been using ubuntu for a while now and I am really happy with it. However, when I wanted to make use of some games or some software that required a more intense use of my gpu... I faced a problem. I did not have my ati card installed. 

After days of surfing the web trying to find out how to install my driver... I came across this thread, followed the instructions and everything went well untill this step:

```
sudo aticonfig --initial -f
```

I get an error:
```

Uninitialised file found, configuring.
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-10

```

I actually don't mind using always the high performance gpu... I just want to be able to run MyUnity in 3D, Lord of Ultima, and Kino. 

I don't know if my friend installed some drivers before I tried to install these drivers. All I know is that I get that error and that now I have the amd catalyst center in my apps... but when I try to open it I get this:

> 
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

Any help will be very welcome :)

Thanks!

---

### Post by arinx3 on 2012-08-19
1st of all Thank you very very much to **@Alexislavie  @Niccola @codeguru11** for your effort. My Laptop is dv6-6155tx with intel i5, hybrid card (Intel 3000 and Ati radeon 6490m). I was really frustrated for over 4 days with the over heating problem of discrete card then suddenly i found this awesome thread.......

It works just fine and now i m able to run Ubuntu 12.06 with the integrated Card. And with direct rendering the Ubuntu 3D looks just Freaking Awesome........

Thank you again guys. =D>=D>=D>. U Rock !:guitar:

P.S - I am new to ubuntu and this forum. I registered just to say thanks to you guys !

---

### Post by KevMaverick on 2012-08-24
Superb solution - I'm able to have full graphics functionality at last!

Thanks for all the hard work to solve this problem!

Incidentally, if not already added, here's my details:

HP dv6-6c77sa

---

### Post by Domovoi419 on 2012-08-25
Thanks

---

### Post by hueys on 2012-08-29
Wow... Thank you so much! I followed the tutorial exactly and now my hybrid graphics is running flawlessly. (radeon 6770m on hp dv6 here) :D:D

---

### Post by miatawnt2b on 2012-08-31
> **sarntam said:**
> I got the graphics working with this guide. (I did need to apply the patch to get direct rendering working for the integrated graphics though)

Samsung 700Z3A-S02, Intel HD 3000, AMD Radeon 6490M, VGA: working/working, HDMI: working/working

You need the adapter for Samsung's proprietary connector to plug in a VGA monitor, it is supported out of the box though.

Other recommendations for this laptop:

[LIST]
[*] Install samsung-tools and samsung-laptop from the [Linux on my Samsung PPA]("https://launchpad.net/%7Evoria/+archive/ppa/"). (enables backlight when you use the Grub kernel switch acpi_backlight=vendor, also check the Voria forums instructions on how to add backlight support to xorg.conf. Still didn't work for me, I used xbindkey and xbacklight in the end)
[*] Install Jupiter (CPU power saving tool)
[*] Enable power saving (see thread at [CrunchBang forums]("http://crunchbanglinux.org/forums/topic/11954"))
[*] Add kernel switches for better performance of CPU / integrated graphics (see Phoronix [#1]("http://www.phoronix.com/scan.php?page=news_item&px=OTYwNA") [#2]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1"))
[*]Install the proprietary WiFi Card driver offered in the "additional drivers" dialogue of Ubuntu to enable power saving for the WiFi card.
[/LIST]

Did you add all of the kernel switches listed in #1 and #2?
Thanks!
-J

---

### Post by Rosterbyte on 2012-09-02
Thanks! this tutorial working perfectly with HP Pavilion g6 111el, intel 3000 + AMD 6470M.

I have 2 questions:

1) In such cases it is preferable to use the dedicated card rather than the integrated?
2) This tutorial will work also for Ubuntu 12.10 and the new GNOMEbuntu? 

Sorry for my bad english ):P

---

### Post by Tahakki on 2012-09-02
Can confirm this works on HP Pavilion M6-1054sa. However, installing the drivers the way the OP shared is not necesary - one simply has to install the driver with Jockey (not the post-release driver) and then run "aticonfig --initial" to set up, and follow the OP's instructions from there.

Thanks!

---

### Post by ksanatos on 2012-09-02
Thank you!
Thants work, but dont perfectly for me.
HP Probook 4530s, Intel HD 3000, AMD 6490m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: [COLOR="Red"]not working[/COLOR]/[COLOR="Lime"]working[/COLOR]
Ubuntu 12.04.1 clean(but vgaswitcher was working)
1) To start x-server with amd card I need to stop x-server, config drivers, and start x-server again manualy. I don't see it in main thread, thants why I just restarts my lightdm service and it's doesn't work first.
2) Intel card doesn't work normally. With xorg.conf for amd card it not even starts. Than I made other config for intel card. Now x-server starts(more precisely lightdm starts), but normal unity doesn't work.
3) Now with active amd card powerred intel card! On keyboard I can fry egg! Laptop can work from battery just 1.5 hours.
Can you help me with this? I'm thinking about reinstall ubuntu and just disactive amd card like I do before, but don't want to do it, coz I want to use amd card, even if I will can't use my intel card.

---

### Post by Penguissimo on 2012-09-02
> **Rosterbyte said:**
> Thanks! this tutorial working perfectly with HP Pavilion g6 111el, intel 3000 + AMD 6470M.

I have 2 questions:

1) In such cases it is preferable to use the dedicated card rather than the integrated?
2) This tutorial will work also for Ubuntu 12.10 and the new GNOMEbuntu? 

Sorry for my bad english ):P

1) It depends on what you use your laptop for. If you do a lot of things that need strong graphics (serious gaming, video production) you'll probably want to use the dedicated card most of the time. If you only do things that aren't heavy on graphics (web browsing, YouTube, light gaming), you'll probably want to use the integrated card more often so you can save battery.

2) I'm no expert, but I don't see anything that would prevent it from working with that setup, assuming the Catalyst drivers work properly with the kernel that comes with 12.10.

And your English is fine; it's better than that of many native speakers ;)

P.S. I have to report that this tutorial does NOT work with a Clevo P170EM, but I imagine that this is mostly due to [this bug]("http://ati.cchtml.com/show_bug.cgi?id=555"). If/when this gets fixed, I'll try it again and report back!

---

### Post by AbbasKhalil on 2012-09-02
3D Rendering has failed for me on Intel Sandy bridge gpu on Ubuntu 32bit installation.
Everything worked fine on the 64 Bit Installation of Ubuntu.

I for one also ran this extra command in the procedure for the 32bit installation
[FONT=Arial][SIZE=2]cd /usr ; sudo ln -svT lib /usr/lib[FONT=Arial]32[/FONT][/SIZE][/FONT]
i replaced the end lib64 with lib32 as the drivers looks for a /usr/lib32 folder in a 32bit installation whereas ubuntu works only with the folder named 'lib'. 

Any suggestions on what I can do to enable 3D rendering on an intel sandy bridge running with dual ATI Hybrid.

I have a HD 7600 series card on my laptop.

Cheers.

---

### Post by xalatar on 2012-09-02
> **orbus said:**
> Hello,

I have a Dell Vostro 3550 (i3, AMD 6630). This method works perfectly, the CPU temperature during average usage is between 49-54 celsius:P 

BUT compare to Windows 7, the keyboard is more hotter under Linux than Windows 7:confused:
I use Mint 13 with E17, powertop, jupiter to reduce powerusage. I turn off AMD card, but the cover around the "qwertasdfyxcv" keys's are very hot.

If someone have Dell Vostro 3550 whith same configuration, can check this with his/her machine?

I have also Vostro 3550 but with i5. Left side of keyboard is always really hot since I can remember (compare to W7). It's strange to me but I got used to.  If anybody have idea why it happens...

---

### Post by RossRyan on 2012-09-03
Hi all,

I am looking for advice with my HP ProBook 4730s, Ubuntu 12.04 on board:

[I]test@test:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6400M Series
OpenGL version string: 4.2.11631 Compatibility Profile Context[/I]

I sucessfully install drivers thanks to this great guide (THANK YOU Alexislavie!), but it looks liek my FPS is quite low:

[I]test@test:~$ glxgears
6203 frames in 5.0 seconds = 1240.517 FPS
6212 frames in 5.0 seconds = 1242.257 FPS
5937 frames in 5.0 seconds = 1187.067 FPS
7657 frames in 5.0 seconds = 1531.345 FPS
6841 frames in 5.0 seconds = 1368.017 FPS
6730 frames in 5.0 seconds = 1345.840 FPS
6697 frames in 5.0 seconds = 1339.275 FPS
6776 frames in 5.0 seconds = 1355.193 FPS[/I]

(main card, I suppose it can make it bether with its 1024 MB memory..)

I know glxgears are not accurate, but main problem is low performance in 3D games. Do you have any tip, what can I try? Thank you!

---

### Post by RossRyan on 2012-09-03
BTW after running "sudo aticonfig --initial --input=/etc/X11/xorg.conf" and reboot:

test@test:~$ glxgears
23508 frames in 5.0 seconds = 4701.493 FPS
24152 frames in 5.0 seconds = 4830.324 FPS
24307 frames in 5.0 seconds = 4861.223 FPS
24318 frames in 5.0 seconds = 4863.460 FPS
24188 frames in 5.0 seconds = 4837.522 FPS
24354 frames in 5.0 seconds = 4870.620 FPS
24492 frames in 5.0 seconds = 4898.369 FPS
24304 frames in 5.0 seconds = 4860.660 FPS
[COLOR="Lime"]24431 frames in 5.0 seconds = 4886.159 FPS[/COLOR]
[COLOR="Orange"]13802 frames in 5.0 seconds = 2760.086 FPS[/COLOR]
[COLOR="Red"]6325 frames in 5.0 seconds = 1264.916 FPS[/COLOR]
6250 frames in 5.0 seconds = 1249.514 FPS
6395 frames in 5.0 seconds = 1278.837 FPS
6509 frames in 5.0 seconds = 1301.701 FPS
6249 frames in 5.0 seconds = 1249.638 FPS
6271 frames in 5.0 seconds = 1254.141 FPS
6289 frames in 5.0 seconds = 1257.666 FPS
6271 frames in 5.0 seconds = 1254.126 FPS
6280 frames in 5.0 seconds = 1255.886 FPS
6261 frames in 5.0 seconds = 1251.836 FPS
6325 frames in 5.0 seconds = 1264.916 FPS

Why?

EDIT: It is still the same - after reboot fps about 5k, but after while 1k. Interesting thing:

aticonfig --pplib-cmd "get activity"

1) when FPS about 5k:

[B]Current Activity is Core Clock: 750MHZ
Memory Clock: 900MHZ[/B]
VDDC: 1100
**Activity: 78 percent**
Performance Level: 2
Bus Speed: 5000
Bus Lanes: 16
Maximum Bus Lanes: 16

2) when FPS about 1k:

[B]Current Activity is Core Clock: 750MHZ
Memory Clock: 900MHZ[/B]
VDDC: 1100
**Activity: [COLOR="Red"]22[/COLOR] percent**
Performance Level: 2
Bus Speed: 5000
Bus Lanes: 16
Maximum Bus Lanes: 16

...for the first time I thought, that it is some problem with power profile. But it looks like card in not running in low-power mode - clocks are still at 750-900 mhz. But why is fps and "activity" getting low?

---

### Post by THPubs on 2012-09-07
Thanks a lot for this guide! It actually worked! But there are some problems... I tried to switch the VGA to intel and after the reboot, the desktop won't load. It takes me to the login screen and after I enter the password, nothing comes... Just the wallpaper!

Another problem is the heat... The ATI GPU gets a bit hot (not too much but higher than in windows.) Any way to fix it?

Im using a HP DV6-6011tx laptop with ATI Radeon HD 6770 M GPU.

---

### Post by Rosterbyte on 2012-09-07
I decided to install in partition a linux distro, but with KDE as DM.

I've an HP Pavilion g6 1111el with intel/AMD graphic cards system, and this tutorial (that i followed in all 3 steps) work perfectly with ubuntu 12.04 unity 3d and gnome shell.

But with kubuntu as DM i must apply also the second step for direct rendering on the integrated card?

Once i did it but i had a startup error with kubuntu 12.04 (black screen)!

Thanks for help, you are great! :D

---

### Post by moknatal on 2012-09-07
Thank You for Your work!!!

It works on Lenovo ThinkPad Edge E420 (1141PZ5).
Configuration - Intel HD Graphics 3000/AMD Radeon HD 6630M.
[FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT].

---

### Post by THPubs on 2012-09-08
> **THPubs said:**
> Thanks a lot for this guide! It actually worked! But there are some problems... I tried to switch the VGA to intel and after the reboot, the desktop won't load. It takes me to the login screen and after I enter the password, nothing comes... Just the wallpaper!

Another problem is the heat... The ATI GPU gets a bit hot (not too much but higher than in windows.) Any way to fix it?

Im using a HP DV6-6011tx laptop with ATI Radeon HD 6770 M GPU.

Please forgive the blind idiot (Me)... I didn't followed the instructions to fix direct rendering... Now it works! Thanks a lot for the guide!

---

### Post by markino75 on 2012-09-10
Worked on 



[LIST]
[*]**HP Pavilion dv6-6c82sl**
[*]**N[B]otebook**, **Intel Core i5-2450M**  
[/B]
[*]Radeon HD7470 1GBi
[*] Linux mint Maya (MATE)
[/LIST]

---

### Post by Kraaijenzank on 2012-09-10
Thank you so much for your very detailed guide! It worked flawlessly for me!

**HP Pavillion dm4-2102eo**, Intel HD 3000, AMD 6470m, HDMI Intel/AMD: working/working, VGA Intel/AMD: working/working

Running Ubuntu 12.04 with Unity.

---

### Post by AmjAdAsh2Ar on 2012-09-10
[SIZE="4"]People I really need a similar solution to ATI Radeon 5xxx/intel hybrid cards .. my discrete card is Ati Radeon 5650m [/SIZE]

**_[SIZE="3"]PLEASE[/SIZE]_**

---

### Post by Tobo27 on 2012-09-10
Hi guys!

I just bought a new laptop: an HP pavilion g6, this is my lspci | grep VGA output:

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

```While trying the guide in the first message of this thread, at this point:

> [FONT=Arial][SIZE=2]Now let's install them :
     Code:
     sudo dpkg -i fglrx*.deb 
[/SIZE][/FONT]I get this Error message:
```

Error! Bad return status for module build on kernel: 3.2.0-30-generic-pae (i686)
```Well, it's the second time I try to install the ati driver, the firs time I get the same error, I ignored it and continued to the next step. I was no more able to start Xserver, i had to login by a console so I decided to install againg the whole system.

Now, I want to avoid any problem, so what am I supposed to do with the error?

Thank you in advance
Tobo.

EDIT: I'm running Ubuntu 12.04 for i386

---

### Post by clement.analogue on 2012-09-10
> **AmjAdAsh2Ar said:**
> [SIZE=4]People I really need a similar solution to ATI Radeon 5xxx/intel hybrid cards .. my discrete card is Ati Radeon 5650m [/SIZE]

**_[SIZE=3]PLEASE[/SIZE]_**

I opened a bug in launchpad. You can go to "[This bug affects you and 8 other people]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024/+affectsmetoo")[]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024/+affectsmetoo")" on the following page so dev can see it's a real problem for some people :
[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024)

---

### Post by Tobo27 on 2012-09-10
Ok guys, I looked around and I found this:
[http://ubuntuforums.org/showthread.php?t=1969827](http://ubuntuforums.org/showthread.php?t=1969827)

It worked very well

Hope useful ;)

Bye!

---

### Post by Tobo27 on 2012-09-10
New issues!

If i try to start ubuntu using the Intel HD3000, after the login screen I see my desktop background and i can move the mouse pointer, but there is nothing else.

Anyone knows how I could fix this? 

Thank you
Tobo.

EDIT>> ok, I'm in, but I had to set ubuntu 2D in the login option. 
but uhm...I still don't know what to do :D

EDIT2>> solved in this way [http://ubuntuforums.org/showpost.php?p=11857337&postcount=173](http://ubuntuforums.org/showpost.php?p=11857337&postcount=173)

---

### Post by _fried_ on 2012-09-13
Hello RossRyan,

I have exactly the same problem on my system (H3000/6470M), no clue however. Could it be related to Compiz?  :confused:




> **RossRyan said:**
> BTW after running "sudo aticonfig --initial --input=/etc/X11/xorg.conf" and reboot:

test@test:~$ glxgears
23508 frames in 5.0 seconds = 4701.493 FPS
24152 frames in 5.0 seconds = 4830.324 FPS
24307 frames in 5.0 seconds = 4861.223 FPS
24318 frames in 5.0 seconds = 4863.460 FPS
24188 frames in 5.0 seconds = 4837.522 FPS
24354 frames in 5.0 seconds = 4870.620 FPS
24492 frames in 5.0 seconds = 4898.369 FPS
24304 frames in 5.0 seconds = 4860.660 FPS
[COLOR=Lime]24431 frames in 5.0 seconds = 4886.159 FPS[/COLOR]
[COLOR=Orange]13802 frames in 5.0 seconds = 2760.086 FPS[/COLOR]
[COLOR=Red]6325 frames in 5.0 seconds = 1264.916 FPS[/COLOR]
6250 frames in 5.0 seconds = 1249.514 FPS
6395 frames in 5.0 seconds = 1278.837 FPS
6509 frames in 5.0 seconds = 1301.701 FPS
6249 frames in 5.0 seconds = 1249.638 FPS
6271 frames in 5.0 seconds = 1254.141 FPS
6289 frames in 5.0 seconds = 1257.666 FPS
6271 frames in 5.0 seconds = 1254.126 FPS
6280 frames in 5.0 seconds = 1255.886 FPS
6261 frames in 5.0 seconds = 1251.836 FPS
6325 frames in 5.0 seconds = 1264.916 FPS

Why?

EDIT: It is still the same - after reboot fps about 5k, but after while 1k. Interesting thing:

aticonfig --pplib-cmd "get activity"

1) when FPS about 5k:

[B]Current Activity is Core Clock: 750MHZ
Memory Clock: 900MHZ[/B]
VDDC: 1100
**Activity: 78 percent**
Performance Level: 2
Bus Speed: 5000
Bus Lanes: 16
Maximum Bus Lanes: 16

2) when FPS about 1k:

[B]Current Activity is Core Clock: 750MHZ
Memory Clock: 900MHZ[/B]
VDDC: 1100
**Activity: [COLOR=Red]22[/COLOR] percent**
Performance Level: 2
Bus Speed: 5000
Bus Lanes: 16
Maximum Bus Lanes: 16

...for the first time I thought, that it is some problem with power profile. But it looks like card in not running in low-power mode - clocks are still at 750-900 mhz. But why is fps and "activity" getting low?

---

### Post by wegah on 2012-09-13
Seems a good news are coming in AMD front.

For everyone that can't do the catalyst work. LIKE ME.
PRIME. The native solution for open source drivers.
Still in earlier stages but ALREADY work for most RADEON driver cards.

NEEDS;
UBUNTU QUANTAL;
PROPOSED PACKAGES OPENED;
ppa:xorg-edgers/ppa

UPDATE
DIST_UPGRADE

REMOVE ANY XORG.CONf
REBOOT

The only manual thing need to be compiled by hand is the new xrand 1.5 >

git clone --depth 1 git://people.freedesktop.org/~airlied/xrandr -b prime
cd xrandr
./autogen.sh --prefix=/opt/xorg
make
sudo make install

( the missing packages he tell you can be installed by the synaptic, not the need of external git or files).

When finished.
go to "cd /opt/xorg/bin"

EXECUTE "xrandr --listproviders"

You will receibe something like this;

"
Provider 0: id: 144 cap: b nc: 2 no: 6 nap 1 name:Intel
Provider 1: id: 89 cap: d nc: 6 no: 4 nap 1 name:radeon
"
Then just use "xrandr --setprovideroffloadsink 89 144"( the number you get from the command executed before.

Ok, If you didn't receive an error.

Now, just do a test.
EXECUTE this command  "DRI_PRIME=0 glxinfo"
if no error and you receive this;
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 9.0-devel
OpenGL shading language version string: 1.30

everything is ok .

EXECUTE this command  "DRI_PRIME=1 glxinfo"
If no error and you receive this;
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD JUNIPER
OpenGL version string: 2.1 Mesa 9.0-devel
OpenGL shading language version string: 1.30


VOILA.... WELCOME to at last some 3d working with your hardware.

Now. every program you start with "DRI_PRIME=1" before the command . will run under AMD GL driver.

Still not possible to switch the cardand both cards need to be working ( mean will be more hot than common, like in windows). but better then nothing.. and GAMES WORK PERFECT

Just some number..
DRI_PRIME=0 glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.331 FPS
300 frames in 5.0 seconds = 59.998 FPS
301 frames in 5.0 seconds = 60.003 FPS

DRI_PRIME=1 glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
7244 frames in 5.0 seconds = 1448.640 FPS
7273 frames in 5.0 seconds = 1454.410 FPS
6915 frames in 5.0 seconds = 1382.891 FPS

Just for note. Mine hardware HPshit ENVY 17 3d 2100 CTO INTEL/AMD6850m

---

### Post by lasanthafdo on 2012-09-15
Thanks for the info... Your post worked perfectly for Ubuntu 12.04 LTS fresh install with AMD-12.8 Catalyst Driver downloaded from AMD site. My config is


[LIST]
[*][FONT=Arial][SIZE=2]**HP Probook 4540s**, Intel HD 4000, [/SIZE][/FONT][FONT=Arial][SIZE=2]AMD 7650m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[/LIST]

---

### Post by Bucic on 2012-09-16
> **Alexislavie said:**
> Only muxless system.
Muxed system have a switch in the BIOS, this is why muxless system are a problem, because they do not have this option.
My system is *muxed**. Can anyone point me to a guide on how to install drivers for switchable graphics that are to be switched after computer is rebooted, not while system is running?


*
My system has *ATI RV635 [Mobility Radeon HD 3650]*. According to 

> Hybrid Graphics and Catalyst

There are two basic types of hybrid designs. Older hybrid systems use a multiplexor (mux) to switch between GPU's. Newer systems (those with PowerXpress >= 4.0) are muxless. As far as I can tell, PowerXpress 4.0 *started with RadeonHD 6000-series GPU's*, and systems with older ATI GPU's have a mux, but don't quote that. 
it's identified as *muxed*
source: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

My system details:
Lenovo Thinkpad T500
Switchable Graphics with Intel GMA 4500MHD and ATI Mobility Radeon HD 3650 (256 MB)

---

### Post by noxified on 2012-09-17
i'm gonna get an asus x44h with i3 and AMD Radeon HD 6470M .it will work linux fine?(it has an intel hd 3000 too)

---

### Post by teknikk7 on 2012-09-18
I have an Alienware m18x. Dual 7990 with i7 HD3000.  I disabled onboard video via BIOS settings leaving only PEG enabled.  I have installed the ATI driver from the website and keep getting the error when I launch catalyst control center.

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Any ideas guys?
 Here's the lspci output:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
01:00.1 Audio device: ATI Technologies Inc Device aab0
07:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
08:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
09:00.0 Network controller: Intel Corporation Device 0887 (rev c4)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
0a:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)


Also when I do this:

root@bt:~# sudo aticonfig --initial -f
aticonfig: No supported adapters detected


Thanks for any help guys...

---

### Post by orbus on 2012-09-19
> **teknikk7 said:**
> I have an Alienware m18x. Dual 7990 with i7 HD3000.  I disabled onboard video via BIOS settings leaving only PEG enabled.  I have installed the ATI driver from the website and keep getting the error when I launch catalyst control center.

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Any ideas guys?
 Here's the lspci output:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
01:00.1 Audio device: ATI Technologies Inc Device aab0
07:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
08:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
09:00.0 Network controller: Intel Corporation Device 0887 (rev c4)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
0a:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)


Also when I do this:

root@bt:~# sudo aticonfig --initial -f
aticonfig: No supported adapters detected


Thanks for any help guys...

Hi,

I have a Vostro 3550 (Intel3000/AMD6630M) I tried to install the new Catalyst 12.9 and I got the same "aticonfig: No supported adapters detected" error. 12.8 works perfectly with my machine, you should try it: [**Catalyst 12.8 driver download**]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
I hope it helps. ):P

---

### Post by teknikk7 on 2012-09-20
> **orbus said:**
> Hi,

I have a Vostro 3550 (Intel3000/AMD6630M) I tried to install the new Catalyst 12.9 and I got the same "aticonfig: No supported adapters detected" error. 12.8 works perfectly with my machine, you should try it: [**Catalyst 12.8 driver download**]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
I hope it helps. ):P

I have been using 12.8...  No go.

Thx

---

### Post by orbus on 2012-09-20
> **teknikk7 said:**
> I have been using 12.8...  No go.

Thx

Then try lower versions from Catalyst for example 12.6.

Which kernel version do you use?

---

### Post by Kaiket on 2012-09-20
Works perfectly on Sony Vaio VPCSA3C5E.
Just registered to say that =P
Thank you very much for the post.

---

### Post by teknikk7 on 2012-09-20
> **orbus said:**
> Then try lower versions from Catalyst for example 12.6.

Which kernel version do you use?

Well I have Dual 7970 in crossfire (Alienware M18x R2).  I don't think I can go that low.

---

### Post by Infra1515 on 2012-09-21
Hello . I'm using HP Probook 4530s with i5 2410 and ATI Radeon 64xx DGPU. Installed the drivers as per instructions - the ati chip got enabled and works pretty good . However switching to the integrated GPU does not seem to work . Whether I do it from the AMD Catalyst Control Center or thru the terminal with the command aticonfig --px-igpu the result is the same - the computer would boot but unity wont load . The only thing I can see is my icons on the desktop and can open a terminal to switch back to the discrete gpu. No unity panel , no unity top bar , no icon border , nothing. I would be really glad if someone could tell me if they had success in resolving this issue. ( the HP Probook 4530s is marked as working in the OP ).

---

### Post by freesbee on 2012-09-22
It is very frustrating.
I have exactly the same configuration (HP Envy 13 with ATI Radeon/Intel).
My installation is clean, of 12.04 64bit, and I did not install any previous fglrx
I followed the instructions step by step, and everything worked propely.
When I try to build the package with the command

```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```I get the error

```
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui)
```I do not get the package, so I cannot go any further. 
Any idea what I could try?

---

### Post by hipnosys on 2012-09-25
Followed the guide to the absolute letter, and it worked like a charm! :KS

Although AMD have updated their drivers, I decided to go with 12.4 as outlined in the instructions. 

I have followed other guides a few times previously and have ended up with a unbootable machine. 

Switched to the intel graphics for the first time and watched in amazement as my battery indicator started going up!

Can't thank you enough really.                       ):P

I am using Ubuntu 12.04 64bit. Core i5-2430M CPU

**HP Probook 4330s**, Intel HD3000, AMD 6400M, HDMI Intel/AMD not tested/not tested VGA Intel/AMD not tested/not tested

---

### Post by agmegharaj on 2012-09-26
Really a great work alex.. thanks a lot for this. I have not yet tried this yet but I am having similar problem that is.

HP Pavilion dm4 with configuration as shown below

cpu intel Core i5 2.26 GHz 
RAM 4.0 GB
Graphics processor 512MB ATI Mobility Radeon(TM) HD 5450 switchable graphics [HDMI, VGA].


I installed ubuntu 10.04 ( without AMD graphics driver) it was working fine, but when I installed AMD graphics drivers AMD Catalyst™ 12.8 Proprietary Linux x86 Display Driver, than the problem started from then When I boot I was get black screen.

Than I thought to upgrade from ubuntu 10.04 to 12.04 using the bootable pen drive but was getting black screen than read on some forums that was because of the switchable graphics, than upgraded ubuntu 12.04 by setting to "nomodeset". It was working, again thought to install graphics driver AMD Catalyst™ 12.8 Proprietary Linux x86 Display Driver, again after installing this, when I boot I am getting blank scree .

Can anyone help me to inatall ubuntu 12.04 along with AMD Catalyst™ 12.8 Proprietary Linux x86 Display Driver.

Any help is highly appreciated.



I will go home try you method... Will inform you the result shortly 
Thank you.

---

### Post by Bucic on 2012-09-26
To anyone savvy in graphics configuration and interested - there's a bounty at askubuntu.com to crack [http://askubuntu.com/questions/189540/how-to-re-configure-graphics-from-intel-integrated-to-intel-ati-switchable](http://askubuntu.com/questions/189540/how-to-re-configure-graphics-from-intel-integrated-to-intel-ati-switchable)

---

### Post by ksanatos on 2012-09-30
Hi!
I have HP ProBook 4530s. Cards is: Intel SB/AMD RadeonHD 6490M
I install latest amd driver(12.9 beta) on my 3.5.4 kernel(Ubuntu 12.04.1).
AMD card work great, but I already have heater in my room, and I don't need it by my notebook.
When I use Intel card it can't use Unity3D(like some people named it).
*/usr/lib/nux/unity_support_test -p*
> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 1.4 (3.0 Mesa 8.0.2)

Not software rendered: yes
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
[COLOR="Red"]GL vertex buffer object: no[/COLOR]
GL framebuffer object: yes
GL version is 1.4+: yes

Unity 3D supported: no

Step 2 in howto useless. 'cause in **/usr/lib/dri/** folder(don't have **/usr/lib32** folder) only one link to **/usr/lib/*fglrx*/dri/fglrx_dri.so** named **fglrx_dri.so**. There is no lib for intel video card.

*ls -la /usr/lib/dri*
> drwxr-xr-x   2 root root  4096 &#1089;&#1077;&#1085;&#1090;. 29 13:19 .
drwxr-xr-x 230 root root 53248 &#1089;&#1077;&#1085;&#1090;. 29 21:23 ..
lrwxrwxrwx   1 root root    42 &#1089;&#1077;&#1085;&#1090;. 29 13:19 fglrx_dri.so -> /etc/alternatives/i386-linux-gnu_fglrx_dri


*env LIBGL_DEBUG=verbose glxinfo | grep error*
> libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/i965_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/i965_dri.so failed (/usr/lib/fglrx/dri/i965_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering

Sory for my english, please.

---

### Post by thrombus on 2012-09-30
I have been using integrated graphics for several months now in an attempt to reduce power consumption, though it was still high compared to windows 7 (powertop showed range of 17-22 watts with typical use including web browsing).

I noticed the computer ran hotter under ubuntu 12.04 compared to windows 7 and became suspicous that the discrete gpu might still be on, even though I was using integrated graphics.  So, I switched back to discrete graphics and I'm now I'm getting improved power usage of 13-17 watts!!

My laptop is a Samsung Chronos series 7.  I had installed the catalyst drivers a while ago differently than the method posted in this forum.  I installed fglrx-updates and fglrx-amdcccle-updates through Synaptics.  I have not had any other graphics problems.  

I am just trying to find out if anyone might have an explanation, or if anyone else has noticed more power use with  integrated graphics.  Maybe I need to reinstall my drivers using this method.

---

### Post by roudy1989 on 2012-10-02
I've got exactly the same behavior with my Samsung Serie 7 700Z3A-S02DE Chronos.

---

### Post by wegah on 2012-10-03
> **teknikk7 said:**
> I have an Alienware m18x. Dual 7990 with i7 HD3000.  I disabled onboard video via BIOS settings leaving only PEG enabled.  I have installed the ATI driver from the website and keep getting the error when I launch catalyst control center.

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Any ideas guys?
 Here's the lspci output:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
01:00.1 Audio device: ATI Technologies Inc Device aab0
07:00.0 VGA compatible controller: ATI Technologies Inc Device 6800
08:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
09:00.0 Network controller: Intel Corporation Device 0887 (rev c4)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
0a:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)


Also when I do this:

root@bt:~# sudo aticonfig --initial -f
aticonfig: No supported adapters detected


Thanks for any help guys...

Dual HD7990 but show your pci have "01:00.0 VGA compatible controller: ATI Technologies Inc Device 6800.."

"ATI Technologies Inc Device 6800"?

I'm missing something?
did you try the opensource driver first? IN CASE your card already is supported?

---

### Post by wegah on 2012-10-03
> **thrombus said:**
> I have been using integrated graphics for several months now in an attempt to reduce power consumption, though it was still high compared to windows 7 (powertop showed range of 17-22 watts with typical use including web browsing).

I noticed the computer ran hotter under ubuntu 12.04 compared to windows 7 and became suspicous that the discrete gpu might still be on, even though I was using integrated graphics.  So, I switched back to discrete graphics and I'm now I'm getting improved power usage of 13-17 watts!!

My laptop is a Samsung Chronos series 7.  I had installed the catalyst drivers a while ago differently than the method posted in this forum.  I installed fglrx-updates and fglrx-amdcccle-updates through Synaptics.  I have not had any other graphics problems.  

I am just trying to find out if anyone might have an explanation, or if anyone else has noticed more power use with  integrated graphics.  Maybe I need to reinstall my drivers using this method.

did you used "vgaswitcheroo" do disable the non used card ( in case of you are not using catalyst0? 
sudo echo 'OFF' > /sys/kernel/debug/vgaswitcheroo/switch

If no. then you have 2 cards working same time. This is the cause of TEMPERATURE.

---

### Post by delsus on 2012-10-05
I have been out of the Ubuntu scene for a few months now and I was wondering is there are still problems with hybrid graphics, my laptop on Ubuntu was defaulting to the integrated chip, and nothing I could do would allow me to switch it off, to force it on the discreet chip, making the fglrx driver mess everything up (boot up failure).

I want to see how well one of my games runs under wine and for this I need the discreet chip with the fglrx driver, I have an ATI mobility radeon HD 5470 and a first gen i5.

Any help will be appreciated.

---

### Post by thrombus on 2012-10-07
wegah:  I have not installed vgaswitcheroo.  I only turned off the discrete chip through Catalyst.

If I want to use the integrated chip only, do I need run vgaswitcheroo in addition to Catalyst?

---

### Post by clement.analogue on 2012-10-07
You don't install vgaswitcheroo. It's in the kernel. The one in Ubuntu 12.04 has vgaswitcheroo.

---

### Post by iowabeakster on 2012-10-07
Asus B43 with Intel i5 and ATI 6470.  

Anybody got anything working on Asus yet? 

To the guy asking about Asus on this thread a couple weeks ago... I wouldn't get your hopes up.  I've been trying(and checking back here occasionally) off and on since April. And I usually can't get a single response of any kind around here.  I guess the point of this thread is for everyone who has a model of computer that it has been already established that it works on, to reconfirm that over and over and over.

I've tried every updated driver since 12-4... and it doesn't work.  I even found a Asus Bios update over a month ago (and installed it). As has always been the case, the driver installs fine, but the ati-config command generates basically a blank file and on reboot... black screen... no graphics at all.  So I delete the config file to get default graphics working again.  Then I wait a month or so and try again.

---

### Post by BryanMM on 2012-10-07
Works great on my setup if you would like to add to your list:

MSI FX420-050US, Intel HD 3000, AMD 6470m, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

Thanks for the post, much appreciated.

---

### Post by .jekyll on 2012-10-08
Hi. I have a HP Pavilion dv6-6B51nr, with the AMD 6770M graphic card (I don't know the Intel model). I'm on Ubuntu 12.04. 

After following the instructions, the integrated card still cannot render menus and icons on the desktop unless logging in with Ubuntu 2D. I've altered the [FONT=Arial][SIZE=2] /etc/X11/Xsession.d/10fglrx file and it didn't make a difference.

What could I do to fix this?


Also, I would like to add that it would be useful if the main post listed these instructions 
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx)

for those who, like me, had installed all that stuff (I learned the hard way that I couldn't simply disregard the warning about a fresh install). 

Thank you so far and hopefully we can get this fixed too. 

Edit: I'd like to point out that since installing the driver as written here, instead of through Additional Drivers made the notebook run MUCH hotter and drain its battery way quicker.
[/SIZE][/FONT]

---

### Post by ksnerph on 2012-10-10
Thanks a lot, it helped me to enable the feature!!!
I am using Ubuntu precise on HP ENVY 13-1030ca with integrated Intel graphics and ATI Mobility Radeon 4330 RV710 with installed Catalyst 12.6.

IMPORTANT!!!
Everything start working after modifying "Device" section in /etc/X11/xorg.conf:

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:0@1:0:0"
EndSection

before it was:

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

new format has been taken from /var/log/Xorg.0.log

Good luck!!

---

### Post by Unclean009 on 2012-10-11
> **Infra1515 said:**
> Hello . I'm using HP Probook 4530s with i5 2410 and ATI Radeon 64xx DGPU. Installed the drivers as per instructions - the ati chip got enabled and works pretty good . However switching to the integrated GPU does not seem to work . Whether I do it from the AMD Catalyst Control Center or thru the terminal with the command aticonfig --px-igpu the result is the same - the computer would boot but unity wont load . The only thing I can see is my icons on the desktop and can open a terminal to switch back to the discrete gpu. No unity panel , no unity top bar , no icon border , nothing. I would be really glad if someone could tell me if they had success in resolving this issue. ( the HP Probook 4530s is marked as working in the OP ).

I was the one who originally said that the 4530s works with this solution. I can confirm this again today as I reformatted. I followed the steps in the OP exactly except with the 12.8 drivers. 

Good luck.

---

### Post by Miktor on 2012-10-11
This was working almost fine (had some crashes under certain circumstances). 

But today I updated my packages, and it no longer works. Crashes at startup, and I have to remove xorg.conf for it to work again. I'm pretty clueless as of now to what has happened. I've tried newer versions, older versions, but nothing works anymore.

Oh, and of course, my computer is a lenovo thinkpad e320, with an amd6630 graphics card

---

### Post by Mohamed Elsayed on 2012-10-18
> **.jekyll said:**
> Hi. I have a HP Pavilion dv6-6B51nr, with the AMD 6770M graphic card (I don't know the Intel model). I'm on Ubuntu 12.04. 

After following the instructions, the integrated card still cannot render menus and icons on the desktop unless logging in with Ubuntu 2D. I've altered the [FONT=Arial][SIZE=2] /etc/X11/Xsession.d/10fglrx file and it didn't make a difference.

What could I do to fix this?


Also, I would like to add that it would be useful if the main post listed these instructions 
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx)

for those who, like me, had installed all that stuff (I learned the hard way that I couldn't simply disregard the warning about a fresh install). 

Thank you so far and hopefully we can get this fixed too. 

Edit: I'd like to point out that since installing the driver as written here, instead of through Additional Drivers made the notebook run MUCH hotter and drain its battery way quicker.
[/SIZE][/FONT]

I have a HP Pavilion dv6-6b80ee, with the AMD 6770M graphic card and I have the same problem ...

---

### Post by Mohamed Elsayed on 2012-10-18
Can I upgrade to Ubuntu 12.10 ??? or I'll have problems with hybrid graphics ??? should I uninstall it first????

---

### Post by mlux on 2012-10-18
> **Mohamed Elsayed said:**
> Can I upgrade to Ubuntu 12.10 ??? or I'll have problems with hybrid graphics ??? should I uninstall it first????

Same Question for me!
The first post on this page let me think that it is not working:
[http://www.upubuntu.com/2012/10/how-to-repair-failed-amd-catalyst.html](http://www.upubuntu.com/2012/10/how-to-repair-failed-amd-catalyst.html)
> "Be careful! AMD Catalyst driver 12.8 not working without a patch for  kernel 3.5+ . Catalyst 12.9 (Beta)  works with this kernel and kernel  3.6+"I want to upgrade from 12.04 to 12.10. But I have installed Catalyst Control Center 12.6. So I think it will not work if the post is correct.

---

### Post by stunrock on 2012-10-18
how can i install the beta 12.9?

should i create the deb packages or should I .run the installer?

:confused:

---

### Post by mlux on 2012-10-19
> **stunrock said:**
> how can i install the beta 12.9?

should i create the deb packages or should I .run the installer?

:confused:


[http://www.upubuntu.com/2012/09/how-to-install-amd-catalyst-129-driver.html](http://www.upubuntu.com/2012/09/how-to-install-amd-catalyst-129-driver.html)

I downloaded this (beta) Catalyst 12.9 three weeks ago and tried to install it on Ubuntu 12.10 Beta 64 Bit for my "Intel® HD Graphics 3000 & AMD Radeon&#8482; HD 6630M" hardware. But the installer did not let me continue the installation process because a message appears that shows, that my card is not supported.
The 12.6 Catalyst on Ubuntu 12.04 64 Bit works well on my System (I followed the description from post #1 of this thread).

EDIT:
Today I tested the Catalyst 12.9 on Ubuntu 12.10. I created the .deb-files. But it does not work. I only see the login-screen. After entering the password for my user, nothing happens....

---

### Post by chulex67 on 2012-10-19
so does this tutorial works for my laptop? its a sony vaio i have an i5 with a 7550m

---

### Post by Rosterbyte on 2012-10-19
could you update this tutorial for ubuntu 12.10?
Thanks! :)

---

### Post by THPubs on 2012-10-20
Currently there's a bug with Ubuntu 12.10 and the ATI drivers... (Check the bug report : [https://bugs.launchpad.net/fglrx/+bug/1068661]("https://bugs.launchpad.net/fglrx/+bug/1068661"))

I tried the fglrx drivers in official Ubuntu repositories (which worked for Ubuntu 12.04) and followed this guide and tried the drivers 12.8, 12.9 and even 12.4... Nothing worked!

---

### Post by Rosterbyte on 2012-10-20
> **THPubs said:**
> Currently there's a bug with Ubuntu 12.10 and the ATI drivers... (Check the bug report : [https://bugs.launchpad.net/fglrx/+bug/1068661]("https://bugs.launchpad.net/fglrx/+bug/1068661"))

I tried the fglrx drivers in official Ubuntu repositories (which worked for Ubuntu 12.04) and followed this guide and tried the drivers 12.8, 12.9 and even 12.4... Nothing worked!

:(

I hate computer with switchables graphics :mad:

---

### Post by Unclean009 on 2012-10-22
I also couldn't get anything working with 12.10. This depresses me.

---

### Post by orbus on 2012-10-23
(Vostro 3550 / AMD 6630M)

I tried with this solution: [http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

with latest Catalyst 12.08 / 12.09 / 12.10 but the result is the same, not working :confused:

Do I have to back to 12.04 ... ?

---

### Post by rompelstompel on 2012-10-24
It was the same when 12.04 came out at first. We should just be patient while the gurus are at work trying to solve this.

---

### Post by Penguissimo on 2012-10-24
Working BEAUTIFULLY on a Clevo P170EM/7970M in 12.04 with Catalyst 12.10. Only problem is that suspend/resume seems a little wonky now...

---

### Post by Rosterbyte on 2012-10-25
Can i install ubuntu 12.04, follow this step to install switchable grapchics and then upgrade to ubuntu 12.10? I will lost the drivers compatibility?

---

### Post by HungerGalaxy on 2012-10-25
> **Rosterbyte said:**
> Can i install ubuntu 12.04, follow this step to install switchable grapchics and then upgrade to ubuntu 12.10? I will lost the drivers compatibility?

Yes, on booting Unity won't load. Like rompelstompel said, just wait for the gurus to sort this out

---

### Post by P0eight on 2012-10-26
Okay Guys, I think I traveled through half the internet without finding a solution. I installed both Ubuntu 12.04 and 12.10 on my Dell Vostro 3350 and deactivating the AMD GPU just worked fine with switcheroo. BUT... now that Unity has to run on the Intel Card I get heavy window flickering when browsing the internet i.e. Same happens within Gnome 3, Gnome Classic and Gnome Classic 2D. The strange thing is: KDE works just fine without any flickering. The moment I reactivate the dedicated AMD GPU, the flickering is gone.

Anyone got a solution to this, because I can't find any. :-(

Thanks guys..

---

### Post by Niccola on 2012-10-27
Very strange,
seems like my Radeon HD6770M have no support in latest drivers for Ubuntu 12.10

Is anybody else having same issue? What GPUs model?

I've installed latest 12.10 and 12.11 beta and Im always entering in a low graphics mode.

---

### Post by sarvigalava on 2012-10-27
> **Niccola said:**
> Very strange,
seems like my Radeon HD6770M have no support in latest drivers for Ubuntu 12.10

Is anybody else having same issue? What GPUs model?

I've installed latest 12.10 and 12.11 beta and Im always entering in a low graphics mode.

Same for my 6750M on Samsung series 7 laptop. It is similar to 6770M but lower clocked. I can't find any driver that will work properly. Installed 12.8, 12.9,12.10, 12.11 beta, reinstalled ubuntu 5 times with no succes. I will use windows until I get decent drivers. It is sad to buy so expensive laptop and to use it like an air heater (open source drivers)

---

### Post by nardusg on 2012-10-27
Hi

Join the club, with every new release of the fglrx drivers I get my hopes up, just to get disapointed again. Windows is not an option...

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]

Regards

Nar

---

### Post by skynetsaa on 2012-10-27
Hello man! I three days was puzzled how to setup my video card of Ati.  And i did all, how you wrote. And my notebook working! HP 4740s. Thanks a lot! 
ati catalist 12.10 + video AMD Radeon HD 7650M
:guitar:

---

### Post by roudy1989 on 2012-10-28
> **sarvigalava said:**
> Same for my 6750M on Samsung series 7 laptop. It is similar to 6770M but lower clocked. I can't find any driver that will work properly. Installed 12.8, 12.9,12.10, 12.11 beta, reinstalled ubuntu 5 times with no succes. I will use windows until I get decent drivers. It is sad to buy so expensive laptop and to use it like an air heater (open source drivers)

I've got the Samsung Series 7 Chronos 700Z3A-S02de with 6490M and it does not work with Ubuntu 12.10 and neither ATI Catalyst 12.10 nor 12.11beta. Both make me start into low graphics mode.
I would really appreciate if even the acpi_call module (google for it, its hosted on github) would work with recent kernels. But it's support seems to be dropped from the author.
All I want is to stop the dedicated card :-) Thats enough for my work

Well, I decided to downgrade to Ubuntu 12.04.1 and stick with that version. Installed fglrx_updates. Works! :-)

---

### Post by Alexislavie on 2012-10-29
> **Niccola said:**
> Very strange,
seems like my Radeon HD6770M have no support in latest drivers for Ubuntu 12.10

Is anybody else having same issue? What GPUs model?

I've installed latest 12.10 and 12.11 beta and Im always entering in a low graphics mode.

I'm updating the post about this. I experienced the same issue, but found a way to get it away.

---

### Post by nardusg on 2012-10-29
Please share your way ;)

---

### Post by Alexislavie on 2012-10-29
WTF !? I'm sorry, I just can't edit the main post, the EDIT link isn't there.
I don't why it is gone...

---

### Post by nardusg on 2012-10-29
Not good :( lol

---

### Post by Alexislavie on 2012-10-29
Quick tip :
I am still using 12.04.1, I won't upgrade to 12.10, so I can't tell if it will work on 12.10, but it works on my 12.04.1 computer.

I had the low graphics mode window after upgrading AMD Catalyst from 12.8 to 12.10.
The thing is that this window was displayed very well (I mean with the maximal resolution my screen can display at 1366x768px). So I didn't understand why Ubuntu was telling me I was running in low graphics mode...
What I did :
On the low graphics mode window, click "Exit and go to console login" (~something like that).
While you're now on tty1, enter your username, then your password to login.
Now write without the quotes "startx" and press Enter. Once your session has launched (although it may not load all the element as the panel), you should see that your desktop is running "normally" with it's default resolution.
Now go back to tty1 (Press CTRL + ALT + F1) and press CTRL + ALT + DEL.
Your computer will reboot.

And as I expect (it worked for me), X11 will launch normally, and you won't see anymore that low graphics mode window.

---

### Post by nardusg on 2012-10-29
will try that, thanks. will give feedback.

---

### Post by Alexislavie on 2012-10-29
Ubuntu Forums now sucks, they modified Edit rules, you can't edit a post after 1 week.
I will move this thread elsewhere.

---

### Post by Niccola on 2012-10-29
Seems that problem is about xserver-xorg-intel package.

A workaround was proposed (By Nick Andrick) in [URL="https://bugs.launchpad.net/ubuntu/+bug/1068661"]this thread at launchpad bug
[/URL] 
I've tested and worked for me with an HD 6770M hybrid with Intel HD 3000

Access [THIS ppa link]("https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal") , click in [xserver-xorg-video-intel - 2:2.20.0-0~andrik1]("https://launchpad.net/%7Eandrikos/+archive/ppa/+sourcepub/2755647/+listing-archive-extra") to expand and download xserver-xorg-video-intel deb file for your architecture (amd64 or x86), you must download the 2 following files:

xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
and
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb
where XXX must me your architecture identifier (x86 or amd64)

Then open terminal and go to directory where files were downloaded, then type:
```
sudo dpkg -i xserver-xorg-video-intel*.deb
```after package installation, execute following command:
```
sudo dpkg-reconfigure Xorg
```reboot your machine and install amd fglrx driver

TIP: I've installed 12.11 beta and first time I execute 'sudo amdconfig --initial -f' command it returns me that my graphic card is not supported. But I've rebooted, then I logged in Ubuntu (also without Unity bars)

But don't worry, wait about 1 minute until finish loading your OS, then press CTRL + ALT + T  (to open terminal) and execute following commands:

```
sudo amdconfig --initial -f
sudo reboot
```Now everything works like a charm after rebooting...

---

### Post by nardusg on 2012-10-29
Oooooh wow man :)

That worked for me... Thanks a mil...

Now to peg the xserver-xorg-intel in synaptic.

nardusg@nar:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6700M Series
OpenGL version string: 4.2.11978 Compatibility Profile Context

I am on the 12.11 Beta driver.

---

### Post by Niccola on 2012-10-29
Did you report the same issue that happened with me?

I mean,
when you installed, amdconfig reported, at first time, your graphic card is not supported?

Also when you rebooted, did Unity loaded at first reboot?

---

### Post by nardusg on 2012-10-29
Mine loaded first time after creating aticonfig --initial -f

---

### Post by Niccola on 2012-10-29
> **nardusg said:**
> Mine loaded first time after creating aticonfig --initial -f

Ok,
That happened for me because I didn't installed dbg package first time.

Thanks for information =D
let's enjoy powerful of fglrx + Ubuntu  12.10 :guitar:

---

### Post by polyrhythmic on 2012-10-29
Between [**Niccola's comment #503**]("http://ubuntuforums.org/showpost.php?p=12324761&postcount=503") and the [**Unoffical CCHTML AMD/ATI wiki instructions**]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL"), gnome-shell is running like a charm on Quantal 12.10 with AMD 12.11 beta driver, on this Samsung Series 7 Chronos, HD6750M.

Many thanks to all.

---

### Post by sarvigalava on 2012-10-29
Thanks Nikola. Discrete card is working (6750m) but I cannot start xserver on integrated card (seg fault). Still better than nothing

---

### Post by dmoos on 2012-10-30
> **Alexislavie said:**
> Ubuntu Forums now sucks, they modified Edit rules, you can't edit a post after 1 week.
I will move this thread elsewhere.
@alexislavie
 
could you post a link where you move the thread to. just wanted to try your method and it didn't work for me, maybe after your update. thx

---

### Post by owkland on 2012-10-30
I installed as you did, then installed drivers as it shows on first post, and after restart it shows: Run in low-graphics   :(

Can you please make a full tutorial step by stept, please!:confused:

---

### Post by GDK2008UK on 2012-10-30
I am running AMD Phenom II X3 CPU with Nvidia 9500GT and no problems. I wonder if you guys that are having problems with AMDATI I don't know why you are having problems with these cards as Apple Corp uses these Graphics in their Apple Macs even their Power Tower system and they don't get any problems so why not get an Apple Powertower .

---

### Post by GDK2008UK on 2012-10-30
if I offended any one here then I apologize.

---

### Post by suprman2020 on 2012-10-31
> **Niccola said:**
> Seems that problem is about xserver-xorg-intel package.

A workaround was proposed (By Nick Andrick) in [URL="https://bugs.launchpad.net/ubuntu/+bug/1068661"]this thread at launchpad bug
[/URL] 
I've tested and worked for me with an HD 6770M hybrid with Intel HD 3000

Access [THIS ppa link]("https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal") , click in [xserver-xorg-video-intel - 2:2.20.0-0~andrik1]("https://launchpad.net/%7Eandrikos/+archive/ppa/+sourcepub/2755647/+listing-archive-extra") to expand and download xserver-xorg-video-intel deb file for your architecture (amd64 or x86), you must download the 2 following files:

xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
and
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb
where XXX must me your architecture identifier (x86 or amd64)

Then open terminal and go to directory where files were downloaded, then type:
```
sudo dpkg -i xserver-xorg-video-intel*.deb
```after package installation, execute following command:
```
sudo dpkg-reconfigure Xorg
```reboot your machine and install amd fglrx driver

TIP: I've installed 12.11 beta and first time I execute 'sudo amdconfig --initial -f' command it returns me that my graphic card is not supported. But I've rebooted, then I logged in Ubuntu (also without Unity bars)

But don't worry, wait about 1 minute until finish loading your OS, then press CTRL + ALT + T  (to open terminal) and execute following commands:

```
sudo amdconfig --initial -f
sudo reboot
```Now everything works like a charm after rebooting...

This seemed to work but then I started segfaults when I try to start the xserver on both the Intel and AMD graphics card.

---

### Post by ksanatos on 2012-11-01
Patch for x86-video-intel(for ubuntu xserver-xorg-video-intel) works. Install patched version of intel drivers, than install fglrx, than add in "/etc/X11/Xsession.d/10fglrx" this path ':/usr/lib/i386-linux-gnu/dri/'[FONT=Arial][SIZE=2][SIZE=2][SIZE=2][SIZE=2]. Works great, until reboot with enabled Intel video card, than system doesn't loading, even can't enter in tty. How can I solv it?
[/SIZE][/SIZE][/SIZE] [/SIZE][/FONT]

---

### Post by sarvigalava on 2012-11-01
> **ksanatos said:**
> Patch for x86-video-intel(for ubuntu xserver-xorg-video-intel) works. Install patched version of intel drivers, than install fglrx, than add in "/etc/X11/Xsession.d/10fglrx" this path ':/usr/lib/i386-linux-gnu/dri/'[FONT=Arial][SIZE=2][SIZE=2][SIZE=2][SIZE=2]. Works great, until reboot with enabled Intel video card, than system doesn't loading, even can't enter in tty. How can I solv it?
[/SIZE][/SIZE][/SIZE] [/SIZE][/FONT]

Same for me. OS hangs and doesn't  respond even to Cntrl+ alt+ del. Need to long press power button in order to shutdown laptop

---

### Post by ksanatos on 2012-11-01
I have really bad solution, but I can't make another, except waiting for fixing. It's make dual-boot two ubuntu, first for intel card, second for amd card. Some pieces can be combined, like /home folder, /var/cache/apt/archives folder, /opt, etc. Write couple script for syncing files. Really bad idea, but I don't know what to do, and I really need properly working both cards.

---

### Post by orbus on 2012-11-04
Hi,

I have a Dell Vostro 3550 Intel3000/AMD 6630M.

I use Ubuntu Gnome Shell Remix 64bit with Amd Catalyst 12.11 beta. 
My problem is when I exit from any 3D games which runs on full screen (for example: Trine2 of Torchlight) the screen starts flickering and I can stop flickering when I logout and login again. 

This problem is the same with older distros too. I used Ubuntu 12.04 with Unity/XFCE/KDE/Gnome-shell but the problem is the same?

Have anyone encountered this problem?

---

### Post by Carlos Araujo on 2012-11-06
not working for me!


AMD RADEON HD 7570M
INTEL HD 4000 

on Dell Inspiron 5423 14z

---

### Post by Rosterbyte on 2012-11-06
Someone can rewrite a guide for ubuntu 12.10? perhaps in a new topic?

---

### Post by ksanatos on 2012-11-12
There is another solution. [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Script_solution](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Script_solution)

---

### Post by beidl on 2012-11-13
For those of you still rocking Ubuntu 12.04, I've created a little indicator applet for you guys!

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

Not only does it allow switching the GPU from within the panel, but it also works around a bug where 32 bit OpenGL games were not able to be played while running the integrated GPU.
Please test it and report bugs.
This also includes a Xsession script so you will never have to modify the 10fglrx script again! :-D

---

### Post by Penguissimo on 2012-11-13
> **beidl said:**
> For those of you still rocking Ubuntu 12.04, I've created a little indicator applet for you guys!

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

Not only does it allow switching the GPU from within the panel, but it also works around a bug where 32 bit OpenGL games were not able to be played while running the integrated GPU.
Please test it and report bugs.
This also includes a Xsession script so you will never have to modify the 10fglrx script again! :-D

This is an awesome idea, and thanks for your effort! Unfortunately I used this once, and now when I log in with the discrete card activated, I'm forced into Unity 2D. This persists even across a removal of xorg.conf and a purge and reinstall/reconfiguration of fglrx. Any ideas as to what I can do to fix this?

edit: I poked around like a blind idiot for a while, and it seems to be related to the creation/existence of /etc/ld.so.conf.d/multiarchfix.conf. I'm in way over my head here, but removing that file manually and running aticonfig --px-dgpu got things working again. Is this a bug, or did I just do something monumentally stupid by accident? (I'm working on the assumption that it's the latter :))

---

### Post by beidl on 2012-11-14
> **Penguissimo said:**
> This is an awesome idea, and thanks for your effort! Unfortunately I used this once, and now when I log in with the discrete card activated, I'm forced into Unity 2D. This persists even across a removal of xorg.conf and a purge and reinstall/reconfiguration of fglrx. Any ideas as to what I can do to fix this?

edit: I poked around like a blind idiot for a while, and it seems to be related to the creation/existence of /etc/ld.so.conf.d/multiarchfix.conf. I'm in way over my head here, but removing that file manually and running aticonfig --px-dgpu got things working again. Is this a bug, or did I just do something monumentally stupid by accident? (I'm working on the assumption that it's the latter :))

This file usually should be removed when switching to the DGPU using the indicator (in /usr/lib/amdindicator/dgpuon). I'll take a look at it.

---

### Post by Penguissimo on 2012-11-16
beidl very generously helped me work through all of the stupid things I had done to cause my problem, and as a result, things are working perfectly now! This is a VERY handy little piece of software!

---

### Post by emgiezet on 2012-11-16
> **Niccola said:**
> Seems that problem is about xserver-xorg-intel package.

A workaround was proposed (By Nick Andrick) in [URL="https://bugs.launchpad.net/ubuntu/+bug/1068661"]this thread at launchpad bug
[/URL] 
I've tested and worked for me with an HD 6770M hybrid with Intel HD 3000

Access [THIS ppa link]("https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal") , click in [xserver-xorg-video-intel - 2:2.20.0-0~andrik1]("https://launchpad.net/%7Eandrikos/+archive/ppa/+sourcepub/2755647/+listing-archive-extra") to expand and download xserver-xorg-video-intel deb file for your architecture (amd64 or x86), you must download the 2 following files:

xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
and
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb
where XXX must me your architecture identifier (x86 or amd64)

Then open terminal and go to directory where files were downloaded, then type:
```
sudo dpkg -i xserver-xorg-video-intel*.deb
```after package installation, execute following command:
```
sudo dpkg-reconfigure Xorg
```reboot your machine and install amd fglrx driver

TIP: I've installed 12.11 beta and first time I execute 'sudo amdconfig --initial -f' command it returns me that my graphic card is not supported. But I've rebooted, then I logged in Ubuntu (also without Unity bars)

But don't worry, wait about 1 minute until finish loading your OS, then press CTRL + ALT + T  (to open terminal) and execute following commands:

```
sudo amdconfig --initial -f
sudo reboot
```Now everything works like a charm after rebooting...


Dude you've saved my life and gaming on ubuntu 12.10 :)

---

### Post by ivoSmash on 2012-11-17
Thank you very much!!! It worked! One headache less. Thanks!

---

### Post by ivoSmash on 2012-11-17
Excuse me! I have a problem. constantly I have to restart de notebook because there is an update. I repeated step 2 a couple of times and I cant solve it. please help!!! i have a 64bit system.

---

### Post by Bordee on 2012-11-18
I also used Niccola's solution from post 503 to install Catalyst on Ubuntu 12.10 on my HP dv6t with hybrid Intel 3000/AMD 6700 radeon integrated graphics. I appreciate this good work as getting Catalyst to work on my HP dv6t has been a nightmare. Thanks again.


I was able to install the vanilla fglrx-updates through Synaptic, and I didn't need to do a manual install of the AMD driver from their web site.

One very important note. Using the patched Intel driver from the PPA referred to in Niccola's post is, at least for now, critical. I mistakenly did an apt-get update after installing Catalyst and getting it to work, and a non-patched version of the Intel drivers got updated. On reboot, I couldn't get X to start. I then reinstalled the patched drivers, followed the instructions in post 503 and PINNED the two intel drivers in Synaptic to prevent them from getting updated. After pinning, I was able to update my system without any corresponding Catalyst problems.

---

### Post by rebornishard on 2012-11-19
> **orbus said:**
> (Vostro 3550 / AMD 6630M)

I tried with this solution: [http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html](http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html)

with latest Catalyst 12.08 / 12.09 / 12.10 but the result is the same, not working :confused:

Do I have to back to 12.04 ... ?

:lolflag: i update to 12.10 too, me with (Vostro 3450/ AMD 6630M)
install 12.10 viola, i got blank and broken desktop

---

### Post by ksanatos on 2012-11-22
Script for Intalling & Uninstalling Amd Catalyst drivers.
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Script_solution](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Script_solution)

---

### Post by miatawnt2b on 2012-11-30
Is anyone else having problems with the integrated intel gpu in 64bit quantal?

I am using catalyst 12.11b8 (have tried older versions as well) and the andrik ppa for the xserver intel piece.  dgpu works fantastic, but if I switchto igpu, my system locks up at boottime about 9 out of 10 times.

Any ideas?
-J

---

### Post by nawrot on 2012-12-03
Thanks, this solution works for:

DELL inspiron 7520 SE

ps.
I used 12.10 ADM  drivers instead of 12.04

---

### Post by lachoneus on 2012-12-03
Working great on my HP Envy 15 3033cl with Radeon HD 7690M/Intel.

Running Kubuntu 12.10

Thank you!

Note:

I have ran into this little problem twice, and have stumbled onto the solution twice after finding no answers for it on the internet.  Probably because most of the users are installing through Ubuntu, and not Kubuntu.

After I install the catalyst driver and I check to make sure that I am switched to the AMD GPU, I run the "glxgears" demo.  The demo starts, but there isn't any movement, it just sits still.  If you grab the window and move it around, then you can see the gears moving. The same thing happens with Blender, a 3D modeling and rendering program.

After days of frustration, and no answers to my problem online, I stumbled on the problem.  Under System Settings>Desktop Effects>Advanced(tab)>,  the "Compositing Type" was set to xRender.  After switching this to OpenGL everything begins working as it should.  I guess this makes sense, since both of these applications are OpenGL dependent.

My guess is after first installing Kubuntu it defaults to xRender compositing, seeing that it couldn't install any additional drivers during the OS installation.  If I do a fresh install in the near future, I will keep an eye on this.

If you are trying to install the catalyst driver on Kubuntu 12.10, and you run into this problem, I hope this helps.

---

### Post by markackerman8@gmail.com on 2012-12-03
FINALLY a working Ubuntu :guitar:

   Kubuntu 12.10 : (same as Ubuntu 12.10) seems to be why Muxless cards works Finally after 11 months of trying every combination of proprietery driver installation and Open Source mesa drivers. And being stuck in windows.  Note it is ONLY with the Open Source Mesa Drivers, not the FGLRX drivers from either "Additional Drivers", or Downloaded and compiled from AMD's website.
   Until now it has been uselessly flickering like hell - at best, or unable to login with "X", at worst.  And any 3d rendering -was MINIMAL at best so that even Unity couldn't run in my HP Envy 17-2196ca - Top of the LINE $2000 computer, and Games - Not A chance to even load a screen.
Some Details
- Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
- [ATI/ Mobility Radeon HD 6850m Series], 
  - Kernel module - radeon
  - OpenGL/ES version - 3.0 Mesa 9.1-devel (git-54ff536 quantal-oibaf-ppa)
- Kubuntu 12.10 - linux kernel 3.6.8

 
• 3.0 Mesa 9.0 Nov, 2012,    latest 9.1 is bleeding edge! - Awesome
&#8728; Now - OpenGL/ES version - 3.0 Mesa 9.1-devel (git-54ff536 quantal-oibaf-ppa), after
&#8227; - sudo add-apt-repository ppa:oibaf/graphics-drivers
• and as a Diff., WAS ABLE TO GO FROM MEDIUM TO HIGH EFFECTS IN GAME - League of Legends - very high still bad (windows handled it well)
• Fglrx driver on benchmark website shows 100-300% better performance, though the open source is catching up with -10-50% better with Git version 3.1 Mesa vs 3.0
• Ubuntu - kernel linux 3.5.0-19 - 2012-Oct-12,    latest stable 3.6 - 2012-Nov-26 - awesome, and made League of Legends run even noticable better.

I will try yet again the Fglrx drivers now that 12.10 ubuntu is so functional.  
and Note **KDE in Kubuntu is made for better 3D gaming Support with their Plasm Desktop setup, and has finally got me switched from Gnome - and it is turning out to be way more forward thinking and in the mind of high perfrmance desktop and gaming computer - putting unity and gnome to shame!!

Good Luck 
and any questions feel free o contact me
Mark
markackerman8(at)gmail.com

---

### Post by beidl on 2012-12-03
I was able to get a (almost) perfectly working Quantal setup on my HP ProBook 4730s (HD 3000 + Radeon 6470M), did a direct upgrade from Precise.
Before upgrading, I purged fglrx from my system, also removed the xorg.conf by hand of course.
Upgraded Precise -> Quantal and reboot.
Then I added Nick Andrik's ppa, updating and upgrading the packages.
```
sudo add-apt-repository -y ppa:andrikos/ppa && sudo apt-get update && sudo apt-get upgrade
```
The packages "xserver-xorg-video-intel" and "xserver-xorg-video-intel-dbg" should be upgraded to Nick's compatible ones afterwards.
I pinned those packages by modifying/creating the file /etc/apt/preferences. "What's the content of that file?" you might ask.
```
Package: xserver-xorg-video-intel
Pin: version 2:2.20.9-0ubuntu2+andrik2
Pin-Priority: 1001

Package: xserver-xorg-video-intel-dbg
Pin: version 2:2.20.9-0ubuntu2+andrik2
Pin-Priority: 1001

```

Now, because why not, it's time to install pending SRU's to our system.

```
sudo add-apt-repository -y ppa:unity-team/sru && sudo apt-get update && sudo apt-get upgrade
```
This upgrades your Unity and Compiz packages to newer ones which have fixes for unredirected rendering.
Those fixes will be merged into the mainline Unity and Compiz sources, but we are bleeding edge people, right?
Useful if you are in the Steam for Linux Beta but you don't want to leave Unity just for gaming!

Then I've added the xorg edgers ppa and upgraded packages again.
```
sudo add-apt-repository -y ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

NOTE: If your Linux kernel doesn't get updated automatically, install it manually with "sudo apt-get install linux".
In case some dependencies are missing, use autocomplete in the terminal to install the 3.7 image and header files.
At the time of this post, the newest version should be 3.7.0-4-generic.

NOW IT'S TIME TO INSTALL THAT SON OF A BAD MOTHER CALLED FGLRX!

NOTE: If you are in the Steam for Linux Beta, you might want to download the fglrx version 9.010 beta, NOT beta 8.
Beta 8 has a known problem which causes Steam to segfault. In that case, download that older version,
build the packages manually, install them using standard "dpkg -i" procedures AND pin all the fglrx packages in /etc/apt/preferences.

But if you don't care about all that fancy stuff:
```
sudo apt-get install fglrx fglrx-dev; sudo amdconfig --initial -f; sudo amdconfig --px-dgpu
```
Also, do the usual 10fglrx modifications (or you use my xsession script from my github repo... or even better, install my [AMD Indicator applet]("https://github.com/beidl/amd-indicator") :D).
NOTE: If the installation fails, fglrx has not been patched with kernel 3.7 compatibility.
That means you would have to patch one of fglrx's files.
```
sudo ln -s /usr/src/linux-headers-3.7.0-4-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.0-4-generic/include/linux/version.h
cd ~
wget http://catalyst.apocalypsus.net/files/arch-fglrx-3.7.patch
cd /usr/src/fglrx-9.010/
sudo patch < ~/arch-fglrx-3.7.patch
sudo apt-get install -f
sudo amdconfig --initial -f; sudo amdconfig --px-dgpu

```
Everything should be fine now... except of a few discrepancies.

I've noticed that the IGPU would hang after a few minutes of using. I'm not sure how exactly I got rid of this, but my combination of 
tweaks consists of a few kernel argument tweaks and setting compiz's refresh rate to 59 rather than 60 (using ccsm of course).
My kernel arguments in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 i915.semaphores=1 pcie_aspm=force acpi_osi=Linux reboot=acpi"
```
I'm not sure when I'll hit a GPU hang again, but in case it hits you, just "CTRL-ALT-F1" into tty1, wait a few seconds, or even login in this bash 
and get the dmesg output for further inspection. Then just go back to tty7 using "CTRL-ALT-F7".
I've been able to write this post without a single GPU hang, even when provocating the system with a lot of window movements,
workspace switches and window spread madness.

The only 3 minor problems which I'm facing now: 
1) I shut down my laptop with the IGPU being activated. After a few hours (mostly over night) I try to boot into Ubuntu again, but it hangs at the splash screen, 
probably just before handing over the display 'n stuff to X.
In that case, I hard reset my laptop by long-pressing the power button and boot up again. It should work then.

2) Also with the IGPU being activated, starting the Catalyst Control Center causes the X server to be killed, so I have to log back in.
If you want to switch the active GPU, either use a Terminal or my indicator.

3) Using my indicator, switching from the IGPU to the DGPU, the DGPU isn't being picked up after the X server is killed. Workaround in my AMD Indicator:
Replacing "sudo pkill X" with "sudo reboot" in my /usr/lib/amdindicator/*gpuon scripts.

It worked after a lot of trial and error, but now everything seems to work fine. I'm a pretty happy camper now!
I'm even running the latest stable kernel now, which is awesome if you are after that bleeding edge Linux crack.

If you are brave enough to try it, tell me if it worked for you. :D

---

### Post by markackerman8@gmail.com on 2012-12-03
I just tried  my hundreth attemp to install Fglrx drivers after seeing some optimism from Nicola's Intel fix from Post #503.  I installed the to .deb packages but they weren't the:
xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
and
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb

as the link only has these now:
xserver-xorg-video-intel_2.20.9-0ubuntu2+andrik2_amd64.deb 
and 
xserver-xorg-video-intel-dbg_2.20.9-0ubuntu2+andrik2_amd64.deb

I installed them and rebooted without his next command:
sudo dpkg-reconfigure Xorg
which failed in starting in Terminal mode (no X) and luckily I had another compter to find my error so ran the aforemntiond config command from termianl, with no errors but still couldn't get to the login screen.  It gets close but then goes to a black terminal type screen w text login - arghhhh.  removing xorg.conf doesn'y help this time either.  I wish i had a tutor for this 11 months and still no fglrx driver.

I am trying yet another reinstall and will use a ppa for the andrik1  !!!! and update it (xserver-xorg-video-intel) through synaptik, and do a restart aafter a 
# sudo dpkg-reconfigure Xorg   - I guess
and then try my last fglrx attempt (12.10 again) for the next 2 months argghhh.  Unless anyone has any new ideas.  I get immediate email notification so I will respond quickly to any suggestions. And of course if I get it working I will indeed report it and how I did it.

Cheers, Mark

p.s. I will try EVERYTHING I can mange in the above post I just read - though I don't understand half of it -

 wish me luck Beidl

---

### Post by markackerman8@gmail.com on 2012-12-03
Beidl HELP !!!!!!!!!!!!!!!!
I did everything you said up to the point of installing the fglrx drivers, and then <i did a reboot for good measure, and everything seemed soooo good, up to date everything went so well !!!!!!!!

then it after the fglrx and a reboot, the <<<<kubuntu screen teawsed me that it was going to get to the loginscreen  but then bammmmm
black login terminal type screen AGAIN 

HELP !!!!!!!!!!!!!!!!!!!!!!!!!!!!

I will try anything to get back into Ubuntu - I hate windows !

Thanks in advance, Mark

---

### Post by beidl on 2012-12-04
> **markackerman8@gmail.com said:**
> Beidl HELP !!!!!!!!!!!!!!!!
I did everything you said up to the point of installing the fglrx drivers, and then <i did a reboot for good measure, and everything seemed soooo good, up to date everything went so well !!!!!!!!

then it after the fglrx and a reboot, the <<<<kubuntu screen teawsed me that it was going to get to the loginscreen  but then bammmmm
black login terminal type screen AGAIN 

HELP !!!!!!!!!!!!!!!!!!!!!!!!!!!!

I will try anything to get back into Ubuntu - I hate windows !

Thanks in advance, Mark

Which GPU did you activate prior to reboot?
Also, which FGLRX version did you install?

EDIT: Apply the patch to fglrx and run the following command in tty1 (CTRL-ALT-F1):
```
sudo dpkg-reconfigure fglrx; sudo amdconfig --px-igpu
```
Shutdown, pull your battery for a few seconds, turn on.
You should boot into the login screen. Log in, and switch to the DGPU:
```
sudo amdconfig --px-dgpu; sudo reboot
```

---

### Post by huxtee on 2012-12-04
Hi Beidu, I have followed your instruction but things didn't turn out so well. After installing the beta catalyst drivers upon rebooting, xorg seems to have broke. I managed to purge fglrx and delete xorg.conf and get the gui working again but unity is not working.

Im using a dell inspiron 5520 with an i5(intergrated HD4000) and 7600m graphics.

Kernal
```
brian@brian-inspiron5520:~$ uname -a
Linux brian-inspiron5520 3.7.0-4-generic #12-Ubuntu SMP Wed Nov 28 09:30:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

X
```
brian@brian-inspiron5520:~$ X -version

X.Org X Server 1.13.0.901 (1.13.1 RC 1)
Release Date: 2012-11-22
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
Current Operating System: Linux brian-inspiron5520 3.7.0-4-generic #12-Ubuntu SMP Wed Nov 28 09:30:01 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-4-generic root=UUID=ff1fc86f-2930-4c2a-9f29-63733532ac52 ro quiet splash vt.handoff=7
Build Date: 23 November 2012  10:45:25AM
xorg-server 2:1.13.0.901+git20121123+server-1.13-branch.c0e68f8e-0ubuntu0ricotz~quantal (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.26.0
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

Here's the output from installing fglrx
```
brian@brian-inspiron5520:~/Downloads$ sudo dpkg -i fglrx_9.010-0ubuntu1_amd64.deb 
Selecting previously unselected package fglrx.
(Reading database ... 290438 files and directories currently installed.)
Unpacking fglrx (from fglrx_9.010-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:9.010-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-9.010 DKMS files...
First Installation: checking all kernels...
Building only for 3.7.0-4-generic
Building for architecture x86_64
Building initial module for 3.7.0-4-generic
ERROR (dkms apport): kernel package linux-headers-3.7.0-4-generic is not supported
Error! Bad return status for module build on kernel: 3.7.0-4-generic (x86_64)
Consult /var/lib/dkms/fglrx/9.010/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.7.0-4-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```


Please tell if you need any more details, thanks.
Brian Huxtable

---

### Post by MikeCyber on 2012-12-04
I use a Nvidia but only a quick look and I saw some errors:

Consult /var/lib/dkms/fglrx/9.010/build/make.log

---

### Post by huxtee on 2012-12-04
> **MikeCyber said:**
> I use a Nvidia but only a quick look and I saw some errors:

Consult /var/lib/dkms/fglrx/9.010/build/make.log

make.log
```
DKMS make.log for fglrx-9.010 for kernel 3.7.0-4-generic (x86_64)
Wed Dec  5 02:47:49 EST 2012
AMD kernel module generator version 2.1
kernel includes at /lib/modules/3.7.0-4-generic/build/include not found or incomplete
file: /lib/modules/3.7.0-4-generic/build/include/linux/version.h

```

I'm confused :(

---

### Post by beidl on 2012-12-04
It appears to me that you did not run this command...
```
sudo ln -s /usr/src/linux-headers-3.7.0-4-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.0-4-generic/include/linux/version.h

```

EDIT: maybe I pasted the wrong symlink command, posted tested one.

I've uploaded a patched version of AMDs newest fglrx drivers which works with Steam.
Of course, do the symlinking before installing it with "dpkg -i fglrx*.deb"
[http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs](http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs)

---

### Post by markackerman8@gmail.com on 2012-12-04
> **beidl said:**
> It appears to me that you did not run this command...
```
sudo ln -s /usr/src/linux-headers-3.7.0-4-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.0-4-generic/include/linux/version.h

```

EDIT: maybe I pasted the wrong symlink command, posted tested one.

I've uploaded a patched version of AMDs newest fglrx drivers which works with Steam.
Of course, do the symlinking before installing it with "dpkg -i fglrx*.deb"
[http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs](http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs)

Beidl - You Rock

i just spent a half hour w a Linux guru going over your suggestions, and am left with a renewed optimism that this 11 month issue may finally have a resolution BECAUSE of YOU.  I will be home in the hour and will do everything you said after from a fresh install - yet again.  I SURE HOPE YOU ARE MY SAVIOUR IN THIS WORKS !!!!!

I will keep you apprised of both success or lack there of, and thanks again,
Mark

---

### Post by markackerman8@gmail.com on 2012-12-05
well Beidl, 

no luck - ARGHHHHHHH - everything up to amdconfig....went painfully but successfully- but after it, it either went to terminal, or after a very basic Xorg.conf file I manually wrote it just went to a grey screen.  Deleting the file allows me to get into Kubuntu, and lshw recognizes the fglrx driver (Your version - patched, was installed), but it certainly isnt functioning.  Assume I did eeverthing you said and alittle more too.  Wow, at least it installed and allowed a reboot, and just the config process is screwing it up.  

Is it hopeless, at this point? - or do You by chance have any other ideas.  I sure thought this might work especially with yor extensive installation, and our similar systems - mine an HP Envy 17-2195 Intel HD3000/amd-Radeon 6850m,  Any nore help will wure be appreciated - I will try anything.

Mark
p.s. sorry I an not giving you all the details - as I am exhausted

---

### Post by beidl on 2012-12-05
> **markackerman8@gmail.com said:**
> well Beidl, 

no luck - ARGHHHHHHH - everything up to amdconfig....went painfully but successfully- but after it, it either went to terminal, or after a very basic Xorg.conf file I manually wrote it just went to a grey screen.  Deleting the file allows me to get into Kubuntu, and lshw recognizes the fglrx driver (Your version - patched, was installed), but it certainly isnt functioning.  Assume I did eeverthing you said and alittle more too.  Wow, at least it installed and allowed a reboot, and just the config process is screwing it up.  

Is it hopeless, at this point? - or do You by chance have any other ideas.  I sure thought this might work especially with yor extensive installation, and our similar systems - mine an HP Envy 17-2195 Intel HD3000/amd-Radeon 6850m,  Any nore help will wure be appreciated - I will try anything.

Mark
p.s. sorry I an not giving you all the details - as I am exhausted

Did you edit the 10fglrx file?
If not, get my Xsession script which does the same:
```
cd /etc/X11/Xsession.d/
sudo wget https://github.com/beidl/amd-indicator/raw/master/11switchable

```
And reboot.

---

### Post by markackerman8@gmail.com on 2012-12-05
> **beidl said:**
> Did you edit the 10fglrx file?
If not, get my Xsession script which does the same:
```
cd /etc/X11/Xsession.d/
sudo wget https://github.com/beidl/amd-indicator/raw/master/11switchable

```
And reboot.
  Thanks Beidle for the Continued Help !!

  No I din't have a clue what that 10fglrx file referred to.  I will try what you just posted now and edit the results.
  And please be as explicit as possible with the instructions as I am rusty w Linux as this problem has shoved me back inot Windows for the past 11 1/2 months arghhhhh.  But I Do know how to cut and past commands in terminal - :p

and for othersw reading this here is the content of the file he uploaded "11switchable"
---------------------------------
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib/x86_64-linux-gnu/dri:/usr/lib/i386-linux-gnu/dri
export LIBGL_DRIVERS_PATH
---------------------------------

Mark
note: I am not surprised that I still couldnt login as I had made a minimal Xorrrg.conf file - as a desperate attempt to get it working last night.  So now I have deleted eevery Xorg.conf type file which I am sure willlet me in (as it's the sudo amdconfig --initial -f; sudo amdconfig --px-dgpu) that always kills it - so I guess once I am back in - I will try ..
sudo amdconfig --initial -f; sudo amdconfig --px-igpu
in hopes that at least with the integrated card I might have a better chance (and with Beidl's script for the /etc/X11/Xsession.d/10fglrx already installed) Lets hope it's a miracuous day !!
I will edit it again either way,
Cheers

OK I am about to do it I Just did the DREADED !!!!!
             sudo amdconfig --initial -f
which always hoses my reboot, so before I reboot I thought i would show you the resulting Xorg.conf, that invariably screws my reboot
(note - I also will do: 
             sudo amdconfig --px-igpu,  before I reboot - wish me Luck.)
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
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

---

### Post by UbuntAlbania on 2012-12-05
nice one bro :) thanks

---

### Post by huxtee on 2012-12-05
> **beidl said:**
> It appears to me that you did not run this command...
```
sudo ln -s /usr/src/linux-headers-3.7.0-4-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.0-4-generic/include/linux/version.h

```

EDIT: maybe I pasted the wrong symlink command, posted tested one.

I've uploaded a patched version of AMDs newest fglrx drivers which works with Steam.
Of course, do the symlinking before installing it with "dpkg -i fglrx*.deb"
[http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs](http://ubuntuone.com/7D7u8DgDzIAaC4qokYbUzs)

Hi Beidl I have tried the process again from the beginning,
I have upgraded x-org, unity, and linux kernals from the PPAs
ppa:andrikos/ppa
ppa:unity-team/sru
ppa:xorg-edgers/ppa

but when I reboot and log in every thing seems ok except their is no unity.
```
brian@brian-inspiron5520:~$ unity
The program 'unity' is currently not installed. You can install it by typing:
sudo apt-get install unity
brian@brian-inspiron5520:~$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libunity-core-6.0-5 (= 6.12.0+bzr2799sruubuntu0+806) but it is not going to be installed
         Depends: libunity-protocol-private0 (>= 6.12.0) but 6.10.0+bzr188sruubuntu0+152 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by markackerman8@gmail.com on 2012-12-06
Still goes to tty1 instead of the login screen after amd config and a reboot- ARGHHHHHHH

Anything else I can try,  ANYTHING????????????????????? snif, snif 

Desperately, Mark



> **markackerman8@gmail.com said:**
> Thanks Beidle for the Continued Help !!

  No I din't have a clue what that 10fglrx file referred to.  I will try what you just posted now and edit the results.
  And please be as explicit as possible with the instructions as I am rusty w Linux as this problem has shoved me back inot Windows for the past 11 1/2 months arghhhhh.  But I Do know how to cut and past commands in terminal - :p

and for othersw reading this here is the content of the file he uploaded "11switchable"
---------------------------------
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib/x86_64-linux-gnu/dri:/usr/lib/i386-linux-gnu/dri
export LIBGL_DRIVERS_PATH
---------------------------------

Mark
note: I am not surprised that I still couldnt login as I had made a minimal Xorrrg.conf file - as a desperate attempt to get it working last night.  So now I have deleted eevery Xorg.conf type file which I am sure willlet me in (as it's the sudo amdconfig --initial -f; sudo amdconfig --px-dgpu) that always kills it - so I guess once I am back in - I will try ..
sudo amdconfig --initial -f; sudo amdconfig --px-igpu
in hopes that at least with the integrated card I might have a better chance (and with Beidl's script for the /etc/X11/Xsession.d/10fglrx already installed) Lets hope it's a miracuous day !!
I will edit it again either way,
Cheers

OK I am about to do it I Just did the DREADED !!!!!
             sudo amdconfig --initial -f
which always hoses my reboot, so before I reboot I thought i would show you the resulting Xorg.conf, that invariably screws my reboot
(note - I also will do: 
             sudo amdconfig --px-igpu,  before I reboot - wish me Luck.)
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
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

---

### Post by beidl on 2012-12-06
> **huxtee said:**
> Hi Beidl I have tried the process again from the beginning,
I have upgraded x-org, unity, and linux kernals from the PPAs
ppa:andrikos/ppa
ppa:unity-team/sru
ppa:xorg-edgers/ppa

but when I reboot and log in every thing seems ok except their is no unity.
```
brian@brian-inspiron5520:~$ unity
The program 'unity' is currently not installed. You can install it by typing:
sudo apt-get install unity
brian@brian-inspiron5520:~$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libunity-core-6.0-5 (= 6.12.0+bzr2799sruubuntu0+806) but it is not going to be installed
         Depends: libunity-protocol-private0 (>= 6.12.0) but 6.10.0+bzr188sruubuntu0+152 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Do you have any ppa's that contain modified unity versions? I can't imagine there would be dependency problems because would have them as well.

@markackerman8@gmail.com, as long as both 10fglrx and 11switchable are in the Xsessions.d folder, there shouldn't be any problem. Maybe pull the power once because that's what I had to do.
Maybe you guys can retry this without the Unity SRU ppa.
And as long as you pin the packages, there should be no issue when an upgrade tries to overwrite the modified intel xorg drivers.

---

### Post by markackerman8@gmail.com on 2012-12-06
[QUOTE=beidl

@markackerman8@gmail.com, as long as both 10fglrx and 11switchable are in the Xsessions.d folder, there shouldn't be any problem. Maybe pull the power once because that's what I had to do.
Maybe you guys can retry this without the Unity SRU ppa.
And as long as you pin the packages, there should be no issue when an upgrade tries to overwrite the modified intel xorg drivers.[/QUOTE]

Thanks again Beidle,  ):P
w.r.t. the unity ppa - it is the only thing which seemed odd to me in your initial instructions (the only thing I understood - anyway).  Another odd thing, is that though I do have a /etc/X11/Xsessions.d/10fglrx file though it is a type of a shortcut, as it is only 0 kBs, and in properties says it points to: /etc/alternatives/x86_64-linux-gnu_10fglrx, 
   which is also a "pointer" and in turn points to: /usr/lib/fglrx/10fglrx,
Which is finally a "text" type file and its' contents are:

LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
	LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH 

   This code means little to me, though may help you understand what is hanging my system with the fglrx drivers installed "and more importantly configured".  Wow and I thought with you having such great knowledge, and a similar System that we might be able to finally get my discrete card functional arghh. 
Both: HP, Intel HD3000, 6850m (6000 series), muxless, and Kubuntu 21.10 with bleeding edge Kernel 3.7.0... 

   I will give it your new suggestion a try ("retry this without the Unity SRU ppa"), though I don't know how it will effect my Kubuntu "Unity-Less" system.  I guess you mean a New fresh re-install of Kubuntu 12.10 yet again, huh.  Well why not? Anything to get this working.

   If you have any troubleshooting steps you would like to have me try - I will try Anything Beidl.  Especially if it would help me understand this 12 moth old Nightmare a little better in the process.

Mark
[email]markackerman8@gmail.com[/email]
and feel free to email me directly - And for those interested in the development of this -  I promise to post a complete solution if EVER it gets solved.
edit **
I researched the 10fglrx file issue and google referred me back to this websites first page Step 2:
"STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :"
WHICH I HAVE NEVER DONE !!!!!!!!!!! this would be a HUGE error on my part should it prove to be why I have 11 months of Disfunctionality - WOW - Wish me luck

---

### Post by beidl on 2012-12-07
> **markackerman8@gmail.com said:**
> 
edit **
I researched the 10fglrx file issue and google referred me back to this websites first page Step 2:
"STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :"
WHICH I HAVE NEVER DONE !!!!!!!!!!! this would be a HUGE error on my part should it prove to be why I have 11 months of Disfunctionality - WOW - Wish me luck

Make sure to first try the tutorial on the first page with Ubuntu 12.04 with Catalyst 12.9 (all newer versions have problems from my testing)

---

### Post by markackerman8@gmail.com on 2012-12-07
> **beidl said:**
> Make sure to first try the tutorial on the first page with Ubuntu 12.04 with Catalyst 12.9 (all newer versions have problems from my testing)

Beidl :guitar:
you rock, thanks.  I was just about to try a new install after thelast changes didnt alow me toget to the login screan withough deleting xorg.cong with iether Igpu or dgpu active arghhhh.  But I sure will try with what you suggested.   am happy to change a few things up.  I am going to stick with Kununtu though unless you offer any reason to the contrary - Unity SUCKS !!! LOL

Thanks, Mark

---

### Post by beidl on 2012-12-07
> **markackerman8@gmail.com said:**
> Beidl :guitar:
you rock, thanks.  I was just about to try a new install after thelast changes didnt alow me toget to the login screan withough deleting xorg.cong with iether Igpu or dgpu active arghhhh.  But I sure will try with what you suggested.   am happy to change a few things up.  I am going to stick with Kununtu though unless you offer any reason to the contrary - Unity SUCKS !!! LOL

Thanks, Mark

If everything goes right, you'd have to the following just to be safe:
[http://www.kubuntuforums.net/showthread.php?50876-RESOLVED-Desktop-Effects-won-t-stay-on&p=242611&viewfull=1#post242611](http://www.kubuntuforums.net/showthread.php?50876-RESOLVED-Desktop-Effects-won-t-stay-on&p=242611&viewfull=1#post242611)
Else, the effects settings won't stay turned on after a log out (of course, that's another big problem with fglrx)

---

### Post by markackerman8@gmail.com on 2012-12-07
> **beidl said:**
> If everything goes right, you'd have to the following just to be safe:
[http://www.kubuntuforums.net/showthread.php?50876-RESOLVED-Desktop-Effects-won-t-stay-on&p=242611&viewfull=1#post242611](http://www.kubuntuforums.net/showthread.php?50876-RESOLVED-Desktop-Effects-won-t-stay-on&p=242611&viewfull=1#post242611)
Else, the effects settings won't stay turned on after a log out (of course, that's another big problem with fglrx)

Beidl,
Thanks for sticking with the "CAUSE". so far as ALWAYS -always always, and I mean Always (11 months with a renewed attempt every month or two and hundreds of hours - EVERY TIME - as soon as I:
        sudo aticonfig --initial -f
	sudo reboot
The installation is screwed and only reboots into tty1, the only solution EVER (so far) at this point is to delete the xorg.conf file, and reboot.  

Can anyone help me troubleshoot my fglrx problem?

I would be happy to list re4sults from:
  sudo lshw | less
  dmesg | grep drm
  glxinfo | egrep render
         or ANY OTHER COMMAND  - AS I DON'T KNOW MUCH ?

PLEASE !!!!! and THANKS.

Mark,
  p.s. Beidl - of course I will try your last suggestion - but I am quite certain - that compositing - enabled or disabled in Compiz is the least of my worries.  If I could see Compiz at all I would be elated :p

edit:
tried to get back into Kubuntu with fglrx driver installed but not configured (no xorg.conf) again, which usually is no problem - and now a new thing ... It starts up w a black screen (I hear it logging in - ODD?).  Tried everything (all fail safe modes and tty1 update/upgrade, and a few other things - no luck.  Oh well what's another day without a new install of Kubuntu (insert sarcastic grin here)
  At this point I refuse to try a reinstall unless anyone has any new suggestions - PLEASE !!!!!!!!!!!!!!!!!!!!!!!

---

### Post by shinylenin on 2012-12-08
So, where to start...?

First of all thanks to all of you, this thread made my life with my HP dv6-6180eg much more easier!

I have an Intel3000/HD6770M and only with the 12.11 beta drivers I could get my HP work properly. 

But I have one issue: I can't toggle the screen backlight, but I found a fix to it:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

The thing now is that I neither can swith off nor reboot my dv6. Even when I get rid of those arguments in my /etc/default/grub file, I can't do it. 

Does anyone have a fix to this? This is the only thing which doesn't work on my dv6...

Thanks in advance!

---

### Post by markackerman8@gmail.com on 2012-12-08
Shinylenin,
Being a fellow HP user (mine HP Envy 17-2195), did you do anything special to get the proprietary drivers to work, as NO MATTER what I try I can't restart "X", after aticonfig - 11 months of trying and continuing - arghhh.
Thanks, Mark

---

### Post by shinylenin on 2012-12-08
> **markackerman8@gmail.com said:**
> Shinylenin,
Being a fellow HP user (mine HP Envy 17-2195), did you do anything special to get the proprietary drivers to work, as NO MATTER what I try I can't restart "X", after aticonfig - 11 months of trying and continuing - arghhh.
Thanks, Mark

Hey Mark,

I am not sure if I can help you with your problem, but I can at least tell you how I got my HP to work.


[LIST=1]
[*]I made a fresh install and did an update
[*]Then I excecuted this command from beidl's [post]("http://ubuntuforums.org/showpost.php?p=12386383&postcount=536"): ```
sudo add-apt-repository -y ppa:andrikos/ppa && sudo apt-get update && sudo apt-get upgrade
``` to update the drivers for the integrated Intel chip. 
[*]I did **NOT** update my kernel to 3.7 because apparently the driver for my ATI card is not fully supported by the new kernel.
[*]Then I excecuted each command provided by the [first post]("http://ubuntuforums.org/showpost.php?p=11712748&postcount=1")
[*]I didn't install driver 12.10 but the newest beta driver 12.11 since I couldn't start X with the officially released one.
[/LIST]

I am not sure if this is going to help you but if you can change the graphic chip in your BIOS settings, change it to the dGPU (I guess you have an ATI chip). 

I hope this will help somehow!

---

### Post by andrikos on 2012-12-09
Hello everybody,

I am really glad that my updated packages manage to go around bug: [#1068404]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1068404").

For hybrid fglrx/intel setups to function properly there is still bug: [#1088220]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1088220")

Practically this makes X server crash when using the integrated GPU. On my setup it crashes in the beginning of every second reboot.

If anyone had this problem and managed to solve it, let me know and I will update my packages to include this solution

Thanks,
Nick

---

### Post by markackerman8@gmail.com on 2012-12-09
> **shinylenin said:**
> Hey Mark,

I am not sure if I can help you with your problem, but I can at least tell you how I got my HP to work.


[LIST=1]
[*]I made a fresh install and did an update
...
...
[*]I didn't install driver 12.10 but the newest beta driver 12.11 since I couldn't start X with the officially released one.
[/LIST]

I am not sure if this is going to help you but if you can change the graphic chip in your BIOS settings, change it to the dGPU (I guess you have an ATI chip). 

I hope this will help somehow!

Shiny,
I guess what would be a weekend without another re-install of Ubuntu to TRY and fix this.
I will try what you suggested, though I have one question and One Observation.

q?/ What Kubuntu 12.10 or 12.04 did you use? and for others is one or the other more likely to work with ATI HD3000/ AMD-ATI-Radeon 6xxxm 'Muxless' setups?
  And Shiny I think you must have a 'Muxed' System, as only they have Cios options to switch between cards - in my understanding.

As it is I will try with Kubuntu 12.10, as I th9ink you used that because you referenced Kernel 3.7 whisk is closer to it.

Mark - Wish me luck
one Note:  The Open Source/ Mesa-git which updates almost daily Is getting better constantly, and with Kubuntu's Plasma desktop, their is a game called LOL, which is working almost flawlessly now, and has had serious problems even a week ago and still even in Ubuntu.

---

### Post by markackerman8@gmail.com on 2012-12-11
> **shinylenin said:**
> Hey Mark,

I am not sure if I can help you with your problem, but I can at least tell you how I got my HP to work.


[LIST=1]
[*]I made a fresh install and did an update
[*]Then I excecuted this command from beidl's [post]("http://ubuntuforums.org/showpost.php?p=12386383&postcount=536"): ```
sudo add-apt-repository -y ppa:andrikos/ppa && sudo apt-get update && sudo apt-get upgrade
``` to update the drivers for the integrated Intel chip. 

....

I hope this will help somehow!
I restarted after the ppa/ update/ upgrade/ made sure to install both files (including the xserver-xorg-video-intel.dbg), and locked them restarted for good measure and BAMMMM LOCKED out again into tty1.

Tried reinstall again with more caution, and same thing  --  wow what is wrong ??

Do I have to give up for another month, and then be 13 months wiothout good drivers?/

please help?

Mark

---

### Post by MarcoDePollo on 2012-12-11
Man, I've been watching this thread for the past six months, hoping for some magic to happen, instead of hoping for HP to release a bios where I could actually choose fixed mode.

I'm currently running Kubuntu 12.10 and whenever I switch to Andrik's modified Intel-driver, I get segfaults.

[http://paste.ubuntu.com/1424888/](http://paste.ubuntu.com/1424888/)

Envy 17-3000.

---

### Post by markackerman8@gmail.com on 2012-12-11
> **MarcoDePollo said:**
> Man, I've been watching this thread for the past six months, hoping for some magic to happen, instead of hoping for HP to release a bios where I could actually choose fixed mode.

I'm currently running Kubuntu 12.10 and whenever I switch to Andrik's modified Intel-driver, I get segfaults.

[http://paste.ubuntu.com/1424888/](http://paste.ubuntu.com/1424888/)

Envy 17-3000.

Marco,
Wow Finally a friend with an envy 17 as well - mine is HP Envy 17-2195ca.  I have not found anyone with one that works with proprietary drivers.  But Marco - I am quite certain that our "Muxless" systems CANNOT have a switch in the Bios as it ALWAYS requires a combination of both Cards to some degree.  If you ever get yours working PLEASE email me 
markackerman8(AT)gmail - I would almost kill to get back to Ubuntu full time from 12 months now stuck in Windows with this Laptop,

Cheers, Mark

---

### Post by MarcoDePollo on 2012-12-11
> **markackerman8@gmail.com said:**
> Marco,
Wow Finally a friend with an envy 17 as well - mine is HP Envy 17-2195ca.  I have not found anyone with one that works with proprietary drivers.  But Marco - I am quite certain that our "Muxless" systems CANNOT have a switch in the Bios as it ALWAYS requires a combination of both Cards to some degree.  If you ever get yours working PLEASE email me 
markackerman8(AT)gmail - I would almost kill to get back to Ubuntu full time from 12 months now stuck in Windows with this Laptop,

Cheers, Mark

A nice HP supporter told me that it was supposed to have a "fixed mode" and that "I should wait for a BIOS update" - and I've read other reports where other HP laptops have had a "fixed mode" added.
But then again, another HP supporter told me to "try and disable that virtualization-thingy, maybe that'll work" so I don't really have my hopes up for this.

Here's hoping for a breakthrough.

---

### Post by markackerman8@gmail.com on 2012-12-11
Marco,

Trust me when I say Muxless system which are the bleeding edge type of Switchable graphics cards and the majority of expensive laptops in the past 2 years CAN"T have bios switches.  I have spoken to Executive case mangers to Envy Support MANAGERS to confirm this after one EXECUTIVE case manager mislead me that it would come soon - but even he finally said he was misinformed.  It seems so few people even in Envy AWESOME Tech support even know what MUXLESS Switchable graphics are - - Soo SAD.

Mark

---

### Post by MarcoDePollo on 2012-12-11
Welp, then I get a +1 for not investigating this in-depth.

And, it certainly explains some of the mouth-breathing suggestions I've been getting from the support, like "disable the Intel Graphics in the Windows Device Manager, that'll solve your problem".

---

### Post by andrikos on 2012-12-11
> **MarcoDePollo said:**
> Man, I've been watching this thread for the past six months, hoping for some magic to happen, instead of hoping for HP to release a bios where I could actually choose fixed mode.

I'm currently running Kubuntu 12.10 and whenever I switch to Andrik's modified Intel-driver, I get segfaults.

[http://paste.ubuntu.com/1424888/](http://paste.ubuntu.com/1424888/)

Envy 17-3000.


```
[    29.967] (II) LoadModule: "fglrx"
[    29.967] (WW) Warning, couldn't open module fglrx
[    29.967] (II) UnloadModule: "fglrx"
[    29.967] (II) Unloading fglrx
[    29.967] (EE) Failed to load module "fglrx" (module does not exist, 0)
```

Actually your fglrx module is not loaded, could you please follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND)
and report what is happening?
Practically it is the same method as explained by beidl

---

### Post by MarcoDePollo on 2012-12-12
> **andrikos said:**
> ```
[    29.967] (II) LoadModule: "fglrx"
[    29.967] (WW) Warning, couldn't open module fglrx
[    29.967] (II) UnloadModule: "fglrx"
[    29.967] (II) Unloading fglrx
[    29.967] (EE) Failed to load module "fglrx" (module does not exist, 0)
```

Actually your fglrx module is not loaded, could you please follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND)
and report what is happening?
Practically it is the same method as explained by beidl



This is the log after I tried the workaround: [http://paste.ubuntu.com/1426812/](http://paste.ubuntu.com/1426812/)

So, then I removed xorg.conf to try and get a desktop:
[http://paste.ubuntu.com/1426816/](http://paste.ubuntu.com/1426816/)

---

### Post by andrikos on 2012-12-12
> **MarcoDePollo said:**
> This is the log after I tried the workaround: [http://paste.ubuntu.com/1426812/](http://paste.ubuntu.com/1426812/)

So, then I removed xorg.conf to try and get a desktop:
[http://paste.ubuntu.com/1426816/](http://paste.ubuntu.com/1426816/)

Probably you have an error in your xorg.conf

Make sure you run
amdconfig --install -f
and try again.

If this doesn't work then attach also your xorg.conf along your Xorg.log

---

### Post by MarcoDePollo on 2012-12-12
xorg.conf generated by amdconfig: [http://paste.ubuntu.com/1426876/](http://paste.ubuntu.com/1426876/)

xorg.log [http://paste.ubuntu.com/1426890/](http://paste.ubuntu.com/1426890/)

---

### Post by andrikos on 2012-12-12
> **MarcoDePollo said:**
> xorg.conf generated by amdconfig: [http://paste.ubuntu.com/1426876/](http://paste.ubuntu.com/1426876/)

xorg.log [http://paste.ubuntu.com/1426890/](http://paste.ubuntu.com/1426890/)

Can you also give the output of this command?
lspci -nn|grep -i vga

---

### Post by MarcoDePollo on 2012-12-12
```
lspci -nn|grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series] [1002:6740]

```

---

### Post by Niccola on 2012-12-16
Today I went to reboot my laptop and it's frozen on a strange reboot black screen with Ubuntu Points counting down and up. Seems a Segmentation Fault

I just could reboot it turning off and on again by pressing Power button.

Then I just observed that it's happening every time I reboot or shutdown my laptop.


is someone with same problem?

---

### Post by rikkinho on 2012-12-16
yes is a bug from fglrx, so far no solution i think

---

### Post by markackerman8@gmail.com on 2012-12-17
I am glad Andrikos is still monitoring this site, it gives me hope.  

A note regarding the open source radeon drivers which has finally at least got 50% functionality in my Intel/Amd Kubuntu, fglrx 0% functional with EVERYTHING trued and retried over and over ....

anyway back to the point, the new upcoming linux kernel 3.8 has continued to improve the Radeon driver with renewed optimism, 
here are some quotes:

Story just appeared on Slashdot (no comments yet) at:

> [http://hardware.slashdot.org/story/12/12/16/2134223/amd-radeon-performance-preview-on-linux-38](http://hardware.slashdot.org/story/12/12/16/2134223/amd-radeon-performance-preview-on-linux-38)

Comments ought to be interesting when they arrive.  Meanwhile, the /.
story links to this:

> With word this week that there's some performance improvements for
> the open-source Radeon Linux graphics driver to be found with the
> Linux 3.8 kernel as a result of the a-synchronous DMA engine support,
> some very early benchmarks of the "drm-next" code were done from five
> different AMD Radeon graphics cards. In extreme cases, the
> open-source graphics driver can deliver 10x higher OpenGL frame-rates
> with the experimental kernel.

...

> The Radeon OpenGL benchmarks were done with the Phoronix Test Suite
> and the user-space during this DRM testing was Mesa 9.1-devel Git
> from 13 December and the xf86-video-ati 7.0.0 DDX driver.
> SwapBuffersWait was disabled for the ATI DDX.

at

> [http://www.phoronix.com/scan.php?page=article&item=amd_drm38_radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_drm38_radeon&num=1)

---

### Post by cyanide911 on 2012-12-17
I tried this on my new setup with Linux Mint, and I'm experiencing terrible battery life. Around 60-70 minutes on a full charge on integrated GPU. And my laptop seems to be getting heated up as well, with little or no use.

Any further steps I can take to improve battery and thermal performance?

---

### Post by rikkinho on 2012-12-17
if you have intel/amd turn off your amd card, i have hope ubuntu 13.04 with kernel 3.8 brings hybrid graphics support (a working solution ofc)

[http://ubuntuforums.org/showthread.php?t=1917897](http://ubuntuforums.org/showthread.php?t=1917897)

---

### Post by andrikos on 2012-12-18
For those tried my PPA (both fglrx + intel packages) and still having X server crashing (low graphics mode) make sure that you have no other X related third party PPAs enabled (There was a case with a guy using the intel driver from xorg-edgers).

If you want to improve battery life and eliminate heating problem, install fglrx and use the intel gpu (amdconfig --px-igpu).
Beware that this has a bug and X-server might crash on every second reboot and/or after resume.
This bug and a workaround can be seen here:
[https://bugs.launchpad.net/fglrx/+bug/1088220](https://bugs.launchpad.net/fglrx/+bug/1088220)

If you want to use the intel GPU but without fglrx then use vgaswitcheroo in order to switch off the discrete cpu.

---

### Post by andrikos on 2012-12-19
> **MarcoDePollo said:**
> xorg.conf generated by amdconfig: [http://paste.ubuntu.com/1426876/](http://paste.ubuntu.com/1426876/)

xorg.log [http://paste.ubuntu.com/1426890/](http://paste.ubuntu.com/1426890/)

I think the problem is this:
```
(WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
(EE) this is a Muxless PX A+I platform, we doesn't supported it
(EE) No devices detected.
```

What do you get when you run?
```
dpkg --list  "fglrx*" xserver-xorg-video-intel "xserver*core" "xorg-server*"
```

---

### Post by MarcoDePollo on 2012-12-20
> **andrikos said:**
> 
What do you get when you run?
```
dpkg --list  "fglrx*" xserver-xorg-video-intel "xserver*core" "xorg-server*"
```

I get
```

sudo dpkg --list  "fglrx*" xserver-xorg-video-intel "xserver*core" "xorg-server*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
un  fglrx-glx                            <none>                                          (no description available)
ii  xserver-xorg-core                    2:1.13.0-0ubuntu6.1     amd64                   Xorg X server - core server
ii  xserver-xorg-video-intel             2:2.20.9-0ubuntu2       amd64                   X.Org X server -- Intel i8xx, i9xx display driver
dpkg-query: no packages found matching xorg-server*

```

My installation is fully opdated.

I tried with a fresh install, just to make sure some random fault wasn't causing it, but when I switch to the modified video-intel drivers, xorg consistently segfault on startup.

---

### Post by andrikos on 2012-12-20
Please follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND)

There are some bugs in the official versions of the packages that need to be fixed, before that you can use the packages I have prepared

---

### Post by MarcoDePollo on 2012-12-20
> **andrikos said:**
> Please follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND)

There are some bugs in the official versions of the packages that need to be fixed, before that you can use the packages I have prepared

That is exactly the problem, I can not use your packages. Nevermind that Xorg just dumps me at a shell-login when ever the fglrx-drivers are meant to be loaded, but simply asking X to start with your modified intel-driver consistently gives me a segfault:

[http://paste.ubuntu.com/1452611/](http://paste.ubuntu.com/1452611/)

---

### Post by andrikos on 2012-12-20
Why can't you use my packages?
Currently is the only way to effectively use the intel/fglrx hybrid systems

I see that you get this error:
```
(WW) Warning, couldn't open module fglrx
(II) UnloadModule: "fglrx"
(II) Unloading fglrx
(EE) Failed to load module "fglrx" (module does not exist, 0)
```

Please paste the output when you install the fglrx drivers again from my PPA (after you purge them)

---

### Post by MarcoDePollo on 2012-12-21
> **andrikos said:**
> Please follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND)

All right, Post-workaround, just before the reboot.

```
sudo aticonfig --px-list
PowerXpress: Discrete GPU is active (High-Performance mode).
```


```
sudo aticonfig --px-dgpu
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!
```

Just out of curiosity, are the warnings anything to be worried about?

---

### Post by MarcoDePollo on 2012-12-21
Xorg log with fglrx installed:

[http://paste.ubuntu.com/1454140/]("http://paste.ubuntu.com/1454140/")

---

### Post by markackerman8@gmail.com on 2012-12-21
Marco and Andrikos, ):P

> **MarcoDePollo said:**
> Xorg log with fglrx installed:

[http://paste.ubuntu.com/1454140/]("http://paste.ubuntu.com/1454140/")

Marco I noted this in your Xorg.log
   not good news.

[    20.004] (II) Module intel: vendor="X.Org Foundation"
[    20.004] 	compiled for 1.13.0, module version = 2.20.9
[    20.004] 	Module class: X.Org Video Driver
[    20.004] 	ABI class: X.Org Video Driver, version 13.0
[    20.004] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    20.004] (EE) this is a Muxless PX A+I platform, we doesn't supported it


Guys,

I am trying yet another re-install (147th !!!), which I doubt will work but I want to try with your last 5 posts just in case a miracle has happened.

Marco can you tell me how to put a copy of my Xorg.0.log into a hyperlink like you did so I don't waste so much space on this blog ??

and guys can you please help me troubleshoot this install with specific requests as a last attempt this month for a serious attempt at getting this working??

Thanks, Mark.):P

---

### Post by synace on 2012-12-21
Hey all. Sony Vaio SVZ13116GXX here with external docking station.

lspci:

```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
16:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
```

cannot get dock-connect monitors working.

tried newer kernel: 3.6.9-030609-generic
tried catalyst 12.10 and beta
tried separate x (no screens detected)

currently trying a separate x window w/ the radeon module loaded and running.

of note, laptop works 'out of the box' on Linux Mint w/ the ports on the laptop, 3 monitors (laptop + VGA + HDMI)

kinda wish the dock was just a port-replicator so that it would 'just work' as well.

Thoughts?

---

### Post by synace on 2012-12-21
small breakthrough... 

accidently started xorg w/o backgrounding it. noticed the dock monitors light up.

switched to vt1 and xrandr -d :8

got a x cursor and monitors detected.

HDMI-1 connected (dock)
VGA-1 connected (dock)
eDP-0 connected (laptop)
VGA-0 disconnected (laptop)
HDMI-0 disconnected (laptop)
DisplayPort-0 disconnected (?)

i'm close..

---

### Post by markackerman8@gmail.com on 2012-12-21
Andrikos and Morkos,

I am starting yet again with a fresh install.  I am going to give you a play by play of EVERYTHING I do and did, and will edit it after successive restarts - so please help me trouble shoot as I am trying soooo hard.

1/ Installed Kubuntu 12.10, and Updated it, restarted
2/ - sudo add-apt-repository ppa:andrikos/ppa
   - sudo apt-get update
   - sudo apt-get -y upgrade
            The following packages will be upgraded:
               libmtp-common libmtp-runtime libmtp9 xserver-xorg-video-intel
            4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
   - sudo apt-get --reinstall install xserver-xorg-video-intel
     - Setting up xserver-xorg-video-intel (2:2.20.9-0ubuntu2+andrik2) ...
   - apparehntly successful
3/ Went in Software Manager to Lock it to current version and notieced the "dbg" file of andrikos ppa wasnt installed , si I did so
   - locked both xserver-xorg-video-intel files
4/ Went to fist paget to install all pre-requisite packages
    First we're going to download all the prerequisite packages :
    C ode:
    sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
    sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
    sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
   If you're using Ubuntu 64bits please run those two commands (32bits users don't have to) :
     Code:
    sudo apt-get install ia32-libs lib32gcc1 libc6-i386
  Note** I know this probably wasn't necessary but saw no harm in doing so
         to make sure nothing was missing.
5/ Restarted before installing any fglrx packages to see if Andrikos ppa has stopped "X" from working as always in the past.
   ACTUALLY - since it always wont restart at this point in the past,  I will actually install the fglrx - FIRST - Then restrart
   - sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates
     - The following NEW packages will be installed:
       fglrx-amdcccle-updates fglrx-updates lib32gcc1 libc6-i386
     - all installed with no problems
6/ did "STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :" from first page
   - gksu nano /etc/X11/Xsession.d/10fglrx   , - for 64 bit system
7/ sudo aticonfig --initial -f
8/ Reboot 
   - Wish me luck (of course I will edit this with the results)
   Mark):P
  DAMMNNNNN of course it didn't work - couldn't log in as USUAL
            -              s0000000000000            -
9/it said
"Segmentation Fault at address 0x7f............., 
   Please consult /var/log/Xorg.0.log"
so here it is
 [http://paste.ubuntu.com/1456249/](http://paste.ubuntu.com/1456249/)

the end o0f which shows
[    16.560] (EE) 7: /usr/bin/X (0x7f5e0fd7f000+0x448ad) [0x7f5e0fdc38ad]
[    16.560] (EE) 
[    16.560] (EE) Segmentation fault at address 0x7f5e0cbf9d09
[    16.560] 
Fatal server error:
[    16.560] Caught signal 11 (Segmentation fault). Server aborting

Please HELP ME, Mark

---

### Post by MarcoDePollo on 2012-12-22
> **markackerman8@gmail.com said:**
> Marco and Andrikos, ):P



Marco I noted this in your Xorg.log
   not good news.

[    20.004] (II) Module intel: vendor="X.Org Foundation"
[    20.004] 	compiled for 1.13.0, module version = 2.20.9
[    20.004] 	Module class: X.Org Video Driver
[    20.004] 	ABI class: X.Org Video Driver, version 13.0
[    20.004] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    20.004] (EE) this is a Muxless PX A+I platform, we doesn't supported it


Yeah, this is the error I usually get. I tried switching to the latest Intel-driver, from a ppa, still without luck but atleast then X segfaulted.

It also makes me wonder why it complains about not finding anything on PCI@1:0:1, since that is the HDMI-audio - unless it somehow conflicts with snd_hda_intel.


> Marco can you tell me how to put a copy of my Xorg.0.log into a hyperlink like you did so I don't waste so much space on this blog ??

[s]Save your Xorg.0.log somewhere convenient and then go to paste.ubuntu.com and paste it there, that gives you a handy little link for it.
I would add it as an attachment here but usually the log is too big.[/s]

I see you found out:)

---

### Post by markackerman8@gmail.com on 2012-12-22
> **MarcoDePollo said:**
> Yeah, this is the error I usually get. 
 ...
[s]Save your Xorg.0.log somewhere convenient and then go to paste.ubuntu.com and paste it there, that gives you a handy little link for it.
I would add it as an attachment here but usually the log is too big.[/s]

I see you found out:)

Thanks anyway Marco):P
this is getting ridiculous a year later - wow

---

### Post by MarcoDePollo on 2012-12-23
> **markackerman8@gmail.com said:**
> Thanks anyway Marco):P
this is getting ridiculous a year later - wow

Well, at least we have better desktopdrivers thanks to [s]Linus[/s] Valve - so there's always that:)

---

### Post by Lyfang on 2012-12-24
What is your result of running this OpenGL benchmark test inside a web browser? Please write which test you run and result. Thanks. [http://have2chat.net/benchmark/?v=1](http://have2chat.net/benchmark/?v=1)

---

### Post by usernamestaken on 2012-12-24
Current system specs:
i7 3770k (intel integrated GPU, disabled in the bios)
HD 7970 x2
Sabertooth Z77


Issue:
Installing the AMD driver (both from AMD site and using repos) results in a black screen, OR X failing to start complaining that no screens were found.  Black screen requires reboot and nomodeset to get to a prompt where I can uninstall the driver.

What I have tried:
Downgrading X to 1.12 via PPA

andrikos' patched fglrx and intel packages

Rebuilt kernel to remove vgaswitcharoo, and arbitration.  Disabled one, then the other, then both.  Kernels were from Ubuntu kernel PPA and built using the recommend build process. tried 3.5.0 and 3.7.1

Using the intel card as the primary display (I only want the AMD's for opencl anyway).  This would boot to a 2d state only, and fglrx gave errors, so did glxinfo.  

Installing driver using AMD install, and building as a quantal package and installing from there.

Allowing X to use radeon seems to do alright, but opencl is not supported under this driver.  Any ideas on what else I can try?  Any info you need to maybe narrow down the issue?

---

### Post by Hekla on 2012-12-26
Hello,

Having decided to try and deal with my graphics card after a half-year gap in trying, I attempted the method outlined earlier in this thread. I am now in the odd situation of the AMD card working well but xserver doesn't start on the integrated card (and indeed, I installed the fglrx drivers from low graphics mode, as the intel drivers didn't work). If I'm correct, the Intel drivers allow the AMD drivers to work but they themselves don't work or aren't configured correctly to work with the Intel chip?

What might be preventing the successful use of the Intel drivers?

My discrete graphics card is the 6600M.
The processor is the i5-2430M.

Thanks for all the work so far. Being able to actually use this graphics card beyond the my windows installation is brilliant.

Hekla

---

### Post by wegah on 2012-12-27
> **markackerman8@gmail.com said:**
> Marco,

Trust me when I say Muxless system which are the bleeding edge type of Switchable graphics cards and the majority of expensive laptops in the past 2 years CAN"T have bios switches.  I have spoken to Executive case mangers to Envy Support MANAGERS to confirm this after one EXECUTIVE case manager mislead me that it would come soon - but even he finally said he was misinformed.  It seems so few people even in Envy AWESOME Tech support even know what MUXLESS Switchable graphics are - - Soo SAD.

Mark


You are wrong.
Muxless systems use the same output hardware ( most the intel base) and just switch the processor ( being short).

The manufaturer bios can do 3 kinds of choices when build the bios.
1. give you the option of choice from WHAT default processor will be enabled by default using the output hardware when the computer boot ( not the default card used) but the trigged output.

2- you dont have this choice. but the manufacturer do a well done code and turn the discrete one ON by default.

Both cases are the ones the official catalyst work switching or the opensource one.

3 case. You computer come from a **** brand like hp. a company dislike users. but love their money.

About HP. 
Just computer with the ADVANCED OPTIONS in bios can do it. From second generation envy 17 and ahead is a nono.

HP was very clear about this. They release this devices for windows not linux. they will not give support for windows.
And same in windows windows 8 users or windows 7 already have big troubles with muxless drivers ( they how usual leave all second generation users stuck with old drivers and the 3 generation have problems).

OBS. After they do this official statement about non windows. They released all bios not single signed ( for non hack mods). But they double and tripled signed the files Just to be certain of no one will open this options under bios.
Like the UEFI mode enable disable. We have an expensive hp and intel chipset but we barely can change  the date.

Most of well coded expensive non mainstreamer notebooks have do have this choice.

And believe you. the low end ones from china. the plastic ones. All have this options to. The bios most of time is full filled with choices.

Mine mum use a chinese low end one with almost the same configuration from mine 2100cto. All plastic, all simples. But she can switch to UEFI mode and the default output path for video cards in bios. The i7, intel, amd card are exact the same.
I even can install macosx  almost 100% out of box. Minor glitches with wifi just.

HP is a ****.

---

### Post by Bucic on 2012-12-29
Can anyone take a look here?
Intel and AMD no-mux switchable graphics
[http://ubuntuforums.org/showthread.php?t=2099126](http://ubuntuforums.org/showthread.php?t=2099126)

---

### Post by LarcBP on 2013-01-02
Dell N4110 14R
Processor: Intel I5
Graphics: ATi Radeon 6470M & Intel HD Graphics 3000

I tested all drivers and tried with PPA's and another solutions.
The only real solution for me is the last Catalyst (12.10) after install this and switch to Discrete Graphics (because when you reboot you get a shell, you need switch the graphics and restart X), the hybrid graphics finally works!
[IMG]http://s1.postimage.org/5sz62pahr/Captura_de_tela_de_2012_12_31_13_19_17.png[/IMG]

---

### Post by jayeshsan on 2013-01-02
Hi,

I've Dell Vostro 1540 laptop with Ubuntu 12.10 installed. Its working fine but not good with hi-res images. Is there any graphic driver available ?

---

### Post by MarcoDePollo on 2013-01-02
> **jayeshsan said:**
> Hi,

I've Dell Vostro 1540 laptop with Ubuntu 12.10 installed. Its working fine but not good with hi-res images. Is there any graphic driver available ?

You've posted in the wrong thread. The Dell Vostro 1540 comes with Intel HD graphics only, with no "Discrete Graphics" to switch to when the need arises.

So, my guess is that the proper driver is already loaded by Ubuntu.

Note, Intel HD-graphics, despite its name, is not as feature-rich as dedicated GPU's from AMD or Nvidia, so expect some rough edges here and there.

---

### Post by markackerman8@gmail.com on 2013-01-04
> **LarcBP said:**
> Dell N4110 14R
Processor: Intel I5
Graphics: ATi Radeon 6470M & Intel HD Graphics 3000

I tested all drivers and tried with PPA's and another solutions.
The only real solution for me is the last Catalyst (12.10) after install this and switch to Discrete Graphics (because when you reboot you get a shell, you need switch the graphics and restart 

Can you be more specific which ppa's you used, which Intel-xorg-video thing, what aticonfig command you used to switch to the discrete card, and any other specific info to help my 13 month dilemma being stuck in windows with my Intel HD 3000, and ATI Radeon 6850m.

Every combination of (ubuntu distro, catalyst driver version, intel ppa, and "andrikos' patched fglrx and intel packages", Discrete or Integrated on/off),  I have tried with have always resulted in a fail to start X.

Please Help HP SUCKS:KS

Thanks Mark:D

---

### Post by markackerman8@gmail.com on 2013-01-04
Wegah, Thanks -
- for clarifying yet again HP SUCKS !!

Any help getting my HP Envy 17 running with Ubuntu would be much appreciated,

Cheers, Mark):P

> **wegah said:**
> You are wrong.
Muxless systems use the same output hardware ( most the intel base) and just switch the processor ( being short).

The manufaturer bios can do 3 kinds of choices when build the bios.

... .... ....

About HP. 
Just computer with the ADVANCED OPTIONS in bios can do it. From second generation envy 17 and ahead is a nono.

HP was very clear about this. They release this devices for windows not linux. they will not give support for windows.
And same in windows windows 8 users or windows 7 already have big troubles with muxless drivers ( they how usual leave all second generation users stuck with old drivers and the 3 generation have problems).

OBS. After they do this official statement about non windows. They released all bios not single signed ( for non hack mods). But they double and tripled signed the files Just to be certain of no one will open this options under bios.
Like the UEFI mode enable disable. We have an expensive hp and intel chipset but we barely can change  the date.

Most of well coded expensive non mainstreamer notebooks have do have this choice.

And believe you. the low end ones from china. the plastic ones. All have this options to. The bios most of time is full filled with choices.

Mine mum use a chinese low end one with almost the same configuration from mine 2100cto. All plastic, all simples. But she can switch to UEFI mode and the default output path for video cards in bios. The i7, intel, amd card are exact the same.
I even can install macosx  almost 100% out of box. Minor glitches with wifi just.

HP is a ****.

---

### Post by Mijuca on 2013-01-04
1. Ubuntu 12.04
2. Toshiba
3. Toshiba Satellite L850-18T 
4.  I recently bought notebook Toshiba Satellite l850-18t  - [SPECS]("http://bl.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=BL&LNG=32&userAction=SMP_RESULTS_PAGE&partNumber=PSKDNE-00R00RY4&serialNumber=&USER_ACTION=Serial%20number#tab0;") and i have problem with 2 usb ports, i think with 2 usb 3.0 porst on the left side and with drivers for my ati radeon 7670m.

1. Only 1 usb port works, and other 2 on the left side dont work neither  with 2.0 or 3.0 usb drives... When i plug-in usb nothing happen...

2. I cant find drivers for my graphic card and linux finds some for ati radeon 6*** older version... 


please help me :smile:

any help for my toshiba with amd 7670m and intel i5???

---

### Post by MarcoDePollo on 2013-01-04
> **Mijuca said:**
> 1. Ubuntu 12.04
2. Toshiba
3. Toshiba Satellite L850-18T 
4.  I recently bought notebook Toshiba Satellite l850-18t  - [SPECS]("http://bl.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=BL&LNG=32&userAction=SMP_RESULTS_PAGE&partNumber=PSKDNE-00R00RY4&serialNumber=&USER_ACTION=Serial%20number#tab0;") and i have problem with 2 usb ports, i think with 2 usb 3.0 porst on the left side and with drivers for my ati radeon 7670m.

1. Only 1 usb port works, and other 2 on the left side dont work neither  with 2.0 or 3.0 usb drives... When i plug-in usb nothing happen...

2. I cant find drivers for my graphic card and linux finds some for ati radeon 6*** older version... 


please help me :smile:

any help for my toshiba with amd 7670m and intel i5???

With regards to the graphics, this will probably fit your needs:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
See the first page of this thread on how to install the drivers.


Maybe asking another question in the hardware-forum will get you help with your USB-troubles. This is, after all, a thread about hybrid graphics.

---

### Post by MarcoDePollo on 2013-01-04
> **markackerman8@gmail.com said:**
> Wegah, Thanks -
HP SUCKS !!


Yeah, I'm thinking, Asus maybe, next time I'm getting a laptop.

---

### Post by MarcoDePollo on 2013-01-13
Holy Crap!

I gave a daily build of kubuntu 13.04 a spin, just to check it out.
I decided to give it another shot at getting this hybrid graphics working and initially I figured the installation failed, mainly because installing the drivers resulted in a coredump, and well, bugger me with a fishfork, if I haven't got the "AMD - Testing Use Only" in the lower right corner of my screen. (I installed 12.11 beta)

It runs like.. like something that doesn't run very well, but I can start CCC without any problems.

Update: Well, I guess this explains a few things: In the background of the beta-logo, there's a crossed-out 3D, so I guess acceleration doesn't really work - but now there is a glimmer of hope.

Screenshot: [http://imgur.com/l9cED](http://imgur.com/l9cED)

---

### Post by MarcoDePollo on 2013-01-13
This just keeps getting better and better.

There was an update to the Fglrx drivers, so I installed them directly from Ubuntu's repo and it's working. It's actually working.

The logo in the bottom says "unsupported hardware" but CCC confirms it, as does fgl_glxgears, it's actually working.

Here: have another screenshot [http://imgur.com/YUHd4](http://imgur.com/YUHd4)

Edit: right, I had tried to install the fglrx-drivers from Ubuntu's repo, with the same result I got from AMD's betadrivers, but when I tried purging the drivers, they weren't installed. I guess they were after all. Looks like driver from Ubuntu is 12.9

---

### Post by MarcoDePollo on 2013-01-15
I've tried reinstalling a new "daily", just to see if the first success was a fluke. Installing fglrx still results in an error, but the result is the same, drivers are installed and running.

aticonfig will report that no supported adapters are found, but cccle will list the card and relevant information.

But, something happened on kernel-level, because my intel-graphics is no longer listed in lspci - and cccle mentions nothing of switchable graphics.

sudo lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
09:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
10:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
11:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
12:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

Not that I'm complaining:)


Oh, and:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
        Subsystem: Hewlett-Packard Company Device 1689
        Kernel driver in use: fglrx_pci

---

### Post by MarcoDePollo on 2013-01-15
Removed fglrx and a subsequent reinstall:

sudo apt-get install fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/86.4 MB of archives.
After this operation, 257 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package fglrx.
(Reading database ... 108339 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a9.010-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a9.010-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx (2:9.010-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-9.010 DKMS files...
Building only for 3.8.0-0-generic
Building for architecture x86_64
Building initial module for 3.8.0-0-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-0-generic/updates/dkms/

depmod.....

DKMS: install completed.                                                                                                                                                
update-initramfs: deferring update (trigger activated)                                                                                                                  
Setting up fglrx-amdcccle (2:9.010-0ubuntu1) ...                                                                                                                        
Processing triggers for initramfs-tools ...                                                                                                                             
update-initramfs: Generating /boot/initrd.img-3.8.0-0-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted (core dumped)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


Post-reboot; Yup, still working, games run perfectly.

---

### Post by pajew on 2013-01-15
Thanks for the guide. First I was trying it on Ubuntu 12.10 without success. System hangs on boot. The second approach I've made on Ubuntu 10.4. I've used Catalyst 12.10 downloaded from AMD site and it is working. 
My laptop is Dell Vostro 3560.
I'm abble to switch VGA and both of them are OK. But my laptop even on integrated Intel continues to hot and fan is noisy. :confused:

---

### Post by markackerman8@gmail.com on 2013-01-16
No joy again

though thanks to MarcoDePollo for his help trying.

13.04 Kubuntu , Additional drivers or AMDs downloaded and installed or sudo apt-get install fglrx - All result in CCC saying no drivers present and a 2D screen.

At least with Kubuntu I can still get into a 2D Desktop - better than black screen of Death but still not good enough to use.

Any NEW tips are VERY WELCOME !!:)

Mark
[email]markackerman8@gmail.com[/email]

---

### Post by mauriciofauth on 2013-01-18
I read every page and every comment and finally worked for me!

Thank you very much **Alexislavie**, **Niccola**, **andrikos**.

**Samsung Series 7 Chronos NP700Z4A-SD1BR**, Intel HD 3000, AMD HD6750M, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

I used this solution for my Ubuntu 12.10:

```

sudo apt-get purge fglrx*
sudo add-apt-repository ppa:andrikos/ppa
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get --reinstall install xserver-xorg-video-intel
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates
sudo aticonfig --initial -f

```

---

### Post by beidl on 2013-01-18
AMD released Catalyst 13.1 today, with (**finally**) full support for X.org 1.13 and fixes for PowerXPress.
Also, in the release notes, the only Ubuntu version marked as supported is 12.10.

[Download is right here!]("http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip")

I'd suggest trying it with a fresh install **without** Nick Andriks PPA first.
Since I got rid of my HP ProBook 4730s (HD3000 + 6470M) laptop exactly because of the problems 
with switchable graphics, I won't be able to test it myself.

---

### Post by markackerman8@gmail.com on 2013-01-18
Damn black screen of death and it seemed so promissing too !!
14 months and still noi luck.
arghh any tips of course welcome
mark

---

### Post by Miktor on 2013-01-18
> **beidl said:**
> AMD released Catalyst 13.1 today, with (**finally**) full support for X.org 1.13 and fixes for PowerXPress.
Also, in the release notes, the only Ubuntu version marked as supported is 12.10.

[Download is right here!]("http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip")

I'd suggest trying it with a fresh install **without** Nick Andriks PPA first.
Since I got rid of my HP ProBook 4730s (HD3000 + 6470M) laptop exactly because of the problems 
with switchable graphics, I won't be able to test it myself.

I tested it and it didn't work for me. There's some segfault inside the driver somewhere...

---

### Post by rikkinho on 2013-01-19
amd ccc 13.1 hangs shutdown/reboot after switch first time to intel :( amd not do anything that works, i really need to sell my laptop

---

### Post by Hurricane043 on 2013-01-19
> **rikkinho said:**
> amd ccc 13.1 hangs shutdown/reboot after switch first time to intel :( amd not do anything that works, i really need to sell my laptop

Getting a similar issues

13.1 works fine, and the switchable graphics options are in the AMD CCC. But switching to the iGPU crashes the X server for me.

---

### Post by stat30fbliss on 2013-01-19
> **mauriciofauth said:**
> I read every page and every comment and finally worked for me!

Thank you very much **Alexislavie**, **Niccola**, **andrikos**.

**Samsung Series 7 Chronos NP700Z4A-SD1BR**, Intel HD 3000, AMD HD6750M, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

I used this solution for my Ubuntu 12.10:

```

sudo apt-get purge fglrx*
sudo add-apt-repository ppa:andrikos/ppa
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get --reinstall install xserver-xorg-video-intel
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates
sudo aticonfig --initial -f

```

You sir, are awesome.  This worked for me as well.  Thanks!

System:
Dell XPS-8300
Intel i5
Radeon 6850
OCZ Vertex 4 128SSD

---

### Post by markackerman8@gmail.com on 2013-01-20
> **stat30fbliss said:**
> You sir, are awesome.  This worked for me as well.  Thanks!

System:
Dell XPS-8300
Intel i5
Radeon 6850
OCZ Vertex 4 128SSD

Well tried exactly that no luck - perhaps someone will see my 100th attempton this forum and feel sorry enooough to find a working alternative - PLEASE 13.5 months later

[email]markackerman8@gmail.com[/email]   ):P

---

### Post by leonardt on 2013-01-21
just wanted to say that following [the first response in this askubuntu post]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working"), I was able to get switchable graphics working on an HP Envy 15 3040 nr running a Radeon HD 7690M and 12.10

---

### Post by MarcoDePollo on 2013-01-21
> **leonardt said:**
> just wanted to say that following [the first response in this askubuntu post]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working"), I was able to get switchable graphics working on an HP Envy 15 3040 nr running a Radeon HD 7690M and 12.10

That's great. That post on Ask Ubuntu is the textbook example of how to get hybrid graphics working for most configurations.

---

### Post by markackerman8@gmail.com on 2013-01-22
Wow tried yet again as the above post showed a few differences, and after Andrikos xserver-xorg-video-intel and configure - AGAIN Clack Screen of death after reboot - Anyone with sympothy on my 100th attempt over the year and any suggestions please rep[ly, Please and Thanks

[email]markackerman8@gmail.com[/email]

---

### Post by Burkey on 2013-01-22
Not able to specifically help I am afraid Mark, however the Andrikos PPA worked fine on my Sony Vaio with AMD/Intel hybrid but it may be worth checking out the new 13.1 driver AMD has just released.

I am very keen to see how quickly that can make it into the 12.10 repos actually so I can remove Andrikos one as I have conerns 12.11 beta is causing me crashes in Eye Of Gnome (open a larg image, set to 100% size and click/drag.. observe X server crash).

---

### Post by markackerman8@gmail.com on 2013-01-23
> **Burkey said:**
> Not able to specifically help I am afraid Mark, however the Andrikos PPA worked fine on my Sony Vaio with AMD/Intel hybrid but it may be worth checking out the new 13.1 driver AMD has just released.

I am very keen to see how quickly that can make it into the 12.10 repos actually so I can remove Andrikos one as I have conerns 12.11 beta is causing me crashes in Eye Of Gnome (open a larg image, set to 100% size and click/drag.. observe X server crash).

Already tried ukubuntu alpha 13.04 w/wout andrikos PPA, and w/wout amd's 13.1, and w/wout 12.11 beta, and w/wout just fglrx form the repos arghhh

thanks anyway

---

### Post by semperfizh on 2013-01-26
In order to get 3D to work on the integrated card, is it possible to remove catalyst and install intel driver from Ubuntu repos? I was thinking of something like this:

```

sudo apt-get purge fglrx*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot

```

It seems that the workaround from the initial post, which suggests editing /etc/X11/Xsession.d/10fglrx, does not work. Hence one can not use Unity 3D or equivalent on the integrated GPU.
Running Ubuntu 12.04

---

### Post by harpal on 2013-01-28
I installed the drivers for my amd radeon HD 7600m graphic card as given in the askubuntu post. When I executed the following command ```
sudo aticonfig --initial -f
```
and rebooted, I lostmy login screen. Virtual console opens up. Then I removed the drivers using ```
sudo apt-get remove fglrx
```
but it too didn't work. I get virtual console when I boot ubuntu.

---

### Post by beidl on 2013-01-29
> **harpal said:**
> I installed the drivers for my amd radeon HD 7600m graphic card as given in the askubuntu post. When I executed the following command ```
sudo aticonfig --initial -f
```
and rebooted, I lostmy login screen. Virtual console opens up. Then I removed the drivers using ```
sudo apt-get remove fglrx
```
but it too didn't work. I get virtual console when I boot ubuntu.

You probably still have the xorg.conf file around.
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Niccola on 2013-01-29
I just installed Catalyst 13.1 and I have some performance improvements on my HD 6770M. However, I also having some black-screens with mouse cursor in lightdm logging screen, which problem I workaround restarting lightdm service through another TTY::

CTRL + ALT + 1 for TTY1
then,
log in!
then:

```

sudo service lightdm restart

```

However, Im having some freezing and black screen when reboot/shutdown. Only happens after install fglrx and andrikos xserver-xorg-video-intel* drivers

Is somebody experiencing same problem when shutting down/rebooting?

[IMG]http://dl.dropbox.com/u/13977411/bd/20130128_204553.jpg[/IMG]

---

### Post by rikkinho on 2013-01-29
good news, new beta driver 13.2, resolves the hangs on shutdown (of x), works fine on me,

Ubuntu 12.04 kernel 3.5.7.4, mesa 9.0.1 (intel updates ubuntu x-team)

and the indicator from beidl (many thanks)

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

:guitar:

steam games work (cs 1.6 and team fortress 2)

---

### Post by Dans564 on 2013-01-30
> **rikkinho said:**
> good news, new beta driver 13.2, resolves the hangs on shutdown (of x), works fine on me,

Ubuntu 12.04 kernel 3.5.7.4, mesa 9.0.1 (intel updates ubuntu x-team)

and the indicator from beidl (many thanks)

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

:guitar:

steam games work (cs 1.6 and team fortress 2)

Is there a PPA for the beta drivers or did you install manually?

---

### Post by rikkinho on 2013-01-30
manually! i download from amd website and created packages

---

### Post by Dans564 on 2013-01-30
> **rikkinho said:**
> manually! i download from amd website and created packages

Thankyou! did the same and mine is fully working now!

---

### Post by Niccola on 2013-01-30
Excellent! Everything working fine now! I am not experiencing any bug nor faults, neither freezes or hangs with Catalyst 13.2 Beta 3

I recommend to follow the wiki cchtml tutorial for driver installation and tips.

kudos to AMD!

---

### Post by take-kun on 2013-01-30
I'm experiencing several problems even with the latest 13.2 drivers and my radeon 7970M with Ubuntu 12.10,  kernel  3.5.0-23-generic.

Granted, the shutdown bug was fixed, but I still have the following issues:

1) When using an external monitor and the dedicated card is enabled, X simply crashes
[     9.295] (II) fglrx(0): pEnt->device->identifier=0x7fbdfc1c0ff0
[     9.367] (II) pEnt->device->identifier=(nil)
[     9.367] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[     9.367] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[     9.930] (II) fglrx(0): PowerXpress: Diagnostic output from /usr/lib64/fglrx/switchlibGL:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link

[     9.948] (EE) 
[     9.948] (EE) Backtrace:
[     9.949] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7fbdfa6b4b76]
[     9.949] (EE) 1: /usr/bin/X (0x7fbdfa50c000+0x1ac9a9) [0x7fbdfa6b89a9]
[     9.949] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fbdf9832000+0xfcb0) [0x7fbdf9841cb0]
[     9.949] (EE) 3: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxPxPreInit+0x11e) [0x7fbdf6c629be]
[     9.950] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxPreInit+0x1fcb) [0x7fbdf6c3f2cb]
[     9.950] (EE) 5: /usr/bin/X (InitOutput+0xb02) [0x7fbdfa5a3b52]
[     9.950] (EE) 6: /usr/bin/X (0x7fbdfa50c000+0x44386) [0x7fbdfa550386]
[     9.950] (EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fbdf84b776d]
[     9.950] (EE) 8: /usr/bin/X (0x7fbdfa50c000+0x448ad) [0x7fbdfa5508ad]
[     9.950] (EE) 
[     9.950] (EE) Segmentation fault at address 0x50
[     9.950] 
Fatal server error:
[     9.950] Caught signal 11 (Segmentation fault). Server aborting

2) When booting with an external monitor and the integrated card is enabled, X doesn't crash, but it doesn't start either. It keeps on a black screen forever

3) After X starts without the external display, I can plug it. When I'm using the integrated card, it works fine, but with the external display the image is "scrambled" (see the attachment for a photo of the screen). This problem didn't happened when I was using Ubuntu 12.04 and catalyst 12.10

4) When the dedicated card is enabled, some applications makes X crash and go back to the login screen when doing some specific operations. For example, I can always reproduce this problem using Ubuntu's default image viewer. I open an image and try to drag it to create a shortcut, for example. This makes X crashes instantly.

Another application that produces the same effect: when I'm developing android applications and I try to edit layouts, dropping buttons, scaling components, etc. I have the XOrg.0.log for this problem, here's the backtrace:

[    35.225] (II) fglrx(0): EDID vendor "CMO", prod id 5926
[    35.225] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.225] (II) fglrx(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP) 
[    44.198] (II) fglrx(0): EDID vendor "CMO", prod id 5926
[    44.198] (II) fglrx(0): Printing DDC gathered Modelines:
[    44.198] (II) fglrx(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP) 
[    80.862] (EE) 
[    80.862] (EE) Backtrace:
[    80.862] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7ffb55278b76]
[    80.862] (EE) 1: /usr/bin/X (0x7ffb550d0000+0x1ac9a9) [0x7ffb5527c9a9]
[    80.862] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7ffb543f6000+0xfcb0) [0x7ffb54405cb0]
[    80.862] (EE) 3: /usr/bin/X (miResolveColor+0x3) [0x7ffb55256e53]
[    80.862] (EE) 4: /usr/bin/X (FakeAllocColor+0x62) [0x7ffb55117902]
[    80.862] (EE) 5: /usr/bin/X (0x7ffb550d0000+0x198373) [0x7ffb55268373]
[    80.862] (EE) 6: /usr/bin/X (0x7ffb550d0000+0x199ddd) [0x7ffb55269ddd]
[    80.862] (EE) 7: /usr/bin/X (miPointerUpdateSprite+0x29a) [0x7ffb5526430a]
[    80.862] (EE) 8: /usr/bin/X (0x7ffb550d0000+0x1945bd) [0x7ffb552645bd]
[    80.863] (EE) 9: /usr/bin/X (0x7ffb550d0000+0xe6c7b) [0x7ffb551b6c7b]
[    80.863] (EE) 10: /usr/bin/X (0x7ffb550d0000+0x12e3b7) [0x7ffb551fe3b7]
[    80.863] (EE) 11: /usr/bin/X (0x7ffb550d0000+0x5e039) [0x7ffb5512e039]
[    80.863] (EE) 12: /usr/bin/X (0x7ffb550d0000+0x66723) [0x7ffb55136723]
[    80.863] (EE) 13: /usr/bin/X (0x7ffb550d0000+0x5ff83) [0x7ffb5512ff83]
[    80.863] (EE) 14: /usr/bin/X (0x7ffb550d0000+0x141538) [0x7ffb55211538]
[    80.863] (EE) 15: /usr/bin/X (0x7ffb550d0000+0x55a91) [0x7ffb55125a91]
[    80.863] (EE) 16: /usr/bin/X (0x7ffb550d0000+0x4456a) [0x7ffb5511456a]
[    80.863] (EE) 17: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7ffb5307b76d]
[    80.863] (EE) 18: /usr/bin/X (0x7ffb550d0000+0x448ad) [0x7ffb551148ad]
[    80.863] (EE) 
[    80.863] (EE) Segmentation fault at address 0x7feb565cf2b6
[    80.863] 
Fatal server error:
[    80.863] Caught signal 11 (Segmentation fault). Server aborting
[    80.863] 
[    80.863] (EE) 

Again, just to be clear: this "drag" problem happens only with the dedicated card enabled. It works fine with the integrated card.

Did anyone noticed the same kind of problems? 

Thanks for reading my rant.

---

### Post by rikkinho on 2013-01-30
tomorrow and see that in my laptop

---

### Post by rikkinho on 2013-01-30
I tried it and had no problems with an external monitor (hdmi)

with amd card on,  like you say.

I´m with 6770m, maybe the problem only afects 7000m series (Southern Islands)

:S

---

### Post by alifa on 2013-01-31
Hi
Can I use the new drivers to switch freely between graphic cards?(I mostly use the integrated.)
cause last time I tried them ,I ended up with a black screen.
I have an HP dv6t which is running opensuse 12.2 with ati 6770m and Intel 3000.

---

### Post by take-kun on 2013-01-31
I haven't tried with hdmi, I used the DVI output, so I can't say whether I'd have the same kind of problem with hdmi.
Also, I'll emphasize that I have this kind of problem with Ubuntu 12.10. I had no issues with 12.04.

---

### Post by take-kun on 2013-02-01
> **alifa said:**
> Hi
Can I use the new drivers to switch freely between graphic cards?(I mostly use the integrated.)
cause last time I tried them ,I ended up with a black screen.
I have an HP dv6t which is running opensuse 12.2 with ati 6770m and Intel 3000.

Assuming everything is fine, you can easily switch between using the commands provided in the first post. But everytime you change the card, you must logout.
The switch is working.

---

### Post by anion155 on 2013-02-02
I made it )))
HP ProBook 4530s
Intel Sandy Bridge/AMD RadeonHD 6490M
Ubuntu 12.10
AMD Catalyst 13.2 Beta 3
whitout andrikos ppa
At first install X-bleeding edges, but on catalyst installing it's make kernel cry... Without it everything works perfect ))
Don't know about Steam games, 'case don't have bought HL or CS.

---

### Post by sarvigalava on 2013-02-03
> **anion155 said:**
> I made it )))
HP ProBook 4530s
Intel Sandy Bridge/AMD RadeonHD 6490M
Ubuntu 12.10
AMD Catalyst 13.2 Beta 3
whitout andrikos ppa
At first install X-bleeding edges, but on catalyst installing it's make kernel cry... Without it everything works perfect ))
Don't know about Steam games, 'case don't have bought HL or CS.

How did you installed driver ? I installed using automatic mode. The driver works ok with dedicated gpu but switching is not working. If I select integrated gpu system hangs at boot. Further switching to dedicated gpu aslo doesn't work. I reinstalled the driver and I am using only dedicated gpu.


Someone knows how to fix this issue ?

Thanks.

---

### Post by rikkinho on 2013-02-05
you can t innstall auto, you need/have to create packages, and then install them. look page 1 , page 53 and 63

---

### Post by l6griffin on 2013-02-05
Newbie here, Just installed Ubuntu 12,2 on

HP2000z-300 Laptop
ATI Radeon HD 6310

I checked the ATI  and there is a new version 13.1 available.

My problem is I haven't been able to change the command line to get it;

[FONT=Arial][SIZE=2]wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)[/SIZE][/FONT]a little help please.

Larry

---

### Post by MarcoDePollo on 2013-02-06
> **l6griffin said:**
> Newbie here, Just installed Ubuntu 12,2 on

HP2000z-300 Laptop
ATI Radeon HD 6310

I checked the ATI  and there is a new version 13.1 available.

My problem is I haven't been able to change the command line to get it;

[FONT=Arial][SIZE=2]wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)[/SIZE][/FONT]a little help please.

Larry

```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
```

That should get you going.

---

### Post by l6griffin on 2013-02-06
Thanks Marco,

That did it. I had assumed that run needed to be on the end. I may yet learn as much about Linux as I did CP/M and DOS.

Edit. spoke too soon. Have a problem with another command and don't see the problem;

larry@larry-HP-2000-Notebook-PC:~/catalyst13.1$ sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip: 1: ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip: Syntax error: ")" unexpected

tried several variations no help.

edit; extracted .run file from .zip

Nope it hung;
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit

after this there is a inverted square blinking cursor.  All I can see to do is ctrl C to abort

I screwed up time to start over

Larry

---

### Post by MarcoDePollo on 2013-02-06
You need to run the installer with --buildpkg Ubuntu/precise
assuming you're running ubuntu 12.4.2, if you are running 12.10 replace precise with quantal. Note the capital U in Ubuntu.

That will create .deb-files in you current directory.
Install those with sudo dpkg -i fglrx*.deb.

---

### Post by l6griffin on 2013-02-06
I caught that, and also found that what I thought was a *hang* was actually the install window for Catalyst hidden. Not a clean install, so I've re-installed, and erased the previous install. I want this install to be near perfect. Hopefully I've learned all commands that need to be used. I may use the beta this time around. I've got a work around for finding finding the file. I've downloaded them to a USB drive.

Thanks for your help.

Larry

---

### Post by psychok9 on 2013-02-09
Hello guys! I'm a little confused with the "mux stuff".
On my Sony Vaio SVE1712Z1EB, I can't see integrated graphics neither on Windows 8, I've only Radeon HD 7650M on devices management, GPU section...
On Sony UEFI bios, no 1 option for switch integrated/dedicated.
The integrated (Intel i7 Ivy Bridge) seems totally disabled.
My impression is right or muxless configuration hide the integrated gpu?
Thank you.

---

### Post by belorios on 2013-02-10
Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

---

### Post by MarcoDePollo on 2013-02-10
> **psychok9 said:**
> Hello guys! I'm a little confused with the "mux stuff".
On my Sony Vaio SVE1712Z1EB, I can't see integrated graphics neither on Windows 8, I've only Radeon HD 7650M on devices management, GPU section...
On Sony UEFI bios, no 1 option for switch integrated/dedicated.
The integrated (Intel i7 Ivy Bridge) seems totally disabled.
My impression is right or muxless configuration hide the integrated gpu?
Thank you.

Your impressions sound right, if there is no option in BIOS to disable integrated graphics, it sounds like it is just disabled by default if the hardware isn't showing up in Windows.

---

### Post by MarcoDePollo on 2013-02-10
> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!


Congratulations:) Another success-story:)

---

### Post by andrikos on 2013-02-10
I have packaged the latest beta version from upstream ( 13.2-beta3 ) in my PPA:
[https://launchpad.net/~andrikos/+archive/xserver/](https://launchpad.net/~andrikos/+archive/xserver/)

In my system, this version resolves the problem of hubrid fglrx/intel in quantal without the need to change anything in the intel driver (just use the default 2:2.20.9-0ubuntu2 version shipping in quantal).

Could anyone please test these packages in your systems in order to see if this is a proper fix and if any regressions appear?

Thanks,
Nick

The commands to use, are appended. Please make use you have no third party repositories messing with your X server components (e.g. xorg-edgers):
```
sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/xserver
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f
```

---

### Post by shinylenin on 2013-02-11
I can confirm, this method works great!

I have a dv6 with an Intel card and HD6770M!


> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

---

### Post by psychok9 on 2013-02-11
> **MarcoDePollo said:**
> Your impressions sound right, if there is no option in BIOS to disable integrated graphics, it sounds like it is just disabled by default if the hardware isn't showing up in Windows.

In that case, I can consider it muxless (potentially hybrid) or without Intel totally mono-gpu?

I ask because I have several problems with the AMD driver, and the only ones that work are the 13.2 beta but with some problems on startup.

Thanks!

---

### Post by markackerman8@gmail.com on 2013-02-11
Wow another bitter disappointment :sad: I trried "Originally Posted by belorios" suggestion to the "T", and got the TTY1 blackscreen after the first suggested reboot.  I finished then last 7 steps with a little optimism - but NO JOY- ARGHHHHHHH.  

Thankfully for the last 2 months/14 the radeon driver has got me to 30% functionaloity in graphics - but i sure would love to get the proprietary graphics working !!!!!!!!!!!!!!!!!!!

And thanks for all the help so far from

MarcoDePollo, :KS
and recently ....
Kristoffer (belorios:KS
Cheers,  Mark
[email]markackerman8@gmail.com[/email]

---

### Post by MarcoDePollo on 2013-02-12
> **psychok9 said:**
> In that case, I can consider it muxless (potentially hybrid) or without Intel totally mono-gpu?

I ask because I have several problems with the AMD driver, and the only ones that work are the 13.2 beta but with some problems on startup.

Thanks!

Well, according to [Sony]("http://www.sony.co.uk/product/vaio-e-series/sve1712z1e") and [Intel]("http://ark.intel.com/products/71670/Intel-Core-i7-3632QM-Processor-6M-Cache-up-to-3_20-GHz-BGA") there is supposed to be Intel HD graphics - if you choose to configure your own E-series, it has an Intel HD option, so it is present. The spec-sheet for the CPU confirms it.

So, in your case, I'd say it's mono-gpu, the Intel HD is disabled.

As for the driver-troubles, well, I guess it's down to a bit of luck, really. I have only been able to use my AMD graphics on my laptop after I decided to give (K)Ubuntu Raring a spin.

---

### Post by belorios on 2013-02-12
> **MarcoDePollo said:**
> Congratulations:) Another success-story:)

Thanks! 

> **andrikos said:**
> I have packaged the latest beta version from upstream ( 13.2-beta3 ) in my PPA:
[https://launchpad.net/~andrikos/+archive/xserver/](https://launchpad.net/~andrikos/+archive/xserver/)

In my system, this version resolves the problem of hubrid fglrx/intel in quantal without the need to change anything in the intel driver (just use the default 2:2.20.9-0ubuntu2 version shipping in quantal).

Could anyone please test these packages in your systems in order to see if this is a proper fix and if any regressions appear?

Thanks,
Nick

The commands to use, are appended. Please make use you have no third party repositories messing with your X server components (e.g. xorg-edgers):
```
sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/xserver
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f
```

Thanks for your awesome work! I will test this tomorrow! 

> **shinylenin said:**
> I can confirm, this method works great!

I have a dv6 with an Intel card and HD6770M!

Congratulations! Glad it helped!

---

### Post by Souptik on 2013-02-12
> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

[COLOR=Red]Can anyone tell me what "Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages."  is ? 
A step-by-step guide for that step would be appreciated.:)[/COLOR]

---

### Post by psychok9 on 2013-02-12
> **Souptik said:**
> [COLOR=Red]Can anyone tell me what "Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages."  is ? 
A step-by-step guide for that step would be appreciated.:)[/COLOR]

Launch on your Ubuntu without parameters, 1st option.

---

### Post by Souptik on 2013-02-12
I tried out as told .... But the step 
```
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
```The output came : 
> Selecting previously unselected package fglrx-updates.
(Reading database ... 197702 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a9.010-0ubuntu1~andrik7_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx-updates_2%3a9.010-0ubuntu1~andrik7_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a9.010-0ubuntu1~andrik7_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-updates_2%3a9.010-0ubuntu1~andrik7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
I am giving the fglrx-uninstall.log file :
> *** AMD Catalyst(TM) Proprietary Driver Uninstall Log 2013-02-13 02:49:49 ***
File is missing from system /usr/lib/fglrx/switchlibGL.
File is missing from system /usr/lib/fglrx/switchlibglx.
File is missing from system /usr/lib/fglrx/fglrx-libGL.so.1.2.
File has been removed, //usr/lib/libGL.so.1.2, since last install.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.
What should I do ?? :confused:
Should I install the missing files and how ?? 
Or force uninstall ??

---

### Post by jwhirl06 on 2013-02-12
Has anyone gotten this to work on the 7850m? I've tried everything and get get it. It keeps reverting to low-graphics mode.

---

### Post by DowntownScience on 2013-02-12
First I would like to say thank-you!  Your development is incredible.
 
I followed Belorios's tutorial part way to the "T" and had it working after the first reboot. (after installing Catalyst 13.1)
 
However, instead of going with the PPA and commands he posted I went with your updated PPA and commands.  When I rebooted I got a black screen with a bunch of commands.  I'm a bit of an Ubuntu/Linux newbie so I wasn't sure what I was to capture for you and/or how!  Apologies.
 
My setup is:
 
Ubuntu 12.10 64-bit. (fresh install fully up to date)
Dell Optiplex 990 w/ integrated Intel VGA.  RADEON HD 6450 expansion card.
 
> **andrikos said:**
> I have packaged the latest beta version from upstream ( 13.2-beta3 ) in my PPA:
[https://launchpad.net/~andrikos/+archive/xserver/](https://launchpad.net/~andrikos/+archive/xserver/)
 
In my system, this version resolves the problem of hubrid fglrx/intel in quantal without the need to change anything in the intel driver (just use the default 2:2.20.9-0ubuntu2 version shipping in quantal).
 
Could anyone please test these packages in your systems in order to see if this is a proper fix and if any regressions appear?
 
Thanks,
Nick
 
The commands to use, are appended. Please make use you have no third party repositories messing with your X server components (e.g. xorg-edgers):
```
sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/xserver
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f
```

---

### Post by Souptik on 2013-02-12
[SIZE=3]Finally made it !!The first method posted by [Alexislavie]("http://ubuntuforums.org/member.php?u=1138228") works !!\\:D/[/SIZE]

Here:
[http://ubuntuforums.org/showthread.php?p=11712748&mode=linear#post11712748](http://ubuntuforums.org/showthread.php?p=11712748&mode=linear#post11712748)

Just some updates are required :

We have to use Catalyst 13.1 instead of 12.4.

Consequently , the download link given as : 
```
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)
``` should be ```
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip)
``` as pointed out by [MarcoDePollo]("http://ubuntuforums.org/member.php?u=1763412")



 As you can see this will give you a .zip file : Extract it and keep the extracted .run file in the same directory (not absolutely necessary but i would rather follow it) before applying the chmod +x command on it .




Needless to say ```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
``` has to be changed to Ubuntu/quantal if you are using Ubuntu 12.10 or Linux Mint 14 and the .run file name will change to [COLOR=Red]amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run[/COLOR]


[COLOR=Red][COLOR=Black]Hope this helps !![/COLOR]
[/COLOR]

---

### Post by jwhirl06 on 2013-02-13
I too an in the HP Envy crowd afflicted by many re-installs and no working options. Giving the directions above a try, as I haven't tried them in that order yet.

---

### Post by MarcoDePollo on 2013-02-13
> **jwhirl06 said:**
> I too an in the HP Envy crowd afflicted by many re-installs and no working options. Giving the directions above a try, as I haven't tried them in that order yet.

If it doesn't work you should give a daily build of Raring a shot, it worked for me.

---

### Post by jwhirl06 on 2013-02-13
> **MarcoDePollo said:**
> If it doesn't work you should give a daily build of Raring a shot, it worked for me.

Roger that, was copying the iso soon as you suggested it. Do I need any drivers or does it work out of the box?

---

### Post by jwhirl06 on 2013-02-13
No go on Ubuntu 13.04 with Andrikos PPA. Intel IvyBridge graphics works great out of the box, the second I install ATI from Andrikos PPA I've got a low graphics mode.

---

### Post by MarcoDePollo on 2013-02-13
> **jwhirl06 said:**
> No go on Ubuntu 13.04 with Andrikos PPA. Intel IvyBridge graphics works great out of the box, the second I install ATI from Andrikos PPA I've got a low graphics mode.

Try without Andrikos' PPA - either with regular fglrx or AMD's proprietary, though they lack kernel 3.8 support. I've had great success with the regular fglrx.

Note: there's a bug in initramfs so there is a chance of a coredump when the kernelmodules are being built. With the result that both my laptop and my desktop have an "unsupported hardware"-watermark - but it works great:)

---

### Post by jwhirl06 on 2013-02-13
> **MarcoDePollo said:**
> Try without Andrikos' PPA - either with regular fglrx or AMD's proprietary, though they lack kernel 3.8 support. I've had great success with the regular fglrx.

Note: there's a bug in initramfs so there is a chance of a coredump when the kernelmodules are being built. With the result that both my laptop and my desktop have an "unsupported hardware"-watermark - but it works great:)

Are you also on the IvyBridge and ATI 7xxx Series card on your laptop? I just don't want to hose up my new install.

---

### Post by MarcoDePollo on 2013-02-13
> **jwhirl06 said:**
> Are you also on the IvyBridge and ATI 7xxx Series card on your laptop? I just don't want to hose up my new install.

Sandy Bridge / HD6770 (I think, 6000-series anyway).

I fully understand not wanting to mess with a new install, once it's running, I just can't suppress my own desire to tinker;)

---

### Post by psychok9 on 2013-02-14
> **MarcoDePollo said:**
> Note: there's a bug in initramfs so there is a chance of a coredump when the kernelmodules are being built. With the result that both my laptop and my desktop have an "unsupported hardware"-watermark - but it works great:)

Hello! What's the bug? Does a workaround exist?
Sony Vaio, Intel i7 (HD4000 disabled) + HD 7650M (Catalyst 13.2 with watermark)
Thanks!

---

### Post by MarcoDePollo on 2013-02-14
> **psychok9 said:**
> Hello! What's the bug? Does a workaround exist?
Sony Vaio, Intel i7 (HD4000 disabled) + HD 7650M (Catalyst 13.2 with watermark)
Thanks!


[https://bugs.launchpad.net/debian/+source/kmod/+bug/1073062](https://bugs.launchpad.net/debian/+source/kmod/+bug/1073062)

No workaround yet... But, acceleration should work, at least it does for me and the catalyst control center sees the card and is more than willing to configure it.

---

### Post by ozp on 2013-02-16
Hello.

I have a Inspiron-7520 (15R Special edition) with ubuntu 12.10

It has intel HD 4000 and AMD Radeon HD 7700M Series (7730M)

I have vgaswitcheroo installed since I had to turn off the discrete card because of heat issues (CPU over 70°C). With IGD card only, its stays at 56°C.

sudo cat /sys/kernel/debug/vgaswitcheroo/switch - gives:

```

0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```


Also I had to install and configured the "i8kmon" deal, so the FAN could be controled. Before that the FAN would spin at maximum RPM all the time. (this is a issue for a lot of people with similar specs)

So, for now my system is usable, but of course that I'd like to have the proper AMD driver installed to get better performance.

What I dont know is if I can follow the step-by-step instructions at the first page because Its says that its for a "fresh install" of ubuntu. And I have the i8kmon and vgasitcheroo instaled....

I dont have a urge to use the AMD card, because I dont play with the computer and dont use any special app that requires the AMD performance.

So if there is a chance for better support and easy setup in the near future (ubuntu 13.04 for example), id ratter wait...

but if there is no chance for better support and easy setup in the near future, Id preffer to install the AMD driver now.

What do you say? 

regards

---

### Post by delsus on 2013-02-17
I was wondering if there have been any recent developments in hybrid graphics with radeon HD 5xxx series cards. All I want to do is use my discreet card for hardware acceleration and gaming, I have everything I need working in Ubuntu 12.10 except my discreet card. 

I can use echo DDIS > (path to switch file) then log out and it will switch to my discreet card, but when I use an  initramfs script applied to grub with these steps [https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup](https://help.ubuntu.com/community/HybridGraphics#Script_for_use_during_bootup) my integrated card is still being used.

Also I have an Intel 5 series chipset, anyone have any idea if I would be able to blacklist the driver for the intel GPU in order to force the laptop to use the discreet card, and if so which driver would I need to blacklist?

Thanks for any help.

---

### Post by CoOloKey on 2013-02-19
Hello guys, I have a Dell Vostro 3450, with board AMD / INTEL done the procedure as descritou worked perfectly, however when I switch to the integrated video it does not render the Unity leaving I only use the terminal, did step 2 as described only did not work.

One thing I noticed was that when I use the command "sudo aticonfig - px-iGPU" to change the plates he has some messages that do not seem normal, but following screenshots are in PT-BR:

```
weslei@Weslei-Dell-Vostro-3450:~$ sudo aticonfig --px-igpu 
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: aviso: saltar a criação de /etc/OpenCL/vendors/amdocl64.icd porque o ficheiro associado /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (do grupo de ligação i386-linux-gnu_gl_conf) não existe.
update-alternatives: aviso: saltar a criação de /usr/lib32/libaticalcl.so porque o ficheiro associado /usr/lib32/fglrx/libaticalcl.so (do grupo de ligação i386-linux-gnu_gl_conf) não existe.
update-alternatives: aviso: saltar a criação de /usr/lib32/libaticalrt.so porque o ficheiro associado /usr/lib32/fglrx/libaticalrt.so (do grupo de ligação i386-linux-gnu_gl_conf) não existe.

PowerXpress: Integrated GPU is selected (Power-Saving mode), please restart Xserver(s) for changes to take effect!
weslei@Weslei-Dell-Vostro-3450:~$ 
```

I'm using version 4.12 LTS as the topic and the Catalyst 12.10.

Sorry my writing used Google Translator:lolflag:

Thanks.

---

### Post by MeshachBlue on 2013-02-21
If you have followed other steps and end up with** low graphics mode**, simple move the** mouse,** click on **next/ok** then go **"open console"**. Log in, and type in:
```
startx
```I followed the following steps and I have a mostly stable system (every so often on boot it drops into low graphics mode and I have to follow the following steps. I haven't yet worked out why it runs this mode sometimes and not others...)



Instructions for Catalyst 13.1 with Ubuntu 12.10 64-bit

On my system the following set up is mostly stable. I have an HP dv6 Radeon 6770M with intel hybrid graphics.

This is adapted from Alexislavie's original post:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

And from the wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

**Step 1:**
Make sure *universe* and *multiverse* are enabled in your repository sources (System -> Administration -> Software Sources). or Applications->Ubuntu Software Center->Edit->Software sources->Other software: check canonical partners. 

**Step 2:**
Pre-requisite packages:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic
```For 64-bit users:
```
sudo apt-get install lib32gcc1
```[B]Step 3:
[/B]Download Catalyst 13.1, extract it, then mark it as executable:
```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip 
unzip amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip 
chmod +x amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run
```[B]Step 4:
[/B]Create and install the packages:
```
sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --buildpkg Ubuntu/quantal 
sudo dpkg -i fglrx*.deb
```Configure the x server:
```
sudo aticonfig --initial -f
```[I]

Reboot computer
[/I]
```
sudo aticonfig --px-dgpu
```[I]

Reboot Computer

[/I][B]Step 5:

[/B]Open the following file:
```
sudo gedit /etc/X11/Xsession.d/10fglrx
```for 32-bit make the file read:
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```For 64-bit:
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```[B]

Step 6:
[/B]Reboot, computer will open up into "low graphics mode". Shake the mouse, click "ok/next". Then Select "Open Console" (It's the bottom option) then "ok/next".

Log in to your user, (by typing your username and password into the terminal that appears)

Then type 
```
startx
```The computer should start as normal, although sometimes I am greeted only by my wallpaper and nothing else. If this is the case, press Ctrl + Alt + F2, then log in once more. And type: 
```
sudo shutdown -r now
```This will reboot your computer, and all should be fine on log in. (If it is not though, rinse and repeat step 6...)

---

### Post by ramivei on 2013-02-22
Hello,

I want to try and use ubuntu on my lenovo E520 with switchable graphics and ATI 6630. I saw this thread and I'm sure it has the solution for running ubuntu on my mechine. however, I don't want to read all the thread with it's 61 pages so can you direct me for the solution?

moreover, I am not very familiar yet with the linux terminal yet (I'm starting to study it).

Thanks

---

### Post by Niccola on 2013-02-22
Hey guys,
I've been working a lot last days and I have no time to test new released Catalyst 13.2 Beta 6 and **I would like to know if someone here tried it and give me some detailed response about driver functionality and fixed bugs/errors.**

Specifically someone which have a system with Intel HD3000 with AMD HD6XXXM Series...

I am running over Catalyst 13.2 beta3 and I have no problems at all. However, I heard my laptop fan yelling a lot and battery during only 2h over Intel HD3000 against 4h with older Catalyst drivers. Seems that 13.2 beta3 doesn't disable dGPU at all but not sure.

**Someone having same behavior?**

---

### Post by acetech on 2013-02-23
Hello guys,

          I am a novice in ubuntu, but I love to learn things. these are my recent experiences.  I just made a fresh install ubuntu 12.04.02 with everything upto date. then followed the procedure mentioned in the first post of this thread. everything went well with switching between the integrated and discrete working perfectly. Since i am in love with gnome3 installed gnome 3 in ubuntu12.04.02, this is when things started looking bad.  The switching between the cards worked but i encountered these problems 
 
1. when i am in integrated graphics card restart/shutdown (even by terminal too) is not proper i.e the system doesn't restart/shutdowns, with the screen saying segmentation fault

 2. but everything is fine when i use the discrete card  with the restart/shutdown.

the above are my experiences with lightdm and with gdm i get a perfect shutdown in integrated gpu but not a reboot.

Don't know what to do in gnome3.....
everything is fine in unity....

hope You guys would help me out....

My configuration  dell inspiron 7520 with intel hd4000/amd hd7730m 
ubuntu 12.04.02 
catalyst 13.1

---

### Post by aznboi on 2013-02-25
great thread, got switchable graphics working 100% on my HP g6 2200 Select Edition.

AMD 7670m 2GB
Intel 4000 HD

---

### Post by SimonDPRZ on 2013-02-25
nice thread got in switchable graphics working for intel hd4000 and radeon hd7970m 

just one questing last time i did linux updates why graphics stopped working. I didn't use this thread then it was just the propiarty driver 12.* Must i do something specific to update the linux updates? or is this problem fixed? 

greetz

---

### Post by StrikerNL on 2013-02-25
Works fine on HP Pavilion dv6-6b04ed

---

### Post by SimonDPRZ on 2013-02-25
I cheered to soon when i installed the drivers i played css and teamfortress 2 which ran great with amd  graphics then I switched to intel drivers now a few days later i switched to amd drivers and my laptop allways reboots in low graphics mode

---

### Post by hipermagic on 2013-02-25
So, I'm using HP Pavilion dv6 with AMD/intel graphics and I'm trying the new 13.2 beta 6 drivers. I followed the instalation guide provided [[COLOR="DarkOrange"]_here_[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL") and I always get the following bugs:

[SIZE="2"]-Graphic crash when I logout (system forces me to go on low-graphics mode)[/SIZE] --edit: this one is fixed now, I think.

-After a "long" (15~20 minutes) period of use, my computer is usually unable to reboot or shutdown, freezing while doing so (with no error message) and making me force shutdown.

Just wondering if anyone here has experienced similar problems and/or knows a fix for these.

---

### Post by dirimemat on 2013-02-26
Hello all,

I've been following this thread since the beginning. I was wondering if anyone had a chance to run fglrx drivers on a Sony Vaio VPCZ23 series. My specs are:

> 
$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
16:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]


I am running Ubuntu 12.10, with kernel 3.5.0-25-generic. I also tried 12.04. I did almost everything suggested in this topic, including Andrikos packages however everytime when I reboot my laptop, I end up with low graphics, then switch to tty1 and remove xorg.conf. I tried 13.1 beta6 lately, again with no success.

One thing I notice about my hardware on dmesg output is:
```

[    3.366033] drm: registered panic notifier
[    3.366161] [Firmware Bug]: ACPI(GFXA) defines _DOD but not _DOS
[    3.366971] acpi LNXVIDEO:02: registered as cooling_device4
[    3.367051] ACPI: Video Device [GFXA] (multi-head: yes  rom: no  post: no)
[    3.367079] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1e/device:1f/device:22/device:23/device:24/LNXVIDEO:00/input/input4
[    3.367134] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367138] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367140] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367143] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367146] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367149] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367152] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the curre
nt driver doesn't work.
[    3.367771] acpi device:3d: registered as cooling_device5
[    3.367857] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.367879] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:09/input/input5
[    3.367924] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.368182] [drm] initializing kernel modesetting (TURKS 0x1002:0x6740 0x104D:0x9084).
[    3.368209] [drm] register mmio base: 0xC0200000
[    3.368211] [drm] register mmio size: 131072
[    3.446297] ATOM BIOS: Sony
[    3.446349] [drm] GPU not posted. posting now...
[    3.450401] radeon 0000:16:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    3.450403] radeon 0000:16:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    3.450409] mtrr: no more MTRRs available
[    3.450410] [drm] Detected VRAM RAM=1024M, BAR=256M
[    3.450411] [drm] RAM width 128bits DDR

```

I have no idea if that firmware bug has anything to do with this or not.

Thank you and good luck to everyone. I hope I can run this after such a long time.

---

### Post by Wrezter on 2013-02-27
Hello!

I've got a Dell Inspiron 15 3521 notebook with the following specs:

- Intel Core i3-3217U 1.80GHz
- 6GB RAM
- 750GB HDD
- Intel HD Graphics 4000 + AMD Radeon 7670M 1GB

I'm using Ubuntu 12.04.

My problem is the next:

After a long time I have been able to install the proprietary AMD driver from the AMD site, and it seems that I can change between the two cards. In command line with the "aticonfig --px-igpu/dgpu" commands and with the graphical Catalyst Control Center too. The direct rendering in the IGPU is activated too. But even if this integrated card is active, the fan of the discrete card is running at full speed. (As without driver.)

I've tried to solve this problem with the "aticonfig --pplib-cmd "set fanspeed 0 50"" command, and with this utility:

[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

However, none of them worked. I don't know what to do. Any idea?

Thank you!

Wrezter

---

### Post by Wrezter on 2013-03-02
Any help? Since now I've tried almost everything, but I think I need to go back to Windows...

---

### Post by schender on 2013-03-02
Hi guys,


i obviously havé a little extra ordinary configuration.

Its an GeForce 7025 in the Core with an Athlon X2. And additionaly i have a Radeon 6600 HD as PCI-E.

I tried one time to get a hybrid system working on LMDE but  failed completly. I actually never read something with this combination of graphics cards-



Does some one know, if this is actually possible with LMDE?  On windows 7 i got this running, except the performance isnt that great.



Can someone help me with this? Problem is to get  a parallel installation of the two drivers gfxlr and nvidia. 

Can some one tell me if this is actually possiblke?

---

### Post by schender on 2013-03-02
can some one please comment my post? im googling my ass off and i dont get wiser

---

### Post by dirimemat on 2013-03-02
> **schender said:**
> can some one please comment my post? im googling my ass off and i dont get wiser

Welcome to the club :)

---

### Post by ozp on 2013-03-02
> **Wrezter said:**
>  the fan of the discrete card is running at full speed. (As without driver.)

I think the FAN problem is not related to drivers. 

You may be able to solve this annoyance by configuring the "i8kutils" deal

[http://askubuntu.com/a/256935/124181](http://askubuntu.com/a/256935/124181)

---

### Post by MarcoDePollo on 2013-03-03
> **schender said:**
> Hi guys,


i obviously havé a little extra ordinary configuration.

Its an GeForce 7025 in the Core with an Athlon X2. And additionaly i have a Radeon 6600 HD as PCI-E.

I tried one time to get a hybrid system working on LMDE but  failed completly. I actually never read something with this combination of graphics cards-



Does some one know, if this is actually possible with LMDE?  On windows 7 i got this running, except the performance isnt that great.



Can someone help me with this? Problem is to get  a parallel installation of the two drivers gfxlr and nvidia. 

Can some one tell me if this is actually possiblke?

That will not run as a hybrid solution - what you have in windows is either the Nvidia OR the AMD.
The Nvidia-graphics is integrated into the chipset on the motherboard and no designed for a hybrid-solution, 
so your best bet is to disable the integrated Nvidia-graphics in the BIOS and just use the AMD.

If you can't disable it, your bios should allow for a prioritized list (PCI-E->PCI->IGP). Remember to then reduce Video Memory to the lowest you can, so the integrated doesn't eat up memory that it won't need.

---

### Post by cheshire mouse on 2013-03-03
> **andrikos said:**
> 
```
sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/xserver
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f
```

[COLOR=#ff0000]didn't work[/COLOR] for me

 vostro 3550, ati HD6630M, ubuntu 12.10 x64 clean install

---

### Post by MarcoDePollo on 2013-03-03
> **cheshire mouse said:**
> [COLOR=#ff0000]didn't work[/COLOR] for me

 vostro 3550, ati HD6630M, ubuntu 12.10 x64 clean install

Maybe a nice "sudo lspci|grep VGA" would help - along with a description of how it "doesn't work"?


Just a tip to all the recent posters: If you can, disable the integrated graphics. Most, but not all, manufacturers provide this in BIOS
and will save you time and trouble.

Like a good friend told me earlier today; "Life is too short to mess with switchable graphics in Linux".

---

### Post by cheshire mouse on 2013-03-04
> **MarcoDePollo said:**
> Maybe a nice "sudo lspci|grep VGA" would help - along with a description of how it "doesn't work"?


here is lspci
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] (rev ff)

```

 and Xorg.log after reboot
[http://paste.ubuntu.com/5585285/](http://paste.ubuntu.com/5585285/)

---

### Post by Unclean009 on 2013-03-04
I had a solution to this issue a few months ago on my HP Probook 4530s but recently reformatted and now am having issues again.... sigh.

---

### Post by MarcoDePollo on 2013-03-04
> **cheshire mouse said:**
> here is lspci
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] (rev ff)

```

 and Xorg.log after reboot
[http://paste.ubuntu.com/5585285/](http://paste.ubuntu.com/5585285/)

See if this makes a difference: [https://bbs.archlinux.org/viewtopic.php?id=145358](https://bbs.archlinux.org/viewtopic.php?id=145358)
(solution is in comment #4)


Should you end up with the watermark, it is easily removed.

---

### Post by cheshire mouse on 2013-03-05
> **MarcoDePollo said:**
> See if this makes a difference: [https://bbs.archlinux.org/viewtopic.php?id=145358](https://bbs.archlinux.org/viewtopic.php?id=145358)
(solution is in comment #4)

comment #4 changed things but system is still unusable: after logon there is no dash, no panel and windows are without decoration (no titles, no close/minimize buttons)
if i switch to igpu (aticonfig --px-igpu) everything works as it should

xorg log [http://paste.ubuntu.com/5588158/](http://paste.ubuntu.com/5588158/)

---

### Post by Aoi v1 on 2013-03-05
Just did a fresh install of LM 14.1, Sony VAIO VPCCA-17FL, Radeon 6630m... It's been more than a year that I had to switch back to windows because of my computer's crappy hybryd card :( Back then this thread didn't exist and I've read it almost completely. I'll try several solutions posted in here and report everything ASAP. ;) If you've got any suggestions on which solutions definitely don't work with this model or which ones I should try first, just tell me.

Update, Catalyst 13.1 drivers did not work, on restart X server was not able to start. Going to try other solutions.

---

### Post by Aoi v1 on 2013-03-06
I just tried this method on a Vaio VPPCA17FL, Intel Sandybridge HD3000 ADM Radeon HD6630m... X server crashed after the first mentioned reboot, but after finishing it all went pretty good! =D temperature has gone below 56°C to 49°C (through sensors). It's way too late already, so I'll test the graphics tomorrow. Big thanks to every single person who has been contributing for the past 15 or so months!! :') 

> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

---

### Post by Srocchi on 2013-03-06
Worked right on my Dell with AMD7730/Intel HD 4000. I will try the HDMI and VGA port tests when I have a TV or a monitor accessible.


[LIST]
[*][FONT=Arial][SIZE=2]**DELL Inspiron 1[SIZE=2]5[/SIZE]R SE (N7520)**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 4000, AMD 7730m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[/LIST]

---

### Post by Unclean009 on 2013-03-07
> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

I made it to this part quickly but I'm afraid to try to switch to the intel gpu in the chance of not booting.

---

### Post by innsmouthrain on 2013-03-07
Reporting a success for Clevo 150em, also known as XMGP502 with customization as below.

No problems experienced whatsoever as soon as I found this forum post. However it took me a couple of days to get through the jungle of other stuff on google to get here. Most hits on the google "linux ATI 7970m" or "ubuntu p150em" gave posts from 2010 or users _speculating_ about whether they could use the hybrid graphics or not. Most threads ended with someone using only the integrated card (what a waste!!). I am happy I found this thread. 

Thanks a bunch :)

[COLOR=#666666][FONT=Arial]XMG P502 PRO Gaming Notebook 39,6 cm (15.6 ") [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. 39.6 cm (15.6 ") Full HD (1920 * 1080) Non-Glare [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. AMD Radeon HD 7970M 2048MB GDDR5 | TDP: 100W [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. Intel Core i7-3630QM - 2.40 to 3.40 GHz 6MB 45W [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. 16GB (2x8192) SO-DIMM DDR3 RAM 1600MHz Crucial [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. 1000GB SATA II 5400rpm Seagate Momentus (ST1000LM024) [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. Crucial M4 256GB mSATA SSD (CT256M4SSD3) [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. Support frame for additional SATA-II hard drive (instead of the optical drive) for XMG XMG P501 and P502 [/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]. Intel Centrino Advanced-N 6235 (with Bluetooth) [/FONT][/COLOR]

---

### Post by Aoi v1 on 2013-03-07
Everything was going ok, but suddenly something went wrong... after installing Catalyst and switching to the Intel graphics card, 90% of times after rebooting, I get the error "KVM disabled by BIOS"... I checked it and indeed it was disabled, but enabling it does nothing, LM just won't start :( any way of changing to AMD graphics card? BIOS doesn't show any option.

---

### Post by petecan on 2013-03-08
To innsmouthtrain: I'm so jealous. I have a quite similar machine (Clevo 150em + HD7970M) and I have been now fighting for 4 days with the ATI drivers. Frustration is as much that I'm even thinking of returning the new shiny laptop. The most I get is to install the drivers from andrikos or from ATI. It still boots up in "low graphics mode" and for making it work better I need to remove the line *"BusID       "PCI:1:0:0""* in xorg.conf. Then it boots but glxinfo fails miserably when I activate the dgpu - so it is quite useless. Paradoxically, switching to the igpu makes the fan run constantly, but glxinfo works.

Once I though I had it working but then, for no reason, it started to be broken again. So can you confirm that there is a way to get the ATI GPU fully working? Is it the *"Install 12.10 -> 13.1 from ATI -> 13.2 from andrikos"* way? Could you share with me your xorg.conf?

Thanks a million!

> **innsmouthrain said:**
> Reporting a success for Clevo 150em, also known as XMGP502 with customization as below.

No problems experienced whatsoever as soon as I found this forum post. However it took me a couple of days to get through the jungle of other stuff on google to get here. 

---

### Post by innsmouthrain on 2013-03-08
> **petecan said:**
> To innsmouthtrain: I'm so jealous. I have a quite similar machine (Clevo 150em + HD7970M) and I have been now fighting for 4 days with the ATI drivers. Frustration is as much that I'm even thinking of returning the new shiny laptop. The most I get is to install the drivers from andrikos or from ATI. It still boots up in "low graphics mode" and for making it work better I need to remove the line *"BusID       "PCI:1:0:0""* in xorg.conf. Then it boots but glxinfo fails miserably when I activate the dgpu - so it is quite useless. Paradoxically, switching to the igpu makes the fan run constantly, but glxinfo works.

Once I though I had it working but then, for no reason, it started to be broken again. So can you confirm that there is a way to get the ATI GPU fully working? Is it the *"Install 12.10 -> 13.1 from ATI -> 13.2 from andrikos"* way? Could you share with me your xorg.conf?

Thanks a million!


Hi dude!

No problem! 

First, I must remember to tell you that I am using Xubuntu 12.04. Gnome will mess up your gaming experience anyway, so if you want performance, try to stay off it. Personally, I find the methods I have used to be poorly documented and most of the time I have no deep understanding of what I am doing, just copying commands other people write. This is generally not a very efficient way of figuring out the root cause of problems and achieving the result you are after. But the both the hardware and this technology as a whole is very new and so I just try to mess around until I get something working  and then figure out as much as I can afterwards. Just you know, don't get frustrated and angry with yourself. Nobody seems to fully know how to get it working yet.

I have pasted my xorg.conf below, but I'm not sure if it will help you. I followed the steps in this first post here in the thread very precisely except for the driver download which I took from the wiki link he pasted. I also read that wiki page thouroughly and followed their procedure for removing the old drivers before anything else. Try to make sure you follow the steps correctly. If you're afraid that you have some settings wrong you can back up your files and restart the system installation from start, it doesn't take long on a beast of a machine like this.

I also posted my grub conf, in case you have some settings wrong there. By the way, the dwords part in my xorgs aren't working. I'm trying to get the brightness keys running so I d That way I can make sure it actually works.

```
 moth@charm:~$ cat /etc/X11/xorg.confSection "ServerLayout"
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
        BusID       "PCI:1:0:0"
        Option "RegistryDwords" "EnableBrightnessControl=1"
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

```
And here is my /etc/default/grub:
```
moth@charm:~$ cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text modeset=1 acpi_backlight=vendor acpi_osi=Linux"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```


The first poster already posted this link, but in case you missed it: the wiki link, [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

### Post by acetech on 2013-03-10
Hi guys,

I just made a clean install of ubuntu 12.04 and after upataing the packages I just made through the switchable graphics process as mentioned in the first thread of this post. Everything worked fine. Strangely when I made my system to reboot/shutdown from my integrated gpu, it doesn't get restarted/shutsdown. The screen shows segmentation fault in the last line and hangs there indefinitely until i manually press my power button to power off the system. I do have one doubt, earlier i used to have the so called fancy Advanced format drives with my ubuntu partition misaligned by 1024 bytes. Could this segmentation fault be associated with this misalignment?

This is my experience from switchable graphics and I just wanted to know whether some of you guys have already experienced/ experiencimg the problem of booting/shutting down only from discrete gpu? I don't mind using only the dgpu....

---

### Post by petecan on 2013-03-11
Thanks a million innsmouthrain (quick note, [the brightness keys work with kernels >=3.7]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041116") out of the box). Knowing that there was at least someone with essentially my exact same system (a Clevo 150em + AMD 7970m) and a working linux installation was essential for me to keep the computer, as windows would have never been an option. Now I have it (sort of) working! And I believe things will get much better soon, when hopefully the drivers in the official repos will work out of the box and more and more people with enduros will be working in linux. I put my money on a couple of months after raring is released.

Right now I have an ubuntu 12.10 + 13.2beta7 drivers working, getting great performance on GPGPU computations out of the graphics card. The igpu does not work so well, the fan is always on and in order to change back to the dgpu I need to tweak LD_LIBRARY_PATH and reboot a couple of times. So at the moment I work only with the DGPU on an external screen connected via DVI.

For the records, a will distill how I got it and a few of the ways how I did not get it. During my first attempts, I was unsuccessful  with either 12.04 or 12.10. This was probably my bad, as I was trying to follow the instructions in the [unofficial AMD linux community]("http://wiki.cchtml.com/index.php/Main_Page"), that seem to be correct if one follows them carefully. An extra complication in my case is that I was trying to make it work with my external monitor, which turns out to be another source of frustration with enduro. After a few attempts, and after realizing that there were already drivers for raring in [Nick Andrik's PPA]("https://launchpad.net/~andrikos/+archive/ppa") I decided to install the daily snapshot of ubuntu 13.04. That was a great success for the first few hours, as not only the graphics card was properlly set-up but also the external monitor was working much faster (with my current setup it takes about a minute to show something, then everything works well). I think xorg (intel drivers) is getting better in that release. Unfortunatelly, (my bad again) I accepted a kernel update that broke the whole system again. And then I was unable to get it working back, even reinstalling from scratch. This was really frustrating, because I can cope with early versions of the drivers and broken installation procedures, but it is harder to cope with things that sometimes work, sometimes, depending on the order things are done and the versions of the kernel/xorg/drivers.

At that point, I decided not to try anymore with raring and stick with an stable, officially supported by AMD distro. So I came back to 12.10, and as suggested by a previous post I 1) installed 13.1 using the AMD installer and 2) installed Nick Andrik's ubuntu-repack of the 13.2 beta3 drivers. With this I got the working setup I have right now. With the following annoyances:
[LIST]
[*]The power-express settings are not remembered between sessions. So at the moment I need to open the catalyst center and change to low-performance if I want the GPU fan to stay quite while I'm not launching computations at it. 
[*]Some tools, like shutter, do not work properly. 
[*]The external monitor takes about one minute to get the image. Then it works normally, and I know that this seems to get fixed in the next release of ubunut, around the corner. 
[*]Switching to the intel gpu is unusable: the fan is crazy. Since it works for other people, a wild guess is that this is due to this bizarre driver installation over driver installation I have. In fact, there is [a big problem with the OpenGL ]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1068404")libraries here: the switcher/update alternatives script from AMD gets it wrong and puts a 0-sized library in */usr/lib/libGL1.2.so*. This does not allow to switch back to dgpu (amdconfig) does not work. A workaround (only useful to be able to switch back to dgpu, the system is still broken) is to use *ls /usr/lib/fglrx/fglrx-libGL.so.1.2* instead (and boot a couple of times, as the first one we get some pretty segmentation fault). For example: 
[/LIST]
```

sudo ln -s */usr/lib/fglrx/fglrx-libGL.so.1.2* */usr/lib/fglrx/libGL.so.1.2*
sudo ln -s */usr/lib/fglrx/libGL.so.1.2* [I]/usr/lib/fglrx/libGL.so.1
sudo LD_LIBRARY_PATH=[/I]*/usr/lib/fglrx/ amdconfig --px-dgpu*

```

Trying to fix those I installed version 13.2beta7 again directly using AMD installer, which proved to be not better nor worse (except that probably screwed up a bit more the problem with the libraries). I will for sure try to fix the mess with my messy installation and all the other problems soon enough, after I rest a bit from so much restarting the machine (and perhaps doing something useful with the computer, for a change!). If I find something I will post it here. In any case, a note of optimism: my current setup is already good enough and I believe things are gonna get much more hassle-free when ubuntu raring is released.

---

### Post by snake2903 on 2013-03-14
> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10 
[*]Upgrade 
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

``` 
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages. 
[*]REBOOT 
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

``` 
[*]Reboot 
[/LIST]
Now it's time for champagne!

Hi, i have HP ProBook 4730s with Intel HD3000 integrated and AMD Radeon HD 6490M discrete graphic cards, and fresh install of Linux Mint 14 ( Ubuntu 12.10).
I tried this tutorial and after installing 13.1 drivers, Xserver didn't start, but in terminal run rest of command and everything works ok.
I run Catalyst Control Center and switch to my Intel card.... after restart all works.
But there is one problem....

After installing everything i installed latest version of Adobe Flash player downloaded from their website... and after installation Xserver didn't started... i try to reinstall everything but nothing helps.


What could be the problem with Adobe Flash and this drivers?

---

### Post by Mohamed Elsayed on 2013-03-15
[COLOR=#000000]Hi, i have HP pavilion Dv6-6b80ee with Intel HD3000 integrated and AMD Radeon HD 6770M discrete graphic cards.
my problem is "no direct rendering" with integrated graphics card

[/COLOR][COLOR=#000000]
[/COLOR]```
$ glxinfo | egrep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
```
[COLOR=#000000]

[/COLOR]```
$ gksu gedit /etc/X11/Xsession.d/10fglrx
[COLOR=#000000]
[/COLOR]LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri
if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/lib32/fglrx/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
    if [ ! -z $LD_LIBRARY_PATH ]; then
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:
    fi
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
    export LD_LIBRARY_PATH
  fi
fi
export LIBGL_DRIVERS_PATH
```
[COLOR=#000000]

[/COLOR]```
$ echo $LIBGL_DRIVERS_PATH[COLOR=#000000]
[/COLOR]/usr/lib/fglrx/dri
```


any help please?

---

### Post by dirimemat on 2013-03-15
Has anyone tested his hybrid system with 13.04 beta release?

---

### Post by Mohamed Elsayed on 2013-03-16
> **phoenix6434 said:**
> For all pangolin (32 bit) users with an AMD/Intel Hybrid Graphic Solution. It's possible to use the installation via apt. There's also a direct rendering bug on the integrated card. Here is my solution

You can install the fglrx driver via apt.

```
sudo apt-get install fglrx
```

after installation let's configure the Xserver (xorg.conf file) for the first time:

```
sudo aticonfig --initial -f
```

There is also the bug for direct rendering on the integrated card. To fix it you have to edit the following file (it's nearly the same fix like the one from Niccola):

```
gksu gedit /etc/X11/Xsession.d/10fglrx
```

If you're using a 32bit system add at the end of 1th line this text : ":/usr/lib/i386-linux-gnu/dri" without the quotes. The file should now look like this :


```


LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib/i386-linux-gnu/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH

```

If you have the integrated card activated reboot your system.

You can check the result after the reboot with glxinfo. If direct rendering is activated, it shows "direct rendering: yes".

```
glxinfo | grep rendering
```

You can also test it with the glxgears command.

Unity 3d should work now in integrated mode.


thank you very much.It's working now.I've been searching for about 8 months to make it work.
I have hp pavilion Dv6-6b80ee with intel HD3000 and AMD radeon 6770M.now direct rendering is working with integrated card
thank you again:)

---

### Post by MarcoDePollo on 2013-03-18
AMD has released 13.3 beta 2, now with kernel 3.7/3.8 support. For those running 13.04, packages can be built with 
```
--buildpkg Ubuntu/raring
```

[Get it here]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13.3-beta2-linux-x86.x86_64.zip")

---

### Post by htrex on 2013-03-22
> **MarcoDePollo said:**
> AMD has released 13.3 beta 2, now with kernel 3.7/3.8 support. For those running 13.04, packages can be built with 
```
--buildpkg Ubuntu/raring
```

[Get it here]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13.3-beta2-linux-x86.x86_64.zip")

I'm tring Catalyst 13.3 beta2 self built packages on a dual GPU (Intel i7/AMD 6770) HP notebook and unhopefully X can't start, nothing works so far to have a fully functional Ubuntu 13.04 graphical desktop.

---

### Post by Fake Sketch on 2013-03-23
I have followed step by step the guide but I have 1 problem:

When I do[FONT=Ubuntu Mono][COLOR=#000000]: "[/COLOR][/FONT]sudo dpkg -i fglrx*.deb" I get a system error that states that fglrx had an error while installing and thus failed to install.

Note that I used the same version and same computer as de OP.

---

### Post by innsmouth.rain on 2013-03-23
> **petecan said:**
> Thanks a million innsmouthrain (quick note, [the brightness keys work with kernels >=3.7]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041116") out of the box). Knowing that there was at least someone with essentially my exact same system (a Clevo 150em + AMD 7970m) and a working linux installation was essential for me to keep the computer, as windows would have never been an option. Now I have it (sort of) working! And I believe things will get much better soon, when hopefully the drivers in the official repos will work out of the box and more and more people with enduros will be working in linux. I put my money on a couple of months after raring is released.

Right now I have an ubuntu 12.10 + 13.2beta7 drivers working, getting great performance on GPGPU computations out of the graphics card. The igpu does not work so well, the fan is always on and in order to change back to the dgpu I need to tweak LD_LIBRARY_PATH and reboot a couple of times. So at the moment I work only with the DGPU on an external screen connected via DVI.

For the records, a will distill how I got it and a few of the ways how I did not get it. During my first attempts, I was unsuccessful  with either 12.04 or 12.10. This was probably my bad, as I was trying to follow the instructions in the [unofficial AMD linux community]("http://wiki.cchtml.com/index.php/Main_Page"), that seem to be correct if one follows them carefully. An extra complication in my case is that I was trying to make it work with my external monitor, which turns out to be another source of frustration with enduro. After a few attempts, and after realizing that there were already drivers for raring in [Nick Andrik's PPA]("https://launchpad.net/~andrikos/+archive/ppa") I decided to install the daily snapshot of ubuntu 13.04. That was a great success for the first few hours, as not only the graphics card was properlly set-up but also the external monitor was working much faster (with my current setup it takes about a minute to show something, then everything works well). I think xorg (intel drivers) is getting better in that release. Unfortunatelly, (my bad again) I accepted a kernel update that broke the whole system again. And then I was unable to get it working back, even reinstalling from scratch. This was really frustrating, because I can cope with early versions of the drivers and broken installation procedures, but it is harder to cope with things that sometimes work, sometimes, depending on the order things are done and the versions of the kernel/xorg/drivers.

At that point, I decided not to try anymore with raring and stick with an stable, officially supported by AMD distro. So I came back to 12.10, and as suggested by a previous post I 1) installed 13.1 using the AMD installer and 2) installed Nick Andrik's ubuntu-repack of the 13.2 beta3 drivers. With this I got the working setup I have right now. With the following annoyances:
[LIST]
[*]The power-express settings are not remembered between sessions. So at the moment I need to open the catalyst center and change to low-performance if I want the GPU fan to stay quite while I'm not launching computations at it.
[*]Some tools, like shutter, do not work properly.
[*]The external monitor takes about one minute to get the image. Then it works normally, and I know that this seems to get fixed in the next release of ubunut, around the corner.
[*]Switching to the intel gpu is unusable: the fan is crazy. Since it works for other people, a wild guess is that this is due to this bizarre driver installation over driver installation I have. In fact, there is [a big problem with the OpenGL ]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1068404")libraries here: the switcher/update alternatives script from AMD gets it wrong and puts a 0-sized library in */usr/lib/libGL1.2.so*. This does not allow to switch back to dgpu (amdconfig) does not work. A workaround (only useful to be able to switch back to dgpu, the system is still broken) is to use *ls /usr/lib/fglrx/fglrx-libGL.so.1.2* instead (and boot a couple of times, as the first one we get some pretty segmentation fault). For example:
[/LIST]
```

sudo ln -s */usr/lib/fglrx/fglrx-libGL.so.1.2* */usr/lib/fglrx/libGL.so.1.2*
sudo ln -s */usr/lib/fglrx/libGL.so.1.2* [I]/usr/lib/fglrx/libGL.so.1
sudo LD_LIBRARY_PATH=[/I]*/usr/lib/fglrx/ amdconfig --px-dgpu*

```

Trying to fix those I installed version 13.2beta7 again directly using AMD installer, which proved to be not better nor worse (except that probably screwed up a bit more the problem with the libraries). I will for sure try to fix the mess with my messy installation and all the other problems soon enough, after I rest a bit from so much restarting the machine (and perhaps doing something useful with the computer, for a change!). If I find something I will post it here. In any case, a note of optimism: my current setup is already good enough and I believe things are gonna get much more hassle-free when ubuntu raring is released.

Glad to hear it's working out ;)

I couldn't get dota 2 working with wine and while trying to fix it the sound unexplicably just died system-wide. I tried to find a solution on google but the endless amounts of threads about similar problems combined with the Ubuntu community's attitude of "just do this and it will work" made it a horrible experience to me. 
Imagine:
 1. Have a problem
 2. Google for error message
3. Find a thread
4. Reply to thread is "downgrade kernel"
5. TS says "It worked!"
end of story.

I really, really could not find any technical information about any problems I had. Despite browsing for hours through tons of posts.

What if I don't want to downgrade my kernel? What if I want brightness keys still intact for instance? The replies need to be of the form:

"I think this is the root cause, can you see if you have any errors in <thislog.log> ?
 Yes, it says <blahblah>
 Then changing this option/upgrading this driver/uninstalling this feature will fix it"

This way it is actually possible to fix things. Permanently. I wish this community would post technical information. Not just random "advice" without explanation. 

The frustration from the quickfix attitude made me leave Ubuntu and I now have a working set-up on Arch Linux instead.

Goodbye Ubuntu, I loved you when I met you in 2004, but you seem to have grown into something that is too much like windows and too little like linux.

---

### Post by lucas castro on 2013-03-23
I've followed these instructions and my integrated/intel graphics seems to work fine, I can switch the graphics easily too. However, when a I use the discrete/High performance card, my cairo dock and its desklets, begins to flash at random without stopping, specially when I mouse over one of them the flashing becomes more intense. Do you know why this happen ? Is there anything that I do in order to fix this ?

Thanks,
Lucas

---

### Post by MarcoDePollo on 2013-03-25
AMD has released 13.3 Beta 3, this time with actual patch-notes:
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

The driver can be downloaded [here]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.zip")

---

### Post by jwhirl06 on 2013-03-25
> **MarcoDePollo said:**
> AMD has released 13.3 Beta 3, this time with actual patch-notes:
[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

The driver can be downloaded [here]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.zip")

Will give this a stab now, gonna reinstall a fresh build of 12.10. See where it gets me. Has anyone gotten the new drivers to work on an 3rd Gen i7/Radeon HD 7850M combo yet?

---

### Post by markackerman8@gmail.com on 2013-03-30
This is my bimonthly attempt # 122 to get proprietary ATI /AMD 6850m working. :mad:  

Now 15 months trying with no success, except with open source default drivers. :) I have posted over 20 posts here with a lot of help but still no functionality.  Here is what I am trying on my second root partition with Raring installed.

Uninstall firstly the current AMD driver with these two commands:
&#8728; sudo sh /usr/share/ati/fglrx-uninstall.sh
&#8728; sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
&#8728; andrikos  03/30/13 - trying AGAIN
    &#8227; sudo apt-get purge fglrx*
    &#8227; sudo add-apt-repository ppa:andrikos
    &#8227; sudo apt-get update
    &#8227; Update the fglrx and intel drivers:
      &#8226; sudo apt-get install fglrx xserver-xorg-video-intel
    &#8227; Don't forget to enable the fglrx driver
      &#8226; sudo aticonfig --initial --force
and about to reboot - If like all other 100 attempts I expect it to on go to ttf1 (terminal type screen), :mad:

If it works I will DEFINITELY post it.  But assume it won't and tired of wasting my time.  Anyone with sympothy and any novel ideas out their?  I would surely like to get this OLD problem fixed.  :P

Cheers, Mark

p.s. Confirmed  - it DID NOT work, back to tty1, and removing /etc/Xorg/xorg.conf and startx got me back in with no opengl functionality
any direct contact to [email]markackerman8@gmail.com[/email] would be much appreciated - getting sick of this, arghhh :-(

---

### Post by MarcoDePollo on 2013-03-31
> **markackerman8@gmail.com said:**
> This is my bimonthly attempt # 122 to get proprietary ATI /AMD 6850m working. :mad:  

Now 15 months trying with no success, except with open source default drivers. :) I have posted over 20 posts here with a lot of help but still no functionality.  Here is what I am trying on my second root partition with Raring installed.

Uninstall firstly the current AMD driver with these two commands:
&#8728; sudo sh /usr/share/ati/fglrx-uninstall.sh
&#8728; sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
&#8728; andrikos  03/30/13 - trying AGAIN
    &#8227; sudo apt-get purge fglrx*
    &#8227; sudo add-apt-repository ppa:andrikos
    &#8227; sudo apt-get update
    &#8227; Update the fglrx and intel drivers:
      • sudo apt-get install fglrx xserver-xorg-video-intel
    &#8227; Don't forget to enable the fglrx driver
      • sudo aticonfig --initial --force
and about to reboot - If like all other 100 attempts I expect it to on go to ttf1 (terminal type screen), :mad:

If it works I will DEFINITELY post it.  But assume it won't and tired of wasting my time.  Anyone with sympothy and any novel ideas out their?  I would surely like to get this OLD problem fixed.  :P

Cheers, Mark

p.s. Confirmed  - it DID NOT work, back to tty1, and removing /etc/Xorg/xorg.conf and startx got me back in with no opengl functionality
any direct contact to [EMAIL="markackerman8@gmail.com"]markackerman8@gmail.com[/EMAIL] would be much appreciated - getting sick of this, arghhh :-(

Skip Andrikos' repo and go straight for AMD's driver, try the latest beta.
Try and start X without doing "aticonfig --initial -f"
If the xorg.log complains about not finding a device on pci@1:0:1, try and remove the pci-identifier from xorg.conf

And finally, lots of sympathy - had raring/kernel 3.8 not fixed my own woes I'd have thrown the laptop out the window.

---

### Post by vindolin on 2013-04-01
> **markackerman8@gmail.com said:**
> and about to reboot - If like all other 100 attempts I expect it to on go to ttf1 (terminal type screen), [IMG]http://ubuntuforums.org/images/smilies/icon_mad.gif[/IMG]

Do you start from SSD?
In 95% of all boots my 12.10 does not boot to the desktop and I have to "sudo service lightdm restart" to get there.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489), [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410)

---

### Post by jwhirl06 on 2013-04-04
Has anyone had any success with the 7850M and the Sandybridge graphics?

---

### Post by bradgy on 2013-04-08
> **belorios said:**
> Hi all!

Read alot of the posts on this board, and some other boards =), and I worked my own way of getting hybrid graphics to work on my Vostro 3350 (hd3000/hd6490).

So here is my steps for any of you who cannot get it to work by the steps previously described. 

[LIST=1]
[*]Fresh install of 12.10
[*]Upgrade
[*]Installed Linux source and headers
```

sudo apt-get install linux-source linux-headers-generic

```
[*]Install official driver from AMD (13.1), run the installer and install the driver directly **WITHOUT **generating packages.
[*]REBOOT
[*]Run the following commands to install drivers from Andrikos ppa
```

sudo apt-get purge fglrx* 
sudo add-apt-repository ppa:andrikos/ppa 
sudo apt-get update 
sudo apt-get -y upgrade 
sudo apt-get --reinstall install xserver-xorg-video-intel 
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates 
sudo aticonfig --initial -f

```
[*]Reboot
[/LIST]
Now it's time for champagne!

So, this method worked for me, after so long trying to get switchable graphics going!!

I used the 13.3 beta drivers instead of the 13.1 stable and it appears step 6 onwards isn't needed... I'm still trialling things though. Will keep y'all updated.

I have a feeling this'll work for raring too, but I haven't upgraded yet. Still getting used to a fully functional ubuntu desktop!!

HP DV6 6146 tx i7 2630QM (sandyb) 8GB x64 Ubuntu 12.10 Intel HD 3000, AMD 6770m, HDMI Intel/AMD: working/working, VGA Intel/AMD: not tested/not tested

Thanks again to all the help on this thread!

---

### Post by tmacyunn on 2013-04-09
any good news for 13.04 ?

---

### Post by petecan on 2013-04-11
Regarding 13.04, I wouldn't go for that yet. At least wait until it is officially supported by catalyst.

I have a clevo p150em (intel HD 4000) wit a radeon HD7970m.

In the last couple of days I have backed up my "almost-working" (discrete gpu yes, intel gpu no) 12.10 setup and tried an update to 13.04. Once there, I cleaned up the drivers and installed 13.3beta3. Unfortunately I was unable to make the dgpu work. Most probably I was bitten by another bug regarding the coordination of intel and catalyst drivers on loading, the symptons as follows in Xorg.log

```

[    16.634] (EE) fglrx(0): Failed to allocate caches, disabling RENDER acceleration
[    16.638] (EE) fglrx(0): [intel] Failed to allocate video resources for front buffer 1920x1080 at depth 24
```

A quick search for this reveals the following posts:
[LIST]
[*][http://forums.gentoo.org/viewtopic-t-949372-start-0.html](http://forums.gentoo.org/viewtopic-t-949372-start-0.html) 
[*][https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1068404](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1068404) 
[/LIST]

As you see, a change in the (kernel) intel driver can get things nasty. I  tried to apply a suggested patch to the raring kernel, but with no joy  (actually something very similar was already there). The bug in ubuntu has just been assigned to the "Canonical X Group", but I think the ball is more on the AMD side. They will need to fix their catalyst driver to make it work with the latest intel driver on Enduro, at least with my machine. And I think they are aware of these problems (I haven't been able to find a place to submit bugs directly to the AMD fglrx crew though).

So now I'm back to my dirty but working 12.10 setup and I will keep an eye on the bug progression. I will probably wait a bit until things get released to try again.

---

### Post by Aikidoka69 on 2013-04-14
Arg!  Been trying to get this running for about a day after having it work in 12.10.  Went to 13.04 as 12.10 out of the box kept giving me errors and MTP was not working for my Razr Maxx HD.  Looks like I'll just use the Intel GPU for while instead of going back.

---

### Post by ppierpaolo on 2013-04-19
I've got an** AMD HD 8730M** Graphic card and I recently installed Ubuntu 12.10.
Ubuntu only recognizes my Intel HD Graphics 4000 card, and this causes my Dell Inspiron 15r 5521 to overheat.

Does the guide above work for AMD HD 8730M graphic cards?
If not, what can I do? How can I use that graphic card? I don't want to delete Ubuntu and go back to Windows.

---

### Post by MarcoDePollo on 2013-04-20
> **ppierpaolo said:**
> I've got an** AMD HD 8730M** Graphic card and I recently installed Ubuntu 12.10.
Ubuntu only recognizes my Intel HD Graphics 4000 card, and this causes my Dell Inspiron 15r 5521 to overheat.

Does the guide above work for AMD HD 8730M graphic cards?
If not, what can I do? How can I use that graphic card? I don't want to delete Ubuntu and go back to Windows.

There's a few options available here. First, you can try with Andrikos' PPA:

```

sudo apt-get purge fglrx*
sudo add-apt-repository ppa:andrikos/ppa
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get --reinstall install xserver-xorg-video-intel
sudo apt-get -y install fglrx-updates fglrx-amdcccle-updates
sudo aticonfig --initial -f

```
This will replace the existing Intel-driver with Andrikos' patched Intel-driver and install a patched FGLRX-driver.

If you a feeling a bit more adventurous, you can try and download the driver from AMD (perhaps even go for the latest beta) and see what happens.

In case you go for that instead:
```

unzip <driver-file>
chmod +x <driverfile>
sudo ./<driver-file> --buildpkg Ubuntu/quantal
sudo aticonfig --initial -f

```

---

### Post by ppierpaolo on 2013-04-20
Hi Marco, thank you for your answer.
I tried the first way (with andrikos' ppa) but when I get to the last command I get this output:

```

sudo aticonfig --initial -f
aticonfig: No supported adapters detected

```

I rebooted my system but now I don't have Unity anymore. I dont' have a /etc/X11/xorg.conf file anymore and the command "startx" doesn't work, it freezes on "loading extension glx".
What am I supposed to do now?

Edit: i removed andrikos' ppa and all the packages I installed with apt-get commands. But my ubuntu didn't let me to use unity and got stuck on a login screen even if I put the correct password. I deleted the .Xauthory file and rebooted, and now it seems that I cant use firefox al least.

So, the andriko's ppa way doesn't work for me. Or: was there something I had to do when I received the "aticonfig: No supported adapters detected" message?

What can I do now?

---

### Post by MarcoDePollo on 2013-04-20
> **ppierpaolo said:**
> Hi Marco, thank you for your answer.
I tried the first way (with andrikos' ppa) but when I get to the last command I get this output:

```

sudo aticonfig --initial -f
aticonfig: No supported adapters detected

```

I rebooted my system but now I don't have Unity anymore. I dont' have a /etc/X11/xorg.conf file anymore and the command "startx" doesn't work, it freezes on "loading extension glx".
What am I supposed to do now?

Edit: i removed andrikos' ppa and all the packages I installed with apt-get commands. But my ubuntu didn't let me to use unity and got stuck on a login screen even if I put the correct password. I deleted the .Xauthory file and rebooted, and now it seems that I cant use firefox al least.

So, the andriko's ppa way doesn't work for me. Or: was there something I had to do when I received the "aticonfig: No supported adapters detected" message?

What can I do now?

first:
```

sudo rm /etc/X11/xorg.conf
sudo apt-get remove fglrx*

```

then, please post the output of 
```

lspci

```

---

### Post by Niccola on 2013-04-22
I'm having frozen black screen when rebooting/shutting down even with fglrx 13.3 beta3

I'd like to know if somebody else have same behavior?

---

### Post by MarcoDePollo on 2013-04-23
> **Niccola said:**
> I'm having frozen black screen when rebooting/shutting down even with fglrx 13.3 beta3

I'd like to know if somebody else have same behavior?

Nothing so far, on Sandy Bridge/HD6770 or something like that.

---

### Post by MarcoDePollo on 2013-04-25
AMD has released 13.4 - [get it while it's hot]("http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip").

---

### Post by sarvigalava on 2013-04-25
Does it work with ubuntu 13.04 ?

---

### Post by MarcoDePollo on 2013-04-25
> **sarvigalava said:**
> Does it work with ubuntu 13.04 ?
Yes, yes it does. Build it with:
```

--buildpkg Ubuntu/raring

```

---

### Post by jwhirl06 on 2013-04-25
> **MarcoDePollo said:**
> Yes, yes it does. Build it with:
```

--buildpkg Ubuntu/raring

```

Are you running sandybridge and the 7xxx series or ivybridge and 6xxx series?

---

### Post by MarcoDePollo on 2013-04-25
> **jwhirl06 said:**
> Are you running sandybridge and the 7xxx series or ivybridge and 6xxx series?
Sandybridge+HD7xxx.

Edited: Apparently it's a HD7690.

---

### Post by razorxpress on 2013-04-25
I tried to install 13.4 and it failed just like past few releases. My card is 6470M. I haven't been successful to run catalyst driver in Ubuntu 13.04 till date for AMD graphics cards. One thing I noticed was /usr/lib/i386-linux-gnu/dri is added to /etc/X11/Xsession.d/10fglrx by the installation, so /usr/lib/x86_64-linux-gnu/dri might be unnecessary. I tried different things. I copied switchlibGL and switchlibglx to /usr/lib64 as noted in [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide). I also tried the andrikos-ppa (it hangs integrated, so don't try this). 

One thing to note though the installation is fine. When you boot, an error message pops up saying graphics card is not configured. If you use "sudo aticonfig --px-igpu" and login it works (for 13.4). You should have xorg.conf first. As soon as you try to switch to AMD (dgpu) it has same problem. I followed the cchtml.com guide and added different links but does not work.

---

### Post by rechter77 on 2013-04-26
Hi friends,
I finished install my fresh Ubuntu 13.04 and would like install fglrx (ATI driver).
But, I tried install the new AMD proprietary 13.4 and got a low graphics mode after reboot.
When I install both fglrx or fglrx-updates the system don't boot.
When I was using the precise version I instaled with success through repository ppa:andrikos/ppa in x86 version.
can someone please help me?

Thanks in advance.

Here is my lspci output:

christopher@inspiron:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
[COLOR=#ff0000]**00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)**[/COLOR]
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
[COLOR=#ff0000]**02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7550M/7570M/7650M]**[/COLOR]
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)

---

### Post by Niccola on 2013-04-26
> **MarcoDePollo said:**
> Yes, yes it does. Build it with:
```

--buildpkg Ubuntu/raring

```

MarcoDePollo,


Could you please tell us if it's fglrx working out of the box over Ubuntu 13.04?
I mean, does it need some patch or fix (like andrikos xorg-video-intel in 12.10?)

Or it just works following wiki.cchtml installation guide?

P.S.: For me, only Catayst 13.2 works without hanging at rebooting/shutting-down

---

### Post by jwhirl06 on 2013-04-26
> **MarcoDePollo said:**
> Sandybridge+HD7xxx.

Edited: Apparently it's a HD7690.

Whoops, I meant to ask Sandybridge with Radeon 6xxx or Ivybridge with Radeon 7xxx, I have the Ivybridge with the Radeon 7850m

---

### Post by duydangle on 2013-04-26
> **rechter77 said:**
> Hi friends,
I finished install my fresh Ubuntu 13.04 and would like install fglrx (ATI driver).
But, I tried install the new AMD proprietary 13.4 and got a low graphics mode after reboot.
When I install both fglrx or fglrx-updates the system don't boot.
When I was using the precise version I instaled with success through repository ppa:andrikos/ppa in x86 version.
can someone please help me?

Thanks in advance.

Here is my lspci output:

christopher@inspiron:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
[COLOR=#ff0000]**00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)**[/COLOR]
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
[COLOR=#ff0000]**02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7550M/7570M/7650M]**[/COLOR]
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)

I get the same problem with 7650M & Intel HD 4000 + 13.04 & CCC 13.4. But I can boot normally into power-saving mode. Low graphics mode when switching to dedicated graphics card.

---

### Post by MarcoDePollo on 2013-04-26
> **Niccola said:**
> MarcoDePollo,


Could you please tell us if it's fglrx working out of the box over Ubuntu 13.04?
I mean, does it need some patch or fix (like andrikos xorg-video-intel in 12.10?)

Or it just works following wiki.cchtml installation guide?

P.S.: For me, only Catayst 13.2 works without hanging at rebooting/shutting-down

It works out of the box, for me. But, somewhere in the kernel-build for Raring some setting is actually disabling my integrated Intel-graphics, so an lspci only lists my discrete graphics.
If I boot up an older Ubuntu - or any other distro, even with one based on kernel 3.8, the Intel graphics are back.

```

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
**01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6730M/6770M/7690M XT]**
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
09:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
10:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
11:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
12:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)



```

---

### Post by MarcoDePollo on 2013-04-26
> **jwhirl06 said:**
> Whoops, I meant to ask Sandybridge with Radeon 6xxx or Ivybridge with Radeon 7xxx, I have the Ivybridge with the Radeon 7850m

I had to look up what HP had to say, just to be sure:)

The CPU is an i7-2670QM, which confirms it's Sandy Bridge. The graphics is also confirmed to be "Radeon HD 7690m XT",
which I assume is a rebranded Series 6000-chip, because CCC tells me it an "HD6700 Series".

Marketing.

---

### Post by BastiFantasti on 2013-04-26
Hi,

I have the same issue on my Sony Vaio after upgrading to ubuntu 13.04. I'm trying to install the latest 13.4 driver version. 
integrated graphics card works (fine) - switching to external works but results in a low resolution startup of the Xserver.



My vaio has:

```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series]

```

there's a strange error in the xorg logout when starting with external graphic


```

[    32.155] ukiDynamicMajor: found major device number 250
[    32.155] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    32.155] ukiOpenDevice: node name is /dev/ati/card0
[    32.155] ukiOpenDevice: open result is 20, (OK)
[    32.155] ukiOpenByBusid: ukiOpenMinor returns 20
[    32.155] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[B][COLOR=#ff0000][    38.859] (EE) fglrx(0): Failed to allocate caches, disabling RENDER acceleration
[    38.868] (EE) fglrx(0): [intel] Failed to allocate video resources for front buffer 1920x1080 at depth 24[/COLOR][/B]
[    38.868] 
Fatal server error:
[    38.868] failed to create screen resources
[    38.868] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    38.868] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    38.868] (EE) 
[    38.868] (II) AIGLX: Suspending AIGLX clients for VT switch
[    38.868] (II) fglrx(0): Backup framebuffer data.
[    38.871] (II) fglrx(0): Backup complete.
[    38.889] Server terminated with error (1). Closing log file.

```

---

### Post by slim3250 on 2013-04-26
Hi,
I'm using HP Pavilion dv6-6112tx with HD 6770M / Intel HD, just started to use Ubuntu yesterday with the new release of 13.04.
After the installation, the fan is running in high mode and my laptop seems to be overheated. I suspected this is happening because of the Hybrid card issue. 
By default, it seems that it runs in high-performance graphic mode. 

So, I tried the method from [http://ubuntuforums.org/showthread.php?p=12501880#post1250188](http://ubuntuforums.org/showthread.php?p=12501880#post1250188) but it didn't work for 13.04 64bit using 13.4 drivers
However, it seems to work fine on 12.04.2 LTS  64bit with AMD 13.4 drivers.
Note: in 12.04.2 Before installing AMD drivers, there's always error reporting: "xorg crashed with sigabrt" after entering GUI. 

This is the step by step guide: 
1. Upgrade the HP DV6 BIOS to F.1B and after the bios update, change the bios setting (under 'system config' - 'switchable graphics mode' change to "fixed")
2. Fresh Install Ubuntu 12.04.2 
3. Update and install linux headers / source
```
sudo apt-get update
sudo apt-get upgrade
```
4. reboot
5. install linux headers / source 
```
sudo apt-get install linux-source linux-headers-generic
```
6. reboot
7. install prereq package for amd 13.4 drivers
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
sudo apt-get install lib32gcc1 

```7. download and install 13.4 drivers using manual installation [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Alternative_Manual_Installation](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Alternative_Manual_Installation)
```
wget [http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-catalyst-13.4-linux-x86.x86_64.zip)
unzip amd-catalyst-13.4-linux-x86.x86_64.zip
chmod +x amd-catalyst-13.4-linux-x86.x86_64.run
./amd-driver-installer-catalyst-13.4-x86/x86_64.run
```
Follow GUI Installation and choose the basic one "ATI/AMD proprietary FGLRX graphics driver" and automatic
8. reboot
9. test your installation by running
```
fglrxinfo
fgl_glxgears
```
10. Activate power-saving mode 
```
amdconfig --pxl            # List current activated GPU
sudo amdconfig --px-igpu   # Activate integrated GPU (Power-Saving mode), must re-start X to take effect

```
11. reboot
12. The fan should be quiet and the hybrid mode should be working now

Reference:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Intel.2FATI_Hybrids")

---

### Post by jmite on 2013-04-27
When I install 13.4 from debs generated from the AMD website .run file, during the "aticonfig --initial -f" I get the following error:

```

PowerXpress info: Diagnostic output from /usr/lib64/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link

```

Then when I boot I get X starting in low graphics mode.

Does anybody know what might be causing this and how I can fix this?
I'm on a SandyBridge/AMD66xx hybrid on a Sony Vaio running Raring.

---

### Post by MurgaNikolay on 2013-04-27
Hi, 

My notebook: HP Pavilion dv6-6b63sr

```

nikolay@nikolay-pc:~$ lspci
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff)

```

After install catalyst 13.4  (using packages or amd installer) i got error in xorg.0.log log and X is not started.

If I switch to integrated video:
```

sudo amdconfig --px-igpu

```

System boot normaly.
The temperature of the notebook dropped and fan is quiet.

xorg.0.log:

```

[    20.174] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    20.174] X Protocol Version 11, Revision 0
[    20.174] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    20.174] Current Operating System: Linux nikolay-pc 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64
[    20.174] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=ea020471-21c6-4d5b-a00d-cb660e25416a ro quiet splash
[    20.174] Build Date: 17 April 2013  10:43:13PM
[    20.174] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    20.174] Current version of pixman: 0.28.2
[    20.174]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.174] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.174] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 27 09:11:10 2013
[    20.174] (==) Using config file: "/etc/X11/xorg.conf"
[    20.174] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.190] (==) ServerLayout "X.org Configured"
[    20.190] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    20.190] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    20.190] (**) |   |-->Device "aticonfig-Device[0]-0"
[    20.190] (**) |-->Input Device "Keyboard0"
[    20.190] (==) Automatically adding devices
[    20.190] (==) Automatically enabling devices
[    20.190] (==) Automatically adding GPU devices
[    20.190] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.190]     Entry deleted from font path.
[    20.190] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.190]     Entry deleted from font path.
[    20.191] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.191] (**) ModulePath set to "/usr/lib/xorg/modules"
[    20.191] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.191] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.191] (WW) Disabling Keyboard0
[    20.191] (II) Loader magic: 0x7f6f15b3ed20
[    20.191] (II) Module ABI versions:
[    20.191]     X.Org ANSI C Emulation: 0.4
[    20.191]     X.Org Video Driver: 13.1
[    20.191]     X.Org XInput driver : 18.0
[    20.191]     X.Org Server Extension : 7.0
[    20.191] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.192] (--) PCI:*(0:0:2:0) 8086:0116:103c:3388 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00006000/64
[    20.192] (--) PCI: (0:1:0:0) 1002:6740:103c:3388 rev 0, Mem @ 0xa0000000/268435456, 0xc6500000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[    20.192] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.192] Initializing built-in extension Generic Event Extension
[    20.192] Initializing built-in extension SHAPE
[    20.192] Initializing built-in extension MIT-SHM
[    20.192] Initializing built-in extension XInputExtension
[    20.192] Initializing built-in extension XTEST
[    20.192] Initializing built-in extension BIG-REQUESTS
[    20.192] Initializing built-in extension SYNC
[    20.192] Initializing built-in extension XKEYBOARD
[    20.192] Initializing built-in extension XC-MISC
[    20.192] Initializing built-in extension SECURITY
[    20.192] Initializing built-in extension XINERAMA
[    20.192] Initializing built-in extension XFIXES
[    20.192] Initializing built-in extension RENDER
[    20.192] Initializing built-in extension RANDR
[    20.192] Initializing built-in extension COMPOSITE
[    20.192] Initializing built-in extension DAMAGE
[    20.192] Initializing built-in extension MIT-SCREEN-SAVER
[    20.192] Initializing built-in extension DOUBLE-BUFFER
[    20.192] Initializing built-in extension RECORD
[    20.192] Initializing built-in extension DPMS
[    20.192] Initializing built-in extension X-Resource
[    20.192] Initializing built-in extension XVideo
[    20.192] Initializing built-in extension XVideo-MotionCompensation
[    20.192] Initializing built-in extension SELinux
[    20.192] Initializing built-in extension XFree86-VidModeExtension
[    20.192] Initializing built-in extension XFree86-DGA
[    20.192] Initializing built-in extension XFree86-DRI
[    20.192] Initializing built-in extension DRI2
[    20.192] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    20.192] (II) LoadModule: "glx"
[    20.351] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.542] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    20.542]     compiled for 6.9.0, module version = 1.0.0
[    20.542] Loading extension GLX
[    20.542] (II) LoadModule: "fglrx"
[    20.542] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    21.616] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    21.616]     compiled for 1.4.99.906, module version = 12.10.5
[    21.616]     Module class: X.Org Video Driver
[    21.616] (II) Loading sub module "fglrxdrm"
[    21.616] (II) LoadModule: "fglrxdrm"
[    21.616] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    21.743] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    21.743]     compiled for 1.4.99.906, module version = 12.10.5
[    21.743] (II) AMD Proprietary Linux Driver Version Identifier:12.10.05
[    21.743] (II) AMD Proprietary Linux Driver Release Identifier: 12.104                               
[    21.743] (II) AMD Proprietary Linux Driver Build Date: Mar 28 2013 21:07:25
[    21.743] (++) using VT number 7

[    21.743] (WW) Falling back to old probe method for fglrx
[    21.862] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    21.875] ukiDynamicMajor: found major device number 250
[    21.875] ukiDynamicMajor: found major device number 250
[    21.875] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    21.875] ukiOpenDevice: node name is /dev/ati/card0
[    21.875] ukiOpenDevice: open result is 10, (OK)
[    22.769] ukiOpenByBusid: ukiOpenMinor returns 10
[    22.770] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    22.868] (--) Chipset Supported AMD Graphics Processor (0x6740) found
[    22.887] (II) fglrx: intel VGA device detected, load intel driver.
[    22.887] (II) LoadModule: "intel"
[    22.887] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.900] (II) Module intel: vendor="X.Org Foundation"
[    22.900]     compiled for 1.13.3, module version = 2.21.6
[    22.900]     Module class: X.Org Video Driver
[    22.900]     ABI class: X.Org Video Driver, version 13.1
[    22.900] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    22.900] (II) AMD Video driver is signed
[    22.901] (II) fglrx(0): pEnt->device->identifier=0x7f6f175d2140
[    22.901] (II) intel(1): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    22.901] (II) intel(1): pEnt->device->identifier=(nil)
[    22.901] (EE) Screen 1 deleted because of no matching config section.
[    22.901] (II) UnloadModule: "intel"
[    22.901] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    22.901] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[    23.020] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    23.020] (==) fglrx(0): RGB weight 888
[    23.020] (==) fglrx(0): Default visual is TrueColor
[    23.020] (**) fglrx(0): Option "Tiling" "off"
[    23.020] (**) fglrx(0): Option "LinearFramebuffer" "on"
[    23.020] (**) fglrx(0): ChipID override: 0x0116
[    23.020] (**) fglrx(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    23.020] (--) fglrx(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    23.020] (**) fglrx(0): Framebuffer linear
[    23.020] (**) fglrx(0): Pixmaps linear
[    23.020] (**) fglrx(0): "Tear free" disabled
[    23.020] (**) fglrx(0): Forcing per-crtc-pixmaps? no
[    23.021] (II) fglrx(0): Output LVDS1 using monitor section aticonfig-Monitor[0]-0
[    23.021] (--) fglrx(0): found backlight control interface acpi_video1 (type 'firmware')
[    23.036] (II) fglrx(0): Output VGA1 has no monitor section
[    23.340] (II) fglrx(0): Output HDMI1 has no monitor section
[    23.388] (II) fglrx(0): Output DP1 has no monitor section
[    23.388] (II) fglrx(0): EDID for output LVDS1
[    23.388] (II) fglrx(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    23.388] (II) fglrx(0): Year: 2009  Week: 1
[    23.388] (II) fglrx(0): EDID Version: 1.3
[    23.388] (II) fglrx(0): Digital Display Input
[    23.388] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    23.388] (II) fglrx(0): Gamma: 2.20
[    23.388] (II) fglrx(0): No DPMS capabilities specified
[    23.388] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.388] (II) fglrx(0): First detailed timing is preferred mode
[    23.388] (II) fglrx(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    23.388] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    23.388] (II) fglrx(0): Manufacturer's mask: 0
[    23.388] (II) fglrx(0): Supported detailed timing:
[    23.388] (II) fglrx(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    23.388] (II) fglrx(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
[    23.388] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    23.388] (II) fglrx(0): Unknown vendor-specific block f
[    23.388] (II) fglrx(0):  AUO
[    23.388] (II) fglrx(0):  B156XW02 V2
[    23.388] (II) fglrx(0): EDID (in hex):
[    23.388] (II) fglrx(0):     00ffffffffffff0006afec2200000000
[    23.388] (II) fglrx(0):     01130103802213780ac8959e57549226
[    23.388] (II) fglrx(0):     0f505400000001010101010101010101
[    23.388] (II) fglrx(0):     010101010101121b5642500026302018
[    23.388] (II) fglrx(0):     340058c1100000180000000f00000000
[    23.388] (II) fglrx(0):     00000000000000000020000000fe0041
[    23.388] (II) fglrx(0):     554f0a202020202020202020000000fe
[    23.388] (II) fglrx(0):     004231353658573032205632200a00c0
[    23.388] (II) fglrx(0): Not using default mode "320x240" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "512x384" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "640x480" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "640x512" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "800x600" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "896x672" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "928x696" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "960x720" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "576x432" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "700x525" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "720x450" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "800x512" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "960x540" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "960x600" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Not using default mode "1024x768" (doublescan mode not supported)
[    23.388] (II) fglrx(0): Printing probed modes for output LVDS1
[    23.388] (II) fglrx(0): Modeline "1366x768"x60.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz eP)
[    23.388] (II) fglrx(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    23.388] (II) fglrx(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    23.388] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    23.388] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    23.388] (II) fglrx(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    23.388] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    23.404] (II) fglrx(0): EDID for output VGA1
[    23.708] (II) fglrx(0): EDID for output HDMI1
[    23.708] (II) fglrx(0): Manufacturer: DEL  Model: a07a  Serial#: 875837004
[    23.708] (II) fglrx(0): Year: 2012  Week: 35
[    23.708] (II) fglrx(0): EDID Version: 1.3
[    23.708] (II) fglrx(0): Digital Display Input
[    23.708] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    23.708] (II) fglrx(0): Gamma: 2.20
[    23.708] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    23.708] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.708] (II) fglrx(0): First detailed timing is preferred mode
[    23.708] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    23.708] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    23.708] (II) fglrx(0): Supported established timings:
[    23.708] (II) fglrx(0): 720x400@70Hz
[    23.708] (II) fglrx(0): 640x480@60Hz
[    23.708] (II) fglrx(0): 800x600@60Hz
[    23.708] (II) fglrx(0): 1024x768@60Hz
[    23.708] (II) fglrx(0): Manufacturer's mask: 0
[    23.708] (II) fglrx(0): Supported standard timings:
[    23.708] (II) fglrx(0): #0: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    23.708] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    23.708] (II) fglrx(0): #2: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    23.708] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    23.708] (II) fglrx(0): #4: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    23.708] (II) fglrx(0): Supported detailed timing:
[    23.708] (II) fglrx(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    23.708] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    23.708] (II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    23.708] (II) fglrx(0): Serial No: Y1H5T28U446L
[    23.708] (II) fglrx(0): Monitor name: DELL U2412M
[    23.708] (II) fglrx(0): Ranges: V min: 50 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    23.708] (II) fglrx(0): EDID (in hex):
[    23.708] (II) fglrx(0):     00ffffffffffff0010ac7aa04c363434
[    23.708] (II) fglrx(0):     2316010380342078eaee95a3544c9926
[    23.708] (II) fglrx(0):     0f5054a1080081408180a940b300d1c0
[    23.708] (II) fglrx(0):     010101010101283c80a070b023403020
[    23.708] (II) fglrx(0):     360006442100001a000000ff00593148
[    23.708] (II) fglrx(0):     35543238553434364c0a000000fc0044
[    23.708] (II) fglrx(0):     454c4c2055323431324d0a20000000fd
[    23.708] (II) fglrx(0):     00323d1e5311000a2020202020200054
[    23.708] (II) fglrx(0): Printing probed modes for output HDMI1
[    23.708] (II) fglrx(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz eP)
[    23.708] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    23.708] (II) fglrx(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    23.708] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    23.708] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    23.708] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    23.708] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    23.708] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    23.708] (II) fglrx(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    23.756] (II) fglrx(0): EDID for output DP1
[    23.756] (II) fglrx(0): Output LVDS1 connected
[    23.756] (II) fglrx(0): Output VGA1 disconnected
[    23.756] (II) fglrx(0): Output HDMI1 connected
[    23.756] (II) fglrx(0): Output DP1 disconnected
[    23.756] (II) fglrx(0): Using fuzzy aspect match for initial modes
[    23.756] (II) fglrx(0): Output LVDS1 using initial mode 1024x768
[    23.756] (II) fglrx(0): Output HDMI1 using initial mode 1024x768
[    23.756] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.756] (==) fglrx(0): DPI set to (96, 96)
[    23.756] (II) Loading sub module "dri2"
[    23.756] (II) LoadModule: "dri2"
[    23.756] (II) Module "dri2" already built-in
[    23.756] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    23.756] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.756] (==) fglrx(0): Default visual is TrueColor
[    23.756] (**) fglrx(0): Option "DPMS" "true"
[    23.756] (==) fglrx(0): RGB weight 888
[    23.756] (II) fglrx(0): Using 8 bits per RGB 
[    23.756] (==) fglrx(0): Buffer Tiling is ON
[    23.756] (II) Loading sub module "fglrxdrm"
[    23.756] (II) LoadModule: "fglrxdrm"
[    23.756] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    23.756] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.756]     compiled for 1.4.99.906, module version = 12.10.5
[    23.758] ukiDynamicMajor: found major device number 250
[    23.758] ukiDynamicMajor: found major device number 250
[    23.758] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    23.758] ukiOpenDevice: node name is /dev/ati/card0
[    23.758] ukiOpenDevice: open result is 15, (OK)
[    23.758] ukiOpenByBusid: ukiOpenMinor returns 15
[    23.758] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    23.758] (**) fglrx(0): NoAccel = NO
[    23.758] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    23.758] (--) fglrx(0): Chipset: "AMD Radeon HD 6700M Series" (Chipset = 0x6740)
[    23.758] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3388)
[    23.758] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    23.758] (--) fglrx(0): Linear framebuffer (phys) at 0xa0000000
[    23.758] (--) fglrx(0): MMIO registers at 0xc6500000
[    23.758] (--) fglrx(0): I/O port at 0x00005000
[    23.758] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    23.776] (II) fglrx(0): Battery is used
[    23.776] (EE) fglrx(0): Failed to get ConsoleMode
[    23.776] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    23.776] (--) fglrx(0): Video RAM: 2097152 kByte, Type: GDDR5
[    23.776] (II) fglrx(0): PCIE card detected
[    23.776] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    23.776] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    23.783] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x80000000)
[    23.783] (II) fglrx(0): RandR 1.2 support is enabled!
[    23.783] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    23.783] (==) fglrx(0): Center Mode is disabled 
[    23.783] (II) Loading sub module "fb"
[    23.783] (II) LoadModule: "fb"
[    23.783] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.811] (II) Module fb: vendor="X.Org Foundation"
[    23.811]     compiled for 1.13.3, module version = 1.0.0
[    23.811]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.811] (II) Loading sub module "ddc"
[    23.811] (II) LoadModule: "ddc"
[    23.811] (II) Module "ddc" already built-in
[    23.986] (II) fglrx(0): Eyefinity capable adapter detected.
[    23.986] (II) fglrx(0): Adapter AMD Radeon HD 6700M Series has 6 configurable heads and 0 displays connected.
[    23.987] (==) fglrx(0):  PseudoColor visuals disabled
[    23.987] (II) Loading sub module "ramdac"
[    23.987] (II) LoadModule: "ramdac"
[    23.987] (II) Module "ramdac" already built-in
[    23.987] (==) fglrx(0): NoDRI = NO
[    23.987] (==) fglrx(0): Capabilities: 0x00000000
[    23.987] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    23.987] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    23.987] (==) fglrx(0): UseFastTLS=0
[    23.987] (II) fglrx(0): TearFreeDesktop is not supported on PowerXpress systems currently.
[    23.987] (--) Depth 24 pixmap format is 32 bpp
[    23.987] (II) LoadModule: "glesx"
[    23.987] (II) Loading /usr/lib/xorg/modules/glesx.so
[    24.238] (II) Module glesx: vendor="X.Org Foundation"
[    24.238]     compiled for 1.4.99.906, module version = 1.0.0
[    24.238] Loading extension GLESX
[    24.252] (II) fglrx(0): SNA initialized with SandyBridge backend
[    24.252] (==) fglrx(0): Backing store disabled
[    24.252] (==) fglrx(0): Silken mouse enabled
[    24.252] (II) fglrx(0): HW Cursor enabled
[    24.252] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.364] (**) fglrx(0): DPMS enabled
[    24.364] (II) fglrx(0): [DRI2] Setup complete
[    24.364] (II) fglrx(0): [DRI2]   DRI driver: i965
[    24.364] (II) fglrx(0): direct rendering: DRI2 Enabled
[    24.364] (WW) fglrx(0): Option "VendorName" is not used
[    24.364] (WW) fglrx(0): Option "ModelName" is not used
[    24.364] (WW) fglrx(0): Option "Shadow" is not used
[    24.364] (WW) fglrx(0): Option "Tiling" is not used
[    24.364] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    24.364] (==) fglrx(0): hotplug detection: "enabled"
[    24.364] Loading extension ATIFGLRXDRI
[    24.364] (II) fglrx(0): doing swlDriScreenInit
[    24.364] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    24.364] ukiDynamicMajor: found major device number 250
[    24.365] ukiDynamicMajor: found major device number 250
[    24.365] ukiDynamicMajor: found major device number 250
[    24.365] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    24.365] ukiOpenDevice: node name is /dev/ati/card0
[    24.365] ukiOpenDevice: open result is 17, (OK)
[    24.365] ukiOpenByBusid: ukiOpenMinor returns 17
[    24.365] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    24.365] (II) fglrx(0): [uki] DRM interface version 1.0
[    24.365] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    24.365] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    24.365] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f6f1570d000
[    24.365] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    24.365] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    24.365] (II) fglrx(0): swlDriScreenInit done
[    24.365] (II) fglrx(0): Kernel Module Version Information:
[    24.365] (II) fglrx(0):     Name: fglrx
[    24.365] (II) fglrx(0):     Version: 12.10.5
[    24.365] (II) fglrx(0):     Date: Mar 28 2013
[    24.365] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    24.365] (II) fglrx(0): Kernel Module version matches driver.
[    24.365] (II) fglrx(0): Kernel Module Build Time Information:
[    24.365] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.8.0-19-generic
[    24.365] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    24.365] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    24.365] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    24.365] (II) fglrx(0): [uki] register handle = 0x00004000
[    24.444] (II) fglrx(0): DRI initialization successfull
[    24.444] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01040000
[    24.444] (II) fglrx(0): Intel display surface mc addr for AMD: 9fcf8000
[    24.445] (==) fglrx(0): Backing store disabled
[    24.445] Loading extension FGLRXEXTENSION
[    24.445] (**) fglrx(0): DPMS enabled
[    24.445] (II) fglrx(0): Initialized in-driver Xinerama extension
[    24.445] (**) fglrx(0): Textured Video is enabled.
[    24.445] (II) fglrx(0): GLESX enableFlags = 848
[    24.445] (II) fglrx(0): GLESX is enabled
[    24.445] (II) LoadModule: "amdxmm"
[    24.445] (II) Loading /usr/lib/xorg/modules/amdxmm.so
[    24.535] (II) Module amdxmm: vendor="X.Org Foundation"
[    24.536]     compiled for 1.4.99.906, module version = 2.0.0
[    24.536] Loading extension AMDXVOPL
[    24.536] Loading extension AMDXVBA
[    24.536] XvScreenInit: screen devPrivates ptr non-NULL before init
[    24.562] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    24.563] (II) fglrx(0): Enable composite support successfully
[    24.563] (WW) fglrx(0): Option "VendorName" is not used
[    24.563] (WW) fglrx(0): Option "ModelName" is not used
[    24.563] (WW) fglrx(0): Option "Shadow" is not used
[    24.563] (WW) fglrx(0): Option "Tiling" is not used
[    24.563] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    24.563] (II) fglrx(0): X context handle = 0x1
[    24.563] (II) fglrx(0): [DRI] installation complete
[    24.564] (WW) fglrx(0): Framebuffer compression is disabled by the driver: Video Ram = 262144 kByte
[    24.564] (--) RandR disabled
[    24.568] (II) SELinux: Disabled on system
[    24.569] ukiDynamicMajor: found major device number 250
[    24.569] ukiDynamicMajor: found major device number 250
[    24.569] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    24.569] ukiOpenDevice: node name is /dev/ati/card0
[    24.569] ukiOpenDevice: open result is 18, (OK)
[    24.569] ukiOpenByBusid: ukiOpenMinor returns 18
[    24.569] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    25.573] ukiDynamicMajor: found major device number 250
[    25.573] ukiDynamicMajor: found major device number 250
[    25.573] ukiDynamicMajor: found major device number 250
[    25.573] ukiOpenDevice: node name is /dev/ati/card0
[    25.573] ukiOpenDevice: open result is 19, (OK)
[    25.573] ukiGetBusid returned 'PCI:1:0:0'
[    25.573] ukiOpenDevice: node name is /dev/ati/card1
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card2
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card3
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card4
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card5
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card6
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card7
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card8
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card9
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card10
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card11
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card12
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card13
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card14
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiOpenDevice: node name is /dev/ati/card15
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: open result is -1, (No such device)
[    25.573] ukiOpenDevice: Open failed
[    25.573] ukiDynamicMajor: found major device number 250
[    25.573] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    25.573] ukiOpenDevice: node name is /dev/ati/card0
[    25.573] ukiOpenDevice: open result is 19, (OK)
[    25.573] ukiOpenByBusid: ukiOpenMinor returns 19
[    25.573] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    27.719] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    27.720] ukiDynamicMajor: found major device number 250
[    27.720] ukiDynamicMajor: found major device number 250
[    27.720] ukiDynamicMajor: found major device number 250
[    27.720] ukiOpenDevice: node name is /dev/ati/card0
[    27.720] ukiOpenDevice: open result is 20, (OK)
[    27.720] ukiGetBusid returned 'PCI:1:0:0'
[    27.720] ukiOpenDevice: node name is /dev/ati/card1
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card2
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card3
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card4
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card5
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card6
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card7
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card8
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card9
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card10
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card11
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card12
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card13
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card14
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiOpenDevice: node name is /dev/ati/card15
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: open result is -1, (No such device)
[    27.720] ukiOpenDevice: Open failed
[    27.720] ukiDynamicMajor: found major device number 250
[    27.720] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    27.720] ukiOpenDevice: node name is /dev/ati/card0
[    27.720] ukiOpenDevice: open result is 20, (OK)
[    27.720] ukiOpenByBusid: ukiOpenMinor returns 20
[    27.720] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    28.079] (EE) fglrx(0): Failed to allocate caches, disabling RENDER acceleration
[    28.082] (EE) fglrx(0): [intel] Failed to allocate video resources for front buffer 1024x768 at depth 24
[    28.082] 
Fatal server error:
[    28.082] failed to create screen resources
[    28.082] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    28.082] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    28.082] (EE) 
[    28.082] (II) AIGLX: Suspending AIGLX clients for VT switch
[    28.082] (II) fglrx(0): Backup framebuffer data.
[    28.086] (II) fglrx(0): Backup complete.
[    28.118] Server terminated with error (1). Closing log file.

```

 P.S. If i  Install driver with using deb packages I get error as in the previous post:

```

update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link

```

---

### Post by BastiFantasti on 2013-04-27
Hi there,

I've managed to install the fglrx driver and use the external graphics adapter. 
The problem is the new intel graphics driver.

Here's what I did:

0. Ensure that you have the deb files for the current AMD driver (created with --buildpkg as described in previous posts)

1. open a shell and download a previous version of the intel driver and it's dependencies:

```

mkdir temp
cd temp
wget http://launchpadlibrarian.net/119461148/libudev0_175-0ubuntu13_i386.deb
wget http://launchpadlibrarian.net/111621162/xserver-xorg-video-intel_2.20.2-1ubuntu1_i386.deb

```

2. remove the eventually installed fglrx and the installed intel drivers. When removing the intel driver let it remove both packages

```

cd ..
sudo apt-get remove fglrx*
sudo apt-get remove xserver-xorg-video-intel

```

3. install the older driver with its dependencies

```

cd temp
sudo dpkg -i libudev*
sudo dpkg -i xserver-xorg-video-intel_2.20.2-1ubuntu1_i386.deb

```

4. now install the fglrx packages (go to the folder containing the fglrx deb files). Warnings about defect link groups can be ignored (at least I did ;-) )
```

cd <your folder with fglrx drivers>
sudo dpkg -i fglrx*.deb

```

5. backup and remove the existing xorg.conf

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

6. create a new config file and switch to the external graphics adapter

```

sudo aticonfig --px-dgpu
sudo aticonfig --initial -f

```

7. reboot :-)

---

### Post by laci37 on 2013-04-27
I have tried this on my new HP Pavillion G6-2303sh-d4y36ea that has a HD7670. When I try to run aticonfig It says "No supported adapters detected". Also I did not update the BIOS, because I don't have Windows on the computer. I can't get the graphics working. I also had an issue with the wifi, so I'm using 12.04 x64 with a 3.6.6 kernel. The graphics card shows up in lspci. Any ideas?

EDIT: Also my touchpad stopped working after rebooting.

---

### Post by Aldoo on 2013-04-27
> **BastiFantasti said:**
> Hi there,

I've managed to install the fglrx driver and use the external graphics adapter. 
The problem is the new intel graphics driver.

Here's what I did:


That worked for me.
My card was not recognized at first (like previous poster), but after reinstalling the driver from AMD site (not using .deb packages) and powering the PC off and on, that finally worked.
Only remaining problem, maybe unrelated: I cannot control the screen backlight anymore (be it using either the discrete or integrated GPU).

Note to others: Basti's steps are for 32bits setups. I had to look for 64bits packages on another source. (Take the packages from Quantal updates repository, for instance).

---

### Post by jwhirl06 on 2013-04-27
> **Aldoo said:**
> That worked for me.
My card was not recognized at first (like previous poster), but after reinstalling the driver from AMD site (not using .deb packages) and powering the PC off and on, that finally worked.
Only remaining problem, maybe unrelated: I cannot control the screen backlight anymore (be it using either the discrete or integrated GPU).

Note to others: Basti's steps are for 32bits setups. I had to look for 64bits packages on another source. (Take the packages from Quantal updates repository, for instance).


What setups do you guys have? IvyBridge and 7xxx series?

---

### Post by MurgaNikolay on 2013-04-27
> **BastiFantasti said:**
> Hi there,

I've managed to install the fglrx driver and use the external graphics adapter. 
The problem is the new intel graphics driver.


That worked for me too.
I install from amd installer.

I have similar problem with Aldoo  - I cannot control the screen backlight and I broke Skype :smile:
After the launch Skype I get an error:

```

Segmentation fault

```

I fix this using command:
```

sudo apt-get install libgl1-mesa-glx --reinstall

```

---

### Post by Aldoo on 2013-04-27
> **jwhirl06 said:**
> What setups do you guys have? IvyBridge and 7xxx series?

Yes exactly.
It's a Dell Inspiron 7520.

Ah, concerning the backlight, it was an unrelated issue (related to something else that changed in Raring, I suppose).
It can be fixed by disabling ACPI interface for backlight control, in which case, other software will fall back to direct hardware control. To do this, just add "acpi_backlight=vendor" to your kernel options (can be added in /etc/defaults/grub in variable GRUB_CMDLINE_LINUX_DEFAULT, then execute "update-grub".).

---

### Post by Antarell on 2013-04-27
> **BastiFantasti said:**
> Hi there,

I've managed to install the fglrx driver and use the external graphics adapter. 
The problem is the new intel graphics driver.

Here's what I did:

0. Ensure that you have the deb files for the current AMD driver (created with --buildpkg as described in previous posts)

1. open a shell and download a previous version of the intel driver and it's dependencies:

```

mkdir temp
cd temp
wget http://launchpadlibrarian.net/119461148/libudev0_175-0ubuntu13_i386.deb
wget http://launchpadlibrarian.net/111621162/xserver-xorg-video-intel_2.20.2-1ubuntu1_i386.deb

```

2. remove the eventually installed fglrx and the installed intel drivers. When removing the intel driver let it remove both packages

```

cd ..
sudo apt-get remove fglrx*
sudo apt-get remove xserver-xorg-video-intel

```

3. install the older driver with its dependencies

```

cd temp
sudo dpkg -i libudev*
sudo dpkg -i xserver-xorg-video-intel_2.20.2-1ubuntu1_i386.deb

```

4. now install the fglrx packages (go to the folder containing the fglrx deb files). Warnings about defect link groups can be ignored (at least I did ;-) )
```

cd <your folder with fglrx drivers>
sudo dpkg -i fglrx*.deb

```

5. backup and remove the existing xorg.conf

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

6. create a new config file and switch to the external graphics adapter

```

sudo aticonfig --px-dgpu
sudo aticonfig --initial -f

```

7. reboot :-)



Have all the Internet Points I can give, worked a treat thanks :-)

PS: This is on my DV6-6023TX with 64bit Kubuntu upgraded from 12.04 -> 12.10 -> 13.04. This made finding the old packages easier (in the apt cache).

---

### Post by BastiFantasti on 2013-04-28
Hi,

There needs to be one more step done. The package needs to be blocked in the current version. 
This can be done using synpatic by selecting the package xserver-xorg-video-intel and clicking on:

```

Package > lock version

```

otherwise the package will be reverted to the newest version after the next update.

Here are some more ways on how to do it withoud synaptic: [http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

---

### Post by duydangle on 2013-04-28
I would like to know are there a way to make the 13.4 fglrx work with 13.04 intel driver? My priority is to work with integrated graphic card on ubuntu. Switch to dedicated graphics card would be nice, but roll back to old driver is not a choice, at least for me.

By the way, outside the topic: How to make ubuntu work faster and cooler? I think the fan works harder than on Windows 7, and the cpu is warmer than on Windows.

---

### Post by jmite on 2013-04-29
> **Aldoo said:**
> That worked for me.
My card was not recognized at first (like previous poster), but after reinstalling the driver from AMD site (not using .deb packages) and powering the PC off and on, that finally worked.
Only remaining problem, maybe unrelated: I cannot control the screen backlight anymore (be it using either the discrete or integrated GPU).

Note to others: Basti's steps are for 32bits setups. I had to look for 64bits packages on another source. (Take the packages from Quantal updates repository, for instance).

Quantal updates has xserver-xorg-video-intel (2:2.20.9-0ubuntu2.1). Will this version work, since it is different from the one originally listed?

---

### Post by jmite on 2013-04-29
Scratch my above comment, works just fine with BastiFantasti's instructions and the versions from Quantal Updates.

For reference, this is a Sony Vaio with AMD66xx discrete gpu and Sandy Bridge integrated GPU. 

I get 242.279 FPS in glxgears!

---

### Post by valek2282 on 2013-04-29
build xserver-xorg-video-intel_2.21.6-0ubuntu4_amd64 who normally works with the latest fglrx driver (defaul enabled uxa acceleration, and not sna)[https://docs.google.com/file/d/0B0tTaH4qTIIXdDF3NThFWUtrYlU/edit?usp=sharing](https://docs.google.com/file/d/0B0tTaH4qTIIXdDF3NThFWUtrYlU/edit?usp=sharing)

---

### Post by willis on 2013-04-29
> **valek2282 said:**
> build xserver-xorg-video-intel_2.21.6-0ubuntu4_amd64 who normally works with the latest fglrx driver (defaul enabled uxa acceleration, and not sna)[https://docs.google.com/file/d/0B0tTaH4qTIIXdDF3NThFWUtrYlU/edit?usp=sharing](https://docs.google.com/file/d/0B0tTaH4qTIIXdDF3NThFWUtrYlU/edit?usp=sharing)

This version works with integrated graphics, but with UXA I get screen tearing in the gnome-shell expose, and with both UXA and SNA external displays won't work.

---

### Post by jwhirl06 on 2013-04-29
The steps did not work for me, and hosed my graphics, going to have to reinstall

---

### Post by ppierpaolo on 2013-04-29
> **jwhirl06 said:**
> The steps did not work for me, and hosed my graphics, going to have to reinstall

Could you please specify what graphic card you're using?

---

### Post by jwhirl06 on 2013-04-29
> **ppierpaolo said:**
> Could you please specify what graphic card you're using?

System Specs:

HP Envy 17T-3200 CTO
Intel i7 
AMD Radeon HD 7850M/Intel HD Ivybridge Graphics
16GB DDR-1600

---

### Post by Drew5744 on 2013-04-29
Yes, xserver-xorg-video-intel (2:2.20.9-0ubuntu2.1) works.  I installed it last night & all has been good (except for flickering when I plugged in my external monitor, but that's probably a different issue).

---

### Post by willis on 2013-04-30
> **Drew5744 said:**
> Yes, xserver-xorg-video-intel (2:2.20.9-0ubuntu2.1) works.  I installed it last night & all has been good (except for flickering when I plugged in my external monitor, but that's probably a different issue).

Drew, can you confirm that both cards work?  And are you able to use your external monitor with the intel card?

Are you using the 13.4 catalyst driver from the website?

---

### Post by torghoundy on 2013-04-30
HiThe steps did not work for me too.I am using 13.04 on my HP probook 4530s Radeon hd 6490m and intel HD 3000

---

### Post by Aldoo on 2013-04-30
> **willis said:**
> Drew, can you confirm that both cards work?  And are you able to use your external monitor with the intel card?

Are you using the 13.4 catalyst driver from the website?

In my case (similar to Drew's) I am able to use both cards (not at the same time). No OpenGL acceleration with Intel (but I haven't looked a lot into how to enable it). I haven't tested whether external screen worked with Intel.
With the discrete GPU (using Catalyst 13.4), external screen works, but it seems I cannot switch back to the laptop screen after.

---

### Post by willis on 2013-04-30
I found that this askubuntu thread worked perfectly: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355)

I can use both cards and use an external monitor on both as well.

---

### Post by terebet on 2013-05-01
> **willis said:**
> I found that this askubuntu thread worked perfectly: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355)

I can use both cards and use an external monitor on both as well.


That solution worked almost perfectly here (ivy bridge + 7570m). The only issue happens when I switch from integrated to discrete card, i get low resolution problem. But, if I reboot my system, the problem goes away. This problem doesn't happen when I switch from discrete to integrated. 

PS: I'm using ubuntu 13.04 64 bits and catalyst 13.4.

---

### Post by CU2 on 2013-05-02
> **terebet said:**
> That solution worked almost perfectly here (ivy bridge + 7570m). The only issue happens when I switch from integrated to discrete card, i get low resolution problem. But, if I reboot my system, the problem goes away. This problem doesn't happen when I switch from discrete to integrated. 

PS: I'm using ubuntu 13.04 64 bits and catalyst 13.4.

This solution also works for me. GPU is in Power-Saving mode now. I am using Ubuntu 13.04 64-bit and Catalyst 13.4 on Dell Inspiron 7520 (15R SE with FullHD), 7700M + Intel 4000.:KS:KS

---

### Post by Falc7 on 2013-05-03
Yay that seems to have worked :D

Anyone managed to get the screen brightness control working?

Skype is broken for me too, the following didn't help :(
sudo apt-get install libgl1-mesa-glx --reinstall

---

### Post by Aldoo on 2013-05-03
> **Falc7 said:**
> Anyone managed to get the screen brightness control working?
Yes, see my post above.

> **Falc7 said:**
> Skype is broken for me too, the following didn't help :(
sudo apt-get install libgl1-mesa-glx --reinstall
Ah, same problem for me. It is looking for a 32bits libGL which, for some reason, was not installed by the catalyst installer.

---

### Post by m4tik on 2013-05-03
Hi guys,

I try to install the AMD drivers for my Probook 4540s (Intel 3000/Radeon 7650M) according to instructions given in thread: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355#288355). After execute the following command:
```
sudo dpkg -i xserver-xorg-video-intel_2.21.6-0ubuntu4_amd64.deb
```
I get error:
```
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel: xserver-xorg-video-intel depends on xorg-video-abi-13; however:
Package xorg-video-abi-13 is not installed.
dpkg: error processing xserver-xorg-video-intel (--install):  dependency problems - leaving unconfigured
```
I have read many posts and tried many instructions but each of them failed. I'm suprised, because many of you have installed the drivers correctly, but I can't (Xubuntu 13.04 64-bit)...

---

### Post by tmacyunn on 2013-05-04
Hi guys, i follow the post and make the Discrete GPU work. the package is 'xserver-xorg-video-intel_2.20.9-0ubuntu2.1_amd64' and 'amd-catalyst-13.4-linux-x86.x86_64'. Also i install amd64 version Ubuntu. But i just can use the discrete video care, i have amd6630m && hd3000, when i [COLOR=#000000][FONT=Microsoft YaHei]switch to ipgu with aticonfig, the screen is black. [/FONT][/COLOR]

---

### Post by tmacyunn on 2013-05-04
> **m4tik said:**
> Hi guys,

I try to install the AMD drivers for my Probook 4540s (Intel 3000/Radeon 7650M) according to instructions given in thread: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355#288355). After execute the following command:
```
sudo dpkg -i xserver-xorg-video-intel_2.21.6-0ubuntu4_amd64.deb
```
I get error:
```
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel: xserver-xorg-video-intel depends on xorg-video-abi-13; however:
Package xorg-video-abi-13 is not installed.
dpkg: error processing xserver-xorg-video-intel (--install):  dependency problems - leaving unconfigured
```
I have read many posts and tried many instructions but each of them failed. I'm suprised, because many of you have installed the drivers correctly, but I can't (Xubuntu 13.04 64-bit)...

It seems you need to install libudev0 package, search in the website; [WebUpd8]("http://www.webupd8.org/"). Hope it helps.

---

### Post by Falc7 on 2013-05-04
Your solution for the backlight worked for me :)

Out of curiousity, what is the difference between the xserver-xorg-video-intel file linked in the above post, and the one in the repos? According to the package manager, they both have the same version number? Should I never update the xserver-xorg-video-intel from the repos again on this version of ubuntu?

---

### Post by CU2 on 2013-05-04
> **Falc7 said:**
> Your solution for the backlight worked for me :)

Out of curiousity, what is the difference between the xserver-xorg-video-intel file linked in the above post, and the one in the repos? According to the package manager, they both have the same version number? Should I never update the xserver-xorg-video-intel from the repos again on this version of ubuntu?

Same question here. Now I can see an X.Org-X-Server-Intel-i8xx/i9xx update. Version is same as I installed in the solution: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-working/288355)

Changelog of the new update is: [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2%3A2.21.6-0ubuntu4/+changelog](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2%3A2.21.6-0ubuntu4/+changelog).

Now I am wodering if I should update or not!?:confused:

---

### Post by valek2282 on 2013-05-05
package manager to see this update because the modified driver is different size. I have compiled from source to activate UXA graphics acceleration for the integrated core, because the SNA acceleration does not work with the proprietary driver from AMD, the conclusion from this: if you install the driver (xserver-xorg-video-intel) from repository environment then X will not start))) Good luck)

---

### Post by lebaghaloo on 2013-05-06
i dont see mine in the supported section. is there any other solution? :(

12.04 LTS

sean@sean-HP-ENVY-14-Notebook-PC:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

---

### Post by razorxpress on 2013-05-07
Sorry for my last weeks post. I also confirm this solution works ([http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)).

---

### Post by Linukses on 2013-05-10
It works for me. Thank you. :) But i have one question. After downgrade intel drivers, can i install this upgrade? 
[IMG]http://ubuntuone.com/3SGksxsEwJGVzlJaIMFBTQ[/IMG]

---

### Post by MarcoDePollo on 2013-05-10
> **Linukses said:**
> It works for me. Thank you. :) But i have one question. After downgrade intel drivers, can i install this upgrade? 



No, if you do, it will break the graphics again. You can lock the installed version, so it won't want to update it again.

---

### Post by Linukses on 2013-05-10
Thank you for answer. And please, can you tell me how a i can do it? I try find some way, but there is no success... :(

By the way. Instuction (for Ubuntu 13.04) works with HP Probook 4530s - AMD Radeon HD 6490M + Intel HD 3000 Sandy Bridge

Sorry for my english... I do my best. :)

---

### Post by plbs on 2013-05-11
> **razorxpress said:**
> Sorry for my last weeks post. I also confirm this solution works ([http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)).

It worked for me too (Dell Vostro 3450, i5 2410 + ati 6630m) but only for Ubuntu 13.04 64 bit. I tried the 32 bit solution, but it was impossible to make it work.

---

### Post by MarcoDePollo on 2013-05-12
> **Linukses said:**
> Thank you for answer. And please, can you tell me how a i can do it? I try find some way, but there is no success... :(

By the way. Instuction (for Ubuntu 13.04) works with HP Probook 4530s - AMD Radeon HD 6490M + Intel HD 3000 Sandy Bridge

Sorry for my english... I do my best. :)

You do it from Synaptic. My Synaptic is in english but the menu-structure can't deviate too much.
(I'd deliver a screenshot, but Gnome is acting up at the moment, but here goes)
Start up Synaptic and enter xserver-xorg-video-intel.

Highlight the package and go to the Package menu. There you can find a menuentry called Lock Version. If all goes well, a small padlock should appear.

---

### Post by cosname on 2013-05-12
Thank you for post! It made me to use another post to solve this solution.

And it worked for me:
**DELL Inspiron 15R (N5520****) ****i7 **[B]with [FONT=Verdana]AMD Radeon HD 7670M 1 Gb
[/FONT][/B]
But i used this link, where "For 13.04 writened"
[http://askubuntu.com/a/288355](http://askubuntu.com/a/288355)
there was the same actions as in you post, and here is more information...

Hope that this driver will solve power saving problem to. Will see after charging will be fully done.

---

### Post by Linukses on 2013-05-14
> **MarcoDePollo said:**
> You do it from Synaptic. My Synaptic is in english but the menu-structure can't deviate too much.
(I'd deliver a screenshot, but Gnome is acting up at the moment, but here goes)
Start up Synaptic and enter xserver-xorg-video-intel.

Highlight the package and go to the Package menu. There you can find a menuentry called Lock Version. If all goes well, a small padlock should appear.

Thanks. I've got it, but updater still show me to update this driver. I am tried reboot my PC however result is a same... Is it correct and xserver-xorg-video-intel will never be update? Or it must dissapear?

---

### Post by Shabakthanai on 2013-05-16
:popcorn:I do not have your experience or skill or understanding of the process.  My new build has an AMD 8350 8 core 4.2
ghz processor with 16ghz ddr3 1866 RAM.  My video card is an XFX R7850 Double Dissipation 2GB DDR5.  My operating system is a dual-boot Kubuntu 13.04 / Windows 7 Professional Sp1.  My boot drive is a 256gb SATA III SSD.  Both the Win 7 and Kubuntu OS's are on that SSD.  I have never been a gamer and have only Bioshock and TombRaider in my Library right now in the Win 7 OS.

Will your instruction work for my video card and operating system?  If not, can you direct me to the appropriate help source.  Thanks for any reply.  I don't really have the understanding to search a solution without help. :)> **Alexislavie said:**
> [FONT=Arial][SIZE=2]If you do want to make the switch possible between your Intel and your AMD graphics cards, then this post is for you. If you do not own a AMD hybrid graphic card, please leave this thread, and post your problems in a thread made for AMD single graphic or Intel single graphic.

[B]Edit: The solution seems not to work with ATI 5xxx graphic cards, try at your own risk.
Warning: Works only for muxless systems.
Warning 2: Check if your BIOS is updated, if not update it ! (You will need Windows). This is your computer manufacturer that "implements the switch on your mother card, and modify the video drivers for Windows to work on your computer". If an AMD 6630m (for example) works on a HP computer, this doesn't mean the same video card will work for sure (for example) on a ASUS computer.
[/B] 
**Edit bodhi.zazen**: [COLOR=darkred]**Best check hardware compatibility before following this tutorial. If your hardware is not listed as supported, this tutorial will not help you. See [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) **[/COLOR]

The following solution has been tested on a DELL Vostro 3550, with an AMD 6630m card and an Intel HD 3000 (Sandybridge) card (integrated into a Intel core i5). The version of Ubuntu used is 12.04 LTS (further versions should works too). **The system is very stable, and everything works well.**
This tutorial requires the use of the terminal, but still is simple if you're a beginner, you will just have to past some commands on it and press "Enter".
*(Tip for beginners : to past a command on a terminal, just press CTRL+SHIFT+V, it is the same shorcut as usual just don't forget to press SHIFT when pasting).*

Before beginning this tutorial, we will suppose you are following it on a fresh install (i.e. You did not install vgaswitchroo or flgrx (via jockey-gtk : The proprietary driver installer application from Ubuntu). Please also install all updates available for your computer before starting (and reboot if you're proposed to).
[B][COLOR=red]
STEP 1 - Installing latest AMD catalyst drivers :[/COLOR][/B]

As I'm writing this the latest version is 12.4, please check this page to know if there is a new version : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)[/SIZE][/FONT][FONT=Arial][SIZE=2] (this also includes the guide to install them).

First we're going to download all the prerequisite packages :
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
```If you're using Ubuntu 64bits please run those two commands (32bits users don't have to) :
```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
```We can now download the AMD catalyst 12.4 driver :
```
cd ~/; mkdir catalyst12.4; cd catalyst12.4/
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run
chmod +x amd-driver-installer-12-4-x86.x86_64.run
```And create Ubuntu packages of it :[/SIZE][/FONT][FONT=Arial][SIZE=2]
```
sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
```Now let's install them :
```
sudo dpkg -i fglrx*.deb
```and configure the Xserver (xorg.conf file) for the first time :
```
sudo aticonfig --initial -f
```Now reboot your computer.

Test the switch to the discrete card :
```
sudo aticonfig --px-dgpu
```Then reboot again your computer.
[B] 
[COLOR=red]STEP 2 - Enabling, fixing the bug for direct rendering on the integrated card :[/COLOR][/B]
*Thanks to **[Niccola]("http://ubuntuforums.org/showpost.php?p=11819555&postcount=107")** for finding the actual fix.*[/SIZE][/FONT][FONT=Arial][SIZE=2]

_[COLOR=darkorange]If you ever apply an fglrx update, or your system automatically update fglrx, YOU WILL HAVE to repeat STEP 2, otherwise direct rendering will be missing on integrated gpu (i.e. No Unity 3D or Gnome Shell or Gnome Classic + Compiz on the Intel graphic). If you have an other solution (like loading a script on startup) please post it.[/COLOR]_

Open the /etc/X11/Xsession.d/10fglrx file with root rights :
```
gksu gedit /etc/X11/Xsession.d/10fglrx
```If you're using a 32bits system add at the end of 4th line this text : *"/usr/lib32/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32 
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```If you're using a 64bits system add at the end of 4th line this text : *"/usr/lib/x86_64-linux-gnu/dri/*" without the quotes. The file should now look like this :
```
 LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri 
if [ `uname -m` = 'x86_64' ]; then 
if [ -d /usr/lib32/fglrx/dri ]; then 
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
if [ ! -z $LD_LIBRARY_PATH ]; then 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH: 
fi 
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}/usr/lib32
export LD_LIBRARY_PATH 
fi 
fi 
export LIBGL_DRIVERS_PATH
```Now save the file.

**[COLOR=red]STEP 3 - Enjoy your hybrid graphic system ! :[/COLOR]**

Reboot your computer to see the changes, it should boot up with the discrete card.[COLOR=black]

[/COLOR]**[COLOR=red]Useful informations, commands :[/COLOR]**

Power consumption is a lot better now, it seems that my battery last 4 times more with the integrated card, but this isn't still good as in Windows. If someone find or know tricks to decrease power consumption a little more please post it !

I do not recommend to update the catalyst driver once it's installed (if it works), if you really want to upgrade then check this page to find instructions : [/SIZE][/FONT][FONT=Arial][SIZE=2][http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)[/SIZE][/FONT][FONT=Arial][SIZE=2]

The AMD driver GUI application doesn't provide settings for screen configuration, but only 3d settings. This is a missing feature.

[I]Switching commands :
[/I]```
aticonfig --pxl # List current activated GPU
sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect
sudo aticonfig --px-igpu # Activate integrated GPU (Power-Saving mode), must re-start X to take effect
```Verify the Open GL's libraries used :
```
fglrxinfo
```Verify if the direct rendering is used :
```
glxinfo | egrep render
```Install mesa-utils, and test the card 3d power (compare the fps) :
```
sudo apt-get install mesa-utils
glxgears
```[COLOR=Red]If something goes wrong and your[/COLOR][COLOR=black][COLOR=Red] computer doesn't boot (i.e. black screen), press CTRL+ALT+F3, log yourself into your account and enter those commands :[/COLOR]
[/COLOR]```
sudo rm /etc/X11/xorg.conf
sudo startx
```And you should be able to see your desktop.
[COLOR=red]
[/COLOR]**[COLOR=red]List of fully supported computers :   [/COLOR]**[COLOR=DarkOrange]// Updated 05/16/2012 (American date format).[/COLOR]
[/SIZE][/FONT]   
[LIST]
[*][FONT=Arial][SIZE=2]**ACER      7750g**, Intel HD 3000, AMD 6650m, HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL Inspiron 14R (N4110)**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**DELL      Vostro 3550**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Envy 14t-2000 CTO**, Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP ENVY 15-3090CA**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6630m, HDMI Intel/AMD: not  tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dm4-2160sf**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavillion dm4-2110sp**,[/SIZE][/FONT][FONT=Arial][SIZE=2] Intel HD 3000, AMD 6470m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6102sg**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6169sl**, Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6178sl**, Intel HD 3000, AMD 6770m, HDMI Intel/AMD: working/working, VGA      Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv6-6192sf**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6770m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion dv7-6070ef**, Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/working,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Pavilion g4-1001tx**[/SIZE][/FONT][FONT=Arial][SIZE=2], Intel HD  3000, AMD 6490m, [/SIZE][/FONT][FONT=Arial][SIZE=2]HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**HP Probook 4530s**, Intel HD 3000, [/SIZE][/FONT][FONT=Arial][SIZE=2]AMD 6490m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested,      VGA Intel/AMD: not tested/not tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo e520**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6630m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**Lenovo G-770**,[/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6650m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SB1S1E**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**SONY Vaio VPC-SC1AFM/S**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6470m[/SIZE][/FONT][FONT=Arial][SIZE=2], HDMI Intel/AMD: not tested/not      tested, VGA Intel/AMD: [/SIZE][/FONT][FONT=Arial][SIZE=2]not tested/not      tested[/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=2]
If you want to add your computer, please do want it (this will help other users), **_make a post and indicate your configuration [COLOR=Red]like those above[/COLOR]_**. 
[/SIZE][/FONT][FONT=Arial][SIZE=2]I will then add it to the working list.
[/SIZE][/FONT][FONT=Arial][SIZE=2]_I repeat as many people do not get it : "[COLOR=Red]like those above[/COLOR]" ! It take you two minutes to write it, this saves me time, and I can update more frequently this thread._ Also posts like "It works on HP Pavilion dm4" are USELESS, I won't add a computer with an incomplete computer model number. Exception for computers without a precise model name (example : DELL Vostro 3550, Lenovo e520).
[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black]


_Useful links :_
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://forums.gentoo.org/viewtopic-p-6936730.html](http://forums.gentoo.org/viewtopic-p-6936730.html)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can thanks that guy because his post really helped me to understand how the ati hybrid graphics works.
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=royalblue][http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics](http://en.gentoo-wiki.com/wiki/Fglrx-hybrid-graphics)[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black] You can also check this Gentoo wiki about hybrid graphics, this is some Gentoo's users that actually found first a solution on how to make AMD hybrid cards to work on Linux.[/COLOR][/SIZE][/FONT]

---

### Post by pasquale4289 on 2013-05-18
Hi, can I post my xorg.log? I'm not able to understand if my problem is one of those you're discussing above.

---

### Post by rohit3221 on 2013-05-19
Hi..Followed your steps..but now when I use discrete gpu, Kubuntu loads into recovery...whereas when I load it into Integrated GPU mode, it again loads back into GUI mode..Any help ?

---

### Post by Ishayu on 2013-05-20
I tried doing this on a MacBook Pro 8,2. Don't do that... :S

After completing all the steps, I get to a point where the graphics stack is ill configured, and X won't start. FGLRX will attempt to kill itself or in some cases kill initramfs, which causes a kernel panic. But that isn't the biggest problem...
The biggest problem is that X won't start, and neither will your CPU or GPU fans! Linux will try to save your ass by throttling the CPU speed lower and lower, but Linux will warn you about hardware check fails, and the temperature of my CPU measured 105 degrees on all cores before I shut it down. That is really bad.

Just to make matters a little bit worse, if you try to not do anything, you'll have the open source AMD drivers start an xserver with Unity on it AND you'll have the intel open source drivers start an xserver with Unity on it, so you'll have two unity's on top of each other that both perform every single task you assign your computer, and one of them only runs in 1280x800 while the other runs at full resolution. I'm unsure which is which.

If someone could point me towards a tutorial for getting this to work on my MBP I'd be most appreciative, but I'm not trying this again...

---

### Post by Przedzmirski on 2013-05-21
Hybrid Grapchis worked for me!! I used this thread, like others said before:

[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

My specs: [COLOR=#000000][FONT=Arial]*[SIZE=2]**DELL Inspiron 14R (N4110)**, [/SIZE]*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*[SIZE=2]Intel HD 3000, AMD 6470m,[/SIZE]*[/FONT][/COLOR][COLOR=#000000][FONT=Arial][I][SIZE=2] HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working
[/SIZE][/I][/FONT][/COLOR]
Anyway, thank you very much for everyone who contributed here. Helped a lot!

Just one issue: When i'm using the discrete GPU, if I open an image in the default image viewer, and try to move it, my session is killed o.0. Do somebody experienced something like this yet?

Thank you all! And good luck with Hybrid =D
:guitar:

---

### Post by laci37 on 2013-05-21
Has any one got this working with kernel version >= 3.6? I can't install the deb packages, because DKMS prints an error, that my kernel is unsupported. I have 12.04 with kernel 3.6.6. [I also asked this question on askubuntu.com]("http://askubuntu.com/questions/298153/amd-intel-hybrid-graphics-driver-on-3-6-6-kernel"). There I have posted some log files.

---

### Post by MeshachBlue on 2013-06-01
Finally Working!

I have a HP dv6-6024TX -- [http://www.mln.com.au/product/?itemID=3545](http://www.mln.com.au/product/?itemID=3545)

This is exactly what I did.

1)
Fresh install of Ubuntu 12.10 64bit

2)
Ran all updates

3)
Installed the following:

> sudo apt-get install linux-headers-generic

4)
Downloaded the AMD driver:
[http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip)

5)
Extracted the zip and marked the .run file for execution

6)
Ran the file in the following way:

> sudo ./amd-driver-installer-catalyst-13-4-x86.x86_64.run

7)
Clicked the TOP option "Install Driver ... "

8)
Pressed NO to restart

9)
Typed this into the terminal:

> sudo amdconfig --initial

10)
Then I rebooted.

11)
SMILED with great JOY... even said HALLELUJAH :) workes wonderfully... one can change graphics using the catalyst control centre...
It is great.


This helped:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by snake2903 on 2013-06-02
[FONT=Arial][SIZE=2]Hi, i have HP ProBook 4730s with Intel HD 3000 and AMD Radeon 6490m hybrid system,
I installed fresh Linux Mint 15 64-bit (Ubuntu 13.04) and did every steps in this tutorial:

[URL="http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355"]http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355

[/URL]I used latest stable AMD drivers, 13.4 version.
Everything works great. I tried switch to Intel HD, restart, works. I tried switch to AMD 6490m, restart, works.
Nothing crashed. I make scripts for switching, like in tutorial and works great.
Only thing i didn't try is HDMI. When try it, i'l edit post.

[B]
HP Probook 4730s[/B], Intel HD 3000, [/SIZE][/FONT][FONT=Arial][SIZE=2]AMD 6490m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested **yet**/not tested **yet**,      VGA Intel/AMD: **working**/[/SIZE][/FONT][FONT=Arial][SIZE=2]**working**[/SIZE][/FONT]

---

### Post by rikkinho on 2013-06-04
ubuntu 13.04

amd 13.6 beta kernel 3.8 intel hd 3000 with 6770m works with xna intel drivers, without problems.... but... really bad perfomance on steam, really really bad amd sucks, the 13.1 works a lot better on steam games, i cant undertand this type of regression the dev team from need amd prop driver needs to be fired, bad support on windows bad support on linux, i hope mir bings hybrid graphics with opensource driver i&#7743; tired with this garbage drivers.

---

### Post by Dystout on 2013-06-06
I am having no success following the guide found [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355) in any of Ubuntu, Xubuntu, or Mint (all 13.04).  Everything seems to go alright up unto the final reboot, and then I am unable to get back into a GUI.  I have consistently received one error while following the steps in the guide, which I will post later once I reinstall one of the distros for the umpteenth time (as I can't access anything on the one I have installed right now).  I am presented with the terminal log in, and am able to in order to access the terminal prompt.  Mint is the only one that presents me with errors, about the xserver being unable to start due to a faulty graphics configuration (or something like that).  I have an Envy 15t-3200 with hybrid intel hd 4000/radeon hd 7750, if that changes anything.  I would really love some help if anyone can offer it; I am dying to get this working.

---

### Post by mauriciofauth on 2013-06-11
[AMD Catalyst 13.6 Beta]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") has released!

Someone has tested this version?

---

### Post by orbus on 2013-06-16
> **mauriciofauth said:**
> [AMD Catalyst 13.6 Beta]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") has released!

Someone has tested this version?

Yes, I tried it. Serious Sam 3 seems to be faster than 13.4, but Portal and Half-Life 2 has poor performance. I need to delete Catalyst and I need to play with my Intel HD3000 instead of Radeon HD6630:(

Has someone try Half-life 2, Portal with any of Catalyst version?

Using the catalyst is much slower in games than Intel HD3000, have you got any idea why? I tried these games with Ubuntu 12.04/12.10/13.04 with any of Catalyst versions.

Have someone any experiences about Catalyst / AMD Hybrid / Steam games?

---

### Post by Antarell on 2013-06-21
Is there a better solution from having to downgrade the intel Xorg package yet? Does xorg edgers fix it the problem?

---

### Post by jackschmidt on 2013-06-28
I've just confirmed that you still need the old intel Xorg package even with the 13.6 beta drivers.

---

### Post by ppierpaolo on 2013-06-30
Sorry, could someone please recapitulate what's the right procedure, and what AMD radeon graphic cards work with that procedure? I'm having some problems trying to read all the thread.

---

### Post by jackschmidt on 2013-06-30
This is what I did if you are referring to the Intel Xorg package solution:
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

### Post by pokepal101 on 2013-07-09
Whoo! Thanks a lot! I can confirm that this works on my laptop (using Catalyst 13.4):

**HP Pavilion DV7-6108TX**, Intel HD 3000, AMD 6770M, HDMI Intel/AMD: not tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested

Minecraft (Intel graphics): 9FPS
Minecraft (AMD card): 40FPS

---

### Post by Przedzmirski on 2013-07-11
> **pokepal101 said:**
> Whoo! Thanks a lot! I can confirm that this works on my laptop (using Catalyst 13.4):

**HP Pavilion DV7-6108TX**, Intel HD 3000, AMD 6770M, HDMI Intel/AMD: not tested/not tested, Mini DisplayPort Intel/AMD: not tested/not tested

Minecraft (Intel graphics): 9FPS
Minecraft (AMD card): 40FPS

Could u say what version of ubuntu are u using now? Probably 12.04 or 12.10, am i right? In my dell with intel hd3000/ amd radeon 6470m and ubuntu 13.04, using the catalyst 13.6 doesn't changed significantly the performance of my machine.. =/ at least for now.

---

### Post by pokepal101 on 2013-07-11
> **Przedzmirski said:**
> Could u say what version of ubuntu are u using now? Probably 12.04 or 12.10, am i right? In my dell with intel hd3000/ amd radeon 6470m and ubuntu 13.04, using the catalyst 13.6 doesn't changed significantly the performance of my machine.. =/ at least for now.

I'm running 12.04.2 (64-bit version). Installing the drivers didn't improve the performance of the machine during regular tasks; the difference was only noticeable when gaming (or performing other GPU-intensive tasks).

---

### Post by Przedzmirski on 2013-07-12
Are u having the overheat problem? With the cooler turned on all the time? When I tried to use ATI drivers, i got this and some bugs like logging off when trying to move an open image in image viewer, besides the less smoothing window changing, with some flickerings and etc.

---

### Post by Niccola on 2013-07-13
Is someone's backlight button working? I don't have my backlight settings works since last Catalyst beta release 13.6

> **Przedzmirski said:**
> Are u having the overheat problem? With the cooler turned on all the time? When I tried to use ATI drivers, i got this and some bugs like logging off when trying to move an open image in image viewer, besides the less smoothing window changing, with some flickerings and etc.

Normally the opensource driver cause overheating problem. Could you verify if you entered the command 
```
amdconfig --initial -f
```

It creates a xorg.conf file with AMD proprietary drivers definitions. Should help on overheating problem.

---

### Post by Niccola on 2013-07-15
I just want to advise after installing Catalyst 13.6 beta can cause backlight control stop working.

To who it may concern,
there's an workaround by adding acpi_backlight=vendor at linux kernel line on /etc/default/grub file (as root):

(example)
/etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=vendor**"
```

then run update-grub2 command as root and reboot.

---

### Post by insnFM on 2013-07-18
hi guys, help needed
I was trying to install ATI dual graphics on my HP dm4 2000 (GPU's are in the supported list) using the tutorial on the first page and after the very first reboot I've got the message regarding the low graphics mode because of incorrectly configured drivers. I'm stuck here with the two options:
-proceed to terminal mode with unconfigured hardware.
-roll back to a stock drivers and get a blank desktop. 
Let me know pls, what's went wrong here, and how can I get my dual graphics ?
Thnx

UPD: ubuntu 13.04 on board

---

### Post by mauriciofauth on 2013-08-11
@insnFM
Have you tried this?
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

### Post by Niccola on 2013-08-13
[SIZE=4]**Please everyone with Intel+AMD Hybrid Graphic cards READ this:**[/SIZE]

As many installation instructions available on the web, it's difficult do find out the best procedure to install Intel+AMD Hybrid cards and put them to work flawlessly. Due to this, I made a lot of research and I've built my own procedure for this installation on Linux Systems. I've tested it on Ubuntu based systems 13.04+ (Xubuntu, Linux Mint 15 and Stock Ubuntu) and worked very well. [SIZE=3]**13.8 beta 1**[/SIZE] driver used, please try by your own other drivers and post results.

[SIZE=4]**However,**[/SIZE] regarding many different laptop/desktop manufacturers available over there, it's quite difficult to affirm if this procedure will work to everyone... I hope so and [SIZE=4]**PLEASE**[/SIZE], post if it worked for you or [SIZE=4]**NOT **[/SIZE](and let us help you)

The following installation instructions are was made by me as a collection, involving lots of instructions available in the Web and documentations (References available on the bottom)...

[SIZE=4][B]BEFORE:
[/B][/SIZE]*It is recommended to install is on a fresh ubuntu 13.04 based install 
*make sure you have no AMD fglrx driver installed:
```
sudo apt-get remove --purge fglrx*
```
*Make sure your AMD discrete GPU is ACTIVATED through vgaswitcheroo:
```
sudo su
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
exit
```

1 - Prepare the system to proprietary AMD driver manual installation, installing prerequisites on the system, to help to compile and create the correct amd driver according to your system. So, to install the driver compiler prerequisites, execute the following command in terminal:
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic xserver-xorg-core libgcc1 mesa-utils
```


[SIZE=3]**64-bit (x86_64) ONLY: MUST execute this two commands also:**[/SIZE]
```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
```

Then, reboot system:
```
sudo reboot
```

2 - Install Intel Linux Graphics Installer
BEFORE AMD driver installation we have to install latest Intel driver. However, latest intel driver isn't available on Ubuntu repositories as default, so we have to install it through Intel linux Graphics Installer. This tool is developed by intel and supports latest Ubuntu version by default.
**NOTE:** Please read carefully [Intel Linux Graphics Installer 2013Q2 webpage]("https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2") for complete notes and download it to other distributions and other Ubuntu versions:
[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

prepare a directory for Intel Linux Graphics Installer:
```
mkdir ~/IntelLinuxGraphicsInstaller
cd ~/IntelLinuxGraphicsInstaller
```

2.1 - Download and Install Intel Linux Graphics Installer
Ubuntu 13.04 **64-bits (x86_64)** systems:
```
wget https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb
sudo dpkg -i intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_amd64.deb
```

Ubuntu 13.04 **32-bits (x86)** systems:
```
https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.2-0intel3_i386.deb
sudo dpkg -i intel-linux-graphics-installer_1.0.2-0intel3_i386.deb
```

2.2 - Execute and Install Intel Linux latest Graphics Driver
```
sudo intel-linux-graphics-installer
```
Follow procedure window clicking on "Next" and "Install" then wait until driver installation successful completes.

Then, reboot your system by clicking on the Intel Linux Graphics Installer window Reboot button, or:
```
sudo reboot
```

2.3 - After rebooting just install Intel Linux Graphics Installer Public Key to trust on Intel repository for future updates:
*[COLOR=#333333][FONT=Arial]"In order to "trust" the Intel® Linux Graphics Installer, you will need to add keys to Ubuntu's software package manager ("apt"). Open a terminal, and execute these line:"[/FONT][/COLOR]*
```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | \
sudo apt-key add -
```
AND:
```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | \
sudo apt-key add -
```

3 - Create a driver directory and download driver direct from amd.com
```
cd ~/ && mkdir amd-fglrx-driver && cd amd-fglrx-driver
wget http://www2.ati.com/drivers/beta/amd-catalyst-13.8-beta1-linux-x86.x86_64.zip
unzip amd-catalyst-13.8-beta1-linux-x86.x86_64.zip
chmod a+x amd-catalyst-13.8-beta1-linux-x86.x86_64.run
```

3.1 - AMD **13.8 Beta 1** Driver Installation
```
./amd-catalyst-13.8-beta1-linux-x86.x86_64.run --buildpkg Ubuntu/raring
sudo dpkg -i fglrx*.deb
```
3.2 - Post installation configuration
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo amdconfig --initial -f
sudo amdconfig --px-dgpu
```

4 - Reboot the system and check installation

```
sudo reboot
```

after rebooting... check driver installation
```
fglrxinfo
fgl_glxgears
glxgears
```

Enjoy the powerful of Intel+AMD hybrid video experience on Linux! :guitar:

[SIZE=3]**PLEASE comments your results and HW configuration**[/SIZE]


References:
[CCHTML Wiki Ubuntu 13.04 Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide")
[AMD Driver Page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
[Intel Linux Graphics Installer 1.0.2]("https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2")
[ask.ubuntu Question]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work")

---

### Post by refraction222 on 2013-08-16
[FONT=Arial][SIZE=2]
I've been studying this issue for a long time, thanks to your post, i have successfully installed both amd and intel driver, and both in direct rendering . Now my laptop is much cooler.
I'll test HDMI output as soon as i get an HDMI wire.
ps. Under ubuntu 13.04, after i manually installed AMD discrete driver and reboot, i fall into this bug:[/SIZE][/FONT][https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)[FONT=Arial]. but anyway this post works under 12.04.2, thanks a lot![/FONT]:P
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]Here's my result:

[LIST]
[*][FONT=Arial][SIZE=2]**DELL Inspiron 14R (N4110)**, [/SIZE][/FONT][FONT=Arial][SIZE=2]Intel HD 3000, AMD 6630m,[/SIZE][/FONT][FONT=Arial][SIZE=2] HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: working/working[/SIZE][/FONT]
[/LIST]

---

### Post by eng-alimohamedali on 2013-08-21
i had problem as i do the line 
sudo dpkg -i fglrx*.deb 
then i reboot and i cant boot again i got black screen after ubuntu logo

---

### Post by ajinkya2 on 2013-09-11
AMD ATI supports linux mobile now.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by ajinkya2 on 2013-09-11
AMD 8730m :(( 

```

ajinkya@ajinkya-Inspiron-3521:~/Downloads$ sudo aticonfig --initial -f
aticonfig: No supported adapters detected



```

---

### Post by mauriciofauth on 2013-09-18
Amazing, Niccola!
This guide worked perfectly for me.
Congratulations!

Samsung Series 7 Chronos NP700Z4A-SD1BR, Intel HD 3000, AMD HD6750M, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested

---

### Post by acapop77 on 2013-09-23
@Niccola it worked great. I have tried many solutions that I found on  the net but only this one worked for me. With others solution after  reboot I always got to 'Low Graphic Mode' where no fix that I tried  helped and I ultimately got stucked each time. Well this one worked, so  thank you for that.

Dell Vostro 3560 on Ubuntu 13.04 64-bit:  Intel® Core™ i7-3612QM CPU, Intel Corporation 3rd Gen Core processor  Graphics / AMD Radeon HD 7670M.
HDMI tested on AMD card only - works  good only for single monitor mode, only laptop or only external. If both  monitors are turned-on weird graphic bug - not usable in mirror or  side-by-side mode. Just nothing works good if both displays are ON, in  single monitor mode all is good, picture and sound working fine. Yes and  HDMI Sound is working good on external.

Sorry for not testing Intel graphic - I just don't dare to :). This is my production machine so I need it running, sorry :)

Almost forgot, I used latest AMD stable 13.4 driver. Did all steps as described for 64-bit, only had one issue when trying to install Intel Graphic Driver, got missing dependacy for soem ttf fonts, so just installed that and next time I tried Intel Driver went smooth. Had no issues, errors or anything in the rest of the process.

Once more thanks Niccola :)

---

### Post by texnl on 2013-09-25
Nicola worked for my system: Ubuntu 13.04 / Lenovo IP y470p (i5 Sandy, HD 7690m), used beta2 driver from AMD, had to do step 2.3 before 2.2 because it was getting some update errors.
Many thanks ;)

---

### Post by Uuganbaatar on 2013-09-30
> **Niccola said:**
> [SIZE=4]**Please everyone with Intel+AMD Hybrid Graphic cards READ this:**[/SIZE]

As many installation instructions available on the web, it's difficult do find out the best procedure to install Intel+AMD Hybrid cards and put them to work flawlessly. Due to this, I made a lot of research and I've built my own procedure for this installation on Linux Systems. I've tested it on Ubuntu based systems 13.04+ (Xubuntu, Linux Mint 15 and Stock Ubuntu) and worked very well. [SIZE=3]**13.8 beta 1**[/SIZE] driver used, please try by your own other drivers and post results.
...

Thanks. I can switching between Intel and AMD cards without problem. Perfect!

[LIST]
[*]**Dell Inspiron 7520 (15R SE) **Intel HD 4000, AMD 7730M, HDMI Intel/AMD: not tested/not tested, VGA Intel/AMD: not tested/not tested
[/LIST]

---

### Post by griz2 on 2013-10-02
@Niccola
Thanks for the guide. It's the only one that got me so far. Sadly I still have some problems.

**System**
Ubuntu 13.04 (Raring)

**Driver**
amd-catalyst-13.8-beta2-linux-x86.x86_64.zip

**Hardware:**
MSI ge700
Intel Core i5 430M - Intel HD Graphics
mobile Radeon HD 5730

**Result:**
Not using amdconfig generated Xorg.conf file is breaking the Unity and only desktop shows up after login.
Using amdconfig generated Xorg.conf file causes "The system is running in low-graphics" mode and reports in Xorg log file that there are no devices detected / no screens found.

---

### Post by petersphilo on 2013-10-04
> **Ishayu said:**
> I tried doing this on a MacBook Pro 8,2. Don't do that... :S
After completing all the steps, I get to a point where the graphics stack is ill configured, and X won't start. FGLRX will attempt to kill itself or in some cases kill initramfs, which causes a kernel panic. But that isn't the biggest problem...


Same here (nearly).
i tried this on a MacBook Pro 8,3 (same hardware as the MacBook Pro 8,2 except 17-inch) and got nearly the same result...
i've been trying to install the Radeon proprietary drivers for other reasons (don't really care about the intel chip, i just need to run the AMD proprietary driver in order to run X-Plane)
If anyone's got any ideas for me, i'd be greatly appreciative!
Cheers!

---

### Post by Feby_Philip_Abraham on 2013-10-04
@Niccola: You're just awesome buddy!! Now I've got completely switchable AMD/Intel GPUs on my laptop.

**Device**: HP Pavilion dv6-6180SE Entertainment Notebook
**Config**: Intel Core i7-2670QM, AMD Radeon HD 6770M
**OS**: Ubuntu 12.10 (Quantal)
**Kernel**: Linux 3.5.0-41-generic
**Driver**: amd-catalyst-13.4-linux-x86.x86_64

One tiny issue though. The Intel drivers don't seem to support Linux kernels above 3.9. I tried install the Intel drivers with Kernel 3.11.1 and the installer kept showing that the OS was not supported. However, it worked perfectly when I reverted back to 3.5.0.

---

### Post by DominikCZE on 2013-10-05
[COLOR=#000000]@Niccola:   Unfortunately, not a single intel driver works with *12.04 LTS*. 
[/COLOR]> Checking if Intel graphics card available... OKRetrieving information from 01.org... OK
Checking distribution... Failed


EDIT:

It looks like that after about ten tries with plenty of other advice, your guide finally worked for installing the AMD drivers. There is still nothing showing up in the proprietary drivers tab, but the check worked and I can now launch Steam without an error. I guess the intel card is running on some generic drivers preinstalled with ubuntu. 
The annoying thing now is that I think the computer is permanently in high performance mode, so the GPU fan is constantly on.
Hardware:
Clevo p150em - Intel® Core&#8482; i7-3610QM CPU @ 2.30GHz, AMD Radeon HD 7970M 

OS and kernel: Ubuntu 12.04 LTS, Linux 3.2.0-54-generic

Driver: [COLOR=#000000][FONT=Ubuntu Mono]amd-catalyst-13.8-beta1-linux-x86.x86_64[/FONT][/COLOR]

---

### Post by jmite on 2013-10-12
Has anyone made progress on getting this to work on Saucy?

---

### Post by DominikCZE on 2013-10-20
And.... an unknown update broke the driver. Had to restore back to default.

---

### Post by stormforce133 on 2013-10-22
The Intel Driver Installer does not support Saucy, I'm still waiting, with my hotty and noisy HP Pavilion DV7 Quad Edition (i7-2630QM/6770M) :P

EDIT: I've just installed Catalyst beta 13.11 following @Niccola 's guide, without the Intel driver and worked flawlessly (except for black Google Chrome titlebars when using Discrete GPU)

Thank you!!

EDIT2: Bugs so far: 1) No titlebars in Google Chrome while using DGPU. 2) No brightness control
I've not tested HDMI output yet.

EDIT3: HDMI output works fine on Intel GPU, I've not tested DGPU.

EDIT4: Brightness workaround:
[COLOR=#333333][FONT=UbuntuRegular]in /etc/default/grub file add or modify this line:
[/FONT][/COLOR]GRUB_CMDLINE_LINUX="acpi_backlight=vendor"Then sudo update-grub and reboot.

---

### Post by cRaZyBisCuiT on 2013-10-26
> **Niccola said:**
> [SIZE=4]**Please everyone with Intel+AMD Hybrid Graphic cards READ this:**[/SIZE]
[...]

Since the productive system of my girlfriend is affected with the ATI switchable issue I just can't try what you said right now. She really needs her system to be up and running atm. I wonder if anybody (including you, Niccola) knows if this mehtods will run with "the old muxed systems. They used to work with only one old catalyst in the past. I really wonder why they shutted down the support later  on :(

---

### Post by emuboy on 2013-10-28
I managed to work all both graphics card on my vaio vpcsb with ubuntu 13.10:

Do a fresh install,do all the updates , install amdcccle and amdxdg-su with :

```
sudo apt-get install amdcccle amdxdg-su
```

reboot, launch amdcccle, choose your graphic card ad log out.


TLTR:

It's works guy! near out of the box :D

---

### Post by Niccola on 2013-10-29
I'll create a guide to install Hybrid Graphics on Ubuntu 13.10 with latest beta driver (13.11beta6). I'm already running it on my box. However, Ubuntu 13.10 already implements and supports Hybrid Graphics by installing following packages:

```
sudo apt-get install fglrx fglrx-pxpress
```
reboot and try! Please don't forget to post results!

source: [Ubuntu Wiki]("https://wiki.ubuntu.com/X/Config/HybridGraphics#A13.10")

---

### Post by Niccola on 2013-10-29
As expected, instructions in my last post install successfully fglrx driver on Ubuntu 13.10 derived. This driver is supported by official Ubuntu Canonical Team and may be error free and Ubuntu friendly.

I do recommend people who don't have latest graphic cards and those who don't want to command line, but prefers simple ways. Follow next steps:

```
sudo apt-get install fglrx fglrx-pxpress
```

then reboot and voilà! everything works out of box!

But if you want enjoy latest drivers provided by AMD, follow my post [#815]("http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069"), taking care the following:

1 - It is no necessary to install Intel Linux Graphic Installer on Ubuntu 13.10 systems because It has already latest graphic drivers provided by Intel
2 - It is no more necessary to install ia32-libs package because multi-arch linux was totally merged on Ubuntu 13.10

So, download latest driver from AMD (today is 13.11beta6) and install is as guided step by step on post [#815]("http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069")

You can also follow instructions at [wiki.cchtml]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide") unofficial guide

Best Regards all!

---

### Post by pier_92 on 2013-10-31
Hello to everyone! 
I did what the very first tutorial in this thread suggested step by step but I just achieved that the graphics didn't work anymore. 
I am using an HP pavillon dv6 running Ubuntu 12.04 and when I rebooted my laptop after having done everything he gave me the screen "The system is running in low-graphics mode", so that all I could do was restoring last working graphic setting. 
Someone can help me? 

Thanks!

---

### Post by ssshikari01 on 2013-11-01
Your laptop sucks as my does: as i can judge by my li'l experience of using ubuntu+hp, hp has a muxless system which is unsupported by [FONT=Arial][SIZE=2]proprietary drivers. All i can advice you - use opensource drivers. Low performance, overheating, but no black screens at least. [/SIZE][/FONT]

---

### Post by sarvigalava on 2013-11-02
Samsung series 7 with radeon 6750m works fine with ubuntu 13.10 and latest drivers. No issue found for 3 days of usage. (with exception the black tabs in chrome on discrete graphics)

---

### Post by bellzebu on 2013-11-11
I did not try to install Catalyst anymore, I was trying to install it in all ways but it is impossible. Xserver-xorg-video-ati works fine but I am damned to play games on Windows :/

A good Hybrid Graphics support is a support that not forces you to waste hours of your time tweaking and cheating and testing to install a single driver.

---

### Post by rogier.delporte on 2013-11-16
I've been trying for 2 days straight, but I can't seem to get switchable graphics working for me. I run debian wheezy with gdm 3. The dedicated gpu works just fine, but when I want to switch to integrated gpu, the whole thing derps like crazy... Gnome wont start and fglrxinfo tells me uable to open display(null). I used the instructions on [http://wiki.cchtml.com/index.php/Debian](http://wiki.cchtml.com/index.php/Debian) . I followed the package manager approach. I'm certain I haven't set up catalyst right to work with the intel gpu...

btw: I'm on a dell inspiron 14z(5423, 3rd generation Intel HD graphics, AMD Radeon HD7570M, if I'm not mistaken.

---

### Post by AngelGenchev on 2013-11-24
Yes, it works, it's time for champagne, unless there were not some weird problems after that:
1) With Intel GPU, the bad is that my PC hangs upon Xfce logout. The good: Intel's driver works very well, vsync is on, no tearing in VLC, no tearing in OpenGL, some lagging when you drag windows in xfce.
2) With ATI GPU, and monitor@VGA output, vsync is not switchable on by any means (0x00000800 flag, TexturedVideoSync, Wait to vertical refresh always on in control center). Strong video tearing in VLC, CPU usage - one of the cores is 100% when rendering OpenGL apps. Since I can't watch tear-free video, it's unusable for anything than gaming. The good: PC doesn't hang upon Xfce logout.

All this tested with Xubuntu 12.10 + Compton OpenGL compositor (to prevent tearing caused by xfwm4's built-in compositor). 
Machine: 1.5yr. old Dell Vostro 3350, Core i7 for Intel GPU, Radeon HD 6400M/7400M ATI Caicos, external monitor @ VGA output.

I think I'm going to remove fglrx and **return** to switcheroo way of disabling the DGPU, because I felt that X.org startup was faster. Also there werent the  hang problems on XFCE logout. 
The problems were: 1) hang when resume from suspend-to-ram in ATI atombios. 2) vgaswitcheroo interface didn't manage to switch DGPU off from rc.local, so I had to run rc.local again by hand - in terminal.
My advice: Stay away from hybrid graphics. You can see that in every case there are problems. Use laptops with single GPU to save your nerves.
Problem 1) has workaround here:  [Fix Suspend - wake freeze]("https://help.ubuntu.com/community/HybridGraphics#Fix_Suspend.2BAC8-Wake_Freezing").

---

### Post by milleyj on 2013-11-27
I was delighted to hear that support was finally here for hybrid graphics cards.  My Dell 7520 (15r SE) has been useless to me without being able to run linux adequately.

I'm having some troubles though.  Here's what I've done so far:

Fresh install of 13.10 + installed all updates
Installed fglrx and fglrx-pxpress and was notified that my AMD card was activated.
Switched to my integrated Intel card (as I have very little need for the extra graphical power) in AMD Control Center
Rebooted, everything works fine and I'm a happy boy.
Rebooted again after some updates (nothing graphics related) and boom - the dreaded low graphics screen... I revert to default settings and reboot


Now I'm back in business though with some issues.

Running any aticonfig option presents me with the following error:
```
$ aticonfig --pxl
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed
```

Running aticonfig --initial gives me this:

```
Uninitialised file found, configuring.
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0

```


So now aticonfig will at least tell me which card is active (the integrated card, as expected).  However, AMD control center refuses to open and gives me another error message:

"No AMD graphics driver is installed, or the AMD driver is not functioning properly.Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig."


Rebooting again and I'm faced with the low graphics screen :(

Any thoughts?

---

### Post by AngelGenchev on 2013-11-29
You need to reinstall the fglrx driver (I guess).  I think you could do it this way also: Download FGLRX driver package run it to generate .DEB packages, run it again to install everything, reboot - if fglrx not present - install the .DEB packages with sudo dpkg -i fglrx_*driver_name*......DEB.
But first, try to create new initial configuration (as root) with **sudo aticonfig --initial**. You need to use sudo or log in as root user for hardware configuration tasks.

---

### Post by michelmarechal on 2013-11-29
Does is works with AMD-AMD hybrid cards? I have one Radeon 4200 (onboard) and one Radeon 6370 (off-board) on my notebook, but it's almost impossible to make them work right.

Thx!

---

### Post by markswh89 on 2013-12-03
I'm sorry to get this thread dirty with a probably useless question, but there are 85 pages and I honestly doubt that the answer will be yes, so hunting down more info would only be tedious with an almost certain zero payoff.

I've read the instructions provided, and some of the pages. I was just wondering...

Is there support for Mobility Radeon HD 5xxx series now? My laptop is a HP G62-b21SL, if more in details specs are required.

---

### Post by manoj.cherukat on 2013-12-04
my laptop is HP 440G1 with haswell corei7 processor and AMD HD graphics (Mars, I think the Radeon HD 8xxxM version). using ubuntu 13.10. The drivers for AMD graphics are not installed by default. The performance is good on the Intel HD graphics. but, no matter what I do to install AMD graphics, I got a broken unity. Now I will try Nikola's method with stable driver. (13.4) working with 13.11 beta and opensource fglrx gave me broken unity. But, I'm not sure if I had installed fglrx-pxpress. Will do that and report back.
I would also like to try to install just amdccle and amdxdg-su and logout and try again as mentioned in one of the post for Sony Vaio. 
Regards,
Manoj

---

### Post by manoj.cherukat on 2013-12-04
Delighted! It was working all along, and I couldn't figure out! The reason being after rebooting and logging in, there was this black screen for some good length of time, which I thought was a crash of the unity desktop. I followed Nikola's post step by step and there was this reboot STEP after installing essentials and the same black screen with cursor came up..I waited and I get the desktop! Then I knew, that the driver would work after all, and this 'delay' in getting to the unity desktop was not because of the driver. So then here are my specs with success flag 'set' :-
Laptop : HP Probook 440G1, OS: Ubuntu 13.10, Kernel: 3.11.0-14-generic, Processor :i7-4702MQ CPU @ 2.20GHz Discrete: [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] Driver: AMD x64 for Linux Beta version 13.11. The open source driver fglrx could not detect the 8750M hardware.
I tried switching from AMD graphics to the Haswell one using Catalyst control centre (gksudo amdcccle) and reboot got me smoothly into the Intel HD graphics. I found power consumption and CPU utilization reasonable in idle mode of AMD graphics. 
HDMI works for AMD graphics, but no audio on TV (that would be my next troubleshoot) , The audio from laptop speaker only.
During a random test, laptop froze on waking from sleep, that may be a random issue, not sure have to test more. 
Nikola..much thanks to you! I was seeing this old movie "An affair to remember" your name reminded me of cary grant in the movie..may you get as much love in life as him! 
Thanks and Regards,
Manoj

---

### Post by rogier.delporte on 2013-12-06
I run Debian Wheezy and I followed the instructions on [http://wiki.cchtml.com/index.php/Debian](http://wiki.cchtml.com/index.php/Debian), however, I did not build the driver, I just got the package from the repository. Before, my system worked fine with the intel gpu, but I can't set up the configuration for switching to the igpu... my xorg.conf looks like this:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
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
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
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
```

Obviously, xorg.conf doesn't point to the igpu, but I just can't get it set up. It's also important to note that the [FONT=Arial][SIZE=2]/etc/X11/Xsession.d/10fglrx did not exist and t[SIZE=2]here's no directory [/SIZE][/SIZE][/FONT]/usr/lib/fglrx/dri aticonfig clearly isn't able to point to the propper intel driver. I use a Dell inspiron 14z 5423 amd hd7570m and intel graphics HD 4000. Any help?
[FONT=Arial][SIZE=2][FONT=Arial][/FONT][/SIZE][/FONT]

---

### Post by markswh89 on 2013-12-07
Does anyone know what this means?

```
mswh@G62LU:~/catalyst$ sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
: not foundr-installer-12-4-x86.x86_64.run: 1: ./amd-driver-installer-12-4-x86.x86_64.run: 
./amd-driver-installer-12-4-x86.x86_64.run: 2: ./amd-driver-installer-12-4-x86.x86_64.run: Syntax error: redirection unexpected
mswh@G62LU:~/catalyst$ 
```

I tried multiple ubuntu based distros, kubuntu, ubuntu 12.4 LTS, even the last one, nothings seems to help me with this. I tried to understand, it seems like a problem related to bash but I'm a newbie and I really can't wrap my head around this. I tried googling and searching the forums, but to no avail. I tried asking people I know, but they have no idea. This forum is my last hope :/

---

### Post by gnusci on 2013-12-26
This is how I fixed my problem with a Radeon 3000.

1) sudo dpkg --configure -a
2) sudo reboot
3) sudo apt-get install -f
4) sudo apt-get install --reinstall xserver-xorg-core xserver-xorg
5) sudo reboot
6) working fine now :)

---

### Post by caymus on 2013-12-26
I havent followed the developpement since years, but some years ago, xorg wasnt made, & not able to handle 2 differents brands graphic cards at the same time for DE, now maybe there are hacks to do this with xorg, while we are waiting for Weston/Wayland.

But i thing this is the same problem as Nvidia/Intel Optimus technology.

Xorg is realy a old technology, improved over decades, but at the begining, no one have started this project with multi brand graphic cards support in mind at the same time. (cannot swap form one gpu driver to another, etc, in live).

Actualy i dunno, but everyone are working on Weston/Wayland (or MIR :rolleyes:)

---

### Post by Azrael84 on 2013-12-26
I have a AMD Radeon HD 8670M+Intel hybrid under Ubuntu 12.04.3 LTS. Upon installation of Ubuntu jockey seemed to automatically install the proprietary fglrx drivers (I think version 13.10.10, at least this is module loaded in dmesg log). Most things seem to work, although if I do "modinfo fglrx" it doesn't find the module (despite "lsmod | grep fglrx" showing references to such a module, and the xorg log showing it loading). Why is this?

---

### Post by Azrael84 on 2013-12-28
> **Azrael84 said:**
> I have a AMD Radeon HD 8670M+Intel hybrid under Ubuntu 12.04.3 LTS. Upon installation of Ubuntu jockey seemed to automatically install the proprietary fglrx drivers (I think version 13.10.10, at least this is module loaded in dmesg log). Most things seem to work, although if I do "modinfo fglrx" it doesn't find the module (despite "lsmod | grep fglrx" showing references to such a module, and the xorg log showing it loading). Why is this?

I realise now that the answer to this is that the module is being "aliased":

    modprobe --resolve-alias fglrx
    fglrx_experimental_13

    grep -r fglrx /etc/modprobe.d/
    /etc/modprobe.d/fglrx.conf:# This file was installed by fglrx-experimental-13
    /etc/modprobe.d/fglrx.conf:alias fglrx fglrx_experimental_13

thus " modinfo fglrx_experimental_13" is what I should be running. Nothing to get worried about after all.

---

### Post by naught101 on 2014-01-09
So, after days of screwing around with varying instructions, I finally got my **Samsung Chronos 7** video working. This laptop uses an intel/AMD hybrid graphics:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (rev ff)
```


As described here: [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) , All I had to do was remove all fglrx related packages, remove the xorg.conf (I never had one before anyway, move yours somewhere safe if you want a backup), purge packages from other xorg PPAs, and install fglrx and fglrx-pxpress:

```
sudo apt-get purge fglrx*
sudo ppa-purge xorg-edgers
sudo rm -rf /etc/X11/xorg.conf
sudo aptitude install  fglrx fglrx-pxpress
```

After that, my AMD graphics was working for the first time (e.g. I could run glxgears, and fglrxinfo). But the AMD card was causing really glitchy graphics, so I used AMDCCLE to switch to the internal car (intel), which works well. 

The computer now runs about 10-15 degrees hotter than it did before. I'm not sure why that is - the link above mentions that this will happen for nvidia, but not for AMD, but maybe it's something similar. If anyone knows how to cool it back down on the intel GPU, or stop the glitching on the AMD GPU, let me know.

---

### Post by rikkinho on 2014-01-11
i see lot of people with problems here. if you want a good support install ubuntu 14.04 (is alpha i know but its really stable) it works just fine. enable vsync with amd discret (no tearing). i test with intel hd 3000 and amd 6770m. ubuntu 12.04 12.10 (really bad) or even 13.04 not work well or simply not work

---

### Post by -=gr!n=- on 2014-01-26
I have DELL Inspiron 3721 (certified by Canonical for Ubuntu ](*,)) and same problem with integrated Intel and discrete AMD Radeon HD 7670M.
Helped to me:
```
sudo add-apt-repository [B]ppa:ubuntu-x-swat/x-updates
[/B]sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install fglrx fglrx-pxpress
```

---

### Post by polyrhythmic on 2014-01-28
Not to derail this entire thread, but on my **Samsung Chronos 7** (Intel HD 3000, Radeon HD 6400M) I have Catalyst 13.12 running on kernel 3.13 *(edit: on Ubuntu 13.10 Saucy)* thanks to this thread:
[New Catalyst 13.12 non-beta is out!]("http://ubuntuforums.org/showthread.php?t=2194891")

Which leads to these kernel debs:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-trusty/)

And these Catalyst debs:
[http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer-updates/)

Catalyst 13.12 needs at least kernel 3.12 for its DKMS modules though, so run at your own risk.  But the drivers from the original post and in the standard repos are now pretty old.

---

### Post by Niccola on 2014-03-31
Latest AMD fglrx beta driver 14.3 beta V1.0 B22 from 12/03/2014 works wonderfully on Ubuntu 13.10 with Intel Linux Graphic Installer 1.0.4;
> Considerations:
latest AMD fglrx beta driver 14.3 v1.0 b22 is running great on my laptop HP dv6 with AMD Radeon HD6770M and Intel core i7 2nd gen and Intel HD Graphics 3000.
After its installation, system is quiet as NEVER and very cold. Performance is better based on my experience.
IMO this is the best driver EVER from AMD. I hope you all enjoy the same experience than me

Installation as following:

***OBS: Supposing that you already had uninstalled any fglrx driver from you distribution***


First, update/install Intel Linux Graphics Installer 1.0.4 for Ubuntu 13.10, you can get it [here]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux").
64 bits OSes:
```
cd ~/
wget https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb
sudo dpkg -i intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb
```
32 bits OSes:
```
cd ~/
wget https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_i386.deb
sudo dpkg -i intel-linux-graphics-installer_1.0.4-0intel1_i386.deb
```

It would be interesting adding following Intel licensing keys for driver updates validation:
```

[COLOR=#000000]wget -[/COLOR]-no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | \
sudo apt-key add -
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | \[COLOR=#000000]
sudo apt[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]key add [/COLOR][COLOR=#000000]-[/COLOR]
```
then execute Intel Linux Graphics Installer on dash or through terminal:
```
intel-linux-graphics-installer
```
Follow instructions (Begin > Install > Next...) until it finishes successfully. Rebot is necessary after it succeeds

Before installing, latest AMD fglrx driver, lets install dependencies:
```
sudo apt-get install cdbs dh-make dkms execstack dh-modaliases linux-headers-generic libqtgui4
```

x64 bits must install:
```
sudo apt-get install lib32gcc1
```

Now, lets install latest AMD fglrx 14.3 Beta v1.0 B22 and its initial settings:
download it [here]("http://support.amd.com/pt-br/download/desktop?os=Linux+x86"), or wget through following commands:
```
cd ~/
wget http://www2.ati.com/drivers/beta/Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip
unzip Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip
cd fglrx-13.35.1005/
chmod a+x amd-driver-installer-13.35.1005-x86.x86_64.run
sudo ./amd-driver-installer-13.35.1005-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Must Reboot now

if installation was successful, Ubuntu will display naturally.
I recommend next settings to configure your AMD card to run smoothly and tear-free:
```
sudo amdconfig --sync-vsync=on$ sudo amdconfig --sync-video=on
sudo amdconfig --set-pcs-u32=MCIL,PP_PhmUseDummyBackEnd,1
sudo amdconfig --set-pcs-u32=DDX,EnableTearFreeDesktop,1

```

Enjoy your system!

---

### Post by HonorableGoat on 2014-03-31
While I'm searching through this thread I wonder if someone will be able to shed some light on my problem.  I am using a Dell Inspiron 15R-5537.

I have the following result from a lspci | grep VGA:
```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M]

```

I need to use the beta drivers, which is all well and good.  I can install them and they operate fine using the discrete GPU.  If change the graphics chip using the AMD CCC to the Intel gpu and then reboot I have no problem.  However if I try and change back to the discrete GPU after this I need to go back and then uninstall and then reinstall the drivers from AMD because the gui encounters an error and needs to run in low graphics mode.

Can anyone shed some light on this?  Changing via aticonfig or the GUI produces the same result.

---

### Post by Niccola on 2014-04-19
> **HonorableGoat said:**
> While I'm searching through this thread I wonder if someone will be able to shed some light on my problem.  I am using a Dell Inspiron 15R-5537.

I have the following result from a lspci | grep VGA:
```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M]

```

I need to use the beta drivers, which is all well and good.  I can install them and they operate fine using the discrete GPU.  If change the graphics chip using the AMD CCC to the Intel gpu and then reboot I have no problem.  However if I try and change back to the discrete GPU after this I need to go back and then uninstall and then reinstall the drivers from AMD because the gui encounters an error and needs to run in low graphics mode.

Can anyone shed some light on this?  Changing via aticonfig or the GUI produces the same result.

Man, could you please share more details about your problem?

Try to switch between cards using following commands and share results...

switch to integrated graphic card:
```
sudo amdconfig --px-igpu
```

switch to discrete graphic unit:
```
sudo amdconfig --px-dgpu
```

P.S.: You don't need to reboot your system. Only log out and log in back again...

Please share your results (with more details, if possible)

---

### Post by HonorableGoat on 2014-04-21
Hey, sorry about that, you have pretty much given me the solution (kind of) below.  My issue was changing between the graphics cards on my laptop. 

I can swap using the command lines below, without restarting. 

My problem now is that if I leave it on the integrated graphics and reboot then I get put into low graphics mode and have to uninstall proprietary drivers and reinstall to get it all back up in running.  Trying to switch from the terminal while getting put into low graphics mode tells me that no supported cards are found.   Is this normal?

I don't mind having to stay in the dedicated graphics mode but it would be nice to be able to run integrated graphics without having to worry about this..  I'm still toying around with drivers and a few things.

---

### Post by Niccola on 2014-04-25
> **HonorableGoat said:**
> Hey, sorry about that, you have pretty much given me the solution (kind of) below.  My issue was changing between the graphics cards on my laptop. 

I can swap using the command lines below, without restarting. 

My problem now is that if I leave it on the integrated graphics and reboot then I get put into low graphics mode and have to uninstall proprietary drivers and reinstall to get it all back up in running.  Trying to switch from the terminal while getting put into low graphics mode tells me that no supported cards are found.   Is this normal?

I don't mind having to stay in the dedicated graphics mode but it would be nice to be able to run integrated graphics without having to worry about this..  I'm still toying around with drivers and a few things.

You're experiencing some inconsistency on Intel driver module loading. I recommend you to reinstall latest intel linux driver

---

### Post by psehouri on 2014-05-03
Hello, another user with ATI hybrid problem... many nights I have passed without sleeping, and I can't install fglrx ...
Here's my configuration : 
```

lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M] (rev ff)

```

I use Ubuntu 14.04 with kernel 3.13.0-24-generic 64 bits

I tried many differents installations, but each time, amdcccle can't be launched because  it says that my fglrx is not installed properly...

Is someone facing this problem too and how to solve it please !!!!

I don't know where to look...

I retry another time this procedure : 

```

sudo apt-get remove fglrx*

```

then,
```

sudo apt-get install fglrx fglrx-amdcccle

```

and then when I do :
```

sudo aticonfig --adapter=all --initial

```

the system says me : 
```

sudo: aticonfig: command not found

```

So, I search whereis aticonfig, and I can find it in /usr/lib/fglrx/bin/
So I execute it
```

sudo  /usr/lib/fglrx/bin/aticonfig --adapter=all --initial
Unable to open /etc/ati/control, please reinstall the driver.
/usr/lib/fglrx/bin/aticonfig: No supported adapters detected

```

If I reboot, nothing changed...


It's always the same, even if I use proprietary drivers : 
fglrx-13.35.1005
or fglrx-14.10
or fglrx-14.10.1006

/usr/lib/fglrx/bin/fglrxinfo only and always says me : 

```

display: :0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version string: 1.4 (3.0 Mesa 10.1.0)

```

---

### Post by Feby_Philip_Abraham on 2014-05-31
I recently installed Ubuntu 14.04 (fresh install, got rid of Windows entirely) and followed Niccola's instructions on Pg 86 to get AMD/Intel hybrid setup working. Upon reboot I see the login screen. But after I login I can see only the dektop background with the cursor. Seems like Unity has not loaded.

I had used the latest stable drivers from the AMD driver page for Linux x86_64. I am running the 3.13.0-27-generic kernel. I had even tried the latest beta, but no luck.

Same is the case when I install the fglrx driver from the Additional Drivers windows.

Any fixes to get Unity working.

I had already tried to login using tty1 and then installed compiz-settings-manager and tried to enable the Unity plugin, but it doesn't make any difference.

Any help would be greatly appreciated.

Thank You
Feby

---

### Post by hugoalmeida4 on 2014-06-01
I get the same as[**[COLOR=#000000] psehouri[/COLOR]**]("http://ubuntuforums.org/member.php?u=718353") 	 can you please help us?

---

### Post by arrrghhh-6 on 2014-07-13
> **hugoalmeida4 said:**
> I get the same as[**[COLOR=#000000] psehouri[/COLOR]**]("http://ubuntuforums.org/member.php?u=718353")      can you please help us?

Run

```
sudo fglrxinfo
```

To understand which card is being used.

Run

```
sudo amdconfig --px-igpu
```

To switch to the Intel card.  Should instruct you to reboot.

I have done the fglrx install per the [official Hybrid Graphics documentation](https://wiki.ubuntu.com/X/Config/HybridGraphics), but I also noticed the laptop seems to run hotter and battery life is shorter when using the Intel card...  Need to do more testing, but this seems odd to me.

---

### Post by acetech on 2014-07-20
I just got a fresh install of ubuntu gnome 14.04 on my Dell inspiron 7520 (Intel HD3000/amd HD 7730M). My graphics card details are below 

lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M] (rev ff)

by following the [cchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide")   I installed fglrx....
But when I restarted after initialising fglrx, my system was stuck in the booting page itself(the one with gnome symbol) nearly for an hour. I tried rebooting several times, but couldn't get into the login page.

So my question is ***whether the solution mentioned here by niccola on Pg.86 is specific only for ubuntu with lightdm(ubuntu 14.04) or can also be applied for gdm(ubutnu gnome 14.04)?***

The reason is becuse the wiki procedure and the mentioned solution on Pg.86 are nearly identical in all cases. But still I am not getting into gnome. 

Could you guys help me out in  clarifying my doubt, please.

---

### Post by sinan4 on 2014-08-09
> **Niccola said:**
> Latest AMD fglrx beta driver 14.3 beta V1.0 B22 from 12/03/2014 works wonderfully on Ubuntu 13.10 with Intel Linux Graphic Installer 1.0.4;


Installation as following:

***OBS: Supposing that you already had uninstalled any fglrx driver from you distribution***


First, update/install Intel Linux Graphics Installer 1.0.4 for Ubuntu 13.10, you can get it [here]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux").
64 bits OSes:
```
cd ~/
wget https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb
sudo dpkg -i intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb
```
32 bits OSes:
```
cd ~/
wget https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_i386.deb
sudo dpkg -i intel-linux-graphics-installer_1.0.4-0intel1_i386.deb
```

It would be interesting adding following Intel licensing keys for driver updates validation:
```

[COLOR=#000000]wget -[/COLOR]-no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | \
sudo apt-key add -
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | \[COLOR=#000000]
sudo apt[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]key add [/COLOR][COLOR=#000000]-[/COLOR]
```
then execute Intel Linux Graphics Installer on dash or through terminal:
```
intel-linux-graphics-installer
```
Follow instructions (Begin > Install > Next...) until it finishes successfully. Rebot is necessary after it succeeds

Before installing, latest AMD fglrx driver, lets install dependencies:
```
sudo apt-get install cdbs dh-make dkms execstack dh-modaliases linux-headers-generic libqtgui4
```

x64 bits must install:
```
sudo apt-get install lib32gcc1
```

Now, lets install latest AMD fglrx 14.3 Beta v1.0 B22 and its initial settings:
download it [here]("http://support.amd.com/pt-br/download/desktop?os=Linux+x86"), or wget through following commands:
```
cd ~/
wget http://www2.ati.com/drivers/beta/Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip
unzip Linux_AMD_Catalyst_14.3_Beta_V1.0_B22_March12_2014.zip
cd fglrx-13.35.1005/
chmod a+x amd-driver-installer-13.35.1005-x86.x86_64.run
sudo ./amd-driver-installer-13.35.1005-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb
sudo amdconfig --initial -f
```

Must Reboot now

if installation was successful, Ubuntu will display naturally.
I recommend next settings to configure your AMD card to run smoothly and tear-free:
```
sudo amdconfig --sync-vsync=on$ sudo amdconfig --sync-video=on
sudo amdconfig --set-pcs-u32=MCIL,PP_PhmUseDummyBackEnd,1
sudo amdconfig --set-pcs-u32=DDX,EnableTearFreeDesktop,1

```

Enjoy your system!
[FONT=system][SIZE=3]
[/SIZE][/FONT][FONT=tahoma][COLOR=#333333]I'm using Ubuntu 14.04 on the HP 4530s with AMD Radeon HD 6490M/Intel HD Graphics 3000 Switchable graphics.[/COLOR]
[COLOR=#333333]I have installed the first Intel driver from [here]("https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.6-0intel1_amd64.deb").[/COLOR]
[COLOR=#333333]Then I reboot so far there are no problems[/COLOR]
[COLOR=#333333]Then I install the ati driver "amd-catalyst-14-4-rev2-linux-x86-x86-64-may6.zip" and reboot.[/COLOR]
[COLOR=#333333]The system is opening low graphic mode. I also tried switch integrated Intel graphics card everything works fine. Any ideas what to do to fix this problem?[/COLOR][/FONT]

---

### Post by justin60 on 2014-08-13
I am super new to linux and am struggling with my Lenovo W500 laptop to get rid of some startup errors and to get my switchable graphics to work.

At the moment I have 
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV635/M86 [Mobility Radeon HD 3650]

Please bear with me as I am VERY new to ubuntu and do not know much other than copy and paste to terminal.

very willing to learn though!

I am on 14.04 ubuntu and trying to get this graphics issue resolved.  Thank you so much!

---

### Post by Niccola on 2014-09-08
Hey everybody getting errors (low graphic mode, etc...). Please post the following command's output:

```
[COLOR=#333333][FONT=Ubuntu]sudo lshw -C display; lsb_release -a; uname -a[/FONT][/COLOR]
```

---

### Post by HonorableGoat on 2014-09-14
Oh hi!

Has anyone run into the problem of a disappearing AMD proprietary driver when they switch back to the low power Intel GPU?  I've just switched back and all of a sudden I do not have access to the AMD Control Panel to change back.

---

### Post by Niccola on 2014-09-19
If you guys are on Ubuntu 14.04, DON'T INSTALL latest Intel Linux Graphic Driver (2014Q2)!!!

I do only recommend a fresh install of Ubuntu 14.04 and install fglrx ONLY!

That's because Intel Linux Graphic Installer Driver 2014Q2 upgrades Linux Kernel to 3.15 and Xserver to 1.15.1 and fglrx doesn't run with those versions

---

### Post by HonorableGoat on 2014-09-21
Currently using the 14.6 Beta driver as the 14.4 Official doesn't support 14.04.

To fix my disappearing driver issue I uninstalled the latest intel open source drivers and then reinstalled the 14.6 drivers.  I probably should have used apt to install fglrx, but this works for now.  The Unofficial AMD wiki didn't really mention too much about the drivers released in Trusty, although I assume the 8850M is supported as it's not a new card and was supported in previous releases.  

I still have difficulty switching between my Intel and AMD cards, so I pretty much just live with my AMD card enabled.

---

### Post by wyfsysf on 2014-10-17
> **Niccola said:**
> Hey everybody getting errors (low graphic mode, etc...). Please post the following command's output:

```
[COLOR=#333333][FONT=Ubuntu]sudo lshw -C display; lsb_release -a; uname -a[/FONT][/COLOR]
```

```
konig@konig-Lenovo-G500:~$ sudo lshw -C display; lsb_release -a; uname -a
  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d8000000-d83fffff memory:c0000000-cfffffff ioport:4000(size=64)
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
Linux konig-Lenovo-G500 3.13.0-38-generic #65-Ubuntu SMP Thu Oct 9 11:36:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


``````

sudo aticonfig --px-dgpu
sudo: aticonfig: command not found
```



my xorg.conf is empty.if &#305; paste it my backup xorg.conf &#305; m getting low graphic mode error.

---

### Post by QuimNuss on 2014-10-19
> **HonorableGoat said:**
> 
To fix my disappearing driver issue I uninstalled the latest intel open source drivers and then reinstalled the 14.6 drivers.  I probably should have used apt to install fglrx, but this works for now.  The Unofficial AMD wiki didn't really mention too much about the drivers released in Trusty, although I assume the 8850M is supported as it's not a new card and was supported in previous releases. 

Can you provide the commands to uninstall the intel driver and install the 14.6 version?

Which of the guides did you follow to get the fglrx working? Nicola's #857 ?

On sidenote, following this thread I couldn't figure out whether 5xxx is muxed or muxless and whether the BIOS is blocked as there is no switch there. Can somebody explain how to find that out? I googled around but it's unclear... most posts just say below 5xxx is probably muxed, above 5xxx is probably muxless.

Nobody posted the OP or nicola's solutions works for 5xxx so...

---

### Post by Niccola on 2014-10-24
As I expected, Ubuntu 14.10 Utopic Unitorn is running well with native fglrx. This is the set up I recommend everyone:

Fresh Installation Ubuntu Utopic Unicorn 14.10
install native fglrx:

```

sudo apt-get install fglrx-updates

```

I am working to fix some issues regarding fglrx on 14.04 LTS though

---

### Post by waqar2 on 2014-12-30
Dear All,

I have an AMD/Intel hybrid graphics setup in my Dell Laptop running Ubuntu 14.10 64-bit. Following are my VGAs:

```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series]

``` 

I have tried to use fglrx and fglrx-updates from the official Ubuntu PPA as well as downloaded it manually from AMD's website, but I am unable to start X. I see following errors in the Xorg.0.log:
```

[    49.776] (EE) Screen 1 deleted because of no matching config section.
[    51.485] (EE) fglrx(0): Failed to allocate caches, disabling RENDER acceleration
[    51.491] (EE) fglrx(0): [intel] Failed to allocate video resources for front buffer 1366x768 at depth 24
[    51.492] (EE) failed to create screen resources(EE) 

``` 

I have tried "nearly" every tutorial available to make fglrx work, but i have failed. Also Nick Andrick's PPA does not contain builds for Utopic. ANY/ALL suggestions are most welcome.

Thank you.
Waqar.

---

### Post by ivanml1992 on 2015-03-01
**Installing notebook graphics driver in ubuntu 14.04.2**

I'm using ubuntu 14.04.2 64-bit with Radeon HD 7730M in a DELL inspiron 7720, which has hybrid graphics. I was looking for a way to install the proprietary drivers on my system, but Nicolla's #857 post only talked about the drivers for desktop cards, wich came as a .run file, opposed to the .deb packages found [here]("http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064#"). I followed the method described [here]("http://askubuntu.com/questions/568443/installation-of-newest-amd-drivers-fails/568524#568524"), but couldn't install the dependencies from amd page, so I tried installing the .deb packages and dealing with the dependencies erros found as suggested in the comments. But none of the dependencies specified in AMD's release notes were required, and the only package necessary was **dkms**.

Finally, the final method that worked for me was:

Download packages for ubuntu 14.04 found in the first link.

```
sudo dpkg --add-architecture i386
sudo apt-get install lib32gcc1 libc6-i386
sudo apt-get install dkms
sudo dkms -i core-driver-package-from-amd.deb
sudo dkms -i fglrx-package-from-amd.deb
sudo dkms -i dev-package-from-amd.deb
sudo dkms -i amdcccle-package-from-amd
```

Then reboot.

The only issue I ran into with this method, was that when I turn my computer on the screen appears chopped (don't know how to describe it accurately), but closing the lid making my computer go into suspend and then waking it solves this.

Regarding the **hybrid graphics** support, amd catalyst comes with an option to swich graphis, but I didn't test that, since it was said here that 14.04.2 has problems with linux intel driver.

---

### Post by zakiur on 2015-09-01
Hi guys. 
 
My system config is 
HP Pavilion DV6 3112tx laptop with Windows 10 and Linux Mint 17.2 
AMD Radeon HD5650 shows up as Madison hybrid with Intel HD3000 Ironlake 
 
I tried installing fglrx in Ububtu 15.04 using the method on this thread. It gets installed but X goes into Low graphics mode. Default drivers work perfectly with Intel, however I am unsure as to how to switch to AMD. 
 
However here is the issue I don't care about the Intel, I need the AMD to run with steam games. I cant even switch to AMD. I'm happy with Open source drivers or the proprietary ones whichever works. Catalyst Control Centre does not load gives an error Device not found. 

[IMG]http://i61.tinypic.com/28k0zfp.png[/IMG]

**With fglrx installed details are:**

_Running glx gears with fglrx runs very slow and choppy with msg: _
> XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"

_Running aticonfig --initial gives:_ 
> PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx: 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken 
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link 
 
Using /etc/X11/xorg.conf 
Saving back-up to /etc/X11/xorg.conf.fglrx-1

_Running lshw gives:_
```
*-display                
       description: VGA compatible controller 
       product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68C1] 
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002] 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom 
       configuration: driver=radeon latency=0 
       resources: irq:44 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff 
  
*-display 
       description: VGA compatible controller 
       product: Core Processor Integrated Graphics Controller [8086:46] 
       vendor: Intel Corporation [8086] 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: msi pm vga_controller bus_master cap_list rom 
       configuration: driver=i915 latency=0 
       resources: irq:43 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)
```

_Running lspci gives: _
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller]) 
    Subsystem: Hewlett-Packard Company Device [103c:144a] 
    Flags: bus master, fast devsel, latency 0, IRQ 43 
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M] 
    Memory at b0000000 (64-bit, prefetchable) [size=256M] 
    I/O ports at 5050 [size=8] 
    Expansion ROM at <unassigned> [disabled] 
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit- 
    Capabilities: [d0] Power Management version 2 
    Capabilities: [a4] PCI Advanced Features 
    Kernel driver in use: i915 
 
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06) 
-- 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1] (prog-if 00 [VGA controller]) 
    Subsystem: Hewlett-Packard Company Mobility Radeon HD 5650 [103c:144a] 
    Flags: bus master, fast devsel, latency 0, IRQ 44 
    Memory at a0000000 (64-bit, prefetchable) [size=256M] 
    Memory at c4400000 (64-bit, non-prefetchable) [size=128K] 
    I/O ports at 4000 [size=256] 
    Expansion ROM at c4440000 [disabled] [size=128K] 
    Capabilities: [50] Power Management version 3 
    Capabilities: [58] Express Legacy Endpoint, MSI 00 
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+ 
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?> 
    Kernel driver in use: radeon
```

_Finally here's my xorg log:_
```
[    32.096] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    32.096] X Protocol Version 11, Revision 0
[    32.096] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    32.096] Current Operating System: Linux zack-HP-Pavilion-dv6-Notebook-PC 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64
[    32.096] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=08f2aed5-1049-441a-8fe0-1571d570c1b2 ro quiet splash vt.handoff=7
[    32.096] Build Date: 12 February 2015  02:49:29PM
[    32.096] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    32.096] Current version of pixman: 0.30.2
[    32.096]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.096] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.096] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep  1 06:38:42 2015
[    32.096] (==) Using config file: "/etc/X11/xorg.conf"
[    32.096] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.097] (==) ServerLayout "amd-layout"
[    32.097] (**) |-->Screen "amd-screen" (0)
[    32.097] (**) |   |-->Monitor "amd-monitor"
[    32.097] (**) |   |-->Device "amd-device"
[    32.097] (==) Automatically adding devices
[    32.097] (==) Automatically enabling devices
[    32.097] (==) Automatically adding GPU devices
[    32.097] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.097]     Entry deleted from font path.
[    32.097] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    32.097]     Entry deleted from font path.
[    32.097] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    32.097]     Entry deleted from font path.
[    32.097] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    32.097]     Entry deleted from font path.
[    32.097] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    32.097]     Entry deleted from font path.
[    32.097] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    32.097] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.097] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.097] (II) Loader magic: 0x7f2b5f6a0d40
[    32.097] (II) Module ABI versions:
[    32.097]     X.Org ANSI C Emulation: 0.4
[    32.097]     X.Org Video Driver: 15.0
[    32.097]     X.Org XInput driver : 20.0
[    32.097]     X.Org Server Extension : 8.0
[    32.097] (II) xfree86: Adding drm device (/dev/dri/card0)
[    32.098] (--) PCI:*(0:0:2:0) 8086:0046:103c:144a rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005050/8
[    32.098] (--) PCI: (0:1:0:0) 1002:68c1:103c:144a rev 0, Mem @ 0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    32.098] Initializing built-in extension Generic Event Extension
[    32.098] Initializing built-in extension SHAPE
[    32.098] Initializing built-in extension MIT-SHM
[    32.098] Initializing built-in extension XInputExtension
[    32.098] Initializing built-in extension XTEST
[    32.098] Initializing built-in extension BIG-REQUESTS
[    32.098] Initializing built-in extension SYNC
[    32.098] Initializing built-in extension XKEYBOARD
[    32.098] Initializing built-in extension XC-MISC
[    32.098] Initializing built-in extension SECURITY
[    32.098] Initializing built-in extension XINERAMA
[    32.098] Initializing built-in extension XFIXES
[    32.098] Initializing built-in extension RENDER
[    32.099] Initializing built-in extension RANDR
[    32.099] Initializing built-in extension COMPOSITE
[    32.099] Initializing built-in extension DAMAGE
[    32.099] Initializing built-in extension MIT-SCREEN-SAVER
[    32.099] Initializing built-in extension DOUBLE-BUFFER
[    32.099] Initializing built-in extension RECORD
[    32.099] Initializing built-in extension DPMS
[    32.099] Initializing built-in extension Present
[    32.099] Initializing built-in extension DRI3
[    32.099] Initializing built-in extension X-Resource
[    32.099] Initializing built-in extension XVideo
[    32.099] Initializing built-in extension XVideo-MotionCompensation
[    32.099] Initializing built-in extension SELinux
[    32.099] Initializing built-in extension XFree86-VidModeExtension
[    32.099] Initializing built-in extension XFree86-DGA
[    32.099] Initializing built-in extension XFree86-DRI
[    32.099] Initializing built-in extension DRI2
[    32.099] (II) LoadModule: "glx"
[    32.099] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    32.099] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    32.099]     compiled for 6.9.0, module version = 1.0.0
[    32.099] Loading extension GLX
[    32.099] (II) LoadModule: "fglrx"
[    32.099] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    32.119] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    32.119]     compiled for 1.4.99.906, module version = 15.20.2
[    32.119]     Module class: X.Org Video Driver
[    32.119] (II) Loading sub module "fglrxdrm"
[    32.119] (II) LoadModule: "fglrxdrm"
[    32.119] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    32.119] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    32.119]     compiled for 1.4.99.906, module version = 15.20.2
[    32.119] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[    32.119] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[    32.119] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[    32.119] (++) using VT number 8

[    32.122] (WW) Falling back to old probe method for fglrx
[    32.161] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    32.178] ukiDynamicMajor: found major device number 250
[    32.178] ukiDynamicMajor: found major device number 250
[    32.178] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    32.178] ukiOpenDevice: node name is /dev/ati/card0
[    32.178] ukiOpenDevice: open result is 9, (OK)
[    32.178] ukiOpenByBusid: ukiOpenMinor returns 9
[    32.178] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    32.180] (--) Chipset Supported AMD Graphics Processor (0x68C1) found
[    32.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    32.180] (II) fglrx: intel VGA device detected, load intel driver.
[    32.180] (II) LoadModule: "intel"
[    32.181] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    32.181] (II) Module intel: vendor="X.Org Foundation"
[    32.181]     compiled for 1.15.1, module version = 2.99.910
[    32.181]     Module class: X.Org Video Driver
[    32.181]     ABI class: X.Org Video Driver, version 15.0
[    32.181] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    32.181] (EE) this is a Muxless PX A+I platform, we doesn't supported it
[    32.181] (EE) No devices detected.
[    32.181] (==) Matched intel as autoconfigured driver 0
[    32.181] (==) Matched intel as autoconfigured driver 1
[    32.181] (==) Matched modesetting as autoconfigured driver 2
[    32.181] (==) Matched fbdev as autoconfigured driver 3
[    32.181] (==) Matched vesa as autoconfigured driver 4
[    32.181] (==) Assigned the driver to the xf86ConfigLayout
[    32.181] (II) LoadModule: "intel"
[    32.182] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    32.182] (II) Module intel: vendor="X.Org Foundation"
[    32.182]     compiled for 1.15.1, module version = 2.99.910
[    32.182]     Module class: X.Org Video Driver
[    32.182]     ABI class: X.Org Video Driver, version 15.0
[    32.182] (II) UnloadModule: "intel"
[    32.182] (II) Unloading intel
[    32.182] (II) Failed to load module "intel" (already loaded, 32555)
[    32.182] (II) LoadModule: "modesetting"
[    32.182] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.183] (II) Module modesetting: vendor="X.Org Foundation"
[    32.183]     compiled for 1.15.0, module version = 0.8.1
[    32.183]     Module class: X.Org Video Driver
[    32.183]     ABI class: X.Org Video Driver, version 15.0
[    32.183] (II) LoadModule: "fbdev"
[    32.183] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.183] (II) Module fbdev: vendor="X.Org Foundation"
[    32.183]     compiled for 1.15.0, module version = 0.4.4
[    32.183]     Module class: X.Org Video Driver
[    32.183]     ABI class: X.Org Video Driver, version 15.0
[    32.183] (II) LoadModule: "vesa"
[    32.184] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.184] (II) Module vesa: vendor="X.Org Foundation"
[    32.184]     compiled for 1.15.0, module version = 2.3.3
[    32.184]     Module class: X.Org Video Driver
[    32.184]     ABI class: X.Org Video Driver, version 15.0
[    32.184] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[    32.184] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[    32.184] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[    32.184] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    32.184] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    32.184] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    32.184] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    32.184] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    32.184] (II) FBDEV: driver for framebuffer: fbdev
[    32.184] (II) VESA: driver for VESA chipsets: vesa
[    32.184] (++) using VT number 8

[    32.185] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    32.185] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    32.185] (WW) Falling back to old probe method for fglrx
[    32.185] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    32.185] (WW) Falling back to old probe method for modesetting
[    32.185] (WW) Falling back to old probe method for fbdev
[    32.185] (WW) Falling back to old probe method for vesa
[    32.185] (EE) No devices detected.
[    32.185] (EE) 
Fatal server error:
[    32.185] (EE) no screens found(EE) 
[    32.185] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    32.185] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    32.185] (EE) 
```

Help I have tried so many methods I cant even remember. I just want to run the AMD card I don&#8217;t care what driver it is.. Any ideas or suggestions??

---

### Post by MsKK on 2015-09-03
Any news with 14.04.3 release?

---

### Post by redguy41 on 2015-12-11
Any suggestions on Ubuntu 15.10 Intel and AMD hybrid graphics? I cannot get AMD to work either with Propriertary drivers nor fglrx, I have even tried the proposed willy updates and betas.
Lenovo z51-70. AMD r9 radeon 8900 HD.

---

### Post by lbug7575 on 2016-01-14
excellent post

---

### Post by marcsabat on 2016-03-04
For the life of me I cannot seem to make the integrated Intel card work properly.
I own an HP Pavillion DV7 with and AMD Radeon HD 6730M/6770M/7690M XT (according to lspci) and integrated Intel graphics card running an Ubuntu 14.04 installation.

**I don't care for discreet graphics card: I just want the Intel card working so the cooling fan shuts de f*** up.**

The thing is I had this system working properly before but since last fglrx-updates installation Intel card won't work properly (AMD works fine but raises the temp). 

glxinfo says "Error: couldn't find RGB GLX visual or fbconfig" when switching to Intel through AMD control panel.

**Anyone knows what can I do? Is there a way to disable the AMD card without installing fglrx?**

Thanks in advance.
Ps: What a mess is this AMD/Intel/Ubuntu thing...

**UPDATE with more info:**
grep EE /var/log/Xorg.0.log shows this (when starting with Intel card enabled):
(II) LoadModule: "glx"
[     3.803] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.805] (II) Module glx: vendor="X.Org Foundation"
[     3.805]     compiled for 1.14.3, module version = 1.0.0
[     3.805]     ABI class: X.Org Server Extension, version 7.0
**[     3.805] (EE) module ABI major version (7) doesn't match the server's version (8)**
[     3.805] (II) UnloadModule: "glx"
[     3.805] (II) Unloading glx
[     3.805] (EE) Failed to load module "glx" (module requirement mismatch, 0)

Any clues? Can't seem to find the exact problem when I google it...

**UPDATE. This solved my problem:**
Purge fglrx. Then (and this was the important part for me):
sudo apt-get install --reinstall xserver-xorg-core
Then installing fglrx again.

Why reinstall xserver-xorg-core? Because this is the package that contains the file /usr/lib/xorg/modules/extensions/libglx.so.

Don't know what happened on the first place but this is what worked for me.

---

