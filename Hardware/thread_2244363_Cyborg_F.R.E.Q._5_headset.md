---
title: "Cyborg F.R.E.Q. 5 headset"
date: 2014-09-15
forum: Hardware
---

### Post by Bradley_Hardy on 2014-09-15
I'm running Ubuntu 14.04 and trying to use a Cyborg F.R.E.Q. 5 headset. The sound works fine, except for the fact I get a constant, but quiet, whine whenever no sound is being played. The only relevant topic I found about this online was [here]("http://askubuntu.com/questions/292786/static-background-noise-while-using-new-headset"), but the steps detailed in the accepted answer didn't do anything to fix the problem. The noise isn't present in Windows 7 on the same computer.

That on its own wouldn't be too much of an issue as the sound is, while slightly annoying, quiet enough that I can just ignore it most of the time. However, connecting the microphone (which is detachable) makes the sound much louder, unbearably so. In addition to that, when I mute the microphone (using the sound settings or by pressing the mute button on the headset), left clicking with my mouse completely ceases to function! All other mouse functionality keeps working. For this problem, I couldn't find anything at all of use on the internet, and as above, this isn't an issue on Windows.

Any help with fixing these problems would be much appreciated!

---

### Post by Bradley_Hardy on 2014-09-16
Bumping since this fell to the second page.

---

### Post by maxinstuff2 on 2014-09-16
I will have a go :/
EDIT: I rectified an error in this (xorg.conf.d is a directory, not a file. DUUUH!)
note: this is just for the mute button. I have no idea what your sound issue is :(

I use cyborg keyboard and mouse, and these gaming devices have lots of buttons that Ubuntu often does not map correctly by default (neither does windows but they have custom drivers/software).

My Cyborg mouse needed config to map the buttons properly into xorg or it would crap out soon after login.
It sounds like it might think the mute button is the left mouse button? So when mute is on it thinks the mouse button is being pressed?

Maybe if you map the headset as a mouse, and specifically map no buttons, it could fix it?
I believe this may help, so here is a procedure to try it. 

In a terminal (Alt+Ctrl+T):
```
lsusb
```
To list connected usb devices. This will give you the device name. Note it down. This weird behaviour might mean your computer sees it as TWO devices, a headset and a mouse. If so note the mouse name.

Then -
```
cd /etc/X11/xorg.conf.d
```
If you get an error that the folder does not exist (it probably won't but it's better to check) then:
```
cd /etc/X11
sudo mkdir xorg.conf.d
cd xorg.conf.d
```
to create that folder.

Then create a config file -
```
gksudo gedit
```
Gedit (text editor) will open and please add this block:
```
Section "InputClass"        Identifier "Mouse Remap"
        MatchProduct "*your exact device name from above*"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "0 0 0"
EndSection
```

Save and exit (as "whateveryouwant.conf" if it didn't exist already). The name of the file doesn't matter as long as it ends with .conf
Log out and back in.

What this does is remaps the "Mouse" device, with left mid and right buttons disabled. Note that any other buttons you have that are supposed to do something on your computer will no longer work (as opposed to hardware controls on the device).
If this borks your headset then delete the code from xorg.conf.d (using the same procedure as above) and log out and in again.

This may or may not work - buttonmapping might still get picked up automagically.... if so then greater minds than I will be required :|

---

### Post by Bradley_Hardy on 2014-09-17
Thanks for responding!

When I do lsusb, interestingly the headset doesn't actually show up on the list, but there are two copies of "Saitek PLC", my mouse, and when I unplug the headset one of these goes away, so you may be onto something. However, both 'mice' have the same name, so might adding that block completely stop my mouse from working? Here's the output from lsusb, if it helps. The lower entry of "Saitek PLC" is the one that disappears when I unplug the headset:

```
Bus 002 Device 007: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 006: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 002 Device 008: ID 06a3:0004 Saitek PLC 
Bus 002 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 06a3:3a22 Saitek PLC 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by maxinstuff2 on 2014-09-17
Try this instead:
```
xinput list
```

And please re-check my post above because it contained an error in the procedure (xorg.conf.d is brand new to me, sorry)

EDIT: I found this page on the wiki that is pretty much exact what you want. Scroll down a bit and there is a step by step example of disabling a specific button on a mouse. If this works you can make it permanent using my updated procedure above.
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by Bradley_Hardy on 2014-09-18
Well, that stopped the mute button from being handled as a left-click... but it also stopped my microphone from working entirely.

---

### Post by maxinstuff2 on 2014-09-18
OK - we've established then that it can be disabled which is good. 
Delete the config file you created and log out and back in. 

Now get the automatically detected mapping as described on the wiki page:
```
[COLOR=#333333]xinput list | grep 'id='
```

Note the id of the device and:
```
[/COLOR][COLOR=#333333]xinput get-button-map *id*
```
Where "id" is the numbered id of the device.
You will get a long string of numbers kind of like this (might be longer or shorter) "[/COLOR][COLOR=#333333]1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10"[/COLOR][COLOR=#333333]. 
We'll try deciphering that to get a working mapping.

Can you paste the output here please?[/COLOR][COLOR=#333333]
[/COLOR]

---

### Post by Bradley_Hardy on 2014-09-19
The output was:```
1 2 3 4 5
```

I just tried ```
xinput set-button-map 8 0
``` and that fixed the problem. My microphone still works and can be muted -- thanks a lot for your help with this. I guess I just change the config file and use "0" instead "0 0 0" to make it do that automatically on boot?

Interestingly, I just discovered that muting the microphone actually completely gets rid of the background whine through my headset, even when the microphone isn't attached. I guess that this means the sound is microphone noise being played back through the speakers, and even when it isn't attached it picks up some static? Do you have any idea how I could disable that? In Windows 7 there's an option for it in the sound settings, but I can't find that in Ubuntu.

---

### Post by Bradley_Hardy on 2014-09-20
Bump again.

---

### Post by maxinstuff2 on 2014-09-22
Glad we could sort out he buttons issue. For the audio problem I am.... less helpful. 

All I can suggest is to have a poke around in alsa and see if fiddling with volume settings helps - maybe the mic volume is too loud?
In a terminal just run "alsamixer" to get into the interface. I'm not very familiar with audio though so I'm not sure how much more help I can be :(

---

