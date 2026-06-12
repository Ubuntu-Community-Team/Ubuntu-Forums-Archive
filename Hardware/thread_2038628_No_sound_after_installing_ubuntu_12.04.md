---
title: "No sound after installing ubuntu 12.04"
date: 2012-08-07
forum: Hardware
---

### Post by sithira_msn on 2012-08-07
hi,
I have installed Ubuntu 12.04 recently and experienced there is no sound at all. but when i logged as guest sound is working fine.

in normal user login there is no sound card found in sound settings.

 please be kind enough to advice.:confused:

---

### Post by f1ndingwalden on 2012-08-07
Try checking in additional drivers in system settings.

---

### Post by sithira_msn on 2012-08-07
nothing in system settings. here i have attached a pic

---

### Post by f1ndingwalden on 2012-08-07
No, under system settings, under hardware, instead of going to sound, go to additional drivers, and activate any addition drivers that are recommended. If this still doesn’t work, check and see if your sound card is on the list even if its not recommended, but there are often different version, and you want to activate the recommended one.

---

### Post by sithira_msn on 2012-08-07
there is no any addotional driver as shown in the attachment brother.

---

### Post by f1ndingwalden on 2012-08-07
Well, crap.  What kind of computer do you have?

---

### Post by f1ndingwalden on 2012-08-07
And sorry if im not much help,  I just had a similar problem before and thought I might be able to help. I guess not, but check out this thread I found, tell me if this helps.
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
Good luck, I'm going to bed, Ill check this thread again tomorrow when I wake up.
:guitar:

---

### Post by sithira_msn on 2012-08-07
acer Aspire 4736Z

---

### Post by f1ndingwalden on 2012-08-08
Follow these guides;
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

This one will probably do the trick, assuming you have a basic knowledge of the terminal;
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Shadius on 2012-08-08
> **sithira_msn said:**
> hi,
I have installed Ubuntu 12.04 recently and experienced there is no sound at all. but when i logged as guest sound is working fine.

in normal user login there is no sound card found in sound settings.

 please be kind enough to advice.:confused:

You can try reloading ALSA by doing the following command in Terminal:
```
sudo alsa force-reload
```

You can also launch ALSA by doing:
```
alsamixer
```

---

