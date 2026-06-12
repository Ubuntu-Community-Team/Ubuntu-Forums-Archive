---
title: "HOWTO: HP Compaq 6720s and ubuntu 7.10 Gutsy Gibbon : a (hopefully) complete guide"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by slayer^_^ on 2008-01-05
_**Update**_: this page refers now ONLY to 7.10 Gutsy Gibbon. If you're searching for infos about 8.04 LTS Hardy Heron. I've made a new dedicated guide. You can reach it here [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) .

First of all, don't go crazy with this laptop, there are just **three** major issues to take care of!

_**0) Ubuntu eats your laptop hard disk**_
_**1) Ethernet card not working** _
_**2) Wireless card not working** _
_**3) 3D Desktop effects not available - troubles with video playback - wrong allocation of video memory (updated)** _
_**[4) Closing the lid makes your system freeze**_

Once done, you can fully enjoy your laptop !!!

_**0) Ubuntu eats your hard disk**_

As reported on launchpad, **_this is not an Ubuntu bug_**. Ubuntu respects the hard disk producers' directives, the problem is that with these directives, when using the battery, the hard disk executes a mount cycle per minute; if the average life of a hard disk is 600.000 cycles, you can see where the problem is, i.e. reduced life. 
However we can fix it in a very simple way...

1) Create a file named 99-hdd-spin-fix.sh

2) Open it and put these strings: 
> 
#!/bin/sh and hdparm -B 255 /dev/sda

3) Save the file in these folders:

> /etc/acpi/suspend.d/

> /etc/acpi/resume.d/

> /etc/acpi/start.d/ 

all done!

_**1) ]Ethernet card not working** _
it appears to be an ubuntu bug (i had no problems with the wired with fedora 8 for example) but there are two ways to quickly solve this trouble:

**Simple Way** : Boot with the pci=noacpi parameter:

howto : open a terminal window and input the command

```
sudo gedit /boot/grub/menu.lst
```

However you may change "gedit" with "kwrite" if you are using kubuntu, with "mousepad" if you are using xubuntu, or "nano" if you wanna edit the file using the terminal (or you have no graphic interface - for exaple if you installed a server edition);

Once the text file has shown up, locate this section:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a089c41b-e47e-444e-b389-e5a23ed610ee ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Add the "pci=noacpi" option to the kernel string, so it has to result like this:


```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a089c41b-e47e-444e-b389-e5a23ed610ee ro quiet splash pci=noacpi
```

Now reboot, ethernet should work !!!

_remember_ : you have to add the "pci=noacpi" option every time you update the kernel or install certain packages from synaptic or apt-get (or simply check if the "pci=noacpi" option is present if ethernet is not working)

**Hard Way** : To solve _once for all_ the ethernet trouble under ubuntu you have to upgrade the firmware of your ethernet device (or the biod of your motherboard), but you need windows to do this operation (however if you search in the ubuntu forums you'll find a way to do this operation under ubuntu too)


_**2) Wireless card not working**_

A common trouble of the broadcom wireless devices under many (if not all) linux distribution. There are _two_ (again) ways to solve this trouble, one using restricted drivers named _bcm43xx-fwcutter_ and one using _ndiswrapper_. 

I'll explain only the _ndiswrapper_ way because many users state that fwcutter allows you to use your wireless device only up to 11 Mbps, ndiswrapper works great instead:

First of all you got to blacklist the existing non-working driver for your wireless device. open a terinal window and type:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist bcm43xx" to the bottom of the text file, save it and close it;

Now download the XP drivers from the HP homepage (or from your driver cd):

[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

If your laptop is a slightly different model download the right driver package, the rest of the procedure is the same:

Then you got to extract this archive with "cabextract"

Install the package "cabextract" from the Synaptic Package Manager or input in a terminal window:

```
sudo apt-get install cabextract
```

Now install the package "ndiswrapper-utils" from the Synaptic Package Manager or input in a terminal window:

```
sudo apt-get install ndiswrapper-utils
```

Then open a terminal window and locate the folder in which you download the driver file, for example:

```
cd /home/yourusername/
```

Be sure that it's the right folder with the "ls" terminal command, the sp34152.exe file should appear. Then:

```
cabextract -d /home/yourusername/arandomname sp34152
```

Then enter the folder in which you extracted the driver package:

```
cd /home/yourusername/arandomname
```

By entering the command "ls" you should see that the bcmwl5.inf file is present, then install it:

```
sudo ndiswrapper -i bcmwl5.inf
```

Check if everything has gone fine:

```
sudo ndiswrapper -l
```

Should tell you somthing like "driver installed, device present"

Now let's write the ndiswrapper configuration file

```
sudo depmod -a
```

Then

```
sudo modprobe ndiswrapper
```

Then

```
sudo ndiswrapper -m
```

Now add the ndiswrapper modules by opening a terminal window and typing:

```
sudo gedit /etc/modules
```

And adding "ndiswrapper" to the bottom of this file.

Now REBOOT , everything should work fine ;)

