---
title: "RecordMyDesktop sound recording issues."
date: 2008-11-30
forum: General Help
---

### Post by iDellG3 on 2008-11-30
Hello Ubuntu forums, Again, I am having trouble with RecordMyDesktop, I am trying to get my voice in the video recording, but I am not sure how to do that, my imput recording device is a USB camera microphone, can any one give me directions on how to configure RecordMyDesktop so the sound works on the application?

---

### Post by neu2buntu on 2008-12-11
you need to check the output of :: arecord -l ...... this will show you the soundcard setup, my setup works with hw:0,0 and then open volume control (right click on the speaker symbol in panel) then click preferences and make sure input sources are ticked ,then in volume control click record and then in options choose mic (if i remember right front mic is the inbuilt mic)

---

