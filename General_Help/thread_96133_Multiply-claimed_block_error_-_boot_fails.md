---
title: "Multiply-claimed block error - boot fails"
date: 2005-11-28
forum: General Help
---

### Post by stuoolong on 2005-11-28
The other day my computer failed to boot. It said it had run fsck because there had been no filesystem check after 100 logins or something, when running fsck it found multiply-claimed blocks. 
Took me a while to work out what this meant, it gave the names of twof iles and I think it means they had both been installed into the same section of the hard drive. 
So it told me to log in as root, and to mount the filesystem using:

# mount -n -o remount,rw /

Which I did, then it said to run the fsck manually, without using the -a and -p options. I have no idea what this means but I typed fsck, which resulted in a warning saying that running this program on a mounted filesystem will probably result in major damage. Frightened, I decided to take the easy option and delete one of the files - I recognised one of them as being part of a game I no longer use, so I knocked out the whole directory:

# rm -rf "directory name"

On reboot, fsck ran again, said it had fixed some errors, and forced another reboot. Now everything seems shipshape.

My question is though, how do you prevent this kind of error happening? Is it a bug in the way Synaptic has installed one of the packages? Does Linux have an equivalent of Windows' Defragger?
And could I have saved both files?

---

### Post by babygigi on 2005-11-28
i'm having the same problem right now... can u go through it and explain what u did?

---

### Post by ymcp on 2005-11-29
Hi.  I had a very similar problem recently.  This is what I did to fix it:

After (I think) 30 system startups, a fsck was forced.  It failed & left the system with a console root prompt.  The error messages were something like:

> root file system error
duplicate or bad block
multiply-claimed blocks inode 3335957.32768
file /lib/modules/2.6.12-9-386/kernel/drivers/video/console

After reading everything relevant that I could find on google, I ran the following command:

> #e2fsck -c -y /dev/hda1

Some articles claimed that this command should not be run on a mounted root partition.  Other claimed that it was OK as long as it was only mounted read-only.

This seems to have done some sort of repair, and the system now boots fine.  However, use at your own risk... I don't really understand what it did.  Something about creating duplicates of bad blocks.

I am a bit concerned that some of my files might be corrupted.  Can anybody advise?

Thanks.

---

### Post by stuoolong on 2005-11-29
babygigi - 

The prompt told me to enter the root password, then remount as rw, giving me the command I listed above. 

Since I knew that one of the files listed was expendable (the game file) I simply deleted it as printed above. Then I rebooted.

I did not know what the other file was, and it looked like it might be important. If both the files are important ones, that is where I get stuck. Now I think about it, it does make sense what ymcp has done - if the drive is in read only status, you can't delete anything and fsck just rearranges the data. 

Anyone out there understand this better?

---

### Post by stuoolong on 2005-11-29
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by stuoolong on 2005-11-29
Looking briefly at the man pages, it seems that e2fsck differs from fsck in that it works specifically with an ext2 or ext3 file system, whereas fsck can work with any file system.

---

### Post by babygigi on 2005-11-30
Well i just typed in fsck and it asked me a few questions all which i just answered yes and now it works so yay! thats all i did...i wonder what went wrong.. anybody know?:???:

---

### Post by stuoolong on 2005-12-03
*bump*

---

