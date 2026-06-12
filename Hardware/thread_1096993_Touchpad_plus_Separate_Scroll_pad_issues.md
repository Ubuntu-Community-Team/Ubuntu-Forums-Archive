---
title: "Touchpad plus Separate Scroll pad issues"
date: 2009-03-15
forum: Hardware
---

### Post by dilbertjcg on 2009-03-15
Ok so I'm a relative Newb.  I've played around in the past on Ubuntu, but have finally had it with Windows and have gone full bore into Ubuntu Ibex.  I have almost everything working and even got my Flash, Dreamweaver, and World of Warcraft working under Wine.

However I have a couple issues, the most notable is my Synaptics touchpad. I have one of those touchpads that has a separate pad just for vertical scrolling.  The problem is that I have two vertical scrolling areas now, one on the vertical scrolling designated area and one on my touchpad.

I've tried so many different things from updating and modifying my xorg.conf file, my hal file, to downloading gsynaptics and seeing if that could help, all while restarting X server a bunch of times, and logging in and out.  Nada.  

In fact I had to reinstall at one point because something in the xorg.conf file caused me to not be able to boot up.  Now I'm kind of leary working on it.  Now with my fresh install I don't have anything in my xorg.conf file or any hal file under third party apps for Synaptics.

I'm completely lost and would appreciate any help you could give. For now I just have scrolling turned off.

---

### Post by gonintendo on 2010-07-17
bump i have the same issue

---

### Post by gonintendo on 2010-07-17
i should add im using 10.4 so i can't edit the xorg.conf (apparently it doesn't exist anymore)

---

### Post by demosthenese on 2010-07-17
Try this. First list your input devices

```
xinput --list
```

You should see your synaptics device listed there. On my laptop it is "SynPS/2 Synaptics TouchPad"

Then turn off the scrolling region but adjust the command to the device name found by the previous command.

```
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Synaptics Edge Scrolling" 8 0 0 0 
```

Hopefully this won't turn off your secondary scroll pad too.

If you want to make the change persistent then you will need to put the latter command in a script and run it at login.

---

### Post by gonintendo on 2010-07-19
so if i use this in the terminal, it will reset when i reboot? meaning there is no harm done if i just try it?

---

### Post by gonintendo on 2010-07-19
k i tried it and it ended up turning the separate scrolling region off.

---

### Post by gonintendo on 2010-07-28
bump

---

