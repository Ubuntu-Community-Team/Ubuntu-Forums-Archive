---
title: "M200 Tablet Screen Not Responding"
date: 2011-03-09
forum: Hardware
---

### Post by daibewklein on 2011-03-09
Hi - 
I just installed 10.10 on my toshiba m200.  Everything seems to working fine except the screen recognizing pen touch.  Do I need to enable something somewhere?  I'm new to ubuntu and could use some getting this working.  thanks!

---

### Post by Favux on 2011-03-10
Hi daibewklein,

The toshiba m200 should work out of the box with Maverick.  It has a serial internal connection so it is a serial tablet PC as opposed to a usb tablet PC.

Check to see that the Wacom X driver wacom_drv.so in xf86-input-wacom is installed.  Ubuntu calls the package that has xf86-input-wacom "xserver-xorg-input-wacom".  Do a search for that in Synaptic Package Manager or the Software Center and make sure it is installed.  It should be by default.  If it isn't, install it and reboot.

Maybe the keywords in the 50-wacom.conf at /usr/share/X11/xorg.conf.d aren't matching your tablet.  Let's check the output in a terminal of:
```
xinput list
```
first.

---

### Post by mad13mark on 2011-09-21
I have a similar issue.  10.10 on a M200.
The pen worked at the beginning but no longer works.

I checked, and the "xserver-xorg-input-wacom" package is installed.

output of [SIZE=1]xinput list:[/SIZE]
[FONT=Courier New][SIZE=1]&#9121; Virtual core pointer                  id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer        id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                        id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                  id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard       id=5    [slave  keyboard (3)]
    &#8627; Power Button                      id=6    [slave  keyboard (3)]
    &#8627; Video Bus                         id=7    [slave  keyboard (3)]
    &#8627; Power Button                      id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard      id=9    [slave  keyboard (3)]
    &#8627; Toshiba input device              id=12    [slave  keyboard (3)][/SIZE][/FONT][FONT=Courier New][B][SIZE=1]
[/SIZE][/B][/FONT][SIZE=1]
I'm also still digging on how to enable the buttons on the bezel while in tablet mode as well as the four soft buttons on the one side.

On another note, has anyone had any luck with the SD reader on this machine?


[/SIZE]

---

### Post by Favux on 2011-09-21
Hi mad13mark,

Welcome to Ubuntu forums!

Your Wacom input tools (stylus & eraser with two side buttons?) aren't showing up in *xinput list*.

First check in /usr/share/X11/xorg.conf.d that you have a file called 50-wacom.conf.  If you do post the contents.

Also if it is there we should look at your Xorg.0.log to see if it will tell us what's going wrong.  It is located at /var/log.  Since it is big you can compress it by right clicking on it and using Create Archive.  Then attach it to your next post with Manage Attachments below.

---

### Post by mad13mark on 2011-10-02
Contents of 50-wacom.conf

Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
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
EndSection


----------------------
I tried re-installing xserver-xorg-input-wacom without results.

---

### Post by Favux on 2011-10-02
The wacom.conf appears OK and it seems to match the tablet to the X driver (xf86-input-wacom or what Ubuntu calls the xserver-xorg-input-wacom package) but there appears to be some kind of initialization error:
```
[    22.849] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    22.849] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    22.849] (II) LoadModule: "wacom"
[    22.849] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    22.849] (II) Module wacom: vendor="X.Org Foundation"
[    22.849] 	compiled for 1.8.99.905, module version = 0.10.8
[    22.849] 	Module class: X.Org XInput Driver
[    22.849] 	ABI class: X.Org XInput driver, version 11.0
[    22.849] (**) Option "Device" "/dev/ttyS0"
[    22.849] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    22.849] (II) Serial Wacom Tablet: other types will be automatically added.
[    22.849] (**) Serial Wacom Tablet stylus: always reports core events
[    22.850] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    22.850] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    22.850] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    22.850] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    22.851] (II) UnloadModule: "wacom"
[    22.851] (EE) PreInit returned NULL for "Serial Wacom Tablet"
```
Let's see if we can verify it is on ttyS0.  What is the output of?:
```
sudo dmesg | grep ttyS

```
We may want to try to set up an xorg.conf instead of a wacom.conf.  Do you have one at /etc/X11?  If so please post the contents.

