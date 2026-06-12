---
title: "Help with busted raid after upgrade"
date: 2018-08-05
forum: Hardware
---

### Post by ulao3 on 2018-08-05
I wanted to take my 14 to the latest and did a dist-upgrade but I'm left with a broken boot. (apparently it didn't upgrade). 

First I never had a good boot because my second raid drive died. No one could even help me resync them. So the only way I could boot was to run recovery and just boot from there. 

Now I have to select a previous boot (recovery) and I can once again gain access to my system. I'd much rather fix this then do a full install. 

At the current time I can boot normally now but I'm stuck in a loop saying. 
[COLOR=#333333][FONT=monospace]incrementally starting raid arrays[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]mdadm: Create user root not found[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]mdadm: create group disk not found[/FONT][/COLOR]
[FONT=monospace][COLOR=#333333]incrementally started raid arrays[/COLOR][/FONT]

[FONT=monospace][COLOR=#333333]I just need some guidance I don;t even know what to look for or at. I only have one drive in my system and it is part of a broken array. Is there a way to just skip all this raid stuff and boot to my current os on that drive?


[/COLOR][/FONT]

---

### Post by mastablasta on 2018-08-06
> **ulao3 said:**
> 
First I never had a good boot because my second raid drive died. No one could even help me resync them. So the only way I could boot was to run recovery and just boot from there. 

Raid is made specifically for this case. if one disk fails (dies) you are supposed ot add another one and sync it with the working disk. RAID is there to help you work while disk is damaged. it is not there to do backups. you need a separate disk for that. 

so i would first repair the RAID array (new drive&sync).

QUOTE]
Now I have to select a previous boot (recovery) and I can once again gain access to my system. I'd much rather fix this then do a full install. 
[/QUOTE]

i don't know that much about RAID, but the system can be reinstalled, written over, or you can do a full install where you reformat the drive. as i understand RAID is basically mirrored image of the drive, but otherwise it behaves as if there was only one drive in the machine. ofcoruse it depends what RAID you are using (i use RAID1).

if you have a working system the fastest resolution (if you can't repair the RAID array) would be to do a fuill backup, reinstall, the restore the settings from backup. i used about 3 hours doing it last time i did it, but that was because my backups were damaged, so i had to find the settings files and extract the good files from a broken image first. with good backups and it should take you more than 30-45 mins.

---

### Post by ulao3 on 2018-08-06
> Raid is made specifically for this case. if one disk fails (dies) you  are supposed ot add another one and sync it with the working disk. RAID  is there to help you work while disk is damaged. it is not there to do  backups. you need a separate disk for that.


well maybe in a perfect world. Here is my old thread when it occurred. 

[https://ubuntuforums.org/showthread.php?t=2283184](https://ubuntuforums.org/showthread.php?t=2283184)

What good is raid if no one understands how to fix it? it really comes down to popularity. On Windows this is a walk in the park but when it comes to linux everyone ducks and hides. I'm mean I'm no linux guy but I know my way around. Figured Raid would "help" me so I set it up. Though as you can see no one can help. Thus my entire point in this post. Although I do appreciate the candor on your part, is there no one that understands how raid works on linux?

I would assume I could drop in a new drive, and with some command map and sync. I just see no info on this and was never able to get any suggestions or help.

---

### Post by springshades on 2018-08-08
I think the big problem here is that your computer was set up in a fairly complicated way (relative to most computers) and yet you have no idea how it was set up. That may mean that you set it up a long time ago and don't remember what you did, or it may mean that someone else set it up for your and didn't tell you anything about it.

For example, in your previous thread, no one had any way of knowing that you were running a RAID1 until your third post. Most people would not have known what was even running your raid until now due to the mdadm messages. To a lot of people, if you say software raid they assume fakeraid rather than true software raid. Not only that, but it looks like you're probably running bootable mdadm RAID. A lot of people do that, but I wouldn't touch it personally. I don't think that Windows even has the ability to do a true bootable software RAID. As far as I know, the closest thing in Windows is fakeraid to allow the RAID array to start up before the OS boots.

To fix the RAID itself, you need to remove the bad drive from the array:

mdadm --manage /dev/mdX --remove /dev/sdXX

You'll need to find the proper values to replace the X's with. The command to get the stats for your RAID array are:

cat /proc/mdstat

Then you'll need to buy a very similar hard drive to your original, partition and possibly align it, then add it to the RAID.

I can never remember the flags you need to align the partition nicely off the top of my head, it always requires some google-fu, but the mdadm command to add the new drive to the RAID is:

mdadm --manage /dev/mdX --add /dev/sdXX

The sdXX is now going to be the new partition that you just made. Once you do this, mdadm should automagically rebuild your RAID unless there is an error. Note that getting an error during a rebuild isn't terribly uncommon. Generally, your computer doesn't know that your hard drive has failed until it runs across errors. A RAID rebuild is one of the only things that is going to read through every single bit on your HD so it may find invisible errors.

In my opinion, unless you know what you are doing, you probably shouldn't manage a RAID on your own with mdadm unless you have at least 3 hard drives. You can use something cheap like a small SSD to boot your OS with normal partitions. No RAID. Then, you can use the other two drives in a RAID to store your important data. True software RAID is a really nasty chicken and egg problem. The mdadm program is managing your RAID array, but it's a program running on your OS, but your OS can't boot until the RAID array is running, etc...

---

