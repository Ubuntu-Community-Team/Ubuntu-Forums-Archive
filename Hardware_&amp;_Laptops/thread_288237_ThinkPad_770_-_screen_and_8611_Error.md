---
title: "ThinkPad 770 - screen and 8611 Error"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by johnpenner on 2006-10-29
this is actually a thinkpad hardware issue, but i had to 
get through it in order to get ubuntu working, 
so here goes -- 

basically, i recently inherited an old ibm thinkpad 770, on which
i wanted to install ubuntu -- but i found the unit will not boot 
with a non-functional trackpoint device -- yielding an error 8611. 
it is possible to disable this by hacking the PRAM as follows: 

- Turn the ThinkPad on. It gets the error 8611, 
  and you get a popup to TEST or RESTART. 
- Type RETURN to Test -- this gets you to a screeen full of System Tests. 
- Get out of the Test Screen, by typing ESC, 
	this gets you to the main BIOS 'Easy Setup' page. 
- Choose 'Config', it comes up with: Memory; SystemBoard; Display, etc. 
- Type: CTRL-D (undocumented!) -- this gets you into 
	the 'System Configuration Edit Utility', which allows you 
	to edit the BIOS BootCode in the CMOS (hack!). 
- Change the value at Offset 20h from: 00, to: 01. 
- Type F2 to Save, and then F3 to Exit the Hex Editor, 
	then type: ESC to get back to the 'Easy-Setup' page, 
	and select: Restart (hit Enter in response to OK?). 
- It should now reboot, and bypass the 8611 error. 

after that, dapper installed without too much trouble (but no sound!!). 
does anyone know how to get sound working on a thinkpad 770?? 

also, there was a problem in that the default ubuntu did not 
recognize the full resolution of the thinkpad 770 screen (1024 x 768). 

going to: System > Preferences > Screen Resolution, only 800x600
and 640x480 resolutions show up -- annoying to not be able 
to use your whole screen!!  

basically it comes down to not enough display RAM. 
the default xorg.conf in /etc/X11 has the 'DefaultDepth' set 
to 24 (in the "Screen" section), and this limits the resolution 
to 800x600 -- changing this to 16 gives you only 16 bit colour, 
but allows you to use the full 1024x768 screen -- knowing this 
would have saved me hours -- hope it can help someone here. :-D 

cheers from toronto! 
JRP

---