_**3D Desktop effects not available - troubles with video playback**_
Sorry, your video card has troubles with compiz in ubuntu and its driver is currently blacklisted. This conflict will probably be fixed in the Ubuntu 8.04 Hardy Hoary. You _can_ , however, enable most of the 3d-desktop effects and the video playback un-blacklisting the video driver (but you cannot post about bugs related to this unblacklisting, you do this operation at your own risk - i didn't experience any problems yet, however...)

Open a terminal window and input this code:

```
sudo mkdir /.config/compiz
```

Then

```
sudo gedit /.config/compiz/compiz-manager
```

Past this string into the text file:

```
SKIP_CHECKS=yes
```

Save it and close it.

Now let's enable the video playback option. Open a terminal and input this code:

```
gstreamer-properties
```

Click the Video tab. change the Default Output Plugin: value to "X Window System (No Xv)".

Now let's enable the 3d desktop effects:

Go to System > Preferences > Appearance. Choose the Visual Effects tab and enable your desired option. Log out and log in for the changes to take effect.

You can also enable additional Compiz-Fusion effects by installing the settings manager.

```
sudo apt-get install compizconfig-settings-manager
```

Go to System > Preferences > Advanced Desktop Effects Settings to play with cool Compiz effects. 

**DISCLAIMER**  _i took the info about the video card configuration here:_ 

[http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

**(thank you guys)**

**_Now let's correct the allocation of the video memory_** (_**!!!NEW!!!**_)

_**CORRECT ALLOCATION OF VIDEO MEMORY**_

The "intel" driver is not able to do a correct allocation of the video memory. But we can solve manually the problem:

In terminal:

> sudo gedit /etc/X11/xorg.conf 

Then add the underlined options in the text file

```
[...]

Section "Device" 
          Identifier "Videocard0" 
          Driver "intel" 
          _Option "LinearAlloc" "6144"_
          _Option "CacheLines" "agoodnumberyoudecide"_
          _Option "AperTexSize" "agoodnumberyoudecide" _
[...]
```

From the intel website:

_Option "CacheLines" "integer"_ Decreasing this amount leaves more for 3D textures. Increasing it can improve 2D performance at the expense of 3D performance. The default used for a specific configuration can be found by exam- ining the Xorg log file


_Option "AperTexSize" "integer"_ Default: 32768


I suggest these settings: Cachelines = 768 ; AperTexSize = 131072

However you decide those values! Still pasting from the intel website:

Option "CacheLines" "integer"
This allows the user to change the amount of graphics memory
used for 2D acceleration and video when XAA acceleration is
enabled. Decreasing this amount leaves more for 3D textures.
Increasing it can improve 2D performance at the expense of 3D
performance. Default: depends on the resolution, depth, and
available video memory. The driver attempts to allocate space
for at 3 screenfuls of pixmaps plus an HD-sized XV video. The
default used for a specific configuration can be found by exam-
ining the Xorg log file. 

Option "AperTexSize" "integer"
Give the size in kiB of the AGP aperture area that is reserved
for the DRM memory manager present in i915 drm from version
1.7.0 and upwards, and that is used with the 3D driver in Mesa
from version 6.5.2 and upwards. If the size is set too high to
make room for pre-allocated VideoRam, the driver will try to
reduce it automatically. If you use only older Mesa or DRM ver-
sions, you may set this value to zero, and activate the legacy
texture pool (see Option "Legacy3D" ). If you run 3D programs
with large texture memory requirements, you might gain some per-
formance by increasing this value. Default: 32768. 

_**4) Closing the lid makes your system freeze**_

Try this command in the terminal:

```
sudo gedit /etc/rc.local
```

Put this line in the text file:

```
echo 1 > /proc/acpi/video/*/DOS
```

Save, close, reboot and try. It should work!

any problems? :)

---

### Post by AlesUbu123 on 2008-01-05
Thank you for your excellent post! 

I have some questions:

[LIST=1]
[*]Did you experience that laptop freezes after closing the lid of 6720s? I have solved this by putting a line
```
echo 1 > /proc/acpi/video/*/DOS
```
into /etc/rc.local
[*]Have you tried hibernation? It does not work for me. 
[*]After waking the computer from suspend, the screen backlight does not always turn on. Sometimes it helps if I try increasing the brightness with shortcut keys (Fn+F9). Sometimes it just doesn't wake up and I have to reboot.
[*]How is your battery holding on? In XP the battery lasts for almost 5 hrs and in Gutsy 3 and some more minutes with all possible hacks enabled.:( (MAJOR SETBACK FOR ME!)
[*]Some CompizFusion effects do not work as they should, for example Shift Switcher and Blur windows and Rain effect...
[/LIST]

Hope we save all the issues with Gutsy on HP 6720s in the future.
I was really pleased how it worked almost perfectly out of the box for me...:)

