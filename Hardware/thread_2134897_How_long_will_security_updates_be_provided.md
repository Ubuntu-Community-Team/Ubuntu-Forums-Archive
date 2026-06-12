---
title: "How long will security updates be provided?"
date: 2013-04-12
forum: Hardware
---

### Post by breezypt on 2013-04-12
I was just forced into updating my system to ubuntu 12.10 after a 12.04 upgrade, that fouled everything up and would just go into an error screen endlessly. At least you fixed compiz crashing every 2 minutes in .10. My question is simple how long will security updates be provided for 12.10?

---

### Post by slickymaster on 2013-04-12
> **breezypt said:**
> I was just forced into updating my system to ubuntu 12.10 after a 12.04 upgrade, that fouled everything up and would just go into an error screen endlessly. At least you fixed compiz crashing every 2 minutes in .10. My question is simple how long will security updates be provided for 12.10?

12.10 will be supported until April 2014.

---

### Post by breezypt on 2013-04-12
What do we do then for security?

---

### Post by howefield on 2013-04-12
Upgrade to the next version.

LTS releases are supported for 5 years, from 12.04 onward.

Non LTS releases are currently supported for 18 months, until 13.10 when I believe the support period will reduce to 9 months.

---

### Post by slickymaster on 2013-04-12
> **howefield said:**
> Upgrade to the next version.

Exactly.

---

### Post by deadflowr on 2013-04-12
What forced you to upgrade?

---

### Post by breezypt on 2013-04-12
I had 12.04 running perfectly. Not one problem. Along pops up update manager, and says I need updates. So I updated. After the update, my computer would not boot into the login screen, it went into cli with errors. I am starting to get the hang of this after countless reinstalls and hard drive reformats. I think if I only allowed the security update to take place, then  maybe I would still be using my 12.04. But the only way to keep my files was to put in the 12.10 boot repair CD, it said it repaired it, but when I went to boot, all it did was install memory tests, and old kernals that I knew nothing about. I tried everything not to lose 12.04 it was running so good, short of not seeing my android, I figured I will live with that, but everything worked and it was long term support. Now I am back stuck in 12.10. Which is better this week then it was last week. Last week compiz crashed every 10 minutes, this week its running . I'm just looking for an OS that everytimeI run the recomended updates I don't lose the OS.

I know I am not as smart as a lot of the experienced linux people. But I am trying. The only thing that I did that was different form a normal install to 12.04 was to put the real nvidia driver into the kernal becuase no matter what the devs say that nouvoue does not provide hardware acceleration. I just bought a GTX 650 card, so I downloaded the driver (310) from nvidia and learned how to install it. I went into tty1, stopped lightdm, ran the driver as an executable, then rebooted. After that 12.04 was in mint condition....until the update popped up, then all heck broke lose...if I did something wrong please tell me, I want to learn this and can take criticism.

thanks ,

John

---

### Post by howefield on 2013-04-12
Could have been a number of things, but probably a kernel update which didn't agree with the nvidia drivers.

Your card is supported by the 304.88 driver in the 12.04 repositories.

---

### Post by deadflowr on 2013-04-12
> **breezypt said:**
> 
I know I am not as smart as a lot of the experienced linux people. But I am trying. The only thing that I did that was different form a normal install to 12.04 was to put the real nvidia driver into the kernal becuase no matter what the devs say that nouvoue does not provide hardware acceleration. I just bought a GTX 650 card, so I downloaded the driver (310) from nvidia and learned how to install it. I went into tty1, stopped lightdm, ran the driver as an executable, then rebooted. After that 12.04 was in mint condition....until the update popped up, then all heck broke lose...if I did something wrong please tell me, I want to learn this and can take criticism.

thanks ,

John

I don't think you anything wrong per se.
But one thing I would recommend is to install the drivers from the repos instead downloading/installing the drivers from the web.

Most of the time repo drivers are easier to deal with, and as my own experience, crash the system less often.

---

### Post by breezypt on 2013-04-12
howefield ~ I think your right on the dime, because there were kernel updates in there along with nvidia current updates in there, I should have unchecked both and just did the security updates. But 12.10 is running now, & I ain't messin with it.  When the time comes maybe 13.04 will be LTS by then, & I'll just upgrade to that. All is not bad I had a habit in the past of backing up graphics onto DVD's when they got so cheap, I just found a bunch of pictures I thought I had lost forever on a previous hard drive reformat. And 12.10 just read them in and I was able to copy them into my pictures folder. I notice a lot of improvements in 12.10 over the past few weeks. My gratitude to the developers who I know must work tirelessly on this. Thank You! I'm going to mark this thread as solved.

---

### Post by howefield on 2013-04-12
Perhaps deactivating the proprietary driver prior to installing the newer kernel and then reactivating once updates were done would have been better.
 
A watch out for 12.10 in that when I used it, any kernel updates wouldn't have the associated headers installed automatically which would bork the nvidia drivers. Easy enough to fix, but a pain in the neck, perhaps that isn't the case now.

13.04 won't become LTS, as an interim release it will be supported for 18 months. 14.04 should be the next LTS all being well.

---

