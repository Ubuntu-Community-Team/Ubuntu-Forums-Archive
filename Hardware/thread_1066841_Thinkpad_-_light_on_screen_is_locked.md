---
title: "Thinkpad - light on screen is locked"
date: 2009-02-11
forum: Hardware
---

### Post by Thomaes on 2009-02-11
At first, I could easily adjust the "light" on the screen with the correct keys.

Now, after an update it seems, the light on the screen is locked at one level. That is, I can try to change it with the keys, it'll register it but won't actually do anything. It's stuck.

I've got a lenovo thinkpad r61, and the Ubuntu I've installed is just the default. No meddling with system files at all.

---

### Post by Fire_Chief on 2009-02-11
Are you referring to the screen brightness?
As you said, this would normally be adjusted by using the Fn + Home or Fn + End keys to increase and decrease the screen brightness.

You may want to check the settings in System -> Preferences -> Power Management. It has settings for the screen brightness level.

Cheers!

---

### Post by Thomaes on 2009-02-11
Yes, I was thinking of the brightness.. I'm tossing the slider in power management around but nothing is happening. If I take the power adapter out of the computer, nothing happens. Usually, the brightness would be slightly dimmed.

---

### Post by Fire_Chief on 2009-02-11
You could try the tpb application (found in Synaptic) which produces an onscreen display for all thinkpad specific buttons.

Not sure if it actually controls the functions though.
By chance do you know if the function key shortcuts are disabled in the BIOS?

Also, do you happen to know what those recent updates were?

Cheers!

---

### Post by Thomaes on 2009-02-11
No, when I press the correct keys, that bar with the current brightness pops up on the screen. It's slow to respond though, like, lagging seriously. Even though the bar changes, the actual brightness on the screen doesn't change.

---

### Post by era86 on 2009-02-11
I know on the T61 this is solved by updating the BIOS.  You may want to check that out on the Lenovo website.

---

### Post by Thomaes on 2009-02-11
Hmm, strange. It worked when I first installed Ubuntu. Could some kind of update ensure a failure in the brightness controller?

---

### Post by Katja.f on 2009-02-11
I have the same problem on my ThinkPad x61s: it worked a month ago or so, but does not work any more. Today I needed to restart my computer a couple of times till the brightness was ok -- it was too bright when I used it on battery and then too dark when plugged in. I think this bug is described here: 
[http://ubuntuforums.org/showthread.php?t=1018511](http://ubuntuforums.org/showthread.php?t=1018511)

But how can I downgrade to 2.6.27-10 if it is not on the list in synaptic?

---

### Post by era86 on 2009-02-13
Katja - I believe the Kernel image is still available on the machine.  You just have to modify the GRUB to display the kernel you want.  Did you upgrade from a previous version or do a clean install on your X61?

Thomas - could be an update with the power manager?  I recall having the same issue. Have you tried looking here: [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by smbm on 2009-02-24
I had this problem on my R61. This fixed it for me:

[https://bugs.launchpad.net/linux/+bug/311716/comments/75](https://bugs.launchpad.net/linux/+bug/311716/comments/75)

---

