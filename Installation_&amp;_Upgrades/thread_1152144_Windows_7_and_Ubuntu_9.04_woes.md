---
title: "Windows 7 and Ubuntu 9.04 woes"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by XPM on 2009-05-07
I installed Ubuntu 9.04 x64 first, then the windows 7 RC.

Recovered grub and it worked.
Although if I booted windows 7 it would automatically REWRITE the MBR.

So, I tried to install the Acronis OS selector.

It worked the first time (boot into linux)
But when I booted into windows and rebooted, acronis would not load and windows 7 would automatically start up.

What gives and how can I fix this?
It's so annoying!

---

### Post by XPM on 2009-05-07
Sorry for bumping but I am REALLY impatient.
I don't wan't to be a douche about it...I just miss linux alot :)

---

### Post by XPM on 2009-05-07
This is the last time I'm asking for help.
I get no help, and for those who cannot answer, I get no directions or anything

I've had 3 computers with these problems in the past so I know I must not be alone.
Thinking about getting rid of it all together.
I wont reinstall grub for every boot.
Thanks for nothing.
This isn't the first time I've asked for help with no replies.
If there was a form about how useful one would find the forum my score would go 0.

---

### Post by Mark Phelps on 2009-05-08
So MS Windows seven keeps messing up your machine -- how is that a Linux or Ubuntu problem?

Acronis OS Selector is an MS Windows product -- and it apparently doesn't work.  Again, how is that a Linux or Ubuntu problem?

What part about this being the "Ubuntu forums" don't you get?

Your impatience is not OUR problem.  Polite behavior around here is to bump no more often than once every 24 hours, not twice in 8 hours!

---

### Post by gta117 on 2009-05-08
> **Mark Phelps said:**
> So MS Windows seven keeps messing up your machine -- how is that a Linux or Ubuntu problem?

Acronis OS Selector is an MS Windows product -- and it apparently doesn't work.  Again, how is that a Linux or Ubuntu problem?

What part about this being the "Ubuntu forums" don't you get?

Your impatience is not OUR problem.  Polite behavior around here is to bump no more often than once every 24 hours, not twice in 8 hours!

Hey man, I can understand his impatience, while I am not justifying it, I do feel it. You are right yes. 


But when you have Mothers day on the line like me, and a few other things, it soon becomes a race against time. ;) Anyways, Its all good man, thanks for the reminder.


As for me, if it is so appropriate, it would be great if you might be able to help me out at all. I figured a 2 line request might not hurt, even if its a lil off topic. ;)

-gta117

---

### Post by Mark Phelps on 2009-05-08
> **gta117 said:**
> Hey man, I can understand his impatience, while I am not justifying it, I do feel it. You are right yes. 


But when you have Mothers day on the line like me, and a few other things, it soon becomes a race against time. ;) Anyways, Its all good man, thanks for the reminder.


As for me, if it is so appropriate, it would be great if you might be able to help me out at all. I figured a 2 line request might not hurt, even if its a lil off topic. ;)

-gta117

I'm not getting into an argument with you.  Fact of the matter is, this is NOT an MS Windows support forum.  While many of us DO use MS Windows, and we do provide some support when we can, it's unreasonable to come here and expect us to fix a Windows 7 problem within a few hours of the posting.  And then, to complain repeatedly after that about no respone -- well, that's just not the way to treat those of us who volunteer our precious little free time to help folks out.

The time spent complaining about lack of response could have been better spent finding solutions in forums more appropriate to the problems. 30 seconds of Googling would have turned up the Windows 7 forum -- where such issues are more likely to get immediate attention.  Another 30 seconds of Googling would have turned up the Wilders Security Forum -- where issues related to Acronis products would have received immediate attention.

So, while I understand impatience, I have no sympathy for folks who come here with non-Linux, non-Ubuntu problems and then complain when we don't JUMP to solve their problems -- when they won't even spend a minute or two trying to find a more appropriate tech forum.

---

