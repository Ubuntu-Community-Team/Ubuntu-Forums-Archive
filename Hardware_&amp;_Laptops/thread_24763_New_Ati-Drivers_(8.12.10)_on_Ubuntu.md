---
title: "New Ati-Drivers (8.12.10) on Ubuntu?"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by MadMan2k on 2005-04-08
Did anyone actually manage to install them on Ubuntu?

This is how far I got:
- downloaded the drivers
```

$ ~/fakeroot alien fglrx_6_8_0-8.12.10-1.i386.rpm
# dpkg -i --force-overwrite fglrx-6-8-0_8.12.10-2_i386.deb
# cd /lib/modules/fglrx/build_mod/
# ./make.sh
# cd ..
# ./make_install.sh

```
- restarted the X-Server

```

$ export LIBGL_DEBUG=verbose
$ fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Addition:
```

$ cat /var/log/Xorg.0.log | grep EE
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

```

linux-iamge-2.6.10-5-k7 / linux-headers-2.6.10-5-k7 installed

it would be kind, if the official module maintainer could say how he made it  :-)

---

### Post by ubuntu-geek on 2005-04-08
There will be an official package out shortly :)

---

### Post by MadMan2k on 2005-04-08
[QUOTE=ubuntu-geek]There will be an official package out shortly :)[/QUOTE]
that is good news, but Im still curious  :wink:

---

### Post by donar73 on 2005-04-08
No problems here, they are running fine! :-)

---

### Post by MadMan2k on 2005-04-08
Could you give me some infos about your system Kernel/ Graphics
and describe how you installed the driver?

---

### Post by donar73 on 2005-04-09
CPU: Athlon XP 2800+
Board: MSI K7N2 Delta ILSR (NForce2 Ultra)
RAM: 512 MB
Graphics: Radeon 9500

I installed the driver following this dircetions (which I found here in another thread):

1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm 
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig

Note: **before** you start check if you have installed the linux-headers for your kernel and gcc (Synaptic)

---

### Post by buellman on 2005-04-09
hi!

does transset and so on work with the new driver?

greets. buellman

---

### Post by bobmitch on 2005-04-09
[QUOTE=buellman]hi!

does transset and so on work with the new driver?

greets. buellman[/QUOTE]


There is no mention of composite compatibility in the changelog, so I`d guess not.  It`s the one thing I`m waiting for the drivers to support. :)

---

