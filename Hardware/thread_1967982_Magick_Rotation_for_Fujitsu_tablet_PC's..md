---
title: "Magick Rotation for Fujitsu tablet PC's."
date: 2012-04-28
forum: Hardware
---

### Post by Favux on 2012-04-28
[SIZE="3"][COLOR="Blue"]Fujitsu tablet PC support has been added to Magick Rotation![/COLOR][/SIZE]

Robert Gerlach's new **fujitsu-tablet.ko** has been accepted into the 3.3 kernel.  Amongst other things it provides notification of whether the screen is physically in laptop or tablet mode/orientation.  And yes, this is the Robert Gerlach of the **fjbtndrv PPA**.

**Magick Rotation** is an application that will automatically change screen orientation and input tool (stylus, touch) orientation when you physically rotate the screen.  With Robert's assistance Fujitsu tablet PC's have been added to Magick.  A Fujitsu tablet PC owner, dog-soldier, reports that it works for him:  [http://ubuntuforums.org/showthread.php?t=1966821](http://ubuntuforums.org/showthread.php?t=1966821)

A DKMS (dynamic kernel module support) implementation of the fujitsu-tablet.ko is in the MagickExtras folder along with instructions so the driver can be used with the older kernels in Ubuntu releases including Precise.  The included version of fujitsu-tablet.c (4-4-12) also has Robert's new patch that fixes tablet state reporting for some models (should be in the 3.4 kernel) and another patch from Robert that allows it to build down to the 2.6.32 kernel (Lucid's).

Magick Rotation is here:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)
Revision 33 on Magick's unstable branch is the testing version with the fujitsu-tablet dkms implementation.  Its tarball is here:  [http://bazaar.launchpad.net/~magick-admin-team/magick-rotation/unstable/tarball/33](http://bazaar.launchpad.net/~magick-admin-team/magick-rotation/unstable/tarball/33)  To install, after you right click on the tarball and extract it, drill down to the unstable folder and run MAGICK-INSTALL by double-clicking on it.  It should be executable.  Then install the dkms of fujitsu-table.ko.  As mentioned the dkms package and instructions are in the MagickExtras folder.

To simplify things for yourself you may want to right click on the unstable folder and chose Copy and then Paste it on your Desktop. Then right click on the copied unstable folder on the Desktop and rename it 'magick-rotation' (without the quotes). That will get you to where you'd be with the Magick Rotation 1.6 release tarball (coming soon).  You can remove Magick with MAGICK-UNINSTALL in the MagickUninstall folder.

Please feel free to post your results if you do use Magick Rotation for your Fujitsu tablet PC.

---

### Post by dog-soldier on 2012-04-28
you will also need to install the dkms frame work from the software center in order to install

---

### Post by pvdh on 2012-05-05
Hello,

I made a clean install Ubuntu 12,04 (french ve) on my Fujitsu T4215, with magick rotation : woks perfectly !

I just hesitate to remove dkms install and folder (as explained at the end of the  fujitsu-tablet_README.txt).
Are they unnecessary after installation or do you provide this to uninstall everything ?

And what about further upgrade ? is it possible to add a source list to get the upgrade/stable version when available ?

Finally, i don't understand the option "BIOS hinge switch values reversed" in the setup control panel.

Thanks a lot for this amazing job !

patrick

---

### Post by Favux on 2012-05-05
Hi pvdh,

Welcome to Ubuntu forums!

> I made a clean install Ubuntu 12,04 (french ve) on my Fujitsu T4215, with magick rotation : woks perfectly !
Outstanding!  :)  You are our second tester.
> I just hesitate to remove dkms install and folder (as explained at the end of the fujitsu-tablet_README.txt).
Are they unnecessary after installation or do you provide this to uninstall everything ?
Correct, the dkms install and folder(?) are necessary if you want the fujitsu-tablet.ko on your system.  Those instructions are provided if you want to uninstall everything.  You're right to point out that someone with a Fujitsu tablet PC might want to uninstall Magick Rotation but keep fujitsu-tablet.ko.  Perhaps I should make that clearer.
> And what about further upgrade ? is it possible to add a source list to get the upgrade/stable version when available ?
The "official" version 1.6 should be released shortly.  With you we now have 2 testers confirming.  Usually we like at least 3.

Currently there isn't a Magick Rotation PPA so you can't get an automatic update.  We've chosen to work on our little Installer, and now with version 1.6 companion Uninstaller.  With 1.6 the Installer works in Ubuntu, Mint (and hopefully Debian), Fedora/Redhat, and openSUSE.  And an ARCH pkgbuild is available, but not our work.
> Finally, i don't understand the option "BIOS hinge switch values reversed" in the setup control panel.
Don't worry about that.  That only applies to the HP 4200 and 4400 models.  They do just what it says, return 0 when everyone else returns 1, and 1 for 0.  There is a FAQ on the site for them.
> Thanks a lot for this amazing job !
You are welcome.  Thanks for trying it out!

---

### Post by Cobuntu on 2012-05-05
Hi Favux, me again. I installed it on my Fujitsu T730 running 12.04 x64 by renaming the folder on my Desktop as suggested. The installation seems to have worked, it asked me to restart, the DKMS was already installed and then I also installed the stuff from the MagickExtras according to fujitsu-tablet_README.txt. It also installed but after a restart nothing works. But I have the 'gerlach"-folders you asked for in the above posts.

I guess it might be partly because you have to have working Hardware Buttons? I managed to install those around December 2011 in 11.10 but they stopped working a few weeks later. I have five of those buttons, but only the very right seems to work. It is supposed to send ALT and when I press it, the HUD shows up or disappears. 

