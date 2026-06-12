---
title: "Unusual Dual Booting Issue -- Hardy and XP"
date: 2008-08-18
forum: General Help
---

### Post by Ragingterror on 2008-08-18
I recently started making the transition from XP to Linux by setting up a dual-boot on my old Dell Dimension 3000 (P4 processor, 3.0 GHz, 2 GB RAM).  I've been running XP and Hardy for more than a month with no problems to speak of... until today.

Booting up the computer this afternoon, every time I selected Ubuntu, the kernel would start to load briefly and then the computer would reset and return to the selection screen.  I downloaded, installed, and attempted to use WinGrub to fix the issue to no avail.  Since I had no important data in Ubuntu and had installed it from within Windows, I decided to try uninstalling and reinstalling it.

Now I can't get the Live CD to work (I'm using the disk shipped straight from Canonical).  If I try to boot from CD (regardless of my boot order in BIOS--I've tried both HD and CD-ROM first), the CD is skipped over entirely and XP boots up.  If I try to install from the CD or an ISO within XP, I get as far as the reboot before the aforementioned problem repeats itself.  I tried wiping everything Linux-related from my hard drive (including Grub and all references to ubuntu in boot.ini), leaving only XP, then repeating the above step.  I had the same problem.

The last thing I tried, out of desperation and intense frustration, was booting from the spare minimal-install CD I have left-over from my old laptop.  This time, the CD loaded up, I was able to select a language and start the installer.  The linux kernel started to load... and then the computer rebooted again and loaded up XP instead.

What on Earth is going on here?  I've tried literally everything I can think of on the software side of things to no avail.

:confused:

---

### Post by kubug on 2008-08-18
I would suggest at this point to take a look at your hardware. Start with using the memtest tool included on the Ubuntu CD. 

If the test runs clear (no red errors appearing) on all the test your memory is good (it will take a couple hours). From there I would start looking at peripherals. Did you try unplugging everything (USB hubs, printers, etc) and boot? 

Have you cleaned the inside of your computer lately? Is dust overheating your computer? Those old P4's really did get hot!

It does look like some hardware issue though. Try some of these suggestions and see what happens.

---

### Post by Ragingterror on 2008-08-18
> **kubug said:**
> I would suggest at this point to take a look at your hardware. Start with using the memtest tool included on the Ubuntu CD. 

If the test runs clear (no red errors appearing) on all the test your memory is good (it will take a couple hours). From there I would start looking at peripherals. Did you try unplugging everything (USB hubs, printers, etc) and boot? 

Have you cleaned the inside of your computer lately? Is dust overheating your computer? Those old P4's really did get hot!

It does look like some hardware issue though. Try some of these suggestions and see what happens.

The last time I cleaned my case was roughly 6 months ago.  I check it every few months, and the inside typically stays pretty clean.  I doubt the cause is dust.

I'll get started with these suggestions straight away and report back soon.

---

### Post by Ragingterror on 2008-08-19
After disconnecting my peripherals, I was able to get the install cd to work, but only one time.  I decided to try another install, went through the account creation steps, and set a partition size.

The install progressed normally for a while before freezing up on a black screen, forcing yet another reboot.  XP still functions normally although I now have 30 gigs of HD space locked away at the moment.

I'm now having all the same problems I was dealing with before.  So far as I can tell, the memory checks out.

---

### Post by FluffyElmo on 2008-08-19
This really sounds like a RAM issue. Alternately it might be your CD-ROM failing, though that wouldn't explain the initial problem that started the situation. Worst case would be your motherboard but one thing at a time.

Did you select memtest from the LiveCD boot menu and let it run for a long while? RAM issues can be subtle and may not appear immediately. If you have more than one memory stick remove all but the primary one and then test each stick individually. Trial and error will often show the bad one.

It could also be your CD-ROM, if you have access to another drive try that to see if you get any further in the install procedure.

It can be frustrating to diagnose hardware problems as it involves a lot of trial and error. Since you are having issues with both XP and Ubuntu though that is the most likely cause.

---

### Post by kubug on 2008-08-19
> **Ragingterror said:**
> After disconnecting my peripherals, I was able to get the install cd to work, but only one time.  I decided to try another install, went through the account creation steps, and set a partition size.

The install progressed normally for a while before freezing up on a black screen, forcing yet another reboot.  XP still functions normally although I now have 30 gigs of HD space locked away at the moment.

I'm now having all the same problems I was dealing with before.  So far as I can tell, the memory checks out.

Rather odd that XP is working fine still. Have you tried different distros? In my experience you are more likely to see a blue screen of death from Windows than Linux giving up on you. 

FluffyElmo's suggestion that it could be the CD-ROM is valid too. 

I would like you to boot into Windows and run this program:
[Prime95 32-bit]("http://files.extremeoverclocking.com/file.php?f=103")
After installing, choose "Just Stress Testing" and choose "Blend".

If it at any point fails, we know it's not 100% stable in Windows either. If it runs for a few hours (1 at least) without stopping, it is more a software problem with Linux 

There is a good how-to for "stress" testing here:
[Anandtech How-To Stress Test]("http://forums.anandtech.com/messageview.aspx?catid=28&threadid=1901991&enterthread=y")

These tests are to find out what part of your computer is unstable. Memtest86 is for your memory, and selecting certain tests in Prime95 will tell you if it is your CPU. 

Mind you, if you have CPU problems, it could also be motherboard problems or Power Supply problems.

Oh... and if you want to be really thorough you can open you case and look for bad capacitors. Go here for more info: [http://www.badcaps.net/]("http://www.badcaps.net/") You might have no problem there, but it doesn't take long to check to make sure. Look for "bulged" or "leaking" capacitors. Again, just to be thorough,

---

