---
title: "Adesso NuForm keyboard touchpad no response"
date: 2018-07-12
forum: Hardware
---

### Post by hikikomoridev on 2018-07-12
I have a model year 1995 NuForm ergonomic keyboard that I recently won from an eBay auction:
[https://www.ebay.com/itm/Vintage-Touchpad-by-Cirque-PCK-303T-Adesso-NuForm-Ergonomic-Keyboard/163128293584?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649](https://www.ebay.com/itm/Vintage-Touchpad-by-Cirque-PCK-303T-Adesso-NuForm-Ergonomic-Keyboard/163128293584?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649)

I am currently using this keyboard now. I am using it with the old style IBM to PS/2 converter. The keyboard has a cable that is split onto two, the old IBM interface connector, and a serial connector. The keyboard's built in touchpad is not making any response. I am assuming the keyboard's touchpad works through that serial connector (You can see from the auction's images that the interface is split onto 2). My motherboard does not have a serial connector, so that serial connector is being routed through a serial to usb adapter. I am unsure what do to, do I need to call some driver through the terminal to make it all work or are these propetary keyboards not really supported in the Ubuntu world? 

Thanks :)

---

### Post by #&amp;thj^% on 2018-07-12
It might not be supported in linux.
but lets see with:
```
xinput list
```
**Paste back using code tags to preserve the format.**

---

### Post by hikikomoridev on 2018-07-12
```

xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; MemsArt MA144 RF Controller             	id=9	[slave  pointer  (2)]
&#9116;   &#8627; MemsArt MA144 RF Controller             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; MemsArt MA144 RF Controller             	id=8	[slave  keyboard (3)]
    &#8627; C-Media Electronics Inc.       Microsoft LifeChat LX-3000	id=11	[slave  keyboard (3)]
    &#8627; MemsArt MA144 RF Controller             	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard 

```

---

### Post by hikikomoridev on 2018-07-12
I worked it out, under terminal, the device is activated using ```
[COLOR=#333333][FONT=UbuntuMono]inputattach --microsoft /dev/[/FONT][/COLOR][COLOR=#1D2129][FONT=Helvetica]ttyUSB0
```
[/FONT][/COLOR]https://help.ubuntu.com/community/SerialMouseHowto

---

### Post by #&amp;thj^% on 2018-07-12
Good Job! :)

---

