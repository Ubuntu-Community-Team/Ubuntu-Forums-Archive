---
title: "DRIVER FInd"
date: 2008-08-29
forum: General Help
---

### Post by enzodad on 2008-08-29
I am currently only having one problem with WOW the 3-5 sec glitch. im reading a guid that says to :::::
 Glitch every 3-5 sec

If you see a noticeable graphical studder every 3 to 5 seconds or so for this you need to edit /etc/X11/xorg.conf and add something like:

Option "UseFastTLS" "2"

to the Video card "Device" Section. This of course is normally a problem with the proprietary Linux Drivers for ATI cards. 


But i cont find it????????

The theres a re tune/complie stuff i cant do that im neew and to damn scared. might as well go back to xp.. here is site i got info from  [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)... im just haveing way to many problems with linux  cant even get volume control to work,,, See other posts

---

### Post by jerome1232 on 2008-08-29
What is it you can't find? xorg.conf or the "devices" section?

how are yo'u trying to edit xorg.conf? note the "X" in "X11" is a capital "X

I've never had issues with wow on wine.

You should be able to edit like this 
(gnome instructions)
```
gksudo gedit /etc/X11/xorg.conf
```
(kde)
```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by enzodad on 2008-08-29
i dont know really im just following the guide i am viewing and posted.. i have a lame fast screen flicker and its annoying and i cant play.
Its like im alt+tabing lol

---

### Post by jerome1232 on 2008-08-29
Did you try typing the commands I gave you? That will open xorg.conf in a text editor so you can add the lines like the guide you posted says to do.

---

### Post by enzodad on 2008-08-29
yeah i did. and added the line the guid suggested now my linux is choppy slow like cpu is overloaded

---

### Post by enzodad on 2008-08-29
I give up im switching back this is BS. cant play wow or anyother games flickering glitch bs.

---

### Post by jerome1232 on 2008-08-29
Well if you heavy into gaming windows will be best for you, that's just about all I use it for.

---

