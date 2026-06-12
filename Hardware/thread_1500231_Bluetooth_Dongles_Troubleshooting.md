---
title: "Bluetooth Dongles Troubleshooting"
date: 2010-06-02
forum: Hardware
---

### Post by markackerman8@gmail.com on 2010-06-02
Hello and thanks for viewing this post.

I have got my Brother (new to Ubuntu) to buy a bluetooth headset to ease our communications!!  Now I thought it would pair easily as he already has 2 bluetooth USB dongles:
1/ windows bluetooth keyboard/mouse 7000
2/ and another bluetooth keyboard/mouse unit.

ODDLY!!!
- they both work fine, BUT, there is no bluetooth icon showing in the notification area!!! and yes they are both Bluetooth and are working
- when I open up System/Preferences/Bluetooth, it says no bluetooth devices connected, which simply isn't true.
- now how can I setup a new device when the program says there is no hardware present?  Too weird

Any troubleshooting tips?  and My bluetooth on my computer works perfectly well with a logitech Dongle for my keyboard/mouse and acts as a general purpose bluetooth Dongle.  Why wont either of his? or will they?

Thanks :confused:

---

### Post by efflandt on 2010-06-03
Are you trying to use a keyboard/mouse dongle for the Bluetooth headset.  That may not work, because the dongle is usually for HID devices only (keyboard and mouse).

While my diNovo Edge keyboard/mousepad will work with any Bluetooth, the dongle that came with it is strictly for keyboard or mouse only.  And it actually did not work in 10.04 LTS at first because it "did" bring up in the Bluetooth applet, and I had to change something in /lib/udev/rules.d/70-hid2hci.rules to make it work (and not bring up the Bluetooth applet).

So he may need a regular Bluetooth dongle to use the headset.  Not sure which ones work easily.  I have an older Motorola dongle with Broadcom chipset that was automatically recognized by Linux.

---

### Post by markackerman8@gmail.com on 2010-06-03
Yes indeed, I am trying to use an HID (assumming that means keyboard/mouse) dongle to work with a headphone/mic earpiece (for my brother).

At least on my different Ubuntu system my Logitech keyboard/mouse dongle brings up the bluetooth icon in which I at least have the option to look for other things.  

Was I just lucky? and are his 2 so specifically designed for their hardware that they don't prompt the "Bluetooth Icon"?

Arghhhh, any ideas of a usb bluetooth dongle that is cheap and functional?

---

