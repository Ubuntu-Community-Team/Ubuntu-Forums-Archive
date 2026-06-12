---
title: "Really scared about partitions, HELP!"
date: 2008-11-16
forum: General Help
---

### Post by The_Lost_World on 2008-11-16
Alright. So I had a C: and D: partition on my Windows laptop, and I know that's useless for double-booting Ubuntu, so I deleted my D: partition, but it still says I only have 60 or so GB of space on my C: partition (which is what I have Windows Vista installed on). I understand that there is some unallocated space on my hard drive now, so how do I get that unallocated space onto by C: drive?

I hope I didn't make a mistake by deleting that D: drive... :confused:

Thanks so much for your help!

---

### Post by Marius Derekus on 2008-11-16
Wait one minute, I think i can help.

---

### Post by tuxxy on 2008-11-16
Maybe you need to expand the partition with the new space you created.

---

### Post by DGortze380 on 2008-11-16
> **The_Lost_World said:**
> Alright. So I had a C: and D: partition on my Windows laptop, and I know that's useless for double-booting Ubuntu, so I deleted my D: partition, but it still says I only have 60 or so GB of space on my C: partition (which is what I have Windows Vista installed on). I understand that there is some unallocated space on my hard drive now, so how do I get that unallocated space onto by C: drive?

I hope I didn't make a mistake by deleting that D: drive... :confused:

Thanks so much for your help!

Are you trying to dual boot or no?

---

### Post by jflaker on 2008-11-16
OK....I hope you didn't have anything on that D: partition you needed.  Though, it was likely a factory restore partition

Since D: is gone, you might as well use the free space.

Since you can't change partitions that are currently in use, Boot the Ubuntu live CD and then go into SYSTEM>ADMINISTRATION>PARTITION EDITOR, then stretch the partition to the remainder of your disk.  Save your changes and reboot without the CD and now windows should have much more space!

I must warn you, BE CAREFUL as you can as easily delete your partition

---

### Post by melojo on 2008-11-16
> **The_Lost_World said:**
> Alright. So I had a C: and D: partition on my Windows laptop, and I know that's useless for double-booting Ubuntu, so I deleted my D: partition, but it still says I only have 60 or so GB of space on my C: partition (which is what I have Windows Vista installed on). I understand that there is some unallocated space on my hard drive now, so how do I get that unallocated space onto by C: drive?

I hope I didn't make a mistake by deleting that D: drive... :confused:

Thanks so much for your help!

I am a little confused of what you want?

You deleted your d: partition, the space is their you just are not using it.  If you want to increase c: to use the space from d: that you deleted you need to resize the partion.  You could do this with the ubuntu cd or through windows.

---

### Post by CatKiller on 2008-11-16
You can install Ubuntu into the free space that you created by deleting that partition (your D: drive). You don't need to mess with the C: partition at all, unless you particularly need it to be bigger for Windows.

---

### Post by The_Lost_World on 2008-11-16
Wow, that was really fast! Thank you. ^_^

I'm going to do what jflaker said.

Yes I am trying to double boot.

Speaking of which, could anyone show me how to double boot, like what do I need to do with my partitions and etc? I want to keep my Windows as well, lol.

---

### Post by CatKiller on 2008-11-16
> **The_Lost_World said:**
> I'm going to do what jflaker said.

Yes I am trying to double boot.

If you're dual-booting, you'll need that space to install Ubuntu into. Not necessarily all of it, but certainly some. So don't extend your Windows partition all the way.

> Speaking of which, could anyone show me how to double boot, like what do I need to do with my partitions and etc? I want to keep my Windows as well, lol.

I'd advise leaving the free space as it is, and selecting "Use largest free space" in the Ubuntu installer. That way you won't affect your Windows partition at all. You'll get two new partitions, one for the Ubuntu install itself, and one for swap space.

The installer will automatically sort out your dual-boot for you, by installing a boot-loader (called GRUB) onto your hard drive that will give you a menu to select whether you want to boot into Windows or into Ubuntu.

