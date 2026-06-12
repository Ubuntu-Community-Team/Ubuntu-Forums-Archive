---
title: "Weird PC lockup/freeze on my i7 desktop?"
date: 2015-11-17
forum: Hardware
---

### Post by cybrsaylr on 2015-11-17
It occurs several minutes after boot up where the mouse becomes totally unresponsive, along with the keyboard. Believe all the USB ports also go dead on my i7 in the signature below. This happens after doing a cold start. I don't leave the PC on 24/7. What I have to do is a 'hard shutdown', then restart the PC and usually all is well but once in awhile everything locks up again where I have to do a hard shutdown again. Once the PC warms up completely all is well. It does not lock up again until the next day when booting up again cold. This Dell i7 is 6 years old and has been trouble free and still faster than new with a 3 year old 128GB SSD that I installed. 

It seems that once it is fully warmed up this lockup never occurs.
Anyone have any ideas what may be causing this lockup?

---

### Post by khelben1979 on 2015-11-17
OK, is this happening with both operating systems?

---

### Post by tgalati4 on 2015-11-17
Dell has spent over a billion dollars (US) to replace bad power supplies.  The fact that it has to "warm up" is consistent with a bad solder joint or a bad capacitor in the power supply.

---

### Post by cybrsaylr on 2015-11-17
Yes it happens with both Ubuntu and Windows 7 on this i7 desktop. I just did a cold start boot up into Win7 and after a few minutes everything froze up. Had to do a hard shutdown, then restart and Windows did a checkup on PC then restarted normally and after a minute froze again. Repeated restart again and all appeared to run normally. Then restarted and went into Ubuntu and all appears normal with no lockups. 
FWIW that 128 Kingston SSD always showed an error message from day one when it was installed, when running Disks > Smart Data & Self tests, reporting SSD is failing due to low temp! After several minutes this red flag goes green, once PC SSD disk warms up to 99 degrees Fahrenheit. However PC never locked up like it is doing now. Years ago I did contact Kingston telling them of this and after some checking Kingston claimed it was no problem, just a too tight parameter setting on the SSD disk temps.

---

### Post by weatherman2 on 2015-11-17
Sounds like a failing power supply or motherboard.  Hope it's the power supply - relatively easy to try another one and see if that fixes the problem.  Failing motherboard probably isn't fixable by the average person and are almost always replaced not repaired.

It could be some other component besides the motherboard.  To try to narrow it down, remove all possible components (e.g. hard drives, video cards, everything but what is required to POST).  Once you do that, after the PC is cold, boot Ubuntu from a live USB and run Memtest for a while and see if you get the same freezes.  If so, and you have already tried a different power supply, it is probably the motherboard.

---

### Post by cybrsaylr on 2015-11-17
OK. Will play around with trying that. PC has two hard drives. A 2TB Seagate HDD with Windows 7 and a 128GB SSD with Ubuntu 14.04 and Ubuntu 12.04. Posted that so you know it froze up on both OSs that are on separate hard drives. As I said once it is thoroughly warmed up PC runs fine with no issues.

---

### Post by cybrsaylr on 2015-11-18
OK disconnected the SSD and then did a cold boot up of Windows 7. After six minutes of running W7 and PC locked/froze up everything. Mouse red LED light went out and all USB ports are dead, as it did with Ubuntu. Then had to do a hard shutdown. Restarted PC and got a series of fast beeps, on the initial Dell splash screen. This never happened before but this is with running W7. Hit and held down the power button again. Then restarted again. This time all was well and W7 started up normal. W7 wanted to do a disk scan, which I skipped and went into a normal start up. Now that PC must be warmed up sufficiently all seems to be running well and am able to make this posting.

---

### Post by weatherman2 on 2015-11-18
OK, sounds like you have ruled out the SSD as a cause of the problem, anyway.  You might still remove other components like I suggested and try again to see if you can eliminate them.

You might also try re-seating your RAM - just pull out RAM sticks and re-insert them securely.

