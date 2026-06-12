---
title: "How to remove Ubuntu and GRUB from my PC without harming Vista?"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by boopit on 2009-07-14
[B]
[/B]

                   I'm experiencing some problems with Vista right now due to some failed software installations and various other screwups by me. So I want to do a clean recovery of my machine and restore it to the factory settings. I also have Ubuntu 9.04 installed, and am afraid that if completely restore vista, it might not install with GRUB right and therefore be invisible to GRUB and I won't be able to boot into vista.

The first thing alot of people will do when they see this question is: Tell me to do a google search on it. I've done this, and found MANY, I mean MANY articles on how to do this. All of them require a vista installation disk. I don't have a vista installation disk. All i have are a set of recovery disks I made when i first got my computer (an HP S5160F) not too long ago. How can i remove GRUB and Ubuntu successfully and do a clean recovery of my computer and then reinstall everything successfully with no harm done?

(NOTE: I am somewhat a linux noob, so i need this explained in the simplest of terms please)

---

### Post by lisati on 2009-07-14
***Important:*** make a backup of important data before making changes to your system. 

There are different possible answers. Here goes with a summary of one of them.

**1. Removing Ubuntu**
It is possible, using the partitioner on an Ubuntu LiveCD (check "System->Administration->Partition editor" on the menu) to delete the Ubuntu partition(s) and to grow the Windows partition to use the whole disk.

**2. Removing Grub**
I'm not familiar with the HP recovery disks, but a set of recovery disks I made for my Compaq machine (manufactured by HP) it's possible to do a little repair work. You'll need to use the disks to boot into a "recovery console" (command line) to issue the "fixmbr" and "fixboot" commands. This should get things so it will boot Windows again.

---

