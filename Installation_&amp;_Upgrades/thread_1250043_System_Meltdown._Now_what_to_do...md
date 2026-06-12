---
title: "System Meltdown. Now what to do..?"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Thanh-BKK on 2009-08-26
Hello.

I was happily browsing the web when suddenly Swiftfox decided to hang (in fact i just praised Ubuntu on this forum mere minutes earlier). I closed it (it closed normally) and restarted it and upon that restart it acted like it had just installed all the add-ons, i.e. no configuration was saved. During re-configuring those add-ons Swiftfox became extremely sluggish and almost stayed grey all the time. I closed it again (again it closed normally after some time) and tried it again - same.

I then shut down the machine and restarted it - which is when the trouble REALLY started, the disk checker came up and got stuck at 3%, dumping me to a terminal-like screen..... there it said "run fsck manually" so i did, i had no idea the drive needs to be unmounted etc......

End of the story, i did that a few times, at some stage i was able to actually boot and get into my account alright, all files were where they were supposed to be but the icon theme had changed and the system ran extremely sluggish..... further reboots sometimes the computer didn't find either one of the HDD's...... 

What i could determine is that all corruption seems to be on /dev/sda6 which is my "home" partition (as fsck only complains about that partition). 

Now i am still not sure if it is my HDD that just died or the mainboard (or rather the IDE controller, as booting from the CD which is a SATA drive still works fine) so i am going to replace them both.

But i would like to know if there is any way of rescuing my obviously damaged "home" partition..? In case the HDD is still is still ok, that is. Because i REALLY don't want to have to go through a re-install of OS including all the apps (a TON of them!) including all the customizations, configurations etc. 

I would highly appreciate any advice on this issue as it effects my production computer. 

Kind regards.....

Thanh

---

### Post by dstew on 2009-08-26
It sounds like the partition has become corrupted, possibly from a disk hardware fault. You can try to copy files from the partition, and maybe you will get some. But, to get your installed programs off, that would be harder, since it is not a matter of copying files from one partition. As you know, installed programs have pieces all over the place, such as scripts, binarys, and configuration files, which will be in your root partition, in a variety of directories.

You could try making an .iso (image) of your /home partition, using partimage or another program like that. Of course, it will copy the bad sectors along with the good. Maybe it would be better to try to copy files.

Did you exhaust all attempts at repairing the partition? If you boot a Live CD, and then try```
sudo fsck /dev/sda6
```what output do you get?

---

### Post by Thanh-BKK on 2009-08-26
Hi.

Yeah i exhausted all possibilities there... i did that with the live-CD and all i got was a never0-ending array of I/O errors, DDY (or something like that) errors and "failed to read block xxxx". I guess it must be an HDD failure (hardware).

I have swapped the HDD and am in fact typing this from a fresh install of Ubuntu 9.04 Jaunty, IF my system destroys itself like that i can as well go for the current version of Ubuntu, LTS or not...... now i am going through the nightmare of re-installing my billion apps and getting my desktop to look like before (of course the icon theme i used before is not compatible with Jaunty, AAAARGH!!!) 

And i have to get back to the very beginnings and try to remember.... "how did i get my four data partitions to auto-mount..?" and "how did i get the transparency in those window frames..?" and "how did i get shortcuts to folders on the desktop..?"

Oh well.... one thing for sure, as soon a this is running and configured again i WILL clone that HDD to have an identical one for backup! I did that with the data drive all the time which is why THAT one did NOT die. The only one to die MUST be the one without a backup. As always.

Best regards.....

Thanh

---

