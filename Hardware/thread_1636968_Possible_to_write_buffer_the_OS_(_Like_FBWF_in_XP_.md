---
title: "Possible to write buffer the OS ( Like FBWF in XP embedded ) to write protect SSD?"
date: 2010-12-03
forum: Hardware
---

### Post by XA Hydra on 2010-12-03
*whew* How to even ask this! :)

-the current situation-

I am currently typing this post from an EeePC 900a. I use this machine in an ultra-low power solar setup, and also as a backup machine for work. The machine has a tiny 4GB SSD, and a 16GB SD card. I love the fact that it has no moving parts, but flash doesent endure writes forever.. To get around this I trimmed the fat on a windows XP install and added some DLLs from XP Embedded to enable FBWF (File based write filter). This allows the OS to allocate a user-defined amount of RAM upon boot to direct copies of any file that is written or modifed away from specified disks. The benefits are two-fold. Not only does it prevent ANY SSD writes, but it also makes the machine INCREDIBLY fast (screw up the OS? Reboot! ). If needed (updates, new programs, etc.) the feature can be temporarily disabled. ( The SD Card acts as the "home folder" of sorts )


-the ideal situation-

Quite simply, I'd rather be running ubuntu. All my other machines do, and the only reason I have not here is because I simply DON'T KNOW HOW to get this same result.
The first thing that comes to mind is the live CD. This would work, but I occasionaly tweak things and modernize software.

-Can Ubuntu be configured as if it were a custom, "moved-in" live CD, but with the ability to temporarily allow changes? (effectively creating a Read-Only OS) 

I see many tips and tricks to "minimize writes", but thats not quite what I want. I want them completely out of the picture most of the time. I may not be totally fulfilled running Windows on here, but it sure has been reliable and quick running as if it were "firmware".

...I have searched around for quite awhile before posting this and have been unsuccessful finding someone who has mentioned or did it first. Any assistance would make my day. 

If you have read this far, you have my thanks :)

---

### Post by TecsolAus on 2010-12-06
Hi,
Having just worn out the RAM Drive on a Comfile CUPC-P80 panel PC running Ubuntu, I'd love to hear any advice on this area.
An Ubuntu equivalent of XP Embedded's File Based Write Filter would be ideal.

---

### Post by cariboo on 2010-12-28
There is a couple of things you can do to affectively stop writes to the drive. First if you got the ram you can move /tmp to ram. Have a look at [this]("http://http://ubuntuforums.org/showthread.php?t=633776") thread for a how to.

Second, stop logging to /var/log, that may be the tough part, as there are quite a few applications that create and update logs.

---

### Post by rolkau on 2010-12-28
Use aufs to setup a union between the real filesystem containing the persistant data and a tmpfs which will receive the writes, and then setup a shutdown script that uses the aubrsync utility from the aufs2-utils package to merge the writes to disk (or an upstart script that does so periodically).

---