---

### Post by The_Lost_World on 2008-11-16
> **CatKiller said:**
> If you're dual-booting, you'll need that space to install Ubuntu into. Not necessarily all of it, but certainly some. So don't extend your Windows partition all the way.



I'd advise leaving the free space as it is, and selecting "Use largest free space" in the Ubuntu installer. That way you won't affect your Windows partition at all. You'll get two new partitions, one for the Ubuntu install itself, and one for swap space.

The installer will automatically sort out your dual-boot for you, by installing a boot-loader (called GRUB) onto your hard drive that will give you a menu to select whether you want to boot into Windows or into Ubuntu.
Wow, thanks CatKiller! That's incredibly easy, a lot easier than I thought it would be. ^_^ I think I will install my Ubuntu tomorrow, and I'll come back here to tell you all if it worked out okay. =D

---

### Post by CatKiller on 2008-11-16
Don't forget to back up any important data from your Windows partition, in case you do inadvertently do anything to your Windows partition. The chances that you'll need to use your backup are remote, but if you don't have one and find that you do need it then you'll kick yourself.

---

### Post by The_Lost_World on 2008-11-17
I have my files backed up. I'm going to install, but should I have a restore CD for Windows ready first? I hope I can find another writable DVD, if so, lol. Or do you think it's too much trouble for the small chance of anything happening?

---

### Post by Deathray on 2008-11-17
> **The_Lost_World said:**
> I have my files backed up. I'm going to install, but should I have a restore CD for Windows ready first? I hope I can find another writable DVD, if so, lol. Or do you think it's too much trouble for the small chance of anything happening?

As long as you select "Install to largest continuous free space available" you should have no fear of any data being deleted as this will not happen! :)

Just make sure that you completely deleted the partition in Windows by right clicking Computer, selecting Manager. Go to Disk Management and delete D: until you can verify that it is actually "Un-allocated space".

---

### Post by CatKiller on 2008-11-17
> **The_Lost_World said:**
> I have my files backed up. I'm going to install, but should I have a restore CD for Windows ready first? I hope I can find another writable DVD, if so, lol. Or do you think it's too much trouble for the small chance of anything happening?

It depends entirely on how much better it will make you feel :)

Good luck!

---

### Post by The_Lost_World on 2008-11-17
Yea, it's totally unallocated. ^_^ Thanks, I think I will install now, I'll be back and tell you if all is well. ^_^

---

### Post by Deathray on 2008-11-17
Great now you're prepared. Good luck! We'll be here to help if necessary! :)

---

### Post by The_Lost_World on 2008-11-17
Uh oh. 

I did everything right but in the middle of install (22%) it said that I might have a bad CD/Disk Drive/Hard Disk or something and it canceled. It also said I might wanna move my system to a cooler location.

What's going on?

---

### Post by The_Lost_World on 2008-11-18
Perhaps I should just clean the CD (did that already) and retry? Can't hurt anyways.

---

### Post by DGortze380 on 2008-11-18
> **The_Lost_World said:**
> Uh oh. 

I did everything right but in the middle of install (22%) it said that I might have a bad CD/Disk Drive/Hard Disk or something and it canceled. It also said I might wanna move my system to a cooler location.

What's going on?

Sounds like you've got a bad CD or are overheating.

---

### Post by The_Lost_World on 2008-11-18
A bad CD? Like scratched, or a bad ISO image or something?

I cleaned the disk and I'll keep my laptop cooler and retry I guess. It was really hot.

---

### Post by CatKiller on 2008-11-18
> **The_Lost_World said:**
> Uh oh. 

I did everything right but in the middle of install (22%) it said that I might have a bad CD/Disk Drive/Hard Disk or something and it canceled. It also said I might wanna move my system to a cooler location.

What's going on?

I've never seen this before, but hard drive temperature checks are part of the SMART checks. I guess that these were triggered during the operation, and the process cancelled to prevent data corruption.

