---
title: "Touch screen on Fujitsu t4310 &amp; Lucid"
date: 2010-10-14
forum: Hardware
---

### Post by arbre_vert on 2010-10-14
Hi everyone,

I am the happy owner of Fujitsu's t4310 laptop since 6 months now. Unfortunately I have never been able to get the touch screen fully functioning under Ubuntu. Pen & Eraser are working but not the finger touch. Even more tragic - or lucky I should say - is that everything runs smoothly on Win 7... 

I eventually gave up looking for solutions and hoped an miraculous update would fix the issue. As time goes by I do not see anything coming up and I'm tired of Windows... 

Anyone got it working?

I am running Ubuntu Lucid 2.6.32-25-generic. Any help is welcome.

---

### Post by Wittekind on 2010-10-25
Hi arbre_vert,

did you make any progress?
I had the same idea to switch to Ubuntu, esp. to Ubuntu 10.10. because I read that there were made huge improvements in using multitouch. I also use an T4310 but I can only use my pen with the (touch)screen, no finger touch :(.

I tried many tutorials and helps but this point I think I have to switch back to Win7.
What a pity.

Wittekind

---

### Post by arbre_vert on 2010-12-24
Nope, on December 24th, 2010, no progress from my side. Computer fully updated, last ubuntu distribution.

---

### Post by limotux on 2010-12-25
Hi,
Merry Xmas and happy new year.

I'm the same situation.
Running Lucid, KDE on T4310.
Everything is running fine out of the box, but still no luck with touch screen or any tablet features.

I have tried several advices here and there especially [https://help.ubuntu.com/community/T4310](https://help.ubuntu.com/community/T4310)

When I try to install 

[LIST]
[*]fsc-btns-kernel-source 
[*]fjbtndrv
[/LIST]
An error happens and refuses to install properly, which I find (by searching) it is a common problem as well.

I hope someone can help and guide me step by step, maybe it is something related to my setup or configuration.

Unfortunately I'm posting this now using M$ Windoz (which I really hate and feel so nervous using it)

Can a volunteer stand out and help?

---

### Post by Favux on 2010-12-26
Hi,

Does anyone know what digitizer/touchscreen it uses?  A lot of Fujitsu's use a serial Wacom digitizer.  Multitouch should work for them if it is Wacom.

Enter in a terminal:
```
xinput --list
```
and
```
dmesg | grep [Ww]acom
```
and post the outputs.

---

### Post by limotux on 2010-12-26
Hi... thanks a lot for attempting to help.
 Here is the result of the first one:

Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; stylus                                    id=6    [slave  pointer  (2)]
&#9116;   &#8627; eraser                                    id=7    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                id=16   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                  id=17   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=18   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=9    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=10   [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=11   [slave  keyboard (3)]
    &#8627; Power Button                              id=12   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=13   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=14   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=15   [slave  keyboard (3)]

But the second one nothing comes out.!!
I tried with both w & W for wacom!

AFAIK it should be a wacom tablet.

---

### Post by Favux on 2010-12-26
Alright, from your xinput list you appear to be using a xorg.conf.  Is it the one in the community wiki?  First of all that one has a cursor section which none of the tablet pc's have.  The cursor refers to the Wacom tablet mouse.  Everyone gets confused on that.  So you can delete the cursor section and the cursor line in "ServerLayout".  You'd have to add a touch section and a touch line in "ServerLayout".

But a xorg.conf configuration in Lucid isn't recommended.  You are suppose to use the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/.  We might have to add another serial snippet for the Fujitsu's in there depending on what yours looks like.

You can use xorg.conf if you want to go that route.

And let's look at the output of:
```
ls -l /dev/input/by-path
```

---

### Post by jruh64 on 2010-12-26
Hi, I also have a T4310 and just installed Ubuntu10.10 a couple days ago.
The touchscreen has never worked yet but the pen did work, Today the pen doesn't work anymore but that's a separate issue I guess.

I do know that it certainly is a Wacom digitizer, it has a "Wacom Penabled" sticker right on it.

Here is the output of "ls -l /dev/input/by-path":

[B]total 0
lrwxrwxrwx 1 root root 9 2010-12-26 20:24 pci-0000:00:1d.0-usb-0:2:1.0-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2010-12-26 20:24 pci-0000:00:1d.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 pci-0000:00:1d.7-usb-0:4:1.0-event -> ../event6
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 platform-i8042-serio-0-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 platform-i8042-serio-4-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 platform-i8042-serio-4-mouse -> ../mouse0[/B]


I hope this helps you to help us.  I am new to Ubuntu and by no means any kind of code reading, writing wizard.

It sure would be sweet if we could get the touchscreen to work. I installed the desktop version, would the netbook version have better support for touchscreen?

Thanks, John

---

### Post by jruh64 on 2010-12-26
I also tried **"dmesg | grep [Ww]acom"** and got nothing out.

I got different results for **"xinput --list"**:


[B]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Bluetooth Notebook Mouse 5000 	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                         	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; FJ Camera                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)][/B]


Could it be that the pen (stylus) is Wacom but the touchscreen is not?

John

---

### Post by Favux on 2010-12-26
Hi John,

OK, at a guess your tablet is using one or both of these events:
```
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 platform-i8042-serio-4-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 platform-i8042-serio-4-mouse -> ../mouse0

```
Let's look at your wacom.conf.  Since you have Maverick it will be called 50-wacom.conf and in /usr/share/X11/xorg.conf.d/.  Post the contents of that file.

Yes, occasionally another driver like Synaptic or evtouch can grab touch away.  We could check in Xorg.0.log at /var/logs and find out.  But hold off on that for now.

Let's look at the output of:ls -l /dev/input/by-id:
```
ls -l /dev/input/by-id
```
for now, and maybe even
```
ls -l /dev/input/
```

---

### Post by jruh64 on 2010-12-26
ok, here is contents of 50-wacom.conf:

[B]Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
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
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection[/B]


Output of **ls -l /dev/input/by-id**:

[B]total 0
lrwxrwxrwx 1 root root 9 2010-12-26 20:24 usb-1690_0741-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2010-12-26 20:24 usb-1690_0741-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-12-26 20:23 usb-Chicony_Electronics_Co.__Ltd._FJ_Camera-event-if00 -> ../event6[/B]


