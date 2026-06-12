---
title: "Touchpad thinkpad X240 not detected anymore"
date: 2018-07-18
forum: Hardware
---

### Post by lucatastrophe on 2018-07-18
Hi everyone, 

I have a thinkpad x240, and given the horrible original touchpad I changed it following this guide: [http://diy.mironto.sk/thinkpad-x240-replacing-touchpad-and-keyboard/](http://diy.mironto.sk/thinkpad-x240-replacing-touchpad-and-keyboard/)
It worked fine for more than 1 year until I got an issue with the touchpad gluing and I had to remove and put back the ribbon cable. Big trouble at the following reboot, the PC refused to boot with 7 beeps. With a short research online I understood that the trouble was with the touchpad. Once disconnected I can boot without trouble, but without touchpad!

My first idea was that I damaged somewhat the touchpad: I put back the old one, same problem. 
Then I thought I damaged the ribbon cable. I removed it and test each contact (not easy when you don't have the right equipment!!), they seem to be working.
Finally I'm turning on the direction of a software issue. In the BIOS the touchpad is activated. 
xinput list gives this output:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

```

As far as I can understand the touchpad is not detected. 
I'm using linux mint 18.3.

I'm not enough experienced to tell if it is a hardware or software problem. I'm using linux since 10 years, but so far I was always able to find my problems around, this time I need some guide to better understand which is the problem. 
Thanks for any kind of help.

---

