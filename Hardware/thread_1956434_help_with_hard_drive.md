---
title: "help with hard drive"
date: 2012-04-10
forum: Hardware
---

### Post by lRevl on 2012-04-10
hi i just installed ubuntu today because i had a boot error or virus when i turned my computer it came up with 

Der Bootsektor dieser Diskette wurde neuerstellt.       
. ..Benutzen Sie den DOS-Befehl SYS um diese Diskette bootfähig zu machen!..
Bitte  legen Sie nun eine Systemdiskette ins Laufwerk und ..drücken Sie eine Taste.

i was trying to get the files from my hard drive to back them up and try to fix my laptop but when i went to click on my hard drive it would only show one file "file:///media/disk/&#9578;Aá&#8993;%02.í&#9566;"
i dont really understand im not very good at computers all i really want is my legal files and to fix my laptop so i can use XP again.

your help is greatly obliged thank you :)

---

### Post by jadtech on 2012-04-11
I think we need someone to translate this to English not sure  what language that is but if there is a menu to change it  might help you under stand ..
 i'm  pretty sure you might find its not a virus or boot error but a greeting  and a notice about installing  ..

the file it shows you I believe is the disk in your CD drive

---

### Post by lRevl on 2012-04-11
According to Google translate that means, "The boot sector of the  diskette has been created. They use the DOS SYS command to make the  diskette bootable! Please insert a system disk into the drive now and  print it one button" and i dont have a cd in my dvd drive im running ubuntu through a usb drive i tried to research this and so far all i have found is that is is a boot error virus that creates a fake boot secctor so i cant boot into windows xp. i dont have a installation disk for xp (pre installed on laptop) so i pretty much suck right now :(

---

### Post by DWade on 2012-04-11
If your computer has the windows XP key on it, you can use a Live CD and download a windows XP ISO off of one of web sites.

 Just Google: windows xp iso.  and the version that was installed on your computer (i.e. XP Home SP2 or Pro sp2)

Once you have the ISO downloaded burn a CD and reinstall.

---

### Post by lRevl on 2012-04-11
if i do that will i be able to get my info back and would it fix my boot error virus or would i still have to find out about that after i get on xp?

---

### Post by wbosher on 2012-04-11
You probably don't want to reinstall Windows or you'll loose everything. Try the recovery console first to fix the boot sector.
 
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
 
User Fixboot and Fixmbr, there are detailed instructions on using this in the link above.
 
Hope this helps.

---

### Post by lRevl on 2012-04-11
so what you are saying is use a recovery disk to start this then use the fixboot and fixmbr commands to fix this problem, and if it does what about the virus wouldnt it currupt the boot again?

---

### Post by wbosher on 2012-04-11
Yes. When you get a Windws CD and boot into it, it will give you an option to start the recovery console. It's a command line interface and you can use these two commands, it should fix your problem hopefully. You can run a chkdsk from there also.
 
I would definately try this before doing a complete reinstall, as this could wipe everything.

---

### Post by lRevl on 2012-04-11
but wouldnt the virus corrupt the boot again once i do this?

---

### Post by wbosher on 2012-04-11
If it is indeed cuased by a virus and not just some Windows glitch, then you should run a virus scan once you can boot back into Windows.

---

### Post by CharlesA on 2012-04-11
> **DWade said:**
> If your computer has the windows XP key on it, you can use a Live CD and download a windows XP ISO off of one of web sites.

 Just Google: windows xp iso.  and the version that was installed on your computer (i.e. XP Home SP2 or Pro sp2)

Once you have the ISO downloaded burn a CD and reinstall.
As a general rule, it's not a good idea to grab some random Windows ISO and install it. What if it was messed with and you get owned?

---

### Post by lRevl on 2012-04-11
so what would you suggest good sir?

---

### Post by wbosher on 2012-04-11
Normally, I would agree with what CharlesA said about grabbing any old ISO, but it doesn't seem like you really have any other option unless you know someone with a Windows CD.
 
In my personal experience, I've download Windows ISOs from "various places" in the past and never had any problems. 
 
I do have a legal copy now though Microsoft. ;)

---

### Post by CharlesA on 2012-04-11
> **lRevl said:**
> so what would you suggest good sir?
You could always try running a AV boot cd and seeing if it finds anything on the Windows drive.

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

---

### Post by lRevl on 2012-04-11
so the version that i have the key for is XP home edition but i know that i had updated to sp3 so do i get home edition or just download sp3?

---

### Post by DWade on 2012-04-11
> **CharlesA said:**
> As a general rule, it's not a good idea to grab some random Windows ISO and install it. What if it was messed with and you get owned?

Yes and no.  Look for a site that Guarantees the safety of files.  Or take the chance to get The ISO so you can make a CD and then run the repair console. or  You can pay about 30.00 dollars from the computer manufacture to get you a restore disk.

Remember if you got another hard drive you can use it for storing data on and then boot with the live CD down load and install from software installer the antivirus program and then run it to check the disk

---

### Post by lRevl on 2012-04-11
> **CharlesA said:**
> You could always try running a AV boot cd and seeing if it finds anything on the Windows drive.

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

but how would this help with the boot problem, im kinda confused about it :/

---

### Post by wbosher on 2012-04-11
Running the antivirus from a boot CD is a good suggestion (wish I'd though of it). That will ensure your system is clean before you fix the boot system.
 
Once that is done, then do the recovery console if you're comfortable with an unknown Windows ISO.
 
That will hopefully get you up and running again.
 
If you just need to get some files from the hard drive, you could make a bootable Ubuntu CD or USB and boot into it. You can see Windows files this way and may be able to copy them onto another device. Worth a try.

---

### Post by lRevl on 2012-04-11
so what should i look for in one of these av boot disk?

---

### Post by DWade on 2012-04-11
Antivirus by itself on a resque CD is 
Bitdefender and Kaspersky you can get the ISO from there sites.

On the desktop CD of Ubuntu when you use it as a live CD with a secondary hard drive you can load from clamTK virus Scanner and update and scan the drive.

---

### Post by DWade on 2012-04-11
here are the links to rescue disks"
Kaspersky:[Click here]("http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk/")
Bit Defender: [Click Here]("http://download.bitdefender.com/rescue_cd/")
AVG: [Click here]("http://www.avg.com/us-en/avg-rescue-cd")

---

### Post by DWade on 2012-04-13
> **lRevl said:**
> so the version that i have the key for is XP home edition but i know that i had updated to sp3 so do i get home edition or just download sp3?

Your serial key is for either windows XP plain, sp1, sp2 or sp3.  I tired puting my serial number in on sp3 for sp2 and it refused it.  but then again you have to have the sp3 disk to rescue your system if you have sp3 installed.  you will have to download two iso's.

But you may get by, if you you download ultimate boot CD [http://www.ultimatebootcd.com/download.html]("http://www.ultimatebootcd.com/download.html") and use the FDISK /mbr command from MS-DOS to reinitialize a generic MBR or download MS DOS [http://www.bootdisk.com/]("http://www.bootdisk.com/") .  Use GParted to make sure the windows partition is the boot partition. Then boot into windows

Send me a Private message with email and I will give a detailed how too.

---

