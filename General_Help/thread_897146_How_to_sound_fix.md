---
title: "How to sound fix"
date: 2008-08-21
forum: General Help
---

### Post by weweboom on 2008-08-21
My built-in microphone is broken. When I record video there is no sound, when I start sound recorder, it tells me 

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

Either how do I change the multimedia settings (where are they located) or how do I fix this?

---

### Post by EMCGFX on 2008-08-21
I found this on blog @ [http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

Due this in terminal:

Run alsamixer
Unmute all the outputs by hitting &#8220;m&#8221;
Hit tab to go the capture settings
Highlight the &#8220;Mic&#8221; setting using the arrow keys.
Hit space to enable the microphone.
Highlight the &#8220;Capture&#8221; setting using the arrow keys.
Hit space to enable capture (note that just because you have volume bar
here doesn&#8217;t mean it is enabled).
Hit escape.

Let me know if it works.

---

