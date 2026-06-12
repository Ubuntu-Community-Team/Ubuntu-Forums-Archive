---
title: "built in webcam driver?"
date: 2009-02-26
forum: Hardware
---

### Post by twitch2197 on 2009-02-26
i have ubuntu hardy, and i'm running it on a compaq presario a900. I'd like to use my built-in webcam but i don't know where to go or if there even IS a linux driver for it. where could i find one? (besides google- i'm already working on that)

---

### Post by booshire on 2009-02-27
cheese could work, or a simple google search for "ubuntu webcam" apps
should be able to check if there are drivers by seeing if anything is pointing at /dev/video*

---

### Post by twitch2197 on 2009-02-27
all i get when i open cheese is a screen that reminds me of "this is a test of the emergency broadcast system".
all the multicolored bars.
and how does one find if anything is pointing to /dev/video?

---

### Post by Crafty Kisses on 2009-02-27
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2) To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post the results of this command:
```
lsusb
```

---

### Post by twitch2197 on 2009-02-28
heres what lsusb gave me:
```
Bus 004 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by Newfoundlander on 2009-04-23
I also have a Presario A900 with Ubuntu 8.10.  I used to get only a black screen in Cheese until I went under preferences and changed the resolution to 320x240 and everything works great now.  Hopefully that will work for you too.

Cheers,

Steve

---

