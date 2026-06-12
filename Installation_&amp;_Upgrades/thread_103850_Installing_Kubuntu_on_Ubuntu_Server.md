---
title: "Installing Kubuntu on Ubuntu Server"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Chiaro on 2005-12-14
I've been thinking, and I wanted to install Kubuntu recently. But, the only CD I have is the ubuntu install CD. So I thought I would make a clean install, install Ubuntu Server, and then type in

```
sudo apt-get install kubuntu-desktop
```

Would this work? Or would I have to type in

```
sudo apt-get install kde
```

and then install everything else normally?

Thanks,

Chiaro

---

### Post by az on 2005-12-14
[QUOTE=Chiaro]I've been thinking, and I wanted to install Kubuntu recently. But, the only CD I have is the ubuntu install CD. So I thought I would make a clean install, install Ubuntu Server, and then type in

```
sudo apt-get install kubuntu-desktop
```
[/QUOTE]

Yes.


The same goes for edubuntu-desktop.

xubuntu-desktop does not seem to depend on the Xserver, though, but that is not your question.
(For xubuntu, do
sudo apt-get install x-window-system-core xubuntu-desktop)

---

