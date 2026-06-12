---
title: "Issue with graphics on Acer Aspire One Netbook"
date: 2014-05-10
forum: Hardware
---

### Post by ryan84 on 2014-05-10
So I have this old Acer Aspire One netbook that had Windows XP on it. Because XP was very sluggish on it and also due to end of support, I installed Ubuntu 13.10 on it as a second partition. A few days ago, I upgraded it to Ubuntu 14.04 and I got this message.
[IMG]http://i.imgur.com/EnBZEpPl.jpg[/IMG]
Then, I get a terminal that looks like this
[IMG]http://i.imgur.com/oNFgEdJl.jpg[/IMG]
I have no idea why it no longer works. It worked well before upgrading.

---

### Post by Bashing-om on 2014-05-10
ryan84; Hi ! Welcome to the forum .

Maybe, you had a proprietary graphics driver installed, and in the upgrade process it got broke.

Try and boot with the 'nomodeset' boot option for ATI/Nvidia chip sets (most common).
Tutorial:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If you boot with an added boot parameter, will look at making the proper adjustment to install the graphics driver.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mörgæs on 2014-05-11
For hardware from the XP era L/Xubuntu is often a better choice.

---

### Post by MartyBuntu on 2014-05-11
It's a netbook with relatively weak graphics.

LXDE or MATE desktop for best results.

---

### Post by Yellow Pasque on 2014-05-11
Please give output of:
```
lspci -k
```

Just copy/paste the text. Do not take a screenshot.

---

### Post by ryan84 on 2014-06-24
OK, I have no idea what anyone is saying. Can you give me a better explanation?

---

### Post by Yellow Pasque on 2014-06-24
You are being urged to do a fresh install of an Ubuntu variant that does not run the Unity desktop (since Unity requires decent 3D acceleration which your netbook may not be capable of).
[http://lubuntu.net/](http://lubuntu.net/)

Otherwise, please follow direction in my previous post (Ctrl+Alt+T to open a terminal).

---

