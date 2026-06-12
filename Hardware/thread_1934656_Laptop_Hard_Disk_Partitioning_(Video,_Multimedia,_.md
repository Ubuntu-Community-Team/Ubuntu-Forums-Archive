---
title: "Laptop Hard Disk Partitioning (Video, Multimedia, Audio Usage)"
date: 2012-03-02
forum: Hardware
---

### Post by janisgeiger on 2012-03-02
I own an internal 320 GB hard disk and want to set up my laptop to be a good working environment for video editing, audio production and graphic design. (Pretty much the maximum task I can offer to this device I guess (did I mention I'd also code some software and texture my 3D levels?))

So, I'd be glad if someone has some experience in this to share, if so, thanks.

I figured it'll be pretty much impossible to optimize it for every need individually, so I think I'll have to find a compromise, and therefore aim to roughly divide it into three spaces

A linux distro on the first partition + swap space on 2nd
Main OS, main OS for working on video + audio (not storing the content).

A 2nd area subdivided into [Storage]

-Video-
-Main Audio Project Files-
-Documents, tarballs (trash), etc-
-External Music-

The files of my projects themselves, plus something like cross-plattform-storage-files

A 3rd area containing Vista (as slimweight as I can possibly make it), containing Photoshop and maybe audio production software that doesn't run on Linux.

Does this sound like a good idea?

I've read about read/write speed access of hard drives, getting slower to the inner (right) area of the hard disk, affecting the performance of video rendering and audio work containing multiple tracks, thus I came up with this idea. I suppose this is true for Linux also, not only for Windows, right?

As my video partition will be a lot smaller than my audio, I'd put it in front of the audio partition, as some kind of compromise between being able to work good with video, but optimal for my circumstances in audio as well.

Another idea would be to create a "Working Partition" right before linux, about 5-15 GB, that stores the contents of my current projects only... But wouldn't this slow down my system and thus not providing any real advantage? Any experience / advice?

As I want to use Vista mainly for Photoshop (CS5), but not very often, I'd put it at the end of the drive, even if that slows it down, to get my video and audio partition as close to the outer edge of the drive as possible, but *probably* not in front of Linux because I don't want the actual system to slow down.

Is there anyone having had similiar aims in setting up a laptop, or some experience in what I want to do?

Thank you! Cheers.



PS: Another thing is the term "Scratch Disk". It seems to be used by software like Photoshop, and also Blender. 2 softwares I might use.... Holliemollie.

---

### Post by TheFu on 2012-03-02
A single physical HDD has a limited number of "primary partitions". That limit is 4.  Some OSes **must** boot from a primary partition.  I don't know if Windows does anymore, just that it used to require that.  Linux can boot from any partition typ, but since there really isn't any count limit to the number of logical partitions, it makes sense to use logical partitions for everything.  Windows can access data/programs/anything on a logical partition provided it is NTFS or FAT-whatever formated.

a) primary partition for Windows
b) Extended Partition for everything else.
b1) logical partition for Linux
b2) logical partition for swap
b3) logical partition for "data"

As to any other organization, if you only have 1 physical disk involved it doesn't matter. 1 disk will only go so fast.  A laptop drive will be slow regardless of what you do. Sorry.  I've never bothered trying to get 5% better throughput by worrying about the physical location of data on a laptop HDD.

Perhaps someone else will post a better solution?

---

### Post by janisgeiger on 2012-03-02
Ok, thanks, especially for that hint about the extended partitions... was about to create a new "primary partition" for all of my media stuff (couldn't create a new extended one) and already copying to it, but it makes better sense that way, so I will completely reformat and copy it anew.

I will put vista at the complete end of the drive nevertheless.

To me, it's some kind of a mental note that you, in my case I, still can do relevant creative stuff without having to afford a MacBook or having to buy huge audio software like Logic, just trying to do it in the best way I can with the hardware I have. So far, the switch to Linux was dreadful and crazily-complicated, but I hope it will pay off in the end.

Maybe I'll post a link if a project comes to existance.



PS: And thanks for kind of relieving the seriousness about my worries, I  know I'm a bit funny concerning my sub-optimal setting, but still I was  just kind of in mind of this article and picture
[http://media.soundonsound.com/sos/may05/images/pcmusician2.l.jpg](http://media.soundonsound.com/sos/may05/images/pcmusician2.l.jpg)
[http://www.soundonsound.com/sos/may05/articles/pcmusician.htm](http://www.soundonsound.com/sos/may05/articles/pcmusician.htm)

Which shows access would still be slower than it already is, which I  wouldn't want, which would be better at the beginning of the drive. Who knows. Cheers!

---

### Post by TheFu on 2012-03-03
Real world performance improvements are harder to achieve than simply moving the data to the inside of a HDD.  Most laptop HDDs are slow - even my "fast"  7200rpm spinning laptop HDD can't touch the performance of a desktop "black" HDD spinning at the same speed. If you really want more speed, put in a SSD.  

Tuning the file system with OS settings for a large disk cache can help hide how slow the disk really is too.  I have no idea how to do that on Windows, but for Linux you can google and find those settings.

If you need external storage and it won't be flash/SSD, then use eSATA or USB3 - in that order. USB2 is slow and in comparison to the first 2, so is firewire.

---

### Post by janisgeiger on 2012-03-04
Ok, let me just tell you one thing: Linux is completely crazy.

To move my existing Ubuntu into an extended partition, I made a backup .img file, ~24GB in size. I booted into a live environment and happily erased the whole Ubuntu partition.

How the hell.... after a day being lost inside google & forum threads about "HOW TO EXTRACT/RESTORE from an .IMG file" (to a new partition)

I just mounted the image into a folder and used the CP (CP!!!!) command and *nothing else* to just copy it. 

I had errors before just doing it via gksudo-nautilus- so who (the hell) would've thought something like this small command would fix everything?

And why the hell did it copy these files in under a nano-second?

And why the hell can I completely boot back into Ubuntu now, being on a logical drive in my extended partition, as if nothing happened? Even the folders on the desktop are where they used to be, everything. Even JACK, the biggest headache for me in the first place, is working without any problems??

"What is going on in the linux world?"

To go back on-topic: I might have to research further about how to install an additional SSD drive (directly), I doubt my laptop would support this without any further fixes like "convert my DVD drive into an optical bay hard drive caddy"

which definately sounds promising and would take my set upto another level I guess. At the moment, and following my initial thoughts, I have 5GB unollacted space for current projects - have to digg further which file system I will use, and if it makes any difference / advantage if i put it on a primary partition ... - then the big extended partition containing- Linux (...) - all these media things - and Vista Windows at the end on its own NTFS partition.

[SIZE=1]If I make Vista slimweight and re-install it in sometime and check out how to further optimize, I might have finally achieved my goal of optimizing my hardware in the best way I can.[/SIZE]

Crazy project I know... :D Now I'll see if deleting my backup img won't do no harm. - the original folder i extracted it too is empty, so I guess everything has definately been copied to its own place. but let me tell you, "accidents" like these just leave me pretty  puzzled... Well...

---

