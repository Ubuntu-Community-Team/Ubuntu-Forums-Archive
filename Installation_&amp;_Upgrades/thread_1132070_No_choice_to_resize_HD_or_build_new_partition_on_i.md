---
title: "No choice to resize HD or build new partition on install"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by fbp90crx on 2009-04-21
I used to have Ubuntu as the only OS on my old desktop but then I put XP back on due to programs I had to have for school that were PC only. Now I want to put Ubuntu back on but I want to dual boot so I can still boot into windows when necessary. 
I thought this would be fairly easy but every time I try to install Ubuntu from a cd, it wants to use the whole disk, I have no choice to resize my hard drive for a new partition. I have also tried to resize my partition though disk management but this didn't work either. What else can I try? or am I doing something wrong.
Thanks in advance

---

### Post by Therion on 2009-04-21
What version of Ubuntu are you trying to install?

---

### Post by lalun09 on 2009-04-21
I have exactly the same problem with my Ubuntu 8.10 Live CD, when I try to replace Linux Mint with Ubuntu. (My computer is setup as a dual-boot with Windows XP)

---

### Post by fbp90crx on 2009-04-21
I'm trying to load Ubuntu 8.10

---

### Post by Therion on 2009-04-21
I am confused by the fact that Intrepid is not recognizing that WinXP is already resident on the drive you wish to install to.

When you get to the partitioning stage of the install, what options ARE you presented with?  Most likely one of them will work.  If not there's a couple ways we can try working around it, but I really don't think it will come to that.

One: You can try installing Jaunty.  Jaunty's default option is to set up a dual-boot configuration if it detects another OS resident on the install drive.

Two: You can try using gParted LiveCD to pre-partition the drive you want to install on (shrinking the XP partition) and using the option for installing to the "largest, contiguous free-space" on the drive.

---

### Post by fbp90crx on 2009-04-21
The only options on the partitioning table are guided - use this disk and Manuel.

I may see if I try jaunty if I can find a CD that I haven't used yet lol. Have most of the bugs been worked out with jaunty? Thats why I wanted to load hardy because I know its all been worked out for the most part.

---

### Post by Therion on 2009-04-21
Try using a Jaunty Daily Build CD.  They're the most up to date.  
Jaunty is gonna be released in a couple days so you know there isn't that much that's going to change between now and then.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by fbp90crx on 2009-04-21
Wait, I'm sorry. I just looked at the cd. I was trying to load 8.04

---

### Post by fbp90crx on 2009-04-21
Ok, so jaunty just finished and I burnt it to a cd and tried it. It is still giving me the same 2 options. Use the whole disk and manuel. Its not letting me a new partition.

---

### Post by fbp90crx on 2009-04-22
I still can't find a way to build a partition. Anyone know any other ways?

---

### Post by j.daniel on 2009-04-30
Well, you need to go to "Maunal" configuration.

That said, I have not managed to do it yet with Jaunty. All the guides here says that there are supposed to be a "Resize" option when selecting the only partition there is (Windows ntfs on my computer), but all I have is "Edit" and "Delete". In the Edit view there is no such thing as a size or resize option, only a drop down of different file systems. I have played around some (without actually executing anything) and there is no way that I have found to set this up as dual boot from the "Install" icon on the desktop.

I think I will try out 8.04 and see if that installer is the same.

Cheers
/ Daniel

---

### Post by j.daniel on 2009-04-30
Ok, News:

I ran 8.04 - same game. Downloaded and a live CD of GParted: voialá, there it was: GParted said that the NTFS partition was not in order (something about bmp:s or something) and that it would not touch it even with a 10 foot pole, it said that I needed to boot windows and run chkdsk /f on the partition.

I did so, a few reboots later (chkdsk needs that), I started  GParted again and the NTFS partiton was green ok!

Just for the heck of it I did not touch the partitioning with GParted, but booted the 9.04 again just to see and all of a sudden I had a lot more choises!

So my problem was due to an inconsistent NTFS system, but the big thing here is that the Ubuntu installer sad nothing about it - I think that it should have done as GParted and said that the NTFS partition was not in order and therefore it could not do anything else than to format the whole thing.

Anyway; I'm now one step further!

Cheers
/ Daniel

---

