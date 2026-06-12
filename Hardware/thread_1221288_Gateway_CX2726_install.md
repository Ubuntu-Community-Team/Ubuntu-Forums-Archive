---
title: "Gateway CX2726 install"
date: 2009-07-23
forum: Hardware
---

### Post by Zuke24 on 2009-07-23
I am brand new to Ubuntu (and Linux in general) and trying it out on different systems.  Currently, I'm trying to install it on a Gateway Convertable Tablet CX2726. 

I have used the search function, and I have found various threads that talk about different parts of the install but haven't had any luck with any of them.  I'd like to put them all the issues I've been having in one place, and if anyone can point me in the right direction or tell me if I'm just stuck, I'd really appreciate it!

System: [Gateway CX2726]("http://support.gateway.com/s/Mobile/Q106/ViperC/1013921Rsp2.shtml") 
OS: Ubuntu 9.04 Desktop i386

Video:
Works well and correctly sets the resolution.  Hard to tell if it's just me or a compatibility issue, but menus and video seem sluggish.  Tried looking for newer drivers only to find there aren't any.

Tablet:
Nothing but pain.  I've tried manually copying the fpit driver and editing my serial.conf and xorg.conf, and I MUST have done it wrong cause now the system just reboots to my background and mouse cursor!

Buttons:
The only guides I can find on them say there is no way to use them in Linux (speaking of the buttons along the bottom of the screen that tell it to rotate and whatnot).  Of course, those same guides haven't been updated in a couple years!

PCMCIA, SD Reader, firewire, and audio input all haven't been tested.  

Here's where I'm really starting to feel hopeless: I read through all these forum boards and I get the feeling that all guides are either "Well, this worked for me, but it may actually scrap your system" or "It worked for me, but that was 3 years ago and the newest distro includes new dependencies that will ensure this will NOT work now."

I really don't want to sound like the new whiny windows user, but  isn't there SOME place that has the newest answers, with new drivers?  I'm feeling very lost here!:(

---

### Post by Favux on 2009-07-23
Hi Zuke24,

Wasn't there a finepoint (fpit) driver in the Jaunty repository (Synaptic Package Manager)?

In Jaunty you should be using a .fdi file rather than the xorg.conf.  The Jaunty fpit driver would hopefully include the .fdi packaged in with it.

---

### Post by Zuke24 on 2009-07-24
Hmm, I'll check.  Any pointers on where I should look?  I edited my xorg.conf to match another thread on here, and nothing changed at all.  If Jaunty (and now Karmic) don't use the xorg, then that'd make sense!  When I find the FDI, what should I do with it?

And more in a general use kin of question; does Ubuntu have a sort of Device Manager similar to Windows where I can just tell it "Hey, use this diver for this hardware!"?

---

### Post by Zuke24 on 2009-07-24
And I'm sorry; I forgot to mention that I already installed the fpit drivers from the package manager.

So a bit of an update:
I'm reckless, so I went ahead and updated to Karmic Koala and updated everything I could find.  New status:

