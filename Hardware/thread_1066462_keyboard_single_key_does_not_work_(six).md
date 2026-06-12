---
title: "keyboard: single key does not work (six)"
date: 2009-02-10
forum: Hardware
---

### Post by Marconaut on 2009-02-10
Hello all,

I have a strange problem with my keyboard on Ubuntu 8.10 kernel 2.6.27-9 on a Dell XPS M1530 notebook. Funny enough I only discovered this because a password working elsewhere didn't work on my new Linux (I got a lot to work here but I would still consider myself a newbie..):

The problem is I cannot type "six": 123457890 is all the numbers I get. Not that I find six more important than other numbers, but I would really like to have it working on my keyboard.

Here is what I get using xev when I type 5 six 7 (of course six meaning the number, I cannot type it!):

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1352942, (270,793), root:(1265,819),
    state 0x10, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XmbLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1353014, (270,793), root:(1265,819),
    state 0x10, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1353540, (270,793), root:(1265,819),
    state 0x10, keycode 16 (keysym 0x37, 7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XmbLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1353612, (270,793), root:(1265,819),
    state 0x10, keycode 16 (keysym 0x37, 7), same_screen YES,
    XLookupString gives 1 bytes: (37) "7"
    XFilterEvent returns: False


I am using a german keyboard and set the layout to Generic Evdev-managed keyboard. The '&' associated with 'six' on the same key works fine as you can see. I have not found any other key not working.

What can I do? I thought I could start crying but decided not to.

Cheers,
Marco

---

### Post by Marconaut on 2009-02-12
I forgot to mention that the 'six'-key works before I log in (when typing the user name) and it also works wen bootin WinXP.

If I do

xmodmap -pke

I get

....
keycode  13 = 4 dollar 4 dollar onequarter currency onequarter
keycode  14 = 5 percent 5 percent onehalf threeeighths onehalf
keycode  15 = 6 ampersand 6 ampersand notsign fiveeighths notsign
keycode  16 = 7 slash 7 slash braceleft seveneighths braceleft
keycode  17 = 8 parenleft 8 parenleft bracketleft trademark bracketleft
....

so here actually everything seems ok to me.

Anyone can give me hint on how to fix this problem.

Marco

---

### Post by Marconaut on 2009-02-18
Hello there,

I finally found something that seems to be the same problem and it solves mine:

[http://ubuntuforums.org/showthread.php?t=785029](http://ubuntuforums.org/showthread.php?t=785029)

I guess this should be reported as a bug...
How would I do that?

Cheers,
Marco
(who can type "6" now!)

---

