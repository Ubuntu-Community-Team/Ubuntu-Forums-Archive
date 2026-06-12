---
title: "Middle Mouse Button on Touchpads"
date: 2012-10-01
forum: Hardware
---

### Post by karat on 2012-10-01
I recently got a Lenovo P580.  The touchpad's mouse buttons are internal.  The whole pad clicks, but where you are touching when it clicks does matter.

At least, under windows it does.  Under Ubuntu, I don't have a right mouse button.  Everything is a left mouse click.  This is tragic for someone who is used to having a 3-button mouse.

Actually, is there any concrete way of testing this?

---

### Post by karat on 2012-10-01
[http://www.howtogeek.com/118817/how-to-swap-the-two-and-three-finger-touchpad-tap-actions-on-ubuntu/](http://www.howtogeek.com/118817/how-to-swap-the-two-and-three-finger-touchpad-tap-actions-on-ubuntu/)

Actually, two finger worked for right click, but three finger was turned off by default.  This told me how to turn it back on.

---

### Post by karat on 2012-10-02
> **karat said:**
> [http://www.howtogeek.com/118817/how-to-swap-the-two-and-three-finger-touchpad-tap-actions-on-ubuntu/](http://www.howtogeek.com/118817/how-to-swap-the-two-and-three-finger-touchpad-tap-actions-on-ubuntu/)

Actually, two finger worked for right click, but three finger was turned off by default.  This told me how to turn it back on.

Actually, it's advice didn't work.  I found 3 ways of solving this, but none of them worked.  Eventually, it screwed up my login.

What's the recommended way of doing this?  Is it safe to add Option "TapButton2" "2" in 30-synaptic.conf?  Last time I tried, my login was screwed up even after I fixed it.

---

### Post by karat on 2012-10-02
> **karat said:**
> Actually, it's advice didn't work.  I found 3 ways of solving this, but none of them worked.  Eventually, it screwed up my login.

What's the recommended way of doing this?  Is it safe to add Option "TapButton2" "2" in 30-synaptic.conf?  Last time I tried, my login was screwed up even after I fixed it.

Er, I meant 50-synaptics.conf.  Anyway, how can I tell if a .conf file is going to be used?  If I copy the file, make changes, and leave it in that directory, will it be read?

---

### Post by karat on 2012-10-02
Further details:

* The synclient commands work for just that session, but pointing the gnome daemon at a script didn't do anything upon reboot.
* Making my own version of the 50-synaptics.conf file didn't work.

I suspect something is overriding both of these.

---

### Post by karat on 2012-10-02
[http://askubuntu.com/questions/26290/50-synaptics-conf-options-not-working](http://askubuntu.com/questions/26290/50-synaptics-conf-options-not-working)

The above link suggests that the gnome daemon is overwriting any other touchpad settings I make upon startup.  It looks like my options are either to disable the gnome daemon's management of the touchpad or wait for this issue to be fixed -- it might be a bug?

Any other suggestions?

---