VPN works great, and the keychain remembers my password without issue!  Definite improvement!
Desktop graphics are MUCH faster and smoother.  I know it's just appearance, but it sure helps me FEEL like it's moving faster.  Menus are snappy and everything respond much better.
Firefox 3.5 is much better than the 3.0 I was playing with before.  I still miss my Chrome, and Chromium seems to have limited support in the works.  :-(

Thanks!

---

### Post by Zuke24 on 2009-07-24
OK, I'm getting the hang of "where to search for info".  I found the FDI folder, but there's next to nothing in there.  Are all FDI's stored in the same place?  And how would I know how to write my own FDI for the digitizer?

---

### Post by Favux on 2009-07-24
Hi Zuke24,

The 10-wacom.fdi is in "/usr/share/hal/fdi/policy/20thirdparty/" and a lot of other .fdi's are in "/usr/share/hal/fdi/".  You can also find .fdi's in "/etc/hal/fdi/".  A missing .fdi might explain the problem.  Or there may not be a .fdi configuring the serial setting, or if there is the setserial setting you set interferred.  And depending on things xorg.conf may or may not work.  How's that for definite?

System>Administration>Hardware Drivers.  But that's for proprietary stuff.  Everything else should be in Synaptic Package Manager.

---

### Post by Zuke24 on 2009-07-24
Well, reading more and more and more, it seems the fpit does not "work?" with the FDI system and needs the xorg, and so people who have the Fujitsu Digitizer have to work with the older xorg.conf instead of the new system.  

Now, I'm confused by that; is there a way to force the system to recognize the older system?

---

### Post by Favux on 2009-07-24
Hi Zuke24,

It almost for sure will work with HAL/.fdi but it sounds like no one has figure it out yet.

The xorg.conf runs last and should work, you'll just lose usb hotplugging.  Maybe if you post the xorg.conf you tried to use.

Edit:  And the original unmodified Jaunty or Kharmic xorg.conf.

---

### Post by Zuke24 on 2009-07-24
My xorg.conf
===================================

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "RightEdge" "5820"
EndSection

Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents" "true"
Option "TrackRandR" "on"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
InputDevice "Tablet"
EndSection
=====================================

---

### Post by Favux on 2009-07-24
Hi Zuke24,

OK, are the video sections the same as the original xorg.conf?

In Jaunty and Kharmic the .fdi files configure the keyboard, mouse, and touchpad.  So we can remove them.
```
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents" "true"
Option "TrackRandR" "on"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Tablet"
EndSection
```
Make sure you back up the xorg.conf and be prepared to restore it if needed.

---

### Post by Zuke24 on 2009-07-24
Yes they were.  OK, I've made those edits and restarted.  No change! :(

Someone else suggested to me that I go back to the last time this configuration worked, which I think was 8.04.  Thing is, I noticed Kharmic provided a noticeable boost to system reponse, boot time, and graphics and I'd rather not have to lose all that!

---

### Post by Favux on 2009-07-24
Hi Zuke24,

I don't blame you.  Didn't expect change, just wanted to remove extraneous entries.

A couple of things.  We need to figure out if setserial and serial.conf work with Jaunty.  If it does you should be OK.  Or is it already preconfigured for you?  So in a terminal enter:
```
dmesg | grep ttyS
```
and post any output.

Another is your xorg.conf finepoint section doesn't have:
```
	# "BaudRate" may need tweaking (9600, 19200, or 38400).
	Option		"BaudRate"		"19200"
```
You can look at how jonthemiller and I set up a M285-E on the thread:  [http://ubuntuforums.org/showthread.php?t=1064838](http://ubuntuforums.org/showthread.php?t=1064838)  Should be some useful info. for you in there.

---

### Post by Zuke24 on 2009-07-24
zuke@Merlin:~$ dmesg | grep ttyS
[   14.832994] ttyS0: LSR safety check engaged!
[   14.833608] ttyS0: LSR safety check engaged!
[   18.651974] ttyS0: LSR safety check engaged!
[   22.071372] ttyS0: LSR safety check engaged!
[   22.071990] ttyS0: LSR safety check engaged!
[   22.999768] ttyS0: LSR safety check engaged!
zuke@Merlin:~$ ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3  /dev/ttySL0
zuke@Merlin:~$

---

### Post by Favux on 2009-07-24
Hi Zuke24,

"ttyS0: LSR safety check engaged!" is a new one on me.  What we need is the output that would tell us what line to use in serial.conf.  It does look like the tablet is using ttyS0 though, so that's something.  Try adding "sudo" in front of the dmesg command.

So let's try to summarize.

-Kharmic alpha 3
-fpit driver from Kharmic repository.  (what's the version number?)
-fpit package apparently didn't install a fpit.fdi
-Did you install setserial?
-You said you put something in serial.conf.  What was the line you used?

---

### Post by TrevT93 on 2009-07-25
Hi.  I'm also new to Ubuntu (running 9.04), and my tablet PC is nearly the same as Zuke24's (a Gateway CX2750), and like his, I can't get the tablet to do anything.  I've been working on this issue forever, and nothing up to this point has helped much.

My biggest problem seems to be that when my xorg.conf file has a ServerLayout section, after the file has been replaced and I restart my computer, I get an error message (Problem parsing the xorg.conf file, Error parsing the xorg.conf file).

Should I just not use a serverlayout section?

---

### Post by Favux on 2009-07-25
Hi TrevT93,

Welcome to Ubuntu Forums!

Great!  Glad you joined us.  The more participating, the more likely we are to figure this out.

Yes, start without the "ServerLayout".  The fact that it's breaking X may mean something with your tablet is almost active.  When Jaunty first came out putting Wacom entries in "ServerLayout" (actually adding "ServerLayout" since it wasn't present, just the 3 video sections) would break X for some folks.  I couldn't see a pattern.  I thought it was a consequence of moving to HAL/.fdi, but it turned out to be a bug.  There was a patched xorg-xserver in a ppa Timo had that seemed to fix it.  And as near as I can tell Jaunty has been updated with it.  So have you done all the updates?

Could you post your xorg.conf and tell us what you've done?  Also post the "ServerLayout" that breaks X?

It's possible if we get the xorg.conf figured out we may be able to translate it into a fpit.fdi.

---

### Post by Zuke24 on 2009-07-25
OK, tried it with the sudo and there was no change.  I was able to get ahold of someone with nearly the exact same tablet as I use, and tried to use his exact xorg.conf and serial.conf.  Here they are.
```

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Tablet"
    Driver        "fpit"
    Option        "Device"        "/dev/ttyS0"
    Option        "InvertY"
    Option        "MaximumXPosition"    "12550"
    Option        "MaximumYPosition"    "7650"
    Option        "MinimumXPosition"    "400"
    Option        "MinimumYPosition"    "400"
    Option        "SendCoreEvents"    "True"
    Option        "TrackRandR"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Tablet"
EndSection

```

```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```

It didn't work.  :(  Also, I found a fpit.fdi on Google and tried that as well!
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input">
   <match key="info.product" containts="PnP Device (FPI2004)">
    <merge key="input.x11_driver" type="string">fpit</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.InvertY" type="string">true</merge>
    <merge key="input.x11_options.MaximumXPositon" type="integer">12550</merge>
    <merge key="input.x11_options.MaximumYPositon" type="integer">7650</merge>
    <merge key="input.x11_options.MinimumXPositon" type="integer">400</merge>
    <merge key="input.x11_options.MinimumYPositon" type="integer">400</merge>
    <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    <merge key="input.x11_options.TrackRandR" type="string">true</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

It didn't work either.

---

### Post by Favux on 2009-07-25
Hi Zuke24,

OK, why make it easy?

Let's start with the "xserver-xorg-input-fpit  1:1.3.0-1  X.Org X server -- FPIT input driver" in Synaptic Package Manager.  Go to it in Synaptic and tell Synaptic to reinstall it.  Hopefully you uninstalled your previous manual attempt to install it and it is not interfering with the Synaptic install of fpit.

I found a fairly intricate "official" 10-fpit.fdi.  It looks like it was added to the package, so let's see if we can find it.  While in Synaptic with the fpit driver highlighted go to Package>Properties>Installed Files and see if you can find the .fdi and if so where it is installed.

Also in Synaptic make sure "setserial  2.17-45" is installed, and maybe also reinstall it.  I can't find anything about changes to setserial use in Jaunty (although in Synaptic it says "This version has a completely new approach to configuration...") so I'm going to assume it's the same.  And the same for serial.conf.

Now in "/etc/serial.conf" change:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
to (we'll assume it is the right line):
```
/dev/ttyS0 port 0x03F8 irq 4 autoconfig
```
Then in a terminal enter:
```
sudo /etc/init.d/setserial reload
```
You may have to restart several times and restart X several times to get it to "kick" in.

And you would either have the "official" .fdi in place (not the one you found) or the finepoint entries in xorg.conf.

Good luck!

---

### Post by Zuke24 on 2009-07-26
I'm sorry, but a silly question here.

How do I restart X?  Doesn't that automatically restart when I restart the computer?

---

### Post by Favux on 2009-07-26
Hi Zuke24,

Sorry, I forgot in Jaunty upstream disabled restarting X.  It used to be ctrl-alt-backspace.  The thought was people were accidentally hitting this combination.  To re-enable it add to the xorg.conf:
```
Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection
```
or these are suppose to work:

USE ALTGR + SYSRQ + K
or ALTGR + PRINTSCREEN + K instead.

Did you find the .fdi?  Looking at it I wonder if the problem is your finepoint digitizer isn't identifying itself as a "FUJ" like "FUJ02B2".  Instead it may be something like the "FPI2004" in the .fdi you found.  We could look at "xinput --list" and "lshal" to find out.  If so we could just add it to the match lines of the "official" .fdi.

---

### Post by Zuke24 on 2009-07-26
OK, since I'm using Karmic, my version of fpit is actually one version newer.  It does not include a FDI file in it's installation.  I googled 10-fpit.fdi and found [this]("http://mirrors.evolva.ro/zenwalk/source/x/xorg-driver-fpit/").  I moved it to /etc/hal/fdi/policies/10-fpit.fdi.

I also changed my setserial as you suggested and restarted the service.

All to no avail! :(

---

### Post by Favux on 2009-07-26
Yes, that's the .fdi I'm talking about.  So maybe your finepoint isn't identifying with the "FUJ", which should be for a Fujitsu laptop.  So enter in a terminal "lshal>lshal.txt".  You can then open it with gedit and search it for finepoint or tablet etc.  Find the section(s) for your tablet and let's look at them.

Also see what "xinput --list" is calling the digitizer.

---

### Post by TrevT93 on 2009-07-26
> **Favux said:**
> Hi TrevT93,

Welcome to Ubuntu Forums!

Great!  Glad you joined us.  The more participating, the more likely we are to figure this out.

Yes, start without the "ServerLayout".  The fact that it's breaking X may mean something with your tablet is almost active.  When Jaunty first came out putting Wacom entries in "ServerLayout" (actually adding "ServerLayout" since it wasn't present, just the 3 video sections) would break X for some folks.  I couldn't see a pattern.  I thought it was a consequence of moving to HAL/.fdi, but it turned out to be a bug.  There was a patched xorg-xserver in a ppa Timo had that seemed to fix it.  And as near as I can tell Jaunty has been updated with it.  So have you done all the updates?

Could you post your xorg.conf and tell us what you've done?  Also post the "ServerLayout" that breaks X?

It's possible if we get the xorg.conf figured out we may be able to translate it into a fpit.fdi.

Thanks for both the warm welcome and helpful first response!  I can tell you this much: my xorg.conf never had a ServerLayout section, and when it is added, no matter what I put in there, I end up having to use recovery mode to get GUI usage back.  Possibly I should only put the tablet in that section?  I'll get back to you on that, when I've tried it.

Yes, my copy of Jaunty has been fully updated, as of yesterday, and I found the fpit driver in the Synaptic Package Manager and (re)installed it.

As for the xorg.conf...(I removed the comments for this forum post because it would be too long)

```

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
```

I don't have the tablet section in because it ends up getting deleted every time I have to use the recovery to restore xorg.conf.  I had it in there for a while, to no avail.  What exactly should I put in there, the same as what you told Zuke24?

Thanks again.

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Let's first try adding a "ServerLayout" and see if it breaks X.  Add the following after the Screen Section:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
#	Identifier	"X.org Configured"	# New for Jaunty?
EndSection
```

Also check and see if a 10-fpit.fdi was installed.  You can try using Synaptic like I suggested in post #18 above.

---

### Post by TrevT93 on 2009-07-26
Okay, good news-bad news.  The good news is that this time, the ServerLayout did not cause an error upon reboot.  The bad news is that, after a reinstallation of the specified driver, I did not find any .fdi files in the driver's installed files.

Should I now add the tablet back into the xorg.conf and see how it works?

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Right, try that.  It should go above the Device Section.  Just leave out it's "ServerLayout" entry for now.

But first let's see what output you get with:
```
dmesg | grep ttyS
```
And try adding sudo if needed.  Also:
```
ls /dev/ttyS*
```

---

### Post by TrevT93 on 2009-07-26
Okay, I added the tablet back into xorg.conf.

The first one you gave me didn't return anything, even using sudo.  The second one returned this:

```
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3  /dev/ttySL0
```

Except that the first four were highlighted in black, letters colored in yellow, and the last one was colored a light blue.  Do the colors mean anything, anyway?  (I don't know, still new to this.)

---

### Post by Favux on 2009-07-26
Hi TrevT93,

So nothing broke, but the tablet isn't working?

The colors probably mean something, but I don't know what.  It's looking more possible that serial configuration has changed somehow in Jaunty.  But I know others have gotten serial tablets set up.  So press on.

Could you post your current xorg.conf and seperately the "ServerLayout" you were trying that didn't work?  Or at least the finepoint line you had in it.

---

### Post by TrevT93 on 2009-07-26
No, nothing broke.  My tablet runs Ubuntu 9, Windows Vista, and Windows 7 RC1 in partitions, and the tablet works with both copies of Windows.  So at the very least, I know the tablet works.

This is the backup of the last xorg.conf that I tried which ended up failing:

```
Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents" "true"
Option "TrackRandR" "on"
Option "BaudRate" "19200"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection
```And the ServerLayout:

```

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Tablet"
EndSection
```

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Good.  Ok I want you to comment out (#) these lines:
```
# Option "SendCoreEvents" "true"
# Option "TrackRandR" "on"
# Option "BaudRate" "19200"

```
And then add the "InputDevice "Tablet" " line to "ServerLayout" and restart.  Be ready for breakage!

For comparison I want to show the Finepoint sections for a Gateway M 285-E:
```
Section "InputDevice"
	Identifier	"Finepoint Tablet"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS0"
	# "BaudRate" may need tweaking (9600, 19200, or 38400).
	Option		"BaudRate"		"19200"
	# For a passive pen, e.g. Stylistic 3400 use "true".
	Option		"Passive"		"false"
	# To make the touchscreen respond automatically to
	# resolution changes and screen rotation:
	Option		"TrackRandR"
	# Not sure if "SendCoreEvents" line is necessary.
	Option		"SendCoreEvents"	"true"
	Option		"Buttons"		"2"
	# not sure which button line works or both together?
#	Option		"Button2"		"3"
	# These may need tweaking.
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"InvertY"
EndSection
```
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Finepoint Tablet"
EndSection
```
Does your stylus have a battery?

---

### Post by TrevT93 on 2009-07-26
Let me just say this.  I've had to get my pen replaced at least four times for overuse (once for breakage).  Those batteries don't last too long, but at least I know someone who will replace the battery very cheaply.  Yes, they do in fact have batteries.  I thought all of FinePoint's did.

The rest of this post is reserved for edits.  I can't do the rest of the instructions now, but I'll get to it in a few hours, and put the results in this post.

EDIT: more good news, more bad news.  The good news is...my computer didn't break!  Small accomplishment, but it's still something I was not able to do before, if that means anything.  The bad news is, of course, that the tablet still doesn't work.

---

### Post by Zuke24 on 2009-07-26
Hello hello hello!

```
zuke@Merlin:~$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
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
"TOUCHSCREEN"    id=2    [XExtensionPointer]
    Type is Fujitsu Stylistic
    Num_buttons is 3
    Num_axes is 2
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 400
        Max_value is 12550
        Resolution is 9500
    Axis 1 :
        Min_value is 400
        Max_value is 7650
        Resolution is 10500
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=8    [XExtensionPointer]
    Type is MOUSE
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
    Type is TOUCHPAD
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
zuke@Merlin:~$ 

```So have we just been calling it the wrong thing the whole time?  My lshal didn't list Fujitsu anywhere, or finepoint.  It only listed the tablet in one area as "TabletPC" which was under machine type.

PS, I thought the stylus was passive.  I see no place to replace a battery on mine.  I've confirmed it works under XP, Vista, and 7.

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Good.  So let's see if one of the three lines is causing the breakage.  Remove the comment (#) from the 3 lines we commented out one line at a time.  Start with the baud line then reboot.  Then the SendCore line, reboot.  And finally the RandR line.


Hi Zuke24,

If you have a passive stylus (no battery) you need this line:
```
	Option		"Passive"		"true"

```
in your xorg.conf.

So xinput is seeing it and calling it:
```
"TOUCHSCREEN"    id=2    [XExtensionPointer]
    Type is Fujitsu Stylistic

```
We need to look at the section(s) in lshal you're talking about, or one that has something like what's in xinput.  And yes the .fdi may not have the right name or identifier for the match line.

---

### Post by TrevT93 on 2009-07-26
> **Zuke24 said:**
> PS, I thought the stylus was passive.  I see no place to replace a battery on mine.  I've confirmed it works under XP, Vista, and 7.

Is your stylus the silver kind with a black top and bottom?  If so, it's a battery-requiring model.  So is the black one with grey top and bottom.  It's just that it needs to be sent to a professional to have the battery replaced...Gateway's idea of a good joke, since Finepoint no longer exists.

I've been experimenting for the last hour or so.  Removing the commenting mark from in front of the TrackRandR line doesn't cause the break.  Neither does SendCoreEvents.

Looking around the 'net, I've found there's another option, "AlwaysCore".  Should that be used in the xorg.conf?  It didn't break it, at least, when I added it in.

Going to try to disable the baud line then reboot.  I'll edit this with results in about a minute.

EDIT: that doesn't cause an issue either.  So then, what about the xorg.conf caused my computer to not boot properly before, and why does it suddenly work?

---

### Post by Favux on 2009-07-26
Hi TrevT93,

I do not know.  Leave all the lines uncommented now since they don't break X.

Now I think you have to install setserial in Synaptic and the serial line in serial.conf like I described in post #18.  It doesn't seem that anything in Jaunty (a .fdi somewhere) is configuring the serial stuff for you.  That seemed to be a possibility with X breaking like it was.  Good luck!

---

### Post by TrevT93 on 2009-07-26
I wish it was that easy.  I've had setserial for a long time (since another of my attempts at fixing the seemingly unfixable), and I tried editing serial.conf to what you said in post 18.  No dice...

---

### Post by Favux on 2009-07-26
Bummer.

If you have the right line for your tablet... We're back to wondering if something has changed in Jaunty that we're unaware of.  A syntax change?  A name change, where serial.conf is supposed to be called something else?  Or located somewhere else?  I didn't see anything when I searched last time.  I guess it's back to research.  Unless you have an idea?

You could check the setserial package and see if there is a read me, or try "man setserial" in a terminal.

---

### Post by TrevT93 on 2009-07-26
Well, are we absolutely certain that the tablet is ttyS0, not one of the others?  I did come up with 5 for that one command you gave me back on post 27.  What was the ttySL0 one anyway, and why did it come up in a different color than the rest of them?  That might be nice to know, because it could mean something.

Of course, I could be (and probably am) totally wrong, because this is my first experience in Linux in general.  There's so much I don't know (but that I would like to know).

Other than that...well, I haven't found anything recent on this tablet issue on the 'net.  And Finepoint isn't around to help anymore.  And Gateway has gotten tired of hearing from me...not that I expect them to be of any help anyway.  I started here because I was completely unsure of anything.  One of my friends got me started on Ubuntu.  He had a tablet too...a Wacom one.  I wish I did too, because his worked without setup.

I guess I'll keep watching this thread for any updates, and just work with my trackpad for now.  Speaking of which, my trackpad's scroll area is about double the width it's supposed to be.  Know a quick fix to that, or where on this forum I'd find one?  (It's a Synaptics.)

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Believe me, I have a Wacom, and you do have to configure it.  Having the stylus "work" out of the box is not the same as having the whole thing working.  But they came the closest yet in Jaunty.

To find the active port you can use xxd. The program xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen an move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```
changing to S1, etc.

Sorry, I've seen some threads dealing with similar issues re Synaptic though so the answer is probably in the forum.

The frustrating thing is the answer to Finepoint on Jaunty is probably out there, we just don't know what term to search with.

---

### Post by TrevT93 on 2009-07-26
If you would believe it (and you probably would), nothing out of any of them.  Each one, ttyS0 through ttyS3, went right to the next terminal line.  ttySL0, however, didn't quit the moment I pressed enter (I had to press ctrl+C to quit it), although it didn't do anything when I pressed my pen to the screen, or moved it around near the screen.  As to whether or not that means anything, I don't have a clue.

---

### Post by Favux on 2009-07-26
Hi TrevT93,

I think it means serial stuff has changed.  But how?

My guess has been that all this is suppose to be precongfigured through .fdi's or whatever.  And the preconfiguring is what's interferring with dmesg grep ttyS and setserial (which may be deprecated?) and now xxd.  Or maybe I'm being too optimistic and they didn't do any of that.

I think I've seen serial wacom tablet pc's just set up without needing setserial and the serial.conf line.  It's probably blindingly simple.

---

### Post by TrevT93 on 2009-07-26
I don't understand, though.  What are FDI's, and how did the old system work without them?  And does this mean I might have to change to an older version of Ubuntu in order to get my tablet working?

---

### Post by Favux on 2009-07-26
Hi TrevT93,

Heck, you may have to.

The HAL/.fdi thing enables USB hotplugging among other things.  xorg.conf is being deprecated in HAL's favor.

A .fdi configures hardware.  .fdi = device information file

So there are now things like 10-fpit.fdi and 10-synaptic.fdi etc. configuring the hardware.  They started introducing it in Intrepid.

---

### Post by TrevT93 on 2009-07-26
I'd hate to think that I'd actually have to downgrade to get something to work.  The tablet's not essential, because I can still use it in Vista/7.  But it would be nice.  Ubuntu 9.04 has worked like a charm to this point.

I'll keep watching until I find a solution.  And you're sure that there's no FDI which enables the tablet to function?

---

### Post by Favux on 2009-07-26
Hi TrevT93,

No I'm not sure.  That's what Zuke24 and me are working on.  We both found the same .fdi, 10-fpit.fdi which he links in post #21.

---

### Post by Zuke24 on 2009-07-26
OK, so I tried to upload the lshal but evidently it's too big for the forums.

I uploaded it to my site, and you can read it [here.]("http://www.stolendroids.com/wp-content/uploads/2009/07/lshal.txt")

Trev, I'm in the same boat as you here;  new to Linux and Ubuntu, and I don't want to have to downgrade to a older distro just to get this to work.  When I get into work tomorrow, I might just break out the other TabletPC we have on the shelves; it's an IBM an has a Wacom.

---

### Post by Favux on 2009-07-26
Hi Zuke24,

As usual with lshal my eyes glaze over.  Anyway at first pass these are the relevant sections:
```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
  info.callouts.add = {'hal-system-setserial'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FPI2004)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
  input.device.set = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.id = 'FPI2004'  (string)
  pnp.serial.baud_base = 38400  (0x9600)  (int)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x6a8'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  serial.port = 0  (0x0)  (int)
```
Notice it does seem to be auto configuring the serial port.  This may be my hypothetical interference.  Notice also the serial line is different from what you thought.  HAL is saying:
```
/dev/ttyS0 port 0x6a8 irq 4 baud_base 38400
```
And that: 
```
pnp.id = 'FPI2004'
```
So to the second match line in the 10-fpit.fdi you'd need to add:
```
<match key="@info.parent:pnp.id" contains_outof="FUJ02B2;FUJ02B3;FUJ02B4;FUJ02B6;FUJ02B7;FUJ02B8;FUJ02B9;FUJ02BC;FPI2004">
```
And if you're sure it's a passive (no battery) pen to you'd add the same to the passive pen subsection match line.

---

### Post by Zuke24 on 2009-07-27
No, it seems mine is active after all!  So, should I edit my serial.conf to match that line?

/dev/ttyS0 port 0x6a8 irq 4 baud_base 38400

??

---

### Post by Favux on 2009-07-27
Hi Zuke24,

I'm not sure.  I think for the HAL/.fdi method we should not do anything with setserial and serial.conf yet.  Maybe that's only with xorg.conf?

Try adding 'FPI2004' (without the quotes) to the match line of the active section of the .fdi.  Like with the match line above, ie add it to both.  The .fdi should then pick up your tablet.

If that doesn't work then we can look at serial.conf etc.  Are you sure your stylus battery is good?

I found someone setting up an fpit type driver in Jaunty through the xorg.conf.  I'm not sure how relevant it is.  So we probably should take a look:  [http://rvshiro.wordpress.com/2009/07/04/fujitsu-p1510-touchscreen-under-jaunty-jackalope/](http://rvshiro.wordpress.com/2009/07/04/fujitsu-p1510-touchscreen-under-jaunty-jackalope/)

---

### Post by Favux on 2009-07-27
Hi Zuke24,

Since the coordinates are different along with the BaudRate it's probably better to add a "Gateway" subsection to the .fdi.  We can experiment in there.

I really don't understand why HAL is saying your BaudRate is 38400 when it is 19200 in the xorg.conf's and the Fujitsu Active Pen subsection.  The coordinates may need tweaking and we can also try adding some of the lines from the xorg's to the Gateway subsection if needed.

---

### Post by TrevT93 on 2009-07-27
@Post 49: Funny, I've seen that site before.  I know I have.  But I chose to ignore it because I didn't think it would help us.  I'll give it a shot and see what happens, though.  Expect more in this post.

EDIT 2: I just looked better at that model discussed in the article, and it's just a touchscreen...not an actual tablet (according to Fujitsu).

---

### Post by ace214 on 2009-07-27
Hi Favux,

I've been trying to help Zuke set up the finepoint, as I have done it on my Gateway CX2619 before.

We used the following xorg.conf and serial.conf to no avail, which is weird because they seem to work for me. When I simply edit my xorg.conf with that info, the pen will make the cursor flicker randomly around the screen until I configure the serial ports. However, we couldn't get the pen to do this for Zuke, which is weird... It seemed to be set-up in his Xorg log, but configuring the serial port seemed to do nothing. I wonder if it is a serial problem with this particular laptop, although [I have seen other laptops of this model work before]("http://www.linuxquestions.org/questions/showthread.php?p=2585896#post2585896").

I'm not sure what else to do, as this works for me and [seems to work for models similar to Zuke's]("http://ubuntuforums.org/showthread.php?t=942109"). I'd like to help out though.

Xorg.conf: 
```
Section "InputDevice"
        Identifier      "Tablet"
        Driver          "fpit"
        Option          "Device"                "/dev/ttyS0"
        Option          "InvertY"
        Option          "MaximumXPosition"      "12550"
        Option          "MaximumYPosition"      "7650"
        Option          "MinimumXPosition"      "400"
        Option          "MinimumYPosition"      "400"
        Option          "SendCoreEvents"        "True"
        Option          "TrackRandR"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        InputDevice     "Tablet"
EndSection

```

/etc/serial.conf
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400

```

---

### Post by Favux on 2009-07-27
Hi ace214,

I agree.  That should work for Zuke24 and TrevT93.  I don't know why it doesn't.

Could the battery be low or dead in Zuke24's stylus?  But that doesn't explain why TrevT93 can't get set up.  I don't think either are getting stylus activity with just xorg.conf set up.

It's very useful that you've confirmed finepoint and serial.conf works in Jaunty.  Did you have to do anything special with setserial?

Thanks for the help!


Hi TrevT93,

The site is mainly concerned with installing "xf86-input-fujitouch-0.6.5".  But it confirmed serial.conf works in Jaunty, which ace214 also confirms.  And the line:
```
InputDevice     &#8221;touchscreen&#8221; &#8220;CorePointer&#8221;
```
which may be something you already tried.

---

### Post by ace214 on 2009-07-27
Serial.conf has worked for me since Gutsy and does in Karmic as well. I just install it, put that in serial.conf and restart.

Also, I made that first fdi file that Zuke found. I don't remember where I came up with the model number, but I noticed a typo in that line. Perhaps it might be worth it to fix the typo and try it.

Maybe Zuke, clear out the xorg.conf and serial.conf and try the fdi file with the typo fixed? Although, when I tried that, I seem to remember that it wasn't going to work because of the way finepoint pens work. Don't remember why though...

---

### Post by Favux on 2009-07-27
Hi everyone,

Found something.  In "/usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi" the second section refers to 'FPI2004' and sets the baud_base to 38400.

So ace214 what is your identifier in lshal or "xinput --list"?  Is it also 'FPI2004'?  TrevT93 you might want to check it too.

Since it's already configured I wonder if we can leave it out of the .fdi?

---

### Post by ace214 on 2009-07-27
I have that in my lshal but it doesn't have anything like that in my xinput --list.
Then, I wonder if the X functions need to be in a separate file that will inherit the options of that one.

---

### Post by Favux on 2009-07-27
Right.  Will it stay with the .fdi or what?  I guess the only way to figure it out is to experiment.  And then things seem different with xorg.conf.  Don't know why, it should be a chain with .fdi's applying first then xorg.conf.  The last setting should apply.  And I don't know where serial.conf fits into the chain.

---

### Post by ace214 on 2009-07-27
Yeah, I think you can just create a new fdi file with just the xorg settings, mostly, it just doesn't seem to be tied to the pointer in anyway with that file that you found.

Unfortunately, my testing abilities may be nill for a while- I just pulled that laptop out of my bag and the pivot hinge snapped internally... Now my screen is floppy...

---

### Post by Favux on 2009-07-27
Total bummer!  You did not need that.

Yes, that's the plan.  See if it the first match line works and then experiment in the Gateway subsection.  And if you want you can pull it out and just have a Gateway fpit.fdi.  If it's not active we can get match lines that pull it out from Zuke24's lshal sections.  Plenty there to work with.

---

### Post by TrevT93 on 2009-07-27
> **Favux said:**
> Hi everyone,

Found something.  In "/usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi" the second section refers to 'FPI2004' and sets the baud_base to 38400.

So ace214 what is your identifier in lshal or "xinput --list"?  Is it also 'FPI2004'?  TrevT93 you might want to check it too.

Since it's already configured I wonder if we can leave it out of the .fdi?

I don't understand (still learning this stuff).  Did you want me to look in that file and see what the second section said?  If so, then it does say FPI2004.  And it sets the serial port at ttyS0 and the baud_base at 38400 in that same section.

---

### Post by Favux on 2009-07-27
Hi TrevT93,

Thank you for checking that out.  So it looks like these models:
```
Gateway CX2619
Gateway CX2726
Gateway CX2750
```
use the same digitizer identifying as FPI2004 to HAL.

So ace214 should be right and all three should use the following line in serial.conf:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
And the following line should also work:
```
/dev/ttyS0 port 0x03F8 irq 4 autoconfig
```
And also the same .fdi should work for all three.

Edit:  Sorry TrevT93 misread your post.  The question is is your digitizer identifying itself as FPI2004 also?  Try in a terminal "xinput --list" or "lshal".  "lshal>lshal.txt" should make a text version appear on your desktop, or your /home/username directory anyway.
If so the upshot is that you should be able get things going using the xorg.conf.  You need to repeat the steps carefully.  I'd start by going to Synaptics and reinstalling finepoint and setserial.  Maybe even consider doing a complete uninstall of both, rebooting and then reinstalling them.  Then make sure your xorg.conf has the finepoint entries.  Reboot.  You should detect activity from your stylus.  Then check "/etc/serial.conf".  If the line above isn't there add it.  If the line is different replace it.  Then reboot, maybe several times.

---

### Post by ace214 on 2009-07-28
> **Favux said:**
> Total bummer!  You did not need that.

Tell me about it. I've found some hinge sets online, so I'm gonna open it up over the next few days. I am always hesitant to do more than replace ram/hdd, etc. on laptops though...

---

### Post by Favux on 2009-07-28
Hi ace214,

Tell me about it.  All I can do is give gratuitous advice.  Be very very patient.  Slow and methodical.  And if you don't have the right tool, eg small screwdriver, don't try to make do.  Go get one.

---

### Post by ace214 on 2009-07-28
> **Favux said:**
> Hi ace214,

Tell me about it.  All I can do is give gratuitous advice.  Be very very patient.  Slow and methodical.  And if you don't have the right tool, eg small screwdriver, don't try to make do.  Go get one.

Yeah, I have some "precision" screw drivers that I got to replace a watch battery once, so I will use those. I think I just need to be very careful about being sure the right screws go back in the right places.

---

### Post by Zuke24 on 2009-07-28
I work on laptops all the time, and Favux is right; use the right tools.  Also, don't let one stubborn screw ruin everything.  If you try and force it, you risk stripping out the screw head, and then you're only left with trying to bore out the screw with a drill bit and a can of compressed air!

Look for service manuals, as laptops are much more complex than desktops.  If you're lucky, Gateway builds them like Dell and they're easy to work inside.  If you're not, then it's like a Lenovo or Dell XPS.  :(

Oh, and an update for anyone following:  I've given up on the CX2726!  We had another tablet here at work that no one wanted, so I took it and it turns out it's MUCH more powerful, has a wacom tablet, and is overall much easier to configure.  Thanks to Favux for helping me setup the touch calibration!

---

### Post by TrevT93 on 2009-07-28
Okay, but I'm still in search of a solution if it's available.

Oh, and good luck on the hinges; that was a nasty problem for me when mine broke.

---

### Post by TrevT93 on 2009-07-28
Sorry I doubleposted, but I think this is important enough.

> **Favux said:**
> Edit:  Sorry TrevT93 misread your post.  The question is is your digitizer identifying itself as FPI2004 also?  Try in a terminal "xinput --list" or "lshal".  "lshal>lshal.txt" should make a text version appear on your desktop, or your /home/username directory anyway.
If so the upshot is that you should be able get things going using the xorg.conf.  You need to repeat the steps carefully.  I'd start by going to Synaptics and reinstalling finepoint and setserial.  Maybe even consider doing a complete uninstall of both, rebooting and then reinstalling them.  Then make sure your xorg.conf has the finepoint entries.  Reboot.  You should detect activity from your stylus.  Then check "/etc/serial.conf".  If the line above isn't there add it.  If the line is different replace it.  Then reboot, maybe several times.

Thank you for notifying me of this important edit in a PM, because I had not noticed this before.  Here's what I have for you: after using xinput --list, I came up with a lot of entries, including my USB wireless mouse, my Synaptics touchpad, and my keyboard.  However, there is no FPI2004.  Instead, there is this section (which I believe is the tablet):

```
"TOUCHSCREEN"    id=2    [XExtensionPointer]
    Num_buttons is 3
    Num_axes is 2
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 400
        Max_value is 12550
        Resolution is 9500
    Axis 1 :
        Min_value is 400
        Max_value is 7650
        Resolution is 10500
```

---

### Post by ace214 on 2009-07-28
I opened the swivel cover and discovered that the heads of the screws that hold the hinges to the swivel base actually popped off of the screws. So, I think I can actually screw them back into the base without even opening the case. Just gotta find some super small screws. I'm going to have trouble resisting going to Home Depot in the morning and going to work instead... :-)

I'll try to write an fdi soon.

---

### Post by Favux on 2009-07-28
Hi TrevT93,

OK, then you need to look at lshal or lshal>lshal.txt.  With the txt you can open in gedit (text editor) and use find FPI2004 or tablet, etc.  See if you can come up with the relevant sections like in the post a couple pages back.

Hi ace214,

That's a hopeful finding.  It would be good to get you back, esp. working on the .fdi.

---

### Post by ace214 on 2009-07-29
> **Favux said:**
> That's a hopeful finding.  It would be good to get you back, esp. working on the .fdi.

2.5mm screws did the trick! Be back soon...

---

### Post by ace214 on 2009-07-29
Made an fdi but it doesn't work. Here it is anyway:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="pnp.id" contains="FPI2004">
        <append key="input.x11_driver" type="string">fpit</append>
        <append key="input.x11_options.Type" type="string">stylus</append>
        <append key="input.x11_options.InvertY" type="string">true</append>
        <append key="input.x11_options.MaximumXPositon" type="integer">12550</append>
        <append key="input.x11_options.MaximumYPositon" type="integer">7650</append>
        <append key="input.x11_options.MinimumXPositon" type="integer">400</append>
        <append key="input.x11_options.MinimumYPositon" type="integer">400</append>
        <append key="input.x11_options.SendCoreEvents" type="string">true</append>
        <append key="input.x11_options.TrackRandR" type="string">true</append>
    </match>
  </device>
</deviceinfo>
```

It looks like it would work in theory for me, but it doesn't... I've created [another thread]("http://ubuntuforums.org/showthread.php?t=1226332") to see if I can get some help on it.

---

### Post by TrevT93 on 2009-07-29
Okay, got it.  Seems to me like a treasure trove of information.  But that also could be because I don't know much about Ubuntu yet.

```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
 info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
 info.product = 'PnP Device (FPI2004)'  (string)
 info.subsystem = 'pnp'  (string)
 info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
 linux.hotplug_type = 2  (0x2)  (int)
 linux.subsystem = 'pnp'  (string)
linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
pnp.id = 'FPI2004'  (string)
pnp.serial.irq = 4  (0x4)  (int)
pnp.serial.port = '0x6a8'  (string)
```

For example, the serial port is 0x06a8...weren't we putting 0x03f8 into serial.conf before?

And also, why is the tablet identified differently in two places, as FPI2004 in one and TOUCHSCREEN in another?

---

### Post by ace214 on 2009-07-29
> **TrevT93 said:**
> Okay, got it.  Seems to me like a treasure trove of information.  But that also could be because I don't know much about Ubuntu yet.

```
udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'
 info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
 info.product = 'PnP Device (FPI2004)'  (string)
 info.subsystem = 'pnp'  (string)
 info.udi = '/org/freedesktop/Hal/devices/pnp_FPI2004'  (string)
 linux.hotplug_type = 2  (0x2)  (int)
 linux.subsystem = 'pnp'  (string)
linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
pnp.id = 'FPI2004'  (string)
pnp.serial.irq = 4  (0x4)  (int)
pnp.serial.port = '0x6a8'  (string)
```

For example, the serial port is 0x06a8...weren't we putting 0x03f8 into serial.conf before?

And also, why is the tablet identified differently in two places, as FPI2004 in one and TOUCHSCREEN in another?
FPI2004 is what HAL gets and TOUCHSCREEN is what the driver supplies to X.

Try using the xorg config I posted a [couple pages back]("http://ubuntuforums.org/showpost.php?p=7688013&postcount=52"), and change that number in your serial.conf. I still think you would've gotten some result, though, even if the serial wasn't set right.

---

### Post by TrevT93 on 2009-07-29
BREAKTHROUGH!!  (kinda-sorta)

I changed serial.conf to say this:

```

/dev/ttyS0 port 0x06A8 irq 4 autoconfig

```And post-restart, I brought the pen to the screen, and the cursor went wild.  All over the place.  When I tapped the screen, it would click (from wherever the cursor happened to be).

That is amazingly good.  Now at least we KNOW we're on the right track!

Oh, and ace, I've been using a section almost exactly like that in my xorg.conf file, but I added the Option "passive" line too.

---

### Post by ace214 on 2009-07-29
> **TrevT93 said:**
> BREAKTHROUGH!!  (kinda-sorta)

I changed serial.conf to say this:

```

/dev/ttyS0 port 0x06A8 irq 4 autoconfig

```

And post-restart, I brought the pen to the screen, and the cursor went wild.  All over the place.  When I tapped the screen, it would click (from wherever the cursor happened to be).

That is amazingly good.  Now at least we KNOW we're on the right track!

Excellent- take out the autoconfig and put in "baud_base 38400"

So it appears that having something in serial.conf prevented you from getting that reaction. That's why when I was helping Zuke, I had him do them one at a time, but it didn't seem to help... Weird...

---

### Post by TrevT93 on 2009-07-29
No response.  Not even the all-over-the-place reaction from before.

EDIT: in fact, setting the baud_base to 19200 doesn't provoke a response from the tablet either.

So now what's wrong?

---

### Post by Favux on 2009-07-29
Hi TrevT93,

That happened after you removed autoconfig and put the "baud_base 38400" in?  If so go back to autoconfig and show us your current fpit section and "ServerLayout" in xorg.conf.

---

### Post by TrevT93 on 2009-07-29
Alright, here it comes (note that I've done some work on my xorg.conf since the last time we worked with it, working on the Synaptics touchpad and the graphics adapter):

```

Section "InputDevice"
    Identifier    "Tablet"
    Driver        "fpit"
    Option        "Device"        "/dev/ttyS0"
    Option        "InvertY"
    Option        "MaximumXPosition"    "12550"
    Option        "MaximumYPosition"    "7650"
    Option        "MinimumXPosition"    "400"
    Option        "MinimumYPosition"    "400"
    Option        "SendCoreEvents"    "true"
    Option        "TrackRandR"
    Option        "Passive"        "false"
EndSection
```

```

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
#    Identifier    "X.org Configured"    # New for Jaunty
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Tablet"        "CorePointer"
EndSection
```

---

### Post by Favux on 2009-07-29
Hi TrevT93,

Did changing back to autoconfig get the activity back?  You would need to reboot.  Because you are right, that's precious.  It means you almost have things working.

If activity is back try changing "ServerLayout" to:
```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Tablet"
EndSection
```

---

### Post by TrevT93 on 2009-07-29
Did as told.  But, probably as expected, no changes.  (Yes, changing back to "autoconfig" brought back the erratic movement.)

---

### Post by Favux on 2009-07-29
Hi TrevT93,

So the response is back.  Is it the same kind of erratic as before?  If that makes sense.  That would indicate the "CorePointer" bit in "ServerLayout" wasn't doing anything.

Try adding to the fpit section:
```
	Option		"BaudRate"		"38400"

```

---

### Post by TrevT93 on 2009-07-29
Made sense enough to me.  Again, I did as you described.  Same erratic movements when the serial.conf was using autoconfig, same nothingness when it was using baud_base 38400.

---

### Post by Favux on 2009-07-29
Hi TrevT93,

So baud wasn't it.  Well you almost have it working.  We just need to rethink.  Review what we've tried.  Maybe you need to change the port?  But to what?  And you're sure your battery is good?

---

### Post by TrevT93 on 2009-07-29
> **Favux said:**
> Hi TrevT93,

So baud wasn't it.  Well you almost have it working.  We just need to rethink.  Review what we've tried.  Maybe you need to change the port?  But to what?  And you're sure your battery is good?

Absolutely.  This is a brand new pen.  Had to send out for it a few days ago (in fact, the day I first posted in this thread is the day I finally got a working pen again), and then tried it out a little bit on Windows.

---

### Post by ace214 on 2009-07-29
I think you may need to add a uart to your serial.conf.
Do "dmesg | grep ttyS0" When I do this, I get "ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A"

So, I would add uart 16550A to the serial conf line after the port. Try it first with the baud_base in as well.

[I've seen one person report having to add this with your machine]("http://www.linuxquestions.org/questions/showthread.php?p=2585896#post2585896").

---

### Post by Favux on 2009-07-30
Hi TrevT93,

Before you go ahead and try ace214's suggestions first try in a terminal:
```
sudo /etc/init.d/setserial reload
```
And see what that does.  Then try rebooting and restarting X a few times.

---

### Post by TrevT93 on 2009-07-30
Nothing did anything, unfortunately.  Restarting my computer a few times after using setserial reload produced no different results.  And the dmesg command in a terminal didn't return anything, with or without sudo.

---

### Post by ace214 on 2009-07-30
> **TrevT93 said:**
> Nothing did anything, unfortunately.  Restarting my computer a few times after using setserial reload produced no different results.  And the dmesg command in a terminal didn't return anything, with or without sudo.
Try adding the uart 16550A to your serial.conf.

---

### Post by TrevT93 on 2009-07-30
Adding uart 16550A causes the same erraticness as before.  So does uart 16954 (in the Linux forums post you showed me before).

EDIT: I tried "dmesg | grep ttyS*" in the terminal to see if something different would happen (compared to the last time I tried it), and it returned this:

```
[    0.004000] console [tty0] enabled
```

I don't know whether or not that means anything, but at least it's a change from before.  (Does that just mean that the tablet is working?)

---

### Post by Favux on 2009-07-30
Hi TrevT93,

I'm not sure what it means.  But at least it's new.

I think we've tried most things.  My suggestion would be to comment out that .fdi subsection that is configuring the baud_base in case it is interfering with setting up through xorg.conf.  I know of one other case where a .fdi interfered with setting up in xorg.conf.

So go to "/usr/share/hal/fdi/policy/10osvendor/" and open up "10-tabletPCs.fdi":
```
gksudo gedit /usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi
```
The second section refers to 'FPI2004' and sets the baud_base to 38400.  It looks like:
```
<!-- to get the device up we need to set the baud_rate correct -->
      <match key="pnp.id" contains="FPI2004">
	<merge key="input.device.set" type="string">/dev/ttyS0</merge>
	<merge key="pnp.serial.baud_base" type="int">38400</merge>
      </match>
```
Notice the first line is "commented out" using <!--  -->.  So just cut and paste the trailing --> to include the whole subsection.  Like so:
```
<!-- to get the device up we need to set the baud_rate correct
      <match key="pnp.id" contains="FPI2004">
	<merge key="input.device.set" type="string">/dev/ttyS0</merge>
	<merge key="pnp.serial.baud_base" type="int">38400</merge>
      </match> -->
```
Save and close.  Reboot.

You don't have a 10-fpit.fdi installed anywhere do you?

---

### Post by TrevT93 on 2009-07-30
No, I searched the system and came up with no 10-fpit.fdi.  And the commenting out didn't change anything.

---

### Post by Favux on 2009-07-30
Hi TrevT93,

Ok, go back to the autoconfig line in serial.conf.  That's what first got you activity.  Then do the setserial reload line.  And reboot a few times.

---

### Post by TrevT93 on 2009-07-30
Again, no change.  (And I feel like my two sentence replies are unnecessarily driving up my post count...but it's the only way to respond, I suppose.)

---

### Post by Favux on 2009-07-30
Hi TrevT93,

Did you remember to try adding the baudrate line to xorg.conf?

So in review:

-Your hardware is working.  It works in windows and your battery is fresh.
-Ace214 is able to get his working using xorg.conf in Jaunty and Kharmic.
-We've eliminated any potential interference from the BaudRate .fdi.
-There is no fpit.fdi to cause interference.
-We've looked at several variations of the fpit xorg.conf and tried them all.
-We know setserial works in Jaunty.
-We have the correct serial line for serial.conf and have tried several variations that should work.
-We know the fpit driver works in Jaunty.  That would be my prime suspect at this point, except ace214 says it works.

As far as I can tell that leaves us with one of either of these two possibilities.  See if these make sense to you.
1)  Ace214 talked about activity once the xorg.conf was set up, even without the serial line in serial.conf (post #52).  I suspect in Zuke24's case the stylus battery was dead, which is why he didn't get activity.  But you are getting activity.  So maybe something is wrong with your serial.conf file.  The permissions?  Was it there or did you create it?  If so how?  The exact method or commands, if you remember them.

There should be error(s) in System>Administration>System Log, probably in Xorg.O.log.

2)  Something is wrong with your Jaunty install.  That may be why dmesg gets you nothing.  You may need to download a new iso and burn a new CD (at slow speed) and reinstall it.

Or we can see if a 10-fpit.fdi would work for you.

---

### Post by TrevT93 on 2009-07-30
Yeah, even with the baudrate line in xorg.conf, I get the same response.

serial.conf was created by me the first time I tried solving this, using other people's forum threads.  It wasn't in existence before.  I just opened GEdit and saved the file I made as serial.conf to the etc folder.  As for the permissions, under "owner" it says read and write, and the other two ("group" and "other") are read only.

As for the Xorg.0.Log, there are no errors.  A few warnings, but everything seems fine.  Here's the section with the tablet, if you can make sense of it:

```

(**) TOUCHSCREEN: always reports core events
(**) FPIT device name: TOUCHSCREEN
(**) Fpit associated screen: 0
(**) Option "MaximumXPosition" "12550"
(**) FPIT maximum x position: 12550
(**) Option "MinimumXPosition" "400"
(**) FPIT minimum x position: 400
(**) Option "MaximumYPosition" "7650"
(**) FPIT maximum y position: 7650
(**) Option "MinimumYPosition" "400"
(**) FPIT minimum y position: 400
(**) Option "InvertY"
(**) Option "Passive" "false"
(**) Option "TrackRandR"
(**) FPIT invert X axis: No
(**) FPIT invert Y axis: Yes
(**) FPIT swap X and Y axis: No
(**) FPIT Passive button mode: No
(**) FPIT RandR tracking: Yes
(II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: Fujitsu Stylistic)
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "38400"
(**) Option "StopBits" "0"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "10"
(**) Option "Vtime" "1"
(**) Option "FlowControl" "None"

```

As for number two...well, if I'm going to be doing that, then I want to be absolutely sure that all my other options were exhausted.  And I'll probably use unetbootin this time to mount Jaunty to a flash drive.  My laptop supports booting from flash disks, and the transfer rate would probably be phenomenal compared to a CD.

---

### Post by Favux on 2009-07-30
Hi TrevT93,

We may have found the problem.  When I look at other .conf in /etc/ I see permissions are for root.  As user I can't do anything to them.  You should go ahead and look at them and see what I mean.  Unfortunately ace214 is gone for a week so we can't ask him.  But I think you were suppose to create the file with:
```
gksudo gedit /etc/serial.conf
```
save and close which would give it root permissions.  But I'm not positive.  I'm gathering you didn't do this.

Your Xorg.log looks OK and I don't see any errors in what you've posted.  I don't know if serial.conf not working would give errors in it.

It sure seems suspicious that we're at where ace214 said he was, activity with xorg.conf, before he added the serial line.

---

### Post by TrevT93 on 2009-07-31
The permissions are back at "root", but that did not change the problem with the tablet, unfortunately.  I thought it would do it (but then again, what do I know?).

EDIT: my xorg.conf had the same problem, so for good measure, I replaced it with a root-permissioned copy.  Again, though, no change.

---

### Post by Favux on 2009-07-31
I really don't understand that.  The xorg.conf is automatically generated on install, and in Jaunty holds video sections.  It is a basic system file.  You should not have been able to edit it ever without being root:
```
gksudo gedit /etc/X11/xorg.conf
```
And I guess I thought /etc/serial.conf, if not automatically generated by serial devices, was generated by setserial.  But I've never been sure.

---

### Post by TrevT93 on 2009-07-31
Yeah, well, I never quite knew what I was doing, so whenever I wanted to modify the xorg.conf, I opened it (just double-clicking it) with GEdit, made changes, then saved it to my desktop and then "sudo mv"ed it to the right folder, which probably changed its permissions to the non-root ones.  At least now I know how to do it properly.

And, no, serial.conf didn't exist, even after installing setserial.  I had to make it myself, and of course didn't do it the proper way.

---

### Post by Favux on 2009-07-31
Hi TrevT93,

Sorry, partly our fault, we should have checked with you.  Permissions on both should be Owner and Group both root with access grayed out.  As should access for Others.  Another thing that trips up a lot of folks is that the X in "/etc/X11/" is capitalized.  Is it possible you've been editing:
```
/etc/x11/xorg.conf
```
and not:
```
/etc/X11/xorg.conf
```
?

So I don't know what to try now.  I guess with sudo mv you didn't mess xorg.conf up too much or your system wouldn't have booted.  You could remove serial.conf with:
```
sudo rm /etc/serial.conf
```
Then completely uninstall setserial with Synaptic and reboot.  Then reinstall setserial and put serial.conf back with the line.  But I'm not sure what that will do for you.  Frankly I'm baffled.  Given what ace214 has told us we should have it working by now.  So we're probably missing something obvious.  One of those deals where you make a wrong assumption and never notice it even after going over it multiple times.

---

### Post by TrevT93 on 2009-07-31
As for using exact case, don't worry.  I'm obsessive-compulsive when it comes to typing things out.  (Notice I haven't missed a single period, left a misspelled word, or anything like that so far this thread?  This is how I am all the time when it comes to my computer.)

As for removing setserial, I think I've actually done exactly that sometime during the course of our struggle.  But to be completely sure, I'll do that now and get back to you in this post.

EDIT: no luck.  As I had believed.  I did everything by the book this time, since I now know better.

Actually, I'm thinking that, since the school year is approaching, I should get a fresh install of Ubuntu.  I do the same with Vista, since I have the recovery console built into my computer.  Plus, we could see if anything is different post-reinstallation.  What do you think?

---

### Post by Favux on 2009-07-31
Hi TrevT93,

I think that's probably the way to go.

But to be sure I'm not taking anything for granted what I mean by complete uninstall is in Synaptic when you right click on setserial you chose not uninstall but complete uninstall.  That way any configuration files it has are removed too.  If that isn't what you've done please try that.  You can leave serial.conf in place this time.  I know some people add the serial line to I think it's rc.local.

We could also see if a .fdi works.  That should be relatively quick.  Of course you'd be the first it works for, as far as we know.

---

### Post by TrevT93 on 2009-07-31
I didn't take any chances and chose "complete uninstall" when I was in Synaptic the first time.

If you can get the FDI working, then let's try that before I move right into the uninstall everything route.

---

### Post by Favux on 2009-07-31
Hi TrevT93,

Well you'd be the only person testing the .fdi until ace214 gets back.  I reviewed a bunch of stuff and it's the best I can do right now.

-First comment out the entire fpit section and entire "ServerLayout" in xorg.conf, ie place a "#" in front of each line.
-Move the trailing comment, -->, in the 10-tabletPCs.fdi back to where it was, activating the BaudRate part of the .fdi.
-Reboot
-Install the 10-fpit.fdi in "/etc/hal/fdi/policy/":
```
gksudo gedit /etc/hal/fdi/policy/10-fpit.fdi
```
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

          <!-- Gateway Finepoint - Active pen devices -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains="FPI2004">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">fpit</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
        <merge key="input.x11_options.Passive" type="string">false</merge>
          <merge key="input.x11_options.TrackRandR" type="string">true</merge>
          <merge key="input.x11_options.MaximumXPosition" type="string">12550</merge>
          <merge key="input.x11_options.MaximumYPosition" type="string">7650</merge>
          <merge key="input.x11_options.MinimumXPosition" type="string">400</merge>
          <merge key="input.x11_options.MinimumYPosition" type="string">400</merge>
          <merge key="input.x11_options.InvertY" type="string">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
Save and close.
-Reboot (a few times, if need be)

As you know from previous posts ace214 and I aren't sure if the serial.conf and setserial should be installed or not.  I think he removed the serial line from serial.conf while we test the .fdi's.  Leave them active for now.  If it doesn't work try:
-Remove serial.conf (might as well do that rather than just the line)
-Reboot
Still doesn't work
-Completely uninstall setserial
-Reboot

If it doesn't work not too much time lost.

Good luck!

---

### Post by TrevT93 on 2009-08-01
Yeah, didn't work.

Tell me when you want me to go about reinstalling Ubuntu.

---

### Post by Favux on 2009-08-01
Hi TrevT93,

Well that's disappointing.

Up to you.  Whenever you've decided searching the forums, googling, and reviewing this thread is a dead end.

Boy, do I hope a reinstall is the magic fix you need.

---

### Post by TrevT93 on 2009-08-01
So do I.  I just did my annual reset of Vista and am working on reinstalling anything of importance; as soon as I'm done with that, I'll do Ubuntu as well.  I don't have that much I would need to reinstall on Ubuntu, so it should be much quicker than Vista is.

---

### Post by Favux on 2009-08-01
Hi TrevT93,

Good luck!

First thing I'd do after installing and doing all the updates is:
```
dmesg | grep ttyS0
```
and see if it gives you the serial output.

---

### Post by TrevT93 on 2009-08-01
Well, I did it while running it live off my flash drive, and it still came up with nothing.

Does that change anything?

---

### Post by Favux on 2009-08-01
Not a clue.  I sure wish it would give you the output though.  Either before or after setserial's installed.  Some folks say setserial interferes with the getting the output, which is why I want you to try it first thing.

---

### Post by TrevT93 on 2009-08-02
Okay, reinstall complete.  No output using dmesg | grep ttyS0...or with sudo.

---

### Post by Favux on 2009-08-02
Hi TrevT93,

Alright.  Try putting the xorg.conf stuff back in and rebooting.  See if you get the activity back that ace214 talked about.

Then I'm not sure:  serial.conf first or setserial?  Either way you want to try it try the dmesg command again after setserial is installed.

---

### Post by TrevT93 on 2009-08-02
Nevermind all of that!  It WORKS!!!!!!!

Well, kind of.  Still one issue to resolve.  After following [these instructions]("https://help.ubuntu.com/community/FujitsuStylus"), using the setserial reload command, and then restarting my computer, the cursor follows my stylus.  Quite more stably than Windows ever did (something I didn't understand, because I thought it was just the cruddy hardware).  The only problem seems to be that the right click is being more or less held down, even though I am not pressing the right click, or even pressing the point to the screen.

Sooooooooooo close...

So why did it work this time around?  I've followed those instructions before, I know I have.  I think they were the first thing I tried.

EDIT: the above problem is remedied by holding down the right-click button.  If that is helpful at all.

---

### Post by Favux on 2009-08-02
Hi TrevT93,

Awesome!  Good job.

Is it possible some of those configurations were still on your last install?

Now you're where we were at trying to deal with the stylus button on the Gateway M 285-E.  That's what the button lines are for in the xorg.conf in post #30.

---

### Post by TrevT93 on 2009-08-02
I looked back at the post and tried both of the button lines, including un-commenting the Option "Button2" line.  No go.

---

### Post by Favux on 2009-08-02
Hi TrevT93,

OK.  I don't think the fpit readme tells us much but we can look at it.  Have you tried "man fpit" in a terminal?

The wiki you used has a script to toggle between touch and stylus.  Yours doesn't have a touch screen does it?

Edit:  Here's what the fpit readme says:
> Hints if you are having problems (Thanks to Aron Hsiao):

Problem 1:  Side switch being reported as wild button numbers
	   (like 249 instead of 3): 

Solution:  Add the following to your xinitrc: 

	xsetpointer TOUCHSCREEN
	xmodmap -e 'pointer = 1 2 3'

This should be re-stating the defaults, but Aron Hsiao agrees that it appears
to be an XFree86 4.x bug.
Although from the wiki it should be '1 3 2'.  And we should see what "xinput --list" is calling the tablet.  The "xsetpointer name" sets whatever name is as the primary pointing device.  So maybe all that's need is the xmodmap.

---

### Post by ace214 on 2009-08-03
I would undo that last step on that tutorial about right click.
I got right-click to work by following [this wiki page]("https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse") to get the commands, and set the button map on the stylus to 1 3 2.

Also, xmodmap didn't work for me in Jaunty.

---

### Post by Favux on 2009-08-03
Hi ace214,

Thanks.

So:
```
xinput set-button-map "name" 1 3 2
```
where you got the name from:
```
xinput list | grep 'id='
```
and to view current button map:
```
xinput get-button-map "name"
```
And then plug the line into ~/.xstartup or other init file.

---

### Post by TrevT93 on 2009-08-03
Nevermind, nevermind (I thought I posted this earlier, but as it turns out I didn't...).

The final instruction works, but I forgot to follow the end of it...by typing "ms s" in the terminal, the right click sorts itself out.

Anyway, to close, thank you both for the useful help.  One last thing: are there any good applications for a tablet PC, namely some kind of notebook I can write in with my stylus?

---

### Post by ace214 on 2009-08-03
> **TrevT93 said:**
> are there any good applications for a tablet PC, namely some kind of notebook I can write in with my stylus?

I use Xournal. It is in the repos. I also use it for highlighting PDFs for school.

---

### Post by Favux on 2009-08-03
Hi TrevT93,

Alright, all done!

You'll want to check out CellWriter also.  And if you like pen flicks check out Tom Jaeger's EasyStroke.

---

