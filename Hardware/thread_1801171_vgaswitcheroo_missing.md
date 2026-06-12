---
title: "vgaswitcheroo missing"
date: 2011-07-10
forum: Hardware
---

### Post by Aggie135 on 2011-07-10
this is my first foray into the ubuntu forums, so please go easy on me =P

i have been trying to get switchable graphics to work on my new laptop, which i understand has limited support from linux, and ive been having some difficulty

my understanding is that the main tool for switching graphics is switcheroo, but this does not appear to be installed on my machine. 
i tried following instructions on
[http://ubuntuforums.org/archive/index.php/t-1751726.html](http://ubuntuforums.org/archive/index.php/t-1751726.html)
but when i ran 
grep -i switcheroo /boot/config-2.6.*
in terminal, i got nothing (and manually looking through my config file, there is no switcheroo)

and when i type
ls -l /sys/kernel/debug/vgaswitcheroo/switch

i get:
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

help?

---

### Post by Aggie135 on 2011-07-10
UPDATE

i followed the instructions at 
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
which is a very useful resource, and now i am able to see a menu after running switch_between_cards.sh, and can choose between discrete and dedicated graphics. however there is no check next to the card currently running, no notification in the corner like his screenshots show, and not even a ficker in the screen, which makes me think still something is wrong
also the vgaswitcheroo folder in debug is still missing
:(

---

### Post by AION2009 on 2011-07-11
What part actually did bring the vgaswitcheroo folder to the /sys/kernel/debug/ ?

Because I'm missing it too and I'm not too keen on running scripts which (to my understanding) need the folder to work. And they are not meant to create / enable the folder?

---

### Post by nlion on 2011-10-19
> **Aggie135 said:**
> UPDATE

i followed the instructions at 
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
which is a very useful resource, and now i am able to see a menu after running switch_between_cards.sh, and can choose between discrete and dedicated graphics. however there is no check next to the card currently running, no notification in the corner like his screenshots show, and not even a ficker in the screen, which makes me think still something is wrong
also the vgaswitcheroo folder in debug is still missing
:(

I'm having this same issue. Any help here?

If I run ```
locate switcheroo
``` all that I get back is
```
/usr/src/linux-headers-3.0.0-12/include/linux/vga_switcheroo.h
/usr/src/linux-headers-3.0.0-12-generic-pae/include/config/vga/switcheroo.h
/usr/src/linux-headers-3.0.0-12-generic-pae/include/linux/vga_switcheroo.h

```

---

### Post by sevenearths on 2011-12-28
I'm having exactly the same problem (I did install and the subsequently remove the fglrx driver). Anyone come up with a solution for this yet (apart from a reinstall)

---

### Post by markackerman8@gmail.com on 2012-01-17
Please help a newbie with switchable graphics nightmare!
Basics,
intel i7-2630 with integrated graphics, amd/ati HD 6850m.
I have been trying to get this functional for weeks.  At this point the Open source ati driver seems to have been installed (like everyone elses - enabled and in use).  But aticonfig - initial says no adapter found !!!
ack@Arawn:~$ aticonfig - initial
aticonfig: No supported adapters detected

and 
ack@Arawn:~$ grep -i switcheroo /boot/config-3.0.*
/boot/config-3.0.0-12-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.0.0-14-generic:CONFIG_VGA_SWITCHEROO=y
 shows the kenels has vgaswitcharoo 

- great but - no file ..
ack@Arawn:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

please help a newbie that would be very happy to just have the discrete power hungry card working and not the power-saving wimp intel-integrated card.

I could really use some direction ... thanks :)

Mark

---

### Post by BillaSong on 2012-02-07
> **markackerman8@gmail.com said:**
> Please help a newbie with switchable graphics nightmare!
Basics,
intel i7-2630 with integrated graphics, amd/ati HD 6850m.
I have been trying to get this functional for weeks.  At this point the Open source ati driver seems to have been installed (like everyone elses - enabled and in use).  But aticonfig - initial says no adapter found !!!
ack@Arawn:~$ aticonfig - initial
aticonfig: No supported adapters detected

and 
ack@Arawn:~$ grep -i switcheroo /boot/config-3.0.*
/boot/config-3.0.0-12-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.0.0-14-generic:CONFIG_VGA_SWITCHEROO=y
 shows the kenels has vgaswitcharoo 

- great but - no file ..
ack@Arawn:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

please help a newbie that would be very happy to just have the discrete power hungry card working and not the power-saving wimp intel-integrated card.

I could really use some direction ... thanks :)

Mark

I'm newbie in ubuntu, but I was and still am researching about switchable graphics. Try using vga_switcheroo. And as I've read in most posts you must disable open-source ATI driver, for switcheroo to work. And here you can see how to make it work with scripts:

[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
[B][U]
And my problem[/U][/B] :(:

I hope it helps, cuz' I have problem as some others with missing vgaswitcheroo directory (/sys/kernel/debug/vgaswitcheroo/switch). So I hope that someone can help, cuz' I'm loosing my mind with it =/... I've tried:

- 2x reinstalling ubuntu (once with 64 bit and once with 32 bit)
- Adding to /etc/rc.local few codes:

1. code was:
```

chown "username" /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```2. code was (guiding by 3 post in [http://ubuntuforums.org/showthread.php?t=1896445&highlight=vgaswitcheroo](http://ubuntuforums.org/showthread.php?t=1896445&highlight=vgaswitcheroo)):
```

modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```- Installing open-source driver (later uninstalling it)
- Installing official ATI CCC 12.1.
- Installing Ubuntu Control Center and using switcheroo inside it

Nothing helped, there is no switcheroo directory and no script or program helps =/.
With running code:
```
grep -i switcheroo /boot/config-2.6.*
```I get:
```
CONFIG_VGA_[COLOR=Red]SWITCHEROO[/COLOR]=y
```And with running code:
```
locate switcheroo
```I get:
```
/usr/src/linux-headers-2.6.35-32/include/linux/vga_switcheroo.h
/usr/src/linux-headers-2.6.35-32-generic-pae/include/config/vga/switcheroo.h
/usr/src/linux-headers-2.6.35-32-generic-pae/include/linux/vga_switcheroo.h

```
I've even tried to mount directory:
```
mount -t debugfs none /sys/kernel/debug
``` And I got that it is already mounted.
But if I run:
```
sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
```I get:
```
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```Oh yes now I have Ubuntu 10.10 with kernel 2.6.35.32 on Lenovo G770, with ATI HD6650M and Intel HD3000.

Please and thank you for any help, Billa

---

### Post by BillaSong on 2012-02-07
Hey all... I've done it :D... I've installed again ATI CC and with CC switching graphics between ATI and Intel works perfectly =)... You can download CC on link:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Thank you anyway, Billa

---

### Post by markackerman8@gmail.com on 2012-02-17
Well Still No Real Luck - Aaarghhhhh

thanks for the replies though

The last thing in my many attempts was to reinstall ubuntu to install the amd/ati driver thru additionhal drivers (post release) as I read that this was the only one to work with vgaswitcheroo.  Oddly after the reinstall of Ubuntu 11.10 and no updates I saw the switch file (/sys/kernel/debug/vgaswitcheroo/switch) for my first time  (Ubuntu 3.0.0-12) (no additional driver yet).  Then I tried to install the ati driver no luck  - errors so I thought I should update Ubuntu - restart and try again.  After the restart my kernel was at 3.0.0-16 from 12, and no /sys/kernel/debug/vgaswitcheroo folder at all arghh going backwards now pls pls help.
Mark
-----------------

here is a sumary of some of the things I have tried to date:
For 2 months and over 100 hours, I have been trying to get my new HP Envy 2195ca working with the Swichable dedicated AMD/ATI HD 6850m graphics card and not the embedded Intel hd3000 low end card,  with no success.  I think perhaps I am missing something basic and don't know what it is???   Here is what I have tried (part thereof) :
&#8227; Installed using additional drivers - seemingly successfully - ie. says enabled, and active and green dot, but
• running ATI's CCC gives:
&#8728; There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
&#8728; No AMD graphics driver is installed, or the AMD driver is not functioning properly.
&#8728; Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
&#8227; Installed from the amd website:    amd-driver-installer-12-1-x86.x86_64.run, (previous version over the past 2 months as well)
• created the 3 debian packages seemingly successfully and installed all three:
&#8728; fglrx_8.930-0ubuntu1_amd64.deb,    plus 2 similarly named ones
• For the first time using 12.1 today I seemingly successfully ran:
&#8728; aticonfig --initial -f, with no errors  BUTTTTTT
&#8227; after a reboot just a black screen with a few tiny white dots flicking around
• and safe mode works fine
• I can get back into Ubuntu Normal mode by deleting 
&#8728; /etc/X11/xorg.conf (perhaps I just need the right file contents for switchable graphics)
&#8227; Again PLEASE HELP. and Thanks in advance
&#8227; Here is some additional information 
• lspci -nn | grep VGA
&#8728; 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
&#8728; 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Broadway [ATI Mobility Radeon HD 6800 Series] [1002:68a8]
• Recommended configuration for X.org
&#8728; No configuration is necessary for ATI driver in the modern versions of Ubuntu. You can safely take away your xorg.conf and your computer will run fine. 
•     To see if your driver uses KMS (Kernel Mode Setting), run command 
&#8728; ack@Arawn:~$ dmesg | grep drm
[    9.153946] [drm] Initialized drm 1.1.0 20060810
[    9.400960] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.402250] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.402255] [drm] Driver supports precise vblank timestamp query.
[   13.040646] fbcon: inteldrmfb (fb0) is primary device
[   13.040932] fb0: inteldrmfb frame buffer device
[   13.040935] drm: registered panic notifier
[   13.049332] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0


• vgaswitcheroo 
&#8728; Never has worked and probably because there is NEVER a file called
&#8227; /sys/kernel/debug/vgaswitcheroo/switch
&#8227; root@Arawn:/home/ack# echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
• bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; root@Arawn:/home/ack# grep -i switcheroo /boot/config-3.0.*
&#8227; /boot/config-3.0.0-16-generic:CONFIG_VGA_SWITCHEROO=y
&#8728; To test if vga_switcheroo is enabled, look for the switch file: 
&#8227; ls -l /sys/kernel/debug/vgaswitcheroo/switch
• ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; never once had this switch file with or without open source/fglrx/ or no driver at all
&#8227; If you are not using the open-source radeon driver (or the nouveau driver in case of nvidia hardware), there won't be a /sys/kernel/debug/vgaswitcheroo/switch file. 
• hmmmmmm  tried a reinstall as stated at the top of this post which left em with no /vgaswitcheroo FOLDER or /switch file

HEELppppPPPPP PLEASE
Mark

---

### Post by jonnyboysmithy on 2012-03-04
Try this on ubuntu 12.04 beta. It worked for me:[http://ubuntuforums.org/showthread.php?t=1906803&highlight=hybrid+graphics+fix](http://ubuntuforums.org/showthread.php?t=1906803&highlight=hybrid+graphics+fix)

I suspect the vgaswitcheroo missing is because ati drivers were/are still there.
Anyway try it on a liveusb.

---

