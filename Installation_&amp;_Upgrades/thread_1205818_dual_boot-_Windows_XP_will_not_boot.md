---
title: "dual boot- Windows XP will not boot"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Ron H on 2009-07-06
Situation:
I have an Acer Aspire One. I repartitioned using a live CD and installed Ubuntu 8.10. Both Ubuntu and XP booted properly. I upgraded to Ubuntu 9.04. 

Now Ubuntu boots but XP will not. I get a message saying that the Windows is an unbootable partition and a code something like 0 .. 0000000000000.

How can I get XP to boot?

---

### Post by enli on 2009-07-06
May be NTFS structure on XP parition is currupt.

Try ntfsfix as told in this thread - [http://ubuntuforums.org/showthread.php?t=92405](http://ubuntuforums.org/showthread.php?t=92405)

If that doesnt work, you need to boot from XP cd and go into recovery console. [http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

then run command chkdsk [driveletter here] /r
e.g. chkdsk C: /r

That might fix the problem.

---

### Post by Ron H on 2009-07-06
Thanks for the quick reply.
I followed the thread to ntfsfix. When I entered 'sudo ntfsfix /dev/hda1' in Terminal the response was, "this command does not exist"

Ron

---

### Post by enli on 2009-07-07
I cant use Ubuntu for couple of days due to some reason. So I cant tell you exactly how to install that program "ntfsfix" but maybe someone guild you.

If you dont want to wait and try to fix the problem, try second approach of using XP recovery console and chkdsk as I mentioned.

---

### Post by Ron H on 2009-07-07
Enli,
I added a cd player, changed the boot order, and attempted to load a recovery disc. The result: the screen went blank and nothing loaded. Now nothing loads, the screen is blank whether I have the cd installed or not. It looks like I now own a brick.

Regards,

Ron

---

### Post by enli on 2009-07-07
This looks bad. I never had a problem like this. I did some searching and it suggests that there might be problems with the partition scheme.

Are you able to access your XP partition from Ubuntu? If not try the following.

As you are familiar with the partitioner, start your Ubuntu livecd and Go to System > Administration > Disk partitioner. Hide all your linux partitions including the swap by right clicking on them ( I dont remember the exact option, but it should be there somewhere and I dont have access to Ubuntu right now ).

When you are done that try the XP Recovery CD part again and run chkdsk. And also run commands "fixboot" and "fixmbr".

Boot again without CD in drive and see if that helps. If XP starts you are good to go or else I think you need to delete NTFS partition and re-create and install XP again.

If XP starts then to get back the grub menu, boot using Ubuntu livecd and enter these commands in terminal , Applications > Accessories > Terminal

```

sudo grub
find /boot/grub/stage1
(hd0,x)
root (hd0,x)
setup (hd0)
quit

```

In above commands after second line you will see (hd0,x) where x could be anything 4,5..Replace that number with x in subsequent commands. Reboot.

---

