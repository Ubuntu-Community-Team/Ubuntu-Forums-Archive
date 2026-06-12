---
title: "Acer Travelmate TM8371 weird X crash"
date: 2010-08-15
forum: Hardware
---

### Post by Rolf NB on 2010-08-15
Greetings and salutations.

I noticed that my Acer Netbook, running Xubuntu 10.04/32bit, has this weird tendency to crash/restart its X server when I type the string "kill 92".

X always, reproducibly crashes when I type "92" into a terminal under X.
X always, reproducibly crashes when I type "92" into the name entry box on the logon screen that comes up when I click "other" (below the face browser thingy).
X sometimes crashes when I type "kill 92" into the Google search field in a fresh firefox window. It also crashes when I type "l 92" into a fresh mousepad (gedit workalike) instance.
In fact X crashes when I just click on the empty desktop and type "ll 92", with not a single window open.
That's all using the netbook's own keyboard. If I plug in a USB keyboard OTOH, it takes a few more characters. E.g. to crash X on the logon name entry, I have to type "ill 92", but if I do that, it crashes always, reproducibly.

In all cases, the X server cycles the instant I depress the 2 key.

No crashes happens in a local text-mode tty (e.g. CTRL+ALT+F2).
No crashes happen in a ssh console controlled from a different machine.
No crashes happen in ssh'd X applications controlled from a different machine (e.g. ron@other:~$ ssh -X ron@netbook mousepad).

For kicks, I booted an older kernel that was still listed in Grub, and the same crashes kept happening.

It's so weird. Logs/dmesg | tail don't reveal anything. The one bit I've found is the very last line in /var/log/Xorg.0.log.old:```

 ddxSigGiveUp: Closing log
```But maybe I'm not looking in the right places.

Exact model number is Acer Travelmate TM8371-352G16n. It's a Core 2 Solo/GMA 4500HD machine.

Is there anything I can do to diagnose this further?

---

### Post by Rolf NB on 2010-08-16
So I went off on a hunch and killed off plymouth```
sudo chmod a-x /bin/plymouth
sudo chmod a-x /sbin/plymouthd
```One reboot later the issue is resolved.

And the occasional (maybe 10~20% of all boots) misplacement of the login box, which was what caused that hunch in the first place, seems to have vaporized as well.

Where to I sign to get plymouth out of Ubuntu?

---

