---
title: "I have boken the xorg.config file"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Pausa on 2007-08-05
Hello,
i am a novice on linux sistems and i wanted resolve an issue with the scrolling of the firefox pages, i thinked it was an graphic issue so i have looked for a new graphic driver, i found a post on this forum, and i can't retrive it, where was discussed this problem but i haven't done all that the post propose so now ubuntu doesn't start and say that have a problem with the file xorg.conf. I have an acer laptop with the mobile intel 945gm express.

HELP!!!!

---

### Post by waggygee on 2007-08-05
> **Pausa said:**
> Hello,
i am a novice on linux sistems and i wanted resolve an issue with the scrolling of the firefox pages, i thinked it was an graphic issue so i have looked for a new graphic driver, i found a post on this forum, and i can't retrive it, where was discussed this problem but i haven't done all that the post propose so now ubuntu doesn't start and say that have a problem with the file xorg.conf. I have an acer laptop with the mobile intel 945gm express.

HELP!!!!

uh, If you have a backup just restore it. If not, try boot from your live cd and copy the one from there (this should work, i think). If you need more help or explaining feel free to ask

---

### Post by Pausa on 2007-08-05
I haven't backuped it and i think that the problem is that i must edit the xorg file with the specifics that was indicated in the post that i can't retrive becose i have made a new driver installation that i can't uninstall. If i must only substuite the file booting from cd i don't know how mount the disk in write access mode.

thanks for the answer

---

### Post by callan79 on 2007-08-05
> **Pausa said:**
> I haven't backuped it and i think that the problem is that i must edit the xorg file with the specifics that was indicated in the post that i can't retrive becose i have made a new driver installation that i can't uninstall. If i must only substuite the file booting from cd i don't know how mount the disk in write access mode.


You may have tried this already, but this is what I did when I broke my Xorg.conf by messing around with it manually.

This assumes you can at least log into a command prompt :)

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Pausa on 2007-08-05
If don't happen to you often that somebody call you genius it is becouse the world is unfair, but not this time. Man you are a GENIUS. Thanks alot after i have inserted the sudo etc. around 20 questions it was asked to me and around 19 i can't answer but i tried and now it work fine and WITHOUT  the line issue that have push me to change the graphic driver so it is perfect. THANKS

ciaooooooooo


ps: the post that i haven't well read  is this one:
[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

### Post by fredj on 2007-08-05
Now make a backup copy of your xorg.conf before you try any other experiments.

---

### Post by Pausa on 2007-08-06
ok

---

