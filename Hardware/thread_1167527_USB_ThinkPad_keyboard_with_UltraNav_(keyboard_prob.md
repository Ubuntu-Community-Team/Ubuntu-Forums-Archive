---
title: "USB ThinkPad keyboard with UltraNav (keyboard problems)"
date: 2009-05-23
forum: Hardware
---

### Post by vace117 on 2009-05-23
Hello. I am looking for some help with getting the IBM/Lenovo ThinkPad external USB keyboard (with UltraNav - a combined trackpoint and touchpad) to work on Ibex.

The keyboard mostly worked out of the box, but there are a few extremely annoying problems, that I don't have enough knowledge to troubleshoot. 

I already described the issues I have with the TouchPad on that keyboard here: [http://ubuntuforums.org/showpost.php?p=7330425&postcount=10](http://ubuntuforums.org/showpost.php?p=7330425&postcount=10)

In this thread I would like to discuss the issues with the keyboard itself.

When I start or switch an X server (I have 2 running), log in to GNOME or just plug in the keyboard when already logged in, the keyboard enters 1 of 3 random states:

1) NumLk mode. In this mode some letter keys produce numbers and the leftmost LED indicator is ON. Rarely, I can get out of this mode by pressing *Shift-NumLk*, but most of the time that does nothing.

2) Some keys generate completely wrong scan codes. For example, the *Down* arrow generates the code for *Return*. According to *xev*:
```
KeyPress event, serial 33, synthetic NO, window 0x2e00001,
    root 0x156, subw 0x0, time 154200413, (181,137), root:(1049,613),
    state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
"   XmbLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

```

3) Normal operation mode.

I can't figure out a way to get the keyboard into mode #3 reliably, although so far I've always been able to get it to work by taking advantage of the randomness of the situation, i.e. unplugging and plugging the keyboard until it ends up in mode #3. Sometimes this takes over 20 attempts, although once it gets into mode #3, it stays there.

Furthermore, the keyboard wreaks havoc on GNOME's keyboard layout switcher. It becomes impossible to switch to any layout other than USA. Sometimes I can recover from this state by pressing a button on my normal PS/2 keyboard, which I still have hooked up. Then I can type in Russian, but only on the PS/2 keyboard. As soon as I press any button on the USB keyboard, the layout snaps back to USA.

Please note that if I log in to a minimalistic window manager, like IceWM, I can easily setup and switch layouts with *setxkbmap*, so this is definitely some GNOME weirdness. Also, logging in to IceWM does not cause a re-initialization of the keyboard, whereas logging in to GNOME does. You can see the details I got from Xorg.0.log in this post: [http://ubuntuforums.org/showpost.php?p=7330425&postcount=10](http://ubuntuforums.org/showpost.php?p=7330425&postcount=10) . What part of GNOME would need to re-initialize all of the hardware on the USB keyboard?

I should also add that in a text console, the keyboard always works properly (in mode #3). 

I have no idea how to start troubleshooting these issues (random init being the higher priority), so any ideas would be greatly appreciated.


Thanks,


Val

---

### Post by frig.neutron on 2009-05-29
is this the keyboard?

[http://www-307.ibm.com/pc/support/site.wss/MIGR-45868.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-45868.html)

---

### Post by vace117 on 2009-05-29
> is this the keyboard?

No, it's actually this one:
[IMG]http://vace.homelinux.com/wiki/uploads/6/64/31p9490_thinkpad_travel_keyboard.jpg[/IMG]
[http://www-307.ibm.com/pc/support/site.wss/MIGR-45849.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-45849.html)

---

