---
title: "Error 15: missing file on installation"
date: 2008-11-23
forum: General Help
---

### Post by inspironxpuser on 2008-11-23
Hi, I have a Dell Inspiron 5150 laptop with XP and am curious about trying out Ubuntu since I've been hearing so much about it and would like to see if I could live in a Microsoft free environment. 

Yesterday I downloaded the 8.1 iso file and created a live boot CD as per the instructions.  The CD seemed to be successfully created and when inserted comes up with three options something like 1. live demo mode+installation 2. Install ubuntu and 3. Documentation/support.  Option 1 doesn't seem to work but Option 2 does install Ubuntu and when rebooting the laptop the option to boot to XP or Ubuntu is present for about 3 seconds. When I select boot to ubuntu an coundown timer comes up and then a screen displays five different options on how to load the OS but when selecting each option an error message appears stating Error 15: missing file initrd and then goes to grub>

I currently have Ubuntu loaded within windows on an external hard drive and after reading some of the online support documentation it appears as if I may have to load this missing file in addition to those that are present on the installation CD. Any ideas on how to do this? Or should I just try to create some free disc space on the internal hard drive and load Ubuntu there? At present there is 7GB free but Ubuntu needed 5GB to load.

Any help appreciated, TA.

---

### Post by decard_pain on 2008-11-23
if option 1 don't work i'd say it was a bad burn of the disk try redownload and burn again 

that looks like grub is looking in the wrong place


edit
it it a usb drive?
if it is i can pretty much guess the usb drive is not being detected at boot up.
go into the bios and look for usb legacy support(sometimes has keyboard by it)

---

### Post by inspironxpuser on 2008-11-23
I was wondering if the disc burn was a problem but downloaded the iso file from three different sources and made various CD's and all loaded ubuntu but when booting to ubuntu I got the same error message.  I can't remember what the exact error message was when I tried to run the option 1 but will try again tonight.

If I can't get it working there is a linux mag out at the moment that comes with a CD that has 7 different linux OS to try. This may be more reliable.

Yes external hard drive connected via USB. Will look for option to point boot to external device. ta

---

### Post by inspironxpuser on 2008-11-25
OK. Tried loading again from the CD (Option 1) says I need to reboot, but when I select OK to reboot, XP just shuts down and restarts and doesn't seem to go back to the bios screen to select booting to an alternate OS. You actually have to turn the computer off fully and turn on again to get to the bios option to select boot XP or Ubuntu. I managed to get into some bios options but couldn't didn't manage to find an option to select external drive so gave up on that option. Managed to delete some files on the internal hard drive and install ubuntu, rebooted computer and selected ubuntu.  The ubuntu background comes up (the browny coloured screen).  All appeared well but then the fan came on and the screen started flickering badly and after about ten minutes the computer turnedd itself off as it was overheating.  

Because I have installed ubuntu inside XP, rather than in a seperate partition, does this mean that XP is also being started in the background at the same time?  It would explain the computer shutting down due to overheating as one of the reasons that I am trying to step away from XP is that is seems to be taking longer and longer to load up and I don't know why exactly.  It seems to me that with every windows update it is getting slower.  Oh well it may be time to retire the old laptop and start again.

---

### Post by ago on 2008-11-25
> **inspironxpuser said:**
> 
Because I have installed ubuntu inside XP, rather than in a seperate partition, does this mean that XP is also being started in the background at the same time?
No, the same code is running as in a normal Ubuntu installation. And only the ubuntu code is running.

---

