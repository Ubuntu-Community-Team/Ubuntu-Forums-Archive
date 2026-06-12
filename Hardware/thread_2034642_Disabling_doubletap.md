---
title: "Disabling doubletap"
date: 2012-07-28
forum: Hardware
---

### Post by heinz357 on 2012-07-28
Hello, total beginner to the world of Ubuntu, so please go gently with me!:)

I've recently set up a desktop running 12.04, to learn to use Linux as best I can, and to do all the things on that I dont need my main PC for....

yes, I know this is the laptops section, but... I've just picked up a little wireless keyboard with a touchpad and mouse buttons on, just like a laptops.

Everything is working perfectly, straight from the box, even all the shortcut keys, and the dual purpose ones, so I'm really impressed with it so far, but, I cant find a setting that lets me disable doubletap on the touchpad, without disabling the touchpad entirely?!

....not being a laptop user, doubletap irritates the hell out of me....if I want to click on something, I'll LMB it!!:confused:

So, as the laptop experts of the forum, I thought you guys/girls would be the most qualified to point me in the right direction!

...please!:)

---

### Post by cortman on 2012-07-28
What's the make and model of the wireless keyboard/touchpad?
If the touchpad is by Synaptic, you can edit those settings using Synclient. Just type

```
synclient
```

in a terminal to bring up all the options.

---

### Post by heinz357 on 2012-07-28
Wow! Thanks for the speedy reply!

Its a Maplins n99ka, and I tried synclient, and got...

"Could'nt find synaptics properties. no synaptics driver loaded!"

...any ideas?

---

### Post by cortman on 2012-07-28
> **heinz357 said:**
> Wow! Thanks for the speedy reply!

Its a Maplins n99ka, and I tried synclient, and got...

"Could'nt find synaptics properties. no synaptics driver loaded!"

...any ideas?

Hm, please post the output of

```
xinput
```

post it in [CODE] tags- the little hash # mark on the editing toolbar.

---

### Post by heinz357 on 2012-07-29
Right, ok, sorry for the delay!

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ORTEK W/L Keyboard/Mouse                	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; ORTEK W/L Keyboard/Mouse                	id=8	[slave  keyboard (3)]

```

---

### Post by cortman on 2012-07-29
Not much time this morning, but I assume by "doubletap" you mean tap to click?
If so, have you tried changing that setting in System Settings>Mouse and Touchpad?

---

### Post by heinz357 on 2012-07-29
Yes, I mean tap to click, was'nt too sure what it was called!;)

Thank you for taking the time out to help, it is very much appreciated!

...System Settings>Mouse and Touchpad was the first place I went to after switching on for the first time after plugging in the kb/m, but could'nt for the life of me find an option for the touchpad settings??

---

### Post by cortman on 2012-07-30
> **heinz357 said:**
> Yes, I mean tap to click, was'nt too sure what it was called!;)

Thank you for taking the time out to help, it is very much appreciated!

...System Settings>Mouse and Touchpad was the first place I went to after switching on for the first time after plugging in the kb/m, but could'nt for the life of me find an option for the touchpad settings??

Forgot that you're on a desktop- it wouldn't have the touchpad tab. Run

```
sudo apt-get install xserver-xorg-input-synaptics
```

I'm banking on the touchpad being a Synaptic (it's hard to find much information on it) and this will install the driver. When it's done installing, run

```
synclient TapButton1=0
```

And see if that does it.

---

### Post by heinz357 on 2012-07-30
Hi, followed your instructions, and got this...

```
matt@matt-desktop:~$ sudo apt-get install xserver-xorg-input-synaptics
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
matt@matt-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
matt@matt-desktop:~$ synclient TapButton1=0
Couldn't find synaptics properties. No synaptics driver loaded?
matt@matt-desktop:~$ 

```

....I think it just does'nt want to play?!:confused:

---

### Post by cortman on 2012-07-30
Strange- try a reboot and the synclient command again.

---

### Post by heinz357 on 2012-07-30
Ok, straight from re-boot...

```
matt@matt-desktop:~$ sudo apt-get install xserver-xorg-input-synaptics
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
matt@matt-desktop:~$ synclient TapButton1=0
Couldn't find synaptics properties. No synaptics driver loaded?
matt@matt-desktop:~$
``` 

So same outcome, but without me trying to delete lang packs in he middle?

....could this be something to do with the fact that I customized he desktop a little??:confused:

Thanks again for your efforts in trying to resolve this!!;)

---

### Post by cortman on 2012-07-30
> **heinz357 said:**
> Ok, straight from re-boot...

```
matt@matt-desktop:~$ sudo apt-get install xserver-xorg-input-synaptics
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
matt@matt-desktop:~$ synclient TapButton1=0
Couldn't find synaptics properties. No synaptics driver loaded?
matt@matt-desktop:~$
``` 

So same outcome, but without me trying to delete lang packs in he middle?

....could this be something to do with the fact that I customized he desktop a little??:confused:

Thanks again for your efforts in trying to resolve this!!;)

More than happy to help. But I'm a little stumped.

(just as a side note, the autoremove has nothing to do with the current problem)

Could you post the output of

```
cat /etc/X11/xorg.conf
```

Thanks.

---

### Post by heinz357 on 2012-07-30
No problem!

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by cortman on 2012-07-31
> **heinz357 said:**
> No problem!

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

Ok, we'll try adding this to xorg.conf. Open the file by running

```
gksu gedit /etc/X11/xorg.conf
```

and add

```
Section "InputClass"
    Identifier         "Touchpad"
    Driver             "synaptics"
    MatchIsTouchpad    "on"
    Option         "TapButton1" "1"
EndSection
```

to the end of it. Save, reboot, and see if you can run the synclient command.

---

### Post by heinz357 on 2012-07-31
Ok, did the above, pasted the text onto the text file that opened,saved, rebooted, and ran synclient again and got...
```
-desktop:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?
```

Ok, I've probably, in the course of attempting to customize things, and get other things to run that wont, messed something up I should'nt have been playing with. So, I think a fresh install might be a good idea, just to make everything work like it should, and save both of us the ballache of trying to find out what went wrong.

I cannot thank you enough for the help you've given, and will run through the first page again to find the adjustments needed to make this work, as soon as I finish re-installing!:guitar:

---

### Post by cortman on 2012-07-31
> **heinz357 said:**
> Ok, did the above, pasted the text onto the text file that opened,saved, rebooted, and ran synclient again and got...
```
-desktop:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?
```

Ok, I've probably, in the course of attempting to customize things, and get other things to run that wont, messed something up I should'nt have been playing with. So, I think a fresh install might be a good idea, just to make everything work like it should, and save both of us the ballache of trying to find out what went wrong.

I cannot thank you enough for the help you've given, and will run through the first page again to find the adjustments needed to make this work, as soon as I finish re-installing!:guitar:

If you're willing to reinstall, that's definitely the easy way out. :)

More than happy to help. Post back with your progress after the reinstall!

---

