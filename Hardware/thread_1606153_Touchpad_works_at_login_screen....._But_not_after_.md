---
title: "Touchpad works at login screen..... But not after =["
date: 2010-10-26
forum: Hardware
---

### Post by HelloMyNameIsJonny on 2010-10-26
Hello,
 
I have an HP Pavillion dv6 laptop. It currently dual boots Windows 7 and Ubuntu 10.10.
 
I found Windows to be annoying, so Ubuntu was my weapon of choice, and things were good.
 
When I installed 10.10 all the hardware worked as it should, and it stayed that way for a couple of weeks.
 
Until one sad day when the touchpad stopped working.... :(
 
At first I thought it might be a hardware issue, although upon booting into Windows, I discovered that it worked perfectly, 
 
The next time I booted into Ubuntu I noticed something of interest.
 
On the log in screen, the touchpad works as normal, you are able to move the cursor and click without any problem, you can also use the little button that disables the touchpad.
 
However, upon actually logging into the system, it stops working....
 
There is no error, or anything that would indicate why it stops. It just stops...
 
You cant click, you cant move the cursor, you cant do anything!
 
I have plugged in a USB mouse after all this has happened, and it worked fine
 
I really cannot see as to why it is now objecting to the touchpad
 
So any help would be greatly appreciated!

---

### Post by gyussz on 2010-10-26
Try this script in terminal or *alt + F2*
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
Any luck?

---

### Post by sw0rn on 2010-10-26
Having the same problem on my laptop.
When I use [CODEsudo cat /dev/input/mouse1][/CODE], I can see that my touchpad is getting input. 
I've tried making a xorg.conf (I don't have one) but that didn't work. Suggestions?

---

### Post by devilsdisciple on 2010-11-22
Thanks gyussz.
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true


That did it for me.

Thanks a ton..

---

### Post by Arminho on 2010-11-23
> **gyussz said:**
> Try this script in terminal or *alt + F2*
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
Any luck?

Thanks, gyussz! I had the same problem, you fixed it!

---

### Post by gyussz on 2010-11-23
No problem :) Glad I could help!

By the way for those who have the same problem like I had (touchpad hotkey didn't work), here's a script I wrote to solve it (with a little help from this forum:) ):

```

status=$(gconftool -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)
if [ "$status" = "true" ]; then
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 0
else
	gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled 1
fi

```

(Easiest way is to save it to your home folder (I mean: /home/*username*/) as "tpfunction" or whatever name you like, and bind a keyboard shortcut for the following command:
```
sh ./tpfunction
```

---

### Post by Regisz on 2011-06-10
> **gyussz said:**
> Try this script in terminal or *alt + F2*
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
Any luck?

Cool!! It worked for me too! Thx a lot!

---

### Post by metalbird on 2013-03-29
Sorry to say this didn't work for me. I have Ubuntu 11.04 and its strange how the touchpad worked for months and suddenly stopped.  It works until I sign in, then I have to use a mouse. Small price to pay for the advantages of Linux!


GO LINUX!!

---

