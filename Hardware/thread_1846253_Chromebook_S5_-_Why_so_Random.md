---
title: "Chromebook S5 - Why so Random?"
date: 2011-09-18
forum: Hardware
---

### Post by hypertyper on 2011-09-18
I was initially very excited to install Ubuntu on my Chromebook because it's incredibly fast and it gives me the opportunity to have more offline functionality without losing anything of ChromeOS.

Now, two days and two Ubuntu installs later, I'm very frustrated. The first time round getting the sound to work wasn't difficult. I followed the instructions in the comments of Jay's blog entry:
by replacing /etc/modprobe.d/alsa-base.conf by the /etc/modprobe.d/alsa.conf from chromeos

Having reinstalled Ubuntu the same process doesn't help to fix the sound. I still have sound on my headphones but the integrated speakers don't work. I've checked alsa config tool (forgot the name) and various settings, ran the script from the community help file, all to no avail. I reinstalled because I had tried different suggestions I found online and assumed I had messed something up. The reinstall hasn't helped at all.

The second problem has been just as random. The keyboard on the S5 is far from standard in terms of function keys. I managed to load the Keytouch file that someone else made for the Cr48 and it worked perfectly. Then, out of the blue, the brightness up and down stopped working. Now, again, the xdotool commands for increasing and decreasing monitor brightness have stopped working as well, like they did on the previous install, without rhyme or reason.

I haven't changed anything that, to me at least, seems even remotely connected to stopping xdotools from working or stopping the brightness keys from working. I've used the same file to try and fix the sound. I'm going through the same process getting different results.

What am I doing wrong?

What causes xdotools to fail without error message?

How can the brightness keys just work and then stop?

I know the S5 wasn't exactly built for Ubuntu but I was under the impression it runs on the same core. I can deal with a lot of things, randomness like this on a laptop isn't one of them.

I'd really appreciate any help. I'm trying to get my head around Linux / Ubuntu and I'm keen to learn. I'd love to know what I'm doing wrong.

Thank you!

edit: Now I've rebooted without changing anything at all and the speakers have started working. Is that how it's going to be?

This is what the xev output looks like for the brightness down key:

> FocusIn event, serial 36, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   0   

KeyRelease event, serial 36, synthetic NO, window 0x4a00001,
    root 0xab, subw 0x0, time 925888, (-432,195), root:(540,248),
    state 0x10, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


---

### Post by kerry_s on 2011-09-18
Not random, just bugs. 
For the brightness use xbacklight, put the shortcuts in the normal keyboard shortcuts. 
Example:
Click the add button
Name= down
Command= xbacklight -25

Name= up
Command= xbacklight +25


I use 25, you can pick what you want 10,15,etc... Try it in terminal first till you get a number you like. 

Have no clue on you sound.

your so lucky, my mom just broght my old cr-48, so here's a pic.

---

### Post by hypertyper on 2011-09-18
Thanks for your response. 

I mean the bugs are random in their appearance. They are not reproducible thus hard to fix.

I've tried xbacklight and just tried it again. I get an error saying "No outputs have backlight property". Apparently that means it's a driver issue?

It's frustrating because the XF86 commands worked for a while and I have no clue what broke them.

I wish I was better at programming since chromeOS is opensource so clearly the solutions to all of this are out there somewhere...

---

### Post by kerry_s on 2011-09-18
bummer :confused:

---

### Post by hypertyper on 2011-09-18
Clearly Ubuntu does have control over the screen brightness. In power options I can adjust the levels (at least in the on AC tab) and enable/disable the bright backlight on battery.

Which mechanism / package / function do the power options access? Maybe that can be my way in since neither xbacklight nor XF86MonBrightness are having any effect (any more).

---

### Post by kerry_s on 2011-09-18
/etc/acpi/
In there you'll see 2 scripts, 1 for up & 1 for down.

---

### Post by hypertyper on 2011-09-19
I found the scripts. Executing them doesn't do anything.

"acpi_fakekey $KEY_BRIGHTNESSDOW"

Executes without error and effect.

---

### Post by hypertyper on 2011-09-20
New approach, new problems...

I looked at the ubuntu tweak source code since UT can adjust the brightness no problem. I wrote a script which uses the same mechanism to change the brightness.

```
#!/bin/bash
#read current value
current=$(gconftool-2 -g /apps/gnome-power-manager/backlight/brightness_dim_battery)

new=$(($current + 10))

#limits lowest possible setting
if (( $new > 99 )) 
then
	new=99
fi

#set new value
gconftool-2 -s /apps/gnome-power-manager/backlight/brightness_dim_battery --type int $new
```

I can execute those scripts via "bash -c ~/c=bUp.sh" etc. I set this up yesterday and it worked fine. Today I boot up my laptop and executing the scripts still works but the shortcuts have stopped working. I reconfiured the shortcuts to execute the same script and add a different shortcut, same key with CTRL modifier.

Ubuntu still recognises the original brightness keys but it's refusing to execute the scripts.

Any suggestions what might be going on? 

Ty

---

### Post by hypertyper on 2011-09-23
I've played around some more and came up with a script that modifies the gconf values for brightness. It's not a great solution but it's working for me. xdotools did not.

[http://www.codetopf.com/2011/09/samsung-chromebook-ubuntu-fixing_23.html](http://www.codetopf.com/2011/09/samsung-chromebook-ubuntu-fixing_23.html)

Anybody who can change brightness through gconf-editor / ubuntu tweak should be able to use those scripts.

[http://dl.dropbox.com/u/9732528/BrightnessUp.sh](http://dl.dropbox.com/u/9732528/BrightnessUp.sh)
[http://dl.dropbox.com/u/9732528/BrightnessDown.sh](http://dl.dropbox.com/u/9732528/BrightnessDown.sh)

If anybody has a better solution I'm keen to hear it. The actual keys worked initially but I have no idea how and why they stopped.

---

