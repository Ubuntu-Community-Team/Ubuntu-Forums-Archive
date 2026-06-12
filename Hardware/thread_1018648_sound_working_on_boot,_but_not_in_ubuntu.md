---
title: "sound working on boot, but not in ubuntu ???"
date: 2008-12-22
forum: Hardware
---

### Post by shinew on 2008-12-22
So I just noticed that my Audigy2 ZS Platinum sound card is not working, after it finish boots i meant..
I hear the sound from my speakers everytime it boots at, at the login screen, and when the xserver launches. Then I just couldnt' get the sound to work no matter which type of files i play with, including online music/videos. please help! :confused:

---

### Post by gettinoriginal on 2008-12-22
I found this site extremely helpful with sound issues:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Good luck :P

---

### Post by shinew on 2008-12-22
> **gettinoriginal said:**
> I found this site extremely helpful with sound issues:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Good luck :P

hey thanks!
I found out what the problem was right after I posted it. I was looking for the "delete" button...
so stupid me, apparently if "blacklist pcspkr" module on boot, i not only disable the annoying pc built-in speaker sound, the actual sound card sound was disabled as well...:lolflag:
I haven't confirm this with a reboot yet, but I'm just going assume so, because after enabled the pcspkr after logged, the sound suddently just works. And then it will still work if I manually disable the pcspkr sound again. weird...

thanks for the quick reply anyway!

---

### Post by gettinoriginal on 2008-12-22
Glad you found the problem, and you're welcome. :P

---

### Post by shinew on 2008-12-22
I still need help on this issue though. [http://ubuntuforums.org/showthread.php?t=1018555](http://ubuntuforums.org/showthread.php?t=1018555)
 So if you know anything about it, let me know. I'm thinking about placing an order today :D

---

