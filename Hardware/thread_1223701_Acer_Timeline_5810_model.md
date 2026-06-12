---
title: "Acer Timeline 5810 model"
date: 2009-07-26
forum: Hardware
---

### Post by Friqenstein on 2009-07-26
Hello all,

I've been searching for threads on the 5810 model, but cannot seem to find anything out there. I've seen threads regarding the 4810 and lower model #s.

I'm looking to buy the 5810 Timeline model. My current laptop has served me well, but I want more battery life and a bit more umph from my video card. I don't need to play games, but I do have some apps that currently struggle with my little Intel video card. (not accelerated)
Here is the link to the lappy I'm looking at: [Acer 5810]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4786616&CatId=2510")
It has some nice specs. The Vid card advertises a bit more power than most normal Intel video cards, so I'm hoping it can handle the resolution/textures for my apps. It also says that it is accelerated, not sure if that is going to help or just generate more heat.
The other selling points are the battery life and heat reduction.

However I'm a bit perplexed about the HDD. My current laptop uses a SSD and I absolutely love it. I've gone through several internet sites trying to get hardware specs on this new Acer's HDD, but it only every says "320GB HD"... well duh! Is it sata? SSD? IDE? Nobody seems to know what type of drive it is. Even on Acer's site they do not list the HD type. It just says HD.
Anyway, here comes my questions:
1) Has anybody had any experience with this model and Ubuntu/Linux?
2) Are there any hardware issues known right off the bat?
3) Anybody know what type of HDD is in this darn thing?

I'm sure that Ubuntu will handle most, if not all, of the hardware just fine, I just wanted to make sure before I make the plunge. But this lappy is so much cheaper than my current one it's pretty much a steal.

Any info is greatly appreciated.
L8ra

---

### Post by Friqenstein on 2009-07-26
Hello all,

A quick update. I just had a LiveChat session with a TigerDirect rep, and he said the HDD is a SATA drive... which really bums me out. I was really hoping to stick with a SSD, but I guess Acer isn't going that route for some reason with these Timeline models.

I'm still searching for the other questions/input.

L8rz

---

### Post by Friqenstein on 2009-07-26
Ok, so I've found a bit more info.
It seems that the Intel video card has issues right out of the box using Ubuntu. At least that's what I've read so far.
My current laptop uses an Intel vid card, but it isn't the newer ones that are currently being used in the Acer units.

I'm also trying to find out what the decibel rating is for the fans when they are going full out. I want to know if the unit is overtly loud trying to dissipate all the heat since Acer is advertising extreme cooling efficiency.

Anybody using a 4810 unit can probably confirm this. I'm sure the 4810 and 5810 are pretty darn similar in performance.

I also just noticed that the touchpad is offset to the left just a bit due to the larger keyboard on the 5810 as apposed to the 4810 and below. This looks as though it could be a big problem for people like me who use the keyboard extensively. Having my thumb or palm accidentally brush the touch pad while I'm typing commands or documents always posses a problem in my eyes.
The more I think about it, the more I'm starting to like the idea of the 4810 over the 5810.

Any info still welcome.
Tnx

---

### Post by wesbalmer on 2009-08-02
I want to put Ubuntu on my 5810TZ-4274, I was just worried about losing my battery life. I have searched for a long time to no avail, wondering if the touchpad gestures will be lost. For instance you have the ability to zoom in, and scrolling freely across the pad. I really love my timeline, I'm a student and is perfect to take to school. Battery life is amazing. I noticed that using 802.11g drains battery down to 5 hours on a full charge, however using n makes it last the full 8. Any info would be much appreciated as well.

---

### Post by clarknova on 2009-08-13
Virtually all available aftermarket SSDs use the SATA interface. Switching out the Timeline's SATA HDD for the SSD of your choice should not be a problem. What you need to find out is the size of the included HDD. Most laptops use a standard 2.5" HDD, but it's possible, especially in the low-energy models, it could be 1.8" (in which case you still have SSD options).

I'm looking at the 13.3" model which is available with an 80GB SSD (but not in Canada :P )

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115593&Tpk=acer%20timeline%20ssd](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115593&Tpk=acer%20timeline%20ssd)

