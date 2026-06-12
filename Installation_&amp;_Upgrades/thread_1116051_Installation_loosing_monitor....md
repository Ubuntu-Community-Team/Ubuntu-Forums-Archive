---
title: "Installation loosing monitor..."
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by smartidiot1989 on 2009-04-04
Hello! Today i finally decided to install Ubuntu. I burned a disc and rebooted my computer at which point i got the Ubuntu screen and a bunch of options.

When i choose to install, i get the Ubuntu logo and a loading bar for a while then my computer restarts.

I can see absolutely nothing on my monitor, but I can hear my DVD-drive and Harddrive obviously doing something. After a few minutes my monitor is "Out of range!".

Any idea what's my problem? :( I heard currently there are bad driver support for ATI cards but that shouldn't give me this kind of result? Here's my computer specs..

Phenom II 920 x4 2,8ghz
2 x 1GB Cellshock
DFI LP DK790FXB M2RSH
**HD3870 512MB**
**Monitor: Benq FP241W**

It was Ubuntu 8.10 I tried to install.

---

### Post by tlois on 2009-04-04
It does sound as though a video card problem.  Do you have another computer available to see if it will work on it as live boot? Another way to give more clues is if you have your speakers turned on- if you hear the bootup drums, but video goes into standby, then a vid driver problem I would assume.

---

### Post by smartidiot1989 on 2009-04-05
> **tlois said:**
> It does sound as though a video card problem.  Do you have another computer available to see if it will work on it as live boot? Another way to give more clues is if you have your speakers turned on- if you hear the bootup drums, but video goes into standby, then a vid driver problem I would assume.
I did as you said, and I can hear the bootup drums, so it seems as if my Video Card goes into standby for some reason?

Is there a way to solve this problem?

---

### Post by Pasdar on 2009-04-05
It sounds like the frequency settings are too high, go into safe mode and change the video settings.

---

### Post by smartidiot1989 on 2009-04-05
> **Pasdar said:**
> It sounds like the frequency settings are too high, go into safe mode and change the video settings.
Could you specify frequency settings?

---

### Post by wpshooter on 2009-04-05
1) Have you checked the intregrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?  You should ALWAYS do this first before attempting to install Ubuntu on a system for the first time.

2) Have you tried installing using the safe graphics mode parameter ?

3) If #2 does not work, then try installing from the ALTERNATE (text based) CD version of Ubuntu instead of the live/desktop version.

---

### Post by Pasdar on 2009-04-05
> **smartidiot1989 said:**
> Could you specify frequency settings?
I'm sorry. I didn't read your message properly and thought you had already installed it. If you already had a functioning Ubuntu and ever got a message, "Out of Range", it is because the monitor frequency settings are outside of the range of what can be displayed by your monitor. You are actually trying to install it, and that changes things. It must be caused by something else.

---

### Post by balaknair on 2009-04-05
At the first screen you get on booting from the CD, choose the 'safe graphics mode', this usually works if your video card is giving you trouble and allows you to install Ubuntu. After installing, boot into Ubuntu, and install the proprietary drivers(don't change any video settings till you do this), and restart. Now you can increase the resolution and enable desktop effects.

---

