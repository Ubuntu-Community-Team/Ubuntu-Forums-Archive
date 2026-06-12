---
title: "Fujitsu tablet T4020D not working maverick linuxWacom"
date: 2011-03-09
forum: Hardware
---

### Post by chadonline on 2011-03-09
After installing ubuntu 10.10 to my fujitsu lifebook T4020D, touch screen/tablet screen did not work. 

I followed the section1 steps successfully at:
[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

and installed linux wacom drivers, but touchscreen still not working

here are some more details:

dmesg | grep Wacom
[   18.655954] wacom: v1.52-pc-0.4:USB Wacom tablet driver

lsmod | grep wacom
wacom                  30801  0 


xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]


any help is appreciated

thank you
chad

---

### Post by Favux on 2011-03-09
Hi Chad,

Welcome to Ubuntu forums!

A natural misunderstanding.  Section 1 installs the usb kernel driver/module wacom.ko.  You don't need that since the internal connection with a Fujitsu Lifebook T4020D is a serial one.  So all you need is the X driver wacom_drv.so.  That's in the xserver-xorg-input-wacom package.  The package has xf86-input-wacom (where the X driver comes from), the default version for Maverick is 0.10.8.  It sounds like the default version isn't working for you so you need to update xf86-input-wacom.

That's what section 2 on the linuxwacom HOW TO does.  You might prefer to use part II. on the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") which does the same thing.  So clone the xf86-input-wacom git repository and reboot and see if the Wacom digitizer starts working.

Hope this helps.

---

### Post by chadonline on 2011-03-11
Thanks for the quick response. I followed the section 2 steps and cloned the git repository but still no luck. One thing surprised me that It is still showing usb after all the new steps. Is there anything else I need to do?

---

### Post by Favux on 2011-03-11
Could you show me the contents of your 50-wacom.conf in /usr/share/X11/xorg.conf.d?

---

### Post by chadonline on 2011-03-11
Here are the contents of the folder /usr/share/X11/xorg.conf.d  (i also zipped and attached them all just in case) 

total 24
-rw-r--r-- 1 root root  115 2010-08-09 16:36 50-vmmouse.conf
-rw-r--r-- 1 root root  622 2010-09-22 21:20 51-synaptics-quirks.conf
-rw-r--r-- 1 root root  171 2010-09-22 21:20 50-synaptics.conf
-rw-r--r-- 1 root root 1099 2011-01-09 06:16 10-evdev.conf
-rw-r--r-- 1 root root  125 2011-01-14 19:09 60-magictrackpad.conf
-rw-r--r-- 1 root root  833 2011-03-10 17:56 50-wacom.conf


Thanks

---

### Post by Favux on 2011-03-11
Well, your 50-wacom.conf looks normal so that's not the problem.

Is your install a 64-bit install?

We don't care about lsmod or dmesg because that shows us the wacom.ko, which is the usb driver.

Nothing in *xinput list* yet?  Let's see what's in your Xorg.0.log located at /var/log.   Right click on it and compress it with Create Archive.  Attach it to your next post with Manage Attachments below.

---

### Post by chadonline on 2011-03-12
No, it shouldn't be a 64bit install.

Here is the xinput list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]


I attached the Xorg.0.log AND Xorg.0.log.OLD located at /var/log

---

### Post by chadonline on 2011-03-15
any ideas?

---

### Post by Favux on 2011-03-16
It doesn't look like you have the Wacom X driver installed.  There is no sign of the Wacom module in Xorg.0.log.

You should have had the default xf86-input-wacom-0.10.8 (the X driver) automatically installed with Maverick.  When you compiled/cloned 0.10.11+ it should have been right over it.

Check in Synaptic Package Manager that you have xserver-xorg-input-all installed.  If you uninstalled that xf86-input-wacom won't work.  If it isn't installed install it.  That will also bring 0.10.8 back as a dependency (removing one removes the other, installing one installs the other) so you'll have to reclone xf86-input-wacom.  Were there any errors or other problems when you cloned the git?

If that's not the problem do you know if the hardware works?  The digitizer works in Windows for example?

---