---

### Post by TexLogic on 2009-08-15
> **Friqenstein said:**
> Ok, so I've found a bit more info.
It seems that the Intel video card has issues right out of the box using Ubuntu. At least that's what I've read so far.
My current laptop uses an Intel vid card, but it isn't the newer ones that are currently being used in the Acer units.

I'm also trying to find out what the decibel rating is for the fans when they are going full out. I want to know if the unit is overtly loud trying to dissipate all the heat since Acer is advertising extreme cooling efficiency.

Anybody using a 4810 unit can probably confirm this. I'm sure the 4810 and 5810 are pretty darn similar in performance.

I also just noticed that the touchpad is offset to the left just a bit due to the larger keyboard on the 5810 as apposed to the 4810 and below. This looks as though it could be a big problem for people like me who use the keyboard extensively. Having my thumb or palm accidentally brush the touch pad while I'm typing commands or documents always posses a problem in my eyes.
The more I think about it, the more I'm starting to like the idea of the 4810 over the 5810.

Any info still welcome.
Tnx

I bought a 5810T and installed both 32 and 64 bit versions of Jaunty.  I love it.  Very few issues.  For video, add the Driver and AccelMethod option as follows to the Configured Video Device in /etc/X11/xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver  	"Intel"
	Option 		"AccelMethod" "UXA"
EndSection

I've found this to deliver the best performance with Intel's crappy video card and drivers.  OpenGL performance is very good.

I don't know about DB units, but the machine is very quiet.  Fan just whispers, esp compared to the Macbook that this machine replaced.  I've never heard the fan get any louder or softer, despite long periods with a heavy CPU load.

I've not found the offset mousepad to be a problem.  It's centered below the main keyboard so doesn't feel oddly placed.  There are also some solutions around for setting up the mousepad so that it does not respond to taps for a settable amount of time (e.g., .25 of a second) so that the cursor doesn't move when you inadvertently hit it while typing.  Google "syndaemon".

The hotkey for setting the brightness does not work out of the box with the 2.6.28 kernel.  Upgrade to the 2.6.30 kernel to fix.  There is also a software fix using xrandr that works with the 2.6.28 kernel.

Sound out of the box is set low.  Install the gnome ALSA mixer to set the master, PCM, and Front volumes to max.  You can then control with the hotkey.

Be sure to install the 64 bit version of Ubuntu to take full advantage of the installed 4GB of RAM.  You'll need to get the alpha version of the 64 bit Adobe Flash plugin to get flash working in Firefox, but I've found it to be very stable.

Hibernation and suspension seem to be flaky in the 64 bit version; often suspension returns you to the login window and suspension wakes up and simply reboots.  They work well in the 32 bit version.  This is the only issue with the 64 bit version that I find annoying, as I often have a lot of stuff open and running and want to suspend or hibernate rather than logout.  As with most such issues, I expect a fix before long.

Hope that's useful.  I recommend the machine very highly.  It's very slim and light (for its size) with a beautiful 15.6" screen. 

TexLogic

---

### Post by Sashin on 2009-08-15
> I bought a 5810T and installed both 32 and 64 bit versions of Jaunty. I love it. Very few issues. For video, add the Driver and AccelMethod option as follows to the Configured Video Device in /etc/X11/xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Driver "Intel"
Option "AccelMethod" "UXA"
EndSection

I've found this to deliver the best performance with Intel's crappy video card and drivers. OpenGL performance is very good.

Would this be recommended with the acer 4810T as well?

---

### Post by TexLogic on 2009-08-15
> **Sashin said:**
> Would this be recommended with the acer 4810T as well?

It's at least a similar chipset if not identical; I believe I've seen UXA recommended for the 4810 as well.  Best thing to do is just try it out and compare to the performance you get with the default.

TexLogic

---

### Post by escuadra1941 on 2009-08-24
Hi I'm a spanish, first of all, sorry for my english, I've just bought a timeline 5810.
Can you tell me how to configure my laptop, step by step?
I want to install Jaunty Jackalope, and erase vista. 
Thanks for all

---

