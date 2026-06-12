---
title: "Disable Compositing From Terminal?"
date: 2009-12-06
forum: Hardware
---

### Post by likemindead on 2009-12-06
Need HALP.

I made the mistake of trying to enable compositing in Xubuntu 9.10 & my laptop immediately informed me that I had made a grievous error.

Now when I'm in Xfce, all I get is horrid white lines everywhere.

How do I turn compositing back off via the CLI? I'll also need help with vi/vim. I'm not terribly used to them. Many thanks in advance.

---

### Post by likemindead on 2009-12-06
I did it! Thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=425477"). Looks like it works in Karmic too. Here's what I did.

First, I hit Alt+Ctrl+F2 to get the the CLI. Then I logged in. Then the following.

```
sudo nano /etc/X11/xorg.conf
```

Due to the weirdness that *buntu has made of Xorg you will be creating a new file. Add the following.

```
Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection 
```

Hit F3 to save. Then exit nano (Ctrl+x). Then reboot "sudo reboot". I have my Xfce desktop back! And the notifications are no longer garbled! Huzzah!

---

