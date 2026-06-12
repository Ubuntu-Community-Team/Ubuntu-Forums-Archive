---
title: "Touchpad stop working after shutting the lip"
date: 2017-10-08
forum: Hardware
---

### Post by kazakore on 2017-10-08
It's a pretty new laptop but I'm sure it wasn't doing this a couple of weeks ago as I have carried it between rooms without noticing this until just the other day. But when I close the lid the touchpad stops working. Occasionally it may start working later, like many minutes later. But so far right now it's been 20 minutes and it's not started working again so far this time. Often I just log out and in to get it back again....

Laptop is a HP EliteBook 840 G2, so supposed fully Ubuntu Certified (*cough cough* what a load of bleep that is!) since 14.04.

I run Ubuntu Studio 16.04 so XFCE based.

Opening up settings and disabling and re-enabling the trackpad does nothing. The buttons related to the trackpad work all the time, except when the full trackpad is disabled through the setting previously mentioned. Luckily this laptop has the control nipple and two sets of buttons so easier than most for getting around the system while touchpad is disabled if I really need to.....


What can I do to get my touchpad to always work and not die on closing the lid? Or at least how can I bring it back? Is there a synaptic deamon that can be stopped and started or something? Why would this suddenly break?


EDIT:

OK just noticed additional slightly strange behaviour. If I close the lid and open it then the mouse works on the lock screen. I type my password and enter the session and it's not working there.

Also touching the trackpad makes the keyboard backlight activate so it is seen to some extent, but it doesn't move the pointer...

I've tried xinput disable/enable and it doesn't help.


I only quite recently enabled the lock screen so that's probably why I've only just noticed this issue. Pretty sure it's related to that.

---

### Post by martinr on 2017-10-08
Hi kazakore,

I'm also experiencing Synaptic problems on Xubuntu 16.04. You could try the following when the touchpad is kaput.
```

$ sudo modprobe -r psmouse
$ sudo modprobe psmouse

```

---

### Post by kazakore on 2017-10-09
I have a feeling mine might be related to lightdm, the login manager in use (I believe) but maybe it's more general with locking and not the session manager....

> **martinr said:**
> Hi kazakore,

I'm also experiencing Synaptic problems on Xubuntu 16.04. You could try the following when the touchpad is kaput.
```

$ sudo modprobe -r psmouse
$ sudo modprobe psmouse

```

Yeah that seems to work. Removing the module stops both mouse (trackpad and nipple) working, whereas nipple continues working on lid open, then after reloading it both come back within a couple of seconds.

Thanks :)

---

### Post by martinr on 2017-10-09
> **kazakore said:**
> I have a feeling mine might be related to lightdm, the login manager in use (I believe) but maybe it's more general with locking and not the session manager....

You could test that by configuring not to lock the screen when the lid is closed. Then close the lid and see if the touchpad is frozen.

---

### Post by kazakore on 2017-10-11
> **martinr said:**
> You could test that by configuring not to lock the screen when the lid is closed. Then close the lid and see if the touchpad is frozen.

That's pretty much what I did but without enough testing to be conclusive....

I had recently enabled the lock screen and shortly after noticed the problem. Posted the thread before the idea had clicked. Trackpad was freezing every time (although not always forever.)

Disabled the lock and trackpad worked every time.

But now I've taken my laptop to work so re-enabled the lock and the trackpad is also behaving itself after closing the lid....

---

### Post by martinr on 2017-10-11
Disabling lightdm didn't make a difference in my case.
Left-clicking once or twice sometimes unfreezes the keyboard, but not the touch-pad.

---

### Post by kazakore on 2017-10-14
Well strangely mine has been stable since disabling the screenlock feature and re-enabling it. Can't say I actually got to the bottom of the problem though...

I hope you find a cure to yours martinr. Symptoms definitely sound a little more extreme than mine though as my keyboard always worked fine.

---

