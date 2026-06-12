---
title: "intuos pro medium not recognised ubuntu 12.04"
date: 2013-10-07
forum: Hardware
---

### Post by indeable on 2013-10-07
hey guys i just got a new wacom tablet thinking that that dandy little wacom settings button in system settings would work. 
anyway it wont recognise it. i checked a few other threads and got further confused. any help i can get would be appreciated.

thanks :D

also i keep trying to install a package recomended on the software center but keep getting a conflict error.
The following packages have unmet dependencies:
 xserver-xorg-input-wacom:i386 : Depends: xorg-input-abi-16:i386
                                 Depends: xserver-xorg-core:i386 (>= 2:1.10.99.901)

---

### Post by Favux on 2013-10-08
Hi indeable,

Welcome to Ubuntu forums!


You're in luck.  Support for your model was just added to the recently released drivers:
input-wacom-0.19.0, see [http://sourceforge.net/p/linuxwacom/mailman/message/31485674/](http://sourceforge.net/p/linuxwacom/mailman/message/31485674/)
xf86-input-wacom-0.23.0, see [http://sourceforge.net/p/linuxwacom/mailman/message/31455616/](http://sourceforge.net/p/linuxwacom/mailman/message/31455616/)

So you'll need to update them:
[https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)
[https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

Step by step instructions on compiling the drivers in Ubuntu is available on the [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").  However you'll need to update the driver version numbers since I haven't done that yet.

Could you do me a favor and show me what the Product ID is for that tablet?  Enter in a terminal the command **lsusb** and post the output line that contains **Wacom** in it.

---

### Post by squiregrand on 2013-10-09
Hi Favux and Indeable,

I too, have purchased a Intuos Pro and it isn't recognised at all. I was excited when you said that Support had been added :D. I followed the BambooPT HOW TO, it was pretty hard for me to follow, but I got there, but have still got no recognition. I tried again, but still nothing.  

I get no out put in terminal from teh following ```
lsmod | grep wacom
```
my lsusb gives me "Bus 006 Device 002: ID 056a:0315 Wacom Co., Ltd "

Any Ideas? 

Will the Drivers likely be included in 13.10? Because I'm happy to wait for that. 

Thanks in advance.

---

### Post by Favux on 2013-10-09
Hi squiregrand,

Sounds like you are new to compiling.  In that case nice work getting through the HOW TO's steps.  :)  If the output after you enter the commands didn't spit back any errors, and they aren't real subtle, then you might still be OK.

For whatever reason some systems don't auto-load the Wacom kernel driver/module wacom.ko.  You can "force" it to load by adding it to the modules file in /etc.  To edit modules run this command:
```
gksudo gedit /etc/modules
```
and then add **wacom** to the bottom of the list of modules/drivers that should be in there.  There are usually at least 2 or 3.  Reboot and with luck the Intuos Pro will be working and you should see wacom in **lsmod**.

Thanks for lsusb output.  Since the Pros are in the current release of xf86-input-wacom my guess is 13.10 will have them.  But that is just the X driver and you also need the kernel driver.  I doubt 13.10's kernel will have Pro support.  I'm not sure when support for the Pro's was submitted to the kernel's linux-input mailing list but it was very recent.  So it has to be after 13.10's kernel freeze.  Ubuntu's kernel team would probably have to backport Pro support from that kernel to 13.10's kernel, which is unlikely.  My guess is you'll still have to compile input-wacom to get a wacom.ko that supports the Pro in 13.10.

---

### Post by squiregrand on 2013-10-10
I haven't done much compiling, even though I've used Ubuntu for a bout 3 years now. Thanks for the encouragement. The only error I noticed was when I did the Frankensever patch, but that's becuase I used the wrong one the first time. Got it to work with the appropriate output the second time. 

I added **wacom** to the modules list but still no joy. I can see it in the **lsmod** now, which is good, but the system settings tab for wacom still has no recognition, and I'm getting no response from the cursor. Perhaps I did the compiling wrong, is it worth going back through the process on both drivers again? What do you reckon?

Thanks again.

---

### Post by Favux on 2013-10-10
The System Settings Wacom configuration applet won't show your tablet because its older version of libwacom doesn't have the tablet's data file in it.  So ignore that and instead concentrate on whether or not the pointer arrow tracks the pen.

I'd start with concentrating on input-wacom's wacom.ko and make sure that was being compiled correctly.  As a first step I'd make sure that it was the freshly compiled wacom.ko auto-loading.  Check in /lib/modules/`uname -r`/kernel/drivers/input/tablet/ for the wacom.ko.  Using Properties get the date and see if it is the same date as when you compiled the new one.  The `uname -r` returns the kernel version your system is using and you can get that by running **uname -r** in a terminal.  If it is the same date then I'd try recompiling, checking the outputs for errors.  After making sure I was using the 0.19.0 version of input-wacom.


Edit:  I should mention folks are just starting to attempt to get these new models working in linux.  So you are a bit of a pioneer.  That means I can't rule out a glitch that might be tripping you up until a few more folks report on their mileage.

---

### Post by squiregrand on 2013-10-12
Thanks Favux. 

The Date is corect so I'll try to compile again. See how I go...

---

### Post by squiregrand on 2013-10-12
I've recompiled the wacom.ko drivers but still no sucess. Do I have to redo the steps for xf86-input-wacom driver as well?

Thanks Again.

---

### Post by squiregrand on 2013-10-12
Alright, I've done the whole proces through again but still no cigar. I think that i didn't have any errors, but around the 'make' comands I was a bit unsure of what was happening, so not sure if there could have been an eror or not. 

on the b) section, when I got to 'make' it didn't do much, I think it said something like > nothing to make for 'all' not sure if that was supposed to happen, I don't have the exact text as I rebooted. can get it if that's helpful. 

Thanks for all your help Favux, I think maybe this is one of those Glitches I'm going to have to wait on. Let me know if you have any thoughts.

---

### Post by Favux on 2013-10-12
Well shoot.  Sounds like it should be working.

Just to be sure your release of Ubuntu is Precise (12.04) correct?

I checked input-wacom0.19.0 and the newly compiled wacom.ko for 12.04 should be showing up in the 2.6.38 folder.  In other words the code for support in the 12.04 3.2 kernel is there.
> Do I have to redo the steps for xf86-input-wacom driver as well?
Not totally sure.  The Pen might work through the generic stylus fall back in the X driver.  It could be without the Pro models added to wcmValidateDevice.c the X driver won't recognize them.  You do need the updated xf86-input-wacom for the correct resolution, and model number in wcmUSB.c.
> nothing to make for 'all' 
Don't worry that isn't an error it is just reporting a make file result.  Errors tend to be summarized towards the end of the output and begin with **ERROR**.  If you saved the output I could take a quick look.

Looks like we may need someone else trying to compile support for the Pro and see if we can figure it out.  Josep Febrer on the linuxwacom-discuss mailing list reported success but he didn't offer details.  Don't even know his Distro or release.

---

### Post by squiregrand on 2013-10-14
I am on 12.04 LTS, that's right. 

I redid the steps for xf86-input-wacom driver again anyway but with no luck. 

It does seem like I didn't get any errors....Guess I'm waiting. I might try compile on one of my other PC's with 12.04, just to see how I go. 

thanks Again. I'll keep checking incase there's new info comes up. Serves me right for buying such a new product, it only just barely works in windows as well.

---

### Post by AussiePozzie on 2013-10-19
Just joined the intuos pro club, ...gotten the digitizer yesterday.

I have tried several times to get the xf86 driver installed, but the upon the ./configure command, it tells me that doxygen is missing and xorg-xserver is missing.

So, ...I installed the doxygen suite, some 650 MB, reran the ./configure command again, it found doxygen alright, but was still reporting xorg-server missing.

Googling got me to the xorg-server site, I downloaded the file, extracted it, again after ./configure, the error that it was missing some library, ...can't remember the name anymore.

Googling for it, I couldn't find anything.

A European website was offering a ppa for the Wacom driver, tried that one too, but it wouldn't compile for 31 kernel. Equally so the ppa suggested on sourceforge, same problem, ...seems that these two ppa's are copies of each other.

squiregrand, no need to blame yourself, Wacom can't sell you another product, as these are discontinued. I gotten my intuos pro only because my ancient intuos2 pen failed and I can't find a replacement for it.

It looks like we'll have to wait until April next year for 14.04 to get released, hopefully then the driver issue will be sorted out.

---

### Post by Favux on 2013-10-19
Hi AussiePozzie,

> and xorg-xserver is missing
That doesn't make any sense.  You wouldn't have a graphical environment without the X Server, just the command line.  What is the output of:
```
Xorg -version
```
run in a terminal?

I wonder if it isn't complaining that the package xserver-xorg-input-all is missing, which would happen if you uninstalled xserver-xorg-input-wacom?

---

### Post by AussiePozzie on 2013-10-19
Hi Favux,

Here is the output:

smaragd@smaragd:~$ Xorg -version

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux smaragd 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=67005cdf-2a1c-462e-8981-88f2a0436e6e ro quiet splash
Build Date: 16 October 2013  04:46:41PM
xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.28.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.

Seems like it's installed allright.

I had guessed that I wouldn't see anything on the onitor if xorg-server wasn't installed.

Here is the output of xinput: 

smaragd@smaragd:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1024    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:2011    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]


No intuos pro listed.

If I plug in my **daughter's Bamboo**, is what I get:

smaragd@smaragd:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1024    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:2011    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen stylus             id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen eraser             id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Finger touch           id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Finger pad             id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]

Lists it right away!

xsetwacom -V                  = 0.19.0
lsmod | grep [Ww]acom     = wacom                  62214  0 
xsetwacom list                 = blank, no return

Not sure if I can make any sense out this issue.

---

### Post by AussiePozzie on 2013-10-19
Favux,

Following a hunch, after you mentioned the "xserver-xorg-input-all", I tried to install it, here is the screen:

smaragd@smaragd:~$ sudo apt-get install xserver-xorg-input-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11-apps x11-session-utils x11-xfs-utils xinit libfs6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom
Suggested packages:
  gpointing-device-settings touchfreeze
The following packages will be REMOVED:
  libgl1-mesa-dri-lts-raring libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring
  libgl1-mesa-glx-lts-raring:i386 libglapi-mesa-lts-raring libglapi-mesa-lts-raring:i386
  libxatracker1-lts-raring ubuntu-desktop x11-xserver-utils-lts-raring xorg
  xserver-common-lts-raring xserver-xorg-core-lts-raring xserver-xorg-input-all-lts-raring
  xserver-xorg-input-evdev-lts-raring xserver-xorg-input-mouse-lts-raring
  xserver-xorg-input-synaptics-lts-raring xserver-xorg-input-vmmouse-lts-raring
  xserver-xorg-input-wacom-lts-raring xserver-xorg-lts-raring xserver-xorg-video-all-lts-raring
  xserver-xorg-video-ati-lts-raring xserver-xorg-video-cirrus-lts-raring
  xserver-xorg-video-fbdev-lts-raring xserver-xorg-video-intel-lts-raring
  xserver-xorg-video-mach64-lts-raring xserver-xorg-video-mga-lts-raring
  xserver-xorg-video-modesetting-lts-raring xserver-xorg-video-neomagic-lts-raring
  xserver-xorg-video-nouveau-lts-raring xserver-xorg-video-openchrome-lts-raring
  xserver-xorg-video-r128-lts-raring xserver-xorg-video-radeon-lts-raring
  xserver-xorg-video-s3-lts-raring xserver-xorg-video-savage-lts-raring
  xserver-xorg-video-siliconmotion-lts-raring xserver-xorg-video-sis-lts-raring
  xserver-xorg-video-sisusb-lts-raring xserver-xorg-video-tdfx-lts-raring
  xserver-xorg-video-trident-lts-raring xserver-xorg-video-vesa-lts-raring
  xserver-xorg-video-vmware-lts-raring
The following NEW packages will be installed:
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
0 upgraded, 11 newly installed, 41 to remove and 0 not upgraded.
Need to get 2,454 kB of archives.
After this operation, 37.3 MB disk space will be freed.
Do you want to continue [Y/n]? 

I am a little apprehensive about proceeding with the install, as it is telling me that it will remove a whole swag of stuff, on the one hand, on the other, I think that those bits it wants to install are most likely essential to the digitizer being recognized.

What's your take?

---

### Post by Favux on 2013-10-19
I wouldn't.  I don't understand what it is telling us.

I asked because they added a new dependency between xserver-xorg-input-wacom and xserver-xorg-input-all quite a few releases ago.  Can't have one without the other and uninstalling one uninstalled the other.  That was new back when.  So I was wondering if you had uninstalled xserver-xorg-input-wacom and that had uninstalled xserver-xorg-input-all.  Unless it has changed in Raring both of them should be installed by default.

Not seeing the Pro in **xinput list** indicates that you don't have the new wacom.ko from input-wacom-0.19.0 correctly compiled or copied into the correct place.  You need the new wacom.ko for kernel support of the Pro.  The copy command should look like:
```
sudo cp ./3.7/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
assuming you are in the input-wacom folder.

---

### Post by AussiePozzie on 2013-10-19
Here is the screenshot of the wacom.ko properties window:

Name:        wacom.ko
Type:        Document (application/x-object)
Size:        94.7 kB (94,744 bytes)

Location:    /lib/modules/3.8.0-31/kernel/drivers/input/tablet
Valume:        unknown

I would think that it is in the right location, and since I haven't touched it since the recent system install, I would also imagine that it would be correctly compiled by **default**, ...or maybe not.

Anywho, ...I have looked for wacom.ko but can't find it by itself, am I then assuming correctly, that it is only awailable in the xf86 package, or some other package, and can't be installed by itself?

Googling for "update wacom.ko" showed no useful results either.

---

### Post by Favux on 2013-10-19
Well a wacom.ko (the Wacom kernel driver/module) comes automatically with the kernel.  What I kind of wanted you to do was check the wacom.ko in /lib/modules/3.8.0-31/kernel/drivers/input/tablet Properties and make sure it was the same date as when you compiled it from input-wacom-0.19.0 so we know it is the new working wacom.ko.  In other words it was copied to the correct location.

Or have I confused myself and you haven't compiled a wacom.ko?  You understand there are two drivers, the Wacom kernel driver and the Wacom X driver?  This HOW TO has a walk through on how to compile them:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)  Sorry if I'm going over old territory.

---

### Post by AussiePozzie on 2013-10-19
I went to the linux mint forum, as you suggested, and started, line by line, to install the wacom.ko, when at the line:

sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev  autoconf libtool

it asked me to agree to the same removal of drivers as I shown in the 2nd last post. I knew what was going to happen, but still let it proceed, ...just to make sure my instincts are still on par.

The line 

./configure --prefix=/usr 

didn't produce any error messages during the configure stage, but as soon as it was commencing the compiling, two errors came up, telling that for 31 kernel it couldn't compile. My instincts were about to be proven right, ...right here!

The line: 

sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

told me that there is **no** file wacom.ko in 2.6.38 directory, which I thought was odd, ...so I went into the filemanager and checked, and lo and behold, the wacom.ko was not there, ...full stop!

I knew it was pointless to run the last line:

sudo depmod -a

but I did it anyway, ...and then rebooted.

Well, my instincts seem to be on par allright, ...it came only as far a 'checking battery state' and then seized.

Now I'll be spending the rest of the day and A good portion of the night in rebuilding my system from scratch.

I maybe pulled up the moderators for the following harsh criticism, ...but, for crying out loud, 
[B]
PLEASE GET[/B] **DEVELOPERS TO _*MAINTAIN*_ THEIR DISTROS AND PPA'S!**

---

### Post by Favux on 2013-10-19
Check the 3.7 folder, that's where the new wacom.ko should be.  Not the 2.6.38 folder.  That is the copy command I gave you above in post #16.

Since you didn't actually copy a wacom.ko into place you shouldn't have changed your system so I have no idea what is wrong.  You shouldn't need to rebuild anything.

I think the linuxwacom developers having support available within a month of the release of the Pro's is amazing.

I know you are frustrated.  Even if you did something with xf86-input-wacom simply unplugging the tablet and rebooting should get it to start OK.  Did you ever reboot after you compiled xf86-input-wacom?

---

### Post by AussiePozzie on 2013-10-20
There were several folders, all with different numbers, ...I went and checked **each** one of them: _**NO**_ wacom.ko! Only because I joined the forum a week ago, isn't any indication of my linux exposure, ...I've been with linux since 9.10, ...it's only because this **buggy** 12.04, much akin to Windows, that I am having all these problems, none of which were there with all these previous releases.

[B]You have missed the _line_, mate: 
[/B]
_*sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool*_

which did removed **ALL** of these drivers:  

 The following packages will be REMOVED:
libgl1-mesa-dri-lts-raring libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring
libgl1-mesa-glx-lts-raring:i386 libglapi-mesa-lts-raring libglapi-mesa-lts-raring:i386
libxatracker1-lts-raring ubuntu-desktop x11-xserver-utils-lts-raring xorg
xserver-common-lts-raring xserver-xorg-core-lts-raring xserver-xorg-input-all-lts-raring
xserver-xorg-input-evdev-lts-raring xserver-xorg-input-mouse-lts-raring
xserver-xorg-input-synaptics-lts-raring xserver-xorg-input-vmmouse-lts-raring
xserver-xorg-input-wacom-lts-raring xserver-xorg-lts-raring xserver-xorg-video-all-lts-raring
xserver-xorg-video-ati-lts-raring xserver-xorg-video-cirrus-lts-raring
xserver-xorg-video-fbdev-lts-raring xserver-xorg-video-intel-lts-raring
xserver-xorg-video-mach64-lts-raring xserver-xorg-video-mga-lts-raring
xserver-xorg-video-modesetting-lts-raring xserver-xorg-video-neomagic-lts-raring
xserver-xorg-video-nouveau-lts-raring xserver-xorg-video-openchrome-lts-raring
xserver-xorg-video-r128-lts-raring xserver-xorg-video-radeon-lts-raring
xserver-xorg-video-s3-lts-raring xserver-xorg-video-savage-lts-raring
xserver-xorg-video-siliconmotion-lts-raring xserver-xorg-video-sis-lts-raring
xserver-xorg-video-sisusb-lts-raring xserver-xorg-video-tdfx-lts-raring
xserver-xorg-video-trident-lts-raring xserver-xorg-video-vesa-lts-raring
xserver-xorg-video-vmware-lts-raring

after which, ...*of course*, the system didn't have what to start **WITH**, ...and hence stalled at the "checking battery state" line. And you still think I wouldn't have neede to rebuilt it from scratch?

I would need **first** to get the system to **COMPILE** this infernal xf86 driver, **BEFORE** I can go start playing with the hardware.  

That the support is only after a month is commendable, ...certainly, ...it would be immeasurably **BETTER** though, if it actually would work too, ...you know!  

My instincts tell me that it is most likely an issue of the 31 kernel and amd64, ...if the xf86 was written for **BOTH**, I'm pretty sure there wouldn't be next to no problems.

I am under the impression that it wasn't written for either.

---

### Post by Favux on 2013-10-20
If I am messing up and something is wrong with the HOW TO I would greatly appreciate your help in fixing it.

Ordinarily I don't think adding developmental libraries for compiling results in a bunch of system files being uinstalled.  Warnings that old versions will be replaced is more what I would expect to see.  So I don't understand what you are telling me about the result of:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```

For me the question becomes exactly what release of Ubuntu are you using?  The thread title implies Precise (12.04).  But you've now said twice:
> t is most likely an issue of the 31 kernel
Why do you keep saying you have the 3.1 kernel?  Precise has the 3.2 kernel.  But we had already established you are using Raring i.e. the 3.8 kernel with the output of **Xorg -version**.
> Current Operating System: Linux smaragd 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64
So now I'm thinking I missed the significance of smaragd, whatever that is.  What is the output of?
```
cat /etc/issue
```

Because you are not using the hybrid ABI Precise uses:
> xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
I didn't mention the bug the frankenserver patch addresses for xf86-input-wacom.  The bug causes system freezes or crashes unless the patch is applied.  But you appear to have the Raring 1.13 X Server, not the Precise 1.11/1.12 hybrid that identifies itself as 1.11.

Anyway I'm trying to understand if you have some sort of idiosyncratic set up that is causing trouble with the compiling and so on.  Or am I just completely missing the boat?

---

### Post by AussiePozzie on 2013-10-20
Mate, you need to start paying attention, ...

> sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtoolI wouldn't have expected that this line will cause you such consternation, as it is actually not that line, but what it **causes**, that is the core issue here! Your dismissive attitude, that you expect some 'old versions' to be replaced, is a touch out of reality, as what it is replacing, are actually critical components of the system setup and hence critical to it's operation.

I would humbly submit, that you start focusing on the list of _***removed***_ items **first**, and then compare this to what it was **replaced with**, and then see if the system is likely to recover from such massive changes. A hint: ...it won't!

This thread was started on a **12.04** basis (or did I get that wrong?), ...what sense, then, would it make for me to beat my head against reinforced concrete, i.e. me having a **different** distro?

Instead of having to exemplify the complete kernel discription, pedantically 3.8.0-31-generic, as it is the **current** kernel, and everyone would be reasonable expected to be aware of it, I prefer to just type the last two digits **31** for efficiency sakes. I didn't type **3.1**, ...no, I typed **31**! Taking things at face value is rather appropriate here.

'smaragd' is my machine's **name**, I would have thought, that when the line starts with **smaragd@smaragd:~$** then that would be readily identified as the machine name, ...but then again, that's me.
[U][I]
Mate, ...you really need to start paying attention![/I][/U]

Here is your cat output:

smaragd@smaragd:~$ cat /etc/issue
Ubuntu 12.04.3 LTS \n \l

let's see if you won't misinterpret that too.

You seem to be readily jumping to conclustions, for me to be able to implement **patches**, I would need first to have to be able to **compile** wacom.ko, which I have explained to you in the previous post didn't happen due to some errors during compilation (can't remeber their codes anymore), hence, the copy command couldn't find wacom.ko as it **wasn't** compiled!