In the terminal I am getting output when I press the buttons after
sudo xxd -g1 /dev/input/magick-rotation

---

### Post by Favux on 2012-05-05
Hi Cobuntu,

> n the terminal I am getting output when I press the buttons after
sudo xxd -g1 /dev/input/magick-rotation 
With the magick-rotation symlink present then the fujitsu-table.ko should be present.  But to check do you see the symlink in /dev/input?  Also do you see the gerlach folder in /usr/src?  Do you also see the gerlach folder in /var/lib/dkms?  And in the output of ***lsmod*** do you see **fujitsu-tablet**?
> I guess it might be partly because you have to have working Hardware Buttons? I managed to install those around December 2011 in 11.10 but they stopped working a few weeks later. I have five of those buttons, but only the very right seems to work. It is supposed to send ALT and when I press it, the HUD shows up or disappears. 
No, Magick detects the tablet mode state ACPI signal from the BIOS through the fujitsu-tablet.ko (SW_TABLET).  The fujitsu-tablet.ko should have all the bezel buttons functioning.  Do you see the bezel button's key code and a Press and Release event after you run ***xev*** in a terminal and press a bezel button?  You can bind the Rotation bezel button to a rotation script, see the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830"), if you want.  That's what Robert Gerlach's fjbtndrv has been doing.

---

### Post by Cobuntu on 2012-05-05
Hello favux,

I checked everything:
  	 	 	 	 	 	   

/dev/input: symlink 'magick-rotation', target event8
 
 
/usr/src:
  fujitsu-tablet-2.3.2
  fujitsu-tablet-20120404-gerlach
 

/var/lib/dkms:
  fujitsu-tablet


  in the output of lsmod: fujitsu_tablet         12984  0




after running ***xev*** in a terminal and pressing:
Bezel button 1: nothing
Bezel button 2: nothing
Bezel button 3: nothing
Bezel button 4: curser in terminal starts blinking and the mouse curser on the screen starts blinking as if I press STRG to look for it (if I had set that in mouse settings)
Bezel button 5: curser in terminal starts blinking and the HUD menu appears/disappears

---

### Post by Favux on 2012-05-05
OK, everything looks good.  On Magick's rotating green arrow icon right click and choose Advanced Setup. Check the box by the "Debugging logging tool" and hit Save and close.  Rotate the screen to tablet and back to laptop and post the magick-log.  We'll see what that shows.

Alright it sounds like the bezel buttons need to be set up further.  The Rotation HOW TO talks about how to do that mainly in appendix 2.  It's been a while since I looked at how fjbtndrv handled that.  Not sure I ever understood it, but can't remember.  Basically it sounds like Fujitsu tablet PC's need a **fujitsu-tablet** keymap in /lib/udev/keymaps.  I don't know if it is Ubuntu that does that or if that comes from udev upstream.  Probably the latter.  In which case someone (Robert?) should probably submit one.

---

### Post by Cobuntu on 2012-05-05
Favux, I supose 'Magick's rotating green arrow icon' is supposed to be among Unity's Indicators? I whitelisted all but there is no such button. Could it be that it is not running and if so how do I start it manually?

---

### Post by Favux on 2012-05-05
Interesting.  Go to /usr/share/magick-rotation.  Then double click on the magick-rotation file and choose Run.  The icon should show up in the system tray/notification area.

---

### Post by Cobuntu on 2012-05-05
Ok, I double clicked the file, it opened in gedit. I right clicked and tried to run ans root and user, nothing happened. I right clicked into properties: not marked as executable. I marked it executable and got the indicator. I checked run at startup, restarted and got it immediately. GREAT!



But:
I tried the stylus in laptop mode in xournal. Works perfectly. I turn the hinge and lock it to tabletmode. Screen follows as set in settings. I try the stylus - works perfectly, no offset.
I swich back to laptop mode. I try the stylus - offset, and the same with the finger but not with the touchpad! 
  	 	 	 	 	 	   xsetwacom set "Serial Wacom Tablet stylus" Mode "Absolute"
still offset

 xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"
works perfectly now


Back into tablet mode: stylus + touch in xournal work perfectly
Back into laptop mode: stylus is offset in xournal, touch is perfect. 

But

xsetwacom get "Serial Wacom Tablet stylus" Mode
reads Absolute. 


Here is the log: 

