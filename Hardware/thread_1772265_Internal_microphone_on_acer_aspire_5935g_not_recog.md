---
title: "Internal microphone on acer aspire 5935g not recognized"
date: 2011-05-31
forum: Hardware
---

### Post by PiniFloyd84 on 2011-05-31
Hi, internal microphone on acer aspire 5935g isn't recognized. I have a HDA Intel Realtek ALC889. I tried changing the options in "/ etc / modprobe.d / alsa-base.conf" but nothing. Can anyone help me?

---

### Post by ChrisKu on 2011-05-31
> **PiniFloyd84 said:**
> Hi, internal microphone on acer aspire 5935g isn't recognized. I have a HDA Intel Realtek ALC889. I tried changing the options in "/ etc / modprobe.d / alsa-base.conf" but nothing. Can anyone help me?
 
Could you provide a little more detailed? What exactly are you experiencing when you are saying "the mic isn't recognized"?

---

### Post by PiniFloyd84 on 2011-05-31
The external jack microphone works perfectly. Pavucontrol and audio options show me: "analogic microphone" (external jack microphone that works), "analogic line-in" and "analogic input".  I do not know if the "analogic input" is the internal microphone, however, even if it still does not work; the "input level" bar does not move and skype, sound recorder, etc. do not receive the internal microphone signal.

---

### Post by ChrisKu on 2011-05-31
> **PiniFloyd84 said:**
> The external jack microphone works perfectly. Pavucontrol and audio options show me: "analogic microphone" (external jack microphone that works), "analogic line-in" and "analogic input".  I do not know if the "analogic input" is the internal microphone, however, even if it still does not work; the "input level" bar does not move and skype, sound recorder, etc. do not receive the internal microphone signal.

I would suggest to try to boot Ubuntu from a LiveCD and check whether your internal mic works in that environment. If yes we would need to look at your settings, if no ...
(This hint might sound a little "simple" but this aproach has helped me quite a few times :))

---

### Post by PiniFloyd84 on 2011-06-02
> **ChrisKu said:**
> I would suggest to try to boot Ubuntu from a LiveCD and check whether your internal mic works in that environment. If yes we would need to look at your settings, if no ...
(This hint might sound a little "simple" but this aproach has helped me quite a few times :))

Also in this way it doesn't work

---

### Post by ChrisKu on 2011-06-02
Could you place a link to the output of

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```here?

---

### Post by PiniFloyd84 on 2011-06-02
The link: [http://www.alsa-project.org/db/?f=d7e0b21117825f34227db8ca826437b4fb468b28](http://www.alsa-project.org/db/?f=d7e0b21117825f34227db8ca826437b4fb468b28)

---

### Post by ChrisKu on 2011-06-02
You stated in your first post:

> I tried changing the options in "/ etc / modprobe.d / alsa-base.conf" but nothing

I don't know whether you removed the changes you made but I would have expected a line saying

```
options snd-hda-intel model=acer
```

Did you try that option?

The second thing I noticed is that your mic channel seems to be muted. Have you checked ALL your channel levels using Alsamixer?

---

### Post by PiniFloyd84 on 2011-06-02
> **ChrisKu said:**
> You stated in your first post:

> I tried changing the options in "/ etc / modprobe.d / alsa-base.conf" but nothing                      I don't know whether you removed the changes you made but I would have expected a line saying

```
options snd-hda-intel model=acer
```Did you try that option?


I tried it and I removed it. With that option appeared in alsamixer "Front Mic" option, but all the audio stopped working. I also tried other acer options for ALC889, in case there was someone compatible, but nothing.

```

acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire    Acer Aspire 9810
acer-aspire-4930g Acer Aspire 4930G
acer-aspire-6530g Acer Aspire 6530G
acer-aspire-7730g Acer Aspire 7730G
acer-aspire-8930g Acer Aspire 8930G

```> **ChrisKu said:**
> 
The second thing I noticed is that your mic channel seems to be muted. Have you checked ALL your channel levels using Alsamixer?

Yes, I did it

---

### Post by ChrisKu on 2011-06-02
Sorry mate, if you unmuted your mic channel and still get no result, I am stuck. I guess you have browsed through all the threads in this forum saying "internal mic not working". Maybe and expert like lidex can help. Good luck!

---

### Post by PiniFloyd84 on 2011-06-02
thanks anyway

---

