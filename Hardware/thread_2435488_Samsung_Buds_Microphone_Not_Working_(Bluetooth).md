---
title: "Samsung Buds Microphone Not Working (Bluetooth)"
date: 2020-01-21
forum: Hardware
---

### Post by skatedawe2 on 2020-01-21
Hi!

Has anyone got their Samsung Buds (Bluetooth) headphones working in Ubuntu, with the microphone?
The sound and bluetooth is pairing and working, i can lissen to music, but i don't get it connected as Microphone in.
I understand that you have to change the bluetooth profile from A2DPsink to HSP, correct?

Can someone maybe share some light and give some recommendation what to do? 
Can we solve this together?

**My Setup**
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan

```

Samsung Galaxy Buds

Blueman Bluetooth Manager Version 2.0.8

---

### Post by CelticWarrior on 2020-01-22
> **skatedawe2 said:**
> I understand that you have to change the bluetooth profile from A2DPsink to HSP, correct?

Correct.

You can change the profile in sound settings.

---

### Post by skatedawe2 on 2020-01-22
> **CelticWarrior said:**
> Correct.

You can change the profile in sound settings.

I'm running;
pulseaudio 13.0

You can see below that it's unavailable, which draws me to that its not yet supported. But why?

[IMG]https://i.imgur.com/xxLOcPt.png[/IMG]

Can someone confirm that they have got it to work?

---

### Post by CelticWarrior on 2020-01-22
That doesn't mean it isn't supported. That means the Samsung buds weren't correctly identified.

---

