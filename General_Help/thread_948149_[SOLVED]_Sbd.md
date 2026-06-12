---
title: "[SOLVED] Sbd"
date: 2008-10-14
forum: General Help
---

### Post by TaskmasterC on 2008-10-14
I made the SBD, but am not sure how to use it. Please advise, also, will it have to stay in the drive from now on?

---

### Post by cariboo on 2008-10-15
What is SBD? A little more information would be helpful.

Jim

---

### Post by TaskmasterC on 2008-10-15
Im sorry, the Super Boot Disk. Someone told me to make it, and it would fix the problem

---

### Post by jerome1232 on 2008-10-15
Wouldn't it be a better Idea to post in your original thread where you were advised to use it? 

Otherwise a link to the original thread and maybe some more info would be helpful, like what is the problem?

---

### Post by TaskmasterC on 2008-10-15
Sorry, I am to new to this. The original post is titled grub problems. I keep getting error 17 when I try to load linux. I had to reload Vista and it knocked out the grub loader. I did as I was told and now get the loader screen, gut linux will not load. It gives error 17, then nothing. I am not sure how these threads work, so if this message is also in the wrong place, I appologize. Thanks for any help you can offer.

---

### Post by jerome1232 on 2008-10-15
Okay I have never used the Super Boot Disk before but I know you should be able to accomplish this from an Ubuntu live cd, I've done it before.

Just follow this guide and it should get you straightened out, If you aren't sure about something feel free to ask questions before you try something.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by TaskmasterC on 2008-10-15
ok, I did that, and this message came up.....


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ade5528

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12794   102767773+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb3           12795       38536   206772615    7  HPFS/NTFS
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

---

### Post by jerome1232 on 2008-10-15
After entering 'sudo grub' you should have gotten a prompt like this
```
         [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```

Did that not happen?

I've never had this not work for me so The last suggestion I have is to try some methods outlined [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") The first method is what I had you try (explained a little better on this link too), take a look at the other methods as well.

hope that helps.

---

### Post by TaskmasterC on 2008-10-15
Yes sir, I did get that screen. The last screenshot was what came up after I did the outline. I am going to try to reboot without the disk and see what happens. I will let you know. Oh, thanks for taking the time to help me, I appreciate it.

---

