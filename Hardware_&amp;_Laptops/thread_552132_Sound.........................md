---
title: "Sound........................"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Keymone on 2007-09-16
alsa sound is working only for root user. any suggestions? please......

---

### Post by Keymone on 2007-09-16
and yes - i am in the audio group. when i run amarok from under root user everything is fine and when i run from under my user it says "xine was unable to initialize any audio devices". both amaroks are configured to use alsa sound drivers.

---

### Post by Keymone on 2007-09-16
any suggestions?
i promise i will delete my windows xp after i will get sound under linux - this is the only reason holding me :)

---

### Post by NightCrawler03X on 2007-09-16
Try, as root, running "alsaconf", NOTE - Make sure that X is not running.
Follow the on screen instructions, choose what you think will work, then logout/login, startx, and test soemthing (as user) that plays sound.

If all goes well, your sound should work quite nicely with all the correct permissions.

PS:
When I say "as root", I don't mean "su".
Kill X so that you have a console login, and actually specify login name "root", then type your root password.

---

### Post by Keymone on 2007-09-17
did not help :(

any way to completely remove everything sound-related in ubuntu? and install it from scratch?

---

### Post by dabl on 2007-09-17
> **Keymone said:**
> alsa sound is working only for root user. any suggestions? please......

Is it possible that you were logged in as the root user when you were configuring something?  Or perhaps when you were copying your music files onto your Linux system?  Just throwing out ideas here -- are you sure you (the user) have permission to play what you are attempting to play?  It could be more of a "permissions" problem than a "ALSA sound" problem.  :)

---

### Post by Keymone on 2007-09-17
thanks for reply, no, i'm sure it is ALSA problem - files i am trying to play located on NTFS volume with R access for everyone. and the message i get when start amarok is something like "xine was unable to initialize any audio drivers".

---

