---
title: "Wacom issues"
date: 2009-08-10
forum: Hardware
---

### Post by jqke on 2009-08-10
In short, my Wacom tablet is crashing Jaunty.


I loved the plug-it-in-and-go, but, entering GIMP I noticed I got no pressure sensitivity.

So I looked through everything I could find on the forums and on other help pages concerning the ubuntu + Wacom issue.

Lo and behold, being the young anxious pup I am, I started typing things away in the terminal and testing and retesting and typing and installing and now as a consequence of my impatience I am left with this problem.

I plug in the tablet, and it's all good. I can navigate, double click, etc, but as soon as I open a program the screen goes black and blinks occasionally when I drag the cursor. If I unplug it soon after the screen goes black I am brought to the login screen. If I do not, my laptop becomes unresponsive and I have to power down.


What can I do to go clean slate and start over again? If possible. And where can I find a SIMPLE and EASY walk-through for setting up my tablet?

I'm new, if you couldn't tell.

I just want my wacom to work! I really don't want to use Windows every time I want to use Illustrator/GIMP.

Thanks.

---

### Post by Favux on 2009-08-10
Hi jqke,

We need some more information.  What Wacom tablet do you have?  Do you remember what you did?  Can you tell us what it was?

So right now you can boot your laptop, correct?  Can you boot it with the Wacom tablet plugged in?

---

### Post by jqke on 2009-08-10
I have a small Wacom Bamboo. I do not remember everything I did.

I installed/downloaded a few things through the terminal. The thing that seemed to start the problem was when I opened a code page and pasted something in that was for configuring the tablet and saved it as an fdi file. I think it was fdi?

I can boot it, yes, and with the tablet plugged in. The problem occurs when I open a program like gimp.

---

### Post by jqke on 2009-08-10
I'm sure I did each of these from the Wacom Community Document.

sudo apt-get install xserver-xorg-input-wacom wacom-tools

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.default

sudo gedit /etc/X11/xorg.conf

sudo kate /etc/X11/xorg.conf

---

### Post by Favux on 2009-08-10
Hi jqke,

That doesn't sound too bad.  Which .fdi file did you put in and where did you get it?

In Jaunty you don't need the xorg.conf anymore.  That's most likely the problem.  Could you post your current xorg.conf?

Jaunty uses HAL/.fdi.  HAL (hardware abstraction layer) and .fdi (device information file).

You should have the two linuxwacom packages you mentioned installed.  In Jaunty they are a special version of 0.8.2-2 that has been patched to support Xserver 1.6 and HAL.  Check in Synaptic Package Manager that both are installed and are the 0.8.2-2 version.

---

### Post by jqke on 2009-08-10
My actions are so impulsive :b

I also followed the "manual installation" instructions here to attempt to solve the crashing problem this yesterday:

[http://www.moosechips.com/tag/wacomfdi/](http://www.moosechips.com/tag/wacomfdi/)

Where can I find the xorg.conf?

---

### Post by jqke on 2009-08-10
By the way, I can't thank you enough for your help.

---

### Post by jqke on 2009-08-10
I just tried to boot my laptop with the tablet plugged in and it brought me to the ubuntu load screen and then the screen turned black for ten minutes or so until I powered down and rebooted without it plugged in and it worked fine.

---

### Post by Favux on 2009-08-10
Hi jqke,

Not a problem.  The location is in the sudo commands above.
```
/etc/X11/
```
You can get there with Places (Nautilus).  You should also have a backup called "xorg.conf.default".  That's probably what we want to restore.  So post both of them.   By the way if you are in Ubuntu and not Kubuntu to edit it you use:
```
gksudo gedit /etc/X11/xorg.conf
```
But first you have to be careful and make a backup, which is what this line is doing:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.default

```
Except you may want to change the name of the backup file.

---

### Post by jqke on 2009-08-10
I did a file search in my home files and computer for "xorg" and found nothing.

When I put in the second code

gksudo gedit /etc/x11/xorg.conf

I get this:

Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
tobin@ubuntu:~$ sudo cp etc/x11/xorg.conf /etc/x11/xorg.conf.default
cp: cannot stat `etc/x11/xorg.conf': No such file or directory

---

### Post by jqke on 2009-08-10
No files with "xorg," but eight or nine in the linux_wacom folder with "config"

---

### Post by Favux on 2009-08-10
Hi jqke,

I didn't ask you to run either of those commands.  I wanted you to go to "/etc/X11/" using Nautilus and find the two files, right-click on them and open them in text editor and post them (copy and paste).  Also what "linux_wacom folder"?  What is that?  Did you install something from a tar package you downloaded?  Are you still using the terminal you used for that?

Also noticed you haven't yet answered some of my questions.  For example I wanted you to check in Synaptic if the linuxwacom packages are installed (but not to install them if they aren't), and if so what versions.