### Post by clarknova on 2009-08-24
This guide says it better than I can. It sounds like you aren't planning to dual-boot Windows, so you can skip right to Chapter 4.

[https://help.ubuntu.com/9.04/installation-guide/amd64/index.html](https://help.ubuntu.com/9.04/installation-guide/amd64/index.html)

---

### Post by escuadra1941 on 2009-08-24
OK I try to follow it.
Thanks

---

### Post by escuadra1941 on 2009-08-24
Ok I try to follow it.
Thanks

---

### Post by dwinks on 2009-09-28
I've got a Acer Timeline I purchase a few months back.  Under Windows (Vista, 7 and Server 2008) I get 7-8 hours of battery life.  Even under fairly intense usage it never drops below 7 hours.

Under Ubuntu 9.10 I am unable to even get 4.5 hours.

I specifically bought this laptop for its 8 hour battery life.  Powertop suggests various things, all of which I've tried and none of which brought the battery life to even a tolerable fraction of the 8 hours it should get.

What exactly is the deal with this laptop?  I've had other laptops before, and they got the same or better battery life in Linux.  Why is this one quite literally HALVED when running Linux, it makes no sense.  It especially makes no sense as I could run Prime95 on Windows and STILL not manage to use the battery in less than 6 hours.

---

### Post by executorvs on 2009-09-29
has anyone else noticed that the fan driver for the 5810 doesn't load correctly. in dmesg you will see 
[   15.860575] acerhdf: Acer Aspire One Fan driver, v.0.5.16
[   15.860581] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 5810T/V1.23, please report, aborting!

I wonder if this could be one source of power drain.

my other thoughts are the dvd-rw not turning off (or running properly for that matter) could be another point of power consumption.

also the screen brightness.

has anyone found work arounds for all three of these? if so what's your battery life?

if you haven't found a work around might I suggest adding yourselves to the relevant bug reports. hopefully if we cause enough traffic over these someone will notice.

---

### Post by Friqenstein on 2009-09-30
This is very curious indeed. I'm getting about a max of 3.5 hours from my laptop (4810) and I cannot figure out why. I've read another thread that stated when using the wireless in G mode it uses much more power than N mode. Perhaps this is one problem as well as the fan issue, but I haven't noticed any error messages regarding the one listed above about the fan.

I hope we come up with something soon because I'm in the same boat as most who posted here... I bought this unit specifically for the battery life & light weight. If I'm never going to get any more than 3.5hrs of battery life, then it's pretty lame. Granted it's better than my last laptop which only gave me a max of 2 hours and ran as hot and loud as a coal train.

---

### Post by coolvibe on 2009-09-30
I found a workaround to fix the brightness controls.

First you have to disable KMS, and then you have to set a kernel parameters. Basically, you add the following to your grub kernel commandline: "nomodeset acpi_backlight=vendor"

I will have to test that last cmdline with a KMS-enabled setup. But at least this works for me. It even solves some of the flickering I have noticed.

EDIT: It doesn't work with KMS enabled.

---

### Post by Jester05 on 2009-10-08
Hey guys, I want to apologize if anything I ask seems stupid or trivial.. I've just recently been looking to the Acer Timeline series and haven't had a lot of time to see how well things have been progressing within the linux community in terms of support/functionality.  To my understanding with ubuntu 9.10 alpha * they have been pulling decent batterylife (7.5hrs).  Is there any truth to this, if so what sort of activities could one expect to do within that battery life.  I assume wifi would essentially be out the window but what about CPU load, watching movies for example?  Speaking of CPU, how well do you think a timeline running a 1.30 would handle semi-intense CPU loading software such as Matlab, Gimp, etc.  I know a guy that has a netbook, in windows he said it wont run matlab at least in any truely functional way but with Ubuntu Netbook Remix he said he can run matlab while still carrying out typical laptop functions.  Also, if any of you think I may be better served by a different model laptop please let me know.  I am in my 5th yr of my electrical engineering bach. degree and am considering masters so it'd be nice to have a laptop I can squeeze another couple years out of without having to drop alot of cabage.  Obviously I'm looking for something with decent batterylife, I love the idea of the timeline pulling 7-8 but anything 3-4+hrs (assuming wifi is in use) would be good.  Also, I'm a linux veteran so batterylife under linux operation will be my primary concern.  I would perferably install Arch and optomize it for whatever laptop I'm running but if I go with a timeline I believe I will stick with ubuntu given the amazing support base.  Also, is there any notion of an "ubuntu _timeline_ remix?"  Any insight/comments are appriciated.  Thanks guys!

---

### Post by executorvs on 2009-10-08
after a few of the more recent updates, and if I turn my screen brightness down until right before it starts flickering, I get almost 6 hours with wifi being actively used over a very weak signal (good signal and I would probably in the 6 hour range).

I have the 1.3ghz processor and while it is not high res game worthy it runs gimp, blender, qcad, sagcad, sweethome3d, and therion without any issues.

besides, I have a desktop for modern games and this runs C&C first decade, C&C3, star craft, and a bunch of sid meier games. do I really need more distractions?

---

### Post by dwinks on 2009-10-08
Having thoroughly attempted everything I could think of, I eventually settled on Windows 7 for my 5810.

9.10 does NOT give anywhere close to 7.5 hours.  I got 4.5 tops.

9.10 also doesn't allow for ANY change to the backlight setting, and the previous work around does NOT work anymore.

Overall it's "acceptable" as far as linux goes, but I didn't spend money on a new laptop specifically for 8+ hour battery life to end up with half that.  Plus the backlight made seeing the screen difficult under most lighting conditions (it was always at max, which is WAY too bright indoors).

Basically, Vista or 7 on this particular laptop, at least for current and the 9.10 releases is a FAR better option.

Oh, and there are drivers that completely power off the DVD drive, which adds nearly an hour under windows, and that function will likely never ever work on Linux.

Overall I'm very pleased with this laptop, and very pleased with Windows 7.  For now I'll just continue to RDP into my Ubuntu install running on my desktop in virtualbox, at least I can use Linux for 8+ hours at a time that way.

---

### Post by waterpot on 2009-10-08
I have a desktop for modern games and this runs C&C first decade 
I try it

---

### Post by executorvs on 2009-10-08
I keep checking and posting the lack of screen brightness control in hopes of getting it going in time for final.

you can use the command "xrandr --output LVDS --set BACKLIGHT_CONTROL native" in terminal to adjust the screen brightness. it's not ideal but it allows you full range of control from off to max bright. each time I finish checking to see if the updates fixed the issue I set the command to run after login.

and some of the recent updates have gotten me past the 5 hour mark if I'm not being to intensive with my usage. I also wish the battery gauge was somewhere near accurate on any of the laptops I've used.

---

### Post by dhscaresme on 2009-10-20
> **dwinks said:**
> 

Oh, and there are drivers that completely power off the DVD drive, which adds nearly an hour under windows, and that function will likely never ever work on Linux.



@dwinks,
Would you mind posting your sources for that info? I have a hard time believing that to be true, but I'd like to know otherwise if it's true.

---

### Post by X1R1 on 2009-11-23
Brightness is the main power drainer for the battery, the lower the brightness, the more your laptop battery can last, So if you havent fixed the brightness issue, you battery life will suck, the fixes are different on Jaunty and karmic, but they are both on this thread.

Powertop is a pretty good tool and can save you like half an hour.

Also, if you use compiz, that also drains battery pretty quick, so you can try to disable it to see how much life you can gain.

Currently I get like 6 or more hours from my battery (with compiz enabled) and the full 8 on vista. So any more tips are highly appreciated.

---

### Post by didibanner on 2010-01-16
Does anyone else have this problem:

When I plug in earphones, I get this loud noise like static on a radio.

Sometimes I get the same sounds from the speakers when the computer is starting up as well.

Any suggestions would be great.

Thanks

---

### Post by oldtimer94 on 2010-02-14
Hi, I was searching a lot to figure out this backlight control thing for  Acer Aspire 5810T laptop, and thought it needs a summary to be  understood - the info is scattered in bits and pieces. I edited this  post after upgrading to Lucid 10.4.

I am using currently Kubuntu 9.10 Karmic Koala, kernel version  2.6.31-19-generic (in the meantime upgraded to Lucid Lynx 10.4, works with  that too)


Steps: 
1. Edit /etc/default/grub and add the following to the  GRUB_CMDLINE_LINUX_DEFAULT parameter value:

nomodeset acpi_backlight=vendor

It was another parameter suggested somewhere, don't remember exactly for  what, I added that too: i8042.nomux

My parameter line looks like this after editing:
GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux nomodeset acpi_backlight=vendor  quiet splash"

When you update grub as follows, that parameter value will be appended  to the end of your grub command line in the /boot/grub/grub.cfg file. 
 
2. run sudo update-grub

oldtimer@acer:~$ sudo update-grub

This will enable xrandr to change the backlight.

Do not edit directly the /boot/grub/grub.cfg file. Your changes will be  lost when you upgrade grub, and you will have to edit it again.
 
example of /boot/grub/grub.cfg after running update-grub:

-- cut --
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1                         
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1                                            
        insmod ext2                                            
        set root=(hd0,6)                                       
        search --no-floppy --fs-uuid --set  b24b3e5f-8a29-4da3-9208-d44f85d5d8f8
        linux   /vmlinuz-2.6.31-19-generic  root=UUID=0352da7b-e385-4ec0-9f39-53196d5cb74e ro i8042.nomux nomodeset  acpi_backlight=vendor quiet splash
        initrd  /initrd.img-2.6.31-19-generic                                                                                               
}                                               

