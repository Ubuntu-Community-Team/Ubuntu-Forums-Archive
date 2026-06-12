---
title: "Laptop Brightness - Nvidia?"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by Bahbuu on 2006-11-04
I just installed Ubuntu 6.06

My laptop - Sony VAIO VGN SZ-18GP
and currently using Geforce 7400 (i think, or something similar)

The brightness is at max. and i can't reduce it (it's really killing my eyes)

I tried going to System > Preferences > Power Management 
but it doesn't reduce it even if I lower the settings

If I use the function keys on my laptop to reduce brightness, Ubuntu freezes and I'll have to press the 'power' button for a few seconds to force it to shutdown

How can I resolve this problem?

Thanks

---

### Post by Lorian on 2006-11-04
I have the opposite problem on my monitor, it is too dark. As I have an NVIDIA card I can use nvidia-settings to bump up the brightness and contrast to the right level. But while it saves the settings, it only applies them once you go into nvidia-settings again. Ie. when you turn yourn computer on, you need to run nvidia-settings and it will instantly apply your previously selected settings, you can then quit it.

---

### Post by coffeecat on 2006-11-04
Sony uses software drivers, rather than hardware, to control the function keys and of course the drivers that come with Vaios are Windows ones.

I managed to get the Fn keys, including the brightness ones, working on my VGN-FS215B Vaio with [this howto]("https://www.granny.homelinux.org/%7Elinho/files/delta.ubuntu"). It's for Breezy, but works OK in Dapper. Haven't tried it in Edgy yet. There are alternative howtos [here]("http://users.skynet.be/thomasvst/linux-on-laptop/") and [here]("http://www.linux-laptop.net/hosted/ubuntu_sonyvaiovgnfs315b.html"). Again, they were written for Breezy, but should work.

Before you run the installation scripts, make sure you have the build-essential package installed. If you've never compiled source code before and you run into problems, there should be plenty of people who can help you here.

**Edit:** - two points. The nvidia card is nothing to do with the problem - it's the lack of software drivers in your Linux installation that is the issue. Unlike you, before I got the Fn keys working, if I tried them the system didn't freeze - there was just no response.

---

### Post by smackenzie on 2007-03-24
Thanks for this post - I'm having exactly the same issue so I'll try it.  I'm running Dapper on a Sony VGN-SZ220P.  I'll post my results..

---