10x

---

### Post by slayer^_^ on 2008-01-06
Thank you for your excellent post!

Thank you for your really interesting post, here are my answers:

   > 1. Did you experience kernel panics after closing the lid of 6720s? I have solved this according to: [http://ubuntuforums.org/showthread.php?t=587390&page=3](http://ubuntuforums.org/showthread.php?t=587390&page=3)
   > 2. Have you tried hibernation? It does not work for me.
   >  3. After waking the computer from suspend, the screen backlight does not always turn on. Sometimes it helps if I try increasing the brightness with shortcut keys (Fn+F9). Sometimes it just doesn't wake up and I have to reboot.

err... at the time i never experiences these problems (perhaps because i never closed the lid with ubuntu working, never tried suspend or hybernation too - just don't need them). I'll do some checks and, if i experience the problem and can solve it i'll update my guide with the tips you suggested. thanx for letting me know it!

   > 4. How is your battery holding on? In XP the battery lasts for almost 5 hrs and in Gutsy 3 and some more minutes with all possible hacks enabled. (MAJOR SETBACK FOR ME!)

I experience the same lasting time. I can't sayanything about it because i guess it's a reasonable lasting time for the use i do with it! however the question is: what's the lasting time with Windows Vista? :D

  >  5. Some CompizFusion effects do not work as they should, for example Shift Switcher and Blur windows and Rain effect...

It's because, as I wrote in the guide, the video card driver is blacklisted. C'mon, we all hope it'll be fixed in the Hoary Hedgeog release :)

Thanx again for your patience and time.
I can just hope that every ubuntu user owner of this laptop posts his experience here to help other owners. :popcorn:

---

### Post by AlesUbu123 on 2008-01-07
Hey I hope that together we learn to configure Ubuntu to run perfectly on this great laptop. :)

> I experience the same lasting time. I can't sayanything about it because i guess it's a reasonable lasting time for the use i do with it! however the question is: what's the lasting time with Windows Vista?
I would really like to know your opinion on this: do you think that XP and Vista could overestimate the length of battery life (5hrs). I don't understand why ubuntu runs quiter and   starts fan rarely than Windows, yet the battery life is still significantly reduced. I would be really happy if someone could explain this to me? Those 5 hours of battery life in XP are really tempting, but I can't stand Windows and I have Ubuntu nicely configured so I would't like switching to XP when on batt.

> It's because, as I wrote in the guide, the video card driver is blacklisted.
My compiz runs ok, but the bugs I mentioned in previous post still cause my Shift switcher to stop showing windows after a second of starting the effect (to fix this I had to uncheck "Show reflections" in the Compiz Configuration Manger) and the Focus Blur option in Blur Windows effect causes unfocused windows to get blank, etc. Probably the intel driver is still a bit buggy.

+bug no 6. Another thing I noticed is that after waking from suspend, one of my thermal sensors (number 5) changes from 20&#730;C to 50&#730;C causing my fan to run all the time. Suspend and hibernate functions are obviously still not completely implemented in Gutsy. 

> C'mon, we all hope it'll be fixed in the Hoary Hedgeog release
I soooo could't agree more. Please Ubuntu team: start fixing the existant bugs instead of adding so many new features!!

Regards!!
Ales

---

### Post by slayer^_^ on 2008-01-09
> Power and Battery
Battery
	6-cell (47 WHr) Lithium-Ion battery
Power supply
	External 65-watt AC adapter, 6-foot (1.8-meter) power cord included. Total length including external AC adapter is 12 feet (3.66 meter).

err i really think that xp overstimates the autonomy of this kind of battery... xp is a quite old system, it can't even calculate exactly (in real-time) the time needed to copy a file from a compact disc...

---

### Post by samstre on 2008-01-09
hi! I've also got the 6720s (GR644ET) and I've also experienced the lousy battery time in gutsy...

currently i have no windows installed... 3 hrs are good with me but there is a another thing thats bugging me: When I'm closeing my display lid, the screen turns black when the lid is still open (something like 20°) and turns on again if completely closed.

My Ethernet-card just works with the pci=noacpi setting in menu.lst
(although I've upgraded my BIOS to F.07) <- I've also tried the Versions F.03 and F.05!

Another problem is that my laptop freezes from time to time... (i was not able to find out the reason)



I'm sorry for my bad English... It is obviously not my mother tongue :)

---

### Post by AlesUbu123 on 2008-01-10
> My Ethernet-card just works with the pci=noacpi setting in menu.lst
(although I've upgraded my BIOS to F.07) <- I've also tried the Versions F.03 and F.05!

Now that you have upgraded to BIOS F.07 - have you tried removing the pci=noacpi setting from the kernel line? (with this BIOS upgrade, my NIC works just normally even without the noacpi parameter). Correct me if I am worng - I am thinking this could potentially affect your lid closure problems? Though I am not sure. :)

> Another problem is that my laptop freezes from time to time... (i was not able to find out the reason)
Does this happen under any special circumstances? 
Have you tried booting from a Live CD after such a freeze and checking /var/log/messages from there?

Have a nice day!

---

### Post by samstre on 2008-01-10
thank you for your incredible fast answer!

yes! I've tried to remove the pci=noacpi from the menu.lst...but when i do that, the card doesn't get any IP from a DHCP server, and if i set the IP manually, I can't ping any computers within the network...

yeah! you are right! the F.07 BIOS should fix the lid problem, but it doesn't :(
but i think thats an ubuntu problem, because as far as i know, ubuntu doesn't use the BIOS ACPI functions, ubuntu tries to implement it by itself! <- i could see that because, when i boot, or when I'm in the BIOS the screen turns black, when the lid is closed! :lolflag: but not when i have booted the kernel!

can anybody do me a favor and try to install the **iasl** package from the universe repository. (it's the intel acpi compiler/decompiler)

change the directory to Desktop (because the files are saved into the current directory, so you can delete them afterwards)
```
cd /home/<user>/Desktop/
```

then get the DSDT table into a file:
```
sudo cat /proc/acpi/dsdt > dsdt.dat
```

then disassemble the dsdt.dat by the iasl
```
iasl -d dsdt.dat
```

and after that recompile the dsdt.dsl file, created by the decompiler
```
iasl -sa dsdt.dsl
```

now the compiler shows ACPI errors and warning if there are any!
you should get the: ```
Warning  1103 -        Possible operator timeout is ignored ^
```

is that right?!?! please confirm if so...

know to my freeze problem: i was not able to find out any special circumstances! maybe it happens more often, when my battery is low!
i could not say that definitely because the laptop only freezed 10 times or so since i have him. (i installed ubuntu 4 months ago)

today i'll try other BIOS(es?) <- i don't know the plural of BIOS :) with the LIVE-CD...

last but not least i wanna thank you all for that wonderful thread! it's by far the best out there!
thank you all!


have a nice day to!

---

### Post by slayer^_^ on 2008-01-10
the pci=noacpi option allows the ethernet to work but perhaps affects something else too... that's why it's suggested to upgrade the bios rather than keep using that option indefinitely.

however someone suggests to totally disable the acpi option with this option :

```
acpi=off pci=noacpi
```

add this to the kernel line, give it a try and let us know :)

best regards

---

### Post by samstre on 2008-01-10
with the code line ```
acpi=off pci=noacpi
``` the lid closing-bug is gone... 
but i also got another freeze ... but i could not boot the system from a live cd because i didn't got one... so i'm currently downloading one :)

