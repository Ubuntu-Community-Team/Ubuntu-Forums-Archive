---
title: "Transmission hogs Hard Drive after ugrading to Intrepid 8.10"
date: 2008-11-18
forum: General Help
---

### Post by upallnight on 2008-11-18
The Transmission Bittorrent client seems to be writing unnecessaryly to the hard drive causing everything to slow way down.
In the System Monitor, Transmission is listed as using around 22% CPU and has a Waiting Channel value of "futex_wait".
I'm sure its transmission because after closing the client, the constant hard drive writing stops.

Has anyone else had this problem and found a fix?

---

### Post by Th3Professor on 2008-11-18
Transmission's a nice program, mostly for the elegance in its simplicity. However, I use something more complex when I want to have more control. If you're open to trying another application, you might find Deluge an acceptable alternative. There are others that also provide nice features.

---

### Post by upallnight on 2008-11-18
> **Th3Professor said:**
> Transmission's a nice program, mostly for the elegance in its simplicity. However, I use something more complex when I want to have more control. If you're open to trying another application, you might find Deluge an acceptable alternative. There are others that also provide nice features.

I used Deluge for a year but every once in a while, the database it used to keep track of torrents would get corrupted and it bothered me enough to switch to Transmission.
Transmission has been very robust and has all the necessary features like throttling, file priorities, and a nice web interface.

I think the problem is when Transmission is resuming a partially completed torrent and checking the already downloaded data.
It seems to freeze when doing this but after a few minutes it finishes checking the data and starts responding again.

---

### Post by Th3Professor on 2008-11-18
you said robust :lolflag:

---

