---
title: "Wacom pen &amp; touch (CTH 460) stopped working"
date: 2010-08-22
forum: Hardware
---

### Post by elektra on 2010-08-22
So I got my CTH 460 (pen & touch) working fine by following these instructions [http://gutsywww.ubuntuforums.org/showthread.php?t=1515562](http://gutsywww.ubuntuforums.org/showthread.php?t=1515562) (thanks Favux for the marvellous How To btw) and all was good with the world.
Then I turned my laptop on without having the wacom plugged in and the next time I plugged the tablet in, it didn't work. So I did a bit of digging and figured that this was due to hotplugging issues because I'm using the xorg driver. Since trying to fix this I have also run an update so my kernal version has changed, which has made the situation even more difficult. 

xinput --list returns no wacom info at all but the tablet shows up under lsusb.
the xorg conf file is still in place and the wacom module still appears under /etc/modules so I guess it's still loading
however, my xf86-input-wacom directory has disappeared and when I tried just ripping it all out and starting from scratch the instructions above fail at this point because the rebuild doesn't build this directory. Anybody know how to get around or fix this?

can anybody give me any ideas on what to try to get this working again please? and is it possible to get it working so that I can unplug it without going through this every time? If this has been covered before could someone point me to the link please?

system: acer aspire 5315, lucid lynx, kernal version 2.6.32-24-generic 
tablet: CTH 460 wacom bamboo pen & touch 

any help would be greatly appreciated

---

### Post by Favux on 2010-08-22
Hi elektra,

Welcome to Ubuntu forums!

To hot plug you have to use the 10-wacom.conf, not the xorg.conf.

When a new kernel comes through the wacom.ko that is in it's modules directory is the default 0.8.4-4 which doesn't work for the Bamboo P&T.  Just recompile the 0.8.8-8 wacom.ko (I.) and copy it into place.

Not sure what you're talking about with the xf86-input-wacom directory.  But you should be able to tell Synaptic Package Manager to install or reinstall xserver-xorg-input-wacom which will get you the default Lucid 0.10.5 xf86-input-wacom.  Then just clone the git and compile over it (II.).

---

### Post by elektra on 2010-08-23
Hi Favux,

thanks so much for your help, much appreciated. I'm trying to recompile the linuxwacom and have run into another problem at this point:

[FONT=monospace]sudo cp ./src/2.6.30/wacom.ko /lib/modules/'uname -r'/kernel/drivers/input/tablet/wacom.ko

I'm substituting '2.6.32-24-generic -r' for 'uname -r' as this is the kernel that I'm running and I keep getting the error:

cp: cannot create regular file '/lib/modules/2.6.32-24.generic -r/kernel/drivers/input/tablet/wacom.ko': No such file or directory

any ideas what I'm doing wrong? I've manually checked and the wacom.ko file is in the destination kernel directory but I don't know if this is the default one or the one I'm trying to replace it with, if that makes sense. 

Toying with the idea of just moving on if I can't sort it and coming back to it later if it becomes a problem, what do you think?
[/FONT]

---

### Post by elektra on 2010-08-23
So I pushed on, rebooted and hurrah, the tablet is recognised and kinda works. Then I followed the rest of the directions and cloned git and built xf86-input-wacom. Everything worked fine up until ./autogen.sh --prefix=/usr under xf86-input-wacom when I got this:

No package 'xrandr' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


which I'm guessing is an unmet dependency??

so I tried installing xrandr to be told that x11-xserver-utils has replaced it, so I installed that instead and got exactly the same error. 

any suggestions as to how I solve this please? I've attached a dump of the terminal output, just in case it's my error and I can't see it (more than likely as I'm not entirely sure what I'm doing, other than following someone else's masterful directions). 

Any help would be greatly appreciated, as I really need to get this working and it's now confusing the hell outta me

thanks

---

### Post by Favux on 2010-08-23
It looks like 'libxrandr-dev' is the unmet dependency.  So either add it to the dependency line or:
```
sudo apt-get libxrandr-dev
```

I'm able to compile xf86-input-wacom without it.  I do have libxrandr2 installed.  Maybe it's video card or video driver specific?  Which video card and video driver do you have?