But all of these things are to try to eliminate the motherboard (the worst case problem) as the real cause of your problem.  And also the power supply, which, again, I suggest you try to swap out to see if that fixes the problem.

By the way, it's probably not a wise idea to boot any operating system when you know you have this kind of issue.  "Hard shutdowns" etc. can corrupt your files and should be avoided if at all possible.  If I were you, I would get into a habit of turning on the PC and say going into BIOS setup or a boot menu for something and wait about 10 minutes to "warm it up" before booting anything.

---

### Post by tgalati4 on 2015-11-18
Or, pull the disks out, put them in external USB enclosures and use a USB stick to Live Boot and continue to troubleshoot.

---

### Post by cybrsaylr on 2015-11-18
> **weatherman2 said:**
> You might also try re-seating your RAM - just pull out RAM sticks and re-insert them securely.

  And also the power supply, which, again, I suggest you try to swap out to see if that fixes the problem.

By the way, it's probably not a wise idea to boot any operating system when you know you have this kind of issue.  "Hard shutdowns" etc. can corrupt your files and should be avoided if at all possible.  If I were you, I would get into a habit of turning on the PC and say going into BIOS setup or a boot menu for something and wait about 10 minutes to "warm it up" before booting anything.

Thanks for the troubleshoot help so far guys.

Re RAM: The last few weeks I would get a weird report sporadically on System Monitor which only showed 3.9 GiB of RAM (or half my RAM avail) when it always showed 7.8 GiB of RAM from day one and as it is showing right now. Usually a PC restart rectified that in the past, which would bring the report back up to 7.8 GiB.

Haven't had a chance to get a new power supply to test if that is the problem.

Awhile back somebody gave a way of avoiding "Hard shutdowns" but forgot how it's done.
Anyone know how to do that?

Besides going into BIOS setup or a boot menu for something and wait about 10 minutes to "warm it up" before booting anything. Could the same be done by using GRUB, by switching to another OS then waiting that 10 minutes for a warm up? 

What makes this a pain troubleshooting is when fully warmed up this i7 runs great.
Have to wait till it's cold to troubleshoot it.


Is there anything in "Disks" > Smart Data & Self tests, that may show what the problem is?

---

### Post by weatherman2 on 2015-11-18
> **cybrsaylr said:**
> Awhile back somebody gave a way of avoiding "Hard shutdowns" but forgot how it's done.
Anyone know how to do that?

No.  If you have a hardware problem like you have, you probably can't avoid hard shut-downs sometimes.  In your case, the best way to avoid them is to wait to warm up the PC before using it.

> Besides going into BIOS setup or a boot menu for something and wait about 10 minutes to "warm it up" before booting anything. Could the same be done by using GRUB, by switching to another OS then waiting that 10 minutes for a warm up? 

If you can stop the Grub menu from booting an OS, that is reasonably safe, but you'll still have to do a hard shutdown if the PC locks up in that state.  It seems safer to me to "park" in BIOS setup instead.

> Is there anything in "Disks" > Smart Data & Self tests, that may show what the problem is?

Your problem does not sound like a hard drive issue to me.  You have already ruled out the SSD.  If you did what I suggested earlier and unplug all unneeded device including all drives then power up cold and boot a live USB and find you still have the problem, you could rule out all drive problems (and the other components you have removed) for sure.

---

### Post by cybrsaylr on 2015-11-18
OK did this. Opened up the box and cleaned vacuumed it out, it was due.
Then removed and firmly reseated the 4 RAM sticks. 
Disconnected the 2TB HDD. Running solely off the SSD.
Was able to "park" the PC with GRUB. I have 3 choices Ubuntu 14.04, 12.04 and Win7. Once you select something other than the default on these choices all is parked/suspended until you hit 'enter' on the desired OS.  

On reboot System Monitor shows 7.8 GiB RAM being used. 
Also 'Disks' shows the SSD temp dropped to 80 degrees F and it had a RED flag. To play it safe, I immediately shutdown PC, then reboot and used GRUB to park the PC until it warmed up. Then after several minutes hit enter and booted up with 14.04.  'Disks' shows the SSD temp warmed up to 93 degrees F and that RED flag was gone, as was expected. .

