---
title: "Indicator Applet Crash"
date: 2010-07-15
forum: Hardware
---

### Post by xtremesupremacy3 on 2010-07-15
Ok, your going to have to really bare with me on vagueness here, but this is my problem.

I have an MSI CR700 laptop, details in my sig.

When I am on Pidgin, and want to change my status through Pidgin, all is fine. However, when I try to do that using the Indicator Applet, after about 3 seconds, the leds on my laptop switch, making the ones furthest to the right (Caps Lock On and another I don't know the use of) blink and the laptop has fully crashed.
Now I am guessing it has to do with a memory crash.

The thing is, now when I try and use Empathy, even when I open the app, it does the exact same. Yet this does not happen when I select for instance 'Ubuntu One' from the Indicator Applet.

Any idea what this could be, or how I would check where there may be record to being closer to the exact problem?

Arthur

---

### Post by dino99 on 2010-07-15
few solutions:

- you might have some usefull errors logged to go ahead
- into synaptic: remove/purge then reinstall the indicator applet
- look into /var/crash/ for that issue and report it (double click)

---

### Post by xtremesupremacy3 on 2010-07-15
Thank you, I will do that.

I also noticed through Google that people have experienced a crash with Empathy if VMWare is installed due to couchDB and VMWare kernel patches not working nicely together.

Seeing that I do have VMWare player, I will uninstall VMWare and test that too, will post results so that other people experiencing this may be helped.

Thanks again for the quick reply

---

### Post by dino99 on 2010-07-15
you're welcome but cant help much as i dont use vmware/pidgin/couchdb

---

### Post by xtremesupremacy3 on 2010-07-15
Well I can confirm that VMWare Player and CouchDB and it's connected services don't work well together.

After having removed VMWare Player, Empathy works perfectly, and changing status through the Indicator Applet also works perfectly.

Arthur

---