what should/could i do now? any further recommends?

best regards samstre :)

---

### Post by AlesUbu123 on 2008-01-11
Hi samstre,
when did the computer freeze? When you were booting or when you closed the laptop's lid?

Regards!

---

### Post by samstre on 2008-01-11
when i closed my laptop lid...

i think the problem with my lid is all about the /etc/acpi/ scripts!
first of all it looks like the script /etc/acpi/events/lidbtn is never used!

if changed the /etc/acpi/events/lidbtd from:

```
# /etc/acpi/events/lidbtn/
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

to:

```
# /etc/acpi/events/lidbtn/
# Called when the user closes or opens the lid

event=button[ /]lid
#action=/etc/acpi/lid.sh
action=/home/samstre/Desktop/lid.sh
```

here my own lid.sh:

```
echo "Lid Closed/Opened"
```

but Lid Closed/Opened is never echoed on any tty or terminal... :(


and even if the lid.sh would be executed it wouldn't work...
the original lid.sh something thats called CheckPolicy()...

. /usr/share/acpi-support/policy-funcs

```
if [ `CheckPolicy` == 0 ]; then exit; fi
```

and CheckPolicy() alwas return 0.... :(

```
grep closed /proc/acpi/button/lid/*state
```
returns the right value... state: closed if closed and nothing if opened... so the rest of the script should work...

but why the hell is that script never executed???

btw: can anybody please send me his /etc/acpi/lid.sh and his /usr/share/acpi-support/screenblank

thanks in advance
samstre

---

### Post by samstre on 2008-01-11
sry ... doublepost :)

---

### Post by AlesUbu123 on 2008-01-11
Hey,
I am currently in Fedora and I have not been able to find the files you requested on my system. 
My computer was also freezing when I closed the lid, but I have fixed this using [http://ubuntuforums.org/showthread.php?t=587390&page=3](http://ubuntuforums.org/showthread.php?t=587390&page=3)
> 
Hello,
I'm using Debian unstable + 2.6.23 kernel from [http://kernel-archive.buildserver.ne...n/l/linux-2.6/](http://kernel-archive.buildserver.ne...n/l/linux-2.6/) on HP 6710b and have the same problem - when I close the lid the laptop freezes. In my case removing acpid didn't work. When using boot parameter acpi=off the problem was gone. I found out that video.ko acpi module was causing the problem.

In [http://git.kernel.org/?p=linux/kerne...cdcbf7cb1ce4ed](http://git.kernel.org/?p=linux/kerne...cdcbf7cb1ce4ed) I found the solution for my problem:

# echo 1 > /proc/acpi/video/*/DOS

