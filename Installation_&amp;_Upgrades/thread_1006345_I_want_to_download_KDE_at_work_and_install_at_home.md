---
title: "I want to download KDE at work and install at home"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by ghuqu on 2008-12-09
I have Ubuntu 8.10 at home and I am using a Verizon Wireless USB Connection to access the internet. Where I am located, sometimes the signal is pretty strong, other times the USB just waits and waits for a signal...So now here is my question: I want to download KDE 4.1.3 at one place with a much faster connection and then install the packages when I get home. How would I go about doing so? All I see are tarballs on the KDE.org website, but no debs. Anyone have a solution for me?  I did manage to install the KDE nightly package the other night, but it took hours to download everything I needed, plus Nightly is still in beta and I want to check out KDE at it's most stable.

---

### Post by taurus on 2008-12-09
Perhaps you could download the Kubuntu desktop/alternate CD and burn it to a CD.  Then, mount it at home on your Ubuntu and install the kubuntu-desktop from a terminal!

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by ghuqu on 2008-12-09
I definitely could give it a go. Thank you!

---

