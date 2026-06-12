---
title: "How can I temporarily map the ENTER key to the SHIFT key (see picture)?"
date: 2012-01-26
forum: Hardware
---

### Post by rocksockdoc on 2012-01-26
My Lenovo X61 keyboard lost it's ENTER key about a week ago (the three-piece key has two cheap plastic 'spring' thingeys on the underside, one of which has a tab that broke off. The other cheap piece of plastic is intact, as is the actual key).

I've been using the ENTER key without the top & the two plastics below it ... but today, the little blue cup fell off. Now I'm stuck!

I never bought the two pieces of plastic below a key before but I assume they're available somewhere (or maybe I have to buy a whole new keyboard).

Until I buy a new set of plastic springey things (or keyboard if I can't find just the two pieces of plastic below the key), can you tell me how to REMAP the ENTER key to, say, the SHIFT key?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211473&stc=1&d=1327612744[/IMG]

---

### Post by wolfen69 on 2012-01-26
There are some good answers [here]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys"). But it sounds like you will need a new keyboard, which are pretty cheap.

---

### Post by rocksockdoc on 2012-01-26
> **wolfen69 said:**
> There are some good answers [here]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys"). 

That thread was great ... and it referenced this thread:
- [B][Assign PgUp and PgDn keys - eeePC]("http://ubuntuforums.org/showthread.php?p=11643313#post11643313")
[/B]
Here's what I tried based on that advice.

```
Here is how I tried to switch the mapping of the ENTER key to the SHIFT key
(and vice versa):

$ uname -a
REPORTS:
Linux box 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux

$ which xmodmap
REPORTS:
/usr/bin/xmodmap

$ which xev
REPORTS:
/usr/bin/xev

$ xev
(ignore the next fifty lines or so)

PRESS THE ENTER KEY (notice the third line):
KeyPress event, serial 33, synthetic NO, window 0x5600001,
    root 0x110, subw 0x0, time 263441120, (738,242), root:(771,314),
[COLOR=DarkRed]     state 0x0, **keycode 36** (keysym 0xff0d, **Return**), same_screen YES,[/COLOR]
    XLookupString gives 1 bytes: (0d)
    XmbLookupString gives 1 bytes: (0d)
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5600001,
    root 0x110, subw 0x0, time 263441271, (738,242), root:(771,314),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    XLookupString gives 1 bytes: (0d)
    XFilterEvent returns: False

PRESS THE SHIFT KEY (notice the third line):
KeyPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x110, subw 0x0, time 263592202, (464,368), root:(497,440),
[COLOR=DarkRed]     state 0x0, **keycode 62** (keysym 0xffe2, **Shift_R**), same_screen YES,[/COLOR]
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5600001,
    root 0x110, subw 0x0, time 263592298, (464,368), root:(497,440),
    state 0x1, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

What's important is the third line of each keypress:

FOR:
state 0x0, keycode **[COLOR=DarkRed]36[/COLOR]** (keysym 0xff0d, **[COLOR=DarkRed]Return[/COLOR]**), same_screen YES,
The name "Return" is the name of the behavior of the key pressed.
The number of the key pressed is "36".

state 0x0, keycode [COLOR=DarkRed]**62**[/COLOR] (keysym 0xffe2, **[COLOR=DarkRed]Shift_R[/COLOR]**), same_screen YES,
The name "Shift_R" is the name of the behavior of the key pressed.
The number of the key pressed is "62".

REVERSE THE MAPPING:
$ xmodmap -e "keycode 62 = Return"
$ xmodmap -e "keycode 36 = Shift_R"

SAVE THE RESULTS:
$ xmodmap -pke > ~/.Xmodmap
$ vi ~/.xinitrc
ADD
 xmodmap ~/.Xmodmap

```

The main problem was that the reversal did NOT work.

The ENTER key was mapped to the SHIFT_R key; but the SHIFT_R key was not mapped to the ENTER key. Go figure.

So I must conclude a SHIFT_R key is more complex than the RETURN key.

In addition, I need the SHIFT_R, so I will try out a different key to use for the currently defunct RETURN button.

---

### Post by rocksockdoc on 2012-01-26
Since swapping the SHIFT_R key with the RETURN key only worked in one direction, and, since I need the SHIFT_R key ... I tried swapping the BACKSLASH (\) key with the enter key instead.

This worked (barely) ... but it will do for now (until I buy a new key spring).

```

$ xev
(ignore the first fifty lines or so)
\
REPORTS: 
state 0x0, keycode **[COLOR=DarkRed]51[/COLOR]** (keysym 0x5c, **[COLOR=DarkRed]backslash[/COLOR]**), same_screen YES,

```So, now we know:
keycode 36 = Return
keycode 51 = backslash

So, to swap the RETURN key and the BACKSLASH KEY:
```

$ xmodmap -e "keycode 51 = Return" 
$ xmodmap -e "keycode 36 = backslash"  

```Then, to make a log of the new keyboard mapping:
```

$ xmodmap -pke > ~/.Xmodmap

```To make the change permanent, I put this line in the ~/.Xinitrc file & rebooted:
```

$ vi ~/.Xinitrc  
  xmodmap ~/.Xmodmap
$ sudo reboot

```Interestingly, the change was NOT permanent! 

What happened was that there was NO MAPPING on the boot screen; but as soon as I logged into the boot screen, up popped this question of whether to load the keyboard re-map file or not:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211501&stc=1&d=1327639812[/IMG]

Only after loading the keyboard map file did the mapping take effect.

So I'd say it works ... almost perfectly ... so it's good enough for now (until I buy new key springs).

---

### Post by gleble on 2012-07-09
How did you use the terminal without an enter key?

---

