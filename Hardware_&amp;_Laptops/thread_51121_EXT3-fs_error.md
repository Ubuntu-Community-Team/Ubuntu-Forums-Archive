---
title: "EXT3-fs error"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-07-22
I am using Gnome and Evolution for email. Twice this week the following has occurred:

I left Evolution open along with an email reply I was composing while I was interrupted and had to walk away from the computer for a few minutes. When I came back I could minimize Evolution's main dialog and/or the reply dialog, but neither would allow me to type or even close them. Both times I decided to just reboot and both times the shutdown process would hang with a repeating message as follows:

"EXT-fs error (device hda2) in start_transaction: journal has aborted"

To shut down both times I had to disconnect the power.

When I booted each time following the event there was a message showing that the journal was being recovered and in each case all seemed fine and restored to a moment about 15-30 seconds before the point where I had walked away from the computer (i.e. the message I was composing was recovered by Evolution minus part or all of the final sentence).

Two questions: What caused the problem?? How do I prevent/fix it?

---

### Post by DJ_Max on 2005-07-22
Your hard drive may have some bad sectors.

Boot from the first CD and when you're in the shell

```
fsck /dev/hda2
```

---

### Post by matthew on 2005-07-22
> fsck /dev/hda2
Done. Here's the output:

> Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/: clean, 187557/1281696 files (1.6% non-contiguous), 1192432/2560359 blocks
No errors noted. No fixes mentioned.

I thought this info about my HD and partitions might be of interest so I decided to include it:

> Size: 80 Gb Hdd, currently dual booting Ubuntu with Win XP

Partitions:
Name/type/size/mountpoint

hda1 ntfs 15.3 Gb WinXP *mounts read-only as /media/windows in ubuntu
hda2 ext3 10 Gb /
hda3 ext3 30.5 Gb /home
hda4 extended, includes hda5 & hda6
hda5 fat32 19.4 Gb /home/matt/music
hda6 linux-swap 1 Gb

hda5 and 6 used to be part of hda1's ntfs partition. As I am using XP less and less I decided to remove space from its partition and make a shared space accessible from both. Since I am now using XP for almost nothing, hda5 holds my mp3s and almost nothing else.

I didn't have a swap file to start out with because with 1 Gb ram I figured it wasn't necessary, but I created one now because I want to try to get the hibernate function to work. Haven't tried yet...soon, though.

Thanks, DJ_Max for the advice. Any other ideas? Anyone else?

---

### Post by DJ_Max on 2005-07-22
I did a quick search, and found
[http://www.ubuntuforums.org/showthread.php?t=1995](http://www.ubuntuforums.org/showthread.php?t=1995)

I'm gonna do some more searching if that doesn't help.
Side note:
Also, about the swap, no matter how much RAM you have, Linux will cache and use as much as possible, so even if you have 4GB Linux will use around 3.5-3.8GB or even more. So a rule of thumb is to make the swap 2x your ram amount.

---

### Post by matthew on 2005-07-22
That was an interesting thread. Thanks. 

I don't think it is my power supply, though, as this is a laptop and it was plugged in with a full charge on the battery as a backup. Hmm..

Another question:
Think I should resize my swap? I don't think it would be hard to resize the neightboring partition slightly to get the space.

---

### Post by matthew on 2005-07-23
*bump*

---

### Post by kb00heda on 2005-08-09
Unfortunately --- for me! --- I have the same problem: recently, my system (which also happens to be a laptop) has hung. When trying to restart X, I got the intimidating error messages going like

"EXT3-fs error (device hda1)"

and so on. (In effect there seems to be a problem reading from the disc.) Sometimes my machine even fails to boot afterwards, making me retry several times before succeeding. I do not know whether this is hardware related or not? Us being two having the similar problem perhaps makes it more likely to be something else.

If no one can help us out, I eventually will try to reinstall my system from scratch, which I intended to do soon enough anyway. However, if our HDDs are broke, things are definately looking worse.

---

