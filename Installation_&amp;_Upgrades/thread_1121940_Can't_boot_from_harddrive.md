---
title: "Can't boot from harddrive"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by rockin roll on 2009-04-10
I have PC with Win XP already installed on an 60gb ide, I bought a 80gb ide to install ubuntu onto as dual-boot.
As I did not particularly wish to partition the main drive, I installed  the 80GB IDE drive as pimary master and the 60 as slave. I then booted the ubuntu 8.1 live CD and installed ubuntu to the IDE drive without any problem. However, when the computer tryed to re-booted at the end of the install, it would not boot.
Changed the bios settings to make the 80gb drive boot first, but got the same result. I also have not reconected the 60 gb drive yet i figured i would boot up and make shure ubuntu was going work on the 80gb first.
I then booted ubuntu from the live CD every thing worked fine. 
 then select 'boot from first hard disk', which gave the following error ISOLINUX : DISK ERROR 01, AX=0201, DRIVE 80

 So i went back in the bios in the boot menu it took a few seconds for the menu to come up witch it had never done before. when it did come up it would not show the hard drive just said "no drive"
Looked at a few other setting came back to the boot menu and there it was right were it was suposed to be. whats up with that? So i powerd down checked all conection just to make shure. Tryed to boot up and same things are happening. Total lost at this point. I need help please and thanks. PS Im a total noob to linux and been looking all over the net for 2 days trying to fix this.

---

### Post by rockin roll on 2009-04-10
bump

---

### Post by oldos2er on 2009-04-10
I don't know if Win* will boot from a slave drive. Maybe someone else can confirm or deny that?

 Do you have the jumpers set properly for master and slave?

---

### Post by adalal on 2009-04-10
well, im not much of an expert, but from the looks of it GRUB isn't starting up... or the drive's messed up.. have a look at this:

[http://ubuntuforums.org/showthread.php?t=627443]("http://ubuntuforums.org/showthread.php?t=627443")

Try formatting the entire drive maybe? and reinstalling.. and i think Windows doesn't allow to be started from a slave anyways, im not quite sure, look at this bit up...

---

### Post by rockin roll on 2009-04-10
The drive windows is on is not even conected at this point. So theres only one drive there that i just tryed with a reinstall of ubuntu 8.1. I think its a grub problem to but dont know how to fix it. When go to the bios boot menu at the top of the list for booting it say NONE for the IDE drive. so i goto the main menu pimary master says none untill i click on it then it changes to show the drive. i go back to the boot menu and now it shows the drive. It does this each time i go to the bios. This has never happen before so ??? Then put the cd back in and it boots no problem. reading that link now thanks.

---

### Post by rockin roll on 2009-04-10
Ok heres the update. I had my jumers set to maser and slave. I put them to CS Cable select i did not know this. pluged in both drive's the maser drive with ubuntu is the black plug the gray plug goes to the slave (windows) drive. powered it up and bam booted strait into ubuntu. Im so happy. Now all i have to figure out is how to get it to boot one or the other without going to the bios. Thanks again for the link, for thats were i got the info on the jumpers and cable select thing.

---

