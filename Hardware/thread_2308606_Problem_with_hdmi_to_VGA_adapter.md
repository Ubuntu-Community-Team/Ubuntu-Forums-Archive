---
title: "Problem with hdmi to VGA adapter"
date: 2016-01-04
forum: Hardware
---

### Post by levi4 on 2016-01-04
So I'm having the weirdest problem with using a hdmi to vga video converter on ubuntu, specifically one of these [http://www.ebay.com/itm/1080P-HDMI-Male-to-VGA-Female-Video-Converter-Adapter-Cable-For-PC-DVD-HDTV-TV-/221909515908?hash=item33aad67e84:g:iekAAOSw14xWPWWM](http://www.ebay.com/itm/1080P-HDMI-Male-to-VGA-Female-Video-Converter-Adapter-Cable-For-PC-DVD-HDTV-TV-/221909515908?hash=item33aad67e84:g:iekAAOSw14xWPWWM)

If I plug a hdmi monitor into the port it works fine, so the hdmi port on the computer works.
If I plug the monitor into the dvi port via an adapter it works fine, so the monitor works with the computer.
If I plug the monitor with the hdmi adapter into the hdmi port on my windows 8.1 laptop it works fine, so the whole setup seems to work.

Yet when I plug the monitor with the adapter into the ubuntu computer (xps420) it does not

Edit: Thinking it might be a linux issue I just tested the adapter with a raspberry PI and it worked flawlessly, really at a loss for what to think here

---

### Post by Redalien0304 on 2016-01-13
Try to modify the /boot/config.txt file. Uncomment (remove #) & change the hdmi_group=2, hdmi_mode=9. for output 800x600 60mhz.
that is changes i had to make for pi hdmi to vga adapter

---

