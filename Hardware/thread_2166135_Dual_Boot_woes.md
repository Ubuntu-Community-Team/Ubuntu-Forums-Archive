---
title: "Dual Boot woes"
date: 2013-08-07
forum: Hardware
---

### Post by yorgu2 on 2013-08-07
Thanks to david_p at askubuntu I was able to figure out my problem, turns out I had to set a BIOS password in order to gain access of the advanced options. 
You can read everything here: [http://askubuntu.com/questions/328415/ubuntu-13-04-not-recognizing-windows-8](http://askubuntu.com/questions/328415/ubuntu-13-04-not-recognizing-windows-8)

---

### Post by yorgu2 on 2013-08-07
Help please!

---

### Post by Iowan on 2013-08-07
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

---

### Post by QIII on 2013-08-07
Hello, yorgu2!

Please do not bump your posts so soon.  Remember that we are all volunteers here and spend our time here as we have it to give.

It could be that the person who has the very best answer for you lives in Kolkata, Calgary, Auckland or Bankok.  That person may be asleep, at work, eating, spending time with their children or watching a favorite TV program.  Not everyone here knows the answer to every question.

Please wait 24 hours before bumping a question to give everyone a chance to see it.  Please be patient.

Thanks.

---

### Post by oldfred on 2013-08-07
You show the signed Linux kernel so Ubuntu should be with secure boot on.
But do you have secure boot on or off?
Have you turned fast boot off as that can cause many issues.
You do not have any install that will boot in legacy mode or CSM/BIOS, just UEFI or UEFI with secure boot.

You do show that in Boot-Repair you ran the file rename function. That is for the few systems that will not boot Windows with secure boot off. Most should also boot Windows with secure boot off. Did you test it both ways?

If you want to restore to the un-renamed Windows efi file.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by yorgu2 on 2013-08-08
Secure boot is indeed on, and I see nothing in the BIOS about "fastboot". I never set anything, I just hit the "recommended" button. Also, if I want to disable secure boot I must switch to legacy mode, and I'm unable to boot windows in legacy mode.
**EDIT:** By hitting the restore option I am now able to once again enter windows, but ubuntu is still inaccessible.

---

### Post by oldfred on 2013-08-08
I would try with secure boot off.

I think there is both a Windows fast boot setting and a UEFI fast boot setting. Not sure if related. 

       [http://mjg59.dreamwidth.org/24869.html](http://mjg59.dreamwidth.org/24869.html)

   > One of the requirements for Windows 8 certified hardware is that it must complete firmware initialisation within a specific amount of time, something that Microsoft refer to as "Fast Boot". Meeting these requirements effectively makes it impossible to initialise USB, and it's likely that certain other things will also be skipped.

---

### Post by yorgu2 on 2013-08-08
As I said before the only way I can disable secure boot is to switch to legacy mode, and I was warned against that. I also see no "fastboot" option listed in my BIOS.
I'll show you a picture of the BIOS later on.

---

### Post by oldfred on 2013-08-08
What PC is this? and have you tried updating UEFI/BIOS? Vendors have found a lot of issues with their UEFI and are regularly updating it.

---

### Post by yorgu2 on 2013-08-08
Read the askubuntu link, its a Gateway NE56R31U.

---

### Post by yorgu2 on 2013-08-10
Bump.

---

### Post by oldfred on 2013-08-10
Some systems will only install in BIOS/CSM/Legacy mode.
 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

Update to UEFI/BIOS may fix some issues or:

You then have to use Boot-Repair to convert to UEFI mode, and rename the Windows efi file to be grub2's shim file which has the Microsoft signing key. Then from grub menu you boot Windows backed up efi file.

      
 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[URL="http://ubuntuforums.org/showthread.php?t=2103778"]http://ubuntuforums.org/showthread.php?t=2103778

[/URL]
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

[URL="http://ubuntuforums.org/showthread.php?t=2103778"]
[/URL]

---

### Post by yorgu2 on 2013-08-10
> **oldfred said:**
> 
      
 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[URL="http://ubuntuforums.org/showthread.php?t=2103778"]http://ubuntuforums.org/showthread.php?t=2103778

[/URL]
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

[URL="http://ubuntuforums.org/showthread.php?t=2103778"]
[/URL]

Tried this and was unable to boot recieved the following message "HDD: has been blocked by the current security policy".

---

### Post by oldfred on 2013-08-10
Can you turn secure boot off and boot? You should be able to boot both Windows & Ubuntu with secure boot off, but still in UEFI mode not CSM.

---

### Post by yorgu2 on 2013-08-10
The only way I've managed to turn Secure boot off is to turn UEFI off, and then I can't boot into windows.

---

### Post by oldfred on 2013-08-11
There requirement from Microsoft is that you must be able to turn secure boot off. But the assumption is that UEFI is still on, so Gateway may be technically correct to Microsoft contract, but not compiling with UEFI standards if you cannot boot in UEFI mode and secure boot off.

Hopefully Gateway will update UEFI to include UEFI boot with secure boot off. I would complain to vendor.

Then the only way to boot anything other than Windows is to install the full secure boot version of Ubuntu kernels and use the rename function with Boot-Repair as explained in post #12.

---

### Post by yorgu2 on 2013-08-11
Nevermind, the issue has been fixed, check my original post for more info.

---

