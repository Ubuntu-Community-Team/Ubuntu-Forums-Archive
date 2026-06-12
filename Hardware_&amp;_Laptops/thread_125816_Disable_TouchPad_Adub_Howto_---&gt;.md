---
title: "Disable TouchPad Adub Howto ---&gt;"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by adub on 2006-02-04
Ok maybe this will reach someone and maybe it will not.   Today I spent probably too much time trying to figure out how to disable the touchpad...lol

so now its time for me to repay my fellow ubuntu community and hopefuly save someone some time

I'm running breezy/badger 5.10 btw but should work on others

I searched around and learned about various programs probably one of the better ones and the one i went with is qsynaptics

1)    apt-get install qsynaptics

2     update your xorg.conf     (be sure to always back up your xorg.conf before editing)

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"              <------ add this line
EndSection


This line is added to enabled x shared memory

3)  Now  your qsynaptics program works beautifully to disable it the option button on the home screen.  You can also enable for later use so is better than disabling in bios.  Unfortunately,  my bios revision didn't have an option to disable synaptics touchpad so I had to resort to the above.


Make note that commenting out your xorg.conf til your blue in the face or deleting things in there wont work just follow the above and you should be ok.


UPDATE:  Each time X loads you will have to open qsynaptics and hit apply to reapply the settings at the moment i dont have a work around for this, but it gets the job done and definitely not too much of a hastle to load a program and hit apply then close  = )

UPDATE:  Make note also there are other good features with Qsynaptics like disabling tapping.

UPDATE:  This is a little obvious since we are editing xorg.conf but you will need to restart X    ctrl   +  alt  +  backspace   or just reboot

---

### Post by mendy on 2006-05-30
Worked for me too!

Just remember to reboot.

I was doing all sorts of things until I rebooted, and then qsynaptics came up fine.

I also got continuous error messages before that.

---

