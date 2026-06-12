---
title: "Fatal1ity gaming headset problem"
date: 2008-10-20
forum: Hardware
---

### Post by Peter_G on 2008-10-20
So, today I got my shiny new fatal1ty gaming headset, all was going well till I opened it up and realized it was [the USB one]("http://us.creative.com/products/product.asp?category=437&subcategory=442&product=17806"), And I think I need an xfi driver or something like that to get it to work, is ther anyway to get this headset to work?

Addition details: when plugged in I can hear the start up ubuntu sound but thats all I get out of them.

---

### Post by Peter_G on 2008-10-20
*bump bump*

---

### Post by markbuntu on 2008-10-20
USB headests are not a problem, in fact they are very handy items that you can do a lot with.

All you need to do is direct your playing audio stream to them. You can do this in the pulse audio volume control. You can direct the stream to the usb headest by right clikcing on the stream and choosing move stream. You can also make the headset the default in the Output Device tab by right clicking on it. You can do the same for the headset mic in the Input Device tab.

You can have one thing on your speakers and another on your headset if you want. Like skype on the headset and music from your speakers. Or you can make a virtual device in pulseaudio so you can use both devices at the same time.

If you are not using pulseaudio but are using ALSA then you can change the device in System/Preferences/Sound but this gives direct hardware access to your applications and is not really the best way to go because conflicts will ensue. You can also use asoundconf-gtk which is a small ALSA application that you can use to change your default sound card to the usb headset and will have fewer application conflicts. 

But really, the best way to deal with multiple sound devices is to use pulseaudio.

If you want to know more, you can look at the guide to multiple sound cards I have written here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

If you need more help, let me know. If this solves your problem please mark this thread as solved using the thread tools above.

---

