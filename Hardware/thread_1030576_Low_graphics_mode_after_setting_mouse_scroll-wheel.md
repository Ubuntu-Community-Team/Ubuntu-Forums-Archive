---
title: "Low graphics mode after setting mouse scroll-wheel"
date: 2009-01-04
forum: Hardware
---

### Post by arielt1985 on 2009-01-04
Hello,
I'm using hardy on a IBM ThinkPad X32. I tried to configure the scroll-wheel on my laptop by adding these line to xorg.conf:

Section "InputDevice" 
**** Identifier "Configured Mouse" 
**** Driver "mouse" 
**** Option "CorePointer" 
**** Option "EmulateWheel" "true" 
**** Option "EmulateWheelButton" "2" 
**** Option "YAxisMapping" "4 5" 
EndSection 

After restart the scroll-wheel still doesn't work, and I got a notification that Ubuntu cannot identify my graphics card and that I will have to configure it myself. 
After removing the line above from my xorg everything got back to normal.
Any suggestions?

Thanks
Ariel

---

### Post by arielt1985 on 2009-01-04
Of course, the lines I added to xorg were without the stars: ****

---

