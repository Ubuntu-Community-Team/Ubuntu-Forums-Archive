---
title: "Skype webcam 11.04 work around"
date: 2011-05-01
forum: Hardware
---

### Post by RoddNZ on 2011-05-01
Hi I upgraded my Laptop to 11.04 yesterday ... 
installed skype to day seemed to ran will until I tested the video.. no go

loaded cheese ... webcam worked well...
it started to remind me of a similar issue back with ubuntu 7.04 ...

the work around back then was loading code into the skype ICON command line ....

I tried the following script and it works for me... it may work for you..

"env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"

    paste it into the command line of a skype icon on your desktop or the quick launch panel...

right hand click on the skype icon select properties and in the popup window you should see a line with "command" beside it... delete the word skype and paste in the following code
 
enjoy

---

### Post by Stagleton on 2011-05-02
I will try this when I get home. I downloaded Cheese and it would not work for my webcam....hoping I can get skype to work but it seems i must be missing a driver or something..
 
yes yes, n3wb here

---

### Post by mannynunez on 2011-05-02
Trying to implement this workaround and it seems easy enough but... when I right click the skype icon in either the launcher or from the desktop I do no get a property window. In fact, I get nothing. Hmmm.

---

### Post by Stagleton on 2011-05-03
> **mannynunez said:**
> Trying to implement this workaround and it seems easy enough but... when I right click the skype icon in either the launcher or from the desktop I do no get a property window. In fact, I get nothing. Hmmm.


yeah same here, I couldn't get it to work...

---

### Post by osfight.de on 2011-05-26
Worked for me, check also here

[http://ubuntuforums.org/showthread.php?t=1759012](http://ubuntuforums.org/showthread.php?t=1759012)

---

### Post by Ian Clark on 2011-06-18
Worked for me. Running Ubuntu 10.04 on an HP laptop with a Traveler PC webcam.

---

### Post by ssreddy555 on 2011-06-19
Applications >> Internet >> Skype >> Add this Launcher to Panel > Right click >> Properties >>Command

Now copied & Pasted the whole command including the word skype.

When I launch Skype now from the panel icon, video is working nicely.

Thanks a lot.

Amazing how I could find an answer in the forums to virtually any problem I have been confronted with.

I tried to find drivers in windows to this 11 yr old webcam - Intel CS 110 for the 64 bit for Windows 7. I just could not find one.

Open source is such a great place to be in. I have been using Ubuntu from the last 7 months and feel very happy I have switched from Windows almost completely.

---