Could you please check if it works for you too.

Hey - in your previous post you mentioned sth about a fault in the DSDT tables. Do you think this could affect the function of our 6720s? 

Regards!

---

### Post by samstre on 2008-01-11
Yeah there is a waring in the DSDT table (warnings can be ignored). I've fixed the waring according to [http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix)
^^
sorry i only found the german version :)

i've changed my dsdt and updated it... now i got no warnings, no errors...

but still no change...

i've tried the acpi=off option, but still no change... :(

---

### Post by AlesUbu123 on 2008-01-13
Hey samstre! 
I have tried debugging the DSDT tables and I also got this:

> dsdt.dsl  8740:                         Wait (\_SB.C1AB, 0x10)
Warning  1103 -        Possible operator timeout is ignored ^ 

ASL Input:  dsdt.dsl - 16390 lines, 587425 bytes, 7570 keywords
AML Output: dsdt.aml - 71710 bytes 1211 named objects 6359 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 2583 Optimizations

What do you think that means? 
I am in fact having some problems with the thermal zones setting on my computer, they are different every time I boot my computer. Sometimes my fan starts working at temperatures of 34 &#730;C and somtimes at temperatures of 49 &#730;C. 
Even dmesg shows that thermal_zones are not consistent!! Check this out:

At one time I get this from dmesg
> Jan 13 12:08:53 localhost kernel: ACPI: Thermal Zone [TZ0] (34 C)
Jan 13 12:08:53 localhost kernel: ACPI: Thermal Zone [TZ1] (30 C)
Jan 13 12:08:53 localhost kernel: ACPI: Thermal Zone [TZ3] (22 C)
Jan 13 12:08:53 localhost kernel: ACPI: Thermal Zone [TZ4] (20 C)
Jan 13 12:08:53 localhost kernel: ACPI: Thermal Zone [TZ5] (74 C)

And then after rebooting I can get totally different thermal_zones!?
> Jan 13 14:17:09 localhost kernel: ACPI: Thermal Zone [TZ0] (48 C)
Jan 13 14:17:09 localhost kernel: ACPI: Thermal Zone [TZ1] (48 C)
Jan 13 14:17:09 localhost kernel: ACPI: Thermal Zone [TZ3] (43 C)
Jan 13 14:17:09 localhost kernel: ACPI: Thermal Zone [TZ4] (20 C)
Jan 13 14:17:09 localhost kernel: ACPI: Thermal Zone [TZ5] (49 C)

1. Do you think that DSDT compiler warninga could contribute to this?? 
2. Have you noted this inconsistencies in thermal_zones  (fans turned being on at different temperatures, sometimes the computer is really quiet and after rebooting fans are on almost instantly and it is louder, and I have noted that after using suspend fans are also turned on very soon)?
3. Has fixing DSDT tables resolved this?
4. Could you possibly post the output of this command?
> dmesg | grep Thermal
5. How did you fix the DSDT table? :)

I am really intrigued now :D And pretty much out of any clues what could be wrong.... :(

Regards, Ales

---

### Post by samstre on 2008-01-15
i'm sorry that i've been offline for such a long time!

1. i'm not quite shure... they say that compiler warnings can be ignored...
2. i haven't noted inconsistencies (because i haven't looked for any :) )
3. i've fixed the dsdt table right after installing so i can't say anything... but i'll test within the next few days
4.  ```
[    3.488000] ACPI: Thermal Zone [TZ0] (53 C)
[    3.492000] ACPI: Thermal Zone [TZ1] (54 C)
[    3.496000] ACPI: Thermal Zone [TZ3] (46 C)
[    3.504000] ACPI: Thermal Zone [TZ4] (20 C)
[    3.508000] ACPI: Thermal Zone [TZ5] (41 C)
```
5. that is quite easy...

1. install the iasl package
2. read the current dsdt table and save it into a file ```
sudo cat /proc/acpi/dsdt > dsdt.dat
```
3. please make a copy of your dsdt.dat, so you can restore it, if you do something wrong!! ```
cp dsdt.dat /home/<user>/save_dsdt.dat
```
4. disassemble your dsdt.dat ```
iasl -d dsdt.dat
``` this will create the dsdt.dsl file
5. compile your dsdt.dsl ```
iasl -sa dsdt.dsl
``` you will see a warning ```
save_dsdt.dsl  8740:                         Wait (\_SB.C1AB, 0x10)
Warning  1103 -             Possible operator timeout is ignored ^ 

```
6. open the dsdt.dsl, got to line 8740 and change the value 0x10 to 0xFFFF
7. save the file!
8. recompile the file ```
iasl -sa dsdt.dsl
``` now there should be no warnings at all
9. copy the file to the initramfs-tools dir ```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
```
10. update the dsdt ```
sudo update-initramfs -u
```
11. now reboot :)