2012-05-06 04:36:57: cur_state: 2 
2012-05-06 04:36:57: old_state: None 
2012-05-06 04:36:57: calling rotation b: 
2012-05-06 04:36:57: right
2012-05-06 04:36:58: calling cellwriter --show-window
2012-05-06 04:36:58: Change to Tablet mode
2012-05-06 04:36:58: checking for rotation
2012-05-06 04:36:58: /usr/bin/checkmagick64
2012-05-06 04:37:16: cur_state: 0 
2012-05-06 04:37:16: old_state: 2 
2012-05-06 04:37:16: calling rotation a: 
2012-05-06 04:37:16: normal
2012-05-06 04:37:16: calling cellwriter --hide-window
2012-05-06 04:37:16: Change to normal state
2012-05-06 04:37:16: checking for rotation
2012-05-06 04:37:16: /usr/bin/checkmagick64
2012-05-06 04:37:43: cur_state: 2 
2012-05-06 04:37:43: old_state: 0 
2012-05-06 04:37:43: calling rotation b: 
2012-05-06 04:37:43: right
2012-05-06 04:37:43: calling cellwriter --show-window
2012-05-06 04:37:43: Change to Tablet mode
2012-05-06 04:37:44: checking for rotation
2012-05-06 04:37:44: /usr/bin/checkmagick64
2012-05-06 04:38:22: cur_state: 0 
2012-05-06 04:38:22: old_state: 2 
2012-05-06 04:38:22: calling rotation a: 
2012-05-06 04:38:22: normal
2012-05-06 04:38:22: calling cellwriter --hide-window
2012-05-06 04:38:22: Change to normal state
2012-05-06 04:38:22: checking for rotation
2012-05-06 04:38:22: /usr/bin/checkmagick64
2012-05-06 04:43:25: checking for rotation
2012-05-06 04:43:25: /usr/bin/checkmagick64
2012-05-06 04:44:04: cur_state: 2 
2012-05-06 04:44:04: old_state: None 
2012-05-06 04:44:04: calling rotation b: 
2012-05-06 04:44:04: right
2012-05-06 04:44:04: calling cellwriter --show-window
2012-05-06 04:44:04: Change to Tablet mode
2012-05-06 04:44:04: checking for rotation
2012-05-06 04:44:04: /usr/bin/checkmagick64
2012-05-06 04:45:01: cur_state: 0 
2012-05-06 04:45:01: old_state: 2 
2012-05-06 04:45:01: calling rotation a: 
2012-05-06 04:45:01: normal
2012-05-06 04:45:01: calling cellwriter --hide-window
2012-05-06 04:45:01: Change to normal state
2012-05-06 04:45:01: checking for rotation
2012-05-06 04:45:01: /usr/bin/checkmagick64
2012-05-06 04:45:55: cur_state: 2 
2012-05-06 04:45:55: old_state: 0 
2012-05-06 04:45:55: calling rotation b: 
2012-05-06 04:45:55: right
2012-05-06 04:45:56: calling cellwriter --show-window
2012-05-06 04:45:56: Change to Tablet mode
2012-05-06 04:45:56: checking for rotation
2012-05-06 04:45:56: /usr/bin/checkmagick64
2012-05-06 04:46:14: cur_state: 0 
2012-05-06 04:46:14: old_state: 2 
2012-05-06 04:46:18: calling rotation a: 
2012-05-06 04:46:18: normal
2012-05-06 04:46:18: calling cellwriter --hide-window
2012-05-06 04:46:18: Change to normal state
2012-05-06 04:46:18: checking for rotation
2012-05-06 04:46:18: /usr/bin/checkmagick64
2012-05-06 04:59:33: cur_state: 2 
2012-05-06 04:59:33: old_state: 0 
2012-05-06 04:59:33: calling rotation b: 
2012-05-06 04:59:33: right
2012-05-06 04:59:33: calling cellwriter --show-window
2012-05-06 04:59:33: Change to Tablet mode
2012-05-06 04:59:33: checking for rotation
2012-05-06 04:59:33: /usr/bin/checkmagick64
2012-05-06 04:59:53: cur_state: 0 
2012-05-06 04:59:53: old_state: 2 
2012-05-06 04:59:54: calling rotation a: 
2012-05-06 04:59:54: normal
2012-05-06 04:59:54: calling cellwriter --hide-window
2012-05-06 04:59:54: Change to normal state
2012-05-06 04:59:54: checking for rotation
2012-05-06 04:59:54: /usr/bin/checkmagick64

---

### Post by Favux on 2012-05-05
Basically it works but with glitches.

Well first I just checked the Magick Rotation site rev. 33 and the magick-rotation file should have been downloaded as executable.  I'm a bit baffled as to how it was changed on your Fujitsu.  So weird.  Nice job figuring that out by the way.

The offset is another weird thing.  Have you installed CellWriter?  If not do so and see what happens.

What's the output of:
```
xsetwacom list
```
again when all of this is going on?

Otherwise maybe it is something to do with the touch being set to "Relative" problem you're having.  I need to think about this a bit.  Thank you for the debugging_log.

---

### Post by Cobuntu on 2012-05-06
Favux, you were right, I did not have CellWriter installed. I installed it and did not apply the touch patch. I tested in Xournal:
Notebook Mode: Touch offset, Stylus perfect (to clarify: whenever I do not apply the Wacom workaround the finger is offset like 4 centimeters south-west from where it actually appears on the screen)
> Tablet Mode: Touch offset, Stylus offset - but when I go with the stylus into CellWriter Training Mode it works perfectly within CellWriter. Touch is as offset as out of CellWriter.
> Notebook Mode: Touch offset, Stylus perfect again; when I try the Touch here, it suddenly is offset like 2 centimeters north-west within Cell-Writer. Changing in and out of CellWriter with the finger it changes direction and length of the offset every time. Stylus still perfect.
> Tablet Mode: as above
> Notebook Mode: as above

$xsetwacom list
Serial Wacom Tablet stylus          id: 16    type: STYLUS    
Serial Wacom Tablet eraser          id: 17    type: ERASER    
Serial Wacom Tablet touch           id: 18    type: TOUCH     


