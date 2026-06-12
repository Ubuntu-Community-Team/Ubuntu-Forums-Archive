---
title: "Support for extra Vaio buttons?"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by Orochi on 2007-06-07
I have Feisty installed on my Sony Vaio computer. The Vaio comes with a lot of extra buttons such as play/pause, next, previous, launch dvd player, and volume controls. The mute button works since it appears to be a hardware switch, but the rest of the buttons do nothing in Ubuntu. Are there drivers available that let you use these extra buttons?

---

### Post by 444 on 2007-06-07
Try going to Keyboard Shortcuts and pressing those keys to set them to certain tasks. Works for mine...

---

### Post by Orochi on 2007-06-07
That works for most of the media buttons, but volume up, volume down, and the launch dvd player button all show up as the same key in keyboard shortcuts. The DVD button doesnt really matter, but I'd like to be able to properly use volume up and down if possible.

---

### Post by 444 on 2007-06-07
Run 'xev' from the command line and try to get the keycodes for them. If they are different then I think you can put the keycodes in Shortcuts, if they're the same I dunno what to say...

---

### Post by Orochi on 2007-06-07
Yeah they all have the same keycode :( Guess I'll have to assign some other buttons to be sound control.

---

### Post by yingjai on 2008-01-16
Just curious. Will there ever be any support for these media keys or has the community given up on it? I understand that xev reports the different media keys to have the same keycode, but how come Windows can separate them from one another?

---

### Post by sammydadams on 2008-01-17
what is model?...i'm running gutsy and they all work on mine play/pause and everything else up there works in Exaile...i'm on a fz180e laptop tho......a lot of the Fn buttons dont work tho...only mute for me

---

### Post by tuatha on 2008-01-18
The (badly named) jog-dial keys work in media players (eg RhythmBox), ie 
vol+, vol-, play/pause, prev, next but, as you say, the events detected by X (as shown by xev) appear to be the same (below was for the |<< (prev) & >>| (next) keys).

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  111 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

You can see 2 & 111 but don't get excited because this is Vol+ & Vol- respectively:

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  111 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Surely there must be a lower level keyscanning application that detects what the BIOS sees not just the X abstraction layer?  I'll have a dig & see what I can find (not a Linux expert but will play around a bit more on this)

tuatha (Sony Vaio FZ-21S)

---