-- cut --

3. reboot

4. test if nomodeset acpi_backlight command worked with the command  xrandr --prop:

oldtimer@acer:~$ xrandr --prop
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis)  345mm x 194mm
        EDID_DATA:
                00ffffffffffff0030e4020200000000
                00130103802313780a28659759548e27
                1e505400000001010101010101010101
                010101010101561d56c6500020303020
                350059c2100000190000000000000000
                00000000000000000000000000fe004c
                4720446973706c61790a2020000000fc
                004c503135365748332d544c41310039
        PANEL_FITTING:  full_aspect
                supported: center       full_aspect  full
        BACKLIGHT_CONTROL:      combination
                supported: native       legacy       combination  kernel
        BACKLIGHT: 1039 (0x0000040f)    range:  (0,1039)
   1366x768       60.0*+
   1360x768       59.8
   1024x768       60.0
   800x600        60.3
   640x480        59.9
HDMI-1 disconnected (normal left inverted right x axis y axis)
        BROADCAST_RGB: 0 (0x00000000)   range:  (0,1)

if you see the BACKLIGHT_CONTROL line, means that you were successful.  Otherwise this line is missing.

You can see the supported modes below the BACKLIGHT_CONTROL line:
                supported: native       legacy       combination  kernel
 
you can use first three, kernel mode will not work with the command  below. In my experience the only difference between them is the range,  otherwise the result is the same. You can check the range in the  BACKLIGHT line, here is combination mode, with range 0-1039. Native give  you the highest resolution, range from 0 to 2078

