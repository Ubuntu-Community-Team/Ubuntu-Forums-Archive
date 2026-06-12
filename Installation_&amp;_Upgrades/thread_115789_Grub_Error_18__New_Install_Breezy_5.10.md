---
title: "Grub Error 18  New Install Breezy 5.10"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by interse on 2006-01-11
I have tried several times to do a new install of 5.10.  Tried also to do a new install of 5.04.  In all cases, I get, upon rebooting, Grub Error 18.

I even tried, previous to the most recent tries, formatting with Windows 98 and Windows installed.   Then tried Ubuntu 5.10.  No luck

Strange, but I had installed Ubuntu 5.04 and upgrade to 5.10 on this machine w/o a hitch.  I did manage to crash my system yesterday.  Now I can do a clean install.

HELP?

---

### Post by Kipper on 2006-01-11
I think folks will need a few more details in order to help you with this. 


GRUB error 18 is explained as:

[I]Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.[/I]

Somehow, I think you are going to say - "What the ****?"

So what's your hardware? How's your BIOS setup for your hard drive(s)?
Is this a daul-boot set-up or just Ubuntu? In the fresh install how did you partition? How did you use the "GRUB boot loader option"?

If you just did a complete re-install over exisitng partitions with a format and installed GRUB on the MBR I'm puzzled about this error.

