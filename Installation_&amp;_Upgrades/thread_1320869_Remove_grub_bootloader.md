---
title: "Remove grub bootloader"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by chufflar on 2009-11-09
I have installed ubuntu on to and external usb hard disk drive, when I boot up my computer I get the grub loader come up then I get an error message 22. This began to annoy me so I thought I'll just remove the loader for now and go back to windows till I have more time to play around. So I used the xp install disk and typed fixmbr then fixboot. Both came up with sucess messages but when I reboot I still get the same message.

Any help would be much appreciated!

Thanks

---

### Post by darkod on 2009-11-09
Did you try using first fixboot then fixmbr? I don't remember how it was on XP any more but the sequence was sometimes confusing.

Also, one or both commands needed C: as argument, I think. Check with help fixboot and help fixmbr when in XP recovery console.

---

### Post by chufflar on 2009-11-09
I will try now and post back in a moment! Thanks for the speedy reply!

---

### Post by chufflar on 2009-11-09
No luck unfortunately I have just tried it both way rounds and it made no difference.

---

### Post by darkod on 2009-11-09
That's strange. Did you check the correct syntax first with help fixboot and help fixmbr?

And then used C: where needed in the commands?

---

### Post by chufflar on 2009-11-09
Yeah I checked and it automatically prompts that the selected drive will be c: if you dont specify anyway.

---

### Post by darkod on 2009-11-09
I would still try once more with C:. Don't trust windows. :)

Other than that, sorry, no idea. XP restore has always worked that way.

---

### Post by darkod on 2009-11-09
Take a look at this also
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by chufflar on 2009-11-09
Thanks a lot for your help I think I'll give the last one a try it sounds half promising!

---

### Post by chufflar on 2009-11-09
Unfortunately this doesn't work either! Now I'm really stuck!

---

### Post by darkod on 2009-11-09
wow. very very strange.

Depending how desperate you are, you could always try Windows Repair.

Instead of choosing Recovery Console on the XP cd, select Install. Then press F8 I think for the agreement, and in the next screen there will be option Repair Windows.

That will search for installations and should find yours. If it doesn't, then you're really stuck.

If it does just select that installation and continue with repair.

NOTE: XP repair will keep all your files and programs installed but it replaces all windows files with the ones fron the cd. That means you have to do all windows updates etc.

Also you might want to plug the drive in another PC and make a backup just in case before trying this.

---

### Post by KP314 on 2009-11-09
Try using a boot disk to get to a DOS prompt and get to your C: drive and run the below command. If it doesn't work while on your C: drive then go back to the drive letter the boot disk originally had you at and run it.

fdisk /mbr

---

### Post by oldfred on 2009-11-09
Which drive are you booting from in BIOS. Try switching drives.

---

### Post by amoskittelson on 2009-11-11
What about using Testdisk, as mentioned in this Youtube video:

[http://www.youtube.com/watch?v=OSQqyIvIMwY&feature=related](http://www.youtube.com/watch?v=OSQqyIvIMwY&feature=related)

or Super Grub Disk:
[http://teamoftechnologist.blogspot.com/2009/09/how-to-remove-grub-bootloader-and-set.html](http://teamoftechnologist.blogspot.com/2009/09/how-to-remove-grub-bootloader-and-set.html)

---

