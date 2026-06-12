---
title: "How to Disable Left Ctrl and Alt Keys"
date: 2008-11-26
forum: General Help
---

### Post by Tips on 2008-11-26
I'm looking for a way to completely disable the left Ctrl and Alt keys on my Thinkpad T43.

The reason is because I have a repetitive strain injury in my left hand that is made worse whenever I make the movement to hit Ctrl-c and Ctrl-v.  I try not to hit those key combinations, but I forget because it's a habit :)

If I could disable those keys I think my hand will get better more quickly because I'll be forced to learn to use the right-side Ctrl and Alt keys.

---

### Post by kanikilu on 2008-11-26
You can use xmodmap to do this. See this post for an example:

[http://ubuntuforums.org/showpost.php?p=5276944&postcount=3](http://ubuntuforums.org/showpost.php?p=5276944&postcount=3)

---

### Post by Tips on 2008-11-26
Thanks... 

I tried this command:

```
~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

Then this, based on the link you mentioned:

```
xmodmap -e '0x25 = NoSymbol'
```

I got this error:

```
$ xmodmap -e '0x25 = NoSymbol'
xmodmap:  unknown command on line commandline:1
xmodmap:  1 error encountered, aborting.
```

Is the NoSymbol supposed to be typed literally?  I also tried it with *sudo*.

---

### Post by Tips on 2008-11-26
Update -- I tried this:

```
xmodmap -e "remove mod1 = Alt_L"
```

It looks like it did something, but the left ALT key still works:

```
~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1      ,  Alt_R (0x71),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)

```

(ALT_L is gone now)

I was using this page for ideas:
[http://www.xfree86.org/4.0.1/xmodmap.1.html](http://www.xfree86.org/4.0.1/xmodmap.1.html)

---

### Post by kanikilu on 2008-11-26
To disable the Left Control:

```
xmodmap -e "remove Control = Control_L"
```

To re-enable the Left Control:

```
xmodmap -e "add Control = Control_L"
```

To disable the Left Alt:

```
xmodmap -e "keycode 64 = "
```

To re-enable the Left Alt:

```
xmodmap -e "keycode 64 = Alt_L Meta_L Alt_L Meta_L Alt_L Meta_L"
```

Note: My left alt is "64", yours may be different, use the "xev" utility to check.

---

### Post by Tips on 2008-11-27
Thanks! That worked perfectly...

---

### Post by Tips on 2008-12-07
For anyone looking to do this for some reason I put this in my startup sessions to make it permanent:

```
xmodmap -e "remove Control = Control_L";xmodmap -e "keycode 64 = ";xmodmap -e "remove Shift = Shift_L";
```

---

