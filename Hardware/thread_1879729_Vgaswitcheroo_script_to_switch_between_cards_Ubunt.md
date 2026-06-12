---
title: "Vgaswitcheroo script to switch between cards Ubuntu 11.10"
date: 2011-11-12
forum: Hardware
---

### Post by vedovatti on 2011-11-12
Hi there,

I would like to ask help to the community to a script to change between graphic cards. I have a hybrid graphic card (ATI/INTEL).

Now, on the link: [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) is a good description about how to use the vgswitcheroo on Ubuntu 10.10 but the script to change between cards doesn't work for other ubuntu versions.

If there anybody out there that could adapt the script to Ubuntu 11.10?

Cheers

---

### Post by marifzein on 2011-11-15
same problem. My notebook : HP pavilion G4-1212TX , intel icore-5 sandybridge
VGA :
- Intel Integrated Grapic Processor
- AMD radeon HD 6470M

I have dual boot , ubuntu 11.10 and win 7
With Win 7 via catalyst I can switching VGA ( intel or AMD radeon).
In ubuntu 11.10 , i have a lot of trouble , i have to set "nomodeset" in grub to avoid black screen.
Need help ...

---

### Post by vedovatti on 2011-11-16
Hi there,

Check this: [http://ubuntuforums.org/showthread.php?t=1744188&page=5](http://ubuntuforums.org/showthread.php?t=1744188&page=5)

So recommendations about the switchable graphics. Seems property ATI does not support switchable graphics anymore and the only option is open-source drivers using vgswitcheroo. It was supported on the Catalyst 11.6 but not working 100% so many bugs. Now seems not supported anymore.

Anyway, on that forum do whats on the comment 14. It really works on my hybrid graphics. And then use the comment 27 to shutdown the computer without trouble.

The only problem is that I cannot successfully change via script to Integrated. I have to modify the /etc/rc.local file and restart to change to ATI discrete.

Cheers

---

### Post by vedovatti on 2012-05-13
I just solved the main problem I had,that was to switch hybrid graphics with a script. The solutions is on the comment 9 in the [http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317) . Just as additional info I have a HP tm2 (Intel/ATI) and Ubuntu 12.04. Finally I can manage both cards.

---

### Post by adi93 on 2013-05-07
Check out the following link for ubuntu 12.10. It doesn't exactly help to switch the graphic cards, but rather turns them on or off. Maybe someone can write a program based on this that allocates graphic card to different programs, like in windows.
[URL="http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/"]http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/

[/URL]

---

