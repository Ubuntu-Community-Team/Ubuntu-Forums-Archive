---
title: "Lenovo T410 Wireless problems"
date: 2010-10-27
forum: Hardware
---

### Post by dark fader on 2010-10-27
OK, I have a couple of years experience maintaining Linux servers so I'm not a complete beginner. I know my way around a Linux install, but I wouldn't call myself an expert Linux user.

When working on a Rails project I decided that Windows was too slow, so I put WUBI on my work lap-top to test it out. In general Ubuntu works quite nicely and I'm spending all my dev time there now. There was a problem with hibernate freezing the machine before I shut it off, but that's small fry.

The big problem is the network adapter. Occasionally it'll just stop working and refuse to connect to anything - including a wire connection. This is often after a reboot or wake from sleep. I need to reset in these cases.

More consistently, it can't see hidden networks. This is irritating as my work network is hidden. It just sits there attempting to connect forever, repeatedly asking for the same (correct) password. I can connect fine on the Windows partition.

Sometimes it'll take exception to a network it's previously been fine with and display the same behaviour.

If I try to change networks it tells me I've just disconnected from a network which it was connected to a long time previously - even if it's not been in range for hours.

Are there any things I can do to update the drivers or troubleshoot the problems? It's a fly in an otherwise very enticing ointment.

I'm on 10.04 - I'm waiting until a deadline has passed before attempting a version upgrade.

Any help or ideas would be much appreciated.

---

### Post by KaiO on 2010-10-27
You might try to replace (the default) networkmanager with Wicd.
It is in the repositories and is IMO far superior to networkmanager when it comes to wireless.

Earlier versions would automaticcally remove networkmanager but you might have to check that you're not running two network managers at the same time.

---

### Post by dark fader on 2010-10-28
Thanks for the reply. Although it seems like a much nicer program all round, it is incapable of connecting to my home (unhidden) network. It tries authentication several times before telling me I have a bad password.

I'm going to try it at work - if it can connect to the hidden network here I would at least have a solution to the problem -albeit an incredibly wonky one.

---

