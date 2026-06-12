---
title: "-512 size USB drive?"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Tdraket on 2008-01-28
I bought a 500GB western digital external hard drive.  I had it plugged into one of my friends computer that ran winblows and some random error popped up on the computer and shut down.  After that my hard drive wont mount or even display it's drive size correctly.  I could care less about the data I had on it.  When I tried to use GParted to reformat it, the drive shows up as -2872832.00 B in size.  Then it says there is -512 B unallocated space which shows up as the entire drive.  So I say format the -512 B and it says I need to set the disklabel on /dev/sdb/ which is the drive.  So I try to set the disk label and it says error while setting new disklabel.  I tried to use some program named testdisk and it showed the drive as being 2000 something GB.  I did some fix scan thingy with it which ran for 4 days and in the end it did nothing.  I'd appreciate any help I can get.

---

### Post by Herman on 2008-01-28
Hello Tdraket,
I don't know about other people's USB external hard drive enclosures, but I do know that with my own 2.5" laptop hard drive enclosure, the USB enclosure's electronic board does something to the way the hard drive is seen by the computer. When drives are swapped between the laptop and the computer, (the laptop hard drive and the external USB hard disk are switched around), they either aren't bootable or are not even readable in one or the other until they're reformatted. I haven't investigated exactly why that happens, but that's what mine's like.

Try to isolate the problem.

The first thing I would try , to begin with would be removing the hard disk from inside the USB caddy and plugging it into a normal SATA or PATA (IDE) cable connected to a motherboard.
That's to simply things a bit to start with.

If your luck improves it might tend to indicate a fault in the USB enclosure's electronics. 

Install smartmontools in Ubuntu and take a look at the messages in the memory of your hard drive's electronic card with smartmontools.
```
sudo apt-get install smartmontools
```I don't think you can test it while it's inside the USB enclosure, I think you probably can when it's plugged directly into your motherboard though, but only if your hard drive supports S.M.A.R.T.
Here is some help to get you started with smartmontools, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").
See if you can find out anything that way, that might tell you the whole story.

I suspect heat buildup can be an issue in external hard drive enclosures. 
 You said it failed right away though, so maybe some electronic part has blown and it might just be a faulty part. Maybe you'll have a warranty claim.

Good luck with it, I hope everything will work out well with it.
If it looks like the fault is in the USB caddy's electronics I'm not sure, but you might need to have it in another USB enclosure to access your data. 
Regards, Herman

---

