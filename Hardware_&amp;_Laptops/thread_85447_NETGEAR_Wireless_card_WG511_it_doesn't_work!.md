---
title: "NETGEAR Wireless card WG511: it doesn't work!"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by taniwha on 2005-11-02
Hi there,
Any good to make this network card work in Ubuntu?
It appears among the network devices but after that, there is nothing I can do to make it work.

Thanks,
taniwha

---

### Post by GeeJay on 2005-11-11
I could not get this wireless card to work with Mandriva but it works fine with Ubuntu 5.10.

I am a newbie but here are a few suggestions:

1. My card is based on the prism chips.
2. Make sure it is plugged into the PCMCIA slot when you install Ubuntu.
3. Check your network devices - there is a command for this or use the GUI tool in Gnome
4. My network card was eth0 and wireless card eth1
5. Make sure in the network applet you have set the card to be enabled and maybe default internet.
6. Make sure you have correct encryption set on card that wireless point expects, password etc. I typed in the generated WEP hex password.
7. Run the iwconfig command which should tell you if there is anything wrong with your card config.

I have had nearly perfect serbvice from my card since installing Ubuntu.

---