### Post by Wiebelhaus on 2009-05-08
That's because windows seven is stupid , you have to install Win7 first on primary hard drive and Ubuntu second on secondary hard drive and use grub which handles the job effortlessly.

---

### Post by florus on 2009-05-08
@sx66gns Please can you confirm - are you saying that to dual boot with Windows7 you need two hard drives? :confused:

---

### Post by XPM on 2009-05-08
I fixed it by letting acronis boot grub and grub booting windows from there

---

### Post by jmrasor on 2009-05-08
I'm triple-booting Ubuntu, WinXP, and Windows 7.
I first installed WinXP years ago, and have done the updates.
I first installed Ubuntu Hardy months ago, and have done the updates. Now running Jaunty.
I installed Windows 7 yesterday. Brief procedure:
1.  Used Gparted to shrink a partition on one of my drives. Got 58 GB unallocated space that way. Gparted is slow, but got the job done.
2.  Installed Windows 7. It saw the unallocated space, and easily installed there.
3.  As with other versions, Windows 7 took over the boot loader. On finishing installation, the reboot offered both Windows 7 and the earlier version, WinXP. Both worked. No boot to Ubuntu possible.
4.  I booted with rescuecd, a Gentoo derivative. Ran grub find /boot/grub/stage1: it was at (hd2,0). Your (hdX,Y) will probably be different. Ubuntu installer CD could not get this; neither could installed Ubuntu before the Windows 7 installation.
5.  Then, still in grub, ran root (hd2,0), then ren setup (hd0). That restores GRUB as the bootloader. Thanks to Simple Thoughts [http://blog.taragana.com/index.php/archive/how-to-dual-boot-windows-7/](http://blog.taragana.com/index.php/archive/how-to-dual-boot-windows-7/) for this.
6.  Reboot. Grub presented the usual choices, Ubuntu or WinXP. On choosing WinXP, I got the Windows boot loader, offering WinXP and Windows 7. Both worked.
7.  I rebooted to Ubuntu, and changed the title of the Windows XP Professional choice to just plain Windows.
8.  I rebooted to Ubuntu, and to the two Windows versions. All worked.

---

### Post by XPM on 2009-05-08
Thing is... Everytime i rebooted after having restored grub..everything worked peachy.

Until I booted windows 7
It wrote over the MBR for some bizarre reason

So after I had used windows 7 (every time) I had to reboot to the live cd and restore grub.

---

### Post by coffeecat on 2009-05-08
> **XPM said:**
> Thing is... Everytime i rebooted after having restored grub..everything worked peachy.

Until I booted windows 7
It wrote over the MBR for some bizarre reason

So after I had used windows 7 (every time) I had to reboot to the live cd and restore grub.

Yes, that is very bizarre. I'm posting from Windows 7 (RC) at the moment, on sda1 on a multiboot with various versions of Ubuntu and other distros on logical partitions (sda6 upwards). All I can say is that Windows 7 is **not** overwriting the MBR each time I boot up. I get the grub menu (from Jaunty) each time.

I doubt whether this is a built-in feature of W7, and I'm at a loss to understand how your install is replacing the MBR each time. Very odd. Apart from Acronis OS selector, do you have any other Windows hard disc utilities installed?

---

### Post by scottuss on 2009-05-08
> **Mark Phelps said:**
> I'm not getting into an argument with you.  Fact of the matter is, this is NOT an MS Windows support forum.  While many of us DO use MS Windows, and we do provide some support when we can, it's unreasonable to come here and expect us to fix a Windows 7 problem within a few hours of the posting.  And then, to complain repeatedly after that about no respone -- well, that's just not the way to treat those of us who volunteer our precious little free time to help folks out.

The time spent complaining about lack of response could have been better spent finding solutions in forums more appropriate to the problems. 30 seconds of Googling would have turned up the Windows 7 forum -- where such issues are more likely to get immediate attention.  Another 30 seconds of Googling would have turned up the Wilders Security Forum -- where issues related to Acronis products would have received immediate attention.

So, while I understand impatience, I have no sympathy for folks who come here with non-Linux, non-Ubuntu problems and then complain when we don't JUMP to solve their problems -- when they won't even spend a minute or two trying to find a more appropriate tech forum.


+1, don't fetch Windows problems here. I bet any money that if I posted "I have a problem with Ubuntu blah blah blah" on a Microsoft forum I'd get shunned. You may have gotten some help without the scorn if you hadn't bumped the posts so soon! It's just rude! :mad:

---

### Post by coffeecat on 2009-05-08
> **scottuss said:**
> +1, don't fetch Windows problems here.

The OP is dual-booting Windows 7 and Ubuntu. For some inexplicable reason, Windows 7 is interfering with grub and therefore with the OP's enjoyment of Ubuntu. It seems to me therefore a perfectly valid reason to post about this issue on this forum. Futhermore, Windows 7 RC was only released three days ago and will be available for free download and use until the end of July, which means that more and more people are going to be using it with Ubuntu. So, if this is a "feature" of Windows 7, then we are going to be seeing more of this problem. Therefore it is entirely reasonable to discuss this here and now.

Or have you simply let your irritation at the OP's initial impatience get the better of you?

---

### Post by florus on 2009-05-08
OK, so XPM bumped too often. Perhaps this could have been brought to his attention in a less confrontational manner. To a newby to the forums, seeing a query receding through pages 5...6...7... means it may never get a reply. We are supposed to be a friendly community that encourages inexperienced converts.

---

### Post by scottuss on 2009-05-08
> **coffeecat said:**
> The OP is dual-booting Windows 7 and Ubuntu. For some inexplicable reason, Windows 7 is interfering with grub and therefore with the OP's enjoyment of Ubuntu. It seems to me therefore a perfectly valid reason to post about this issue on this forum. Futhermore, Windows 7 RC was only released three days ago and will be available for free download and use until the end of July, which means that more and more people are going to be using it with Ubuntu. So, if this is a "feature" of Windows 7, then we are going to be seeing more of this problem. Therefore it is entirely reasonable to discuss this here and now.

Or have you simply let your irritation at the OP's initial impatience get the better of you?

But the OP is using a boot manager that is nothing to do with Ubuntu, is using pre-release (Microsoft) software and was then very rude about not getting any help, what is to be expected? I stand by my point that if I had done the same on a Microsoft forum, I would have had a similar response.

I don't want to sound un-friendly to new users but demanding help with things that are nothing to do with Ubuntu, then bumping and *then* replying with a rude follow up post, nah I'm sorry but that does need making a point of. It's rude!

---

### Post by caljohnsmith on 2009-05-08
> **XPM said:**
> This is the last time I'm asking for help.
I get no help, and for those who cannot answer, I get no directions or anything

I've had 3 computers with these problems in the past so I know I must not be alone.
Thinking about getting rid of it all together.
I wont reinstall grub for every boot.
Thanks for nothing.
This isn't the first time I've asked for help with no replies.
If there was a form about how useful one would find the forum my score would go 0.
Please keep in mind, XPM, that all forum members and Ubuntu forum staff who help here in the forums are volunteering their time, including myself, so you are not "entitled" to any sort of help. If you want people's help, please be patient and considerate, because rudely complaining that no one is helping you will certainly not motivate people to come to your aid. Also, please observe the [Forum Do's and Don'ts]("http://ubuntuforums.org/showthread.php?t=885580") and don't bump your thread sooner than every 24 hours. 

Even though you have a dual-boot setup between Ubuntu and Windows, it is not a Ubuntu problem if Windows for some reason constantly overwrites the MBR, so you should not expect help with that type of problem in the Ubuntu forums. Yet if you ask questions about a non-Ubuntu problem like you did in a considerate manner in these forums, often someone will help you anyway, including myself; since we realize that many Ubuntu users dual-boot with Windows, we often answer strictly Windows-related problems/questions anyway, but not for anyone who is less than considerate.

This thread is now closed.

Regards,
John

---

