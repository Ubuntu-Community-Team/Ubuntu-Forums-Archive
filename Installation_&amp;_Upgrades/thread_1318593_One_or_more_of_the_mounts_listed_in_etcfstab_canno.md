---
title: "One or more of the mounts listed in /etc/fstab cannot yet be mounted"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by plunder on 2009-11-07
Ever since I upgraded through Update Manager, the day after release, I'm getting the "One or more of the mounts listed in /etc/fstab cannot yet be mounted" thing. Everything boots normally, it seems as though everything is fine.. here is the ```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
i'm interested in correcting it, anyone have any ideas where the problem is?

ubuntu 9.04 64-bit -> ubuntu 9.10 64-bit
filesystem: ext3

---

### Post by josekym on 2009-11-07
Hello,

I have the same problem (using Ubuntu 9.10 32-bit), which appeared after I updated from 9.04 via Update Manager.

Even though I get the message on startup, my system still boots fine and seems to be ok during operation.  I guess it's just a cosmetic issue?

---

### Post by plunder on 2009-11-07
yeah there doesn't seem to be an error in my /etc/fstab and when I
```
sudo mount -a
```
I get no errors there, hopefully we can resolve this rogue error

---

### Post by fedexfrt357 on 2009-11-08
Same here guys, upgraded to 9.10 from 9.04 thru update manager...getting the same message at boot. As with yours, it does continue and seem to be fine... 

I am dual booting with XP, and the "27 GB Filesystem" (windows)  is not mounting at boot... It mounts manually from desktop without any problem, and I guess its really not a big deal... but it would be nice for it all to go error free... :)

---

### Post by fedexfrt357 on 2009-11-08
Well, maybe I'm on the wrong track here...

I followed the instructions here... [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)
and got the windows partition to mount automatically, but I still get the same message at boot... "head spinning"... lol

---

### Post by plunder on 2009-11-08
I'm not making any progress on this solution, I can't seem to find anything wrong :|

I like your sig tho, It's not broke but I wanna fix it! (not till its broke tho) :D

---

### Post by winotree on 2009-11-08
So did anyone other than me repartition their system *after* installing version 9.10?  I didn't need the swap file that was installed so deleted it and that error message showed just afterwards -- in fact it specifically mentioned that a swap file was on sda5 at installation.  I commented that line out in fstab *and that was the end of that.*  Not elegant but effective.

---

### Post by plunder on 2009-11-08
i didn't alter my partitions when I upgraded

---

### Post by omegamormegil on 2009-11-08
You are probably getting this message because fsck is checking one of your disks for errors and the boot process is waiting for the device to become available.  

If you just wait, it should complete after a few minutes and the system should boot.  If you power off the computer during this process, or if you are forced to power if off after the system locks up, you will get this prompt the next time you start the computer.

---

### Post by fedexfrt357 on 2009-11-09
> **winotree said:**
> So did anyone other than me repartition their system *after* installing version 9.10?

I didnt

---

### Post by aalmeida on 2009-11-09
I also get this message after upgrading to 9.10, but there are two further lines in the message:

Swap: waiting for uuid=00855371c-[....]
Press ESC to enter a recovery shell.

So it looks like the problem really is the swap partition.
Pressing ESC seems to open a shell, but then a few lines run automatically and the shell is closed even before I have time to check what is going on.

I also noticed that sometimes the system needs a lot of time to save files. So I thought my hard disk has some problem. The disk manager tells me that it has one bad sector. With gparted I checked the main partition for errors, but gparted cannot check the swap partition...

In the meanwhile I bought a new bigger hard disk, that I needed anyhow, and will try to install 9.10 from scratch...

---

### Post by plunder on 2009-11-09
> **omegamormegil said:**
> You are probably getting this message because fsck is checking one of your disks for errors and the boot process is waiting for the device to become available.  

If you just wait, it should complete after a few minutes and the system should boot.  If you power off the computer during this process, or if you are forced to power if off after the system locks up, you will get this prompt the next time you start the computer.

if this is the case maybe there is a line we can add
```
sleep 4
```
to not get the error?

---

### Post by manuti on 2009-11-10
**Fresh install** of **Karmic** and same problem.

Karmic amd64 with 2 hard disk on a HP550, one internal HD ( / + Vista + multimedia fat32 partition )and a express card SSD 16Gb ( /home )

---

### Post by prupert on 2009-11-10
I am also getting teh exact same error, including the message about pressing Esc to enter a recovery console.

While it aint a problem, for anyone new to Ubuntu, this might seem very scary.

I was on 9.04, upgraded to 9.10RC, looks like it is an upgrade issue.

Do people from launchpad view these posts and add bugs to their list, or should be do it. If so, what package should we file this under??

---

### Post by Stephen_at on 2009-11-11
I'm getting it too, it seems to be harmless and nothing seems to be wrong but it shouldn't be happening.

---

### Post by Velophile on 2009-11-11
I've been getting the same thing since upgrading, have a look at this bug:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720)

Seems to cover my symptoms.

---

### Post by Stephen_at on 2009-11-11
It would look like it. I've never managed to really see what it says as I only get on screen for second or so.

---

### Post by Velophile on 2009-11-12
From the looks of the bug report a fix is in the pipeline, for me it's a cosmetic thing, the machine still boots ok and works fine so I'm happy enough to leave it.

---

### Post by Schobs on 2009-11-12
I'm sorry when this post is slightly off topic, but it does have to do with a mount root fs problem! (If there is a similar post already about this problem/ bug, could you please redirect me..)

