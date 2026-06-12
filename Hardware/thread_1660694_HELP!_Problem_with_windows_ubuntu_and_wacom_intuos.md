---
title: "HELP! Problem with windows ubuntu and wacom intuos 4?"
date: 2011-01-05
forum: Hardware
---

### Post by noobXD on 2011-01-05
first sorry for my English... i know it sucks :)
i would be very glad if someone could just help me

 i have ubuntu lucid 10.4 and windows xp in the same computer with a bipartition of the disk created with virtual machine manager, and i have a usb pc tablet wacom intuos4 M and i use samba to share archives and that is how i could install the tablet (i mean... the software of the tablet) because if i put a CD Ubuntu is the only one that recognizes the CD (sorry i know i am messy in writing)

in ubuntu the expresskeys do not work but the pressure sensibility works very well, the
problem is that when i enter the virtual machine and i try to enter the software of wacom or even use the pressure in any painting program it does not work

i guess that as i said earlier windows does not recognize the hardware(USB entry) or cds or dvd im sorry if this has been posted already or if it is in the wrong place(i think that it is ok because it says hardware & laptops)

well thank you for reading and understanding that English is not my first language and that i am a complete noob... thank you very much!

---

### Post by Favux on 2011-01-05
Hi noobXD,

Welcome to Ubuntu forums!

I'm not sure I quite understand the problem.  Is Windows XP on the virtual machine of a Ubuntu install?  Or is it a XP VMM install with Ubuntu in the virtual machine.

Pressure works in Ubuntu.

Pressure does not work in XP mounted in the virtual machine?

You should be able to have the express keys and OLED's working in Ubuntu also.

---

### Post by noobXD on 2011-01-05
thank you for replying Favux

yes, is like you said "Pressure does not work in XP mounted in the virtual machine" (thank you for taking the time) 

it does work in ubuntu but im not able to use the express keys in both, 

i have the ubuntu wacom control panel but still... i dont know what is the problem of the express keys, 
every time i press one key the cursor appears in the top left corner and when i change the key commands in the wacom control panel they come back to the same (top left corner)
i read that is a bug of the control panel but i dont know how to solve it
(though i guess i can live with that)

but is the pressure in windows the problem that is killing me, i tried to go (in windows) to control panel but it says that there is no tablet, 
 i can use the tablet as a mouse (still it says that there is no tablet i dont understeand)

---

### Post by Favux on 2011-01-05
In Lucid enter in a terminal:
```
xinput --list
```
and
```
xsetwacom list
```
and post the outputs.
> but is the pressure in windows the problem that is killing me, i tried to go (in windows) to control panel but it says that there is no tablet,
i can use the tablet as a mouse (still it says that there is no tablet i dont understeand) 
Did you install the Wacom tablet software CD in XP?  I don't know anything about virtual machines.  So you'll need someone else to help you to get the virtual XP to read CD/DVD's.

---

### Post by noobXD on 2011-01-05
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 eraser                    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 cursor                    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 pad                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9                           id=11    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]



Wacom Intuos4 6x9 eraser ERASER    
Wacom Intuos4 6x9 cursor CURSOR    
Wacom Intuos4 6x9 pad PAD       
Wacom Intuos4 6x9 STYLUS  


wow that was fast thank you! 
i made a copy of the data from the cd and puted in the shared folder (so yes i guess i can say that i installed the software,) the software was installed successfully.
i think that as it cant recognize cd or dvds or usb it cant recognize the tablet (usb port) am i right? i don't know

---

### Post by Favux on 2011-01-05
Both of those outputs look correct.

In Lucid the default X driver is wacom_drv.so, which is in the xf86-input-wacom 0.10.5 package.  The package is called xserver-xorg-input-wacom in Synaptic Package Manager.  I think you need a newer one.  Please use part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") to clone the xf86-input-wacom git repository.

You may not need to do part I., which is the usb kernel driver wacom.ko.  Your wacom.ko seems to be working for your Intuos4 M.

I am rewriting (procrastinating on rewriting) the Intuos4 xsetwacom script.  That should help you too.
> i think that as it cant recognize cd or dvds or usb it can recognize the tablet (usb port) am i right? i don't know 
That sounds correct.  It sounds like you need to enable usb communication to the XP running in the virtual machine.  I'm assuming the CD/DVD optical drive is also on a usb port like the tablet.  There are virtual machine settings to do that I believe.

---

### Post by noobXD on 2011-01-05
ok i made the part II but now GIMP does not work and i lost the pressure sensibility D :
should i try to make what it says in part II? i dont know how to make the pressure come back : (

---

### Post by Favux on 2011-01-05
That shouldn't break Gimp.
> should i try to make what it says in part II?
Did you mean part I.?  Lets look at the output of xinput and xsetwacom list again first.

---

### Post by noobXD on 2011-01-05
im really sorry... i meant part III
i already did part II

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 eraser                    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 cursor                    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 pad                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 6x9 stylus                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

Wacom Intuos4 6x9 eraser            id: 8    type: ERASER    
Wacom Intuos4 6x9 cursor            id: 9    type: CURSOR    
Wacom Intuos4 6x9 pad               id: 10    type: PAD       
Wacom Intuos4 6x9 stylus            id: 11    type: STYLUS

---

### Post by Favux on 2011-01-05
No, don't do part III.  You shouldn't need to do it.

The outputs look good.

What's wrong with Gimp?  Did you reconfigure your extended input devices?

---

