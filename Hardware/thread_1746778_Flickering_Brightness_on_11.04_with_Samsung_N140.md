---
title: "Flickering Brightness on 11.04 with Samsung N140"
date: 2011-05-02
forum: Hardware
---

### Post by angus_young on 2011-05-02
Can anyone help,

I seem to have an issue with brightness levels on my samsung n140

The machine works fine for a long period (always connected to the PSU)

but after a while, the Brightness starts to flicker from Full brightness to down one level and back.

The Notification box appears at the top right of the screen showing the level dropping and rising, can get the machine to do anything, can get out of this, only way out is to power down the netbook

Any Ideas?

Cheers

---

### Post by spigolo on 2011-05-02
> **angus_young said:**
> Can anyone help,

I seem to have an issue with brightness levels on my samsung n140

The machine works fine for a long period (always connected to the PSU)

but after a while, the Brightness starts to flicker from Full brightness to down one level and back.

The Notification box appears at the top right of the screen showing the level dropping and rising, can get the machine to do anything, can get out of this, only way out is to power down the netbook

Any Ideas?

Cheers

hi, i'd suggest you take a look in the [voria forums]("http://www.voria.org/forum/index.php"), there are a couple of workarounds partially working (ie: usable netbook).

i've been led to think it's some issue with gnome-power-manager, but i cant prove it and i'd love to know somebody else's opinion.

---

### Post by telarius on 2011-05-10
> **spigolo said:**
> hi, i'd suggest you take a look in the [voria forums]("http://www.voria.org/forum/index.php"), there are a couple of workarounds partially working (ie: usable netbook).

i've been led to think it's some issue with gnome-power-manager, but i cant prove it and i'd love to know somebody else's opinion.


i agree it seems to come from power management like a problem in handling turning off the screen light or dimming it.
i have a stop trick that lets me go on with my work by pressing Fn + Volume Up or Down
im running an n130 and my biggest regret with ubuntu was trusting it to upgrade to the 11.04, just as buggy as xp was.

---

### Post by jayjohnson on 2011-05-18
I would just like to confirm that this is happening to me on a Samsung N130 ever since I upgraded to version 4.11. I am able to get back to work by holding [fn] and jamming the 4 arrow keys (brightness / volume controls) for a few seconds.

Additionally, if I hold [fn] and press both brightness keys simultaneously, the problem occurs instantly.

Thank you.

---

### Post by Barnickal on 2011-05-25
I have a Samsung N130 and am having the same issue. Also, when plugging into a monitor (37" Samsung TV), since the upgrade it sometimes has black over sections of the screen and I have to press the 'fn+f4' several times before it fixes. ANyone else finding that?

---

### Post by Leoazul on 2011-05-30
I'm having exactly the same problem using a Samsung N210. I've been using Alt+Tab to turn it off when it begins. I saw another issue that can be related, when we turn off the light with Fn+F5 we can turn it on again immediately. But if we wait a little bit with the light turned off it's impossible to turn it on again. I have to restart to fix each time it happens. I'm really disappointed with 11.04.

---

### Post by Barnickal on 2011-09-25
> **Barnickal said:**
> I have a Samsung N130 and am having the same issue. Also, when plugging into a monitor (37" Samsung TV), since the upgrade it sometimes has black over sections of the screen and I have to press the 'fn+f4' several times before it fixes. ANyone else finding that?

Yeah I've had that issue. It's really annoying. Coincidentally, I too am pluggin it into a Samsung TV.

---

### Post by Barnickal on 2011-09-25
oops, duplicated the post, how do I delete this?

---

### Post by kwaanens on 2011-10-16
Having the same problem with a Samsung x125 after upgrade to Oneiric. The problem is especially visible when I unplug the power, when brightness should be reduced.
I mever had this behaviour with Natty, I might add.

---

### Post by Wolftrait on 2011-10-23
This has also been occurring to my Samsung R540 with 11.10 Interestingly enough, the flickering hadn't been happening till after I updated to 11.10 from 11.04.  It only occurs when unplugged, and is left running on battery power.

---

### Post by leftcase on 2011-10-23
This has happened to me with a Samsung NC10. Fresh install of Oneiric, didn't have the problem with Natty before.

---

### Post by leftcase on 2011-10-23
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/810093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/810093) - It looks like this relates to the samsung_laptop kernel module. There is a fix in the pipeline for it though so hopefully it should be soon :-/

For the time being, you can disable the dim screen on idle setting which stops the immediate flickering. Disabling the samsung_laptop module achieves the same ends but then you probably won't be able to use brightness up and down keys. Like me, you'll probably also find that the brightness up down only gives you three settings. Off, very dim, super bright!

Don't forget to hit the 'this bug effects you' link on the bug report.

---

### Post by grant.pirie on 2011-11-02
Hi, I had this problem with my son's Samsung N130 when I installed ubuntu 11.04. I couldn't find a fix at the time but have since installed 11.10 and then used Fortunato Ventre's repositories at [http://www.voria.org/forum/viewtopic.php?f=3&t=296](http://www.voria.org/forum/viewtopic.php?f=3&t=296) and used synaptic to install the samsung-wireless, samsung-backlight and samsung-tools packages, rebooted and the problem went.  So I would recommend upgrading to 11.10 and trying again.

Lots of people have had this same problem and Voria finally managed to pin it down I think, with some help.

Lots of luck

---

### Post by kwaanens on 2011-11-02
The Voria repository fixed this for me as well :)

---

