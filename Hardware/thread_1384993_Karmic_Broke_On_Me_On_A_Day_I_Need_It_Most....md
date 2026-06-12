---
title: "Karmic Broke On Me On A Day I Need It Most..."
date: 2010-01-19
forum: Hardware
---

### Post by AlexanderDGreat on 2010-01-19
Hi, I'm so upset with Ubuntu Karmic, I was using it since December 2009, then all of a sudden my dvdrom failed on a day I needed to present something in the office! I removed quiet splash and I noticed something wrong, can you help me fix this? I'm using a HP DV2000 Series Laptop

```
[    1.575003] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.605132] usb 1-4: configuration #1 chosen from 1 choice
[    1.908024] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    2.120094] usb 3-2: configuration #1 chosen from 1 choice
[    6.052029] ata5: link is slow to respond, please be patient (ready=0)
[   11.036029] ata5: device not ready (errno=-16), forcing hardreset
[   16.232029] ata5: link is slow to respond, please be patient (ready=0)
[   21.048028] ata5: SRST failed (errno=-16)
[   26.244029] ata5: link is slow to respond, please be patient (ready=0)
[   31.060028] ata5: SRST failed (errno=-16)
[   35.876982] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   35.877062] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   35.883054] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[   35.883130] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[   36.256028] ata5: link is slow to respond, please be patient (ready=0)
[   66.104028] ata5: SRST failed (errno=-16)
[   71.132028] ata5: SRST failed (errno=-16)
[   71.132089] ata5: reset failed, giving up
[   71.132181] ata6: port disabled. ignoring.
```

Also, here's something that came up recently (attached picture) Karmic says, there's something wrong with my drive, but I used my manufacturer's scan disk, and there're no bad sectors! I think it's a bug.

