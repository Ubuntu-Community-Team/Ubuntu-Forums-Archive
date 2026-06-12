---
title: "screen resolution problem"
date: 2008-07-29
forum: General Help
---

### Post by l3larg on 2008-07-29
i posted on the absolute beginner area but no one knew what to do so 

my screen resolution is set to 1064 by 768 but the amount shown on screen is only 640 by 400 make me need to scroll to see the rest of the screen which make me feel sick at time just looking on the computer so HELP:confused::(

---

### Post by eric3_14159 on 2008-07-29
What kind of screen do you have? Under System->Preferences->Screen Resolution, do you have any options to configure what kind of screen to expect?

---

### Post by Diabolis on 2008-07-29
This is a problem with your graphics card. You can reconfigure it with this command:
```
sudo dpkg-reconfigure xserver-xorg
```

You can also modify your screen resolution directly in this file:
```
sudo nano /etc/X11/xorg.conf
```

Both methods do the same thing, but the first one has a "wizard" that will guide you through the process.

---

### Post by l3larg on 2008-07-30
> **Diabolis said:**
> This is a problem with your graphics card. You can reconfigure it with this command:
```
sudo dpkg-reconfigure xserver-xorg
```

You can also modify your screen resolution directly in this file:
```
sudo nano /etc/X11/xorg.conf
```

Both methods do the same thing, but the first one has a "wizard" that will guide you through the process.

the first one didnt work and i have zero clue on how to use the second command help?

---

### Post by Ataris on 2008-07-30
What video card do you have?

Read the third-to-last post in this thread if it applies to you:

[http://ubuntuforums.org/showthread.php?t=870013&page=2](http://ubuntuforums.org/showthread.php?t=870013&page=2)

---

### Post by l3larg on 2008-07-30
S3 Unichrome Pro VGA Adapter

---

