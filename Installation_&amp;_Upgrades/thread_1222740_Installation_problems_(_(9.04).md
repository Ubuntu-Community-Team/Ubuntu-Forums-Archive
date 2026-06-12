---
title: "Installation problems :( (9.04)"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by Chrisname on 2009-07-25
I just installed Ubuntu alongisde Windows Vista, which I'm running now.

I have a few issues on installation, though.

Firstly that GRUB is now the default boot loader. I would rather not use GRUB. I prefer the simple bootloader which defaults with Windows. Probably just because it's familiar. I don't mind switching, really (I'd rather not though); but I also share this machine with three other people who would stare at you blankly at the mere mention of an operating system other than Windows.

What is worse, however, is that upon booting my machine; I'm confronted with eight different boot options. Three for Ubuntu (ubuntu, memtest, etc.), three for "Vista Loader" and two for Vista that I added to menu.lst after reading something on these forums. I'm on Vista at the moment, because I was going to play around in EasyBCD and see what I could do; but it can't edit GRUB, unfortunately. The rest of the people who are going to be using this machine are unlikely to enjoy the prospect of having to pick an option out of eight in ten seconds, or be booted into an unfamiliar OS on which they do not have accounts, and cannot gain access to. When I try to boot Vista (which I'm on right now), I'm asked to run CHKDSK. I allowed it to run once (it took about ten minutes); and rebooted, however it's asking me to run it again. I ignored it, and that's how I came to be on Vista now.

Sorry for the wall of text; in short:
I just installed Ubuntu on a seperate partition with Windows running. I don't want to use GRUB because it's unfamiliar and because my parents, both over the age of fifty, have never used anything other than Windows and it's bootloader. Then there's the issue that there are simply too many options. I know which one to pick, but there are eight; and only ten seconds to pick one in. If I choose Ubuntu it loads fine, if I choose Vista, I've got to cancel CHKDSK before I can boot.

So, can I use Ubuntu without GRUB; and how can I do so? Also how can I sort out this issue with Vista and CHKDSK (I know this is an Ubuntu forum, but it's related to Ubuntu as it occurred after I installed it. I'm not blaming Ubuntu though; it was almost certainly my fault), I will probably have to reinstall Windows, but I'd rather not. Is there a fix for these issues?

Also, strangely, the last time I booted Ubuntu; when I shut the system down, the speaker (the speaker built-in to the motherboard) went crazy, emitting loud beeps. The only knowledge I have of the system speaker is that it's usually used for a POST failure; so why it would be used when the system is shutting down doesn't make any sense to me.

Thanks, and apologies if I haven't worded my question very well.

Other than the above, I love Ubuntu. I've been using Mint for the last couple of weeks; but on a recommendation from a friend, I switched to Ubuntu. Needless to say I'm quite annoyed, but as I say, it's most probably my own fault. I'd rather continue to use Ubuntu if I can get these issues fixed; as opposed to format the partition again.

I have used the "Check if Already Posted" button and none of the results seemed relevant, sorry if this has already been resolved, but I **have** checked...

Thanks again.

I'm on Ubuntu now; so if there are any terminal commands I need to run, I'll be able to run them.
Hopefully without the lovely motherboard screaming at me.

Update:
I just discovered that it **wasn't** a very good idea to format the partition with Ubuntu on it. Now I can't even load windows. I'm using the live CD; but hopefully I can fix this. I guess that's a lesson learned...

---

### Post by mikewhatever on 2009-07-25
That's a lot of text, so I'll try and answer at least some of the questions.

Grub is the boot loader Ubuntu users, which allows you to boot either Ubuntu or Windows. It can be easily configured to boot either OS by default without timeouts and showing the boot menu. It's also easy to get help with GRUB around here. You can use a different boot loader, anything you like, in fact, but then you should be comfortable with configuring it to your liking.

Windows is asking for the disk check because one of the partitions got changed, probably when you resized it while installing Ubuntu. Let it run and finish, even tough it may take some time.

> Update:
I just discovered that it wasn't a very good idea to format the partition with Ubuntu on it. Now I can't even load windows. I'm using the live CD; but hopefully I can fix this. I guess that's a lesson learned...

You need a boot loader to load an OS. Either will do, but since you removed Ubuntu, restoring the Windows boot loader is a logical step. I am not familiar with Vista, but here are some results from a google search:
[http://www.pronetworks.org/forums/how-to-restore-vista-boot-loader-t76643.html](http://www.pronetworks.org/forums/how-to-restore-vista-boot-loader-t76643.html)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Chrisname on 2009-07-25
> **mikewhatever said:**
> That's a lot of text, so I'll try and answer at least some of the questions.

Grub is the boot loader Ubuntu users, which allows you to boot either Ubuntu or Windows. It can be easily configured to boot either OS by default without timeouts and showing the boot menu. It's also easy to get help with GRUB around here. You can use a different boot loader, anything you like, in fact, but then you should be comfortable with configuring it to your liking.

Windows is asking for the disk check because one of the partitions got changed, probably when you resized it while installing Ubuntu. Let it run and finish, even tough it may take some time.



You need a boot loader to load an OS. Either will do, but since you removed Ubuntu, restoring the Windows boot loader is a logical step. I am not familiar with Vista, but here are some results from a google search:
[http://www.pronetworks.org/forums/how-to-restore-vista-boot-loader-t76643.html](http://www.pronetworks.org/forums/how-to-restore-vista-boot-loader-t76643.html)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
Thanks.

Incidentally I was going to reinstall Ubuntu so that I could at least get GRUB back and boot into Windows; then restore BCD.

The issue with Windows trying to run the check disk program was that I rebooted immediately after running it; and it asked to run it again. So I did, and rebooted again, and it asked to run it again, so I cancelled and skipped straight to boot.

I've sorted out worse problems on this machine; just never with an unfamiliar OS...

But once I get it all figured out I plan to use Ubuntu. It's a good OS; I'm on the LiveCD now.


Also, as I got my current PC from an OEM; I don't have a restore disk (>:() and instead I have a "recovery" partition. Which is useless without a bootloader. So I'm reinstalling GRUB because I found out a few commands to overwrite the MBR using recover.

And sorry for the massive amount of text. I'm not one who is quite able to word things in four words where four hundred would do.

Right so I restored Windows by installing Ubuntu, booting into Windows through GRUB, and using EasyBCD to rewrite the MBR. So now all that's left is to reinstall Ubuntu (I formatted the partition) inside a VM. I'm not going to go through that again for a little while...

Thanks for your help :)

---

### Post by mikewhatever on 2009-07-25
Just in case you ever try Ubuntu or another Linux distro, search for a guide to follow. There is actually a proper way of resizing Vista's partitions.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

