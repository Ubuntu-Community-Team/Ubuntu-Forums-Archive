---
title: "3TB Hard Drive"
date: 2014-11-04
forum: Hardware
---

### Post by process91 on 2014-11-04
My friend had a 3TB external Seagate Backup Plus hard drive which stopped working (no power whatsoever). I guessed that the drive was probably fine, but the USB enclosure was bad, so I opened it up and plugged the drive into my computer (which runs Ubuntu). Here's the output from gdisk:```
GPT fdisk (gdisk) version 0.8.5Partition table scan:  MBR: MBR only  BSD: not present  APM: not present  GPT: not present***************************************************************Found invalid GPT and valid MBR; converting MBR to GPT format.***************************************************************Disk /dev/sdd: 5860533168 sectors, 2.7 TiBLogical sector size: 512 bytesDisk identifier (GUID): 51078203-F924-440C-9606-A99815D09CC7Partition table holds up to 128 entriesFirst usable sector is 34, last usable sector is 5860533134Partitions will be aligned on 2048-sector boundariesTotal free space is 5127969645 sectors (2.4 TiB)Number  Start (sector)    End (sector)  Size       Code  Name   1            2048       732565503   349.3 GiB   0700  Microsoft basic data
```I expected to find a GPT table since this is over 3TB, but gdisk seems to indicate that there is no GPT table. I know there is data on here that I don't want to lose, so I connected it to a windows computer using a USB/Sata connector, however Windows 8 also showed a 349GB hard drive instead of the full 3TB partition which was there previously. Any suggestions?

---

### Post by process91 on 2014-11-04
Forum software is acting up - newlines were removed from my code block despite all attempts to mitigate the issue, and furthermore the "Edit Post" functionality doesn't seem to respond either, so here's a reply which will hopefully contain better formatted output from gdisk:GPT fdisk (gdisk) version 0.8.5Partition table scan:  MBR: MBR only  BSD: not present  APM: not present  GPT: not present***************************************************************Found invalid GPT and valid MBR; converting MBR to GPT format.***************************************************************Disk /dev/sdd: 5860533168 sectors, 2.7 TiBLogical sector size: 512 bytesDisk identifier (GUID): 51078203-F924-440C-9606-A99815D09CC7Partition table holds up to 128 entriesFirst usable sector is 34, last usable sector is 5860533134Partitions will be aligned on 2048-sector boundariesTotal free space is 5127969645 sectors (2.4 TiB)Number  Start (sector)    End (sector)  Size       Code  Name   1            2048       732565503   349.3 GiB   0700  Microsoft basic data

---

### Post by westie457 on 2014-11-04
Hi, Testdisk is possibly the best tool to use here though it will take a long time on a 3TB drive (read overnight).

Testdisk is available in the repo's or with instructions and guides from here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Fixparts is another option though I am not sure it is the right tool for this. [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by oldfred on 2014-11-04
If an external drive, we have seen many that partition with MBR and two partitions with some proprietary or unusual bits to make it work. That was for compatibility with XP as XP did not work with gpt partitioned drives. Some had 4K logical sectors not the standard 512 sectors. Although new drives all are 4K physical.

We also have seen unpartitioned drives that then are like a super floppy and some other odd ball configurations. Those were usually users mis-configurating drive as near as we can tell.

Best just to stay with gpt as that now works with current versions of Windows & Ubuntu.

---

### Post by process91 on 2014-11-04
It was an external drive. Of course I would love to stick with GPT once I get the hard drive working, but that unfortunately doesn't seem to help me with getting the data off for now. I think there may have been some proprietary partition formatting going on, as the drive (reportedly) did work with Windows XP. I will contact Seagate to see if they have any suggestions.I checked out fixparts, but the documentation seems to suggest that it only is designed to go from GPT to MBR (and somehow seems to suggest that MBR is "better"?), whereas I believe (if the drive did previously have a GPT) I need to got the other way. I know gdisk can accomplish this (r then f options) but it is not clear to me if that will attempt to recreate an existing GPT or if it will literally just convert the current MBR partition layout to GPT.Thanks for the replies thus far, and sorry that the forum software still seemed to remove all the newline formatting from my gdisk output. That is very frustrating, especially since the documentation for bbcode seems to indicate that it should not do that, especially in a code environment.

---

### Post by process91 on 2014-11-04
Any post I make seems to be removing all newlines. I'm using Chromium. Newlines seem to work everywhere else. For instance, here are five number which I have entered with newlines between each:12345I suspect after I click "submit reply" they will appear inline with the rest of the text, and this whole post will be one big paragraph. Any suggestions for this problem while we're at it?

---

### Post by coffeecat on 2014-11-04
Look at your browser plugins and don't block scripts on this forum.












Chromium works fine for me.

---

### Post by oldfred on 2014-11-04
I am using Firefox, so do not know if there is some internal setting in Chromium?
1,
2

I do get opposite issue as I now use Zim as my notes. But copying text from Zim adds extra line feeds.

---

### Post by ajgreeny on 2014-11-04
@ process91.

Are you typing direct into the reply or advanced reply box, or are you using a text editor of some sort and copying the text from that to the forum?

---

### Post by process91 on 2014-11-04
I am typing directly into the reply box (quick or advanced seems to make no difference).Here's a newline, let's see if it works this time.

---

### Post by process91 on 2014-11-04
The only plugin/script I had running was adblock. I just disabled it - Here's another try...

---

### Post by ajgreeny on 2014-11-05
Very strange!

What happens if you close chromium, temporarily rename the **~/.config/chromium** folder as a backup, then restart chromium?  Does the forum reply system then behave itself?

If so it is some config setting that causes this problem, but it might take a lot of finding and maybe easier to just setup chromium as you want it again.

---

### Post by process91 on 2014-11-09
Thanks for the suggestions. I did do that, and even with a clean profile the returns in my reply are removed. Since I don't post here too much, I'm not worried about it, but it is strange. (Here I put two returns, but you won't see it.)I contacted Seagate and they verified that they use something proprietary built into the external hard drive enclosure which allows the disk to be read. They said there would be no way to read it without the enclosure. Therefore it seems like my best option is to buy the base for the enclosure, which (thankfully) is sold separately for about $20.

---

