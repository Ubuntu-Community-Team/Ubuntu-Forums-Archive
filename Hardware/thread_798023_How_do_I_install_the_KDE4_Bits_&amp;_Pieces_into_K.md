---
title: "How do I install the KDE4 Bits &amp; Pieces into Kubuntu 8.04?"
date: 2008-05-17
forum: Hardware
---

### Post by OzzyFrank on 2008-05-17
I originally thought the Kubuntu CDs for Hardy had both the stable KDE 3.5.x and the somewhat experimental KDE4.x desktops on the one disc. Well, that's how I read the announcement, but turns out that there are 2 Kubuntu CDs, and that the one for download everywhere is the standard one with 3.5.x, and that the KDE4 one you have to go looking for and only installs that version of KDE.

I actually just added KDE to my Ubuntu with the standard **sudo apt-get install kubuntu-desktop**, which gave me the stable version, not the cutting-edge KDE4 one. So the question is how do I change this so that it runs KDE4? Is it as simple as picking the main KDE4 packages in Synaptic/Adept and letting it uninstall previous versions? Or will this result in a weird (and unstable?) mix of the 2 KDE versions?

---

### Post by teaker1s on 2008-05-17
it's in repositories if you have wired/wireless internet

```
sudo apt-get install kde4
```

---

