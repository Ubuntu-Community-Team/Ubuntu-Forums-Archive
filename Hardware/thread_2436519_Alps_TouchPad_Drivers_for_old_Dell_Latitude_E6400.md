---
title: "Alps TouchPad Drivers for old Dell Latitude E6400"
date: 2020-02-07
forum: Hardware
---

### Post by rastaman18 on 2020-02-07
Hello. I have a Dell E6400 that was manufactured in 2009. I abandoned Windows in 2016 and loaded Ununtu 16 and it has performed great ever since, currently running Ubuntu 18.04. A couple weeks ago my keyboard had an unfortunate run in with a glass of wine. Got everything powered off in time and ordered a new keyboard. All keys on the new KB worked fine with the exception of the Touchpad and  associated L-R buttons. I thought perhaps a new defective, so I had them send me a new one. Same thing.
   I am  a novice with Linux,  my wireless mouse works fine, but I feel I'm maybe missing a driver or something. I've read that Alps drivers can be a bit weird on Dell laptops.

 I list xinput and receive the following:

Virtual core pointer                                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                       id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M325                                          id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad       id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick               id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                                      id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                    id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                                  id=6    [slave  keyboard (3)]
    &#8627; Power Button                                             id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                              id=8    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_2M: Integrate           id=9    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                   id=12    [slave  keyboard (3)]

   I've been jerking around trying to find a solution online, but realized I'm not Linux savvy enough to start messing around. If anyone could point me in the proper direction it would be most appreciated. Thanks, Tom

---

### Post by mörgæs on 2020-02-09
Hi, welcome to the fora.

> **rastaman18 said:**
> I've read that Alps drivers can be a bit weird on Dell laptops.


If you think that drivers are the problem then a good test is live booting 20.04 to see if anything changes.

---

### Post by rastaman18 on 2020-02-09
Ah, good idea. I'll give it a go. Thanks

---

### Post by rastaman18 on 2020-02-10
Well, booting a newer version was a good idea to test the drivers, but I booted 19.10 from a Flashdrive and still no response from the Touchpad, or it's associated left /right buttons.
Considering what I've read about Alps Touchpad drivers being troublesome with Dell laptops, can I use a Synaptics driver instead? Sorry if that's a dumb question, it's just that I don't know.

---

### Post by mörgæs on 2020-02-13
> **rastaman18 said:**
> 
Considering what I've read about Alps Touchpad drivers being troublesome with Dell laptops...

Please post the links.

---

### Post by rastaman18 on 2020-02-16
You mean the links I've read with people having Alps issues? Many of them are R rated; I can if you want but they are pretty old. I'm just trying to find out if I'm stuck having a non-functioning Touchpad on a new keyboard; or if there is an alternative option available to me. I don't want to square root it to death, I just thought as a novice user I might be missing something obvious.

---

### Post by wildmanne39 on 2020-02-16
> You mean the links I've read with people having Alps issues? Many of them are R rated
Please do not post any R rated links on the forum as that is against the rules.

---

### Post by rastaman18 on 2020-02-17
I wasn't planning to. Was just making a point.

---

