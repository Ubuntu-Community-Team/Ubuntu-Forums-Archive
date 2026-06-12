---
title: "Touchpad on ThinkPad T430 not working Ubuntu 18.04.3 LTS"
date: 2019-10-16
forum: Hardware
---

### Post by spacewalk22 on 2019-10-16
Having trouble getting the touchpad recognized. Using ThinkPad T430 to run Ubuntu 18.04.3 TLS. Any recommendations?

---

### Post by kurt18947 on 2019-10-17
Sorry if I'm stating the obvious but you've looked at the Settings - Devices - Mouse and Touchpad menu to make sure it's enabled? I have a T430 and the touch pad works as expected (though I prefer the trackpoint most of the time). If the touchpad becomes unresponsive sometimes it helps to toggle between Two-finger Scrolling and Edge Scrolling.

---

### Post by spacewalk22 on 2019-10-17
Hi. Yes, I should have mentioned that I don't see TouchPad at all in Settings - Devices - Mouse and Touchpad and this laptop does not have the function key to toggle the TouchPad. I also verified its enabled in BIOS.

---

### Post by #&amp;thj^% on 2019-10-17
What does this show:
```
apt policy xserver-xorg-input-synaptics
```
Might not hurt to see this as well:
```
**xinput --list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=13	[slave  keyboard (3)]

```

---

### Post by spacewalk22 on 2019-10-17
[B]apt policy xserver-xorg-input-synaptics

[/B] xserver-xorg-input-synaptics:
   Installed: 1.9.0-1ubuntu1
   Candidate: 1.9.0-1ubuntu1
   Version table:
  *** 1.9.0-1ubuntu1 500
         500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
         100 /var/lib/dpkg/status
 
 
 **xinput --list** 
 
 &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
 &#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
 &#9116;   &#8627; HID 062a:0000                               id=10    [slave  pointer  (2)]
 &#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=13    [slave  pointer  (2)]
 &#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
     &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
     &#8627; Power Button                                id=6    [slave  keyboard (3)]
     &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
     &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
     &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
     &#8627; Integrated Camera: Integrated C             id=11    [slave  keyboard (3)]
     &#8627; AT Raw Set 2 keyboard                       id=12    [slave  keyboard (3)]
     &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

---

### Post by #&amp;thj^% on 2019-10-17
The device is not present in 'xinput list' output, so not surprising that Xorg does not report it either. Forget trying to configure an absent device in any desktop utility until it is first present.
Something is amuck here.

---

### Post by mörgæs on 2019-10-19
If you run the same commands in a live boot of 19.10 do you get a different output?

---

