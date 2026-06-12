---
title: "Does the fpit (Fujitsu touchscreen) driver work with Gutsy or Hardy?"
date: 2008-04-22
forum: Hardware
---

### Post by cyriss on 2008-04-22
Hi everyone,

I've got a Fujitsu 3500 tablet PC that I'm trying to get Hardy (and eventually Ubuntu Mobile) working on.  Currently, I'm having a lot of trouble getting the touchscreen to work.  I've followed the HOWTO here:

[http://ubuntuforums.org/showthread.php?t=456110](http://ubuntuforums.org/showthread.php?t=456110)

The main problem that I'm having is that when I touch the touchscreen, X restarts so it seems that it doesn't like something about the fpit driver.

I haven't seen any posts indicating success with the fpit driver and the 3400/3500 under any versions of Ubuntu after Feisty, so perhaps its a problem with newer versions of X?

I'm hoping that someone may have gotten gotten fpit to work with Gutsy or Hardy and can offer me some advice.  If it is X, is it possible to downgrade to 7 or even 6.8 (I believe one person suggested that this was the last version to support fpit) or is this just too old to run on new Ubuntu versions?  

Any help would be greatly appreciated!

thanks,
Graham

---

### Post by ace214 on 2008-04-23
I got it working on Gutsy but not on Hardy. [I am actually filing a bug report.]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/220869")

I've also tried compiling the fpit module from source and it seems to do nothing. My setserial is a little different from that howto. It's the one I used in Gutsy from the discussion at [this topic]("http://ubuntuforums.org/showthread.php?t=146279&page=2").

---

### Post by cyriss on 2008-04-23
Thanks for the reply.  Did X crash (restart) on you in Hardy?  What kind of symptoms did you experience?  Also, what kind of tablet do you have?  The thread you referred to suggests a Gateway cx2610.

---

### Post by ace214 on 2008-04-23
Yes X crashes when I get the pen near the screen. My laptop is a Gateway c2619.

---

### Post by sohack on 2008-04-28
hello guys, just another linux user. I went through the whole process on how to get the fujitsu (fpit) driver set up on Gutsy by patching or replacing the xf86Fpit.c file and it just worked!!!!!!!!!!. I've got a cx2735m convertible Gateway with a FPI2004 Fujitsu on it. 

After upgrading to Hardy, all problems came back, X server started crashing whenever I get the pen near the Touchscreen. Any suggestions would be extremely appreciated guys.

Thanks in advance

---

### Post by ace214 on 2008-04-28
I filed a bug report but it hasn't been responded to. Perhaps you guys could go post on the bug page stating that you have the issue as well. The link is in my former post.

---

### Post by aziobro on 2008-04-29
This seems to be related to xorg-server 1.4. I have found some bug reports elsewhere relating to this same issue.
[http://bugs.gentoo.org/show_bug.cgi?id=193193](http://bugs.gentoo.org/show_bug.cgi?id=193193)

[https://bugs.freedesktop.org/show_bug.cgi?id=14057](https://bugs.freedesktop.org/show_bug.cgi?id=14057)

I have followed some of the patches and managed to get the driver to load and not crash the system.
I also tried to fix the scaling issue.
I managed to get xinput to report the messages of movement, button presses from the driver, but the mouse cursor does not respond to it. 

I have a gateway cx210x that was working with a modified version of the fpit driver. 
There seems to be a lot of posts related to issues with xorg server 1.4. There are also mentions of this being fixed in a newer version of xorg server, but I have to figured out how to use these fixes.

---

### Post by ace214 on 2008-04-29
Yes, I just posted on the freedesktop buzilla this afternoon and am also trying to get it fixed. I will post back here if anything happens as it seems to be an upstream issue.

If I use the most recent GIT version, X doesn't crash but the pointer doesn't work. If I use the recent patches posted on that bugzilla page, X crashes...

---

### Post by ace214 on 2008-04-30
Ok, if I use the latest GIT version of the driver AND I do not use the AlwaysCore option in my xorg.conf and have SendCoreEvents "true" the pen registers on the screen. Follow the other topics to set your setserial. It didn't work for me unless I did not have a BaudRate option in my xorg.conf. But now everything works. Ask if you need more specific information.

I have attached the compiled driver. It goes in /usr/lib/xorg/modules/input/.

---

### Post by sohack on 2008-04-30
OK, guys it finally worked after spending about 3 hours. Just like ACE214 said, download the GIT version  "git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-input-fpit", you need to apply the patch they provide you with, which is basically the one that worked for me so I have attached a copy of my "xorg.conf and the "patch" in question. Set the correct UART, PORT and IRQ values through "setserial", Compile it and that should do it.


THanks for your help.

---

### Post by ace214 on 2008-04-30
I did not use that patch....
I'll try it later to see if it makes any difference.

---

### Post by montgoj on 2008-05-01
Ok, I've got most of the way through this.  But how do I determine the correct "UART, PORT and IRQ values" for setserial?

---

### Post by ace214 on 2008-05-01
> **montgoj said:**
> Ok, I've got most of the way through this.  But how do I determine the correct "UART, PORT and IRQ values" for setserial?

Type "dmesg | grep ttyS0" into a terminal.

---

### Post by z_kvn on 2008-05-02
wonderful, i gonna check it out tonight with my Fujitsu U810
Hope everything work out smoothly~

---

### Post by sohack on 2008-05-03
hmmm, it seems that for some reason, whenever I do "xrandr -o inverted" for going to Tablet mode, I get no clicking neither with the stylus nor with the touchpad, however it does track the cursor

---

### Post by TomDupont on 2008-05-11
I tried this version on my Stylistic lt c-500 freshly upgraded to heron.  The X server did not crash anymore like the one from the repository.  

  But I have issue with the calibration.  The sensitive area of the screen is just a little square about the size of a touchpad located to top left corner.  If I travel inside this box.   I can see the arrow crossing the screen    

   I tried to tune with the options  : 
         Option "MaximumXPosition" "800"    # old value 4096 
         Option "MaximumYPosition" "600"    # old value 4096
         Option "MinimumXPosition" "10"       # old value 0
         Option "MinimumYPosition" "10"       # old value 0

But it did not changed anything.


I will look forward.

Thank for your help.


B.R.
Tom

---

### Post by ace214 on 2008-05-11
> **TomDupont said:**
> 
         Option "MaximumXPosition" "800"    # old value 4096 
         Option "MaximumYPosition" "600"    # old value 4096
         Option "MinimumXPosition" "10"       # old value 0
         Option "MinimumYPosition" "10"       # old value 0

Try multiplying each of these by 10 (i.e. 8000, 6000, 100, 100).

---

### Post by cyriss on 2008-05-15
I installed the compiled driver that ace214 posted (thanks!) on my Stylistic 3500 running a fresh Hardy install.  The touchscreen works now without crashing, but I'm having the same scale problem as TomDupont (only a small 2x2" square of the screen registers touch, although its scaled up to the entire screen).  I tried multiplying the Max/Min X/Y Position values in xorg.conf, but it doesn't make any difference.  Any ideas?

---

### Post by nashley on 2008-05-16
I can confirm this patched driver (from ace214) works for Stylistic ST4110P & Hardy/8.0.4 using more or less the same xorg.conf as sohack.

I had to set BaudRate=9600, Passive=True (it's the P in 4110P), TrackRandR (not tested, but no crash), SendCoreEvents=True, Device=/dev/ttyS0 and MaximumXPosition=MaximumYPosition=4096, MinimumXPosition=MinumumYPosition=0

(the pointer jumped around wildly when BaudRate WASN'T set, although it could be me not understanding xorg.conf format; 'Option "BaudRate"' with no value made it go bad...)

setserial /dev/ttyS0 irq 4 port 0x0220 autoconfig with /etc/serial.conf the same

I commented out my "Synaptics Touchpad" /dev/psaux section.

(And as an aside, I had to use "Driver" "i810" for the configured video device to get a non-corrupted display beforehand)

Thanks all!

---

### Post by cyriss on 2008-05-18
Well, I couldn't get the patched or unpatched fpit driver to work properly on my 3500 (still was having the weird scaling issue regardless of how my xorg.conf was configured), so I modified the source to scale the xy values that the drive posts to the xserver.  It ain't pretty and it's certainly not the proper way to fix the problem, but it works.  I'm included a copy of my compiled driver in the hope that it helps someone else.  The scaling constants were derived empirically for my tablet (Fujitsu Stylistic 3500), but it would certainly be easy to change for other devices. 

Just stick it in /usr/lib/xorg/modules/input and you should be good to go.

-Graham

---

### Post by Rayagreen on 2008-05-22
I used your patched driver on my Stylistic 3400 and no more resets.  It also detects the stylus but the scaling is off.  The pointer tracks well with the taps in the upper left corner and drifts further ahead as I tap lower or to the right.  I'm pretty sure that's because the 3400 is 800x600 to the 3500's 1024x768 resolution.  Would you mind compiling a driver with constants for 800x600 resolution or describe where you changed the scaling in the driver so I can give it a shot?

Thanks



> **cyriss said:**
> Well, I couldn't get the patched or unpatched fpit driver to work properly on my 3500 (still was having the weird scaling issue regardless of how my xorg.conf was configured), so I modified the source to scale the xy values that the drive posts to the xserver.  It ain't pretty and it's certainly not the proper way to fix the problem, but it works.  I'm included a copy of my compiled driver in the hope that it helps someone else.  The scaling constants were derived empirically for my tablet (Fujitsu Stylistic 3500), but it would certainly be easy to change for other devices. 

Just stick it in /usr/lib/xorg/modules/input and you should be good to go.

-Graham

---

### Post by cyriss on 2008-05-24
Here's a copy of the driver that should work for 800x600 displays.  This archive also includes the source so you can modify the constants further if you want.

---

### Post by DacKodo on 2008-05-26
I used:

```

Section "InputDevice"
        ....
        Option		"MaximumXPosition"	"1024" # resolution of
        Option		"MaximumYPosition"	"768"  # my screen
        Option		"MinimumXPosition"	"0"
        Option		"MinimumYPosition"	"0"
        ....
```

```

Section "Monitor"
        ....
        DisplaySize     211 158  # screen size in mm
        ....
```

This works great on my 4110P.

PS. Thanks!

---

### Post by Rayagreen on 2008-05-27
> **cyriss said:**
> Here's a copy of the driver that should work for 800x600 displays.  This archive also includes the source so you can modify the constants further if you want.
Cyriss,
That worked great.  Thanks!

---

### Post by smesohotech on 2008-05-28
> **Rayagreen said:**
> Cyriss,
That worked great.  Thanks!
I also used Cyriss 800x600 driver but still have the tracking problem. Could it be due to the xorg.conf? I am using a 3500 with 800x600 screen.

---

### Post by cyriss on 2008-05-28
Does the other drive I posted work with the display set to 1024x768?  Please describe the scaling problem and post your xorg.conf.

---

### Post by smesohotech on 2008-05-29
> **cyriss said:**
> Does the other drive I posted work with the display set to 1024x768?  Please describe the scaling problem and post your xorg.conf.

Hi my display is not the 1024x768 its the svga indoor one. :( My problem is the same as the other guy - touch anywhere and it goes to the top left hand corner but your 800x600 driver doesnt seem to work for my 3500.

---

### Post by cyriss on 2008-05-31
Are you sure that your device uses /dev/ttyS0 (my 3500 uses /dev/ttyS1)?  There are a few other settings in your xorg.conf and serial.conf that are different from mine as well (MaximumXPosition/MaximumYPosition are usually 4070/4020 on the 3500 and your baud rate seems high).  Here are copies of my xorf.conf and serial.conf; give them a try and let me know what happens.

-Graham

---

### Post by smesohotech on 2008-06-01
hi many thanks it worked. You are right, its ttyS1. However the pointer is slightly out of alignment, I guess I have to fiddle with the X and Y coordinates.

---

### Post by themischiev on 2008-06-26
STYLISTIC 3400 HARDDRIVE IMAGE FOR DOWNLOAD?

I wonder if any of you have an image of the Fujitsu Stylistic 3400 hard drive that I could download, what happens is that I was trying to install an operating system in the unit but with no success. (I DON'T HAVE THE EXTERNAL FLOPPY UNIT)

---

### Post by tkrause22 on 2008-07-09
hey great thread I have a gateway cx2618 and my pen tracks great but no right click on the body of the pen any help with this would be appreciated.

---

### Post by tkrause22 on 2008-07-09
> **sohack said:**
> hmmm, it seems that for some reason, whenever I do "xrandr -o inverted" for going to Tablet mode, I get no clicking neither with the stylus nor with the touchpad, however it does track the cursor

I have the same problem any help here?:-k

---

### Post by forcijo on 2008-07-14
> **sohack said:**
> OK, guys it finally worked after spending about 3 hours. Just like ACE214 said, download the GIT version  "git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-input-fpit", you need to apply the patch they provide you with, which is basically the one that worked for me so I have attached a copy of my "xorg.conf and the "patch" in question. Set the correct UART, PORT and IRQ values through "setserial", Compile it and that should do it.


THanks for your help.

Hi,

I'm pretty new with Linux.  I have a Stylistic 3400 with Ubuntu.   How do I apply this patch? I have the driver and the patch ....just don't know how to combine them.  I'm ok with setserial & xorg.conf.

John

---

### Post by cyriss on 2008-07-15
You don't need to patch and compile the source.  Look back at the rest of this thread for two pre-compiled versions of the driver (one for 1024x768 and one for 800x600) that I posted.  Both should work on the 3400.

---

### Post by stylistic on 2008-07-16
Could anybody tell me how to compile xf86FPit.c?

The header files are not found. I tried looking for them by myself in */usr/dev*, but not all header files were found (e.g. 
*exevents.h*. Others were there several times
(e. g. *errno.h*).

I tried to compile my own version as the scaling factor SCALE_Y in the patched driver for 800x600 is producing a deviation of like 1cm at the bottom of the screen. I just thought of patching this.

---

### Post by forcijo on 2008-07-16
> **cyriss said:**
> You don't need to patch and compile the source.  Look back at the rest of this thread for two pre-compiled versions of the driver (one for 1024x768 and one for 800x600) that I posted.  Both should work on the 3400.

Cyriss,

Thanks for the reply. I tried your serial.conf, xorg.conf, and xf86FPit.  No luck.  I've also tried every other combo possible as posted in this forum. The pen works but only in the upper left corner with a full screen scaling.  Somehow the computer thinks the touchscreen is a mouse and multiplies the position by a factor by five or so.  It's been a long frustrating week and if I gksudo and restart one more time I'll scream.   My problem is somewhere other than in my xorg and setserial.  I'm open for suggestions.

John

---

### Post by huhabla on 2008-09-17
> **forcijo said:**
> Cyriss,

Thanks for the reply. I tried your serial.conf, xorg.conf, and xf86FPit.  No luck.  I've also tried every other combo possible as posted in this forum. The pen works but only in the upper left corner with a full screen scaling.  Somehow the computer thinks the touchscreen is a mouse and multiplies the position by a factor by five or so.  It's been a long frustrating week and if I gksudo and restart one more time I'll scream.   My problem is somewhere other than in my xorg and setserial.  I'm open for suggestions.

John

Hi,
i have patched the fpit driver to solve the scaling issue.
Additionally i have implemented an automated tablet calibration.
Now the driver is working without any problems on my FS ST4120pw.
A patch for the latest git version is attatched. It would be great if 
anyboy can test the patched driver on a different tablet pc.
Any feedback is welcome. 

Soeren

---

### Post by ulukapata on 2008-09-17
this'll tell you...

[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

---

### Post by huhabla on 2008-09-17
> **stylistic said:**
> Could anybody tell me how to compile xf86FPit.c?

The header files are not found. I tried looking for them by myself in */usr/dev*, but not all header files were found (e.g. 
*exevents.h*. Others were there several times
(e. g. *errno.h*).

I tried to compile my own version as the scaling factor SCALE_Y in the patched driver for 800x600 is producing a deviation of like 1cm at the bottom of the screen. I just thought of patching this.

Hi,
you need the xorg-sdk and the libtool library. If you have installed
them, the autogen.sh script will create all needed files. 
Then ./configure && make will build the driver.

Soeren

---

### Post by pwebster25 on 2008-11-02
> **tkrause22 said:**
> hey great thread I have a gateway cx2618 and my pen tracks great but no right click on the body of the pen any help with this would be appreciated.

I am trying to setup a the fpit on my cx2618.  What instruction set did you follow to set yours up?  Did you ever resolve the right click thing?  My pen doesn't track at all yet but I think I have installed the fpit driver.  I run Hardy on it and am a fairly nube but can use the terminal.

There are so many different sub-threads in this thread, I'm not sure which one to follow.

My resolution is 1280 x 768 (wider than most of those listed on here).

---

### Post by shahav on 2009-04-22
> **cyriss said:**
> Here's a copy of the driver that should work for 800x600 displays.  This archive also includes the source so you can modify the constants further if you want.

This indeed solved the problem on my fj-3400, now the touchscreen works just fine, before it was acting as a small touch*pad* in the upper left corner.
once again, 10x
R.

---

### Post by perryc on 2009-04-29
Just installed Jaunty (9.04) and had the 10X scale problem with the touchscreen on my Stylistic 3500 until I added "TrackRandR" "on" to the  to xorg.conf.  My touchscreen section now looks like this:

```
Section "InputDevice"
        Identifier      "Touchscreen"
        Driver          "fpit"
        Option          "Device"                "/dev/ttyS1"
        Option          "BaudRate"              "9600"
        Option          "Passive"
        Option          "CorePointer"
#        Option         "Rotate"                "CW" <= works, but screen does not rotate via xrandr
        Option          "MaximumXPosition"      "4070"
        Option          "MaximumYPosition"      "4020"
        Option          "MinimumXPosition"      "0"
        Option          "MinimumYPosition"      "0" 
        Option          "TrackRandR"               "on"
EndSection

```

---

### Post by cgalpin on 2009-05-29
Thanks perryc!

The "TrackRandR" option fixed it for my Stylistic LT C-500 as well, with the default jaunty xserver-xorg-input-fpit

---

