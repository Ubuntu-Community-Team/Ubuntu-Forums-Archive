---
title: "Getting the buttons on a laptop to work..."
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by [Cyanide] on 2005-08-09
I have an eMachine M5305 laptop, everything works wonderfully.

But there are a few buttons that I'd like to get to work. Well actually it seems like they work (according to xev) but there's just no applications tied to them so they don't launch/do anything.

Is there a way to configure these dummy buttons to launch whatever the hell I want?

Here's the output xev gives me when I press one of the buttons:

```
KeyPress event, serial 29, synthetic NO, window 0x3600001,
    root 0x48, subw 0x0, time 17178280, (133,271), root:(149,368),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

```

---

### Post by s_p_a_r_k_y on 2005-08-09
yea, I have a "Mail" button at the top of my laptop. I went to System->Preferences->Keyboard Shortcuts and simply clicked the action i wanted to assign the button to and pressed the button. Now I just hit that button to load e-mail ooo how to meet kinky local girls...my favorite e-mails..

hope it helped

---

### Post by [Cyanide] on 2005-08-09
[QUOTE=s_p_a_r_k_y]yea, I have a "Mail" button at the top of my laptop. I went to System->Preferences->Keyboard Shortcuts and simply clicked the action i wanted to assign the button to and pressed the button. Now I just hit that button to load e-mail ooo how to meet kinky local girls...my favorite e-mails..

hope it helped[/QUOTE]

Ahhhh I didn't realize it was that easy, now I feel like a retard :grin:

---

