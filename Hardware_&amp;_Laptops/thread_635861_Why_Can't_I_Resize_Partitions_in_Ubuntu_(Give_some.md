---
title: "Why Can't I Resize Partitions in Ubuntu (Give some Free NTFS Space to Ext3)?"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2007-12-09
Was at a mate's place and ran into his drive decreasing in space after using the built-in "Copy Disc" (read [http://ubuntuforums.org/showthread.php?p=3919946&posted=1#post3919946](http://ubuntuforums.org/showthread.php?p=3919946&posted=1#post3919946) for more on the cache not flushing, especially if you know where the cache is, as I don't!). I saw that the drive had little breathing space anyway, so decided to grab some of the free space on the 230Gb unused NTFS partition and give it to the 9Gb Ext3 partition, but "Resize" was not even an option... no matter what I did.

I installed both **gparted** and **qtparted**, ran them as-is and with sudo (qtparted wouldn't even load properly without that anyway), and still no difference. Resize was not available for any drive or partition I selected, and even deleting the NTFS partition and recreating it made no difference.

So what am I doing wrong here? Why can't I resize anything in either editor? How do I achive this successfully? Many thanks in advance!

---

### Post by wjp.reg on 2007-12-09
Did you unmount the partitions before trying to change them?

---

### Post by OzzyFrank on 2007-12-09
I figured that may be a factor so tried unmounting the ext3 partition, but got an error (sorry, can't remember exactly what it said, but I have seen mention of not being able to unmount and resize in other posts too).

Is there a way to unmount all drives at once? Also, are there other partitioners that are better to use? Also, when I tried unmounting I may have been running it without sudo so is that a factor too? Cheers

---

### Post by wjp.reg on 2007-12-09
> **OzzyFrank said:**
> I figured that may be a factor so tried unmounting the ext3 partition, but got an error (sorry, can't remember exactly what it said, but I have seen mention of not being able to unmount and resize in other posts too).

Is there a way to unmount all drives at once? Also, are there other partitioners that are better to use? Also, when I tried unmounting I may have been running it without sudo so is that a factor too? Cheers

Thought you were trying to resize the NTFS partition?  Would the ext3 partition happen to have been your ubuntu root partition?  That would explain why you wouldn't be able to unmount it :-)

---

### Post by AgentZ86 on 2007-12-09
> **OzzyFrank said:**
> Was at a mate's place and ran into his drive decreasing in space after using the built-in "Copy Disc" (read [http://ubuntuforums.org/showthread.php?p=3919946&posted=1#post3919946](http://ubuntuforums.org/showthread.php?p=3919946&posted=1#post3919946) for more on the cache not flushing, especially if you know where the cache is, as I don't!). I saw that the drive had little breathing space anyway, so decided to grab some of the free space on the 230Gb unused NTFS partition and give it to the 9Gb Ext3 partition, but "Resize" was not even an option... no matter what I did.

I installed both **gparted** and **qtparted**, ran them as-is and with sudo (qtparted wouldn't even load properly without that anyway), and still no difference. Resize was not available for any drive or partition I selected, and even deleting the NTFS partition and recreating it made no difference.

So what am I doing wrong here? Why can't I resize anything in either editor? How do I achive this successfully? Many thanks in advance!

Run live Gparted CD, don't run Gparted from your mounted drive. Works every time.
Or perhaps the Live Ubuntu CD.

I hope this helps.

---

### Post by OzzyFrank on 2007-12-09
> **wjp.reg said:**
> Thought you were trying to resize the NTFS partition?  Would the ext3 partition happen to have been your ubuntu root partition?  That would explain why you wouldn't be able to unmount it :-)

So... any answers to these questions, or just more questions (no offence... but does come across as you having fun at my ignorance). As for the questions about resizing the NTFS partition, sorry, I thought I made it abundantly clear in the first post what I was trying to do that for... to give space to the ext3 partition.

If what you are saying is you cannot do anything to your Ubuntu partition while using it, then that means that using Partition Magic in Windows is actually much easier, and that the partition editors in Ubuntu are basically useless... perhaps good for just deleting an NTFS partition (oh, OK, and for reszing unmounted partitions)? So I'd perhaps be laughing at the difference between doing simple tasks like this in Ubuntu and Windows.

Forgive my ignorance on this... as you may have figured I am just expecting more out of the partition editors coz I have used Partition Magic (and other programs) to do these tasks while in Windows. I would not even mind if the Ubuntu apps told me it could finish the tasks without a reboot and did so out of Ubuntu... it just doesn't give me the option.

OK, so the answer is to boot with a disc that can handle this task. Or use Partition Magic, hehe!

---

### Post by edm1 on 2007-12-09
Last time i used partition magic on windows (well it was a few years ago) i couldnt edit a mounted drive. The mere concept of it is ridiculous, it'd be like trying to change the tyre on your car whiles someones driving it. Trying to run an application off a HD which isnt even mounted??? Which is why you need to use a [live CD]("http://gparted-livecd.tuxfamily.org/") as the application is running in the RAM.

---

### Post by wjp.reg on 2007-12-09
> **OzzyFrank said:**
> So... any answers to these questions, or just more questions (no offence... but does come across as you having fun at my ignorance). As for the questions about resizing the NTFS partition, sorry, I thought I made it abundantly clear in the first post what I was trying to do that for... to give space to the ext3 partition.

If what you are saying is you cannot do anything to your Ubuntu partition while using it, then that means that using Partition Magic in Windows is actually much easier, and that the partition editors in Ubuntu are basically useless... perhaps good for just deleting an NTFS partition (oh, OK, and for reszing unmounted partitions)? So I'd perhaps be laughing at the difference between doing simple tasks like this in Ubuntu and Windows.

Forgive my ignorance on this... as you may have figured I am just expecting more out of the partition editors coz I have used Partition Magic (and other programs) to do these tasks while in Windows. I would not even mind if the Ubuntu apps told me it could finish the tasks without a reboot and did so out of Ubuntu... it just doesn't give me the option.

OK, so the answer is to boot with a disc that can handle this task. Or use Partition Magic, hehe!

Sorry OzzyFrank; wasn't having fun with your misfortune and I hope you're having some luck in your silence.

gparted is just as good and arguably better than Partition Magic while there may be a learning curve as with all software.

cheers!

---

### Post by OzzyFrank on 2007-12-09
So you're saying all those times I swapped space between various partitons and filetypes while using Partition Magic in Windows on various computers... I was actually hallucinating?? Well, seems to have worked. But the mere concept of that is ridiculous, so I'm sorry but I'll have to go with "it worked".

---

### Post by OzzyFrank on 2007-12-09
> **wjp.reg said:**
> Sorry OzzyFrank; wasn't having fun with your misfortune and I hope you're having some luck in your silence.cheers!

That's OK, hehe... but I do see a lot of people in these forums who just basically come in to say "Don't you know how stupid you are??" than answer the damned questions... so I always expect the worse when posting here (unfortunately). But some people really don't feel much power in their lives, so who am I to intrude on their ego-boosting power trips?

Anyway, my point is this... since the 90s (or maybe beginning of this century) I've been able to open Windows apps for the tasks at hand, and if they couldn't finish a task while in Windows, they would reboot, do the task in DOS-Land, then boot back into Windows, all done. In Linux it seems this isn't possible.

I am not asking that Linux apps change the way they work, just asking if there is an app that behaves like the Windows ones, ie says "Yeah, sure, no worries buddy... I can do that... but we're gonna need to reboot to do so". Obviously there is no work around, and looks like you guys are saying there is nothing like Partition Magic that takes all the pain out of it, so I'll have to reboot with a disc and do it. Cheers

---

### Post by schauerlich on 2007-12-09
> **OzzyFrank said:**
> That's OK, hehe... but I do see a lot of people in these forums who just basically come in to say "Don't you know how stupid you are??" than answer the damned questions... so I always expect the worse when posting here (unfortunately). But some people really don't feel much power in their lives, so who am I to intrude on their ego-boosting power trips?

Anyway, my point is this... since the 90s (or maybe beginning of this century) I've been able to open Windows apps for the tasks at hand, and if they couldn't finish a task while in Windows, they would reboot, do the task in DOS-Land, then boot back into Windows, all done. In Linux it seems this isn't possible.

I am not asking that Linux apps change the way they work, just asking if there is an app that behaves like the Windows ones, ie says "Yeah, sure, no worries buddy... I can do that... but we're gonna need to reboot to do so". Obviously there is no work around, and looks like you guys are saying there is nothing like Partition Magic that takes all the pain out of it, so I'll have to reboot with a disc and do it. Cheers

When you reboot and go into "DOS-Land" to finish the task, you're unmounting the Windows partition so you can mess with it.

---

### Post by AgentZ86 on 2007-12-09
> **OzzyFrank said:**
> So you're saying all those times I swapped space between various partitons and filetypes while using Partition Magic in Windows on various computers... I was actually hallucinating?? Well, seems to have worked. But the mere concept of that is ridiculous, so I'm sorry but I'll have to go with "it worked".

Windows is a bit different that is why every time you change something while using windows, including the partition space etc. it asks you to reboot the system all day long. Because the changes don't get completed until the drive gets unmounted and the new partitions is activated on soft-reboot. But if you turn off the computer the new partition will many times not even get created without a soft-reboot similar to the fdisk utility which was windows/dos main source of partitioning, that required a soft-reboot in order for the partition to become active and bootable.

So in order for a partition to become active and bootable typically requires a soft-reboot unless there is some new type of partitioning tools out there that no long need to do this.

Gparted, Partition Magic either way I've used them all, WD diag and several others as well. Basically all work about the same.

However, I've not heard of any problems like this for Gparted from the Live CD or Ubuntu from the Live CD, and you can surely resize,partition/repartition,format etc. from the Gparted Live CD, Partition Magic CD, and many of the utilities that comes with your hard drive will do this as well, but many of them also boot from a floppy or CD not from the hard drive in order to accomplish this. And they all still require a soft-reboot to my knowledge.
Anyhow Gparted or Ubuntu Live is so simple I don't understand why there would be any problem using this utility to do a simple resize, since you will have to restart the computer anyhow in any case. Also Gparted does have the ability to copy your partitions and paste them to another partition if desired etc. Like if you want to copy a partition to another hard drive and them resize your partitions then past your copy back to your origin again if you want. Very simple to use. But still requires a re-boot as usual.

Well I hope this helps. and FYI Gparted is free GPL and Partition Magic is not unless you have a bootleg copy or something that came with your hardware or OS etc. 

Well happy hacking.

---

### Post by OzzyFrank on 2007-12-09
**AgentZ86**: Good, informative answer!!

Still means we need an idiot-proof app like PM that will do it with the soft-boots or whatever [COLOR="Red"]without you needing to know about unmounting etc[/COLOR]... which means a total newbie to partitioning could do it and not have to spend time just to find out they need a boot disc to do it.

So please note all I am aware that PM has to unmount etc etc etc... but it is idiot proof in that anyone can do it. Note all that I am **not saying that I cannot do it with a live or boot CD**... the original question was if there was a way to do this in the apps mentioned _while in Ubuntu_ (OK, the answer is a resounding NO, I get it!!) or if there was another app more like PM.

The reason I could not use a CD to partition my friend's PC was coz I didn't have one with me. So i went to use the installed apps, thinking they would do like PM, but no go. So maybe I should have put it as[COLOR="#ff0000"]**_ Is there any way to do it WITHOUT a boot disc_**[/COLOR]? Hope this puts it more into perspective, and that all can see I am not asking "Why can't I do it?" but "Can I do it without a boot disc... like with PM in Windows". Hope you guys see what I mean now. Cheers

---

