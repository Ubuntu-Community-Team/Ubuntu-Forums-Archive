---
title: "CRT problem"
date: 2009-01-01
forum: Hardware
---

### Post by sluthy on 2009-01-01
I've had my 8.04 box up and going for a while, and initially it had a 15in LCD 1280x1024 on it that worked fine. Then, we fixed up the old XP box and gave the monitor to it and replaced it with an old 15in Dell CRT from a neighbour. It works fine - the BIOS page, GRUB etc starts and loads fine, and the Ubuntu orange loading bar screens loads fine, but once it gets to the login page, it goes all screwy.

The screen is overlaid on itself ~5 times so there's 5 cursors running around and it's barely legible. I try changing the resolution down to 1024x768 but the change won't hold, either over VNC or locally. Then, when I manage to navigate the mess and restart it/shut it down, the orange bar progress shutdown screen is perfect.

Is this a driver issue, or a config issue? Any ideas?

---

### Post by sluthy on 2009-01-02
Bump. Wow, one day and the thread's already 9 pages back.

---

### Post by Sprut1 on 2009-01-02
Probably xorg.conf - basically you need to find the correct resolution, this is not a widescreen?

---

### Post by sluthy on 2009-01-02
LCD is 5:4, CRT is 4:3 (I assume).

I can change the resolution now - for some reason I couldn't before, maybe some conflict while trying to change it over VNC? Doesn't fix the problem however.

Anyway, I've got some photos up to try and explain what it looks like. These are at 1024x768.

[VNC screenshot, what it should be]("http://photos-e.ak.fbcdn.net/photos-ak-snc1/v1957/189/62/571047750/n571047750_1697276_636.jpg")
[What it actually looks like]("http://photos-c.ak.fbcdn.net/photos-ak-snc1/v1957/189/62/571047750/n571047750_1697274_9460.jpg")
[Same, with the main menu open]("http://photos-d.ak.fbcdn.net/photos-ak-snc1/v1957/189/62/571047750/n571047750_1697275_73.jpg")

What I can't explain is why it's only happening after booting. If it was a hardware or connection problem (CRT's VGA cable is a permanent one), it would be present right from boot. But no, it's perfect until the Username: screen. If it was a problem with X or some other config problem, it would've been present on the LCD wouldn't it?

The only thing I can see is the monitor is 60Hz, but the Screen Resolution box says 61Hz. I'm assuming this is just semantics, but could it be a sync issue?

---

### Post by linux_tech on 2009-01-02
In terminal type:
```
xrandr
```
 to see if there are any other resolution settings available

---

### Post by sluthy on 2009-01-03
Hmm, nope. Nothing but the standard choices.

This is bizarre. I'm considering swapping the two computers' displays around again just to get things working (the other computer's on its last legs anyway by the looks of it, motherboard keeps losing HDDs on startup).

---

### Post by sluthy on 2009-01-04
...okay, scratch what I said about the LCD being fine - I swapped them, and it's doing the exact same thing. That writes off the CRT as a problem, and suggests the onboard graphics perhaps? I've also noticed the onboard gigabit NIC is also now only reporting as 100Mbit, please don't tell me the motherboard's stuffed? Unless I've installed a dodgy automatic update?

---

