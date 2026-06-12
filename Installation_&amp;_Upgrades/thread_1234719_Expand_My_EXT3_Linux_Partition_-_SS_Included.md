---
title: "Expand My EXT3 Linux Partition - SS Included"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by therocco2k on 2009-08-08
I've Shrunken Windows so I can add a little more space to Linux to Store my Databases (Windows is for games, and thats it....)

I've done some research and fiddling around, and cannot seem to find the answer. I'm right now on Ubuntu Live CD and fiddling in GParted.

How can I add the unallocated space Above the Extended Partition (34.5GiB) to /dev/sda5 - My Main Linux Ubuntu Installation - Without ruining anything.

Is it possible?

Here is a Screenshot of my Hard-Drives layout:
[IMG]http://www.fatbottoms.net/extra/gparted.jpg[/IMG]


Thank you ALOT in advance, I need this extra Space to Store 20 GiB of Database as I'm phasing away from Windows for good, but arn't quite ready yet. Thanks again.

:KS For Winner

---

### Post by therocco2k on 2009-08-08
I Don't think this should be impossible - However, I'm really into Linux and have started several important databases on it.

I'd like to Expand the Drive with the Unallocated drive - BUT, if there is no way to do this, is my only other option to clean install of Ubuntu?

I wouldn't mind this SO much, but I've laid the style and information out on the exisiting linux install to my liking.

If I have to do a Clean Install, ... well I've never "Backed Up" a computer. I don't know the extent of what backup I can do. Does it save everything from my Wallpaper to my Packages and settings or does a backup mean only save the files I need. I do have a DVD Burner, but I do not think it's Dual Layer and that means 4GB at a Time.

Any Suggestions PLEASE?

---

### Post by feb3 on 2009-08-08
Please don't quote me as I am absolutely no expert on partitioning. The only thing that I can say is that I have very recently had success with shifting partitions around using the free Easeus Partition Manager. 
However, it seemed to me that you could only work with partitions that were next to each other so I had to take a bit off this, add it to that etc etc until I got what I wanted. 
For instance, I wanted to retrieve some empty space from WinRE as it was far too big. This I did successfully but to add that space to the C drive (it was to the left of it), Easeus shifted all the information up, which took some time. When the computer rebooted it gave the option to recover as it thought something was amiss. I ignored it and clicked Start Windows normally, the drivers were added, it rebooted, and that was it.
There is also a copy facility but I didn't pursue this and just worked steadily in my own way.
Not sure if this is of any help but good luck.

---

### Post by ptn107 on 2009-08-08
The only way I think to incorporate free space into already-made extended partitions (your /sda3) is to remake [and size] it from scratch (which will of course wipe the information inside the extended partition).

---

### Post by drs305 on 2009-08-08
> **therocco2k said:**
> 
How can I add the unallocated space Above the Extended Partition (34.5GiB) to /dev/sda5 - My Main Linux Ubuntu Installation - Without ruining anything.
Is it possible?
:KS For Winner

I wrote a guide about resizing an Ubuntu system partition. Be sure to back up important data before doing any work with partition resizing. This operation may take quite a bit of time since you will be moving your entire ubuntu partition (1+ hours probably) so check your power sources.

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by therocco2k on 2009-08-08
Thank you DRS305 - Now anybody else with this problem (And I know Thousands of people are switching from Windows to Linux every day) Will have a Guide, Thanks to DRS305. People like you that make this forum great.

Thanks again,
Great Day!

---