magick-log:
2012-05-06 04:36:57: cur_state: 2 
2012-05-06 04:36:57: old_state: None 
2012-05-06 04:36:57: calling rotation b: 
2012-05-06 04:36:57: right
2012-05-06 04:36:58: calling cellwriter --show-window
2012-05-06 04:36:58: Change to Tablet mode
2012-05-06 04:36:58: checking for rotation
2012-05-06 04:36:58: /usr/bin/checkmagick64
2012-05-06 04:37:16: cur_state: 0 
2012-05-06 04:37:16: old_state: 2 
2012-05-06 04:37:16: calling rotation a: 
2012-05-06 04:37:16: normal
2012-05-06 04:37:16: calling cellwriter --hide-window
2012-05-06 04:37:16: Change to normal state
2012-05-06 04:37:16: checking for rotation
2012-05-06 04:37:16: /usr/bin/checkmagick64
2012-05-06 04:37:43: cur_state: 2 
2012-05-06 04:37:43: old_state: 0 
2012-05-06 04:37:43: calling rotation b: 
2012-05-06 04:37:43: right
2012-05-06 04:37:43: calling cellwriter --show-window
2012-05-06 04:37:43: Change to Tablet mode
2012-05-06 04:37:44: checking for rotation
2012-05-06 04:37:44: /usr/bin/checkmagick64
2012-05-06 04:38:22: cur_state: 0 
2012-05-06 04:38:22: old_state: 2 
2012-05-06 04:38:22: calling rotation a: 
2012-05-06 04:38:22: normal
2012-05-06 04:38:22: calling cellwriter --hide-window
2012-05-06 04:38:22: Change to normal state
2012-05-06 04:38:22: checking for rotation
2012-05-06 04:38:22: /usr/bin/checkmagick64
2012-05-06 04:43:25: checking for rotation
2012-05-06 04:43:25: /usr/bin/checkmagick64
2012-05-06 04:44:04: cur_state: 2 
2012-05-06 04:44:04: old_state: None 
2012-05-06 04:44:04: calling rotation b: 
2012-05-06 04:44:04: right
2012-05-06 04:44:04: calling cellwriter --show-window
2012-05-06 04:44:04: Change to Tablet mode
2012-05-06 04:44:04: checking for rotation
2012-05-06 04:44:04: /usr/bin/checkmagick64
2012-05-06 04:45:01: cur_state: 0 
2012-05-06 04:45:01: old_state: 2 
2012-05-06 04:45:01: calling rotation a: 
2012-05-06 04:45:01: normal
2012-05-06 04:45:01: calling cellwriter --hide-window
2012-05-06 04:45:01: Change to normal state
2012-05-06 04:45:01: checking for rotation
2012-05-06 04:45:01: /usr/bin/checkmagick64
2012-05-06 04:45:55: cur_state: 2 
2012-05-06 04:45:55: old_state: 0 
2012-05-06 04:45:55: calling rotation b: 
2012-05-06 04:45:55: right
2012-05-06 04:45:56: calling cellwriter --show-window
2012-05-06 04:45:56: Change to Tablet mode
2012-05-06 04:45:56: checking for rotation
2012-05-06 04:45:56: /usr/bin/checkmagick64
2012-05-06 04:46:14: cur_state: 0 
2012-05-06 04:46:14: old_state: 2 
2012-05-06 04:46:18: calling rotation a: 
2012-05-06 04:46:18: normal
2012-05-06 04:46:18: calling cellwriter --hide-window
2012-05-06 04:46:18: Change to normal state
2012-05-06 04:46:18: checking for rotation
2012-05-06 04:46:18: /usr/bin/checkmagick64
2012-05-06 04:59:33: cur_state: 2 
2012-05-06 04:59:33: old_state: 0 
2012-05-06 04:59:33: calling rotation b: 
2012-05-06 04:59:33: right
2012-05-06 04:59:33: calling cellwriter --show-window
2012-05-06 04:59:33: Change to Tablet mode
2012-05-06 04:59:33: checking for rotation
2012-05-06 04:59:33: /usr/bin/checkmagick64
2012-05-06 04:59:53: cur_state: 0 
2012-05-06 04:59:53: old_state: 2 
2012-05-06 04:59:54: calling rotation a: 
2012-05-06 04:59:54: normal
2012-05-06 04:59:54: calling cellwriter --hide-window
2012-05-06 04:59:54: Change to normal state
2012-05-06 04:59:54: checking for rotation
2012-05-06 04:59:54: /usr/bin/checkmagick64
2012-05-06 09:51:59: checking for rotation
2012-05-06 09:52:00: /usr/bin/checkmagick64
2012-05-06 10:04:03: cur_state: 2 
2012-05-06 10:04:03: old_state: None 
2012-05-06 10:04:03: calling rotation b: 
2012-05-06 10:04:03: right
2012-05-06 10:04:03: calling cellwriter --show-window
2012-05-06 10:04:03: Change to Tablet mode
2012-05-06 10:04:03: checking for rotation
2012-05-06 10:04:03: /usr/bin/checkmagick64
2012-05-06 10:05:09: cur_state: 0 
2012-05-06 10:05:09: old_state: 2 
2012-05-06 10:05:09: calling rotation a: 
2012-05-06 10:05:09: normal
2012-05-06 10:05:09: calling cellwriter --hide-window
2012-05-06 10:05:09: Change to normal state
2012-05-06 10:05:09: checking for rotation
2012-05-06 10:05:09: /usr/bin/checkmagick64
2012-05-06 10:05:59: cur_state: 2 
2012-05-06 10:05:59: old_state: 0 
2012-05-06 10:06:00: calling rotation b: 
2012-05-06 10:06:00: right
2012-05-06 10:06:00: calling cellwriter --show-window
2012-05-06 10:06:00: Change to Tablet mode
2012-05-06 10:06:00: checking for rotation
2012-05-06 10:06:00: /usr/bin/checkmagick64
2012-05-06 10:06:14: cur_state: 0 
2012-05-06 10:06:14: old_state: 2 
2012-05-06 10:06:14: calling rotation a: 
2012-05-06 10:06:14: normal
2012-05-06 10:06:14: calling cellwriter --hide-window
2012-05-06 10:06:14: Change to normal state
2012-05-06 10:06:15: checking for rotation
2012-05-06 10:06:15: /usr/bin/checkmagick64
2012-05-06 10:19:44: cur_state: 2 
2012-05-06 10:19:44: old_state: 0 
2012-05-06 10:19:44: calling rotation b: 
2012-05-06 10:19:44: right
2012-05-06 10:19:44: calling cellwriter --show-window
2012-05-06 10:19:44: Change to Tablet mode
2012-05-06 10:19:45: checking for rotation
2012-05-06 10:19:45: /usr/bin/checkmagick64
2012-05-06 10:20:28: cur_state: 0 
2012-05-06 10:20:28: old_state: 2 
2012-05-06 10:20:28: calling rotation a: 
2012-05-06 10:20:28: normal
2012-05-06 10:20:28: calling cellwriter --hide-window
2012-05-06 10:20:28: Change to normal state
2012-05-06 10:20:28: checking for rotation
2012-05-06 10:20:28: /usr/bin/checkmagick64