---

### Post by mad13mark on 2011-10-02
Thanks for helping me out on this!

output of sudo dmesg | grep ttyS
[    0.516050] 00:09: ttyS0 at I/O 0x338 (irq = 4) is a 16550A
[   23.783031] ttyS0: LSR safety check engaged!
[  621.696779] ttyS0: LSR safety check engaged!
[ 1210.876801] ttyS0: LSR safety check engaged!

I don't have xorg.conf in etc/X11/

---

### Post by Favux on 2011-10-02
Alright it looks like it is on ttyS0, which is where you would expect it.  Let's see if the dmesg result is congruent with the setserial output.  Run this command in a terminal and post the output:
```
sudo setserial -g /dev/ttyS0
```

---

### Post by mad13mark on 2011-10-02
Comparison of the results:

~$ sudo dmesg | grep ttyS
[    0.511858] 00:09: ttyS0 at I/O 0x338 (irq = 4) is a 16550A
[   22.703733] ttyS0: LSR safety check engaged!
[  237.496796] ttyS0: LSR safety check engaged!

~$ sudo setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4

And they match....

---

### Post by Favux on 2011-10-03
That seems to shoot down that idea.  We were seeing similar errors in lubuntu but the dmesg and setserial outputs didn't match.  I suppose it could be the baud rate instead of the port or irq.  So lets try adding to /etc/serial.conf the following anyway:
```
/dev/ttyS0 port 0x338 irq 4 baud_base 34800
```
using:
```
gksudo gedit /etc/serial.conf
```
That way the driver will know what the baud rate is from the get go.

---

### Post by mad13mark on 2011-10-03
Just tried that and did a full re-boot.  Still no results.

I've been browsing through the "**HOW TO:  Install a LinuxWacom Kernel Driver for Tablet PC's"** forum for clues.  I noticed you've been posting over there a lot.  Does 11.04 have the same issues?  I am trying to decide if it's worth it right now to upgrade from 10.10.

---

### Post by Favux on 2011-10-03
I don't know how to answer that.  Natty and now Oneiric have changed the serial stack.  Instead of the old 4 serial ports available, ttyS0 to ttyS3, there are now 32!  I haven't found any documentation explaining the change.  Nor have I seen any real difference in serial tablet setup except that maybe tablets set up on ttyS0 before are now mapped to ttyS4 for some reason.  I don't think most users are aware of this since now days things are handled transparently by the wacom.conf and they don't have to manually set up their xorg.conf.  Except those who run in to trouble.  And that seems to be at about the same frequency as before.

Alright, since it didn't make a difference remove the line you added from the serial.conf.  Before going to a xorg.conf I'd like to try one other thing.

Back in July a udev guru explained that the Fedora serial ISDV4 rules were "hopelessly borked" and should be causing all kinds of strange problems.  As far as I can tell Ubuntu's rules are identical, just splitting one line into two for four total instead of Fedora's two.  Since we do see all kinds of strange problems with ISDV4 serial tablets (Wacom serial tablet PCs) I figure let's try the new rules Peter Hutterer came up with to address the issues Lennart brought up.  They look like this:
```
ACTION!="add|change", GOTO="wacom_end"

# Match all serial wacom tablets with a serial ID starting with WACf
# Notes: We assign NAME though we shouldn't, but currently the server requires it
#        We assign the lot to subsystem pnp too because server reads NAME from
#        the parent device. Once all that's fixed, as simple SUBSYSTEM="tty"
#        will do and the ENV{NAME} can be removed.
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

LABEL="wacom_end"
```

