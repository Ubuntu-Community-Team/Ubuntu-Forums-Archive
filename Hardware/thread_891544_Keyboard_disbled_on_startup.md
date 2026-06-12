---
title: "Keyboard disbled on startup"
date: 2008-08-16
forum: Hardware
---

### Post by pickarooney on 2008-08-16
I have this hugely annoying problem since I upgraded my desktop to Hardy. Every time I power down the PC, when I boot up again the PS/2 keyboard is disabled in Kubuntu. I have to reboot no less than three times for it to work again. The keyboard is enabled during bootup as I can get into the boot manager but once KDE is loaded there is no longer any reaction from the keyboard.

Where should I start looking?

---

### Post by CORRIE on 2008-09-01
Sorry I can't solve your problem...I have exactly the same thing too! I'm using a PS2 keyboard which works fine in Windows and logs me into Kubuntu also but then goes dead.

Sounds like a Kubuntu problem?
Hopefully someone can help us...

---

### Post by Harmony_Of_Distortion on 2008-09-05
Hello I have the same problem with my laptop. Does enyone know something about this?

---

### Post by Crafty Kisses on 2008-09-05
If you can somehow post these results, it would be helpful:
```

lsusb
```

---

### Post by putonghua73 on 2008-10-31
> **CORRIE said:**
> Sorry I can't solve your problem...I have exactly the same thing too! I'm using a PS2 keyboard which works fine in Windows and logs me into Kubuntu also but then goes dead.

Sounds like a Kubuntu problem?
Hopefully someone can help us...

Snap! I'm experiencing the *exact* same problem. 

Running Kubuntu 8.04.1 from a Live CD (which has been checked for errors - no errors reported) using a Microsoft Natural PS/2 keyboard and a Microsoft PS/2 mouse, both of which work perfectly in Win XP, boot-up and in BIOS - none of which works once KDE loads.

**Update:** checked my keyboard and it is a USB keyboard, that uses a PS/2 connector.

After reading [_this_]("http://ubuntuforums.org/showthread.php?t=858296&highlight=keyboard") thread, I've changed my keyboard settings from EN English (United Kingdom) to EN English (United States).

Further reading suggests that activating [_'slow keys'_]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/59616") is the cause. However, considering that my keyboard does not work straight from the get-go when KDE loads, I'm not sure if this is the cause.

This is much more than a "hugely annoying" problem - it's more like a **deal-breaker**. With both keyboard and mouse disabled on startup, I have absolutely no way to access settings in KDE. 

First time I've used linux in 12 years, so I expect *some* issues. What I do *not* expect is no working input devices. Am extremely disappointed, but will try to perservere. However, I am mindful of W.C Fields' quip, [I]"If at first you don't succeed, try, try again. Then quit, no use being a damned fool about it".
[/I]

**Update:** tested F3 Keymap and F5 Accessibility options from KDE loader screen. Keyboard defaults to USA and set accessibility options to none. KDE loads and nada. No input devices.

I'm **done** with Kubuntu 8.04.1 - I'll try Ubuntu 8.04.1 tomorrow, when I get some time.

Regards

---

### Post by putonghua73 on 2008-11-01
I know it's bad form to reply to my post, but I have experienced the *exact* same problem with Live CD for Ubuntu 8.10

This leads me to believe:
(1) Configuration issue, or
(2) Bad source files at [_pendrivelinux.com_]("http://www.pendrivelinux.com/")

I'm leaning towards a configuration issue, rather than a bad data source because both Kubuntu 8.04.1 and Ubuntu 8.10 report no errors on disk, therefore I'm less inclined to believe it is a data issue since the problem *only* occurs once the DE loads.

I've noticed that Ubuntu 8.10 has a 'On-screen Keyboard' option, within F5 Accessibility options. I'll perservere and see if I can find some configuration options to allow my input devices [keyboard and mouse] to be recognised.

Not an emergency or in any rush as I'm performing a 'test-run' at this stage via the Live CD (at least that was the intention ;-)), and I am relatively happy with Win XP. I also have other more immediate priorities that are occupying my time. 
 
I think it would have been easier (if I had time) to configure Arch linux from scratch ;-) At least, I *might* have my input devices working ..

**Update:** after some targetted googling i.e. site:ubuntu.org disabled keyboard and mouse, I found [_this_]("http://ubuntuforums.org/archive/index.php/t-186689.html") archived thread which suggests that the problem is caused by USB legacy option enabled in BIOS. Okay. Time to disable and re-test. Cross all of your extremities and wish me luck, folks!

**SOLVED!**
Disable USB Keyboard and Mouse support in BIOS. Save, then boot. 
Am typing from Ubuntu 8.10 Live CD - and am loving the simplicity and elegance of Gnome so far. Feel so *responsive* by comparison to Win XP. Time to install on my USB drive so I can take this baby for a test-run to make sure that everything works and then evaluate whether I will be in a position to permanently delete Win XP in a couple of weeks time.

---

### Post by Izmmm on 2009-02-01
Hey there having what I believe to be the same problem.  I installed 8.10 (Ubuntu) and everything was going smoothly until first boot.  Keyboard and Keypad are responsive until I get to the login screen and than nothing.

I'm using a Dell Latitude C600.  Anyone got any tips?

Thanxz Izmmm

---

### Post by Izmmm on 2009-02-01
Well I installed Kubuntu to see if it would make any difference.  No such luck it once again freezes on the login screen.  Any thoughts?

Thanxz Izmmm

---

### Post by kdekeyboarddeadafterlogin on 2009-05-13
Symptom: shortly after a graphical login to KDE the keyboard fails to respond.
Test 1: Before login, repeated pressing of the capslock/numlock keys will ordinarily cause related lights to flash on the keyboard where such lights are present. Once logged in, repeated pressing causes no lights to flash.
Test 2: other users on the same computer /can/ use their keyboards once logged in.
Test 3: keyboard becomes operable again once mouse used to log out.
Cause: Kde accessibility tool "Slow keys" has become active on that account.
Solution: Log in to kde as per normal. Depress and hold a shift key for more than 8 seconds: two beeps will be heard, then a dialog for slow keys will be presented. Click 'continue' to agree to deactivate slow keys. Keyboard should now respond properly.
Test environment here: KDE 3.5.10, based on Kubuntu 8.04.1

Cheers y'all -- A

---

