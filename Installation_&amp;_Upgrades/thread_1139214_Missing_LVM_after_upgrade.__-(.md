---
title: "Missing LVM after upgrade.  :-("
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by frediE on 2009-04-26
i used the following instructions to create a mirrored data disk (was not my boot disk) and it was working very well.  however after i upgraded from 8.10 - 9.04 it did not come back.  i was ok setting it up (and even did some testing before putting all my data on it) but now that it is not working i would really appreciate a little guidance to bring it back.

these are the instructions i used to set it up.
[https://help.ubuntu.com/community/Installation/RAID1+LVM](https://help.ubuntu.com/community/Installation/RAID1+LVM)


during boot it stops and states it can not find the /dev/md0 (which is true it doesn't exist) but i don't know if can just create it again.  i don't want to loose all my data.  yikes.

any help would be great.  sdb and sdc are my disk (i pulled sdc as a precaution to getting this working.  i figure it gives me another shot.  :(

---

### Post by frediE on 2009-04-26
not sure if this helps but if i do a cat /proc/mdstat i get the following

md_d0 : inactive sdb1[0](S)

---

### Post by frediE on 2009-04-27
Think i would have better luck in the server forum?  i had two disks mirrored and i am not sure how to bring them back.  i don't believe the data is gone, but i don't what to make any changes util i get some guidance.  a am new to lvm.

---

### Post by frediE on 2009-04-28
just fyi i was able to reproduce this with virtual box so i am going to do some testing and try and get it back.... if anyone has any experience with this it would really be helpful.  :-)

---

### Post by frediE on 2009-04-28
on my virtualbox system i was able to do a 

mdadm -As
/dev/md0: File exists
mdadm: /dev/md/0 has been started with 1 drive (out of 2).

i mounted it and i was able to retrieve all my data.


however i did it on my main system and i got the following...
mdadm -As 
mdadm: No arrays found in config file or automatically

am i getting closer?????

---

### Post by mikereed on 2009-05-13
Not sure if this is exactly what you are after but it may give you some helpful ideas.  Here is my original thread:

[http://ubuntuforums.org/showthread.php?t=1009031](http://ubuntuforums.org/showthread.php?t=1009031)

Good luck.

---

### Post by Lampi on 2009-05-13
> **frediE said:**
> am i getting closer?????
you are,

check your partition entries in /etc/mdadm/mdadm.conf - they should correspond with the devices you find using "mdadm -Esv" I assume some of your uuid strings changed some while ago, causing the problem.

---

### Post by frediE on 2009-05-13
thanks lampi!


that was the key.  i started digging into what the mdadm.conf is and that looks to be the issue.

i was able to get my mirror raid back with info found in this mdadm bug...
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/316670]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/316670")



(THANKS lunomad!)
```


During boot I was prompted with a warning, no valid partitions found on /dev/sdc, hit ctrl-D to continue. Because this isn't a root partition, I was able to continue booting with ctrl-D, which took me all the way to the gdm login. I then dropped to a shell with ctrl-alt-F1. There were no questions about degraded mode booting.

I fixed my problem with the following steps:

1. Stop the false md_d0 array
$ sudo mdadm --stop /dev/md_d0

2. Assemble the degraded md0 (only sdb was found) and mount it
$ sudo mdadm --assemble --scan
$ sudo mount /dev/lvm-raid/homelv /home

3. use mkconf to find the configuration option
$ sudo /usr/share/mdadm/mkconf

4. gedit /etc/mdadm/mdadm.conf to include the output from mkconf AND to use only sdb
DEVICE /dev/sdb*
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=6a291d6f:27049e9f:b95e1135:52246c3f

5. Reboot --> ubuntu found and mounted my array just fine (mount info for LVM is my fstab)

6. Re-add sdc to md0
$ sudo mdadm /dev/md0 --re-add /dev/sdc1

7. Watch rebuild!
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[0] sdc1[2]
      976759936 blocks [2/1] [U_]
      [==>..................] recovery = 14.2% (139109312/976759936) finish=381.7min speed=36570K/sec

unused devices: <none>

I'm not sure why mdadm wanted to build the (incorrect) md_d0 and not the (correct) md0.

```

---

### Post by Lampi on 2009-05-13
> **frediE said:**
> I'm not sure why mdadm wanted to build the (incorrect) md_d0 and not the (correct) md0.
I can only assume the uuid has changed for some reason - usually it only *should* change when you (re)create your array, but mdadm sometimes drives me nuts as well changing the uuid for no obvious reason (sure there is one, just don't now what it is I'm doing wrong).

BTW: If it bothers you again the next time you boot, you will have to update your initrd as well after you changed the mdadm.conf entries. This only concerns you if your root partition is sitting on a raid array, if it's not mirrored it's not assembeled in initrd I guess.

---