5. set your preferred mode:
xrandr --output LVDS --set BACKLIGHT_CONTROL native

if you get an error, check the connected device in the 3rd line of  xrandr --prop, might be LVDS1 etc. if you restarted the X server and  adjust the above command accordingly

6. set brightness, parameter within the range of selected mode, highest  number brightest:

xrandr --output LVDS --set BACKLIGHT <parameter>

example:
oldtimer@acer:~$ xrandr --output LVDS --set BACKLIGHT 1600

after brighness set, besides brightness change you see the modified  parameters if running xrandr --prop:

oldtimer@acer:~$ xrandr --prop
 Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis)  345mm x 194mm
        EDID_DATA:
                00ffffffffffff0030e4020200000000
                00130103802313780a28659759548e27
                1e505400000001010101010101010101
                010101010101561d56c6500020303020
                350059c2100000190000000000000000
                00000000000000000000000000fe004c
                4720446973706c61790a2020000000fc
                004c503135365748332d544c41310039
        PANEL_FITTING:  full_aspect
                supported: center       full_aspect  full
        BACKLIGHT_CONTROL:      native
                supported: native       legacy       combination  kernel
        BACKLIGHT: 1600 (0x00000640)    range:  (0,2078)
   1366x768       60.0*+
   1360x768       59.8
   1024x768       60.0
   800x600        60.3
   640x480        59.9