And output of **ls -l /dev/input/**

[B]total 0
drwxr-xr-x 2 root root    100 2010-12-26 20:24 by-id
drwxr-xr-x 2 root root    160 2010-12-26 20:24 by-path
crw-r----- 1 root root 13, 64 2010-12-26 20:23 event0
crw-r----- 1 root root 13, 65 2010-12-26 20:23 event1
crw-r----- 1 root root 13, 66 2010-12-26 20:23 event2
crw-r----- 1 root root 13, 67 2010-12-26 20:23 event3
crw-r----- 1 root root 13, 68 2010-12-26 20:23 event4
crw-r----- 1 root root 13, 69 2010-12-26 20:23 event5
crw-r----- 1 root root 13, 70 2010-12-26 20:23 event6
crw-r----- 1 root root 13, 71 2010-12-26 20:23 event7
crw-r----- 1 root root 13, 72 2010-12-26 20:23 event8
crw-r----- 1 root root 13, 73 2010-12-26 20:24 event9
crw-r----- 1 root root 13, 63 2010-12-26 20:23 mice
crw-r----- 1 root root 13, 32 2010-12-26 20:23 mouse0
crw-r----- 1 root root 13, 33 2010-12-26 20:24 mouse1[/B]

Thanks, John

---

### Post by Favux on 2010-12-26
Hi John,

I think we're narrowing in on it.  Your wacom.conf looks good.  It has the Fujitsu identifier snippet, so we're good there.  And you didn't add any wacom stuff to your xorg.conf in /etc/X11/ (if you even have one), correct?

I'd like to see your Xorg.0.log now.  It is in /var/log.  Right click on it and compress it with Create Archive.  Then use Manage Attachments below to add it to your next post.  Let's see if there is any sign of touch in it.

I'm suspecting the problem is xf86-input-wacom, the X driver.  I'm trying to remember if there was a recent commit in the last month or two that added touch to the Fujitsu's.  I think that's vaguely ringing a bell.

---

### Post by jruh64 on 2010-12-26
here is the compressed xorg.0.log file. 
I am not sure what i added, i know i installed some touch related items from the ubuntu software centre yesterday but i certainly did not add to or edit any files manually.

I know its a separate issue but my pen started working again after another reboot.

I will have to rejoin tomorrow evening and sign off for the night. I appreciate the help. Please understand that this is mostly over my head though.

Thanks, John

---

### Post by Favux on 2010-12-26
Great!  Enough memory banks got fired off that I remembered.  I am pretty sure you're having the problem Rafi was dealing with in this bug report:  [https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/671438](https://bugs.launchpad.net/ubuntu/+source/utouch/+bug/671438)

You don't need the patch he posted though.  You should be able to clone the xf86-input-wacom git repository and get the functionality you need.  I don't know for sure if they are going to backport the patch into Maverick.

See part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Since you have Maverick don't worry about the xorg 1.8 macros part, Maverick already has it.

---

### Post by jruh64 on 2010-12-27
OK I had to try that before going to bed and it seems to work!!
Favux, you rock!! Thank you!!
I haven't played with it much yet but I was able to zoom the screen in and out in Chromium.  I couldn't use my finger to scroll up and down though.  maybe a way i can set this up?
will play with it more tomorrow.
Again, thanks a bunch.  Hope this works for others also.

John

---

### Post by jruh64 on 2010-12-27
Favux, 

The touchscreen is now working although I don't think I can get gestures to work (back, forward, scroll, copy, paste etc).

I now have a folder on my desktop called **xf86-input-wacom**.  Can I move this folder or will I need to keep it there?

Thanks, John

---

### Post by Favux on 2010-12-27
Hi John,

Yes you can move the xf86-input-wacom folder to where you want or even delete it.  I would probably keep it just in case.

The gestures you should have are single finger dbl tap for left click, two finger dbl tap (first finger down, second finger taps) for right click.  Pinch zoom and two finger horizontal and vertical scroll.

See the Touch & Gesture Tips near the bottom of the HOW TO.

It might help to set up a .xsetwacom.sh (a xsetwacom script) that runs at start up.  You can then try slowly varying parameters once you get used to your tablet's feel.  You can probably use the X200 .xsetwacom.sh example in the tablet pc tar attached to the bottom of the second post.  You can get rid of the single finger touch section.  The Thinkpads are also serial Wacom so it should be close to what you need.  Just remember to use your "Device names" (in quotes) in the commands that 'xinput --list' returns for you.

---

### Post by jruh64 on 2010-12-27
OK I am getting used to the gestures and they are working pretty well.
The tablet buttons right below the screen don't do anything now but honestly I rarely used them when booted into Windows except to rotate the screen from landscape to portrait etc.  But I don't want to sound like I'm complaining, I am very happy to have the touch and pen working.
As far as setting up a script to run at startup, I am a little (or a lot) confused as how to do that.  Sorry I am an absolute novice.  Is this a file that I just get and place in some folder?

Thanks again, John

---

### Post by Favux on 2010-12-27
Right.  You download the tar.  Extract the tar by right clicking and saying extract here.  Rename the X200 whatever to .xsetwacom.sh by right clicking on it and chosing Rename.

The .sh means it's a script.  Drag it to your /home/username directory, top left in Places and drop it there and it'll show up in your /home/username/ directory.  The . in front of xsetwacom makes it a hidden file so to see it you would check Show Hidden Files in View in Places (which is really Nautilus).  Set it up to autostart by following the instructions in IV.

Your bezel buttons and rotation are suppose to be enabled by the fjbtndrv (fujitsu button driver).  See Robert Gerlach's PPA:  [https://launchpad.net/~khnz/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~khnz/+archive/ppa?field.series_filter=maverick)

---

### Post by jruh64 on 2010-12-27
OK I think I found the right file, downloaded and extracted it.  I now have (among others) a file called **Favux_Sample(12-17-10)_X200t&X201t_.xsetwacom.sh** .  Is this the file you are referring to?
I notice there is also one named "**....Fujitsu T4210..**"  Would that be close enough for my T4310?
So how do I run this script or set it to run it at startup?

Thanks for your patience and help.

John

---

### Post by Favux on 2010-12-27
Sure, not a problem.

Right the X200 one is the one I was thinking of because it has a multitouch section like you have.  But you can compare it to the Fujitsu one too.

---

### Post by Favux on 2010-12-27
Sure, not a problem.

Right the X200 one is the one I was thinking of because it has a multitouch section like you have.  But you can compare it to the Fujitsu one too.

Look in part IV. of the HOW TO for instructions.

---

### Post by jruh64 on 2010-12-27
I got everything set up now and it all works well.  I did use the X200 one as you recommended.  Will leave it as is for now but might try tweaking it in future if i feel brave enough.
Also got the buttons working, thanks for directing me.
Very happy with everything right now, thank you!!

John

---

### Post by Favux on 2010-12-27
Nice job John!  You absorbed a lot in a short time.

---

### Post by limotux on 2010-12-31
Hi,

First of all Happy New Year to all.

I've been so busy over the past few days but I was following you.
Today I tried to mimic what you did to get my the tablet working. (Fujitsu T4310).
I have only the pen working, nothing more. I felt a bit confused and was not able to reach the results you got.

I found this link [http://blog.brettalton.com/2010/08/28/how-to-install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx/](http://blog.brettalton.com/2010/08/28/how-to-install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx/)
and tried mindlessly to do (from the updated link [http://blog.brettalton.com/2010/08/28/install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx-using-ppas-tutorialhowto/:](http://blog.brettalton.com/2010/08/28/install-the-wacom-bamboo-driver-in-ubuntu-10-04-lucid-lynx-using-ppas-tutorialhowto/:)
  "
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms xf86-input-wacom
 "
and I got:
sudo apt-get install wacom-dkms xf86-input-wacom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xf86-input-wacom
 
Any ideas?

I think adding a repo that has xf86-input-wacom would do. Am I right?

---

### Post by limotux on 2010-12-31
... and now I'm getting this error:

' E: fsc-btns-kernel-source: subprocess installed post-installation script returned error exit status 1
E: fscrotd: dependency problems - leaving unconfigured
E: fscd: dependency problems - leaving unconfigured
E: fjbtndrv: dependency problems - leaving unconfigured

Any ideas?

---

### Post by Favux on 2010-12-31
Hi limotuxm,

What dkms means is dynamic kernel module support:  [http://linux.die.net/man/8/dkms](http://linux.die.net/man/8/dkms)  That means you would no longer need to compile the wacom.ko usb kernel module for each kernel update, it would be done for you.  However you have a serial Wacom digitizer in-built in your tablet, not a usb digitizer.  So it is irrelevant to you.  Besides the last time I looked DoctorMo's repository was using an outdated version of linuxwacom for the wacom.ko.

Of more concern to you is:
> E: Couldn't find package xf86-input-wacom
Because that is the new Wacom X driver and both serial and usb tablets need that.  I'm guessing the PPA is referencing an older xf86-input-wacom which is no longer posted at the LWP site.
> I think adding a repo that has xf86-input-wacom would do. Am I right? 
Exactly.  You need the latest one, 0.10.10+.  I don't know of a repo that has it which is why I linked you to part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or section 2 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Any other errors with the fjbtndrv PPA?  Describing the missing dependencies?

---

### Post by limotux on 2010-12-31
Thanks a lot Favux and I wish you the happiest ever new year.
I'm not sure I fully understand what is posted on the links you mentioned, never handled such stuff!

Well, I posted the errors that appeared to me, (maybe there are some others, but I think these are the most related.)

I hope you can help me get things working.

Any info, tests, outputs ... etc. you need just tell me...

---

### Post by Favux on 2010-12-31
It looks scary but isn't so bad once you dive into it.

If touch isn't working the first thing you need to do is update the X driver xf86-input-wacom.  You can do that following part II. of the Bamboo P & T HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

You open up a terminal and copy & paste each command in line by line and hit enter after each command.  Ask if you have questions.

---

### Post by limotux on 2010-12-31
Thanks Favux, doing 
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev libncurses5-dev

gave me:
apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fsc-btns-kernel-source (2.2.0.3-real2.2-2~lucid) ...

------------------------------
Deleting module version: 2.2.0.3
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/fsc_btns/2.2.0.3/source ->
                 /usr/src/fsc_btns-2.2.0.3

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.32-21-generic cannot be found at
/lib/modules/2.6.32-21-generic/build or /lib/modules/2.6.32-21-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
dpkg: error processing fsc-btns-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of fscrotd:
 fscrotd depends on fsc-btns-kernel-source; however:
  Package fsc-btns-kernel-source is not configured yet.
dpkg: error processing fscrotd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fscd:
 fscd depends on fsc-btns-kernel-source; however:
  Package fsc-btns-kernel-source is not configured yet.
dpkg: error processing fscd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fjbtndrv:
 fjbtndrv depends on fsc-btns-kernel-source; however:
  Package fsc-btNo apport report written because the error message indicates its a followup error from a previous failure.
                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                    No apport report written because MaxReports is reached already
                                                  ns-kernel-source is not configured yet.
 fjbtndrv depends on fscrotd; however:
  Package fscrotd is not configured yet.
 fjbtndrv depends on fscd; however:
  Package fscd is not configured yet.
dpkg: error processing fjbtndrv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fsc-btns-kernel-source
 fscrotd
 fscd
 fjbtndrv
E: Sub-process /usr/bin/dpkg returned an error code (1)

Why is this?

Now, what to do?

p.s.:  I'm online now for some time... I hope we can do something about tablet now.
p.p.s: currently upgrading to linux-image-2.6.32.27-generic

upgrade done

---

### Post by limotux on 2010-12-31
wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2)
suceeded with no errors
I'll carry on and keep you posted

---

### Post by limotux on 2010-12-31
Well, now I finished until the end of part II, but I'm not sure I'm understanding what to do next?!:(

Still touch not working. Only pen.

I hope you can help me that till now everything is ok so not to proceed while something is wrong. I'll be waiting for your advice so not to mess things up.

Thanks a lot.

P.S. Not only the pen, the buton that changes screen orientation, and screen orientation when flipping the screen to tablet mode are working.

BUT the  pen  moves in the opposit direction (did not rotate with the screen) and have bad calibration, before calibration was better.
please help

---

### Post by Favux on 2010-12-31
Sorry, a storm knocked out my ISP for a few hours.

Good.  Any problems with part II.?

Let's see what the output in a terminal of:
```
xinput --list
```
shows us.

---

### Post by limotux on 2011-01-01
Hi Favux, I hope everything is ok. The weather has gone crazy allover the world.

Here is the output
```

 xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; cursor                                    id=6    [slave  pointer  (2)]
&#9116;   &#8627; stylus                                    id=7    [slave  pointer  (2)]
&#9116;   &#8627; eraser                                    id=8    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=18   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=19   [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                        id=20   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=10   [slave  keyboard (3)]
    &#8627; Video Bus                                 id=11   [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=12   [slave  keyboard (3)]
    &#8627; Power Button                              id=13   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=14   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=15   [slave  keyboard (3)]
    &#8627; fsc tablet buttons                        id=16   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=17   [slave  keyboard (3)]


```

What next?

---

### Post by Favux on 2011-01-01
Alright, we're not seeing touch in it.  But we are seeing cursor.  Which suggests you are configuring your digitizer through xorg.conf.  You don't need to do that in Maverick (or Lucid).  You are in one of them right?  Which one?

Let's look at what you have in the xorg.conf (/etc/X11).  In X servers 1.7 (Lucid) and up, while you can use xorg.conf, you are "suppose" to use the wacom.conf in xorg.conf.d.  It will have a different # in front and location depending on which release you are using.

---

### Post by limotux on 2011-01-01
I'm on Lucid, the file xorg.conf has the following

```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
     # TabletPC Pen Device
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri2"
        Load  "glx"
        Load  "dri"
        Load  "record"
        Load  "dbe"
        Load    "wacom"                 # added
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
#### ADDED ####
# These lines should go after the detected mouse and touchpad
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
        Option          "button2"       "3"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
        Option          "Button1"       "2"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
##### added end #####
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by Favux on 2011-01-01
OK, the 10-wacom.conf will be at /usr/lib/X11/xorg.conf.d/ and we need to look at it if you want to use it.

If you want to use the xorg.conf you'll need to change the cursor section to touch.  The cursor is the wacom tablet mouse which you don't have.  So the cursor section becomes:
```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "touch"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "touch"
        Option          "Mode"          "absolute"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection

```
and the "ServerLayout" line becomes:
```
        InputDevice     "touch"
```
Also note "SendCoreEvents" is deprecated starting with X server 1.7 (Lucid) and up.  So you can remove it from stylus and eraser too.

You'd also need to disable the wacom.conf if there is a serial snippet picking up your digitizer.

---

### Post by limotux on 2011-01-02
mmm... sorry for my ignorance!:confused:

I don't know what I should decide, or what are the differences between using 10-wacom.conf or using xorg.conf

All what I can say is that I have Fujitsu T4310, running Lucid, and using the pen that came with it.
I'm after using the full tablet features, including the eraser at the other end of the pen, using the buttons on the screen, having the pen to rotate with the screen... normal and full tablet use including touch and/or multitouch and gestures.

So, I don't know the difference, what do you think I should select? Which has better or more precise calibration?
Asking this is mainly for learning more, I would have simply selected one solution randomly and that's it.
Again, sorry for my ignorance. I never dealt with a tablet before.

**p.s.: The mouse rotates properly with the screen but not the pen.**

---

### Post by Favux on 2011-01-02
The idea of going to the .conf files was to enable usb hotplugging.  Since a serial digitizer doesn't hotplug it shouldn't matter to you.  I guess the "proper" thing now is the wacom.conf instead of the xorg.conf.  You can think of the .conf files in xorg.conf.d as extensions of the xorg.conf, sort of.

---

### Post by limotux on 2011-01-02
Thanks a lot for your help Favux.
I'll try your recommendations and keep you posted, but in a few hours, I have to go now.

---

### Post by limotux on 2011-01-02
Thanks a lot Favux,


Allow me to repeat what you said in my own words to be sure I understand what you said. I care about learning more than just getting my problem solved.

I understand that:
1- The tablet hardware in the Fujitsu 4310 is Wacom brand, and it is a serial device.
2- Serial device are ... mmm something like "always on" does not need activation or mounting as USB devices do (like mounting the external USB  hard disk)
3- The file 10-wacom.conf is the file that contains the hardware configuration of the tablet, let the computer now what devices are there and where are their drivers... etc.

Am I understanding properly?
What I understand now is that I should edit 10-wacom.conf to include the  code in the two boxes above. Am I right? (just want to be sure before  doing something silly)

The original 10-wacom.conf contains only the following:
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection


```I don't see in 10-wacom.conf something simillar to the code in the first box, so I should add it?
What and where is "ServerLayout" that you mentioned? Should I add the code as well to the same file?

Thank you for your patience and sorry for asking too much.

---

### Post by Favux on 2011-01-02
Hi limotux,

You have it correct except the code is for the xorg.conf, not the wacom.conf.  Since you are going with the wacom.conf instead of the xorg.conf you should comment out (#) all the Wacom sections and the Wacom lines in "ServerLayout".

Your 10-wacom.conf is an early one and lacks the serial snippet for Fujitsu tablets:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
EndSection

```
Add it in like so:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection
```
To edit it you can use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```

---

### Post by limotux on 2011-01-02
Hi Favux, It seems that I... did it again! ooops... sorry. Seems to me that I misunderstood and really messed things up and couldn't boot my laptop. But fortunately I could boot live cd and revert to the old settings.

Now, here is my current working xorg.conf, then my current working 10-wacom.conf.
The xorg.conf
```


Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
     # TabletPC Pen Device
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri2"
        Load  "glx"
        Load  "dri"
        Load  "record"
        Load  "dbe"
        Load    "wacom"                 # added
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
#### ADDED ####
# These lines should go after the detected mouse and touchpad
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
        Option          "button2"       "3"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
        Option          "Button1"       "2"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
##### added end #####
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```The 10-wacom.conf

```



Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
    Identifier "Wacom serial class identifiers"
    MatchProduct "WACf|FUJ02e5|FUJ02e7"
    Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```Well, I hope you can do the required modification in both and post them so I'll just copy and paste to get tablet working.

I'm sorry for not understanding you properly, I know it is my problem. May be because I'm so busy with lots of things and exhausted.

I'll highly appreciate your help.
After getting things to work, allow me to bother you with few questions to be sure I understand the subject properly.

---

### Post by Favux on 2011-01-02
Good escape.  You should always back up working .conf files if you are making changes to them so you can restore them from the command line if you break X or whatever.  Of course a live CD works too.  :)

Your 10-wacom.conf looks correct now.

You should now comment out the Wacom entries in your xorg.conf like so:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
     # TabletPC Pen Device
#        InputDevice     "cursor"        "SendCoreEvents"
#        InputDevice     "stylus"        "SendCoreEvents"
#        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri2"
        Load  "glx"
        Load  "dri"
        Load  "record"
        Load  "dbe"
        Load    "wacom"                 # added
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
#### ADDED ####
# These lines should go after the detected mouse and touchpad
#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "cursor"
#        Option          "Device"        "/dev/ttyS0"
#        Option          "ForceDevice"   "ISDV4"
#        Option          "Type"          "cursor"
#        Option          "Mode"          "absolute"
#        Option          "Speed"         "3.0"
#        Option          "Threshold"     "2"
##       Option          "DebugLevel"    "10"
##       Option          "MaxX"          "24576"
##       Option          "MaxY"          "18432"
#EndSection
#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "stylus"
#        Option          "Device"        "/dev/ttyS0"
#        Option          "ForceDevice"   "ISDV4"
#        Option          "Type"          "stylus"
#        Option          "Mode"          "absolute"
#        Option          "button2"       "3"
##       Option          "Tilt"          "on"
##       Option          "TiltInvert"    "on"
#        Option          "Threshold"     "2"
##       Option          "DebugLevel"    "10"
#EndSection
#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "eraser"
#        Option          "Device"        "/dev/ttyS0"
#        Option          "ForceDevice"   "ISDV4"
#        Option          "Type"          "eraser"
#        Option          "Mode"          "absolute"
#        Option          "Button1"       "2"
##       Option          "Tilt"          "on"
##       Option          "TiltInvert"    "on"
#        Option          "Threshold"     "2"
##       Option          "DebugLevel"    "10"
#EndSection
##### added end #####

etc.
```
And reboot.

By the way for future thought it is unlikely you need the keyboard and mouse sections and their "ServerLayout" lines either.

---

### Post by limotux on 2011-01-03
:confused:

I don't understand why me?
I left everything as is. 

I just copied the code in the second box above from top till "#### added End..."
On rebooting it didn't as before, I got an error message something like "unknown user id"

Again, I reverted to the original xorg.conf through live cd.

What am I missing?
I know I might be asking way too much but, would you please do the file for me and post it back so I'd just copy and paste it in the xorg.conf ? Please. Maybe this way I'll compare what works and what doesn't.

I feel sorry about myself!

here is my currently working xorg.conf (in folder /etc/X11) :
```


Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
     # TabletPC Pen Device
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri2"
        Load  "glx"
        Load  "dri"
        Load  "record"
        Load  "dbe"
        Load    "wacom"                 # added
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
#### ADDED ####
# These lines should go after the detected mouse and touchpad
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
        Option          "button2"       "3"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
        Option          "Button1"       "2"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
##### added end #####
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

---

### Post by Favux on 2011-01-03
Hi limotux,

I just commented out the Wacom stuff.  So I didn't do the whole xorg.conf in the box above.  Just enough to show what needed to be commented out.  So my example left out your video sections.

In the attached xorg.conf I have removed all of the Wacom stuff.  I also removed the keyboard and mouse stuff.  It looks like there is other stuff that can be removed, but I figured this is enough editing for now.  The xorg.conf should work.  Just completely replace your current one with it (copy and paste).  After backing up your current one of course.

---

### Post by limotux on 2011-01-03
WOW... :guitar: =D>

[CENTER][SIZE=6][COLOR=Blue]Fauvux, The Tablet Master
[/COLOR][/SIZE][/CENTER]

That's great... thanks a lot Favux.
Now, touch works and pen as well. Working properly only when screen is in landscape mode  as a tablet or as laptop.

When in portrait position, pen and touch are pointing somewhere else and moving the opposite direction! As if the screen coordinates rotated but they dont rotate with it.

Also it does not seem I have gestures. A long press with finger or pen does not give the sub menus expected. The right and left click buttons on the pen don't seem to work. (only right click submenu when the pen physically touches the screen), I saw it working before when on short distance from screen.
The screen senses the pen from a little distance and only moves the cursor, nothing more.

What to do?

P.S. what software to calibrate both touch and pen?
PPS how to slow down virtual keyboard as it repeats buttons so quickly

---

### Post by Favux on 2011-01-03
Good!  Nice progress.

Those are two separate issues.  How are you rotating now?  Are you using a rotation script?  If so can I see it?

For gestures, etc. we should probably set you up with a xsetwacom start up script like jruh64.  Do you want to take a look at those posts first?

---

### Post by limotux on 2011-01-03
Dear Favux,

It's you really who made the progress.

Well, the screen rotates automatically when I flip the screen, or press a button on the frame of the screen.

AFAIK, I didn't try or download any scripts myself.
I'll be looking now at the previous posts and hopefuly understand. But still I'll appreciate if you can tell me what to do.

---

### Post by limotux on 2011-01-03
Favux, a little gift for you, I hope you will find it interesting... [here]("http://2leep.com/news/1885/1227/")

---

### Post by Favux on 2011-01-03
> Well, the screen rotates automatically when I flip the screen, or press a button on the frame of the screen.

AFAIK, I didn't try or download any scripts myself.
Didn't you install the fjbtndrv through the PPA?  In addition to "activating" your bezel buttons that should be what's giving you the automatic rotation.  It should also be rotating your stylus and touch for you.

---

### Post by limotux on 2011-01-03
> **Favux said:**
> Hi John,

Yes you can move the xf86-input-wacom folder to where you want or even delete it.  I would probably keep it just in case.

The gestures you should have are single finger dbl tap for left click, two finger dbl tap (first finger down, second finger taps) for right click.  Pinch zoom and two finger horizontal and vertical scroll.

See the Touch & Gesture Tips near the bottom of the HOW TO.

It might help to set up a .xsetwacom.sh (a xsetwacom script) that runs at start up.  You can then try slowly varying parameters once you get used to your tablet's feel.  You can probably use the X200 .xsetwacom.sh example in the tablet pc tar attached to the bottom of the second post.  You can get rid of the single finger touch section.  The Thinkpads are also serial Wacom so it should be close to what you need.  Just remember to use your "Device names" (in quotes) in the commands that 'xinput --list' returns for you.

This seems to work:guitar::guitar:

What about orientation of pen and touch with screen?
I'm still reading the whole thread , Hope I'll be smarter this time.

---

### Post by limotux on 2011-01-03
Ok Favux, I understand I should implement from post #19 in this thread.

To be sure and safe before messing things up, this would fix the problem of the touch and pen not rotating with the screen?

You mean  this file [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/) ?
I remember fjbtndrv is already installed!

OMG... I feel terrible for not being able to learn easily, it might be age related... honestly.
Sorry I'm causing you lot's of headache.

---

### Post by Favux on 2011-01-03
Gerlach's PPA with the fjbtndrv should fix rotation for you.  Do that first and let's get that working before moving on to the xsetwacom script.

---

### Post by limotux on 2011-01-03
> **Favux said:**
> Didn't you install the fjbtndrv through the PPA?  In addition to "activating" your bezel buttons that should be what's giving you the automatic rotation.  It should also be rotating your stylus and touch for you.

Yes I did, but I don't know why pen and touch don't rotate. They only work properly in landscape direction.!!!

---

### Post by Favux on 2011-01-03
Well did you just install it?  Or did you do it a while ago?  If it was a while ago try reinstalling it and making sure it's the version for your release.

We can also look at the output of your:
```
xinput --list
```

---

### Post by limotux on 2011-01-03
Here is the result
```



&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                        id=12   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=16   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                 id=17   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=18   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=19   [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=20   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=9    [slave  keyboard (3)]
    &#8627; Power Button                              id=10   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=11   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=13   [slave  keyboard (3)]
    &#8627; fsc tablet buttons                        id=14   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=15   [slave  keyboard (3)]


```

I installed it like 2 days ago while with you here (my earler posts when it gave me problems then succedde to install... remember? [here]("http://ubuntuforums.org/showpost.php?p=10299976&postcount=26") and later)

---

### Post by Favux on 2011-01-03
That's what I though.  Maybe it didn't install right.  I don't think anything is wrong with the Maverick update.  I think folks, once it is installed, report it working.

Let's look at the output of these two commands:
```
xinput list-props "Serial Wacom Tablet stylus"
&
xinput list-props "Serial Wacom Tablet touch"
```

---

### Post by limotux on 2011-01-03
Please note I'm on Lucid, KDE...

```


Device 'Serial Wacom Tablet stylus':
        Device Enabled (125):   1
        Device Accel Profile (242):     0
        Device Accel Constant Deceleration (243):       1.000000
        Device Accel Adaptive Deceleration (245):       1.000000
        Device Accel Velocity Scaling (246):    10.000000
        Wacom Tablet Area (266):        0, 0, 26312, 16520
        Wacom Rotation (267):   0
        Wacom Pressurecurve (268):      0, 0, 100, 100
        Wacom Serial IDs (269): 227, 0, 2, 0
        Wacom Display Options (270):    -1, 0, 1
        Wacom Capacity (271):   -1
        Wacom Pressure Threshold (272): 27
        Wacom Sample and Suppress (273):        2, 4
        Wacom Enable Touch (274):       1
        Wacom Hover Click (275):        1
        Wacom Enable Touch Gesture (276):       1
        Wacom Touch Gesture Parameters (277):   50, 20, 250
        Wacom Tool Type (278):  "STYLUS" (282)
        Wacom Button Actions (279):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (280):       0, 0



```and

```


Device 'Serial Wacom Tablet touch':
        Device Enabled (125):   1
        Device Accel Profile (242):     0
        Device Accel Constant Deceleration (243):       1.000000
        Device Accel Adaptive Deceleration (245):       1.000000
        Device Accel Velocity Scaling (246):    10.000000
        Wacom Tablet Area (266):        0, 0, 2631, 1652
        Wacom Rotation (267):   0
        Wacom Serial IDs (269): 227, 0, 3, 0
        Wacom Display Options (270):    -1, 0, 1
        Wacom Capacity (271):   -1
        Wacom Pressure Threshold (272): 27
        Wacom Sample and Suppress (273):        2, 4
        Wacom Enable Touch (274):       1
        Wacom Hover Click (275):        1
        Wacom Enable Touch Gesture (276):       1
        Wacom Touch Gesture Parameters (277):   50, 20, 250
        Wacom Tool Type (278):  "TOUCH" (281)
        Wacom Button Actions (279):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (280):       0, 0



```

---

### Post by Favux on 2011-01-03
> I'm on Lucid, KDE
Thanks for reminding me.

As you can see from the list-props the devices are on the Wacom driver.  So that isn't the problem.

Did you also update the default xf86-input-wacom?

You can look at my [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 & 3 should work for you.  But mainly I'm thinking you could just run the rotation xsetwacom commands and verify that xsetwacom works for you.

Actually Tom Jaeger's method (3) might be best because apparently fjbtndrv is already rotating the screen orientation for you.

---

### Post by limotux on 2011-01-04
Thankx a lot Favux,

I found that default xf86-input-wacom is not installed!
I searched and found [this]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom")

I did ```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
cd xf86-input-wacom
./autogen.sh --prefix=/usr
make && make install

```But the last command
```

make && make install 
```gave an error as follows
```

make  all-recursive
make[1]: Entering directory `/home/limo/xf86-input-wacom'
Making all in conf
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
Making all in src
make[2]: Entering directory `/home/limo/xf86-input-wacom/src'
  CC     xf86Wacom.lo
  CC     wcmCommon.lo
  CC     wcmConfig.lo
wcmConfig.c: In function &#8216;NewWcmPreInit&#8217;:
wcmConfig.c:515: warning: implicit declaration of function &#8216;asprintf&#8217;
wcmConfig.c:515: warning: nested extern declaration of &#8216;asprintf&#8217;
  CC     wcmISDV4.lo
wcmISDV4.c: In function &#8216;isdv4ProbeKeys&#8217;:
wcmISDV4.c:910: warning: format not a string literal, argument types not checked
wcmISDV4.c:928: warning: format not a string literal, argument types not checked
  CC     wcmFilter.lo
  CC     wcmUSB.lo
  CC     wcmXCommand.lo
  CC     wcmValidateDevice.lo
wcmValidateDevice.c: In function &#8216;wcmOptionDupConvert&#8217;:
wcmValidateDevice.c:320: warning: implicit declaration of function &#8216;asprintf&#8217;
wcmValidateDevice.c:320: warning: nested extern declaration of &#8216;asprintf&#8217;
  CC     wcmTouchFilter.lo
  CCLD   wacom_drv.la
make[2]: Leaving directory `/home/limo/xf86-input-wacom/src'
Making all in man
make[2]: Entering directory `/home/limo/xf86-input-wacom/man'
  GEN    wacom.4
  GEN    xsetwacom.1
make[2]: Leaving directory `/home/limo/xf86-input-wacom/man'
Making all in include
make[2]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/include'
Making all in tools
make[2]: Entering directory `/home/limo/xf86-input-wacom/tools'
  CC     xsetwacom.o
  CCLD   xsetwacom
  CC     isdv4-serial-debugger.o
  CCLD   isdv4-serial-debugger
make[2]: Leaving directory `/home/limo/xf86-input-wacom/tools'
make[2]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Leaving directory `/home/limo/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/xf86-input-wacom'
Making install in conf
make[1]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `install-exec-am'.
test -z "" || /bin/mkdir -p ""
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
/usr/bin/install: cannot remove `/usr/share/hal/fdi/policy/20thirdparty/wacom.fdi': Permission denied
make[2]: *** [install-dist_fdiDATA] Error 1
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/limo/xf86-input-wacom/conf'
**make: *** [install-recursive] Error 1**

```What does that mean? What to do?

---

### Post by Favux on 2011-01-04
That's what part II. "Install Xorg's 0.10.10+ xf86-input-wacom for Lucid (the X driver)" of the Bamboo HOW TO does, it installs the latest version of xf86-input-wacom which is 0.10-10+:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

The default xf86-input-wacom in Lucid is the 0.10-5 version.  It lacks some fixes for Fujitsu tablet pc's and some xsetwacom features and fixes.

---

### Post by limotux on 2011-01-04
> **Favux said:**
> Thanks for reminding me.

As you can see from the list-props the devices are on the Wacom driver.  So that isn't the problem.

Did you also update the default xf86-input-wacom?

You can look at my [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 & 3 should work for you.  But mainly I'm thinking you could just run the rotation xsetwacom commands and verify that xsetwacom works for you.

Actually Tom Jaeger's method (3) might be best because apparently fjbtndrv is already rotating the screen orientation for you.

Thanks Favux for your patience.

Because I installed the buggy xf86-input-wacom, I repeated step II and reinstalled.

Now, I want to be accurate and precise so I won't bother you that much.
You gave me some options, but... mmm... I don't want to decide by myself.
Please tell me a specific detailed thing to do..

---

### Post by limotux on 2011-01-04
OK... trying still to learn... regarding Tom Jaeger's method 3, it says "You need to download Tom Jaeger's  deb package that contains his C script. The script automatically senses  your screen orientation and flips the stylus, eraser, and touch to  match. To download go to **[Tom's repository]("http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/")** and get “wacomrotate_0.3.1_jaunty_amd64.deb” dated 4-13-10 for Lucid"

But my Fujitsu T4310 is not AMD64, it is Intel cor 2 duo, and I'm running the 32 bit version of Lucid.

So, please be patient with me and tell me detailed steps. I don't want to keep messing things up.

---

### Post by Favux on 2011-01-04
Alright, I take it the fresh install of 0.10.10 didn't fix the rotation problem.

You'd want the 0.3.1-0 i386.deb dated 9-15-10.  Just download the deb and dbl click on it and it will install itself.

---

### Post by limotux on 2011-01-04
this  oone [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/wacomrotate_0.3.1-0thjaeger1_i386.debv](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/wacomrotate_0.3.1-0thjaeger1_i386.debv)  ?/

---

### Post by Favux on 2011-01-04
Yes.  Besides a .deb (debian) package won't install if it is the wrong architecture.

By the way you can use Synaptic Package Manager to see what packages are installed.  However one you've compiled won't show up because it doesn't register itself with the Package Manager.  A .deb will register itself.

---

### Post by limotux on 2011-01-04
> **limotux said:**
> this  oone [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/wacomrotate_0.3.1-0thjaeger1_i386.debv](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/wacomrotate_0.3.1-0thjaeger1_i386.debv)  ?/

ok done... will test and tell you the results

update: still touch and pen don't rotate

---

### Post by limotux on 2011-01-04
I've been reading about this issue. It appears to me that what works for someone, doesn't necessary work for the other! I've seen several posts that gave me this impression. Tough it seems illogical.

---

### Post by jruh64 on 2011-01-04
Hi Favux, Limotux,
 
Belated Happy New Years!
 
I have still been following this thread but was hesitant to post because I don't want to complicate things.
 
I believe Limotux and I are both in the same boat right now (except I am on Maverick).   I originally though I had everything working but I have discovered that I also have the same or similar issue with screen rotation.  The pen and touch are working correctly in both landscape orientations but are 180 degrees out of sync in both portrait orientations (move the pen or touch down=pointer goes up, move pen right=pointer goes left, and vice versa).
 
This morning I downloaded the "[wacomrotate_0.3.1_i386.deb]("http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/wacomrotate_0.3.1_i386.deb")" file from Tom Jaeger and installed it (I right clicked on the file and selected "install through Ububtu Software Centre"). I assume that's all I needed to do to install it.  I then rebooted to be sure but unfortunately the screen rotation issue remains unchanged.
 
Let me know what I can do to help us all resolve this. Favux, I can't thank you enough for the help you've already provided.
 
Thanks, John

---

### Post by limotux on 2011-01-04
Hi jruh64, Many Happy New Years.

Thank you for your post. I was so dissapointed and angry with myself that I am not understanding properly and causing headaches to Favux.

There seems to be an issue somewhere, but I believe Favux is capable of sorting it out unless it is a bug somwhere that needs attention.

Actually I was thinking that after getting things working properly I'd try to do an algorithm so to write a script or create a deb to install and automatically gets things working for tablets with simillar hardware. But till now we are not done yet.

I hope we  can sort it out.

I'll keep researching and trying and will post the results if any.

---

### Post by Favux on 2011-01-04
Alright, it is affecting both of you.  If there is a bug in fjbtndrv affecting wacom devices but not screen orientation I would have thought wacomrotate would fix that.

We need to do some diagnostics.  First make sure you're both actually on the wacom driver.  To confirming that look at your Xorg.0.log in /var/log.  If you open it in gedit you can look at your digitizer initializing by using Find and searching 'wacom'.

Let's look at the output in a terminal of:
```
lspci | grep VGA
```
This will tell us what video card/chipset you have.  Are you using a proprietary video driver for it?
```
xrandr -q --verbose
```
This will tell us if a method 1 script will work.
```
xinput --list
```
This will verify what "Device names" to use in the script.

---

### Post by jruh64 on 2011-01-04
ok here is part of my 'Xorg.0.log' that references anything wacom:

```
[    16.565] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    16.565] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    16.565] (II) LoadModule: "wacom"
[    16.565] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    16.565] (II) Module wacom: vendor="X.Org Foundation"
[    16.565] 	compiled for 1.9.0, module version = 0.10.10
[    16.565] 	Module class: X.Org XInput Driver
[    16.565] 	ABI class: X.Org XInput driver, version 11.0
[    16.565] (**) Option "Device" "/dev/ttyS0"
[    16.566] (**) Option "StopBits" "1"
[    16.566] (**) Option "DataBits" "8"
[    16.566] (**) Option "Parity" "None"
[    16.566] (**) Option "Vmin" "1"
[    16.566] (**) Option "Vtime" "10"
[    16.566] (**) Option "FlowControl" "Xoff"
[    16.566] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    16.566] (II) Serial Wacom Tablet: other types will be automatically added.
[    16.566] (**) Serial Wacom Tablet stylus: always reports core events
[    17.080] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    17.080] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    17.080] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=2631 maxY=1652 resX=10 resY=10 
[    17.080] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    17.080] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    17.080] (**) Option "Device" "/dev/ttyS0"
[    17.080] (**) Option "BaudRate" "38400"
[    17.080] (**) Option "StopBits" "1"
[    17.080] (**) Option "DataBits" "8"
[    17.080] (**) Option "Parity" "None"
[    17.080] (**) Option "Vmin" "1"
[    17.080] (**) Option "Vtime" "10"
[    17.080] (**) Option "FlowControl" "Xoff"
[    17.080] (**) Serial Wacom Tablet eraser: always reports core events
[    17.080] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=2631 maxY=1652 resX=10 resY=10 
[    17.080] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[    17.080] (--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=2540 resol Y=2540
[    17.080] (**) Option "BaudRate" "38400"
[    17.081] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[    17.081] (**) Option "Device" "/dev/ttyS0"
[    17.081] (**) Option "BaudRate" "38400"
[    17.081] (**) Option "StopBits" "1"
[    17.081] (**) Option "DataBits" "8"
[    17.081] (**) Option "Parity" "None"
[    17.081] (**) Option "Vmin" "1"
[    17.081] (**) Option "Vtime" "10"
[    17.081] (**) Option "FlowControl" "Xoff"
[    17.081] (**) Serial Wacom Tablet touch: always reports core events
[    17.081] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=2631 maxY=1652 resX=10 resY=10 
[    17.081] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
[    17.081] (--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=2631 bottom Y=1652 resol X=10 resol Y=10
[    17.081] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    17.081] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
[    17.081] (--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=2540 resol Y=2540
```

I assume this confirms that I am on the Wacom driver?

Here is out put of **lspci | grep VGA** :

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


And output of **xrandr -q --verbose**:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x41
	Timestamp:  10206201
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1280x800+0+0 (0x46) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x42
	Timestamp:  10206201
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	BACKLIGHT: 3 (0x00000003)	range:  (0,11)
	Backlight: 3 (0x00000003)	range:  (0,11)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
  1280x800 (0x46)   71.1MHz -HSync -VSync *current +preferred
        h: width  1280 start 1304 end 1336 total 1440 skew    0 clock   49.4KHz
        v: height  800 start  803 end  809 total  823           clock   60.0Hz
  1024x768 (0x47)   94.5MHz +HSync +VSync
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x48)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x49)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x4a)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x4b)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x4c)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x4d)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x4e)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4f)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x50)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x51)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x52)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x53)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x55)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x56)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x57)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x43
	Timestamp:  10206201
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x44
	Timestamp:  10206201
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
DP2 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x45
	Timestamp:  10206201
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
```

and also output of **xinput --list**

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=18	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=19	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                         	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=11	[slave  keyboard (3)]
    &#8627; FJ Camera                               	id=13	[slave  keyboard (3)]
    &#8627; fsc tablet buttons                      	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

```

Thanks again, John

---

### Post by Favux on 2011-01-04
Hi John,

Happy New Year.

Is that all there is to the video line?

The Xorg.0.log does seem to confirm you're on the wacom driver.  That's what the lines like:
```
[    17.081] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)

```
indicate.

The xrandr output says you should be able to use a method 1 script in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Use the right hand one to simplify things.  Where the script has, for example:
```
xsetwacom set stylus rotate  CW 

```
change both stylus lines to read:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate  CW 

```
And similar with the eraser and touch lines.  Remember the xsetwacom commands will work in a terminal too as individual commands.

---

### Post by jruh64 on 2011-01-04
Favux that's all that came out of the video line, I tried it a 2nd time to verify. I am fairly certain that I never installed any proprietary drivers for video though. 'System > Administration > Additional Drivers' states that there are no proprietary drivers in use on this system.

 I will read through and try to follow the Rotation HOW TO.  What is the difference between right and left handed script? ( I am left handed)

Thanks, John

---

### Post by Favux on 2011-01-04
If your battery protrudes it provides a handle to hold the tablet.  Since your left handed you might want the left hand script.

Usually the Intel chipsets give a number like 955, that's why I asked.  Your using the Open Source Intel drivers then, there aren't any proprietary ones like there are for Nvidia or ATI.  You probably don't have a xorg.conf either because it's not needed by the Intel video driver.

You can test the xsetwacom commands before you try a script.  I can help you with the script if you have trouble.

---

### Post by jruh64 on 2011-01-05
OK I tested those commands and found something odd:

the following:
```
xrandr -o left 
xsetwacom set "Serial Wacom Tablet stylus" rotate CCW
``` 
produces the same problem with wacom inputs a mirror image of what they should be.

So I tried:
```
xrandr -o left 
xsetwacom set "Serial Wacom Tablet stylus" rotate CW
``` 
works!! It seems rotating screen left needs wacom to rotate CW, rotating screen right requires wacom to rotate CCW. Oddly I didn't need to run the corresponding commands for touch and eraser.  they all rotated when i ran the command for stylus. (?)

So would I need to use the scripts from the Rotate HOW TO and just switch the CW and CCW lines?  Or is there something I can edit in the scripts, button drivers etc that is already on my system?

I'm feeling optimistic right now despite my ignorance. :-)

Thanks, John

---

### Post by Favux on 2011-01-05
Hi John,

Nice work!

That's interesting and rings a dim bell.  I think there was a point where xsetwacom reversed left and right.  But I thought that was a while ago and was fixed.  Your using xf86-input-wacom cloned from the git repository, correct?

It shouldn't work for all three unless another script of some kind is active.  You'd have to show me what script you installed, if you remember.  And wacomrotate would count as a script.

Just change CW for CCW for all 3 devices then and use the method 1 script.

---

### Post by jruh64 on 2011-01-05
I had to review our earlier posts to remember what we had done in past but yes I did clone the xf86-input-wacom from the git repository. I followed your instructions from the 'Bamboo P & T HOW TO'.  That was what got the touch working on my system.

I then copied **Favux_Sample(12-17-10)_X200t&X201t_.xsetwacom.sh** and renamed it to **.xsetwacom.sh** as my startup script.  It is as follows:
```
## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = "Serial Wacom Tablet stylus" = ID 19
xsetwacom set "Serial Wacom Tablet stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet stylus" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet stylus" PressCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet stylus" TPCButton "on"  # or is Relative needed for gestures?"  # stylus tip + button, or "off" for hover mode
xsetwacom set "Serial Wacom Tablet stylus" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet stylus" Button1 "1"  # left mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button2 "3"  # right mouse click
xsetwacom set "Serial Wacom Tm Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## eraser = "Serial Wacom Tablet eraser" = ID 17
xsetwacom set "Serial Wacom Tablet eraser" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet eraser" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet eraser" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet eraser" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet eraser" PressCurve "0 10 90 100" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet eraser" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet eraser" Button1 "1"
# coordinates are the same as uablet stylus" Button3 "2"  # middle mouse click
# sample X200t coordinates, default coordinates in /var/log/Xorg.0.log
#xsetwacom set "Serial Wacosed for the stylus
#xsetwacom set "Serial Wacom Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## depending on your model use the applicable following touch section ##
## I deleted the single finger touch section, jruh ##

## two finger (2FG) or multitouch
## touch = "Serial Wacom Tablet touch" = ID 18
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default,  or "off"
xsetwacom set "Serial Wacom Tablet touch" Gesture "on"  # or "off"
xsetwacom set "Serial Wacom Tablet touch" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet touch" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet touch" ClickForce  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet touch" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"  # or Relative cursor movement; is Relative needed for gestures? 
xsetwacom set "Serial Wacom Tablet touch" TapTime "250"  # default is 250 ms
xsetwacom set "Serial Wacom Tablet touch" Button1 "1"  #  needed for 2FG touch?
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 14 ZoomDistance "50"  # default is 50
xsetwacom set 14 ScrollDistance "2000"  # default is 20
xsetwacom set 14 TapTime "250"  # 2FG R click, default is 250 ms
# sample X200t coordinates
#xsetwacom set "Serial Wacom Tablet touch" topx "?"
#xsetwacom set "Serial Wacom Tablet touch" topy "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomx "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomy "?"

## Developed with vfrjim
```

There is also a file called **rotate-wacom.sh** located at /usr/lib/fjbtndrv and it is as follows:
```
#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
	n*) val=0 ;;
	r*) val=1 ;;
	l*) val=2 ;;
	i*) val=3 ;;
	*)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
	if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
		xinput set-prop "$dev" 'Wacom Rotation' $val
	fi
done

exit 0
```

I assume this one also runs at startup but I don't know how to tell.
I don't know of any other scripts that are running but there certainly could be.

So should I now set up the new scripts from method 1 script in the Rotation HOW TO ?  Or could I edit something in the scripts I already have? I am wondering what switching these 2 values would do:
```
r*) val=1 ;;
l*) val=2 ;;
```
(from the 'rotate-wacom.sh' script.) Is this script part of the fujitsu tablet button driver?

Will revisit this evening after work.

Thanks again, John

---

### Post by limotux on 2011-01-05
I'm  watching! Trying to figure out what's going on!
I feel that we'll celebrate tonight and have fireworks...:guitar:
But I'll wait till the end. (unfortunately I'm not left handed, and though my hardware is 64 bit I'm on Lucid 32 bits)

---

### Post by Favux on 2011-01-05
Hi John and limotux,

Nice detective work again John.

```
I am wondering what switching these 2 values would do:
```
That's exactly what I would try at this point.  That way you would end up with a rotation script already bound to your rotation button/swivel hinge switch without having to go through the steps to do that manually.

Plus you now know how to construct your own rotation script or modify the current one if needed again.

---

### Post by limotux on 2011-01-05
Hi Favux and John,

mmm... at this level I feel lost, but I think you are done... right?

If so, what about me?
I believe John is on a 64 bit Lucid, and is left handed, while I'm on 32 bit Lucid and right handed.

I don't want to try things by myself and complicate things for Favux.

What can I do Favux in my case? A bit by bit and in detail please.

---

### Post by jruh64 on 2011-01-05
Favux, I will try switching those values when I get home from work.  Hopefully it will solve this for both Limotux and me.
 
Limutux, I am on 32 bit maverick.  I think my system should be very similar to yours.
I think it should work regardless of left or right handed.
 
Either way, will also stick with this until we both get it resolved. WIll do what i can to help but i just barely understand what is going on myself.  We're very fortunate to have Favux to help us.
 
What is the status of your touch screen now?  I am thinking we are both at the same point: touch and stylus working properly except while screen is in portrait mode?
 
Thanks, John

---

### Post by limotux on 2011-01-05
Hi John, We are in the same situation.
Touch works as expected. Only stylus/pen and touch are pointing oposite direction in portrait mode.

Some other minor problems, (will check for a solution later), like... mmm... virtual keyboard repeats button touches really fast so it is unusable), touch calibration...)

I feel sorry I can't understand what's going on... never handled scripts.

But I really appreciate Favux help.

---

### Post by jruh64 on 2011-01-05
Success!!

I edited the file called rotate-wacom.sh and the wacom tablet now rotates correctly with the screen rotation.

Original code from this file:
```
case "$ORIENTATION" in
	n*) val=0 ;;
	r*) val=1 ;;
	l*) val=2 ;;
	i*) val=3 ;;
	*)  exit 1 ;;
```
I switched the 'r' and 'l' (right and left) to get:
```
case "$ORIENTATION" in
	n*) val=0 ;;
	l*) val=1 ;;
	r*) val=2 ;;
	i*) val=3 ;;
	*)  exit 1 ;;
```

I also tried switching the values '1' and '2' and it also works just as well, but I preferred to keep the numbers in order.

Limotux, I think you should also have this file. Mine is located at /usr/lib/fjbtndrv
If you have it you can easily make the change that I made (switch the 'l' and 'r') and likely you will also have proper tablet use in portrait mode.

Cheers, John

---

### Post by Favux on 2011-01-05
Congratulations John,

This is the first time I'm aware of that anyone has posted the rotation script fjbtndrv is implementing.  The first time I've seen it anyway.

---

### Post by limotux on 2011-01-06
WOW....:guitar::guitar::guitar:

You are two genius guys!

Thank you very much!

I changed the content of the .sh as John did and it worked even without rebooting.

You are great guys!

Now I can say I own a tablet for the first time!

I had a problem with the virtual keyboard xvkbd, it was a bit tiny but I resized it, it used to get focus but now fixed menu -> Advanced -> Special Window Settings -> Workaround.

Still have to find how to place it in the panel for easy access.

:guitar::guitar::guitar:

---

### Post by jruh64 on 2011-01-06
Hi Limotux, very glad you got it to work also!! I am no genius but I suspect Favux might be. :-) I certainly wouldn't have known where to start without his help.

I found there are other onscreen keyboards available from the Ubuntu Software Center.  I have one called **onboard** that you might also like better.

Cheers, John

---

### Post by limotux on 2011-01-06
Great :guitar: we now have Tablets!
As for handwriting, Xournal looks great but it had a funny problem. When I start it in an orientation and change it 90 degrees the stylus seems misaligned, it moves in the correct direction but far away from where the tip is, though the stylus still points at the application buttons and menus properly :confused:

I tried Jarnal and it works perfect. So it appears to me a bug in Xournal.
Initially I see Jarnal is really feature rich, I can say it is an app you need some time to discover and master all features.

I will give onboard a try and let you know how things are going.

I'll try to discover if it is possible to:
1- Get decent character recognition (in various languages including CTL, as hebrew, arabic, in addition to latin)
2- Use stylus inside several applications especially browsers to write emails, wordprocessor, spreadsheet... etc. with #1 included (sounds crazy or too ambitious?!)
3- Find a list of applications that can take stylus input (knotes, tomboy, text editor...)

I'll get back to you as soon as I find something new or interesting.

I should always thank you Favux for all your support, and thank you John, you did a great job.

---

### Post by Favux on 2011-01-06
Cool limotux,

You're set up!

The applications I find indispensable for a tablet pc are CellWriter, Xournal, and EasyStroke.  Can't count Magick Rotation yet because we only have it working for HP and Dell tablet pc's at this point.  ;)

CellWriter has letter recognition.  It switches between being an onscreen keyboard and the letter recognition function.  You can use it to input text into other applications with writing along with the keyboard.

EasyStroke lets you set up gestures with the stylus to do things like scroll etc.

---

### Post by limotux on 2011-01-06
Thanks Favux, your always there for help.

I have tried cellwriter few days ago, but uninstalled it after I read someone here said he solved his rotation problem after uninstaling it!!

I'll give it another try though I couldn't make it to put input in other applications.
What I understood about it is that I can write with the stylus (somewhere I don't know) and it recognizes the text and input it in ANY other application. I should try and find out.

For John, I just installed onboard, to my eyes it seems to me as a clone of xvkbd but it works without problems. xvkbd used to steel focus, hence not typing!

I think I'll stick with onboard for now while trying cellwriter again.

Will keep you posted!:guitar:

---

### Post by jruh64 on 2011-01-06
I have Cellwriter but I didn't realize it also is an onscreen keyboard, I thought just handwriting recognition. I will try it again as well as Xournal and Easystroke (hadn't heard of them before now).

There is also a script called **switch-vkeyboard.sh** located in /usr/lib/fjbtndrv (same folder as the **rotate-wacom.sh** script that we just edited.  This script seems to dictate which virtual keyboard launches when you go into tablet mode.
```

#!/bin/bash
# Sample script for fscd.
# Copy or link this script to rotate-normal and rotate-tablet.
#
# Copyright (C) 2008-2010 Robert Gerlach <khnz@users.sourceforge.net>
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2.
################################################################################

oskb_bin=
[ "$oskb_bin" ] || oskb_bin="`type -p onboard`"
[ "$oskb_bin" ] || oskb_bin="`type -p cellwriter`"
[ "$oskb_bin" ] || oskb_bin="`type -p matchbox-keyboard`"
[ "$oskb_bin" ] || oskb_bin="`type -p xvkbd`"
[ "$oskb_bin" ] || oskb_bin="`type -p kvkbd`"



[ "$oskb_bin" ] || exit 0

case "$MODE" in

  tablet)
    if test "$ACTION" = "rotated"; then
      "$oskb_bin" &
    fi
    ;;

  normal)
    if test "$ACTION" = "rotating"; then
      pid=$( pgrep -u "$USER" "`basename "$oskb_bin"`" )
      if [ "$pid" ]; then
        kill -TERM $pid
      fi
    fi
   ;;

esac

exit 0
```

Edit it such that your favorite keyboard is listed first, and that one will launch when you go into tablet mode.

Favux, thanks again for all your help, now one step closer to dropping Windows altogether :-)

John

---

### Post by Favux on 2011-01-06
Thanks John,

More of fjbtndrv's magic exposed.  We do the same thing with Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  Our default option is CellWriter.  In Magick's Advanced Setup you just change the name of the onscreen keyboard you want.

---

### Post by jruh64 on 2011-01-06
Magick Rotation sounds sweet, too bad just for HP, but we got things working on Fujitsu now thanks to you.

I haven't figured out how to use Easystroke yet and it seems I am not smart enough to install Xournal but I did use Jarnal a bit and it's pretty nice.

Cheers, John

---

### Post by limotux on 2011-01-09
Hi guys, sorry I was too busy last few days.
Everything is going fine here. I even installed the latest virtualbox and it is awesome, it is a great leap forward compared to previous versions (if interested [look here]("http://ubuntuforums.org/showthread.php?p=10335257#post10335257"))

John, I'm using Jarnal now, it is more advanced than xournal.

Ok, to get going with Jarnal first of all you should know you don't really "install" it.

1- Extract the zipped file anywhere.
2- Find the file Jarnal.sh
3- Chenge property of the file and set it as executable.

That's all, click it (or double click) it to run it.

Is it working for you?

I see an interesting feature, when you close a file you wrote, it gives you several options including emailing it. but I couldn't figure out how to set it up to email. it fails.

I'll keep you posted if I got it working.

---

### Post by jruh64 on 2011-01-09
hi Limotux,

How is your touch screen etc working out?  Mine is all good except I noticed I cannot use gestures to scroll when in portrait mode.  I can live with it for now but might ask for help or try to figure it out eventually.  I can use the tablet buttons to page up and down at least.

I do have Jarnal and I like it.  I also tried the email option but there doesn't seem to be any way of associating my email address, server, etc to it.  I am thinking it might be a feature that was never finished yet.
It would be nice if Jarnal recognized and used the eraser end of the pen but it's not a big issue, it has an eraser tool.

I have version '920' with library 0, option to update to 'current version 999' or 'stable 24' and library 5. I might do that.
I set it up to launch in my applications menu but there was no icon for it so I drew some (but not very good).

Cheers, John

---

### Post by limotux on 2011-01-10
Hi John, 
It is almost fine here guestures are behaving funny somehow in Firefox, to drag page up or down it enlarges, reduces and sometimes select text, sometimes moves up or down.
I can't figure out what's going on with touch and gestures in firefox.

But with Okular it is working fine, I can move a page up or down with one finger.
Havent tried other stuf in okular.

For Jarnal you can configure it to have the tip to work as eraser with a click of the button on stylus. I use it that way.

Maybe I just need to practice more with gestures on firefox and other apps.

Still couldn't find a way to get Jarnal to send email. But as far as I have read, there is a file in the folder where Jarnal is that needs to be edited and include the mail address or setup in it.

If you succeeded let me know.
Any Ideas about gestures especially in firefox,do you know where can I read about gestures, I may be doing wrong things or need practice.
Keep in touch

---

### Post by Favux on 2011-01-10
Hi limotux,

See "Touch & Gesture Tips for the Bamboo in Linux" in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") near the bottom.

Now that you're getting used to your touch you might want to start playing a little with the xsetwacom parameters.  ZoomDistance and ScrollDistance come to mind.  :)

---

### Post by limotux on 2011-01-14
hmmm... funny things happening to me...

Jarnal stopped working... jarnal.sh is marked as executable but it doesn't respond!
removed everything and started all over again... same situation!!

Any ideas?

---

### Post by limotux on 2011-01-14
> **Favux said:**
> Hi limotux,

See "Touch & Gesture Tips for the Bamboo in Linux" in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") near the bottom.

Now that you're getting used to your touch you might want to start playing a little with the xsetwacom parameters.  ZoomDistance and ScrollDistance come to mind.  :)

Hi Favux...

How are things going with you.
I really appreciate your help.

It's been some time that funny things are happening to me like [here]("http://ubuntuforums.org/showthread.php?t=1666798").
Now, though I had jarnal working now it doesn't...!

I'll keep trying ... I find it much more feature rich and the pen-pointing is more precise.

I just want to get things working and try all your suggestions..

---

### Post by limotux on 2011-01-14
Hi John, how is it going with you? How is Jarnal? easystroke? any news about it?
I haven't had time to try...

---

### Post by jruh64 on 2011-01-16
Hi Limotux,
 
Sorry I haven't been on here lately.  Jarnal seems to to work ok for me so far.  I really haven't used it much though.  I use my fujitsu as a laptop more than as a tablet. 
Have you been able to repair your jarnal installation.  Sorry i don't know how to fix that. I would start a new thread specifically for that as i am sure there are people who could help you with it.
 
Cheers, John

---

### Post by limotux on 2011-01-16
Hi John, glad to see you again.
I have already made a thread but nobody answered!

But it was sorted out, [here]("http://ubuntuforums.org/showthread.php?t=1667530")

It seemed to be a java problem.
I checked History in synaptic, and found that I messes things up, so I reinstalled what I messed up.

Now working fine!

---

### Post by limotux on 2011-01-16
... and I have trained cellwriter as well to recognize my handwriting. It appears it needs some training AND changing my handwriting for some characters like i, t, 1, l, 0, o, O :mad:
But it is getting much better.

Cellwriter as well needs to be wider to be able to use comfortably, not just few cells to write in.
Maybe there is a way to get more cells to write in on the screen and get more rows, or automatically add a new row on reaching the rightmost cell in a row. :-k

---

### Post by limotux on 2011-01-16
... and I have trained cellwriter as well to recognize my handwriting. It appears it needs some training AND changing my handwriting for some characters like i, t, 1, l, 0, o, O :mad:
But it is getting much better.

Cellwriter as well needs to be wider to be able to use comfortably, not just few cells to write in.
Maybe there is a way to get more cells to write in on the screen and get more rows, or automatically add a new row on reaching the rightmost cell in a row. :-k
(sorry for the double post, it seems a result of a double click on submit button)

---

### Post by Favux on 2011-01-16
Hi limotux,

Just go into Setup and you can increase the number of cells and the size of the cells.  Its suppose to let you increase the row number too but that isn't working for me.

---

### Post by limotux on 2011-01-16
Hi Favux... it's been so long since saw you... you always come to rescue...
I did it... increased width... number of rows still doesn't change though I change it in setup

---

### Post by bluewanders on 2011-01-19
Hey Everybody,

I wanted to start off by thanking everyone who has been posting in this thread... it has helped immensely.  Ive been following for a while... and in the last few days you guys have managed to solve pretty much every lingering problem Ive had with my T4310.  So again... great work, and thanks.

I do have one problem left... and its a rather strange one to me, considering what I am reading here.  Ive got the touch, multitouch, and bezel buttons working.  However, it appears that the fjbtndrv does not detect when I go into tablet mode at all.  Is there a setting somewhere Ive been missing?  I loaded it from the ppa on a new install of both 64bit meerkat and meerkat notebook... on both the buttons begin working, but theres no detection when I lay the screen down... by that I mean no autorotation and it doesnt start an onscreen keyboard.

I take it this isnt normal for the rest of you with a T4310 after the install... What did I miss?  

Heres what Ive done so far... install the fjbtndrv from the ppa, complete section II of the Bamboo How-to, set up the .xsetwacom.sh script... and changed the rotate script to fix the reverse cursor responses when the screen is rotated.

---

### Post by Favux on 2011-01-20
Hi bluewanders,

Let's see if jruh64 & limotux can help you.  Since you changed the rotation file you know where jruh64 found it, so we start knowing you have it there.

If you guys are interested we could see if we can get the Fujitsu's working on Magick Rotation.  It's more flexible and offers more features for rotation than fjbtndrv.  You'd still use fjbtndrb for the bezel buttons of course.  We just added the Lenovo ThinkPads so I'm feeling flush with success and probably falsely optimistic.

---

### Post by bluewanders on 2011-01-20
Hi Favux

Right... I know fjbtndrv is working... and working well in most cases... Ive been going through all the files trying to identify where it captures the hinge switch that tells the laptop to go into tablet mode... no luck.  I seem to recall in other Fujitsu tablets like the U series there was a Bios setting for detection of tablet mode.  No such luck... in this case.  

Magick Rotation is brilliant by the way... my old gateway convertible loved you guys.  I would tend to say though that we already have a tool someone has worked really hard on designed specifically to integrate what we have... no sense re-inventing the wheel... I just need to get it configured correctly and get it documented for the next guy.

---

### Post by Favux on 2011-01-20
lol  I came that close to pulling the trigger on one of the Gateway convertibles.  I didn't know someone had it working on those.  Please share the details if you're so inclined.

Well, I sure understand that position.  Still if you haven't looked at Magick in a while it is quite improved.  You might want to take a quick look see:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by bluewanders on 2011-01-20
It was a hand-me-down from my father, grandpa linux himself, I think he threw it together in an attempt to get me to come over to linux tell the truth.  I replaced it with this one about 6 months ago.  It was just absolutely painful going back to windows after running his little monster, but I dropped it in my backback off the roof of a 5 story bulding and sobbed wretchedly over my beloved electronics... it had to be done (along with replacing my mp3 player, phone, camera, and gps)... I would ask him what all he did... he was the IT professional, im in the robotics field... but hes not around anymore.  

I didnt mean to sound insulting by the way... if you guys want to tackle integrating the T series into Magick Rotation... thats great.  I would provide any assistance you need, although I am not that Linux savvy yet...  I merely meant you shouldnt add to the workload if you had other things you wanted to get accomplished.  

Oh and by the way... you didnt miss much on those convertibles... they were WAY too heavy to be a decent mobile tablet... but the large screen was great for taking notes during class and the microphone was good enough to record lectures.  Built quality was awful... toward the end that thing had more duct tape than plastic.  It didnt handle life in a backpack nearly as well as these happy little fujitsus do.

Edit:  Oops!  Looking at your launchpad... it might have been something else he was using for the automatic rotation...

---

### Post by limotux on 2011-01-22
Hi bluewanders, I hope you had your tablet working properly.

I assume that you missed something along the way. I'd suggest you try to go to the first post, try to make a step by step guide, then start applying those steps very carefully.

I'd suggest after you install something to reboot then update the whole system to be sure the all changes are detected and up to date.

I'm sorry I'm not techie as Favux or John (he was much smarter than me)

Start allover step by step and keep us posted with the results.Maybe someone can help. I will do my best to help anyway.

---

### Post by jruh64 on 2011-01-22
Hi Bluewaders, welcome.

I am really not sure but I suspect the file /usr/lib/fjbtndrv/switch-vkeyboard.sh is what activates the tablet mode when button is activated.

I got to admit I don't really understand code so I just guess and hope it was written intuitively.

We can compare contents of this file if that would help. I am running the 32 bit version of Maverick but otherwise we should have identical setups?

Cheers, John

---

### Post by bluewanders on 2011-01-30
Hi guys...

Sorry for the delay... work has been hectic... Ive been on a plane almost every day for the last month.  Lots of laboratories with broken robots right now I guess... either that or the yearly budgets are in and they can finally afford to have us come out.  

To get back to you on the issue... Ive been doing quite a bit of testing/breaking/recovering in the past couple weeks since I posted... the switch_vkeyboard.sh doesnt actually handle the rotation, it handles turning the virtual keyboard on/off when an autorotation is detected.  The actual autorotation is handled my a module appended to your linux kernel by the fsc_btns package that gets installed along with the fjbtndrv... right now ubuntu is on 2.6.35-x whatever x is at the moment, I think 25?  At any rate... .35 is a pretty unstable kernel, and was what was causing the problem.  I think you guys got pretty lucky really to have it work the first time right off the bat... at any rate, after I upgraded to linux kernel 2.6.36 and installed the fjbtndrv if found the rotation integration to be pretty well flawless... if not a bit more snappy in comparison to the few times I got it to work on 2.6.35...  Naturally, like I was saying before, im far from an epert, or even experience/educated enough to consider myself an authority.  So take all this with a grain of salt... as one newbie to another.

Oh... and im not sure if you guys knew this or not... but with the fjbtndrv package... most of those bezel buttons have more than one function... button 4 acts as a 'FN' button to change the others to a secondary function... and the 'ENT' button acts as an 'Alt' button to activate a 3rd functionality... try playing with it a little and experiment with the different combinations to see what you come up with.

Cheers!

EDIT:  I should clarify... Ubuntu 10.10 Maverick Meerkat is running 2.6.35...  I dont remember what kernel Lucid Lynx is running

---

### Post by limotux on 2011-02-15
Hi everybody...

Hi Favux, I messed up my tablet pc few days ago and I had to reinstall from scratch.
[LEFT]I could get everything working, touch is enabled, but I could not go further.
The problems I'm facing are:
1- no multitouch
2- no screen rotation
3- screen buttons not working

I have noticed some "errors" and messages that indicate there is something wrong, but... mmmm... sorry... I'm unable to understand what is wrong or what to do.

The attached file contains details of each command an it's output, hoping this will make it easier to help me. (unable to attach, so it is quoted below)

Can you help me again?

My current status:
```

 limo@mint ~ $ cd '/home/limo/Linux Files'
limo@mint ~/Linux Files $ cd linuxwacom-0.8.8-10
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/limo/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-28-generic/build
checking kernel version... 2.6.32-28-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-28-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-28-generic/build M=/home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
make[1]: *** No rule to make target `Files/linuxwacom-0.8.8-10/src/2.6.30'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [all] Error 2


Your wacom.ko is available under 
    /home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/limo/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-28-generic/build
checking kernel version... 2.6.32-28-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-28-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-28-generic/build M=/home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
make[1]: *** No rule to make target `Files/linuxwacom-0.8.8-10/src/2.6.30'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [all] Error 2


Your wacom.ko is available under 
    /home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom --prefix=/limo
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/limo/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-28-generic/build
checking kernel version... 2.6.32-28-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-28-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-28-generic/build M=/home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
make[1]: *** No rule to make target `Files/linuxwacom-0.8.8-10/src/2.6.30'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [all] Error 2


Your wacom.ko is available under 
    /home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[sudo] password for limo: 
Sorry, try again.
[sudo] password for limo: 
[sudo] password for limo: 

[1]+  Stopped                 sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`limo -r`/kerel/drivers/input/tablet/wacom.ko
The program 'limo' is currently not installed.  You can install it by typing:
sudo apt-get install limo
[sudo] password for limo: 
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ sudo depmod -a
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ lsmod | grep wacom
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ 

```Really thank you very much.

[/LEFT]

---

### Post by Favux on 2011-02-15
Hi limotux,

This command isn't right.
```
~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom --prefix=/limo

```
Instead use:
```
./configure --enable-wacom --prefix=/usr
```
so it goes to the /user directory, not /user/local.  The /user/local is a legacy when the pc's were kind of dumb and hooked up to a server. Unfortunately it's still the default which is why you have to add the --prefix=/user flag.  So user means a directory name already on the system, not your username.

Then it tells you your compiled wacom.ko is at:
```
Your wacom.ko is available under 
    /home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30

```
Then:
```
$ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

```
is right, not:
```
$ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`limo -r`/kerel/drivers/input/tablet/wacom.ko

```
uname is a little command line program that gets the kernel to tell it's version number.  Enter:
```
uname -r
```
in a terminal and you'll see what I mean.  If you enter 'man uname' you'll see other switches like -a or -m.  To shut the manual down enter control+z.  So uname is the kernel name not your name.

I think you're close.  When you're back in the linuxwacom folder again run:
```
make clean
```
before you run the configure line.  That will clear the previous attempts.

---

### Post by limotux on 2011-02-17
Hi Favux,
Thanks a lot for your kind help as usual

Well, here is what I tried... but... sorry for my ignorance:
```
limo@mint ~ $ ./configure --enable-wacom --prefix=/user
bash: ./configure: No such file or directory
limo@mint ~ $ ./configure --enable-wacom --prefix=/usr
bash: ./configure: No such file or directory
limo@mint ~ $ ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom refix=/user
bash: /home/limo/Linux: No such file or directory
limo@mint ~ $ ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom refix=/usr
bash: /home/limo/Linux: No such file or directory
limo@mint ~ $ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drrs/input/tablet/wacom.ko
[sudo] password for limo: 
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
limo@mint ~ $ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drrs/input/tablet/wacom.ko
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
limo@mint ~ $ 
limo@mint ~ $ sudo cp ./src/2.6.30/wacom.ko /lib/modules/`limo -r`/kernel/dris/input/tablet/wacom.ko
The program 'limo' is currently not installed.  You can install it by typing:
sudo apt-get install limo
cp: cannot stat `./src/2.6.30/wacom.ko': No such file or directory
limo@mint ~ $ uname -r
2.6.32-28-generic
limo@mint ~ $ 

```?!:sad:

p.s. I have a folder called usr not user

---

### Post by Favux on 2011-02-17
Oops, you are correct.  A typo, sorry.  Should read:
```
./configure --enable-wacom --prefix=/usr
```

---

### Post by limotux on 2011-02-18
This is what I got!!
```
$ ./configure --enable-wacom --prefix=/usr
bash: ./configure: **No such file or directory**
```edit: just installed wacomrotate_0.3.1_i386.deb from [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/)
edit: just installed wacomrotate_0.3.1_i386.deb from [http://ppa.launchpad.net/thjaeger/ta...w/wacomrotate/]("http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/")
edit 2: still no fjbtndrv !!!

---

### Post by Favux on 2011-02-18
You cut the line off at the prompt "$", so I can't see the directory behind it.  But my guess is you weren't in the correct directory when you issued the command?  Everybody with Ubuntu has a /usr directory in the root directory.  Unless on some sort of server setup maybe.  Hard to believe Mint doesn't too.  With Places (Nautilus) click on File System.  That's your root directory.  See if there is a /usr directory in it.

---

### Post by limotux on 2011-02-18
there is usr directory and it contains bin  games  include  lib  lib64  local  sbin  share  src subdirectories

```
limo@mint / $ cd /usr
limo@mint /usr $ ls
bin  games  include  lib  lib64  local  sbin  share  src
limo@mint /usr $ ./configure --enable-wacom --prefix=/usr
bash: ./configure: No such file or directory
limo@mint /usr $ 
 

```

---

### Post by Favux on 2011-02-18
Hi limotux,

You should not be running the:
```
./configure --enable-wacom --prefix=/usr

```
line in the /usr directory.  The source code the configure line is suppose to compile is not there.  How the heck did you get there?  :)

It is in the folder you downloaded.  You are suppose to run in in the unpacked linuxwacom tar/source code.  Reread the instructions and pay attention to the directory changes.

---

### Post by limotux on 2011-02-18
ok... done! (with some errors or notes I think, here are the results:
```
limo@mint ~/Linux Files $ cd '/home/limo/Linux Files/linuxwacom-0.8.8-10'
limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/limo/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-28-generic/build
checking kernel version... 2.6.32-28-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-28-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-28-generic/build M=/home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
make[1]: *** No rule to make target `Files/linuxwacom-0.8.8-10/src/2.6.30'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [all] Error 2


Your wacom.ko is available under 
    /home/limo/Linux Files/linuxwacom-0.8.8-10/src/2.6.30


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

limo@mint ~/Linux Files/linuxwacom-0.8.8-10 $ 

```

what next?

---

### Post by limotux on 2011-02-19
> **Favux said:**
> Hi limotux,

I just commented out the Wacom stuff.  So I didn't do the whole xorg.conf in the box above.  Just enough to show what needed to be commented out.  So my example left out your video sections.

In the attached xorg.conf I have removed all of the Wacom stuff.  I also removed the keyboard and mouse stuff.  It looks like there is other stuff that can be removed, but I figured this is enough editing for now.  The xorg.conf should work.  Just completely replace your current one with it (copy and paste).  After backing up your current one of course.

:confused:

I did[ this]("http://ubuntuforums.org/showpost.php?p=10311550&postcount=46"), trying to do same steps as before, surprisingly after downloading the file and renaming it... I rebooted. But touch wasn't working at all!!!

So, I reverted to the old file and now touch is working, finger and stylus, but still no rotation, no multitouch, no fjbtndrv !!!

really sorry I'm unable to help myself.
I hope you can still help.

---

### Post by limotux on 2011-02-19
> **limotux said:**
> ok done... will test and tell you the results

update: still touch and pen don't rotate

Now I did [URL="http://ubuntuforums.org/showpost.php?p=10315895&postcount=68"]this
[/URL] and installed wacom rotate... nothing new happens!
what should I do?

---

### Post by Favux on 2011-02-19
Hi limotux,

Let's start over.

With Lucid you have the 2.6.32 kernel and the 1.7 X server.  To verify, enter in a terminal:
```
Xorg -version
```
The 1.7 X server does not use linuxwacom.  linuxwacom's X driver only works on X servers less than 1.7.  For 1.7 and up you have to get the X driver from xf86-input-wacom.  That's part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562"), not part I.

You have a serial tablet pc, not a usb one.  Part I. on the Bamboo P & T HOW TO is only for usb tablets.  Serial tablet pc's do not need the wacom.ko.  Which is the usb kernel driver/module.

---

### Post by limotux on 2011-02-19
Thanks a lot for your kind help.
This is the output:
```
limo@mint ~ $ Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux mint 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=4caec5a8-0fae-40f8-9a2d-d13fcaa1c389 ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
limo@mint ~ $ 

```

---

### Post by limotux on 2011-02-19
mmm... I tried, and here is the output (there were few errors I see):

```

limo@mint ~ $ sudo apt-get install git-core
[sudo] password for limo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
limo@mint ~ $ wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2/download
--2011-02-20 02:50:16--  http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2/download
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2?r=&ts=1298159416&use_mirror=garr [following]
--2011-02-20 02:50:17--  http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2?r=&ts=1298159416&use_mirror=garr
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2 [following]
--2011-02-20 02:50:17--  http://garr.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2
Resolving garr.dl.sourceforge.net... 193.206.140.34, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|193.206.140.34|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 439013 (429K) [application/x-bzip2]
Saving to: `download.1'

100%[===================================>] 439,013     31.7K/s   in 15s     

2011-02-20 02:50:32 (29.5 KB/s) - `download.1' saved [439013/439013]

limo@mint ~ $ sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
limo@mint ~ $ 
limo@mint ~ $ tar xjvf util-macros-1.8.0.tar.bz2
tar: util-macros-1.8.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
limo@mint ~ $ 
limo@mint ~ $ 
imo@mint ~ $ clear
limo@mint ~ $ ^C
limo@mint ~ $ cd '/home/limo/Linux Files'
limo@mint ~/Linux Files $ tar xjvf util-macros-1.8.0.tar.bz2
tar: Record size = 8 blocks
util-macros-1.8.0/
util-macros-1.8.0/xorg-macros.pc.in
util-macros-1.8.0/COPYING
util-macros-1.8.0/aclocal.m4
util-macros-1.8.0/Makefile.am
util-macros-1.8.0/missing
util-macros-1.8.0/xorgversion.m4
util-macros-1.8.0/configure
util-macros-1.8.0/xorg-macros.m4.in
util-macros-1.8.0/configure.ac
util-macros-1.8.0/Makefile.in
util-macros-1.8.0/ChangeLog
util-macros-1.8.0/README
util-macros-1.8.0/install-sh
util-macros-1.8.0/INSTALL
limo@mint ~/Linux Files $ 
limo@mint ~/Linux Files $ cd util-macros-1.8.0
limo@mint ~/Linux Files/util-macros-1.8.0 $ 
limo@mint ~/Linux Files/util-macros-1.8.0 $ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/limo/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating xorg-macros.pc
config.status: creating Makefile
config.status: creating xorg-macros.m4
limo@mint ~/Linux Files/util-macros-1.8.0 $ make
make: Nothing to be done for `all'.
limo@mint ~/Linux Files/util-macros-1.8.0 $ 
limo@mint ~/Linux Files/util-macros-1.8.0 $ sudo make install
[sudo] password for limo: 
make[1]: Entering directory `/home/limo/Linux Files/util-macros-1.8.0'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/aclocal" || /bin/mkdir -p "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'xorg-macros.m4' '/usr/share/aclocal/xorg-macros.m4'
test -z "/usr/share/util-macros" || /bin/mkdir -p "/usr/share/util-macros"
 /usr/bin/install -c -m 644 'INSTALL' '/usr/share/util-macros/INSTALL'
test -z "/usr/share/pkgconfig" || /bin/mkdir -p "/usr/share/pkgconfig"
 /usr/bin/install -c -m 644 'xorg-macros.pc' '/usr/share/pkgconfig/xorg-macros.pc'
make  install-data-hook
make[2]: Entering directory `/home/limo/Linux Files/util-macros-1.8.0'
rm -f /usr/share/aclocal/xorgversion.m4
make[2]: Leaving directory `/home/limo/Linux Files/util-macros-1.8.0'
make[1]: Leaving directory `/home/limo/Linux Files/util-macros-1.8.0'
limo@mint ~/Linux Files/util-macros-1.8.0 $ cd ..
limo@mint ~/Linux Files $ cd ./Desktop
bash: cd: ./Desktop: No such file or directory
limo@mint ~/Linux Files $ 
limo@mint ~/Linux Files $ ^C
limo@mint ~/Linux Files $ cd /home/limo
limo@mint ~ $ ^C
limo@mint ~ $ cd /home/limo/Desktop
limo@mint ~/Desktop $ wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2/download
--2011-02-20 02:54:53--  http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2/download
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2?r=&ts=1298159693&use_mirror=garr [following]
--2011-02-20 02:54:54--  http://downloads.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2?r=&ts=1298159693&use_mirror=garr
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://garr.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2 [following]
--2011-02-20 02:54:54--  http://garr.dl.sourceforge.net/project/linuxwacom/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2
Resolving garr.dl.sourceforge.net... 193.206.140.34, 2001:760:ffff:b0::34
Connecting to garr.dl.sourceforge.net|193.206.140.34|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 439013 (429K) [application/x-bzip2]
Saving to: `download'

100%[============================================================>] 439,013     31.7K/s   in 22s     

2011-02-20 02:55:17 (19.6 KB/s) - `download' saved [439013/439013]

limo@mint ~/Desktop $ 
limo@mint ~/Desktop $ git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
Initialized empty Git repository in /home/limo/Desktop/xf86-input-wacom/.git/
remote: Counting objects: 9433, done.
remote: Compressing objects: 100% (4056/4056), done.
remote: Total 9433 (delta 7371), reused 6751 (delta 5363)
Receiving objects: 100% (9433/9433), 2.49 MiB | 52 KiB/s, done.
Resolving deltas: 100% (7371/7371), done.
limo@mint ~/Desktop $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                                      
Ign file: binary/ Release                                                                            
Ign file: binary/ Packages                                                                           
Ign file: binary/ Packages                                                                           
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                                       
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US                                    
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US                                
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US                                  
Ign http://packages.linuxmint.com isadora-kde Release.gpg                                            
Ign http://packages.linuxmint.com/ isadora-kde/main Translation-en_US                                
Ign http://packages.linuxmint.com/ isadora-kde/upstream Translation-en_US                            
Ign http://packages.linuxmint.com/ isadora-kde/import Translation-en_US                              
Hit http://linux.dropbox.com maverick Release.gpg                                                    
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US                                 
Get:2 http://packages.linuxmint.com isadora Release [7,235B]                                         
Get:3 http://packages.linuxmint.com isadora-kde Release [6,464B]                                     
Hit http://linux.dropbox.com maverick Release                                                        
Get:4 http://ppa.launchpad.net lucid Release.gpg [307B]                                              
Ign http://ppa.launchpad.net/zekr/ubuntu/ lucid/main Translation-en_US                               
Hit http://ppa.launchpad.net lucid Release.gpg                                                       
Hit http://archive.canonical.com lucid Release.gpg                                                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                             
Ign http://packages.linuxmint.com isadora/main Packages                                              
Hit http://security.ubuntu.com lucid-security Release.gpg                                            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                   
Hit http://linux.dropbox.com maverick/main Packages                                                  
Hit http://archive.ubuntu.com lucid Release.gpg                                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                             
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ lucid/main Translation-en_US                    
Ign http://packages.linuxmint.com isadora/upstream Packages                                          
Ign http://packages.linuxmint.com isadora/import Packages                                            
Ign http://packages.linuxmint.com isadora-kde/main Packages                                          
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                      
Ign http://packages.linuxmint.com isadora-kde/import Packages                                        
Get:5 http://ppa.launchpad.net lucid Release [57.3kB]                                                
Ign http://ppa.launchpad.net lucid Release                                                           
Ign http://packages.linuxmint.com isadora/main Packages                                              
Hit http://archive.canonical.com lucid Release                                                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                   
Hit http://security.ubuntu.com lucid-security Release                                                
Hit http://ppa.launchpad.net lucid Release                                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                               
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                             
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                              
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                     
Hit http://archive.ubuntu.com lucid Release                                                          
Ign http://packages.linuxmint.com isadora/upstream Packages                                          
Ign http://packages.linuxmint.com isadora/import Packages                                            
Ign http://packages.linuxmint.com isadora-kde/main Packages                                          
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                      
Hit http://ppa.launchpad.net lucid/main Packages                                                     
Hit http://archive.canonical.com lucid/partner Packages                                              
Ign http://packages.linuxmint.com isadora-kde/import Packages                                        
Hit http://security.ubuntu.com lucid-security/main Packages                                          
Hit http://ppa.launchpad.net lucid/main Packages                                                     
Hit http://packages.linuxmint.com isadora/main Packages                                              
Hit http://archive.ubuntu.com lucid-updates Release                                                  
Hit http://security.ubuntu.com lucid-security/restricted Packages                                    
Hit http://security.ubuntu.com lucid-security/universe Packages                                      
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                    
Hit http://packages.linuxmint.com isadora/upstream Packages                                          
Hit http://archive.ubuntu.com lucid/main Packages                                     
Hit http://archive.ubuntu.com lucid/restricted Packages                               
Hit http://archive.ubuntu.com lucid/universe Packages                                 
Hit http://archive.ubuntu.com lucid/multiverse Packages                               
Hit http://packages.linuxmint.com isadora/import Packages                             
Hit http://archive.ubuntu.com lucid-updates/main Packages                                            
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                      
Hit http://packages.linuxmint.com isadora-kde/main Packages                           
Hit http://packages.linuxmint.com isadora-kde/upstream Packages                       
Hit http://archive.ubuntu.com lucid-updates/universe Packages   
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                                      
Hit http://packages.linuxmint.com isadora-kde/import Packages                                        
Hit http://packages.medibuntu.org lucid Release.gpg                                                  
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                      
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US                                  
Hit http://packages.medibuntu.org lucid Release                                                      
Hit http://packages.medibuntu.org lucid/free Packages                                                
Hit http://packages.medibuntu.org lucid/non-free Packages                                            
Fetched 14.2kB in 11s (1,209B/s)                                                                     
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC9C35EAEF400C7C
limo@mint ~/Desktop $ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
libxrandr-dev is already the newest version.
libncurses5-dev is already the newest version.
xutils-dev is already the newest version.
autoconf is already the newest version.
libtool is already the newest version.
pkg-config is already the newest version.
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni libswt-mozilla-gtk-3.5-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
limo@mint ~/Desktop $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
limo@mint ~/Desktop $ 
limo@mint ~/Desktop $ sudo apt-get build-dep xf86-input-wacom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
limo@mint ~/Desktop $ tar xjvf xf86-input-wacom-0.10.11.tar.bz2
tar: xf86-input-wacom-0.10.11.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
limo@mint ~/Desktop $ 
limo@mint ~/Desktop $ ^C
limo@mint ~/Desktop $ cd /home/limo
limo@mint ~ $ ^C
limo@mint ~ $ cd '/home/limo/Linux Files'
limo@mint ~/Linux Files $ tar xjvf xf86-input-wacom-0.10.11.tar.bz2
tar: xf86-input-wacom-0.10.11.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
limo@mint ~/Linux Files $ 
limo@mint ~/Linux Files $ cd xf86-input-wacom-0.10.11
bash: cd: xf86-input-wacom-0.10.11: No such file or directory
limo@mint ~/Linux Files $ 
limo@mint ~/Linux Files $ ^C
limo@mint ~/Linux Files $ cd '/home/limo/Linux Files/xf86-input-wacom'
limo@mint ~/Linux Files/xf86-input-wacom $ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
configure: WARNING: Libtool does not cope well with whitespace in `pwd`
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating conf/Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating include/Makefile
config.status: creating tools/Makefile
config.status: creating xorg-wacom.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
limo@mint ~/Linux Files/xf86-input-wacom $ make
make  all-recursive
make[1]: Entering directory `/home/limo/Linux Files/xf86-input-wacom'
Making all in conf
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/conf'
Making all in src
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/src'
Making all in man
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/man'
Making all in include
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/include'
Making all in tools
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/tools'
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom'
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom'
limo@mint ~/Linux Files/xf86-input-wacom $ sudo make install
Making install in conf
make[1]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/conf'
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/conf'
make[2]: Nothing to be done for `install-exec-am'.
test -z "" || /bin/mkdir -p ""
test -z "/usr/share/hal/fdi/policy/20thirdparty" || /bin/mkdir -p "/usr/share/hal/fdi/policy/20thirdparty"
 /usr/bin/install -c -m 644 wacom.fdi '/usr/share/hal/fdi/policy/20thirdparty'
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/conf'
make[1]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/conf'
Making install in src
make[1]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/src'
make[2]: Entering directory `/home/limo/Linux Files/xf86-input-wacom/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
/bin/bash: /home/limo/Linux: No such file or directory
make[2]: *** [install-wacom_drv_laLTLIBRARIES] Error 127
make[2]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/src'
make: *** [install-recursive] Error 1
limo@mint ~/Linux Files/xf86-input-wacom $ 


```

rebooted... still same situation of course.

---

### Post by Favux on 2011-02-19
Hi limotux,

In the command line you can't have a space in a folder name like:
```
make[1]: Leaving directory `/home/limo/Linux Files/xf86-input-wacom/src'

```
It reads the space in a directory path as meaning something.

The Desktop will take 'Linux Files' but the command line won't accept the space.  That's why you see names like 'Linux_Files' or 'Linux-Files".  That covers your bets if you might use the name in a directory path in the command line.

---

### Post by limotux on 2011-02-19
ok... I renamed the directory... will repeat allover again.

---

### Post by limotux on 2011-02-24
Hi favux,

Sorry for delay, was so busy over the past few days.
I renamed the folder not to have spaces and repeated the steps.. still same situation, no auto rotate , no multitouch...
I appreciate your patience and hope you take my hand step by step... one step at a time

---

### Post by limotux on 2011-03-02
here is the xorg file

---

### Post by Favux on 2011-03-04
Hi limotux,

Hmmm.  That looks like a normal Xorg.0.log:
```
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.10
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Serial Wacom Tablet: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
(--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
(--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) Serial Wacom Tablet stylus: hotplugging dependent devices.
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "38400"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=100000 resol Y=100000
(**) Option "BaudRate" "38400"
(**) Serial Wacom Tablet touch: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "38400"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
(--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=2631 bottom Y=1652 resol X=10000 resol Y=10000
(II) Serial Wacom Tablet stylus: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
(--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=26312 bottom Y=16520 resol X=100000 resol Y=100000
```
From the Xorg.0.log everything should be working.

Ok, so stylus works, correct?

Do you have touch shut off with a script?  An xsetwacom script or touch toggle script you forgot about?

---

### Post by limotux on 2011-03-07
> **Favux said:**
> Hi limotux,

Ok, so stylus works, correct?

Do you have touch shut off with a script?  An xsetwacom script or touch toggle script you forgot about?

I have the xsetwacom as follows:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

# my new section

Section "InputClass"
      Identifier "Wacom eraser class"
      MatchProduct "Wacom"
      MatchProduct "eraser"
      Option "Foo" "bar"
EndSection
```

I feel lost

---

### Post by Favux on 2011-03-07
Hi limotux,

First I want you to reclone the xf86-input-wacom git repository.  That's Part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  It looks like you are using 0.10.10 and we want you up to 0.10.11+.

Your wacom.conf isn't right.  X server 1.7 can't configure dependent devices like the eraser.  That will become available with X server 1.10, i.e. Natty.  In the xf86-input-wacom folder, in the conf directory is the current wacom.conf.  Since Lucid has it's wacom.conf in a non-standard location xf86-input-wacom won't be able to update it.  It looks like:
```

Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
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
```
For Lucid use:
```

gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
and replace your current 10-wacom.conf contents with the ones above.

Then to turn multi-touch on try turning gestures on.  Enter in a terminal:
```

xsetwacom set "Serial Wacom Tablet touch" Gesture on
```
and see if it works.  I think I have the "device name" correct, check *xinput list* to be sure.  You do have 2 finger touch right?  Otherwise ignore this gesture stuff.

---

### Post by limotux on 2011-03-08
Wow... thanx Favux,

I changed 10-wacom.conf with what you suplied and did
xsetwacom set "Serial Wacom Tablet touch" Gesture on
Now multitouch is working. but shouldn't it be placed somewhere in a file to be run every time I restart the machine?

Edit: I was right, I rebooted and had to issue the command again to get multitouch.

Well... I'll restart out of curiosity and do the rest and let you know
Thanks a lot... you are always saving me.:KS

---

### Post by limotux on 2011-03-08
```
limo@mint ~/Linux_Files $ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**git-core is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.15+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because the error message indicates its a followup error from a previous failure.
        Errors were encountered while processing:
 firefox
 firefox-3.0
 firefox-3.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
limo@mint ~/Linux_Files $ 

```hmm... a problem with firefox?!
ok... I had a problem with firefox few days ago.. but I installed FF v.4 beta and it is running fine, installed as well "swiftfox", which is based on FF and running fine as well.

:-k

because it says that "[B]git-core is already the newest version." I assume it installed before that and carry on....
[/B]

---

### Post by limotux on 2011-03-08
well... finished ```
Part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562"). 
```

Surprisingly multitouch worked by itself without me doing anything.

Still no rotation, no buttons... etc... as before... only added multitouch.
Here is what I did and error messages attached
What you think?

---

### Post by Favux on 2011-03-08
> Surprisingly multitouch worked by itself without me doing anything.
Great!  It recognizes your tablet PC supports 2FGT and is turning support for gestures on automatically like it is suppose to.

So now for your rotation and buttons you need to install fjbtndrv.  That's covered in a couple of posts early in the thread.  I think you said something about errors?  Go over it again and if there are errors post them so we can see what's happening.

Edit:  Not real sure how installing those libraries for the compile pulled in Firefox.  Never seen that before.  Some sort of Mint packaging for Firefox conflict I guess.  Or maybe because Chrome is installed too?  Otherwise the compile of xf86-input-wacom looks good.

---

### Post by limotux on 2011-03-09
here is what happened:
```
limo@mint ~ $ cd /home/limo/Linux_Files
limo@mint ~/Linux_Files $ tar zxf fscd-*.tar.gz
tar: fscd-*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
limo@mint ~/Linux_Files $ ^C
limo@mint ~/Linux_Files $ cd /home/limo/Linux_Files/fjbtndrv-2.2.1
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ tar zxf fscd-*.tar.gz
tar: fscd-*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XRANDR... yes
checking for XINPUT... no
configure: error: Package requirements (x11 xi xext xtst) were not met:

No package 'xtst' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XINPUT_CFLAGS
and XINPUT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ make
make: *** No targets specified and no makefile found.  Stop.
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ sudo make install
[sudo] password for limo: 
make: *** No rule to make target `install'.  Stop.
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ 

```

---

### Post by Favux on 2011-03-09
I forget, why are we trying to compile fjbtndrv?  Can't we just add the PPA and apt-get install?
```

sudo add-apt-repository ppa:khnz/ppa

sudo apt-get update

sudo apt-get install fjbtndrv
```

---

### Post by limotux on 2011-03-11
first command went fine I think
```
limo@mint ~ $ sudo add-apt-repository ppa:khnz/ppa
[sudo] password for limo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 13656879026EA184512DC7C8ACCA38C8E88D7B6F
gpg: requesting key E88D7B6F from hkp server keyserver.ubuntu.com
gpg: key E88D7B6F: "Launchpad PPA for Robert Gerlach" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

but the update gave an error!

```
W: Failed to fetch http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Favux on 2011-03-11
Sounds like the sources.list has been corrupted.  Try:
```
sudo apt-get -f clean

sudo apt-get update

sudo apt-get upgrade
```
If that doesn't work try changing the mirror/server - go into either System -> Administration -> Synaptic Package Manager -> Settings -> Repositories or System -> Administration -> Software Sources and try another server.

---

### Post by limotux on 2011-03-13
```
 p, li { white-space: pre-wrap; } The file or folder http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz does not exist.

```

I had the same error. It seems it is removed/renamed...

Can't we instel from the file previously downloaded? i.e. fjbtndrv-2.2.1.tar.gz
!!!!

---

### Post by limotux on 2011-03-13
Ok... where I extracted there is folder "/home/limo/Linux_Files/fjbtndrv-2.2.1"
and as I do the following:
```
limo@mint ~/Linux_Files/fjbtndrv-2.2.1 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XRANDR... yes
checking for XINPUT... no
configure: error: Package requirements (x11 xi xext xtst) were not met:

No package 'xtst' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XINPUT_CFLAGS
and XINPUT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
:o

---

### Post by Favux on 2011-03-13
OK, you're missing at least one library.  Since you've compiled xf86-input-wacom you've got most of the X development libraries.  Let's try adding the following one:
```
sudo apt-get install libxtst-dev
```
and see if that's what it wants.  Or does it also want others?

---

### Post by limotux on 2011-03-13
```
limo@mint ~ $ sudo apt-get install libxtst-dev
[sudo] password for limo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  x11proto-record-dev
The following NEW packages will be installed:
  libxtst-dev x11proto-record-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 29.0kB of archives.
After this operation, 184kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  x11proto-record-dev libxtst-dev
Authentication warning overridden.
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/main x11proto-record-dev 1.14-2 [5,590B]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/main libxtst-dev 2:1.1.0-2 [23.4kB]
Fetched 29.0kB in 3s (9,168B/s)      
Selecting previously deselected package x11proto-record-dev.
(Reading database ... 182561 files and directories currently installed.)
Unpacking x11proto-record-dev (from .../x11proto-record-dev_1.14-2_all.deb) ...
Selecting previously deselected package libxtst-dev.
Unpacking libxtst-dev (from .../libxtst-dev_2%3a1.1.0-2_i386.deb) ...
Processing triggers for man-db ...
Setting up firefox (3.6.15+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
Setting up x11proto-record-dev (1.14-2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
     Setting up libxtst-dev (2:1.1.0-2) ...
Errors were encountered while processing:
 firefox
 firefox-3.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
limo@mint ~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firefox (3.6.15+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.5:
 firefox-3.5 depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-3.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
     Errors were encountered while processing:
 firefox
 firefox-3.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
limo@mint ~ $ sudo apt-get install fjbtndrv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fjbtndrv
limo@mint ~ $ 

``` then I did the following:
```
limo@mint ~ $ sudo add-apt-repository ppa:khnz/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 13656879026EA184512DC7C8ACCA38C8E88D7B6F
gpg: requesting key E88D7B6F from hkp server keyserver.ubuntu.com
gpg: key E88D7B6F: "Launchpad PPA for Robert Gerlach" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
limo@mint ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                                     
Ign file: binary/ Release                                                                           
Ign file: binary/ Packages                                                                          
Ign file: binary/ Packages                                                                          
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                                      
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US                                   
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US                               
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US                                 
Ign http://packages.linuxmint.com isadora-kde Release.gpg                                           
Ign http://packages.linuxmint.com/ isadora-kde/main Translation-en_US                               
Ign http://packages.linuxmint.com/ isadora-kde/upstream Translation-en_US                           
Hit http://packages.medibuntu.org lucid Release.gpg                                                 
Ign http://getswiftfox.com unstable Release.gpg                                                     
Hit http://archive.ubuntu.com lucid Release.gpg                                                     
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                            
Hit http://security.ubuntu.com lucid-security Release.gpg                                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                  
Ign http://packages.linuxmint.com/ isadora-kde/import Translation-en_US                             
Hit http://ppa.launchpad.net lucid Release.gpg                                                      
Ign http://ppa.launchpad.net/zekr/ubuntu/ lucid/main Translation-en_US                              
Ign http://ppa.launchpad.net isadora Release.gpg                                                    
Hit http://archive.canonical.com lucid Release.gpg                                                  
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                            
Hit http://linux.dropbox.com maverick Release.gpg                                                   
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US                                
Get:2 http://packages.linuxmint.com isadora Release [7,235B]                                        
Ign http://getswiftfox.com/builds/debian/ unstable/non-free Translation-en_US                       
Ign http://ppa.launchpad.net/khnz/ppa/ubuntu/ isadora/main Translation-en_US                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                      
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ lucid/main Translation-en_US                   
Hit http://ppa.launchpad.net lucid Release                                                          
Get:3 http://packages.linuxmint.com isadora-kde Release [6,464B]                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                  
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                              
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                            
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                    
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                    
Hit http://linux.dropbox.com maverick Release                                                       
Hit http://security.ubuntu.com lucid-security Release                                               
Hit http://archive.ubuntu.com lucid Release                                                         
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                     
Hit http://archive.canonical.com lucid Release                                                      
Ign http://getswiftfox.com unstable Release                                                         
Ign http://ppa.launchpad.net isadora Release                                                        
Hit http://ppa.launchpad.net lucid Release                                                          
Ign http://packages.linuxmint.com isadora/main Packages                                             
Hit http://linux.dropbox.com maverick/main Packages                                                 
Hit http://ppa.launchpad.net lucid/main Packages                                                    
Ign http://getswiftfox.com unstable/non-free Packages                                               
Hit http://archive.ubuntu.com lucid-updates Release                                                 
Hit http://security.ubuntu.com lucid-security/main Packages                                         
Hit http://archive.canonical.com lucid/partner Packages                                             
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US                                 
Ign http://ppa.launchpad.net isadora/main Packages                                                  
Ign http://getswiftfox.com unstable/non-free Packages                                               
Ign http://packages.linuxmint.com isadora/upstream Packages                                         
Ign http://packages.linuxmint.com isadora/import Packages                                           
Ign http://packages.linuxmint.com isadora-kde/main Packages                                         
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                     
Ign http://packages.linuxmint.com isadora-kde/import Packages                                       
Hit http://archive.ubuntu.com lucid/main Packages                                                   
Hit http://archive.ubuntu.com lucid/restricted Packages                                             
Hit http://archive.ubuntu.com lucid/universe Packages                                               
Hit http://archive.ubuntu.com lucid/multiverse Packages                                             
Hit http://security.ubuntu.com lucid-security/restricted Packages                                   
Hit http://security.ubuntu.com lucid-security/universe Packages                                     
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                   
Hit http://ppa.launchpad.net lucid/main Packages                                                    
Ign http://packages.linuxmint.com isadora/main Packages                                             
Hit http://getswiftfox.com unstable/non-free Packages                                               
Ign http://ppa.launchpad.net isadora/main Packages                                                  
Hit http://archive.ubuntu.com lucid-updates/main Packages                                           
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                     
Hit http://packages.medibuntu.org lucid Release                                                     
Err http://ppa.launchpad.net isadora/main Packages                                                  
  404  Not Found
Hit http://archive.ubuntu.com lucid-updates/universe Packages                                       
Ign http://packages.linuxmint.com isadora/upstream Packages                                         
Ign http://packages.linuxmint.com isadora/import Packages            
Ign http://packages.linuxmint.com isadora-kde/main Packages          
Ign http://packages.linuxmint.com isadora-kde/upstream Packages      
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages      
Ign http://packages.linuxmint.com isadora-kde/import Packages
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.linuxmint.com isadora/main Packages
Hit http://packages.medibuntu.org lucid/non-free Packages 
Hit http://packages.linuxmint.com isadora/upstream Packages
Hit http://packages.linuxmint.com isadora/import Packages                                           
Hit http://packages.linuxmint.com isadora-kde/main Packages                                         
Hit http://packages.linuxmint.com isadora-kde/upstream Packages                                     
Hit http://packages.linuxmint.com isadora-kde/import Packages                                       
Fetched 13.9kB in 9s (1,490B/s)                                                                     
W: Failed to fetch http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
limo@mint ~ $ sudo apt-get install fjbtndrv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fjbtndrv
limo@mint ~ $ 

```I had a problem with firefox before but I downloaded and extracted to home partition...
I wonder if there is any relation!

Given this situation, what do you think if I should make a fresh install of the latest Linux Mint 10 KDE 64 bit and try doing it myself as per this thread?
would you help me then if I got stuck?
Please...
OK?

---

### Post by Favux on 2011-03-13
Alright, that may be the best course.  It is looking like you really scrambled things with FireFox and that's what's causing the problems.  Be sure you do all the updates once installed.

---

### Post by limotux on 2011-03-16
OK... 
it seems I won't be upgrading to 11.04 soon... maybe the next release as  I found 11.04 so strange, slow rendering... and other problems.

I reinstalled LM 9 (Lucid), KDE, 32 bit. I updated and upgraded everything now.
I'll appreciate helping me again step by step.
I don't want to mess things up again.

I know I'm asking a lot... but I really need to start doing serious work...

---

### Post by Favux on 2011-03-16
Well Natty is still Alpha.  And the Unity interface will probably have teething problems for a while.

Let's try to get some baselines on your Mint install this time before we do anything so we know where we're starting from.

Let's nail down the kernel and X server versions:
```
Xorg -version
```
What version of xf86-input-wacom does Synaptic Package Manager say you have?  It's the xserver-xorg-input-wacom package.  Also let's see what:
```
xinput list
```
looks like along with your Xorg.O.log in /var/log.

---

### Post by limotux on 2011-03-18
```
limo@lm ~ $ Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux lm 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-29-generic root=UUID=2aba6757-fdf0-4716-9853-07937c57dd84 ro quiet splash
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.

```and 

```
limo@lm ~ $ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                         id=12   [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=15   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=16   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                       id=17   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=18   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=9    [slave  keyboard (3)]
    &#8627; Power Button                              id=10   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=11   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=13   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
limo@lm ~ $ 

```I really appreciate your kind help.

---

### Post by Favux on 2011-03-18
Hi limotux,

OK, we're basically back to a "Lucid" install which should mean you have the default xserver-xorg-input-wacom package.  The version should be 0.10.5.  That's the package that contains xf86-input-wacom.  You should check in Synaptic Package Manager and verify the version.

That version does not recognize that your Fujitsu tablet PC has touch which is why we aren't seeing a touch device in the *xinput list*.  What would be good is to have the baseline Xorg.0.log that confirms that touch isn't seen.  Remember it is in /var/log.  To compress it use right click Create Archive and then attach it to your next post with Manage Attachments below.

After that the next step is to update the xf86-input-wacom by cloning it's git repository.  That's part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  It should go pretty quick for you this time.  After you reboot *xinput list* should show touch and it should be working.

---

### Post by limotux on 2011-03-19
ok... here is "file:///var/log/Xorg.0.log"

---

### Post by Favux on 2011-03-19
Thanks.  The Xorg.0.log shows what we expected.  The stylus and eraser are happily set up (and should be working) but there's no sign of touch with 0.10.5, so time to update xf86-input-wacom.

---

### Post by limotux on 2011-03-19
hi Favux... everything went fine until:
```
limo@lm ~/limo/Linux_Files/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:45: error: xorg-macros version 1.8 or higher is required but 1.5.0 found
/usr/share/aclocal/xorg-macros.m4:39: XORG_MACROS_VERSION is expanded from...
configure.ac:45: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
limo@lm ~/limo/Linux_Files/xf86-input-wacom $ 
limo@lm ~/limo/Linux_Files/xf86-input-wacom $ make
make: *** No targets specified and no makefile found.  Stop.
limo@lm ~/limo/Linux_Files/xf86-input-wacom $ 

```

---

### Post by Favux on 2011-03-19
Right, remember Lucid (your Mint) has Xorg macros 1.5.  Follow the steps just above cloning the git to update macros from 1.5 to 1.8 before cloning the git.  It's the second step in **a) First**, "For Lucid only update to xorg-macros v. 1.8".

---

### Post by limotux on 2011-03-19
This is what I already did... and repeated as you mentioned... see the attached file

---

### Post by Favux on 2011-03-19
Well it is saying:
```
configure.ac:45: error: xorg-macros version 1.8 or higher is required but 1.5.0 found

```
You can check the xorg-macros.m4 file in the /usr/share/aclocal directory with right click Properties and make sure it has todays date so you know it is the file you compiled.

So repeat the macro compile and reboot before you go on to do the git clone.

---

### Post by limotux on 2011-03-20
hi..
I rebooted, repeated section II, now stylus working, still no rotation and no  touch.
Please check the attached file. I noticed there are some error in "make" and
> limo@lm ~/limo/Linux_Files/util-macros-1.8.0/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:40: required file** `../ltmain.sh' not found**
autoreconf: automake failed with exit status: 1
limo@lm ~/limo/Linux_Files/util-macros-1.8.0/xf86-input-wacom $ 

sorry for bothering you that much.

---

### Post by limotux on 2011-03-20
> **Favux said:**
> Well it is saying:
  .. check the xorg-macros.m4 file in the /usr/share/aclocal directory with right click Properties and make sure it has todays date so you know it is the file you compiled.

So repeat the macro compile and reboot before you go on to do the git clone.

the date and time are correct... just few minutes ago as I rebooted.

---

### Post by Favux on 2011-03-20
Ok, you have me thoroughly confused once again.  Why are you cloning xf86-input-wacom inside the util-macros-1.8.0 directory/folder?  i.e.:
```
limo@lm ~/limo/Linux_Files/util-macros-1.8.0/xf86-input-wacom $ 
```
Each (util-macros-1.8.0 & xf86-input-wacom) should be a separate folder on your Desktop, not nested inside each other.  Pay attention to your directory changes when you download them.  Be sure you're in your Desktop for each, so each downloads onto the Desktop.  I'm guessing that's what's confusing the make rules, you're getting things too recursive.  In other words once the macro update is installed that's the last you should need to deal with it and it's folder.

---

### Post by Favux on 2011-03-21
Hi limotux,

I found the main problem.  A copy/paste error occurred somehow in the last edit or two and the line to download "util-macros-1.8.0.tar.bz2" got garbled.  I fixed it.  Sorry.

---

### Post by limotux on 2011-03-21
Hi Favux, thanks for your patience with me...
sorry... I don't understand your latest post. I believe I just used the folder Linux_Files instead of the desktop to avoid clutter...

mmm... what to do now? where was the error?

---

### Post by Favux on 2011-03-21
The error was in downloading the util-macros-1.8.0 update for Lucid.  The line was wrong and wasn't downloading util-macros, but is now fixed.  So now you can update the macros and then clone the git repository.

---

### Post by tj10001 on 2011-03-23
OK my stylus is working and so is my touch screen, but for some reason I just can't get multi touch to work.

---

### Post by Favux on 2011-03-23
Hi tj10001,

Welcome to Ubuntu forums!

Let's see if Xinput sees touch.  What's the output in a terminal of:
```
xinput list
```
And then what does the wacom X driver see?
```
xsetwacom list
```

---

### Post by limotux on 2011-03-24
> **Favux said:**
> The error was in downloading the util-macros-1.8.0 update for Lucid.  The line was wrong and wasn't downloading util-macros, but is now fixed.  So now you can update the macros and then clone the git repository.

Hi Favux, 
I repeated everything from the beginning as shown at  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Still seems there is a problem. Please check the attached file especially the end.

I appreciate your help. I feel stuck.

I'll reboot now and see what happens.

Edit: after reboot same as before, only stilus working, no touch, no rotate, no buttons.
Please take my hand step by step.

---

### Post by Favux on 2011-03-24
Hi limotux,

Let me repeat again.  linuxwacom-0.8.8-11 doesn't do anything for you.  That's only to make the usb kernel driver wacom.ko which your serial tablet doesn't need.


Hi tj10001,

Welcome to Ubuntu forums!

Do you see touch in *xinput list*?  Have you tried the xsetwacom commands to turn touch and gestures on?
```

xsetwacom set "Serial Wacom Tablet touch" Touch on  # or off
xsetwacom set "Serial Wacom Tablet touch" Gesture on  # or off

```
Using the "device name" you see in *xinput list* of course, but that's probably it.

---

### Post by limotux on 2011-03-24
> **Favux said:**
> Hi limotux,

Let me repeat again.  linuxwacom-0.8.8-11 doesn't do anything for you.  That's only to make the usb kernel driver wacom.ko which your serial tablet doesn't need.


....




**ok... but I'm still lost... please help.. been trying but I'm going nowhere **:(

---

### Post by Favux on 2011-03-24
Please reread this stuff if you haven't and take notes if you haven't.  It just isn't that hard.  I suspect you have some sort of mental block going on.

You have to help me.  For example what does *xinput list* show?  You should be seeing your input devices if you compiled xf86-input-wacom successfully, you know stylus, eraser, and touch.  Give me concrete things to work with.  You already know enough to do all of this on your own.

---

### Post by limotux on 2011-03-25
hi Favux,

The problem is that I am trying to repeat things as we did before but getting some errors.. at the same time I don't understand fully everything.

Anyway, as you requested here is the output:
```
limo@lm ~ $ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                         id=12   [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=15   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=16   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=17   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=18   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                 id=19   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=9    [slave  keyboard (3)]
    &#8627; Power Button                              id=10   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=11   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=13   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
limo@lm ~ $ 

```and I can only understand that wacom is installed for stylus and touch...
but can't understand why only stylus working without touch, rotation, and buttons.

If you remember, the same steps worked for john but not for me, you mentioned [here]("http://ubuntuforums.org/showpost.php?p=10584614&postcount=163") that there was a problem and you corrected it... 

and though I understand that in the above output that  "Serial Wacom Tablet eraser" are installed I dont understand what does " id=18   [slave  pointer  (2)]" mean or what to do with it.

On the other hand, you said I can install fjbtndrv [as per your post]("http://ubuntuforums.org/showpost.php?p=10541352&postcount=142") 

but I get:
```
limo@lm ~ $ sudo add-apt-repository ppa:khnz/ppa
[sudo] password for limo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 13656879026EA184512DC7C8ACCA38C8E88D7B6F
gpg: requesting key E88D7B6F from hkp server keyserver.ubuntu.com
gpg: key E88D7B6F: public key "Launchpad PPA for Robert Gerlach" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
limo@lm ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                                                       
Ign file: binary/ Release                                                                                             
Ign file: binary/ Packages                                                                                            
Ign file: binary/ Packages                                                                                            
Ign http://ppa.launchpad.net isadora Release.gpg                                                                      
Ign http://ppa.launchpad.net/khnz/ppa/ubuntu/ isadora/main Translation-en_US                                          
Hit http://ppa.launchpad.net lucid Release.gpg                                                                        
Hit http://linux.dropbox.com maverick Release.gpg                                                                     
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US                                                  
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                                                        
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US                                                     
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US                                                 
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US                                                   
Ign http://packages.linuxmint.com isadora-kde Release.gpg                                                             
Ign http://packages.linuxmint.com/ isadora-kde/main Translation-en_US                                                 
Ign http://packages.linuxmint.com/ isadora-kde/upstream Translation-en_US                                             
Hit http://archive.canonical.com lucid Release.gpg                                                                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                              
Hit http://archive.ubuntu.com lucid Release.gpg                                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                              
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ lucid/main Translation-en_US                                     
Ign http://ppa.launchpad.net isadora Release                                                                          
Hit http://linux.dropbox.com maverick Release                                                                         
Get:2 http://security.ubuntu.com lucid-security Release.gpg [198B]                                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                    
Ign http://packages.linuxmint.com/ isadora-kde/import Translation-en_US                                               
Get:3 http://packages.linuxmint.com isadora Release [7,235B]                                                          
Hit http://archive.canonical.com lucid Release                                                                        
Hit http://ppa.launchpad.net lucid Release                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                              
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                      
Hit http://linux.dropbox.com maverick/main Packages                                                                   
Hit http://archive.ubuntu.com lucid Release                                                                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                    
Get:4 http://security.ubuntu.com lucid-security Release [44.7kB]                                                      
Get:5 http://packages.linuxmint.com isadora-kde Release [6,464B]                                                      
Ign http://ppa.launchpad.net isadora/main Packages                                                                    
Hit http://archive.canonical.com lucid/partner Packages                                                               
Hit http://archive.ubuntu.com lucid-updates Release                                                                   
Hit http://ppa.launchpad.net lucid/main Packages                                                                      
Hit http://archive.ubuntu.com lucid/main Packages                                                                     
Hit http://archive.ubuntu.com lucid/restricted Packages                                                               
Hit http://archive.ubuntu.com lucid/universe Packages                                                                 
Hit http://archive.ubuntu.com lucid/multiverse Packages                                                               
Ign http://ppa.launchpad.net isadora/main Packages                                                                    
Ign http://packages.linuxmint.com isadora/main Packages                                                               
Err http://ppa.launchpad.net isadora/main Packages                                                                    
  404  Not Found
Hit http://archive.ubuntu.com lucid-updates/main Packages                                                             
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                                       
Ign http://packages.linuxmint.com isadora/upstream Packages                                                           
Ign http://packages.linuxmint.com isadora/import Packages                                                             
Ign http://packages.linuxmint.com isadora-kde/main Packages                                                           
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                                       
Ign http://packages.linuxmint.com isadora-kde/import Packages                                                         
Get:6 http://security.ubuntu.com lucid-security/main Packages [160kB]                                                 
Hit http://archive.ubuntu.com lucid-updates/universe Packages                                                         
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                                                       
Ign http://packages.linuxmint.com isadora/main Packages                                                               
Ign http://packages.linuxmint.com isadora/upstream Packages                                                           
Ign http://packages.linuxmint.com isadora/import Packages                                                             
Ign http://packages.linuxmint.com isadora-kde/main Packages                                                
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                            
Ign http://packages.linuxmint.com isadora-kde/import Packages                                              
Hit http://packages.linuxmint.com isadora/main Packages                                                               
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]                                             
Get:8 http://security.ubuntu.com lucid-security/universe Packages [65.9kB]                                            
Get:9 http://security.ubuntu.com lucid-security/multiverse Packages [1,990B]                                          
Hit http://packages.linuxmint.com isadora/upstream Packages                                                           
Hit http://packages.linuxmint.com isadora/import Packages                                                             
Hit http://packages.linuxmint.com isadora-kde/main Packages                                                           
Hit http://packages.linuxmint.com isadora-kde/upstream Packages                                                       
Hit http://packages.rssowl.org lucid Release.gpg                                                                      
Ign http://packages.rssowl.org/ubuntu/ lucid/main Translation-en_US                                                   
Hit http://packages.medibuntu.org lucid Release.gpg                                                                   
Hit http://packages.rssowl.org lucid Release                                                                          
Hit http://packages.linuxmint.com isadora-kde/import Packages                                                         
Ign http://packages.rssowl.org lucid/main Packages                                                                    
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                                       
Ign http://packages.rssowl.org lucid/main Packages                                                                    
Hit http://packages.rssowl.org lucid/main Packages                                                                    
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US                                                   
Hit http://packages.medibuntu.org lucid Release                                                                       
Hit http://packages.medibuntu.org lucid/free Packages                                                                 
Hit http://packages.medibuntu.org lucid/non-free Packages                                                             
Fetched 287kB in 19s (15.1kB/s)                                                                                       
W: Failed to fetch http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
limo@lm ~ $ 
limo@lm ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                                                       
Ign file: binary/ Release                                                                                             
Ign file: binary/ Packages                                                                                            
Ign file: binary/ Packages                                                                                            
Ign http://ppa.launchpad.net isadora Release.gpg                                                                      
Ign http://ppa.launchpad.net/khnz/ppa/ubuntu/ isadora/main Translation-en_US                                          
Hit http://ppa.launchpad.net lucid Release.gpg                                                                        
Hit http://linux.dropbox.com maverick Release.gpg                                                                     
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US                                                  
Hit http://security.ubuntu.com lucid-security Release.gpg                                                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                    
Hit http://archive.ubuntu.com lucid Release.gpg                                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                              
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                                                        
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US                                                     
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US                                                 
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US                                                   
Ign http://packages.linuxmint.com isadora-kde Release.gpg                                                             
Ign http://packages.linuxmint.com/ isadora-kde/main Translation-en_US                                                 
Ign http://packages.linuxmint.com/ isadora-kde/upstream Translation-en_US                                             
Ign http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/ lucid/main Translation-en_US                                     
Hit http://archive.canonical.com lucid Release.gpg                                                                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                              
Ign http://ppa.launchpad.net isadora Release                                                                          
Hit http://linux.dropbox.com maverick Release                                                                         
Hit http://packages.rssowl.org lucid Release.gpg                                                                      
Ign http://packages.rssowl.org/ubuntu/ lucid/main Translation-en_US                                                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                    
Hit http://packages.medibuntu.org lucid Release.gpg                                                                   
Hit http://security.ubuntu.com lucid-security Release                                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                              
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                      
Hit http://archive.ubuntu.com lucid Release                                                                           
Ign http://packages.linuxmint.com/ isadora-kde/import Translation-en_US                                               
Hit http://ppa.launchpad.net lucid Release                                                                            
Get:2 http://packages.linuxmint.com isadora Release [7,235B]                                                          
Hit http://linux.dropbox.com maverick/main Packages                                                                   
Hit http://archive.canonical.com lucid Release                                                                        
Hit http://packages.rssowl.org lucid Release                                                                          
Ign http://ppa.launchpad.net isadora/main Packages                                                                    
Hit http://security.ubuntu.com lucid-security/main Packages                                                           
Hit http://archive.ubuntu.com lucid-updates Release                                                                   
Get:3 http://packages.linuxmint.com isadora-kde Release [6,464B]                                                      
Hit http://ppa.launchpad.net lucid/main Packages                                                                      
Hit http://archive.canonical.com lucid/partner Packages                                                               
Ign http://packages.rssowl.org lucid/main Packages                                                                    
Ign http://ppa.launchpad.net isadora/main Packages                                                                    
Hit http://security.ubuntu.com lucid-security/restricted Packages                                                     
Hit http://security.ubuntu.com lucid-security/universe Packages                            
Hit http://security.ubuntu.com lucid-security/multiverse Packages                          
Hit http://archive.ubuntu.com lucid/main Packages                                          
Hit http://archive.ubuntu.com lucid/restricted Packages              
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Ign http://packages.linuxmint.com isadora/main Packages
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                                                  
[B]Err http://ppa.launchpad.net isadora/main Packages                                                               
  404  Not Found[/B]
Hit http://archive.ubuntu.com lucid-updates/main Packages                                                             
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                                       
Ign http://packages.rssowl.org lucid/main Packages                                                                    
Ign http://packages.linuxmint.com isadora/upstream Packages                                                           
Ign http://packages.linuxmint.com isadora/import Packages                                             
Ign http://packages.linuxmint.com isadora-kde/main Packages                                                           
Ign http://packages.linuxmint.com isadora-kde/upstream Packages                                                       
Ign http://packages.linuxmint.com isadora-kde/import Packages                                         
Hit http://packages.rssowl.org lucid/main Packages                                                    
Hit http://archive.ubuntu.com lucid-updates/universe Packages        
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://packages.linuxmint.com isadora/main Packages
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Ign http://packages.linuxmint.com isadora/upstream Packages                                                     
Ign http://packages.linuxmint.com isadora/import Packages
Ign http://packages.linuxmint.com isadora-kde/main Packages
Ign http://packages.linuxmint.com isadora-kde/upstream Packages
Hit http://packages.medibuntu.org lucid Release
Ign http://packages.linuxmint.com isadora-kde/import Packages
Hit http://packages.linuxmint.com isadora/main Packages   
Hit http://packages.medibuntu.org lucid/free Packages                                                                 
Hit http://packages.linuxmint.com isadora/upstream Packages                                                           
Hit http://packages.medibuntu.org lucid/non-free Packages                                                             
Hit http://packages.linuxmint.com isadora/import Packages                                                             
Hit http://packages.linuxmint.com isadora-kde/main Packages                                                           
Hit http://packages.linuxmint.com isadora-kde/upstream Packages                                                       
Hit http://packages.linuxmint.com isadora-kde/import Packages                                                         
Fetched 13.9kB in 11s (1,218B/s)                                                                                      
[B]W: Failed to fetch http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]
limo@lm ~ $ 
limo@lm ~ $ sudo apt-get install fjbtndrv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]E: Couldn't find package fjbtndrv
limo@lm ~ $ [/B]

```
What is my mistake here? (in bold) is it my fault? All what I can say that I might be so unlucky, there is nothing I can do wrong in a copy/paste thing.

well... what do you think?

---

### Post by limotux on 2011-03-25
Hi...
Now multitouch working after doing the above.

Still no fjbtndrv, no rotate...

as in [http://ubuntuforums.org/showthread.php?t=1116103&highlight=fjbtndrv](http://ubuntuforums.org/showthread.php?t=1116103&highlight=fjbtndrv) 
sudo add-apt-repository ppa:khnz; sudo apt-get update; sudo apt-get -y install fjbtndrv
is not working for me! I'm getting 
> limo@lm ~/limo/Linux_Files/fjbtndrv-2.2.1 $ sudo apt-get -y install fjbtndrv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package fjbtndrv**
limo@lm ~/limo/Linux_Files/fjbtndrv-2.2.1 $ 

---

### Post by limotux on 2011-03-25
Hi Favux,

What about the .deb packages at [https://launchpad.net/~khnz/+archive/ppa/+buildjob/1996623]("https://launchpad.net/%7Ekhnz/+archive/ppa/+buildjob/1996623")

fjbtndrv as I read is not that easy for most.

---

### Post by Favux on 2011-03-26
Outstanding!  Nice work getting multi-touch working.  :)

But see that's what I mean.  You say:
> Now multitouch working after doing the above.
But "what above".  You don't tell me.  My guess is you compiled and installed the macro 1.8 update and successfully cloned the xf86-input-wacom repository.  But it is just a guess.

The fjbtndrv seems to want the Isadora-kde package for translation for some reason and that's the hang up.  Not sure if that's a packaging problem with the PPA or maybe Mint doesn't have Isadora available.  Either that or your package list is mangled again.

So what's true?:
Your in the Mint equivalent of Lucid.  Yes?
Are you using a KDE version of Mint?
Your Mint install is not in English, correct?

Yes you should be able to use a deb.  But the deb you link to is for 32-bit installs - i386.  Is your install 32-bit, possible if it is KDE, or 64-bit?  To find out check which kernel you are running:
```
uname -r
```
The deb should just fail to install if you have a 32-bit deb and try to install it on a 64-bit system.  It'll give an error message but shouldn't harm anything.

---

### Post by limotux on 2011-03-27
well... finally everything is sorted out. 
The reason for the error message that fjbtndrv could not install maybe was the file requested was at [I][http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/](http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/)**isadora**/main/binary-i386/Packages.gz

