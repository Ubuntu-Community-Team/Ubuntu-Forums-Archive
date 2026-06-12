---
title: "Disaster! Can't boot"
date: 2008-08-22
forum: General Help
---

### Post by chriswhitworth on 2008-08-22
I am in big trouble. I have a PC that will not boot. I installed ubuntu 8.04 from the download site. I could not figure out how to get it to run on my Apple Cinema 23" at full resolution. Seems like it would only go up to 1440x1280 or something. I found many suggestions but they all seemed more technical than I was willing to deal with. So I decided to uninstall it. This turned out to be more difficult than I thought it would be.

For one thing, it created a Boot Loader which was fine for me to get around when booting up, defaulting to Ubuntu, but my wife was another story.

My PC is a Lenovo ThinkCentre. It runs a 2.2 ghz Core 2 Duo with a gig of RAM. Just got, as a matter of fact. It has an internal DVD burner and several USB ports. It does not have a diskette drive. 

I secured a copy of Norton Partition Magic to reclaim the partition Unbuntu had me create when I installed it. I figured if I deleted the partition with all of its' contents, I would be able to go back to what I had. This has not turned out to be the case. 

When I was completing the Partition Magic steps, a reboot was in order. This is when the problem arose. The Boot Loader is still there, sort of. On my screen I see the following:

GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 17 

- (blinking)


It has been blinking for some time now. I realize I did this to myself, but I need help. I went into the BIOS and set the CD-drive to be the first boot device, inserted my Ubuntu disk hoping if I could re-install it, I could get back to where I was, but the CDROM won't start up.

I need any suggestions anyone might have. Even to other sources that might be able to help out.

---

### Post by chriswhitworth on 2008-08-22
Follow up: I have been searching for the Error 17 and found that it is common. The problem is that most of the suggestions involve booting with a floppy disk, which my machine does not have. 

I have tried to change the boot order in my BIOS to make the CD be the boot device, but it will not come to life. The startup only wants to go to the GRUB loader. Also, I am clueless when it comes to typing in commands at the 'root'. How do you get there when all I can get to come up is the Error 17 message?

---

### Post by mb_webguy on 2008-08-22
The problem is that GRUB lived on the partition you nuked.  GRUB can't load because you killed it.

While you didn't specifically mention it, I'm assuming you have a version of Windows installed.  If that's the case, you can fix the problem by booting from the Windows installation cd and repairing your installation.  

If that doesn't work, then boot from the Windows installation cd again, choose to repair your installation, then choose the option to go to the command line and type "fixmbr".  

If *that* doesn't work, then do the same but this time type "fdisk /mbr" at the command line.

---

### Post by chriswhitworth on 2008-08-23
mb_webbuy,

Thanks very much for your response. I sort of figured something along those lines, but am not sure how to proceed. I interrupt normal startup and get into the BIOS where I try to place the CD as the boot device, but I can't get the CD to wake up.

Is ultimately what I am trying to do in this case is remove the GRUB?

---

### Post by trashjunkid on 2008-08-23
chriswhitworth-

In your bios setup, go to the boot priority page and disable every other boot up option except the cd-rom drive where you've put your boot cd. It should not be necessary, but I have needed this approach on a few machines to get the cdrom to boot.

Good luck,
Trashjunkid

---

