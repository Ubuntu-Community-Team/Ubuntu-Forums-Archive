---
title: "Odd behavior of xrandr in Lucid/Karmic"
date: 2010-05-02
forum: Hardware
---

### Post by theSuperman on 2010-05-02
Ever since upgrading from Jaunty to Karmic, and even in my fresh install of Lucid, I have noticed a weird behavior with Xrandr.  In all previous versions, running just 'xrandr' would output the devices and their resolutions. Well, now in Karmic and Lucid, running xrandr will do that, but it will also activate all monitors connected.

(This is done on an EEE PC 1000)
EXAMPLE: I plug an external monitor into the VGA port. Run Xrandr. Will display resolutions, and will also enable that external monitor as an extended desktop. 

EXAMPLE2: I have my external monitor plugged in, and I run the command:
'xrandr --output VGA1 --auto --output LVDS1 --off' to turn off my internal screen and leave my external screen on. Running 'xrandr' again to see my current resolution will reactivate my internal screen.

I've never seen this behavior in any versions prior to Karmic.  Is this how xrandr is supposed to work? Im seeing issues running Totem while having an external screen connected. It acts as if 'xrandr' was run and will re-activate my internal laptop screen.

EDIT: Here is a video of what happens:
[http://www.youtube.com/watch?v=i-N_Elfhlzw]("http://www.youtube.com/watch?v=i-N_Elfhlzw")

---

### Post by theSuperman on 2010-05-02
Running 'compiz --replace' and various games with Wine also show the same issue as I mentioned with xrandr. 

Has anyone else seen this? I cannot be the only one.

---

### Post by theSuperman on 2010-05-07
I take it nobody notices this except for me? I cannot be the only one having this problem.

Lucid has been the most buggy version of Ubuntu that I have run.

---

### Post by manuw2009 on 2010-05-07
Hi
I'm facing troubles with xrandr too : turning off my laptop screen while tv out is on kills x
I thought it was due to my xorg edgers packages (which by the way help my intel card a lot !)
I found out compiz is involved too : turning it off enables me to switch my s video on but not to turn my laptop screen off...:(

---

### Post by theSuperman on 2010-05-07
> **manuw2009 said:**
> Hi
I'm facing troubles with xrandr too : turning off my laptop screen while tv out is on kills x
I thought it was due to my xorg edgers packages (which by the way help my intel card a lot !)
I found out compiz is involved too : turning it off enables me to switch my s video on but not to turn my laptop screen off...:(

Yeah I had the same problem in Karmic. I had to disable compiz before changing my resolution. It was a pain; I ended up writing scripts to always disable Compiz before changing resolutions. 

I find this problem to be worse than it was in Jaunty, since I am not able to run compiz at all on an external screen, nor can I use Totem or wine to play games.

---

