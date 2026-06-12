---
title: "IBM ThinkPad R30 = beep beep beep on volume special keys."
date: 2008-11-18
forum: Hardware
---

### Post by sTpny on 2008-11-18
Hi People, Tony here, from Penguin Migrations in Penticton, BC, Canada, and as usual, I've got a problem.  

This problem involves an IBM ThinkPad R30 that beeps three short beeps, over and over again, as soon as I touch the either of the special keys for volume up or volume down. Not only do these special keys not control the volume, choosing to beep instead, but the incessant beeping continues until I press the special key for muting the sound, which does work. The result is no beeps, but also, no sound.  

Things seemed to be working perfectly on this system until I first pressed these "special" keys.  Now, the system, which already has a buyer, is unsellable. I cannot get the sound to work properly, and I've tried.

Googling the problem, I found out that there is a module for controlling ibm thinkpads, including the special keys, via acpi, notably, ibm-acpi, now replaced with thinkpad-acpi. ( [http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi) ) I looked at my modules with modprobe -l. and the thinkpad-acpi module is not loaded. How do I add it? and can this be the problem? 

It seems unlikely, since Ubuntu (Ubuntu 8.04) doesn't even need to be loaded (wtf?) to start or stop the beeping, but hey, what do I know. Could this be a hardware problem? a missing bootup option? a buggy bios? What should I do?

I couldn't find any mention of this beeping problem anywhere, but I found out about xbindkeys, which should give the key-codes for any key when invoked with the --key option, but pressing these keys produced nothing. I also found tpb in the repos, which said it would control the volume with the special keys, but it didn't. However, the on screen display did work, showing the volume bar going up or down, depending on which key I pressed. wtf? 

I removed tpb when I read that it is old and conflicts with the newer hotkey-setup. Reading /usr/share/hotkey-setup/ibm.hk, I found out that the R30 has no hardware mixer, and what the heck is dev/nvram? Is my problem related to this?  I am so at a loss.  I just don't know what to do. Please Please Please HELP ME!! 

Tony

Penguin Migrations - Breaking Windows and Smashing Gates!

---

### Post by Martin281 on 2008-12-18
Hi,

I have solved on my R30 the same problem you have described in your article. To say the truth I have headache too to make clear what causes the stupid beeping when pressing volume buttons. At first I disabled all alarm settings in BIOS but without success, then I ran IBM PC Doctor Diagnostics with no problem result. Then I tried to connect external speakers to line out connector and booted windows..without problems, sound working excellent. So I supposed that there is no problem with sound card at all, problematic should be only the source of the sound...BIOS. So I flashed the latest version (1.40) but the problem remained. So I looked through the R30 service manual - section beep codes...3 short beeps represent "POST error". So I tried to change HW configuration - removed HDD..without success...removed CD-ROM module and the problem solved..with the CD-ROM removed windows worked perfectly with sound:o)) So I reinstall the CD-ROM again and everything is fine. So my idea is, that you changed a lot of things in notebook configuration...new CD-ROM, another HDD etc at once and BIOS didn't accept all these changes correctly at once. Maybe that helps you! Martin

---

