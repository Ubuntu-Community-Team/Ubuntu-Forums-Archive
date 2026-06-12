---
title: "[SOLVED] pc locks up after trying login"
date: 2008-11-28
forum: General Help
---

### Post by haggus on 2008-11-28
I am having trouble getting into anything other than console login. Any session other than shell causes the screen to display a rainbow of colors and symbols but nothing else. I have tried recovery mode and still result. I am not really sure how to troubleshoot this and I could really use some help thanks.Using 8.04 on a Intel dual core 2Gb ram two 250 Gb Hd one with ubuntu other with windows and nvidia 8500gt video.

---

### Post by evildragon2 on 2008-11-28
It probably us something wrong with your xorg.conf file. Type:
```
sudo dpkg-reconfigure xserver-xorg
```
To reconfigure it. Tell me if it helps.

---

### Post by haggus on 2008-11-28
> **evildragon2 said:**
> It probably us something wrong with your xorg.conf file. Type:
```
sudo dpkg-reconfigure xserver-xorg
```
To reconfigure it. Tell me if it helps.

Thanks I tried to reconfigure xserver no change when I login.

---

### Post by Sef on 2008-11-28
1) What video driver are you using?

2) If you have onboard graphics, turn it on and see if the same problem exists.

---

### Post by haggus on 2008-11-28
> **Sef said:**
> 1) What video driver are you using?

2) If you have onboard graphics, turn it on and see if the same problem exists.

Hi thanks for the reply I managed to catch an error with kdm during bootup,so I installed gnome and switched to gdm. Which got me to the desktop. Although much of the desktop was missing. I restarted with an xfce session and for some reason way beyond me a message came up that the hard drive was full. Well I went to a failsafe session into my /home directory to the last folder I was working with. I was backing up a dvd with dvd::rip. Anyway long story short folder filled hd. Once I deleted it everything works fine. That is all I can explain with my knowledge level currently. It may be time to do a backup and possibly clean install I believe I have been upgrading since 6.10 to 8.04 probably lots of extra junk maybe a clean 8.04 would be a good solution.

---

