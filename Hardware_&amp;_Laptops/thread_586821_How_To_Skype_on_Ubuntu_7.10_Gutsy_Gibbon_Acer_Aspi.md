---
title: "How To: Skype on Ubuntu 7.10 Gutsy Gibbon Acer Aspire 5610Z"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Sabot on 2007-10-22
After installing Skype from their website, You can install the debian file.  You can even add the repository they offer to synaptic and stay up to date. There was one problem though. I could not get audio from the headset mic that I plugged into the ports on the front of the laptop. After fighting for hours, I found the solution.

1. In the upper right hand side of the screen there is an icon for audio (Next to date and time).
2. Right click the Audio icon and choose Open Volume Control.
3. From the Edit menu choose Preferences.
4. Make sure there are checks next to the following items:
Headphone
PCM
Line-In
CD
Microphone
Mic Boost
PC Speaker
Capture
Channel Mode
Input Source

5. Close the Preferences window.
6. Go back to the Volume Control Window
7. Click the Options tab
8. Set Channel Mode to 2ch
9. Set input source to Mic (not Front Mic)
10. Click the Recording tab
11. Click the mic icon for the capture slider to unmute the mic (there should no longer be a red x there). You can adjust the volume of your mic by using the sliders.
12. Close the Volume Control window.

Now when you use Skype you will have audio when you talk.

---

### Post by KKop on 2007-10-22
Great!  Thanks for these steps.  I had the same problem getting Skype to work.

---

### Post by alexef on 2007-11-01
Thank you a lot. This works for every single program needing audio capture (i.e. Ekiga). Now if I could make de Broadcom WiFi chip work...

---

### Post by wilerk on 2007-11-15
Hi there,

Thanks for the information, I have small problem still. I don't see the options tab in my volume control. 

Also I installed the realtek drivers and the mic is not working.

Any pointers would be greatly appreciated.

Regards,

Xander

---

### Post by Sabot on 2007-11-15
The options tab only appears if you have selected Channel Mode in the preferences. I am not familier with the realtek drivers. I use a stock Ubuntu 7.10.

---

### Post by mickthejew on 2008-01-21
What if you can't see the "Channel Mode" tab in your Sound Preferences?

---

### Post by Sabot on 2008-01-21
It should not matter.  The default worked for me.

---

