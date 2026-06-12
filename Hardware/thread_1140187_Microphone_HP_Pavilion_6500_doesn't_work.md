---
title: "Microphone HP Pavilion 6500 doesn't work"
date: 2009-04-27
forum: Hardware
---

### Post by attorianzo on 2009-04-27
Like the title.
The built-in microphone in my comp doesn't work (but works with windows).

I have read this:

[http://ubuntuforums.org/showthread.php?t=1019732&highlight=pavilion+microphone](http://ubuntuforums.org/showthread.php?t=1019732&highlight=pavilion+microphone)

But does anyone got through this problem?

---

### Post by upptown on 2009-04-29
I had the same problem. I had to dig around in all of the volume options to find out that the front mic is muted by default.  

Click on the volume control applet then click "volume control".  

Set the device to HDA Intel (ALSA mixer).  

Go to preferences and make sure that "Front Mic" is selected (this will give you a slider on Volume Control to control the front mike).  You should see that the front mic is muted when the slider is displayed. 

Un-mute and you are in the house! 

Hope this helps.

---

