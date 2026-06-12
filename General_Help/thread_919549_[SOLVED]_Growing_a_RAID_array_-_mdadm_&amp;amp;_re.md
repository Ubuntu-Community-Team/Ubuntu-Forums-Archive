---
title: "[SOLVED] Growing a RAID array - mdadm &amp;amp; resize2fs"
date: 2008-09-14
forum: General Help
---

### Post by Kissell on 2008-09-14
Okay, so our software RAID-6 ran out of space, and I decided to add another disk and grow the array...  I've never done this before, and thought it was awesome that it looked so easy, because in windows isn't even possible through the native OS.

So I added the disk (mdadm --add /dev/md0 /dev/sdm)

No problem, mdadm now showed an extra spare...  then I grew it (mdadm --grow /dev/md0 --raid-devices=12)...  this was a little odd, because it didn't think about it, it just did it, no processing time...  no blinking lights on the disk activity LEDs.

So since it appeared to not be doing anything I did the next command, the resize2fs command (resize2fs /dev/md0) and again, it looked like nothing happened (no activity on the disks, no led blinking).  

But, then I noticed the file system had no files...  well that sucks...  and since there appeared to be no activity, i unmounted it and then stopped the md0 manually using mdadm...  and since it was down I just decided to reboot for good measure and let it bring itself back up.

During the reboot the md0 array wouldn't mount, and after continuing to boot I now see that mdadm is running as a process taking up 66% of the RAM and all the disk LEDs are flashing...  I assume it's doing the file system resize...  but it's been running for over 12 hours now (rebuilding/resyncing the array after a disk failure takes less time than this)...  is there anyway I can see what's going on?

(mdadm --detail /dev/md0) won't work, and neither will (cat /proc/mdstat), because the md0 is not active/started...  I cannot assemble it because it says it's busy (as I can verify because all the disk LEDs are flashing)...  all I can do is run "top" and see that mdadm is taking up a lot of memory and is the most active process. 

At this point I would really love to be able to see some sort of progress indicator, something to tell me everything is going to be okay...  

Currently I can't use the volume as the md0 is not active, and I can't assemble it because it's busy, but I can't see what it's doing or how much longer it's going to take...  and I'm starting to get really worried about the data.  Obviously I don't want to reboot in the middle of whatever it's doing, but I have no idea what to do other than wait it out, and after 12 hours I'm starting to get very anxious about the data.

---

### Post by fjgaude on 2008-09-14
I don't know the size of the drives you are using in the raid6 array, but large drives take lots of time...

If you used that resize2fs command on the mounted array I can't say what might have happened if you are not using ext3 as a filesystem.

I would read, study the man pages for resize2fs to see if all was carried out as required.

Let us know what you find, what you think.

---

### Post by Kissell on 2008-09-14
There were eleven 750GB drives in the healthy RAID-6 before I expanded it to twelve.

actually, since in "top" it's showing mdadm as the busy process...  and now resize2fs...  I'm thinking that it's actually still growing the array from the "mdadm --grow /dev/md0 /dev/sdm" command.  because I hear that should take a long time and it never did that before the reboot.

It's STILL going, but unfortunately I can't see any progress since the /proc/mdstat and mdadm --detail commands both need an active md0 to see progress indicators...  it appears to be growing it (i assume) even though md0 is stopped...  

i guess i really have no choice but to continue to sit and wait, i guess...  if anyone has any other suggestions or a way for me to see the progress of whatever mdadm is doing that would be awesome.  I know it's doing something because it's running non-stop as a busy process, and all the disk LEDs are flashing...  but since md0 is inactive I can't do any of my normal commands to check it's progress...  it's been almost 24 hours now, and it's still not done doing whatever it's doing...  I'm really worried that it's not really doing anything and that i'm just wasting time waiting for it, and it's never really going to finish because it's not really doing anything productive.

---

### Post by Kissell on 2008-09-14
Problem Solved!

Okay, so I did "ps -ef|grep mdadm" and found out that the entire 24 hours mdadm has been running, it was running this command "mdadm --assemble --scan"...  so basically all the drives were non-stop busy because it was trying to assemble the array the entire time, over and over again, but everytime it was getting an error "mdadm: Failed to restore critical section for reshape, sorry." but the error wasn't showing up on the console or in dmesg.  If I manually try to assemble the array it gets that error.  So I killed all those processes of mdadm that were actually not doing anything except continuing to fail to attempt to assemble the array.

But now what?  I have done everything I know how to do...  right?  so I found a guy with a similar problem on another forum site, and he said he fixed the problem by upgrading mdadm.  The latest mdadm in the Ubuntu repository is v2.6.3 and this is the version I was running.  But I downloaded the new unstable debian package for v2.6.7 from "http://packages.debian.org/sid/i386/mdadm/download" and installed it.  Instantly after the install it correctly assembled the md0 device and started reshaping it to add the extra disk I told it to grow too.

Phew!  Holy crap this was a scary weekend.  Now the array is up and I can see progress with my normal commands like cat /proc/mdstat.  I don't have a backup of this data (not my fault, entirely a budget/risk decision that I disagree with, "RAID-6 is should be plenty safe, we can't afford a backup solution this large").

