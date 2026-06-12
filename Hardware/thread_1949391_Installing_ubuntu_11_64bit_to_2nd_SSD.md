---
title: "Installing ubuntu 11 64bit to 2nd SSD"
date: 2012-03-30
forum: Hardware
---

### Post by patw on 2012-03-30
Hi All,
Apologies in advance for any overly simple questions. I've been using ubuntu for a few years and love it, but my original install was fairly simple, writing over a winxp HDD and using live CD.

However, I just shelled out a large amount to get an HP Pavillion HPE 8xt, pre-installed w/Win7 64bit pro and it is i7 2600 CPU, 1TB HDD, 16G Ram.
I removed all the bloat-ware and trimmed it down to pretty much just fresh windows.

My goal was to install ubuntu by itself on a 2nd SSD 128G SATAIII :
[http://www.amazon.com/Plextor-PX-128M3S-2-5-Inch-Solid-State/dp/B006I38EJ2/ref=sr_1_1?ie=UTF8&qid=1333095220&sr=8-1](http://www.amazon.com/Plextor-PX-128M3S-2-5-Inch-Solid-State/dp/B006I38EJ2/ref=sr_1_1?ie=UTF8&qid=1333095220&sr=8-1)
Unfortunately, HP is not too clear about the motherboard, but after some long research, I figured out they only support SATAII @3G even 
though they call it SATA3 (3G).. a bit deceptive.
[http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02854392&printver=true](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02854392&printver=true)
That being said, I understand that I can still install the SATAIII SSD,
but will simply be limited by the 3G speed bottleneck. I figure the cost is not much more than a SATAII, so I can still have the latest for the future.

Ok, I've thought about transferring windows7 with ubuntu to the 2nd SSD (and wiping reformatting dr. 1 as storage only), but I'm very worried about not doing it right and being hosed without the original win 7  install disks from HP (even though I did make system restore disks already).  So, it seems a reasonable approach would be to simply run windows very infrequently for Office and maybe 1 or 2 other apps, but mainly have Ubuntu on the SSD only, running most of the time, and using the 1THDD for data storage.

I'm confused about all the tech lingo regarding formatting and terminal commands for partitioning. So I hope my questions make sense;
1) If I just add in the SSD to a SATA 2 port (i.e. label, but actually SATA 3 (3G) PORT 2 in HP parlance). Can I just run live CD and get it to boot into the 2nd drive at start up?
2) I'm still unclear about pre-formatting. If it is a fresh drive, does the live install disk do the actual formatting as I step through it?
3) If I go with installing only ubuntu on drive 2, do I need to click,
'install alongside windows?' even though it isn't really on the same drive?
4) If I say not install along windows, does it still give a prompt to switch back to windows at boot up, or would I manually need to go to BIOS and change order. Also, do I still need to go to BIOS (and swap cables) to set the now primary drive to be SSD on port SATA1 or can HDD 1 still reside there? Or does the install take care of that?
5) I hear talk about setting AHIC in BIOS, but am a bit unclear on what that means. Do i need to set it that way?

I spent a lot of time reading and researching, but the technical jargon can be a bit above my head. I am eternally grateful to any advice before I start this venture, as I'd be really rattled if I hosed the new system by attempting this.

Thanks Again,
Pat

---

### Post by patw on 2012-03-30
bump.

SSD is arriving today.
No one has any input?
Is there any other information I can add to clarify.
I would greatly appreciate ANY advice before potentially putting my new system in FUBAR land.

One other point: I received the SSD and on the back it says MARVELL SMART SATA 6G/s.
I've read somewhere where someone said to ditch the MARVELL controller. Don't know if that has anything to do w/ the drive itself,
or the box is simply showing compliance, but it worries me.

P.S. I edited the title for more detail, but it didn't get updated outside of the inner thread.

---

### Post by patw on 2012-03-30
Good News and Bad News.

