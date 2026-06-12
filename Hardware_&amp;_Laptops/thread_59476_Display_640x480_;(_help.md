---
title: "Display 640x480 ;( help"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by Gargamella on 2005-08-24
i've got as display an acer al502,in win xp i use 1240x768,in linux it let me choose only 640x480,i don't know if it's a display or a video card problem,but in win xp it's alright,

the video card is an ibm default Intel(R) 82845G/GL/GE/PE/GV

and the display is an acer al502,2 years old

i advise this problem in each version of linux i tryed.

if u've got an idea,i'm here waiting for a reply

thanks ](*,)

---

### Post by ubuntme on 2005-08-24
can you post your xorg.conf?

cat /etc/X11/xorg.conf

---

### Post by Gargamella on 2005-08-24
here it is my xorg.conf

---

### Post by ubuntme on 2005-08-25
this bit looks a bit funny:

```
"1024x768" "832x624" "800x600" "720x400" "640x480"
``` 

what display modes are avaliable in windows?  I would try replacing all of the modes above with what you have with the modes avaliable from windows, shouldn't they be wide screen modes?.  Mine for example looks like this:
```
"1280x1024" "1024x768" "832x624" "800x600" "640x480"
``` 
but my monitor is the standard aspect (4/3)

If it still doesn't work, I would consider deleting the lower resolutions so that xorg has to select a higher one.  This is a trick I have used sucessfully before.

Also your monitor section dosn't have a refresh rate, mine looks like this:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     75
EndSection
``` 

Usually you have a range for vertRefresh but I have forced mine to the highest value (which means I don't get the highest res but thats ok).  Refresh rates can be found in you monitor docs.

Hope that is some help, I remind you to back up you xorg.conf before you play with out.

good luck

---

