---
title: "Toshiba Tecra M4 built-in Bluetooth device is not detected"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by anasofiapaixao on 2006-06-27
Okay, now this has definately puzzled me. I tried everything, installed everything there was to install, and Ubuntu just doesn't detect my laptop's buit-in bluetooth device.

I was trying to receive files from a friend's Sharp GX25. After some research I thought the problem was with compatibility between Linux and the phone. But she had the genial ideia of connecting her USB bluetooth dongle to my laptop. What was my surprise when I saw it doing the party all by itself; that dongle is a  true headache on her Windows desktop but as soon as I connected it Kbluetoothd detected it, and receiving files was just as easy as clicking an "accept" button.

I ran hcitool dev and checked the device manager: when the blutooth dongle is not connected, it doesn't detect any bluetooth devices. So the problem IS with my lovely Tecra M4... I remeber having to run I-Don't-Know-What Toshiba applet before device manager actually detected the existence of my bluetooth sleeping beauty in Windows. But now I am totally lost on this one.

**In a nutshell**: how can I make Ubuntu detect my built-in bluetooth device?

P.S. - I tried Toshiba's site to look for OEM drivers, naïvely as Toshiba is *like this* with Microsoft... those jerks don't have Linux drivers available for download at all.

EDIT: Gnome Bluetooth file sharing works as well.

---

### Post by didobuntu on 2006-06-27
I have exactly the same problem with a built in bluetooth moue device in my Asus W2Jc laptop ... it cannot be detected

---

### Post by anasofiapaixao on 2006-06-28
... And the same thing with the IrDA port, but one thing at a time... EWW SCREW YOU TOSHIBA. Lol.

(Kidding. I love Toshiba)

---

### Post by didobuntu on 2006-06-28
look at the bluez web site ... I saw that the built-in bluetooth mouse for TOSHIBA laptops can be updated ... there is a Howto there

---

### Post by williamgjames on 2006-06-28
You may have to turn the bluetooth device on.  It may be off by default on boot.  Have you tried Fn-F8 keyboard combination to turn wireless off then on.  This works on a Toshiba Quosmio.  On my machine it turns on and off both wireless-G and Bluetooth.  There is also a utility to do the same, I believe it is called toshset and it can be installed via synaptic.  I can't remember the exact syntax but it is something like toshset bluetooth on. Hope this helps.

---

### Post by anasofiapaixao on 2006-06-29
[QUOTE=williamgjames]You may have to turn the bluetooth device on.  It may be off by default on boot.  Have you tried Fn-F8 keyboard combination to turn wireless off then on.  This works on a Toshiba Quosmio.  On my machine it turns on and off both wireless-G and Bluetooth.  There is also a utility to do the same, I believe it is called toshset and it can be installed via synaptic.  I can't remember the exact syntax but it is something like toshset bluetooth on. Hope this helps.[/QUOTE]

You just made my day. Thanks :) toshset was already installed! All I had to do was:

```
sudo toshset -bluetooth on
```

And run Gnome bluetooth or kbluetoothd before receiving. Thanks!

---

### Post by bradlis7 on 2008-03-01
> **anasofiapaixao said:**
> You just made my day. Thanks :) toshset was already installed! All I had to do was:

```
sudo toshset -bluetooth on
```

And run Gnome bluetooth or kbluetoothd before receiving. Thanks!

Ok, I tried to run that command, and it just said "Bluetooth unavailable". Did you do anything before running that command?

Do you have information on getting this laptop to a working state on your blog? It was protected so I couldn't get to it.

---

