---
title: "Dell 6400 volume keys stopped working"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by pertti on 2007-05-19
Hi all,

I have a Dell 6400 / E1505 laptop which has been working great with Ubunt, but a problem has appeared recently. The volume keys (mute and volume up/down) have stopped working for no apparent reason. The other multimedia keys work fine.

The funny thing is that it seems that they are "recognized", sort of. If I press the mute key the volume popup appears with the mute icon, but the sound isn't really turned off. If I try the mute a few times more the icon on the popup changes accordingly. If I press volume up, the popup shows the volume at ~5% (it starts at 0), but then key presses on the volume popup (not mute, not volume up/down). The real volume level doesn't change during all this, I have to change it using the volume applet.

I've checked and reconfigured the keys on the keyboard shortcuts preferences, but with no effect. Any idea?

Thanks in advance

---

### Post by darthnick on 2007-06-24
Hi,

I had the same problem and I solved it by going to **System > Preferences > Sound** and by **highlighting "Master"** in the "Default Mixer Tracks" list at the bottom. This will indeed bind the shortcut to the correct channel, the master one.

Hope this helps

---

### Post by pertti on 2007-06-24
> **darthnick said:**
> Hi,

I had the same problem and I solved it by going to **System > Preferences > Sound** and by **highlighting "Master"** in the "Default Mixer Tracks" list at the bottom. This will indeed bind the shortcut to the correct channel, the master one.

Hope this helps

Great! Thanks! I had already abandoned all hope on this one :D.

---

### Post by zadehas on 2007-06-30
Thank you, that solved my problem also. I would have never thought of it.

---

### Post by Jeruleus on 2007-07-09
Golly.  I had this problem and, in fact, had given up until today when it came up in a conversation I was having with a friend, at which point I decided to resume my search for a cure.  Thanks guys.

---

