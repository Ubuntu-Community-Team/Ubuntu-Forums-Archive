---
title: "Huion W58 Graphics Tablet Suddenly Stopped Taking Pressure Input"
date: 2017-04-03
forum: Hardware
---

### Post by lordamit on 2017-04-03
Hi all,

I am using Kubuntu 16.10 and have a Huion W58 tablet. It used to work out of the box. 

For the last few days - when I plug in the tablet, it is being detected correctly. It is also capturing the tablet cursor properly and capturing the pen tap click and the pen button clicks properly. 

However, it is not detecting any pressure. As a result, I can not draw on any drawing app that relies on pressure based drawing. Krita is throwing a segmentation fault as soon as I am touching the tablet with the pen. Using MyPaint, here is a sample output from mypaint app console: 


```
[FONT=monospace][COLOR=#000000]press= 0.000, speed1= 2.5767    speed2= 2.1952  stroke= 0.013   custom= 0[/COLOR]
.000 
press= 0.000, speed1= 2.5791    speed2= 2.1955  stroke= 0.015   custom= 0
.000 
press= 0.000, speed1= 2.5815    speed2= 2.1958  stroke= 0.017   custom= 0
.000 
press= 0.000, speed1= 2.5839    speed2= 2.1961  stroke= 0.019   custom= 0
.000 
press= 0.000, speed1= 2.5862    speed2= 2.1963  stroke= 0.021   custom= 0
.000 
press= 0.000, speed1= 2.5886    speed2= 2.1966  stroke= 0.024   custom= 0
.000 
press= 0.000, speed1= 2.5909    speed2= 2.1969  stroke= 0.026   custom= 0

[/FONT]
```

I have checked it using windows and the hardware is working properly.

Here are some system specific details:

```

uname -a
[FONT=monospace][COLOR=#000000]Linux amit-laptop 4.8.0-45-generic #48-Ubuntu SMP Fri Mar 24 11:46:39 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
[/FONT]
```

```

x[FONT=monospace][COLOR=#000000]input[/COLOR]
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9116;   &#8627; PenTablet Consumer Control                id=16   [slave  pointer  (2)]
&#9116;   &#8627; PenTablet Pen                             id=17   [slave  pointer  (2)]
&#9116;   &#8627; PenTablet Mouse                           id=18   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; HP Truevision HD                          id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                       id=13   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=14   [slave  keyboard (3)]
    &#8627; PenTablet Keyboard                        id=15   [slave  keyboard (3)]
    &#8627; PenTablet System Control                  id=19   [slave  keyboard (3)]

[/FONT]

```

Can someone please help me? I am willing to provide any other information required! TIA.

---

