---
title: "Turn off the screen"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by IamAcoconut on 2007-02-01
My LCD does turn  off completely when the lid is closed, but during inactivity period it just goes blank, and the backlight remains shining. How can I set the display to be turned off after a certain period of inactivity?

Thanks in advance :)

---

### Post by IamAcoconut on 2007-02-02
*bump*

---

### Post by H.E. Pennypacker on 2007-02-11
I'd love to know myself!

The bigger trick is getting the backlight to turn back on after the lid is opened.

---

### Post by IamAcoconut on 2007-02-12
> **H.E. Pennypacker said:**
> The bigger trick is getting the backlight to turn back on after the lid is opened.You mean, there's a simple way to shutdown the screen completely from console? Than we need some activation script like those the screensaver uses, right?

---

### Post by IamAcoconut on 2007-02-13
Oh, I didn't understand you at first... My screen actually does turn back on, when I open the lid. Problem is it stays on forever unless I shut it. Is that really an issue?

---

### Post by kerry_s on 2007-02-13
You can try and create a launcher with> xset dpms force off <as the command then just click on it to turn the screen off. I use a desktop icon on my laptop. On my desktop i have a menu entry for "Screen Off".

---

### Post by IamAcoconut on 2007-02-14
**[SIZE="1"]Double post - please delete.[/SIZE]**

---

### Post by IamAcoconut on 2007-02-14
> **kerry_s said:**
> You can try and create a launcher with> xset dpms force off <as the command then just click on it to turn the screen off. I use a desktop icon on my laptop. On my desktop i have a menu entry for "Screen Off".
Thanks a lot. This should have solved my problem.
But it didn't.
My screen indeed turns off completely, but after just a few **seconds** the backlight is back on! 
Why does this happen?

---

### Post by kerry_s on 2007-02-14
> **IamAcoconut said:**
> Thanks a lot. This should have solved my problem.
But it didn't.
My screen indeed turns off completely, but after just a few **seconds** the backlight is back on! 
Why does this happen?

Are you using a external laser mouse? I noticed that will sometimes turn it back on depending whats under it. You can try and put a 5 second wait time to take your hand off the mouse.->

 sleep 5 && xset dpms force off

---

### Post by IamAcoconut on 2007-02-15
This is not the case. I did try unplugging the mouse, and result is the same.

And I have to make it clear - my LCD didn't exactly turn back on. Only it's backlight did. (The screen is black, yet 'shining')

---

### Post by kerry_s on 2007-02-15
You might want to check your bios and make sure your power management is set to user specified, which means OS controlled. I have no idea why the back light would be coming back on. Does the backlight turn off after a period of time or it just stay on permanently?
Also can you post your system info so i can look it up.

---

### Post by IamAcoconut on 2007-02-15
It stays on permanently.
**Edited**: I've just checked the BIOS settings. Only option referring to the display was the 'AutoDimm' function. I disabled it, but it changed nothing.

What info should I repost for you?

---

### Post by kerry_s on 2007-02-15
> What info should I repost for you?

make,model.
Your computer info so i can google around for similar problems and maybe come across a fix.

---

### Post by IamAcoconut on 2007-02-15
> **kerry_s said:**
> make,model.
Your computer info so i can google around for similar problems and maybe come across a fix.The make won't tell you anything as it's a local manufacturer (Techmex)
How can I find detailed info about my hardware in Ubuntu?

The chipset is Intel 855 GME+ICHM4
Intel Integrated Extreme Graphic 2
Celeron M360 1.4
TFT's an ordinary 15" XGA

I didn't experience this problem in Windows.

---

### Post by kerry_s on 2007-02-15
Okay try this one, it turns everything off->

sleep 5 && xset +dpms && xset s off off && xset dpms 0 0 0 && xset dpms force off

or use a script->

#!/bin/sh

sleep 5
xset +dpms & 
xset s off off &
xset dpms 0 0 0 &
xset dpms force off &
  

make the script executable, and point the command at it(/home/user/.screen-off)

---

