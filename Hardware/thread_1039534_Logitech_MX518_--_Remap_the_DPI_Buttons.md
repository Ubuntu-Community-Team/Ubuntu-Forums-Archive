---
title: "Logitech MX518 -- Remap the DPI Buttons"
date: 2009-01-14
forum: Hardware
---

### Post by Mimfort on 2009-01-14
I use a Logitech MX518 USB mouse.  I need to disable the DPI function of buttons 6 and 7 (Marked '+' and '-' on the mouse) and remap them to keybinds.

These DPI adjustment buttons are hardware-controlled.  None of the drivers or hacks (Such as g5_hiddev and lomoco) appear to support the newest MX518.  Xev does not report any events in response to these button presses.

I understand that I'm straying a bit from the 'Ubuntu Way' in asking this, but does anyone have any tips or insight into a solution for my problem?  I understand what needs to be done, but I'm a new convert to Linux and a bit unfamiliar.

I'm determined to get these buttons remapped, if I have to hairlip everyone on Bear Creek to do it.  I can script.  I can program a bit of C.  I'm willing to write my own hack and spend a few months learning how to do so (I'm retired!) but I'm hoping that someone out there can give me a few pointers as to where to begin.

I believe that the mouse has a mode that reports those button presses to the OS.  If I knew how to poll the device and issue command strings to the hardware controller I could certainly work something out.

Anyone?

---

### Post by David Harkness on 2010-09-23
I know you posted this over a year and a half ago, but did you have any luck? I have an older MX510 that I use with XP, and it has a control panel to map all the buttons. These two I map to Home and End which is great for web browsing and working alike, and I'd love to map my MX518's buttons at work on Ubuntu 10.04 Lucid Lynx.

I found [information about using evdev]("http://ubuntuforums.org/showthread.php?t=439300&highlight=logitech+518+mouse") in another post, but it doesn't mention anything about the extra buttons or mapping. :(

---

### Post by Tweak42 on 2010-10-30
I found this post and thought you would want to know was able to get my Logitech MX518 fully working and dpi buttons remapped.  The steps I took to get working for 10.10.  The steps I roughly took (minus reboots)

[LIST=1]
[*]Install lomoco from synaptic
[*]Edit /etc/default/lomoco to force 1200 dpi mode (800 dpi mode will NOT allow remapping)
[*]Launch xev in a xterm and verify that the buttons are sending events, xev will spew alot of text you should see button 10, 11 and 12 in there.  If they aren't registering something isn't configured right, go back and fix.
[*]Install btnx and btnx-config from synaptic
[*]Use btnx-config to poll and capture the events, then assign each to keys.  The gui is pretty self explanatory.
[/LIST]

---

### Post by Tweak42 on 2010-10-30
I just discovered [http://www.hidpoint.com/](http://www.hidpoint.com/) after I got my MX518 working and installed it to try out. It's a slicker interface, supports many devices, but does NOT (as of this writing) support remapping the MX518 dpi buttons.

---

### Post by Bimps on 2010-11-02
> **Tweak42 said:**
> I found this post and thought you would want to know was able to get my Logitech MX518 fully working and dpi buttons remapped.  The steps I took to get working for 10.10.  The steps I roughly took (minus reboots)

[LIST=1]
[*]Install lomoco from synaptic
[*]Edit /etc/default/lomoco to force 1200 dpi mode (800 dpi mode will NOT allow remapping). **Restart Ubuntu.**
[*]Launch xev in a xterm and verify that the buttons are sending events, xev will spew alot of text you should see button 10, 11 and 12 in there.  If they aren't registering something isn't configured right, go back and fix.
[*]Install btnx and btnx-config from synaptic
[*]Use btnx-config to poll and capture the events, then assign each to keys.  The gui is pretty self explanatory.**Restart Ubuntu.**
[/LIST]

Thanks for this! Just added in bold for those like me who forgot to restart after step 2. 

btnx starts okay, registers all clicks, but yesterday didn't map any buttons, although I restarted Ubuntu. This morning, it worked. But because I remapped the forward button to open a terminal, when I'm in Firefox, it opens a terminal *and* goes forward one page.

---

### Post by proxximity on 2010-12-03
Thank you for these instructions, it works great!
The problem is just one part: 

> Edit /etc/default/lomoco to force 1200 dpi mode (800 dpi mode will NOT allow remapping)

The mouse in 1200 dpi-mode is not convenient to use (at least for me, it's just too fast, although I set the mouse-sensivity in the KDE-menu to the lowest settings). 

Why is it like that, that the buttons can't be remapped in 800dpi-mode? Any chance to fix this?

---

### Post by Tweak42 on 2010-12-05
> **proxximity said:**
> Thank you for these instructions, it works great!
The problem is just one part: 



The mouse in 1200 dpi-mode is not convenient to use (at least for me, it's just too fast, although I set the mouse-sensivity in the KDE-menu to the lowest settings). 

Why is it like that, that the buttons can't be remapped in 800dpi-mode? Any chance to fix this?

I know it's stupid, but I have no idea why the driver behaves that way since the windows side doesn't do that.:frown:  I ended up using 1200dpi by setting sensitivity to to lowest and adding the command ```
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Constant Deceleration" 2
``` to my Startup Applications to compensate.

Also there another command ```
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Velocity Scaling" 1
``` that I didn't end up using. Try adjusting the numbers and maybe you can get 1200 dpi working for you.

---

### Post by DrewBoo on 2011-04-14
> **Tweak42 said:**
> I found this post and thought you would want to know was able to get my Logitech MX518 fully working and dpi buttons remapped.  The steps I took to get working for 10.10.  The steps I roughly took (minus reboots)

[LIST=1]
[*]Install lomoco from synaptic
[*]Edit /etc/default/lomoco to force 1200 dpi mode (800 dpi mode will NOT allow remapping)
[*]Launch xev in a xterm and verify that the buttons are sending events, xev will spew alot of text you should see button 10, 11 and 12 in there.  If they aren't registering something isn't configured right, go back and fix.
[/LIST]

Fantastic!  It works for the first time (in Natty 11.04 beta) and it's never worked before.

I have one of the newer MX518 mice, which looks the same but didn't completely work with earlier versions of Ubuntu/lomoco.

So odd that it only works at 1200 dpi.  No big issue.  I just turned the mouse sensitivity down in Ubuntu's mouse settings.

Now I have Compiz Scale and Compiz Expo mapped to mouse buttons.

Thank you!

---

### Post by Tweak42 on 2011-08-29
Hey MX518 users,
  I did a clean install of 11.04 and started having issues with my MX518 sensitivity settings constantly reseting.  I run the script ```
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Constant Deceleration" 2
``` at login, but often randomly at the desktop and in game, the mouse will pause (feels like usb device connection reset) then then the sensitivity resets to super sensitive and I have to run the script again to fix it.

I never had this problem in 10.10, and I've done a cursory look thru the log files and have not found any thing obvious erroneous.  Has anyone experience this behavior?

---

### Post by outa on 2012-05-20
Hey,
I got this to work using lomoco the way it's described here, but I'd like to go one step further:
Under Windows 7, I mapped the +/- buttons to something called "Cruise  up/down" which made a document smoothly scroll up / downwards. I'd like to have the same behavior in Linux.

The problem is that this is (probably?) not a simple key stroke or command execution, so I guess I can't use tools like xbindkeys or btnx.
So far I've re-mapped the buttons to the up- and downwards motion of the mousewheel using xinput ([https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)), but now the screen only scrolls 3 lines per button press. I want it to keep scrolling when I hold down the button.

Any ideas about this? thx in advance.

---

### Post by jozi on 2012-07-15
Would also be interested to find out how to map the dpi buttons to cruise up/down. I tried following the 5 steps above but btnx is no longer available under 12.04.

---

### Post by Tweak42 on 2012-07-16
> **jozi said:**
> Would also be interested to find out how to map the dpi buttons to cruise up/down. I tried following the 5 steps above but btnx is no longer available under 12.04.

I'm not sure if or how you can duplicate the cruise function in ubuntu, but btnx can be manually downloaded and installed from launchpad.  I believe these are intended for 11.10 but still work in 12.04

[https://launchpad.net/ubuntu/precise/+package/btnx](https://launchpad.net/ubuntu/precise/+package/btnx)
[https://launchpad.net/ubuntu/precise/+package/btnx-config](https://launchpad.net/ubuntu/precise/+package/btnx-config)

---

### Post by jozi on 2012-07-16
btnx detects every button except the two dpi buttons :(

I really miss the cruise up/down buttons!

---

### Post by Tweak42 on 2012-07-17
> **jozi said:**
> btnx detects every button except the two dpi buttons :(

I really miss the cruise up/down buttons!

Are you sure you changed the dpi higher than 800?  The MX518 defaults to 800 so you have to change it using lomoco.  In my [post]("http://ubuntuforums.org/showpost.php?p=10049623&postcount=3") I stated if it isn't changed, btnx does NOT detect the +/- button presses.

Once you up the dpi, the mouse sensetivity will be all over the place but you can compensate for this using xinput.  These are the settings I use after experimenting around with various parameters.  I run it from a script file launched from the Startup Applications when I login.

```
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Profile" 7
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Constant Deceleration" 2
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Adaptive Deceleration" 2
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Velocity Scaling" 10
```

---

### Post by Horbo on 2013-06-28
Hmm, thought I'd finally found an answer that would let me play my games how I like, but even though my mouse IS an MX518 (it's printed on the bottom) when I try to use Lomoco I get an error:
```
002.002: 046d:c051 Unsupported Logitech device: HP`
```
That device is my mouse.   I have no idea what the "HP`" at the end is.

This is what lsusb show me:
```
Bus 001 Device 003: ID 0bc2:3332 Seagate RSS LLC Expansion
Bus 002 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 002 Device 004: ID 046d:0a18 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Does anyone have any alternative methods?

---

### Post by Horbo on 2013-06-28
Well I don't have another solution yet, but after finding this page: [https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working#Why_standard_methods_are_not_enough.3F](https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working#Why_standard_methods_are_not_enough.3F)
I tried easystroke (it's in the repos, I installed via Synaptic), and although I haven't got it all sorted yet, when using it I can at least get games to acknowledge that the DPI buttons exist, which is something!

Add a new Action, set Type to Key, and in Details add Alt+Right as the key combo (i.e. hold down Alt and press the right arrow).
Now while easystroke is running, games (I tested Portal in Steam) will accept the button, although that's as far as I've got.

If I manage anything else I'll post it here, and jopefully if anyone else does first they will post it here...

---

### Post by Horbo on 2013-06-28
I take it back :(

I was testing with button 10, not buttons 6 and 7 which are my problem ones.

Easystroke doesn't recognise buttons 6 or 7 either.

---

### Post by Tweak42 on 2013-06-28
Wish I could add more, but it sounds like a newer hardware revision.  My two MX-518 are several years old, and the lsusb shows:

Bus 002 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse

---

### Post by Horbo on 2013-06-29
I have been searching today, and although I still don't have a solution, I thought I'd share the little snippets about this issue that I've learnt, in case someone finds them useful:

 - Keys, and most mouse buttons send scancodes (which look like 0xa4), which are translated to keycodes (which look like 278, or 0x116)
 - Some special events (for example, although not necessarily, a laptop lid closing) don't generate scancodes, they only generate an ACPI event, which don't translate to key codes
 - The two buttons in question on the (newer, dev c051) MX518 generate neither scan codes nor acpi events... :(  (although keycodes do exist for them: 278 and 279)

Useful tools (most need sudo):
showkey -s
showkey -k
setkeycodes
xinput
evtest
acpi_listen
/lib/udev/keymap -i input/eventX   (where X is the device id, e.g. 2, as seen in xinput for example)

Useful files:
/usr/share/doc/udev/Readme.keymap.txt
/usr/include/linux/input.h

Useful URLs:
[https://wiki.ubuntu.com/Hotkeys/Architecture](https://wiki.ubuntu.com/Hotkeys/Architecture)
[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)
[http://askubuntu.com/questions/237251/how-do-i-remap-the-search-button-on-my-logitech-mx400](http://askubuntu.com/questions/237251/how-do-i-remap-the-search-button-on-my-logitech-mx400)
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

---