---

### Post by elektra on 2010-08-23
thanks for that, much appreciated. 

If I've queried this correctly the graphics card is an Intel GM965/GL960 Integrated Controller. Does that sound right? Or am I looking at the wrong info? 

Will try installing libxrandr-dev now and let you know if I get success

Out of curiosity is there a common/logical way of working out what missing dependencies are in these situations? Would be really cool if I could learn how to figure these things out....
 
Thanks again for your help

---

### Post by Favux on 2010-08-23
Hi elektra,

> If I've queried this correctly the graphics card is an Intel GM965/GL960 Integrated Controller. Does that sound right?
That's right.
```
lspci | grep VGA
```
> Out of curiosity is there a common/logical way of working out what missing dependencies are in these situations?
Not that I know of.  Basically you hope for a clue in the configure or make file and google it and also check for it in Synaptic Package Manager.

---

### Post by elektra on 2010-08-23
It works!  :D

Hot-plugging now working (so far, anyway) and Chris Bagwell's suggestion for modifying the wcmCommon.c file has definitely made an improvement to the touch, so thanks for including that in the How To. 

Presumably every time I update the kernel I'll need to recompile linuxwacom and xf86-input-wacom? 

Will I need to replace the 10-wacom.conf file every time as well? I am using the 50-wacom.conf file, but I've inserted it into the 10-wacom.conf file that was already in /usr/lib/X11/xorg.conf.d/. (by deleting what was there then copying & pasting) - that's ok, right?

Oh, and I double checked the graphics card info and it's definitely an Intel GM965/GL960. 

Thanks so much for your help Favux, and all the work you and everyone else put into the development of these drivers, appreciate it.

I'm off to play with my new tablet :lolflag:

---

### Post by Favux on 2010-08-23
Great!  :)
> Presumably every time I update the kernel I'll need to recompile linuxwacom and xf86-input-wacom? 
Just linuxwacom for the wacom.ko.
> Will I need to replace the 10-wacom.conf file every time as well?
No.
> I am using the 50-wacom.conf file, but I've inserted it into the 10-wacom.conf file that was already in /usr/lib/X11/xorg.conf.d/. (by deleting what was there then copying & pasting) - that's ok, right?
Shouldn't be a problem for you.

---

### Post by elektra on 2010-09-16
Thanks for the clarification Favux, much appreciated. 

3 weeks on and the tablet is still working fine, even the hotplugging is working :D  

thanks again for the help

---

### Post by Jammet2 on 2010-11-08
Can anyone sum up in 3 sentences what one must do to get the CTH 460 Bamboo USB working? Default configuration, no bells, no whistles, no choices, no extras, no 'you can do it here, OR there'? No Enterprise A, B C or D?".

Get driver-x. ./configure --with-usb -X ; make ; make install
Edit line 3 of whatever.conf, remove #, save, quit, reboot. DONE!

Anything like that?

PS: I'm sorry. Having a really bad day here.

---

### Post by Favux on 2010-11-08
Hi Jammet2,

Follow the Bamboo P&T HOW TO step I. to compile a wacom.ko.  Couple of minutes and your done.  See:  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

---

### Post by Jammet2 on 2010-11-09
Thank you, so much! Again you saved me there, and yes, it only took compiling the package and rebooting. I hope my early comment didn't strike you as overly rude, I apologise, too. :)

---

### Post by manixtate on 2010-11-16
Hi, 

Just a query to those who know.

I'm thinking about getting this tablet for Christmas. 

I would like to know whether there is support for the gesture controls at all?

TIA for any responses.

---

### Post by Favux on 2010-11-16
Hi manixtate,

Yes there are gestures.  One finger dbl tap left click, two finger dbl tap right click.  Two finger horizontal and vertical scrolling.  Pinch zoom.  And two finger rotate.

Of course it depends on what app. you're in.

Gesture code is being changed from the original linuxwacom type to MT compliant code.  Patches have been submitted to xf86-input-wacom and MT code for the wacom.ko (usb kernel driver) has been submitted and is expected in kernel 2.6.37.

---

