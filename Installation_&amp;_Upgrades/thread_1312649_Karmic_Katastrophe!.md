---
title: "Karmic Katastrophe!"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Umang on 2009-11-03
Hi,
I upgraded to Karmic Koala on Sunday and it wasn't a great experience. I'm still having a lot of problems, please do suggest what I should do. I've been using Ubuntu since 7.10 and have upgraded every six months. This is the first time that it has been so unpleasant. I have only had small issues otherwise.

If how I upgraded is relevant then here's what I did. I downloaded the alternate iso file. Checked the md5sum and it was correct. Mounted the iso (I usually burn a CD, but tried mounting directly this time). I upgraded as usual.

There was no error during the upgrade. Everything seemed fine.

**_First major problem:_**

After the reboot, I was not able to login to my account. Every time I put in my password, it would start loading (the fancy new scrolling) and the screen resolution would change. Then more loading and it would resolution would change again. Finally, I'd see the login screen again. So I logged in from root, and completed the partial upgrade. After a reboot, I was able to login to my own account. **(No terrible problem till now)**

Yesterday, I logged into my account and did my work for a few hours. I then logged out to let others use the computer. The exact same loop that I was talking of started happening. Except no login screen appeared. The sound that usually indicates login screen ready would play at the end of every loop. But the login screen never appeared. I pressed the power button on the CPU and booted again. This time the loop happened again - no login screen.

So I used the old kernel and it worked (extremely slow boot). I was told on the IRC to go to recovery mode and do an apt-get upgrade. I did. The new kernel now worked.

But, the original problem of not being able to login now kicked back in - only on one of the accounts. Tried to login and the scrolling splash stated. Looped and then came back to the login screen (gdm).

I went back to the old kernel and it worked properly (slow again). The old kernel doesn't feel very good. Boot times are very slow on the old one. Though this problem is not consistently showing up, I want to have it fixed, rather than have my family members calling me every few days.

**_Second major problem:_**

I have been flooded with Crash reports ever since I upgraded. Xorg and Metacity crash once every hour at an average. I've uploaded the reports. I don't really know what to do. Mail notification and a couple of other programs have also crashed a few times, but Xorg and Metacity are the only ones still crashing (at least I think so).

**_Minor problems/regressions:_**

Everyone in my family complained that in Jaunty the login times had increased significantly (they don't care about performance, so if they notice something, it's got to be major). 

Now, with Karmic, boot times and login times have shot over the roof. It takes longer for xsplash (black screen with white Ubuntu logo) to go than it took me to boot from start (including grub and login) in Jaunty. Then usplash (scrolling screen) takes forever to get to gdm. Not to mention the many minutes it takes to get from gdm to a ready desktop (nothing loading).