### Post by buellman on 2005-04-09
[QUOTE=bobmitch]There is no mention of composite compatibility in the changelog, so I`d guess not.  It`s the one thing I`m waiting for the drivers to support. :)[/QUOTE]

me too :-)

greets. buellman

---

### Post by MadMan2k on 2005-04-09
[QUOTE=donar73]
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME[/QUOTE]
danke! :) that was it - after I uninstalled the linux-restricted-modules, it worked for me too

---

### Post by crvendramini on 2005-04-09
[QUOTE=donar73]CPU: Athlon XP 2800+
Board: MSI K7N2 Delta ILSR (NForce2 Ultra)
RAM: 512 MB
Graphics: Radeon 9500

I installed the driver following this dircetions (which I found here in another thread):

1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm 
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig

Note: **before** you start check if you have installed the linux-headers for your kernel and gcc (Synaptic)[/QUOTE]

Works like a charm...  :grin: 

thanks

---

### Post by emuman on 2005-04-09
I use Linux 2.6.11 and had to apply two patches to use version 8.12.10 (see attachment).

---

### Post by hamster2k3 on 2005-04-09
Hey guys, I haven't tried these drivers, but tried some previous drivers, and was getting hang.

Any of you had these "hangs" in X ? And is it solve now ?

I was getting them while using 3D stuff or some extensive video work..

Thanks!

---

### Post by donar73 on 2005-04-10
> Works like a charm...

thanks

You shouldn't thank me, as I wrote, this solution is not from me, the original poster was **delltony** who posted this on the 4th of March 2005: 
> Re: How do I intall ATI drivers for Xorg in hoary?
dude the x.org driver in universe is crap if you ask me. for one it has a bug in that when you run fglrxconfig it wants to generate a xf86config-4 file instead of the xorg.conf file and also the frame rate will be around 300fps where with the new driver from ati its more like 5000fps and runs well with open gl. With that being said here is what you do but you wil probably have some issues if you upgrade with metacity so you will have to temp uninstall the fglrx (the ati one) and then put the xorg one back nd then upgrade then turn around and put the fglrx (the ati one) back in place. at least thats how i got around the errors with meta city.

so here goes the quick and simple down and dirty way of how i got it to work and works well i might add:

1. Download official driver .rpm from the ATI website.
2. Remove fglrx packages using synaptic.
3. Shut down gnome. [ From terminal: sudo /etc/init.d/gdm stop ]
4. cd to where you downloaded the driver rpm file.
5. sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
6. sudo mv /lib/modules/YOURKERNELVERSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. dpkg --force-overwrite fglrx_6_8_0-8.10.19-1.i386.deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. modprobe fglrx
13. fglrxconfig

I only posted his solution here because in my eyes it's the easiest way to get the most actual ATI-drivers runnig... So thanks to **delltony**!  :-)

---

### Post by bobmitch on 2005-04-10
[QUOTE=donar73]You shouldn't thank me, as I wrote, this solution is not from me, the original poster was **delltony** who posted this on the 4th of March 2005: 


I only posted his solution here because in my eyes it's the easiest way to get the most actual ATI-drivers runnig... So thanks to **delltony**!  :-)[/QUOTE]

I wonder where delltony got it from?

[HINT](http://www.ubuntuforums.org/showpost.php?p=73422&postcount=4) 


;)

---

### Post by donar73 on 2005-04-10
> I wonder where delltony got it from?

HINT



ooops...  O:)

---

### Post by bobmitch on 2005-04-10
[QUOTE=donar73]ooops...  O:)[/QUOTE]

Where did I get it from...?  

:D

---

### Post by allgood on 2005-04-11
Hi,

I did all the things that donar73 asked and every thing is looking good.Installing the new drivers got me like 500 or more FPS but when I do fglrxinfo it tells me that:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5010 (X4.3.0-8.12.10)

and reading the first post I realized that it supposed to use mesa instead could be the problem?Anyone could tell me? [-o<

---

### Post by mangar on 2005-04-11
will the new official package be in the hoary repository?
if not, then where ?

thanks in advance

---

### Post by bobmitch on 2005-04-11
[QUOTE=allgood]Hi,

I did all the things that donar73 asked and every thing is looking good.Installing the new drivers got me like 500 or more FPS but when I do fglrxinfo it tells me that:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5010 (X4.3.0-8.12.10)

and reading the first post I realized that it supposed to use mesa instead could be the problem?Anyone could tell me? [-o<[/QUOTE]

Your output seems fine - the opengl vendor string being ATI signifies that you have hardware 3d acceleration enabled now.  This is good. :)
Mesa opengl is a software opengl implementation, so you really *don`t* want to see this. 

Hope this helps. :D

---

### Post by wbeck85 on 2005-04-12
and when you say that, do you mean it will be available via apt-get? and which repository? eta?

thanks

---

### Post by daniels on 2005-04-12
8.12.10 is in Breezy already (first upload to Breezy, was done days ago but the archive hasn't been processing since Hoary's release).

