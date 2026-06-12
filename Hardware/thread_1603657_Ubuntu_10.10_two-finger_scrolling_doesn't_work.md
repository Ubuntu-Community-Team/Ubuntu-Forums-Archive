---
title: "Ubuntu 10.10 two-finger scrolling doesn't work"
date: 2010-10-23
forum: Hardware
---

### Post by pandacat17 on 2010-10-23
Hey everyone!
(I really hope this was the right category...it seemed the most appropriate)
     I just installed ubuntu 10.10 on my thinkpad t410 and so far I'm loving it. The only (fixable) downside for me is that I cannot enable two-finger scrolling in the preferences. After spending all day trying various solutions on the internet and these forums, I decided to post asking for help. 


Thanks!
pandaaacatttt17

---

### Post by P4man on 2010-10-23
Have you tried installing "pointing devices" and configure it there?

---

### Post by IcarusR on 2010-10-23
Try using synclient from a terminal.

```
synclient -l
```

Will show current options, 1 is set & 0 not set

```
man synclient
```

To see synclient manual.

Synclient set the options used by synaptics.

```
man synaptics
```

To see synaptics manual with list of all options.

---

### Post by pandacat17 on 2010-10-23
> **P4man said:**
> Have you tried installing "pointing devices" and configure it there?



Yes, I have. Everything is enabled inside of that box but I still cant use two-finger scrolling.

---

### Post by pandacat17 on 2010-10-23
> **IcarusR said:**
> Try using synclient from a terminal.

```
synclient -l
```

Will show current options, 1 is set & 0 not set

```
man synclient
```

To see synclient manual.

Synclient set the options used by synaptics.

```
man synaptics
```

To see synaptics manual with list of all options.



I've tried using the synclient commands in terminal a number of times...but I don't think I quite understand what to do. When I enable (put to 1) VertTwoFingerScroll nothing is changed. Are there other options I need to be changing?

---

### Post by Slyon on 2010-11-01
Hey Guys!

creating the file [FONT="Courier New"]**/usr/share/X11/xorg.conf.d/50-twofingerscroll.conf**[/FONT] with the following content:
```
Section "InputClass"
	Identifier	"Zwei-Finger-Bildlauf für Touchpads einschalten"
	MatchProduct	"SynPS/2 Synaptics TouchPad"
	MatchDevicePath	"/dev/input/event*"
	Option		"VertTwoFingerScroll"	"on"
	Option		"EmulateTwoFingerMinW"	"8"
	Option		"EmulateTwoFingerMinZ"	"40"
EndSection
```

And setting **desktop->gnome->peripherals->touchpad->scroll_method** to **2** in **gconf-editor** did the magic for me!

Now I have Two-Finger-Scrolling with Ubuntu 10.10 on my Thinkpad T410!

-- Slyon

---

### Post by ptosiani on 2010-11-04
WHY??? WHY???

Why do we need to follow all this steps that sometimes we don't understand...?

Why is not enough to setup VertTwoFingerScroll to 1 in synclient...?

Why is not enough to modify gconf-editor variable /desktop/gnome/peripherals/touchpad/scroll_method to 2....?

Why do we need to create this file /usr/share/X11/xorg.conf.d/50-twofingerscroll.conf...?

now I end up with a buggiest 2 finger scrolling that works randomly and 90% in the inverse direction...!

----- "I've got blisters on my fingers!" ](*,)](*,) ------

---

### Post by ptosiani on 2010-11-04
Hey! now is working... this is what I did:

1. Install "Pointing Devices"

2. Open System / Preferences / Pointing Devices and disable Vertical and Horizontal Scrolling.
 
3. Open a terminal (ctrl + alt + t) and execute this commands: 
```

synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinZ=40 
synclient EmulateTwoFingerMinW=8

```  

4.Open a terminal (ctrl + alt + t) and execute this commands:
```

gconf-editor

``` 

5. Navigate and find this key: /desktop/gnome/peripherals/touchpad/scroll_method

6. Assign the value '2'

7.Open a terminal (ctrl + alt + t) and execute this commands:
```

cat /usr/share/X11/xorg.conf.d/50-synaptics.conf 

``` 

8. Copy the Identifier name, in my case, it was "Touchpad catchall"
```

Identifier "touchpad catchall"

```

9. Execute this command, as a Super User.
```

sudo nano /usr/share/X11/xorg.conf.d/50-twofingerscroll.conf

```

10. Write this, making sure to put your Identifier.
```

Section "InputClass"
        Identifier      "touchpad catchall"
        MatchProduct    "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Option          "VertTwoFingerScroll"   "on"
        Option          "EmulateTwoFingerMinW"  "8"
        Option          "EmulateTwoFingerMinZ"  "40"
EndSection

```

And that's all!

---

### Post by chrnovx on 2010-11-05
Thank you ptosiani for the great post!

---

