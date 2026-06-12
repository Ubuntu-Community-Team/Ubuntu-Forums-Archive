---
title: "[SOLVED] What is wrong with my file system?"
date: 2008-11-06
forum: General Help
---

### Post by Dave54 on 2008-11-06
I booted up my computer into ubuntu and got some error messages. I ran "sudo -f fsck" for each of my hard drives, and everything looked fine. I reboot, and get the same error message: (it's at the command line so I wrote down everything I could see)```
     e2fsck -b 8193 <device>

1ter: recovering journal
500gig: clean, 29479/61063168 files, 71967058/122096000 blocks
1ter: clean, 5816/122109952 files, 178772650/244190000 blocks
fsck died with exit status 8
                                            [fail]
 * File system check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
 * A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing:
apt-get install apt
bash: apt-get: command not found
root@dave-comp:~#
```Here's the log found at /var/log/fsck/checkfs:```
Log of fsck -C -R -A -a 
Thu Nov  6 13:21:13 2008

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sdc1
/dev/sdc1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

1ter: recovering journal
500gig: clean, 29479/61063168 files, 71967058/122096000 blocks
1ter: clean, 5816/122109952 files, 178772650/244190000 blocks
fsck died with exit status 8

Thu Nov  6 13:21:13 2008
----------------
```I don't know where to start to fix this. Can anyone tell me what this means?

---

### Post by snova on 2008-11-06
Your filesystem appears to be corrupted, though precisely how should be recorded in /var/log/fsck/checkfs. Though how you're going to access that is a tricky question...

Do you dual-boot? Try to access your Ubuntu partition from Windows (you'll need Ext2 drivers for Windows) and find that file, then post it.

---

### Post by Dave54 on 2008-11-06
> **snova said:**
> Your filesystem appears to be corrupted, though precisely how should be recorded in /var/log/fsck/checkfs. Though how you're going to access that is a tricky question...

Do you dual-boot? Try to access your Ubuntu partition from Windows (you'll need Ext2 drivers for Windows) and find that file, then post it.

Thanks for the help snova, bit it looks like you missed a part of my post. Yes I do dual-boot, Yes I do have an ext2 IFS driver installed in windows, and that's how I posted the log you're looking for in the first post.

Oh, something I forgot to mention. If I press CONTROL-D (as the instructions say) to exit, Ubuntu finishes booting up no problem.

I am posting this from windows because I don't want to risk any further damage.

---

### Post by snova on 2008-11-06
> **Dave54 said:**
> Thanks for the help snova, bit it looks like you missed a part of my post. Yes I do dual-boot, Yes I do have an ext2 IFS driver installed in windows, and that's how I posted the log you're looking for in the first post.

Oh, duh. :p

Well, somehow the superblock was corrupted. Fixing it... Well, it gave you a command. Try booting into recovery mode and running it.

```
e2fsck -b 8193 <device>
```

By the looks of it, <device> is /dev/sdc1. It should be safe to run even if it isn't, since -b just tells it to use an alternative superblock.

---

### Post by Dave54 on 2008-11-06
> **snova said:**
> Well, somehow the superblock was corrupted. Fixing it... Well, it gave you a command. Try booting into recovery mode and running it.

```
e2fsck -b 8193 <device>
```

By the looks of it, <device> is /dev/sdc1. It should be safe to run even if it isn't, since -b just tells it to use an alternative superblock.It didn't work. Here's what it said:```
root@dave-comp:~# e3fsck -b 8193 /dev/sdc1
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: No such file or directory while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@dave-comp:~#
```[COLOR="Silver"]I know that /dev/sdc1 is the drive named "1ter" (it's 1 terabyte big). If you look in my first post, it says:```
1ter: recovering journal
...
1ter: clean, 5816/122109952 files, 178772650/244190000 blocks
```I wonder why it says it's clean if it's having so much trouble?[/COLOR]

I can read all the data on /dev/sdc1 with no problem in both Ubuntu and Windows.

Any other ideas?

Oh, before you send me to recovery mode again, please tell me:
1. How do you make it scroll one page at a time? "shutdown --help" is not very helpful if you can only see the very bottom...
2. How do you shut down? "shutdown -now" didn't work, and since I was root, sudo didn't help either. (I had to resort to ALT+Sys Rq + r,s,e,i,u,b. I hope I didn't further corrupt my drive :( )

---

### Post by snova on 2008-11-06
> **Dave54 said:**
> 1. How do you make it scroll one page at a time? "shutdown --help" is not very helpful if you can only see the very bottom...
2. How do you shut down? "shutdown -now" didn't work, and since I was root, sudo didn't help either. (I had to resort to ALT+Sys Rq + r,s,e,i,u,b. I hope I didn't further corrupt my drive :( )

1. No idea. Try piping the output through less, or more.
2. Try 'halt'. Assuming one of those commands is the command to sync/unmount, it should be fine.

I'm running out of ideas... I'm no FS expert.

It keeps saying the device file is missing... I thought it might have other causes, but maybe that should have been checked first. What's the output of "ls /dev/sd*"? Then we can be sure the device even exists.

What are the contents of /etc/fstab? Maybe it's trying to mount a drive that doesn't exist, and that's causing the error.

---

### Post by Dave54 on 2008-11-06
> **snova said:**
> It keeps saying the device file is missing... I thought it might have other causes, but maybe that should have been checked first. What's the output of "ls /dev/sd*"? Then we can be sure the device even exists.

What are the contents of /etc/fstab? Maybe it's trying to mount a drive that doesn't exist, and that's causing the error.I think you're right. After I said that /dev/sdc1 is "1ter", I booted back into ubuntu to double check. Turns out the live CD and the installed version named the drives differently. Here's the output of sudo blkid:```
dave@dave-comp:~$ sudo blkid
Password:
/dev/hda1: TYPE="ntfs"
/dev/hda2: LABEL="Linux" UUID="f6d48df2-897b-4741-832d-c29879f02c8b" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="781949e5-0975-4354-9334-9b0f176a3005" TYPE="swap"
/dev/sda1: LABEL="1ter" UUID="84d34cf0-3004-4fe9-a9eb-b242e2526bca" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: LABEL="500gig" UUID="0677f6f7-3f2c-4c3c-9246-e5009be5198d" SEC_TYPE="ext2" TYPE="ext3"
dave@dave-comp:~$
```Sure enough, /dev/sdc1 doesn't exist.
This must be a problem with my fstab. I can go though and proofread it on my own. Thanks for all the help, snova!

EDIT: It seems I have a hard time learning. Just found this from a year and seven months back: [http://ubuntuforums.org/showthread.php?t=415691]("http://ubuntuforums.org/showthread.php?t=415691")

---

