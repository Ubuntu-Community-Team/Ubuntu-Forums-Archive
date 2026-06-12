---
title: "Special MCE buttons on RF remote"
date: 2010-11-18
forum: Hardware
---

### Post by dumb07 on 2010-11-18
Hi,
I just bought an RF based remote control, to use with my MythTV. It's this one here: [http://www.focus.com.tw/products-con.php?p_id=74&id=36](http://www.focus.com.tw/products-con.php?p_id=74&id=36)

It's registered as:
HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input12

HOLTEK Wireless 2.4GHz Trackball Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input13

And most of the buttons work just fine, but the special MCE buttons doesn't generate any input, I've tried both xev and showkey, even a cat /dev/input/event12 and event13, but no response at all.

Is there any chance on getting these buttons to work or is it a driver issue. I was thinking on downloading the source for the usb hid core and setting in it debug mode, to see if anything is logged when pressing the buttons, but would that just be a waste of time?

Hope for any help.

/Thomas

---

