---
title: "Error 1 Again..."
date: 2008-11-16
forum: General Help
---

### Post by wausaubill on 2008-11-16
I am back again, sorry for those who tried to help out when I posted before, but I was too busy to follow-up, so here we go again.

I downloaded the latest WUBI installer and ran it, and once again I am getting "Error 1" (from Grub apparently) when I try to boot into Ubuntu.

Here is the text of Error 1:  1: Filename must be either an absolute filename or blocklist.

There are several menu.lst files and I have looked at them, but can't really make head nor tail out of them in terms of causing this error.

I am running Windows XP and here is the way things are set up on my machine and perhaps why GRUB is having such a hard time.  :)

I have 2 internal hard drives on my machine.  The first internal hard drive is partitioned into 5 partitions (don't ask me why I did that now!)  They are labled by Windows as: C:, F:, G:, H:, and I:.

There is a floppy drive B: and a CD drive, D:

I also have a usb drive E:

When I downloaded WUBI I put it on the I: drive and when I installed I told WUBI I wanted Ubuntu on the E: drive.

When I reboot, I get the GRUB menu and when I pick Ubuntu, I get Error 1.  I get Error 1 pretty much not matter what option on the menu I choose.

I can boot into Windows fine.

Any ideas?

Thanks in advance!

Bill

---

### Post by tuxxy on 2008-11-16
Try a forum search for solved error 1 threads like this for example 

[http://ubuntuforums.org/showthread.php?t=372070](http://ubuntuforums.org/showthread.php?t=372070)

---

### Post by 73ckn797 on 2008-11-16
> **wausaubill said:**
> When I reboot, I get the GRUB menu and when I pick Ubuntu, I get Error 1.  I get Error 1 pretty much not matter what option on the menu I choose.

I have never seen error 1 and I play around too much and have seen many grub errors. Please designate what the actual error is, if in fact there is "error 1".

Is it error 17 or what?

---

### Post by wausaubill on 2008-11-16
Thank you tuxxy, but no, that doesn't seem to solve my problem at all.

And yes, 73ckn797,  there is a GRUB Error 1, here is what it says in the GRUB manual:

[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors")

[INDENT]14.3 Errors reported by the Stage 2

The general way that the Stage 2 handles errors is to abort the operation in question, print an error string, then (if possible) either continue based on the fact that an error occurred or wait for the user to deal with the error. 

The following is a comprehensive list of error messages for the Stage 2 (error numbers for the Stage 1.5 are listed before the colon in each description): 
1 : Filename must be either an absolute filename or blocklist
This error is returned if a file name is requested which doesn't fit the syntax/rules listed in the Filesystem.[/INDENT]

But that doesn't seem to help me solve the problem either...

:(

---

### Post by 73ckn797 on 2008-11-17
> **wausaubill said:**
> And yes, 73ckn797,  there is a GRUB Error 1, here is what it says in the GRUB manual:

[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)
[INDENT]14.3 Errors reported by the Stage 2

The general way that the Stage 2 handles errors is to abort the operation in question, print an error string, then (if possible) either continue based on the fact that an error occurred or wait for the user to deal with the error. 

The following is a comprehensive list of error messages for the Stage 2 (error numbers for the Stage 1.5 are listed before the colon in each description): 
1 : Filename must be either an absolute filename or blocklist
This error is returned if a file name is requested which doesn't fit the syntax/rules listed in the Filesystem.[/INDENT]But that doesn't seem to help me solve the problem either...

:(


I stand corrected, thanks.

---

### Post by ago on 2008-11-18
Press the insert key rapidly after selecting "ubuntu". Make sure you are on grub4dos and not grub, and make sure that the appropriate menu.lst is loaded. You can post here the commands that grub4dos is executing.

---

### Post by wausaubill on 2008-11-18
Thanks Ago.  I took your advice and rebooted.  I assume the insert key goes command by command.  Anyway...I did get a couple of error messages that said the number of sectors on my drive were different in the BIOS and the MBR, but I don't think that was a critical problem.

It then said that my boot drive was "80" (sorry not to quote exactly, I was writing all this down) and then said "Starting cMain()"

Then it said, "Open/Default Failure."

Then "Kernel Normal Mode" and then Error 1 message.

The menu (asking whether I wanted Demo, ACIP, Safe Graphic Mode, etc.) did come up, but selecting any item went back to the error 1 msg.

There are several menu.lst files in the ubuntu folder on the drive I installed WUBI to.  One is in \ubuntu\install\boot\grub, one is in \ubuntu\winboot.  I can post either or both here if that would help.

I hope we can figure this out, I would love to get it up and running.  After playing witn WUBI for a while, I will probably go dual boot with Ubuntu installed on the whole external drive.

Thanks!

Bill

---

### Post by wausaubill on 2008-11-18
Ooops, one other thing, it is in fact grub4dos, version 0.4.4

---

### Post by fk27bob on 2008-11-26
I too had the same problem. I'm very new to linux. So I just kept trying the simple things. I think I have this problem figured out.

My setup is similar to the the original poster (except I don't have all the partitions on my XP drive). XP boots from my C: drive and D: is formatted NTFS and is used as a backup to C:

I originally downloaded Wubi and .iso file to C: and tried to install Ubuntu on D: The grub gave me the same "Error 1: Filename must be either an absolute pathname or blocklist" error. I then copied the wubi.exe and .iso file to the D: drive, installed Ubuntu on D: drive via Wubi and grub works as it is supposed to and Ubuntu now is installed on the D: drive and working fine.

The problem seems to be introduced when you use the .iso file instead of the automated installer from Ubuntu. With the installer it asks you which drive to install on before downloading the distro. Then it downloads the file to whichever drive you specified, then installs it for you on that drive. The directions for installing from the .iso file only say that the Wubi.exe file has to be in the same directory as the .iso file, when in fact they need to be in the same directory as each other and both have to be on the same drive you wish to install the operating system.

I also tried installing from the cd using Wubi. It didn't work when I tried to install on the D: drive either.

Sometimes the KISS rule works even with these sometimes complicated machines.

---

### Post by wausaubill on 2008-11-30
Yes, I think you are onto something here Bob. :)  I tried letting WUBI download the iso, but it was so slow (it said it would take 45 days!  -- no kidding) that I abandoned that approach and DLed the iso manually.  

I guess that GRUB got a bit confused at that point. :)

Anyway, I am going to sold the problem by moving some data off my second internal hard drive onto a USB drive (as soon as my USB 2.0 card arrives) and install Ubuntu on the second drive and then use it as my boot drive.

Good luck in your new Linux set-up, Bob!

---

### Post by ago on 2008-12-01
I'd need to know what commands fails exactly. I think that is due to a wrong menu.lst being used. Press ESC at boot, then select the first menu item and press "e", then select the line that starts with "kernel" and press "e". Post here the line.

---

