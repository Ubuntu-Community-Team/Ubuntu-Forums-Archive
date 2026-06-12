---
title: "Crazy Mouse - Thinkpad Lenovo"
date: 2011-06-28
forum: Hardware
---

### Post by redunndancy on 2011-06-28
I have set up ubuntu 10.10 on a Lenovo Thinkpad. I love it, but I got one specific problem I can't seem to fix. Randomly my cursor will go nuts. It has nothing to do with my thumb hitting it while I type and once the mouse starts going crazy I have only found one way to control it. I have to touch both the track pad and the touch pad at the same time. As soon as I take my fingers off either, it goes back to going crazy. 

The other option I have found is to disable which ever periphial is going nuts (track pad or eraser mouse). I do this by 

xinput list

then disable by ... 

xinput set-prop 14 "Device Enabled" 0

Then the mouse will stop going crazy, but I can't use my track pad or eraser mouse (depending on whichever I disabled). For additional information below is the full list of the xinput list command. 

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=10    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=15    [slave  keyboard (3)]

I would love any help on this. I have done a lot of reading and I can't find a solid permanent fix for this.

---