---

### Post by AlesUbu123 on 2008-01-16
Hey samstre!

Thank you for your kind and detailed reply. 

I'll try it as soon I come home!

Regards

EDIT
I tried fixing the tables - and it worked, but sadly this has not changed the thermal management much on my laptop. Still hoping to find something to make it more quieter.

---

### Post by slayer^_^ on 2008-02-01
hey, seems this 'lil guide has had a good success !! 
I guess that this means it has been useful :KS

so... any suggestions to update the first post of the guide? any stable fixes available? just let me know, ok? anticipate thanx for your patience and time...

p.s. many people contacted me asking how to make the wireless card work on fedora 8 (i know this would be an OT)... i just gave it a try but i haven't been able to make it work in a stable way (just with ndiswrapper restarting the network and the networkmanager and dispatcher many times. any suggestions?

---

### Post by flibble42 on 2008-02-03
Just for info - I had no trouble installing the drivers + detecting hw for wireless using ndiswrapper but to actually enable it I had to change the bios settings to set wireless on + bluetooth off by default and turn wireless switching off (BIOS ver F.05). After boot I then had to press the wireless button to turn the light from orange -> blue to actually turn on wireless. 
   
Great guide btw!

---

### Post by slayer^_^ on 2008-02-04
uhm... this sounds quite new! i had troubles like this with other distro i tried (like fedora 8...  hadn't been able to use fwcutter or ndiswrapper on that distro in a stable way).

thak you for posting your experience ;)

---

### Post by amlan_cse on 2008-03-26
[SIZE="4"][FONT="Trebuchet MS"]Slayer u rock... too good[/FONT][/SIZE]

---

### Post by =E= on 2008-03-27
Hi there.  We are considering buying this laptop to dual boot Ubuntu and XP.  Would you 6720 owners recommend buying it given the problems it has or should we consider something else?

Thanks,
=E=

---

### Post by nico_h on 2008-04-10
so i've been trying to install gutsy on a 6720s for a friend of mine. i managed to convince her trying ubuntu to be able watching videos. she didn't manage to solve this problem under vista though installing the required w m player & i didn't want to spend time with it =;. then  the installation of gutsy worked !  i've managed to fix the 3 main problems quickly  thanks to this how to and then to install the right packages so she can watch these videos now. so she can do something with ubuntu she couldn't do as easily (and not at all, so far) with vista \\:D/

moreover, the closing lid problem didn't show up.

a problem's still here though, the laptop freeezes quite often. if it happens again, i'll try to get the var/log messages, but i'm quite desperate about it after reading this post... :-?

i didn't check the power management problem which is not very important so far, and which i don't expect to fix soon since i already fought hard to fix it on my laptop (dapper)... unsuccessfully (it should last 2 hours, lasted 50 minutes which i brought to 1 hour 15 minutes with all possible patches  :-k).

there was a weird problem too, but it *always* shows up when installing linux (like faunos on usb stick, ubuntu studio on my laptop, ubuntu gutsy on the laptop of my friend and so on). i have absolutely no idea why this bug *always* shows up. it makes the internet connexion working very weird (pings everything OK but firefox waits for the websites to answer instead of displaying them ; fix it with editing /etc/systctl.conf and adding the line net.ipv4.tcp_rmem = 4096 87380 174760 (no idea what this fix does, but it works))

and the last problem is that she's going away back home tomorrow and that i won't be able to help her after that. and well, if i don't fix the freezes, she will probably keep ubuntu to watch videos and not much more (if it doesn't freeze too often while watching videos). such a shame !!!!!!!! well.............. i've tried...

to give an answer to =E=, i would rather try with another laptop. and tell HP/Compaq it's such a shame not buying this one because it's not easy enough to install gnu/linux on it !!

---

### Post by =E= on 2008-04-10
Well, we actually bought this laptop and now are successfully running 7.10 and XP (dual boot).  

After partitioning with Partition Magic, we inserted the Alternate CD and proceeded to install.  However, the install failed, giving us a blank screen after just a few seconds.  We tried again with the "install to command line" option and that worked.  After we got the command line, we typed "sudo apt-get install ubuntu-desktop" and the installation went fine after that.