I am going by memory here, ...what I remember seeing in the directories, were wacom.h, ...which I think is the precompile version of the wacom.ko.

Do your homework mate!

I am displaying remarkable patience with your attitude, by explaining things that you **ought** to know.

---

### Post by Favux on 2013-10-20
The cat command showed your release is identifying itself as the Precise LTS.  As far as I am aware Precise (12.04) natively has the 3.2 kernel.  And as I mentioned the 1.11 (actually hybridized with some of 1.12) X Server.

Since you have the 3.8.0-31-generic kernel how did you get it?  The same question applies to your 1.13 X Server.

In other words you don't seem to be in a vanilla Precise Unity release.  You appear to have customized it.  If that is true perhaps you could share what you have done.

That's what I've been trying to understand the last few posts.  We appear to be speaking othogonally to each other, not communicating.

---

### Post by Favux on 2013-10-20
Part of the mystery is solved.  It turns out Ubuntu has changed a fundamental policy I thought was written in stone and is updating the kernel and X Server stack in Precise:  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)  That blows me away.  How can they call it a long term release if they are updating fundamental parts of the system's stack?  I don't know what else is changed with updating the so called HWE stack.  Not seeing a whole lot of information.

I happened to have burned the 12.04.3 iso the other day and just ran it live and sure enough I'm seeing the same **Xorg -version** output you are.  So you are running a "Precise" that is at least partially Raring (13.04).  Now is that why the problems?  Because it's a  hybridized system?  Maybe the package manager points to a mix of the releases?  I just installed Raring the other week and was planning on testing out the Wacom driver compiles on it if that turned out to be what you had.  But is compiling on 13.04 the same as 12.04.3?

