---
title: "I messed up - display is too big."
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by atk_nut on 2009-03-15
It's all my fault, hopefully somebody out there can help!

I was trying to adjust the display resolution on my dell inspiron 6000 and messed it up.  I beleive essentially what I did is made the total display size twice as big as the monitor and set the monitor to display the lower half only.

Everything now boots up fine, but the menu bar is totally off the screen.  (way up where I can't see it.)

If I boot up in recovery, and run:

dpkg-reconfigure xserver-xorg

will that give me a chance to fix it?

If not, how can I fix it?

Thanks.

---

### Post by mhgsys on 2009-03-15
Well , you could try:

You could also make a backup so you know what the original xorg.conf was. 

```

sudo nano /etc/X11/xorg.conf

```

and save it like xorgbackup.conf or something.


also: 
Maybe take a look at this
[http://ubuntuforums.org/showthread.php?p=6897892#post6897892](http://ubuntuforums.org/showthread.php?p=6897892#post6897892)

---

### Post by atk_nut on 2009-03-15
Ok,  I got the display back.  Thanks.

I used ctrl-f2 and ran gnome-display-settings.

The next thing.  (what I was originally trying to do.) is to get the display settings to 1280x800.

Can you help with that?  I've found quite a few threads on it, but I can't seem to get it going.

Thanks.

---

### Post by mhgsys on 2009-03-16
You can open a terminal and edit xorg.conf typ:
```

sudo nano /etc/X11/xorg.conf

```

scroll to 

SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "1280x1024"
        EndSubSection

and adjust your Modes.

save your xorg.conf file and restart X.

```

sudo /etc/init.d/gdm restart

```

If it doesn't work you could edit xorg.conf again in console to adjust it, or you could just 

```


sudo dpkg-reconfigure xserver-xorg

```
again.

Btw,Could you post the info from lspci, I want to know which video card your using.

open a terminal
```

lspci | grep VGA

```

---

### Post by atk_nut on 2009-03-16
Thanks everyone. It's solved!

---

### Post by mhgsys on 2009-03-16
how did you solve it?

Did you solve it with the commands I gave you or did you solve it in another way.
I find it's always interesting to learn new way's.

---