The wi-fi card was automagically detected (restricted drivers module worked fine) and there were no network card problems either.  Most of the function buttons seem to work.  3D worked fine (compiz) after we removed the video card blacklist check (in slayer's first post on this thread).

However, the screen does not turn off when the lid is closed and there are probably suspend/hibernate issues.  The volume control is not as smooth as windows (either really loud or not loud at all).  I doubt the modem works under linux either, but I have not tested it.  Those were the only issues we had (not many at all).

Interestingly, out of the box the touchpad on Linux worked better than on XP!  I had to download a newer driver from HP for XP for the scroll to work.

I don't know why I didn't have these issues that people are talking about here.  If you are having problems, the only thing I suggest is try the Alternate CD instead of the normal one when installing.

Hope this helps.
=E=

---

### Post by slayer^_^ on 2008-04-10
well, this laptop rocks with ubuntu_ gutsy_, i would reccomend it, but:

1 - it's better to use wireless, the pci=acpi tends to make everything slower (ndiswrapper works great, surely better than native drivers)

2 - be sure to give an amount of swap space at least equal to the ram you got (remember that the video card has shared ram).

I can tell ya i tried Hardy in these days and everything works really great... except the wireless (there's a strange ndiswrapper issue though...). I'll manage to work on it, promised ;)

Have a nice day :D

---

### Post by nico_h on 2008-04-11
well thanks for your very quick answers ; time was unfortunately too short to give a try to the alternate CD.

i did give as much space in swap as there is in ram (1 GB).

slayer, i don't understand your first point (better to use wireless / pci=acpi ??)

but well, maybe she'll come back in july or september, so i can install hardy on her computer then !

thanks again for quick answers !

---

### Post by slayer^_^ on 2008-04-15
i was saying that it's better to connect with a wireless method in gutsy, that's because the wired method requests you to use the "pci=noacpi" boot option, that usually tends to make the system work a lttle slower. 


You can update the bios to the last version and get the wired connection work without the pci=noacpi command, but it's obvious that it is a more dangerous option.

The wired connection works well in hardy Heron Beta without a bios flashing and without the "pci=noacpi" boot-option.

As i said before, the only problem with Hardy is the wireless... as soon as i find a method to get it to work as well as in gutsy with ndiswrapper i'll post something about it.

Stay tuned !

---

### Post by Draxx on 2008-04-16
Hi,
Thank you slayer^_^, it's very useful guide.
I've upgraded BIOS to F09 but still no success with wireless connection without pci=noacpi, however it works out of the box on Hardy Heron Beta.  =D>
Now i'm waiting for full release and...  good bye Vista \\:D/

Regards,

Draxx

---

### Post by dixon on 2008-04-16
Does hibernation and suspend work in Hardy?

---

### Post by Draxx on 2008-04-19
Yes, suspend and hibernation works.

---

### Post by slayer^_^ on 2008-04-20
perhaps you wanted to say wired? wireless isn't influenced by upgrading the bios.

however, anyone managed to get ndiswrapper working in hardy with this laptop? i would say it's still better than the native module (but a fix has been committed).

i had very little time to give it a try (this laptop isn't mine)...

just let me know and stay tuned ;)

---

### Post by tech_junky on 2008-04-21
I wonder if you could help - i have read your threads and found them very useful, and wondered if you would be so kind to help me understand ubuntu desktop and some problems it produces.

I have recently bought a hp 6720s laptop and found it to be very nice - as soon as i bought it a killed Vista as it is so bad.  I wanted to learn linux and thought this would be the best place to start.  Ubuntu.

1. The wireless worked straight out of the box on both the live CD and on install.
2. The ethernet didn't - found the problem powersaving mode would wrongly turn off the adaptor - turned off the saving mode on the adaptor.
3. Xorg would wrongly configured display so everything would look all fuzzy.  Fixed that by reloading it and inserting the proper settings.

All ok - however, i have now a serious problem the desktop completely freezes... and the only way out is the on/off button. this happens most of time now and is very irritating and  I'm sure this is going to finish it off if it continues.  Is there anyway i can find the problem?

being a complete linux newbe i'm at a loss where to start.  

Cheers Adrian

---

### Post by slayer^_^ on 2008-04-22
may i have a quick list of your hardware? what's odd is that wireless works out of the box.

let me know

---

### Post by Voland on 2008-04-22
Have anyone tried to check Compiz in Hardy?

---

### Post by slayer^_^ on 2008-04-22
compiz in hardy works like a charm ;)

as i said before, i tried hardy for a bit (i don't own this laptop, so i couldn't try it all teh time) and everything seemed to work, except for the wireless device...

as soon as i will have the time to get the wireless device working i'll post a walkthrough here ;)

bye!

---

### Post by tech_junky on 2008-04-22
adrian@adrian-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
adrian@adrian-laptop:~

Does this help? sorry i'm new to the commands too.

---