---

### Post by weatherman2 on 2015-11-18
Because your problem occurred previously without the SSD even plugged in (when you booted Windows 7 from the hard drive then your PC froze again), we know it has nothing to do with your cold "PC problem."

But if you wish to explore the SSD issue, install GSmartControl and check out the Attributes and Errors.  Whatever "Red" you were seeing ought to show up there.  Check as soon as you successfully boot after cold if you think you see the "red" problem only when the SSD is cold.  But again, it appears to have nothing to do with causing your original problem.

---

### Post by cybrsaylr on 2015-11-19
> **weatherman2 said:**
> But if you wish to explore the SSD issue, install GSmartControl and check out the Attributes and Errors.  Whatever "Red" you were seeing ought to show up there.  Check as soon as you successfully boot after cold if you think you see the "red" problem only when the SSD is cold.  But again, it appears to have nothing to do with causing your original problem.
FWIW. The RED flag in, Disks > Smart Data & Self tests, indicated this Kingston SSD was failing from day one when temp was <88 degrees F. Once it warmed to >89 degrees F the RED went away and Disks > Smart Data & Self tests, report the SSD is OK. I had called Kingston on this 3 years ago. Kingston was quite helpful and said it was a too tight 'temperature' parameter setting on their part and not to worry over it. This SSD has run fine all that time and am very pleased with its performance.

---

### Post by weatherman2 on 2015-11-19
Yes - so that S.M.A.R.T. Attribute can be safely ignored.  It makes no sense that an SSD would be "too cold" anyway unless you have just put it in a freezer before using it or something.

---

### Post by cybrsaylr on 2015-11-21
Well the last couple days did a normal cold start with no lockup/freeze-ups.
Hoping that removing and resetting the RAM solved this issue.
Everything  has been running great since doing that.

The only other thing is a 2TB HDD is still disconnected and am running solely off the SSD.
Maybe tomorrow will reconnect the HDD and see what happens.

---

### Post by cybrsaylr on 2015-11-23
FWIW reconnected the 2TB Seagate HHD last night after shutting down PC.

Did a could start today and all seemed for the most part normal but there was a little quirk. This 2TB HHD has Win7 on partition 1, partition 2 is used for storage and this HDD is about 3 yrs old. It replaced the OEM 1TB Seagate HHD that died after 3 yrs, right after the warranty ran out! 

When doing a cold start today went into Ubuntu 14.04 and a couple seconds after it booted up, 14.04 went into the Login screen. Put in password and 14.04 started all normal as expected but I had it set not to go through any Login screen, just to directly boot up into 14.04 if no other OS was selected on GRUB. PC warmed up normally with no lockups or freeze ups after several minutes as was the initial OP issue. 

This 2TB HDD has 8 bad sectors as shown in the Disks report below: 
[IMG]http://s3.postimg.org/a7lf7vo9v/image.png[/IMG]

Therefore could this 2TB HDD be causing some problems? 
Other than that, all seems to be running well so far.

---

### Post by tgalati4 on 2015-11-23
It's normal for a large drive to have a handful of bad sectors.  If the sector count increases with time and gets into the hundreds, then I would be concerned.  It's possible that the addition of the disk drive pushes the power supply to the edge and causes issues.

---

### Post by cybrsaylr on 2015-11-23
This 6 yr old Dell i7 came with a 400 watt PS.
The only upgrades made were the Kingston SSD little over 3 yrs ago when the OEM 1TB HDD failed. Then added the 2TB HDD a couple months later for Win7 and extra storage. About 1½ yrs ago upgraded the video card through Dell. Selected a video card Dell recommended that would not over tax the existing OEM power supply. Oh and added another optical drive because a buddy gave me one he didn't need but almost never use them both at the same time. Just assume there is no strain if 2 optical drives are there but not used together.

---