### Post by IamAcoconut on 2007-02-15
No joy. After 5 to 20 seconds (this interval seems random) it's back on.

Anything more that I can try?

---

### Post by kerry_s on 2007-02-16
Nope, i'm all out of ideas. I think your system might use some special drivers for power management.

---

### Post by IamAcoconut on 2007-02-18
So I shall abandon all hope, right? This was also an issue on SuSE, but on damn window$ it was perfect :/

---

### Post by H.E. Pennypacker on 2007-02-18
> **kerry_s said:**
> You can try and create a launcher with> xset dpms force off <as the command then just click on it to turn the screen off. I use a desktop icon on my laptop. On my desktop i have a menu entry for "Screen Off".

This works for me, and it is exactly what I need, with one exception.  When I move the mouse, Ubuntu doesn't even ask me for a password.  It goes right back to the desktop.  I need it to ask me for the password.

---

### Post by H.E. Pennypacker on 2007-03-09
Everything I wanted has been solved by [this thread]("http://ubuntuforums.org/showthread.php?t=358432&").

---

### Post by Amm on 2007-03-13
I was having the same problem. if i enter xset dpms force off the back light turns on after a couple of seconds. However if i enter sudo before that and run it as root it stays off.

---

### Post by IamAcoconut on 2007-03-14
> **Amm said:**
> I was having the same problem. if i enter xset dpms force off the back light turns on after a couple of seconds. However if i enter sudo before that and run it as root it stays off.Too bad it doesn't work for me. The backlight still goes back on ](*,)

---

### Post by Amm on 2007-03-14
You could try to use:
```
sudo vbetool dpms off
```
However you will not be able to turn your screen back on. The only way to turn it back on is to close and then open the lid of your laptop.

---

### Post by kuukie on 2007-03-15
The backlight **stays off** for me after I did the following:

Change the line *xset dpms force off* to *vbetool dpms off* in the file /usr/share/acpi-support/screenblank

Now the screen (and backlight) goes off (and stays off) after I close my nx6310's lid and I've also mapped hotkeys in my ~/.fluxbox/keys file like this:

Mod1 x :ExecCommand /usr/sbin/vbetool dpms off
Mod1 c :ExecCommand /usr/sbin/vbetool dpms on

So when I press Alt-X it goes off and back on again with Alt-C.

I have to add that I also 'setuid' (set user id) for vbetool like this: chmod a+s /usr/sbin/vbetool

On a side note: What the hell? How can such a simple thing as switching a screen on/off be such a freaking pain in, of all distributions, Ubuntu? Slackware never produced headaches like that ...

---

### Post by IamAcoconut on 2007-03-18
> **Amm said:**
> You could try to use:
```
sudo vbetool dpms off
```
However you will not be able to turn your screen back on. The only way to turn it back on is to close and then open the lid of your laptop.
This works for me, but screen doesn't go back on after I open the lid.
What can I do to fix this, if I'm using GNOME (not fluxbox)?

---

### Post by Amm on 2007-03-18
Are you sure the screen does not come back when you close and open the lid of the laptop. Keep the lid closed for about 5 seconds then re-open. 
If this still does not work then you need to create a hot key to run the command 
```
sudo vbetool dpms on
```
I have no idea how you would do this because you are using GNOME and because it is a command that requires root usage.
You could enter it in the terminal not being able to see anything on the screen. Always good fun :)

---

### Post by brettr on 2007-03-18
See this post, it should solve all of this

[Force screen on]("http://ubuntuforums.org/showthread.php?t=358432")

---

### Post by kuukie on 2007-03-19
Dang, wrong thread.. disregard this post.

---

### Post by znine on 2007-04-03
I don't know if I'm too late to help anybody or if this makes a difference but when I run any of the scripts  mentioned earlier in the thread on my desktop (even sudo vbetool dpms off), It turns off for a bit then the backlight turns back on and the monitor (Samsung 226BW) searches between digital an analog to find a signal. I believe it behaves similarly if I were to just unplug it from the computer. So maybe your laptop is doing something similar?

---

