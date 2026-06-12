---
title: "How to set up a 4-pin jack in ubuntu 14.04"
date: 2014-07-18
forum: Hardware
---

### Post by %cV4BU£r8Ofp&amp;# on 2014-07-18
I have a laptop with a **4-pin** input (mic+left+right) but actually just the audio works, the **mic input doesn't work**. This laptop also has integrated speakers and a integrated mic (both work). I wanted to use the 4-pin input so i was wondering if there's any way of make it work (actually just left and right work but mic doesn't).

[B]OS: Ubuntu 14.04 LTS
Soundcard: Realtek (don't know the model)
Laptop: Acer Aspire V5-571G[/B]

If you need more info just ask.

---

### Post by tgalati4 on 2014-07-18
That 4th ring is probably microphone power, 3 or 5 volts.  Get a dynamic microphone that needs power supplied to it--that should wake it up.

---

### Post by %cV4BU£r8Ofp&amp;# on 2014-07-20
Well, in Windows the mic worked well so i think it's a software issue...

---

### Post by Ranko Kohime on 2014-07-20
It's worth asking: Have you checked to see if the microphone is being automatically muted?  Open pavucontrol (and install it, if you don't have it installed already), and check the input tab.  If you don't see a change in the port drop-down when you plug in the headset, then check the configuration tab, you may need to select a different profile for your sound card to enable the microphone.

```
sudo apt-get install pavucontrol
```

---

### Post by %cV4BU£r8Ofp&amp;# on 2014-07-22
> **Ranko Kohime said:**
> It's worth asking: Have you checked to see if the microphone is being automatically muted?  Open pavucontrol (and install it, if you don't have it installed already), and check the input tab.  If you don't see a change in the port drop-down when you plug in the headset, then check the configuration tab, you may need to select a different profile for your sound card to enable the microphone.

```
sudo apt-get install pavucontrol
```

Checked but it still don't work. In the input tab nothing changes when i plug the headset (in the output tab it does). Changing configuration tab didn't solve my problem.
In my input tab there are 2 possible ports: Mic and analog entry. Both use the **internal** mic (the one i dont want to use) plus it doesn't detect my headset when i plug in it.

---