### Post by weatherman2 on 2015-11-23
Your login issue might be unrelated to the cold start issue you were having.  Let's hope re-seating the RAM fixed that.  I'm not sure how installing the hard drive caused the SSD install of Ubuntu to do the login screen.  One thing that comes to mind is that you may be using device IDs like /dev/sda1 etc. in your /etc/fstab file to identify partitions to mount at boot.  You should use UUIDs instead, because those don't change when you re-arrange drive order.  If you add a new hard drive then that one may now be /dev/sda whereas the SSD used to be /dev/sda and now is /dev/sdb.  Just a guess - but I would check your /etc/fstab file for any device IDs like /dev/sda1 .  If you see them, replace them with UUIDs (use the blkid command to find the UUIDs of partitions you want to mount).

I don't see the "Current_Pending_Sector" (count) listed in the S.M.A.R.T. Attributes - but perhaps the RAW value is 0.  Still, I'd scroll down in the S.M.A.R.T. data you show above to make sure that one is 0 - it's one of the most important S.M.A.R.T. attributes I pay attention to.  That number above 0 can be potential catastrophic though not always.  It means a sector on your disk is in an unstable state and cannot be read.  If the sector is in a file that the operating system attempts to read/write, you might experience freezes or unusual problems.  It's common for failing hard drives to see an increased number of pending sectors.

Reallocated Sectors are sectors that the drive's firmware has already detected as bad and has mapped "do not use" and replaced with spare sectors.  Every modern hard drive has "space sectors" to replace those that have failed.  So a few Reallocated Sectors isn't necessarily bad, but it makes me pay a little extra attention to such a drive.  If the number keeps going up, I would replace the drive, personally.  A drive only has so many spares, and once you run out of spares to replace failed sectors, the drive is pretty much junk, because new failed sectors cannot be reallocated to spares.

But - at the moment you have 0 Reallocated Sectors on that drive so not an issue yet.  Non-zero pending sectors would be a different story.

---

### Post by cybrsaylr on 2015-11-24
weatherman2 thanks for your helpful input.
Here's the balance of those missing  S.M.A.R.T. Attributes you mentioned:
[IMG]http://s23.postimg.org/9emti7z6z/image.png[/IMG]

---

### Post by weatherman2 on 2015-11-24
Well, those are 8 pending sectors then - not good.

I don't think they would cause "freezes" in Ubuntu, but they certainly could in Windows.  But I doubt it would be "temperature-dependent" - like the cold start problem you were having.

In Windows, you might consider running chkdsk to try to fix any files that contain those 8 sectors.  It's possible that could cause those sectors to be reallocated, maybe not.  If not, I would expect problems in Windows., and I wouldn't store any data I care about on that disk.

---

### Post by cybrsaylr on 2015-11-24
Win7 is seldom run anymore. Mainly kept W7 because it came with the i7. Was planning on getting and installing Win10 on it because it qualifies for the free W10 upgrade. Will have to reconsider that thanks to what you posted.

As far as storage goes I now save important files on 3 HDDs. Started doing this after getting burnt by a HDD failure many years ago when PCs were new to me and I thought they would last a long time like they were touted to. I found out the hard way everything can fail....lol

---

### Post by weatherman2 on 2015-11-24
For what it's worth, hard drives can be found pretty cheap on sale now, especially small ones, as we approach Black Friday.  You don't need a big hard drive for Windows - mostly what you need is reliable data storage.  

I would probably replace that drive.  You could try cloning it so you don't have to re-install from scratch.    You could also wipe it and zero it out afterward; sometimes that will clear pending sectors (I have seen that work in a few cases, not always).  Or just keep using it with Windows 7 for now.  My preference would be, if you are going to keep Windows as a dual boot to stick with W7 anyway  MS will support it until early 2020.

You might also consider installing Windows in a virtual machine in Ubuntu if you need Windows only occasionally.  That's what I do these days.  I prefer to use Ubuntu most of the time and use Windows only when I have to for certain software.  There may be a product key sticker for Windows 7 on the side of your box; if you can get a Windows 7 install disc to match that you can use the key to install Windows 7 in a virtual machine.

