---
title: "Western Digital external hard disk"
date: 2019-07-29
forum: Hardware
---

### Post by christon74 on 2019-07-29
Good morning fellow Ubunters_ O:)_ I have had this problem for a few days now. Some files cannot be opened (please see attachments) or I cannot write new files to the destination folder I have chosen. I have checked the cables, everything is correct. I have read about some special usb shielded cables for external hard disks. Do you think I should buy one?
Thanks in advance for any tip. Have a nice Monday.

---

### Post by Bashing-om on 2019-07-29
christon74; Hello :)

Any time I see " input/output error" I run a file system check.
The target must not be mounted when the check/repair is run.

run:
```

sudo fdisk -lu

```
to know the target.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
see:
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting) <- Basic filesystem checks and repairs
[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

To run the check is cheap insurance,

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by christon74 on 2019-07-29
Hello Bashing-Om O:) and thanks for the answer. Since I am on dual boot (Ubuntu/Windows 7) I have used the chkdsk utility with the sectors repair option. It takes a mighty long time, but I ran it until completion this morning. And now, everything seems back to normal. I have saved a screenshot of the answer you have posted. So now I think I can mark this thread as solved. Thanks again.

---

### Post by Bashing-om on 2019-07-29
christon74; Great !

You do good work :)

Better that it is just a file system fault and not hardware failure :)

[INDENT]help is what we do
[/INDENT]

---

