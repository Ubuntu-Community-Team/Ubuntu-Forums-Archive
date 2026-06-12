---
title: "Disable right/left click in ubuntu 8.10"
date: 2008-11-04
forum: General Help
---

### Post by Megatron2 on 2008-11-04
I'm new here and i didn't find a specific Mouse forum so i'm posting here.

I play some shooting games and i use the left button to shoot and the right button to jump. Sometime you wanna rocket jump, but clicking the left and right button simulates clicking the mouse wheel.

I have tried putting this in my xorg.conf:
> 
Section "InputDevice"
        Identifier              "MOUSE0"
        Driver                  "mouse"
        Option                  "Device"                "/dev/input/mice"
        Option                  "Emulate3Buttons"       "no"
EndSection


But it doesnt work.
Some help would be nice. I have a VX revolution and all the buttons on the mouse works.

BTW installing ubuntu 8.10 worked prefect!

---

### Post by Megatron2 on 2008-11-04
Found some help here:

[http://ubuntuforums.org/showthread.php?t=970277](http://ubuntuforums.org/showthread.php?t=970277)

and here:

[http://ubuntuforums.org/showthread.php?t=968425](http://ubuntuforums.org/showthread.php?t=968425)

---

### Post by Megatron2 on 2008-11-04
Found the solution here: 
[http://ubuntuforums.org/showthread.php?p=6103262&posted=1#post6103262](http://ubuntuforums.org/showthread.php?p=6103262&posted=1#post6103262)

---

