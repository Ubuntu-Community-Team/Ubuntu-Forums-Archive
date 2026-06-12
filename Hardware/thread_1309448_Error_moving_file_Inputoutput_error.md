---
title: "Error moving file: Input/output error"
date: 2009-11-01
forum: Hardware
---

### Post by soni1770 on 2009-11-01
yo, i have a 1tb external hard drive with some .avi on it, 
now i can't delete  some of the files,
i can copy the file to my laptop harddrive then copy it back with anew name, after which i can move or delete the renamed file, but the original remains stuck,  if i try to move it i get always the same Error moving file: Input/output error
any one any idea whats going on?
thanxs in advance

oh, i can still view the .avi with no problems? umm

---

### Post by jasonab on 2009-11-01
I'm a bit new to this myself but here is something you can try

Read: [http://www.tuxera.com/community/ntfs-3g-faq/#ioerror](http://www.tuxera.com/community/ntfs-3g-faq/#ioerror)

Next you can try to check for bad blocks. Check which device your drive is assigned to by running the mount command in terminal. It will be something like /dev/sdb1.

Next in the terminal, unmount the drive and run the fsck tool on the drive, that is if the drive is not partitioned in NTFS format, if it is you have to use the windows chkdsk utility.

unmount the drive:
>  umount /dev/sdb1
run fsck:  
> sudo fsck -pcfV /dev/sdb1

remember to replace /dev/sdb1 with the device location of your drive. Also for safety sake make sure you read the man page for fsck.

---

### Post by soni1770 on 2009-11-01
umount /dev/sdb1 			 		 	 	 run fsck:  
 	

 	 	 		 			 				sudo fsck -pcfV /dev/sdb1

so tried to sudo fsck it, but got some error messages,
then decided just to format the drive to ext4,m luckly i have another 1tb drive so backing up was not a problem, 
just some small issuse getting permission to write to the drive, solved with 

[B]gksudo nautilus 

[/B]how i'm copy all my files back, touch wood, it's looking good,

stop your rymen and i mean it,
anybody want a peanut

thanks anyway for the help :popcorn:

don't think i should mark this a solved cause maybe others can't just format,

---

### Post by jasonab on 2009-11-02
Glad you found a work around. Also thank you, I learnt a new command: gksudo

I'm sorry  the options for fsck differ from filesystem type. The c option above is to check for bad blocks which if you are checking a vfat system is supposed to be t. Also the capital V (print version info) should be a small letter v (verbose). I should have probably told you to use e2fsck first instead. Sorry about that.

---

### Post by soni1770 on 2009-11-02
all's well that ends well, 
take care

---