So we want to edit 69-xserver-xorg-input-wacom.rules at /lib/udev/rules.d.
```
gksudo gedit /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules
```
Ubuntu has the serial rules in the same file as the usb rules, right before them.  It looks like:
```
# udev rules for wacom tablets.
# These rules were compiled for the Debian GNU/Linux distribution,
# but others may, and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS
# of new devices with Ron <ron@debian.org> so that we can try
# to present users with a standard set of device nodes which
# they can rely on across the board.

# Catch the serial tablets and tell X that's what they are
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="WACf*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="FUJ*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

KERNEL!="event[0-9]*", GOTO="wacom_end"

# Port specific link for users of multiple tablets of the same type.
# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"
```
Let's comment out the current serial rules and add the new ones.  But since Ubuntu doesn't use a loop for them we need to modify them slightly:
```
# udev rules for wacom tablets.
# These rules were compiled for the Debian GNU/Linux distribution,
# but others may, and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS
# of new devices with Ron <ron@debian.org> so that we can try
# to present users with a standard set of device nodes which
# they can rely on across the board.

# Catch the serial tablets and tell X that's what they are
ACTION=="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
ACTION=="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

#ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="WACf*", ENV{NAME}="Serial Wacom Tablet"
#ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="FUJ*", ENV{NAME}="Serial Wacom Tablet"
#ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
#ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

KERNEL!="event[0-9]*", GOTO="wacom_end"

# Port specific link for users of multiple tablets of the same type.
# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"
```
Then reboot.  I'm really hoping these make a difference.  It would be nice to get all serial tablet PCs setting up cleanly.

---

### Post by mad13mark on 2011-10-04
Still no recogniton of the screen digitizer after reboot.
Just to verify it's not a pen hardware issue with the stylus, I plugged in an old wacom penpartner.
My M200 recognizes it enough that I can get pointer tracking and a left-click event when the "eraser" end is pressed. 
Sadly no response from a wacom "mouse" (EC-140-0W)

---

### Post by Favux on 2011-10-04
This time let's leave the change in since the old serial rules weren't right.

OK, time to try a xorg.conf and see if that does the trick.  This is the basic form it would take.
```
Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "eraser"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
EndSection
```
You can edit it using:
```
gksudo gedit /etc/X11/xorg.conf
```
This will also create it since you don't have one.  Remember if you did have one post that first before making changes.  That would alter things and we don't want to get an xorg.conf wrong because that can break X.  So always back up a working xorg.conf and be prepared to reinstall it from your Recovery mode boot option's command line in case we break X.

---

### Post by mad13mark on 2011-10-05
That didn't work either.
I will try a few more reboots to see what shakes loose.

The 50-wacom.conf that I listed earlier is in /usr/share/X11/xorg.conf.d

---

### Post by mad13mark on 2011-10-12
I did some digging around, tried putting everything into the /usr/share/X11/xorg.conf.d/50-wacom.conf
Rebooted with no joy.

I did have a random success with the stylus, but it did not survive a hibernate.
Dug around in the log files.
Tablet starts properly (I think) in the example Xorg.2.log, but not in the Xorg.0.log which is what I got with the latest try.

Please take a look at the attached files.  I'm too sleepy to find what's wrong.

---

### Post by Favux on 2011-10-12
What jumps out at me is the successful initiation in Xorg.2.log has the cursor running at BaudRate 19,200 rather than the 38,400 rate I assumed it would be at.  You don't have a cursor (Wacom tablet mouse) of course but I assume the stylus and eraser are also at that BaudRate.  So in your .conf file or xorg.conf you should try the Option:
```
Option "BaudRate" "19200
```
after the *Driver "wacom"* line in the 50-wacom.conf.  In the xorg.conf try it in both the stylus and eraser sections after the *Option "Type"* line.  Of course that means we used the wrong speed for the setserial line.

---

### Post by mad13mark on 2011-10-16
Still no luck.
To verify that the digitizer is generating data I ran the following.
inputattach -dump /dev/ttyS0
as soon as the stylus approached the display it generated the following:

