---
title: "eeepc 901: no wakeup after standby"
date: 2008-11-17
forum: Hardware
---

### Post by scooby79 on 2008-11-17
Hi!

I have a problem with wakeup after standby: I press Fn + F1 (Zzz), blinking cursor, next ist black screen and two blinking leds. I press "Power"-button, leds go on, but display remains dark. Strg+Alt+Backspace doesn't do anything, I have to hard power down.

My configuration is:

- eee 901
- Ubuntu-Eee (downloaded yesterday)
- both ssd are ext2, sda1 = /, sda2 = /home, no swap partition

I'd be very thankful for any hints, because I need standby very often.

---

### Post by silkstone on 2008-11-17
Have you installed the Array kernel?

I'm using a 901 with Ubuntu-eee which has the Array kernel built in. I've set Power Management to Suspend when I close the lid, and it wakes up perfectly by pressing any key.

Hibernate (probably) won't work with no swap, but Suspend should.

If you prefer to stick with eeebuntu, a new version will be out in a week or so, based on Intrepid and with the Array kernel.

---

### Post by scooby79 on 2008-11-17
From array.org

"Please note, if you have already installed Ubuntu-Eee v8.04.1 or Eeebuntu 1.0, you already have my kernel and you're linked into the repository! You don't need to do anything else!"

So I guess, I already have the right kernel. Unfortunately suspend doesn't work at all yet...

-------------- edit ------------------

Solution was: Deplug an USB-Hub which is for ext. mouse and keyboard. With the hub plugged in, I get the freeze while resuming. Without the hub no problems. I need suspend/resume only "outdoor", so that solves my problem.

---

### Post by silkstone on 2008-11-17
Can you check on that? Ubuntu-eee 8.04.1 uses the Array kernel for sure, but the posts on the eeebuntu forum suggest that this may not until the new version is released.

**uname -r** will display the version. Mine is...

```
silkstone@silkstone-eeepc:~$ uname -r
2.6.24-21-eeepc
```

I've tried suspend and awake several times this evening, and it seems to work for me.

EDIT/ Usually I suspend by closing the lid (set to suspend in Power Management) but I've just tried it with Fn-F2 and that works too.

If your kernel is xxx-generic it is not the Array one.

---

### Post by benjamw on 2009-08-05
I am having a similar problem with my 1000H.  If I suspend it (via either closing the lid, or pressing Fn-F1 (Zzz) ), when I try to wake it again, the LEDs come on like it wants to do something, but no screen, it's totally blank.

While testing a theory about my USB mouse receiver, I noticed that when the computer came back out of suspend (but with the blank screen), I could just make out a hint of something on the screen.  It looked like a password field, and as I typed, I could barely see it doing something.  It seems that the computer did wake from suspend OK, but it didn't turn on the LCD screen lamp.

Not sure why this is, or even how to fix it.  But it is rather odd, and if anyboody has any insights, please let me know.

---

### Post by sgosnell on 2009-10-13
Try the [2.6.30 kernel](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9).  The .30 kernel seems to handle the EEE-PC very well out of the box.  Everything works fine for me.

---

