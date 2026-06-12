---
title: "Multiple external monitors using mini DisplayPort: is it possible?"
date: 2015-01-12
forum: Hardware
---

### Post by krespim on 2015-01-12
I have a Dell XPS13 (9333) with a fresh Ubuntu 14.04 install, and a single mini-Display output. I am still waiting for an hdmi converter to connect it to an external monitor, but that should work without a problem. The question, what to do, if at all possible, to have 2 external monitors connected? And what hardware would I need? In [here]("http://askubuntu.com/a/552094/93813") someone did it through a dockstation, but I believe this is specific for those laptop models. I wonder if there is a (cheap) hub out there.

 The monitors are both Dell U2412M, with hdmi and vga connections.

---

### Post by lukeiamyourfather on 2015-01-12
This is sort of possible. There are adapters that create one large virtual display out of multiple smaller physical displays and they use only one input. Below are some example products (probably many others out there).

[http://www.matrox.com/graphics/en/products/legacy/gxm/dh2go/displayport/](http://www.matrox.com/graphics/en/products/legacy/gxm/dh2go/displayport/)
[http://www.startech.com/AV/Displayport-Converters/Mini-DisplayPort-Triple-Head-DisplayPort-Multi-Monitor-MST-Hub~MSTMDP123DP](http://www.startech.com/AV/Displayport-Converters/Mini-DisplayPort-Triple-Head-DisplayPort-Multi-Monitor-MST-Hub~MSTMDP123DP)

As far as Ubuntu is concerned it would show up as one really big display. So maximizing something on that display would span across both physical displays which would be a bit wonky.

---

### Post by krespim on 2015-01-12
Cheers. The 2nd hub you listed is selling at about 100 euros, which is low enough for me to take a punt - though proabably only in 2 months time. 

As for the maximizing, not great but most of the time I don't do it, so it should be fine.

---

### Post by krespim on 2015-01-13
Just to add the list of compatible hubs, a review for the ZOTAC [Mini-DisplayPort to Dual HDMI Adapter Full H]("http://www.amazon.de/dp/B005FSHHHG/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=M31T7Q92LDRJ&coliid=IU8PD9A2ZW8R0") seems to indicate that it is also possible to connect mini-DP to 2 monitors via HDMI. At least from what I understood with my passable german. If someone proficient in German cares to confirm this it would be appreciated. It should be noted that as pointed out, the 2 monitors will act like an oversized one.

---

### Post by krespim on 2015-01-13
Just to add the list of compatible hubs, a review for the ZOTAC [Mini-DisplayPort to Dual HDMI Adapter Full H]("http://www.amazon.de/dp/B005FSHHHG/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=M31T7Q92LDRJ&coliid=IU8PD9A2ZW8R0") seems to indicate that it is also possible to connect mini-DP to 2 monitors via HDMI. At least from what I understood with my passable german. If someone proficient in German cares to confirm this it would be appreciated. It should be noted that as pointed out, the 2 monitors will act like an oversized one.

---

### Post by krespim on 2015-04-28
Quick update. An [answer]("http://askubuntu.com/a/552094/93813") in askubuntu suggests that updating the kernel solves the problems - kind of - but that did now work for me.
Check my new [question]("http://askubuntu.com/questions/615171/laptop-monitor-plus-two-external-monitors-via-dockstation?lq=1").

---

