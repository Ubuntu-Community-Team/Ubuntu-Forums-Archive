---
title: "Mouse click from terminal"
date: 2008-07-13
forum: General Help
---

### Post by Squid Tamer on 2008-07-13
I hate to bother all of ya'll, but I'm looking for a program that allows me to send a mouse click to from the terminal (or more importantly, a script).

I have xvkbd, and it's website says it can do clicks, but all of my attempts have failed.

I've been googleing my fingers off, but I can't find anything.

Please tell me if you know of such an program, or can help me with xvkbd

```
 xvkbd -text "human brain"
```works just fine, but 
```
xvkbd -text \m1
``` and all variations that I have tried so far only type m1.

---

### Post by Squid Tamer on 2008-07-13
Bump

I won't bump this again. I think repeated bumping is bad manners. I'm surprised this didn't get a single view.

---

### Post by marshag63 on 2008-07-13
Squid Tamer, what is "\ml" supposed to do?  What kind of mouse are you using?

marshag63

---

### Post by Squid Tamer on 2008-07-13
Apparently it (or something like it) is supposed to generate a click of the first mouse button. I've tried with spaces, and quotes, but none work.

The website says "\m*digit* - simulate click of the specified mouse button"

I don't think the type of mouse should matter, but it's a wireless optical mouse.

---

### Post by marshag63 on 2008-07-13
Have you defined your mouse in xorg.conf?  Isn't xvkbd an on-screen keyboard?

I found a gentoo howto for setting up a mouse.

[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations)

---

### Post by Squid Tamer on 2008-07-13
My mouse works fine. xvkbd is a virtual keyboard, but it can be used from the terminal using the -text option. The text function works fine, but it's website claims it can generate mouse clicks by using "\m". The man page does not mention this feature.
```

"\m*digit* - simulate click of the specified mouse button "
```

^It says that on it's website, [http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/)

Thanks for the help anyway.

---

### Post by marshag63 on 2008-07-13
You want a left click, correct?

\[keysym] - the keysym keysym (e.g., \[Left])

Oh, I get it now "\m1" means left click is first (1) button?  Maybe check to see what xorg.conf is saying your left mouse button is.  You are specifically want to send a left click to the terminal?

I also found this - says its under xvkbd properties window.

"Automatic Click
    Set on/off of the automatic click feature and the delay before automatic click is activated. If this feature is set, xvkbd will work as if left mouse button is clicked when mouse pointer is moved on a button and stays long enough. You may want to set Jump Pointer? to OFF to avoid auto-repeating."

---

### Post by Squid Tamer on 2008-07-13
Correct, though I tried xvkbd -text \m[left], and xvkbd -text \[left], but they just type out "[left]. I wonder if I have an outdated version.

---

### Post by marshag63 on 2008-07-13
Perhaps taking a peak at xorg.conf can shed some light on what is assigned as left mouse button.  

marshag63

---

### Post by tarvtarv on 2009-12-21
Hows goin mate i was looking for the same thing and found it here [http://ubuntuforums.org/showthread.php?t=1275341&highlight=mouse+click+recorder]("http://ubuntuforums.org/showthread.php?t=1275341&highlight=mouse+click+recorder")

the link is for xdotool wich i have just been playing with great if your ok with a terminal.

One thing it dosent refrence in either xdotools help or the above thread is the the sleep switch usage:sleep x = sleep x seconds.

The sleep function is great, Cause if your using xdotool it all happens really quick so if you need to have it wait a while between clicks use the sleep switch.

Cheers happy scripting

---

