---
title: "How to restore default Keyboard Shortcuts"
date: 2009-03-01
forum: Hardware
---

### Post by IGM0937 on 2009-03-01
Hi, im new to this forum and new to Ubuntu. I have a bit of a problem.

I haven't seen a topic on this, but im using a laptop at the moment and i accidentally changed some of the keyboard shortcuts that for some reason i cant change back because the system cant recognize those buttons in the first place. Im using a Dell Studio 15 Laptop and Ubuntu wont recognize the "eject" button on my Media Touch pad controls

Is there a way of reseting the settings to the original state, because the setting that it had before might have worked with the button. If not, is there a way that i can help to recognize the media buttons.

A BIT OF A HIT...  it recognizes some of my Media buttons by the name "XF86", so my play button would be "XF86AudioPlay"... if this helps at all.

---

### Post by IGM0937 on 2009-03-02
Anyone? :(

---

### Post by K. Hendrik on 2009-03-02
Hi,
could you please explain how you changed the shortcut because there are a lot of ways. (.xbindkeys, fdi-file, gconf...)

---

### Post by IGM0937 on 2009-03-03
i changed them using the built in application you should find in the Ubuntu distribution. Its under System, Preferences and its Keyboard Shortcuts

---

### Post by K. Hendrik on 2009-03-03
ok now i understand your problem, ok it got nothing todo with the hotkeykey assignment if the eject key can't be recognized now it couldn't before.

The key only has a raw value right now not a keycode you need to assign one, the procedure is described [here]("https://help.ubuntu.com/community/MultimediaKeys").

If you need help with that start a terminal, push the unrecognized key a few times and execute:
```

dmesg

```
and Post the last 10-20 lines of the result here.

Edit:
I would need the relust of ```
dumpkeys
``` too.

---

### Post by IGM0937 on 2009-03-09
here you go... if probably done it wrong, but gave it a shoot anyway.. i personally can see anything from the results
```

[   87.008498] CPU0 attaching NULL sched-domain.
[   87.008516] CPU1 attaching NULL sched-domain.
[   87.040125] CPU0 attaching sched-domain:
[   87.040135]  domain 0: span 0-1 level MC
[   87.040140]   groups: 0 1
[   87.040148]   domain 1: span 0-1 level CPU
[   87.040152]    groups: 0-1
[   87.040157]    domain 2: span 0-1 level NODE
[   87.040162]     groups: 0-1
[   87.040170] CPU1 attaching sched-domain:
[   87.040174]  domain 0: span 0-1 level MC
[   87.040178]   groups: 1 0
[   87.040184]   domain 1: span 0-1 level CPU
[   87.040189]    groups: 0-1
[   87.040194]    domain 2: span 0-1 level NODE
[   87.040199]     groups: 0-1
[  117.034796] NET: Registered protocol family 10
[  117.035768] lo: Disabled Privacy Extensions
[  117.036309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  127.560055] eth1: no IPv6 routers present
[ 1166.937304] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1213.856092] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1219.537106] CE: hpet increasing min_delta_ns to 33750 nsec
```

and when i executed "dumpkeys" i got a massive list of assigned keys, but it only showed a portion because the list is so massive that when i scroll to the top i cant see the beginning of the list.. its very limited.

Sorry but im a full on Ubuntu Noob... if there is anything wrong please tell me.

---

### Post by WhatAbout on 2010-07-08
I have the same problem in keyboard shortcuts.

My laptop is thinkpad and the native volume buttons dont respond to the volume control in ubuntu. And i just cant find the key codes maped to them. 

Fun part is that when I press mute on the laptop it lowers the volume to a minimum, but dosent mute. I guess that as the buttons are directly maped to hardware, (amplifier), the button dont shut it down fully. Only a guess. :)

---

