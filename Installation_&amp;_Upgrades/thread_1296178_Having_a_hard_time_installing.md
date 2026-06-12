---
title: "Having a hard time installing"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Biscuitz on 2009-10-20
So far, going on 2 days of trying to install Ubuntu 9.04 on my parents old computer.   It's a Compaq with 512 memory, and 160GB HDD. It's old, as in 2004? Old.     I keep getting the Grub error 18 on load (after installation obviously).   So, I've been Googling my head off the last 2 days to find any answer as to fix this. I thought I found the answer when using cfdisk to partition the HDD and get it to install in the first section of the HDD. I was told (by a source of my own) to make a large partition at the end of the drive and then install Ubuntu in the beginning part.    Using cfdisk to do this, has been hell. When I try to write to the partition it gives me :    WroNo primary partitions are marked bootable. DOS MBR cannot boot this.e. Toggle Bootable Flag of the current partitions.     I never made it bootable. So I toggled the bootable flag, and tried to write, still receiving an error, something about cannot write (I don't even remember now) but the point is, it will not write.  I'm not wanting to update the BIOS (I'm not comfortable with doing so and if something does go wrong and I mess up their computer, I'll never hear the end of it, even though it's my OLD computer that I gave them free). Is there another way around this problem? Can someone explain to me in detail, how to work cfdisk? Is there a manual I can access?   I'm fairly new to Ubuntu/Linux all together, so I have no idea.   I appreciate any patient helpers.

---

### Post by louieb on 2009-10-20
Why don't you use Gparted on the live CD to partition with? Its a whole lot easier. 

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by Biscuitz on 2009-10-20
Hmm, I never knew that. I shall try that, thank you!

---

### Post by oldfred on 2009-10-20
From Herman's site:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

So just make sure your only have the boot part at the beginning of the disk and put data at the end.

GRUB error 18 most commonly occurs when a hard disk is larger than the computer's BIOS was designed for. 

                                       Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

---

### Post by presence1960 on 2009-10-20
[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

See link above for GRUB error 18. That occurs when your BIOS can't read the files necessary to boot because they are beyond the limit that your BIOS can translate. Your computer is not that old so your limit is most likely 137 GB.

You have 2  choices. Create a separate /boot partition for Ubuntu within the first 137 GB of your hard disk or update the BIOS.

Why don't you do this so we can get an accurate picture of what that machine has:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

WE can go from there.

This is not an Ubuntu problem or fault, it is a limitation imposed by your BIOS.

---

### Post by presence1960 on 2009-10-20
> **oldfred said:**
> From Herman's site:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

So just make sure your only have the boot part at the beginning of the disk and put data at the end.

GRUB error 18 most commonly occurs when a hard disk is larger than the computer's BIOS was designed for. 

                                       Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

+1 oldfred, you beat me to the punch! :guitar:

---

### Post by oldfred on 2009-10-20
Presence, one of the few times I have been first but as usual your suggestion of running the boot info script is still better as it will allow us to help the OP if he has problems.

---

