---
title: "HP's in-built microphone does not work"
date: 2009-04-18
forum: Hardware
---

### Post by silentrebel on 2009-04-18
I have quite a frustrating hardware problem: my HP laptop's microphone does not work.  I've been testing it in Sound Recorder...  My eventual hope is to get it working with Skype. 
 
I've opened the mixer with the speaker-icon in the top panel.  I've fiddled with the options and noticed that all the microphone buttons (below the vertical slide-bars) always have x's on them (probably denoting the fact that they are muted).  When I unmute them, close the mixer and reopen it, I notice that they are muted again.

I have read and followed many threads to no avail; some describe problems similar to those I am experiencing but either present ineffective or unclear solutions.  I was wondering if anyone could help me in this matter.
Thank you.

---

### Post by Tobine on 2009-04-18
I've had nothing but problems with my HP mic so I got a headset. Works flawlessly

---

### Post by silentrebel on 2009-04-18
Your suggestion worked like a charm.  I then proceeded to continue looking for a solution to my initial problem:

-I opened the mixer again;
-chose *HDA Intel (Alsa mixer)* as the device;
-opened the *Capture* (Recording) tab (skip if it doesn't exist);
-pressed the *Preferences* button;
-checked *Digital Mic 1*;
-pressed the newly opened dialogue's 
-in the opened *Capture* (Recording) tab, I unmuted the *Digital Mic 1* by clicking the button the below the right vertical slide-bar (make sure there is no *x* on the picture of the microphone);
-I slid the right vertical slider all the way up;
-opened the options tab;
-selected *Digital Mic 1* for the *Digital Input Source * option;
-and selected *Mic* for the *Input Source option*;

I hope this helps everyone else...

---

### Post by Tobine on 2009-04-18
Its great that you have it all worked out! How good is the recording with the HP mic? Mine would only ever work if I turned my laptop around and talked into the battery :rolleyes:. Even then it still sounded crappy

---

### Post by silentrebel on 2009-04-18
My microphone is not anywhere near my battery, fortunately; it is next to my webcam on the top of my laptop's hood.  Nonetheless, the quality is not stunning.  It's merely functional...  I do not think that's Ubuntu's fault though. Shame... The sound *is* better captured with the plug-in microphone.  I maintain that your suggestion was a good one!
Thanks again.

---

### Post by Tobine on 2009-04-18
No sweat!

Yeah its definitely not ubuntu's fault because I also tried it in vista and XP and had the same results

> **silentrebel said:**
> My microphone is not anywhere near my battery

Neither is mine :-k
Whenever I spoke into the actual mic it just came out as buzzing.

---

