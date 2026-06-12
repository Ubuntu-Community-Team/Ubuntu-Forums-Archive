---
title: "Philips SHB7000 bluetooth headset part 2: Microphone"
date: 2016-06-21
forum: Hardware
---

### Post by Starbeamrainbowlab on 2016-06-21
Hello again,

Now that I've (sort of) got my Philips SHB7000 headset's speakers working with my Ubuntu 16.04 laptop (in [this post]("http://ubuntuforums.org/showthread.php?t=2328259")), I'd like to try and get the inbuilt microphone working too. Unfortunately, when my headset is connected it does not, unfortunately, show up as a microphone automatically. Here's a screenshot of the input devices window:

[http://i.imgur.com/ZEX8T07.png](http://i.imgur.com/ZEX8T07.png)


Does anyone know how to get the headset's inbuilt microphone to show up? Here's what I see if I right click on it in the blueman devices window:


[http://i.imgur.com/YeWRUcT.png](http://i.imgur.com/YeWRUcT.png)

---

### Post by X-RED_Tech on 2016-06-21
[COLOR=#000000]Philips SHB7000 is a bluetooth headset and, as usual, it supports both the 'headset' and 'audio sink' (A2DP) profiles. The microphone work **only**&#8203; in headset mode (mono, lo-fi). [/COLOR]

---

### Post by ajgreeny on 2016-06-21
Please do not use large inline images.

Either just use the http links as I have done in my edit, or use the attachment icon (paperclip) in the toolbar, navigate to the image on disk, and then upload it.

---

### Post by Starbeamrainbowlab on 2016-06-22
> **X-RED_Tech said:**
> [COLOR=#000000]Philips SHB7000 is a bluetooth headset and, as usual, it supports both the 'headset' and 'audio sink' (A2DP) profiles. The microphone work **only**&#8203; in headset mode (mono, lo-fi). [/COLOR]

Right. So if I switch it to headset mode / mono, the microphone should show up? That sounds like it would only be useful in a phone call or something like that. Thanks for clarifying that! How would I go about changing it's mode?

> Please do not use large inline images.

Either just use the http links as I have done in my edit, or use the attachment icon (paperclip) in the toolbar, navigate to the image on disk, and then upload it.

Ok. I'll keep that in mind in the future.

---

### Post by jeremy31 on 2016-06-22
Sound settings, click on the SHB7000 and change from A2DP to HSP/HFP, then you should be able to click on the input tab and select the SHB7000 as input if I remember correctly when I did this with the SHB4000

---

### Post by Starbeamrainbowlab on 2016-06-23
Yep, that seems to do the trick. Thanks for all your help!

---

