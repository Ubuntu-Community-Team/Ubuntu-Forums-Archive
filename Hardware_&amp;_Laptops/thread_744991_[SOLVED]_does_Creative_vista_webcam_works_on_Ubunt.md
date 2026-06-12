---
title: "[SOLVED] does Creative vista webcam works on Ubuntu?"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by shokoup on 2008-04-04
Hello, i was using Pclos, but i changed to Ubuntu KDE4, beta, from few days, to get all my h/w work, but i can't make my creative vista webcam works, although it is listed in the hardware, i tried with different applications listed with ubuntu, also with skype, please help me. i pasted the out of command lsusb

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 041e:405f Creative Technology, Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

---

### Post by linuxwizard on 2008-04-04
Your webcam is listed here > [http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx) 

This is the driver you need > [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)

---

### Post by shokoup on 2008-04-06
[COLOR="Blue"][SIZE="5"]Thank you for the great help, it is finally worked,   :guitar: although the pic in some applications is poor, i think with some efforts from me to adjust camera settings everything will be good but  finally it is working.
 I wish to ask some questions, how i could check the driver version in order to use the latest one later when launched, does every program has its own adjusting effects on the camera or there is a master adjustment for the Camera ( hue, brightness,...) because the pic is black in skype, but acceptable in the other linux webcam applications.[/SIZE][/COLOR]

---

### Post by linuxwizard on 2008-04-06
You're Welcome That is good to hear that you got your webcam working. Ekiga & Camorama their are setting you can adjust within the app. Cheese no settings. I don't use Skype can't help you their. But looking here > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > I see your cam listed under > List of Non-Working Webcams > look at the notes.

---