So slow down, reread stuff.  We'll get there.

---

### Post by jqke on 2009-08-10
Here is xorg.conf:

_________________________________________________________

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
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

___________________________________________


I could not locate the xorg.conf.default file.


I checked synaptics and found both wacom-tools and X.Org X server, both are 1:0.8.2.2-0ubuntu2


I did install something from a package, yes. I do not have the same terminal up. But I followed the directions that I found in the readme of the package, which are:

--------------------------------------------------

Most end users would probably only need to update the Wacom X driver and the /etc/X11/xorg.conf file to use the rich features that Wacom tablets offer. The steps could be as simple as:

download the package then
    $ bunzip2 linuxwacom.tar.bz2
    $ tar xvf linuxwacom.tar
    $ cd linuxwacom/prebuilt
    $ su
    # ./uninstall
    # ./install
    # cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
    # gedit /etc/X11/xorg.conf
    # reboot

------------------------------------------------

Looking at the readme *slowly* :) it has a date from 2007 on it.

---

### Post by Favux on 2009-08-10
Hi jqke,

Have to go, back in a few.  The xorg.conf looks good, no changes.

You can't mix versions of linuxwacom.  It looks like you downloaded one and tried to install it.  Was in 0.8.1-4?  Do you still have the unpacked tar on your desktop?  The 0.8.2-2 in Synaptic, are they installed (green box)?  Just asking, don't do anything.

---

### Post by jqke on 2009-08-10
Yes it is 0.8.1-4. I unpacked it and installed, or tried to. But I do still have the unpacked tar.

The 0.8.2-2 versions I mentioned earlier are installed (green box) in synaptic.

---

### Post by Favux on 2009-08-10
Hi jqke,

Did you run the "sudo make install" and did it actually install?  If so we'll have to uninstall linuxwacom 0.8.1-4.  As you've noticed it's older.  And 0.8.1-4 doesn't support the Xserver 1.6 in Jaunty so it won't work.  Keep the unpacked tar where it is, we can use it to help uninstall.

Did you go on to do the "sudo cp src/2.6.26/wacom.ko /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko"?

---

### Post by jqke on 2009-08-11
I did run sudo make install, whether installation was successful, I do not know. It was successful enough to unpack into a seperate folder in my home files.

The second command (sudo cp src) looks very familiar, and I am quite sure that I did use it.

---

### Post by Favux on 2009-08-11
Hi jqke,

Alright so let's reverse those changes.  First let's try to get the 0.8.2-2 wacom.ko (the usb kernel driver) back in place.  This command:
```
cp /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko wacom.ko.$(uname -r)
```
should have made a backup in the directory of the path called 'wacom.ko.$(uname -r)'.  What the 'uname -r' is about is that it is a command that tells you what kernel you're currently running.  Enter it into a terminal to check it out.

This should should restore it:
```
sudo cp /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko.$(uname -r) /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko
```

Now go to Synaptic Package Manager and find both linuxwacom packages.  Right click on them and tell it to completely uninstall them.  Reboot.

When the system comes back up enter these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then in the terminal change directory into the unpacked linuxwacom 0.8.1-4 tar you used.  Then change directory into the "prebuilt" folder.  Then enter:
```
sudo ./uninstall
```
Then reboot.

Now when the system comes back it should be a blank slate concerning linuxwacom.  Now go to Synaptics and reinstall the 0.8.2-2 xserver-xorg-input-wacom and wacom tools.  Reboot.

At this point the only thing we should have to deal with is the .fdi and setting up wacomcpl.  Hopefully!

Good luck!

---

### Post by jqke on 2009-08-11
I do not have a backup file. The second command gives me this error:

cp: cannot stat `/lib/modules/2.6.28-14-generic/kernel/drivers/input/tablet/wacom.ko.2.6.28-14-generic': No such file or directory

---

### Post by Favux on 2009-08-11
Hi jqke,

Well ignore it for now and do the rest of the stuff.  We can get the wacom.ko elsewhere if we need it.

Although you could do a search for 'wacom.ko.$(uname -r)' using the output of "uname -r" in the name.  Maybe its somewhere else.

---

### Post by jqke on 2009-08-11
It works! And I can boot with it without trouble. No pressure sensitivity and limited functionality with tablet/stylus buttons.

---

### Post by Favux on 2009-08-11
Hi jqke,

Outstanding!  So now we're basically where we would be with a fresh install of Jaunty.  Unless we still have a problem with the wacom.ko.  Something to keep in the back of our minds and easily fixed if need be.  To set up your Bamboo see post #2 here:  [http://ubuntuforums.org/showthread.php?t=1184879](http://ubuntuforums.org/showthread.php?t=1184879)  This depends on if you did install a wacom.fdi of some sort somewhere.  So if you did and/or remember where we probably should deal with that too.

By the way the uninstall was basically Appendix 4 on this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  It talks about getting the correct wacom.ko.

The reason I picked Turtleman's thread is we also had to clear a linuxwacom install on his system on another thread.  So you're not alone.

---

### Post by jqke on 2009-08-12
Okay great.

Right now I'm on post #176, here: [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18), and you are saying:

> Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi. After renaming it 10-wacom.fdi of course.

-First download the attached .fdi to your desktop.

I have found the default 10-wacom.fdu, but where is the attached .fdi? Or where can I download it?

---

### Post by Favux on 2009-08-12
Hi jqke,

Did you find it?  It's attached to the bottom of the post #176.  It's labeled test 2.  Just click on it to download.

---

### Post by jqke on 2009-08-12
Okay. I replaced the .fdi file. Now I am at configuring.

I got as far as getting the input list in the terminal. How do I get to .xinitrc to replace names?

> Say you determine that 'PnP Device (WACf008 )' is the name HAL is using for your stylus. Then everywhere in .xinitrc and your rotation script where it says stylus you would replace it with 'PnP Device (WACf008 )'. Repeat this for eraser, etc. This should get wacomcpl and rotation working

This is my list:

> "Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"stylus"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"pad"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 4
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 4 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 71
        Resolution is 1
"cursor"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"eraser"    id=7    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 14760
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 9225
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1

---

### Post by Favux on 2009-08-12
Hi jqke,

You don't need to, the new 10-wacom.fdi did it for you.  If you look at the output of "xinput --list"  you will see the correct linuxwacom names are being used:  stylus, eraser, cursor, and pad.

So now you're ready to set up wacomcpl using Section 3.  That's below where you are.  You're looking at Jaunty Users 3), not Section 3 below.

---

### Post by jqke on 2009-08-12
Great! Side buttons work. Found the wacomcpl, got it set up.

The only thing is pressure sensitivity. I'm not sure how to get that going.

---

### Post by Favux on 2009-08-12
Hi jqke,

Wow!  Real progress.

That's the last link, the one to the Wacom wiki.  Near the bottom of the wiki it shows you how to set up Gimp.  You need to configure the extended input devices.

---

### Post by jqke on 2009-08-12
All right. I followed the directions for configuring extended input devices in gimp, but I still have no pressure sensitivity. I've attempted to use every tool with all possible settings for the tools, and there is no pressure sensitivity.

---

### Post by Favux on 2009-08-12
Hi jqke,

I think the only time I remember someone reporting that it turned out that it was a hardware problem.  The stylus tip was broken.

But you have a couple other possibilities we need to rule out first.  One is if you did install another .fdi?  We didn't nail that down.  Is there a "custom_wacom.fdi" or something similar in "/etc/hal/fdi/policy/"?

Also it could be the wacom.ko.  Check to see if you do have the wacom.ko backup named "wacom.ko.$(uname -r)".  It may actually be located in the root directory where you have bin, boot, etc, and sys and so on.  You could search for it, putting in whatever 'uname -r' gives in a terminal.  Or using "wacom.ko.*" (without the quotes).  Or navigate there with Places (Nautilus).  If so then this line will restore it:
```
sudo cp wacom.ko.$(uname -r) /lib/modules/$(uname -r)/kernel/drivers/input/tablet/wacom.ko
```
And then reboot.

---

### Post by jqke on 2009-08-12
I don't think it is my stylus, because I can plug in my tablet onto my desktop (running Vista), or boot my laptop (the one with ubuntu) into Vista and pressure works fine with Gimp.

The only file in "/etc/hal/fdi/policy/" is 'preferences.fdi', which contains this:

<!-- -*- SGML -*- -->
&#8722;
<!--
 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
&#8722;
<deviceinfo version="0.2">
&#8722;
<!--
 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
&#8722;
<device>
&#8722;
<match key="storage.hotpluggable" bool="false">
&#8722;
<match key="storage.removable" bool="false">
<merge key="storage.automount_enabled_hint" type="bool">false</merge>
</match>
</match>
</device>
</deviceinfo>

_______________________________________________________

I searched for wacom.ko.$ using nautilus, I also searched manually, but did not find anything.

There are, although, two files named wacom.ko.

---

### Post by Favux on 2009-08-12
Hi jqke,

Hmmm.  There shouldn't be.  Did you trace the paths to the two wacom.ko's?  Besides who backs up a file to the root directory?  Unless one is in the right place, ie /lib/modules/etc. and the other is in the unpacked 0.8.1-4 source code?  Which by the way you can delete now.

Rather than try to figure out which is the right one by looking at properties and date etc., let's just put a new one in.  Use 'uname -r' in a terminal to find your kernel version.  Then in Synaptic Package Manager search "kernel".  You want to reinstall the "linux-image" for your kernel version.  It has the kernel modules including wacom.ko.  This is described in Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Then reboot.

---

### Post by jqke on 2009-08-13
Okay. I did the reinstall, and rebooted. No good.

I searched before reinstall and after, and both times I traced the two wacom.ko files to /lib/modules/2.6.28-11-generic/kernel/drivers/input/tablet

---

### Post by Favux on 2009-08-13
Hi jqke,

Hmmmm.  There shouldn't be two there.  Both are named "wacom.ko".  No difference in the names at all?  Is there any indication one is active and the other not?

---

### Post by jqke on 2009-08-13
Hold on! Found something.

The addresses are not the same

One is:

/lib/modules/2.6.28-11-generic/kernel/drivers/input/tablet

And the other is:

/lib/modules/2.6.28-14-generic/kernel/drivers/input/tablet

In 'modules' there are two directories, as you can see.

Their contents are identical.

I don not know what this means.

---

### Post by Favux on 2009-08-13
Hi jqke,

It's suppose to be that way, each kernel with it's own stuff including wacom.ko.  So that isn't it.

I'm not sure what's wrong.  If I understand everything you've done at this point you should have pressure.  So I guess a little review and thinking is in order.

---

### Post by Favux on 2009-08-13
Hi jqke,

Ok, what if the "linux-image" didn't overwrite the 0.8.1-4 wacom.ko?  I assume you are booting with your latest kernel so the wacom.ko we're talking about would be the "/lib/modules/2.6.28-14-generic/kernel/drivers/input/tablet" one.  You could check it with properties and see if something tells you which one it is, date or some such.

If it is the 0.8.1-4 wacom.ko or you are not sure you could remove it with:
```
sudo rm /lib/modules/2.6.28-14-generic/kernel/drivers/input/tablet/wacom.ko
```
and reboot.

Then install the 2.6.28-14-generic "linux-image" through Synaptic again.  And reboot.

---

### Post by jqke on 2009-08-13
Did it, configured gimp, still didn't work. Buttons work, but no pressure.

How exasperating.

---

### Post by Favux on 2009-08-13
Hi jqke,

Let's see what your .xinitrc says.  It's a hidden file in /home/yourusername/ so you have to check on View Hidden Files in Places to see it.  There should be a line like:
```
xsetwacom set stylus PressCurve "0 10 90 100"
```
in there.  That's the pressure line, obviously.

---

### Post by jqke on 2009-08-13
xsetwacom set stylus PressCurve "0 25 75 100"

---

### Post by Favux on 2009-08-13
Hi jqke,

OK, I'm stumped.  Both Gimp and Inskscape?

Far as I can tell it should work.  It does for everyone else.  Hopefully it's something obvious and we'll have an eureka moment any minute.

You're connecting the Bamboo directly to a usb port not a hub, correct?

---

### Post by jqke on 2009-08-13
Both programs, yes.

I'm wiring direct, no hub.

---

### Post by Favux on 2009-08-13
Hi jqke,

Could you go back and check to see if the 10-wacom.fdi is the new modified version?

Edit:  If:
```
xsetwacom list
```
returns stylus, eraser, cursor, and pad it should be installed correctly.

---

### Post by jqke on 2009-08-14
Yep, it's all there.

I'm going to go through our thread here and cover my tracks.

---

