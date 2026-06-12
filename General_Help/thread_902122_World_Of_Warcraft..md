---
title: "World Of Warcraft."
date: 2008-08-27
forum: General Help
---

### Post by enzodad on 2008-08-27
Was wondering if anyone has any luck. i have red and red forum after forum and the ubuntu forums. I installed patched changed wine.. wows config wtf.. when it goes to login screen it constintly flashes Like you would be alt+tab
ANd yeah that sucks Other then that the game works just fine. just cant do much of anything with it flickering. My charecters show up. sound is ok and other then flickering video is good.. Can someone help or give me a R~tards fix?
Thank you

---

### Post by shamusl on 2008-08-27
> **enzodad said:**
> Was wondering if anyone has any luck. i have red and red forum after forum and the ubuntu forums. I installed patched changed wine.. wows config wtf.. when it goes to login screen it constintly flashes Like you would be alt+tab
ANd yeah that sucks Other then that the game works just fine. just cant do much of anything with it flickering. My charecters show up. sound is ok and other then flickering video is good.. Can someone help or give me a R~tards fix?
Thank you

I don't know if this is the right forum to be asking that question, but I'll give it my best shot.

Which version of wine are you running?

---

### Post by geeth on 2008-08-27
Have you added

SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"

To the end of your config.wtf file.


Are you running it in fullscreen or windowed mode?

---

### Post by enzodad on 2008-08-27
Yes i hav added all that in my config.wtf. file. And i am running Wine 1.0,
I tried running it in both full screen and windowed mode

---

### Post by gjoellee on 2008-08-27
> **enzodad said:**
> Yes i hav added all that in my config.wtf. file. And i am running Wine 1.0,
I tried running it in both full screen and windowed mode

Wine 1.1.3 is released an may contain fixes

download a .deb file here:[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by enzodad on 2008-08-27
yeah i just DLed the wine1.1.3 Ugh nothing works. :(

---

