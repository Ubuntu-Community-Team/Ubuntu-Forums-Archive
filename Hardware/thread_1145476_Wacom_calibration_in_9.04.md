---
title: "Wacom calibration in 9.04"
date: 2009-05-01
forum: Hardware
---

### Post by YenTheFirst on 2009-05-01
Hello. I have a Lenovo x60 Tablet, and I'm trying out the 9.04 liveCD before installing it.

The tablet screen works perfectly, and even the touchscreen is enabled and working by default.

The problem, however, is that the calibration on the touch is off. In 8.04, I set parameters with:
 xsetwacom set touch BottomX somevalue

however, xsetwacom doesn't recognize my tablet in 9.04. xsetwacom list returns 0 results. Also, wacomcpl doesn't show any devices when I run it. (I think wacomcpl is based on xsetwacom)

So, I'm sure I'm missing something obvious here, but how does one go about calibrating a tablet in 9.04?

---

### Post by Favux on 2009-05-01
Hi YenTheFirst,

Nope, you are not missing something obvious.  The reason wacomcpl is showing up empty is a bug in Wacom for Jaunty. Timo Aaltonen specially patched the linuxwacom 0.8.2-2 in Jaunty to work with Xserver 1.6 and HAL. Unfortunately the callout in the .fdi file is returning HAL/D-BUS names that linuxwacom doesn't understand. So xsetwacom commands and hence wacomcpl don't work.

While we are waiting for them to fix it we have found a few work arounds. See Jaunty Users near the top of the link here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Once you get wacomcpl working you can calibrate using Section 3.

---

### Post by Amrith Kumar on 2009-05-10
I found that many links on this subject didn't work for me. The names of the devices are incorrect as indicated in most of these posts.

