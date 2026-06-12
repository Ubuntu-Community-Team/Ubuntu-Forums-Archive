---
title: "How do I access my Windows software RAID 0 arrays?"
date: 2015-01-01
forum: Hardware
---

### Post by dan149 on 2015-01-01
Hello.

I'm a new Ubuntu user, and am enjoying it so far. However, there's a big problem stopping me from being able to spend much time with it: I need to be able to access my Windows software RAID 0 arrays in order to really use it as my primary operating system.

I already [posted about this on AskUbuntu]("http://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0"), but I haven't gotten any replies yet, and this is quite a high priority issue for me. All the related information that I was able to find in my research also happened to come from this forum, so I figured I'd probably get a better response here. I hope you don't mind, but I'll just quote what I posted on AskUbuntu:

> I have already researched this subject as best as I could, and I managed to find a very helpful post:

[LIST]
[*][URL="http://ubuntuforums.org/showthread.php?t=833653&p=5217561#post5217561"]can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu?
[/URL] 
[/LIST]
 The post describes how to get Ubuntu to see a Windows RAID 0 array that is made up of two drives. The main command used is _[FONT=courier new]sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2[/FONT]_. According to that user, and the other posters in the thread, it actually does work. That's great.

**I have not tried following these instructions yet.** Why? The post includes a warning about how you must not write to it if you enter the wrong chunk size; it's understandable how that could cause problems. My concern is that my setup is different to their example, and I am not sure that the commands should be entered exactly the same for my setup. **I am afraid to break it by doing it wrong, and therefore wish to get the advice of somebody more experienced.**

This is how my setup differs from their example:

[LIST=1]
[*]I have **three** 1 TB drives, not two drives (of whatever size they used). 
[*]I have **two** RAID 0 partitions spread across those three drives: one 500 GB and 2.3 TB. This means that I need to NOT use the full disks when creating the RAID array, but instead use just part of them. 
[*]I used a **non-default block size** for at least one of my RAID 0 partitions when I set them up years ago. I have no idea if this block size is the same as the chunk size that they mention. My 500 GB partition has a block size of 4 kb (4096 bytes per cluster), and my 2.3 TB partition has a block size of 64 kb (65536 bytes per cluster). 
[/LIST]
 The relevant output from _[FONT=courier new]sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL[/FONT]_ (for just those three RAID0 drives) is:

```
NAME   FSTYPE   SIZE MOUNTPOINT            LABEL
sdb           931.5G            
&#9500;&#9472;sdb1            1M            
&#9500;&#9472;sdb2          127M            
&#9492;&#9472;sdb3        931.4G            
sdc           931.5G            
&#9500;&#9472;sdc1            1M            
&#9500;&#9472;sdc2          127M            
&#9492;&#9472;sdc3        931.4G            
sdd           931.5G            
&#9500;&#9472;sdd1        166.7G            
&#9492;&#9472;sdd2        764.7G 
```

The relevant output from _[FONT=courier new]cat /proc/partitions[/FONT]_ (for just those three RAID0 drives) is:

```
8       16  976762584 sdb
8       17       1024 sdb1
8       18     130048 sdb2
8       19  976631478 sdb3
8       32  976762584 sdc
8       33       1024 sdc1
8       34     130048 sdc2
8       35  976631478 sdc3
8       48  976762584 sdd
8       49  174763008 sdd1
8       50  801865728 sdd2
```

The "Disks" program in Ubuntu displays the following partitions for my drives:

```
/dev/sdb:   GUID Partition Table .
/dev/sdb1:  1.0 MB, Microsoft LDM metadata.
/dev/sdb2:  133 MB, Microsoft Reserved.
/dev/sdb3:  1.0 TB, Microsoft LDM data.
/dev/sdc:   GUID Partition Table partitioning.
/dev/sdc1:  1.0 MB, Microsoft LDM metadata.
/dev/sdc2:  133 MB, Microsoft Reserved.
/dev/sdc3:  1.0 TB, Microsoft LDM data.
/dev/sdd:   Master Boot Record partitioning.
/dev/sdd1:  179 GB, Unknown.
/dev/sdd2:  821 GB, Unknown.
/dev/sdd:   136 MB, Unallocated space.
```

