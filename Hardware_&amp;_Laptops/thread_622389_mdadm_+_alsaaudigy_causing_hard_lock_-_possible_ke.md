---
title: "mdadm + alsa/audigy causing hard lock - possible kernel bug?"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by dutch_gecko on 2007-11-24
I first posted this problem [in the media section](http://ubuntuforums.org/showthread.php?t=617777) but since then I've got some more info, and the problem is looking more sinister than it was back then.

Essentially, there seems to be some kind of conflict between my sound output (on an Audigy 4) and an mdadm raid 5. If, and only if, the sound card is outputting sound, **and** the raid is being accessed, the computer locks up solid. I've found at least one exception to this for, and I may find more.

As described in the thread linked above, this first became obvious when trying to play music from the raid. As soon as I hit play, everything stopped responding. The problem was fixed by moving the music onto a non-raided partition.

Two days ago the lock-up appeared again - but I wasn't accessing the hard drive, only playing sound in a flash file. I then discovered that my housemate had tried to access some music off the raid over my samba share, and that's when I made the link.

Now I don't know what my next step should be. Try new versions of mdadm? Alsa? Newest kernel? Should I remove the sound card and see if the problem persists with the on-board sound?

I'm not sure how to go about finding out what the problem is, so if anyone can direct me to a useful log file or something that would be awesome :D

Also, if I should be filing a bug report, where I need to report it to, and what information to enclose. I'm not very good at bug reports...

---

### Post by dutch_gecko on 2007-11-27
Small follow-up - 

It appears that this problem is caused by the Audigy 4 only. I removed it from my system and enabled on-board sound, which is happily playing while the raid reads and writes. So my guess is this is a bug in the alsa driver?

---

### Post by dutch_gecko on 2007-11-27
Large follow up (apologies for the triple-post, but there's no-one else talking) - 

Having spent several hours swapping hardware in and out of the machine I have finally nailed down exactly where the conflict is.

My computer will crash if and only if:

I am playing sound through the Audigy 4 (on-board Realtek chip is fine)
The RAID 5 is being accessed at that time
An ethernet interface is connected (not necessarily in use)

Using an external ethernet card appeared to have some success but later died. For reasons unknown, the problem will sometimes disappear for half an hour or so and then bite me when I least expect it. All in all, it's very weird.

For those interested, I've filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/172458](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/172458)

---