[https://bugs.launchpad.net/bugs/438136]("https://bugs.launchpad.net/bugs/438136")

I think I'm not really "new" to Linux, but now I don't know, after I updated, it seems Karmic is the one who did this not me, which shattered my confidence in an Ubuntu Linux system. Pls. help.

PS I tried an Ubuntu Jaunty LIVE CD, and my dvd is 100% OK!

---

### Post by DodgeV83 on 2010-01-19
This isn't related to that bad sectors popup, nor is it related to that bug you linked.

Tell us more about what happens when you put a DVD into the drive while in Ubuntu.  Do you hear clicking?  Does it just spit the DVD out?  Tell us everything.

Usually this sort of thing indicates a hardware error, meaning Ubuntu was not to blame.  Isn't it possible it's a bad DVD?  Does the DVD work in other drives on other laptops?

---

### Post by AlexanderDGreat on 2010-01-19
> This isn't related to that bad sectors popup, nor is it related to that bug you linked.

Oh really? Well I thought it was because the bug says...

[COLOR="Red"]palimpsest complains, that the disk has many bad sectors. palimpsest thinks, that SMART value 5 "Reallocated Sector Count" fails (screenshot attached). smartctl reports "[/COLOR]

and

[COLOR="Red"]I can confirm. Suffering from the same issue in 9.10 where Palimpsest is saying my Hitachi HTS541680J9SA00 has many bad sectors. Reallocated Sector Count. Pops it up every time I restart the computer.[/COLOR]

These are very similar to what I'm experiencing. I also have Hitachi Harddisk.

> Tell us more about what happens when you put a DVD into the drive while in Ubuntu.

Well, in the first place, the drive won't OPEN anymore.

> Do you hear clicking?  Does it just spit the DVD out?  Tell us everything.

But this isn't the case when I switch to a LIVECD or if I boot it first in the BIOS. I guess that tells everything that my DVD is 100% OK. [COLOR="Blue"]I think the Kernel broke this.[/COLOR] Forgive me if I'm wrong.

> Usually this sort of thing indicates a hardware error, meaning Ubuntu was not to blame. Isn't it possible it's a bad DVD?  Does the DVD work in other drives on other laptops?

Honestly, I want to believe this, but my dvd is OK, I was able to boot a LIVECD. Yes all DVDs are fine.

PS Also, when I come from suspend/resume - the CD produces this annoying sound as if spinning wildly forever in there so I have to restart the machine.

Thanks for answering DodgeV83. :-|

---

### Post by Hallvor on 2010-01-20
If you need the computer for work you should use a well tested distro with extremely few bugs, like Debian Lenny or Cent OS.

---

### Post by Sylslay on 2010-01-20
8.04 or 9.04 is good for work as any other tested OS, IMHO

---

### Post by AlexanderDGreat on 2010-01-20
> If you need the computer for work you should use a well tested distro with extremely few bugs, like Debian Lenny or Cent OS.

> 8.04 or 9.04 is good for work as any other tested OS, IMHO

Actually, these are great ideas. Thanks, but the hurt has been done.

---

### Post by AlexanderDGreat on 2010-01-20
I regret to say that those above are great ideas.

Indeed, what if I REALLY LIKE Ubuntu? Doesn't this mindset of using an OLD version, limit the amount of Market That Ubuntu Can Reach?

Why don't they stick with 1 distribution and perfect it?

---

### Post by Hallvor on 2010-01-21
> **AlexanderDGreat said:**
> Doesn't this mindset of using an OLD version, limit the amount of Market That Ubuntu Can Reach?


What`s with the business talk? Is that you, Mark?

If you want corporate environment stability, you`d better use a well tested OS with well tested applications. 

If you want a bleeding edge OS, expect bugs. It is really that simple. It would be nice to have the best of both worlds, but it is impossible because they rule eachother out. Software can`t be *both* bleeding edge *and* tested for a long time.

---

### Post by AlexanderDGreat on 2010-01-21
Hi Hallvor, market doesn't mean only business. What I meant to say are people. Surely Ubuntu is marketing to people, but NOT necessarily asking them to spend their money.

> If you want a bleeding edge OS, expect bugs.

I won't sour-grape every problem I have in Ubuntu. Sometimes, I need to ACCEPT the world as it is. It's also healthy to think of problems objectively: it failed, it failed, it worked, it must be good.

For now, even if Ubuntu failed me, I will still love it because of the things it taught me and these forums are filled with good helping volunteers. **Isn't this what Ubuntu is all about?**

I wonder if I've a different job, I won't have the time in the world to research all these BUGS. Will it still be worth it?

---

### Post by Jazzy_Jeff on 2010-01-21
If you don't have time to mess with bugs then you should be using the LTS version of Ubuntu. That is the most stable. I enjoy tweaking my computer so I like using the new releases. If I did need a computer for work that had to be rock solid then I would use the LTS version. Just my .02 cents worth.

---

### Post by t4thfavor on 2010-01-21
Probably a good call for a work machine, especially if you don't know alot about Linux.

I just hate to see a "Release" act like this, it makes those of us who advocate for the Linux community look bad, and we don't have $100b to deal with the screwups like Microsoft does.

Is Dell still carying Ubuntu? If so, use whatever distro they are using because Dell would be pissed if there were problems like this with the systems they sell (not that there arent, I'm just saying they have pull).

Meaning they are more likely to be fixed on a faster schedule.

---

### Post by AlexanderDGreat on 2010-01-22
> I just hate to see a "Release" act like this, it makes those of us who advocate for the Linux community look bad, and we don't have $100b to deal with the screwups like Microsoft does.

I don't mean for this happen. Next time, I won't put into production a release right away, I will test it first. This is the first time in 8 months, I can't solve a problem in Ubuntu.

---

### Post by AlexanderDGreat on 2010-01-24
Solved my problem! DOWNGRADED TO JAUNTY -- Took 1 FULL DAY -- that should have been **_*MY REST DAY, FAMILY DAY, & BASICALLY DO-NOTHING-DAY*_**. Thanks Ubuntu!

Duh... I'm being sarcastic.

---

