---
title: "Ubuntu 13.10 on Samsung Series 5"
date: 2014-01-04
forum: Hardware
---

### Post by valerio.siviero on 2014-01-04
Hello everyone!
My name is Valerio, I just subscribed to the forum :)

I recently installed Ubuntu, coming back to Linux after a period of Mac.
I've got a new Samsung Series 5, NP540U4E, with Windows 8.1 pre-installed and I overwrote it (without UEFI) with Ubuntu 13.10.

After a little bit of tuning I have most of the features working properly.
However, there are some things missing, for which I ask you some help:

1) **Keyboard backlights auto-adjustment and FN control**.

I tried many tutorials out there, but in every of them I get stuck in some of the procedures. The only thing that is working is the command:
echo 0 > /sys/class/leds/samsung\:\:kbd_backlight/brightness 
... that allows me to set it by terminal.
But I would like to do it by FN keys, and also set the way they get on and off randomly (for example when I get back from suspend).

2) **CPU fan mode**.

It looks the FN key works, allowing me to switch from "silent", to "normal", to "overclock". But I can't see any difference in the system when I change between them.
How can I make sure the settings changed?

3) **Wi-Fi FN key LED**.

The FN key works, but when I switch the Wi-Fi off, the LED stil stays on.
How can I make it to turn off when I switch the Wi-Fi off?

---

Even an answer for one of the three matters is appreciated.
I thank you in advance so much for the help and wish you a nice day :)

Thanks,
Valerio.

---

### Post by glitsj16 on 2014-01-04
Hi Valerio,

Most if not all of your questions can be solved by adding the 'Linux On My Samsung' PPA:
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

Have a look around on [http://www.voria.org/forum/](http://www.voria.org/forum/) for instructions on how to use the PPA and how to set things up.

Welcome to the community and goodluck :)

---

### Post by valerio.siviero on 2014-01-04
Dear glitsj,
thanks for the answer :)

I already installed and updated it on my system some week ago.
But it still not works (I am interested especially in the keyboard backlights control).
I searched in the forum but I see nothing helpful :/

Can you redirect me to some useful source of information?

Thanks again,
Valerio.

---

### Post by richardbrucebaxter on 2014-02-03
Note I am having the same problems with the Samsung Series 5 backlight.

There is a lot of advice out there (not all of which is very simple/contained), and much of which appears to work only in specific cases. In my case the backlight keyboard shortcuts work in the Ubuntu WM but not in icewm. I havn't found a command line solution either (which is all I really require).

Cheers -

Richard

---

