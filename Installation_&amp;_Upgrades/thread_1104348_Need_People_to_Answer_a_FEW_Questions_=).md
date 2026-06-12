---
title: "Need People to Answer a FEW Questions =)"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Jjkul1 on 2009-03-23
Ok so I love Ubuntu. I have the live CD and I have been trying it out for 2 months. Now i definitely want to install it to my harddrive. Now my hard drive is ok. It has a fault on the 10Gb partition called D:\ (the computer used to freeze when i tried to access it, but what I did is try to format it and in the middle of the formatting process everything froze solid so the D:\ drive won't operate until it is formatted correctly) but it is not going to be involved as I am going to cut off 23Gb from the 136 Gb C:\ and install ubuntu there. If there is any problem with that please tell me. Will the D:\ drive have any effect on C:\?

I am currently running Vista Ultimate on C:\ and it is very essential to me (because of school).

To the questions now:

1- What could go wrong in the process of partitioning and installation? What if it does?!?!?!? =( explain as fully as you can

2- Assume I have backed up my C:\ drive onto a harddrive. What should I do if the installation orpartitioning messes up?

3- What is a probability anything will happen? I know how to install but is it risky? I can't afford to lose Vista Ultimate as it is essential daily for my school work.

4- Would I be able to get Vista Ultimate back if it is deleted? I have the Home Premium installation CD but the upgrade to Ultimate was through the internet.

5- Will GRUB delete my Longhorn bootloader?

6- Where are extra programs and application installed in Ubuntu? Is it under the same partition as it is installed?

7- If i backup all data and my partition tables go wrong, what do I have to do? is it like plug in the media where i backed it up and boot from there? or should I get my harddrive formatted, restore windows?

Thanks. My laptop's specs:

150 Gb Harddrive
Core 2 Duo 2.4Ghz
3 Gb RAM
15.4 inch screen, 358Mb shared graphics chipset

If you would please give me detailed explanations and help. Thanks.

---

### Post by jfernyhough on 2009-03-23
> **Jjkul1 said:**
> 1- What could go wrong in the process of partitioning and installation? What if it does?!?!?!? =( explain as fully as you canYou could wipe your drive and all its data. Ideally you should take a backup, but in reality very rarely does anything go wrong.

> 2- Assume I have backed up my C:\ drive onto a harddrive. What should I do if the installation orpartitioning messes up?Assuming you used a piece of backup software, run it again and restore the image.

> 3- What is a probability anything will happen? I know how to install but is it risky? I can't afford to lose Vista Ultimate as it is essential daily for my school work.Low. But if in doubt, either try with just a Live CD or install to a USB hard drive. It works surprisingly well, and assuming you don't add any odd display drivers you can simply plug the drive into any PC, boot from it and bingo - you have the same setup ready to go. **Key point: If you can't afford to be without your PC, don't touch it. Seriously.** Been there, done that.

> 4 - Would I be able to get Vista Ultimate back if it is deleted? I have the Home Premium installation CD but the upgrade to Ultimate was through the internet.If you have an Ultimate key then yes, it's trivial (assuming you either have a retail DVD or can download one).

> 5- Will GRUB delete my Longhorn bootloader?Yes. But you will still be able to access Vista via a menu item in GRUB.

> 6 - Where are extra programs and application installed in Ubuntu? Is it under the same partition as it is installed?Normally, yes, all under the root (/) partition. You can change this if you set up (for example) /usr to mount in a different partition, but tbh you'll be hard pressed to fill 10GB with software (as long as you're discerning).

> 7- If i backup all data and my partition tables go wrong, what do I have to do? is it like plug in the media where i backed it up and boot from there? or should I get my harddrive formatted, restore windows?Insert the Windows DVD, boot from it, reformat, run the installer. Microsoft make it surprisingly easy to wipe your PC back to a fresh beginning. ;) Then restore your data. Or if it's a full drive image, just restore it according to your software.

**KEY POINT: Back up your important data. Not program files, but documents, save games, music, etc. etc. Anything you can't get back easily. Burn it onto a CD or two. Put it on a USB pen. Send a copy to a friend. Use an online backup provider. Something. ;)**

---

### Post by Jjkul1 on 2009-03-24
Thanks mate. really helped there. :KS:D:popcorn:

---

### Post by Mark Phelps on 2009-03-24
> **Jjkul1 said:**
> 

1- What could go wrong in the process of partitioning and installation? What if it does?!?!?!? =( explain as fully as you can

If you use the Ubuntu installer or GParted to "shrink" your Vista OS partition to make room for Ubuntu, there is a chance that your Vista installation will get corrupted and be unable to boot after that.  You should be able to fix that by booting from the Vista DVD and doing Startup Repair,


> 2- Assume I have backed up my C:\ drive onto a harddrive. What should I do if the installation orpartitioning messes up?
Your best bet is to do an image backup of your Vista OS partition.  That way, you will get everything back upon a restore.  Not sure a file backup will get you everything back.

> 3- What is a probability anything will happen? I know how to install but is it risky? I can't afford to lose Vista Ultimate as it is essential daily for my school work.
I understand, I have to use Vista daily and would be devastated if it was trashed -- which is why I do regular image backups to external media.  So, as has been said, if you critically need Vista day-to-day, then don't mess around with installing another OS, especially in dual-boot mode.

You could try installing inside windows using Wubi.  That way, if you really like it, you can wean yourself off Vista gradually and later, migrate to Linux-only, without risking damage to Vista.

> 4- Would I be able to get Vista Ultimate back if it is deleted? I have the Home Premium installation CD but the upgrade to Ultimate was through the internet.
Not easily.  You would have to reinstall from DVD and then do the upgrade again. If you downloaded the upgrade from the internet, then you could probably upgrade from that. I don't think the Anytime Upgrades (which is probably what you used) are available anymore for downloading.   So, if you don't have it or can't download it, then the answer becomes NO -- you can't get ultimate back.  There's a possibility that you could install Ultimate if you were to be able to obtain a regular Vista DVD and your license key works.  But the only way to find out for sure would be to attempt that and, if it does NOT work, you won't be able to get Ultimate back.

Also, MS imposes limits on the number of times you can reactivate a license.  Sometimes it's zero; sometimes it's three, other times it varies.  If your reinstall refused to reactivate, you would have to call MS Support in India and convince them to issue you a new license key.

```
7- If i backup all data and my partition tables go wrong, what do I have to do? is it like plug in the media where i backed it up and boot from there? or should I get my harddrive formatted, restore windows?
```
This is where an image backup is invaluable. If you were to hose the partitions, you would just boot from a restore CD (which either come with the imaging programs or can be burned from the imaging programs), plugin the media with the saved image, and run a Restore.  When  done, you're back to where you were before.

Sorry for the long replies, but you did ask for details ...

---

### Post by stchman on 2009-03-24
What is so critical about Vista to your schoolwork?  What apps are you using?

Chances are there are applications that can fit right in.

---

