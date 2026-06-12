---
title: "Why do my hard drives keep dying?"
date: 2008-12-01
forum: Hardware
---

### Post by immensewok on 2008-12-01
I'm running Mythbuntu 8.04 on a 3GHz Pentium 4 with 1G of ram and a fairly generic Asus motherboard (I forget the exact model number). The machine is used primarily for MythTV recordings (standard definition only) and a little bit of gaming via Wine. I've got the OS on a 30G IDE drive and a RAID 0 for storing recordings and videos for Myth.
My RAID is setup through the BIOS (I think its a Via chipset) and identified with dmraid (so I mount /dev/mapper/whatever). Everything works well for a while and then there's a catastrophe.
My first RAID was 2 x 500G SATA drives and they both died within a month. These drives are currently in the mail for a warrantee replacement. My second RAID was 2 x 750G SATA drives and one of them died within just two weeks. Just to be clear, "died" means I get nearly endless I/O errors during boot and reading/writing slows the system to a crawl and then crashes it. In the second case "fdisk -l" can't identify the bad drive at all. 
So my question is, am I putting two much stress on my drives? They're on all the time writing and erasing 1-2 GB files in parallel. Do RAIDed drives get significantly hotter than two independent drives? Would a standalone RAID controller be more reliable than the one built into the motherboard? Is RAID more trouble than its worth?
I guess this is kind of an open question but has anyone else experienced hardware problems with a busy MythBox? Any suggestions for preventing such expensive breakdowns?
My apologies if this should've gone in the MythTV forum.

---

### Post by morphos on 2008-12-01
> **immensewok said:**
> Is RAID more trouble than its worth?

Opinion here: Regardless of the benefits of RAID, you are, at minimum, doubling the chances you take with the possibility of a failed HDD.  You should realize that while RAID is a good solution for some problems, it isn't the solution for all problems.  Is the situation you're trying to solve really requiring RAID?  Would a substitute drive or image be a better swap-in, drop-in solution to your problem?

---

### Post by immensewok on 2008-12-01
> **morphos said:**
> Opinion here: Regardless of the benefits of RAID, you are, at minimum, doubling the chances you take with the possibility of a failed HDD.

That's very true. I setup the RAID because a) these are big files and b) I wanted to see if I could make it work. It was done more out of curiosity than necessity. Also, these files are just TV shows and therefore disposable. RAID may not be the right solution for me (its starting to look that way).
I'm still wondering if the chance of failure is more than doubled with RAID 0 because of something beyond probability. Things like heat, extra reading/writing, or maybe just the high demands of MythTV. Well, is MythTV really all that demanding if I don't mess around with HD content?

---

### Post by tgalati4 on 2008-12-01
Why exactly do you need RAID to play back video?  RAID is helpful if you are doing video editing.  But if you were doing video editing, you would be using a Mac not Linux.

My guess is is either heat (too much) or power (not enough of).  When RAID is used, both drives are cranking in heat and power.  If this is a low-profile case, you may have problems with both.

You also need to break-in your drives before using them.  Try running badblocks on them or doing some non-critical, large-file moving.  You want to stress the drives a little before using them in more critical applications.

Try running your system with the drives outside of the case so you can monitor power (meter leads in the back of the 5V or 12V connector) and temperature.  Install hddtemp so you can see drive temperatures.  Install smartmontools to you can keep watch of your drives before they fail.

Do a search on your VIA chipset and see if others are having problems.  VIA chipsets are not known for performance.  What was the model of the drives?  Hitachi Deathstars perchance?

---

### Post by iggykoopa on 2008-12-01
also in the newer versions of mythtv you can specify more than one folder for storage, so raid isn't really necessary like it used to be.

---

### Post by immensewok on 2008-12-01
> **tgalati4 said:**
> Why exactly do you need RAID to play back video?  RAID is helpful if you are doing video editing.  But if you were doing video editing, you would be using a Mac not Linux.

Need is the wrong word. I had all the pieces to put together a RAID so I figured why not? Now I'm getting the impression that RAID is something you ignore unless you absolutely must have it.

> My guess is is either heat (too much) or power (not enough of).  When RAID is used, both drives are cranking in heat and power.  If this is a low-profile case, you may have problems with both.

My power supply is 550W. I had problems with the PSU before so I bought the new one to make sure I had way too much power. Heat was my suspicion. I'm glad to have it confirmed.

> You also need to break-in your drives before using them.  Try running badblocks on them or doing some non-critical, large-file moving.  You want to stress the drives a little before using them in more critical applications.

I've never heard this but I'll give it a shot next time. I suppose its like stretching before a workout.

> Try running your system with the drives outside of the case so you can monitor power (meter leads in the back of the 5V or 12V connector) and temperature.  Install hddtemp so you can see drive temperatures.  Install smartmontools to you can keep watch of your drives before they fail.

All good stuff to look into. Although it seems like I'll be closing the barn doors after the horses have left and then broken and then lost all my data. Definitely going to keep a closer eye on it next time.

> Do a search on your VIA chipset and see if others are having problems.  VIA chipsets are not known for performance.  What was the model of the drives?  Hitachi Deathstars perchance?

Google says VIA is terrible. I'm not sure if I'll ever RAID again but if I do I'll get a better controller. The drives were Samsung Spinpoints. I got one of those super special limited time offers from NewEgg. They came highly rated and were cheap.

I'm getting the impression that I don't need a RAID. There's no real benefit for me and all I'm doing is pushing my drives to the breaking point.

Anybody else have a story about RAID ruining drives? Or even better, some steps you can take to prevent failure?

---

### Post by immensewok on 2008-12-01
> **iggykoopa said:**
> also in the newer versions of mythtv you can specify more than one folder for storage, so raid isn't really necessary like it used to be.

Is this LVM (I just never figured it out) or something else?

---

### Post by tgalati4 on 2008-12-01
Logical Volume Manager (LVM) allows you to add drives in the future without messing up your existing file system assignments.  I'm not sure if LVM is needed for myth's access to multiple folders.

I've had problems with Hitachi DeskStars on a generic Intel board (DP35P) with on-board RAID controller.  That is why I call them Hitachi DeathStars.

I'm assuming Samsung Spinpoints will now be known as Samsung Splatpoints.

I needed to exercise the DeathStars for them to work reliably with RAID on a client's machine.  He also thought RAID was a good idea, until we ran into problems.  I advised against it, but the client insisted on RAID.  What are you going to do in that situation?

---

### Post by iggykoopa on 2008-12-01
it's not lvm, when your setting up the directories just seperate them with a : i.e. /storage1:/storage2 . It will decide where to put the video based off of how full the drive is and some other stuff, that way at least if one drive goes bad you'll still be able to recover the data from the other. When I first started with mythtv I used lvm and had nothing but problems with it, it's not all that complicated but if you don't need it I wouldn't recommend it.

---

### Post by immensewok on 2008-12-01
> **iggykoopa said:**
> it's not lvm, when your setting up the directories just seperate them with a : i.e. /storage1:/storage2 . It will decide where to put the video based off of how full the drive is and some other stuff, that way at least if one drive goes bad you'll still be able to recover the data from the other. When I first started with mythtv I used lvm and had nothing but problems with it, it's not all that complicated but if you don't need it I wouldn't recommend it.

That's a good tip! I'm going to use it as soon as the computer works again.

---