So, I didn't seem to get any input :( and tend to get impatient.
Good News: I used echo installer with Plextor to transfer over
Win 7 on HP drive. I also used an option to filter partitions and selected not to port over HP recovery partition (as it was hogging 17G).
Echo worked and system rebooted. To verify, I unplugged the 1T HDD drive on sata port 0 and left SSD on port 1. Success. That was good. But oddly it copied over 13 of the 17G partition from HP recover and it was highlighted in red. I didn't want this on the SSD as I have physical recovery disks.

Bad News. When I hook back up HDD to Sata port 0 and check bios to boot from Sata 1 (SSD), I get a dreaded error : cannot find device install repair disk.  I swapped ports to have SSD as port 0 and HDD as port 1. Still have error on launch pointing to SSD as 1st boot.

So I can,
1) Just run win7 off SSD with no connection to HDD and weird fragment of HP recovery that got passed.
2) Try to install ubuntu to get the partition mess fixed.
I have a feeling I should get the win part working first, but maybe not.
Any help would be greatly appreciated.

I've been kind of following this approach so far, but haven't gotten to ubuntu install yet.
[http://lifehacker.com/5837543/how-to-migrate-to-a-solid+state-drive-without-reinstalling-windows](http://lifehacker.com/5837543/how-to-migrate-to-a-solid+state-drive-without-reinstalling-windows)

---

### Post by patw on 2012-03-31
Solved all the issues all night. For anyone else struggling or contemplating transforming an HP pavillion to a dual boot win7/Ubuntu11.1 w 128G PLEXTOR SSD.
0) Get rid of bloatware via PC Decrapifier.
1) Use Echo program (free w/PLEXTOR) to clone win 7 HDD disk to new SSD.
2) Delete HP Recovery in SSD if it still exists (using win 7 disk manager; that was extremely useful in initial partition). 
2a) I repartitioned 60G to Win7 and 60G to Ubuntu (using shrink in win7 disk manager).
3) I swapped SSD to port 0 and HDD to port 1. No more boot issues.
4) After verifying SSD worked over several reboots, I then reformated everything on HDD to NTFS, but only saved the original 17G HP Recover on that drive (just in case) partition.
5) Ran Ubuntu Install and sliced up the 60G partition: 20G to root (/) and 40G to /home.
Used 900+G on HDD 1 to allocate 24G swap (not that it needs it, but still plenty left there).

Verified dual-boot.
Still have some issues to resolve...
1) 24inch HDMI ASUS moniter display looks warped, visually (like stretched). Have some jaggedness of pixels during boot (but maybe it's just now).
2) Ubuntu complained about many drivers missing and not being free.
I'll need to investigate these later. For now, time to sleep.\\:D/

One last point: It was ubuntu 11.10
HP Pavillion HPE 8xt 
Chicago IBISB MB
Intel i7 2600
16 G RAM
1T seagate HDD
1GB DDR3 *Radeon* HD 6570
128G Plextor SSD S3 6G (w/ nice 5yr. warantee and free NTI backup/ echo clone software. Clone worked great except for passing recovery partition when I said not to, but very bad reviews on backup-- so I'll stick to another solution for that).
HP only has S2 3G ports (sort of false advertising showing sata S3 (3G) on specs, but not an issue), just bottlenecked at 3G speed.
It's still blazing fast, IMO.

---

### Post by oldfred on 2012-03-31
Sorry did not see your questions earlier. But it looks like you are solving most of the issues.

Windows is sensitive to which drive it is, so plugging into the same port is important, but you should be able to do a repair and get it to change if you want. Windows is always happier as sda in sda1 (or windows 7 in sda1 & sda2). Ubuntu does not care.

You do have to pay attention to where grub2's boot loader gets installed. I normally suggest keeping each system on a separate drive. I have XP on one old drive and Ubuntu on two others. I also recently got a new 60GB SSD for my old desktop system and put two 30GB partitions for two versions of Ubuntu.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

If using Windows 7 I believe you have to install the AHCI drivers before changing BIOS.

---