I thought of changing the repo to [/I][I][http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/](http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/)**lucid**/main/binary-i386/Packages.gz and it worked fine.

I wonder why, as I'm on linux mint, 32 bit, Isadora!, KDE, and my installation is English.

Then I edited the .sh file to correct the problem of the touch and stylus working the opposite direction as previously done here [http://ubuntuforums.org/showpost.php?p=10321906&postcount=85](http://ubuntuforums.org/showpost.php?p=10321906&postcount=85)

I'm still trying to get the eraser to work as it is still working as another tip of the stylus.
Buttons on stylus, only one button working, it seams to me the other is not.

Any Ideas?
[/I]

---

### Post by Favux on 2011-03-27
Excellent!
> The reason for the error message that fjbtndrv could not install maybe was the file requested was at [http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz](http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz)
I thought of changing the repo to [http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz) and it worked fine.
Thanks for educating me.  I thought Isadora! was a package, instead it is the code name for Mint 9.0.  lol  Since the PPA is for Ubuntu Isadora (Mint 9) isn't used in the directory paths, Lucid is.  So to get the correct directory path you had to change Isadora (what the Mint package manager assumed) to Lucid, which is what the PPA was looking for.

> I'm still trying to get the eraser to work as it is still working as another tip of the stylus.
Have you configured it in the extended input devices in Gimp or Inkscape (or the equivalent in other programs)?  See the screen shots near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
> Buttons on stylus, only one button working, it seems to me the other is not.
Try running in a terminal:
> 
xsetwacom set "Serial Wacom Tablet stylus" Button 2 3
xsetwacom set "Serial Wacom Tablet stylus" Button 3 2

That should be the default, but see if using xsetwacom kick starts something.

---

### Post by limotux on 2011-03-28
```
limo@lm ~ $ xsetwacom set "Serial Wacom Tablet stylus" Button 2 3
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  23
limo@lm ~ $ 

``````
limo@lm ~ $ xsetwacom set "Serial Wacom Tablet stylus" Button 3 2
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  23
limo@lm ~ $ 

```and nothing happens... still no eraser.
In Jarnal I can erase by selecting eraser, but unfortunately it deletes the whole line not what I only erase! It could be a problem seting up or configuring Jarnal?

p.s. I didn't download this [http://ubuntuforums.org/showpost.php?p=10319070&postcount=79](http://ubuntuforums.org/showpost.php?p=10319070&postcount=79)
could it be the reason?

---

### Post by Favux on 2011-03-28
With an updated xf86-input-wacom Button 2, not Button2 should be the correct parameter name.  So I guess it is saying 3 (right click) is out of range, which is crazy.  There seems to be several people with this recently and I don't know why for sure.  Bug in xf86-input-wacom or problem with a Xinput update?

I suppose it could be you need to come up with a script but first I would check in /usr/local/bin for a xsetwacom binary/executable (it should be in /usr/bin). This may mean you forgot the '--prefix=/usr' flag on the xf86-input-wacom configure line. In which case you may have a xsetwacom executable in both locations and are experiencing version conflict. Delete the one in the wrong location, i.e. /usr/local/bin. If this isn't the case then just try re-cloning the xf86-input-wacom git repository and see if copying everything into place fixes things.

---

### Post by limotux on 2011-03-31
hi... 
sorry for the delay... was so busy past few days.

well, from [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) I copied the shown file "10-wacom.conf" into it's place, rebooted, nothing happens.

what does this mean: ```
*NOTE: there is no package **wacom-tools** in Ubuntu 10.04 any more, **so you'll have to use your tablet without it**.*
```Can this be the reason?
I'll keep reading and trying.
If you can advise me I'll appreciate it.

Just to be sure, the eraser is working as a tool from Jarnal (both sides of stylus doing the same thing), but what really bothers me is that deletes the whole line not just the part of it I try to erase.

p.s. would installing [http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb](http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb) from [https://launchpad.net/ubuntu/lucid/+package/wacom-tools](https://launchpad.net/ubuntu/lucid/+package/wacom-tools) help?

---

### Post by Favux on 2011-03-31
wacom-tools contained xsetwacom, wcmcpl, wacdump, and xidump.  Xsetwacom is now part of the regular xf86-input-wacom package so the version in that wacom-tools would not only be obsolete but most likely conflict.  The other 3 are not supported anymore by the xf86-input-wacom X driver and were dropped.  If you installed it that might explain why things don't work correctly.

The wacom.conf from the Wacom wiki isn't correct.  Use the one in my HOW TO's like the Bamboo P&T HOW TO or the copy in your xf86-input-wacom folder.

---

### Post by limotux on 2011-04-02
Hi, I hope I'm not bothering you with this.
Trying to find my way, I find that the file xsetwacom.sh might need some editing to let it know which button no. is the eraser. (The part I made bold below:
```
Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = "Serial Wacom Tablet stylus" = ID 19
xsetwacom set "Serial Wacom Tablet stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet stylus" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet stylus" PressCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet stylus" TPCButton "on"  # or is  Relative needed for gestures?"  # stylus tip + button, or "off" for  hover mode
xsetwacom set "Serial Wacom Tablet stylus" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet stylus" Button1 "1"  # left mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button2 "3"  # right mouse click
xsetwacom set "Serial Wacom Tm Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## eraser = "Serial Wacom Tablet eraser" = ID 17
[B]xsetwacom set "Serial Wacom Tablet eraser" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet eraser" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet eraser" ClickForce "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Serial Wacom Tablet eraser" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet eraser" PressCurve "0 10 90 100" # Bezier curve, default is 0,0,100,100
xsetwacom set "Serial Wacom Tablet eraser" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Serial Wacom Tablet eraser" Button1 "1"[/B]
# coordinates are the same as uablet stylus" Button3 "2"  # middle mouse click
# sample X200t coordinates, default coordinates in /var/log/Xorg.0.log
#xsetwacom set "Serial Wacosed for the stylus
#xsetwacom set "Serial Wacom Tablet stylus" topx "0"
#xsetwacom set "Serial Wacom Tablet stylus" topy "0"
#xsetwacom set "Serial Wacom Tablet stylus" bottomx "26312"
#xsetwacom set "Serial Wacom Tablet stylus" bottomy "16520"

## depending on your model use the applicable following touch section ##
## I deleted the single finger touch section, jruh ##

## two finger (2FG) or multitouch
## touch = "Serial Wacom Tablet touch" = ID 18
xsetwacom set "Serial Wacom Tablet touch" Touch "on" # default,  or "off"
xsetwacom set "Serial Wacom Tablet touch" Gesture "on"  # or "off"
xsetwacom set "Serial Wacom Tablet touch" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Serial Wacom Tablet touch" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Serial Wacom Tablet touch" ClickForce  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet touch" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"  # or Relative cursor movement; is Relative needed for gestures? 
xsetwacom set "Serial Wacom Tablet touch" TapTime "250"  # default is 250 ms
xsetwacom set "Serial Wacom Tablet touch" Button1 "1"  #  needed for 2FG touch?
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 14 ZoomDistance "50"  # default is 50
xsetwacom set 14 ScrollDistance "2000"  # default is 20
xsetwacom set 14 TapTime "250"  # 2FG R click, default is 250 ms
# sample X200t coordinates
#xsetwacom set "Serial Wacom Tablet touch" topx "?"
#xsetwacom set "Serial Wacom Tablet touch" topy "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomx "?"
#xsetwacom set "Serial Wacom Tablet touch" bottomy "?"

## Developed with vfrjim]
```what do you think?

---

### Post by Favux on 2011-04-02
Not a bother.

Well, as I mentioned before (and in the HOW TO) you have to update the script since you are using xf86-input-wacom-0.10.11+ (i.e. cloned it).  For example ClickForce is now Threshold so you need to comment out ClickForce and remove the comment from Threshold.  The defaults of Suppress and RawSample have reversed (they found they accidentally mixed them up in the code), so:
```
xsetwacom set "device name" Suppress 2
xsetwacom set "device name" RawSample 4

```
See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

Now the button commands change from ButtonX to Button X like we talked about before.  Apparently the problem you had in post #178 is a bug and somebody says you can work around it by using *key* as in:
```
xsetwacom set "Serial Wacom Tablet stylus" Button 2 "key 3"

```
instead of:
```
xsetwacom set "Serial Wacom Tablet stylus" Button 2 3

```
so give that a try and see if it works for you.

---