---

### Post by cybrsaylr on 2015-11-27
Yes drives are cheap. Picked up a Black Friday 480GB Sandisk SSD on sale. Now have to decide if W7 or Ubuntu should go on it...lol.

Acronis True Image 2016&#8206; can be used to clone W7 but can it clone Ubuntu 14.04? 
Was thinking of wiping the 128GB SSD clean and putting W7 on it. Then use the new 480GB SSD for Ubuntu which is mainly used.

Right now all W7 is needed for is updating a Garmin GPS because as yet Garmin will not support Linux. Garmin uses only Windows and Mac for updates and had no plans to use Linux when I called them to ask about that.

---

### Post by weatherman2 on 2015-11-27
In that case, if Windows is needed only for that one thing, do consider the virtual machine approach - so much easier to deal with than dual boot.  You may have to muck with exposing the USB ports to the virtual machine but if you can make that work, it would save you sooooo much hassle not having to worry about a dual boot with Windows anymore.

True Image rescue CD version is Linux based.  It seems to be aware of ext partitions at least the newer versions are.  I have used it to clone Linux partitions in the past.

But you can always just use Clonezilla instead, which will definitely clone your Ubuntu SSD to a larger one.

---

### Post by weatherman2 on 2015-11-27
Or just put both Windows 7 and Ubuntu on the new SSD to simplify things.

---

