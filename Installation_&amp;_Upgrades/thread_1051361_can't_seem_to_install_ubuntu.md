---
title: "can't seem to install ubuntu"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Fertech on 2009-01-26
i can't seem to install ubuntu in my maxtor diamondmax 21 320gb pata. does ubuntu supports big hard drives. like i said my hard drive is 320gb. i try it with a live cd, and try to boot from the cd, but it stop where it says loading and it says there. im thinking is cause of the size of the hard drive, but i can be wrong. does anyone has any info on this problem.

---

### Post by Therion on 2009-01-26
The drive capacity shouldn't be a problem.  Are you sure you're working with a good burn of the .iso file?

See this tutorial to make sure you have a good install CD/DVD to work with:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by spcwingo on 2009-01-26
I doubt very seriously that it is HD related.  Have you tried installing from the alternate CD?

---

### Post by Fertech on 2009-01-26
i try to install windows xp and it gave me a blue screen with this error. plug and play detected an error most likely cause be a faulty driver. stop 0x000000ca (0x00000001, 0x84375378, 0x84375628, 0x00000000. i download a iso file for maxtor to test the hard drive, and short and long test pass. i try to install windows 2000 and that was a success, only problem i dont want windows, i want ubuntu. if i take the hard drive out and run the live cd ubuntu it works, if i install the other hard drive that i have maxtor 40gb it works, but when i install the 320gb HD it fails. what i'm think is the hard drive is not working well, cause i did delete everything with the same iso file i tested the hard drive. im just confuse cause the test did pass.

---

### Post by Fertech on 2009-01-27
take a look at this pic. i have no clue whats going on. has anyone seen this error before.

[http://c2.ac-images.myspacecdn.com/images02/12/l_984af728fd9647d2848af5c3f658e849.jpg]("http://c2.ac-images.myspacecdn.com/images02/12/l_984af728fd9647d2848af5c3f658e849.jpg")

[http://c1.ac-images.myspacecdn.com/images02/33/l_192464076c5b4e49a7f76f0a1bc4f890.jpg]("http://c1.ac-images.myspacecdn.com/images02/33/l_192464076c5b4e49a7f76f0a1bc4f890.jpg")

[http://c2.ac-images.myspacecdn.com/images02/12/l_7e6144109f274b38b8f9fa5c08ab4cb1.jpg]("http://c2.ac-images.myspacecdn.com/images02/12/l_7e6144109f274b38b8f9fa5c08ab4cb1.jpg")

[http://c2.ac-images.myspacecdn.com/images02/4/l_2642649d068c4989ae8e3eb305094a9d.jpg]("http://c2.ac-images.myspacecdn.com/images02/4/l_2642649d068c4989ae8e3eb305094a9d.jpg")

---

### Post by Fertech on 2009-01-27
oh i found the problem, i'm checking the cd for errors, so far i found 4 error in the files. how did it get error. i used this cd 2 install on 2 other machines. im going to clean the cd and reboot. if this does not work il just burn a iso file.

---

### Post by Fertech on 2009-01-28
I did install ubuntu from a fresh copy, but when i reboot my computer, and try to boot up from the hard drive it gives me a error 18. i don't know what that means. some people say that is cause my bios wont see all my hard drive, and the kernel takes to long to boot up so i get that error, but im not sure. any idea what this error 18 means.

---

### Post by glotz on 2009-01-28
[QUOTE=http://wiki.linuxquestions.org/wiki/GRUB#Error_18]  Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. [/QUOTE]

Also, this thread contains some suggestions. [http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764)

---

### Post by Josh_Lapointe on 2009-01-28
Here's something I found.

[http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764)

Direct Quote:
--------------------------------------------------------------------------------

Look in your bios and see if there is an option for Master and Slave disks. If it says none turn it on. Another thing is to make sure Grub installs itself during installation into the MBR (master boot record). Another thing is to update the bios because when grub tells the bios how large the disk is, the bios says "I don't handle disks that large". 
Any one of the 3 could be the solution.

Selected cylinder exceeds maximum supported by BIOS.

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Hope this helps.

---

### Post by Fertech on 2009-02-22
this problem has been solved. It was the DVD player, i added a second DVD player , and i was able to install it. thats why i got an error when i check the cd for defects. need to clean my other dvd player. hope this information helps someone else.

---

