---
title: "Aspire 1692 WLMi soundcard does (not?) work"
date: 2008-08-21
forum: Hardware
---

### Post by oz457 on 2008-08-21
Hello all,

I have been installing Ubuntu successfuly with my Aspire 1692. It was a bit tricky with the acpi, but now it works. 
But when the system boots, I hear the tam tam tam sound. Once logged in with the username and passwd, the sound stops working. I have been looking at the volume controll, but all are to the max levels.
Has anyone else experienced this problem?

---

### Post by pytheas22 on 2008-08-21
If you open up a terminal and type:
```

alsamixer
```

you will be able to control the sound volume on channels.  Make sure that every one is maximized.

Also, go to System>Preferences>Sound and try playing with the settings there.  Are you able to play test sounds?

If none of that helps, you may want to follow the [sound troubleshooting guide.]("https://help.ubuntu.com/community/SoundTroubleshooting")  Please let us know if this solves the problem.

---

