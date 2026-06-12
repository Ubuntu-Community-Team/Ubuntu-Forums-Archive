---
title: "Sound too low"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by Zingam on 2005-05-10
When I record a sound I barely can hear it? How can I increase the microphone volume? (well I've upped it in the mixer but it's not enough)

---

### Post by JonahRowley on 2005-05-11
Try the **alsamixer** command.  The GUI mixers often miss some levels, alsamixer will show you everything.  Make sure you boost the level for the input you're using; if you're unsure, boost both line in and mic.

---

### Post by Zingam on 2005-05-11
[QUOTE=JonahRowley]Try the **alsamixer** command.  The GUI mixers often miss some levels, alsamixer will show you everything.  Make sure you boost the level for the input you're using; if you're unsure, boost both line in and mic.[/QUOTE]
 According to the multimedia selector: I'm using OSS, etc. and not ALSA, when I select alsa I get errors. I have built-in Realtek AC'97 codec, I think 655 or someting. This is the first distribution that seems to recognize it and it works partially. Actually it works, except that the mic input is too low.

---

### Post by somuchfortheafter on 2005-05-11
correct me if i am wrong but doesnt hoary use esd?

---

### Post by Zingam on 2005-05-28
[QUOTE=somuchfortheafter]correct me if i am wrong but doesnt hoary use esd?[/QUOTE]
 esd & oss appear in the multimedia system selector, when I try to select ALSA and test it I get an error massage.

---