A good resource page for GRUB problems is here : [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

---

### Post by interse on 2006-01-11
kipper, you were right!  What the *****?  Actually I found that information as well.
  First: I want to get back to Ubuntu in the worst way.  But to try to overcome the Grub Error 18, I reinstalled Windows 98 complete with formatting, of course.  Then tried Breezy.  Error 18.  Also tried Suse 10.0, error 18.  A few hours ago, I tried Fedora Core 4 and all was well.  Did I see 'Grub 2' flash by in FC 4?  I do not want to be in FC4, though now I can continue my work, as I had backup all of my files before the crash that I caused.
  
Hardware:  Asus Mother Board A7S8X-MX Series, AMD Athon XP/Sempron Processor, 512 DDR RAM, 40 GIG Seagate HD  Boot sequence:  CDROM, HD.  

I had the computer built and it came with Win. 95 (the builder knew I was going to devote the machine to Linux.)  I installed Ubuntu 5.04 w/o a hitch and later, upgraded to Breezy 5.10, again w/o problems.  Recently I installed a second hard drive which had Kubuntu on it.  I DID NOT install it to use Kbuntu, but rather as an 2nd drive for storage of backup files.  I had to learn how to activate the second drive.  It placed into /etc/fstab as  /dev/hdb1/second_drive    Yesterday, I tried to clean up, remove the Kubuntu files on hdb1.....too aggressively, obviously.  The whole installation crashed.  My fault!

I now have successfully installed FC4, just to see if any distro could be installed.  I do want to return to Breezy.

As always, I have tried to install Breezy with a clean install and following all of the defaults, i.e. Breezy takes the whole disk.

Can you help me?

---

### Post by Kipper on 2006-01-11
OK, so FC4 installs. It's true there is a new version of GRUB in development, called GRUB2. But I was not aware it was in use.

Anyway your M/board has both SATA and standard IDE controllers I think.

So which type of drive were your trying to install Ubunutu on? And as you now have two drives in your system, how do plan using them?

---

### Post by interse on 2006-01-11
I have two IDE drives, but, I have disconnected the slave drive.  It has Kubuntu on it from long ago, which I never could get to function as a choice in GRUB.  My intention is, now, simply to get back to Ubuntu on the first drive and maybe someday in the far future connect the 2nd drive and then carefully delete the files on it OR even reformat it as ext3.  That day will be when I have considerably more knowledge.  The thread of this undertaking is under my name, about 3 days ago, in Hardware Help.

---

### Post by Kipper on 2006-01-11
Ok, so you just had two IDE drives attached to the same IDE controller in a master slave set up. Assuming you had the jumpers set up correctly on the drives, this should have worked. 

Now you have returned to using just one IDE drive only, have you checked the jumpers settings on your single drive are as they were before you had the two working together.

Did you make any changes to your BIOS when you did all this, apart from  changing the boot order? Particularly in the section that deals with hard drive detection.

---

### Post by interse on 2006-01-11
The slave was jumpered as slave.  I simply removed the cables and left the drive in place for that day in the future.  When I installed it a few days ago, it was seen by Disks Manager (something missing in FC4) and I was shown how (thread in Hardware 3 days ago) to mount it in /second_drive.   Nothing at all was done to the main drive at any time.  Also, FC4 is working fine now so it appears to me, at least, that the drive is detected, etc.  I simply want to return to Ubuntu, desperately.   In the past, I recall having a problem like this which required me to make several attempts at installing 5.04 before 'it took.'  [Something like the proverbial monkeys at the typewriter].

I have been reading on Grub 18 and there are suggestions to set up a partition for the GRUB loader, /boot  (?).  I am likely not knowledgeable enough to get into specific partitioning w/o step by step instruction.  I have also read that it is a good idea to have a separate partition for data storage, again something I would like, but my knowledge level at this point is lacking.

---

### Post by Kipper on 2006-01-11
Ok, as FC4 works but Ubuntu does not, this might suggest a fault in the install process of Ubuntu or the version of GRUB used. Otherwise I don't know what's causig your error 18 as your hardware/BIOS set-up seems to work. 

I assume all of your hard drive capcity is being seen and not just apart of it. If this happened to be a problem then you might need a BIOS update.

If you don't want to keep FC4 you could try an "expert" install of Ubuntu on your master drive and choose to install GRUB on a floopy disk. Not ideal perhaps, booting from a floppy drive is a bit slow. If you choose to do this, you will need to create a root user and standrad user during the install process to ensure the bootloader is installed on /def/fd0, that's the linux name for your floppy drive. 

Otherwise, I'm out of ideas apart from leaving FC4 where it is and putting your second drive back. Install Ubuntu on that and then get FC4 GRUB to boot Ubuntu. You know how to get the two disk working, and in theory there should only be onle file to edit on the FC4 install to get it to boot Ubunutu.

Whatever you do, I'll try to offer help.

---

### Post by interse on 2006-01-11
Thanks for the offer of continued support.  I too am at a loss, since I did have Ubuntu installed and running on this computer a few days ago.  I am quite confident that I did see Grub 2 as Fedora was setting up.  

Suse 10.0 also creates the Grub Error 18.  Since this computer is for Linux, ultimately for Ubuntu again, I may just keep trying to reinstall.  

Could you perhaps give me detailed information on the suggestion, which I am sure I have seen, to install GRUB on a partition of its own so that the parameters, discussed in that cryptic explanation of ER 18, are not exceeded???

Right now I am quite reluctant to re-connect the second hard drive.

---

### Post by Kipper on 2006-01-11
To create a boot partiton on which you can install GRUB, you need to use the "expert" install. Create the appropriate partitions with the partitioner. Make sure you create both a root and standard user. At the install bootloader stage of the install you will be asked to enter the place you want to install GRUB. If for example you created a /boot on the third partition of your hard drive, Linux would refer to this as /dev/hda3. That's what you enter as the place to install GRUB.

See this webpage for details for how to use the partitioner to create a sepcific partition. 

[http://www.users.bigpond.net.au/hermanzone/p14.htm](http://www.users.bigpond.net.au/hermanzone/p14.htm)

They use the example of a /home partition. Same method, but make sure your mount point is called /boot, and the size of the partition will be very small, 50MB is enough. The partitions scheme to aim for is something like:

/
/boot
/home
/swap

You can do without /home. but not the others.

To avoid having to enter all these partions manually, you can use the "guided partioning" to set up the basic partitions and then just add the /boot partition manaully.


Hope that helps.

Back tommorrow.

---

