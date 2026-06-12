---
title: "Cheap Ubuntu HPC Cluster, but first..."
date: 2010-09-08
forum: Hardware
---

### Post by Calaway21 on 2010-09-08
I have acquired ten Compaq D510 SFF Evos. All of which are identical in hardware specs: p4 2.0GHz processor, 512MB RAM, 40GB HDD. Naturally, just as anyone else would, I saw a potential cluster. 

The twist is, I also have access to enough p4 2.8Ghz Hyper-Thread processors to upgrade them all and thereby significantly increase the performance of my cluster. However, the current BIOS version does not support that processor. The good news is that Compaq released an updated BIOS version that does support the new processor.

Now the Question: How do I update the BIOS using a non-windows machine, without a 3.5 inch floppy?

I have tried unpacking the sp23347.exe file to a USB flash drive but to no avail. The current BIOS supports booting from USB media (I loaded the OS that way) but, it will not recognize the new ROM on the flash drive and just boots into the OS.

I would really appreciate any help on this. I plan on making a full documentation on how to configure an HPC cluster with Ubuntu and then posting it for those who would like to do the same.

---

### Post by Fafler on 2010-09-08
Whats inside the .exe file? Theres several ways to go, but first we need to know what were dealing with.

The old P4's aren't that energy efficient, you know, if you plan to use it alot, but still, i would also get myself a cluster if i got 10 machines like that :-)

Look into setting one up with a faster drive and make it netboot the others, disabling the internal drive to save approx 10 watts each. Running systems that way is actually quite fast if it's set up correctly. Get a gigabit interface for each one of them and a switch.

I really look forward to see what you'll get from them.

Edit: One way to do it could making a Windows installation on a spare drive, and just pass it along over all 10 machines, upgrading the BIOS in the process. And dude, pics ;-)

---

### Post by ajgreeny on 2010-09-08
Whether this is an answer or just another red herring, I'm not sure, but I have read somewhere about the possibility of flashing BIOS using free-dos.

I have no idea if the lack of floppy affects that possibility, nor do I have the slightest idea how to flash a BIOS without a floppy, though I presume it must be possible with CDs in some way, or alternatively using the USB boot which you have already tried.

Sorry not to be a real answer provider for you, but just thought it worth mentioning free-dos, in case you have never heard of it.
I've just found this thread:-
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by Calaway21 on 2010-09-08
@Fafler

When I extract the .exe I get "SP23347.cva" and "68602.CAB". If I further extract the .CAB file I get "Rom.bin" and "Rom.sig" which cannot be opened by any application that I have on the computer that I am currently on.

I know the p4's aren't very energy efficient but, the price was right and I want to build this for completely educational reasons. I'm not thinking of using it beyond building it, benchmarking, tweaking, learning, breaking, fixing, rinse and repeat (if you get my drift). I also didn't want to spend any money on it because, if I can figure out how to do it, I would rather put that money toward something with quad-cores and newer technology. This could potentially spawn a new hobby.:D

@ajgreeny
Thanks a lot for that post. I haven't went over it in detail because I'm not near my cluster but, that looks exactly like what I need. I just wonder why it didn't come up in my Google search.


I will definitely post some pics for those who would like to see them.

---

### Post by Fafler on 2010-09-09
Then try out [http://www.flashrom.org/Flashrom](http://www.flashrom.org/Flashrom)
It seem to be the right kind of BIOS file for that, and methods including using GRUB to emulate a floppy won't work as theres no flashing tool included anyway.

---

### Post by Calaway21 on 2010-09-09
Flashrom is a no go. The compatibility table on the flashrom website says that I at least have read capabilities but, I can't even get it to that. I forced it to read and all I got was garbage speckled with little bits of info.

I will try a few more things and then I'll post an update.

---

