---
title: "Broke xsetwacom trying to make tablet work"
date: 2010-12-27
forum: Hardware
---

### Post by stravant on 2010-12-27
I'm attempting to set up a Wacom Bamboo UBS tablet on Ubuntu 10.04 LTS, using the Linux Wacom project drivers, and I'm having some trouble.

Installing the driver went great, the tablet was recognized fine, but I ran into trouble trying to configure xorg.conf. It seems that the section:

Section "InputDevice" 
    Driver "wacom" 
    Identifier "cursor" 
    Option "Device" "/dev/input/wacom"
    Option "Type" "cursor" 
    Option "USB" "on" 
EndSection

Was causing me trouble (x crashed starting up because of "(EE) preinit returned null for cursor"), so I just removed it because things seemed to be working fine without it, and I could still get all of the input from the device.

Now, I have dual screens so I was trying to set up the "TwinView" feature of the driver. First off I used the following and it worked!:

xsetwacom --set "stylus" TwinView horizontal

However, that's just temporary, so I tried adding it to xorg.conf for the device. That didn't work too well, the cursor is always "stuck" at the left hand side of my screen, but still free to move up and down. Looking up how to solve this problem, I found this solution:

"I find that it can be resolved by going into a terminal (Ctrl+Alt+F1), login as root and run wacdump /dev/inputs/wacom. Moving the pen on the tablet will show things happening, and when returning to X, the cursor works as it should - you only have to do this once as far as I can tell."

I tried to do this, but it appeared that "wacdump" did not exist on my system. Futher investigation showed that it was in the "util" part of the Linux Wacom Project distribution, which I built and installed.

Now wacdump was correctly found, however I could not make it work no matter what I did, it always crashes with a segmentation fault, a problem to which I can't find any solution.

So, after that I decided to just use a hack and make a shell script that runs on startup calling xsetwacom to make it work. However to my dismay I discovered that xsetwacom no longer works, I somehow changed it when installing the utils stuff along with wacdump!

It now is phrased like "xsetwacom set ..." instead of "xsetwacom --set ..." as it was originally. It appears that its "set" command no longer has any effect with the new version. I can get the properties of device just fine, but when I call set, it happily completes without any error or having actually changed the property. The output with -v is like so:

"> xsetwacom -v set stylus TwinView "horizontal"
Set: sending 12 3 (0x3)"

Any help on how to just make it work in some way would be appreciated. Either getting the TwinView setting in xorg.conf to work, or just a way to revert the xsetwacom command to the version that worked.

---

### Post by Favux on 2010-12-27
Hi stravant,

A lot of stuff going on there.

Starting with Lucid (X server 1.7) the X driver wacom_drv.so went from linuxwacom to xf86-input-wacom.  So Xorg is now in charge of the X driver.  The linuxwacom X driver will not work in X server 1.7 and up.  That's apparently how you broke xsetwacom.  Also as part of the switch over Xorg dropped the Wacom utilities wacdump, xidump, and wacomcpl.

So you may need to reinstall xf86-input-wacom (the default for Lucid is 0.10.5) using Synaptic Package Manager, if you actually managed to get linuxwacom to compile in Lucid.  It's in the xserver-xorg-input-wacom package.  Confusingly the same name was used for linuxwacom in Karmic and earlier.

Also if you did manage to partially install linuxwacom and didn't use the appropriate flag on the configure line you may have installed an older version of xsetwacom in the wrong location and that might actually be the problem.  So first you might want to check in /usr/local/bin.  If you see a xsetwacom there delete it.  The xsetwacom executable should be in /usr/bin.  If after a reboot that doesn't clear things up then reinstall xf86-input-wacom.

In Lucid you could/should be using the 10-wacom.conf if you want to hot plug the tablet.  Also if you do have an active wacom.conf it might be interfering with the xorg.conf.  You were right to drop the cursor section as that refers to a Wacom tablet mouse which you probably don't have.

---

### Post by stravant on 2010-12-29
Thanks

I found after a some digging that apparently TwinView doesn't work at all with the X version of the driver running.

I uninstalled everything, reverted xorg.conf and then re-built/installed the linuxwacom package from the Linux Wacom Project site again. That got back the old working version of the xsetwacom tool. I gave up on adding the devices to xorg.conf, as they seem to be recognized fine without that now in Gimp / the other relevant programs.

Finally I set up a shell script to set the settings I want on startup, and it all works great now, thanks!

---

### Post by Favux on 2010-12-29
Wow, you've been busy.

In addition to the 'xsetwacom --set "stylus" TwinView horizontal' command if you're still using it you could probably use instead:
```
Option "TwinView" "horizontal"
```
in the 10-wacom.conf below the Wacom driver line in the usb snippet.

No advantage, just a possible option.  Nice work!

Are you using multimonitor lines in your startup script?  What are they?

---

