---
title: "Disabling touchpad buttons while keeping the &quot;tap to click&quot; function"
date: 2020-05-04
forum: Hardware
---

### Post by lestnitsa on 2020-05-04
Hello. I have this problem where my board is cracked and this causes my touchpads buttons to randomly click when I move the laptop. I tried to use xinput commands in order to disable the physical buttons, while keeping the pointer and scroll functions of the touchpad.

 However, I haven't been able to figure out which are the buttons to disable. When I disable the button 1 of the touchpad, it causes both the "left click" and the "tap to click" on the touchpad to not work. Disabling other numbers seem to do nothing. What are your suggestions in this case, so that I can disable the clicking buttons on the touchpad while keeping it for pointing, scrolling, single and double clicking? Thank you.

 Here I have given the information from my terminal:

user@user-Lenovo-Yoga-2-Pro:~$ xinput get-button-map "SynPS/2 Synaptics TouchPad"
1 2 3 4 5 6 7
user@user-Lenovo-Yoga-2-Pro:~$ xinput list --long "SynPS/2 Synaptics TouchPad" 
SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
    Reporting 7 classes:
        Class originated from: 13. Type: XIButtonClass
        Buttons supported: 7
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
        Button state:
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Scroll
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Scroll
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 13. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 15.000000
          flags: 0x0
        Class originated from: 13. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: 15.000000
          flags: 0x0

---

### Post by erind on 2020-05-04
This is what I found online related to your problem. You need to experiment with the command below, because I'm not sure it'll do what you're asking for:  

[https://askubuntu.com/questions/725607/how-to-disable-physical-mouse-buttons-below-touchpad](https://askubuntu.com/questions/725607/how-to-disable-physical-mouse-buttons-below-touchpad)   

From your output, 13 is the id of your touchpad, 

> 
    **xinput list --long 13**    

to get a map of the different buttons and then the option --set-button-map to remap them. For example, 

   **xinput --set-button-map 13      0 0 0 4 5 6 7 8 9 10 11 12**

    disables the first three buttons in touchpad, that is, left, center and right. 

---

