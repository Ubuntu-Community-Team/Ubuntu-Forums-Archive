---
title: "Gateway NV53 - no sound from speakers or headphones."
date: 2010-08-26
forum: Hardware
---

### Post by distrait on 2010-08-26
Hi, this is my first post here, and I need some help.

I'm running Ubuntu 10.04 on my Gateway NV53.  Sound used to work perfectly on the built in speakers, but the other night I plugged in my headphones and sound came through my headphones like one would expect (or not, as I've seen other posts on here describing a problem with the headphones not working with the NV53 and Ubuntu).  Anywho, after I unplugged my headphones, the speakers did not emit sound.  I've rebooted several times since then, speakers still don't work and now the headphones don't work either.

To say my speakers don't work is not entirely accurate.  When the pc starts up it plays that little Ubuntu start up sound when the login screen boots, and it plays it at whatever volume setting I had when I had last shut down.  After I log in, it no longer works though (does not even play the login music).

Also, I had found via a forum search a possible fix for the headphones by adding some code to the end of some text file for alsa mixer and tried it.  Didn't work.

Thanks!

---

### Post by distrait on 2010-08-26
Bump

---

### Post by distrait on 2010-08-28
Can anyone help?

---

### Post by lidex on 2010-08-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by distrait on 2010-08-30
Thank you for the response lidex.  I actually found a solution that someone had implemented on another type of laptop (or desktop, I don't remember the hardware) that simply involved deleting the .sound folder.  I did that and it seemed to have solved my sound issues.  That said, I dunno if deleting said folder could have any other negative side effects.  I have experienced none thus far.  I just came on here to post that solution for anyone who might stumble upon this thread.
 
I don't have my laptop in front of me but I can still run that script once I do if you think it will be useful (or I can do it just for kicks, whatever works).  Eitherway, I do appreciate your response

---

