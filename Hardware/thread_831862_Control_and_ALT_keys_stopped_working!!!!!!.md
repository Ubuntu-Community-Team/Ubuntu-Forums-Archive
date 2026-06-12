---
title: "Control and ALT keys stopped working!?!?!?!?!?!?"
date: 2008-06-17
forum: Hardware
---

### Post by neurostu on 2008-06-17
I don't know what happened but my control and alt keys just stopped working.  I was using them fine until BAM one second they just stopped.

I spent a couple hours on it yesterday but couldn't  get them working again, so I just did a clean re-install hoping that would fix the problem.

It did for a while until a few minutes ago they stopped working again.

Here are the symptoms:
Control Keys don't work WHEN LOGGED IN(even when I change keyboards)
Control keys work when I'm at the login screen
CNTL+ALT+F1 changes to vitural console, 
CNTL+ALT+Backspace restarts X

One more thing:

when I press control (like to use Control-C or control-v) its almost like the text field I'm typing in gets deselected.

I ran xev to see what was up:
Here is what I get when I press control:
```

FocusOut event, serial 528, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 528, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 528, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

as opposed to 
```
KeyPress event, serial 528, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 685600, (4,163), root:(1099,213),
    state 0x0, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 528, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 685704, (4,163), root:(1099,213),
    state 0x1, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
which I get from pressing Shift.

When I press ALT I get the same out put as CNTL.

I think it might have something to do with XChat as it stopped working when I was using xchat... 

I really don't want to have to do a clean reinstall but I will if I have too..

---

### Post by neurostu on 2008-06-17
So I just did a clean install and the problem is still there?  I am going crazy!

---

### Post by neurostu on 2008-06-17
It looks like it is a compiz bug as when I disable all desktop effects the problem goes away.

---

### Post by drewster1829 on 2010-12-29
> **neurostu said:**
> It looks like it is a compiz bug as when I disable all desktop effects the problem goes away.

Old thread, but your comment allowed me to fix it..I lost the functionality of both Ctrl keys on my Acer laptop, and it was due to Compiz. 

Whenever you get the "FocusIn Event" "FocusOut Event" from xev, I think it means the key is bound to something else. What happened on my install is that I had Ctrl-CapsLock set to initiate the Scale plugin in Compiz-Fusion (using Compiz Settings Manager). Well, discovering that I could disable the CapsLock key in the Keyboard settings, I did so.  This is when the problem started.

The thing is that re-enabling the Caps Lock key didn't fix it, so I was stumped as to the cause, until reading this post...apparently that Ctrl-CapsLock bind was somehow switched to just Ctrl (but Ctrl didn't initiate scale by itself...neither did Ctrl-Capslock with Caps Lock disabled). By changing the bind to the Scale plugin to Ctrl-` (the grave symbol), the problem went away...I still have CapsLock disabled, and Compiz runs now, with no problems at all with the Control Keys.

---

