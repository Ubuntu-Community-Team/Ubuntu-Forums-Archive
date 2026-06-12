---
title: "My  daughter borked the touchpad"
date: 2011-02-28
forum: Hardware
---

### Post by Docaltmed on 2011-02-28
I gave my daughter a HP TX2510 laptop, on which she is running Lucid. Tonight, "the internet was *really* slow!" she said, "so I hit the little button above the touchpad. Now nothing works!"

In short, she clicked the button which disables the touchpad. I can plug in a USB mouse and get full functionality, but I can't for the life of me re-enable the touchpad.

I have, of course, tried rebooting with the touchpad enabled and disabled.

grep tells me that the computer sees the touchpad.

I tried messing with the settings under System>Preferences>Mouse.

I'm out of ideas. Can anybody help me?

(btw, daughter asked me "what do I do with problems like this [she can break a computer from 50 paces] when I'm in college?"

"Get a geeky boyfriend," I said.)

Anyway, as I said before: Any suggestions as to how to restore the touchpad?

---

### Post by Favux on 2011-02-28
Hi Docaltmed,

Could be the disable button itself.  Some gunk in there or a spring/contact gone bad?

I hope not.  I'd really hate to try and take it apart just for that.  And that button looks tiny.  Even thinking about it makes me cringe.

Favux

---

### Post by Chronon on 2011-02-28
Try installing gpointing-device-settings and then use the Pointing Devices entry in Preferences.  Maybe it can help.

Why did you tell us the color of her hair?

*EDIT* Hopefully it isn't a hardware failure as Favux has suggested.

---

### Post by Hedgehog1 on 2011-02-28
> **Docaltmed said:**
> ...
In short, she clicked the button which disables the touchpad. I can plug in a USB mouse and get full functionality, but I can't for the life of me re-enable the touchpad.
...


Does the disable/re-enable button have a little LED next to it that lights up when enabled?  If so, is it going on and off?

That would rule out the button itself getting stuck.

If there is no LED, if you boot from the liveCD does the touchpad work?

Looking for options here...

:KS

---

### Post by overdrank on 2011-02-28
Some off topic post were removed. Title edited. Please stay on topic. :)

---

### Post by Favux on 2011-02-28
Hedgehog1 is right about the LED.  Should have thought of that myself.  Head slap.

---

### Post by Docaltmed on 2011-02-28
> **Hedgehog1 said:**
> Does the disable/re-enable button have a little LED next to it that lights up when enabled?  If so, is it going on and off?

That would rule out the button itself getting stuck.

If there is no LED, if you boot from the liveCD does the touchpad work?

Looking for options here...

:KS

The LED goes from red to blue when I press it.

And when I boot from the liveCD, the touchpad works correctly.

That probably helps. What should I do next? (If I need to mess around with the command line, that's cool, I don't mind getting my hands dirty.)

---

### Post by Docaltmed on 2011-02-28
Found the solution[ here]("http://ubuntuforums.org/showpost.php?p=10454533&postcount=14").

> Create a file called
/etc/modprobe.d/touchpad.conf

You can do this by typing
sudo gedit /etc/modprobe.d/touchpad.conf
in your terminal (Applications --> Accessories --> Terminal). It will ask for your password

when the file opens put in it
options psmouse proto=imps
Save the file and restart.

---

### Post by Hedgehog1 on 2011-03-01
> **Favux said:**
> Hedgehog1 is right about the LED.  Should have thought of that myself.  Head slap.

I was right about something?!?!?!

Wait - I got to write today down somewhere.....

OP - Glad you were able to fix it!

---