### Post by chadonline on 2011-03-17
I checked the Synaptic Package Manager and xserver-xorg-input-all was not installed (not sure why, I didn't see any errors). I installed it.
Is the next step reclone xf86-input-wacom ?  If so how can I do that?

---

### Post by Favux on 2011-03-17
I'm assuming when you installed xserver-xorg-input-all it installed xserver-xorg-input-wacom (the xf86-input-wacom-0.10.8 package)?  You rebooted, correct?

If so then follow part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to clone the xf86-input-wacom git repository.

I'm assuming you haven't used any Wacom PPA.

---

### Post by chadonline on 2011-03-18
Right, xserver-xorg-input-all and xserver-xorg-input-wacom are installed and I rebooted. 
I followed the steps to clone the xf86-input-wacom git repository (terminal results are attached)
and rebooted. 

then I did 

cd Desktop
cd xf86-input-wacom
git pull


and stopped there...(touhcscreen still doesn't work) 
I do not know what is Wacom PPA.

Please let me know what is the next step.

---

### Post by chadonline on 2011-03-22
Any updates?

---

### Post by Favux on 2011-03-22
Hi Chad,

Sorry, your cloning of xf86-input-wacom looks good.  Stylus still doesn't work?  I assume you rebooted?  What do you see in the output of?:
```
xinput list
```
Let's look at the 50-wacom.conf in /usr/share/X11/xorg.conf.d and make sure that's good.

---

### Post by chadonline on 2011-03-23
Stylus or touch screen still doesn't work...



xinput list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]


and here is what I have in 50-wacom.conf 


Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection


Please advise...
thanks

---

### Post by Favux on 2011-03-23
Well there's definite progress in the *xinput list*:
```
&#9116; &#8627; Serial Wacom Tablet stylus id=14 [slave pointer (2)]
&#9116; &#8627; Serial Wacom Tablet eraser id=15 [slave pointer (2)]
```
So your input devices are now showing up.  By the way your tablet doesn't have touch does it?  In other words it is not suppose to respond to a finger on it, just the stylus, correct?

Let's check if the wacom X driver is seeing them:
```
xsetwacom list
```

Your 50-wacom.conf looks good.

And a PPA is a personal package archive.

---

### Post by chadonline on 2011-03-23
I believe it is stylus only. 

here is the xsetwacom list
Serial Wacom Tablet stylus          id: 14    type: STYLUS    
Serial Wacom Tablet eraser          id: 15    type: ERASER    

I don't have the original stylus, I am using the stylus from my pda. This should work as well.
I am not getting any response from the screen. 

Please let me know..

thank you

---

### Post by Favux on 2011-03-24
Hi Chad,

> I don't have the original stylus, I am using the stylus from my pda. This should work as well.
Unfortunately that's not true.  A Wacom digitizer is not resistive so not any type of stylus will work.  See:  [http://en.wikipedia.org/wiki/Wacom#Technology](http://en.wikipedia.org/wiki/Wacom#Technology)

It should be only about $20-40 (depending on model and #) to pick one up on wacom.com or fujitsu.com or just google wacom or fujitsu stylus.

So I'm thinking you have everything actually working now.  You just need the stylus.

---

### Post by chadonline on 2011-03-24
oh wow, you are right... I didn't know that original stylus has a  electromagnetic coil/capacitor. I will get one and let you know asap.. 

thank you

---

### Post by chadonline on 2011-03-31
I received my stylus and I am able to use the touchscreen. However, when I rotate the screen the pointer goes to opposite direction of the stylus. It inverts the touch points. For example, when I click at the bottom of the screen, the pointer goes to top of the screen (exactly the opposite direction). Is this a known issue?
what can I do to fix it?

---

### Post by Favux on 2011-03-31
Hi Chad,

Great, so it was the stylus and things are working.  Good.

You have to rotate the Wacom input tools when you rotate the screen.  Usually xsetwacom commands are used.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

But most Fujitsu users install the fjbtndrv (Fujitsu Button Driver) package.  It supports the bezel buttons and provides automatic screen rotation.  See Robert's PPA:  [https://launchpad.net/~khnz/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~khnz/+archive/ppa?field.series_filter=maverick)

---

### Post by chadonline on 2011-04-29
Can I upgrade to ubuntu 11.04? does that impact my wacom drives?

---

### Post by Favux on 2011-04-30
Hi Chad,

The newer Wacom driver in Natty should work fine.  What you would want to check out is if the fjbtndrv has been updated for Natty so you have automatic rotation and the bezel buttons.

---

### Post by chadonline on 2011-05-07
I upgraded to Natty and I lost the pen capability. My xinput list and 50-wacom.conf is just like before but touch screen still doesn't work. 
Please let me know what could be wrong?

Thanks

---

### Post by Favux on 2011-05-07
Let's make sure the wacom.conf is the same.  Natty uses xf86-input-wacom-0.10.11 as the default.  The patch to add *FUJ02e9* was committed about 3 weeks after it came out.  So unless Ubuntu added it it probably isn't there.  I don't know if that is your identifier but we should check.  So the if the line reads:
```
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
```
change it to read:
```
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
```
in this snippet:
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection
```
Then restart with fingers crossed.

---

### Post by chadonline on 2011-05-09
Desktop/xf86-input-wacom-0.11.0/conf/50-wacom.conf

file already had what you wrote above...

is there anything anywhere else?

---

### Post by Favux on 2011-05-10
Hi Chad,

Just to be sure the 50-wacom.conf you are looking at is in the xf86-input-wacom folder from your download of it?

I'm talking about the 50-wacom.conf system file that should be located at /usr/share/X11/xorg.conf.d.  That's the one you need to check.

---

### Post by chadonline on 2011-05-12
I opened this file
/usr/share/X11/xorg.conf.d/50-wacom.conf


contents already had what you wrote:



Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM|Hanwang"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection


Section "InputClass"
      Identifier "Wacom eraser class"
      MatchProduct "Wacom"
      MatchProduct "eraser"
      Option "Foo" "bar"
EndSection

---

### Post by Favux on 2011-05-12
Shoot, it can't be easy can it?

Have you tried restarting X?  Sometimes that initializes the Fujitsu Wacom digitizer.

Let's see what your output of *xinput list* in a terminal looks like.

---

### Post by chadonline on 2011-05-14
how can I restart X ?



xinput list:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; fsc tablet buttons                      	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

---

### Post by Favux on 2011-05-15
Go to Keyboard and open it which opens Keyboard Preferences.  Then in the Layouts tab click on 'Options...'.  Then select the 'Key sequence to kill the X server' and check the box in front of Control+Alt+Backspace.  Close out.

Then press the Control+Alt+Backspace keys.

---

### Post by chadonline on 2011-05-16
ok, ctrl+alt+backspace activates the touch pen. 

As soon as I hit ctrl+alt+backspace, screen turns black and logs me out. I then click on my user name to log back in. And looks like I have to do it every time I start the computer?
Additionally, when I rotate the screen the orientation is not working correctly. and part of the screen doesn't show. Any recommendations for those?

---

### Post by Favux on 2011-05-16
Great!   :)
> ok, ctrl+alt+backspace activates the touch pen. And looks like I have to do it every time I start the computer?

Unfortunately yes.  It appears Fujitsu has changed the protocol slightly on their version of the Wacom digitizers.  I guess none of the dev.s has had access to a Fujitsu tablet PC so they haven't been able to track the problem down.  I suspect only a very minor change to the code is necessary since it works fine after an X restart.  This has been going on for up to 2 years or so.
> Additionally, when I rotate the screen the orientation is not working correctly. and part of the screen doesn't show. Any recommendations for those? 
I think that's two problems.  xf86-input-wacom currently has cw and ccw reversed.  I found the bug and submitted a patch for it which was accepted but hasn't yet been pushed to the git repository.  So for now just reverse cw and ccw on your rotation script.

The missing screen may be due to your video driver.  What video chipset do you have and which driver are you using for it?

---

### Post by chadonline on 2011-05-17
Quote:
"So for now just reverse cw and ccw on your rotation script."[/I]

How can I do that?

Quote:
"The missing screen may be due to your video driver. What video chipset do you have and which driver are you using for it?"

With the Ubuntu 10.10, there was no missing screen. So I do not know if it is related to video chipset. 
Where can I see the cipset and which driver is being used?

Thanks again

---

### Post by Favux on 2011-05-17
> How can I do that?
Are you using the fjbtndrv for rotation?  If so it installs a rotation script somewhere.  Someone finally showed me where and what it looked liked a couple of months ago.  I'll see if I can remember.

To get your video chipset enter in a terminal:
```
lspci | grep VGA
```
And your video driver should be listed in Xorg.0.log in /var/log.

---

### Post by chadonline on 2011-05-17
I was using fjbtndrv with previous ubuntu 10.10.. with the new ubuntu I did not load it. Should I? would that make a differece?

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)


I attached the  Xorg.0.log in /var/log

---

### Post by chadonline on 2011-05-20
Please let me know if you have any updates..

---

### Post by Favux on 2011-05-20
If the fjbtndrv has been updated for Natty I'd install it.  In addition to the rotation script it enables the bezel buttons.  If you don't want to you can use a rotation script from the [rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").

Alright so you have a motherboard video chipset:
> Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
I don't remember that one having problems with Natty, but now we have something to google with.  I'm not sure what this at the end of the Xorg.0.log is telling us:
```
[    46.216] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 1022 < target_msc 1023
[    46.295] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 1027 < target_msc 1028
[    73.599] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 2376 < target_msc 2377
[    73.716] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 2383 < target_msc 2384
[   100.220] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 3637 < target_msc 3638
```
Is that after you tried to rotate?

If there is a xorg.conf we should look at that.  It would be located at /etc/X11.  If I recall correctly some Intel chipsets need a buffer size set (increased) or something done with DRI or some such.  I don't think a randr "on" tye Option is needed or even used for them.

Edit:  googling with 'intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc' is bringing up recent hits for bugs in the xorg intel video driver.  Unfortunately using 'Option "PageFlip" "off"' doesn't seem to help.  Apparently PageFlip has something to do with the EXA acceleration method.  Enabling it used to turn EXA off but apparently you can have both on with the newer drivers.  Except maybe we're seeing a conflict due to a regression?

---

### Post by chadonline on 2011-05-21
> "If the fjbtndrv has been updated for Natty I'd install it. In addition to the rotation script it enables the bezel buttons."

Oddly my bezel buttons (ones at the bottom of the screen) are already working without fjbtndrv. 

> "Is that after you tried to rotate?"

Yes, I believe it was after I rotated the screen. 


> "If there is a xorg.conf we should look at that. It would be located at /etc/X11."

My computer wouldn't boot up to the desktop/home screen with /etc/X11/xorg.conf therefore I had to move it. 


> "Except maybe we're seeing a conflict due to a regression?"

I had pretty much the same issue before. I would like to use my screen folded, straight up (height wise). As I mentioned before, pointer is going the opposite direction when I use the pen. Is there a way to fix that? If so, can you please walk me through?

---

### Post by Favux on 2011-05-21
> Oddly my bezel buttons (ones at the bottom of the screen) are already working without fjbtndrv. 
That's interesting.  So really less need for fjbtndrv?  Did you do a clean install of Natty or an update?
> As I mentioned before, pointer is going the opposite direction when I use the pen. Is there a way to fix that?
Sure.  You want portrait orientation.  Do you want the screen to go right (cw) in portrait or left (ccw)?  And how are you rotating the screen orientation now?

---

### Post by chadonline on 2011-05-21
> That's interesting. So really less need for fjbtndrv? Did you do a clean install of Natty or an update?

I did an update. 

> Do you want the screen to go right (cw) in portrait or left (ccw)? And how are you rotating the screen orientation now?

When I fold the screen to make it portrait, it turns to right (cw) at the moment. Here is the screen shot about the dark space. I did not have the same issue before with Ubuntu 10.10.

---

### Post by Favux on 2011-05-21
Ok, I think fjbtndrv driver got automatically updated with the update and that is what is rotating the screen.  And why the bezel buttons work.  Rather than mess with the fjbtndrv rotation script you can fix the problem by going to the source which is xf86-input-wacom-0.10-11.  It has a bug where cw and ccw are reversed if you update it by cloning the git repository as described in part II. c) of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?p=9496609#post9496609"), the update has the fix in it.

Thanks for the screen shot.  It looks like the video driver is scaling the swapped x & y axes correctly so I don't know why the top is being cut off.  A Natty Unity problem?  Or something like the buffer size not being big enough like I mentioned earlier?

---