HDMI-1 disconnected (normal left inverted right x axis y axis)
        BROADCAST_RGB: 0 (0x00000000)   range:  (0,1)

After upgrading to version 10.4 LTS Lucid Lynx, kernel version  2.6.32-22-generic, I upgraded the BIOS to version 1.35 (it was 1.10  before). 

After the upgrade the Fn+Arrow buttons started to work! They are  changing the brightness in a restricted range, but it is useful anyway.  If you need a bigger change, you can use the above command to change the  brightness, and the Fn keys will work on the new selected range for  fine tuning as you work. 

The new BIOS can be downloaded from the ACER site, drivers section.  Please be aware that if you install a wrong BIOS your comnputer might  end up unusable!!!

I wrote a short script to make this more quick, named sbl:
#!/bin/bash
/usr/bin/xrandr --output LVDS --set BACKLIGHT $1

copy that in /usr/bin and make it executable:

cp sbl /usr/bin ; chmod +x /usr/bin/sbl

you can change the brightness with:
sbl <parameter>
sbl 400     is very low
sbl 650     is bright
 sbl 1039   is brightest
  
I also found a solution in a forum for another annoying problem - could  not use the microphone, I need it for Skype:
[http://ubuntuforums.org/showthread.php?t=1308090&page=2](http://ubuntuforums.org/showthread.php?t=1308090&page=2)
 Open alsamixer and change the mic volume (CAPTURE). The left side to 0  and the right to 100.
 Open alsamixer, push F6 to choose the Audio card. Push F5 (All). Move  with arrow keys on CAPTURE.
 Push Z to decrease the left column and E to raise the right one.
 Now start skype and it should work. 

I hope this helps to save some time.

---

### Post by executorvs on 2010-03-10
The backlight xrand fixes never worked for me under karmic and still don't under lucid. I still can't use the eject button, but I haven't had problems with earphones since karmic's development. anyone else still having these problems under Lucid? 

side note: on the upside this new kernel has a lot more webcam support. it even got a M$ lifecam vx-3000 I was gifted up and running. so there is progress.

---

### Post by executorvs on 2010-03-11
I'm trying to draw more attention to the brightness bug on launchpad as it also affects other timeline models and I suspect a few of the other Aspire series as well.

there is a bug report at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717)

I have marked as duplicates all of the bugs related to the changes in how the brightness keys have failed over time.

if anyone with either a 3810(TZ/TG) or 4810(TZ/TG) or 5810TG could post exact details of how this bug affects there computer under lucid it would be appreciated.

---

### Post by Doodaddy on 2010-03-14
I just got the 5180T and am loving it so far. Ubuntu loaded with zero problems and have no hardware driver issues. Other than the screen brightness issue, the only problem I'm having is the touchpad. 

When I disable the touchpad (using the button just to the right of it), it properly disables it; however, the touchpad function will not restore until a full reboot. Is this common?

---

### Post by TSJason on 2010-03-14
Yeah, that's been my experience too. I've found that if I suspend the machine the touchpad will start working when it wakes up as well.

---

### Post by Doodaddy on 2010-03-15
> **TSJason said:**
> Yeah, that's been my experience too. I've found that if I suspend the machine the touchpad will start working when it wakes up as well.

I didn't have that luck. :-\

---

### Post by kcleworth on 2010-04-11
I've been running ubuntu 9.10 on my Acer 5810t 15.6inch for a few months now... and i've had no problems other than my CD/DVD drive doesn't work at all. I can open and close it and I can hear CD's spinning inside but I can't get access to the drive. 

I know theres nothing wrong with the drive as it boots from CD fine, just wondered if anybody else has had this problem and a solution?

---

### Post by executorvs on 2010-04-11
I'm sure it's mentioned earlier in the thread, but to insert media in drive use the "eject cdrom" command in terminal. if you don't use that command to open the drive you can suspend and resume after inserting the media. it's annoying.