### Post by tehMalone on 2008-04-22
Hi, I'm a total newbie at Ubuntu. I found this guide, and did the first thing, the one with the blacklist, and it worked! (had problem with wireless - bcm43xx)
It is to be said that I am not on the model you describe, but on a HP pavilion dv6510eo, but since the first part worked, i tried to go on. I successfully installed the driver, using a downloaded Vista-driver for my broadcom wirelees card (might be the problem ?).

Now when I try to start, it f**ks up: [ndiswrapper (load_wrap_driver:118 ): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'.

Then I can't do anything, and this is both in recovery mode and normal mode. I can write, but nothing happens.
any1 know what to do now ?? Please be specific, I'm a newbie.


EDIT: just found out that ctrl-alt-delete made me able to use it a terminal-like way.

---

### Post by tehMalone on 2008-04-22
Now, I managed to enter ubuntu with my live-cd, so I think I need to undo the changes made by the guide, any1 know how to do that ?

---

### Post by tech_junky on 2008-04-23
ubuntu gusty looks like it is working - ok but it is still freezing.  What i'm normally doing is browsing on the internet using firefox reading techical notes for work.  Then it just freezes. Clock stops etc... only get out is on/off!

Is the there anything i can update to stop this happening - please see my hardware list above.  Please please me with my 6720s GR665ET.

---

### Post by slayer^_^ on 2008-04-24
tehmalone : you must not use VISTA drivers for ndiswrapper, only windows xp ones... vista drivers won't work ;)

tech_junky : have you tried another OS? just to exclude a hardware or a bios set up problem... many times is dust in the fan ;) tell me if weendoos xp ecs-pi works...

---

### Post by tech_junky on 2008-05-04
HI Slayer,

Sorry i have not been about this last week as i have been busy at work and can't face going on the computer when i get home.

Last friday i installed ubuntu 8.04 - and the freezing problem has been completely fixed.  However, i did experience a locking again but just once. :)

One thing that has mucked up after the install is Amarok with my Ipod.  At the moment i can't think of what the problem is.  gtkpod sees the ipod but amarok doesn't.

Slayer - you mentioned the fan... my fan functioning fine.

---

### Post by madmaxo on 2008-05-04
Great tutorial, thanks! Just one little thing: The web address link to the driver no longer works. I had to hunt around a bit, but found where you can now download the Broadcom XP driver from:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3442832&prodNameId=3442833&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-55703-1]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3442832&prodNameId=3442833&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-55703-1")

Hope that helps!

---

### Post by slayer^_^ on 2008-05-04
fixed links.

Thank You!

---

### Post by sroland81 on 2008-06-01
Hello, i'm running Hardy for amd64, in a Presario F730US with BCM94311 mini-pci (rev 02) and i make wireless work with the firmware thing and the compat-wireless. The thing is that i see in "dmesg" a lot of lines like this:

[ 6845.854087] printk: 154 messages suppressed.
[ 6845.854092] b43-phy0 ERROR: PHY transmission error
[ 6845.845149] b43-phy0 ERROR: PHY transmission error
[ 6845.854143] b43-phy0 ERROR: PHY transmission error
[ 6845.854161] b43-phy0 ERROR: PHY transmission error
[ 6845.845214] b43-phy0 ERROR: PHY transmission error
[ 6845.854203] b43-phy0 ERROR: PHY transmission error
[ 6845.845257] b43-phy0 ERROR: PHY transmission error
[ 6845.854247] b43-phy0 ERROR: PHY transmission error
[ 6845.854264] b43-phy0 ERROR: PHY transmission error
[ 6845.845318] b43-phy0 ERROR: PHY transmission error
[ 7026.788659] printk: 163 messages suppressed.

and i started to search the cause, because the machine used to hang me every 30 min with no keyboard and mouse response... i thaught that maybe was the wireless... and really don't know what this errors are. Then i find out that the kernel 2.6.24 does not support the rev02 hardware, and i found this post about a kernel patch.... but following this instructions i got this in a terminal:

santiago@quaoar:/usr/src/linux$ sudo patch -p1 <  patch_2.6.24_for_4311_2
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -up -X linux-2.6/Documentation/dontdiff linux-2.6/drivers/ssb/b43_pci_bridge.c wireless-2.6/drivers/ssb/b43_pci_bridge.c
|--- linux-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 15:13:44.000000000 -0600
|+++ wireless-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 18:43:49.000000000 -0600
--------------------------
File to patch: 

And here i'm lost... i don't want to be a cowboy because the kernel is not a toy... need help, please.

Thanks Santiago

---

### Post by slayer^_^ on 2008-06-02
this is the gutsy gibbon page for this laptop (i am currently removing the hardy tips).

you can reach the hardy page of this guide here:

[http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

you'll find that kernel-patching method has been updated and now works fine.

let me know your experience (in that other post :) )

have a nice day ;)

---

### Post by vivekrocks on 2008-06-10
This is exactly wht I needed!
thanx a lot :)

---

### Post by slayer^_^ on 2008-06-11
you're welcome ;)

---

