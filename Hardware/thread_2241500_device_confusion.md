---
title: "device confusion"
date: 2014-08-26
forum: Hardware
---

### Post by jgw on 2014-08-26
I have a camera hooked up to my desktop.  I am not sure howto access this device.  When I boot the light goes on for a bit then goes out.  Its a logitech camera.  Then there is the mysterious device.  This is one that worked on my windows machine but I don't think that ubuntu is recognizing it.  It is a camera that starts out with something like 5X zoom and goes up to something like 20X and is useful for examining things up very close.  It is plugged into a usb port.  Oh, in windows there is a program called usbdeview which will show everything hooked up to a usb port.  Is there a way I can get that same information in ubuntu?

Thank you..........

---

### Post by yancek on 2014-08-26
You can get information on usb devices with the command:  lsusb

Cheese is software that can be used with webcams, should be either installed or available in the repositories.  Open the Software Center and type cheese in the Search box, hit Enter and see what you get.  It should indicate if it is installed and if not have an install tab.  Not sure what you want to use the camera for but motion and zoneminder  can be used for motion detection.

---

### Post by jgw on 2014-08-26
Thank you for the reply.

I had cheese installed and it worked with the logitech.  From the usb list I found that my other device camera/magnifier was from Z-Star Microelectronics Corp. and is not recognized by cheese, as far as I can tell.  Here is a picture of that camera (hopefully I have attached it properly):
[ATTACH=CONFIG]255864[/ATTACH]

Thoughts?

---

### Post by digitaleagle on 2014-08-26
Just a thought:  I see a similar device in this thread, and they talk about downloading a driver package.  It's something to try at least.

[http://ubuntuforums.org/showthread.php?t=823857]("http://ubuntuforums.org/showthread.php?t=823857")

---

### Post by jgw on 2014-08-27
Thank you for the reply.  

That link was a bit sketchy but it made me do what I probably should have done in the first place.  I went to the english manufacturer site support and sent them an email about this.  Perhaps they have a driver or thought on how to do this.

Thanks again!

---

### Post by jgw on 2014-08-27
I decided to just go through available camera programs, one after the other, and see what happened.  I came across "camera' and, suddenly, I was hooked up!  Its interesting.  Camera, not unlike Cheese, appear to have no settings or controls.  Cheese will take a picture, Camera seems to have an option for either a camera or video camera but seems to work, in this instance, when either is clicked.   In either case camera is working for me!  I decided to post this and mark it solved.:D

---

