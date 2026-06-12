---
title: "VAIO Synaptics Touchpad Edge Scroll Not Working"
date: 2012-10-26
forum: Hardware
---

### Post by bhatbhai on 2012-10-26
Hi all,

I'm running Ubuntu 12.10 on a Sony VAIO VGN-265F, dual-booting with Windows 7. I recently decided to play around with some new desktop environments such as E17 and Pantheon, but then was a bit disappointed when I noticed my touchpad's edge scroll wasn't working in either of them. I went back to Unity, only to find that now my touchpad scroll isn't working here, either. I've been doing some searching but have not found a good solution yet. Some things to note:

1) When I go to "Mouse and Touchpad," Ubuntu does not offer me touchpad options. Gpointings-device-settings also does not recognize I have a touchpad (it thinks I have a mouse).

2) After doing " $ xinput list " I got this:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (04f2:b14e)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

And once again, you can see that it thinks I have a PS/2 Generic Mouse rather than a touchpad. 

Any help would be GREATLY appreciated.

Oh, and just to be clear, I am only using my touchpad right now and have never used a mouse. The pointing, left-clicking, and right-clicking still works, I'm only missing the edge scroll function.

---

