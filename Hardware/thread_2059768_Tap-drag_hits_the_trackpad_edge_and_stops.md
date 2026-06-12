---
title: "Tap-drag hits the trackpad edge and stops"
date: 2012-09-18
forum: Hardware
---

### Post by sleekweasel on 2012-09-18
My trackpad works fine in most ways - two finger scrolling, etc. but if I 'enable mouse clicks with touch pad' and then use tap-drag to select text without using the trackpad buttons, and hit the edge of the trackpad while I'm dragging, I'm stuffed - the pointer stops moving sideways and I have to start the select all over again, typically using the trackpad buttons this time.

On older Linux boxes (Linpus, for instance) I'm fairly sure that if I hit the edge of the trackpad (while dragging, but maybe all the time), the pointer would move (slowly) in the direction of the edge I'd hit, so if I waited, it would (eventually) reach where I wanted to finish selecting.

On Mac, if you're doing a tap-drag and hit the edge, you quickly jump your finger to the other side of the trackpad and continue the drag as if you hadn't jumped your finger - much like you pick up a mouse and place it elsewhere on the table if you run out of physical space while trying to move the screen pointer.

Either of these solutions (or something equally functional) would suit me, but there doesn't seem to be anything like this in Ubuntu just now - certainly nothing in the Mouse/Trackpad System Settings, which only offers 'enable mouse clicks with touchpad' along with the scrolling options and pointer speed.

I'm not even sure what to call what I'm looking for, to Google for it -- Drift margin? Coast border?

Thanks!

---

### Post by Kopkins on 2012-09-18
Not sure what the issue is, but it seems that it is something with your install. In ubuntu 12.04 on my computer, selecting something, running out of room, results in the mouse slowly continuing.

Best of luck,

Kopkins

---

### Post by sleekweasel on 2012-09-22
Hmm. Well, although I definitely don't see the edge-drift behaviour, I found out that the Synaptics touchpad driver supports the Mac-style 'finger-jump' behaviour - it's just that Gnome doesn't expose it:

xinput list | grep -i touchpad
&#9116;    ETPS/2 Elantech Touchpad                  id=12   [slave  pointer  (2)]

xinput set-prop 'ETPS/2 Elantech Touchpad' 'Synaptics Locked Drags' 1
xinput set-prop 'ETPS/2 Elantech Touchpad' 'Synaptics Locked Drags Timeout' 350

I've added those to my 'start-up applications' and now I'm happy, if surprised at Gnome not making this available... but perhaps they don't have a good way to detect exposed behaviour all the way through their messaging stack.

Edit: Also, there's the rather less obvious solution that has been working all along without my noticing, although it doesn't feel as natural as edge drift or locked dragging: if you hit the edge of the trackpad, then move slowly back to the middle, then quickly towards the edge, whereupon the acceleration coefficient will mean that the pointer is 'thrown' further in that direction and you're not right up against the edge now.

Edit2: Aha, I found the edge drift behaviour - while my trackpad has multi-touch, it doesn't seem to know about pressure - seems to report 0 or 1. So the default settings:

        Synaptics Edge Motion Pressure (360):   30, 160
        Synaptics Edge Motion Speed (361):      1, 212
        Synaptics Edge Motion Always (362):     0

needed tweaking so the 'low' pressure threshold was 1 instead of 30,

xinput set-prop 'ETPS/2 Elantech Touchpad' 'Synaptics Edge Motion Pressure' 1, 160

and while I was there set the minimum motion speed to 120 (much better than 1) and the edge motion to 'always on':

xinput set-prop 'ETPS/2 Elantech Touchpad' 'Synaptics Edge Motion Speed' 120, 212
xinput set-prop 'ETPS/2 Elantech Touchpad' 'Synaptics Edge Motion Always' 1


Perhaps it does know about pressure and I need to tweak some coefficient, but this is plenty for now. And again, still surprised that Gnome's trackpad configurator doesn't expose any of this.

---