My only concern now, is that it estimates it's going to take 2 days to reshape the array...  currently I have it unmounted...  but I really don't want it to be down for two days...  if I mount it the files are there...  but I don't want to risk losing the data...  do I really have to keep it offline for a few days, or is it okay to mount it and use it while it's reshaping?   I normally leave it mounted while resyncing the array after replacing a failed disk and never have any problems, so I think it will be okay if I mount it while reshaping...  but I've never grown a software raid before and I'm just not sure, not comfortable with it yet.  

PS: Why is it that lack of money always comes back to hurt the admin who got rejected for the very purchases which would prevent this?  I mean, all this stress would have been much less if I knew we had a reliable backup of the data.  Still, I have been doing this for many many years, but am still relatively new to the linux environment, so this was all a priceless experience that I really enjoyed (now that it appears the data is going to be okay).

---

### Post by fjgaude on 2008-09-15
Well, I don't have the experience for what happens when you mount an array that is reshaping...

I tell you... I never, never will be involved with important data without at least two backups, usually require three... online, near-line, and off-line. It's the only safe way... raid doesn't really protect if things go wrong, wrong. It just protects with drive failures.

Glad things are coming along for you... let us know what happens if you decide to mount!

---

### Post by Kissell on 2008-09-15
After reading more and reviewing what happened, I believe the resize2fs command never did anything yet...  when I originally ran the --grow command it didn't do anything, no drive activity, and this process of growing/reshaping takes days on a volume this large.  I believe it didn't grow it because the mdadm version didn't work in my environment with the grow command...  as such, when I subsequently did the resize2fs it didn't do anything, because it hadn't grown it yet.  

Then, when I rebooted, mdadm tried to assemble the array but couldn't, and so it always looked like it was doing something (drive activity) because it was continually trying to assemble the array.  Once I upgraded to the beta version of mdadm then it instantly assembled the array and began the reshaping process...  so as such, I don't think the resize2fs command I ran ever had anything to do and will need to be run again once the reshaping is done.  

In the meantime, I decided it would be safe to go ahead and mount and use the volume, since it allows me to do it and it seems others have done this, and because I've done this while resyncing without problem.  So far it appears to be fine with doing this.  I have some files with sfv checksums on the volume and they are still valid, so it appears to be okay to use it while reshaping.  I will unmount it while doing the resize2fs because I don't think it's okay to have it mounted while resizing the file system, but it appears to be fine while reshaping.  

PS: I was just going to mount it just to pull some critical data off, and then unmount it again, but I can't unmount it now.  It allowed me to mount it while it was reshaping, but when I try to unmount it says the device is busy so it can't.  So at this point I have no choice but to leave it mounted during the reshaping anyway, but again, that appears to be an okay thing.

Also, note that the reshaping is going considerably slower than resyncing takes...  resyncing happens on my system at around 20,000KB/sec, and reshaping is getting under 5000KB/sec...  just FYI, for others, since I had never done this before and never heard anyone else mention it being so much slower to grow than to repair.  

Obviously the issue of the backup needs to be revisited...  when we built this system money was tight and 750GB drives cost over $350 each and the risk was acceptable for the low importance of the data...  now drives are like $75 each...  and the importance of the data being stored on here has gone up significantly as availability created demand ("oh, we can just store our new data there, you have plenty of space there")...  So now I don't think money is a valid excuse to be at such a high risk anymore, but when it comes to common sense I'm often told I'm wrong and that if I was just a better magician I wouldn't be making such ridiculous requests.  Funny how the techs and not the budget people are the ones to get blamed when it hits the fan.  If the data would have been lost the issue wouldn't have been the mdadm version having a problem with our architecture, or the denied request for a backup, it would have been that that my skill was inadequate.  Even though it appears I did everything correctly, and mdadm v2.6.3 just couldn't grow it correctly.

---

### Post by fjgaude on 2008-09-15
To unmount an array you have to first stop it.

```
sudo mdadm -S /dev/md<nn>
```

I'll write more when time permits...

Thanks for being so complete in your description of what is happening.

---

### Post by Kissell on 2008-09-16
I didn't want to unmount the array, as it was busy growing it, i just wanted to unmount the file system, and umount wouldn't work because it was busy... but now it's finally done growing/reshaping and umount worked just file.  

Now it looks great, mdadm --detail reveals it has grown to new size, but file system still not showing free space...  so need to use resize2fs.

It forced me to run an e2fsck on the volume first, and I'm running the resize now...  everything looks good and is going according to the original plan, just turned out to be a problem with mdadm v2.6.3.  Still not sure exactly why that latest version didn't work for me.  It worked to build the array and resync it and do everything else i've ever done...  just didn't work to grow it.  but the unstable beta v2.6.7 seemed to work just fine for me.

---

### Post by fjgaude on 2008-09-17
Happy things are working as they should... I've never heard of unmounting a filesystem... the drive/array and the filesystem are together, not separate, unmount one and the other is unmounted.

Let us know if all ends up as you have hoped.

The issue with mdadm 2.6.3 likely is caused by the large drives... things have been moving along in that regard... soon we will see terabyte drives as the smallest we can buy. <smile>

See you down the lines...

---