I had no issues with installing 9.10 via the windows installer (windows 7), but yesterday a whole bunch of updates were released. After installing them and shutting down, I got the following screen while rebooting:

"2.431139 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,3)"

No reaction to any keys...

The recovery mode doesn't work either..

Any help would be much appreciated!

---

### Post by Velophile on 2009-11-12
Hi, I'd start a new thread for that Schobs, it'll probably get missed stuck on the end of this thread.  Sorry I can't help much with the actual error, not one I've come across before

EDIT:

have a look at this thread, might help you:

[http://ubuntuforums.org/showthread.php?t=1299296&highlight=VFS%3A+Unable+mount+root+fs+unknown-block](http://ubuntuforums.org/showthread.php?t=1299296&highlight=VFS%3A+Unable+mount+root+fs+unknown-block)

---

### Post by Schobs on 2009-11-12
Ok, thanks anyway!

---

### Post by Gav Mack on 2009-11-12
> **Velophile said:**
> I've been getting the same thing since upgrading, have a look at this bug:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720)

Seems to cover my symptoms.

There's another bug which causes exactly the same symptoms with the fstab error on startup mounting SSD drives - which I've had for over a month!  If you remove quiet and usplash from the grub boot settings you may see similar logs in dmesg:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852)

If you have the same issue which seems to be a DMA fault please add your contribution to the bug thread - hopefully it will get rectified quicker!

---

### Post by virender singh Thakur on 2009-11-12
:p:p                                  1. Select recovery mode from the boot menu.
2. Select login as root from the menu in recovery mode.
3. Type this at the prompt

# sudo apt-get remove xorg-driver-fglrx
# sudo dpkg-reconfigure -phigh xserver-xorg

4. Exit

# exit

5. Now select Resume normal boot from the menu.

Method can be found here [http://blog.dipinkrishna.info/2009/0...rocess-in.html]("http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html")

---

### Post by Stephen_at on 2009-11-12
That blog post relates to blank screens and problems with the xorg configuration which is unrelated to what we're seeing here.

Even if we're only seeing that message because one of the boot screens is crashing we shouldn't be seeing that message because we shouldn't be having problems mounting disks at each boot up

---

### Post by dhaus111 on 2009-11-12
hey guys, I'm having the same problem.  Keep wanting to reformat and do a clean install but haven't yet.  Is anyone having this problem after a clean install? (I used alternate install disk to upgrade).  I was curious also if you guys had switched any of your partitions from ext3 to ext4 while using jaunty or intrepid?  wondering if that has anything to do with it... Can anybody tell or guess as to how long it takes to have the patch submitted to launchpad to when it gets into my update manager?

cheers
d

---

### Post by peterzay on 2009-11-15
I did a new install (not upgrade) of 9.10 on a Lenovo ThinkPad SL-500 by destroying the OEM Vista and overwriting the entire hard drive.  The only fstab entries are /dev/sda1 for ext4, /dev/sda5 for swap, and /dev/scd0 for cdrom0.

I can play CDs, and I can access my hard drive.  I don't know if swap is ok.

Some boots, I get the message.  Some, I don't.

Perhaps the waiting time is too long on some boots.

---

### Post by peterzay on 2009-11-17
This just in from Canonical:

>From what you say, it sounds like you're not having an error at all!

This is just a message that may appear if the boot is taking longer than
normal to inform you which filesystem(s) aren't responding and give you
the option to drop to a recovery shell.  If the boot completes normally,
then it's just a slow one.

** Changed in: mountall (Ubuntu)
       Status: Incomplete => Won't Fix

---

### Post by omegamormegil on 2009-11-17
Yeah, the message isn't indicative of an error, it is just saying that the boot process is waiting for one of your mounts to become available.  This can be the result of fsck running.  

While getting this error isn't a bug (it's intentional to let you know why the boot is taking longer than it should), I think the message should be worded better.  It isn't clear that the issue the message is describing is normal, or that it will resolve itself if you give it some time.  It seems to imply that there is a problem and that you should press the key to drop to the recovery shell, which isn't very user friendly.  Perhaps a bug should be submitted about the wording of the message.

---

### Post by The_BB on 2009-11-17
In that case I agree. The wording seems to have thrown a lot of people off, including me.

On a related note then, why could it be that Karmic loads "too" slow for some?

---

### Post by JoakimP on 2009-11-19
I edited the /etc/fstab file and renamed all the references to UUID=XXXXXX to whatever they are actually called in /dev:
/dev/sda1
/dev/sda5
etc
and that fixed the warning. I don't get the warning any more but the boot time is equal.

Be sure to make a copy of your /etc/fstab before you do any changes though.

---

### Post by indistinguishible on 2009-11-20
My Ubuntu can't boot up after updating to 9.10. I've read all the thread but it helped me nothing. First of all, my fs was readonly and I can't even change /etc/fstab. This was solved simply, but I can't boot anyway. fsck was running successful.
Then I've found this blog: [http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html](http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html)
I've done all recomendations from there and it started to work. So I think this link will be very useful.

---

### Post by yusufk on 2009-12-23
Going to try the above.

Many people calling this harmless, but this increases my bootup time significantly. Quick boot-up is supposed to be one of the benefits of this version, so I think its quite serious.

Edit:
Ok, it worked. Next up, fix the sound!

---

### Post by Endolith on 2010-01-07
> **omegamormegil said:**
> You are probably getting this message because fsck is checking one of your disks for errors and the boot process is waiting for the device to become available.

That's a bug then.  It should show a "checking disk" message instead.  Is this why my computer doesn't get past the boot screen?  It's scanning the disks, which takes hours?

---

