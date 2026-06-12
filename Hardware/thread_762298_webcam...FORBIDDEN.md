---
title: "webcam...FORBIDDEN"
date: 2008-04-22
forum: Hardware
---

### Post by iwannabealinuxuser on 2008-04-22
Hey everyone,

It's clumsy ol' me again.  Anyway I was trying to video chat with a friend of mine in Ubuntu but when I did it Ubuntu doesn't kno how to use my webcam in fact I don't think its even aware that I have a webcam in my laptop.  If you can help at all that would be great. My laptop is a HP Pavilion dv2315nr,

Thanks Yall

-IWBALU

---

### Post by linuxwizard on 2008-04-22
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the Ekiga didn't work post results of the command > lsusb

---

### Post by iwannabealinuxuser on 2008-04-22
well ekiga worked but when I tryed to do a test device during set up it said it couldnt open video device, I tinkered with the settings and it worked when I hit the webcam button.  yet firefox still wont activate my webcam I go onto sites such as stickam and the webcam will not acitvate

---

### Post by Vegetarianrage on 2008-05-01
I'm having the same issue, but i'd like to point out that the cam works in several other programs besides ekiga, including amsn and skype. Any ideas on getting the webcam to work with flash websites? Stickam in particular?

---

### Post by Vegetarianrage on 2008-05-09
I figured it out. I made a new thread so it would be easier for others to find the solution.

[http://ubuntuforums.org/showthread.php?p=4920639#post4920639](http://ubuntuforums.org/showthread.php?p=4920639#post4920639)

Hope it works for you too. Good luck!

---

