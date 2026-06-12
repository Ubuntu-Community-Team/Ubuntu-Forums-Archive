---
title: "Mounting NTSF Drives"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by eskemojoe007 on 2005-01-30
When trying to mount my windows ntsf drive (hda1) i encounter a variety of problems.  First, the mount in the terminal worked, but i when i went to open the folder i was denied access.  Later, i tried again and the terminal prompted that my kernel didnt support ntsf.  I am a linux newbie but have tried to contact some of my experts and they have no idea what is going on.  As far as i know linux should support the reading of my NTSF drive.

Thanks,
David

---

### Post by lt_kije on 2005-01-30
Can you post the commands you issued to mount the drive? I'll assume you did the following in the terminal:

$ sudo mount /dev/hda1 /some/folder

where /some/folder is the part of the Linux filesystem you want to plug your hard disk into. FYI, I believe NTFS is mounted read-only -- if you found you were unable to create a folder on the disk while running Ubuntu, this is likely the problem (I can't quite tell from your post whether you mean that you couldn't view an existing folder or create a new one).

To check and see if the disk was mounted, use the following command:

$ mount

If /dev/hda1 appears in the list, the disk is mounted. Try to navigate to the folder you mounted the disk to (eg /some/folder) using the following command:

$ cd /some/folder

If you still have trouble, please post the exact commands you use and the feedback you get.

Good luck!

lt_kije

---

### Post by eskemojoe007 on 2005-01-31
Initially i tried what my friends told me, 

$ sudo mount -t ntsf /dev/hda1 /windows

and got this response in my terminal

mount: fs type ntsf not supported by kernel

After trying exactly what was online:

$ sudo mount /dev/hda1 /windows -t ntsf -o umask=0222

I got the same response.  When trying what you suggested the mount appeared to work in terminal but when the "windows" folder poped up a error message came with it saying:

The folder conents could not be displayed
you do not hav the permissions necessary to view the contents of "windows."

When i used the mkdir command to create the folder all i did was

$ sudo mkdir /windows

But the folder actually seems to be (acording to the file system) in /mnt/windows.  As of now i am royally confused and have no ideah what is going on.

Thanks for you help,
David

---

### Post by eskemojoe007 on 2005-01-31
Sorry for the confusion as it turns out i have a /mnt/windows from the time a buddy helped me and a /windows.  So either should work and i have no preference to which it should go.  Also when looking at the properities - permissions it only has the "write" box checked for owner and at the bottom of the window its says "you are not the owner, so you can't change this permissions."  I AM THE OWNER.  How do i fix this?

Thanks again,
David

---

### Post by Grey on 2005-01-31
Man, I've been in your position so many times, it's not even funny.  ;)  But I think I am beginning to get the hang of things in Linux.  I can function fairly normally in it now... short of having NTFS write access, and access to my bloody RAID-0 Array.  (but I'm working on these).

What you want to do is to edit the fstab file in /etc.

1)  Open up a terminal window, and type "sudo gedit /etc/fstab"

This is a file that's loaded when Linux starts.  It's responsible for mounting your hard drives.  All you have to do is add this line to the file (after deleting any of the lines that reference /dev/hda1).

/dev/hda1       /mnt/windows     ntfs    auto,umask=0,ro 0       0

This mounts /dev/hda1 in /mnt/windows, with ntfs file system, it will be loaded up automatically when Linux starts, and it's open to all users in readonly mode.

After you've added this line, reboot, and go to town.  It will be perfectly accessable to your user account now.  :)

---

### Post by crane on 2005-01-31
I added the following two lines to my fstab:

/dev/hda1       /windows/system    ntfs    umask=0222      0       0
/dev/hda2       /windows/games    ntfs    umask=0222      0       0

This allowed me access to but windows drives and is automaticly mounted at boot.

---

### Post by eskemojoe007 on 2005-02-01
Thanks Ya'll!  It worked beautifly.  I am soooo super happy and very excited.

Thanks,
David

---

