---
title: "Logitech Dinovo Mini Bluetooth"
date: 2008-07-15
forum: Hardware
---

### Post by agne on 2008-07-15
Has anyone tried this with ubuntu and got it to work? I'm gonna buy a wireless keyboard in the near future and I want to be certain that it will work.

---

### Post by mpp on 2008-07-18
I too would be interested to know if anyone has this working.  I'm thinking of buying one and using it with my Gutsy desktop.

have fun()
mike

EDIT: oh right, there's another thread here: [http://ubuntuforums.org/showthread.php?t=774578&highlight=logitech+dinovo](http://ubuntuforums.org/showthread.php?t=774578&highlight=logitech+dinovo)

---

### Post by teaker1s on 2008-10-31
how do you find the size,direction pad sensitivity? looking for a small form keyboard for my htpc-but sensitivity and the clam shell flap concern me.

Would like to find one in the flesh,but local stores don't seem to stock any.

or if anyone has other solutions
thanks

---

### Post by bismark on 2008-10-31
I have one of these for my HTPC.  The small size takes a little getting use to but no worse then any Smartphone.

Personally I love it, it works much better then the MS Media Edition Keyboard and another RF keyboard with trackball that I purchased.

I have not tried it with Ubuntu however, maybe I will this weekend.

---

### Post by teaker1s on 2008-10-31
Can you tell me also can lid be removed?

Thank you

---

### Post by racmar on 2008-10-31
I have one, and have used it since 8.04 with no problems.  I've since upgraded to 8.10, also with no problems.

However, I did have to edit /etc/modprobe.d/options and add:
```
options usbhid.quirks=0x046d:0xc71f:0x00080000
```
then reboot.  

Works great.  Sometimes, I do need to pull the battery from my dinovo, when it cannot connect to the dongle.  But that problem is rare.

---

### Post by priegog on 2008-10-31
If I may:
I don't know your particular traveling typing needs, but I got myself a Think Outside foldable bluetooth keyboard. It works right out the box with intrepid and works with vanilla bluetooth (ie: no need for special adapters)
tought you might like to consider it. It's also crazy cheap.

[http://www.amazon.co.uk/Think-Outside-Bluetooth-Stowaway-Keyboard/dp/B0002OKCXE/ref=sr_1_1?ie=UTF8&s=electronics&qid=1225476382&sr=1-1](http://www.amazon.co.uk/Think-Outside-Bluetooth-Stowaway-Keyboard/dp/B0002OKCXE/ref=sr_1_1?ie=UTF8&s=electronics&qid=1225476382&sr=1-1)

---

### Post by teaker1s on 2008-10-31
tempted by the logitech due to it's touchpad and illumination,concerned about not being able to remove lid and with arthritis it's size.  

Ideally an rechargable illuminated bluetooth keyboard with touchpad-think netbook size without screen.

Thank you to the previous poster,another idea to consider.

---

### Post by priegog on 2008-10-31
Not retroilluminated but...
[http://www.amazon.co.uk/gp/product/images/B0017BQL2W/sr=1-7/qid=1225476382/ref=dp_image_0/278-8303024-4988041?ie=UTF8&n=560798&s=electronics&qid=1225476382&sr=1-7](http://www.amazon.co.uk/gp/product/images/B0017BQL2W/sr=1-7/qid=1225476382/ref=dp_image_0/278-8303024-4988041?ie=UTF8&n=560798&s=electronics&qid=1225476382&sr=1-7)

---

### Post by priegog on 2008-10-31
ooops... sorry for the double post. forum's fault, promise!

---

### Post by teaker1s on 2008-10-31
Some great idea's thank you everyone

---

### Post by teaker1s on 2008-11-01
finally we found somewhere that had a di novo mini, the chap on the counter was a like minded sole (htpc) and let me try it- I'm sold (bought it and typing now) only thing I would say is mouse is thumb tip only.
After finding the current way of enabling touchpad caused issues-Ive found another way and posted a wiki page
[https://wiki.ubuntu.com/logitech%20dinovo%20mini]("https://wiki.ubuntu.com/logitech%20dinovo%20mini")

---

### Post by jarobman on 2008-12-28
Just got one today and it worked instantly on my Intrepid HTPC (64-bit).  Typing with it right now and lovin' it!!!

---

