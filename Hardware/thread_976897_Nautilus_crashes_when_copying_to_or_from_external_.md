---
title: "Nautilus crashes when copying to or from external usb drive"
date: 2008-11-09
forum: Hardware
---

### Post by satriaulie on 2008-11-09
Hi!
I've been using ubuntu for a few months now. Started when 8.04 was released.
It's been working perfectly. I have a 500gb Lacie usb drive that I've been using for backup. Also working perfectly up to a few days ago.
I was making a backup to secure my files before I upgraded to 8.10, and as I was copying my videos nautilus crashed. I then gambled and updated without a full backup. Update worked perfectly and all data saved.
Then I reformated the Lacie drive to ext3 and tried a new back up. Nautilus still crashes when I get to the videos.

Anyone know anything about this?
Can it be fixed or is it maybe my drive that is broken?

Saw a thread with something similar, but looked like their problem was mainly the fat32 filesystem. I'm using ext3.

---

### Post by SuperSonic4 on 2008-11-09
I'd check Nautilus first to see if that's to blame. Try copying with the command line ```
cp [COLOR="Red"]~/Desktop/file.odt[/COLOR] /media/[COLOR="Red"]hd[/COLOR]
```

change bits in red to whatever you want to test.

Personally, I like krusader ```
sudo apt-get install krusader
```.
Although it is a KDE app it is a twin panel file manager

---

