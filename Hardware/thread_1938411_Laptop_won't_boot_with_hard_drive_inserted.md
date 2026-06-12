---
title: "Laptop won't boot with hard drive inserted"
date: 2012-03-09
forum: Hardware
---

### Post by faustism on 2012-03-09
Hello all,

I understand that this is not necessarily a Linux/Ubuntu problem, but it has arisen from using Linux/Ubuntu.

I had my computer set up with a Linux and Windows dual boot, and I resized some partitions, and then I booted up again, Grub gave me error 17 I believe. I assumed that this meant it could not find it's files (which were not moved, but the partitioning did change) so I used Boot-Repair to reinstall Grub so that it could find it's files. Then I saved the newly created grub.cfg to grub.cfg.old and wrote a custom one to chainload Windows and Linux (yes, I intend to do this, it makes dealing with multiple distros easiest for me) The reboot went fine, and brought me to grub with the menu entries as I had specified however, one of the Linux ones didn't work. I'm not sure exactly why, but I got an error. Thus, I tried Windows which went into some recovery mode (I think it was trying to load my Recovery partition) so I shut the laptop down manually.

Upon reboot, my computer hangs at the Laptop splash screen (the ASUS name across the center, and the intel logo down to the right). It does not accept any of the commands to get into the BIOS menu (which is Esc) and it won't accept the command to use the built in recovery partition (F9). It will however reload the splash screen (which I assume is some sort of soft reboot?) upon pressing Ctrl+Alt+Delete.

Oddly enough, with the hard drive removed, I can boot the computer from a livecd though it doesn't work with the hard drive inserted. I also tried inserting the hardware while running off the livecd but that left the liveOS crippled (only the desktop environment would work, I couldn't load programs) and I believe the CD drive was disabled because I also couldn't open it. (Though after a reboot without the hard drive, the CD drive does work)

Any help regarding this would be greatly appreciated. Right now the only thing I can do with my laptop is boot off of liveCDs.Thank you in advance for any help/advice you can give me.

-Derek

---

### Post by kikotiger on 2012-03-09
This seems like a hardware problem. Try testing your hard drive with another computer and make sure it works. Your hard drive might be dead or the port on the computer might be bad. If you are using a CD for LiveCD I don't think it will allow you to eject the CD. Try running Ubuntu from a flash drive and test the CD-drive. 
You might want to set-up your BIOS to boot from the CD or USB drive before the hard drive and see if the hard drive works.
Hope any of this helps. Good luck.

---

### Post by faustism on 2012-03-09
Thanks for the quick reply.

I have a hard time believing that it is a hardware failure because it occurred after changing partitions and the MBR. To me that indicates it should be something else.
Also, I don't have any other hardware to test the drive on.

I actually tried ejecting the cd while running live, and it is possible. My main reason for saying that the cd drive was disabled was because I couldn't use any features of the liveOS that weren't loaded into RAM.

Unfortunately, I cannot set the BIOS to boot from the CD drive before the hard drive because (for some strange reason) I can only arrange items in the boot order if they are plugged in.

I did see a setting in the BIOS about AHCI and IDE mode for the SATA controller, so I might try switching from AHCI to IDE and see if that allows me to access the drive.

Thanks,
Derek

---

### Post by oldfred on 2012-03-09
Have you tried a full power down or cold boot. 

Some have reported that some data gets reused on reboot and it does not then work. But a cold boot solves the problem.

---

### Post by faustism on 2012-03-09
Yes, I have tried starting from a cold boot and got the same result.

---

### Post by kikotiger on 2012-03-09
There might be an option in the BIOS where it gives the process of the post instead of the splash screen, it might give you a hint where is hanging. Have you tried reinstalling Ubuntu or reinstall grub?

---

### Post by faustism on 2012-03-09
I cannot access the hard drive because when it is in the computer, the computer either won't boot, or is incapable of accessing it's drives.

I will try looking in the BIOS settings though. thanks for the suggestion.

---

### Post by faustism on 2012-03-09
I recently tried changing the SATA controller setting to IDE instead of AHCI, but the results were the same. I looked for an option to disable the splash screen so I could see the POST output, but there was one. Any other suggestions?

---

### Post by ahallubuntu on 2012-03-09
It's time to test the hard drive - it might have failed.  Or, the motherboard may have failed.

You can test the hard drive by attaching it to a different computer.  If you have a desktop with a SATA hard drive, you can connect your laptop hard drive to the same connectors - they are the same for laptop and desktop (unless your laptop is 5-6+ years old and uses an old PATA-style hard drive).  You can also obtain a USB hard drive enclosure or adapter (handy to have around anyway for future use) to connect the drive to another computer via its USB connector.

DON'T try to boot Windows on another computer, but you can try booting Linux from it.

Try the Ultimate Boot CD to test the drive - burn it (as an image) to a blank CD, boot it on computer with drive attached, start up Parted Magic.  Click on SmartControl, see if any Attributes are highlighted in red.  You can run the short S.M.A.R.T. test there too.  Just a general sanity check on the drive.  But if you can boot Linux on another computer with this drive, chances are it is not failing.

It is quite possible the drive failed while you were resizing partitions originally.  A hard drive can fail at any time or may have been failing prior to this and you didn't realize it.

If your drive is OK then it would be most helpful (though perhaps not easy for you) to try another laptop hard drive in place if the old one.  If you have the same problems and can't boot, then your motherboard is probably bad.

---

### Post by faustism on 2012-03-26
Thanks for all of your responses.

I ended up calling the manufacturer, as my computer is still under warranty. They took it back, replaced the hard drive, and now it all works well.

-Derek

---