### Post by manixtate on 2010-11-18
Thanks very much for your quick rply favux.:D

I think I'll spend the lire.

Sorry for the late response.:p

---

### Post by akshat_space on 2011-01-26
I have bought Wacom Bamboo Pen & Touch yesterday [Model No. CTH-460/k] and tried all options as given on following url [http://gutsywww.ubuntuforums.org/showthread.php?t=1515562](http://gutsywww.ubuntuforums.org/showthread.php?t=1515562)
But none of them worked for me in both Ubuntu 10.04 and 10.10.

I have also added my device in the downloaded driver and compiled it again as suggested on the following url :
[http://ubuntuforums.org/showpost.php?p=9496756&postcount=2](http://ubuntuforums.org/showpost.php?p=9496756&postcount=2)

But none of the methods worked for me...:(
Any help will be greatly appreciated.....

---

### Post by Favux on 2011-01-26
Hi akshat_space,

Welcome to Ubuntu forums!

That should have worked.  You have the 0xd6 correct?  As long as you add your model to the linuxwacom 0.8.8-10 wacom_wac.c or use input-wacom 0.10.10-1 for the wacom.ko and clone the xf86-input-wacom git repository it should be working.

Problems could arise if you installed a dkms version of the wacom.ko.  Or if you had a problem compiling it or copying it into place.  Also sometimes it doesn't auto-load.  Check that with:
```
lsmod | grep wacom
```
You should see 'wacom' in the output.  Some 64-bit systems need an extra flag, see Troubleshooting in the HOW TO.

With the X driver xf86-input-wacom the problems come down to whether you have uninstalled xserver-xorg-input-all (you need it) or whether there was a problem with the compile.

---

### Post by akshat_space on 2011-01-26
Hey, Favux thanks for your quick reply....

Yes mine is 0xd6.

I have started the installation from scratch again and uinstalled the xserver-xorg-input-wacom and wacom-dkms installed earlier.

This time I have used linuxwacom-0.8.8-10 kernel driver and xf86-input-wacom-0.10.3.
Now, my stylus is working but its not recognizing the touch and Buttons and in Gimp the Eraser is not working.
I tried input-wacom-0.10.10 also but same result.:(

The output of xinput --list is....
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Pen              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Finger           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

and the output of dmesg | grep Wacom is....

```
[   13.217654] input: Wacom BambooPT 2FG 4x5 Pen as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input5
[   13.232396] input: Wacom BambooPT 2FG 4x5 Finger as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input6
[   13.238413] wacom: v1.52-pc-0.3:USB Wacom tablet driver

```

and lsmod | grep wacom shows....
```
wacom                  33409  0 
```

Please suggest how can I get the Touch, Buttons and Eraser working.

---

### Post by akshat_space on 2011-01-27
Now , When I an installing xserver-xorg-input-wacom and configuring the file gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf and adding the content with your ***Favux_Bamboo-Pen&Touch_test3.xorg.conf.txt*** file into mine, the touch and buttons started working but now Stylus is not working and the *touch is very jumpy* cant able to do anything with that touch. How, can I fix it...

Now, the input of xinput --list is...
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; stylus                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=7	[slave  pointer  (2)]
&#9116;   &#8627; touch                                   	id=8	[slave  pointer  (2)]
&#9116;   &#8627; pad                                     	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; Power Button                            	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]


```

Please help....:frown:

---

### Post by Favux on 2011-01-27
Hi akshat_space,

OK, you added your new Bamboo Pen & Touch model (CTH460/K; Product ID = 0xd6) to the wacom_wac.c of linuxwacom 0.8.8-10 before compiling as per post #2, correct?
> This time I have used linuxwacom-0.8.8-10 kernel driver and xf86-input-wacom-0.10.3.
Now the question becomes are you really using xf86-input-wacom-0.10.3?  Why did you not clone the git repository for 0.10.10+ as in part II.?  0.10.3 is very old and doesn't support Bamboo P&T's, much less your new model.

You should not need to use the xorg.conf.  The usb snippet in the wacom.conf in xorg.conf.d should be fine.  I'd comment out or remove your wacom entries in the xorg.conf.

---

