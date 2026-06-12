---
title: "Help with harddrive"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by tocky on 2006-11-27
Hi!

I've got a problem with my s-ata, harddrive. First when I tried to install it with dapper drake, ther insallation was completed and there were no problems at all, except when I was about to boot up the computer. Then I got the message, Grub stage 1.5 harddisk error. Happened everytime, so I thought that I would give it a shot, when edgy eft comes out with a more up to date kernel. However before I start the install I want to check with you guys if you know what might be the problem, and if you know it will work or not.

My PC

AMD XP 2600+ Barton Core
Epox 8k9a7i
768 mb ram, pc3200
80 gb s-ata hitachi.

Is it the harddrive that is the problem of the via chipset maybe, can't handle the drive with linux. Works flawless with Windows though.

Here are some screens on my harddrive in the Disks Manager menu.(I've read somewhere that if it shows up in this menu, it ought to work under ubuntu)

[[IMG]http://images6.theimagehosting.com/Screenshot.bab.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot.bab.png)

[[IMG]http://images6.theimagehosting.com/Screenshot-1.2a9.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot-1.2a9.png)

By the way, if this turns out not to be working, can you recommend a drive that works. I was thinkin on Samsung 250gb, since it has had some great reviews.

---

### Post by tocky on 2006-12-02
I think I have found the problem, when I enter System > Administration > Disks, I'll see that my harddrive doesn't have a access path. However I tried to give it an access path, /home, and it worked, so I restarted the system wihout the live-cd, but still I get the same error, "Grub Harddisk error Stage 1.5"

Recent discoveries unveield that in my filesystem under the boot directory there's no grub. Wonder why though, and it seems that I cant install/make one either.

Someone knows how to solve this problem?

---

### Post by tocky on 2006-12-02
I think I've located the problem, it seems that I'm unable to set an access path for my harddrive, that will last after I reboot. I can do it under the live-cd, but as soon as I reboot it wont work, and linux can't boot from the harddrive.

Any1 knows how to fix this, I've experimented with fstab and other stuff but I can't make it work, please help.

Thanks in advance

---