---

### Post by Cobuntu on 2012-05-06
Favux, I switched the 'Rotation State in Tablet Mode' from 'right' to 'inverted' (- because when I migrated from Windows to Ubuntu starting 10.04 I never tried MagickRotation and always had offsets after swiveling. First on my HP tx2 and also since 11.04 when getting a T730. Actually I did not really miss it, because I think since the arrival of widescreen displays on Tablet PCs + especially with Unity, swiffeling right or left is not very useful. But Inverted Mode is!)
So now in Tablet-Mode with the inverted setting, the stylus is NOT offset, it is working perfectly in Xournal and within CellWriter.

---

### Post by Favux on 2012-05-06
Inverted is perfectly fine.

With regard to Portrait orientations there are a couple of things to look at.  First remember you can run shell commands in Magick using Advanced Setup.  Remember to separate them by a ';'.

On tablet PCs while stylus/eraser are usually calibrated well from the start touch often needs to be calibrated.  And the calibration coordinates you determine applied in either your custom xorg.conf.d or as a xsetwacom Area command.  I have to do that with my usb tablet PC.  You can use **xinput_calibrator** for that.  It is in the repositories (Software Center or Synaptic) as Calibrate Touchscreen but will show up if you search *xinput*.

Less likely there can sometimes be glitches in the video driver.  That used to be a big problem in the old days.  To determine your video chipset enter:
```
lspci | grep VGA
```

---

### Post by Cobuntu on 2012-05-06
Favux, since the MagickRotation seems to work pretty well I would like to have it installed on my new SSD installation as well. Should I better wait for the official 1.6 or is it save to repeat what we did before? This way we would also see if the file is executable on a clean install!?


$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

### Post by Favux on 2012-05-06
Hi Cobuntu,

Since you make tester number 3 confirming the Fujitsu support works I think we are ready to release 1.6.

Unstable rev. 33 is essentially identical to what 1.6 will be.  Unless I figure out how to fix the HP TM2t in the meantime.  I'm getting diagnostics from one shortly, I hope.

So whichever way you want to handle it.

---

### Post by Cobuntu on 2012-05-06
Ok, I'll see if I can hold myself back till 1.6 arrives ;-)) Thank you very much for your support! And I will try what you told me about calibration when I have more time again.

---

### Post by dog-soldier on 2012-05-06
just thought i would report back to let you know all is working great. the only problem i seem to have and im not sure if its with magick rotation or something else' the problem is that in laptop mode the mouse will pop the unity bar out, but is tablet mode the stylus wont pop the unity bar out. i have the sensitivity at the lowest but it still wont pop out. do you know of a way to fix this?

---

### Post by Favux on 2012-05-06
Hi dog-soldier,

> just thought i would report back to let you know all is working great.
That's good to hear.  :)

I guess you'll first have to clarify something for me.  I thought they dropped Unity launchbar auto-hide for Precise.  Is there an option to restore it or do you use Ubuntu tweaks or something?  If so maybe there is a problem with that.  I'm still transferring stuff to Precise so I haven't finished setting up in it and learning it.

Anyway that used to happen with Cairo Dock when I had it on the bottom of the screen replacing the bottom panel.  The couple of pixel wide line/active area that detected the mouse cursor could be off the bottom edge of the screen.  So Cairo Dock had an adjustment where you could shift the dock's location up or down as needed.  I suppose Unity doesn't have that yet.  Or an option to shift the active area or make it a little wider?

In that case you might be able to use xrandr to tweak your screen width.  Actually it could be a video driver problem to begin with and xrandr is setting you screen width a little too wide causing the problem.  Either way you can maybe try to use xrandr to change width a teeny bit narrower when in Portrait:  [http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

If you find a good width just load the command through Magick's Advanced Setup.

---

### Post by Favux on 2012-05-07
I'll answer my own question since I upgraded my HP tablet PC to Pecise yesterday evening.

I see in the Unity plug-in in CCSM (compiz configuration settings manager) that the default selection is to always show the bar although there is an auto-hide option.

However in Unity 2-D auto-hide is apparently the default.

So if you are in Unity you need to un-select auto-hide and select show.  For Unity 2-D I don't yet know how you are suppose to change the settings.  Maybe a key value somewhere.

In 2-D I see your problem.  But for me it occurs when I rotate back to laptop.  The launchbar auto-hides and probing for it is finicky, but I am able to get it to pop back out, barely.

---

### Post by dog-soldier on 2012-05-07
im using unity and since my screen isnt all that big i like the auto hide. i like unity now that i have used it for a while but i may need to go back to Gnome2 so i dont have that problem. i just tried it in laptop mode and i have the same problem as in tablet mode so im not sure. i may do a freash install since upgraded from the beta.

---

### Post by Cobuntu on 2012-05-07
Just one little thing I have noticed between upgrade from 11.10 and fresh install with Unity: When you add the Desktop icon to the launcher bar via compiz settings manager, in the upgrade it shows on top of the home button and in the fresh install it shows below the workspaces. Have this noticed on several notebooks so checking out a fresh install could make sense.

---

### Post by dog-soldier on 2012-05-09
Favux
has this been tested on Lubuntu ? the reason im asking is cause im thinking of switching to it or may be Xubuntu not for sure which one yet but Lubuntu runs real good from usb drive

---

### Post by Favux on 2012-05-09
[QUOTE=dog-soldier]has this been tested on Lubuntu ?[/QUOTE]
Not sure.  I guess that means you could be the Lubuntu tester.  :)

