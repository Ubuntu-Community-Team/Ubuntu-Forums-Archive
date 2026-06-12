---
title: "what is with my mouse?"
date: 2010-02-08
forum: Hardware
---

### Post by preit on 2010-02-08
Ok, here is the latest issue i am running into.  My mouse (either touch-pad or usb connected mouse) does not right-click.  Whenever I open an internet browser or any application, the right click just stops working.  I have the same ubuntu on two laptops, and this is only an issue with the presario v5000.  for example, i can't even use right-click now, which makes browsing the internet a pain in the rear.  please someone help me in fixing this issue.  Also, keep in mind that I am a n00b with this linux OS so i need baby-steps.  thank you in advance

---

### Post by pi/roman on 2010-02-08
I've seen similar things before and have not seen a solution but maybe try this.
Open up a terminal and type:
```
xinput --list
```Find the id of the device you want to test then get to a point where the device is working properly and in a terminal type:
```
xinput --watch-props id#
```where id# is the number of the device.  Then open up your browser and try to screw it up and see if any changes show up when it happens.  To stop displaying properties press ctrl/z.

---