My Precise, which is up to date, still says the 3.2 kernel and 1.11 X Server.  No way I'm upgrading it to 12.04.3 just to check this out.  Raring or nothing.

---

### Post by AussiePozzie on 2013-10-20
I was **never** coming in at 90 degrees, ...I have maintained a **very *_straight_* line** in regard to LTS!

ubuntu **never** have set anything in stone, ...you only have _***assumed***_ that! Like I said, ...I am with ubuntu since 9.10, and ever since, kernels I can remember have been updated **regularaly**!

The ongoing support for LTS, thank God, is also including changes to the kernel, as it is vital for additional capabilities, since it is going to stay **quasi** the same release, i.e. 12.04, with additonal capabilities throughout it's service life, ...you need to install an update you knowledge, mate!

[SIZE=6]Your precise is **not** up to date![/SIZE]

I cannot say anything about 13.04 or 13.10, as I am using 12.04 LTS and will continue to use LTS distros **only**, ...but a safe assumption would be that either one of these two would produce either similar or even identical errors as does 12.04 with a 3.8.0-31-generic kernel.

Do you get it now, ...that it is a **_kernel_ issue**?

I am faily certain that it is _**also**_ a x86 versus x64 issue, ...my instincts tell me that that infernal xf86 and wacom.ko in their **current** configurations, would *_**not**_* compile on an AMD64 12.04

Are you going to be 'polite' enough and go and **update** your instructions, by limiting them to maybe **only** a certain kernel and **only** to x86 distros, prior to 12.04, ...instead of purporting that it is suitable for any distro and any bitrate?

Probably not, ...if your up to now obstinance is anything to go by.

---

### Post by Favux on 2013-10-20
> Your precise is not up to date!
It is according to Update Manager.  And I have been getting all the security patches for the kernel and so on.
> I am with ubuntu since 9.10, and ever since, kernels I can remember have been updated regularaly!
That turns out not to be the case.  The Ubuntu Kernel team releases minor updates that include security fixes and occasionally functional improvements.  That's the 31 and so on you mentioned earlier.  But the kernel version itself has not been updated.  So for e.g. Lucid stuck with 2.6.32 with regular minor updates such as 2.6.32-54 or whatever.  I won't be totally categorical about that because I don't track the Kernel team's activities closely.
> my instincts tell me that that infernal xf86 and wacom.ko in their current configurations, would not compile on an AMD64 12.04
I have only been using amd64 for years.  Compiles fine for me in the 3.2 kernel/1.11 X Server Precise, except I have to apply the frankenserver patch.  Just compiled input-wacom-0.19.0 in Raring (3,8 kernel/1.13 X Server) with no problem on amd64 and tested in Gimp.  Did not see anything resembling the output you got with:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```
At the end of the output from the command:
```
./configure --prefix=/usr
```
as usual it helpfully tells you the new wacom.ko is in the 3.7 folder and where to copy it to.  So as I expected:
```
sudo cp ./3.7/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
worked fine.
> Are you going to be 'polite' enough and go and update your instructions, by limiting them to maybe only a certain kernel and only to x86 distros, prior to 12.04, ...instead of purporting that it is suitable for any distro and any bitrate?

Probably not, ...if your up to now obstinance is anything to go by. 
How can I?  You have not yet helped me figure out what went wrong with your 12.04.3 Precise install.  I have nothing to add so far except the new copy command for the 3.7 folder.

Well on to compile xf86-input-wacom.

---

### Post by Favux on 2013-10-20
Alright, the compile of xf86-input-wacom-0.23.0 on Raring was also without problems.  Tested again in Gimp.

So no further light shed on your difficulty.  I'd think/hope if other 12.04.3 users were encountering the same issue(s) they would have posted.  I don't think it is unreasonable to suppose at least one other 12.04.3 user has compiled Wacom drivers.

I do make a habit of preserving a copy of the compile output whenever I first compile software in a new release.  Gives me something to look over and is especially useful as a baseline if I encounter a problem with a later compile of a new version on that release.

---

### Post by AussiePozzie on 2013-10-21
By the looks of it, if you are running 12.04, with a 3.2 kernel, and you are **not** running a LTS distro, and you are **adamant** that your distro is up to date, and your update manager is **working**, mate, ...then you must be having some **remarkable** ubuntu installation!

Either way, I am not disputing that the compilation works on the 3.2 kernel, maybe even in AMD64, but it certainly doesn't work in 3.8 on 12.04 LTS!

I am not at all surprised that the compilation worked in Raring, it is most likely the case that the distro was adjusted accordingly.

I doubt very much that there would be many who are on 12.04 3 and would have intuos pro, ...not something that is often bought, unless one is a dedicated artist or engineering designer, ...like me.

What is your intous pro serial?

The local distributor here is of the opinion that there was some firmware changes between intous5 and intous pro. According to him, if there is a mismatch between the firmware on the digitizer and the compilation version of the driver, the driver won't get compiled. A little far fetched, ...I think.

---

### Post by AussiePozzie on 2013-10-21
Here is the complete output of the ./config of xf86-input-wacom-0.23.0:

