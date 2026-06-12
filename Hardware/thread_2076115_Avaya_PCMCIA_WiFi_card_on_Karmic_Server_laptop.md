---
title: "Avaya PCMCIA WiFi card on Karmic Server laptop"
date: 2012-10-25
forum: Hardware
---

### Post by frankvw on 2012-10-25
I have an old laptop which I use as a server. It has a PCMCIA slot in which I have plugged an old Avaya PCMCIA WiFi card. (The reason being that I'm out in the sticks and my only Internet feed is wireless, which is being delivered to my humble abode via WiFi.)

In /var/log/messages I see the card being inserted into and rejected from slot 0:

```
kernel: pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
kernel: pcmcia_socket pcmcia_socket0: pccard: PCMCIA card ejected from slot 0

```
The 'lspcmcia' command however does not see the card:

```
Socket 0 Bridge:  [yenta_cardbus]  (bus id: 0000:01:03.0)
```

But of course that would have been too easy. :-) I obviously need drivers, client software and other magic to make this work. However, Karmic being a bit long in the tooth (not to mention the PCMCIA card being an antique from the late 1990's) I have not been able to find anything.

Could anyone point me into the right direction? What do I need to get this fossil to work?

Tnx!

// FvW

---

