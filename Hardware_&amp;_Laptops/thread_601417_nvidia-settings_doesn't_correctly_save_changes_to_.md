---
title: "nvidia-settings doesn't correctly save changes to xorg.conf; reverts upon reboot"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-11-03
I have a friend with dual monitors (I myself have dual, but one is actually S-Video to a TV, instead of a computer monitor).  Everytime I want to show something on the TV, I have to open nvidia-settings, modify my twinview settings, and close.  Every time I've ever attempted to save the changes to the configuration to xorg.conf.... it appear to make changes, but they don't really seem to count for anything, and when you restart the computer, everything is back to single monitor mode the way it was before you changed settings.

I've put up with this idiocy with having to reenable my TV's output for over a year now, but my friend has two large flat panels he'd like to get compiz running on and not have to manually set up his monitors every time he turns it on.  How do I fix this?

---

### Post by Cyber-J on 2007-11-03
I think you need to run it as root, if you haven't already, to save the changes. From a terminal do:

% sudo nvidia-settings

At least that is what I had to do in order to get it do it for me. =)

---

### Post by Cyber-J on 2007-11-03
[Accidently posted twice. =])

---

### Post by diablo75 on 2007-11-03
I'm pretty sure that's what I've been doing, but I'll give it another shot and post my results.

---

### Post by diablo75 on 2007-11-03
sudo worked!  Though it's not the first time I've run the program with sudo....just got into a habit of not putting it in front for some reason.  Sweetness!
:guitar:

---

### Post by Jammerdelray on 2007-11-27
worked for me too, thanks

---

