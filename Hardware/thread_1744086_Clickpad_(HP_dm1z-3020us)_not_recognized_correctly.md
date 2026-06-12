---
title: "Clickpad (HP dm1z-3020us) not recognized correctly on 11.04?"
date: 2011-04-30
forum: Hardware
---

### Post by seebs on 2011-04-30
Basic summary:  I have an HP dm1, which is an 11ish inch netbook based on an AMD E-350.  It's pretty decent, and I have gotten wireless working with some help from previous threads.  I'm running 11.04 (the recently released CD version) x86_64.

However, the clickpad pointing device is definitely not all working yet.  Reading around, there is advice to build and install something called &quot;synaptics-dkms&quot; which is a new version of the synaptics driver.  This doesn't work (it won't compile for this kernel), but the Ubuntu bug report on it also suggests that this is already in Natty.  However...  The trackpad doesn't seem to be properly identified.

Adding

Options &quot;AreaBottomEdge&quot; &quot;3700&quot;

to the relevant hunk in xorg.conf.d makes it sort of close; the trackpad doesn't jump around madly when I try to click and drag at the same time.  However, there's no distinction being made between left and right clicks.

It looks as though the xorg driver should be saying it identified this device as a clickpad, but it doesn't.  The logs say... oh, wait.  I don't know how to cut and paste without a working right-click.  Anyway, they say they found a synaptics touchpad, but the word &quot;clickpad&quot; is not used, and everything I've seen suggests that if it's not there, it means the driver is not actually configured correctly to recognize this touchpad.

(If you are not familiar with the term:  &quot;clickpad&quot; means that there is a physically-clicking area of the touchpad which is still also a touchpad surface.  On Windows, and on Linux too when the driver is working, &quot;right click&quot; is identified as a click event where the pressure is on the right side of the touchpad.)

The multitouch functionality isn't working, but the touchpad seems to scroll if I move my finger up and down on the right side of the touchpad.  This is tolerable, but really sort of not what I want.

For what it's worth, I have basic Unix clue and know enough about Linux to mess around with drivers a bit.  I'm more a programmer than a sysadmin, though, and haven't done much in kernels and device drivers.  I am, however, quite willing to put a fair amount of idle time into trying to debug this or fix it.

---

### Post by teak421 on 2011-04-30
I tried to load on my DM1z as well and got the same thing... I'm not as experienced as you so I said that the trouble is not worth it.... I'll wait for a bit and I am sure everything will work great!

So, another few months of bloated Windows on my PC.

Take Care!

- Michael

---

### Post by seebs on 2011-04-30
Okay, I found something in another thread:  [http://ubuntuforums.org/showpost.php?p=10744640&postcount=202](http://ubuntuforums.org/showpost.php?p=10744640&postcount=202)  I followed the quoted instructions in post #202, now everything is peachy with the trackpad.  I don't need the AreaBottomEdge thing anymore, and indeed, I don't have it; I can use the whole trackpad to move around, and click+drag still works, as does right click.  Yay!

---

