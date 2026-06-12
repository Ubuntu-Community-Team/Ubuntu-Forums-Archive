---
title: "Media Volume Keys"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by nhandler on 2007-07-15
I have Ubuntu Gutsy running on a Dell Inspiron 6000 laptop. Using System->Preferences->Keyboard Shortcuts, I mapped the volume media keys to Mute, Volume Up, and Volume Down. The problem is, they are modifying the Line In volume level instead of the Master volume level. Is there any way to change this? Thanks.

---

### Post by hangthedj on 2007-07-15
You may have to set the default channel, i know for kmix you right click on the sound icon then choose 'select master channel'.

---

### Post by nhandler on 2007-07-16
Well, I think I already have the gnome equivalent applied. When I right click on the volume icon on my panel, I am able to select preferences. Then I am able to choose the device and track to control. My sound card and the master level are already selected.

Any other ideas?

---

### Post by joe.turion64x2 on 2007-07-16
I have the same problem, you are running the latest kernel, aren't you?

When I updated to it broke the audio system too.

---

### Post by nhandler on 2007-07-16
I'm running the newest versions of everything in Gutsy. I don't think it was an upgrade that busted this. I can't remember it ever working for me.

---

### Post by bobbyrj3d on 2007-07-17
I had the same problem on Feisty. To fix it I went to System > Preferences > Sound, and under Default Mixer Tracks I selected PCM (or whatever your master channel is).

Hope it works!

---

### Post by nhandler on 2007-07-17
Thanks a lot. That solved the problem. Now I can control the Master volume level using the media keys on my keyboard.

---

### Post by thecure on 2007-09-26
> **bobbyrj3d said:**
> I had the same problem on Feisty. To fix it I went to System > Preferences > Sound, and under Default Mixer Tracks I selected PCM (or whatever your master channel is).

Hope it works!

Running Gutsy and the latest updates killed mine volume controls also but your fix worked for me also. Thank you.

---