---

### Post by kcleworth on 2010-04-11
I just used the Eject Cdrom command and then inserted a Disc... in this case a DVD of Gounod's Faust... and I got this message when it attempted to mount:

Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.devicekit.disks.filesystem-mount is not registered

---

### Post by rbrown3rd on 2010-05-04
> **oldtimer94 said:**
> Hi, I was searching a lot to figure out this backlight control thing for Acer Aspire 5810T laptop, and thought it needs a summary to be understood - the info is scattered in bits and pieces.

I am using currently Kubuntu 9.10 Karmic Koala, kernel version 2.6.31-19-generic

Steps: 
1. Edit /boot/grub/grub.cfg and add the following to the end of your grub command line: 
nomodeset acpi_backlight=vendor

This will enable xrandr to change the backlight................

Thanks oldtimer94, that did it for me.  I am running 10.04 and so far so good for me. I have only had this computer for a day now.  I slicked it yesterday and removed Vista and installed 10.04.  My biggest problem so far is getting Skype to work properly.  I cannot video or audio chat at all.

---

### Post by rbrown3rd on 2010-05-05
Ubuntu 10.04 is gorgeous on the screen of this laptop.  Almost everything runs beautifully.  The almost is my problem.  Unless some solutions are found soon I will reload Windows on my shiny new laptop.  Problems?

1.  I cannot access the camera or the microphone to use Skype.
2.  The best battery life I can get is 5 hrs. 15 mins.
3.  I cannot play a DVD.

I would hate to go back to Vista that the machine came with but if that is what it takes temporarily until people who are smarter than me work out those problems then so be it.

I would enjoy hearing your thoughts before reverting.

Bob

---

### Post by rbrown3rd on 2010-05-06
> **oldtimer94 said:**
> Hi, I was searching a lot to figure out this backlight control thing for Acer Aspire 5810T laptop, and thought it needs a summary to be understood - the info is scattered in bits and pieces.

I am using currently Kubuntu 9.10 Karmic Koala, kernel version 2.6.31-19-generic

Steps: 
1. Edit /boot/grub/grub.cfg and add the following to the end of your grub command line: 
nomodeset acpi_backlight=vendor

This will enable xrandr to change the backlight.

example:
.....................
Just took an update on my 5810 and had to edit grub.cfg again.  But, the brightness control is working again after doing so.

---

### Post by rbrown3rd on 2010-05-09
After researching the threads relating to the 5810 I think Skype and the microphone may have been broken with the upgrade from Karmic to Lucid.  At any rate I am going to leave my 5810 as it is running Ubuntu with those features broken.  I just like it too much to go back to Windows on that machine.  I will just hope that the camera and microphone access will be fixed somewhere down the line.

---

### Post by Doodaddy on 2010-06-06
Recently, my cd drive has stopped burning cd's in both Ubuntu and Vista. Every single attempt ends in failure. Any ideas?

---

### Post by oldtimer94 on 2010-06-07
You are welcome! Check my post again, just edited it. There is a solution for the microphone problem in Skype as well!

---

### Post by rbrown3rd on 2010-06-08
> **oldtimer94 said:**
> .........

After upgrading to version 10.4 LTS Lucid Lynx, kernel version  2.6.32-22-generic, I upgraded the BIOS to version 1.35 (it was 1.10  before). 

..................
  


I hope this helps to save some time.

Downloaded the appropriate Bios update file but it all seems to be DOS based bat file driven.  How do you update the bios using Linux?

Bob

---

### Post by Hatch3r on 2010-06-10
Hi guys,
I'm happy that I'm not having any of the problems with brightness or cd drives but I do have one rather annoying problem.
Occasionally the wireless won't connect to a stored network. The wireless card is picked up and working fine and can see other local networks but it won't connect to my hidden network.
If I reboot from here, it usually connects.

I don't think the card is at fault, as Vista has no problems using wireless networks at all.

Can anyone shed some light on the situation?

Thanks

EDIT:
I've tried a few more times and learned nothing new that was useful. However, occasionally when booted from cold the laptop will connect to the network after a few minutes.

