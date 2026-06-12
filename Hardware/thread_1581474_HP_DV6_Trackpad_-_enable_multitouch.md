---
title: "HP DV6 Trackpad - enable multitouch?"
date: 2010-09-25
forum: Hardware
---

### Post by rumplestilts on 2010-09-25
I believe I managed to enable multitouch on my HP DV6-1030us trackpad after a previous install of Lucid Lynx but I don't remember what I had to download and/or config. I just re-installed from scratch and now need to enable that feature again but, of course, it's not enabled in the mouse preference for the trackpad.

I know someone's already done this and I figured I'd ask here and, perhaps, a kind soul will provide the answer.

Thanks!
Rumple

---

### Post by Stratosmacker on 2010-12-25
Bump... I just got one of these for Xmas, I really don't want to use Winblows just because of a trackpad issue. Any help would be appreciated most gratefully.

---

### Post by pi/roman on 2010-12-26
You should be able to refresh your memory using my guide here:
[http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

In step 4 there are 2 sections: one for Karmic and earlier and one for Lucid and probably later releases, so you can ignore the Karmic section.

---

### Post by Stratosmacker on 2010-12-30
pi/roman Ive been messing around with your link for a while. It is a very good and intuitive link, but unfortunately while Ive managed to get some things working some things still don't due to the nature of my trackpad. The whole thing detects movement, even the button parts meaning when Im holding down the left mouse and dragging at the same time, if my finger im dragging with is lifted the mouse jumps across the screen because I have a finger on the left click button (which is sensitive like the rest of the trackpad). Any ideas on a parameter In synclient that I could change to alter where the trackpad picks ups movement so that the buttons at the bottom are not sensitive to this type of input?

---

### Post by pi/roman on 2010-12-30
You could try adjusting "areabottomedge". For the initial setting try something close to the "bottomedge" setting you see when you list the synaptics options. Then keep lowering it and running your finger along the bottom edge of the touchpad until it stops registering a touch. Then you can raise it back up a little bit and that should be the optimum setting.

---

### Post by Stratosmacker on 2010-12-30
> **pi/roman said:**
> You could try adjusting "areabottomedge". For the initial setting try something close to the "bottomedge" setting you see when you list the synaptics options. Then keep lowering it and running your finger along the bottom edge of the touchpad until it stops registering a touch. Then you can raise it back up a little bit and that should be the optimum setting.

Thanks Ill try that. I didnt know how to work the parameter AreaBottomEdge correctly because when I tried it earlier I set it to one, and the touchpad stopped working momentarily

---

