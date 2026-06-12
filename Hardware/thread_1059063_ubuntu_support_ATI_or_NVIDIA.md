---
title: "ubuntu support: ATI or NVIDIA"
date: 2009-02-03
forum: Hardware
---

### Post by gumbeto on 2009-02-03
Hello,

Which is usually best supported by ubuntu: ATI or NVIDIA? Which one has the best working drivers for linux?

Thank you,
gumbeto

---

### Post by Yashiro on 2009-02-03
They're both terrible if you're used to the functionality found in Windows. Nvidia is possibly, very marginally better, maybe, if the wind is in the right direction.

---

### Post by infm on 2009-02-03
Please elaborate on that, Yashiro
I've been wanting to make a switch, but I really like my ATI catalyst controller and my games.. 
Would you recommend just using a partition to install Ubuntu and just run Windows whenever I want to play a game?

---

### Post by wstout on 2009-02-03
If the choice were between ATI or NVIDIA I would certainly go with NVIDIA. Either way you will need to download the proprietary driver through Hardware Drivers in the System --> Administration menu. I have found that NVIDIA works much better, especially if you are considering running two monitors with your laptop. If I'm not mistaken Intel might be the best way to go. I have never used Intel graphics but I think they have open source drivers that work very well from things I have read. But, to the point I have both ATI and NVIDIA running well with 8.10 with full desktop effects.

---

### Post by shadowhacker on 2009-02-03
> Would you recommend just using a partition to install Ubuntu and just run Windows whenever I want to play a game?

That's what I do. I triple boot Vista, XP, and Ubuntu. I have this setup on a few machines, with a mix of ATI and Nvidia cards. I love Ubuntu, but video support is sketchy at best. Also, I have never been able to get Catalyst working correctly under Ubuntu. If you're wanting to game, do a dual-boot setup.

---

### Post by Yashiro on 2009-02-03
> Would you recommend just using a partition to install Ubuntu and just run Windows whenever I want to play a game?
Yes.

---

### Post by gumbeto on 2009-02-04
Thanks a lot for the replies.

Wasn't ATI releasing the specifications for their cards? I heard about that a lot of time ago. Didn't they do it already? If they did, why aren't there fully functional open-source drivers. And if they didn't, anyone knows when are they expected to do so?

And about NVIDEA: are their specifications open?

Cheers

---

### Post by Yashiro on 2009-02-04
Ati have released most of the information for their cards now. Nvidia have not.

Work on all the video drivers is still ongoing. From a desktop users perspective it's progressing at a snails pace.

---

### Post by luvr on 2009-02-04
> **wstout said:**
> If I'm not mistaken Intel might be the best way to go.
**Absolutely!**

In my experience, the proprietary drivers from nVidia are not nearly as bad as the ones from ATI, but my only computer that runs full-featured graphics under Linux absolutely hassle-free is my Dell Studio 17, which has an integrated Intel video adapter.

I used to be unconvinced that open-source graphics drivers were this critical, but I have learned from experience that they are. ATI graphics adapters will **never** work right until (if ever) full-featured open-source drivers become available for them. I don't believe that nVidia will ever support open-source drivers, so I doubt that these adapters will ever work reliably under Linux.

> **Yashiro said:**
> Ati have released most of the information for their cards now. Nvidia have not.

Work on all the video drivers is still ongoing. From a desktop users perspective it's progressing at a snails pace.

*"At a snail's pace"*? Feels far, **far** slower to me!

In fact, I recently vented my frustration in a post on these forums: [Linux Graphics: An Intel Monopoly?]("http://ubuntuforums.org/showthread.php?t=1058243")

---

### Post by fcorourke on 2009-02-04
I know the feeling, I stumbled upon correct settings in 7.10 and lost them, running VESA right now in 8.10 --- because if you make a mistake all you hear is sound if your computer being ready with NO screen at all. Ubuntu is getting better all the time. I do love it, but graphics are not needed for command line Linux and that is what the movers and shakers use. For morons like me that ust want to use the system by copying command lines from someone else video changes are really dangerous. I know ATI is bad, buying 2 Nvidia cards to check them out

   Fred

---

### Post by luvr on 2009-02-05
I have uninstalled the proprietary ATI drivers, and I'm using the open-source drivers now. I'm no longer interested in the headaches that the proprietary drivers cause.

If I want to see advanced 3D graphics in action, I'll use my Dell Studio 17 laptop instead.

---

