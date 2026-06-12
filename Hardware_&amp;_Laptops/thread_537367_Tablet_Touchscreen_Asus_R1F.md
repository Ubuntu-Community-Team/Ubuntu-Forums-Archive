---
title: "Tablet Touchscreen Asus R1F"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by Falcon.Geek on 2007-08-28
Hello,  I while ago I purchased an Asus R1F tablet pc...up until recently I have just used XP and Vista on it...But do to the fact that I now have to use Red Hat at work, i wanted to have linux on my laptop as well.  I was pleasently surprised at how much works out of the box...( i didn't believe my eyes when it said it connected to my wireless network.) 

However the one thint that doesn't work, is the tablet touch screen.  I installed the wacom tools and all and I have wacom things in my xorg.conf but still no movement or anything when I touch the screen...I can't seem to figure out what input my screen is at.  /dev/input/event3 is the only thing that wacdump will show...and none of the numbers change when I touch the screen.  any advice would be great

---

### Post by UofLSpeed on 2007-09-20
Recently, I was looking at purchasing that same model of tablet.  Unfortunataly, it seems that the model you're talking about does not use a serial connection to the touch screen; it's USB.  This interface is not currently supported by the current linux wacom drivers.

It looks like an awesome tablet, but I don't think you'll be able to get support for your pen in linux at this time.

---

### Post by Falcon.Geek on 2007-09-20
Thanks for your help anyway...But If you are comparing them still, i strongly recommend it.  I use vista on it now, and take it to class.  I and truly believe it is the best choiceIive made.  Truly indispensable tool.

---

### Post by kshepherd on 2008-01-12
Unfortunately the same lack of touchscreen support is true for the Asus R1E.
Progress on Linux support for this Wacom chip can be followed here:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127)

Let us hope that it is supported soon.

---

### Post by artisart on 2008-03-11
ksheperd are you giving people falso hope? yes. I got an email from wacom team. They told me the drivers for penables tablet pcs that have usb interface will be ready in June. You get all discouraged and then declare it bye bye. Just wait till june K?

---

