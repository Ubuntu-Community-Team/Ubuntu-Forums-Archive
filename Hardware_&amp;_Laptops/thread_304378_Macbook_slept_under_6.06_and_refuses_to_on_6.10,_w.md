---
title: "Macbook slept under 6.06 and refuses to on 6.10, why?"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by blinksilver on 2006-11-21
I am not asking for a fix (although that would be perfect : ) ) just a reason why? it just has me really confused. Any takers?

by the way, they are both completely stock installed with all the security updates installed.

---

### Post by jsilve1 on 2006-11-21
Hi. Funny, that.  I was NOT able to get my black macbook to sleep using Ubuntu 6.06 but I AM able to get it to sleep in 6.10.

Things I have found funny (and note that this is using 6.10):

* Sleep works almost perfectly.

* sleep works, but won't wake up, when I have the macbook-backlight-hal package installed.  Uninstall that package and presto! Sleep works again. The package I mean is the one referred to on this page: [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

* Sleep works when I have the Beryl manager running, but only when Metacity is the window manager! Sleep does not work when Beryl is the running window manager!

* Running Beryl and switching back and forth to Metacity will bork things, such as sleep, if I switch too much.

My "safe" configuration right now is basically a stock 6.10 installation, LILO boot loader, and I only gingerly add new packages as needed and uninstall if things like sleep die on me.

6.10 in general has been much better out-of-the box on the blackbook, as sound now works, the function keys for volume, mute, and eject work, and, like i said, sleep works.  The things I do not have working are the trackpad in synaptic driver mode and the iSight.

Now, does anyone know how I can get the function keys for brightness to work? Even mapping them to some user space command would be fine, but I can't seem to figure out how to map the keycodes, which I think are 101 and 212.  Note that I do not mean "F1" and "F2" but rather the dual hardware functions that those keys possess.

later...

---

### Post by est on 2006-11-23
To get FN+F1/FN+F2 working I used xbindkeys with the following lines in my .xbindkeysrc:

```
#dim screen
"/usr/bin/macbook-backlight -10"
    m:0x0 + c:101
    NoSymbol 

#brighten screen
"/usr/bin/macbook-backlight +10"
    m:0x0 + c:212
    NoSymbol
```

This works for me while FN is off by default, and when GNOME loads xbindkeys automatically, which for some reason it doesn't always. (even though it's there in session settings).

---