### Post by uho on 2010-11-10
I don't have a /usr/share/X11/xorg.conf.d

I do however have a /usr/lib/X11/xorg.conf.d and I tried to do the instructions to no avail.

I'm using ATI drivers with synaptics touchpad. Any other info you need?

---

### Post by af3556 on 2010-11-11
To be clear, using the above is turning on an emulated "multitouch", rather than using the trackpad's built-in functionality.

The command 'synclient -m 100' will show the current state of the synaptics trackpad, the "f" column is the no. of fingers detected. For me, with a fresh 10.10 install on a Thinkpad Edge 13, it's only ever 1 (or 0), despite the trackpad hardware supporting multi-touch (xinput list reports a "SynPS/2 Synaptics TouchPad").

Apparently true "multitouch" support is a work in progress (e.g. [bug/308191]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191")).
Ben

---

### Post by Cypher2 on 2010-11-11
Hello,

I am currently running on an HP G60 and have been trying to enable synclient multiple finger gestures on my trackpad using synclient.

What's happening is that when I execute my little script MANUALLY on startup through terminal or run command, all options enable themselves through the regular "synclient blablabla=xyz/0/1"...

Now the thing is that for some reason, When I try to automate the script launch (rc.local, converting the script to execute within /usr/bin or calling the commands with a ; separating them, I only get the standard two finger emulation rather then all of the ones listed below:

----
#!/bin/bash
synclient TapButton1=1
synclient TapButton2=2
synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=10
----

any ideas on how to make my system understand i need to run these.. ALL OF THEM!?

Thanks..

---

### Post by gandaroth on 2010-11-12
[Ptosiani]("http://ubuntuforums.org/member.php?u=193601")'s solution, works great. I now have basic two finger scrolling. Thanks!

---

### Post by Cypher2 on 2010-11-12
Hey there Gandaroth,

his solution does not help when using opensource display driver as dkms isn't registered through X, thus no xorg.conf file to add or edit.

the point is that when I run my little script it works (only manually), if i set it as startup (full script, or one script per command) i only get two finger click emulation for mouse right-click.. rather than the whole thing)

is the any way to get the system to emulate manual script input on startup run?

---

### Post by gandaroth on 2010-11-14
I see what you mean. I usually don't power off often, so I didn't notice it at at first. Although my setup may be different, but I'm having problem with it also. It will work when I manually run it, but when I set it to run automatically I will randomly get jumpy cursor or no scrolling at all on next boot. I'm not sure if it's cause directly by this, but it may be related.

---

### Post by earlycj5 on 2010-11-24
Thank the lord for Ptosiani!

I've been trying to figure this out on my new Dell Adamo.

I could get it to work on login by running a script, but if I'd shut the lid and it suspended, the settings were lost.

This appears to work!!!

---

### Post by Jrgifford on 2010-12-03
> **ptosiani said:**
> Hey! now is working... this is what I did:

1. Install "Pointing Devices"

2. Open System / Preferences / Pointing Devices and disable Vertical and Horizontal Scrolling.
 
3. Open a terminal (ctrl + alt + t) and execute this commands: 
```

synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinZ=40 
synclient EmulateTwoFingerMinW=8

```  

4.Open a terminal (ctrl + alt + t) and execute this commands:
```

gconf-editor

``` 

5. Navigate and find this key: /desktop/gnome/peripherals/touchpad/scroll_method

6. Assign the value '2'

7.Open a terminal (ctrl + alt + t) and execute this commands:
```

cat /usr/share/X11/xorg.conf.d/50-synaptics.conf 

``` 

8. Copy the Identifier name, in my case, it was "Touchpad catchall"
```

Identifier "touchpad catchall"

```

9. Execute this command, as a Super User.
```

sudo nano /usr/share/X11/xorg.conf.d/50-twofingerscroll.conf

```

10. Write this, making sure to put your Identifier.
```

Section "InputClass"
        Identifier      "touchpad catchall"
        MatchProduct    "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Option          "VertTwoFingerScroll"   "on"
        Option          "EmulateTwoFingerMinW"  "8"
        Option          "EmulateTwoFingerMinZ"  "40"
EndSection

```

And that's all!

I can verify that these steps work on 11.04 Alpha 1. I'll be posting here with updates on Alpha 2, Alpha 3, Beta and Release candidate.

---

### Post by JoaoMachado on 2010-12-18
> **Jrgifford said:**
> I can verify that these steps work on 11.04 Alpha 1. I'll be posting here with updates on Alpha 2, Alpha 3, Beta and Release candidate.

10.10 on HP Mini, I even have the same identifier as in the post.

Followed step by step...

John

---

### Post by parigigi on 2010-12-29
Thanks a lot ptosiani for this post. It works great on my t410 as well. The only issue is that multitouch scrolling is not working after resuming the system from the suspended state.

Is there a way to launch the script also after resuming? 
Is there another script that is launched after resuming that overrides these settings?

Thanks a lot

Have a nice day

---

### Post by parigigi on 2011-01-06
Did anybody else experienced the problem after resuming from the suspend state?

Cheers

---

### Post by emir0n on 2011-01-07
> **parigigi said:**
> Did anybody else experienced the problem after resuming from the suspend state?

Cheers

same here,have to remove the /usr/share/X11/xorg.conf.d/50-twofingerscroll.conf to boot up again w/o problems

---

### Post by josephellengar on 2011-01-15
HP dv7t quad. Same identifier as the solution listed above. I did not quote to save space. Followed step by step and it doesn't work. I'm using gnome and 10.10.

---

### Post by martydelaney3 on 2011-01-24
Tested and this works perfectly on my Asus eeePC 1001p. I was wondering though if you could change it so the 2 finger tap emulated a middle click instead of a right click.

---

### Post by Vapor63 on 2011-01-27
> **parigigi said:**
> Did anybody else experienced the problem after resuming from the suspend state?

Cheers

It worked for me for a short while, but after either standby or reboot it seems to have failed.  I re-followed the steps, but found all the settings exactly as they were.  The mouse just "wigs out" and jumps all over when I try it now.

Running Ubuntu Netbook 10.10 on an Asus 1101HA, or, the netbook that should run linux fantastically but is actually the linux-netbook from hell.

---

### Post by zweiundzwei on 2011-01-27
> **Vapor63 said:**
> It worked for me for a short while, but after either standby or reboot it seems to have failed.  I re-followed the steps, but found all the settings exactly as they were.  The mouse just "wigs out" and jumps all over when I try it now.

Same problem here, all of sudden with an EEE PC 1001P. I did a fresh install yesterday but this fix worked for weeks before that!?

---

### Post by nevpark on 2011-02-07
Yep--ptosiani's solution stops working after I suspend/reboot my computer (eeePC 1001P). In [this earlier thread]("http://ubuntuforums.org/showthread.php?t=1594946"), **lores** suggests [making a script that runs on startup]("http://ubuntuforums.org/showpost.php?p=9972494&postcount=8"), (and making a shortcut icon, as that won't work after suspend). 

