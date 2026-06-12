---
title: "Problems with USB"
date: 2016-02-28
forum: Hardware
---

### Post by at35z on 2016-02-28
Hi there,

I had a bootable USB stick on which I previously had a 14.04.3 LTS installation disc. I made it with the pre-installed bootable installer creator. Now I wanted to erase all data on it to install a new version on it to boot from, however, I got this message:

[img]http://i.imgur.com/8nW6Jog.png[/img]

After this, I can't seem to use my pendrive or erase it with the program. It recognizes it as an USB device, however, there is a red circle next to it with an exclamation mark, and when I try to erase it, the message above pop up.

What can I do?

---

### Post by sudodus on 2016-02-28
I suggest that you wipe or re-format your USB stick with one of the options in mkusb's wipe menu. Install mkusb from its PPA. If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.) 

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

See this link for more details: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by at35z on 2016-02-28
> **sudodus said:**
> I suggest that you wipe or re-format your USB stick with one of the options in mkusb's wipe menu. Install mkusb from its PPA. If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.) 

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

See this link for more details: [mkusb/wipe]("https://help.ubuntu.com/community/mkusb/wipe")

Thank you so much, it worked!

---

### Post by sudodus on 2016-02-28
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

