---
title: "Keyboard madness"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by One Quick Question on 2005-10-18
This isn't really a hardware problem, the (PS/2) keyboard works fine, but something is going goofy in Linux, so I assume this is the right place to post. Or... I guess this is what the forum is for ...  Anyway, Linux is confused about my otherwise normal keyboard. This affects tty's too, btw, it's not just in X.
Background: My keyboard used to work fine.  But for a while now, (since Breezy maybe?  I haven't been paying attention), I was getting "*localhost kernel: atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.*" messages.  So, in an innocent attempt at correcting the problem, I found the problem was caused when I pressed the Print Screen key.  I looked up what that keycode was and found 111, so I entered the suggested command.   Apparently this is not it 111.   Either that or I did something else very wrong.  In fact, I don't know if this background information will even be helpful, but it's the best I can think up.

Here is the weird behavior:
As far as I know, all of my keys work properly by themselves.  When I do [Left shift]+[arrow key] though, the text is highlighted and promptly removed.  It has to be the left shift but it doesn't matter which arrow key. If I do that to files, it asks me if I want to delete them.   

Hmm... lemme get some xev results..

Ok, if I press left shift or the arrow keys, I get the proper output values, but the combination of them gets me this:

```

KeyPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707348, (157,8), root:(844,571),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707513, (157,8), root:(844,571),
    state 0x1, keycode 107 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""

KeyPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707522, (157,8), root:(844,571),
    state 0x1, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707588, (157,8), root:(844,571),
    state 0x1, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes:

KeyPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707597, (157,8), root:(844,571),
    state 0x1, keycode 107 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x9f, subw 0x0, time 72707750, (157,8), root:(844,571),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:

```

Out of more innocent idiocy, I also tested out what the kbd_mode command does.  I think I chose -s to start the experiment.  Wow was that a bad idea.  Lucky I knew the L_Alt+SysRq+R magic.  :roll:
Playing around with kbdconfig didn't help either.

I haven't tried rebooting because the system is a server.

Any thoughts?

---

### Post by One Quick Question on 2005-10-18
Ah... hm...  
This just in:  It doesn't always not work.   All of a sudden, it's working properly now.  After many hours of not working.     HMMM...

ARG.  DANGIT.

Don't temp fate.
I just switched to a tty to test it out...  But now all I have to do is press an arrow key for it to delete!!

...

Weirder still:  I went to xev to get some data, and as expected it thinks I'm pressing delete at the same time, BUT when I switched back here ... the arrow keys are fine all of a sudden.  
Except when I just now pressed the end key.  Now the arrow keys are going nuts AND so is the end key.

I suspect I can create more madness, but I don't feel like testing it all out.
... But I do it anyway..
Right now, Print Screen, Scroll Lock, Pause, Insert, Home, Page Up, Delete, End, and Page Down are all ending with Delete.  (This means that when I press the REAL delete key, I get two for the price of one!)

Oh man, this is the weirdest I've ever seen this machine act.

I'm going to go watch Sliders now.

---

### Post by One Quick Question on 2005-10-18
I feel that I shouldn't go and leave you all to watch goofy sci-fi on a bad note.  I am happy to report that, at the moment, everything is working as it should, except Print Screen, which still ends with delete.
I couldn't tell you what changed. All I did was check the system log in tty9 (modified inittab) for oddities and when I came back, it was wor ...  >:
It broke again. ... AND IT JUST FIXED ITSEL ... and it broke again.  
Wow, I've never felt so WTFy before.

---