[http://lists.ubuntu.com/archives/breezy-changes/2005-April/000000.html](http://lists.ubuntu.com/archives/breezy-changes/2005-April/000000.html)

---

### Post by Gunnar on 2005-04-13
Hi all
I have severe problems with my ATI card, in fact it only works in "vesa" mode so all help is appreciated.
Hardware: AMD64 4000+, 2GB main memory, ATI X800 (Hightech Excalibur ATI X800XL Turbo ICE-Q 256M (what a name!)) on an ABIT AN8 mobo (NVIDIA4 chipset, PCIe).
Following the excellent descriptions given here I get as far as "sudo sh make-install.sh" at what time this snip is reported:
-creating symlink
-recreating module dependency list
-trying a sample load of the kernel module
fglrx: module license ....
[fglrx] Maximum ....
[fglrx:firegl_init] *ERROR* Device not found
FATAL:Error inserting fglrx (/lib...):No such device    failed.
<end of that>
lspci reports <snip>
0000:05:00.0 VGA compatible controller: ATI Tech... Unknown device
0000:05:00.1 Display controller: ATI Tech... Unknown device
<end of that>
Regards
Gunnar

---

### Post by jr_G-man on 2005-04-13
I was able to get mine working with the following step:

-Use 'apt-get' to get the normal Ubuntu ATI driver package
-Download the 'official' driver from [www.ati.com](www.ati.com)
-Extract only the 'fglrxconfig' file somewhere on your machine
-Run the 'fglrxconfig' file and it generates a valid xorg.conf file
-Restart X

---

### Post by zAo on 2005-04-13
[QUOTE=Gunnar]Hi all
I have severe problems with my ATI card, in fact it only works in "vesa" mode so all help is appreciated.
Hardware: AMD64 4000+, 2GB main memory, ATI X800 (Hightech Excalibur ATI X800XL Turbo ICE-Q 256M (what a name!)) on an ABIT AN8 mobo (NVIDIA4 chipset, PCIe).
Following the excellent descriptions given here I get as far as "sudo sh make-install.sh" at what time this snip is reported:
-creating symlink
-recreating module dependency list
-trying a sample load of the kernel module
fglrx: module license ....
[fglrx] Maximum ....
[fglrx:firegl_init] *ERROR* Device not found
FATAL:Error inserting fglrx (/lib...):No such device    failed.
<end of that>
lspci reports <snip>
0000:05:00.0 VGA compatible controller: ATI Tech... Unknown device
0000:05:00.1 Display controller: ATI Tech... Unknown device
<end of that>
Regards
Gunnar[/QUOTE]

Try to unload the old driver and load the new one manually, or just reboot. The module was made succesfully so

---

### Post by jozi on 2005-06-02
I'm having major problems trying to get a ati x800xl to work :(

A friend spend about 3hrs trying to get me up and running trough ssh.
After getting everything setup so he could get the drivers of the net he got a error.
I think he got the following:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

Im using the 5.04 version of ubuntu in 64bit flavor and the latest 64bit ati drivers.

I hope someone can help and ill tell my mate to keep an eye on this thread.

Jozi

EDIT: checked version and edited the post

---

### Post by atilasendil on 2005-07-15
Respect !

this is my second post on the forums
and I feel more and more respect for the people here ...

thanks to the guide here I could finally play tuxracer after about 6 or 7 years ...
(couldnot find drivers for my video card then lol)

well ...

almost sunrise time here
and I feel soooo happy
right stevie ?

sorry if this is useless post for most but just wanted to share my gratitude and happiness

---

### Post by brim4brim on 2005-07-15
[QUOTE=jr_G-man]I was able to get mine working with the following step:

-Use 'apt-get' to get the normal Ubuntu ATI driver package
-Download the 'official' driver from [www.ati.com](www.ati.com)
-Extract only the 'fglrxconfig' file somewhere on your machine
-Run the 'fglrxconfig' file and it generates a valid xorg.conf file
-Restart X[/QUOTE]

I followed these instructions before and the fglrxconfig setup an invalid xorg.conf file so when I restarted I was just seeing a blank screen.  Had to use ctrl+alt+F2 to get the console to halt.

Anyone know how to set it up on an X600 mobility card?

If anyone did it successfully can they post how the hell they got it to work please!

---

### Post by canavan on 2005-07-16
[QUOTE=brim4brim]I followed these instructions before and the fglrxconfig setup an invalid xorg.conf file so when I restarted I was just seeing a blank screen.  Had to use ctrl+alt+F2 to get the console to halt.

Anyone know how to set it up on an X600 mobility card?

If anyone did it successfully can they post how the hell they got it to work please![/QUOTE]

The following works for my current X600 notebook, some X300 based notebooks had to use "None,Auto", others only worked with "None,LVDS"

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
        Driver          "fglrx"
        #Option "MonitorLayout" "None,Auto"
        Option "MonitorLayout" "None,LVDS"
        #Option "DestktopSetup" "0x00000100"
        BusID           "PCI:1:0:0"
EndSection
```

---

### Post by mayfer on 2005-08-17
i've been spending hours on trying to get this driver to work now.. i've had similar problems in both fedora 3 and mandrake 10.2 before. now the same thing in ubuntu, argh!

anyway, i'm trying to follow the steps donar has written. however, when i go to /lib/modules/fglrx/build_mod/ and do sh make.sh, i get this message:

```
# sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

```

i tried it with both the synaptic packages and the official ati driver from ati.com.

keeps telling me "incompatible kernel module detected", i'm guessing this is caused by me not being able to generate an ati module?
```
$ cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

---

### Post by mayfer on 2005-08-20
i'm feeling really dumb right now..
i just realized that the wrong kernel version linux-headers were installed.
fixed it, nevermind. if anybody else has the same problem, i'll tell what i did in more detail.

---

