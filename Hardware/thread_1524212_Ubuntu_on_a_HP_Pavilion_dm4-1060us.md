---
title: "Ubuntu on a HP Pavilion dm4-1060us"
date: 2010-07-04
forum: Hardware
---

### Post by minidoc on 2010-07-04
Hi there,

Has anybody given this one a shot? Or anything else in the dm4t series? Any experience would be great. Thanks!

---

### Post by jediborger on 2010-07-05
You can check out this thread here on the progress from a few of us on using the hp dm4t. [http://ubuntuforums.org/showthread.php?t=1517749&highlight=dm4t]("http://ubuntuforums.org/showthread.php?t=1517749&highlight=dm4t")

Overall a very nice laptop and most features do work out of the box and the switchable graphics is looking promising.

---

### Post by minidoc on 2010-07-05
Awesome! Thanks, jediborger!

---

### Post by mandazi on 2010-07-17
I just bought an HP Pavilion DM4-1060us.  I plan on install Ubuntu 64-bit in a few hours.  Will let you know how it goes.

Update on status. I've made several boot CDs for both 64-bit and 32-bit.  Everytime I boot, it goes to a blank screen after the white to orange dots with the Ubuntu logo screen.  This is disappointing. but I've been googling and checking the forums and it seems that many people have the issue.

Update on progess. The issue wasn't that bad when installing.

It goes to blank screen for a moment and then loads, but the brightness is very low so you have to turn it up to see everything.

Installing right now!

So the installation failed after a few times.  I then tried a USB drive instead of the CD and it worked perfectly.  Looks like my CD was busted or something.

So I'm writing this on Ubuntu 10.04 on the HP Pavilion DM4-1060us latptop.

So far the only major issue I see is that my wireless does not work.  Hopefully I can resolve this.

Also the trackpad doesn't like 2 fingers on there for scrolling.

Wireless works!

Just need to go to System > Administration > Hardware Drivers

Make sure you are connected to the Internet via wired connection. It will automatically find the Broadcom wireless driver and ask you to enable it.  Once you enable it, it will download it and install it.


Also left click doesn't work on the trackpad. You just have to tap the pad for left click.

---

### Post by Veector on 2010-07-21
The Touchpad is the most annoying problem that I'm having with my dm4t

---

### Post by mandazi on 2010-07-21
> **Veector said:**
> The Touchpad is the most annoying problem that I'm having with my dm4t
Yes it is very annoying.  My right hand keeps touching it.

I wonder if it can be disabled.  I have a USB mouse connected.  Sometimes the trackpad comes in handy.

---

### Post by Gargon0 on 2010-07-27
hey what boot order did you use to setup ubuntu...because i too am getting a blank screen after seeing the purple ubuntu screen...i have tried using a disc and usb drive... (new pavillion DM4-1065DX) i know they are different slightly maybe...but i am having similar problems...

---

### Post by Veector on 2010-07-27
the reason why the screen is black is because the brightness is all the way down, try increasing the brightness when you get the back screen at boot up. This worked for me.

---

### Post by Gargon0 on 2010-07-27
thank you i will try this

---

### Post by mandazi on 2010-07-27
> **Gargon0 said:**
> hey what boot order did you use to setup ubuntu...because i too am getting a blank screen after seeing the purple ubuntu screen...i have tried using a disc and usb drive... (new pavillion DM4-1065DX) i know they are different slightly maybe...but i am having similar problems...
Increase the brightness (f3)

---

### Post by tapya on 2010-08-20
Hi guys!

I got a problem with the wireless driver :-k,... every time that i restart my laptop i always have to do the same thing: unistall the wireless driver and then intall it once again (System > Administration > Hardware Drivers) in order to make it work.

It looks that you didn't have the same problem, right?... any suggestion?

thanks for your help!!

---

### Post by bpow on 2010-08-24
Just a couple of things I discovered about the dm4 series (mine's actually a dm4t-1000):

[LIST=1]
[*]Switchable graphics don't work yet, but the ati card can be turned off by issuing:

```
echo '\_SB.PCI0.P0P2.PEGP._OFF' > /proc/acpi/call
```

after installing acpi_call.ko (see [details]("http://linux-hybrid-graphics.blogspot.com/")).

[*]The bios on my computer had NX (now apparently known as XD) disabled by default, and no visible option to change that behavior, so MOTD kept warning me. It turns out that pressing the 'A' key right as you enter bios (for me, that's right after entering the bios password) gives you some "Advanced" options, including the ability to enable XD. There are other options there I haven't felt courageous enough yet to try.

[*]The virtual consoles show up blank initially, apparently because they are using fb0. Issuing ```
con2fbmap 1 1
``` makes the first virtual terminal work. I haven't been able to get this working at boot (I thought kernel option 'video=map:1' would work, but it doesn't).

[*]The trackpad is a bit annoying. I found that setting ```
synclient BottomEdge=3500
``` helps with right clicking since it gives more clickable area (at the expense of trackable area). Unfortunately, this setting is lost at sleep/resume or with changing virtual terminals.
[/LIST]

---

### Post by jajaja_622 on 2010-09-24
can anyone tell me what happen to the instant on feature after installing ubuntu?

---

### Post by Veector on 2010-09-25
When you installed ubuntu 10.04 you most likely erased it when you repartitioned your hard drive. During the installation progress, there is a warning before you install ubuntu that tells you that everything in your hard drive will be erased, and the instant-on is stored in the hard drive.

---

### Post by jajaja_622 on 2010-09-26
but does this happen even if i choose to dual-boot with windows when i install ubuntu?

---

### Post by notatoad on 2010-09-29
my wireless only works when the laptop is plugged in.  thoughts?

---

### Post by austinjh on 2010-10-26
Just tried activating the proprietry ATI driver and it broke Xorg. (Ubuntu 10.10 on dm4 1060ea)

Had to use recover mode at boot up and remove the driver to get system working again.

Anybody else had this problem?

I've had 10.10 installed since it was in beta - not sure if I should do a clean install now that its officially released....

---

### Post by GeekGirl1 on 2010-11-05
> **Veector said:**
> the reason why the screen is black is because the brightness is all the way down, try increasing the brightness when you get the back screen at boot up. This worked for me.Yes, that worked for me as well. Thanks!

The only way I could maintain a dual-boot with Windows 7 without wiping out my data was to use the wubi installer. Works fine, it formatted the new area (Win 7 file) with ext4.

Will continue to test the laptop. I'm networked with another dual-boot Win XP / Ubuntu desktop. No problems to share folders or a printer.

---

### Post by GeekGirl1 on 2010-11-06
> **notatoad said:**
> my wireless only works when the laptop is plugged in.  thoughts?Perhaps you are in a bad location. When I plug in my laptop, the signal strength gets another bar (stronger) and the wireless LED indicator (f12 key) blinks slower. On battery, the indicator LED blinks faster.

I'm guessing that external power helps the hardware boost the signal and get better reception. IOW, more power for the radio transmitter and receiver section.

Is there any way to disable the LED from blinking? It's very distracting.

---

### Post by GeekGirl1 on 2010-11-07
For those having problems with insanely crazy touchpad, I found a work-around. My problem was so bad, I was forced back to Windows 7. Not any more. HP Pavilion dm4t.

I think the root cause is a bug that's yet to be fixed. So, download the script from this thread: [Disable touchpad when mouse plugged in]("http://ubuntuforums.org/showpost.php?p=7279443&postcount=5")

First, open a terminal and make the script executable:
```
chmod 755 mouseSwitcher.sh
```
Run xinput to find your mouse's name:
```
xinput list
```

Edit mouseSwitcher.sh and replace the mouse name with the one found in the previous step. I have an Intellimouse, the script fragment looks like this:

```
if xinput list 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)';
    then
```

Run the script.
```
./mouseSwitcher.sh
```

First, you'll get a mouse status report.
```
Reporting 3 classes: ...
...		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
```
When the mouse is plugged in, syndaemon is not running. The touchpad is totally disabled.:):
```
syndaemon: no process found
```
When mouse is unplgged, the script cannot see the mouse. The touchpad is working:
```
unable to find device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)
```
Once you see how it works, you can make it run at starup, create a task bar icon, or run it manually.

---

### Post by mandazi on 2010-12-09
> **notatoad said:**
> my wireless only works when the laptop is plugged in.  thoughts?

I had the same issue when I first installed Ubuntu.  I had to upgrade (or install) the wireless driver by going to System > Administration > Additional Drivers.

Hope that helps.

> **GeekGirl1 said:**
> For those having problems with insanely crazy touchpad, I found a work-around. My problem was so bad, I was forced back to Windows 7. Not any more. HP Pavilion dm4t.


I am still having touchpad problems, but I've grown to not to use it.  My issues are that it can't handle 1 finger going down first and then a second finger touching it.  It also can't do right click.  It also can't drag.

I see your solution involves disabling the touchpad when a USB mouse is plugged in.  I don't see how that solves the issues, at least for me.

---

### Post by ElSlunko on 2010-12-10
I do hope the touchpad issue gets fixed. I figured not install Ubuntu on my dm4 at all and just used it with windows as that's what it was designed for, then got bored and installed Ubuntu onto a USB drive. 10 minutes in gnome and I was already missing ubuntu on my laptop. So I'll probably just end up with a USB mouse and dual booting for the time being.

---

### Post by wcherry on 2010-12-31
Well, here is how I finally decided to deal with the touchpad issue. Touchpad lovers will not like it because it disables most of the cool touchpad features, like edge scrolling, multiple finger detection, etc.

You can basically turn the touchpad into a two button mouse by creating a file /etc/modprobe.d/touchpad.conf, and inside that file, placing the command:

options psmouse proto=exps

[If you want to try this out first, you can just do:

sudo rmmod psmouse
sudo modprobe psmouse proto=exps

]

That gets rid of the jumpiness and enables right click. It, however, disables scrolling, etc. And, I couldn't find a way to do middle click.

To solve the middle click problem, I downloaded a package called mouseemu intended for one button macs.

Here is my file: /etc/default/mouseemu

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


#MID_CLICK="-middle 0 87"         # F11 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 500" # block mouse for 300ms after a keypress


Then restart the mouseemu daemon by:

sudo /etc/init.d/mouseemu restart

Now you can get a middle mouse click by holding down on the "Windows" key and tapping the touchpad. If you hold down the "alt" key and drag on the touchpad it emulates a scroll wheel. So you can get some kind of scrolling back, but not as convenient as edge scrolling, and no horizontal scrolling.

Anyway, not perfect, but works for me so far.

Oh yes, the "TYPING BLOCK" delay helps disable the touchpad while keys are being typed. I found I kept hitting the touchpad while I was typing.

---

### Post by Dr. D on 2011-01-04
Has anyone been able to get the ATI card working? Every time I try to install the proprietary drivers X breaks and I have to uninstall it and switch back to the intel card. 

Any ideas?

---

### Post by magtrask on 2011-02-08
> **wcherry said:**
> Well, here is how I finally decided to deal with the touchpad issue. Touchpad lovers will not like it because it disables most of the cool touchpad features, like edge scrolling, multiple finger detection, etc.

You can basically turn the touchpad into a two button mouse by creating a file /etc/modprobe.d/touchpad.conf, and inside that file, placing the command:

options psmouse proto=exps

[If you want to try this out first, you can just do:

sudo rmmod psmouse
sudo modprobe psmouse proto=exps

]

That gets rid of the jumpiness and enables right click. It, however, disables scrolling, etc. And, I couldn't find a way to do middle click.

To solve the middle click problem, I downloaded a package called mouseemu intended for one button macs.

Here is my file: /etc/default/mouseemu

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


#MID_CLICK="-middle 0 87"         # F11 with no modifier
MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 500" # block mouse for 300ms after a keypress


Then restart the mouseemu daemon by:

sudo /etc/init.d/mouseemu restart

Now you can get a middle mouse click by holding down on the "Windows" key and tapping the touchpad. If you hold down the "alt" key and drag on the touchpad it emulates a scroll wheel. So you can get some kind of scrolling back, but not as convenient as edge scrolling, and no horizontal scrolling.

Anyway, not perfect, but works for me so far.

Oh yes, the "TYPING BLOCK" delay helps disable the touchpad while keys are being typed. I found I kept hitting the touchpad while I was typing.

Hi, I'm still a newbie but determined to get my hp dm3 working.  Could you explain how and where you create this file:  /etc/modprobe.d/touchpad.conf  
Thankyou.

---

### Post by Orion2000za on 2011-02-23
> **Dr. D said:**
> Has anyone been able to get the ATI card working? Every time I try to install the proprietary drivers X breaks and I have to uninstall it and switch back to the intel card. 

Any ideas?

No ideas... I tried once and had to reinstall my dm4-1050ea. I installed this script:
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
and I can switch the ATI on and off - but not switch TO it. That is while using the open source drivers. The best I get at the moment is Intel on and ATI off, thereby saving battery.

---

### Post by Orion2000za on 2011-02-24
Some notes on my experience of the dm4-1050ea so far:
1. As already mentioned, can not get ATI graphics to operate but now have it switched off. Cools computer down and saves battery
2. Touchpad a PITA. However, did manage to set it up so it does not get nervous breakdown from 2 fingers using DKMS package mentioned here:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
3. Managed to set up "disable while typing" by creating a shellscript with the line
syndaemon -d -t
and run it via Autostart

Phew. It is a bit of finicky laptop, beautiful when it works though.

Finally: I upgraded BIOS via Windows to version F.23 - big mistake. Suddenly hardware switch for wireless (fn+F12) did not work (even in Windows..), brightness settings went bananas etc. Reverted to F.17 and all seems as expected.

---

