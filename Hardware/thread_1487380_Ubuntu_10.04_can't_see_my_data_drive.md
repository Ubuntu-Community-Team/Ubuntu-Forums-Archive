---
title: "Ubuntu 10.04 can't see my data drive"
date: 2010-05-18
forum: Hardware
---

### Post by sanddgroper on 2010-05-18
Hi All
I have a 160GB and a 500GB samsung sata drives.The 160GB has the OS
and the 500GB is my backup data drive.At present 10.04 does not see
my 500GB drive on boot.I know it was seeing the drive when I first
installed 10.04 because I transfered all my files from the data drive
to the OS drive.
The thing is that if I boot from the live CD it sees both the drives
on the system.
Also a check in dev/disk/by-id seems to show the existance of a 500
drive.
So is there a nice little piece of command line magic I can apply to
get 10.04 to see this drive again.

Thanks

---

### Post by Phrea on 2010-05-19
Have you tried mounting it using the Disk Utility? [System --> Administration --> Disk Utility]

---

### Post by sanddgroper on 2010-05-19
Thanks for the reply.
No I had not tried that.
But when I do try to mount it using the Disk Utility I get this

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed.

What this means I have no idea other than it thinks it is already mounted.
Another question would be why the drive shows up in the disk utility but
not in Places-->Computer.

---

### Post by sanddgroper on 2010-05-19
Anyone have any idea of the error message above.

Thanks

---

### Post by munky99999 on 2010-05-20
In disk utility there where you get the Error mounting:

Click on Filesystem check first. It'll pop up as clean. Then mount and should go fine.

I believe there is an error in fstab that makes this a problem. 

I havent tested this hypothesis though.

---

### Post by sanddgroper on 2010-05-22
Thanks munky99999 but that did not work.Still the same
error message.
I had a look at my fstab file and I noticed this

/dev/sda1       /               ext4    errors=remount-ro 0       1

The thing is fstab is looking for a Ext4 file system but the
file system on the disk is ext3 even the disk utility mentioned
above sees it as ext3.

What would be the best to do.
1 comment out the line above in my fstab file or
2 errase my fstab file.Will it build a new one on reboot.
I notice when I boot the system using a live CD that the
fstab file for the live CD does not mention any off the
attached drives but they show up just fine under Places
Any suggestions most welcome.

Cheers

---

### Post by joshedmonds on 2010-05-22
Do not erase your fstab!

---

### Post by sanddgroper on 2010-05-22
Ok folks commenting out the line.

/dev/sda1 / ext4 errors=remount-ro 0 1

Seems to have fixed the problem.

Thanks

Cheers

---

### Post by moxxx on 2010-07-09
Guys, I'm less than 24 hours into my Ubuntu life and having the same problem. Can someone explain the last post to me?

I've tried a few different things, including [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263) (Couldn't find any package whose name or description matched "ntfc-config"
) but can't get the thing to mount.

I've been solving small problems here and there on my own but this one has me stumped. Any help would be greatly appreciated.

eta: In Disk Utility, when I try to mount, I get "An error occurred while performing an operation on "echo" (Partition 1 of ATA WDC-rest of drive name): The operation failed"

And when I check the filesystem it says it is NOT clean.

---

### Post by oldfred on 2010-07-09
Most tools in linux stop working on NTFS partitions if they have errors.
You need to go into windows and run chkdsk to fix the partition.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

