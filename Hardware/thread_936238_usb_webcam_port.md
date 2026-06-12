---
title: "usb webcam port"
date: 2008-10-02
forum: Hardware
---

### Post by elitenoobboy on 2008-10-02
I plugged in a usb webcam, which a logitech communicate stx, into one of the ports on my computer, and then launched a viewer called cheese to see if it worked, which it did after about a minute of cheese searching for it. Then I plugged it into a different port so that the cord wasn't in front, and now cheese can no longer view it. It just gives out static and color bars, even if I try putting it back in the original usb socket.

---

### Post by elitenoobboy on 2008-10-04
Does nobody here know why this is broken?

---

### Post by markbuntu on 2008-10-04
I have one of those and it works just fine. I used Ekiga to set it up, I had to get V4l from the repos and use that instead of V4l2 in Ekiga to get it to work but then it recognized the camera by name and cheese and skype and everything else worked. 
Did you close cheese before you did this?
Have you tried rebooting?

---

### Post by elitenoobboy on 2008-10-04
> **markbuntu said:**
> I have one of those and it works just fine. I used Ekiga to set it up, I had to get V4l from the repos and use that instead of V4l2 in Ekiga to get it to work but then it recognized the camera by name and cheese and skype and everything else worked. 
Did you close cheese before you did this?
Have you tried rebooting?
Ekiga just says that no device is found, whether I try v4l or v4l2 and then hit detect devices. For some reason cheese is also taking about 20 seconds just to start up each time I open it, presumably it is trying to find devices, which it never does. Rebooting does nothing.

---

### Post by markbuntu on 2008-10-04
Are you sure that usb port is actually working, try another one.

---

### Post by elitenoobboy on 2008-10-04
> **markbuntu said:**
> Are you sure that usb port is actually working, try another one.
As I said in the original post, it doesn't work in any usb port, not even the original one.

---

### Post by markbuntu on 2008-10-05
it may be broken, try it in another machine.

---

### Post by elitenoobboy on 2008-10-05
> **markbuntu said:**
> it may be broken, try it in another machine.
No, it still works just fine in windows vista on the same machine.

---

### Post by markbuntu on 2008-10-06
Hmmm....Do other things work in the usb ports?

---

### Post by elitenoobboy on 2008-10-08
> **markbuntu said:**
> Hmmm....Do other things work in the usb ports?
I tried my usb flash drive the other day, but that didn't work either. I rebooted, then the flash drive and webcam started working again.
I tested again right now, and the webcam is not working, but the flash drive is. What's weird about the flash drive not working at the time is that it seems to indicate that the problem was that the usb ports went out, but I use a usb keyboard and mouse which have never had reliability problems.
Also, while the webcam isn't working now, it's microphone still is (it wasn't last time I tested the webcam and it wasn't working).

---

### Post by Maheriano on 2008-10-09
I'd like to know how you even got it working in the first place, I'm trying to get Cheese working in Gnome and got nothing but bars and static. And there's no setup option to configure it either.....I plugged in and rebooted, is there anything else? Maybe I can help you with your problem once I get mine working.

---

### Post by markbuntu on 2008-10-09
I used Ekiga to set up my webcam. Then skpe and cheese and everything else started working.

---

### Post by elitenoobboy on 2008-10-12
> **Maheriano said:**
> I'd like to know how you even got it working in the first place, I'm trying to get Cheese working in Gnome and got nothing but bars and static. And there's no setup option to configure it either.....I plugged in and rebooted, is there anything else? Maybe I can help you with your problem once I get mine working.
cheese should just automatically detect it, if it is present, but ubuntu seems to real flaky with it right now.

Apparently, the latest linux kernel is supposed to have better webcam support, so I am hoping that intrepid will fix it when it is released.

---

