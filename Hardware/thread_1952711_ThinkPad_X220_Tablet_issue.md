---
title: "ThinkPad X220 Tablet issue"
date: 2012-04-04
forum: Hardware
---

### Post by sean.d on 2012-04-04
Good evening. I've just gotten myself a new ThinkPad X220 Tablet Notebook.  It's a fantastic machine, but, i have a couple of questions.

1) When i rotate the display, it does not realign the touchscreen input properly.  I.e. if i spin the display 180 degrees, the touch input is 180 degrees off.  There a fix for this?

2) can i somehow set up the Screen Rotation button to either rotate the screen, or open the Display settings panel?

I'm running Ubuntu 12.04 (precise)

---

### Post by Favux on 2012-04-04
Hi sean.d,

This is the X220t resource thread:  [http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)

You need to rotate the wacom input tools along with screen orientation.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

### Post by sean.d on 2012-04-06
Thanks!

I've got the script squared away and working, but, i'm trying to bind it to one of the two buttons on my screen bezel.  I tried setting a keybinding to that script in CompizConfig Settings Manager.  However, pressing said button does not do anything.

I'm sure i'm doing something stupid here... any tips?

---

### Post by Favux on 2012-04-06
Dealing with key codes is described in the Rotation HOW TO mainly in appendix 2.

Check if you see anything, if immediately after you press the bezel button in question, you run:
```
dmesg | grep atkbd
```

---

### Post by SaintDanBert on 2012-05-20
> **Favux said:**
> Hi sean.d,

This is the X220t resource thread:  [http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)

You need to rotate the wacom input tools along with screen orientation.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

I cannot get my X220-tablet to report any sort of key or event
for the screen-bezel buttons (1) orientation, or (2) refresh.
That Redmond software sees and processes them just fine.

Suggestions?
~~~ 0;-/ Dan

---

### Post by sean.d on 2012-05-29
> **Favux said:**
> Dealing with key codes is described in the Rotation HOW TO mainly in appendix 2.

Check if you see anything, if immediately after you press the bezel button in question, you run:
```
dmesg | grep atkbd
```


I get nothing.

---

### Post by lazlo on 2012-05-30
Maybe you should try to run

```
sudo showkey
```

and press the buttons on the bezel.

This way I was at least able to identify the keycodes that were somehow assigned to the buttons on Ubuntu 12.04 for my X201T.

---

### Post by Favux on 2012-05-30
Sure, and usually the message includes "unknown" button or key, so try grepping "unknown" also.

---

### Post by SaintDanBert on 2012-05-30
I see the following:
```

prompt$  dmesg | grep atkbd


[159902.728084] atkbd serio0: Unknown key pressed (translated set 2, code 0x6c on isa0060/
serio0).
[159902.728094] atkbd serio0: Use 'setkeycodes 6c <keycode>' to make it known.
[159903.026735] atkbd serio0: Unknown key released (translated set 2, code 0x6c on isa0060
/serio0).
[159903.026745] atkbd serio0: Use 'setkeycodes 6c <keycode>' to make it known.

ooo

```
I have no idea which physical thing this is complaining about.
How do I confirm that 0x6c is the bezel button?

~~~ 0;-/ Dan

---