### Post by cybrsaylr on 2015-11-27
Well installed Clonezilla but am wondering how do you use it?
Looks like you have to open it in Terminal, did that but what next?
Looks complicated.
Read this that says Clonezilla is easy to use: [http://www.techrepublic.com/blog/windows-and-office/how-do-i-clone-a-hard-drive-with-clonezilla/](http://www.techrepublic.com/blog/windows-and-office/how-do-i-clone-a-hard-drive-with-clonezilla/)
Since all this is new to me it has me stumped....lol

---

### Post by weatherman2 on 2015-11-27
The biggest downside of Clonezilla is the user interface: it is NOT that simple to use.  It is text-based (but with menus so you don't really have to type commands).

Although I think you can install Clonezilla in a Ubuntu installation, I prefer not to use it that way.  instead, I prefer to create a bootable Clonezilla USB or CD.  Anyway, to clone an operating system, you generally DON'T want to clone the "live" mounted partitions unless you used an LVM and are cloning a snapshot of the mounted partition.  Unless you know what an LVM or a snapshot is...you probably haven't done it this way.  In that case, you should do it the way I suggest: create a bootable Clonezilla USB stick or CD.

Go here:

[http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)

and choose "iso" as the file type in step 2.  Then burn to a CD.

OR, download the zip file and use that to make a bootable USB stick instead.  (I don't recall using the zip method - I though I had used an ISO to make a bootable USB, but I don't remember - I haven't created a new bootable Clonezilla stick in a few years now.)

Once you boot the CD or USB stick with Clonezilla on it, it's generally pretty easy IF you pay attention to every step.  Clonezilla can work with "images" meaning it could save a complete snapshot of any partition or disk to say a large external hard drive, and the image could be restored later from that; you could store many Clonezilla images on a single drive that way (this is how I sometimes make backups of my different system drives).  Or instead of images, you can do straight cloning - probably what you want to do - and simply clone from one disk to another, with both connected up at the same time.  Anyway - for the latter case, don't choose "work with images" from the menu, choose the obvious option.

Just follow the Clonezilla menus in beginner mode.  It will show you the commands it is going to run but you can probably ignore them unless you ever plan to use Clonezilla from a command line later.  I don't think I ever have - "beginner mode" is what I've usually used even though I don't consider myself a beginner.  The most important thing is making sure you understand which drive is the SOURCE (the original) and which one is the DESTINATION (the new disk).  Obviously you don't want to clone your blank drive on top of the existing drive!  But I think it will be obvious which is which, and you can't clone a larger drive to a smaller one in Clonezilla as I recall.

Programs like True Image are much, much more user friendly.

---

### Post by cybrsaylr on 2015-11-27
> **weatherman2 said:**
> Go here:

[http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)

and choose "iso" as the file type in step 2.  Then burn to a CD.
Did this and ...WOW that's a lot to digest!
As I said am new to all this.

Did burn an 'iso' CD of it. Then booted up with it, to get a look at Clonezilla-Live. Went through the setup trying to pay attention to what you said, to see what it does. Used all the default settings and "beginner" mode, got to the point where it was ready to 'clone' Ubuntu 14.04 to the 2TB HDD (which is still in. Didn't pull it and replace it with the new SSD yet). Then aborted it all. Hope this was the proper procedure?

As I said this is a lot to digest.

---

### Post by weatherman2 on 2015-11-28
Yep - sounds like you did it right.  Once you have the new SSD and are ready go to with cloning it, plug everything in (and to be safe, unplug temporarily any disk you don't want to touch) then boot the Clonezilla CD again and go back into Beginner Mode.  

It looks more complicated than it is.  Use common sense: if you are cloning a 120GB SSD to a new 500GB SSD, and those are the only two disks plugged in during the clone, chose the 120GB as the source/original and the new 500GB as the destination.  If you can keep track of that, Clonezilla is smart enough to do the rest.

---

### Post by cybrsaylr on 2015-11-28
Good to hear.
When doing the walk through with Clonezilla-Live only the Ubuntu 14.04 partition 2 was selected. What about the swap partition? Will that be created by Clonezilla? 

Here's what the 128 SSD looks like:
Partition 1 is Ubuntu 12.04
Partition 2 is 14.04 with swap
Was thinking about cloning the entire drive because I did a lot of customizing of 12.04 and use it on occasion.  
Can cloning the entire drive be easily done?
[IMG]http://s21.postimg.org/y4o8nwfyv/image.png[/IMG]

---

### Post by weatherman2 on 2015-11-28
Yes, Clonezilla can clone an entire drive even with multiple partitions.  But, it may get complicated because if you are cloning to a larger drive, how will Clonezilla decide how to size the new partitions?  Should it clone them at exactly the same size and leave empty space at the end and let you deal with it?  Or should it proportionally add extra space to all the partitions?

If you are cloning a drive with one OS, with a single / partition (plus swap), this is easy: just add all the new space to /.  Not as easy with multiple operating systems and partitions on a single drive but doable.

In your case, if Ubuntu 14.04 (your usual OS?) is Partition 6 (inside the extended partition), then you might be able to tell Clonezilla to leave Partition 1 (Ubuntu 12.04?) the same size but grow Partition 2 (the container, the extended partition) with all the new free space.  Presumably it will not grow the swap and add all the free space to Partition 6.  But, this is where the user interface of Clonezilla is a challenge; you probably can figure out the command line opts to do what I've just described, but it's not in a graphics window where you can use a mouse to chose sizes and things - you have to do it with menus and commands.

Yes, Clonezilla will create a new swap partition on the new drive.

By the way: it's not really that hard to clone a Linux drive like this manually, and if you do it you might learn some things.  I have cloned drives manually with Gparted many times.  (Boot any Ubuntu CD or USB with Gparted on it.)  Here's how I do it in a nutshell boot Linux, use Gparted to create the new partitions on the new drive, at exactly the sizes you want them.  Then one at a time, go to the source drive in Gparted, right click over each partition and choose "Copy" then back to the new drive and new partition and choose "Paste."  Do that for each partition (no need to copy swap but create a new swap).

Once you've done that, you need to do two or maybe three more things:  temporarily mount the /etc/fstab file of each Linux OS on the drive and update the partition mounts - because the UUIDs of the new partitions will be different.  Use the command "sudo blkid" to find new UUIDs and just replace them in your /etc/fstab files, with a text editor.

Finally, you'll need to re-install Grub.  Do a web search for "ubuntu grub chroot" - that's the method I prefer.   Just copy and paste the few commands they list on the help page (because you don't have a raid, you can ignore all of the mdadm commands - it's only about three commands).

The last thing you might need to do , if you ever use the hibernate feature in Ubuntu (instead of standby/sleep) is to change the partition UUID in the file /etc/initramfs-tools/conf.d/resume (in each operating system).  You'll want to change the UUID (after you've cloned and booted each OS) to the UUID of the new swap partition, then run the command "sudo update-initramfs" .  But if you don't use hibernation (not even enabled by default anymore anyway), you can ignore this paragraph.

The manual approach is more work, but it lets you control easily exactly how you partition things, and even though you can probably figure out the clonezilla commands to size partitions exactly the same way, you'll probably learn more doing it manually.  Up to you!

---

### Post by cybrsaylr on 2015-11-28
Have Gparted  but never used it for cloning.
Clonezilla looks like the better option.

Ubuntu 14.04 is the main OS in Partition 6 and Partition 5 is Swap. Will most likely clone 14.04 at its existing size. Was just concerned if swap would be auto created with Clonezilla. There will be a lot of free space left over. Will this free space show as being fully usable as Ext4? Is there any need to create a separate partition for this extra free space as storage?

---

### Post by weatherman2 on 2015-11-28
You will have to figure out how to tell Clonezilla what to do with the extra free space.  As I said above, it isn't going to read your mind and know you want to keep one partition the same size as your original disk but grow the other partition.  (If you had just one OS partition it would know exactly what to do.)  It can proportionally grow both of them or keep both the same and leave free space at the end of the new drive.  I'm not sure you will have other options in beginner mode.  I'm sure there is a way to tell Clonezilla to keep one partition a fixed size but grow the other one.  (I'm not sure you can clone just the one partition, 14.04, in beginner mode automatically and then immediately boot, if that's what you were thinking about doing.  Clonezilla will want to clone all the partitions on your drive I think.  And you said you want to keep 12.04 too on partition #1, right?)

You could do this: tell Clonezilla to clone all partitions as-is and leave free space at the end.  When it's done, boot a Ubuntu CD, start Gparted, and delete your swap partition (#5), then grow the extended partition (#2).  Then grow your Ubuntu 14.04 partition (#6) to use all but about 8.6GB (you could probably make your swap even smaller than that if you have a lot of RAM).  Then finally create a new swap partition in the remaining free space (8.6GB or whatever you chose to leave free for it.)  These should all be fast operations.  

You'll still need to edit your /etc/fstab file and update the UUID of your swap partition, though, after that, because when you delete and recreate it in Gparted, the UUID of the swap partition will have changed.  I guess these extra steps intimidate some people, but they are easy for me because I've done them so many times.  I encourage you not to be afraid to try a few things like this because you will learn things and be able to do more of this kind of thing more easily in the future.

Or...dig into Clonezilla and figure the options to leave Partition #1 at its current 64GB but add the free space only to Partition #6.  There's got to be a way to do it.

This is where a graphic user interface like you'd have in True Image would be much easier.  You'd be able to resize just the one partition during the clone, with a mouse.  I'm sure you can do it with Clonezilla, too, but it's more work to figure it out.  If you mess up probably not a big deal - these are SSD drives and cloning should be fast, and you can just do it over again if you don't like the way it turned out the first time.

---

### Post by cybrsaylr on 2015-11-29
OK here's what happened using Clonezilla.

It cloned both 12.04 and 14.04, along with Swap and GRUB, exactly as was on the 128GB SSD, onto the new 480GB SSD. Was left with a balance of about 328GB free space, unallocated. 
Shut down. Disconnected the 128GB SSD and attempted to run the new 480GB SSD. 
Gparted showed this all nicely when running 12.04.

12.04 starts up normally with GRUB. Ran it a bit and 12.04 seems normal.
Then shutdown and attempted to run 14.04 which starts up but repeatedly goes to the 'login screen'. Put in correct password and keep getting 'incorrect password messages'! Can't get in as Guest either! 
The password works fine on 12.04 but will not work for 14.04! 

Repeated the install with Clonezilla but get the same results. It lets me run 12.04 but will not accept the correct password to run 14.04!

Don't know what to do?

---

### Post by weatherman2 on 2015-11-29
Boot up Ubuntu 12.04 again on the new drive, then mount your 14.04 partition there.  (So it will show up under /media/blahblahblah - where "blahblahblah" is either a disk label or a UUID string of the partition.)

Then run these commands and give the output of these terminal commands:

```

sudo blkid
sudo more /media/blahblahblah/etc/fstab

```

(replace "blahblahblah" with whatever the label/UUID is when you've mounted your 14.04 partition)

It could also be a case of the home partition permissions not set correctly though I'm not sure why that would happen here:

[http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade](http://askubuntu.com/questions/454576/cant-login-to-ubuntu-14-04-after-upgrade)

You could type Ctrl Alt F2 when you get to the 14.04 login prompt - this gives you a terminal login.  See if you can login there with your username/password and if so, do you get any messages?

---

### Post by cybrsaylr on 2015-11-29
> **weatherman2 said:**
> Boot up Ubuntu 12.04 again on the new drive, then mount your 14.04 partition there.  (So it will show up under /media/blahblahblah - where "blahblahblah" is either a disk label or a UUID string of the partition.)

Then run these commands and give the output of these terminal commands:

```

sudo blkid
sudo more /media/blahblahblah/etc/fstab

```

(replace "blahblahblah" with whatever the label/UUID is when you've mounted your 14.04 partition)

Success .... I hope!

As you suggested, booted up Ubuntu 12.04 again on the new drive, then mount your 14.04 partition there....did this. Then reboot and got GRUB 2, instead of the other earlier GRUB version and 14.04 became the default, first choice, again and boots up 14.04 fine!

Here's the output of 
```

sudo blkid
sudo more /media/blahblahblah/etc/fstab

```

/dev/sda1: UUID="7e0e85e0-18f5-46cf-b176-c9093ae2db7a" TYPE="ext4" 
/dev/sda5: UUID="845dfb70-4e94-43d2-bbe5-b743b1e47b7c" TYPE="swap" 
/dev/sda6: UUID="f0e58547-8d5c-4ec0-9cbf-d6e5cc278b38" TYPE="ext4" 
r@r-Studio-XPS-8000:~$ sudo blkid
/dev/sda1: UUID="7e0e85e0-18f5-46cf-b176-c9093ae2db7a" TYPE="ext4" 
/dev/sda5: UUID="845dfb70-4e94-43d2-bbe5-b743b1e47b7c" TYPE="swap" 
/dev/sda6: UUID="f0e58547-8d5c-4ec0-9cbf-d6e5cc278b38" TYPE="ext4" 
r@r-Studio-XPS-8000:~$ sudo more /media/blahblahblah/etc/fstabweatherman2weatherman2

Did a test on 12.04 which appears to be running fine also, at least right now!

Clonezilla is amazing it took <9 minutes to clone both OSs, Swap and the wrong GRUB, over to the new SSD when Clonezilla actually got working, running after setup.
But as you see it takes some additional tweaking after that, that I knew nothing about.

Thanks for all the help and guidance on this weatherman2!....;)


PS: Have about 328GB of free unallocated space. Plan to use it as ext4 storage. Seems Gparted wants Create as, a Primary Partition. Is this OK?

---

### Post by weatherman2 on 2015-11-29
Glad you got it working.

So how are you going to add the new space to the 14.04 partition?  Or are you just going to create a new, separate partition?

---

### Post by cybrsaylr on 2015-11-29
Not sure what to do with that space....
Was thinking of using it for storage as ext4

---

### Post by cybrsaylr on 2015-11-29
Another option I've see discussed here is using a separate partition like what I have now, for all your Home Files. Some claim this makes things easier by automatically saving files you want, when upgrading to a newer Ubuntu version. What is your opinion on this?

---