---

### Post by dog-soldier on 2012-05-09
ok , i installed magick rotation and it went as normal. 
when i rebooted it wouldnt work so i ran 

```
dogsoldier@dogsoldier-LifeBook-T4210:~$ sudo xxd -g1 /dev/input/magick-rotation
[sudo] password for dogsoldier: 
xxd: /dev/input/magick-rotation: No such file or directory
```

and as you can see its not there

this is on Lubuntu 12.04

---

### Post by Favux on 2012-05-09
So is the udev rule file 62-magick.rules in /etc/udev/rules.d?  In other words does Lubuntu have that directory?  Also the install log should show if it was install there.

---

### Post by dog-soldier on 2012-05-09
> **Favux said:**
> So is the udev rule file 62-magick.rules in /etc/udev/rules.d?  In other words does Lubuntu have that directory?  Also the install log should show if it was install there.

i looked in /ect/udev/rules.d and there is no 62-magick.rules. but in the devel folder there is a 62-magick.rules file. i tried to move it to the /ect/udev/rules.d but cant, it says i dont have permission.

---

### Post by Favux on 2012-05-09
You need to be root to modify a system directory or file i.e. /etc/udev/rules.d.  So if you change directory to where the .rules file is then:
```
sudo cp 62-magick.rules /etc/udev/rules.d/62-magick.rules
```
will copy it to place.  Otherwise if you don't change directory type the full path to 62-magick.rules.

---

### Post by dog-soldier on 2012-05-09
ok please bear with me here.

so since 62-magick.rules is in  
```
 /home/dogsoldier/Downloads/magick-rotation/
```

then i need to do 
```
sudo cp /home/dogsoldier/Downloads/magick-rotation/ 62-magick.rules/etc/udev/rules.d/62-magick.rules
```

or am i thinking wrong?
when i tried 
```
sudo cp 62-magick.rules /etc/udev/rules.d/62-magick.rules
```

i get 
```
dogsoldier@dogsoldier-LifeBook-T4210:~$ sudo cp 62-magick.rules /etc/udev/rules.d/62-magick.rules
[sudo] password for dogsoldier: 
cp: cannot stat `62-magick.rules': No such file or directory

