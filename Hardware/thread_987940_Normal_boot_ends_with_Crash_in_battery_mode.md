---
title: "Normal boot ends with Crash in battery mode"
date: 2008-11-20
forum: Hardware
---

### Post by vikofle on 2008-11-20
Hi all,

I do have a strange problem on my Lenovo/IBM Thinkpad R61, which I seem unable to fix.

After upgrading to 8.10 everything worked fine and normal. I then stumbled upon Hibernation/Standby option in the logoff-dialogue window and have chosen one of the two (dont remember which, however).

Ever after that, when booting on battery power, I see the normal ubuntu logo-boot splash but when the boot process is done and X/GDM login should come up I only see a black Display. Even switching to the terminal by CTRL-F1-F6 doesnt work. I dont get any reaction from the notebook. (although the blinking LEDs tell me its doing something). It seems like a total freeze

When the notebook is plugged to the power line (not running on battery mode) I do have a normal behaviour and a working X.

I swear everything worked fine until that hibernation/standby thing which is why I believe it has something to do with that

Can somebody shed some light on this?

Vik

---

### Post by Steve413z on 2008-11-27
I'm having the same problem, I think it might be a configuration file somewhere.

I think i'm gonna reinstall from scratch this weekend.

---

### Post by Steve413z on 2008-11-27
try:
```
sudo dpkg-reconfigure xserver-xorg
```I think that fixed it for me, however it's a problem that doesn't happen all the time, so it's hard to be sure

But I'm having this problem on a ThinkPad T60 with an ATI x1400

EDIT: I just realized this turns off FGLRX ... so not good advice

---

### Post by Steve413z on 2008-12-02
EDIT: Nevermind that doesn't work either

---

### Post by Steve413z on 2008-12-03
Okay, i finally figured it out, it's a problem with FGLRX

you can duplicate the crash by typing:
```
sudo aticonfig --set-powerstate=1
```[SIZE=3]

now...  this is what finally fixed it for me:
[/SIZE]```
sudo aticonfig --auto-powerstates=off --effective=startup
```[SIZE=3]

this stops the GPU from going into power saving mode, but it stops it from crashing, so hopefully there is a bugfix for this coming from ATI soon
[/SIZE]

---