60 (`) 96 (x) 47 (G) 13 (x) 48 (H) 
c0 (x) 
60 (`) 96 (x) 47 (G) 13 (x) 48 (H) 40 (@) 73 (s) 
48 (H) ac (x) 02 (x) 48 (H) 40 (@) 4e (N) d2 (x) ac (x) 02 (x) 48 (H) 

Which continued as long as the stylus was within range.  Button clicks would produce changes within range as well.

After this, setserial -g /dev/ttyS0 would produce:
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4

where prior to the inputattach command, the same setserial query would claim the /dev/ttyS0 did not exist.

---

### Post by mad13mark on 2011-10-16
After a fresh reboot, setserial again responds:

~$ setserial -g /dev/ttyS[0123]
/dev/ttyS0: No such device
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

Looking through the forums, I thought to try udevadm:

~$ udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)

  looking at device '/devices/pnp0/00:09/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:09':
    KERNELS=="00:09"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="WACf004"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by mad13mark on 2011-10-16
Possibly another clue.
Prior to a low-battery induced hibernate, I had run:

~$ setserial -g /dev/ttyS*
/dev/ttyS0: No such device
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

But just after waking up from hibernate I tried the same in the same terminal:

~$ setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

The question is, what's the difference between the boot sequence and the hibernate wake?  And how do I find the difference?

---

### Post by Favux on 2011-10-16
OK, so both inputattach and udevadm show the correct port is ttyS0.  Where did you get inputattach from?  Did you compile input-wacom?  That converts a serial port input to a usb or serio stream.  If you have that set up that might be interfering.  Using input-wacom's wacom_w8001.ko (a kernel serio driver) and input-attach is an alternative way to set up a ISDV4 serial tablet now.

The lack of a port until after you hibernate does also remind me a little of the problem Fujitsu ISDV4 tablets have initializing.  They often, after a reboot, need to log out (stop X) and log back in (restart X) to get intialized/working.

Does the abscence or prescence of the ttyS0 make any functional difference?  Anyway let's try the setserial set up again but try adding to /etc/serial.conf this instead:
```
/dev/ttyS0 port 0x338 irq 4 baud_base 192000
```
Again using:
```
gksudo gedit /etc/serial.conf
```
In addition you could try adding the following:
```
setserial /dev/ttyS0 port 0x338 irq 4 baud_base 192000
```
 to  the /etc/rc.local file.

---

### Post by mad13mark on 2011-10-17
I don't recall compiling input-wacom.  I came across a mention of inputattach in the forums, looked at it's man page and tried it.

I had already tried your line in serial.conf with no luck.

And the suggested setserial line in /etc/rc.local doesn't seem to have affect either.

I'll try a couple cold reboots to see what shakes loose.

---

### Post by mad13mark on 2011-10-17
Attached is the most recent xorg.0.log from a boot from a full shutdown.

---

### Post by mad13mark on 2011-10-22
Still having no luck with this Toshiba M200 wacom Issue.
I did do some looking for just about any file that may be the issue, but I'm too much of new hand at this to know where I should be searching.
I did look at /var/lib/setserial/autoserial.conf
It does have a line
/dev/ttyS0 uart 16550A port 0x0338 irq 4 baud_base 115200 spd_normal skip_test
the .old version of this has nothing but the comment lines.

Any other places I should be looking?

---

### Post by Favux on 2011-10-22
Nice find with /var/lib/setserial/autoserial.conf.  Seems something setserial is doing.  Can you show me both files, the current and old?  The port is wrong and the *baud_base 115200* bothers me.  Max speed the I/O chip allows.  ISDV4 serial tablets are either at 19200 or 38400 so could that be messing things up?

Your Xorg.0.log above tells us neither ISDV4 baud speed works.  If something else was also on the port it could drop characters but I don't think that is happening.  Do you have any other serial devices?

Maverick didn't have any special problems with serial tablet PCs that I was aware of.

---

