---
title: "Xubuntu BT Catch 22"
date: 2011-04-07
forum: Hardware
---

### Post by qkzoo on 2011-04-07
Hello.

I installed Xubuntu because it's more lightweight than Ubuntu/Gnome.  One of the things it apparently lost was bluetooth support.  The problem here is that I don't have an internet connection without BT, so kind of a catch 22.  I do have a few aptoncds sitting around from a bloated Ubuntu install, but don't know which packages I need (browsing through archive manager).  In Ubuntu, I plug in my BT dongle, and wala, that's about it.  Any suggestions?

Q

---

### Post by qkzoo on 2011-04-09
I've since reinstalled Ubuntu, and am back to normal, but I'd really like assistance with this as I'd like to experiment with Lubuntu or go back to Xubuntu (although I don't really like Xubuntu file manager), still partial to Nautilus.

---

### Post by cchhrriiss121212 on 2011-04-09
Try adding XFCE to your Ubuntu install, you can have more than one DE installed on a single install without breaking anything, Once you have XFCE installed, log out and select it as the default session, it should keep whatever bluetooth service Ubuntu has, but if it doesn't check autostart in the settings manager.
You can also use Nautilus from within XFCE and whatever else you might want from the Gnome desktop, you are free to mix and match whatever features you like as long as you have the HD space for it all.

---

### Post by d3v1150m471c on 2011-04-09
```

sudo apt-get install bluez bluetooth

```You may also consider looking at synaptic by searching bluetooth. I found a few things like gnome-bluetooth and what not.

---

### Post by qkzoo on 2011-04-10
I did try before, a couple different desktops, but it seemed as if things were running in the background that were Ubuntu/Gnome specific.  For instance, when I went to the screensaver dialog, it kept telling me that gnome screensaver was running, even though I was in a Xubuntu session.

Also, when sessions are mixed, all the programs got all jumbled up.

As far as BlueZ, I remember that it was installed in my Xubuntu setup, although I can't remember if I downloaded it, or if it was there by default.

Is it fairly easy to turn specific features on and off?  In my Xubuntu setup, I had installed Nautilus somehow, but couldn't figure out how to make it the default file explorer, as Thumar or whatever it was called would pop up.

---

### Post by cchhrriiss121212 on 2011-04-10
Not sure what you mean by the programs being jumbled up, could you elaborate?
> 
Is it fairly easy to turn specific features on and off?
In settings manager, go to session and startup, and look at the autostart tab to check or uncheck what services you want. You can disable one of your screensavers for example or enable bluetooth, or add an entry for nautilus so that it shows up when you boot.
If you click "run program" from the menu, then type nautilus, you should have nautilus take over from thunar as the default file manager.

---

