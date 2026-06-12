---
title: "[ThinkPad T440s] Problem with touchpad after change for touchpad for T450s"
date: 2018-04-19
forum: Hardware
---

### Post by fuxo on 2018-04-19
Hi guys,

i have NB Lenovo Thinkpad T440s. Is it great device, but has really bad touchpad (no hw buttons). 
This touchpad can be replaced for touchpad for Thinkpad t450s (with 3 hw buttons).

It is "standard operation" and on the internet you can find lot of manuals and videos how replace it for touchpad for Thinkpad T450s.

**Okay, and problem**: After this replacement, new touchpad doing really "crazy" movemens and random clicks.

For illustration i attach videos with original and replaced touchpad.

Original touchpad: [https://www.dropbox.com/s/wi0lh9l7gp6d344/2018-04-18%2021.17.01.mp4?dl=0](https://www.dropbox.com/s/wi0lh9l7gp6d344/2018-04-18%2021.17.01.mp4?dl=0)
Touchpad for T450s: [https://www.dropbox.com/s/s1hzlc7f8bcbw7a/2018-04-18%2021.32.04.mp4?dl=0](https://www.dropbox.com/s/s1hzlc7f8bcbw7a/2018-04-18%2021.32.04.mp4?dl=0)

This problem is in my primary system and same behavior was beed after reboot to LiveCD.

Primary OS: **Xubuntu 17.10**
Live for test: **Xubuntu 18.04**

Have you idea, whether is HW or driver problem?
Thanks for any answers.

Lukas

---

### Post by tinylagarto on 2018-04-19
Did you try to change something from the Xfce mouse settings?

Then you tried it live and on a development release. The question would be how well it would perform on 17.10?

---

### Post by fuxo on 2018-04-19
Hi ivanovnegro2,

no, i use only defaut settings (original touchpad works good with default settings (and on LiveCD too)).

Have you idea which settings can i try to change? 
On which version of Ubuntu can try new touchpad, in your opinion?

Thank you.
[IMG]https://ubuntuforums.org/moz-extension://b46a38a9-39a0-4dff-94e9-35acb034895d/icons/icon.png[/IMG]

---

### Post by cruzer001 on 2018-04-19
There are two packages (drivers) for touchpads.  Which one are you using?

```
apt policy *synaptics libinput*
```

How is your touchpad listed?

```
xinput list
```

Both have settings that can be tweaked for your touchpad.  Depending on which one your running; Google can provide you with a ton of suggestions (as it did for my Dell).

Also got some hits here:

[https://www.google.com/search?client=ubuntu&channel=fs&q=touchpad+Thinkpad+T450+linux+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=touchpad+Thinkpad+T450+linux+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by fuxo on 2018-04-19
Hi guys,

today aj saw absolutly unbelievable thing:

After 3. replacement of original and new touchpad i tried start notebook and touchpad unexpectable works... Without changes drivers, without any settings... I tried only start notebook and always works fine.
I absolute don't know where was a problem - maybe wrong contact on cables, maybe permanently pushed button (both very, very unlikely) but now, always works great.

Thank you for your time.

Lukas.

---

### Post by alex-slab on 2018-07-23
Hi Fuxo,

I'm getting the same issue - jumpy cursor, random clicks - after replacing my trackpad. I actually bought a second new trackpad and cable but still the behaviour is the same. I just wondered whether you had any more insights about what was wrong with yours, and why it started working?

---

