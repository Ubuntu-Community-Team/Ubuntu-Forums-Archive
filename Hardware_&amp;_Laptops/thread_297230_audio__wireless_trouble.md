---
title: "audio / wireless trouble"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by mistknight on 2006-11-10
Hello everyone!

I've installed kubuntu edgy on my laptop (HP pavillion dv5000) but I'm having trouble with the audio driver. On the official HP support driver downloads located at :

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3259284&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3259284&lang=en")

There are two drivers :

1. Microsoft Universal Audio Architecture (UAA) Bus Driver for High Definition Audio

2. Conexant High Definition Audio Drive (requires 1)

Now I've turned the internet upside down, but what's strange is that it seems no one's complaining about this! What's wrong? Where can I find drivers for this? Can anyone help me?

One other strange issue is that when I boot from live, kubuntu identifies my wireless, and sees the wireless networks, but fails to connect (weather it's due to a wrong driver or just some bug I don't know), windows connected with no trouble.

Even after installation, the driver was there, saw networks, but didn't connect. I don't know what happened really when the driver just disappeared all of a sudden! 

How can I run auto-detection again? Or is there some way to restore it? I've already downloaded a driver from intel, but I was hoping I could test it with the original detection before trying intel's. This is the wireless on my laptop (Intel PRO/Wireless 3945ABG).

I would be so grateful if someone can help! I'm pretty newbie but I'm loving kubuntu more everyday! Especially with that breath-taking beryl ;)

---

### Post by ReaderRat on 2006-11-10
**[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by teaker1s on 2006-11-10
if it's the same as my dv6116eu that has a broadcom 4311 chip in it. the main issue is that the kernel has a driver but the chip also requires firmware to function. I would advise you look at this [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy")
 the other issue is some wifi managers don't play nice eg wifi radar the firmware loads, but it connects with no ip address I'm useing network manager applet as gnome network tools don't seem to work correctly either

---

### Post by mistknight on 2006-11-11
Thanks! The sound tutorial worked flawlessly. It turns out the volume was down, way down! I really appreciate this :) 

But back to the wireless, Windows connected to the wireless networks with no problems. The wireless ethernet and wireless networks are detected when I boot from live (although connecting to them fails), same situation after I installed kubuntu edgy (with the same problem, failed to connect), and it seems there's something I did that made it disappear. Now it's not listed in the available ethernet devices at all! I don't know weather it was the correct wireless definition or not since it didn't connect. But I can't do any more testing with it gone!

Is there a away to get it back on my kubuntu? And is there some special router configuration that's required for the "Wireless LAN manager" to successfully connect to the wireless network :-k I've got full access to the wireless routers.

Thanks again for all your help :)

---

### Post by mistknight on 2006-11-11
Anyone? :confused:

---

### Post by strabes on 2006-11-11
Try this:

```

sudo ifconfig eth1 up
sudo apt-get install kwifimanager
sudo dhclient eth1

```

I don't have kubuntu but I would assume that you run it with 'kwifimanager' but I'm not sure on that one.

You could also try installing wifi-radar.

---

### Post by mistknight on 2006-11-13
The utility looks pretty useful. But the problem is there's no wireless device detected in the system in the first place. I installed kwifimanager but it simply gave errors that no "wireless" interface exists :confused: 

I'm really not sure, but it would seem there's something blocking the HW detection, a configuration file maybe? Can anyone help me with this! :( Is there a way to force a new HW detection? Or remove any traces of the old wireless configs so kubuntu can re-detect the wireless??? ](*,)

---

