---
title: "Volume up/down and Mute laptop Fn keys under Xgl (Kubuntu Feisty)"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by tanguyr on 2007-04-30
Hello,

After a fresh installation of Kubuntu Feisty on an Asus W2P, the special laptop "Fn" keys to increase/decrease volume (Fn-F11/Fn-F12) and toggle mute on/off (Fn-F10) are recognized out of the box + when i press them i get a nice screen box saying "Mute on"/"Mute off", or "Volume" with a percentage bar that slides back and forth as i press the buttons. In short: brilliant!

Since a working install is somehow counter to the laws of nature (my nature at least), i then installed Xgl, and now i notice that when i am in an Xgl session, these keys no longer work - neither the effect nor the visible cue. Still works just fine when i am in a regular kde session though. What's strange is that the other Fn keys (like brightness, lcd on/off, etc) all work fine in both Xgl and kde-kwin.

This isn't really a problem for me, it's more that i'm curious about how this stuff is supposed to work, and why it wouldn't under Xgl. I already noticed that these three keys in question just happen to be the ones listed in my /usr/share/hotkeys-setup/asus.hk file, but since i don't know how that stuff works, i'm kinda stuck at "hmmm... interesting". If i do a 

```
tail -f /var/log/acpid
``` 

and pound away on those keys, i see slightly different messages under Xgl or KDE-Kwin:

under KDE-Kwin (works)
```
[Tue May  1 02:37:18 2007] received event "hotkey ATKD 00000031 00000025"
[Tue May  1 02:37:18 2007] notifying client 5110[107:114]
[Tue May  1 02:37:18 2007] notifying client 5738[0:0]
[Tue May  1 02:37:18 2007] client has disconnected
[Tue May  1 02:37:18 2007] notifying client 5738[0:0]
[Tue May  1 02:37:18 2007] executing action "/etc/acpi/voldownbtn.sh"
[Tue May  1 02:37:18 2007] BEGIN HANDLER MESSAGES
[Tue May  1 02:37:18 2007] END HANDLER MESSAGES
[Tue May  1 02:37:18 2007] action exited with status 0
[Tue May  1 02:37:18 2007] completed event "hotkey ATKD 00000031 00000025"
```

under Xgl (busted):
```
[Tue May  1 02:18:55 2007] received event "hotkey ATKD 00000031 00000024"
[Tue May  1 02:18:55 2007] notifying client 5110[107:114]
[Tue May  1 02:18:55 2007] notifying client 5738[0:0]
[Tue May  1 02:18:55 2007] executing action "/etc/acpi/voldownbtn.sh"
[Tue May  1 02:18:55 2007] BEGIN HANDLER MESSAGES
[Tue May  1 02:18:55 2007] END HANDLER MESSAGES
[Tue May  1 02:18:55 2007] action exited with status 0
[Tue May  1 02:18:55 2007] completed event "hotkey ATKD 00000031 00000024"
```

If anybody out there has any info or links they would be much appreciated...

thanks in advance,
/t

---

### Post by tanguyr on 2007-05-07
six day bump.

---

### Post by tanguyr on 2007-05-15
bump again...

c'mon people - somebody must have some idea...

---

### Post by nirpius on 2008-01-01
Did you ever find out how this is done? I've got a similair problem where the visual popups still work but they won't actually affect the volume. Nor will changing anything in Kmix. JUst wondered if you'd come up with any leads...

---

