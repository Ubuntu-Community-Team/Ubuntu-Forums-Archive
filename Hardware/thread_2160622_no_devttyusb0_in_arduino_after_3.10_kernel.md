---
title: "no /dev/ttyusb0 in arduino after 3.10 kernel"
date: 2013-07-07
forum: Hardware
---

### Post by ankit2313 on 2013-07-07
I'm using Ubuntu 13.04 Gnome edition. I have a problem with my Arduino Duemilanove Board. Previously I was using kernel 3.9.2-030902-generic. After I installed kernel 3.10rc6 and I start my arduino IDE I didn't see a serial port /dev/ttyusb0 as before for uploading my code onto the board, Now there is only one /dev/ttyS0. I tried plugging my board in all the usb port but none of them helped in uploading via /dev/ttyS0. I don't know it's actually because of kernel 3.10 but previously everything was working fine. This is the link to [lsusb]("http://paste.ubuntu.com/5853225/") and [dmesg]("http://http://paste.ubuntu.com/5853229/") command output after plugging the board.


The dmesg does show some error in the last lines I tried google out the error but didn't find solution.

---

### Post by DJ_Max on 2013-07-07
Are you uploading via the Adruino IDE? Did you change the serial port in the settings?

---

### Post by m-bachmann on 2013-08-18
For some reason it sometimes switches to [COLOR=#333333][FONT=Georgia]/dev/ttyACM0[/FONT][/COLOR]

See here for details: [http://labby.co.uk/2012/02/setting-up-processing-under-ubuntu-devttyacm0-devttyusb0-fix/](http://labby.co.uk/2012/02/setting-up-processing-under-ubuntu-devttyacm0-devttyusb0-fix/)

Hope this helps (it did in my case).

---

