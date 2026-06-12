---
title: "Bluetooth mouse, need to reconfigure after each boot"
date: 2008-11-21
forum: Hardware
---

### Post by anders.ostling on 2008-11-21
As subject says; I have a DELL D620 laptop with a brand new shining 8.10 installation. All hardware works fantastic directly after installation and updates, but there is one problem that prevents me from giving a ***** stars.

After reboot, the bluetooth mouse is dead. I have to go into the BT settings and remove the pairing, and then do a new pairing. After that, the mouse works fine again until next boot. It's a Logitech Travelmouse in case this is relevant.

Anyone?

---

### Post by Yezinki on 2008-11-23
Were they pairing fine in windows?

Regards,

Yezinki.

---

### Post by anders.ostling on 2008-11-23
> **Yezinki said:**
> Were they pairing fine in windows?

Regards,

Yezinki.

Yes they do, and the pairing works also after a reboot. Note that in Ubunutu, the pairing is still there, but the mouse does not work. I have to remove the pairing and pair again to re-enable the mouse.

Thanks for your interest!

Anders

---

### Post by Yezinki on 2008-11-23
anders.ostling

Wish could have helped more... the reason being I have no 8.10 any more.

I quit 8.10 as my OS & am back to windows.

Have a Dell XPS , 8.10 worked flawlessly on it....no issues with wireless, Dell BT 3.55 Module, Logitech Quick Cam Pro 9000 & Logitech Laser Comfort usb KB & mouse.

Never even had the need to pair the KB or mouse.

To me the issue seems to be the Logitech travel mouse, not having a Linux support.

You have 2 options:

Either to ask for some of our smart, genius members to compile one for you OR to contact Logitech support.

To simplify many Logitech cams wont work with 8.10, but Quick cam does.

Lastly are you using a BT usb/dongle or a module.

If you aren't using a BT module, get one from Dell & all shall be resolved.

I have said almost all options that came to my mind.

Good Luck,

Regards,

Yezinki.

---

### Post by anders.ostling on 2008-11-24
> **Yezinki said:**
> anders.ostling

Wish could have helped more... the reason being I have no 8.10 any more.

I quit 8.10 as my OS & am back to windows.

Have a Dell XPS , 8.10 worked flawlessly on it....no issues with wireless, Dell BT 3.55 Module, Logitech Quick Cam Pro 9000 & Logitech Laser Comfort usb KB & mouse.

Never even had the need to pair the KB or mouse.

To me the issue seems to be the Logitech travel mouse, not having a Linux support.

You have 2 options:

Either to ask for some of our smart, genius members to compile one for you OR to contact Logitech support.

To simplify many Logitech cams wont work with 8.10, but Quick cam does.

Lastly are you using a BT usb/dongle or a module.

If you aren't using a BT module, get one from Dell & all shall be resolved.

I have said almost all options that came to my mind.

Good Luck,

Regards,

Yezinki.

Hi
I am using a USB dongle today since the built-in module lacked support for (at least I could not make it work ...) serial port profile. Therefore I could not sync my phone over bt. It works fine with the dongle though. But I will give it a try with the built in module and Linux. Maybe that it the problem, that I have both a dongle and a built in module?

---

### Post by Yezinki on 2008-11-24
Hi Anders,

2 BT devices i.e a Module & a dongle do clash.

If your BT module is 355, I'm 100% sure you wont have any issues with 8.10, regards to mouse being dead or pairing.

Just unplug the dongle & use the module.

Good Luck.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-24
```
Maybe that it the problem, that I have both a dongle and a built in module?
```

**Correct!**

---

### Post by HyRax on 2008-12-26
> **anders.ostling said:**
> As subject says; I have a DELL D620 laptop with a brand new shining 8.10 installation. All hardware works fantastic directly after installation and updates, but there is one problem that prevents me from giving a ***** stars.

After reboot, the bluetooth mouse is dead. I have to go into the BT settings and remove the pairing, and then do a new pairing. After that, the mouse works fine again until next boot. It's a Logitech Travelmouse in case this is relevant.

Anyone?

Sounds like you have the same problem I did. I got around it by using [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6). Still not perfect, but better than having to delete and re-pair every reboot!

---

### Post by corsairgt on 2009-01-07
I've two Bluetooth mice. A Kensington PilotMouse Mini Bluetooth (model: 72414) and a Logitech V 470. They both pair/work fine with my IBM T-40 (XP Pro) and X-61s (Vista) notebook PC.

I'd pair fine in Ubuntu 8.10 (boot from a USB flash drive). However, after reboot both mice would not work unless I delete the pairing and re-pair again. I think this is a Ubuntu bug.

---

### Post by HyRax on 2009-01-07
> **corsairgt said:**
> I've two Bluetooth mice. A Kensington PilotMouse Mini Bluetooth (model: 72414) and a Logitech V 470. They both pair/work fine with my IBM T-40 (XP Pro) and X-61s (Vista) notebook PC.

I'd pair fine in Ubuntu 8.10 (boot from a USB flash drive). However, after reboot both mice would not work unless I delete the pairing and re-pair again. I think this is a Ubuntu bug.

Yes, it is a bug - the Bluetooth adapter is not told to scan for devices to periodically reconnect. It is being worked on as we speak. In the meantime, [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6) gets you around the problem until it is fixed properly.

---

