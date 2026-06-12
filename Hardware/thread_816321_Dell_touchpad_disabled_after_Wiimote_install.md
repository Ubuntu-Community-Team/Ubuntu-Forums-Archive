---
title: "Dell touchpad disabled after Wiimote install"
date: 2008-06-02
forum: Hardware
---

### Post by kilgor3 on 2008-06-02
I'm on a dell inspiron 600m.  I ran through the walkthrough at; [http://ubuntuforums.org/showthread.php?t=535659&highlight=wiimote](http://ubuntuforums.org/showthread.php?t=535659&highlight=wiimote) to get my Wiimote working under linux.  Now my touchpad doesn't work!  I went back and removed everything I entered into the xorg.conf file, but still nothing.  (Hardy Heron 8.04)

Any suggestions?

---

### Post by Rhubarb on 2008-06-02
Not sure, but this may work:
In your /etc/X11/xorg.conf you must put this paragraph under your synaptic touch pad part (NOT ABOVE):
```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection
```
I could be very wrong as I had just re-installed my video card drivers today replacing my xorg.conf - and my wii remote still functions fine without the xorg.conf modifications.

I should write up a better wiimote howto for Ubuntu hardy soon as it's much easier to do in hardy than that tutorial states.

---

### Post by kilgor3 on 2008-06-02
That did not work.  Basically, I just want to remove everything that walkthrough did to my touchpad.  I dont need the wiimote.  I was testing out its functionality for a media center box I'm working on.  But I still want all the bluetooth stuff.  I'm going through synaptic and removing all the stuff the walkthrough required to install.  I doubt that'll work though.  

I know my way around ubuntu, but once I get to the command line I'm still pretty much a noob.  It's kinda sad, because I've actively been using ubuntu for close to three years now as my main OS and I still feel intimidated by the command line and linux file structure lol

---

### Post by kilgor3 on 2008-06-02
> **Rhubarb said:**
> Not sure, but this may work:
In your /etc/X11/xorg.conf you must put this paragraph under your synaptic touch pad part (NOT ABOVE):
```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection
```
I could be very wrong as I had just re-installed my video card drivers today replacing my xorg.conf - and my wii remote still functions fine without the xorg.conf modifications.

I should write up a better wiimote howto for Ubuntu hardy soon as it's much easier to do in hardy than that tutorial states.

I JUST FIXED IT!!! 
I removed the mouseemu package and it worked right off the bat!  If you ever decide to make a hardy wiimote walkthrough let me know, because the one for gutsy is a bit outdated and I couldnt get the IR to work after hours of trouble shooting it.

---

### Post by TheUnwiseman on 2009-09-17
I had the same problem on my Dell Studio 1537 using Jaunty.  Removing mouseemu fixed it on mine as well.  Thanks!

---

