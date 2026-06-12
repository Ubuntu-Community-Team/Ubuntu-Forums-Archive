---
title: "In need of assistance re-mapping buttons on Pen Tablet Huion 1060 plus / ubuntu 17.4"
date: 2017-05-01
forum: Hardware
---

### Post by caramel-pegasus on 2017-05-01
Hi, 

Recently I got a Huion 1060 Plus tablet working in ubuntu studio 17.4 and I'd like to get started on remapping the buttons. 

The tablet is working out the box in 17.4. 
I've added PTxconf to help solve the scaling across monitors.  (see here: [http://wenhsinjen.github.io/ptxconf/](http://wenhsinjen.github.io/ptxconf/) ) 
Now, I would like to set the buttons to do CTRL+Z (undo) and CTRL+? redo ... among other shortcuts. 

.... However, I'm not even sure where to start. 
Assistance / hints / ideas needed. 

I've been reading here but im uncertain if this would also apply for 17.4 or if its obsolete now that the table works out the box in 17.4
See this link: [https://github.com/DIGImend/digimend-kernel-drivers/issues/26](https://github.com/DIGImend/digimend-kernel-drivers/issues/26)
Scroll down to: "[2] CONFIGURING AND MAPPING TABLET:" 


Anyway, here's some info that might be useful: 

xinput list
```
caramel@pegasus-device:~/Desktop$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; Dell Dell Wired Multimedia Keyboard         id=13    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Pad                              id=11    [slave  pointer  (2)]
&#9116;   &#8627; PenTablet  Pen Pen (0)                      id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Dell Dell Wired Multimedia Keyboard         id=12    [slave  keyboard (3)]
    &#8627; Dell Dell Wired Multimedia Keyboard         id=14    [slave  keyboard (3)]
    &#8627; PenTablet  Pen                              id=10    [slave  keyboard (3)]

```


learning more about xinput... It looks like ID 11 holds the buttons maybe? 

xinput query-state 11
```
caramel@pegasus-device:~$ xinput query-state 11
2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
    button[8]=up
    button[9]=up
    button[10]=up
    button[11]=up
    button[12]=up
ValuatorClass Mode=Absolute Proximity=In
    valuator[0]=0
    valuator[1]=0
    valuator[2]=0
    valuator[3]=0
    valuator[4]=0
    valuator[5]=0
    valuator[6]=0
caramel@pegasus-device:~$ 

```


xinput get-button-map 11
```

caramel@pegasus-device:~$ xinput get-button-map 11
1 2 3 4 5 6 7 8 9 10 11 12 
caramel@pegasus-device:~$

```


[COLOR=#24292E][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by caramel-pegasus on 2017-05-01
(Continued from above... )

Here's an interesting observation when I run "xinput test 11" 

Huion 1060 plus ([picture]("https://drive.google.com/open?id=0Bxme8aTFi0jSb202N2FxQ2Z6U3c"))
I press the buttons in this order: 
(1) (2)
(3) (4)
(5) (6)
(huion logo) 
(7) (8)
(9*) (10*)
(11*) (12*)

And looking at xinput test in the terminal you can see below it seems to skip 4,5,6 and 7. 
physical button (4) is reported as (8), 
physical button (5) is reported as (9),
physical button (6) is reported as (10)
physical button (7) is reported as (11) 
physical button (8) is reported as (12) 

The bottom four physical buttons ...:
(9) (10) 
(11) (12) 
... Give no response. 
It's almost as if ubuntu studio 17.4 thinks the Huion 1060 is a Huion 610 ([picture]("https://drive.google.com/open?id=0Bxme8aTFi0jSQnU4Rm5uTUVMOTQ")) with only 8 buttons. 

```
caramel@pegasus-device:~$ xinput test 11
button press   1 
button release 1 
button press   2 
motion a[0]=12060838 a[1]=10283350 a[2]=0  // (this button seems to report something at random almost as if its clipboard dump or ctrl+v) 
button release 2 
button press   3 
button release 3 
button press   8 
button release 8 
button press   9 
button release 9 
button press   10 
button release 10 
button press   11 
button release 11 
button press   12 
button release 12 
^C
caramel@pegasus-device:~$ 
```


Ideally, I'd like to assign keyboard shortcuts to those buttons being detected. Even if it is only 8. 
Shift, Ctrl+Z , Zoom in, zoom out, F (blender 3d brush strength) 


(Notes to self reading material and clues:) 
[https://unix.stackexchange.com/questions/340643/how-to-remap-xinput-inputs-to-other-keys](https://unix.stackexchange.com/questions/340643/how-to-remap-xinput-inputs-to-other-keys)
[COLOR=#24292E][FONT=-apple-system]xbindkeys [/FONT][/COLOR]https://wiki.archlinux.org/index.php/Xbindkeys

---

