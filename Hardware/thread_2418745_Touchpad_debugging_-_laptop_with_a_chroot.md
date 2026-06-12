---
title: "Touchpad debugging - laptop with a chroot"
date: 2019-05-10
forum: Hardware
---

### Post by pbn5012 on 2019-05-10
I have an Chromebook running Ubuntu with KDE Plasma in a chroot  through Crouton. I recently updated it to 18.04 which I believe is  unsupported right now so this might be futile because the kinks simply  haven't been worked out yet.

  The touchpad has an unusual malfunction which I haven't exactly  pinned down yet. In some contexts, when I tap, release, and then drag, the mouse  continues to hold down. For example, in Dolphin, if I drag the mouse  across the screen, it selects a box, the way you would expect it to  after a double tap. I can't figure out how to get it to release mouse  and stop highlighting when I move the mouse around. In particular, this pathology occurs in the Touchpad settings menu when I hover the mouse over the test "click" button.

  In other contexts, like a textbox, a deliberate double-tap and drag  (which should implement "click and drag") seems to give up and spontaneously release the click automatically after a short period of time, maybe a little less than half a second. For example if I tried to highlight this  paragraph by doubletapping at the upper left and dragging down to the  corner it would only highlight the first few words. If I double tap and  drag in Dolphin, the cursor only *starts* highlighting after half a second. I'm not sure what to make of this.

  There is also a touchscreen. I have no reason to believe any inputs from the touchscreen are interfering here.

  I have tried to use xev to debug but I don't think it is capturing  the data I need, such as whether a click is being held down through a  drag.
  I am on a Chromebook like I said and I don't think the limited  functionality of the chroot allows for virtual terminals within it. So I  can't figure out how to run evtest because I don't know how to get X to  release the touchpad.

The problem is not present upon startup and appears randomly and persists some random amount of time (15 minutes? 2 hours?) after using the machine for a while.

  Any advice?

---

