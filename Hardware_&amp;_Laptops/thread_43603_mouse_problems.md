---
title: "mouse problems"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by gase07 on 2005-06-22
first let me say that i'm a beginner but after not getting the help i needed in the beginners forum i thought more numerous knowledgable people could be found here. this is the thread to my origional discussions on the problem.

[http://www.ubuntuforums.org/showthread.php?t=41759](http://) 

so as an overview i should say that i have a few year old IntelliMouse 1.1A PS/2 Compatible that works just fine with my windows operating system which i currently have on another drive. however, with ubuntu, the mouse responds sluggishly though all buttons work and i can (eventually) move the mouse to where i want it to go. the computer runs well under ubuntu (except for the mouse) and responds immediately to my keyboard commands.  here is the mouse section of my xorg.conf file.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
End Section

i've done some minor messing around with my xorg.conf file but nothing has helped. i've tried "PS/2", "ExplorerPS/2", and "Intellimouse" in my protocol option and also "Mouse1" and "Mouse0" in the identifier. this is all stuff i pulled up from other web help sources from people with remotely similar problems.

so i'm open to any suggestions, guesses or ideas that anyone might have.  remember, i'm a beginner. for all i know the video settings are wrong though i don't understand how that could have anything to do with it. if there are any other settings anyone would like to see, just ask.  thanks for the help.

---