I found a different workaround that is at [http://technophilesdiary.wordpress.com/2009/05/10/ubuntu-9-04-wacom/](http://technophilesdiary.wordpress.com/2009/05/10/ubuntu-9-04-wacom/)

I hope it helps some of you.

---

### Post by Zuke24 on 2009-07-27
Hello all!

I have an X61 and found this topic when trying to calibrate my touchscreen as well.  The stylus is dead on, but my touchscreen is off.  It seems to be right on target in the middle of the screen, but the further out you get, the more "off" it becomes.

I installed the Wacom Tools, and when I run wacomcpl, I get the Control Panel.  However, there are no devices listed in it.  Am I doing something wrong?

---

### Post by Favux on 2009-07-27
Hi again Zuke24,

Nope, you're running into a bug with the serial part of the 10-wacom.fdi.  It doesn't parse the names HAL is returning into linuxwacom names.  To see this in a terminal:
```
xsetwacom list
```
will be blank instead of showing your wacom input devices.  To see the names HAL is returning:
```
xinput --list
```
To fix this you probably want to use rec's script.  See 3 and 3a in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Good luck!

---

### Post by Zuke24 on 2009-07-27
Xinput returned a load of stuff, but I'll only bore you with the pertinent stuff. :P
```
"PnP Device (WACf008)"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"PnP Device (WACf008) touch"    id=3    [XExtensionKeyboard]
    Type is Wacom Touch
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1024
        Resolution is 106
    Axis 1 :
        Min_value is 0
        Max_value is 1024
        Resolution is 141
    Axis 2 :
        Min_value is 0
        Max_value is 255
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
"PnP Device (WACf008) eraser"    id=4    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
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

```

As for 3 and 3a, I'm a little confused as to what you mean.  I followed everything in that first post exactly.

Backing up a little bit, when I installed 9.10 on the X61, the Wacom worked right off the bat!  I installed the wacom-tools, and it wouldn't show the devices in the cpl.  So I followed your guide and got a little worried because suddenly it STOPPED working.  After adding everything to my xorg,conf (in your section 2), I was back to where I was before I started the guide! lol

---

### Post by Favux on 2009-07-27
Hi Zuke24,

I realize you don't realize it but I still don't know what you did.

Did you compile and install linuxwacom 0.8.2-2 as the HOW TO shows you how to do?  You shouldn't have been able to do that because it doesn't support Xserver 1.6.  It should have given an error.

The 0.8.2-2 linuxwacom that comes default with Jaunty is not the same.  It has been specially patched to support HAL and Xserver 1.6.

Rec's script is linked in 3a) in the Jaunty Users section near the top.

Right now HAL is saying:

stylus = PnP Device (WACf008 )
eraser = PnP Device (WACf008 ) eraser
touch = PnP Device (WACf008 ) touch

Which is why wacomcpl doesn't work.

All you need is the two default Jaunty linuxwacom packages and rec's script and you should be good.  You can use xorg.conf if you want to but you lose USB hotplugging.  And you have to compile and install linuxwacom 0.8.3-2 or up.

If you compiled and installed another linuxwacom we'll have to remove that first.

---

### Post by Zuke24 on 2009-07-27
I followed your tutorial in post #1, and I didn't get any errors strangely enough.  Also, I can't seem to find this script that everyone refers to.  I know I'm probably looking in the wrong spot, but I just haven't seen it yet. 

I might just wipe this tablet back to a default install (maybe 64bit this time) and start again, since I'm pretty sure I've done a load of stuff I can't undo.

---

### Post by Favux on 2009-07-27
Hi Zuke24

Rec's script in post #93 here:  [http://ubuntuforums.org/showthread.php?p=7068115#post7068115](http://ubuntuforums.org/showthread.php?p=7068115#post7068115)

To uninstall a linuxwacom you may have compiled and installed, first enter these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then change directory into the unpacked linuxwacom tar you used.  Then change directory into the "prebuilt" folder.  Then in a terminal:
```
sudo ./uninstall
```
You don't need to worry about the wacom.ko since it's for usb not serial tablets.  Go to Synaptics and reinstall the 0.8.2-2 xserver-xorg-input-wacom and wacom tools.

---

### Post by Zuke24 on 2009-07-27
Very cool!

I'm good to go!!

---

### Post by Zuke24 on 2009-07-27
Well, ok just about.

I know I read it somewhere, but why do I keep losing my calibration everytime I reboot?

EDIT:  Fixed it.  Thank you so much everyone!  This is awesome, and I'm really excited to have it all working!

2nd Edit:  No, it's not fixed!  commenting out the line in my .xinitrc file didn't work after all.

---

### Post by Favux on 2009-07-27
Hi Zuke24,

At a guess you didn't make .xinitrc executable.  That's the chmod line in Section 3 of the HOW TO.  Use Places (Nautilus) to navigate to it (remember it's a hidden file so check hidden file in View) and use Properties to check.

---

### Post by Zuke24 on 2009-07-27
Nope, it's executable.  Did that (and did it again just to make sure), double checked the line was still rem'd out, and logged out and back in.  It immediately dumped my calibrations.

---

### Post by Favux on 2009-07-27
Hi Zuke24,

Hmmm.  That shouldn't be happening.  You're almost there.

Go back and check the "/etc/X11/xinit/" and make sure the line is commented out.  Also recheck "System->Preferences->Startup Applications" and make sure the command line is correct.

---

### Post by Zuke24 on 2009-07-27
Sorry, which file am I looking for?  I thought I was looking for the xinitrc in my home folder?

Also, what is supposed to be in my startup apps?

---

### Post by Favux on 2009-07-27
Hi Zuke24,

There's two xinitrc's.  One is wacomcpl's .xinitrc in /home/username/.  Did you go through Section 3 here?:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Zuke24 on 2009-07-28
GAH!!  I thought I did, I must have scrolled down and missed that line!  I'll do it first thing in the morning and report back. :-S

---

### Post by Zuke24 on 2009-07-28
YAY!!!!  The touchscreen is finished!  Thank you sooo much!

Now, my todo list:
[LIST]
[*]Fingerprint Reader
[*]Screen Rotation
[*]WWAN Card (need to buy and install one first)
[*]Learn to program!
[/LIST]

OK, screen rotation is off the list!  And working with someone about getting the finger print reader working:
[http://www.krizka.net/2008/01/28/enabling-fingerprint-scanner-on-thinkpad-x61-running-ubuntu/](http://www.krizka.net/2008/01/28/enabling-fingerprint-scanner-on-thinkpad-x61-running-ubuntu/)

---

### Post by Favux on 2009-07-28
Hi Zuke24,

Outstanding!  Nice job.

For rotation you could look at:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  Method 1 or 3.

Here's the thinkwiki link:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)  It should be helpful.

---

### Post by SaintDanBert on 2010-09-05
I know that Jaunty (v9.04), Karmic (v9.10), and Lucid (v10.04) have all come and gone.

I know that **xinput** has changed and changed and changed.

I know that **hal** came and went.

I know that **xorg.conf** came and went.

I know that **wacom-tools** package came and went.

I use [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator) to calibrate Lucid. I still cannot calibrate Jaunty or Karmic.

I use Karl Hegbloom's tablet-screen-rotation-support packagge to implement screen rotation. Works everywhere. It is available from his PPA [http://ppa.launchpad.net/karl.hegbloom/ppa/ubuntu](http://ppa.launchpad.net/karl.hegbloom/ppa/ubuntu)

One important thing I've learned:
[list]
[*]USB tablets have an effective and working device discovery and configuration process.
[*]built-in, OEM-serial tablets lack effective **discovery** so the configuration does not happen properly
[/list]

With Maverick (v10.10) around the corner in roughly six weeks, can anyone comment about whether  these several tablet issues will be resolved at last?

Wishing and hoping,
~~~ 0;-Dan

---

