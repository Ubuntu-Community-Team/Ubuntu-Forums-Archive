---
title: "HOWTO: setup a Logitech MX500 with evdev in Hardy Heron"
date: 2008-05-20
forum: Hardware &amp; Laptops
---

### Post by CloudBolt on 2008-05-20
As many of you may have noticed, old MX500 configurations stopped working in Hardy sometimes. Now I have heard talk about the mouse working with basic configuration, but, at least for me, the side buttons didn't work.

Also, the first thing I tried to do, when I first switched from Gentoo to Ubuntu, was to get my mouse working using the same configuration I used in Gentoo. But in all versions up to and including Gutsy Gibbon that didn't work. After having run out of possibilities(trying to get my mouse working in Hardy), I decided to give the old config which I used in Gentoo another try (The Gentoo Wiki page can be found [here]("http://www.gentoo-wiki.com/HOWTO_Advanced_Mouse#Option_3:_Configure_by_Autodetection"))

And what do you know, it worked. The basic principle is that you don't configure evdev, you let evdev do what it was meant to do: autodetect the settings.

```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "evdev"
        Option      "evBits"        "+1-2"
        Option      "keyBits"       "~272-287"
        Option      "relBits"       "~0-2 ~6 ~8"
        Option      "Pass"          "3"
EndSection

```

By the way, since this is an autodetect feature, it might work for other mice. Try it out!
I've got all buttons, including cruise control and back/forward working here.

---

### Post by 5h4rk on 2008-06-01
That worked for me. Thanks! But it's not working with Nautilus.

---

### Post by yipperzz on 2008-06-03
Thanks.  Got my MX500 to work with firefox.

---

