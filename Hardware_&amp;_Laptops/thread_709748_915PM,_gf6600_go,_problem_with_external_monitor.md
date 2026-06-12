---
title: "915PM, gf6600 go, problem with external monitor"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by epcp on 2008-02-27
I've installed the newest ubuntu on my laptop, and its running fine when I'm only using the laptop monitor.
As soon as I plug in my external screen it takes forever booting, and when it starts up, everyting is laggy.

I have a Quanta KN1 915PM notebook barebone 15,4W/915PM/GF6600. And the monitor is a 20" BenQ, FP202W.

I really like linux, but because of this problem I'm mainly running XP.. so if anyone know what I can do to fix this I would really appreciate it :)

---

### Post by epcp on 2008-02-28
It appears that my computer slows down as soon as I plug in the PCI-cable for my external monitor. It doesnt matter if I do it before I boot, during boot, or when I have ubuntu up and running.

It also goes back to normal as soon as I pull the plug.

I've tried installing the newest nvidia drivers, and disabeling 915resolution(because of an error during boot saying my chipset was not supported). Neither of them worked. :mad:

---

### Post by Yellow Pasque on 2008-02-28
Well, let's have a look at your /etc/X11/xorg.conf and /var/log/Xorg.0.log files

BTW, 915resolution is a workaround for Intel GPU's on widescreen resolutions

---

### Post by epcp on 2008-02-28
Thank you for replying, I've attached the files in an archive.
I couldn't have the monitor connected the whole time, because it lags so much it's impossible to do anything. So I had it connected a couple of minutes during booting, and then a couple of minutes later when everything was up and running.

---

### Post by epcp on 2008-02-29
bump :-\"

---