```
sapphire@sapphire:~/temp/xf86-input-wacom-0.23.0$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/sapphire/temp/xf86-input-wacom-0.23.0/missing: Unknown '--is-lightweight' option
Try '/home/sapphire/temp/xf86-input-wacom-0.23.0/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=unknown-warning-option... no
checking if gcc -std=gnu99 supports -Werror=unused-command-line-argument... no
checking if gcc -std=gnu99 supports -Wall... yes
checking if gcc -std=gnu99 supports -Wpointer-arith... yes
checking if gcc -std=gnu99 supports -Wmissing-declarations... yes
checking if gcc -std=gnu99 supports -Wformat=2... yes
checking if gcc -std=gnu99 supports -Wstrict-prototypes... yes
checking if gcc -std=gnu99 supports -Wmissing-prototypes... yes
checking if gcc -std=gnu99 supports -Wnested-externs... yes
checking if gcc -std=gnu99 supports -Wbad-function-cast... yes
checking if gcc -std=gnu99 supports -Wold-style-definition... yes
checking if gcc -std=gnu99 supports -Wdeclaration-after-statement... yes
checking if gcc -std=gnu99 supports -Wunused... yes
checking if gcc -std=gnu99 supports -Wuninitialized... yes
checking if gcc -std=gnu99 supports -Wshadow... yes
checking if gcc -std=gnu99 supports -Wcast-qual... yes
checking if gcc -std=gnu99 supports -Wmissing-noreturn... yes
checking if gcc -std=gnu99 supports -Wmissing-format-attribute... yes
checking if gcc -std=gnu99 supports -Wredundant-decls... yes
checking if gcc -std=gnu99 supports -Werror=implicit... yes
checking if gcc -std=gnu99 supports -Werror=nonnull... yes
checking if gcc -std=gnu99 supports -Werror=init-self... yes
checking if gcc -std=gnu99 supports -Werror=main... yes
checking if gcc -std=gnu99 supports -Werror=missing-braces... yes
checking if gcc -std=gnu99 supports -Werror=sequence-point... yes
checking if gcc -std=gnu99 supports -Werror=return-type... yes
checking if gcc -std=gnu99 supports -Werror=trigraphs... yes
checking if gcc -std=gnu99 supports -Werror=array-bounds... yes
checking if gcc -std=gnu99 supports -Werror=write-strings... yes
checking if gcc -std=gnu99 supports -Werror=address... yes
checking if gcc -std=gnu99 supports -Werror=int-to-pointer-cast... yes
checking if gcc -std=gnu99 supports -Werror=pointer-to-int-cast... yes
checking if gcc -std=gnu99 supports -pedantic... yes
checking if gcc -std=gnu99 supports -Werror... yes
checking if gcc -std=gnu99 supports -Werror=attributes... yes
Package xorg-macros was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-macros.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-macros' found
checking whether make supports nested variables... (cached) yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Like I said several posts ago, doxygen and xorg-server aren't on the system.

Doxygen installs fine, but the xorg-server is what stuffs the system up.
 		 			 				:mad:

---

### Post by Favux on 2013-10-21
It is a semantic issue.  For Precise 12.04 I am up to date.  My Precise LTS release identifies itself as:
> ~$ cat /etc/issue
Ubuntu 13.04 \n \l

With:
> ~$ Xorg -version

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux dave-p6520y 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=45ac99c3-ddd0-421f-93c9-433702ed97ea ro quiet splash
Build Date: 16 October 2013  04:35:36PM
xorg-server 2:1.13.3-0ubuntu6.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.28.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.

Thanks for the output.  I'll see if I can figure out what it trying to tell us.

Meanwhile the output I get with library install command is:
```
~/Desktop$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
build-essential is already the newest version.
libncurses5-dev is already the newest version.
libtool is already the newest version.
pkg-config is already the newest version.
x11proto-input-dev is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
libxrandr-dev is already the newest version.
xserver-xorg-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-unique-3.0 libunique-3.0-0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libudev-dev libxinerama-dev xutils-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 383 kB of archives.
After this operation, 1,847 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libudev-dev amd64 198-0ubuntu11.2 [27.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libxinerama-dev amd64 2:1.1.2-1ubuntu0.13.04.1 [8,452 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/main xutils-dev amd64 1:7.7~1build1 [346 kB]
Fetched 383 kB in 1s (221 kB/s)     
Selecting previously unselected package libudev-dev.
(Reading database ... 192797 files and directories currently installed.)
Unpacking libudev-dev (from .../libudev-dev_198-0ubuntu11.2_amd64.deb) ...
Selecting previously unselected package libxinerama-dev:amd64.
Unpacking libxinerama-dev:amd64 (from .../libxinerama-dev_2%3a1.1.2-1ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package xutils-dev.
Unpacking xutils-dev (from .../xutils-dev_1%3a7.7~1build1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libudev-dev (198-0ubuntu11.2) ...
Setting up libxinerama-dev:amd64 (2:1.1.2-1ubuntu0.13.04.1) ...
Setting up xutils-dev (1:7.7~1build1) ...
```
I can give you the output of the update and upgrade commands if you would like.

This is my output for the ./configure command:
```
~/Desktop/xf86-input-wacom-0.23.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/xxxx/Desktop/xf86-input-wacom-0.23.0/missing: Unknown '--is-lightweight' option
Try '/home/xxxx/Desktop/xf86-input-wacom-0.23.0/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=unknown-warning-option... no
checking if gcc -std=gnu99 supports -Werror=unused-command-line-argument... no
checking if gcc -std=gnu99 supports -Wall... yes
checking if gcc -std=gnu99 supports -Wpointer-arith... yes
checking if gcc -std=gnu99 supports -Wmissing-declarations... yes
checking if gcc -std=gnu99 supports -Wformat=2... yes
checking if gcc -std=gnu99 supports -Wstrict-prototypes... yes
checking if gcc -std=gnu99 supports -Wmissing-prototypes... yes
checking if gcc -std=gnu99 supports -Wnested-externs... yes
checking if gcc -std=gnu99 supports -Wbad-function-cast... yes
checking if gcc -std=gnu99 supports -Wold-style-definition... yes
checking if gcc -std=gnu99 supports -Wdeclaration-after-statement... yes
checking if gcc -std=gnu99 supports -Wunused... yes
checking if gcc -std=gnu99 supports -Wuninitialized... yes
checking if gcc -std=gnu99 supports -Wshadow... yes
checking if gcc -std=gnu99 supports -Wcast-qual... yes
checking if gcc -std=gnu99 supports -Wmissing-noreturn... yes
checking if gcc -std=gnu99 supports -Wmissing-format-attribute... yes
checking if gcc -std=gnu99 supports -Wredundant-decls... yes
checking if gcc -std=gnu99 supports -Werror=implicit... yes
checking if gcc -std=gnu99 supports -Werror=nonnull... yes
checking if gcc -std=gnu99 supports -Werror=init-self... yes
checking if gcc -std=gnu99 supports -Werror=main... yes
checking if gcc -std=gnu99 supports -Werror=missing-braces... yes
checking if gcc -std=gnu99 supports -Werror=sequence-point... yes
checking if gcc -std=gnu99 supports -Werror=return-type... yes
checking if gcc -std=gnu99 supports -Werror=trigraphs... yes
checking if gcc -std=gnu99 supports -Werror=array-bounds... yes
checking if gcc -std=gnu99 supports -Werror=write-strings... yes
checking if gcc -std=gnu99 supports -Werror=address... yes
checking if gcc -std=gnu99 supports -Werror=int-to-pointer-cast... yes
checking if gcc -std=gnu99 supports -Werror=pointer-to-int-cast... yes
checking if gcc -std=gnu99 supports -pedantic... yes
checking if gcc -std=gnu99 supports -Werror... yes
checking if gcc -std=gnu99 supports -Werror=attributes... yes
checking whether make supports nested variables... (cached) yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking whether the linker supports -wrap... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating conf/Makefile
config.status: creating doc/Makefile
config.status: creating doc/doxygen.conf
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating include/Makefile
config.status: creating tools/Makefile
config.status: creating test/Makefile
config.status: creating xorg-wacom.pc
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

```
I don't have doxygen installed either.  You don't need it in order to succesfully compile.  The xorg-server and proto packages appear to be your current road block.  I had been wondering if you had done something "big" with your X Server regarding to xorg drivers and such.  But it seems to be this is due to 12.04.3 for some reason.

Actually since I don't think you've successfully compiled the kernel driver (wacom.ko) yet, maybe we should start there?

> According to him, if there is a mismatch between the firmware on the digitizer and the compilation version of the driver, the driver won't get compiled. A little far fetched, ...I think. 
I agree.  That wouldn't affect driver compilation.  If the driver didn't support the changes then the tablet just wouldn't work, or work correctly you'd think.  From the input-wacom git browse history:  [http://sourceforge.net/p/linuxwacom/input-wacom/ci/74ac82b163f238ca511f21a52abd477663ee180e/log/?path=](http://sourceforge.net/p/linuxwacom/input-wacom/ci/74ac82b163f238ca511f21a52abd477663ee180e/log/?path=)  you can see the basic changes:  [http://sourceforge.net/p/linuxwacom/input-wacom/ci/bed4614dec158f9a30a2e677a4e25829aff7f4ce/](http://sourceforge.net/p/linuxwacom/input-wacom/ci/bed4614dec158f9a30a2e677a4e25829aff7f4ce/)  There were others.  I used input-wacom to save me from tracking down the submissions to the kernel's linux-input mailing list.  I do not have a Pro.  Right now I am testing the new Wacom drivers on an Intuos4.

---

### Post by Favux on 2013-10-21
Alright, this may be the problem.
> Package xorg-macros was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-macros.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-macros' found
When I checked Package search xutils-dev in Precise has xorg.macros.m4 but Precise-udates doesn't seem to have the package:  [http://packages.ubuntu.com/precise/xutils-dev](http://packages.ubuntu.com/precise/xutils-dev)  When I check the Raring package is almost the same (same version #):  [http://packages.ubuntu.com/raring/xutils-dev](http://packages.ubuntu.com/raring/xutils-dev)  but includes an additional updated libc6.

So what would happen with a:
```
sudo apt-get install xutils-dev
```
command?  Can 12.04.3 use the 12.04 package or does it try to pull the Raring one?  Which one would Apt call?  Or would it not call either?  In other words what repository would it point to?  I don't know enough in depth detail about these development packages to predict.  Since xutils-dev is in the HOW TO's libraries command it looks like nothing happens and the package isn't available to Apt in 12.04.3.

  I would likely have blithely downloaded and run the xutils-dev Deb package for Precise not even realizing I might be walking into a problem.  And by the way the file list on the xutils-dev page does have in addition to /usr/share/aclocal/xorg-macros.m4, /usr/share/pkgconfig/xorg-macros.pc as mentioned in the output.

---

### Post by AussiePozzie on 2013-10-21
I have installed the xutils-dev package, but this makes no difference:

```
checking whether make supports nested variables... (cached) yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
smaragd@smaragd:~/temp/xf86-input-wacom-0.23.0$ sudo apt-get install xutils-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xutils-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
smaragd@smaragd:~/temp/xf86-input-wacom-0.23.0$ Xorg -version

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux smaragd 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=e33928de-7e22-459c-8d92-d5bda388db27 ro quiet splash
Build Date: 16 October 2013  04:46:41PM
xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.28.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
```

I am inclined to think, that the problem would be rather in the discrepancy between the versions of xorg-server/xorg-xserver, as the app is calling for a version that is either outdate or otherwise not compatible with the version that 12.04 LTS is installed with:

> configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

**vs**

X.Org X Server 1.13.3

provided that **>=1.7.0** is actually saying that it needs to be a version **later** than that, and hence reports that error.

I am wonderin why the app is calling for that release of the xserver anyway? Needed for compilation?

Why isn't the app just happy with what it finds installe on the system and goes an uses it? Why is it calling for a **specific** release?

What makes me thing about your intuos4, ...even if I eventually manage to get the infernal wacom.ko installed, is the intuos **pro** going to work? According to my local distributor, there is a difference between the intuos4 and intuos5/intuos pro. Or will that only proove in the end to be a installing exercise only?

---

### Post by Favux on 2013-10-21
That's too bad.  Which version of xutils-dev did you install?  And how did you install it?
> I am inclined to think, that the problem would be rather in the discrepancy between the versions of xorg-server/xorg-xserver
You might be right.  I'll have to think about it a bit.  How do we determine the appropriate version?  According to the output we need them all >=1.7.0, which at least gives us somewhere to start.  Is this a hybridized X Sever stack?  And is was that on purpose?  Use Package search and compare Precise to Raring for each of them?  Seems like trying that may run into pulling and removing the wrong dependencies which was the problem to begin with.
> I am wonderin why the app is calling for that release of the xserver anyway? Needed for compilation?
My presumption is that it is the Make file doing that.  The developers write it so that it tries to ensure it is in a "sane" environment for a compile.  If that is the issue, it might be a "simple" thing to fix for a developer.  While I can write a basic simple Make file the kind of Make file that comes with a Wacom driver is totally out of my league.  Way too complicated for me to follow.  I mean take a look at the thing.

If we're convinced we've dead ended you can always ask the question on the linuxwacom-discuss mail list.  But they tend not to be very interested in idiosyncratic Distro issues.  Sort of a "if Ubuntu broke it then it is up to them to fix it" attitude.  But hey we could could get lucky.
> even if I eventually manage to get the infernal wacom.ko installed, is the intuos pro going to work?
Yes that's the whole point of using input-wacom-0.19.0 and xf86-input-wacom-0.23.0.  The developers have added the code necessary to get the Pros working.  And they test the code.  That is amazingly fast turnaround for Linux Wacom.  In the past some tablets took a year or more to get supported.  Admittedly some unusual circumstances involved, but still.

Your problem apparently is that Precise 12.04.3 is an atypical environment that they had not anticipated.  Normally you'd think OK file a bug report on Launchpad.  But response can be very slow to basically none.  I've already checked and there have been bug reports filed about kernel modules/drivers not compiliing in 12.04.3.  At least one of them did get fixed it looks like.

While we gaze at our navels on this do you want to try to compile input-wacom?

Edit:  A thought percolates up.  They must have done a successful compile to produce the xorg-xserver-input-wacom package for the X driver.  I wonder if something in there, like say the Debian Patches folder, would tell us how they did it?  Dissecting a deb like that is a bit of a chore, at least for me.

Edit2:  Could be making some headway.  Coming up with 0.19.0 [xserver-xorg-input-wacom-lts-raring (1:0.19.0-0ubuntu1~precise1)] from:  [http://packages.ubuntu.com/search?keywords=xserver-xorg-input-wacom&searchon=names&suite=precise-updates&section=all](http://packages.ubuntu.com/search?keywords=xserver-xorg-input-wacom&searchon=names&suite=precise-updates&section=all)  Whereas the original Precise xserver-xorg-input-wacom was 0.14.0.  And 0.19.0 is the Raring default.  See:  [http://packages.ubuntu.com/precise-updates/xserver-xorg-input-wacom-lts-raring](http://packages.ubuntu.com/precise-updates/xserver-xorg-input-wacom-lts-raring)  Nothing in the ChangeLog is jumping out at me as the fix though.

---

### Post by AussiePozzie on 2013-10-21
Only the one I felt sufficiently **save** to install, ...via synaptic: 1:7.7~1, without risking the system being disabled.

> How do we determine the appropriate version?

Hhmmm, ...good question, ...not sure, ...but my instincts tell me that it ought to be the version which is on the system onto which wacom.ko is to be compiled on. Anything else would most likely result in dependencies being stuffed up and renedering the system unusable, ...what I had before.

I personallly find it absolutely **absurd**, ...to say the least, that the compiling process would depend on a _***specific***_ setup. How can any developer predict what setups his app is going to encounter in it's service life?

I am beginning to get the impression, that this **very** soon support for the intuos pro was a very rush, rush affair, ...not thought through properly and not programmed in a fashion that would accomodate all current distros, but only **one** distro: the one the developer was working with.

> Your problem apparently is that Precise 12.04.3 is an atypical environment that they had not anticipated.

I am fairly confident that my setup isn't too far from 'off the peg', ...I haven't done **any** changes to it at all, only **always** applied the updates as they are coming along, ...like another kernel update came through this morning, it is now 3.8.0-32-generic

I have a virtual machine running in ubuntu, and several releases ago, it used to always re-compile with every new kernel update. The developers of the virtual machine have learned since: the current release doesn't re-compile with every kernel update anymore.

Would be a hint for the wacom developers to follow suit.
> 
While we gaze at our navels on this do you want to try to compile input-wacom?

I'm not flexible enough for that anymore (just kidding), ...but I would think that in 12.04 LTS it **won't** install due to the, **...again**, specific library requirements which stuff up the existing system. I tried it before and messed up my system to the point of fresh install. Not intending to walk down that alley again.
> 
At least one of them did get fixed it looks like.

Where exactly did you look for these bug reports?

---

### Post by Favux on 2013-10-21
> I am fairly confident that my setup isn't too far from 'off the peg'
I meant 12.04.3 itself, not something you had done to it.  But it looks like 12.04.3 isn't the problem because the deb is a dead end as far as I can tell.  They don't seem to have encountered a problem compiling that they had to implement a workaround for.

Grasping at straws I wonder if your /usr/include/xorg directory (or the links to it) got garbled somehow.  So the correct Wacom or Xorg header files aren't totally accessable.  That happens occasionally.  Same with the package cache Apt uses, which is why there are the flushing and repair commands for it.

I understand not wanting to break anything again but my thinking was at least you could get some output we could look at without making any changes.  The kernel module wacom.ko translates the tablet's usb protocol into something an X driver like xf86-input-wacom can use.  Then the xf86-input-wacom driver translates that into instructions for the X Server.

I'm not explaining it well.  Each kernel version comes with different capabilities and the wacom.ko driver wants to access new capabilities and not use deprecated instructions.  So it needs to be aware of what kernel it is dealing with.  The same goes with the X Server.  You can think of it as a nest of if-thens that results in slightly different code being used for different kernel/X Server environments.  For example the multi-touch code was only recently added to the X Server.  That addition meant the Wacom X driver could stop implementing its own in driver workaround and use the new multi-touch services in the X Server.  That simplifies the Wacom X driver and makes maintainance easier.

I don't think it is a question of rushing development or anything like that.  To me it is looking more and more like you just got unlucky and for whatever reason your system is having a problem.  It may not be a general 12.04.3 issue.
> Where exactly did you look for these bug reports? 
[https://launchpad.net/](https://launchpad.net/)
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by AussiePozzie on 2013-10-21
The images won't attach, don't know why, so I can't show you the screen shot.

To discribe: the directory is in the place it's supposed to be and the permissions are **only** for root.

> was at least you could get some output we could look at without making any changes.
The out put is nothing different than that of previous post, ...it comes to the line:
> sudo apt-get install build-essential libx11-dev libxi-dev   x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev   autoconf libtool
after wich execution, it messes up the system completley, and then when the line is on:
> sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
it says that it can't find the wacom.ko ...no wonder, it didn't compile it in first place.

I been down that alley, I know the results.

I'll have a look at these bug reports.

---

### Post by AussiePozzie on 2013-10-21
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1234811](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1234811)

This thread is dealing with the intuos pro support.

I found this at the end of the thread:

[TABLE]
[TR]
[TD][Launchpad Janitor (janitor)]("https://launchpad.net/%7Ejanitor")             wrote             on 2013-10-07:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #3]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1234811/comments/3")           [/TD]
         [/TR]
            [/TABLE]
                               This bug was fixed in the package libwacom - 0.7-1ubuntu2

 ---------------
libwacom (0.7-1ubuntu2) saucy; urgency=low

   * update-to-git.diff: Pull changes up to current git master, since
    cherry-picking stuff seems pointless and fragile (FTBFS). Adds new
    model & styli definitions, fixes typos etc.
  * add-intuos-pro.diff: Dropped, included above.
 -- Timo Aaltonen <email address hidden>   Sun, 06 Oct 2013 16:42:07 +0300

              
                                    [TABLE="class: bug-activity"]
[TR]
         [TD="colspan: 2"]Changed in libwacom (Ubuntu): [/TD]
       [/TR]
          [TR]
       [TD="align: right"]         **status**:       [/TD]
       [TD]         Fix Committed &#8594; Fix Released       [/TD]
[/TR]
[/TABLE]

So, ...how do I lay my hand on that libwacom - 0.7-1ubuntu2 library?

---

### Post by Favux on 2013-10-21
For comparison here is mine:
```
~/Desktop$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
x11proto-input-dev is already the newest version.
x11proto-input-dev set to manually installed.
libx11-dev is already the newest version.
libxrandr-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-unique-3.0 libunique-3.0-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  automake autotools-dev dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdrm-dev libkms1 libltdl-dev libpciaccess-dev libpixman-1-dev libsigsegv2
  libstdc++6-4.7-dev libtinfo-dev libxkbfile-dev m4 mesa-common-dev x11proto-dri2-dev x11proto-fonts-dev
  x11proto-gl-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-video-dev x11proto-xf86dri-dev
  x11proto-xinerama-dev
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc debian-keyring g++-multilib g++-4.7-multilib
  gcc-4.7-doc libstdc++6-4.7-dbg libtool-doc ncurses-doc libstdc++6-4.7-doc automaken gfortran fortran95-compiler
  gcj
The following NEW packages will be installed:
  autoconf automake autotools-dev build-essential dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdrm-dev libkms1 libltdl-dev libncurses5-dev
  libpciaccess-dev libpixman-1-dev libsigsegv2 libstdc++6-4.7-dev libtinfo-dev libtool libxi-dev libxkbfile-dev
  m4 mesa-common-dev x11proto-dri2-dev x11proto-fonts-dev x11proto-gl-dev x11proto-resource-dev
  x11proto-scrnsaver-dev x11proto-video-dev x11proto-xf86dri-dev x11proto-xinerama-dev xserver-xorg-dev
0 upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.4 MB of archives.
After this operation, 44.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libkms1 amd64 2.4.43-0ubuntu1.1 [9,212 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libdrm-dev amd64 2.4.43-0ubuntu1.1 [212 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main mesa-common-dev amd64 9.1.4-0ubuntu0.1 [274 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring/main libsigsegv2 amd64 2.9-4ubuntu3 [14.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ raring/main m4 amd64 1.4.16-5 [203 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ raring/main autoconf all 2.69-1ubuntu1 [568 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ raring/main autotools-dev all 20120608.1 [42.9 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ raring/main automake all 1:1.11.6-1ubuntu1 [578 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ raring/main libstdc++6-4.7-dev amd64 4.7.3-1ubuntu1 [1,704 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ raring/main g++-4.7 amd64 4.7.3-1ubuntu1 [7,993 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ raring/main g++ amd64 4:4.7.3-1ubuntu10 [1,448 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ raring/main dpkg-dev all 1.16.10ubuntu1 [712 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ raring/main build-essential amd64 11.6ubuntu4 [5,672 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ raring/main fakeroot amd64 1.18.4-2ubuntu1 [89.1 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ raring/main libltdl-dev amd64 2.4.2-1.2ubuntu1 [204 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ raring/main libtinfo-dev amd64 5.9-10ubuntu4 [105 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ raring/main libncurses5-dev amd64 5.9-10ubuntu4 [224 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ raring/main libpixman-1-dev amd64 0.28.2-0ubuntu1 [282 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ raring/main libtool amd64 2.4.2-1.2ubuntu1 [305 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libxi-dev amd64 2:1.6.99.1-0ubuntu3.1 [206 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ raring/main libxkbfile-dev amd64 1:1.0.8-1 [89.4 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-dri2-dev all 2.8-1 [12.6 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-fonts-dev all 2.1.2-1 [69.7 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-gl-dev all 1.4.16-1 [22.3 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-resource-dev all 1.2.0-3 [10.7 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-scrnsaver-dev all 1.2.2-1 [25.0 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-video-dev all 2.3.1-2 [17.0 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-xf86dri-dev all 2.1.1-2 [5,630 B]
Get:32 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-xinerama-dev all 1.2.1-2 [4,966 B]
Get:33 http://us.archive.ubuntu.com/ubuntu/ raring/main libpciaccess-dev amd64 0.13.1-2 [23.2 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main xserver-xorg-dev amd64 2:1.13.3-0ubuntu6.2 [274 kB]
Fetched 14.4 MB in 6s (2,329 kB/s)                                                                                
Extracting templates from packages: 100%
Selecting previously unselected package libkms1:amd64.
(Reading database ... 187062 files and directories currently installed.)
Unpacking libkms1:amd64 (from .../libkms1_2.4.43-0ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libdrm-dev.
Unpacking libdrm-dev (from .../libdrm-dev_2.4.43-0ubuntu1.1_amd64.deb) ...
Selecting previously unselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_9.1.4-0ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libsigsegv2.
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu3_amd64.deb) ...
Selecting previously unselected package m4.
Unpacking m4 (from .../archives/m4_1.4.16-5_amd64.deb) ...
Selecting previously unselected package autoconf.
Unpacking autoconf (from .../autoconf_2.69-1ubuntu1_all.deb) ...
Selecting previously unselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20120608.1_all.deb) ...
Selecting previously unselected package automake.
Unpacking automake (from .../automake_1%3a1.11.6-1ubuntu1_all.deb) ...
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libltdl-dev:amd64.
Unpacking libltdl-dev:amd64 (from .../libltdl-dev_2.4.2-1.2ubuntu1_amd64.deb) ...
Selecting previously unselected package libtinfo-dev:amd64.
Unpacking libtinfo-dev:amd64 (from .../libtinfo-dev_5.9-10ubuntu4_amd64.deb) ...
Selecting previously unselected package libncurses5-dev.
Unpacking libncurses5-dev (from .../libncurses5-dev_5.9-10ubuntu4_amd64.deb) ...
Selecting previously unselected package libpixman-1-dev.
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.28.2-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libtool.
Unpacking libtool (from .../libtool_2.4.2-1.2ubuntu1_amd64.deb) ...
Selecting previously unselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.6.99.1-0ubuntu3.1_amd64.deb) ...
Selecting previously unselected package libxkbfile-dev:amd64.
Unpacking libxkbfile-dev:amd64 (from .../libxkbfile-dev_1%3a1.0.8-1_amd64.deb) ...
Selecting previously unselected package x11proto-dri2-dev.
Unpacking x11proto-dri2-dev (from .../x11proto-dri2-dev_2.8-1_all.deb) ...
Selecting previously unselected package x11proto-fonts-dev.
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.1.2-1_all.deb) ...
Selecting previously unselected package x11proto-gl-dev.
Unpacking x11proto-gl-dev (from .../x11proto-gl-dev_1.4.16-1_all.deb) ...
Selecting previously unselected package x11proto-resource-dev.
Unpacking x11proto-resource-dev (from .../x11proto-resource-dev_1.2.0-3_all.deb) ...
Selecting previously unselected package x11proto-scrnsaver-dev.
Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.2.2-1_all.deb) ...
Selecting previously unselected package x11proto-video-dev.
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.3.1-2_all.deb) ...
Selecting previously unselected package x11proto-xf86dri-dev.
Unpacking x11proto-xf86dri-dev (from .../x11proto-xf86dri-dev_2.1.1-2_all.deb) ...
Selecting previously unselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.2.1-2_all.deb) ...
Selecting previously unselected package libpciaccess-dev:amd64.
Unpacking libpciaccess-dev:amd64 (from .../libpciaccess-dev_0.13.1-2_amd64.deb) ...
Selecting previously unselected package xserver-xorg-dev.
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.13.3-0ubuntu6.2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up libkms1:amd64 (2.4.43-0ubuntu1.1) ...
Setting up libdrm-dev (2.4.43-0ubuntu1.1) ...
Setting up mesa-common-dev (9.1.4-0ubuntu0.1) ...
Setting up libsigsegv2 (2.9-4ubuntu3) ...
Setting up m4 (1.4.16-5) ...
Setting up autoconf (2.69-1ubuntu1) ...
Setting up autotools-dev (20120608.1) ...
Setting up automake (1:1.11.6-1ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up fakeroot (1.18.4-2ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libltdl-dev:amd64 (2.4.2-1.2ubuntu1) ...
Setting up libtinfo-dev:amd64 (5.9-10ubuntu4) ...
Setting up libncurses5-dev (5.9-10ubuntu4) ...
Setting up libpixman-1-dev (0.28.2-0ubuntu1) ...
Setting up libtool (2.4.2-1.2ubuntu1) ...
Setting up libxi-dev (2:1.6.99.1-0ubuntu3.1) ...
Setting up libxkbfile-dev:amd64 (1:1.0.8-1) ...
Setting up x11proto-dri2-dev (2.8-1) ...
Setting up x11proto-fonts-dev (2.1.2-1) ...
Setting up x11proto-gl-dev (1.4.16-1) ...
Setting up x11proto-resource-dev (1.2.0-3) ...
Setting up x11proto-scrnsaver-dev (1.2.2-1) ...
Setting up x11proto-video-dev (2.3.1-2) ...
Setting up x11proto-xf86dri-dev (2.1.1-2) ...
Setting up x11proto-xinerama-dev (1.2.1-2) ...
Setting up libpciaccess-dev:amd64 (0.13.1-2) ...
Setting up xserver-xorg-dev (2:1.13.3-0ubuntu6.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```
I noticed the output on the fglrx (ATI video driver) bug report looked familiar.  So maybe there is a problem with how they've linked dependencies for 12.04.3 after all.
> So, ...how do I lay my hand on that libwacom - 0.7-1ubuntu2 library? 
Yeah I saw that.  But libwacom is for the Gnome System Settings Wacom configuration applet gui, not the drivers.  It has data metafiles of the tablets.  So that won't help.

Edit: ** Oops!**  I buried the headline there didn't I.  It kind of looked like Timo said he is planning on backporting the support for the Pros to Precise.  If true at some point in the next month or two it might just start working.  That's also something they almost never did before.  So I don't know if I'm reading too much into what I saw or not.

---

### Post by AussiePozzie on 2013-10-21
Your
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
```
doesn't **remove** anything, ...when I do the same command, ...my system is being **obliterated!**
```
The following packages will be REMOVED:
  libgl1-mesa-dri-lts-raring libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring
  libgl1-mesa-glx-lts-raring:i386 libglapi-mesa-lts-raring libglapi-mesa-lts-raring:i386
  libxatracker1-lts-raring ubuntu-desktop x11-xserver-utils-lts-raring xorg
  xserver-common-lts-raring xserver-xorg-core-lts-raring xserver-xorg-input-all-lts-raring
  xserver-xorg-input-evdev-lts-raring xserver-xorg-input-mouse-lts-raring
  xserver-xorg-input-synaptics-lts-raring xserver-xorg-input-vmmouse-lts-raring
  xserver-xorg-input-wacom-lts-raring xserver-xorg-lts-raring xserver-xorg-video-all-lts-raring
  xserver-xorg-video-ati-lts-raring xserver-xorg-video-cirrus-lts-raring
  xserver-xorg-video-fbdev-lts-raring xserver-xorg-video-intel-lts-raring
  xserver-xorg-video-mach64-lts-raring xserver-xorg-video-mga-lts-raring
  xserver-xorg-video-modesetting-lts-raring xserver-xorg-video-neomagic-lts-raring
  xserver-xorg-video-nouveau-lts-raring xserver-xorg-video-openchrome-lts-raring
  xserver-xorg-video-r128-lts-raring xserver-xorg-video-radeon-lts-raring
  xserver-xorg-video-s3-lts-raring xserver-xorg-video-savage-lts-raring
  xserver-xorg-video-siliconmotion-lts-raring xserver-xorg-video-sis-lts-raring
  xserver-xorg-video-sisusb-lts-raring xserver-xorg-video-tdfx-lts-raring
  xserver-xorg-video-trident-lts-raring xserver-xorg-video-vesa-lts-raring
  xserver-xorg-video-vmware-lts-raring
The following NEW packages will be installed:
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
0 upgraded, 11 newly installed, 41 to remove and 0 not upgraded.
Need to get 2,454 kB of archives.
After this operation, 37.3 MB disk space will be freed.
Do you want to continue [Y/n]?
```
**Why?**

How are my raring libraries different to yours? Better question, **why** are they different?

Humor me, here are the details of the first listings it wants to remove:

[TABLE="width: 500"]
[TR]
[TD]libgl1-mesa-dri-lts-raring
[/TD]
[TD]9.1.4-0ubunut0.1~precise2
[/TD]
[/TR]
[TR]
[TD]libgl1-mesa-dri-lts-raring:i386
[/TD]
[TD]9.1.4-0ubunut0.1~precise2
[/TD]
[/TR]
[TR]
[TD]libgl1-mesa-glx-lts-raring
[/TD]
[TD]9.1.4-0ubunut0.1~precise2
[/TD]
[/TR]
[/TABLE]

show me details of these three libraries on your system, please.

---

### Post by Favux on 2013-10-22
Here, look at the output on this bug:  [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1137247](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1137247)

Does that look familiar?  Aside from the fact it is Quantal Precise instead of Raring Precise I mean.

If so that's what I meant.  It looks like they've somehow got some dependencies crosswired.  Probably don't have the package manager pointing to the correct repository.

---

### Post by AussiePozzie on 2013-10-22
That's almost the identical result to what I get!

Pheew, ...and I was beginning to wonder if **I** am the only one on the planet having these problems!

It seems that his is a bug that doesn't only affect one distro, by seems to be systemic.

You reckon if it's any point to add to the above report, with the slant of the wacom.ko issue?

Now, ...yes, we have hit a wall, ...where from here on?

Just wait?

---

### Post by Favux on 2013-10-22
Yep, there we go.  :)

You mean Precise update point release not Distro I believe.  12.04.2 was the lts-quantal and 12.04.3 is the lts-raring.  I guess so labeled because that is the equivalent release that has the kernel and X Server stack Precise was updated to.  And that's why dinking around with an LTS is so suprising.  It's glitches like this you're trying to avoid, and unfortunately are predictable.

So for some reason they have a consistent dependency problem across the two stack updated point releases.  At least some of the stuff labelled with the suffixes lts-quantal and lts-raring.  As if incorrectly cross-linked.  Wouldn't surprise me if it turned out to be a symbolic link problem.

I think I would file a new bug report and link to the fglrx/lts-Quantal bug report.  If they decide it is in fact a duplicate of the issue they'll consolidate it.  But yes, at the least chime in on the current bug report if the bug report process seems a bit much.  This appears to be an easy fix, just requiring them to point things the right way.
> Now, ...yes, we have hit a wall, ...where from here on?

Just wait? 
Given what we now know yes, as long as you are using 12.04.3.  If I understood what all they did for the X Server update and was a package manager guru we could maybe point Apt in the correct direction.  But as things are that is way more of a challenge then I would want to undertake.  And you probably are not real keen on breaking your system again.  :)

---

### Post by AussiePozzie on 2013-10-22
> And you probably are not real keen on breaking your system again.
Yeah, ...you got that right, mate!

On the other hand, I also would like to give the devlopers a hand and some other poor bugger who might blunder into the same trap as I did, ...even in future.

Since I have a virtual machine running, I think I'll install ubuntu 12.04 3 into the virtual machine and let it fail, on purpose, recording all the details of the process and pass it onto the developers.

Maybe the'll listen up, ...let's see.

The waiting is going to be excruciating!

---

### Post by Favux on 2013-10-22
The virtual machine sounds like a good idea.

I wonder if the root cause is on this bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-raring/+bug/1190148](https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-raring/+bug/1190148)

OK I updated the updated [BambooPT HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408&p=619268#p619268").  Let me know what you think.

---

### Post by AussiePozzie on 2013-10-23
I can only read through the instructions, ...I don't have a Bamboo to test the driver after. The instructions **look** alright, ...

Sorry about that.

Having hit the wall at full speed, and still not gotten any furhter, I have decided to scrap 12.04 LTS, until 14.04 LTS is released, and have installed 13.10

In the naive hope, that 13.10 would by some cosimic coincidence have the proper dependencies installed, I downloaded the xf86 driver, extracted it and ran ./configure, only to get the **identical** errors as with 12.04! Fancy that!

After having **manually** installed, via _***synaptic***_, the following dependencies:
> 
[LIST]
[*]                  [             debhelper                            (>=                8)                       ]("https://launchpad.net/ubuntu/saucy/+package/debhelper")
[*]                  [             dh-autoreconf                       ]("https://launchpad.net/ubuntu/saucy/+package/dh-autoreconf")
[*]                  [             libudev-dev                       ]("https://launchpad.net/ubuntu/saucy/+package/libudev-dev")
[*]                  [             libxi-dev                       ]("https://launchpad.net/ubuntu/saucy/+package/libxi-dev")
[*]                  [             libxinerama-dev                       ]("https://launchpad.net/ubuntu/saucy/+package/libxinerama-dev")
[*]                  [             libxrandr-dev                       ]("https://launchpad.net/ubuntu/saucy/+package/libxrandr-dev")
[*]                  [             pkg-config                       ]("https://launchpad.net/ubuntu/saucy/+package/pkg-config")
[*]                  [             quilt                       ]("https://launchpad.net/ubuntu/saucy/+package/quilt")
[*]                  [             xserver-xorg-dev                            (>=                2:1.11)                       ]("https://launchpad.net/ubuntu/saucy/+package/xserver-xorg-dev")
[*]                  [             xutils-dev                       ]("https://launchpad.net/ubuntu/saucy/+package/xutils-dev")
[/LIST]

...yeees, ...one by one finding them, marking them for installations and the installing them, I have _**finally**_ managed to complie that infernal xf86 driver and install it, or at least there were no errors during the whole process, so maybe I'm kidding myself that it actually was installed.

Maybe I am making the mistake of trusting the 'make install' to copy the new wacom.ko into the right place, ...buuut, ...if you thought the worries were over, ...mate, think again!

[SIZE=4]_**The tablet is still not recognized!**_[/SIZE]

Now what?

---

### Post by Favux on 2013-10-23
Great!  Progress.  :)

It looks to me like you may have only compiled the X driver, xf86-input-wacom-0.23.0, at least from the dependencies you list.  You may also need to compile the kernel driver wacom.ko from input-wacom-0.19.0.

I'm groggy from being up late struggling to write an App Indicator for our little Python applet.  Got it partially working which why I am still conscious.  But it is clear the new spec. is very limiting.  You want to talk about hitting the wall.  I have no idea how I'm  going to get it all working again.  This is silly.  What was wrong with the old System Tray and the good old gtk.StatusIcon?  Why do I now have to write 3 separate versions of code for the same stupid thing so it will work in Unity, Gnome Shell, Gnome/KDE?  Not to mention the Unity whitelist.  And of course I have to update the Gnome Shell extension.  I'm about ready to say the H with this nonsense.

Anyway I'm going to go pass out.

---

### Post by AussiePozzie on 2013-10-23
I sincerely hope, that my cry of joy hasn't woken you, ...**no** matter where on the planet you are!

After compiling and installing the wacom.ko, 

_**[SIZE=4]the tablet is recognized![/SIZE]**_

[LIST]
[*] 	 		 			:razz: 		
 	
[/LIST]

Mate, ...what a drag!

Do you want to mark this thread as solved?

---

### Post by Favux on 2013-10-23
Great!  Happy to hear you can now use your Intuos Pro AussiePozzie.  Nice work sticking with it.  That was way more of an adventure than it should have been.

The OP indeable is the only one who can mark the thread as solved.

---

### Post by AussiePozzie on 2013-10-24
Favux, I have tried and succeeded at getting the xf86 and wacom.ko installed on **12.04 LTS**!

What I found, on **both**, 12.04 **and** 13.10, that the dependencies _***cannot***_ be installed from the terminal!

The dependencies for xf86, which I have listed in the 2nd previous post, have a whole lot of other dependencies attached to them, **and**, more importantly, it is imperative to do the installation in _***synaptic***_, as it only knows of these other dependencies and installs them in the correct relationship.

Furthermore, when searching for some of these dependencies, I found that they were listed, but with a **suffix** of raring, or precise etc.

If I made the selection as the list proposed (**ignoring** the suffix), marked them for installation, and them exectued the installation, the window showed that a swag other drivers would be removed!

***Haaalllooo!***  I've seen that **before**!!!

Unmarking it, and choosing the same depencency, but **with** the _***suffix***_ of raring (*for example*), installed just fine.

Now, ...the wacom.ko

The same thing applied to this driver as well: _**dependencies *cannot* be installed from the terminal!**_

If the line
> sudo apt-get install build-essential libx11-dev libxi-dev  x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev  libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
is executed, it will result in drivers being **REMOVED** and the system _***failing after reboot!***_

Since most of the dependencies for wacom.ko got installed already with the dependencies for the xf86, only one dependency was a new installation.

You must have gotten all the right dependcies installed on your system by another application (miraculously), as your screen shots show that you don't get any removals happening. Lucky you.

I think I should write a HOWTO about this, as it appears that it isn't limited to 12.04, but is rather systemic to ubuntu (as the same thing happened in 13.10).

---

### Post by Favux on 2013-10-24
> Unmarking it, and choosing the same depencency, but with the suffix of raring (for example), installed just fine.
If I understand correctly Synaptic is making the same mistake, but you are able to manually correct it in the Synaptic gui.  That it is making the same mistake makes sense to me as it is my understanding that apt-get, Synaptic, and Software Center all share the same package cache.  When you change a package in one the other two are aware of the change, or at least should be.  You can probably accomplish the same thing with apt-get maybe using the -t (--target-release) flag, maybe in combination with other flags, to ensure the Raring suffix.  See the apt-get manual by running **man apt-get** in a terminal.  That's what I meant by saying a package manager guru could probably help you.  I try to avoid the fancy stuff except except when there is no choice.  Like needing to repair a corrupted cache.
```
You must have gotten all the right dependcies installed on your system by another application (miraculously), as your screen shots show that you don't get any removals happening. Lucky you.
```
I may be wrong but I don't think that is what is going on.  If you are seeing this problem in 13.10 also then they introduced a bug in the package management system at some time.  The bug may have occurred in Quantal.  Then Precise LTS became affected when they backported the Quantal kernel and X Server for 12.04.2.  And it persisted through to 12.04.3.  Anyway I think that is more likely to be what is happening from what we've seen so far.  Although I admit it being there on a fresh install of Saucy makes me uneasy.  Hard to believe they'd let it persist that long.  So I might be wrong.

---

### Post by AussiePozzie on 2013-10-24
Sorry mate, ...you didn't get that right.

It isn't synaptic that is making the same mistake, ...the mistake comes from selecting the _**wrong**_ library!
> sudo apt-get install build-essential libx11-dev libxi-dev   x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev   libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
For _*example*_ ***only***, ...if you search in synaptic for xserver-xorg-dev, ...and synaptic lists:


[LIST]
[*]xserver-xorg-dev
[*]xserver-xorg-dev-lts-quantal
[*]xserver-xorg-dev-lts-raring
[/LIST]

and you stubbornly _**presist**_ in picking *xserver-xorg-dev*, ...only because this is what the instruction says, ...then a swag of drivers will be deleted and your system will be destroyed, full stop! If you pick *xserver-xorg-devlts-**raring*** (as in my case _***only***_) **instead**, then it will be installed correctly and you'll end up laughing. I have learned, that picking the latest one, ...even in 13.10, is the better choice.

Equally so, the other dependencies, if you install them through terminal, they will ge installed **all alone** and crash your system, ...but if you install then through synaptic, synaptic will detect **other** dependencies linked to that particular one dependency, and will install them as well, making your system work.

If you're adamant that it wasn't *you* who installed all these dependencies correctly, fine, then there is only this one option left: another app did it for you during it's installation, either entirely, or at least to a sufficient degree, so everything else could be installed after it, ...after all, in our galaxy things don't just happen.

I would think that it's got to do with the ongoing devlopment of things around ubuntu, ...for more capability, the libraries have to be expaned and crosslinked in different fashions to make them work, ...hence this ever changing landscape of dependencies. Just because a particular order of dependencies worked for one kernel and one app, it **doesn't** go to say, that this identical order of dependencies will work with another kernel even with the same app, let alone if the app too is upgraded.

This isn't Windows, ...you know, where the architecture stays the same for **years** on end.

I'm preeety sure, ...that the developers weren't the ones who stuffed up in this instance.

Say, ...you had any exposure to VM's? Since 3.8.0-32 the VM won't start any guest in 12.04 anymore, see [http://ubuntuforums.org/showthread.php?t=2183410&p=12827177#post12827177](http://ubuntuforums.org/showthread.php?t=2183410&p=12827177#post12827177)

---

### Post by Favux on 2013-10-25
Again semantics.  From my perspective:
```
    xserver-xorg-dev
    xserver-xorg-dev-lts-quantal
    xserver-xorg-dev-lts-raring
```
Are all the same library.  The ones flagged with -lts-quantal or -lts-raring are simply different versions of the same library.  Ultimately they should have only different version numbers and release dates.  My point is the package manager should be making that choice for you transparently and that it isn't doing so is a bug.  That is not the users fault.  Apparently in order to get the correct stack with the updated point releases of of Precise, like 12.04.2 or 12.04.3 you yourself have to know to pick -lts-quantal or -lts-raring.  And you shouldn't have to have to do that.  Where is the documentation for that?  Why doesn't the apt-get output have a custom note warning you of the change and directing you to an explanation?
> the other dependencies, if you install them through terminal, they will ge installed all alone and crash your system, ...but if you install then through synaptic, synaptic will detect other dependencies linked to that particular one dependency, and will install them as well, making your system work.
If things were functionally correctly it wouldn't matter which method you used, including apt-get, that should be done for you by which ever package manager you are using.
> If you're adamant that it wasn't you who installed all these dependencies correctly, fine, then there is only this one option left: another app did it for you during it's installation, either entirely, or at least to a sufficient degree, so everything else could be installed after it, ...after all, in our galaxy things don't just happen.
And this is where you lose me.  My reaction is **what!?**  I've been compiling things, including the wacom drivers, in Ubuntu since Hardy and this is the first time I've seen anything like this.  As far as I am concerned this is new behavior.

The one caveat is now you are telling me this is true also in Saucy?  Remember I compiled the wacom drivers in both Precise and Raring without seeing this.
> Since 3.8.0-32 the VM won't start any guest in 12.04 anymore, see [http://ubuntuforums.org/showthread.php?t=2183410&p=12827177#post12827177](http://ubuntuforums.org/showthread.php?t=2183410&p=12827177#post12827177)
I guess that makes me think "more of the same".  Feel a real lack of enthusiasm about wandering down into that hole.

---

### Post by AussiePozzie on 2013-10-28
There is a nifty front end for wacom tablets adjustment, ...I am particularly after the **mapping** option, called kde-tablet-config.

As you can see, it is written for kde, ...I can install it in ubuntu but can't find the lauch command for it.

Anything you crossed path with?

I have another application k3b, a CD/DVD writer, installed, also written for kde, but it launches just like any other application in ubuntu.

Why doesn't the tablet configuration?

By the way, the wacom tablet configuration that is standard in ubuntu, doesn't lauch the kde and it isn't affected in any way by the installation of kde-tablet-config.

---

### Post by Favux on 2013-10-28
Well k3b probably just uses the KDE Qt toolkit but nothing else KDE specific, which is why it runs.  The Qt and Gnome's Gtk are the graphical toolkits app.s use to draw on the screen.  Now that Qt is OSS they've been integrating support for both on Gnome or KDE based desktops.  Not sure if that's the Distros or upstream, probably both.

The kde-tablet-config is part of the KDE System Settings just like the Wacom tablet applet is part of the Gnome System Settings.  That means it probably needs at least one KDE specific daemon to communicate through dBus and so on.  Just like the Gnome applet needs a Gnome daemon.  I don't know that you can run a KDE daemon in a Gnome based desktop.  Tend to doubt it.

To find out and also answer your question run:
```
kcmshell4 --list
```
In the output you'll find the Wacom KCM module is called **kcm_wacomtablet**.  You run it by proceeding it with **kcmshell4** like so:
```
kcmshell4 kcm_wacomtablet
```
For more information:
```
kcmshell4 --help
```

---

### Post by AussiePozzie on 2013-10-28
Here is the output of kcmshell4 --list:
```
smaragd@smaragd:~$ kcmshell4 --list
The following modules are available:
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(4326) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(4326) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(4326) kdemain: Emitting notifyDatabaseChanged ()
componentchooser       - Choose the default components for various services
device_automounter_kcm - Configure automatic handling of removable storage media
emoticons              - Choose Emoticon Theme
filetypes              - Configure file associations
icons                  - Customize KDE Icons
k3bsetup               - K3bSetup – modify permission for CD/DVD burning with K3b
kcm_activities         - Configure the activities system
kcm_attica             - Manage Social Desktop Providers
kcm_kdnssd             - Configure service discovery
kcm_nepomuk            - Nepomuk Server Configuration
kcm_phonon             - Settings for the Phonon multimedia framework
kcm_ssl                - SSL Versions and Certificates
kcm_wacomtablet        - Wacom Tablet Settings
kcmcgi                 - Configure the CGI KIO slave
kcmkded                - KDE Services Configuration
kcmnotify              - System Notification Configuration
kcmtrash               - Configure trash settings
language               - Language, numeric, and time settings for your particular region
spellchecking          - Configure the spell checker
smaragd@smaragd:~$ kcmshell4 kcm_wacomtablet
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Object::connect: No such signal QDBusAbstractInterface::tabletAdded()
Object::connect:  (receiver name: 'KCMWacomTabletWidget')
Object::connect: No such signal QDBusAbstractInterface::tabletRemoved()
Object::connect:  (receiver name: 'KCMWacomTabletWidget')
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.69'
smaragd@smaragd:~$ 
```
As you can read that the
> kcm_wacomtablet        - Wacom Tablet Settings
is listed, but when the command 
> kcmshell4 kcm_wacomtablet
is issued, then is returns with:
> Object::connect: No such signal QDBusAbstractInterface::tabletAdded()
Object::connect:  (receiver name: 'KCMWacomTabletWidget')
Object::connect: No such signal QDBusAbstractInterface::tabletRemoved()
Object::connect:  (receiver name: 'KCMWacomTabletWidget')
So it appears to be the issue that
> I don't know that you can run a KDE daemon in a Gnome based desktop.  Tend to doubt it.
is most likely true, as the window shows the error:
> KDE tablet service not found
Pity, ...has several useful features.

You perhaps aware of a workaround? Some cheat or something the like?

---

### Post by Favux on 2013-10-28
Sorry, no.  I have it installed in my Kubuntu 12.04.

But the default Kubuntu 12.04 version didn't work with my BambooPT which a year ago was "new".  I had to upgrade it to version 2.0 (came out 5-9-13?).  Used this PPA:  [https://launchpad.net/~maret/+archive/wacom](https://launchpad.net/~maret/+archive/wacom)  Also have to update xf86-input-wacom to at least 0.20.0 (came out 3-4-13) as they tell you to on:  [http://kde-apps.org/content/show.php?content=114856](http://kde-apps.org/content/show.php?content=114856)  That all took a while as you can see from the dates but now everything is functioning.

But I don't think it would matter for you anyway.  I doubt your new tablet is yet in its data base.  So I'm not sure how much functionality it would give you anyway.  Although the dev.s have been responsive and helpful and I've seen them help folks write data base entries for new tablets.  At some point I think they plan to switch the data base to libwacom, which I believe already has the entry for your tablet.

---

### Post by AussiePozzie on 2013-10-29
Sorry mate, I don't quite follow, ...is it not connecting due to


[LIST]
[*]**installation error**, or
[*]due to  the database **not** containing **my** tablet?
[/LIST]

I have done the installation of the kde-tablet-config only yesterday, and it installed without any errors (or at least it didn't show any). The xf86 was installed on the weekend, hence I deem myself safe with having gotten the recent files.

---

### Post by Favux on 2013-10-29
I was trying to say even if you installed a KDE Desktop such as Kubuntu so the KDE Wacom applet works, your Pro tablet won't work without a data base entry.  So I'm not sure how useful it would be to get the KDE Wacom applet running in Gnome, assuming that was possible.

But supposing you want to install a KDE Desktop, which would be a big change just for the one applet.  You could take the data base entry for the Pro from libwacom and try to translate the information there into the same format as the KDE applet's tablet data base entries.  And if having trouble with that ask the KDE Wacom applet dev.s for help.  Maybe even google to see if someone already did it.

---

