---
title: "partitioning corrupted windows image?"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by jrox717 on 2009-06-11
so. I am coming to the ubuntu forums because I trust you guys and I am in way over my head. I've been running ubuntu for a couple of months on my laptop and I finally convinced my family to let me install it (dual booting with xp) on the family computer (dell dimension 4800). great!
first, booting to cd. I have an 8.10 live cd and also a copy on a bootable flash drive (both work). however, the computer won't boot from a flash drive, so I'm stuck with the cd. there are two cd drives, but apparently the bios will only boot from the top one and not the bottom one; HOWEVER, the top drive is broken and the computer doesn't recognize when there's a cd in the tray. 
well, I booted up the live cd in windows and selected "help boot from cd," which I *think* creates a cd image on the computer that it can boot from... I booted into the live cd and everything was great-- fast and lovely.
I opened up the installer, and when I got to the part about partitioning I select guided partitioning, giving ubuntu 10% of the 60 gig disk. but the process failed  for some reason (I'm sorry, I forgot to write down the error message). So, I tried to do manual partitioning using gparted, but it wouldn't let me resize the windows partition, saying that the minimum size was the size it was at the time (something around 57 gigs).
I've heard good things about partition magic so I booted back into windows and downloaded it from [http://www.soft32.com/download_151.html](http://www.soft32.com/download_151.html). being dumb I didn't realize that it was only a demo version (so theoretically it shouldn't do anything). I was in the middle of installing it (coincidence? virus?) when windows shut down and gave me a scary looking black screen, saying it was dumping the image (? I don't remember, sorry) and when it was done the computer shut off.

that's pretty much where I am now. when I turn on the computer I can boot into either windows or the ubuntu image. If I choose windows then the loading screen comes up for a minute then I get a black screen with a popup box saying 
>  the application or DLL C:\WINDOWS\system32\SCESRV.dll is not a valid Windows image. 
and this happens when I'm in safe mode as well. If I choose to boot into ubuntu then I am left with the busybox/initramfs shell, which I've gathered is the file system during boot, so I can't install from it.
this is what I would like to do, in order of preference:
1. figure out exactly what happened. are the windows files still there, or are they totally gone? is there any way to boot into the live cd image that was already made, or was that within windows?
2. find a way to boot from cd so that I can run the windows xp operating system disc and hopefully fix the filesystem, later installing ubuntu. I am maybe considering taking apart the computer and switching the cd drives, but I've never done anything like that before.
3. find a way to boot from the flash drive or some other way to get the live ubuntu cd working, and install over the entire disk. but I think to do this I would have to update the bios? which I might need the computer to do..

I would really appreciate any help or suggestions anyone can give. unfortunately I'm going away for the weekend so I won't be able to respond right away. But thank you so much!!

---

### Post by pedja_portugalac on 2009-06-11
I had so many problems installing Ubuntu on my uncles dell computer.

Good luck to you.

---

### Post by presence1960 on 2009-06-11
did you defrag windows at least once or twice prior to trying to resize? If you don't you will have errors and/or data loss. You must defrag because windows is haphazard about how it places files on the disk, it throws them all over the place. 

**_Always BACK UP data you can't lose or don't want to lose first, then defrag prior to trying to resize the windows partition!!!!!!_**

---

### Post by jrox717 on 2009-06-11
ah, I forgot about defragging. :( I don't use windows often anymore. and I did back things up, except for a game of my sister's that she really didn't want to lose. that's why recovering windows is higher on my list than not recovering windows. but if my only options were reinstall windows or install ubuntu on the whole disk then I would chose ubuntu.
thanks

---

### Post by presence1960 on 2009-06-11
Ok sorry i justread the end of your post and it looks like you really botched it up. To get that other CD drive to boot try going into BIOS and making that CD first boot.

Then if you have files you need to save I would boot off the Ubuntu Live CD (hopefully it will boot after changing the boot order in BIOS). If it boots choose "try ubuntu without any changes to your computer". When the deshtop is ready copy the files to a usb drive or if the other CD drive is a burner you could use that too.

Does your Dell still have a recovery partition? if it does consult your manual or the dell web site for your model to see which key(s) you need to hit when you boot to use the recovery partition. If not hopefully your CD drive is booting and you have bootable recovery disk(s)

Recover windows. When you get it the way you want then **DEFRAG it as some of the worst fragmentation occurs after a windows install/upgrade.** Then boot into the Ubuntu Live CD or use the gparted Live CD to resize the Windows partition.

Install Ubuntu. Good Luck- return here if you need help.

P.S. what model Dell do you have?

---

### Post by presence1960 on 2009-06-11
I looked on dells support & downloads web site and there is no dimension 4800. check that model # or post the dell service tag # affixed on the rear of your machine. I am trying to find out if you have a recovery partition and how to access it in case your CD drive will not boot.

---

### Post by presence1960 on 2009-06-11
this is from a dimension 4700 see if this works to get sytem recovery activated:
```

Using Dell PC Restore by Symantec
Use Dell PC Restore by Symantec only as the last method to restore your operating system. PC
Restore restores your hard drive to the operating state it was in when you purchased the computer.
Any programs or files added since you received your computer&#8212;including data files&#8212;are
permanently deleted from the hard drive. Data files include documents, spreadsheets, e-mail
messages, digital photos, music files, and so on. If possible, back up all data before using PC
Restore.
NOTICE: Using PC Restore permanently deletes all data on the hard drive and removes any applications or
drivers installed after you received your computer. If possible, back up the data before using PC Restore.
To use PC Restore:
1 Turn on the computer.
During the boot process, a blue bar with www.dell.com appears at the top of the screen.
2 Immediately upon seeing the blue bar, press <Ctrl><F11>.
If you do not press <Ctrl><F11> in time, let the computer finish restarting, and then
restart the computer again.
NOTICE: If you do not want to proceed with PC Restore, click Reboot in the following step.
3 On the next screen that appears, click Restore.
4 On the next screen, click Confirm.
The restore process takes approximately 6&#8211;10 minutes to complete.
5 When prompted, click Finish to reboot the computer.
```

Hopefully you didn't delete your recovery partition!

P.S. I looked at a few of the other Dimension models and it looks like they all use Ctrl+F11 to enter recovery mode.

---

### Post by presence1960 on 2009-06-11
> **jrox717 said:**
> ah, I forgot about defragging. :( I don't use windows often anymore. and I did back things up, except for a game of my sister's that she really didn't want to lose. that's why recovering windows is higher on my list than not recovering windows. but if my only options were reinstall windows or install ubuntu on the whole disk then I would chose ubuntu.
thanks
I thought this is your family's machine. I would consult them prior to eradicating Windows. it is after all their machine.

---

### Post by jrox717 on 2009-06-11
thanks, presence, for all your help. I just found what I think is some kind of recovery mode... it's running tests now, which is a good sign. and yeah, I'm sorry, my computer is a dimension 4600- I just read it wrong. about the bios, I still can't boot from the other cd drive (it's just not listed in the bios) BUT I think I found a way to boot from USB, which I'm going to try after the testing is done. 

oh, and don't worry, my family knows exactly what I'm doing. luckily they're relatively ambivalent :)

---

### Post by presence1960 on 2009-06-11
> **jrox717 said:**
> thanks, presence, for all your help. I just found what I think is some kind of recovery mode... it's running tests now, which is a good sign. and yeah, I'm sorry, my computer is a dimension 4600- I just read it wrong. about the bios, I still can't boot from the other cd drive (it's just not listed in the bios) BUT I think I found a way to boot from USB, which I'm going to try after the testing is done. 

oh, and don't worry, my family knows exactly what I'm doing. luckily they're relatively ambivalent :)

My BIOS has a choice of booting order between CD drive, hard disk, floppy & removable drives. Then there is another option for setting the order of the CD drives and hard disks. check to see if your BIOS has this option. if it does you can switch the order of the CD drives in there and just make sure CD is set as first boot in the other option.

---

### Post by jrox717 on 2009-06-30
Ok, the problem is solved! After a lot of fumbling around, I put the program Smart Boot Manager onto a flash drive and booted to that, which allowed me to boot from the Windows install disk. Then I copied the file C:\WINDOWS\system32\SCESRV.dll from another windows computer onto another flash drive and copied that onto the broken computer from the recovery console on the windows disk. voila!
Thank you, everybody, for all the help!

---

### Post by presence1960 on 2009-06-30
> **jrox717 said:**
> Ok, the problem is solved! After a lot of fumbling around, I put the program Smart Boot Manager onto a flash drive and booted to that, which allowed me to boot from the Windows install disk. Then I copied the file C:\WINDOWS\system32\SCESRV.dll from another windows computer onto another flash drive and copied that onto the broken computer from the recovery console on the windows disk. voila!
Thank you, everybody, for all the help!

Glad you got it working. Enjoy Ubuntu!

---