### Post by Favux on 2011-10-22
I just realized you probably don't know what I was talking about with Natty and Oneiric.  To explain here's the challenge we are facing with a X200t:  [http://ubuntuforums.org/showthread.php?t=1863935](http://ubuntuforums.org/showthread.php?t=1863935)

---

### Post by mad13mark on 2011-10-23
The only other possible serial devices I can think of would be IRDA or bluetooth.
One of the docks for my M200 has a single RS232, but I've never connected it.

I've already read through the x200 thread.:)

**/var/lib/setserial/autoserial.conf**
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
/dev/ttyS0 uart 16550A port 0x0338 irq 4 baud_base 115200 spd_normal skip_test

**/var/lib/setserial/autoserial.conf.old**
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#

I'm thinking of doing the manual config mode to set the proper commands.  Any hazards in doing so?

---

### Post by Favux on 2011-10-23
I think adding to the serial.conf is the same as the manual mode but I'm not sure.  So I don't know what hazards there are.

I'm starting to wonder if the problem isn't upstart.  Could you check in /etc/init and see if there is a tty0.conf file?  If there is post the contents if not post the next nearest i.e. tty1.conf if it is there.

---

### Post by mad13mark on 2011-10-24
There is no /etc/init/tty0.conf.  There are tty1 - 6 .conf files.

**tty1.conf contents:**
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1

**tty2.conf contents for comparison:**
# tty2 - getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty2

----------------------
tty 3-6 are the same as tty2.conf except for the expected tty number

---

### Post by Favux on 2011-10-24
Say by any chance did you compile and install input-wacom on your Maverick install recently?  Or maybe the joystick stuff and inputattach from the Linux Console Project?

---

### Post by mad13mark on 2011-10-24
I didn't do any compiling.
Synaptic shows the following supported packages as installed: 
xserver-xorg-input-wacom version 1:0.10.8-0ubuntu1
inputattach version 20051019-12

---

### Post by Favux on 2011-10-24
Alright, those two thoughts are dead ends then.  Back to the drawing board.  :(

---

### Post by Favux on 2011-10-24
I guess we could give up on the ISDV4 serial driver in xf86-input-wacom and try the new kernel serio variation of it wacom_w8001.ko.  I think I mentioned trying that a while ago.  That then requires inputattach so that it is on a /dev/input node.  Then the xf86-input-driver sees the incoming serial port data as usb data and handles it as a usb device.

Maybe we'll have better luck with a different driver.  But it bothers me since things should be working out of the box for you in Maverick without all these shenanigans and we can't find out why it isn't.

What do you think?

---

### Post by mad13mark on 2011-10-25
[B]Another clue, on fresh boot:
[/B]
~$ setserial -g /dev/ttyS0
/dev/ttyS0: No such device

~$ sudo setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4

[B]after returning from a hibernate:
[/B]~$ setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4
~$ sudo setserial -g /dev/ttyS0
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4

**Tried modifing /var/lib/setserial/autoserial.conf:**
#
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
# 8:41pm 24 Oct 2011, Mdf - used above instructions to put into MANUAL.
# old line below
# /dev/ttyS0 uart 16550A port 0x0338 irq 4 baud_base 115200 spd_normal skip_test
# newline below

/dev/ttyS0 uart 16550A port 0x0338 irq 4 baud_base 19200 spd_normal skip_test

Response after boot:
~$ setserial -g -a /dev/ttyS0
/dev/ttyS0: No such device

~$ sudo setserial -g -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x0338, IRQ: 4
    Baud_base: 192000, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal

---

### Post by Favux on 2011-10-25
What happens if you remove the?
```
spd_normal skip_test
```
And also maybe try changing 19200 to 38400?

---

### Post by mad13mark on 2011-10-30
The line in autoserial.conf is now:
/dev/ttyS0 uart 16550A port 0x0338 irq 4 baud_base 38400

And the responses on the setserial queries are:
~$ setserial -g -a /dev/ttyS0
/dev/ttyS0: No such device

~$ sudo setserial -g -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x0338, IRQ: 4
    Baud_base: 192000, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal

---

### Post by mad13mark on 2011-10-30
Of course, after resuming from hibernate, I get:
~$ setserial -g -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x0338, IRQ: 4
    Baud_base: 192000, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal
~$ sudo setserial -g -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x0338, IRQ: 4
    Baud_base: 192000, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal

and still no response.

---

### Post by mad13mark on 2011-10-30
I'm willing to try just about anything at this point....

---

### Post by Favux on 2011-10-30
I'm definitely getting the impression that 19200 is what you want.

It seems the choices are to try wacom_w8001.ko or post on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss) and hope a developer notices you and takes an interest and helps.

I'm just not seeing the problem.  Of course I could be missing something obvious but at this point I'm thinking it is not Ubuntu but the wcmISDV4.c and/or isdv4.h code that is at fault.  It's getting to about line #824 in wcmISDV4.c:
```
			xf86Msg(X_ERROR, "%s: wcmWriteWait error : %s\n",
					pInfo->name, strerror(errno));
```
Which is in the:
```
 * wcmWriteWait --
 *   send a request
```
function.

I really should review what we've done again and think about it.

---

### Post by mad13mark on 2011-11-02
What I find interesting is that it returns 192000, not 19200.

---

### Post by Favux on 2011-11-02
Heck, I totally missed that.  Could that be real and the problem?  A bug in setserial instead of wcmISDV4.c?  But why doesn't setting it manually fix it?  And why would you be "the only one" to walk into it?

---

### Post by mad13mark on 2011-11-02
Dunno.  But I am running a disk-wide search overnight for "192000" text within files to see what I can find.  I have noticed a slowdown in booting in the last few days.  Prolly unrelated though.

---

### Post by mad13mark on 2011-11-03
Found it.  The 192000 was in /etc/rc.local
Must've added an extra zero when pasting from a few posts back.
Changed all to 38400, and it now shows that value when I run sudo setserial:
/dev/ttyS0, Line 0 , UART: 16550A, Port: 0x0338 IRQ: 4
Baud_base: 38400, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal

---

### Post by Favux on 2011-11-03
Good catch.

But the thing still isn't working?

If not I'll post instructions for using input-wacom's alternate serio kernel driver tomorrow.  Assuming you want to give it a shot.  Long day and burned out.  Just pushed Magick Rotation's new uninstaller.

---

### Post by mad13mark on 2011-11-03
I look forward to trying it.  Have some well-deserved sleep.

---

### Post by Favux on 2011-11-03
Alright, here we go.

Try to remove any changes you made to your system back to the defaults except as instructed below.

Check in /lib/modules/your-current-kernel/kernel/drivers/input/touchscreen and see if wacom_w8001.ko is there.  Then check if you have input-attach installed, it should be in /usr/bin.  I'm pretty sure that inputattach, if there, is too old (2005) to work.  It doesn't have the Wacom patch.  Anyway now you know where things go.

So we'll clone input-wacom.  Instructions for that for that are in Appendix 2 in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Except after:
```
./autogen.sh --prefix=/usr
```
you don't want just the usb driver wacom.ko so you'll do a:
```
make

sudo make install
```
So the newly compiled wacom_w8001.ko and inputattach are installed.  The wacom.ko will come along for the ride but you don't care.

Then add to /etc/rc.local the following:
```
inputattach --wacom /dev/ttyS0
```
so it looks like:
```
# By default this script does nothing.

inputattach --wacom /dev/ttyS0

exit 0
```
for 19200 baud.  For 38400 use:
```
inputattach --baud 38400 --wacom /dev/ttyS0
```
Then to avoid any conflict in 69-xserver-xorg-input-wacom.rules comment out (#) the new serial wacom rule you added, the one with the WACf match.  Also in 50-wacom.conf comment out the two serial snippets:
```
#Section "InputClass"
#	Identifier "Wacom serial class"
#	MatchProduct "Serial Wacom Tablet"
#	Driver "wacom"
#EndSection

#Section "InputClass"
#        Identifier "Wacom serial class identifiers"
#        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
#        Driver "wacom"
#EndSection
```
After a reboot you should be on the new serio driver and using the usb code pathways in xf86-input-wacom.

Good luck!

---

### Post by mad13mark on 2011-11-04
Should I uncomment the following line in 50-wacom.conf?
#    MatchProduct "Wacom|WALTOP|WACOM"

---

### Post by Favux on 2011-11-04
I'd have to see the whole usb snippet but I think that's the right idea.

---

### Post by mad13mark on 2011-11-04
And it.....................doesn't work.
I tried both 19200 and 38400.  Multiple reboots.

I tried my old Wacom usb PenPartner, and it works.  Well only for the pressure sense eraser for both of my stylii.  But at least something still works.  Just not the serial one.

---

### Post by mad13mark on 2011-11-04
Tried running:
inputattach -dump /dev/ttyS0
and got data back for both stylii, but for the pen end only.  No response with the side button or the eraser end.

---

### Post by mad13mark on 2011-11-05
The current 50-wacom.conf is:
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
# waltop line enabled for test by MF 5Nov11 1:52p
#    MatchProduct "Wacom|WALTOP|WACOM" 
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

#Section "InputClass"
#    Identifier "Wacom serial class"
#    MatchProduct "Serial Wacom Tablet"
#    Driver "wacom"
#EndSection

#Section "InputClass"
#        Identifier "Wacom serial class identifiers"
#        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
#        Driver "wacom"
#EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

I tried swapping in the the line with "WALTOP" but ran into some boot hangs.  Had to go into "safe" mode to edit it back.  Somehow my vid drivers got borked.

---

### Post by mad13mark on 2011-11-06
I still have the same behaviour where:
sudo inputattach -dump /dev/ttyS0 
only produces output after coming back from hibernate.
At least now, it produces output with pen, eraser, and button 2.  or seems to.

Prior to hibernate:
setserial -g /dev/ttyS0 returns "device does not exist"
aftwards it returns:
/dev/ttyS0, UART: 16550A, Port: 0x0338, IRQ: 4

---

### Post by pakopako on 2013-02-02
Apologies for reviving a dead thread, but this is the only that that popped up with "M200" (my laptop model) and "Wacom."

Not sure what I did, but I was adding IrDA functionality to my Ubuntu (11.04) and after the reboot, I think it may have run into a conflict with my Wacom. How can I tell if there's an IRQ conflict (and more importantly, how I use both at the same time?)

"sudo dmesg | grep ttyS" outputs ttyS**4** -- but that may be the IrDA not Wacom
```
[    0.248082] 00:09: ttyS4 at I/O 0x338 (irq = 4) is a 16550A
[   23.779208] ttyS4: LSR safety check engaged!
[  752.103301] ttyS4: LSR safety check engaged!
[ 1569.530918] ttyS4: LSR safety check engaged!

```
The /etc/X11/xorg.conf:
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Option "RandRRotation" "true"
EndSection
```
And Xorg.0.log says:
```
[    23.767] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    23.777] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    23.777] (II) LoadModule: "wacom"
[    23.778] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    23.778] (II) Module wacom: vendor="X.Org Foundation"
[    23.778] 	compiled for 1.9.99.902, module version = 0.10.11
[    23.778] 	Module class: X.Org XInput Driver
[    23.778] 	ABI class: X.Org XInput driver, version 12.3
[    23.778] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    23.778] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    23.778] (**) Serial Wacom Tablet: always reports core events
[    23.778] (**) Option "Device" "/dev/ttyS4"
[    23.779] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    23.779] (II) Serial Wacom Tablet: other types will be automatically added.
[    23.779] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    23.779] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    23.779] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    23.779] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    23.788] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    23.788] (II) UnloadModule: "wacom"
[    23.788] (II) Unloading wacom
```
And setserial -g /dev/ttyS[0123] is.. odd:
```
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4: No such device
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
```

---

