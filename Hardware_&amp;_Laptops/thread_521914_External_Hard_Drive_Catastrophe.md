---
title: "External Hard Drive Catastrophe"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by Pitbull11188 on 2007-08-09
Ok I'm not sure exactly how to classify this problem so I hope someone can help me from this description:

I moved a bunch of files from my external hd, to another folder on the external hd. However, I didn't use the umount command and just pulled the wire out of the computer. So now the folder everything was supposed to be moved to is empty, and the files aren't located where they were previously. I know they're there still somehow b/c the space is still taken up on the hd.

My theory (based on nothing but uninformed logic):

The system never wrote the info to the new location, but since I "moved" the files they don't show up where they were previously. 

I really need help on this one if I can't get it fixed I'm going to lose my entire music collection, vacation pictures, and a ton of research papers that I would love to have for college. Basically irreplaceable stuff. Please help.

---

### Post by merlinus on 2007-08-09
Are you accessing the drive from ubuntu or windows?  Try doing it with the other OS.

In my experience, if the files are not moved successfully, they will not be deleted from the original source.

-merlin

---

### Post by Pitbull11188 on 2007-08-10
I tried from both and no luck.

I have no idea what to say other than I cannot see the files and they're not listed, but do to the 80gb hd having only 35mb free space and only 1gb of visible files they have to still be there.

---

### Post by merlinus on 2007-08-10
Not that I expect this will change anything, but have you tried View/Show Hidden Files?

Also, you might run chkdsk <drive letter:> /f from windows to see if there are errors and fix them.

-merlin

---

### Post by Pitbull11188 on 2007-08-10
Yes I've tried that and nothing. 

This is basically a plea for help if anyone has any ideas please tell me. I can't afford to lose this info. I know I should have had it backed up and I normally do but I had to reformat my main computer so I figured I'd copy everything over once I was done, but this incident occurred while the other computer was reformatting and I was using the hd between my laptop and family computer.

I didn't safely remove it and I think that has something to do with the problem.

---

### Post by merlinus on 2007-08-10
You might try a rescue/restore live cd:

[SIZE=-1]www.sysresccd.org/

or knoppix:

[/SIZE][SIZE=-1]www.**knoppix**.org/ 

-merlin
[/SIZE]

---

### Post by EndPerform on 2007-08-10
I'm taking it this is an NTFS formatted drive?  If so, it might be worth a shot to boot into Windows and see if you can find a file undelete utility that might help.  I don't have the names of any handy since I use Linux 99% of the time, but that's the only thing that comes to mind right now.

---

### Post by Pitbull11188 on 2007-08-10
No it's Fat32, I use it exclusively for linux 99% of the time, but kep it Fat32 in case my parents needed to use it for windows. I'll try knppix now.

---

### Post by Pitbull11188 on 2007-08-10
I just checked it using knoppix and it was a no go.

---

### Post by merlinus on 2007-08-10
Give sysrescuecd a try.  Link in previous post.

It has lots of tools.

-merlin

---

### Post by Pitbull11188 on 2007-08-11
How would I go about using the rescue cd I have it on cd now but once I put it in which programs should I run. All I know is the info is on the disk, but not accessble to me.

---

### Post by Pitbull11188 on 2007-08-14
Does anyone have any ideas?

---

### Post by merlinus on 2007-08-14
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This app is on the sysrescuecd.

-merlin

---

### Post by K.Mandla on 2007-08-14
You might also try Rescubuntu.

[http://ubuntuforums.org/showthread.php?p=3147679](http://ubuntuforums.org/showthread.php?p=3147679)

I don't know what luck you'll have. If you yanked the cord before it released it, then the cached data might still have been writing. I don't know for sure, but I've had awful luck losing information (in Linux and Windows) when I pulled the drive before it was done caching out. ...

:(

---

### Post by Pitbull11188 on 2007-08-14
The information was 100% done writing, I just didn't use the sudo umount /media/disk command, I simply pulled the plug.

---

### Post by Pitbull11188 on 2007-08-15
Shameless Bump, my life is on this HD someone please at least give me a link to another place where I can get some help.

The drive still has the space used by the data, I just can't access or detect the data. 

Someone please help! :confused:

---

### Post by tgalati4 on 2007-08-16
I assumed you checked  .Trash to see if any files are there.

---

### Post by Pitbull11188 on 2007-08-16
Of course, but thanks for replying.

---

### Post by tgalati4 on 2007-08-16
What is the output of:

fsck /dev/hda

(Be sure to answer no to any repairs suggested.)

It's possible that you have orphaned data chains that may be converted to files.  This is not helpful, because it will fragment any remaining data into small pieces.  It's OK for retrieving text files, but music or photos become toast.

I know that under Dapper when you move large blocks of files, the system gives you the impression that they are moved, but they are really sent to the background where they get processed much slower.  This gives you a responsive desktop for doing other things, but it gives you a false impression that the data has been moved.  I've been burned a few times using an mp3 player and pulling the plug thinking that the music files were transferred only to find that only a handful got transferred.

I don't know if Edgy behaves the same way.

We are going on the assumption that since the disk says that it is partially used, that there must be data on it somewhere.

Since this is a FAT32 disk, Norton Disk Doctor may be helpful.  Ask around, someone has a disk that you can borrow.  If the FAT got messed up, Norton is pretty good at restoring it so you can start to retrieve files.

---

### Post by eric a on 2007-08-16
Not sure what the directory is call on linux, but check the .lost+found directory on the drive. See if you have any files and/or directories with files inside of there. This is where fsck puts unlinked files after repairing a damaged file system.  The files and directories recovered by fsck will be named with the inode number, so you prbably won't find anything named like myphoto.jpg. It will probably be named something like 1232178. Good luck

---

