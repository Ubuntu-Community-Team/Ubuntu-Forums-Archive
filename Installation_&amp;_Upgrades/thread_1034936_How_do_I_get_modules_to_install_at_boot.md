---
title: "How do I get modules to install at boot ?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by bernard.carpenter on 2009-01-09
Hi,

I'm new to Ubuntu and hope someone can help me out.

Just installed Ubuntu 8.10 desktop version. I have a AverMedia AVerTV Hybrid + FM PCI (saa7134 chip) installed and used [this tutorial]("http://translate.google.com.au/translate?u=http%3A%2F%2Fzonabuologica.wordpress.com%2F2007%2F12%2F04%2Fconfigurar-avermedia-avertv-hybrid-fm-pci-chip-saa7134%2F&sl=es&tl=en&hl=en&ie=UTF-8") - translated from Spanish no less - to make it work. It works perfectly, except "the settings" are forgotten after I reboot.

The essential commands were :
[I]
sudo rmmod saa7134_alsa saa7134-dvb saa7134

sudo modprobe saa7134 card=99
sudo modprobe saa7134_alsa
sudo modprobe saa7134-dvb[/I]

Now, my problem is, after re-boot, the modprobe stuff is all forgotten and the card is no longer recognised by ubuntu.

The tutorial says to do this :

*sudo gedit / etc / modules*

and add these lines

[I]saa7134 card=99
saa7134_alsa
saa7134-dvb[/I]

... but it doesnt work ... I edited the /etc/modules file and added the lines, yet when I reboot the card is "gone" and I have to do the modprobe stuff to see get ubuntu to see the card. I guess there is a log file somewhere telling me what's happening, but I have no clue as to where to start looking.

So ... how do I make the modprobe changes "stick" ??

Any help for a linux newbie is greatly appreciated.

---

### Post by Tim Sharitt on 2009-01-09
Try adding the line
```
options saa7134 card=99
```
to /etc/modprobe.d/options or any file in the /etc/modprobe.d directory.

Then run
```
update-modules
```

---

### Post by bernard.carpenter on 2009-01-09
Hey!

Thanks for that. The update-modules command is (apparently) "depreciated and shouldnt be used", but the addition to the /etc/modprobe.d/options file worked perfectly after a reboot.

Awesome! Watching TV right now while I write this (pity there's nothing on as usual)

---

