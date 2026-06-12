---
title: "Installing Realtek sound drivers for my Laptop"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by Cyber Akuma on 2008-04-12
I have a Toshiba Satellite A215-S7413 Laptop, according to Vista, my sound hardware is listed simply as "realtek high definition audio",  I don't know what specific chipset it uses.

I was able to find the drivers here:
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I tried running the ./install file but I saw a bunch of permission denied errors

So I rebooted and tried sudo ./install

However, this seemed to fail too, it looked like it was going well, but it ended stating about needing a curses library.

Anybody know whats wrong or how to get this working in Ubuntu 7.10? I'm pretty new to Linux.

---

### Post by Cyber Akuma on 2008-04-16
Hello? Anyone?

I was given some advice about the curses library and tried to find and install them through the Synaptic Resource Package Manager.

Anyway, after this, it looked like the drivers installed ok, they claimed the install finished and near the eng I was given a window with some configuration options to set, but after all this, I still have no sound options.

I tried rebooting but the volume meter still has a no symbol on it and clicking it gives me an error.

---

### Post by Yellow Pasque on 2008-04-16
Try this:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