I hope I've provided enough information here. So now, my question is this: what is the proper command for me to enter with my setup, so that I can access both of my Windows RAID 0 partitions from Ubuntu?

Thank you very much in advance.

I really hope somebody can help me to get this working. Like I said, I've seen posts from other people here on this forum where they were able to get Windows software RAID working in Ubuntu, so it seems like it's totally possible. I just need to know how to do it correctly for my specific setup.

With the example command of _[FONT=courier new]sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2[/FONT]_, obviously the number of devices would be changed from 2 to 3 (or at least I think so), and I would need to list all three drives: sdb, sdc, and sdd. But my problems are:

[LIST]
[*]What chunk size do I specify? Should I still use 64 like in their example, or what? It sounded like they were using 64 because it's 128 divided by their number of drives, but I have three drives and 128/3 is a fractional number. And I didn't even use the default block size when I made the RAID array in Windows. 
[*]How do I specify the partitions to use? I don't have a single RAID array made up of the full disks; I have two RAID arrays made up of a 167 GB partition on each disk and a 767 GB (or so) partition on each disk, to get a total of 500 GB and 2.3 TB from the arrays. This doesn't seem to match the output I got from the tools I ran though... 
[/LIST]
 Thanks a lot in advance.

---

### Post by weatherman2 on 2015-01-01
> **dan149 said:**
> I'm a new Ubuntu user, and am enjoying it so far. However, there's a big problem stopping me from being able to spend much time with it: I need to be able to access my Windows software RAID 0 arrays in order to really use it as my primary operating system.

I can't help you with this, though I do have to wonder why anyone would want to use a Windows RAID when using Ubuntu as their primary OS?  Just wondering.  If you're going to use Ubuntu as the primary OS, why not use a Linux file system and RAID setup?

Although Linux has reliable drivers to use NTFS partitions now, things will still go more smoothly if you stick to a Linux file system if using a Linux OS most of the time.  There are for example some NTFS performance issues with copying large files.

Many Linux users who need occasional Windows use install Windows in a virtual machine.

But if I needed to get a Windows RAID with a unique setup working in Linux, I'd probably create a dummy RAID (much smaller) with the same setup, same block size, etc. and then figure out how to import that into Linux.  Not much risk in that if something goes wrong.  If it works, then you can proceed with your real RAID.  Of course, I'd also have a backup of my data anyway in case something went wrong.

---

### Post by dan149 on 2015-01-01
Thanks for you reply!

Well, when I say "use it as my primary operating system", I guess I actually mean more like *evaluating* it for that purpose. I'm still new to Ubuntu. I was previously using it in a virtual machine within Windows, before deciding that I liked it enough to install it properly on its own partition. I shrunk my Windows partition, and installed Ubuntu alongside it, so I'm now dual booting. I'm still not completely sure about whether I want to switch over to Ubuntu (running it on bare metal is a different experience to having it in a virtual machine with my host OS easily accessible), which is why I'm keeping my Windows install around. I want to migrate gradually rather than all at once, so that I can more safely go back if I need to. If all goes well (meaning I can work out any issues, like this one), then I might eventually move over to Ubuntu entirely. But since I'm a gamer, I might want to keep my Windows partition regardless of what I do.

All of my important data is currently on my two RAID arrays. I agree that if I move over to Ubuntu permanently, I might want to recreate it with a Linux file system. But *for now*, I'd like to keep it as it is so that I can still work on my Windows install like normal. I just want to get everything working as is for now, so that I can relax and settle more into Ubuntu over time.

Creating a small RAID with the same setup is actually a good idea, since then I could freely test different things to see what works, without worrying about losing my data. But the problem with that is that I don't have any spare drives laying around to test with. I do have backups of my RAID arrays, so I suppose I could potentially just try things with that, but it'd be a lot of time and work to restore several TBs of data if it gets broken... So I'm not sure how I could set up a dummy RAID. I'll have a think about that.

