---
title: "Touchpad unusable"
date: 2015-05-26
forum: Hardware
---

### Post by LordVeovis on 2015-05-26
I just purchased a new Panasonic CF-54 and the touch-pad is not working correctly in Live or installed environment.  When I touch the touch-pad the mouse will move seemingly randomly at extreme speeds jumping around with random right-click, left-click, and clickreleases splashed in.

I am not sure where to even begin on this one.

---

### Post by LordVeovis on 2015-05-26
I can add a little more information after a day of looking into this with no replies.  I am not including copy / paste as this is not the system with the touchpad.

If I look at the ```
 xinput --list 
``` I get 2 mouse devices that are identified despite only having 1 mouse (touchpad) connected.  I have a SynPS/2 Synaptic Touchpad and a PS/2 Generic Mouse.  When I record events on these via ```
 evtest /dev/input/eventX > ~/evtest 
``` reviewing this data was able to show me that the only communication taking place has been on the PS/2 Generic Mouse and no communication on the detected Synaptic Touchpad.

---