Here's [more detailed instructions]("http://mixeduperic.com/linux/ubuntu-1004-how-to-setup-two-finger-scroll-on-laptop-touch-pad.html") (for 10.04 but I assume it'll work for 10.10 too).

---

### Post by tal63 on 2011-03-27
> **ptosiani said:**
> Hey! now is working... this is what I did:

1. Install "Pointing Devices"

2. Open System / Preferences / Pointing Devices and disable Vertical and Horizontal Scrolling.
 
3. Open a terminal (ctrl + alt + t) and execute this commands: 
```

synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinZ=40 
synclient EmulateTwoFingerMinW=8

```4.Open a terminal (ctrl + alt + t) and execute this commands:
```

gconf-editor

```5. Navigate and find this key: /desktop/gnome/peripherals/touchpad/scroll_method

6. Assign the value '2'

7.Open a terminal (ctrl + alt + t) and execute this commands:
```

cat /usr/share/X11/xorg.conf.d/50-synaptics.conf 

```8. Copy the Identifier name, in my case, it was "Touchpad catchall"
```

Identifier "touchpad catchall"

```9. Execute this command, as a Super User.
```

sudo nano /usr/share/X11/xorg.conf.d/50-twofingerscroll.conf

```10. Write this, making sure to put your Identifier.
```

Section "InputClass"
        Identifier      "touchpad catchall"
        MatchProduct    "SynPS/2 Synaptics TouchPad"
        MatchDevicePath "/dev/input/event*"
        Option          "VertTwoFingerScroll"   "on"
        Option          "EmulateTwoFingerMinW"  "8"
        Option          "EmulateTwoFingerMinZ"  "40"
EndSection

```And that's all!

ptosiani,
You are exceptionally awesome. I can confirm this works in Ubuntu 10.10 (Asus 1201 netbook with synaptics touchpad). Thanks again for the perfect instructions. If done correctly this should only take a minute or two to do; you don't even need to restart.

---

### Post by bjordan1979 on 2011-03-29
> **ptosiani said:**
> And that's all!

LOL .. Awesome man. Can anyone confirm if this works on a T410 in Ubuntu 10.04?

---

### Post by Old Codger on 2011-04-03
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

The pointing device did the trick for my aging black MacBook.

---

### Post by jackharvest on 2011-05-08
Still trying to get this to work after restarting... Any tips?

---

### Post by Jrgifford on 2011-05-09
If you upgrade to Natty, you can just enable it in the mouse settings. You don't need to bother with these tricks.

---

### Post by aysiu on 2011-08-22
Wow. Didn't realize I could do two-finger scrolling at all on my old HP Mini, but this thread was very helpful (the Xorg trick). And, yes, it works even after resume from suspend-to-RAM.

---

