---
title: "Ubuntu 12.04: Serial Wacom Tablet touch not in absolute mode when logged in"
date: 2012-05-05
forum: Hardware
---

### Post by Cobuntu on 2012-05-05
I am affected by the problem outlined here: [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/949097](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/949097). It seems to be the problem on several Wacom-Tablet-PCs, mine is a Fujitsu T730 running Ubuntu 12.04 x64. I have a fresh and an upgraded version, it happens on both. This problem did not occur on 11.10.

The suggested workaround mentioned is:
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"

I put it in a shell script in my home and this works always after a restart, but not after suspend.

So I tried to put a shell script in /etc/pm/sleep.d/ but this does not work:
#!/bin/bash99_xsetwacom.sh
case "$1" in
    thaw|resume)
        xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"
        ;;
    *)
        ;;
esac
exit $?




Does someone have any ideas how to solve this issue permanently this way or another?

---

### Post by Favux on 2012-05-05
Hi Cobuntu,

I don't know where an X restart is in the suspend resume order.  If X hasn't started the <device name> is wrong because the Wacom X driver hasn't appended 'touch' to the parent device name yet.  So it would be "Serial Wacom Tablet", which would be OK because you want all of the input tools set Absolute anyway.  But that doesn't matter because xsetwacom wouldn't have started either.

I wonder what would happen if we added a sleep to the script and ran the sleep process in the background?  Would the script then execute after X was started?
```
#!/bin/bash99_xsetwacom.sh
case "$1" in
thaw|resume)
sleep 3s &
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"
;;
*)
;;
esac
exit
```
What we should check out is if the gnome-settings-daemon is causing the problem with dconf-editor.
```
sudo apt-get install dconf-editor
```
Then run dconf-editor and go to org.gnome.settings-daemon.peripherals.wacom.  Look around in there and see if there is a key value for touch and if it is set to Relative.  If it is change to Absolute.


To identify the PnP ID:
> dmesg | grep ttyS
[ 1.106775] 00:0b: ttyS4 at I/O 0x220 (irq = 4) is a 16550A
[ 1.170440] 0000:00:16.3: ttyS5 at I/O 0x1830 (irq = 17) is a 16550A
It probably is on the ttyS4 port so run:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)
```

---

### Post by Cobuntu on 2012-05-05
First I checked your new script. The problem is, when I put it in like that and press SUSPEND Ubuntu goes to the log-in screen!?



Second I tried dconf-editor. Under wacom I find:
serial:0x7f2a:0x1e89da45
> 0xffffe
> 0xfffff
serial:0x7f5e:0x20b8fa45
> 0xffffe
> 0xfffff

When clicking on both serials I see under Name: is-absolute and the Value is not checked.
I checked "is-absolute" in both serials and restarted - but still no working correctly, only after applying 
xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"it works immediately. 

Something I noticed in dconf-editor: It does not matter if I check or uncheck "is-absolute", the setting remains unchanged when I click on SET TO DEFAULT and there is no entry in the left corner behind DEFAULT - neither "true" nor "false".

---

### Post by Favux on 2012-05-05
Hmmm, 0xfffff and 0xffffe are the serial numbers of the default generic stylus and eraser respectively.  So it is showing you the stylus.

That actually makes sense since the Wacom Graphics Tablet applet in Systems Settings doesn't have touch configuration yet.  They probably haven't added touch support to the gnome-settings-daemon yet.  I hadn't looked at that yet so I didn't know.

Well that script change was a long shot.  I don't know much about suspend.

The Wacom X driver should be setting the stylus and eraser to Absolute by default.  And it is, correct?  Despite what the gnome-settings-daemon is or isn't saying.

So what we should try is to add a custom .conf file to /etc/X11/xorg.conf.d.  Call it 52-wacom-options.conf say.  That should tell the driver to have touch at Absolute after the hot plug event of a resume I would hope.  So:
```
Section "InputClass"
	Identifier "Fujitsu tablet PC options"
	MatchDriver "wacom"
	MatchProduct "Serial Wacom Tablet touch"

	# Apply custom Options to this device below.
	Option "Mode" "Absolute"
EndSection
```
I am assuming your ISDV4 device is matching through the first of these two snippets in the 50-wacom.conf in /usr/share/X11/xorg.conf.d:
```
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
```
Which brings up another thought I had.  Is the inputattach rule messing things up?  Check in /lib/udev/rules.d/40-inputattach.rules.  Maybe we should try commenting out?
```
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
```
If your PnP ID is FUJ02e5.  Oh, and if you have that output do you mind posting it?

---

### Post by Cobuntu on 2012-05-05
Hi Favux,

before I do the other stuff, I hope I understood you correctly showing you the output of /lib/udev/rules.d/40-inputattach.rules:

# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"

But after looking at 
  	 	 	 	 	 	   udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)
  my PnP ID is FUJ02e7, not FUJ02e5!

---

### Post by Cobuntu on 2012-05-05
50-wacom.conf in /usr/share/X11/xorg.conf.d:

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
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

# Waltop tablets
Section "InputClass"
    Identifier "Waltop class"
    MatchProduct "WALTOP"
    MatchIsTablet "on"
    MatchDevicePath "/dev/input/event*"
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

---

### Post by Favux on 2012-05-05
> But after looking at
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)
my PnP ID is FUJ02e7, not FUJ02e5! 
Good, that was the port.  Do you mind posting that output?

So you don't have to worry about the inputattach rule.  That doesn't match so shouldn't cause a problemt.

You want to create the custom file and Copy and Paste the snippet I showed into it so:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wacom-options.conf
```
By the way you could use:
```
	MatchProduct "touch"
```
instead of:
```
	MatchProduct "Serial Wacom Tablet touch"
```
if ***xinput list*** did not show any other <device name> with **touch** in it.