Moving partitions around is quite an intensive operation, and hard drives can generate quite a bit of heat when they're working. I guess general precautions apply about ventilation and not using by the oven.

---

### Post by DGortze380 on 2008-11-18
> **The_Lost_World said:**
> A bad CD? Like scratched, or a bad ISO image or something?

I cleaned the disk and I'll keep my laptop cooler and retry I guess. It was really hot.

If it was that hot, then that's probably your issue.

Bad cd as in scratch or incorrect checksum. Install cd's provide an option to check the disc if I remember correctly.

---

### Post by The_Lost_World on 2008-11-18
Oh, just great.

I go in to retry and it doesn't even have the option for "use largest free space" anymore. Just "Manual", "Erase Entire Disk", and "Resize" or something, the resize has a slider for "sda(0, 0, 0)" I think it said. I'd be willing to bet this is because I already tried to install once and it sees this space as not unallocated. Anyways the slider can choose to use more or less of about 60 GB which is half my hard drive, probably the half I wanna use.

So should I give it the maximum space and install?

By the way, DGortze, how would I do that CD check?

---

### Post by DGortze380 on 2008-11-18
> **The_Lost_World said:**
> Oh, just great.

I go in to retry and it doesn't even have the option for "use largest free space" anymore. Just "Manual", "Erase Entire Disk", and "Resize" or something, the resize has a slider for "sda(0, 0, 0)" I think it said. I'd be willing to bet this is because I already tried to install once and it sees this space as not unallocated. Anyways the slider can choose to use more or less of about 60 GB which is half my hard drive, probably the half I wanna use.

So should I give it the maximum space and install?

By the way, DGortze, how would I do that CD check?

Should be an option at the first screen when you boot the cd to check it for errors.

As far as installing.

Choose manual.

Leave you Windows partition alone.
Delete any extra partition you may have created previously.
Out of the free space available create two partitions.

ext3  for  /
swap  for swap (must be 1.5x the amount of RAM you have)

continue with your install.

---

### Post by CatKiller on 2008-11-19
> **The_Lost_World said:**
> Oh, just great.

I go in to retry and it doesn't even have the option for "use largest free space" anymore. Just "Manual", "Erase Entire Disk", and "Resize" or something, the resize has a slider for "sda(0, 0, 0)" I think it said. I'd be willing to bet this is because I already tried to install once and it sees this space as not unallocated. Anyways the slider can choose to use more or less of about 60 GB which is half my hard drive, probably the half I wanna use.

So should I give it the maximum space and install?

By the way, DGortze, how would I do that CD check?

I think you're correct, that it made the partitions before it halted. You can delete the new ones the same as you did the old D: drive, and then continue as before using the largest continuous free space option.

The resize option has probably picked your Windows partition by default, since that's the first partition on the drive. There is likely to be an option to pick a different one to resize. In your case, though, you don't need to touch that partition.

You do also have the option of using the existing partitions that were created during the aborted install. But since you'll be formatting them anyway, you might as well nuke them and let the installer recreate them automatically. There might conceivably be something wrong with them, depending on exactly where in the process the halt happened.

You can manage partitions in the installer itself, or by running System -> Administration -> Partition Editor from the live cd before you start the install again.

If you find that the swap partition has been mounted to be used by the live cd - meaning that it can't be changed - you can open a Terminal at Applications -> Accessories -> Terminal and type ```
sudo swapoff -a
``` to unmount it.

---

### Post by The_Lost_World on 2008-11-19
....

Okay, it had the same error, again. I did everything you guys said (and the thing that would get rid of the old partitions and use the freed space worked) but same error. I think I have a bad CD and I have no idea why, and no, there is not "check CD" option at the boot screen.

---

### Post by The_Lost_World on 2008-11-19
Perhaps I should simply burn another disk? I have plenty.

---

### Post by The_Lost_World on 2008-11-20
Meh, this disk has a couple scratches, I guess I'll just make another.

---