Even logging out takes forever. In Jaunty, it took no more than five seconds to reach gdm after clicking logout (it was click -> 2 seconds -> icons + programs disappear -> 2 seconds -> black screen -> 1 second gdm.

Now, it feels like the whole computer is rebooting when I click logout. I spend at least 20 to 30 seconds watching usplash scroll its irritating bar just to see the login screen!

(Ignore this last problem in brackets if you're bored with listening to problems. usplash is also pretty jerky. The scrolling bar often gets stuck for a few seconds every now and then)

Long story put short: Anything got to do with xsplash, usplash or gdm is **very very** slow since Karmic.

[U]**Conclusion** 
[/U]
With so many problems, most in areas that Karmic advertises itself to be better in (boot times, boot experience, etc), I'm seriously considering downgrading (trust me, I would consider that to be an upgrade) to Hardy so that I can upgrade to Lucid next year without having to see Karmic. Maybe even move to another flavor of Linux if Ubuntu is going to cause so many problems.

I'm not in a mood to sort each of these problems out individually. If you think a reinstall is a good idea then consider the fact that I don't have a separate /home partition as yet (but I have ~5 GB to create one, which should be enough).

What do you think I should do? I'd like to fix everything in one sitting - 5 hours on a weekend (at max).

Thanks

Umang

I'm on an oldish (~7 years) Pentium three machine if that makes any difference.

---

### Post by Umang on 2009-11-03
And there you go! I just logged out, and got stuck in that loop again. When I rebooted, I noticed something interesting.

The computer was in the endless loop again. I pressed Ctrl+Alt+F1, Ctrl+Alt+F2, etc repeatedly. When I finally got the terminal, I pressed Ctrl+Alt+F7 and I got the login screen! (It wouldn't have happened otherwise)...

---

### Post by sonicb00m on 2009-11-03
install it on a new partition from fresh.

copy over whatever you need from your old home to your new home but i don't recommend copying any kind of "configuration" files, especially when it comes system applications....pulse , gnome that kind of thing.

I've had karmic working flawlessly for a long time.

---

### Post by Umang on 2009-11-03
Hi,
Thanks for your reply. I'll do a fresh install. I'll get back with some doubts when I have them. (I plan to do it this weekend)

Thanks again

Umang

PS: Since we've already brought this topic up, and I've searched the forums without getting an exact answer: Now that I will have a separate /home partition, can I always do a clean install instead of upgrading? How will the other member of my family get their accounts back? Will I have to create them separately? (If you think this is off-topic, then I'll post it again later, before upgrading)

Thanks!

---

### Post by bergfly on 2009-11-03
As regards the home partition, everything on it will be unaffected by what happens on the root partition. So everyone's accounts will be good, however some files might not work if you have not reinstalled the appropriate app.  Generally I have two root partitions and a home. That way you can do the install of a newer version in one partition and point it to the /home partition while still having the working system available. GRUB should work this all out for you in the install process.  I am 1 for 7 in terms of upgrades (one has been successful in 7) which is why I came up with this strategy. Of course, it is highly recommended to tJust be aware you will probably have to  manual partitioning during install instead of letting the installer decide.Make a full backup of the entire home partition prior to any work on the upgrade.

---

### Post by Umang on 2009-11-04
The manual partition is fine with me. So, I won't need to create new users? I'll just install and get all four user accounts back?

Thanks for you help! :)

---

### Post by coffeecat on 2009-11-04
> **Umang said:**
> The manual partition is fine with me. So, I won't need to create new users? I'll just install and get all four user accounts back?

Um - just so you're forewarned, there may be a hiccup with this. I'm going from memory here, so what I say might be a bit garbled. I happened to read a thread a couple of days ago where someone had a problem with user accounts in a similar situation. I didn't participate in that thread or bookmark it so I can't give you a link - sorry.

Anyway from what I remember, the OP did a new install of Karmic using the old /home partition in which there were four other accounts apart from theirs. He/she ran the installer, created a first account with the same name, password, etc and it seemed that the installer picked up the old /home/OPname just fine and the OP was able to use all their old settings. But it failed to pick up the other four accounts. The four /home/whatevername folders were still intact and when the OP went to Users and Groups the utility refused to re-create each account, saying it was already there. Only they weren't and only the OPs account was offered on the login screen.

I can't remember the fix but it was fairly straightforward and the missing accounts were restored uncompromised. If you come across this problem, I'm sure a forum search will find the thread, or considering the clunkiness of the forum search facility, a google "site:ubuntuforums.org your search string" might do the trick.

Or perhaps the OP made a mistake in the installer - I don't know. Good luck anyway.

---

### Post by Umang on 2009-11-04
Thanks so much. I did actually read that post, or a similar one, but wasn't sure if that was what would happen in my case.

Anyway, thanks for your help. Although I won't be using the same home folders this time around - I'll just create the new users and then get the files back because I don't want to bring any of the potentially problematic things to my new installation. I was only asking for next time. But now I'm pretty clear about how I'm going to go about doing it. :)

Thanks again!

Umang

---

### Post by Umang on 2009-11-07
Thanks for all the help. I've reinstalled Karmic. Although doing all the backups and partition editing took a few hours, the finally installing was done in under 30 min. :)

I messed up on of the ntfs partitions using gParted (the computer just randomly went off) and lost that partition, but the other two (thankfully more important ones) ntfs partitions that had to be moved/resized are both fine. (I decided to ditch dd_rescue after I had no space left to write the image).

No crashes, login screen appears properly, no random flickering, but I still get message while booting about the resolution usplash uses (not a big problem). Boot time is definately faster than my **old** Karmic installation, but still feels slower than Jaunty.

Once logged in, everything is very fast. So I'm happy. :)

Thanks for all your valuable help!

---

### Post by Umang on 2009-11-12
Another problem. Its been almost a week since I did the fresh install of Karmic. Since the last two days I've been noticing that once in a while (~once in five or ten logins), I am not able to login. My resolution is not the default one. So after three scrolls of the usplash bar, the screen flashes (I guess its supposed to). However, once in a while, after this flash, I get tty1 then another flash and back to the login screen. If I try to login again, it logs in as usual.

It's rare, it's not fatal, but it irritates. Any ideas?

PS: It's only the refresh rate that's different. My refresh rate is 60Hz, the default is 75Hz. At 75Hz, some of the text isn't very clear, and the monitor **sometimes** squeaks.

---

### Post by bknhnd on 2009-11-12
Try to install Ubuntu fully, as in deleting the other partitions. That worked for me.

---

### Post by Umang on 2009-11-13
> **bknhnd said:**
> Try to install Ubuntu fully, as in deleting the other partitions. That worked for me.
No, I did do that. The last problem I posted is what happened after a fully clean (like you said) install. Deleted the old partition and created a new one. Even the /home is new (old documents copied back, a couple of program (e.g. .gnupg) were copied back. Everything else is completely new.

---

### Post by XProflmfao on 2009-11-14
That's just like my problem except my computer crashed and now won't even get into the login screen before the entire screen turns blank and nothing happens...

---