In the meantime, if anyone happens to have any other tips or advice, I'd appreciate it!

---

### Post by dan149 on 2015-01-03
_**Solved!**_

I finally got this working thanks to this Stack Overflow post: [Windows Spanned Disks (LDM) restoration with Linux?]("http://stackoverflow.com/a/22108676/399825")

It was extremely difficult to uncover this elusive information. It took days of searching, and I guess I wasn't finding it because the post makes no mention of RAID, so it wasn't coming up in my search results. It definitely works for my Windows software RAID 0, though.

**The solution:**

The solution is actually quite simple. There's a wonderful tool built specifically for this purpose, called _[FONT=courier new]ldmtool[/FONT]_. It is capable of reading and working with Windows dynamic disks which use LDM (Logical Disk Manager). It is not installed by default, but is included in the Ubuntu repositories. All I had to do was execute two commands:

```
sudo apt-get install ldmtool
sudo ldmtool create all
```

The first command installs _[FONT=courier new]ldmtool[/FONT]_, and the second has it automagically create device mappings for all of the connected Windows dynamic disks. These mappings are located in _[FONT=courier new]/dev/mapper/[/FONT]_ and can be mounted manually with _[FONT=courier new]mount -t ntfs /dev/mapper/mapfilename[/FONT]_, but I didn't need to do that - Ubuntu mounted them for me automatically after I ran the above two commands. That's all I had to do, and I could immediately access them from the file browser!

The linked post includes a suggestion for doing this automatically every boot. Just open the file _[FONT=courier new]/etc/init/mountall.conf[/FONT]_ and add the line _[FONT=courier new][ -x /usr/bin/ldmtool ] && ldmtool create all >/dev/null || true[/FONT]_ immediately before the _[FONT=courier new]exec mountall ...[/FONT]_ line near the end of the file.

Full credit for this solution goes to Christian Hudon, the guy who posted it as an answer over on Stack Overflow. Thanks!

To add some further information to this, I used some other _[FONT=courier new]ldmtool[/FONT]_ commands to query my volumes for information:

```
sudo ldmtool scan /dev/sdd
[
  "e856a65f-e558-11e1-ae19-bc5ff435f790"
]

sudo ldmtool show diskgroup e856a65f-e558-11e1-ae19-bc5ff435f790
{
  "name" : "Dan-PC-Dg0",
  "guid" : "e856a65f-e558-11e1-ae19-bc5ff435f790",
  "volumes" : [
    "Volume1",
    "Volume2"
  ],
  "disks" : [
    "Disk1",
    "Disk2",
    "Disk3"
  ]
}

sudo ldmtool show volume e856a65f-e558-11e1-ae19-bc5ff435f790 Volume1
{
  "name" : "Volume1",
  "type" : "striped",
  "size" : 1048578048,
  "chunk-size" : 128,
  "hint" : "D:",
  "partitions" : [
    "Disk1-01",
    "Disk2-01",
    "Disk3-01"
  ]
}

sudo ldmtool show volume e856a65f-e558-11e1-ae19-bc5ff435f790 Volume2
{
  "name" : "Volume2",
  "type" : "striped",
  "size" : 4811194368,
  "chunk-size" : 128,
  "hint" : "E:",
  "partitions" : [
    "Disk1-02",
    "Disk2-02",
    "Disk3-02"
  ]
}
```

It isn't necessary to run the above commands, as _[FONT=courier new]ldmtool create all[/FONT]_ does all the necessary work to create the mappings. I just included them because I already included information about my setup in the question, so this information might be helpful for anyone coming across this post later. In particular, we can see that according to _[FONT=courier new]ldmtool[/FONT]_, both of my dynamic volumes use a chunk size of 128, despite being created with different block sizes in Windows. I guess this means that block size and chunk size are not synonymous terms. The commands _[FONT=courier new]ldmtool show disk[/FONT]_ and _[FONT=courier new]ldmtool show partition[/FONT]_ can be used to display further information.

---

