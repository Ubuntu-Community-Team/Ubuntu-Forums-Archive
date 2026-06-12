---
title: "Feisty Fawn on Thinkpad X61"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by mfbernstein on 2007-07-17
Just installed Ubuntu on a new Thinkpad X61. Results were mostly positive, and I was particularly pleased at the number of small things that 'just work' out of the box. A few observations and questions:

1) I don't have a CD-ROM drive for the machine, so I used the USB stick method. This worked reasonably well, except that even after I pointed the installer to an ISO image (which it recognized), it continued to complain about a failure accessing the CD-ROM. In the end, it actually did a net-install of everything. I'm thinking I probably should have disabled the IDE CDROM option module in the installer, but still, this was a bit unhelpful.

2) As with the T61, the new SATA controller causes problems: the installer hangs in the disk detection stage. Setting the SATA mode to 'compatibility' instead of 'AHCI' in the BIOS worked around that.

3) Post-install, sound appeared to be enabled, but there was no actual output. Searching around led me to a number of pages dealing with the Intel HDA sound driver (AD1984 in this case). Unfortunately, upgrading ALSA to 1.0.14 manually results in Kernel Panics from the intel_hda_snd module. So no solution to that yet.

4) Suspend on the stock install did not work (lcd backlight is off when system resumes). Added acpi_sleep=s3_bios seems to have fixed that. External USB devices must be unplugged and replugged however.

5) Hibernation fails, with no devices attached. I haven't investigated further.

6) Screen brightness controls pop up a little applet, but don't actually do anything to the brightness.


All that said, overall a great piece of software, and hopefully these few quirks can be easily dealt with.

Thanks.

---

### Post by sheol on 2007-07-18
Convenient that you started this thread, because I was just about to do the same thing.
I purchased the x61s and have installed Kubuntu on it.
Hopefully we can document all the problems and solutions here.

I also had problems with the new SATA controller, as you described.  Solution is simply to go into bios and change it to "Compatability mode".

I also have not yet figured out how to solve the sound problem.

Hibernate works for me.  Sleep works too.

Video: Thinks its vesa out of the box.  When you tell xorg that it's intel, KDE still says its vesa.  OpenGL not working.
Reconfiguring Xorg and telling it it has an intel chipset enables direct rendering but trying to use and openGL application gives a black screen,  restarting the computer seems to be the only way to get out.

Haven't tested all the function keys but fn+f2 fn+f4 and fn+f8 all work.


If anyone has any suggestions on the graphics card or the sound that would be great.

---

### Post by christian.betz on 2007-07-18
I have an X60 (not X61) which Ubuntu installed mostly just fine on. And so I recommended to my girlfriend that she get an X61. Bad idea--- I spent all last night fighting the following issues:

a) Disk Drive not detected: Thanks a lot to the first poster! Setting compatibility mode did allow the SATA disk to be detected.

b) Sound did not work out of the box, but I did eventually get it working. I had to grab the latest development version of of alsa-driver and alsa-kernel. I mostly followed these directions: 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

However, after downloading the tarballs and building everything, it still did not work. I had to install mercurial and use it to fetch the latest development source (instructions are on the alsa development wiki). That worked.

See this posting to the alsa-devel list:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001898.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-July/001898.html)

I used the option model=thinkpad (mentioned in the first link) and then rebooted.
Hopefully this will get into a real ubuntu package at some point -- but I'm not holding my breath and you might not want to either.

c) OpenGL doesn't work: I think it is using VESA too, but I didn't get that far. GL desktop effects do not work at all (they are fine on my X60). I am going to investigate this one tonight.

We'll get all this stuff sorted out soon enough!

---

### Post by anthony_barker on 2007-07-18
I was thinking of picking up one of these (currently still using an old but reliable IBM x24).


What about the touch screen?
Can you get the screen to rotate?
Get get evtouch and evdev to work?
handwriting recognition?
Anyone get gok, dasher working?

Cheers

Anthony

---

### Post by sheol on 2007-07-18
Progress!

I got OpenGL to work!

by:
```

sudo nano /etc/apt/preferences
```

enter:
```
Package: *
Pin: release a=feisty
Pin-Priority: 700

Package: *
Pin: release a=gutsy
Pin-Priority: 200
```

save & exit

```

sudo nano /etc/apt/sources.list
```
save & exit

type:
```
sudo apt-get update
sudo apt-get -t gutsy install xserver-xorg-video-intel
sudo apt-get -t gutsy install linux
sudo apt-get -t gutsy install libgl1-mesa-dri
```


```

sudo nano /etc/X11/xorg.conf
```

*************************************************************
* Update: This Section appears to be unnecessary
*************************************************************
     *  Add the following section to your xorg.conf 
```
Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection
```

    *  Then in the "Device" section add the following line: 
```

Option "monitor-TV" "TVOutput"
```
*******************************************************************
* End unnecessary section
******************************************************************* 

This is from: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61")

I am getting an occasional starnge effect, for example, I have firefox open above the screen saver section of the kde settings, and I am seeing the screen saver thumbnail through the browser.

---------------------------------------------------------------------
Update: This also works for Debian, repositories are:
[ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) experimental
(Simply replace the preceding uses of gutsy with that)
---------------------------------------------------------------------

btw: christian.betz, could you explain in greater detail how you got sound working?

---

### Post by sheol on 2007-07-19
So there seems to remain only a couple of problems:

If anyone has any ideas about how to solve these problems please post them here.

1. The previously mentioned solution to the sound problem is too difficult for many linux users.

2. The previously mentioned OpenGL fix, has a bug where it displays the OpenGL program through windows that aught to be blocking the display.

If anyone has any other issues with these laptops or suggestions for solving the above problem.  please help.

---

### Post by Antioch on 2007-07-19
To the user who wanted to get a tablet working: So far as I know *no* tablet features are available on linux.

As for the sound, I've heard that the sound works in Gusty (so it's all a matter of backporting the newest ALSA drivers any maybe kernel).

