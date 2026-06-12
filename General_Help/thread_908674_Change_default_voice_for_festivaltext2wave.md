---
title: "Change default voice for festival/text2wave"
date: 2008-09-02
forum: General Help
---

### Post by bobonthenet on 2008-09-02
I downloaded and successfully installed a bunch of great new voices for festival and I found one I like.  My goal is to record my study guide as an audio file and listen to it while working out, pretty clever eh?  I figured out how to change the voice in festival but as far as I can tell I need text2wave to be able to output my guide as an audio file.  The problem I am having is that the voice I select doesn't seem to want to stay when I set it in festival and I can't find the command to change it in text2wave.  Is there even a way to do this?  I can get both programs to work but I just can't figure out how to create an audio file with the voice I like from my study guide txt file.

---

### Post by Mister.Vash on 2008-09-02
Take a look at this link and search it for /etc/festival.scm - that is the file where you can set the default voice for festival
[http://ubuntuforums.org/showthread.php?t=751169](http://ubuntuforums.org/showthread.php?t=751169)

---

### Post by rory526 on 2009-08-04
from:

[http://www.cuddletech.com/articles/tekref/festival.ref](http://www.cuddletech.com/articles/tekref/festival.ref)

You can change voices like this:

```
text2wave -o output.wav text.to.speak.txt -eval "(voice_us1_mbrola)"
```

voice_us1_mbrola  = voice type
output.wav        = output audio file
text.to.speak.txt = input text file

---

