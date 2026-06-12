---
title: "[SOLVED] send files from smartphone to ubuntu (bluetooth)"
date: 2008-11-08
forum: General Help
---

### Post by Gonz_91 on 2008-11-08
Hi everyone!

I've seen some tutorials on this, but they all seem a bit outdated, so here it goes:

I've recently found (hehe) my bluetooth dongle, which was lost on the stuff I have on top of my piano, so I plugged it in ubuntu, and i worked. (that's nice)

Now, the problem is, I can send data to my 6680 phone but not from the phone to the laptop. It finds the laptop, I click send, it say "sending..." and then fails, with nothing appearing on Ubuntu.


Can anyone help?

---

### Post by Gonz_91 on 2008-11-08
Got it, just installed gnome-bluetooth



xD

---

### Post by sleepingdragon on 2008-11-09
Strengely, the KDE4 bluetooth tools don't work very well for me. My phone can see the computer (Emblaze Touch 7), but not the other way around. 

To fix this, I installed the Gnome bluetooth tools into KDE4 and added the program "bluetooth-sendto" into the list of programs offered to certain file types - usually listed as "Open With...". I've done it that way so that only certain compatible files can be transferred, namely .jpg .mp3 .mp4 .3gp. This works very well and keeps with the authentication proceudres normally set with bluetooth.

All this used to work with the KDE tools in 8.04, so I'm guessing it's just a bug in a new system.

---