---

### Post by Cobuntu on 2012-05-05
$ udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:0b/tty/ttyS4':
    KERNEL=="ttyS4"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0b':
    KERNELS=="00:0b"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{options}==""
    ATTRS{id}=="FUJ02e7"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by Cobuntu on 2012-05-05
Forgot to answer from above, sorry: Stylus and Eraser work flawless.

$ xinput list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=12    [slave  keyboard (3)]
    &#8627; CNF8248                                     id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

---

### Post by Favux on 2012-05-05
Thanks for the udevadm info output.

So stylus is set to Absolute.

Yep you could use just touch if you wanted to.

---

### Post by Cobuntu on 2012-05-05
Favux, just to be sure: I do not have a folder 'xorg.conf.d' in /etc/X11 so should I create one for putting '52-wacom-options.conf' in it or is it a problem that it is missing?

---

### Post by Favux on 2012-05-05
Oops, I forgot.  It isn't there in my Precise either.  Guess it isn't there by default.

Yes you may have to create it:
```
sudo mkdir /etc/X11/xorg.conf.d
```

---

### Post by Cobuntu on 2012-05-05
Ok this is what I did, but no effect, still no touch after restart (without running the workaround):

  	 	 	 	 	 	   sudo mkdir /etc/X11/xorg.conf.d
 gksudo gedit /etc/X11/xorg.conf.d/52-wacom-options.conf

put in it: 
  	 	 		 			Section "InputClass"
 				Identifier "Fujitsu tablet PC options"
 				MatchDriver "wacom"
 				MatchProduct "touch"
 			
			
 				# Apply custom Options to this device below.
 				Option "Mode" "Absolute"
 			EndSection

---

### Post by Favux on 2012-05-05
Alright, you want to query touch Mode after a restart but before you run the xsetwacom command:
```
xsetwacom get "Serial Wacom Tablet touch" Mode
```
What is the output?  Then do it after you run the xsetwacom set command.

---

### Post by Cobuntu on 2012-05-05
Here we go:

$ xsetwacom get "Serial Wacom Tablet touch" Mode
Relative
$ xsetwacom set "Serial Wacom Tablet touch" Mode "Absolute"
$ xsetwacom get "Serial Wacom Tablet touch" Mode
Absolute

---

### Post by Favux on 2012-05-05
Well there is two ways this could be happening with the xorg.conf.d static configuration set to "Absolute".  The gnome-settings-daemon is resetting it to "Relative".  But we see no key value for touch in dconf-editor so that doesn't seem very likely.  The other is this is a Wacom X driver bug (i.e. in xf86-input-wacom).

Whatever runs last controls, so we're looking at:
/usr/share/X11/xorg.conf.d
/etc/X11/xorg.conf.d
xorg.conf
gnome-settings-daemon
xsetwacom

And that's why the files are numbered because the higher the number the later it runs in it's xorg.conf.d.

I'm thinking you want to post to linuxwacom-discuss with your diagnostics.  I think a developer should take a look at this:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

---

### Post by Cobuntu on 2012-05-05
Ok, I will post my problem there tomorrow.
Thank you very much for your help Favux!

---

### Post by Favux on 2012-05-06
We should try reinstalling xf86-input-wacom-0.14.0, that's the Ubuntu Precise default version plus a couple of patches.  It is in the xserver-xorg-input-wacom package.  So either in Software Center or Synaptic Package Manager reinstall it.

---

### Post by Cobuntu on 2012-05-06
Ok, is this the correct one?
in Synaptic:
Package: xserver-xorg-input-wacom 
Installed Version 1:0.14.0-0ubuntu2

Should I restart before I reinstall it?

---

### Post by Favux on 2012-05-06
No, restart after you install it.  And yes the version you show in Synaptic is the correct Precise default.  It isn't the vanilla 0.14.0 available from the Linux Wacom Project because Ubuntu has added a few patches.

We want to rule out a corrupted install and this should do it.

---

### Post by Cobuntu on 2012-05-06
Hi Favux, no difference:
$ xsetwacom get "Serial Wacom Tablet touch" Mode
Relative

$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=12    [slave  keyboard (3)]
    &#8627; CNF8248                                     id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

---

### Post by Favux on 2012-05-06
Good, we've ruled out an xf86-input-wacom install problem then I think.  Besides do you have two Ubuntu partitions on you Fujitsu with the same thing?

Anyway it looks like we're down to a Wacom X driver problem (or maybe the gnome-settings-daemon).

---

### Post by Cobuntu on 2012-05-06
Two seperate drives. Upgraded 11.10 to 12.04 and boot from that connected as external USB drive for testing. Got a new SSD drive as primary drive in the T730 and installed on that a clean 12.04 - but shows the exact same behavior.

---

