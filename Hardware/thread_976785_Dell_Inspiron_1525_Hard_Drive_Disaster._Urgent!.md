---
title: "Dell Inspiron 1525 Hard Drive Disaster. Urgent!"
date: 2008-11-09
forum: Hardware
---

### Post by sTpny on 2008-11-09
Yikes, I've really done it now.  I was doing a reinstall of the new Ubuntu (Intrepid) when, while the partition editor was busy doing its thing, the power went out. Normally, this wouldn't be a problem, but the battery was stone cold dead when I plugged the laptop in, and the unit lost power while the partitioner was running, now, with the power restored, the unit reports that there is no hard drive!!! It suggests to "reseat the drive" tocorrect the problem. This is a paid install, and it's urgent and important that I remedy this if at all possible. If not, I'm in trouble. (loss of time, loss of money, loss of reputation.) please help. Urgent!

Tony

Penguin Migrations - Breaking Windows and Smashing 
Gates   


ps: The output of dmesg is attached.  I live booted with the all_generic_ide option, which seems to be neeeded to boot this comp from a live cd.

---

### Post by phidia on 2008-11-09
1st thing to try I think is to remove the battery, after shutting down of course, wait a few minutes-replace the batter and then try a restart. 
If you can't boot the system and the live cd still doesn't see the drive after that maybe a power spike killed the drive?

---

### Post by stitchmysmile93 on 2008-11-09
Try running the live cd and installing gparted sudo apt-get update then sudo apt-get install gparted .  then run sudo gparted see if you see your hard disk.  Then delete and create your partitions. Then run the install...

---

### Post by phidia on 2008-11-09
Using the live cd open a terminal and type/enter > sudo fdisk -l
What is the output?

---

### Post by sTpny on 2008-11-09
Wow, that waas fast!  gparted is included on the intrepid live cd. It reports no devices found in the status bar.  Likewise, sudo fdisk -l produces no output, and the hard drive also doesn't show up in the bios. I haven't tried taking the battery out yet. I'll do that now and report back after.

---

### Post by sTpny on 2008-11-09
ok, I pulled out the battery, waited, restarted, and no change. I changed the bootup options to pnpbios=off all_generic_ide irqpoll acpi=off and I noticed the error ...ata3: SRST failed(errno=-16). It repeats three times before going ahead and booting without a hard drive. So, what do you think, am I hooped? Anyone know a good place for cheap (as in less expensive) laptop supplies? (dell inspiron 1525) Anyone have a solution? I know the hd works. The computer is just not seeing it. It just lost its power at the totally wrong time, while it was busy trying to write the partition tables I expect. The error looks like it might be short for "system reset failed", reffering to the hd as ata3. Could a flash of some sort be the answer? This has got me so freaked. It couldn't have happened at a worse time. Ugg

---

### Post by starcannon on 2008-11-09
If I were in this spot heres the list of things that would quickly come to mind:

[LIST]
[*]Pull the drive, find out its brand and make, then go to the manufactures website and download their disk utility and let it run a diagnostic on the drive, if all is well then run the restore the drive to oem state utility; this does however come with the reality that in doing so all data will be lost as the common practice is to write zero's to the drive.
[*]Put the drive in my desktop using an adapter if neccessary and try restoring its functionality that way(added bonus of the drive not needing to be mounted unless I specifically want it to be).
[*]I might also try the [gParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), or the [URL="http://www.ultimatebootcd.com/"]Ulitmate Boot CD
[/URL]
[*]Many bios's have the ability to check the disk as well, I'd also look in there to make sure bios is seeing the disk.
[/LIST]
Thats the short list, if those failed I'd do a little more thinking and digging, and if nothing else I'd cut my losses and save my rep by running out to the nearest computer supply house and buying another hdd for the laptop; if the client is understanding and willing to wait then I'd buy a drive at newegg to save some money. The only thing I'd really be in a real freak out about would be if there is data on the drive that I would need to recover, if so then I would definately make saving that first priority.

When data recovery is required I really like TestDisk's PhotoRec, it grabs all the common files that most users care about.

[LIST]
[*][TestDisk Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")
[/LIST]
Finally, be sure to stop and count to 10, find your towel, and Don't Panic.

GL and hang in there.

P.S. be sure to pick up a non interruptible power supply as soon as you can, it only takes once for it to pay for itself.

---

### Post by sTpny on 2008-11-09
The freak is mostly about the money. I've had unexpected and unrelated expenses this month that have put me way over budget.  Bad timing/freaking thing is much more about that than about any data, of which there is none. All relevant data coexists on another laptop, so no big deal there at all. I just can't put the $$$ out right now, so I'll have to tell the owner that he'll have to wait much longer than quoted for his laptop, and the cost of the drive is most likely much more than I'm charging him for the service. 

Anyhow, the bios does not see the drive at all.  Its like its not even there. Thanks for all the good ideas. I must admit that I'm too much of a newbie to be doing what I am doing, but need is a cruel master sometimes, and so far, I've got nothing but happy customers, and I'd really like to keep it that way. 

I don't have any little screwdrivers yet, so I think I've done about all I can do at the moment. This totally sucks.  Thanks again for the help, and especially the good info.

---

### Post by starcannon on 2008-11-09
You can get a "Jewelers" screwdriver set at most any dollar store, so even on a tight budget that is likely doable. By finding out what drive is in there and downloading its manufactures disk utility you may be able to bring it back, is definitely a great place to start, especially considering the circumstances.

GL and keep on plugging, you'll get there.

---

