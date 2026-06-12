---
title: "Difficulties with read-write permission  hard drive"
date: 2015-10-03
forum: Hardware
---

### Post by tschill on 2015-10-03
Hi there,

I tried to use an external hard drive with Ubuntu 14.04. Usually they mount without problems. But this Seagate 3 TB drive was formatted on an Apple computer and was only mounted with read permissions. The "owner" is defined as user#99. I tried to access it as root to change the permission and get the information, that the drive is read-only. 

I had a look what kind of advice I could find on the internet. I came across these threads [here]("https://askubuntu.com/questions/333287/external-hard-disk-read-only") and [here]("https://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write#"). So I installed hfsprogs and re-mounted the hard drive. Funny thing is that mount -l shows a change in the output (from "/dev/sdb2 on /media/mydevice type hfsplus (ro,nosuid,nodev,uhelper=udisks2)" to "/dev/sdb2 on /media/tschillin/DALEK type hfsplus (rw,force)") and indeed it now shows the option to create a new folder on the hard-drive. But, alas, when creating this folder, the system says, the device is still read-only. I am able, though, after these fiddlings to write on the disk as root, but this is of course not a feasible solution.

I am afraid the problem is the journaling by MacOSX for the hard drive. It was  mentioned that Macs hard drive journaling has to be disabled, otherwise Ubuntu can't write on the drive. Mac's disk utility says it is journaled and so does the output from 

```
sudo fsck.hfsplus /dev/sdb2
** /dev/sdb2
** Checking HFS Plus volume.
fsck_hfs: Volume is journaled.  No checking performed.
```

 Using two different Macs, I tried to remove journaling, but the option to remove it was greyed out on these Macs. Another dead end.

Soooo, here I am and so close to format the drive. Unless there is another possibility. Any suggestion is welcome.
Thank you in advance.


Edit: OK, it is not the drive journaling. I managed to turn it off (in Macs disk utility you have to hold the Option (=Alt) key while opening the File menu, arrr). 
So now the hard drive is automatically mounted as "/dev/sdb2 on /media/mydevice type hfsplus (rw,nosuid,nodev,uhelper=udisks2)". That looked promising, but still it says the destination is read-only. Mhm.

---

### Post by weatherman2 on 2015-10-03
What are you planning to do with this drive?

If you will use it with other Mac computers in the future, you may want to stick with HFS Plus but disable journaling.  However, you may still have a lot of fun trying to get Ubuntu to write reliably to it.  I'm sure it's possible, but I recently tried to do this and gave up after only a short time.

If you will use the drive only with Ubuntu, format it as ext4 and save yourself any future headaches.

As a compromise, format the drive as ext2, a Linux format without journaling.  Then you can install something on any Mac that needs to access the data that allows the Mac to access ext2 volumes.  Not sure about WRITING to ext2, though.  I can tell you that I could not get Mac OS to write to ext4 after some time trying.  ext2 is older and simpler so better supported in different OS's.

---

### Post by tschill on 2015-10-03
Uh, that sounds like my experience. :shock:
2 TB are occupied on this drive and need to be backed up somewhere before formatting. Also I wanted to keep cross-platform compatibility, but with every minute I waste on this problem, this becomes less important. Who needs Macs, anyhow?

---

### Post by tschill on 2015-10-03
Don't give up...

After disabling journaling on the hard drive, I changed the permission for the hard drive to my profile. I used ALT+F2 -> gksu nautilus to have root access for this operation. It still didn't accept me to write to hard drive. But - after a restart of my Ubuntu computer, the drive was mounted as a read-write ("/dev/sdb2 on /media/mydevice type hfsplus (rw,nosuid,nodev,uhelper=udisks2)") and I now I am able to write on it. Hooray! It also still works on Macs. 

Only question remaining - is writing on this hard drive now restricted to my Ubuntu profile? Is there a group permission that allows all registered profiles to have a read-write permission?

---

### Post by weatherman2 on 2015-10-03
Open a terminal window (Ctrl Alt t) and type:

```
sudo ls -lrta /media/USERNAME/mydevice
```

(or just "/media/mydevice" for Ubuntu 12.04 )

Replace "USERNAME" with yours, obviously and replace "mydevice" with whatever yours is.

You' get an output like:

```
-rwxrwxrwx 2 username username 123 Oct 3 15:00 .
```

If instead of "-rwxrwxrwx" you see dashes, that means there is no permission for that group (the last three "rwx" is for "Other").

Both Linux and Mac OS are Unix derivatives with file system security groups of owner, group, and world - you can set read, write, and access (to execute programs) for each group.

But I'm not sure how the user/group permissions would be translated between Linux and Mac OS.  However, if you don't mind allowing anyone to write to the drive, you can always set  "Other" (i.e.. anyone) read/write permissions, with this terminal command:

```
sudo chmod -R o+rw /media/mydevice/ 
```

That should open up writing for everyone, on any operating system.

---

### Post by tschill on 2015-10-04
Thanks, I changed it now for the relevant folders. Afaik MacOS has the same order - owner - staff(=group) - everyone (=others). 

Accidentally I stumbled across the function that Linux automatically adds in the Terminal all missing characters in /folder1/folder2/fileXYZ, when you hit TAB (and there is no ambiguity which path or folder you want to access). Very neat.

As always, it was a pleasure to ask for help here.

---

