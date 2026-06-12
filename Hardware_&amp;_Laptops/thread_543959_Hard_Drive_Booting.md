---
title: "Hard Drive Booting"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by Kymac on 2007-09-05
Sigh... Ok, I know I probably shouldn't be asking about this on this forum, but, what the hell, I'll give it a shot.

My family's computer sometimes doesn't recognize the hard drive when we try and boot it.  After awhile, though, it just starts working again (i think unplugging and reconnecting the IDE cables helps).

Anyway, this would happen about once every 2 weeks on the computer (when it was running windows, 2 weeks i average, sometimes it would be a week, sometimes it would be months).  Being somewhat lazy, I would just ignore it after it fixed itself (and, considering, my inherent lack of knowledge in computers, which I'm trying to fix).  Anyway, about 3 months ago I finally installed Ubuntu onto the family computer (I've been using just Ubuntu on my personal desktop for about 6 months).

Anyway, the problem somewhat stopped, however, I just got a call from my sister, telling me it is doing the same thing (eg. cannot connect to hard drive, Press F1 to continue).

Therefore, I was wondering if I need to replace my IDE cables or something else isn't working right.  Sorry for the lack of info, and even for posting a non-Ubuntu related problem, but I figured I'd just throw this post out there (might as well).

Thank You
  ~Kymac

---

### Post by daveshields on 2007-09-05
Is this computer more than three years old? If so, the intermittent failures suggest that some component may completely fail soon.

The first thing I would do is to back up any critical data on the computer while it's still working. Since you have already made the smart move of installing Ubuntu then you just have to save the contents of the home directory:

$ sudo tar cfz  /home.tgz /home 

If you can write cd's then you can save the data on that, or if it's only a few gigabytes .you can it save it in a gmail or yahoo mail account. If more than that then you could get a new disk, copy the data to that, then substitute the new disk for the old one, install Ubuntu on that, and unpack the tar file.

---

### Post by Kymac on 2007-09-05
The only odd thing is, there are two hard drives in that computer, and (as far as my understand, because I am not physically there) they both seem to go bad at the same time, every time.  

Next time I visit there, I will most likely backup their music (I always tell them to do it, but they don't).

I know the computer is over 3 years old.  It is a Dell Dimension 4600, and I think I remember hearing somewhere (not sure where, or when) that there was something wrong with this model (connection to hard drives???  idk)

---