Graphics, there is a thread [http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943) which talks about how to get the latest Intel backport drivers and all of the 3D working. If you need more info about getting graphics to work try searching for a T61 thread (it's rather long and talks about getting everythign to work). You should also try searching for all threads started by the OP of the thread I linked - he seems to be active in the pursuit of getting X3100 to work flawlessly in Feisty.

Hibernation/Suspend is tricky to get working perfectly in my experience. Try checking thinkwiki.org and looking at T61 install how-to's to see if any of them have it working.

The Santa Rosa chipset (which the X61, T61, R61 are based on) is very new and will take a little bit of time to be supported by linux. However, unlike the old days of Linux, this support should come fairly quickly - expecially considering the fact that Intel works with Canonical (and another company) on linux kernel and driver development. So fear not! I'm sure that these issues will all be completely ironed out when Gusty Gibbon takes her golden flight :KS

---

### Post by sheol on 2007-07-19
Thank you Antioch.

As you can see from the thread the 3D problem has been solved.  The quirkiness is at issue, unfortunately no one has yet confirmed my solution or quirks.

I attempted to grab the ALSA drivers from gutsy, and it seemed to have no effect.  If you could tell me exactly what alsa packages in gutsy are supposed to work I would happily test them.  Unfortunately from what I can tell the alsa driver that supports the X61 is a snapshot, not the latest release, which means it is highly unlikely that it is currently included in the gutsy release.  Our hope for it to be included in Gutsy is entirely dependent on it being released well before the 16th of august.

mfbernstein reports that hibernate and suspend do not work, I am using Kubuntu, and they do work.  It would be interesting if someone could explain the difference.

Yes, I am sure that this will all be sorted out in an official manner soon enough.  If I wasn't willing to put in the time and effort to play with config files I never would have dreamed of getting a new laptop that wasn't officially Linux ready. However in the meantime we have to settle for hacks and work-arounds.

---

### Post by Antioch on 2007-07-20
I believe the ALSA drivers from gusty aren't up to date based on the note that this how-to talked about:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#Can_you_hear_me_now.3F...._What.3F_.28Solved.21.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#Can_you_hear_me_now.3F...._What.3F_.28Solved.21.29)

Check it out. He got the new ALSA drivers working fine. The trick is not only to upgrade to the newest version (10.0.14) but to also apply a few patches that were released at the same time and as such appear to be similar(?). 

He has, in addition to the fix, posted a link to fix the AD1984 as well as T61/X61 sound outputs.

If you do what he did it should work! =D

If not, try looking around and contacting the OP of the thread I linked earlier. Many people (Including that OP) have the same GM965 chipset and have gotten sound working.

---

### Post by sheol on 2007-07-20
> **Antioch said:**
> I believe the ALSA drivers from gusty aren't up to date based on the note that this how-to talked about:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#Can_you_hear_me_now.3F...._What.3F_.28Solved.21.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61#Can_you_hear_me_now.3F...._What.3F_.28Solved.21.29)

Check it out. He got the new ALSA drivers working fine. The trick is not only to upgrade to the newest version (10.0.14) but to also apply a few patches that were released at the same time and as such appear to be similar(?). 

He has, in addition to the fix, posted a link to fix the AD1984 as well as T61/X61 sound outputs.

If you do what he did it should work! =D

If not, try looking around and contacting the OP of the thread I linked earlier. Many people (Including that OP) have the same GM965 chipset and have gotten sound working.

Yes, I've seen this, however I can't really follow what he is doing.  If someone could break it down for us that would be wonderful.

---

### Post by sheol on 2007-07-20
THIS WORKS!

Okay I have figures out how to get the alsa drivers and patch them:
( this is from [http://forums.fedoraforum.org/showthread.php?t=159516]("http://forums.fedoraforum.org/showthread.php?t=159516") )

download latest alsa tarball from [here]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")

download attached patch file

```
sudo tar jxvf alsa-driver-1.0.14.tar.bz2
sudo tar zxvf patch_analog.c.tar.gz
sudo cp ./patch_analog.c ./alsa-driver-1.0.14/alsa-kernel/pci/hda/
cd alsa-driver-1.0.14
sudo ./configure && sudo make
sudo make install 

```

You need to edit some configs too:
```

sudo nano /etc/modprobe.d/alsa-base

```
go to bottom and add:
```

options snd-hda-intel model=thinkpad

```

---

### Post by sheol on 2007-07-20
I tried the above, at first it didn't work.
After doing it you need to do the following things:

run alsamixer in the command line and unmute everything by hitting "M"

make sure you are in the audio group by selecting Users and Groups in the system settings.

reboot.

If you still don't have sound make sure you have ALSA selected in your sound settings

---

### Post by drocko on 2007-07-20
Hello,

I'm working on getting my X61 Tablet up and running and am having some similar issues as the rest of you it seems. 

Currently I am working on getting the tablet operational. udev can see the tablet device but is not creating /dev entries for it. Here is what udev knows about the tablet:

 ```

 udevinfo -a -p /devices/acpi_system:00/device:00/PNP0A08:00/device:01/WACF008:00

looking at device '/devices/acpi_system:00/device:00/PNP0A08:00/device:01/WACF008:00':
    KERNEL=="WACF008:00"
    SUBSYSTEM=="acpi"
    DRIVER==""
    ATTR{hid}=="WACF008"
    ATTR{path}=="__SB_.PCI0.LPC_.DTR_"
```

I've tried to create udev rules to force it to make a /dev/ entry. Anyone have any leads on doing this?

Thanks

---

### Post by sheol on 2007-07-22
Okay, the main things are fixed.
The following are still problems:
The volume control on the laptop stop at 10%.

video card display quirkiness:
  KDE load up screen gets cleared and then only changed parts redrawn
  OpenGL applications can be seen through blocking windows

Working function keys:
func+f3 = display battery information
func+f4 = suspend
func+Pgup = keyboard light
func+ScrLk = maps keys to allow 10 key

Non-working Function keys:
func+f2 = no effect (should be lock screen?)
func+f5 = no effect (should be disable/enable wireless?)
func+f7 = no effect (should be ?)
func+f8 = no effect (should be ?)
func+f12 = no effect (should be hibernate ?)
func+home = no effect (should be brighten screen)
func+end = no effect (should be dim screen)
func+space = no effect (should be zoom ?)
func+sysrq = no effect (should be ?)
func+Pause = no effect (should be break)

if anyone has any ideas...

---

### Post by drocko on 2007-07-22
> **sheol said:**
> THIS WORKS!

Okay I have figures out how to get the alsa drivers and patch them:

```
sudo tar jxvf alsa-driver-1.0.14.tar.bz2
sudo tar zxvf patch_analog.c.tar.gz
sudo cp ./patch_analog.c ./alsa-driver-1.0.14/alsa-kernel/pci/hda/
cd alsa-driver-1.0.14
sudo ./configure && sudo make
sudo make install 

```



Great stuff! Thanks for this. Now i have sound! Note that you should not need to run configure or make with sudo. best practice is to run those as the regular user and only run make install as the super user.

I have discovered some more thinks about the tablet in the x61t and I am about to try some things to get that up and running correctly. I will post the results of my testing.

---

### Post by drocko on 2007-07-22
More from the X61t front... I have the tablet working! I'd say it's a bit of a hack and not for the squeamish. I'll work to get this submitted as a patch.

Here's the deal:

The X61t's tablet is a Wacom device that is connected via a serial connection. (Originally I thought it was USB, my bad). It won't work out of the box in Feisty because the device is too new. Here's what you can do to get it up and running:

1. Install wacom-tools and xserver-xorg-input-wacom
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
```

2. Install the kernel source for the kernel that you are running. I had upgraded to Gutsy's kernel 2.6.22 but this should work if you are on Feisty's as well.

3. Prepare to compile your own kernel. I used directions from [this site.]("http://howtoforge.com/roll_a_kernel_debian_ubuntu_way") 

4. You'll need to modify the source code for the 8250_pnp module:
```
vi /usr/src/linux/drivers/serial/8250_pnp.c
```
Look for this:
```
  /* Wacom tablets */
  { "WACF004",    0 },
  { "WACF005",    0 },
  {       "WACF006",              0       },

```
and add
 ```
  {       "WACF008",              0       }, 
```
right below it.

What this does is let the kernel know that the device you have is actually a Wacom tablet connected via serial and that the kernel should use the serial driver for it.

5. Compile and install the kernel. Follow the instructions on that webpage and you'll end up with a .deb package that will allow you to easily install and remove it in case there are problems.

6. While you wait for the kernel to compile you should modify init script for the Wacom xorg driver. 

```

sudo vi /etc/init.d/xserver-xorg-input-wacom

```

Change line 16 to add WACf008*. make it look like this:
```

WACf008*|WACf006*|WACf005*|WACf004*)

```

This will make your tablet appear at /dev/input/wacom at boot.

7. Check /etc/X11/xorg.conf to make sure that all the tablet devices are looking for the tablet at /dev/input/wacom.

8. Reboot and use the tablet!

I'm not sure if this is totally complete so if someone else gets a chance to try this let me know what kinds of problems they run into.

Now that I've got that up and running I'm going to move to creating scripts for xrandr (hey, it's a tablet), sleep and hibernate, getting more of the Thinkpad buttons working, getting the Cingular (AT&T now?) WWAN adaptor up and running, and testing bluetooth.

I'll report in soon... Good luck everyone!

---

### Post by walrus_t on 2007-07-22
I get "C compiler cannot create executables" when i try your method. Any help please? :) Thanks!

---

### Post by walrus_t on 2007-07-22
I get "C compiler cannot create executables" when i try your method (exactly when i type "sudo ./configure"). Any help please? :) Thanks!

---

### Post by drocko on 2007-07-22
> **walrus_t said:**
> I get "C compiler cannot create executables" when i try your method (exactly when i type "sudo ./configure"). Any help please? :) Thanks!
walrus_t,

Sounds like you have a problem with your system. Check to see if compilers are installed by running this command:

```
dpkg --list | grep gcc
```

you should see something like:
```

ii  gcc                                        4.1.2-1ubuntu1                         The GNU C compiler
ii  gcc-3.3-base                               3.3.6-15ubuntu1                        The GNU Compiler Collection (base package)
ii  gcc-4.1                                    4.1.2-0ubuntu4                         The GNU C compiler
ii  gcc-4.1-base                               4.1.2-0ubuntu4                         The GNU Compiler Collection (base package)
ii  libgcc1                                    4.1.2-0ubuntu4                         GCC support library

```

If you do not then there is possibly a bigger problem. This is on a fresh install of Feisty? You are on an X61?

---

### Post by walrus_t on 2007-07-22
I'm on X61s, and yes, i can see the lines you're talking about.
Here is the exact output i get:

$ sudo ./configure && sudo make
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

File is attached below :) Thanks again for any help (and sorry if these are stupid questions: i'm quite noob :))

---

### Post by drocko on 2007-07-22
walrus t,

Try it without sudo and try installing the kernel-headers package for your kernel. You should also do a bit of Googling for this error. It is common and many things can cause it.

Best of luck!

---

### Post by walrus_t on 2007-07-22
Oh, just edited my last message.
And, oh , yes, it is a fresh install (with Desktop Cd - for i386)
I'll try googling :)

**EDIT: somehow, installing g++ solved this issue:) It is compiling right now, i'm so happy! Thanks thanks thanks!**

---

### Post by Tobba25 on 2007-07-23
Dammit!

I tried installing this g++ thing, but the computer suddenly asks me for the Ubuntu CD!? I dont have that anymore! So I tried burning a new one, but it wont take it.

What to do?

---

### Post by ny_NEx on 2007-07-23
If you get error C cannot create excutables you should try this:

sudo apt-get update
sudo apt-get install build-essential

Hope this helps...

And for sound to work i did what is written here plus instead 

options snd-hda-intel model=thinkpad

i have to do this;

options snd-hda-intel index=0 model=thinkpad

"Then Reboot your machine and then open Gnome Volume Control. Click on the the "Switches" tab and then check Headphone and Speaker."

---

### Post by walrus_t on 2007-07-23
I now have sound on Feisty, on my X61s **but** volume keys (volume up key, and volume down key) doesn't work: if i press one, i can see the volume level increase or decrease but sound level just stay the same.
Only mute sound key seems to work.
Do you have any idea to fix it?:confused:

---

### Post by mbsullivan on 2007-07-23
Another X61 Question:

Has anybody tried messing around with CPU frequency scaling, yet? The following module, which should work for Core 2 Duos, fails for me:

```
sudo modprobe speedstep-centrino
```

A possible workaround is to use the following:

```
sudo modprobe acpi-cpufreq
```

However, speedstep should work... what's the deal?!?

Mike

---

### Post by sheol on 2007-07-23
> **Tobba25 said:**
> Dammit!

I tried installing this g++ thing, but the computer suddenly asks me for the Ubuntu CD!? I dont have that anymore! So I tried burning a new one, but it wont take it.

What to do?

```

sudo nano /etc/apt/sources.list

```

find the line that reads something like

```

deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted

```

comment it out by adding a # to the front of it.

```

sudo apt-get update
sudo apt-get upgrade

```

install g++

---

### Post by sheol on 2007-07-23
> **walrus_t said:**
> I now have sound on Feisty, on my X61s **but** volume keys (volume up key, and volume down key) doesn't work: if i press one, i can see the volume level increase or decrease but sound level just stay the same.
Only mute sound key seems to work.
Do you have any idea to fix it?:confused:

The problem is that kmilo is not compatable with the hardware, so I apt-get removed it.
Instead I installed tpb, and then mapped my keys in my volume control, however this allows sound control to work, it kills you ability to mute.

---

### Post by mbsullivan on 2007-07-23
> Working function keys:
func+f3 = display battery information
func+f4 = suspend
func+Pgup = keyboard light
func+ScrLk = maps keys to allow 10 key

Non-working Function keys:
func+f2 = no effect (should be lock screen?)
func+f5 = no effect (should be disable/enable wireless?)
func+f7 = no effect (should be ?)
func+f8 = no effect (should be ?)
func+f12 = no effect (should be hibernate ?)
func+home = no effect (should be brighten screen)
func+end = no effect (should be dim screen)
func+space = no effect (should be zoom ?)
func+sysrq = no effect (should be ?)
func+Pause = no effect (should be break)

if anyone has any ideas...

I am working off of a Server CD install, and I have some questions for those of you who got some of the function keys working... What modules / packages did you have to install, and what do you have running?

I've installed the ACPI, ACPI_Support and ACPID packages, have acpid running, and have the thinkpad_acpi module loaded.  However, none of the keys respond -- is there anything else that is needed that I'm missing?  

Mike

---

### Post by sheol on 2007-07-23
> **mbsullivan said:**
> I am working off of a Server CD install, and I have some questions for those of you who got some of the function keys working... What modules / packages did you have to install, and what do you have running?

I've installed the ACPI, ACPI_Support and ACPID packages, have acpid running, and have the thinkpad_acpi module loaded.  However, none of the keys respond -- is there anything else that is needed that I'm missing?  

Mike

I think tpb or kmilo should allow you to map a few keys, but so far I haven't been able to get many of them working.

---

### Post by drocko on 2007-07-23
I've gotten some things to work via tpb, but I'll post more when I have good solutions for all of it.

I have been working on making the Cingular WWAN device operational. I'm getting close, but I'm not there yet. Here's what I've done:

1. Run lsusb to get the detauls on the wireless card that's in the laptop. This is the line we care about:
```
Bus 004 Device 002: ID 1199:6813 Sierra Wireless, Inc. 
```
Apparently the 1199 number is the vendor identifier and the 6813 is the model identifier.

2. This card is controlled by a kernel module named sierra. On my system the module was up to date. Fortunately/unfortunately for us our laptops are from the future. You'll need to make 2 changes to the modules source (These are similar to the ones I had to make for the Wacom tablet).  I downloaded the code for the module from the[ Sierra Wireless website.]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=602") 

3. Edit sierra.c. Early in the code you'll see a list of the cards it supports by identifier number. I only found cards up to 6812. Remember how ours is a 6813? 

Add the second line here. You'll need to do this after lines 67 and 93.
```

{ USB_DEVICE(0x1199, 0x6812) }, /* Sierra Wireless MC8775 */ 
{ USB_DEVICE(0x1199, 0x6813) }, /* X61 Mystery Wireless device */

```

4. Make the module per the instructions.
```

make
sudo make install

```

5. It didn't install the module for me so I copied it to the proper spot myself.
```

cd /lib/modules/`uname -r`/kernel/drivers/usb/serial
sudo cp sierra.ko sierra.ko.old
sudo cp /path/to/sierra/sources/sierra.ko .
sudo depmod -A 

```

6. insert the module into the kernel
```

sudo modprobe sierra

```

A bunch of new entries should show up in /dev. For me the modem is /dev/ttyUSB0. 

I tried using the pppd and chat scripts that came in that Sierra package but have had no luck so far. I feel like I'm close but can't quite get there. If anyone has any ideas or luck with this let me know.

Good luck x61rs...

---

### Post by mbsullivan on 2007-07-25
Hi all,

Just wanted to share a bit about the x61 hotkeys... In my case, no hotkeys worked "out of the box".  However, using thinkpad_acpi, they generate ACPI events, and therefore are mappable to your own scripts as follows:

MAPPING x61 HOTKEYS:

(1) make sure that the thinkpad_acpi kernel module (or ibm_acpi for slightly older kernel versions) is loaded.  If not, load it:

```
sudo modprobe thinkpad_acpi
```

(2) make sure that /proc/acpi/ibm/hotkey is enabled with all of the keys masked:

```
sudo -s
echo "enabled" > /proc/acpi/ibm/hotkey
echo "0xff9f" > /proc/acpi/ibm/hotkey

```

(3) make sure that when you press the function keys, they are generating an acpi event:

```
sudo tail -f /var/log/acpid
```

When you hit Fn+F1, the following should be generated:

> [Wed Jul 25 13:28:10 2007] received event "ibm/hotkey HKEY 00000080 00001001"
[Wed Jul 25 13:28:10 2007] notifying client 4681[0:0]
[Wed Jul 25 13:28:10 2007] completed event "ibm/hotkey HKEY 00000080 00001001"

The event string (ibm/hotkey HKEY 00000080 00001001) is needed to assign an event when the key combination is pressed.

(4) there should already be scripts in /etc/acpi/events for ibm-hibernatebtn and others.  If there aren't install acpi_support.

Modify the unworking scripts to point to ones which may work for you.  I've attached some which I'm still tinkering with, but that work reasonably well so far.  I don't have any USB devices, but I assume that more commands would be needed to reload them after hibernation or sleep.

(5) restart acpid:

```
sudo /etc/init.d/acpid restart
```

LOCKING THE SCREEN:

Also, if you would like to make a script to lock the screen (with xlock or xscreensaver or whatever) you may do so.

However, because the script will be run as root (through acpid), you must explicitly run the lock under your username, since (by default) there is no "root" account, per se:

```
sudo -u [your username] /usr/bin/xlock
```

I've attached an example script that could be used as the action from the "lock" key.

BRIGHTNESS KEYS:

The brightness keys do not have any scripts in /etc/acpi/events by default.  However, using /var/log/acpid, their event strings can be found.  They are:

[brightness up]: video LCD0 00000086 00000000
[brightness down]: video LCD0 00000087 00000000

You can create new event scripts yourself which accept this event, and take the action of brightening and dimming the display.

CHANGING DISPLAY BRIGHTNESS:

Can be done in (at least) two ways:

(1) through thinkpad_acpi:

```
echo "up" >/proc/acpi/ibm/brightness
```

or

```
echo "down" >/proc/acpi/ibm/brightness
```

This allows for seven levels of brightness.

(2) for more control, there is a program named xbacklight. Deb packages can be found in some Ubuntu repositories, or the program is freely available online.  In this case, the commands:

```
xbacklight -inc 10%
```

and

```
xbacklight -inc 10%
```

would work, although you may have as fine grained control as you would wish.  Xbacklight appears to allow the screen to be ~7% brighter than /proc/acpi/ibm/brightness, and gets as dark as you want, so it is the method that I prefer.

Hope this helps!
Mike

---

### Post by drocko on 2007-07-25
mbsullivan,

Very cool! I will be trying these things soon!

I got my WWAN to work. Not sure what really did it, but after banging my head on the wall trying to make it connect I removed the SIM, put it in my phone, and returned it to the computer. The SIM didn't work in my phone so I have a feeling just reseating it did the trick. Either way I was able to get online and get about 800 kbps!

---

### Post by skier on 2007-07-25
When I put the X61 in "sleep" using Fn-F4, when you wake up the X61 the display becomes so dull that you can barely read the screen.  How are you getting the display back to normal?

Thanks!

---

### Post by Rossimo on 2007-07-26
I've rolled my own kernel and have gotten the stylus to work, but the wireless no longer starts. Is there any way I can get the restricted modules to work with the new kernel?

---

### Post by drocko on 2007-07-26
Rossimo,

I'm glad you got the stylus working! You'll have to recompile those wireless drivers yourself with the new kernel source to get that to work. Just follow the guide for those again.

Good luck.

---

### Post by volyblmn on 2007-07-27
I finally got the stylus to work too, but I don't think my wireless ever worked.  How exactly to I recompile in order to get the wireless card to come alive?  I skimmed through all how-to's other than the tablet portions so I'm not sure if I skipped a part about getting wireless online.  Thanks for all the info people!

---

### Post by victorgreen on 2007-07-27
Well, thanks to the instructions on this forum and on the installing 7.04 on T61 thinkwiki, my friend who is infinitely more skilled than me and I have gotten most features to work. 

While the function keys for hibernate and sleep will cause the comp to try and do so, hibernate and sleep dont work- the fan continues to run and everything... After trying to make it sleep the lock screen menu comes up, but fn f2 has no noticeable affect. 

The auto fan speed control refuses to react to increased cpu temps from compiling stuff- its easy enough to do manually, but it would be nice if the auto actually worked...

My friend is writing a script for more fn keys to complement the other post about getting them to work. 

The open gl fix on the first page of the forum cut down on weird graphical artifacts in the Ubuntu loading screen, but they are still present in the Ubuntu shutdown screen. 

Does anyone know how to lower cpu speed or turn off one core when not in use etc to save power? I know xp on my g41 allows you to run the cpu at ultra low speed. 

I still havnt got wifi to work, but it should prove easy enough with the drivers for intel abg 3945 on sourceforge. 

These forums are amazing, thanks to everyone who posted instructions.

---

### Post by victorgreen on 2007-07-28
To the user who couldn't get the volume control buttons working- go into preferences sounds and at the bottom where ALSA should be selected, be sure to select the first entry on the list PCM. Once pcm was selected, my volume control buttons worked great. 

Apparently I have the intel 4965 wifi card, I tried the development drivers from intel but they distressed my kernel to the point of failure to boot and the module had to be blacklisted. Has anyone gotten the darn thing to work??

Oh, has anyone gotten google earth to function with the open GL fix on the first page? 10 seconds after I open google earth X crashes. 

Slowly more and more bits of this darn laptop are functioning.

---

### Post by walrus_t on 2007-07-28
Thanks, it works like a charm!

---

### Post by mbsullivan on 2007-07-30
> Apparently I have the intel 4965 wifi card, I tried the development drivers from intel but they distressed my kernel to the point of failure to boot and the module had to be blacklisted. Has anyone gotten the darn thing to work??

The Intel drivers work for me with vanilla kernel v2.6.22.1, ucode 4.44.17, iwlwifi 0.1.2 and mac80211 9.0.2.  Rough directions follow:

```
(1) follow mac80211 instructions:

    (1a) make .deb of kernel file (see another HOWTO for kernel compilation)
            - processor type: Core II
            - MAC80211 debugging enabled
            - MAC80211 module

    (1b) boot to .deb

    (1c) make; make patch_kernel in mac80211 folder

    (1d) goto /lib/modules/`uname -r`/build

    (1e) make modules modules_install

    (1f) make all; make install

    (1g) reboot

    (1h) sudo modprobe mac80211

(2) get latest ucode and drivers

(3) extract ucode, cp to /lib/firmware, chomd +x ucode

(4) make drivers (in iwl4965 folder)

(5) make install drivers (in iwl4965 folder)

(6) change /bin/sh to /bin/bash in load, unload

(7) sudo ./load

(8) drivers should operate normally
```

Let me know if anything else needs explanation.  In the meantime, the Intel Windows drivers work fine with ndiswrapper.  Follow the directions below:

```
(1) install ndiswrapper-common, etc from repositories

(2) download windows drivers and extract, keep NETw4x32.INF

(3) sudo ndiswrapper -i NETw4x32.INF

(4) sudo ndiswrapper -l

(5) sudo ndiswrapper -m

(6) sudo modprobe ndiswrapper
```

The first method is preferred, due to its minimal resource usage with the wireless card enabled.  Ndiswrapper consumed ~5-7% of one core at all times for me.  It is a pain having a kernel newer than the Feisty kernel, however, so if you shy away from backporting apps from Gutsy or compiling them from source, perhaps use ndiswrapper until Gutsy is released.

Hope this helps!  Let me know if you want any more explanation.

Mike

---

### Post by mbsullivan on 2007-07-30
> 
Does anyone know how to lower cpu speed or turn off one core when not in use etc to save power? I know xp on my g41 allows you to run the cpu at ultra low speed.


Following are directions on how to use the superior 'ondemand' frequency governor, which very quickly modulates your CPU frequency to keep the cores cool and quiet during periods of low CPU consumption (saving battery, as well) while very quickly speeding up to provide performance very close to that of running at full speed.

```
(1) sudo modprobe acpi-cpufreq
(2) sudo modprobe cpufreq_ondemand
(3) sudo aptitude install sysfsutils
(4) sudo -s
(5) echo "devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand" >> /etc/sysfs.conf
(6) reboot
```


One note: I believe that the Core II Duo chips should work with speedstep-centrino.  However, I cannot get this module to load.  It concerns me, because I'm not sure if acpi-cpufreq offers voltage scaling in addition to frequency scaling... I need to do more research on the matter when I have some free time.  I've made a post in this thread about it, to no avail.  Anybody know the shortfalls of acpi-cpufreq, and has anybody had success with speedstep-centrino or another CPU module?

Hope this helps.

Mike

P.S. - To clear up a point of confusion, the frequency governors of both CPUs are linked together, such that you only need to change the frequency governor of CPU0 and it will affect both CPUs.

---

### Post by victorgreen on 2007-07-30
Thanks mbsullivan for the wifi instructions. I found the thread for the Intel 4965 card on the forums here: [http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965) 

I have wifi  running with iwlwifi 1.0.0, Mac80211 8.02 and kernel 2.6.22.8 from gutsy. Different versions of the driver and mac80211 seemed to work for different people. 

I will try cpu freq scaling later today.

Has anyone had any success with open gl? I followed the open gl fix on the first page of the forum, the computer says its using the right driver, glxgears works in small view, crashes when the window is expanded and google earth kills X after 10 seconds so totally that it keeps flashing screens that look like X is being reloaded and killed again and again to the point where I hard restart.

---

### Post by sheol on 2007-07-30
> **victorgreen said:**
> Thanks mbsullivan for the wifi instructions. I found the thread for the Intel 4965 card on the forums here: [http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=intel+4965) 

I have wifi  running with iwlwifi 1.0.0, Mac80211 8.02 and kernel 2.6.22.8 from gutsy. Different versions of the driver and mac80211 seemed to work for different people. 

I will try cpu freq scaling later today.

Has anyone had any success with open gl? I followed the open gl fix on the first page of the forum, the computer says its using the right driver, glxgears works in small view, crashes when the window is expanded and google earth kills X after 10 seconds so totally that it keeps flashing screens that look like X is being reloaded and killed again and again to the point where I hard restart.

That's odd.  I haven't gotten that behavior.  I also would like to hear about people experience.

---

### Post by skier on 2007-07-31
Thanks everyone I've got my sound working.:)

Working on the thinkfinger and display after coming out of sleep...

---

### Post by null84 on 2007-08-03
my X61s display still cannot run well. i follow the directions and tried to enable desktop effect but does not work.

i am new at thinkpad. can someone also tell me how to make the middle "mouse button" work?
so i can scroll site easily?

:)  i just got desktop effect work
[http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)

---

### Post by sheol on 2007-08-09
Just a heads up:
I've upgraded to Gutsy.  My computer seems to be running better.  Firefox now never crashes, but KDE restricted device manager crashes everytime I boot up.
Still no support for Fn keys.

---

### Post by Rossimo on 2007-08-09
Has anyone gotten the screen rotation to work? I can't see any ACPI events happening when using the gutsy kernel.

---

### Post by mbsullivan on 2007-08-09
> I can't see any ACPI events happening when using the gutsy kernel.

Make sure that acpid is installed and running. Also, try restarting it after your window manager has launched and you've signed in.

Mike

---

### Post by victorgreen on 2007-08-10
> **null84 said:**
> my X61s display still cannot run well. i follow the directions and tried to enable desktop effect but does not work.

i am new at thinkpad. can someone also tell me how to make the middle "mouse button" work?
so i can scroll site easily?

:)  i just got desktop effect work
[http://ubuntuforums.org/showthread.php?t=506744](http://ubuntuforums.org/showthread.php?t=506744)


HOW did that work for you?? The monitor edit to xorg.conf killed X for me- the only way to get a graphical display back was to change it back

Everything 3D crashes on my X61- google earth, each and every screensaver....

In fact, does anyone know how to edit the selected screen saver from terminal, because when i try to do it graphically the frickin PREVIEW for the screesaver crashes X, I try to restart X and it crashes again on an infinite loop that I can only end with a hard restart. Please help- i cant change the screensaver from one that kills X. I am uninstalling every package that does stuff with screensaver now so I wont have any screensaver but at least my computer wont die after 5 min without use.

---

### Post by victorgreen on 2007-08-10
Has anyone figured out how to configure the red track point dot so you can tap it to left click? The instructions on the thinkwiki seem to be too outdated for an X61.

---

### Post by zorkerz on 2007-08-11
hey all, this thread has been very helpful for me.
I just started another [http://ubuntuforums.org/showthread.php?p=3171965#post3171965](http://ubuntuforums.org/showthread.php?p=3171965#post3171965)
for people with an x61 running Gutsy Gibbon.

---

### Post by zorkerz on 2007-08-12
Hey thankyou sheol for the sound help. I now have sound but am unable to adjust it. I can mute with the mute button but changing the volume up or down has no effect.

---

### Post by victorgreen on 2007-08-13
TO FIX VOLUME BUTTONS AFFECTING SOUND:

System ==> preferences ==> sound at the bottom  make sure the right "device" is selected (sound intel as I recall), but anyways bellow that there is a list of sound related items (pcm, master, line-in, etc). 

Click PCM to select it. (it will be orange). Then your volume buttons should control volume. It worked for me

---

### Post by victorgreen on 2007-08-15
Sorry to bother everyone again, but I thought my X61 was finally working ok (besides no 3d graphics of any kind). I was wrong.

I go to turn on my x61 today and the Ubuntu loading screens gets its orange bar to about 90% and stops. At that point the caplocks light was continuously illuminated. I hard restarted. The bios loading screen comes up and stays there and stays there. Finally with two beeps it gives me hard drive error and asks me to boot from something else. I hard restart again. The bios screen takes longer than usual but it finally boots ok and Im on it now. 

Have I somehow killed my hdd or is this thought to be more of an isolated incident?

---

### Post by sheol on 2007-08-15
> **victorgreen said:**
> Sorry to bother everyone again, but I thought my X61 was finally working ok (besides no 3d graphics of any kind). I was wrong.

I go to turn on my x61 today and the Ubuntu loading screens gets its orange bar to about 90% and stops. At that point the caplocks light was continuously illuminated. I hard restarted. The bios loading screen comes up and stays there and stays there. Finally with two beeps it gives me hard drive error and asks me to boot from something else. I hard restart again. The bios screen takes longer than usual but it finally boots ok and Im on it now. 

Have I somehow killed my hdd or is this thought to be more of an isolated incident?

Make sure the hd is set to compatability mode in the bios

---

### Post by mbsullivan on 2007-08-17
> i am new at thinkpad. can someone also tell me how to make the middle "mouse button" work?
so i can scroll site easily?


Haven't tried it, but there are very clear directions at [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint").

*EDIT*:
> The instructions on the thinkwiki seem to be too outdated for an X61.

Whoops... didn't read your post quite completely... I'll give it a try when I get the chance.

Also, just wanted to share a site that has a lot of goodies on it:
[http://slackwiki.org/ThinkPad_X61s]("http://slackwiki.org/ThinkPad_X61s")

Mike

---

### Post by esr on 2007-08-21
Earlier advice to set acpi_sleep=s3_bios was good but neglected a crucial detail.  You not only need to patch the menu.lst file, you need to run update-grub afterwards!

I've started an X61 installation page on ThinkWiki.  It's here: **[Installation instructions for the ThinkPad X61]("http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_X61")**.  Presently it describes the BIOS tweak and how to get suspend-resume working.

I'd like to add a procedure for getting the Intel 4965AGN working starting from grabbing the 2.6.22 kernel from Gutsy (rather than compiling from kernel sources, which is too much for most users).  I've read Zoltan's magic spell; I'm hoping for something simpler, like a .deb that could be installed through the normal package system.

---

### Post by zorkerz on 2007-08-22
im still not sure where in my menu.lst file i should put acpi_sleep=s3_bios. Could you explain another way for me or post an example one.
thanks

---

### Post by mbsullivan on 2007-08-22
> im still not sure where in my menu.lst file i should put acpi_sleep=s3_bios. Could you explain another way for me or post an example one.
thanks

The option must be added to each kernel's list as follows:

```
title		Ubuntu, kernel 2.6.22.1-9-optimized-2-1
root		(hd0,0)
kernel		/vmlinuz-2.6.22.1-9-optimized-2-1 root=UUID=e0b34e89-6ae4-4512-b90b-3fead17a126a ro quiet splash acpi_sleep=s3_bios
initrd		/initrd.img-2.6.22.1-9-optimized-2-1
quiet
savedefault
```

Perhaps the most intelligent way to do this is to add it to the "additional options" section, as follows:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi_sleep=s3_bios
```

This will automatically insert it into each kernel's option list when update-grub is called.  Otherwise, you would have to manually re-add it each time you update your boot list.

I've attached my menu.lst file as an example.

Mike

---

### Post by zorkerz on 2007-08-22
Im having trouble with update-grub. Here is the terminal output when i type it in.
> sudo update-grub
Searching for GRUB installation directory ... found: /boot/boot/grub
Searching for default file ... found: /boot/boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/boot/grub/menu.lst ... done
It replaces my grub leaving everything blank except my windows boot entry.

adding ascpi_sleep=s3_bios manually however does add backlighting when i resume from suspend. I still get an error saying something is wrong.
thanks all

---

### Post by esr on 2007-08-22
Or, as I describe in the X61 installation instructions on ThinkWiki, you can put it in the kopt comment that is used to generate default options for all kernels.

---

### Post by zorkerz on 2007-08-22
I read your directions on thinkwiki but did not understand how to do it. by the way mbsullivan my menu.lst is exactly the same as yours besides the actual boot entries and the last 3 lines in the default boot options.

your menu.lst says this > ## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false while mine says > ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false not sure if that matters.

Now when I try to return form sleep/suspend/hibernate (I apologize but i use these terms interchangeably I do not know the difference between them feel free to enlighten me) I have backlighting but I still get an error message.

> Sleep Problem Your computer failed to suspend. Check the help file for common problems. This has a link to the quirk website [http://people.freedesktop.org/~hughsient/quirk/.]("http://people.freedesktop.org/%7Ehughsient/quirk/") I have visited here before but Im not able to access it tonight for some reason. problem loading page from firefox.

thats where I am at the moment
and thank you all
elias

I also just discovered i can make my sound work by holding down an [arrow key ]("http://ubuntuforums.org/showthread.php?p=3246495#post3246495")If anyone can make sense of that

---

### Post by victorgreen on 2007-08-26
Can someone please post their xorg conf file so I can copy it into mine?

I still cant do ANYTHING 3D on the computer- no google earth, not even any screensavers. I also cant play avi files from the hardrive. 

When I tried to play a movie, VLC gave me this error:

VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

Now telling me I have insufficient resources is ridiculous when this thing has 2gb of ram and the standard 2gb of swap. I have a feeling its  video issue but I dont really have a way of knowing. 

Please help!

---

### Post by victorgreen on 2007-08-26
Zorkerz, I just had almost the exact same problem. I copied the acpi bio 3 thingy into the grub menu exactly where mbsullivan had them and saved and ran update grub which looked like this:

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-8-generic
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I hit fn f4 and my music kept playing and it locked the screen. I unlocked screen and it said there was an error...

---

### Post by mbsullivan on 2007-08-26
> 
Now when I try to return form sleep/suspend/hibernate (I apologize but i use these terms interchangeably I do not know the difference between them feel free to enlighten me) I have backlighting but I still get an error message.

Sleep and suspend normally both describe "suspend to ram" functionality, and hibernate is normally "suspend to disk".  There is also occasionally a "standby" state, as well.  These three things correspond to different sleep states, as described at [here]("http://acpi.sourceforge.net/documentation/sleep.html").

S0 (Stopgrant) is what is called "standby" in Windows.  It reduces power some, but essentially keeps the computer running without executing any instructions.  I don't know or care how to get it working on the Thinkpad.

S3 (Sleep) is a state for "suspend to ram".  It is normally what is attempted when you press Fn+F4 on the Thinkpad.  Specifically, if you haven't modified your ACPI events, the system will attempt to run /etc/acpi/sleep.sh.  

S4 (Hibernate) is a state for "suspend to disk".  It is normally what is attempted when you press Fn+F12 on the Thinkpad.  Specifically, if you haven't modified your ACPI events, the system will attempt to run /etc/acpi/hibernate.sh.

What kernel version are you running?  I have had some problems getting sleep and hibernate to work with 2.6.21.5, as well as using some non-standard kernel options (i.e. kernel preemption) with 2.6.22.1.  Sleep and hibernate issues are very finicky and tricky to troubleshoot... don't worry about not being able to get them to work right out of the box!

Try the two scripts that I attach (basically simplified sleep and hibernate scripts) and tell us the output that the system gives you.  Also consider trying uswsusp again with s2ram --force and s2disk.

Mike

P.S.- I saw that you had some sort of "mutant ninja" error message with s2ram --force.  I got this in the past, but I can't recall what fixed it.  I believe I changed kernel versions and tried uswsusp again.

P.P.S. - If you use KVM, make sure that the KVM-Intel module is not loaded when trying to suspend or hibernate.  This caused serious kernel issues for me in the past.

---

### Post by mbsullivan on 2007-08-26
> Has anyone figured out how to configure the red track point dot so you can tap it to left click? The instructions on the thinkwiki seem to be too outdated for an X61.

Easy!  Simply do the following:

```
sudo -s
echo -n 1 > /sys/devices/platform/i8042/serio1/press_to_select
```

If you want it to work every time you restart, get the sysfsutils:

```
sudo aptitude install sysfsutils
```

And add the following to the end of /etc/sysfs.conf:

```
devices/platform/i8042/serio1/press_to_select=1
```

> i am new at thinkpad. can someone also tell me how to make the middle "mouse button" work? so i can scroll site easily?

The following should work... Replace the mouse entry of your /etc/X11/xorg.conf with the following:

```
Section "InputDevice"
  Identifier "Mouse1"
  Driver "mouse"
  Option "Protocol" "ExplorerPS/2" # IMPS/2 is not recommend for TrackPoints
  Option "Device" "/dev/input/mice"
  Option "EmulateWheel" "on"
  Option "EmulateWheelTimeout" "200"
  Option "EmulateWheelButton" "2"
  Option "YAxisMapping" "4 5"
  Option "XAxisMapping" "6 7"
EndSection
```

Now reboot, and if you hold down your third mouse button, you should be able to scroll up and down using the trackball.

Hope this helps.
Mike

---

### Post by victorgreen on 2007-08-26
Thank you so much mbsullivan! I'll know whether the mouse things work once I restart, but your code for middle mouse clicking, sudo -s, with the echo 1 > thing gave me an error that device doesnt exist. I did your other steps though so I guess Ill see whether it works upon restart. 

I was wondering if you could post the graphics driver section of your xorg.conf file. I cant get any 3D to work while others have and vlc gives me badalloc errors when I try to play any video file from the hdd. That is particularly maddening... 

Those errors are clearly due to the state of X on this computer. 

Im using generic kernel 2.6.22-8. 

Thanks so much.

---

### Post by mbsullivan on 2007-08-27
> sudo -s, with the echo 1 > thing gave me an error that device doesnt exist

That's strange... did you copy and paste it?  Do you have any folders named /sys/devices/platform/i8042/serioN, where N is a number greater than or equal to 0?

As for video, I'll be glad to post my xorg.conf file, but I don't think I changed it to get video working.  I simply installed the following (as I assume you did):

```
sudo apt-get -t gutsy install xserver-xorg-video-intel
sudo apt-get -t gutsy install libgl1-mesa-dri
```

I'm not sure what to tell you... Do any OpenGL applications work?  Try:

> glxgears

Mike

---

### Post by mbsullivan on 2007-08-27
I finally got around to getting sound to work today.  I found (as did others in this thread) that I needed to install the CVS versions of ALSA in order to get the speakers to work in Feisty.  I found that no kernel patch was required with the Ubuntu patched version of the 2.6.22.1 kernel (revision 9, I believe).  Following is a HOWTO for those who are curious... I submitted a HOWTO under the "tutorial" section of the forums, but following is one tailored specifically to the x61:

HOWTO get the development ALSA drivers built and installed under Feisty (x61 version)

(1) install some packages to support the ALSA CVS build system:

```
sudo aptitude install mercurial autoconf libncurses5 libncurses5-dev
```

(2) download the newest ALSA development drivers (available [here]("http://hg-mirror.alsa-project.org/")):

```
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver
    hg clone http://hg-mirror.alsa-project.org/alsa-kernel alsa-kernel
```

The ALSA-Kernel code is linked to from within the development release of the ALSA drivers (so no separate build/install is necessary).

(3) download the latest stable versions of the ALSA libraries and utilities (available [here]("http://www.alsa-project.org/main/index.php/Download")):

```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
```

(4) untar and unzip the ALSA libraries and utilities: 

```
tar -xjf alsa-lib-1.0.14a.tar.bz2
tar -xjf alsa-utils-1.0.14.tar.bz2
```

(5) build and install the development ALSA drivers:

```
cd alsa-driver; ./cvscompile; sudo make install;
```

(6) build and install the ALSA libraries:

```
cd ../alsa-lib-1.0.14a/; ./configure; make -j 3; sudo make install;
```

(7) build and install the ALSA utilities:

```
cd ../alsa-utils-1.0.14/; ./configure; make -j 3; sudo make install;
```

(8 ) add the thinkpad to the end of the alsa-base file:

```
sudo -s
echo "options snd-hda-intel index=0 model=thinkpad" >> /etc/modprobe.d/alsa-base
```

(9) reboot

(10) Ensure that the volume is turned up:

```
sudo alsamixer
```

To do so, make sure that Headphone and Speaker are both 00 (and not MM == Muted).  If they are muted, press "M" whilst hovering over them.  Also ensure that PCM is turned up to a respectible volume.

(11) Ensure that the speaker is not muted:

```
cat /proc/acpi/ibm/volume
```

If the volume is muted, you can unmute it with the following:

```
sudo -s
echo "up" > /proc/acpi/ibm/volume
```

That is it!  Hopefully, sound will now work through the speakers and the headphone jack.  

I hope this helps!  Let me know if you have any problems.
Mike

---

### Post by zorkerz on 2007-08-27
sound is go again!! mbsullivan you are my x61 god :~)

I ran into a few errors (by my eye) but i imagine none of them are too important as I do now have sound. 

following are my error and the step from the above post that i got it from.

Step 7:
> configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

Step 10: in alsamixer the first internal mic gives continuous high pitched beep unless muted. It seems to be ok to leave this muted.
The mike boost also gives some distortion if it is turned up past 33. So I have it left at 33.


Step 11: > cat: /proc/acpi/ibm/volume: No such file or directory

Step 12:> bash: /proc/acpi/ibm/volume: No such file or directory

cheers

---

### Post by mbsullivan on 2007-08-27
> configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.

Oops... you also need libncurses5 and libncurses5-dev then, too.  You also need these for kernel compilation, btw.  Thanks, I'll edit the HOWTO.

> cat: /proc/acpi/ibm/volume: No such file or directory

Hmmm... do you have the thinkpad_acpi module loaded (lsmod | grep thinkpad_acpi)?  Oh well... so long as sound works!

Mike

---

### Post by victorgreen on 2007-08-27
Thank you so much again mbsullivan. I reinstalled the X drivers as per the two lines of instructions and it seemed to work this time (google earth no longer crashes after 10 seconds). Tap to click also works. 

I checked the /sys/devices/platform/i8042 and found BOTH serio0 and serio1. 

I still have the same video bad alloc issues. Thanks for the xconfig file, Ill compare them tomorrow when I get time.

EDIT- I fixed the bad alloc thanks to an amazing tip from Benanzo of the forums:
VLC:
For VLC select Settings -> Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to X11 video output. Then restart VLC

---

### Post by victorgreen on 2007-08-29
Sorry to post again but I just has a very very weird experience:

My wireless had suddenly lost internet- I still had an ip address and it was still connected but no net. So I disabled and re-enabled the wireless but then it couldnt get another connection to anything becuase the wireless drivers suck so badly. Then I restarted and it took about 10 minutes to restart and nautilus was going really slowly. Cntrl alt backspace had the same nautilus issue. So it finally started ok but the gnome brightness applet which had worked out of the box for me suddenly claimed it couldnt control brightness. I have reinstalled the power manager of which the brightness applet is a part but it didnt help. 

What the heck happened?

---

### Post by esr on 2007-08-30
I asked the ALSA development group to accelerate their next point release (1.0.15), explaining that it would be helpful to ThinkPad users.  Their response was swift and positive; we can expect a new release in about two weeks, which would be mid-September 2007.

---

### Post by gfb1 on 2007-09-04
i've been poking away at my x61t (tablet) and have been having some interesting experiences.
i've been blogging some of them here:
[http://gfb1.blogspot.com/2007/09/lenovo-x60-and-linux-round-2.html](http://gfb1.blogspot.com/2007/09/lenovo-x60-and-linux-round-2.html)

i realize that i'm using the mandriva build; but, some of the same issues exist.  i DO find however that the most interesting aspect is the duplication of keycodes -- resulting in quite a bit of confusion (some of which noted in this forum).

i'm going to try out some of mbsullivan's suggestions in an earlier post and will see what happens.

still no joy with auto-rotate... but, then again, the a-r function in win.vista takes approx 10 seconds to switch the screen. whereas the rotate script [[http://luke.no-ip.org/x60tablet/#rotate_script]](http://luke.no-ip.org/x60tablet/#rotate_script]) via command line is nearly instantaneous...

more to come, and thanks to all for the helpful hints.

---

### Post by mbsullivan on 2007-09-09
Hey guys,

I submitted the following to the tutorials section of the forum for revision and admission.  It can be applied to the X61, so I thought I might repost it here in the meantime for those of you who want to further customize your Thinkpads.

HOWTO: Use tp_smapi to extend the life of your battery

You may or may not be aware that lithium ion batteries (like those present in the newer Thinkpad models) survive best when kept charged between 30%-85%.  They should not be kept fully charged, and should be left off for long periods of time charged to ~%40.  See [here]("http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment") for more tips on Thinkpad battery treatment.

One way to extend the life of your Thinkpad's battery is to control the way it charges -- that is, to make sure that you keep it in the 30%-85% charged range whenever possible.  This is possible easily and quickly through the tp_smapi kernel module.

(1) Download the tp_smapi code [here]("http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=171579").  For the examples presented here, let's assume that you download the tarball to your home directory (~/):

```
wget http://easynews.dl.sourceforge.net/sourceforge/tpctl/tp_smapi-0.32.tgz ~/tp_smapi-0.32.tgz
```

(2) Make sure that you have the necessary pre-requisites installed.  You must have the necessary compiler and build tools (build-essentials), and the kernel source code for your kernel (linux-source-`uname -r`):

```
sudo aptitude install build-essential linux-source-2.6.22
```

(3) Extract the tp_smapi code:

```
tar -xzf ~/tp_smapi-0.32.tgz
```

(4) Change to the new directory, make and install tp_smapi:

```
cd tp_smapi-0.32 && make && sudo make install
```

Should you want to use [HDAPS]("http://www.thinkwiki.org/wiki/HDAPS") (the IBM Active Protection System Linux Drive) in the future, include the HDAPS module in your build:

```
cd tp_smapi-0.32 && make && sudo make install HDAPS=1
```

(5) Make sure that the tp_smapi module is loaded upon startup:

```
sudo -s;
echo "tp_smapi" >> /etc/modules
```

(6) Now reboot, or load the tp_smapi module:

```
sudo modprobe tp_smapi
```

(7) To set the charge thresholds, edit the following files:

> /sys/devices/platform/smapi/BAT0/start_charge_thresh 
/sys/devices/platform/smapi/BAT0/stop_charge_thresh 

For example, to keep the charge constantly varying between 30 and 85% while plugged into AC, use the following commands:

```
sudo -s;
echo "30" > /sys/devices/platform/smapi/BAT0/start_charge_thresh;
echo "85" > /sys/devices/platform/smapi/BAT0/stop_charge_thresh;
```

This may interfere with your ACPI battery charge reports, since it will technically report "charged" at 30% battery (even though it will continue to cycle between 30 and 85 while plugged in).  Thus, for those who use a system monitor (such as Conky or GKrellM), the following may be a more practical solution:

```
sudo -s;
echo "81" > /sys/devices/platform/smapi/BAT0/start_charge_thresh;
echo "85" > /sys/devices/platform/smapi/BAT0/stop_charge_thresh;
```

This will keep the charge below 85% when charged.

Hope this helps!  Most of this information has come from [here]("http://www.thinkwiki.org/wiki/Tp_smapi").  Please let me know if you have any problems.

Mike

---

### Post by zorkerz on 2007-09-09
In step 2 I think you mean the package **"build-essential"** without an s at the end. Also i think the source file is called **linux-source-2.6.22** (for me at least) where as the uname -r command also adds -11-generic.

I was getting an error > Couldn't find any package whose name or description matched "build-essentials"
Couldn't find any package whose name or description matched "linux-source-2.6.22-11-generic"
 so I installed the packages above in bold. I do not think this has entirely solved my problem however because on step 4 I get this output. > $ cd tp_smapi-0.32 && make && sudo make install
Makefile:25: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. You may need to set KSRC and KBUILD to find these..  Stop.
Am I doing something wrong?

---

### Post by mbsullivan on 2007-09-09
> In step 2 I think you mean the package "build-essential" without an s at the end. Also i think the source file is called linux-source-2.6.22 (for me at least) where as the uname -r command also adds -11-generic.

Right you are... thanks!  Made the changes above.

> $ cd tp_smapi-0.32 && make && sudo make install
Makefile:25: *** This driver requires kernel 2.6.19 or newer, and matching kernel sources. You may need to set KSRC and KBUILD to find these.. Stop.

Okay... you should have kernel 2.6.19 or newer, so something must be a bit screwy with the setup of your kernel source.  Goto /usr/src, and extract the kernel source you got from the above step (which should be in a file called linux-source-2.6.22.tar.bz2):

```
sudo -s
cd /usr/src
tar -xjf linux-source-2.6.22.tar.bz2
```

This should extract the source to linux-source-2.6.22.  Be patient... decompressing bzip2 files takes forever!  (If you'd care to speed it up, however, there is a program in the Ubuntu repositories called pbzip2 which can decompress it with multiple threads, taking advantage of both CPU cores.)

Now go into /lib/modules/`uname -r`.  Both the "build" and "source" symbollic links should point to your source folder.  You can check this by observing the output of ln -l, or just create it this way with the following:

```
sudo -s
rm -i /lib/modules/`uname -r`/source /lib/modules/`uname -r`/build
ln -s /usr/src/linux-source-2.6.22 /lib/modules/`uname -r`/source
ln -s /usr/src/linux-source-2.6.22 /lib/modules/`uname -r`/build

```

Hope this helps, and thanks for the feedback!

Mike

---

### Post by skier on 2007-09-13
mbsullivan, nice writeup for getting the backlight fixed after coming out of suspend.  works great.

esr, you need to re-write your wiki it makes absolutely zero sense the way you wrote it up

---

### Post by mbsullivan on 2007-09-15
> mbsullivan, nice writeup for getting the backlight fixed after coming out of suspend. works great.

Thanks!  Glad to help.  I'm happy that the X61 seems to have settled into a nice groove with the new kernel and everything's doable in a short amount of time.  Don't want it to be too easy!

Mike

---

### Post by victorgreen on 2007-09-16
the graphics drivers work fine now. I even installed compiz fusion. The window borders died and the only way I could find to get them back was to install emerald. 

For 2 days it worked great- writing on screen with fire, making it snow etc. Then randomly I turned it on one day and the snow started falling at 2fps. Gkrellm wasnt showing any undo cpu usage, system manager said it was using about 17% of cpu which I had throttled at 800mhz. I increased to my full 2.2ghz. Same low fps. 

I killed compiz in the system manager. Everything worked fine UNTIL I tried to start google earth. It took forever to open and then rendered painfully slow, not more than 10fps. The drivers are all there... 

Also, now compiz starts on startup and even though system manager shows it only using 17% cpu, total cpu usage jumps to 75% and I have to kill it. How do I stop compiz from starting on startup without uninstalling it?

---

### Post by spasticteapot on 2007-09-17
I just purchased an X61.

Which things should I do to make Linux work? Should I start with Feisty or Gutsy?

---

### Post by zorkerz on 2007-09-17
She is a beaut of a computer. a
I would say you should read through this thread and this one
[http://ubuntuforums.org/showthread.php?t=523022](http://ubuntuforums.org/showthread.php?t=523022)
also check out thinkwiki.org
Its alot of reading on those two threads but it will likely answer most of your questions.

As for feisty or Gutsy that depends on how comfortable you are with an unstable operating system. The official Gutsy release has not occurred yet so you are more likely to have problems. However I have been running it on my  x61 for over a month now with no show stoppers.

Also take into consideration how much work your ready to put into it. I installed feisty first found that the wireless drivers did not work out of the box and decided to upgrade to Gutsy. 

In my opinion Gutsy has much better support for the x61 with alot of its features being supported at startup.

hope that gives you somewhere to start
cheers

---

### Post by ppletscher on 2007-09-18
@victorgreen:

Doesn't a killall compiz followed by launching metacity do the trick?

---

### Post by victorgreen on 2007-09-18
> **ppletscher said:**
> @victorgreen:

Doesn't a killall compiz followed by launching metacity do the trick?

I open the system manager and hit kill process like I said, but doing that on every boot kinda sucks. Do you know of a way to make it stop starting on boot?

Also, any guidance into what in tarnation made it go screwy in the first place after running fine for 2 days would be greatly appreciated.

---

### Post by aroch1 on 2007-09-19
I have an R61, and got sound working great on it by following the directions at [ThinkWiki-T61 and Ubuntu 7.10]("http://http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Tribe_5_on_a_ThinkPad_T61#Audio")  Perhaps that would work for you

---

### Post by spiritwing on 2007-09-22
drocko: 
    Thanks for the tips about getting the wacom drivers working. I patched the 8250_pnp.c file and rebuilt the kernel, but the /etc/init.d/xserver-xorg-input-wacom script does not exist on my system. I did install the xserver-xorg-input-wacom package.  Note: I am running Debain/Lenny not Ubuntu so it is not completely surprising that things are a little different.

Could you please post your entire /etc/init.d/xserver-xorg-input-wacom scripts so I can see how it creates the /dev/input/wacom device.

Cheers,
=0)

---

### Post by mbsullivan on 2007-09-22
> drocko:
Thanks for the tips about getting the wacom drivers working. I patched the 8250_pnp.c file and rebuilt the kernel, but the /etc/init.d/xserver-xorg-input-wacom script does not exist on my system. I did install the xserver-xorg-input-wacom package. Note: I am running Debain/Lenny not Ubuntu so it is not completely surprising that things are a little different.

Could you please post your entire /etc/init.d/xserver-xorg-input-wacom scripts so I can see how it creates the /dev/input/wacom device.


His posts were a while ago... you might want to PM him.

Mike

---

### Post by victorgreen on 2007-09-25
While messing about with an external gwc 5.1 usb sound card, I managed to mess up my /etc/asound.conf file to the point where it will not only refused to detect my external sound card, it also refuses to use hda inel sound as a device and instead will only let me select AD1984 the OSS mixer as a device. 

That 'device' makes all sound output utterly horrendous. I was wondering if anyone could post their /etc/asound.conf file so I could try and fix mine.

---

### Post by skier on 2007-09-25
> **victorgreen said:**
> While messing about with an external gwc 5.1 usb sound card, I managed to mess up my /etc/asound.conf file to the point where it will not only refused to detect my external sound card, it also refuses to use hda inel sound as a device and instead will only let me select AD1984 the OSS mixer as a device. 

That 'device' makes all sound output utterly horrendous. I was wondering if anyone could post their /etc/asound.conf file so I could try and fix mine.


See attached

---

### Post by victorgreen on 2007-09-25
Thanks Skier, that fixed my normal audio output, now to figure out how to get my little usb sound card to work...

---

### Post by zorkerz on 2007-09-28
In post [67]("http://ubuntuforums.org/showpost.php?p=3258474&postcount=67") mbsullivian gives directions on how to make the track point work as a mouse button. Im am getting an error when I attempt this.  > echo 1 > /sys/devices/platform/i8042/serio1/press_to_select
bash: echo: write error: Invalid argument

I have two folders in /sys/devices/platform/i8042 named serio0 and serio1 (not sure why this may help but it was asked for a diff problem with the same command above)

any ideas?

---

### Post by mbsullivan on 2007-10-01
> In post 67 mbsullivian gives directions on how to make the track point work as a mouse button. Im am getting an error when I attempt this...

any ideas?

Hmmm... that's my bad.  Try:

```
sudo -s
echo -n 1 > /sys/devices/platform/i8042/serio1/press_to_select
```

The -n will prevent a trailing endline from being appended to the argument.  Sorry about that -- I think I was using sysfs to do it, so I was writing instructions that I (technically) hadn't tried yet.  I edited the original post.

Mike

---

### Post by zorkerz on 2007-10-01
sorry  that did not help, still have the same error

---

### Post by victorgreen on 2007-10-02
I recently bought a little usb sound card made by GWC. As far as I can tell, I need the alsa module snd-usb-audio. This is supposed to be included with the default alsa install, but:

:~$ modprobe snd_usb_audio
FATAL: Module snd_usb_audio not found.


I have no idea how to get it, cause to get the audio working in the first place I had to install the patch for 1.0.14, which is the current stable release. Installing it again wont help then... 

I was wondering if you guys had the module or not, or if you could tell me how to get it.

---

### Post by ^graff_epsilon on 2007-10-02
Although I'm running Gutsy, I'm trying to get my microphone to work and this seems like the best forum to post on. I'm running an X61 tablet, and am not receiving input from my mic.

---

### Post by victorgreen on 2007-10-03
I was thinking about getting an 19 or 20in lcd monitor to hook up to this thing to get some extra screen space when Im just at my desk. Has anyone had any simple success or severe frustration getting an external monitor connected and running? 

Just like with everything else, I just have a feeling that what would be plug and play in Ubuntu on any other system on this will take hours of headache to get working...

---

### Post by mbsullivan on 2007-10-04
> I was thinking about getting an 19 or 20in lcd monitor to hook up to this thing to get some extra screen space when Im just at my desk. Has anyone had any simple success or severe frustration getting an external monitor connected and running?

I don't use the full Ubuntu package and use Fluxbox for my WM, so I can't tell you a WM specific way to get it working with an external monitor.  However, I can verify that the monitor jack on the X61 works fine, and that resolution can be adjusted using the xrandr command (from the command line).

If you want more info, I can give it later... I'm on a Windows machine right now.
Mike

---

### Post by victorgreen on 2007-10-05
Oh Im sure the jack works... I tried plugging into a friend's lcd today. Once it displayed my logon screen in sync with the laptop, and went back to black once I had logged in. Most of the time the screen just said no device connected. 

The thinkwiki for x3100 instruction on connecting external monitor broke x. I had to delete all my changes to regain graphical display. [funnily enough, that happens EVERY time I edit xorg.conf]. 

Im seriously almost to the point of wiping everythng and putting xp on this. Vista is much worse than any non MS OS. Indeed if I had known that xp was supported on this thing before I had already gotten Ubuntu halfway sort of functional, I wouldnt have bothered with Ubuntu in the first place. Ive had excellent Ubuntu experiences with two desktops, and a decent time with it on a much older Thinkpad (T30). 

Please forgive my rant, Im just frustrated.

---

### Post by victorgreen on 2007-10-05
I just had a VERY weird experience with sound. 

I went to the alsa website, downloaded and compiled the lasted release candidate of alsa (1.0.15rc3). My usb soundcard was recognized!! Sound came out, it was amazing. I unplugged it to make sure the onboard still worked, and it did. I was happy. Then I noticed that although my volume up down buttons still displayed the little volume bar rising/falling on the screen, but the volume didnt actually change. Only the gnome applet actually controlled sound. 

I then replugged the usb sound card and set prefs-sound to use it. No sound, no joy. All the sound came out of the onboard speakers. 

I restarted. Now prefs- sound doesnt show the usb sound card as an option and 
:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8220000 irq 19

shows only my onboard when before it showed the USB as well. 

The volume controls work now too. 

Im really confused.

---

### Post by Eric Lee Elliott on 2007-10-12
I hope you all are writing about the same hardware.  I have Z61m.  Most posts & reviews are about a very different Z61m. 9450A38 describes my Z61m with Intel 945 & Atheros WIFI, without ATI.  Other Z61m have much different hardwares.
Suse 10.3 KDE installed Thinkpad T60 sound system & is silent.  Kubuntu 7.10 installed sound, can't start it.
Intel video is fine with acceleration enabled.  Not sure if openGL is working but Amoeba runs faster than my eyes can track.
USB HDD is only USB thing that has not worked from start & does not work with Suse, Kubuntu, DSL or Knoppix.

---

### Post by victorgreen on 2007-10-12
Has anyone gotten the onboard mic to work on this thing? How do I even tell if the computer is recognizing it.

---

### Post by victorgreen on 2007-10-12
I got the internal mic working no problem. Right click the gnome volume control icon. Under playback unmute internal mic and turn up the volume. Turn off internal mic boost, it makes gives weird feedback in headphones. In the recording tab, make sure both capture and capture one are turned up. Under the options tab make the input source on the top "internal mic". Leave the second listed input source "Mic". 

NOTE- if you have headphones plugged and and are talking to somone over the internal mic, if you pull out your headphones, the computer will make a godawfully high pitched LOUD beep until something else is plugged back into the headphone jack. Right now Im using headphones, I have no idea how to solve this problem, maybe by muting internal mic before unplugging headphones. 

Im glad it works, but the beep is seriously evil.

---

### Post by hihihi on 2008-07-10
> **mbsullivan said:**
> ...
LOCKING THE SCREEN:

Also, if you would like to make a script to lock the screen (with xlock or xscreensaver or whatever) you may do so.

However, because the script will be run as root (through acpid), you must explicitly run the lock under your username, since (by default) there is no "root" account, per se:

```
sudo -u [your username] /usr/bin/xlock
```

I've attached an example script that could be used as the action from the "lock" key.

...

thanks 1000x!!!!!
cool, I was checking for weeks now why I couldnt  lock screen, i wondered, BUT thanks to you I now understand:
the sudo -u <my username> option makes all possible...
i am veryvery happy now.
:)
byebye:KS

btw: i got a sony vaio, if that matters

---

