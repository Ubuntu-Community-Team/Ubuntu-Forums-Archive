---
title: "Downgrading from 9.1 to 8.04"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by sjweinberg on 2009-06-23
Hello!

So  I recently upgraded from 8.04 to 8.1 and then immediately to 9.1.

Things seemed okay at first, but I ran into some serious problems.  The most frustrating problem was that Skype is virtually impossible to use--calls disconnect, skype crashes, sound is delayed, things dont work, etc, etc.

When I went to the skype website, the first thing I noticed is that Skype actually only supports up to 8.04, and so I want to go back to 8.04--at least until some real support is offered for other versions.

Is there anyway to go back to 8.04 that does not involve losing all of my data?

Thanks so much for any advice!

---

### Post by merlinus on 2009-06-23
You cannot downgrade, only do a fresh install of 8.04.  If you have a separate /home partition that contains your data, then you simply specify its mountpoint and do not format it during partitioning.

If you only have a / partition containing everything, then you will have to back up data.

Also, did you really expect things would work well using an alpha testing version (9.10)?

---

### Post by sjweinberg on 2009-06-23
I see.  I don't know enough about all of this.  I don't actually know anything about separate /home partitions, but I am almost certain that I dont have such a thing.  I'll back up my data and do a fresh install.

Did I really expect things to work with an alpha testing version?  I was not aware that I was installing an unstable testing version of ubuntu (or whatever alpha means).  sorry for my insolence I guess...

---

### Post by merlinus on 2009-06-23
You might consider 9.04, which is the most current non-testing version.  Of course, I think all computer-related products, whether hardware or software, are always "in testing."
:)

Upon reinstall, however, you may wish to create a separate /home partition so reinstalling and installing newer versions will be much easier.

Also, I experience no problems with skype in 9.04.

---

### Post by irv on 2009-06-23
I know you want to go back to 8.04, but if I was you seeing you are going to do a fresh install, I would try 9.04 first and see if it will work for you. If not, than you could do the 8.04 install. Post and ask if others out here are using Skype with 9.04 and how it works? I don't use it so I can't help with this.

---

### Post by sjweinberg on 2009-06-23
Oh dear, I just realized where all of my total confusion has come from.

I didn't mean 9.1--I meant 9.04!!!!

Sorryyy!!!!!!!!

---

### Post by merlinus on 2009-06-23
OK, but you still cannot "go back" to 8.04 (or 8.10) without doing a fresh install.

But I wonder why you are encountering problems with skype?  It works as well for me now as it has since 7.04.  There is always a bit of an echo, as with cellphones, and talking at the same time as the other person always leads to strange sounds.

---

### Post by irv on 2009-06-23
I have MagicJack and I wish I could use it in Linux, but the software only runs in Windows. I don't it will work with Wine because it loads from the USB device.

---

### Post by merlinus on 2009-06-23
Try running it in VirtualBox.

---

### Post by irv on 2009-06-23
> **merlinus said:**
> Try running it in VirtualBox.

I thought of that, but I have a duel boot system with Vista and Ubuntu, so If I need to use it, I just boot to Vista. My point was I wish it was supported in Linux so it can be used native, but the developer only chose Windows, not Linux.
I think I got this thread off track. Sorry. Maybe we should get back on track.

---

### Post by spcwingo on 2009-06-23
> **irv said:**
> I have MagicJack and I wish I could use it in Linux, but the software only runs in Windows. I don't it will work with Wine because it loads from the USB device.

I did the online chat with one of their reps a few weeks ago and was told that Linux support for Magicjack is planned to be ready by the end of the year.

---

### Post by irv on 2009-06-23
> **spcwingo said:**
> I did the online chat with one of their reps a few weeks ago and was told that Linux support for Magicjack is planned to be ready by the end of the year.

Great, Thanks for the info. I will watch for it.

---

