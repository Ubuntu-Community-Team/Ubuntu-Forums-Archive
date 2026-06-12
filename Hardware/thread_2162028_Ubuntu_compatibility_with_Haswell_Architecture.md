---
title: "Ubuntu compatibility with Haswell Architecture?"
date: 2013-07-12
forum: Hardware
---

### Post by nurfed on 2013-07-12
Hello Community!

I am researching if ubuntu server (13.40) will run on intels new Haswell Architecture and if the integrated GPUs are supported. A few Threads found said there are problems on some reviews it is stated that it works with some flickering.

I am quite a bit confused, since i thought every pc would need some kind of gpu (integrated graphics or external graphic card) to boot. If it doesn't how would I install an operating system, when I cant (at least I think so) connect a monitor to it?

Thanks

---

### Post by grahammechanical on 2013-07-12
Other people have a better knowlege of questions like these.

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

[http://www.phoronix.com/scan.php?page=article&item=fedora19_ubuntu_haswell&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora19_ubuntu_haswell&num=1)

The issue of video drivers does not apply with a server OS because administration is done using the command line. Yes, you will need to plug in a monitor, keyboard and mouse, or you can make a remote connection to the server using another computer with those things. The server OS does not come with a desktop environment.

Regards.

---

### Post by nurfed on 2013-07-13
> **grahammechanical said:**
> 

The issue of video drivers does not apply with a server OS because administration is done using the command line. Yes, you will need to plug in a monitor, keyboard and mouse, or you can make a remote connection to the server using another computer with those things. The server OS does not come with a desktop environment.



Thanks for the link to Phoronix that really helped, for some reason I only found the article they wrote about the [COLOR=#000000][FONT=verdana] i7-4770K.

But for the Quote above: You missunderstood me. I know that server-OS (most of the time) only come as a CLI that you connect via ssh and so on. But what happens if there is no GPU present? Whether integrated nor as a graphics card? I know that the server I am building doesnt really need graphics support. When there is no form of GPU present can I connect a monitor to it, and it would work, to install an OS?

Thanks[/FONT][/COLOR]

---

