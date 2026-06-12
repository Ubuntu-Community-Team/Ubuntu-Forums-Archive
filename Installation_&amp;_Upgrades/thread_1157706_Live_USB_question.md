---
title: "Live USB question"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by grandkodiak on 2009-05-13
Ive been unable to install ANY linux and I think i've narrowed it down to my cd/dvd drive... instead of replacing it i was wondering if there is a way to install a full copy of ubuntu or fedora from a live usb install? i have a usb thumbdrive, but im new to linux and i am not familiar on how a "live" copy works... once its up and running off of the usb stick, can i use it to partition, format and install on my existing harddrive? or will it only let me "try out" the software off of the thumbdrive or something along those lines?

---

### Post by orange-wedge on 2009-05-13
just download the iso of the distro you want and use unetbootin to load it on your thumb drive.

unetbootin is available for linux or windows.

---

### Post by grandkodiak on 2009-05-13
ok i downloaded that and installed it on my usb stick, but when i reboot, it just goes to windows. how do i set it to boot from the usb? i went into bios, and the priority options are the cd drive, raid array and removable drive. im assuming that means usb, but maybe its floppy (which i dont have installed) is there another option i am missing to boot from a usb stick?

---

### Post by lukenz on 2009-05-13
In Bios, look for options that make the boot quiet and disable them. When booting some BIOS' have an option, like press F5 (just an example) where you can select which device to boot to. Disabling a quite boot might just give you the ability to see other options on start up.
 
BIOS can be weird, I have an eee pc 1000 he that I was using to boot up netbook remix. When I set the boot priority it made no change, but pressing esc when it was booting up enabled me to select either my usb or my hard drive (F2 was the option to enter bios). There was also another option in BIOS to select available devices or something similar.
 
Try different USB ports. I have heard that on some pc's the front ones are disabled for boot.
 
Most live cd's have an installer. Ubuntu has a gui installer that you can use if you decide to install it. Otherwise you can just run it as a live cd/usb.
 
 
Luke

---

### Post by lukenz on 2009-05-13
If any of my previous suggestions don't help, could you please send through specs?

---

### Post by grandkodiak on 2009-05-14
Ive looked all around and I cant figure it out.
 
Only reason I am trying to boot from usb is that the main dvd drive doesnt work for some reason, i get sr1 errors and it never boots to gui, kicks to a useless shell for the few releases ive tried, (ubuntu, net and fedora) and it wont let me chose to boot from the other dvd drive i have, and wibu didnt work either, cause it ends up looking for a cd anyway haha.
 
i have a core2 due overclocked at 3.06ghz, 4gb ddr2 ram, twin radeon x1900 crossfire pcie videocards, twin 250 ata drives in raid 0, 1 1gb sata drive, and asus p5w dh deluxe motherboard. dont think anything else is really relevant but let me know. i really appreciate the help, i tried tech support from asus on thier website but i never get responses and thier live chat agent doesnt seem to ever be working!

---

### Post by Gadgetech on 2009-05-14
Are you sure your overclock is 100% stable? It may be causing issues with your DVD drive, especially if you're not running at a standard bus speed.

You might want to try clocking down to the standard speed for your install, just to make sure that isn't the problem.

---

### Post by grandkodiak on 2009-05-14
its been runnin 24/7 for almost 2 years without a hitch :) run some pretty aggressive software/video benchmarking programs until they start to get glitchy then tone it back a good 25% but... i guess ill give it a try later. both drives work fine in vista and xp, the dvd drive is very old though, but never found a need to upgrade i rarely if ever use it!

---

### Post by lukenz on 2009-05-14
Someone else has had the same issue booting off usb with this motherboard. 
 
Is USB legacy enabled, and also all ports?  Worth the try:p
 
See attached

---

### Post by grandkodiak on 2009-05-14
got it, had to go to hard drive list under boot first, move usb to the first choice, then go back to boot priority and usb appeared!
 
BUTTTTTT... seems it didnt help, this time, i got a completly different error, AND it didnt even get to a console, it hung on this screen indefinatly with no response to any key stroke.
 
this mean much to any of you linux peoples? only thing there that makes sense to me is that it mentions radeon at the end, linux not like my graphics cards? i searched google and it seems the radeon x1900 crossfires are listed as supported devices for quite a long time now...?
[]("http://68.37.131.101/linux%20boot.jpg") 
 
[IMG]http://68.37.131.101/linux%20boot.jpg[/IMG]

---

### Post by lukenz on 2009-05-14
Did you see the Grub or Lilo menu before all this??  if so there should be an option in there like:
 
Ubuntu 2.6...... **(recovery mode)**
 
Can you select the one that says Recovery?  It will take you to the command line.  Let me know if that works and I will advise further.

---

### Post by grandkodiak on 2009-05-15
well i get 3 options with ubuntu, default, help and oem. i didnt try oem, but default will freeze after the ubuntu logo, help will freeze but kick to console after the flash screen to this:
 
[IMG]http://68.37.131.101/ubuntu.jpg[/IMG]

---

### Post by lukenz on 2009-05-15
> **lukenz said:**
> Did you see the Grub or Lilo menu before all this??  if so there should be an option in there like:
 
Ubuntu 2.6...... **(recovery mode)**
 
Can you select the one that says Recovery? It will take you to the command line. Let me know if that works and I will advise further.

Apologies, something wrong with my brain...  You're not going to get this menu because ubuntu is not installed.

I am starting to lean towards the thought that it may be a bad install to the usb. My only suggestion now would be to reformat the usb and use unetbootin again, or download another distro for test purposes and give it a shot.  There are real small ones like damn small linux and puppy if you don't want to wait for a big download.  This would at least rule out a corrupt iso.

---

### Post by grandkodiak on 2009-05-15
well i dont think its the iso, ive tried both fedora 10 and ubuntu 9.04 both with no avail... everyone makes fun of windows but it always installs and runs in any shape :( grrr this is frustrating, thought id be up and running like a week ago now

---

### Post by orange-wedge on 2009-05-28
This may be an issue with your ATI graphics cards.

Have you tried Knoppix?  I sometimes have better luck with that distro when all I want to do is boot from a flash drive or CD.

If you want to go straight to an installation of Ubuntu and you have a free partition, you will probably need to use the "Alternate" disk.  But this has no Live CD option and will only allow you to install the full desktop in low graphics mode.  I've used this option when the Live CD didn't support my graphics card, and then installed the proprietary drivers post OS installation.

---

### Post by grandkodiak on 2009-05-29
i actually got it up and running and installed, but the graphics suck and i have no interenet, its set up with correct gateway, dns, ip etc, i cant even ping the router. no idea why, it worked fine in the live environment, and i certainly didnt change anything!

---

