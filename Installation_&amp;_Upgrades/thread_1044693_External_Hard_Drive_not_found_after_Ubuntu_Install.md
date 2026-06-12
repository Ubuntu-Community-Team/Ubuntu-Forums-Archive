---
title: "External Hard Drive not found after Ubuntu Installation; not found on Ubuntu OR XP"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by ViperByte on 2009-01-19
Hello, I am new to the forums and Ubuntu, so I may not be very clear. I have a 100gb Maxtor 6 L100P0 USB Device. I used a bootable CD, and installed Ubuntu on it, hoping to use the XHD to boot Ubuntu from. After installation, I went to XP to boot up Ubuntu. When I looked in My Computer, I did not see my External HardDrive. My PC shows that it is plugged in, but I cannot find it in Computer Management, or in My Computer. Please help! I have vital files and such on my hdd that I cannot afford to lose!!! :confused:
:cry:

---

### Post by alpage2 on 2009-01-19
It sounds like you have booted the computer up into windows, and then are trying to run linux from windows? This is not the way to do it.

For your computer to boot from a USB device, you will probably have to go into your system bios and set it to boot first from an external USB device. Then on exiting the bios, and assuming your XHD is plugged in, it should boot into linux from the XHD.

Reply here if you don't know how to do that.

Hope that helps.
Alan

---

### Post by ViperByte on 2009-01-19
Yeahh... I don't really know how to do that..... and now, my External HardDrive doesn't even show up in Computer Management!! Can anyone please help me!? My Computer doesn't even show the XHD, same with Computer Management. I have unistalled the driver and reinstalled it, and nothing has happened. The XHD only shows up in Device Manager.:(
EDIT: I don't really even care whether I lose all of my stuff; most of it is just games, music, etc. Is there anyway to reformat my XHD in Ext3 form? The problem is, I can't get it to show up anywhere else than Device Manager. Ubuntu (I installed it to the internal) doesn't even see the harddrive!

---

### Post by ViperByte on 2009-01-19
Oh, I almost forgot to mention, the Ubuntu version is 8.0.4, if it makes much of a difference

---

### Post by ViperByte on 2009-01-20
Oh well... I guess its off to Best Buy to get another hard drive... If anyone can still answer this problem, please post it up here! Thanks.

---

### Post by dabl on 2009-01-20
> **ViperByte said:**
> 

When I looked in My Computer, I did not see my External HardDrive. My PC shows that it is plugged in



This makes no sense. What operating system are you talking about? Where does your "PC" show that it is plugged in?

---

### Post by Pumalite on 2009-01-20
Install this driver in Windows (assuming you DID install Ubuntu in your USB):
[http://www.fs-driver.org/](http://www.fs-driver.org/)
See if you can see it now

---

### Post by ViperByte on 2009-01-20
> **Pumalite said:**
> Install this driver in Windows (assuming you DID install Ubuntu in your USB):
[http://www.fs-driver.org/](http://www.fs-driver.org/)
See if you can see it now

I installed FS-Driver, and now, I have a 2nd hard drive or something... It does not have any of the data that my XHD had. I guess it all got erased?
EDIT: This hard drive is NOT the XHD... it only has 39 MB, while my XHD has 100GB.

---

### Post by Pumalite on 2009-01-20
You are seeing an ext3 partition. Supposedly Ubuntu.

---

### Post by ViperByte on 2009-01-20
So what should I do? Wipe the entire harddrive or something? :(

---

### Post by Pumalite on 2009-01-20
Install Ubuntu with the option: 'Use Entire Drive'

---

### Post by cariboo on 2009-01-20
Before doing anything I would suggest you go into the BIOS and set the boot order so that it boots from a USB device, that way you should be able to boot into your newly installed Ubuntu desktop.

Noone has mentioned, Windows is pretty dumb when it comes to other file system types, the only things it can see and access are vfat and NTFS.

Jim

---

### Post by ViperByte on 2009-01-21
I don't know how to go into BIOS, and it still doesn't answer the question if I can get my XHD back!! :o

---

### Post by ViperByte on 2009-01-22
Bump.

---

### Post by ViperByte on 2009-01-23
Another bump.
Can anyone help?!

---

### Post by TSellers on 2009-01-23
This suggestion is purely aimed at looking at your hard drive so you can see if there is any of your data left on it, and will require some resourcefulness on your part.

Get ahold of a 'Hiren's Boot CD' ISO and burn it to DVD or CD. Use Google if you need more info on that subject. Boot the notebook with this disk. Explore the options that are presented to you on the opening menu, everything is there that you will need to mitigate and manage your problem.

I would also suggest that for some of the previous types of questions that you have posed like 'how to get into my Notebook's Bios', you'll be less frustrated and you'd get faster results using Google as a resource.

---

### Post by sigurnjak on 2009-01-23
Usually to get in to bios you need to press del  during boot . Your post screen should tell you how to get in to the bios and once there look for boot option priority . Also you can get more info if you find out your mobo model  and its manual .

---

### Post by ViperByte on 2009-03-22
Sorry for replying after such a long time... but I'm still not sure how to do this! I tried using Hiren's Boot CD, but it didn't work. What utility should I use?

---

### Post by TSellers on 2009-03-22
Your post is a bit vague about what didn't 'work'. If the Hiren's disk did not boot your machine, and assuming your computer's BIOS was set to 'boot from CD', then it's probable that you did not burn the ISO properly to create a bootable disc. 

There's lots of tutorials about how to burn ISO's you can find using Google, the place to start would be with the help files for the ISO burning software that you are using. My favourite is 'Copy to DVD' from VSO. ANother one that works good and is free is Deepburner Free: [http://www.deepburner.com/download/DeepBurner1.exe]("http://www.deepburner.com/download/DeepBurner1.exe")

---

### Post by ViperByte on 2009-03-22
By work, I mean that I could not successfully repartition the XHD.
Also, how might I change the BIOS to boot from CD? Does it have anything to do with the point that CD's boot from my PC at startup?

---

### Post by TSellers on 2009-03-22
Normally Paragon Hard Disk manager that is on that CD will work.

If not, then it's time to chuck the drive and buy a new one and start over, sounds like its time to cut your losses and run.

TO get into your BIOS you need to press the button that is normally designated on your screen when the computer is in POST (just turned on). If you don't see it there, then check the manual for instructions.

---

### Post by belshamash on 2009-04-24
Like many have already said, what you need to do it change you boot sequence. The way you do this is **(MAKE SURE YOUR HD IS PLUGGED IN):**
When you start you computer, before the windows logo there should be at the top of the screen something that says;
F1 to...
F12 boot sequence.
 
What you want to do is press F12(this will allow you to change the boot sequence for just that time) then select the usb and press enter. It will boot from the HD automatically.

---

