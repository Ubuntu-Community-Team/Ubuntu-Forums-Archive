---
title: "Why the big mouse problem?"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Moon-1 on 2007-02-10
Hi. I have been trying different Linux distros (running Ubuntu 6.10 right now) for the past year and I keep running into the same problem with every one. I have a 3 button scroll wheel usb mouse and I have yet to be able to figure out how to use the 3rd button. Why is this such a problem? Plain 2 button mice are probably in the minority now days. Most of the distros do a good job of hardware detection except with the mouse. It doesn't seem like things should be this way considering how sophisticated Linux has gotten. Does anybody have an answer?

Dick[LEFT][/LEFT]

---

### Post by RandomJoe on 2007-02-10
What brand/model mouse do you have?

I haven't had this issue in a LONG time - every 3-button scrollwheel mouse I have works just fine, and even the "3 button" trackballs I have (they're a little odd, not really like the mice) work by default.  All my mice are the opticals shipped by Dell, most appear to be rebranded Logitech mice.

And I guess, now I think of it, all my trackballs are Logitech...!

You might check your xorg.conf file and see what protocol it is using for your mouse.  All mine use "IMPS/2" - seems like I had one install (probably Slackware) that defaulted to just PS/2 and the scrollwheel didn't work.  Changing it to IMPS/2 enabled that.  Here's the relevant section from my xorg.conf - it appears to be the same even on the Slack system I just checked:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

Can't say why you are having so much trouble, other than perhaps your mouse is being misdetected / is misreporting itself so gets configured differently...

---

