---
title: "second hard drive becomes read-only"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by d.j.schroeder on 2006-06-30
I have a strange problem.  After a while (varies between minutes and days) my second hard drive becomes read-only.  It is always fine immediately after boot up.  I have checked fstab, everything is default, nothing weird.  When it happens the computer starts behaving oddly, the mouse will freeze in one position for a few seconds randomly, it seems to take longer to load programs or open windows.  I use the second drive as a shared drive through samba.  When it is not read-only the windows computers can use it no problem.  After it decides to become read-only the window will stop responding on the Windows machines, that is they can't even read the contents.  The Ubuntu host machine will eventually be able to open directories on that drive even after it becomes read-only but it takes forever.

As background the drive is a 500GB Western digital SATA drive, it is nearly new.  The Ubuntu boot disk is also SATA.  I don't know what other background is relevant, please be aware that I am a linux noob.

I found one reference to a similar problem on another linux forum and the problem was traced to bad DRAM.  I have run memtest and found no errors.  Anyone have any idea what could make it become read-only during use?

---

### Post by thingy on 2006-06-30
Darn!

I did a fairly long reply to this post and my logon timed out and Ive lost the text I tried to post.

Anway, the gist of my post was that the behaviour you are experiencing sounds like the windows box is loosing its connection to the samba box and hence windows explorer is blocking which would freeze the window (not sure why your mouse would freeze, is it a usb mouse) in which you were trying to access the shared resource in the samba box.

Do this to find out if it is a network issue: downloading something like ping plotter : [http://www.pingplotter.com/download.html](http://www.pingplotter.com/download.html)

and have it continously ping your samba box and chart its history. I think you will find that if the problem happens again, that there will be some dropped pings indicating that your connection to the samba box had gone down.

Also, check the samba logs to find out what they say.

---

### Post by d.j.schroeder on 2006-06-30
Thanks for the reply.  I like the ping idea and I'll give that a try.  

Just to be clear though the mouse hang ups don't happen on the windows boxes they happen on the Ubuntu box (the host for the samba server and the physical location of the drive).  It is an old PS/2 mouse recycled from an old computer, but the rest of the comp hardware is nearly new.  If the windows boxes to periodically lose connection with the Ubuntu box would that make the file system on the Ubuntu box switch to read-only?

I agree that the time out thing on these forums is set pretty aggressive, I've had the same problem you did with your previous post.

---

### Post by thingy on 2006-06-30
> f the windows boxes to periodically lose connection with the Ubuntu box would that make the file system on the Ubuntu box switch to read-only?

No.

I guess what we need is more information about the state of the machine when it is in this read-only mode. I.e. can you note the output of the mount command, the next time this happens. Also, see if you can ssh into the box and grab the log files. They may indicate if any of the services running have a problem.

---

### Post by d.j.schroeder on 2006-07-19
Ok, I think I figured out what caused the problem.  The files that I put on that second hard drive were all originally on a windows box and I transferred them over my LAN to the second drive on the Ubuntu box.  

The transfer took many hours, since it was more than 300GB of small files.  A couple of times during the transfer something interupted it and it gave an error.  I just skipped those files and kept going.  It was after this transfer that I had the problem of the drive occasionally becoming read-only.

I deleted everything from the second drive and transferred it again.  This time I transferred it in pieces, by directory name one letter of the alphabet at a time.  During a couple of the transfers I got some time-out error.  When that happened I deleted everything from that transfer and started again.  Finally, now that it has been done for more than a week, I have not had another problem.

So, it seems that occasionally, there is some error in transferring a file, and when that happens it leaves something on the hard drive Ubuntu doesn't like.  

Hopefully, this description makes sense.

---

### Post by Kallahorn on 2006-07-28
I am having very similar problems - the second (/media/storage) internal hard drive becomes read-only while transfering large files from my windows server.  If I transfer the files to my primary hard drive (/) I encounter no problems.

[17184292.204000] journal_bmap: journal block not found at offset 3084 on hdg1
[17184292.204000] Aborting journal on device hdg1.
[17184292.208000] ext3_abort called.
[17184292.208000] EXT3-fs error (device hdg1): ext3_journal_start_sb: Detected aborted journal
[17184292.208000] Remounting filesystem read-only

Any ideas? Need more info? I am relatively new to Linux - but have had no trouble figuring stuff out until this problem.

Only way to regain access is by remounting, then the dmesg returns this:

[17185706.232000] __journal_remove_journal_head: freeing b_committed_data
[17185707.236000] EXT3-fs warning (device hdg1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[17185707.240000] EXT3-fs warning (device hdg1): ext3_clear_journal_err: Marking fs in need of filesystem check.
[17185707.240000] kjournald starting. Commit interval 5 seconds
[17185707.240000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[17185707.240000] EXT3 FS on hdg1, internal journal
[17185707.240000] EXT3-fs: recovery complete.
[17185707.240000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by d.j.schroeder on 2006-08-04
My only suggestion is what, in retrospect, I should have done for my large transfers.  Use an external hard drive to move them to avoid any possible network errors.  That would have worked for me, since now that the files are on this machine I basically don't need to write to that drive over the network.  It might not be an appropriate solution for you.

---

### Post by fabertawe on 2006-08-05
If your drive is rebooting as read-only after an error it could be that your 'etc/fstab' entry has the option 'errors=remount-ro'.

'man mount' states
```
errors=continue / errors=remount-ro / errors=panic
    Define the behaviour when an error is encountered. (Either ignore errors and just mark the file system
erroneous and continue, or remount the file system read-only, or panic and halt the system.) The default
is set in the filesystem superblock, and can be changed using tune2fs(8).
```

I'm reading up on all this stuff to better understand my system.

Paul

---

### Post by d.j.schroeder on 2006-08-05
My boot drive does have that option.  The other one, sdb1, which is the one that kept switching to read only, has the default option.

---

### Post by d.j.schroeder on 2006-11-26
Solved

I finally got so frustrated with this problem that I moved the hard drive I was having trouble with to a Windows machine.  On that machine it gave file system errors even after completely reformatting more than once.  

I RMA'd it through newegg.com, where I bought it.  They sent a new one.  It works perfectly.

So I blamed linux/my ignorance of linux and it was actually a hardware problem.

---

