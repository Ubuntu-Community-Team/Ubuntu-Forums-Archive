---
title: "Several problems with sound on a C500 laptop"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by overcaffein8d on 2007-09-15
Hello there. Something is going wrong with my sound. I can turn on a video and watch it in Totem or VLC with proper sound. But that's about all I can do.

I have no sound in Firefox-- youtube, flash... everything, i think.

I think I have tried everything that has been mentioned so far... with no luck.

Also, I have no system sounds...login, logout, etc.
 
And of course, when I plug in headphones, it doesn't mute the speakers. But I'm not as worried about that.

I don't know whether this is the cause, but I think it might be: I tried to upgrade to a gusty kernel [as shown here]("http://ubuntuforums.org/showthread.php?t=511974&highlight=upgrade+kernel"), but then went back to the latest Feisty kernel, using the method shown in the same link.

I have an Intel 82801G (ICH7 family) High Definition Audio Controller (rev 01). on a compaq presario c500 laptop.

I have reinstalled everything pertaining to flash and everything pertaining to alsa. I have run out of ideas. also, my /etc/firefox/firefoxrc file has the line **FIREFOX_DSP="aoss"** in it.

thanks in advance,
dave

---

### Post by overcaffein8d on 2007-09-15
i fixed the gnome and firefox problem with this```
sudo asoundconf reset-default-card
```

---

### Post by longfeather on 2007-11-01
I had a major with the sound not working on a brand new install of 7.10 on a Compaq Presario too.  My solution was to add a kernel parameter for IRQ routing via the GRUB menu.lst file.  Here is a link to an alternative fix:

[http://islandlinux.org/howto/ubuntu-7-10-sound-issue-compaq-presario-c500-laptop-resolved]("http://islandlinux.org/howto/ubuntu-7-10-sound-issue-compaq-presario-c500-laptop-resolved")

---

