---
title: "Driver Advice"
date: 2012-12-12
forum: Hardware
---

### Post by Corelogik on 2012-12-12
Ubuntu 12.04 Precise, nVidia GeForce 440

Which of the highlighted drivers should I be installing?

I currently have the top one installed. The system seems to be working fine, but every once in a while, when the screensaver activates or I launch a video, it stutters for a second or two before smoothing out.

See attached.

---

### Post by papibe on 2012-12-12
Hi Corelogik.

I'd say stay with the recommended one unless stability or major problems. 

The experimental driver's mainly focus is to provide better support for Steam.

Now, having said that. there's nothing that stops you from trying it and see what it brings.

Let us know how it goes.
Regards.

---

### Post by Corelogik on 2012-12-12
Right I was more or less not wanting to use the, effectively beta, drivers. My question was more like which of the top two. One says recommended and one says "version current, post release updates". I was mainly wondering which of those would be best, generally speaking.

---

### Post by papibe on 2012-12-13
The next option, current-updates, is provided for the latest and newest cards, since a slightly newer driver may provide better support (at the cost of being less tested though).

For the minor glitches you are experiencing, you may want to search the forums for some tweaks.

For instance, setting Sync to Vblank on 'Nvidia X Server Settings' helps a lot with HD videos. Also in CCSM (Compiz Config Settings Manager) using the the Undirect Fullscreen Windows option is very useful for both games and video.

Let us know how it goes.
Regards.

---

### Post by Corelogik on 2012-12-13
Copy that. I'll look for those and play around with it a little bit. Like I said, it's working fine, just a couple of very minor annoyances. I was thinking maybe I didn't have the right driver installed or something.

Wheres would I find 'Nvidia X Server Settings' or CSSM, is there some sort of interface I get from the repos?

---

### Post by papibe on 2012-12-13
CCSM is in the repos, and easily installable using the software center.

'Nvidia X Server Settings' should be already installed, since it comes with the Nvidia driver.

Regards.

---

### Post by Corelogik on 2012-12-13
Doh! found the nVidia settings panel and am googling around for the CCSM since software center doesn't seem to show it anywhere. I have Universe selected, along with other things.

---

### Post by Corelogik on 2012-12-13
apt-get found CCSM but software center couldn't. Strange. Oh, and Sync to VBlank was already set in nVidia's panel. Will keep ya posted. Thanks for the assist.

---

### Post by grahammechanical on 2012-12-13
Do not search the software Centre for 'ccsm.' Search for CompizConfig Settings Manager. No space between CompizConfig. That will find it.

Regards.

---

### Post by Corelogik on 2012-12-13
I found CCSM, installed it, but couldn't find "Undirect Fullscreen Windows".

---