```

---

### Post by Favux on 2012-05-09
Almost.
```
sudo cp /home/dogsoldier/Downloads/magick-rotation/62-magick.rules /etc/udev/rules.d/62-magick.rules
```
or as a shortcut for /home/dogsoldier:
```
sudo cp ~/Downloads/magick-rotation/62-magick.rules /etc/udev/rules.d/62-magick.rules
```
when you tried 'cp 62-magick.rules' were you in the magick-rotation folder?  If you get confused as to where you are, and everyone does, use the command 'pwd' i.e. print working directory.  It will tell you where you are at.

---

### Post by dog-soldier on 2012-05-09
> **Favux said:**
> Almost.
```
sudo cp /home/dogsoldier/Downloads/magick-rotation/62-magick.rules /etc/udev/rules.d/62-magick.rules
```

when you tried 'cp 62-magick.rules' were you in the magick-rotation folder?  If you get confused as to where you are, and everyone does, use the command 'pwd' i.e. print working directory.  It will tell you where you are at.

ok ran it and its in there now. i rebooted but still dont work. 

as for the folder i was in when i first tired, i have no idea.

ill be going to bed in a little bit since i have to get up at 2am but will try anything you might think will work when i get home tomorrow.

thanks

---

### Post by Favux on 2012-05-10
> ok , i installed magick rotation and it went as normal. 
If so there shouldn't have been a 62-magick.rules to copy and it should have been in place already.  So it appears something went wrong with the Installer in Lubuntu.  I kind of would like that clarified.  There should be an **install_log** that tells us what the Installer thinks it did.

With the rules in place the magick-rotation symlink should now be in /dev/input.  Did the green arrow icon show up in the system tray after you rebooted?  Next thing on the list would be to check if the checkmagick binary was compiled and installed into /usr/bin.

By the way all of this is detailed in the INSTALLER.txt and Magick-README.txt.

---

### Post by dog-soldier on 2012-05-10
not sure what went wrong last nite but i uninstalled Magick Rotation and reinstalled and now everything works. so i guess we can say this works with Lubuntu also. 

thanks for your time with this old man

---

### Post by Favux on 2012-05-10
Sweet!  :)

Thanks for testing.

---

### Post by Favux on 2012-05-14
Hi,

Is anyone interested in looking into the bezel buttons further?  Cobuntu started to on page 1 of this thread.  He didn't get a X key code for any of them in **xev** as I understand him.  And no reaction at all from the first 3.

If interested list your model and how many bezel buttons and what each one is suppose to do.

Then enter in a terminal ***/lib/udev/findkeyboards***. The output will show what event# the keyboard is on.  Then using that event# enter in a terminal:
```
sudo /lib/udev/keymap -i input/event# | less
```
Then press the bezel button(s) of interest.  After pressing the bezel buttons enter ***esc*** to exit, and you will see the scan codes and the associated udev key codes. Enter ***ctrl-z*** to exit **less**.  Post that output matching each scan code/key code to your bezel button and intended function list.

We then should be able to figure out how to get them to work.  We can use rc.local but as I mentioned to Cobuntu we would ultimately like a **fujitsu-tablet** udev keymap to place in /lib/udev/keymaps.

Again I'm using appendix 2 from the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") and the **README.keymap.txt** at /usr/share/doc/udev/README.keymap.txt.bz.  The README.keymap.txt is basically the instructions to assemble a udev keymap.

---

### Post by Cobuntu on 2012-07-01
Hello Favux, just installed MagickRotation 1.6.1 and it is working perfectly on my Fujitsu T730 (1.6 was not), thank you.
 

 As I would like to have the buttons better supported I would like to contribute as suggested in your last post, because now I am getting xev output. Where is the best place to do this, in this post?  
 

 So, before I installed MagickRotation I installed the Fujitsu Buttons Driver (fjbtndrv) but I do not know if this worked out really perfectly as the buttons do not work in every Ubuntu session (all or some of them, however MagickRotation 1.6.1 always works, so rotating is definitely working)!
 

 This is how I installed in 12.04 x64:
 < ppa was not working and there are missing packages when you download fjbtndrv-2.3.2 and run ./configure: it gives an error: Package requirements (x11 xi xext xtst) were not met:  
 No package 'xi' found  
 No package 'xtst' found this did not work  
 > according to [http://katastrophos.net/andre/blog/2012/05/29/installing-ubuntu-12-04-precise-pangolin-on-fujitsu-u820-u2010-u2020/](http://katastrophos.net/andre/blog/2012/05/29/installing-ubuntu-12-04-precise-pangolin-on-fujitsu-u820-u2010-u2020/) run:  
 sudo apt-get install libxrandr-dev libxtst-dev libxi-dev libhal-dev
 > then download latest driver to desktop: [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/) and unrar
 > cd /home/USER NAME/Desktop/fjbtndrv-2.3.2
 > ./configure
 > make
 > sudo make install (do not forget that!)
 > done, reboot
 < nothing works in 12.04x64; some scripts are here: /usr/local/lib/fjbtndrv
 > go to [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa)
 then open for the latest available: [https://launchpad.net/~khnz/+archive/ppa/+sourcepub/1313773/+listing-archive-extra](https://launchpad.net/~khnz/+archive/ppa/+sourcepub/1313773/+listing-archive-extra) and download all 4 available .deb for the correct platform (i386/amd64) and install in the following order (otherwise fjbtndrv will not install): fsc-btns-kernel-source > fscd > fscrotd > fjbtndrv
 RESTART
 

 

 My Fujitsu T730 has five bezel buttons [Physical number=printed above the button___printed (in color) left on the button___printed (in color) right on the button]:
 1=1___(in blue) A____(in white) scroll key down
 2=2___(in blue) B____(in white) scroll key up
 3=3___(in white) screen rotation symbol
 4=4___(in blue) Fn
 5=DEL___ (in white) ALT
 

 xev+BUTTON 1:
 KeyPress event, serial 36, synthetic NO, window 0x5a00001,  
     root 0xae, subw 0x0, time 7093532, (-515,145), root:(259,197),  
     state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,  
     XLookupString gives 0 bytes:  
     XmbLookupString gives 0 bytes:  
     XFilterEvent returns: False
 

 xev+BUTTON 2:
 KeyPress event, serial 36, synthetic NO, window 0x5a00001,  
     root 0xae, subw 0x0, time 7198570, (-616,124), root:(158,176),  
     state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,  
     XLookupString gives 0 bytes:  
     XmbLookupString gives 0 bytes:  
     XFilterEvent returns: False  
 

 xev+BUTTON 3:
 KeyPress event, serial 36, synthetic NO, window 0x5a00001,  
     root 0xae, subw 0x0, time 7256350, (-328,187), root:(446,239),  
     state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,  
     XLookupString gives 0 bytes:  
     XmbLookupString gives 0 bytes:  
     XFilterEvent returns: False
 

 xev+BUTTON 4:
 KeyPress event, serial 36, synthetic NO, window 0x5a00001,  
     root 0xae, subw 0x0, time 7321409, (-642,135), root:(132,187),  
     state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,  
     XLookupString gives 0 bytes:  
     XmbLookupString gives 0 bytes:  
     XFilterEvent returns: False  
 

 xev+BUTTON 5:
 KeyPress event, serial 36, synthetic NO, window 0x5a00001,  
     root 0xae, subw 0x0, time 7357163, (-597,212), root:(177,264),  
     state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,  
     XLookupString gives 0 bytes:  
     XmbLookupString gives 0 bytes:  
     XFilterEvent returns: False  
 

 

 But with the next step I get stuck:  
 > /lib/udev/findkeyboards
 > /lib/udev/findkeyboards: AT keyboard: input/event4
 > sudo /lib/udev/keymap -i input/event4 | less
 &#8222;Then press the bezel button(s) of interest. After pressing the bezel buttons enter esc to exit, and you will see the scan codes and the associated udev key codes. Enter ctrl-z to exit less. Post that output matching each scan code/key code to your bezel button and intended function list.&#8220;
 < When I press the bezel buttons nothing happens, after pressing ESC it says:  
 Press ESC to finish, or Control-C if this device is not your primary keyboard  
 scan code: 0x01   key code: esc
 (END)

---

### Post by Favux on 2012-07-01
> Hello Favux, just installed MagickRotation 1.6.1 and it is working perfectly on my Fujitsu T730 (1.6 was not), thank you.

however MagickRotation 1.6.1 always works, so rotating is definitely working)!
Great!!!  :D

Thanks for the feedback.  Yours is the first.

Had to respond right away before I even read the rest of your post.  Which I'll now do.

---

### Post by Favux on 2012-07-01
Hi Cobuntu,

> As I would like to have the buttons better supported I would like to contribute as suggested in your last post, because now I am getting xev output. Where is the best place to do this, in this post? 
If you feel you can update it I would suggest starting a new thread for this.  That way you are more likely to get other Fujitsu users participating.  If you don't feel you have the time I'll set it up.

Thread title would be something like:

HOW TO Setup Fujitsu tablet PC bezel buttons

Then the first post title would be:
Participate in developing and testing fujitsu-tablet udev keymaps

And the second post title:
Using fjbtndrv in Precise

I think right now the fjbtn drv is grabbing the keys which is why things aren't working as expected, but is why you are seeing xev keycodes.  So nice work on getting it to compile.  Although I'm pretty sure you don't need libhal-dev.  And its not clear to me what the deb.s did.

Each version of fjbtn drv varied how things were implemented so I'd have to go through it step by step to try and figure out exactly what's happening.

---

### Post by Cobuntu on 2012-07-01
Thanx for checking this out Favux! 

Well, there's a first time for everything, so I am trying: [http://ubuntuforums.org/showthread.php?p=12067610#post12067610](http://ubuntuforums.org/showthread.php?p=12067610#post12067610)

---

### Post by omskates on 2012-07-07
Favux,
Really great to see you still involved in assisting with installation issues for Fujitsu tablet PCs. Thankyou!:)

---

### Post by Favux on 2012-07-07
Hi omskates,

Good to hear from you again.  It's been a while, hasn't it?

Yes, I was very excited when, thanks to Robert, Magick Rotation was now able to support Fujitsu tablet PC's.

---

### Post by purple_goat on 2012-08-03
Favux, thanks a million for this.

Wanted to report it's working with Lubuntu 12.04, but only on the 2nd install.

I installed, added the Fujitsu folder, nothing. Checked /etc/udev/ and there was nothing, uninstall, reinstalled, works great and the proper files are all there.

This is with the Fujitsu Lifebook T4220.

---

### Post by hondoslack on 2012-08-14
I have an issue regarding calibration on a Toshiba P1630. I'm running 12.10 (quantal quetzal). Installation ran well, and rotate works perfectly. I installed "Calibrate Touchscreen", ran the utility, and copied the values to /usr/share/X11/xorg.conf.d/10-evdev.conf. After a reboot, Landscape touch input worked perfect (it was not OOB). However, after rotating the screen, touch input did not work under Portrait, and rotating back to Landscape it was also screwed up. Any suggestions? Thanks!

---

### Post by Favux on 2012-08-14
Hi hondoslack,

I gather the Toshiba P1630 does not have a Wacom digitizer and touchscreen.  Is that correct?

Let's see what it has.  Please post the output of the following terminal commands:
```
lsusb
```
and
```
xinput list
```

I think you've run into a bug in xrotate.py for the CTM method used for evdev rotation.  Apparently this also has been affecting the N-Trig digitizers.  I have what I think is an initial fix on the N-Trig HOW TO but unfortunately no tester as yet.  How would you like the honors?  :)

See the top two posts on the last page of the N-Trig thread:  [http://ubuntuforums.org/showthread.php?t=1252492&page=164](http://ubuntuforums.org/showthread.php?t=1252492&page=164)  The xrotate.py in the second post is the one I'd like you to test.  If you do also let me know what video chipset you have:
```
lspci | grep VGA
```
and whether you run the proprietary driver (if available) for it.

Then if you happen to hook up to a second monitor great!  Let me know what happens then.  I think I need to reindex a for loop for the second monitor case but I need a tester.

---

### Post by hondoslack on 2012-08-20
Sorry for not getting back sooner, I'll get these results back for you tomorrow, too late for tonight. Thanks!

---

### Post by hondoslack on 2012-08-20
> **Favux said:**
> Hi hondoslack,

I gather the Toshiba P1630 does not have a Wacom digitizer and touchscreen.  Is that correct?

Let's see what it has.  Please post the output of the following terminal commands:
```
lsusb
```
```
Bus 002 Device 003: ID 03ee:7320 Mitsumi 
Bus 006 Device 002: ID 08ff:2550 AuthenTec, Inc. AES2550 Fingerprint Sensor
Bus 007 Device 002: ID 0c24:0021 Taiyo Yuden Bluetooth Device
Bus 008 Device 002: ID 0430:0530 Sun Microsystems, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
> and
```
xinput list
```
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Fujitsu Component USB Touch Panel       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                         	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                         	id=9	[slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                         	id=10	[slave  keyboard (3)]
    &#8627; Power Button                            	id=11	[slave  keyboard (3)]
    &#8627; USB Camera                              	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
```
> 
I think you've run into a bug in xrotate.py for the CTM method used for evdev rotation.  Apparently this also has been affecting the N-Trig digitizers.  I have what I think is an initial fix on the N-Trig HOW TO but unfortunately no tester as yet.  How would you like the honors?  :)

I'll see what I can do.
> 
See the top two posts on the last page of the N-Trig thread:  [http://ubuntuforums.org/showthread.php?t=1252492&page=164](http://ubuntuforums.org/showthread.php?t=1252492&page=164)  The xrotate.py in the second post is the one I'd like you to test.  If you do also let me know what video chipset you have:
```
lspci | grep VGA
```
and whether you run the proprietary driver (if available) for it.

Then if you happen to hook up to a second monitor great!  Let me know what happens then.  I think I need to reindex a for loop for the second monitor case but I need a tester.

---

