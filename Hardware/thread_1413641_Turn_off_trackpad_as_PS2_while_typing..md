---
title: "Turn off trackpad as PS/2 while typing."
date: 2010-02-22
forum: Hardware
---

### Post by wbest on 2010-02-22
I have the HP mini 210 with UNR running.  The trackpad does not work correctly from the onset, but I found a thread here that advised me to use:

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
To fix it.  I did, but unfortunately lost my ability to scroll.  The actual buttons worked, but it only reacts like a very simple trackpad (tap to click still works).

Worse, I can't figure out how to set it so it doesn't react when I accidentally press it while typing.  Since I had to use somehat basic functions to get it to work, I don't think any of the mouse options in System seem to work.

So I'm looking to you The Collective to help me figure this problem out.

---

### Post by pi/roman on 2010-02-22
Did it work better before you added the option to psmouse.mousprobe ?

---

### Post by wbest on 2010-02-23
Well, I didn't have the "Ignore while typing" thing on.
But the trackpad worked itself.  What didn't work was the buttons at the bottom (actually part of the trackpad, like the new Macs).  Scrolling did work.  As did 'Tap to click,' just not the actual buttons.
Then, to get the buttons working, I had to run the psmouse command.  Now I don't have many option for the mouse.  I'm considering trying to undo the psmouse thing and just stick with tap to click as the way I work the mosue.

---

### Post by pi/roman on 2010-02-23
I will have to research what the option> psmouse proto=exps does.
In the meantime I have a guide which can you can use to try to configure options:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

---

### Post by pi/roman on 2010-02-24
I tried this option multiple times by first unloading my touchpad driver by:
```
sudo modprobe -r psmouse
```

then reloading it with the exps option by:
```
sudo modprobe psmouse proto=exps
```

Most of the time my touchpad didn't work but one time it loaded as a regular mouse so I believe your touchpad is being loaded as a regular mouse with this option which is why you are not able to use any touchpad features.

---

