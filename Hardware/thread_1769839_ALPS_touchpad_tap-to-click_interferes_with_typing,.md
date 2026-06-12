---
title: "ALPS touchpad: tap-to-click interferes with typing, cannot be turned off"
date: 2011-05-28
forum: Hardware
---

### Post by MarjaE on 2011-05-28
I got a used Sony Vaio E-Series [not my first choice, but what was available] and installed Wubi on it. I started with Ubuntu 10.10 and went on to 11.04 before reinstalling 10.10 in my attempts to fix this bug.

The machine has an ALPS Glidepoint trackpad in front of the keyboard, and it is hard to avoid the trackpad while typing. Wubi/Ubuntu detects the trackpad as a ps/2 mouse, and detects pressure variations - such as tapping, or while typing or moving the cursor - as button1 mouse clicks. [Windows uses the proprietary drivers, and I was able to disable tap-to-click on that side, which rules out some Wubi-specific issues on the Ubuntu side.]

IIRC I've tried installing symantiks, but the ALPS does not use Symantic drivers. I have used one of the mouse diagnostics tools, which could not distinguish taps from left-button clicks, but I have not reinstalled that one. I tried the grub edit involving i8042 - either that one or the symantiks drivers made the trackpad tab appear under mouse preferences - but the trackpad tab did nothing. I also tried Pointing Devices, with no effect.

Some have reported success by editing the synaptics section in xorg.conf.d to limit the maximum tap time to 0, but that has done nothing, and I'm not sure why it would do nything since this does not use Synaptics drivers.

So at this point, as an inexperienced user just trying to get the damn thing working, I'm at a loss. And typing from an older machine.

I can see that there was a debate over the alps.c file and enabling tapping - at one point it disabled  tap-to-click and it is maddening that the system now enables tap-to-click and makes it entirely impossible to disable the (mal)function.

I guess there might be some way to partially fix the bug by disabling the trackpad while typing. There is an option for that under trackpad preference, but not under mouse preferences for some reason. Apparently, some people have suggested using hot keys, but there isn't one set up by default and it looks as opaque/intimidating to me as any of the other suggestions. And less elegant. But even putting a piece of cardboard over the trackpad sounds pretty elegant at this point.

So, I guess right now I'm looking for any working step-by-step instructions to solve this problem.

---

### Post by MarjaE on 2011-05-30
Okay, I now have a hotkey set up to disable the touchpad before typing and enable it after. But I am still having a great deal of trouble, when I'm not typing and am using the touchpad with the touchpad unpredictably "clicking" itself while I try to move the cursor around the screen. It's liable to click on things or open things I do NOT want to click on or do NOT want to open.

---

### Post by jonathon6017 on 2011-05-30
> **MarjaE said:**
> Okay, I now have a hotkey set up to disable the touchpad before typing and enable it after. But I am still having a great deal of trouble, when I'm not typing and am using the touchpad with the touchpad unpredictably "clicking" itself while I try to move the cursor around the screen. It's liable to click on things or open things I do NOT want to click on or do NOT want to open.

I'm not exactly sure but that sounds like something to do with a sensitivity control. Try lowering the sensitivity and see if that helps.

---

### Post by MarjaE on 2011-05-30
> **jonathon6017 said:**
> I'm not exactly sure but that sounds like something to do with a sensitivity control. Try lowering the sensitivity and see if that helps.

I already set the sensitivity as low and the drag-and-drop threshold as high as it will go.

---

### Post by MarjaE on 2011-06-01
> **MarjaE said:**
> Okay, I now have a hotkey set up to disable the touchpad before typing and enable it after. But I am still having a great deal of trouble, when I'm not typing and am using the touchpad with the touchpad unpredictably "clicking" itself while I try to move the cursor around the screen. It's liable to click on things or open things I do NOT want to click on or do NOT want to open.

I upgraded to 11.04, but the upgrade has broken the hotkey.

---

### Post by Llewlyn on 2011-06-04
I am experiencing the same issue.

May I ask you if the Synaptics driver is working for you?
If I take a cat of /var/log/Xorg.0.log here's what I find:

```
[   899.029] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event6)
[   899.029] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[   899.029] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'

```

The evdev driver is preventing me to access all nice features of the touchpad, such as tap-to-click disabling.

What driver are you using?

Ll.

---

### Post by MarjaE on 2011-06-08
Synaptics does not work with the ALPS. I think I am using the alps.c driver, but not sure.

---

### Post by raghukr on 2011-08-27
[http://patchlog.com/linux/fix-inspiron-n7110-alps-touchpad-in-ubuntu/](http://patchlog.com/linux/fix-inspiron-n7110-alps-touchpad-in-ubuntu/)

---

