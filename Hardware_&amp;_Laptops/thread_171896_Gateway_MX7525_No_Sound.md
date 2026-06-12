---
title: "Gateway MX7525 No Sound"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by zpro on 2006-05-07
I can see from the other post, NO-Sound output is flavor of the month.
well, just installed 5.10 ubuntu, and you guess it .. NO SOUND,
all controls are un-muted, Nope. Have downloaded and install all the updates,
but still NO SOUND playback from CD's. 

:confused: :rolleyes:

---

### Post by Monkey_See on 2006-05-07
Hello,

I have a MX7515 which I believe is almost the same as yours ,hardware wise.  For my system I had to disable the "External Amplifier" switch.  I'm not absolutly sure this will work on your system but you can give it a try.

-To do this double click the volume contol in the panel (by default in the top right hand corner)  This will bring up the alsa mixer gui.

-Go to pull down "Edit" and "preferences".  Make sure the "External Amplifier" in the list is checked.  You can close the preferences window

-Then in the main alsa mixer window click on the "Switches" tab and uncheck "External Amplifier"

And now hopefully your sound will be working.

Hope that helps

M_See

---

### Post by zpro on 2006-05-08
Yes, that work.... THANKS +++++:p :p :p :p :p :p

Very ODD,
going to print this, 
I heard the ubuntu drums, when click on applications...
will give it the full test Monday, Look GOOD !

Thanks Again
;)

---

### Post by misu on 2006-05-09
Hi there !
 I have also an MX7525 and i've tried to install ubuntu ... the problem is that i cant use wireless network :( .. what should i do ? Also i have an USB tv tunner and i dont know how to install it .
 And the last question .. can anyone tell me what should i do to boot from an usb hard drive ????
 Thank you ;)

---

### Post by Monkey_See on 2006-05-09
zpro,

Glad it worked for you.

misu,

For your wireless card you will have to use ndiswrapper. see this thread for a good how to:

[http://www.ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper)

you will have to find your windows wireless driver, more specifically the .inf and .sys files, I believe your card is a broadcom 4318 or something similar, please correct me if I'm wrong.

For your tv card, maybe just try installing "tvtime" from synaptic if you haven't tried it already and see if it works.  I haven't had any experience with a usb-tv tuner, so some reaserch may be in order, though I bet there is a good chance some good info can be found here on the forum.

As for booting off a usb hard drive I haven't really done this before, though couldn't you just use the boot menu when you power on the machine F10 or F2, I can't remember which one then choose USB-HDD or similar.

M_See

---

