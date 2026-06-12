---
title: "Wacom Bamboo Not Working"
date: 2010-09-20
forum: Hardware
---

### Post by RFXCasey on 2010-09-20
I just installed 10.04 on my laptop and my Wacom Bamboo tablet isn't working. I have the xorg-wacom module installed but still I'm getting no love. When I start up Gimp and go to preferences/input devices I enable the LinuxInput device but I don't see an option under it for my tablet. I must be doing something wrong.

---

### Post by Favux on 2010-09-20
Hi RFXCasey,

What model of the Bamboo do you have?  Is it one of the newer ones with touch?  If so it won't work out of the box, you need to make some changes.

---

### Post by RFXCasey on 2010-09-21
It's one of the newer wacom pen and touch models. I had it working before in 9.04 or 8.04 I can't remember which but it seem like it's busted in 10.04

---

### Post by Favux on 2010-09-21
Hi RFXCasey,

Basically you have to compile a new wacom.ko to get it working.  And because xf86-input-wacom was so new when Lucid came out (default is 0.10.5) there have been significant improvements so you'll want to compile a newer version of it too.  See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by RFXCasey on 2010-09-22
Wow, that's a pretty drawn out process. It was working great under 9.04 but I can see it seems to be a driver issue. I'll give this process a shot tonight when I get home. Looks like it might take a while.

---