I've just tried setting the wireless network to visible instead of hidden. I'll let you know how that goes.

---

### Post by Hatch3r on 2010-06-11
Good evening! I've spent the last day using Ubuntu with wireless with no problems.
Although it required setting the wireless network to visible which I'd prefer to change back in future.

If I find a solution I'll post it here first.

---

### Post by Carl.Spackler on 2010-09-18
> **oldtimer94 said:**
> 
It was another parameter suggested somewhere, don't remember exactly for  what, I added that too: i8042.nomux

My parameter line looks like this after editing:
GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux nomodeset acpi_backlight=vendor  quiet splash"


This fixes the trackpad disable/re-enable issue on my machine.

---

### Post by coolvibe on 2010-10-19
> **rbrown3rd said:**
> Downloaded the appropriate Bios update file but it all seems to be DOS based bat file driven.  How do you update the bios using Linux?

Bob

Get a FreeDOS boot image for an USB stick and flash using that.

---

### Post by rbrown3rd on 2010-10-19
> **coolvibe said:**
> Get a FreeDOS boot image for an USB stick and flash using that.

Sounds promising. Is there a step by step anywhere?

---

### Post by jantab on 2010-10-30
Now about this brightness control issue:

Fix #25 had worked for me until upgrading to maverick, when I had to remove nomodeset from my kernel settings to be able to get to the desktop. As kernel modesetting was disabled, I kept booting into text mode.

Finally I found another fix which works perfectly. It's a Maverick kernel experimental patch:
[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

Just works! Hope this is incorporated into an official kernel soon.

---

### Post by Lycandreams on 2010-11-24
[QUOTE][QUOTE]Hey people,

I read pretty much everything that has been said in this topic, and it kinda lost me a bit. I have an Acer 5810TG a couple of months ago I had Lucid Lynx on a dual boot with vista but then I formatted the linux partition and installed Maverick Meerkat, my issues are:

[LIST=1]
[*]How do I get the intel GPU to work, because so far it's working on ATI?

[*]Even on ATI, I'm using the linux drivers and cannot adjust the brightness (for my case it's always on low)

[*]I can't get more than 2h45 for a battery life so if someone could help on that because I mainly work outdoors where there's no plug and like everybody here i bought the laptop for the battery
[/LIST]

UPDATE:

I've managed to install the script that runs switcheroo by [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
the script works and I can switch between GPUs but there is no difference so I can't tell if it is really switching or not..!!

Second UPDATE:

Turns out I was wrong and the script works great, I can now switch between cards without powering off and the best thing is that my battery lasts 5h30 now, with the wifi on and an average brightness, if I turn the brightness to the lowest possible and turn off the Wireless it goes up until 7 hours !!

Now I just need to figure out how to make the brightness hotkeys work, because I've been controling the brightness from the terminal.

---

### Post by rbrown3rd on 2011-05-16
I have most of the issues worked out on my 5810 running 11.04 but for one.  The old microphone problem with video chat.  I can make it work using AlsaMixer but I literally have to hold the capture left/right slider to one side or the other while talking. In other words the advice I picked up in one of the threads on the topic revealed that the microphone capture slider has to be moved to one side or the other for the microphone to work.  In my case it will not "stick" so I have to hold it which is a big pain.  Any suggestions?

---

### Post by hefistion on 2011-07-18
> **rbrown3rd said:**
> I have most of the issues worked out on my 5810 running 11.04 but for one.  The old microphone problem with video chat.  I can make it work using AlsaMixer but I literally have to hold the capture left/right slider to one side or the other while talking. In other words the advice I picked up in one of the threads on the topic revealed that the microphone capture slider has to be moved to one side or the other for the microphone to work.  In my case it will not "stick" so I have to hold it which is a big pain.  Any suggestions?
Idem, kubuntu 11.04

salu2

---

### Post by rbrown3rd on 2011-07-18
> **hefistion said:**
> Idem, kubuntu 11.04

salu2

That's very cryptic.  Are you saying to use Kubuntu 11.04 instead of Ubuntu 11.04?   What is idem?

---

