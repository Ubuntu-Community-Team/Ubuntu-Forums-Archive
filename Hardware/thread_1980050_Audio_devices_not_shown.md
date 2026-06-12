---
title: "Audio devices not shown"
date: 2012-05-14
forum: Hardware
---

### Post by palimmo on 2012-05-14
Hello!
Often it happens that, as you can see in one of the two images, I can't see my audio devices.
The list is blank! 
And sometimes are correctly reported.
In both cases the audio works.

Have you any similar experience?
thanks!

---

### Post by roelforg on 2012-05-14
I assume you're using an external device?
I, for one, always need to run
```

pulseaudio -k
pulseaudio --start

```
before it registers my Hercules DJ Console RMX as sound card.

---

### Post by palimmo on 2012-05-14
> **roelforg said:**
> I assume you're using an external device?
I, for one, always need to run
```

pulseaudio -k
pulseaudio --start

```
before it registers my Hercules DJ Console RMX as sound card.
Mh.. I don't use any external device.

---

### Post by roelforg on 2012-05-14
> **palimmo said:**
> Mh.. I don't use any external device.

Could've been.
Laptops tend to have crappy audio, so loads of people buy pci-express/usb/firewire/etc audio cards that they use instead.
And some models don't register until after pulse loaded (for some reason, pulse doesn't detect cards on the fly and needs a reboot to see a new one).
Though mine isn't technically a sound card, it has a 4.0 surround card in it that gives the most crystal clear sound i've ever heard (from a pc, that is, still very good sound! No cracks, pops or static). But hdj_mod makes it appear as a standard 4.0 card to any app (pulse included) so the steps are the same.

---

