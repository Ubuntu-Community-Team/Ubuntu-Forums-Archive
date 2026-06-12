---
title: "Ubuntu 11.04 on notebook HP TouchSmart tm2-2101sl"
date: 2011-08-07
forum: Hardware
---

### Post by Albertoc67 on 2011-08-07
Hi to everybody,
Grannies gave to my daughter a great present: a notebook HP tm2 with touch screen.
The one you can turn the screen ad tilt it on keyboard like a tablet.
Win 7 is the operating system.
I want to install on it the new Ubuntu 11.04 in dual boot with the Win7.
Question: Can I do it? It's a "strange" notebook.
Could I lose some features as the touch screen?
Did anybody of you already try to do that?
Thanks a lot.
Bye from Italy.

---

### Post by Favux on 2011-08-07
Hi Albertoc67,

Sure you should be able to install Ubuntu 11.04 on it alongside windows.  The touch screen should work.  Yes a lot of people have done it.

[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2](https://wiki.edubuntu.org/HP%20TouchSmart%20tm2)
[http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)

For rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

The trickiest part is dealing with the two video chipsets.

---

### Post by Albertoc67 on 2011-09-04
I installed the 10.10 release and it works.
I just not able to set the PC for the automatic rotation of the screen when turned and closed on the keyboard as a tablet.
I tried a lot of times following the 
[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2](https://wiki.edubuntu.org/HP%20TouchSmart%20tm2)
without goal.
I don't understand why.
Hello and tx for the indications



> **Favux said:**
> Hi Albertoc67,

Sure you should be able to install Ubuntu 11.04 on it alongside windows.  The touch screen should work.  Yes a lot of people have done it.

[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2](https://wiki.edubuntu.org/HP%20TouchSmart%20tm2)
[http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)

For rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

The trickiest part is dealing with the two video chipsets.

---

### Post by Favux on 2011-09-04
Make sure your hp_wmi is auto-loading:
```
dmesg | grep wmi
```
If not add it to the end of the list in the modules file in /etc (/etc/modules) and reboot and check again.

---

### Post by diasf on 2011-09-04
I'm on one, just isn't a tm2 but a tx2 (damn AMD chip). I highly recomend magick-rotation to deal with the auto-rotation of the screen and input panel, works like a charm...

---

### Post by Albertoc67 on 2012-02-03
I did the work with maverick and the computer works well.
Yesterday my daughter told me about the not workng webcam,
I didn't take care about that, can you help me?
thanks a lot


> **Favux said:**
> Hi Albertoc67,

Sure you should be able to install Ubuntu 11.04 on it alongside windows.  The touch screen should work.  Yes a lot of people have done it.

[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2](https://wiki.edubuntu.org/HP%20TouchSmart%20tm2)
[http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)

For rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

The trickiest part is dealing with the two video chipsets.

---

### Post by Favux on 2012-02-03
Do you see the webcam in the output of the terminal commands *xinput list* and *lsusb*?  If so please post the output.

Does the webcam not work at all or is it a specific program?  For example does it work in Cheese?

---

### Post by Albertoc67 on 2012-02-04
> **Favux said:**
> Do you see the webcam in the output of the terminal commands *xinput list* and *lsusb*?  If so please post the output.

Does the webcam not work at all or is it a specific program?  For example does it work in Cheese?

thank you very much for the reply, I didn't know cheese so I tryed to installed and the webcam works fine.
My question was about skype: I've just tried once again to understand how to start the webcam without result.
My problem is only how to start the webcam with skype.
The out put of xinput list is:
  alessia@alessia-HP-TouchSmart-tm2-Notebook-PC:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen eraser                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Pen stylus                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E3 Finger touch                 id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]
alessia@alessia-HP-TouchSmart-tm2-Notebook-PC:~$ 

The output of lsusb is:
alessia@alessia-HP-TouchSmart-tm2-Notebook-PC:~$ lsusb
Bus 002 Device 005: ID 10f1:1a16  
Bus 002 Device 003: ID 056a:00e3 Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 138a:0005 DigitalPersona, Inc 
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alessia@alessia-HP-TouchSmart-tm2-Notebook-PC:~$ 

thanks for all
bye

---

