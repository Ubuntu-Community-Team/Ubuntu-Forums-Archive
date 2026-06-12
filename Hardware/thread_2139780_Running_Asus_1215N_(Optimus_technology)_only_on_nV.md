---
title: "Running Asus 1215N (Optimus technology) only on nVidia card"
date: 2013-04-27
forum: Hardware
---

### Post by Forseti on 2013-04-27
Hello,

I have an Asus EEE 1215N that has its battery and touchpad failing so I'd like to turn it into stationary home PC computer.
But there is one obstacle that heeps me from this: HDMI not working. This model of netbook has nVidia ION Optimus technology that switches between Intel and nVidia card to conserve battery power. Intel card is default and HDMI is attached to nVidia.

But since it would be permanently on AC power I'd like to permanently run it on nVidia and use external screen connected through HDMI.
I've got Bumblebee to work recently but it is cumbersome to invoke optirun every time and HDMI isn't working anyway. 

Does anyone know how to do it?

---

### Post by Forseti on 2013-04-28
Well, by chance I stumbled upon solution that works (after some tweaking).
It is based on work of [COLOR=#333333][FONT=sans-serif]Luis Da Costa posted on Arch Linux site: [/FONT][/COLOR][https://bbs.archlinux.org/viewtopic.php?id=133293](https://bbs.archlinux.org/viewtopic.php?id=133293)

I chose "Trick 2" but while it worked it had a two flaws: it used low-res (640*480 I think) and there was no keyboard working at all.
So I switched [FONT=courier new]Option "UseEDID"[/FONT] to [FONT=courier new]"true"[/FONT] - and it turned resolution autodetection and gave me Full HD.
Then, after much trying, I switched [FONT=courier new]Option "AutoAddDevices"[/FONT] to [FONT=courier new]"true"[/FONT] - and I had my keyboard back.

So, there is only one stupid thing that boggles me: when I close the lid, the external monitor goes black and I have no idea how to disable it. Tools from control center doesn't affect that. 
Any ideas?

---

### Post by davidbaumann on 2013-04-29
Hello,

what does dmesg / /var/log/syslog say when cloging the lid?

David.

---

