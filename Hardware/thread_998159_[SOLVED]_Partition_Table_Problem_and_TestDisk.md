---
title: "[SOLVED] Partition Table Problem and TestDisk"
date: 2008-11-30
forum: Hardware
---

### Post by Mostly Harmless Eccentric on 2008-11-30
Hey, guys. I just have some questions that likely won't be too hard. If you'd please take a moment to point me in the right direction, I would be endlessly grateful.  
 
So, first, I recently upgraded my HP Pavillion laptop to Intrepid. For the most part, no issues. There was some trouble with nvidia and the X-server, but I got that sorted out already. There's the problem that HP seems to have with Intrepid where you have to hold a key during start-up or it hangs, but according to my research, no one's sure yet why it does that, or what to do about it. I'll leave that fir a moment. That's just background information. The point is, my laptop is booting Intrepid just fine from the primary parition, and it behaves as well as can be expected, and the install was around Nov. 25th, very recent.
 
Second, I have a little project going with this laptop, and that's where the problem comes up. I'm trying to get it dual booting Ubuntu with Debian, and I want to have a smaller partition that both mount at startup, where I'll keep files I want to use on both sides without duplicating (so, for example, I don't have my music folder occupying twice the space it needs to and wasting GB's already with just that) Ubuntu and Debian would be in the first and second logical partitions, with about 100GB each, then about 30 for the shared one, with 1gb left for swap (I likely don't need that much, but the shared partition not being a nice, round number was iritating me). The non-Ubuntu partitions are empty right now, though, since I haven't gotten Debian working yet, but that's another story.
 
However, I did have it in the other 100gb partition before, but when I was trying to get Intrepid working, and nothing I did with menu.lst seemed to get it using the right kernel, I realized this is because it was reading the version on the Debian side, and since I hadn't managed to get Debian booting right yet anyway, I just used GParted to get rid of it so Grub would use Ubuntu's menu.lst. That worked, and intrepid started starting up correctly. I move on to getting the shared partition mounting at start-up in Ubuntu. I use GParted to label it and the Debian partition-to be for ease of identification and aesthetic reasons. I leave it alone for a day, then later sit down to start on my Debian installing.
 
That's when I realized the existence of this issue. GParted, including the liveCD, can't see my partitions, and reads all of it as unallocated. Fdisk -l sees everything fine, but if I try to manipulate anything from the command line, it says it couldn't open the disk. The partitioner on the Debian installer also sees nothing but unallocated space. I go online and start doing research, and find this is probably caused by a problem with a bad partition table, probably overlapping. I don't know what I did with it, but I likely did *something*, since I've been fiddling with my new toy so much lately. In further researches, I found out about a tool called TestDisk, so I try that and see if I can get my partition table back, but it's not detecting the table I had, just a million other much smaller partitions, none of which, as far as I can see is, is Ubuntu.
 
But, like I said, fdisk -l still sees it, so I do know where the Ubuntu partition begins and ends, and where my swap partition starts and ends, if that's important. Looking around at the features of TestDisk, it looks like I can create a partition with it by defining the starting and ending cylinders. So, I thought I could, using the information from fdisk -l, just define the rest of my disk EXCEPT the Ubuntu and and maybe the swap part as one giant partition to thusly correct the overlap (the swap and Ubuntu are at opposite ends of the disk). Then, if all goes according to plan, I was thinking that with that corrected, GParted would see it as usual and I could set up the Debian and shared partitions again. 
 
So, would I be able to do this, or would I make even more of a mess?
 
Sorry for the wall-O'-text by the way, but I'd been doing so much stuff with it recently, I didn't know how much was relevent...:???:

---

### Post by Mostly Harmless Eccentric on 2008-11-30
> /dev/sda1   *           1       13180   105868318+  83  Linux
/dev/sda2           13181       26325   105587212+  83  Linux
/dev/sda3           26326       30401    32740470    5  Extended
/dev/sda5           26326       30270    31688149+  83  Linux
/dev/sda6           30271       30401     1052257+  82  Linux swap / Solaris

There's the fdisk -l output, by the way. I can't really see what the problem is. Can someone help me out with this, please?

---

### Post by caljohnsmith on 2008-11-30
It sounds like you could be right about having a partition table problem; how about first posting:
```
sudo fdisk -l
sudo parted /dev/sda print
```
And please post the *full* output of the fdisk command, including the header at the top with the disk size, cylinders, etc. Next make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there.

---

### Post by Mostly Harmless Eccentric on 2008-12-05
Phew! I was fiddling around after posting that and got my internet connection in a knot for quite a while there, but it's unraveled. 

Additionally, caljohnsmith, testdisk is a godsend. :p

---

