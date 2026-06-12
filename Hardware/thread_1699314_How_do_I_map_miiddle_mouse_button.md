---
title: "How do I map miiddle mouse button?"
date: 2011-03-03
forum: Hardware
---

### Post by Advice Pro on 2011-03-03
[LIST=1]
[*]How do I configure the middle mouse button?
[*]I downloaded *gpointing-device-settings*, but don't know where it is
[/LIST]

---

### Post by Copper Bezel on 2011-03-03
Map it to what, specifically? Is it not registering a click at all?

If you're not sure, open a terminal and run the command xev , then click the middle mouse button and see if it registers.

gpointing-device-settings should appear in System -> Preferences.

---

### Post by Advice Pro on 2011-03-03
[LIST=1]
[*]The middle mouse button does click.  In Win, it was an autoscroller.  I think in Linux I'll map it to *Enter* or Ctrl+W, some of my most used buttns.
[*]It's not there, I got this screen shot via the Context Menu over the Main Menu.
[/LIST]

---

### Post by Copper Bezel on 2011-03-03
Okay, let's try this then. (And I *think* this is no longer a Hardware question if that's the case, but a Desktop Environments question...?)

Install xdotool and, if you don't have it, Compiz Config Settings Manager.

```
sudo apt-get install xdotool ccsm
```

Open Compiz Config Settings Manager in System -> Preferences.

Select Commands, the first tile in the main CCSM window. 

On the "Commands" tab, set Command 1 to 

```
xdotool key Return
```

or

```
xdotool keydown 'Control' key 'W' keyup "Control"
```

On the "Button Bindings" tab, click box for Run Command 1 and set it to Button 2.

If this conflicts with anything else in CCSM, there will be a popup message that will allow you to disable anything else that's already assigned to Button 2.

Done!

Be warned that some Linux applications will require middle click - it can be very, very useful if left in its normal status. However, with CCSM and XDoTool, you can automate all kinds of features in this way, so they're worth playing with for ideas like this.

---

### Post by Advice Pro on 2011-03-03
After:```
sudo apt-get install xdotool install ccsm
```
I got the following error message:```
E: Couldn't find package ccsm
```

---

### Post by Hakunka-Matata on 2011-03-03
The code in post #4 Read:

```
sudo apt-get install xdotool ccsm
```

---

### Post by Advice Pro on 2011-03-03
Sorry about the typo, but I did get that error.

---

### Post by outskut on 2011-03-05
I just checked, I think the package that Bezel was talking about is called "simple-ccsm", so
$sudo apt-get install simple-ccsm
should do it.
-O

---

