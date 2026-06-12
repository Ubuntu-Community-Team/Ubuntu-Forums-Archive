---
title: "Graphics: Unknown Fix"
date: 2012-07-06
forum: Hardware
---

### Post by Axxon95 on 2012-07-06
If no one has found it yet here is the reason it shows "Graphics: Unknown" on the System Details.
It requires mesa-utils
It brings the commands:
"glxinfo | grep render"   To show the Graphics Adapter(which fixes the Unknown response) with acceleration.
"glxgears"   To test acceleration.

Just thought I'd share this.

If this isn't the correct spot for me to post this information, let me know where for further reference . ):P

---

### Post by kalkems on 2012-07-07
Can you explain this some more. I am having problems with resolution detection, would this addition help?  My graphics card is an Intel 3200 something.

---

### Post by Axxon95 on 2012-07-07
> **kalkems said:**
> Can you explain this some more. I am having problems with resolution detection, would this addition help?  My graphics card is an Intel 3200 something.


Under System Settings/System Details, the Graphics would only show Graphics: Unknown, with mesa-utils it fixes this.
I guess to test if the drivers are installed/working do "sudo apt-get install mesa-utils" and run "glxinfo | grep render" and "glxgears" to test acceleration.

The resolution part, have you tried other screens?
My old eMachine(NVIDIA) shows incorrect resolutions on my pretty old 37" HDTV(through RGB/VGA), but other monitors shows up good.

Here is an example on my PC [http://www.youtube.com/watch?v=oxD6S8P1P3A](http://www.youtube.com/watch?v=oxD6S8P1P3A) Hope this can shine a little light.

---

### Post by kalkems on 2012-07-09
It's found the right graphics card - intel sandybridge mobile.  It does not offer the display 1280x1024 that I need though.  Maybe sandybridge doesn't handle this format.

---

