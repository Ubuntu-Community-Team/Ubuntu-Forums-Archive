---
title: "Ubuntu doing a popcorn noise when playing audio"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Asimonew on 2009-05-31
Hello guys.

I am getting a noise like like a bad frequency every time I try to play some sound. It is a bit like a :popcorn:(popcorn) noise. Please can some one help me.

Every thing start when I wanted to get some sound from SKYPE. I saw some forums and I found that I should remove a component pulseaudio. Right, I did it and the Skype audio worked. Then I also saw in the forum that I should re-install the pulseaudio otherwise Ubuntu would not start. I did so.

When I start Ubuntu 9.04 again it made the instrange noise of bad frequency. So I tried some combination of install and remove the pulseaudio and none of them worked. Nor even the sounds of the Skype did. I tested some videos that were working fine before and still nothing.

Does any know what can I do to bring my good audio back and possibly the skype sounds too?

Many thanks:popcorn:

---

### Post by nyk on 2009-05-31
Try opening Volume Control, and turning up all the different channels. I'm not sure if it will work, but might as well give it a shot!

---

### Post by Asimonew on 2009-06-01
> **nyk said:**
> Try opening Volume Control, and turning up all the different channels. I'm not sure if it will work, but might as well give it a shot!
 
 
I am really a newbie I know:p.
 
I checked my audio and it was not mute.
 
I then found another forum saying some other staff to reinstall the drive.
 
Right, now I had the welcome sound and flash sound, which does not very well too.
 
Anyway, I tried to play a video with totem media player and didn't get any sound. My problem now became the totem, I do not have any sound coming out.
 
If someone know how to solve please help me.
 
Thank you everybody.

---

### Post by apjone on 2009-06-01
Open a terminal or Alt+F2 and type ```
gstreamer-properties
``` and chane the output plugin to the different options listed and test. That worked for me.

---

### Post by Asimonew on 2009-06-02
> **apjone said:**
> Open a terminal or Alt+F2 and type ```
gstreamer-properties
``` and chane the output plugin to the different options listed and test. That worked for me.
 
Great!
 
I think I solved it!
 
Thank you very much everyone!:popcorn:

---

