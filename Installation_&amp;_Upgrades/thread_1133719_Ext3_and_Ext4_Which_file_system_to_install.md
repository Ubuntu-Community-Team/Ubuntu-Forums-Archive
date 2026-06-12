---
title: "Ext3 and Ext4: Which file system to install?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Sef on 2009-04-23
Update: Ext4 is the default file system on Karmic Koala and beyond.   

Disclaimer:- This thread only issues the use of Ext4 on Ubuntu Jaunty(9.04) and does not apply to earlier releases where Ext4 may not have been available as an option due to Ext4 not having been stable.

As you may have noticed, you now have the option of installing Ext4 through Ubuntu Jaunty. Ext4 is quite a big update from Ext3 but it still is only incremental and is backwards-compatible with Ext3, so it is very stable, however a few issues about the filesystem have recently sprung up that may require you to be a little careful when using this filesystem.

**_Reasons to stick to Ext3:-_**

1) Ext3 is the default file system for *buntus.

2) It is very stable, so no worries about losing your data due to crashes.

3) The one that is recommended to be on your work stations.


**_The issues with Ext4:-_**

1) There have been reports of crashes having corrupted configuration files and sometimes more with Ext4 in use.

2) This has been addressed in kernel 2.6.30, however it will not hit Ubuntu Jaunty, but Ubuntu Karmic.

3) [9.04 Release Notes: Other Known Issues]("http://www.ubuntu.com/getubuntu/releasenotes/904") for more detail.

Therefore, while Ext4 is really good, it still does need a few bugs to be ironed out, but all in all, it is quite stable for the average desktop user, just as long as you take regular backups, as you would when using any file system.

And just one more thing, Ext4 is not to be blamed completely, part of the problem stems from programs which fail to adhere to the standard regarding I/O on disk.

More information regarding this matter can be obtained here:
Theodore Tso's(One of Ext4's main developers) blog post regarding this issue:-
[http://thunk.org/tytso/blog/2009/03/...-file-problem/]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/")

Article (29 May 2009):[ The Ext4 File Linux File System]("http://www.h-online.com/open/The-Ext4-Linux-file-system--/features/113403/0") by Dr. Oliver Diedrich

(Thank you to PmDematagoda and bhodi.zazan for helping me improve this thread.)

---

### Post by akrep55tr on 2009-04-23
Thank you very much. This was a big question in my mind.

---

### Post by Demonizer on 2009-04-23
Ext4 cant be THAT bad :( .

---

### Post by porchrat on 2009-04-23
OK that is not great news, I thought the bugs had been ironed out, looks like I'm going to have to use ext3 in my new jaunty jackalope download :(

I had no idea there were so many issues, thanks for info Sef.

---

### Post by vigyani on 2009-04-23
> **Sef said:**
> 
**B) Ext4 is beta:**

1) Ext4 is the new still experimental (nonstable) file system for the *buntus.  

2) It has been known to crash and data has been lost.

3) It is not for workstations that need a stable file system.

4) The current GRUB will not boot into it.  A boot partition must be created.

5) Bugs are stil being worked out of it.  

6) You have the time and enjoy reinstalling your os or oses, if it hoses your system.  (To hose a system is to make the computer unbootable, so a reinstall is necessary.)

7) You frequently back up your system, so in case your data becomes unreadable due to a crash, you can replace it.

Yes, ext4 is faster than ext3, but do you really want to risk losing your data or having to reinstall *buntu and the other oses that are on your system or both?

Hi

It would be really nice if you can provide references and links to substantiate the claims made in this post.

---

### Post by porchrat on 2009-04-23
> **vigyani said:**
> Hi

It would be really nice if you can provide references and links to substantiate the claims made in this post.

That is a good idea. I would like to read these articles as I have only been able to find benchmarks and positive press releases about ext4. It would be nice to read the other side of it.

From what I had read ext4 is marked "stable". I thought it was going to be the default filesystem of Ubuntu, but it seems like ext3 remains the default until at least 9.10.

I see what you mean about the lack of GRUB support, but that is OK as I always use a separate /boot partition anyway.

I am completely seduced by the speed of ext4 in the benchmarks, but if it going to be unpredictable I won't touch it.

---

### Post by vividia on 2009-04-23
I would like to read the source(s) about ext4.  I'm still using ext3 and was considering making the leap.

---

### Post by wanchai on 2009-04-23
Here is something to read:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781)
By the way, Theodore Ts'o is the author of ext4, he wrote some long posts in this thread that are worth reading.

For my system I decided to stay with ext3. I don't need to squeeze the last bit of performance out of my machines and I don't need to use the newest of the newest. Especially not if it's something as critical as a file system that cannot be easily downgraded.

---

### Post by OmegaBLK on 2009-04-23
I was just reading the [release notes for 9.04](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems) and there still are some issues with ext4 support that are not resolved as of the 9.04.  Now an update will come when they are avaialable but, for now:

> 
**Lock-ups when deleting files from ext4 filesystems**

In some cases, deleting files from an ext4 filesystem is reported to cause soft lock-ups in the kernel (330824). Investigation of this problem is ongoing, and it is expected that a fix for this problem will be made available as a post-release update. To avoid this problem, users may wish to install using the default ext3 filesystem and convert their filesystem to ext4 (as documented on the ext4 wiki) once a fix is available.

**Switching to ext4 requires manually updating grub**

If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 9.04 to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot.

**Possible data-loss problems resizing ext4**

The resize2fs tool may cause data loss when growing or shrinking ext4 filesystems off-line. See this mail from the upstream maintainer for more details. Unfortunately we became aware of this too late to fix it in Ubuntu 9.04. If you wish to resize an ext4 filesystem using the tools in Ubuntu 9.04, you may be able to work around these problems by first disabling the flex_bg and uninit_bg features (do not attempt this on a mounted filesystem!):

tune2fs -O ^flex_bg,^uninit_bg /dev/DEVICE_NAME
e2fsck /dev/DEVICE_NAME

However, we still strongly recommend taking significantly more care with backups than usual before attempting to resize an ext4 filesystem.

[source](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems)

---

### Post by aniruddha on 2009-04-23
Awesome stuff, thank you for all the clarifications. And here I was really looking forward to ext4 too. So it goes...

---

### Post by gjoellee on 2009-04-24
I have been using Ext4 for several months, never had any problems at all...

---

### Post by Lisimelis on 2009-04-24
I think it is pretty normal to have some stability issues in the  first year of ext4. After all its been a long time since a new filesystem. It is not like a linux distro were we want the problems to go away from the first updates. I think in 9.10 the ext4 will be even better and pretty soon will be the default file system.

---

### Post by ssam on 2009-04-24
ext3 has been holding petabytes (maybe more) of data for many years on millions of systems. all the serious bugs have been ironed out.

ext4 has tested by kernel hackers, and developers for about a year. over the past few months the number of people testing it has increased a lot (lots of ubuntu and fedora testers). the big issue of data loss on unclean shutdowns was found (the lead ext4 developer thinks that linux crashes are very rare, but this is less true if you have binary graphics drivers, or unstable hardware, or powercuts (and you dont have a UPS)).

there are now patches in the ubuntu 9.04 kernel (and mainline 2.6.30, and other distros) that fix that particular bug.

it is not impossible for there to be a few more nasty bugs in ext4. they will be found as more people use ext4 in unusual situations.

so if you use ext4, you will probably be fine. but make sure you have a good backup regime.

---

### Post by Gina on 2009-04-24
I installed Jaunty into ext4 partitions during the testing phase but would now like to clean up my hard drive and remove numerous partitions used for testing.  However, I have two ext4 partitions at sda17 and sda18 which GParted won't delete and cannot find a mount point for - it thinks these partitions are mounted when they aren't and refuses to delete these partitions and any lower numbered ones.  I can reformat lower ones and reuse them but I seem to be stuck with 18 partitions.  The two old ext4 partitions add up to about 15GB out of a 500GB drive so the loss of space is not very significant.  Just annoying.

I don't want to wipe the entire drive as I have a lot of data on it that would take a long time to restore.

Does anyone have any suggestions how I can get rid of the rogue partitions, please?

---

### Post by graysky on 2009-04-24
> **gjoellee said:**
> I have been using Ext4 for several months, never had any problems at all...

+1

> **Lisimelis said:**
> I think it is pretty normal to have some stability issues in the  first year of ext4. After all its been a long time since a new filesystem. It is not like a linux distro were we want the problems to go away from the first updates. I think in 9.10 the ext4 will be even better and pretty soon will be the default file system.

Actually, ext4 has been around for longer than 1 year.  I can't locate the source on this but believe me, it is *well* tested.

---

### Post by graysky on 2009-04-24
> **Gina said:**
> I installed Jaunty into ext4 partitions during the testing phase but would now like to clean up my hard drive and remove numerous partitions used for testing.  However, I have two ext4 partitions at sda17 and sda18 which GParted won't delete and cannot find a mount point for - it thinks these partitions are mounted when they aren't and refuses to delete these partitions and any lower numbered ones.  I can reformat lower ones and reuse them but I seem to be stuck with 18 partitions.  The two old ext4 partitions add up to about 15GB out of a 500GB drive so the loss of space is not very significant.  Just annoying.

I don't want to wipe the entire drive as I have a lot of data on it that would take a long time to restore.

Does anyone have any suggestions how I can get rid of the rogue partitions, please?

If the partitions are mounted you won't be able to modify them via gparted.  Have you tried booting from the [live gparted CD](http://gparted.sourceforge.net/download.php) and attempting your maintenance?  I offer that because none of your partitions should be mounted by default under the live CD's environment.  Plus, you're using the latest version of gparted by doing so which is always a good thing :)
I haven't seen an example where gparted failed to

---

### Post by OmegaBLK on 2009-04-24
Currently using ext4 for most of my partitions with Jaunty.  Got backups.  Hopefully I do not run into bug [#330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824?comments=all).  

*Fingers crossed*

---

### Post by AbsentHarvest on 2009-04-25
This is good information, I was just looking for how to upgrade ext3 to ext4... I think I will wait until further improvements are made. :]

Thanks.

---

### Post by trot2millah on 2009-04-25
I'm planning a new partition with Jaunty and I want to try out using Ext4, would my other partitions (XP, Linux Mint) be at risk of data loss at all?  I doubt it, but just don't want to risk anything.

---

### Post by Gina on 2009-04-25
> **graysky said:**
> If the partitions are mounted you won't be able to modify them via gparted.  Have you tried booting from the [live gparted CD](http://gparted.sourceforge.net/download.php) and attempting your maintenance?  I offer that because none of your partitions should be mounted by default under the live CD's environment.  Plus, you're using the latest version of gparted by doing so which is always a good thing :)
I haven't seen an example where gparted failed toThank you for your reply :)

I have now downloaded the latest stable GParted and burned it to CD-R. Using that I have successfully deleted the ext4 partitions and others I didn't want.  I see the Live CD GParted supports ext4 filesystems.

Thank you for the suggestion - got me out of a hole :)  

Don't know why I didn't think of it myself :lolflag:

---

### Post by halovivek on 2009-04-25
i am using ext4 in my system. It looks good and fast for huge data. i am using around 1TB harddisk and 320GB hdd internal. most all disks is filled with data. And it is accessing very fast.

Thanks for the update about EXT4 i will take back up and i will use it again.

---

### Post by graysky on 2009-04-25
> **trot2millah said:**
> I'm planning a new partition with Jaunty and I want to try out using Ext4, would my other partitions (XP, Linux Mint) be at risk of data loss at all?  I doubt it, but just don't want to risk anything.

No.  Only data on ext4 partitions can be affected by the bugs mentioned.

> **Gina said:**
> Thank you for your reply :)

I have now downloaded the latest stable GParted and burned it to CD-R. Using that I have successfully deleted the ext4 partitions and others I didn't want.  I see the Live CD GParted supports ext4 filesystems.

Thank you for the suggestion - got me out of a hole :)  

Don't know why I didn't think of it myself :lolflag:

Glad you got your problem solved.

---

### Post by Sef on 2009-04-25
>                      Originally Posted by **Gina**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7141479#post7141479")                 
                 [I]Thank you for your reply :smile:

I have now downloaded the latest stable GParted and burned it to CD-R. Using that I have successfully deleted the ext4 partitions and others I didn't want. I see the Live CD GParted supports ext4 filesystems.

Thank you for the suggestion - got me out of a hole :smile:  

Don't know why I didn't think of it myself :lolflag:[/I]
GParted in Ubuntu is often not the current version, which at times can make a big difference.

As to why you didn't think of that, it is often the simpliest things that we overlook.

---

### Post by zero7404 on 2009-04-25
so, after trying to install 9.04 x64 using the ext4 file system, i've noticed instability with regard to the package manager, in particular, Synaptic....either the new wireless network files have a problem, or something else, because updates and browsing in general crawl to snail's pace...haven't seen that issue when in vista.

so far, i've run into fsck 3 times, on my way out of the OS....
numerous fixes/issues that i had to confirm prior to shutdown/restart.

would ext4 be the reason i am experiencing this ?

i've also seen something i haven't seen for a while, the solid color screen after logout, but only a few colors display...not as many as i've seen a few times in the past with 8.10...

i'd like to reinstall 9.04 one more time, but i think i'm better off with ext3 for the time being....could anyone chime in and explain what causes fsck to run ? i suspect file system errors, but not entirely sure....

---

### Post by autocrosser on 2009-04-26
I have been using ext4 from the first & have had a couple of minor problems--I talked with Theo quite a bit about it late Dec/Early Jan & made a couple of changes to my system as a result.

1. I do REGULAR backups of my important data.
2. Make sure you use a UPS on your desktop system--when doing important file work on a laptop--be plugged in.
3. Read My information in this post: [http://ubuntuforums.org/showthread.php?t=1090488&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1090488&highlight=ext4)  I posted information from Theo's blog about fstab options & how they impact your system.

All-in-all, ext4 works very well for me--my system is totally ext4--2 installs waiting for Karmic, 1 Jaunty final, 1 Jaunty64 that will be Karmic testing & 1 Fedora11.

Ext4 will be the future--I have bid ext3 a fond farewell--it served me well for many years. :)

---

### Post by jcostom on 2009-04-26
> **porchrat said:**
> OK that is not great news, I thought the bugs had been ironed out, looks like I'm going to have to use ext3 in my new jaunty jackalope download :(

I had no idea there were so many issues, thanks for info Sef.

You could always use JFS..  Fast & stable...

---

### Post by psychok9 on 2009-04-26
I'm using Jaunty from the Alpha 5 version on Ext4 fs.
Some weeks ago, I've lost some files after a blackout (amule configuration and corruption of some files temp/part).
I've finding new .30 kernel... and I found here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).
After a correct installation, I get a error: modprobe: FATAL: Could not load /lib/modules/2.6.etc/custom/modules.dep, no such file or directory...

Solution or other kernel/solution? I need a fixed kernel for Ext4 problems (I can't afford UPS).

Thank you!

p.s. nodelalloc can fix the problem, but the framentation of files can get worse a lot.

---

### Post by Monsuco on 2009-04-26
I installed Ubuntu with ext4, but I would like to convert it to the old ext3 system. How do I do that?

---

### Post by Sef on 2009-04-27
> I installed Ubuntu with ext4, but I would like to convert it to the old ext3 system. How do I do that?


You would have to reformat the partition. 

From [Kernelnewbies]("http://kernelnewbies.org/Ext4"):

> Ext4 will use the new data structures only on new data, the old structures will remain untouched and it will be possible to read/modify them when needed. This means, that, of course, that once you convert your filesystem to Ext4 you won't be able to go back to Ext3 again

---

### Post by antiram on 2009-04-27
formatted yesterday with mke2fs -t ext4 -E stripe-width=128,resize=128G on a lvm. today:
```

Apr 27 12:08:43 locutus kernel: [   11.265086] Pid: 4244, comm: hal-storage-cle Not tainted 2.6.28-11-generic #42-Ubuntu
Apr 27 12:08:43 locutus kernel: [   11.265087] Call Trace:
Apr 27 12:08:43 locutus kernel: [   11.265095]  [<ffffffff8036a156>] ext4_da_writepages+0x466/0x490
Apr 27 12:08:43 locutus kernel: [   11.265099]  [<ffffffff8037dbff>] ? __ext4_journal_dirty_metadata+0x2f/0x70
Apr 27 12:08:43 locutus kernel: [   11.265102]  [<ffffffff8036b0f0>] ? ext4_da_get_block_write+0x0/0x180
Apr 27 12:08:43 locutus kernel: [   11.265107]  [<ffffffff802b8ef8>] do_writepages+0x28/0x50
Apr 27 12:08:43 locutus kernel: [   11.265109]  [<ffffffff802b0e31>] __filemap_fdatawrite_range+0x51/0x60
Apr 27 12:08:43 locutus kernel: [   11.265112]  [<ffffffff802b0e57>] filemap_flush+0x17/0x20
Apr 27 12:08:43 locutus kernel: [   11.265115]  [<ffffffff8036695d>] ext4_alloc_da_blocks+0x2d/0x30
Apr 27 12:08:43 locutus kernel: [   11.265117]  [<ffffffff80371335>] ext4_rename+0x195/0x750
Apr 27 12:08:43 locutus kernel: [   11.265121]  [<ffffffff802f0bfb>] vfs_rename_other+0xbb/0xf0
Apr 27 12:08:43 locutus kernel: [   11.265124]  [<ffffffff802f1d87>] vfs_rename+0x147/0x270
Apr 27 12:08:43 locutus kernel: [   11.265127]  [<ffffffff8069e569>] ? _spin_lock+0x9/0x10
Apr 27 12:08:43 locutus kernel: [   11.265130]  [<ffffffff802f3f2e>] sys_renameat+0x20e/0x250
Apr 27 12:08:43 locutus kernel: [   11.265133]  [<ffffffff802d290e>] ? free_pages_and_swap_cache+0x7e/0xa0
Apr 27 12:08:43 locutus kernel: [   11.265137]  [<ffffffff8041c558>] ? __up_write+0x68/0x140
Apr 27 12:08:43 locutus kernel: [   11.265140]  [<ffffffff802f3f86>] sys_rename+0x16/0x20
Apr 27 12:08:43 locutus kernel: [   11.265143]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
```

---

### Post by bacardiandwatermelon on 2009-04-27
> **jcostom said:**
> You could always use JFS..  Fast & stable...

I've been using JFS since Intrepid, had no issues. Doesn't do any start up scans every 30 boots either. Only had one instance when I wished that the JFS file system could be read from within XP..

---

### Post by FastMady123 on 2009-04-28
For me, ext4 works good on my system and I'm really happy with it. It boots faster and I did not get any errors yet.

---

### Post by crazyfrog1234 on 2009-04-29
> **FastMady123 said:**
> For me, ext4 works good on my system and I'm really happy with it. It boots faster and I did not get any errors yet.

Me too, ext4 is better than ext3 and I'm very glad to use it.

---

### Post by Monsieur Gonzalez on 2009-04-29
> **bacardiandwatermelon said:**
> I've been using JFS since Intrepid, had no issues. Doesn't do any start up scans every 30 boots either. Only had one instance when I wished that the JFS file system could be read from within XP..

While I find JFS to be a good filesystem, I quit using it when I saw it had little support from developers (If I remember correctly, only one developer from IBM), so you are less likely to get improvements, bug fixes, etc. 

So I'm using ext4, and saw great improvements both in speed (deleting, mainly) and boot check time; someone wiser might keep their data in ext3 for some time and wait for bugs to be ironed, though.

---

### Post by porchrat on 2009-04-29
> **FastMady123 said:**
> For me, ext4 works good on my system and I'm really happy with it. It boots faster and I did not get any errors yet.

I went with ext3 and I'm happy that I did. It is more than fast enough. There were enough niggly bugs in Jaunty that I really didn't need a potentially unstable filesystem.

---

### Post by kelt65 on 2009-04-29
I've been using xfs for years, no problems ...

---

### Post by nuir on 2009-04-30
ext4 and all is OK
everything seems to run quicker and smooth

---

### Post by Neotelos on 2009-04-30
Basically, if you use Ext4 it's a good idea to update the kernel...
It wont be as stable in the default kernel for Jaunty.

I've already went Ext4 as I needed to compile a new kernel to fix some issues on my hardware...works great!

It does seem to be a tad snappier! :)

---

### Post by espmartin on 2009-05-01
How do you check to see what version of file system you're using?

---

### Post by Partyboi2 on 2009-05-01
> **espmartin said:**
> How do you check to see what version of file system you're using?
Hi, have a look at System>Admin>System Monitor>File Systems

---

### Post by Sef on 2009-05-01
> Basically, if you use Ext4 it's a good idea to update the kernel...
It wont be as stable in the default kernel for Jaunty.


Not necessarily true.   I have the default kernel with ext4 in jaunty and have no problem with stabiltiy.

---

### Post by boyofford on 2009-05-01
I've just spent a week setting up a simple media centre, using juanty and xbmc,it is running with / and /home on Ext4 and another partition for my files on EXT3.
Was a little concerned about potential issues with Ext4 but after some testing found the system to run faster on Ext4 so went for it.

Not to concerned about re-installing jaunty if gets all messed up,
but really don't want to lose all the files on the Ext3 partition, too much to feasibly backup.

Am I safe?:confused:
well as safe as can be.

---

### Post by inxygnuu on 2009-05-01
I would go for it. I have it, and it rocks! not a single problem!:KS

---

### Post by Sef on 2009-05-02
> Not to concerned about re-installing jaunty if gets all messed up,
but really don't want to lose all the files on the Ext3 partition, too much to feasibly backup.

There is no guarantee that if you upgraded to ext4 that all would go well.   That is the reason that you should back up your files on ext3.

---

### Post by psychok9 on 2009-05-02
I've posted some pages back, no one can help me?
I've strange and slow performance with ext3, and with ext4 I don't want lost files, but with the newest/dev 2.6.30-* kernel ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)) I got "modprobe: FATAL: Could not load /lib/modules/2.6.etc/custom/modules.dep, no such file or directory...".

---

### Post by camper365 on 2009-05-03
I have used ext4 for a while now, and I have had multiple kernel panics (because I was stupid and tried to kill init) and other crashes, and I still haven't had issues. I don't doubt that other people have had problems, but I haven't.

---

### Post by shane_orlando on 2009-05-04
The occurrences of bugs at early stages of any file system being developed should not be alarming. Lets just give the developers time, the bugs will be ironed eventually. During this period, we all should play our role in reporting any stability issue encountered.

---

### Post by boyofford on 2009-05-05
> **shane_orlando said:**
> The occurrences of bugs at early stages of any file system being developed should not be alarming. Lets just give the developers time, the bugs will be ironed eventually. During this period, we all should play our role in reporting any stability issue encountered.

True, and the more people who are prepared to test ext4 and report and bugs, the quicker ext4 will be considered the norm.

I'm going to re-install my main computer to ext4 for root (but think i'll leave the home as ext3 for now, just in case)

---

### Post by lovinglinux on 2009-05-05
I'm using ext4 on root and home partitions since the release day and didn't have any problems so far. Today I had my first power failure while running Ubuntu (yes I know, I should get an UPS) and I didn't notice anything abnormal since power came back. Everything seems to be fine.

---

### Post by vldo on 2009-05-05
I have HP Laptop and i choose ext4 filesystem. i have experienced som strange problem and yesterday after normal shutdown my /home partition didnt startup.

I have tried several attempts to correct that (e2fsck -p, -b,..., testdisk ) and at the end partition is not recognized and data is lost.

Im going to try again with some tweaking in fstab (data=journal according to [http://mirror.publicns.net/pub/gnu/tmp/linux-libre-fsf2_2.6.28/linux-2.6.28/Documentation/filesystems/ext4.txt](http://mirror.publicns.net/pub/gnu/tmp/linux-libre-fsf2_2.6.28/linux-2.6.28/Documentation/filesystems/ext4.txt))

---

### Post by ranch hand on 2009-05-05
I have several installations of ext4.  I pushed one to freeze (deliberate), it was a 32bit version.  Took some doing (ram 94.8%).  Ran fine with the ram at 93.7%.

After reboot the only thing I could find out of whack was the alsa mixer had reset my level settings back to default.

No problems with any files or directories.

One of these days I am going to do the same to a 64bit version.  On this box that gives me 2x the CPU.

Ext4 seems real stable and fast to me.  Ubuntu does seem to like this box though.

All that said, I like LTS and so my main OS is Hardy on ext3.

I look forward to 10.04.  I like the idea of having my main OS on ext4.

---

### Post by vldo on 2009-05-06
after while another error in fsck. Even with new kernel installed (2.6.29 Ubuntu 9.04 amd64)

It happened after trashing some files.

fsck -p /dev/sda1

Inodes that were part of a corrupted orphan linked list found
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY

so i tried

e2fsck -vy /dev/sda1

and after that im back into my system. It doesnt seems to be a good state. i will be going back to ext3.

---

### Post by porchrat on 2009-05-08
Seems like there are a lot of mixed experienced with ext4, looking back I'm glad I went with ext3.

---

### Post by logos34 on 2009-05-08
8.04 heron user here, 2.6.24.24...any way to convert to ext4 short of compiling custom kernel _> _2.6.28-? And I suppose I'd need to get patched version of grub?

---

### Post by Sylslay on 2009-05-08
I am useing ext4 since beta version 9,04, on old 40gb Seagate, no problem
so far.
PS.If You don't try, than You don't know , what gone to heppen.:)

---

### Post by RealG187 on 2009-05-09
So could I read an EXT4 drive on 8.10 if it's backwards compatible?

---

### Post by ranch hand on 2009-05-09
While some distros have a problem even seeing ext4, neither 8.04 or 8.10 have any problem with it (see sig).  I transfer stuff from partition to partition all the time, works slickern snot.

---

### Post by freeman2000 on 2009-05-09
At this point, the ext4 file system is not part of Karmic (9.10).  I'm running the Alpha version of Karmic with the 2.6.30-2 kernel, and it is still running the ext3 file system.  This could change in later (beta) releases. I'll run/test the Alpha version a short while before switching over to ext4.  Good luck.

---

### Post by lovinglinux on 2009-05-09
> **freeman2000 said:**
> At this point, the ext4 file system is not part of Karmic (9.10).  I'm running the Alpha version of Karmic with the 2.6.30-2 kernel, and it is still running the ext3 file system.  This could change in later (beta) releases. I'll run/test the Alpha version a short while before switching over to ext4.  Good luck.

What does this mean? They will not use ext4 whatsoever? Who has already ext4 is screwed?

**Additional info about my experience with ext4**

Today I experienced my first problems, but I don't know if they are related to ext4, because I was installing Windows 7 on a virtual box before the problem started and had to kill it. Anyways, after a reboot, fsck couldn't run properly and died with a status error 4. The report suggested to run fsck manually. But I hit control+D and booted normally to do some search in the forums.

Then I rebooted again and started the manual fsck. The problem was in my home partition, but I accidentally ran the fsck on the root partition while mounted. I typed "Y" to fix things until I realized something wasn't right. There were too many questions and too many numbers being displayed on the screen. This scared the hell out of me. Fortunately, it seems that my noobish attempt to fix the problem didn't hurt the system. After a few unsuccessful attempts to solve the issue on the correct partition, I was able to run fsck in the verbose mode from the recover console and the problem was fixed. Everything seems normal and no apparent harm was done. So, if this didn't messed my ext4 system I don't what could do it. 

Since I started to use ext4 I already had a power failure while running the machine, I reinstalled grub several times while testing Windows 7 and other Ubuntu releases and I had this issue with fsck. But everything seems to work fine. The only thing I didn't tested is shrinking an ext4 partition.

So far, I'm pleased with ext4.

---

### Post by mahenkpatel on 2009-05-12
Iam using Ext4 and is pretty stable till now and has given a significant performance boost to my low end laptop.

Iam using this file system as i have all my data in Windows ntfs partitions and Ext4 is only for Ubuntu OS and not for data.:o

---

### Post by ANew on 2009-05-12
Got "Grub error 15" after trying ext4.

---

### Post by boyofford on 2009-05-13
All was going well, then had to kill the omputer at the power source a few times due to lock ups caused by software I guess.

But now the whole system ain't working right! sometimes i can't login properly, sometimes get grub error, sometimes has problems locating program files! don't know enough to blame this all on ext4, but seems likely as got juanty on ext3 on another computer and none of this stuff after hard shutdowns!

gona reinstall, if i can! the livecd can't see my hard drive at the mo!:o

---

### Post by EmyrB on 2009-05-14
Just my 2 pennies worth. I have 9.04 with a root partition of ext3 and a /home, /media/photo's, /media/music partitions all using ext4 and I have not seen an issues with the file system. Fedora 11 will use ext4 as its default file system so either they are insane or they are 100% confident in it.

Cheers

EmyrB

---

### Post by ranch hand on 2009-05-14
I installed Jaunty 64bit twice on the same HDD, both in 2 partitions, 1 with ext3 and 1 with ext4.

The ext3 was a little slower.  No other diference.

Did the same with the 32bit version.  On this box I disable 2 of 4 CPU to run on 32 so the 32 versions run slower.  When run with the box running all 4 there is no difference.

---

### Post by hieuykhoa on 2009-05-15
i'm using 9.04 on EXT4 and it boot 150% faster than 8.10 on ext3!
no problem happened!
EXT4 is good :D!

---

### Post by chriskin on 2009-05-18
> **gertdewots said:**
> 150 % faster? it's imposible.;)

actually it isn't
150% means that it loads 1.5 times faster, which is true
the first days at least :P

---

### Post by raccaman on 2009-05-18
I heard that ext4 save files only when computer works little... if it so, it is impossible to solve the problem also with new kernels because if a file is not saved and the system crashes... there's nothing to do ...Isn't it? It's a question...

---

### Post by ranch hand on 2009-05-18
I have been using ext4 on this box for a month and have had no problems at all.

Saving files is a little faster and they definately load faster when opening them.

---

### Post by lovinglinux on 2009-05-18
> **raccaman said:**
> I heard that ext4 save files only when computer works little... if it so, it is impossible to solve the problem also with new kernels because if a file is not saved and the system crashes... there's nothing to do ...Isn't it? It's a question...

Probably. There has been reports of crashes completely messing with the system, but I had two power failures already here and everything is still running. Nothing weird happening and no data loss.

---

### Post by stimpyjcat on 2009-05-19
i want to use ext4 on my next fresh install but im worried about personal data loss (i use to crash everything i touch :o )

so maybe will make an ext4 root (just want more performance on the system) and ext3 for home (and /boot), that way i think that the loss will be easily repaired if any (just /tmp or /var damaged if lucky)

im right with that idea or was missing something? :-k

---

### Post by raccaman on 2009-05-19
> **lovinglinux said:**
>  Nothing weird happening and no data loss.

I'am happy if you say that!

---

### Post by ranch hand on 2009-05-19
I have been using ext4 since 2 weeks before Jauntys release.  Have had no trouble at all.

If you are worried about it, why not stick with what you are using now?  Wait untill 9.10 comes out and then you can install 9.04.  Should be nice and stable by then.

Or, you could dual boot.

---

### Post by Sef on 2009-05-19
> i want to use ext4 on my next fresh install but im worried about personal data loss (i use to crash everything i touch :eek: )


If ext4 is considered stable, it will be the default file system.  If not, then stick with ext3.

---

### Post by lovinglinux on 2009-05-20
I had another power failure here and had to call the power company to fix it. I know I should get an UPS. Anyways, my Jaunty is still up and running. The only thing I noticed is that Firefox changes its default fonts after these events. I also had a few Firefox crashes caused by the Open Book extension and had to use the CTRL+ALT+Backspace a few times (now I know I can use CTRL+ALT+F1 then kill Firefox), but things are still running fine, including the torrents that were running in the background.

I'm not trying to convince anyone to use ext4, just reporting my experiences with it.

EDIT: actually, there was two power failures today. One was all over my city at 7 am and the other was only on my street at 10 am.

---

### Post by blogx on 2009-05-20
I just thought Ext4 is new, I'd like to try it. But I don't know if there are bugs or not.

---

### Post by ranch hand on 2009-05-21
Works great for me.

---

### Post by redjoel on 2009-05-22
Thanks, Great Post:popcorn:

---

### Post by jimbo99 on 2009-05-28
He's not yanking your chain.  Until a confirmed fix is out across the board one should refrain from using it, regardless of your success.

---

### Post by techfanboy81 on 2009-05-31
For me its ext4 because it is already established, quick and compatible to ext3 and ext2.

Thanks.

---

### Post by Sef on 2009-05-31
> He's not yanking your chain. Until a confirmed fix is out across the board one should refrain from using it, regardless of your success.
As long as one is aware of the problems then it is fine to use it.  As the saying goes - if it breaks, you get to keep both pieces.   (Yes, I am using ext 4 for root and home.)

---

### Post by mevan_snp on 2009-06-01
thanks mate really good info

---

### Post by pansue on 2009-06-04
> ** said:**
> 
I don't think so ,i have been  using ext4 for a long time ,and i don't met any so called issues

---

### Post by ranch hand on 2009-06-04
> **pansue said:**
> I don't think so ,i have been  using ext4 for a long time ,and i don't met any so called issues

+1

I actually have had a couple issues, it is slightly faster and even transfers to/from other (non ext4) partitions is smoother and faster.  I find it is faster to even transfer things from one partition to an other using the ext partition for nothing but control.

---

### Post by Ceedub2 on 2009-06-05
Being a new user. I figured I would go with ext3.

---

### Post by Makatozi on 2009-06-08
I just switched to ext4 over the weekend, so far so good. Lest see how it goes, will post if it falls over.

Cheers,

---

### Post by Polaris96 on 2009-06-08
This is probably a dumb question, but you DID have to back and restore to do that reformat, right?  If ext can reformat a drive and hold the data, I'm chucking reiser!

---

### Post by ranch hand on 2009-06-08
> **Polaris96 said:**
> This is probably a dumb question, but you DID have to back and restore to do that reformat, right?  If ext can reformat a drive and hold the data, I'm chucking reiser!

I think you should back up your /home and just do it.  Jaunty was built for ext4 (I am on it now) and it works great.

---

### Post by Partyboi2 on 2009-06-08
> **Polaris96 said:**
> This is probably a dumb question, but you DID have to back and restore to do that reformat, right?  If ext can reformat a drive and hold the data, I'm chucking reiser!
There are no dumb questions :) 
When you convert to ext4 it should not wipe your data, but in saying this it is always recommend to backup before working on partitions.

---

### Post by Polaris96 on 2009-06-08
you guys rool!  r we talking 

sudo mkfs -t ext4 /dev/sda1  #or similar

or is there a different approach i need?  Also i'm on reiser now.  will it make a diff?

---

### Post by diesal3 on 2009-06-09
From what i've read with reformatting to ext4, it only applies the ext4 rules to new files created after you "convert" the filesystem from ext3 to ext4. i've been using ext4 on Jaunty right from the off and i noticed it was better then ext3 with intrepid.

---

### Post by dE_logics on 2009-06-10
Why not just use reiserfs or if jaunty supports reiser4...its better.

Other options will be JFS and XFS...these 3 are at the top.

---

### Post by PeterBBB on 2009-06-10
*_The issues with Ext4:-_*

One rather serious issue for those dual booting with Windows is the current lack of any Windows driver. 
Shareable partitions neet to be FAT, EXT2/3 or NTFS.

Several times I have resolved problems with unfortunate edits of fstab, menu.lst etc by fixing the mess from Windows.

Just curious; for those who don't need Windows access but want extents to handle large files; have you thought about XFS?

---

### Post by ranch hand on 2009-06-10
> **PeterBBB said:**
> *_The issues with Ext4:-_*

One rather serious issue for those dual booting with Windows is the current lack of any Windows driver. 
Shareable partitions neet to be FAT, EXT2/3 or NTFS.

Several times I have resolved problems with unfortunate edits of fstab, menu.lst etc by fixing the mess from Windows.

Just curious; for those who don't need Windows access but want extents to handle large files; have you thought about XFS?

I never have had problems with Windows file systems.  Gparted wiped them clean easily.;-)

I have never considered XFS in a serious manner.  ext4 is a very stable, fast, segmentation resistant FS and I really like it.  If I could I would convert my other ext2 and 3 OSs to it.  The only problem I have with it is that i need to use an ext4 OS to transfer files to the others (my main OS is still Hardy).

---

### Post by carcar1 on 2009-06-12
I have had abosolutely no problems with ubuntu Jaunty on two machines with ext4 as the file system.

---

### Post by jumbofishmeat on 2009-06-17
I've heard reports of data loss and corruption. It's not quite as refined as it needs to be yet.

---

### Post by Sef on 2009-06-18
> I've heard reports of data loss and corruption. It's not quite as refined as it needs to be yet.


Nothing new there.  It was mentioned on the first post.  Which is why it is not advised for computers that are need stability.

---

### Post by Arup on 2009-06-18
Running ext4 since day one of Jaunty release, not a single glitch so far on my 1 and 2 TB drives. I do have a UPS so there is no chance of dirty shutdown.

---

### Post by running_rabbit07 on 2009-06-19
Here is a case where EXT 4  was a problem.

[http://ubuntuforums.org/showthread.php?t=1190673](http://ubuntuforums.org/showthread.php?t=1190673)

---

### Post by hero1900 on 2009-06-19
if EXT4 has** problems  **why the new alpha by default EXT4 as i heard or it is not
???

---

### Post by running_rabbit07 on 2009-06-19
> **hero1900 said:**
> if EXT4 has** problems  **why the new alpha by default EXT4 as i heard or it is not
???


That'll be sweet as long as it works well. I look forward to it especially if EXT4 gets good use out of the hard drive. I am new to the Ubuntu/Linux world but I am happy that it is working so well the EXT3 I have now. I am looking forward to studying how the versions are different after I finish with the summer semester.

---

### Post by ranch hand on 2009-06-19
> **running_rabbit07 said:**
> Here is a case where EXT 4  was a problem.

[http://ubuntuforums.org/showthread.php?t=1190673](http://ubuntuforums.org/showthread.php?t=1190673)

I am not convinced that was a ext4 problem.  It was resolved by accidentally reformating the entire HDD and using ext3.  The guy used ext4 for about 6 months with no problems.

If he had redone his HDD with ext4 and had the same problem I would believe it but this could have been anything.

---

### Post by Astound on 2009-06-20
For what it's worth, I chose the custom partition option on install and set ext4 file system option since it was available and new.

Freezing issues, already documented, so I did not want to wipe out the partitions and start over.

I then installed/upgraded to Kernel 2.6.30 as suggested, but that opened another can of worms, sound skipping/stuttering.

I then downgraded to Kernel 2.6.29 and automagically everything sorted itself.

System is fast, feels really snappy, scrolling Firefox, switching Desktops does not skip a beat on any music or videos being played.

The speed and performance is awesome, so I named my Desktop Awesome :popcorn:
So when 9.10 arrives, I will be ready on ext4.

In a nutshell, Ubuntu is Awesome, everything just works!

---

### Post by lsatenstein on 2009-06-20
I have been using EXT4 since April, without any problems whatsoever.

It is trivially faster then using ext3, for single user systems.

---

### Post by running_rabbit07 on 2009-06-21
Out of curiousity I made a third OS partition and added Ubuntu 9.04 with EXT4 and it loads faster on startup and looks a little different. I think when I loaded Edubuntu it changed the appearance settings this time, which is good because it looks good. All with no problems so far.

---

### Post by -kg- on 2009-06-21
I've been using ext4 since I installed Jaunty, and have had no problems whatsoever that could be attributed to the ext4 file system.  However, I have read through the entire thread and have seen no questions or comments on one issue that confuses me:

> 4) The current GRUB will not boot into it. A boot partition must be created.

Upon installing Jaunty on ext 4 (all three installations; Ubuntu, Kubuntu, and Xubuntu), I was unaware of this requirement, and installed all three with no boot partition (formatted to ext2/3, as I've read recently).  I installed Kubuntu and Xubuntu on a single root partition, and Ubuntu I installed with an extra /home partition, as this is the desktop environment that I generally use.

I was made aware of this issue because I am intending to install Fedora F11 as an experimental install (I just want to play with it), and it states right in the installation Wiki that you must use a /boot partition formatted to ext2 or ext3 because it's GRUB will not recognize an ext4 partition.

Apparently, Ubuntu's GRUB recognizes an ext4 partition, else how is it booting to any of my Ubuntu installations (flawlessly, BTW)?  Was this GRUB issue resolved between the posting of this thread and now (or should I say, then, since I've had Jaunty for a couple of months or so now)?  I've read nothing on this, and am surprised that, since it seems that F11 came out not too long ago, that they didn't implement it in that release.

Not really a problem, since I can install F11 and, if it's GRUB doesn't recognize Ubuntu on ext4, I can just reinstall Ubuntu's GRUB, which will detect my Ubuntu installations, as well as Fedora's, but it took me by surprise, reading that Fedora's GRUB won't recognize ext4 partitions, when Ubuntu's obviously will.  I assumne that GRUB is part of Open Source and all Fedora would have to do is implement the latest GRUB.

---

### Post by ranch hand on 2009-06-22
I had never heard of the /boot problem.  I installed A2 (with grub2) and had no trouble with it booting right up on my / an /home partitions.

It did not pick up the other 3 OSs on the HDD but that was not an ext4 problem either as 1 of those was ext3 (Hardy).  I have that problem straight now to, pretty good for grub2 in Ubuntu which is not officaooy supporting multi-boot until A3.

I have used ext4 from Jaunty RC on and have no problems with it.

---

### Post by Sef on 2009-06-22
> I've been using ext4 since I installed Jaunty, and have had no problems whatsoever that could be attributed to the ext4 file system. However, I have read through the entire thread and have seen no questions or comments on one issue that confuses me:

 	Quote:
 	 	 		 			 				4) The current GRUB will not boot into it. A boot partition must be created. 			 		

That was true at one point, but starting withUbuntu Jaunty that is not needed anymore.  There was some patches added to the kernel, so it could boot without having a boot partition.   GRUB2 will boot into ext4.

---

### Post by Stason on 2009-06-30
Can ext4 be used under windows?

---

### Post by Sef on 2009-06-30
> Can ext4 be used under windows?


No. It is not designed to use ext4 (nor ext3 nor ext2.)

---

### Post by lovinglinux on 2009-07-01
I had my first lock up today, while deleting several files from the trash. I had to hard reboot, but everything seems to be pretty fine. Considering the number of previous power failures without any damage, I think I'm pretty lucky or ext4 is more robust than I thought.

---

### Post by running_rabbit07 on 2009-07-01
I had a situation like that recently, I was moving files from the desktop to another folder but the folder icons stayed on the desktop for several minutes. I then dragged the folders to the trash bin and clicked empty trash, the folders still didn't disappear so I rebooted. When I restarted the folders were no longer in the folder I had moved them to, I lost over 2 gigs of files. Luckily most of them had been backed up. I don't know if that was due to the EXT4 or just a Ubuntu thing but that is the only time I have lost any files.

---

### Post by wersdaluv on 2009-07-02
I haven't read the whole thread but if it isn't mentioned yet, I just want to suggest stating in the original post that ext3 is beneficial for dual booters because there currently is no ext4 reader app on Windows (afaik). As for me, I use ext4 for root and ext3 for /home :)

---

### Post by running_rabbit07 on 2009-07-02
I am happy with Windows not being able to see what is on the other side. That makes it even less likely that a virus downloaded through windows will effect the Ubuntu partition.

---

### Post by tkrisz on 2009-07-07
I still have an old Gutsy without separate /home partition and have 32 bit on my AMD64. So i plan to install a brand new Jaunty 64 bit with separate /home partition.

I have the following questions:
1. Later i will surely want to use ext4, shall i be able to upgrade to ext4 if i install ext3 now, without reinstalling the whole thing?
2. If i install / ext3 and /home ext4, will there be any problem, if i reinstall / as ext4 in 9.10 or 10.04?
3. Shall i be able to access (r/w) my Xp partition if i install ext4 now? 
4. Or should i install / as ext4 and just upgrade normally to 9.10 and 10.04 as time comes and leave /home in ext3 for whatever compatibility or stability reason?
5. Will there be any compatibility issues between a computer running an ext3 FS and another running an ext4 (guess not, just ask for sure)? 

Sorry for the newbie question.

---

### Post by running_rabbit07 on 2009-07-07
> **tkrisz said:**
> I still have an old Gutsy without separate /home partition and have 32 bit on my AMD64. So i plan to install a brand new Jaunty 64 bit with separate /home partition.

I have the following questions:
1. Later i will surely want to use ext4, shall i be able to upgrade to ext4 if i install ext3 now, without reinstalling the whole thing?
2. If i install / ext3 and /home ext4, will there be any problem, if i reinstall / as ext4 in 9.10 or 10.04?
3. Shall i be able to access (r/w) my Xp partition if i install ext4 now? 
4. Or should i install / as ext4 and just upgrade normally to 9.10 and 10.04 as time comes and leave /home in ext3 for whatever compatibility or stability reason?
5. Will there be any compatibility issues between a computer running an ext3 FS and another running an ext4 (guess not, just ask for sure)? 

Sorry for the newbie question.

I don't have the answers to all of your questions but I can tell you that to change from EXT3 to EXT4 requires formatting the partition. I have had Ubuntu loaded twice for a while and did not have any problems. I had it installed once with EXT3 and once with EXT4 in separate partitions but they were both installed at the same time. I have AMD 64 also and I have removed the EXT3 partition to make the EXT4 bigger. EXT4 runs great on my PC. 

As far as running both file systems for different folders, I have seen people here say you can do it. I personally don't know how to do that.

As for question 3, I can mount my XP partition but I don't know if XP can see the EXT4, I haven't tried it. I have only booted XP 3 times in the past month and every time I do it does so many updates that it has to reboot. As soon as it reboots I go back to Ubuntu.

I do plan to upgrade to Karmic as soon as it comes out but I won't be in the biggest hurry. Jaunty works perfect for me and if it ain't broke, I don't need to fix it. Though the geek within says get it immediately.

I hope this info helps you.

---

### Post by tkrisz on 2009-07-07
Thank you for the answer.
One more questions:
6. If there are errors with the ext4 FS, will these be fixed by the regular updates or by the distro update? And if yes, will the errors be fixed on my /home partition as well?

---

### Post by ranch hand on 2009-07-07
> **tkrisz said:**
> I still have an old Gutsy without separate /home partition and have 32 bit on my AMD64. So i plan to install a brand new Jaunty 64 bit with separate /home partition.

I have the following questions:
1. Later i will surely want to use ext4, shall i be able to upgrade to ext4 if i install ext3 now, without reinstalling the whole thing?
2. If i install / ext3 and /home ext4, will there be any problem, if i reinstall / as ext4 in 9.10 or 10.04?
3. Shall i be able to access (r/w) my Xp partition if i install ext4 now? 
4. Or should i install / as ext4 and just upgrade normally to 9.10 and 10.04 as time comes and leave /home in ext3 for whatever compatibility or stability reason?
5. Will there be any compatibility issues between a computer running an ext3 FS and another running an ext4 (guess not, just ask for sure)? 

Sorry for the newbie question.
Just install ext4.  If you install on 2 partitions with One ext3 and one ext4 you are asking for fragmentation errors more than you will get when you import files from ext3.

Ext4 works fine and is faster and the fragmentation problems will not be as often when we are going from backup files and old OS files in ext4 instead of ext3.  The sooner you change the quicker you will see this.

You wil be aboe to get to your XP files.  XP will not get to your ext4 files (or Vista and I don't think Win7 either).  Ext4 fully supports all MS FS'.

If you are trying to get files from an ext3 partition you will, like with MS, have to work from the ext4 partition or box.  I am sure that ext3 will be patched to support ext4 pretty soon (a lot faster than MS will).

---

### Post by tkrisz on 2009-07-07
Thx for the answer. Meanwhile i went for an ext4 both for / and /home.
Now i'm facing a grub problem.
I've read the release notes, so i'm not surprised.
I've already tried 2 methods, it seems like fixing it (no error reports) but as i reload the "Error 22" is still there and can't boot any OS.

---

### Post by running_rabbit07 on 2009-07-07
If you don't find a fix soon for that, I would recommend starting a new thread titled "Error 22." That way you get help faster from the people who know how to fix that.

---

### Post by caco on 2009-07-09
I have been using ext4 since the official release of Jaunty, and have not lost any file though I have experienced a couple of system lock-ups that needed a forced power off, maybe be caused by the fs or faulty programme codes, or even climate change ;)

 [[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by Revolutionary101 on 2009-07-09
Does anyone know the benefits of using ext4 instead of ext3?

---

### Post by running_rabbit07 on 2009-07-09
[CENTER][LEFT]I know it is a bit faster for me. I was running Ubuntu in two partitions, one with EXT3 and one with EXT4. 


EXT4 was much faster. I now have just EXT4 running and it works great!
[/LEFT]
[/CENTER]

---

### Post by ranch hand on 2009-07-09
> **Revolutionary101 said:**
> Does anyone know the benefits of using ext4 instead of ext3?
short summary;

[http://www.search.com/reference/Ext4](http://www.search.com/reference/Ext4)

the wiki for the project;

[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

Note that ext4 has been around for some time (over 2.5 years) and that it is primarily an improvement over ext3 as it can work with larger drives and larger files better.  

Basically it will work with new computers and the way people use them.

---

### Post by techfanboy81 on 2009-07-11
Will the old data structure be used in the Ext4?

---

### Post by tosh-l33 on 2009-07-13
I thought Ext4 was supposed to be the newer and more advance and improved version. :S

---

### Post by Supermouse on 2009-07-22
I was using ext4 on my eeepc 701 for quite a while, but then, about more or less a week ago, I started to see some IO errors, crashes and such.

Now I'm reinstalling the system using ext3 to see if this is related to the file system.

---

### Post by moster on 2009-07-24
> **Revolutionary101 said:**
> Does anyone know the benefits of using ext4 instead of ext3?

Faster writing, size limits and other are gone, less fragmentation... Nearly everything is pushed little further.

---

### Post by saji1511 on 2009-07-29
> **moster said:**
> Faster writing, size limits and other are gone, less fragmentation... Nearly everything is pushed little further.

hey thanks for this, I have been looking for the same.

---

### Post by ezsit on 2009-07-29
> I have never considered XFS in a serious manner. ext4 is a very stable, fast, segmentation resistant 

Really? XFS has been around a heck of a lot longer, is proven stable with at least a decade of use, and has every feature and more than ext4. You really haven't given XFS a thought? That seems VERY imprudent (uneducated, ill-conceived, nonsensical, rash, and downright ig-nant).

---

### Post by ranch hand on 2009-07-29
> **ezsit said:**
> Really? XFS has been around a heck of a lot longer, is proven stable with at least a decade of use, and has every feature and more than ext4. You really haven't given XFS a thought? That seems VERY imprudent (uneducated, ill-conceived, nonsensical, rash, and downright ig-nant).
The max file size in XFS is smaller than ext4.  XFS is great but ext4 is more flexible and more prepared to deal with the future needs of PC users.

Let's face it, what drive the popularity of any tech is actually what is the current favorite with the people developing the end product.  This is why the open source community is needed to keep a kind of "genetic diversity" in electronic devices.

I am sure that someone out there is working with something that is considered obsolete (XFS is not) that will shock us all silly when it comes out in its new flavor.

I must take this time to correct your use of language.  I believe that when you wrote ig-nant you really meant to write ignert.

---

### Post by ezsit on 2009-07-30
According to wikipedia
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

The capacity of XFS FAR exceeds the capacity of ext4. Largest filesize for XFS is listed as 64Tib (tebibyte) - under Linux, (8EiB filesize limit under IRIX) and the max filesize for ext4 is 16TiB (tebibyte). Also, filesystem volume size under XFS is listed as 8EiB (exbibyte) and only listed as 1EiB (exbibyte) under ext4. I'd say, if the numbers are accurate, XFS was designed with far greater headroom than ext4. 

XFS was designed by SGI to handle supercomputing environments with thousands of processors and hundreds of drive arrays and distributed cluster (or grid) computing environments in commercial, government, and research settings where accountability and reliability were guaranteed by SGI. XFS was designed, built, tested, and deployed long before ext4 was even conceived.

Now I doubt the average desktop user in my lifetime will encounter a hard drive that will push the TiB or EiB limits of either filesystem. I also doubt that anyone has enough time to watch a 16TiB video file. I haven't done the math, but that just might be longer than the average lifespan. All this talk is moot, really. 

Then again, I remember the days when 32K of memory was sufficient and 64K of memory was an extravagant luxury, so maybe we will need such large capacity drives and high capacity filesystems in the not too distant future? Maybe?

Thanks for correction on ignert though.

PS - I'm sticking with ext3 for the foreseeable future. It remains my most trusted filesystem, more than fast enough, and I don't plan on pushing the 16GiB filesize limit or the 2TiB volume size limit. If you really think you need that much capacity, then your desktop needs far exceed mine - I have no problem admitting that.

---

### Post by moster on 2009-07-30
There is reason why is ext4 default FS on fedora. MOst people wait to BTRFS become stable, they will wait for year or so.. It is like that state-of-art FS Solarises ZFS and it is particulary interesting for servers. But desktop users do not need capabilities of FS like that so most of them would probably stay on ext4 because it is fastest FS today available.

---

### Post by ezsit on 2009-07-30
True, ext4 is proving to be the fastest overall FS available. There are features which make it attractive too, like built-in checksum ECC, enhanced timestamping capabilities that will make realtime backups and snapshots feasible, built-in defragmentation, and few more features that will make ext4 a great desktop and server choice. However, at this time, I feel more comfortable going with the ext3 FS simply because I do not require the advantages of ext4 when it is still relatively untested in the wider market. A couple years down the road, when I get new hard drives, maybe I'll give it a shot.

---

### Post by kk0sse54 on 2009-07-30
> **moster said:**
> There is reason why is ext4 default FS on fedora. MOst people wait to BTRFS become stable, they will wait for year or so.. It is like that state-of-art FS Solarises ZFS and it is particulary interesting for servers. But desktop users do not need capabilities of FS like that so most of them would probably stay on ext4 because it is fastest FS today available.

ZFS is pretty sweet, I use it on my desktop, linux wise though I still prefer JFS

---

### Post by moster on 2009-07-30
There is no rush... but I was in situation that I could get all my data off my HDDs and they needed defrag anyway... so I just jump the ext4 ship and off I go :)

---

### Post by Dullstar on 2009-07-30
> **vigyani said:**
> Hi

It would be really nice if you can provide references and links to substantiate the claims made in this post.

> **Sef said:**
> Disclaimer:- This thread only issues the use of Ext4 on Ubuntu Jaunty(9.04) and does not apply to earlier releases where Ext4 may not have been available as an option due to Ext4 not having been stable.

As you may have noticed, you now have the option of installing Ext4 through Ubuntu Jaunty. Ext4 is quite a big update from Ext3 but it still is only incremental and is backwards-compatible with Ext3, so it is very stable, however a few issues about the filesystem have recently sprung up that may require you to be a little careful when using this filesystem.

**_Reasons to stick to Ext3:-_**

1) Ext3 is the default file system for *buntus.

2) It is very stable, so no worries about losing your data due to crashes.

3) The one that is recommended to be on your work stations.


**_The issues with Ext4:-_**

1) There have been reports of crashes having corrupted configuration files and sometimes more with Ext4 in use.

2) This has been addressed in kernel 2.6.30, however it will not hit Ubuntu Jaunty, but Ubuntu Karmic.

3) [9.04 Release Notes: Other Known Issues]("http://www.ubuntu.com/getubuntu/releasenotes/904") for more detail.

Therefore, while Ext4 is really good, it still does need a few bugs to be ironed out, but all in all, it is quite stable for the average desktop user, just as long as you take regular backups, as you would when using any file system.

And just one more thing, Ext4 is not to be blamed completely, part of the problem stems from programs which fail to adhere to the standard regarding I/O on disk.

More information regarding this matter can be obtained here:
Theodore Tso's(One of Ext4's main developers) blog post regarding this issue:-
[http://thunk.org/tytso/blog/2009/03/...-file-problem/]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/")

Article (29 May 2009):[ The Ext4 File Linux File System]("http://www.h-online.com/open/The-Ext4-Linux-file-system--/features/113403/0") by Dr. Oliver Diedrich

(Thank you to PmDematagoda and bhodi.zazan for helping me improve this thread.)

[_Looks like this one would suit you nicely!_](http://en.wikipedia.org/wiki/File:Webcomic_xkcd_-_Wikipedian_protester.png)

---

### Post by Dullstar on 2009-07-30
> **ezsit said:**
> According to wikipedia
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

The capacity of XFS FAR exceeds the capacity of ext4. Largest filesize for XFS is listed as 64Tib (tebibyte) - under Linux, (8EiB filesize limit under IRIX) and the max filesize for ext4 is 16TiB (tebibyte). Also, filesystem volume size under XFS is listed as 8EiB (exbibyte) and only listed as 1EiB (exbibyte) under ext4. I'd say, if the numbers are accurate, XFS was designed with far greater headroom than ext4. 


Good thing later in the post you mentioned that the average user would probably not encounter those sizes.  Would any user need files that big?

---

### Post by bcschmerker on 2009-07-31
Thank you for the briefing on improvements in ext4 w/r/t ext3; I anticipate using ext4 from the outset when Ubuntu Lucid Lynx finally becomes available for testing Autumn 2009 (when Version 9.10 is officially released).  My Gigabyte/AMD-equipped Everex currently runs ext3 on PATA (/dev/hda for System/User, /dev/hdb for Home/Option) for the current Version 8.04-LTS, and I plan on four new SATA drives in AHCI mode for testing the eventual Version 10.04-LTS; obviously I am awaiting Image files for a preliminary Live CD.

---

### Post by seven7seven on 2009-08-08
In all honesty, there isn't a foolproof FS, you can get some nasty problems when expecting them the least - so I'll probably take a chance.

I don't suppose ext4 is unstable enough to cause issues with other partitions on the same drive, is it? :???:

---

### Post by moster on 2009-08-08
> **seven7seven said:**
> In all honesty, there isn't a foolproof FS, you can get some nasty problems when expecting them the least - so I'll probably take a chance.

I don't suppose ext4 is unstable enough to cause issues with other partitions on the same drive, is it? :???:

Noo, it is not alpha or beta. It is considered stable but has few twitches. It will be default in Ubuntu 9.10.

Problem was with hard reset computer when some file is just being written. Apparently, that file could be deleted.

From my knowlegde this could be that situation. Open large .doc file in OpenOffice the change something and try to save it to the same file. And it that moment of saving reset computer or power failure. Now, problem is that you could lose new and old version of file. I do not say you will. But you might, because some of blame is how programmers are saving that file. This with Open Office was just example to make it easier to understand.

---

### Post by ranch hand on 2009-08-08
> **seven7seven said:**
> In all honesty, there isn't a foolproof FS, you can get some nasty problems when expecting them the least - so I'll probably take a chance.

I don't suppose ext4 is unstable enough to cause issues with other partitions on the same drive, is it? :???:
I have 20 partitions on one drive.  Three are ext3.  The other 18 are ext4.  There is no problem on that drive.

---

### Post by kestal on 2009-08-10
I have been using EXT4 on 3 partitions (on 2 separate drives) from my main computer and I have not had *any* problems at all.

---

### Post by johnschong on 2009-08-13
I will also use ext3 instead of ext4, because ext4 is not stable!

I know that not stable may make the system crashes.

Before I use Ubuntu, I use Fedora and RedHat, I know Fedora11 has made ext4 as the 

default selection of Linux File System, will it crashes?

And I heard my friend said that Ubuntu is based on Debian, a stable and a system may run 

for many years without crashes, so I use Ubuntu for my linux system.

Although many people said that ext4 is ok, but I still afraid to use, ha!

---

### Post by exsecant on 2009-08-13
So is there a safe way to shrink an ext4 partition now?

The release notes for 9.04 make it pretty clear that you risk blowing up all your data but surely there must be a fix to such a critical bug by now?

---

### Post by ranch hand on 2009-08-14
I have been doing this with no problems nearly from the release of 9.04.

---

### Post by moster on 2009-08-14
Come on people. There are 800 000 peoples on this forum. Many of them use ext4 and I do not see threads "ext4 blow away my data".

It is one of that fears that you afraid of one thing, and possibility is lower then you are get bitten by *** from shark - in Tibet.

---

### Post by ranch hand on 2009-08-14
> **moster said:**
> come on people. There are 800 000 peoples on this forum. Many of them use ext4 and i do not see threads "ext4 blow away my data".

It is one of that fears that you afraid of one thing, and possibility is lower then you are get bitten by *** from shark - in tibet.
+1

---

### Post by Sef on 2009-08-14
> Come on people. There are 800 000 peoples on this forum. Many of them use ext4 and I do not see threads "ext4 blow away my data".

It is one of that fears that you afraid of one thing, and possibility is lower then you are get bitten by *** from shark - in Tibet.

Having your data blown away is not a common occurrence, but it has happened.  If you prefer to play it safe, then choose ext3; if you do not mind taking a small risk, then choose ext4.   Whatever you use, back up your data.

---

### Post by exsecant on 2009-08-14
> **moster said:**
> Come on people. There are 800 000 peoples on this forum. Many of them use ext4 and I do not see threads "ext4 blow away my data".

It is one of that fears that you afraid of one thing, and possibility is lower then you are get bitten by *** from shark - in Tibet.


If you had read my post you you would have seen that it was talking about risks of data loss when resizing ext4 partitions.  Using ext4 is one thing that I'm sure many people do (myself included); *resizing* is something that I am quite sure is far less common.  As I pointed out the release notes specifically said the bug causes data corruption, and as someone to whom this exact thing has happened in the past, I think it's not unreasonable to be worried that it might happen again.

---

### Post by moster on 2009-08-14
> **exsecant said:**
> If you had read my post you you would have seen that it was talking about risks of data loss when resizing ext4 partitions.  Using ext4 is one thing that I'm sure many people do (myself included); *resizing* is something that I am quite sure is far less common.  As I pointed out the release notes specifically said the bug causes data corruption, and as someone to whom this exact thing has happened in the past, I think it's not unreasonable to be worried that it might happen again.

Unfortunely you are right. I know of same/similar bug existed even before Jaunty came out, and it seems they did not backport patch or it is maybe even another bug. So... waiting for carmic koala to deal with this. Or maybe someone else have something to say.

---

### Post by VMC on 2009-08-15
> **moster said:**
> Unfortunely you are right. I know of same/similar bug existed even before Jaunty came out, and it seems they did not backport patch or it is maybe even another bug. So... waiting for carmic koala to deal with this. Or maybe someone else have something to say.

I think those of us here that are comfortable with using ext4, are not worried.And who's to say, if you did lose data, that it was some other issue and not ext4. 

Yesterday using gparted I moved resized and moved again 4 ext4 partitions. It was a very convoluted attempt to straighten out my systems. Everything went well. Also using gparted and somewhere in that  mix I copied ext4 to unallocated space and other FS's. Nothing. I mean nothing failed. gparted has come a long. I remember a year or two ago it failed miserable. Long before I was using ext4's. My the way, on several occasions I have had reason to just power cycle my system. Never once has ext4 failed. I complained but recovered.

I will continue using Ext4 exclusively. I have yet to lose any data. If you think I'm lucky...well, then I'm lucky a lot.

---

### Post by moster on 2009-08-16
> **VMC said:**
> I think those of us here that are comfortable with using ext4, are not worried.And who's to say, if you did lose data, that it was some other issue and not ext4. 

Yesterday using gparted I moved resized and moved again 4 ext4 partitions. It was a very convoluted attempt to straighten out my systems. Everything went well. Also using gparted and somewhere in that  mix I copied ext4 to unallocated space and other FS's. Nothing. I mean nothing failed. gparted has come a long. I remember a year or two ago it failed miserable. Long before I was using ext4's. My the way, on several occasions I have had reason to just power cycle my system. Never once has ext4 failed. I complained but recovered.

I will always use Ext4. I yet to lse any data. If you thing I'm lucky, then I'm lucky a lot.

It was some problem when NTFS partitions are in game. Of course, it was not 100% that it will bork system even then. So maybe you have no NTFS partitions, maybe they fix that after all or maybe you are just crazy lucky :D

I had no problems with ext4 even I had some hard resets. So it is stable for me :)

---

### Post by geeta4 on 2009-08-16
:lolflag:> **Sef said:**
> Disclaimer:- This thread only issues the use of Ext4 on Ubuntu Jaunty(9.04) and does not apply to earlier releases where Ext4 may not have been available as an option due to Ext4 not having been stable.
 
As you may have noticed, you now have the option of installing Ext4 through Ubuntu Jaunty. Ext4 is quite a big update from Ext3 but it still is only incremental and is backwards-compatible with Ext3, so it is very stable, however a few issues about the filesystem have recently sprung up that may require you to be a little careful when using this filesystem.
 
**_Reasons to stick to Ext3:-_**
 
1) Ext3 is the default file system for *buntus.
 
2) It is very stable, so no worries about losing your data due to crashes.
 
3) The one that is recommended to be on your work stations.
 
 
**_The issues with Ext4:-_**
 
1) There have been reports of crashes having corrupted configuration files and sometimes more with Ext4 in use.
 
2) This has been addressed in kernel 2.6.30, however it will not hit Ubuntu Jaunty, but Ubuntu Karmic.
 
3) [9.04 Release Notes: Other Known Issues]("http://www.ubuntu.com/getubuntu/releasenotes/904") for more detail.
 
Therefore, while Ext4 is really good, it still does need a few bugs to be ironed out, but all in all, it is quite stable for the average desktop user, just as long as you take regular backups, as you would when using any file system.
 
And just one more thing, Ext4 is not to be blamed completely, part of the problem stems from programs which fail to adhere to the standard regarding I/O on disk.
 
More information regarding this matter can be obtained here:
Theodore Tso's(One of Ext4's main developers) blog post regarding this issue:-
[http://thunk.org/tytso/blog/2009/03/...-file-problem/]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/")
 
Article (29 May 2009):[ The Ext4 File Linux File System]("http://www.h-online.com/open/The-Ext4-Linux-file-system--/features/113403/0") by Dr. Oliver Diedrich
 
(Thank you to PmDematagoda and bhodi.zazan for helping me improve this thread.)

---

### Post by ranch hand on 2009-08-16
Jaunty and Karmic are released to be ext4.  I have used Jaunty on ext3 and it is not as good as on ext4.

I have moved and resized one Juanty install that I have to another HDD (made it smaller).  No problem.  My last install of KarmicA4 had the /home partition too small (my fault - note to self - learn to read) so I doubled its size after installation.  No problem.

---

### Post by dasan on 2009-08-20
I think Ext4 is better than ext3
i have kubuntu 9.04 with ext4 
i didn,t have any probs yet..
and my disk check time and disk to disk to copy time is reduced lot...
:lolflag:

---

### Post by moster on 2009-08-23
> **ranch hand said:**
> Jaunty and Karmic are released to be ext4.  I have used Jaunty on ext3 and it is not as good as on ext4.

I have moved and resized one Juanty install that I have to another HDD (made it smaller).  No problem.  My last install of KarmicA4 had the /home partition too small (my fault - note to self - learn to read) so I doubled its size after installation.  No problem.

Can you confirm that Carmic come with default ext4? I doubt Canonical would do that if they think it is dangerous.

---

### Post by Partyboi2 on 2009-08-23
> **moster said:**
> Can you confirm that Carmic come with default ext4? I doubt Canonical would do that if they think it is dangerous.
Ext4 is the default file system for Karmic
[http://www.ubuntu.com/testing/karmic/alpha](http://www.ubuntu.com/testing/karmic/alpha)

---

### Post by ranch hand on 2009-08-23
> **Partyboi2 said:**
> Ext4 is the default file system for Karmic
[http://www.ubuntu.com/testing/karmic/alpha](http://www.ubuntu.com/testing/karmic/alpha)
Just as it was for Jaunty.  Boot to  any LiveCD of Jaunty and see what FS you are using.

---

### Post by Br1987 on 2009-08-26
Ok... thank you very much.... I'm brand new and I'm getting familiar with all this things :)

---

### Post by VMC on 2009-08-26
> **moster said:**
> Can you confirm that Carmic come with default ext4? I doubt Canonical would do that if they think it is dangerous.

If you are in karmic, from Terminal type: ```
df -T
``` that will show you what file system your running.

---

### Post by moster on 2009-08-26
> **VMC said:**
> If you are in karmic, from Terminal type: ```
df -T
``` that will show you what file system your running.

Thanks. i am not on Carmic but I am thinking about it :)

---

### Post by dasan on 2009-08-27
Is there any body who have a bitter experience with EXT4...

tell your experiences not others

---

### Post by techfanboy81 on 2009-09-08
Ext4 have more features and generally have a better performance than ext3.

Features includes the following:  

Delayed allocation & mballoc allocator for better on-disk allocation
 
[LIST]
[*] Sub-second timestamps
[*] Space preallocation
[*] Journal checksumming
[*] Large (>2T) file support
[*] Large (>16T) filesystem support
[*] Defragmentation support
[/LIST]
[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

---

### Post by trjtrj on 2009-09-09
I have Ubuntu 9.04 and WinXP on separate hd and can use grub to boot one or the other.  I like to be able to read and write to the linux file system while in XP, so I use Ext2 Installable File System 1.11a.  That requires an inode of 128.

While installing 9.04, I used a Linux partition utility to force -I 128.  It seems that put me into Ext2 128 mode even though I had selectied Ext3.  Is I 128 not part of Ext3 ??

In later installs, if I go to Ext3 or 4 and use inodes 256, will there be a similar utility for Windows XP or 7 that is as nice as Ext2IFS ?

---

### Post by ranch hand on 2009-09-09
> **trjtrj said:**
> I have Ubuntu 9.04 and WinXP on separate hd and can use grub to boot one or the other.  I like to be able to read and write to the linux file system while in XP, so I use Ext2 Installable File System 1.11a.  That requires an inode of 128.

While installing 9.04, I used a Linux partition utility to force -I 128.  It seems that put me into Ext2 128 mode even though I had selectied Ext3.  Is I 128 not part of Ext3 ??

In later installs, if I go to Ext3 or 4 and use inodes 256, will there be a similar utility for Windows XP or 7 that is as nice as Ext2IFS ?
I think that you are making a mistake to allow Winwhatever any way to access your Linux partitions.  It is opening Ubuntu to all the holes in your MS OS.

A better way to go would be to have another partition that they can both get into (ntfs or maybe reiserfs).

---

### Post by Udayakiran on 2009-09-12
So, do you guys think its safe to use ext4 for my root partition for my ubuntu server installation?

---

### Post by moster on 2009-09-12
> **Udayakiran said:**
> So, do you guys think its safe to use ext4 for my root partition for my ubuntu server installation?

Let me quote one "old sayin". Translated, it goes something like this...
*If you are doomed to be f****, your pants will go down by themselves.*

If you want to be 100% sure, stay on ext3. If you need better performance, I would surely go on ext4 because it is visible faster. Karmic have EXT4 default, so I would say it is safe to use it.

---

### Post by david_doo on 2009-09-12
Well noted with many thanks.

---

### Post by Udayakiran on 2009-09-14
> **moster said:**
> .....
*If you are doomed to be f****, your pants will go down by themselves.*
....

:D

> **moster said:**
> Let me quote one "old sayin". Translated, it goes something like this...
*If you are doomed to be f****, your pants will go down by themselves.*

If you want to be 100% sure, stay on ext3. If you need better performance, I would surely go on ext4 because it is visible faster. Karmic have EXT4 default, so I would say it is safe to use it.

i guess i'll just take a leap of faith... and keep praying i wont meet any rocks at the bottom...

---

### Post by blackfez on 2009-09-24
Is it safe to install ext4 on a netbook with a flash drive instead of hdd?

---

### Post by moneybox123 on 2009-09-26
**Re: Ext3 and Ext4: Which file system to install?** 
Thank you. This was my big question :P

---

### Post by ausmuso on 2009-09-26
Funny how everybody seems to have gone off ReiserFS. Yes, I know Hans Reiser is/has been in trouble with the law but that doesn't detract from the fact that ReiserFS is just very good, very fast and very stable. I have been using it in Ubuntu for years, can anybody tell me why I should change?

---

### Post by Catarina on 2009-09-27
I've been using ext4 on both my Mint and Kubuntu installations, no problems, a couple of crashes here and there (and incompatibilities with Fedora's GRUB), not sure they're the file system problem or not, but it is not an impediment for a desktop user to make a change to ext4. It's faster, and it will become more and more stable as time passes by. Just wait if you don't wanna take the risk ;)

---

### Post by ranch hand on 2009-09-27
> **Catarina said:**
> I've been using ext4 on both my Mint and Kubuntu installations, no problems, a couple of crashes here and there (and incompatibilities with Fedora's GRUB), not sure they're the file system problem or not, but it is not an impediment for a desktop user to make a change to ext4. It's faster, and it will become more and more stable as time passes by. Just wait if you don't wanna take the risk ;)
Fedora does not support ext4 and so does not read your files.  You should be able to edit the menu.lst in Fedora and have it boot fine.

---

### Post by moster on 2009-09-28
> **ausmuso said:**
> Funny how everybody seems to have gone off ReiserFS. Yes, I know Hans Reiser is/has been in trouble with the law but that doesn't detract from the fact that ReiserFS is just very good, very fast and very stable. I have been using it in Ubuntu for years, can anybody tell me why I should change?

If that Reiser guy end up in prison, there will be nobody who will maintain that code. I dont know what is happening right now with Reiser4. Why is he not in kernel...

---

### Post by ranch hand on 2009-09-28
I thought that he was in prison.

---

### Post by moster on 2009-09-28
> **ranch hand said:**
> I thought that he was in prison.

I am not sure he is not. I will look it up :)

He probably have some guys maintaining code for some time, but if he go to prison for 10-20 years ReiserFS will probably end up dead.

Maybe he can code in prison? :) I would like to try Reiser4, it look very promising.

edit:[B]
Hans was sentenced to 15 years in prison, and is currently serving in Creek State Prison.[/B]

huh, what now?

---

### Post by ram2500 on 2009-09-28
double post, sorry

---

### Post by ram2500 on 2009-09-28
I have never used a machine with ReiserFS, but I have heard that it in some respects it performs better than the ext series filesystems. I don't know the particulars, why is the creator of the filesytem in prison? I was promising myself to try the filesystem one day, but I am not sure because 1) I don't endorse criminals, and 2) what about future support? 
(I don't mean to sound rude and judgemental, but I feel like I'd be in support of patronizing a criminal, and he must of done something pretty bad to be in prison for a large sum of time.) 

Anyhow, I am looking forward to the ext4fs after hearing about the real time defragmentation (even though Linux needs little or no disk optimization, my OCD personality is at rest knowing about this new feature:P and when in Windows, it's not uncommon if I defrag 2-4 times a week)

---

### Post by ranch hand on 2009-09-28
He was convicted on circumstantial evidence of killing his estranged wife.  He only got 15 to life because he showed where the body was buried.  With out that it would have been 25 to life.

I think future support looks shaky.

---

### Post by Sef on 2009-09-29
> He was convicted on circumstantial evidence of killing his estranged wife. He only got 15 to life because he showed where the body was buried. With out that it would have been 25 to life.

He pled guilty to second degree murder as part of a plea bargain, for which he was sentenced to 15 years to life.

---

### Post by moster on 2009-09-30
> **Sef said:**
> He pled guilty to second degree murder as part of a plea bargain, for which he was sentenced to 15 years to life.

Do you have any knowledge about what is happening with the code? I mean, it would be real waste. Reiser4 should go into kernel and then... everything stops..

edit:
Well, I did look around.. well, It seems that Linus and kernel hackers do not have enough faith in ReiserFS maintainers that they would do the job done and  maintain that code for prolonged time. There are other reasons too... but here is one of quote from kernel trap.
> 
A lot of other things matter.  Things like a willingness to
maintain the code after it gets merged, or at least turning
the code into something the community is willing to maintain
if the original developers stop maintaining it.

> Namesys kind of abandoned reiserfs after work on reiser4
started.  Taking in a new code base on such a track record
is not a good idea when the code is not in a shape where
the community wants to maintain it.

> 1) keep patching every time you upgrade the kernel

2) use another filesystem

3) become the new reiser4 maintainer and turn the code
    into something that Linus is willing to accept

I think that says all.

---

### Post by tekrei on 2009-10-02
Thank you for information.

---

### Post by Supersquirrel on 2009-10-02
I say Implement full support for HFS+ on linux. HFS+ is one of the better filesystems.

---

### Post by terabyte1 on 2009-10-02
I've not had any problems in ext4 or 64-bit exccept the latter getting in the way of macromedia - big deal! I get speed and very fast journaling - which makes up for it - in Karmic Koala (9.10) its the default jounaling system - since I've had a beta on my virtual box desktop without mishap. :guitar:

---

### Post by wesg on 2009-10-10
Does this opinion of ext4 change when it is not being used as a boot system? If I just want to use it for a storage RAID, would that be pretty stable?

---

### Post by ranch hand on 2009-10-10
I can't believe we are still beating this dead horse.

There is nothing wrong with ext4 that using it and not throwing a lot of ext3 files into it won't fix.  If I am moving a bunch of files to ext4 I set up a storage partition and put them there and open them from there.  Once opened and closed the buggers are ext4.

That partition sometimes gets a little fragmented because of this.  Fine with me.  Once the files are set I move them to my main OS.  The storage partition can be reformated or just deleted.

This is only needed with truely large files.  This is because ext4 will handle them better than ext3.  Ext3 HAS to break them up to get them to fit in it's "small" format.

---

### Post by dabl on 2009-10-15
Or, for 64-bit systems, you could run the only native 64-bit filesystem -- JFS.  :)

---

### Post by bcschmerker on 2009-10-26
> **ranch hand said:**
> ...There is nothing wrong with ext4 that using it and not throwing a lot of ext3 files into it won't fix.  If I am moving a bunch of files to ext4 I set up a storage partition and put them there and open them from there.  Once opened and closed the buggers are ext4.

That partition sometimes gets a little fragmented because of this.  Fine with me.  Once the files are set I move them to my main OS.  The storage partition can be reformated or just deleted....Thank you for a briefing on porting files.  My Everex currently uses ext3, and I have preplanned ext4 (unsupported on Ubuntu 8.04-LTS, as it doesn't run on Kernels prior to 2.6.27) for upgrade, as Lucid will support it from the outset (as do Jaunty and Karmic).  Ideally, the ext4 filesystem should run without problem for Ubuntu 10.04-LTS when it is released Spring 2010; I'd like to help get it there. ;-)

---

### Post by ranch hand on 2009-10-27
> **bcschmerker said:**
> Thank you for a briefing on porting files.  My Everex currently uses ext3, and I have preplanned ext4 (unsupported on Ubuntu 8.04-LTS, as it doesn't run on Kernels prior to 2.6.27) for upgrade, as Limber will support it from the outset (as do Jaunty and Karmic).  Ideally, the ext4 filesystem should run without problem for Ubuntu 10.04-LTS when it is released Spring 2010; I'd like to help get it there. ;-)
Yes, I have Hardy as my "business" OS and that is the real valid reason for not using ext4.

Ext4 will be problem free in Lounge Lizard (I like my names better) because it is trouble free now.

---

### Post by bendib on 2009-10-28
> **Demonizer said:**
> Ext4 cant be THAT bad :( . No, it's not that bad. We fedora users got a nice present in Fedora 11. It's really much faster. Go for it.

---

### Post by susanw on 2009-10-29
Thank you very much VMC I was wondering how to find out which filesystem I was on when I stumbled upon your post.
 (incidently I'm on Karmic and using ext4 and alls going very well, probably still on the beta version but update manager will be ready with an upgrade soon I expect.)

---

### Post by jheaton5 on 2009-10-29
> **ranch hand said:**
> I can't believe we are still beating this dead horse.

There is nothing wrong with ext4 that using it and not throwing a lot of ext3 files into it won't fix.  If I am moving a bunch of files to ext4 I set up a storage partition and put them there and open them from there.  Once opened and closed the buggers are ext4.

That partition sometimes gets a little fragmented because of this.  Fine with me.  Once the files are set I move them to my main OS.  The storage partition can be reformated or just deleted.

This is only needed with truely large files.  This is because ext4 will handle them better than ext3.  Ext3 HAS to break them up to get them to fit in it's "small" format.
A horse is never too dead not to beat it one more time.
Clarification: If I open a file stored on an ext3 drive and save it to my ext4 drive, will the resulting file be ext4?  e.g., an oo file on my ext3 drive opened in oo and saved to my ext4 drive.

---

### Post by chrisplymouth on 2009-10-29
EXT4 is much faster than EXT3 and its stability has improved under successive kernel releases. With Ubuntu 9.10 (if you're brave enough to install it), I recommend EXT4 as the / partition. If you are very paranoid about your data, create a separate /home partition and make it ext3.

---

### Post by dabl on 2009-10-29
> **jheaton5 said:**
> A horse is never too dead not to beat it one more time.
Clarification: If I open a file stored on an ext3 drive and save it to my ext4 drive, will the resulting file be ext4?  e.g., an oo file on my ext3 drive opened in oo and saved to my ext4 drive.

I don't believe there are any different file attributes on files saved on an ext4 filesystem, versus those saved on an ext3 filesystem or an ext2 filesystem.  The file does not know what kind of filesystem it came from or landed on (among *nix filesystems, anyway).  ;)

---

### Post by jheaton5 on 2009-10-29
> **dabl said:**
> I don't believe there are any different file attributes on files saved on an ext4 filesystem, versus those saved on an ext3 filesystem or an ext2 filesystem.  The file does not know what kind of filesystem it came from or landed on (among *nix filesystems, anyway).  ;)

So if I copy files from ext3 partition to ext4 partition all will be well?

---

### Post by ranch hand on 2009-10-29
> **jheaton5 said:**
> So if I copy files from ext3 partition to ext4 partition all will be well?
No, they will be better.

Your files will remain as ext3 until used.  When closed they will be ext4 and on a much faster system.

---

### Post by SteveMcQwark on 2009-10-29
Currently there's an issue with ext4 in Karmic, as seen in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/910overview"). [Launchpad]("https://bugs.launchpad.net/linux/+bug/453579") lists it as critical, and the problem seems pretty severe. I was going to upgrade to Karmic right away (to escape the horrors of Jaunty + Intel GMA) but with this... it might be a good idea to wait it out until it's resolved. Is there any information on this I'm missing?

---

### Post by gOLdenHaWK3D on 2009-10-30
I migrated to ext4 in karmic :) lets see what happens now :D

---

### Post by Docaltmed on 2009-10-30
> **ausmuso said:**
> Funny how everybody seems to have gone off ReiserFS. Yes, I know Hans Reiser is/has been in trouble with the law but that doesn't detract from the fact that ReiserFS is just very good, very fast and very stable. I have been using it in Ubuntu for years, can anybody tell me why I should change?

If a guy is in the middle of an extended visit at the Graybar Hotel, responding to bug reports probably doesn't top his "todo" list.

---

### Post by bruno321 on 2009-10-30
> **SteveMcQwark said:**
> Currently there's an issue with ext4 in Karmic, as seen in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/910overview"). [Launchpad]("https://bugs.launchpad.net/linux/+bug/453579") lists it as critical, and the problem seems pretty severe. I was going to upgrade to Karmic right away (to escape the horrors of Jaunty + Intel GMA) but with this... it might be a good idea to wait it out until it's resolved. Is there any information on this I'm missing?

I'm concerned about this too. I plan on clean installing Kubuntu 9.10 tomorrow, and that would keep me from going ext4.

---

### Post by Oldhacker on 2009-10-30
Attempting to do a side by side install of 9.10 on my AMD64 platform, I got as far as the partitioning where it gave me an error message stating that ext 4 would not be possible, and then it bounced back to the previous screen. There were several error messages when I tried the live CD running before install, but I neglected to write them down after agreeing to the "report bugs" on line message.

It would appear that 9.10 still has a number of bugs that require cleaning up. Happily, my 9.04 was not touched and is still operating normally.

---

### Post by dmagett on 2009-10-31
I believe this is accurate..correct me if not. A reason to stay with ext3:
I use Acronis to back up Windows systems. Acronis (using boot CD) will backup ext3 systems. I use this to backup my Ubuntu 9.04 systems. I was told it won't work on ext4.

---

### Post by nicors.net on 2009-11-01
I have been using EXT4 since May, without any problems whatsoever.

It is trivially faster then using ext3, for single user systems.

---

### Post by VMC on 2009-11-01
> **dmagett said:**
> I believe this is accurate..correct me if not. A reason to stay with ext3:
I use Acronis to back up Windows systems. Acronis (using boot CD) will backup ext3 systems. I use this to backup my Ubuntu 9.04 systems. I was told it won't work on ext4.

Acronis hasn't worked since Linux went from inodes 128 to 256. If you want a good fast backup, try either partclone.ext4 or FSARchiver. Clonezilla is also a good choice. There's a bit of a learning curve involved.

---

### Post by mikechant on 2009-11-02
Note added later in light of the following comment by worlord: 
**This post turns out not to be correct/relevant,** I've just left it (rather than deleting the text) because worlord's reply won't make sense without it!  

> I have been using EXT4 since May, without any problems whatsoever.

According to the kernel guys (and they seem to have the evidence now) this bug was introduced by some recent ext4 patches, so you wouldn't have been affected.
It looks like they are hot on the trail:
[http://bugzilla.kernel.org/show_bug.cgi?id=14354](http://bugzilla.kernel.org/show_bug.cgi?id=14354)
Look at the most recent comments (166 was most recent when I looked).

So there seem to be 3 main options at present:
[LIST=1]
[*]Don't upgrade to 9.10 until this is fixed (probably days rather than weeks)
[*]Upgrade sticking to ext3
[*]Upgrade using ext4 but run an older kernel
[/LIST]

Personally I'm going for option 1; I guess this is about #1 priority for the kernel guys.

Obviously there are all sorts of variations of upgrade/reinstall involving various new or existing filesystems, and I've seen the comments about this problem probably not applying to filesystems which have been upgraded from ext3 to ext4, but I wouldn't like to trust this - it might just occur in different circumstances. So I personally wouldn't use any ext4 filesystems (however they were created/converted) with this kernel until it's fixed.

Further note:
Slightly confused by the kernel versions reffered to in the link above. I *think* what they mean is that this problem applies to the later versions of the 2.6.31 kernel (including the one in Ubuntu 9.10) and also to the 2.6.32 release candidate, but not to earlier releases of 2.6.31. But some of the comments might mean it's only in 2.6.32...

Maybe someone with more kernel knowledge could give their interpretation?

---

### Post by WorLord on 2009-11-02
> **mikechant said:**
> Slightly confused by the kernel versions reffered to in the link above. I *think* what they mean is that this problem applies to the later versions of the 2.6.31 kernel (including the one in Ubuntu 9.10) and also to the 2.6.32 release candidate, but not to earlier releases of 2.6.31. But some of the comments might mean it's only in 2.6.32...

Maybe someone with more kernel knowledge could give their interpretation?

Sure.

The link you posted has to do with the 2.6.32.rc2 and above kernels, and absolutely nothing to do with the Ubuntu bug referenced in this thread.  It looked like the two bugs were related, but in reality, the kernel bug happens with a kernel 9.10 doesn't have, and under *completely* different circumstances.  

The Kernel bug has since been unlinked from the Launchpad bug, and efforts to replicate the 9.10 bug are still ongoing (with no luck - I personally have installed 9.10 on fresh ext4 file systems on two computers now and run tests, but nothing is wrong.)

---

### Post by mikechant on 2009-11-03
Thanks for clarifying that, worlord.
I guess I'll go ahead with a clean ext4 install (as usual, leaving my existing previous release undisturbed!) and do some testing of my own.

---

### Post by the_guv on 2009-11-03
clean Ext4 install works a charm.  

am waiting before doing the upgrade from Jaunty Ext3 to Koala Ext4 because I'm away from my backup box, have terrible connectivity here (temp in Middle East) and can't afford to lose this machine.

.. surely best to play safe and wait.

---

### Post by adalal on 2009-11-04
ext4 is faster.... worth a go...

---

### Post by ssdt on 2009-11-06
Thanks for such a helpful post.

---

### Post by freackout on 2009-11-07
> **vigyani said:**
> Hi

It would be really nice if you can provide references and links to substantiate the claims made in this post.

i played with ext4 a while back (when it became part of kernel), i loved the speed of it whilst also running an ext3 stipped raid on other drives, it was superfast unbelievable at copying over large amounts of files ect, using the ubuntu alternate installs available at the time, yes grub is partly effected in this instance ie needs grub2, however pmagic 4.5 will also mount and fix multiple grub problems you may have, with its supergrub option so yes give it a whirl. just brilliant.

---

### Post by sparkyguy on 2009-11-07
Not sure where to post, but after upgrading to Karmic and subsequently updating all my apps, messing with my wireless driver (unfriendly but eventually got it to work) I then discovered by backup/imaging program of choice (True Image) recognizes ext3 but not ext4 unless I do a total sector-by-sector image. This will create an image file the size of my entire HD on each session, including unused space (big waste and lots of time). I can come up with enough temporary space to do this, but only ONCE. But what's the easiest way to backup, reformat back to ext3, then reinstall what I have created today without actually reinstalling all my apps from scratch? I'm a relative newbie (few months) with Ubuntu (originally installed Hardy then upgraded to Karmic). Suggestions to minimize my pain? I've found lots of links with upgrades from ext3 to ext4, but not much useful to go the other way around.

---

### Post by Deicider on 2009-11-08
so this means ext4 is cool from now on?

---

### Post by WorLord on 2009-11-10
> **Deicider said:**
> so this means ext4 is cool from now on?

I'm giving it a tentative green light for my personal needs, yes.

I'm still paying attention to the LP bug, but the longer it goes on, the less likely I think I'll find a systemic code-related bug there; SO few people are having this issue it could (as has been suggested before) well be RAM or cable problems.  My own efforts to replicate have been utterly fruitless on (now) three machines, of different architectures (ATA and SATA).

I also tend to think that with the amount of attention this bug has gotten, if there WERE a code-related issue with the kernel there, it would have been at least found by now.  Still... nada, there doesn't even appear to be a way to systemically and repeatedly create the issue.

*shrug*  

I think that's as "good to go" as it gets, for now.  :popcorn:

---

### Post by Dubbayoo on 2009-11-10
Wait, so if you're going to install 64-bit you get JFS instead of ext4 or is there a choice? A suggested choice?

---

### Post by Sef on 2009-11-10
> Wait, so if you're going to install 64-bit you get JFS instead of ext4 or is there a choice? A suggested choice?


Unless you have some reason for using another file system, ext4 should work just fine on your system.

---

### Post by kio_http on 2009-11-11
I had jaunty and now Karmic on ext4 and don't seem to have any problems except windows and OS X don't read it.

The speed increase is evident thought so I'm sticking to ext4.:KS

---

### Post by florus on 2009-11-15
I am confused by statements in this thread that you should not copy ext3 files to an ext4 partition (post 187). Surely if you write a file to an ext4 partition, it will become an ext4 file. I can copy files between FAT, NTFS and ext3 with no problem.
The reason for my concern is that I want to copy my Firefox and Thunderbird profiles from a ext3 Jaunty computer to a fresh install ext4 Karmic computer. Would this really cause problems?

---

### Post by Zoot7 on 2009-11-15
I'm using ext4 for both my / partition and /home partition, and also on 2 external 1TB hard drives at the moment.
I find there's a big speed increase in copying lots of small files, and fsck completes a LOT faster.

---

### Post by Sef on 2009-11-15
> I am confused by statements in this thread that you should not copy ext3 files to an ext4 partition (post 187). Surely if you write a file to an ext4 partition, it will become an ext4 file. I can copy files between FAT, NTFS and ext3 with no problem.
The reason for my concern is that I want to copy my Firefox and Thunderbird profiles from a ext3 Jaunty computer to a fresh install ext4 Karmic computer. Would this really cause problems?

It should not cause problems.

Post 187 does not say anything about your worry.  Here is post 187:

> I can't believe we are still beating this dead horse.

There is nothing wrong with ext4 that using it and not throwing a lot of ext3 files into it won't fix. If I am moving a bunch of files to ext4 I set up a storage partition and put them there and open them from there. Once opened and closed the buggers are ext4.

That partition sometimes gets a little fragmented because of this. Fine with me. Once the files are set I move them to my main OS. The storage partition can be reformated or just deleted.

This is only needed with truely large files. This is because ext4 will handle them better than ext3. Ext3 HAS to break them up to get them to fit in it's "small" format.

---

### Post by florus on 2009-11-15
Thanks, Sef.

It was the statement "There is nothing wrong with ext4 that using it and not throwing a lot of ext3 files into it won't fix. If I am moving a bunch of files to ext4 I set up a storage partition and put them there and open them from there." which worried me. The implication being that it was dangerous to copy a lot of ext3 files into an ext4 partition.

---

### Post by ????123856 on 2009-11-15
If you insist feel free to choose either but don't store crucial data on ext4 partition with jaunty or bellow!

---

### Post by HeadHunter00 on 2009-11-22
I have been using ext4 for about 6 months now. Still didn't get any bugs stated in this thread. I also noticed that it is faster in file processing.

---

### Post by parkland on 2009-11-24
I'm sorry, but as of now, I do not trust ext4.

Out of 3 computers here, I upgraded every one to 9.10 / ext4, and only one of them has not completely crashed yet, and I barely use it.

I think ext4 has been "laboratory" tested, but not "real world" tested....

I can not believe they let something so buggy and undependable get released to people who depend on their computers...

What the heck is this; Microsoft?

---

### Post by bcschmerker on 2009-11-24
> **SteveMcQwark said:**
> Currently there's an issue with ext4 in Karmic, as seen in the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/910overview"). [Launchpad]("https://bugs.launchpad.net/linux/+bug/453579") lists it as critical, and the problem seems pretty severe. I was going to upgrade to Karmic right away (to escape the horrors of Jaunty + Intel GMA) but with this... it might be a good idea to wait it out until it's resolved. Is there any information on this I'm missing?Thanks for the heads up; if everybody is on the ball, fixes will be applied across Karmic and Lucid when they're approved for RTM on Karmic.

---

### Post by kraus3742 on 2009-11-25
I have been using ext4 file format since Jaunty release on my secondary partition and I switched to ext4 on my OS partition at the release of Karmic.  I updated to Karmic OS, Ext4 file system and Grub 2.0 manually and have not currently experienced any issues with ext4 file system.

---------------------------------------------------------------------------------------------
Join the Revolution - Do a friend a favor and show them a world without Windows

---

### Post by parkland on 2009-11-25
I'm on my 6th fresh install of 9.10 & ext4 on one pc.

I guess I'm waiting for a fix in the updates....

Try moving 700mb files around on the disk....

I downloaded a 700mb image today, and it was instantly corrupted.

I also have 300+ 700mb-1.4gb movies that are all getting corrupt day by day.

---

### Post by l0r3zz on 2009-11-25
Well my Karmic install just crashed and my ext4 partitions are corrupted beyond repair. Seems like this happened within hours of me taking the latest kernel update. which I think is vmlinuz-2.6.31-15-generic-pae, but not sure. Anyway, I took the update, rebooted and everything was fine. I continued to use it. Started up a torrent download and left it for a few hours, came back and the screen was blank and the system was not responsive, eventually I had to power cycle (HP NC6910) and the system would not boot up. This is a brand new 320GB drive, but what is suspicious is that my /boot partition was ext2 (just for safety sake) and that partition is readable, but all the others are ext4 and they are hosed.  I've only been running for a couple of days so I haven't lost too much work, one revision in a project that I'm working on. Not sure if I'm going to re-install to ext4 or just reinstall to ext3 where I feel safe.  Any suggestions from anyone? Any way I can repair these partitions? Here are the errors from dmesg.

[FONT="Courier New"][/FONT]
[  368.586699] EXT4-fs (sda5): Couldn't mount because of unsupported optional features (40000000)
[  383.993105] EXT4-fs (sda8): Couldn't mount because of unsupported optional features (2000)

---

### Post by Gooorn on 2009-12-01
Hi. Can someone pls comment on this article
```
http://ext4.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu.
```

I have installed Karmic on 3 different laptops (Celeron, Pentium M and Atom) with Ext4 and no problems. Still I don't have nerves to install Karmic on my main business laptop due to this ext4 issues which should never have happened in Ubuntu as a Linux flagship distro.

Thanx

Sinisa Perovic

---

### Post by julianb on 2009-12-01
> Still I don't have nerves to install Karmic on my main business laptop due to this ext4 issues which should never have happened in Ubuntu as a Linux flagship distro

Ubuntu is the most popular Linux distro, but it still has tons of imperfections, which is what you get when you deal with computers. Windows has its own glaring flaws, osX has things it just won't do, etc.

Linux's problem is that in some instances, "it just works" is not true - sometimes it just works IF you know more about computers than 90% of the computer-using population and spend a moment or two fixing stuff. Otherwise it just breaks.

But linux developers are making huge strides in this area and Ubuntu is impressive in its capacity to bring linux to non-experts.

---

### Post by Gooorn on 2009-12-01
> **julianb said:**
> Ubuntu is the most popular Linux distro, but it still has tons of imperfections, which is what you get when you deal with computers. Windows has its own glaring flaws, osX has things it just won't do, etc.

Linux's problem is that in some instances, "it just works" is not true - sometimes it just works IF you know more about computers than 90% of the computer-using population and spend a moment or two fixing stuff. Otherwise it just breaks.

But linux developers are making huge strides in this area and Ubuntu is impressive in its capacity to bring linux to non-experts.

Agree. I'm with Ubuntu almost exclusively from 5.10 release. I was fascinated with every new release how great it is and above all how great the community behind it. This fascination is what made Ubuntu so popular for all the good reasons.
Nevertheless I don't believe that things we had with Jaunty + Intel GMA and now Karmic + Ext4 will bring more people under Ubuntu flag. That was my comment.
This all came when we start talking about Ubuntu looking better than MAC OSX or being better than Vista. For my point of view it was all that staring with 8.04 LTS onwards when the goals were somewhat different.

Still, I'm in love with this community and with Ubuntu which I'm supporting humbly when and where I can. Don't take my criticism for anything but intention to make Ubuntu even better.

---

### Post by P01 on 2009-12-02
Is better than Vista,and this comunity is great.I use Ext3,and no problems.

---

### Post by Bobhuber on 2009-12-04
I've been using Karmic 9.10 for some time with an Ext3 file system and decided to upgrade (change) to Ext4.Every thing went fine as far as the change is concerned and the etx4 system seemed to be stable.HOWEVER the most popular programs I use (Firefox as an example) were much slower on my system. I understand (after reading several articles on the subject) that this is attributed to the way the program(s) are written.Needless to say I've repartitioned to etx3 and restored from a backup that was made before the change.
Untill the software catches up with the operating systems I highly recommend sticking with the ext3 file system.If you manually partition the drive even a fresh install of Karmic loads just fine using etx3. I'm running Karmic (64bit) on an AMD 64 dual core processor with 3 gig of ram and a 265 gig HD.

---

### Post by Piscium on 2009-12-04
I have been using ext4 since jaunty. No problem. Works great.

---

### Post by mikechant on 2009-12-05
I've just been doing some tests. I set up new ext3 and ext4 partitions of about 100Gb each, copied 4 dvd iso files (1.3-3.0Gb each) from an existing ext3 partition to the new ext3 partition, then moved them (cut/paste) from the new ext3 partition to the new ext4 partition and back again.
I did shasum -b checksums on all 4 files at every stage, and all the checksums were identical. 
I did the full test both on 9.04 and 9.10 and both passed.
Personally, on my hardware, I'm becoming more trusting of ext4 as time passes. I wonder if the people who are having the problems have particular hardware in common?
  I'm currently keeping my most important data partitions as ext3 but switching everything else, like root filesystems etc. to ext4.  But I think pretty soon I'll take a final ext3 backup of my crucial 300Gb of data and switch totally to ext4.
I generally seem to get about a 25% performance improvement (e.g. in boot time, sequential file read) from ext4 vs ext3.

---

### Post by Zoot7 on 2009-12-05
> **mikechant said:**
> I generally seem to get about a 25% performance improvement (e.g. in boot time, sequential file read) from ext4 vs ext3.
Ditto.

One thing I notice too, is moving large amounts of small files is considerably faster.

---

### Post by etitor on 2009-12-06
We have two Ubuntus at home: mine is a Karmic on ext4, my wife's is a Karmic on ext3 (I did a fresh install on mine and an update on hers).

Stability and speed are a great plus on my ext4 system.

Only trouble so far: our domestic net. My exports to her computer are not seen by her Karmic. I can see and access her (ext3) exports from my (ext4) system, but not the other way around. So apparently you can't deal with ext4 systems from ext3 systems.

---

### Post by Demosthenesaus on 2009-12-07
I have Ext4 running in an encrypted logical volume on my wifes laptop, should I be concerned?  No problems so far but a little worried.  I also used Ext4 on a recent backup USB external drive, should I be concerned?

Can I downgrade to Ext3?

---

### Post by Marvin666 on 2009-12-07
Could I have jaunty running off an ext4 partition, and /home on an ext3 partition without any troubles?

---

### Post by atoztoa on 2009-12-08
Copying large files in NTFS or FAT32 partitions to ext4 is much slower...

What exactly is the purpose Karmic has ext4?

---

### Post by julianb on 2009-12-08
> Could I have jaunty running off an ext4 partition, and /home on an ext3 partition without any troubles?

I think it's very likely you can do it, trouble-free. The only way to be sure is to try it. So if you have a good reason you want to go that route, then try it out.

---

### Post by Demosthenesaus on 2009-12-08
Is there any compelling reason to adopt EXT4?  I'm using Jaunty on a netbook so will stick with EXT3, however I have adopted EXT4 with full disk encryption on a Karmic laptop.

---

### Post by gadolinio on 2009-12-09
> **akrep55tr said:**
> thank you very much. This was a big question in my mind.
+1

---

### Post by Demosthenesaus on 2009-12-11
I opted instead on the 9.04 netbook to use EXT3 on /boot and EXT4 in /root - seems to work fine.

---

### Post by phillw on 2009-12-14
If you're on Grub2, updating to ext4 from ext3 is painless and quick.

this thread is upside down (read my sig about the problems we had with their tech support bork the forum & backup)

[http://www.vpolink.com/showthread.php?t=365](http://www.vpolink.com/showthread.php?t=365)

Painless :-)

Phill.

---

### Post by tpollak on 2009-12-14
Finally an explanation why I can not boot 9.10 as delivered with grub 2, I selected ext4 for my file ssystem.
grub generates a grub.cfg with ext2 and does not find the disk, changing insmod to ext4 gives can not find file and that is because grub 2 does obivously not support ext4.

Why is there no warning in the installation process on the Live CD ...

---

### Post by phillw on 2009-12-14
> **tpollak said:**
> Finally an explanation why I can not boot 9.10 as delivered with grub 2, I selected ext4 for my file ssystem.
grub generates a grub.cfg with ext2 and does not find the disk, changing insmod to ext4 gives can not find file and that is because grub 2 does obivously not support ext4.

Why is there no warning in the installation process on the Live CD ...

My system is 100% ext4 - Grub2 supports ext4, grub legacy *can* support it with a patch, or several.

I didn't know that boot loading programme had a partitioning and formatting routine written into it. - That is done by the likes of Gparted when you do your installation. 

Sorry if I sound bemused, but I've not come across this before - Can you post your ```
df -T
``` to show the ext2 area that Grub2 creates ?

Thanks,

Phill.

---

### Post by kjtruitt on 2009-12-14
Gateway solo 9500, 750mhz, 384mb ram, 10-gig ibm hd (10 years old):

all attempts to install xubuntu karmic with ext4 resulted in no graphics and a login command line only, or a freezup of the display before it had completed loading, with a message that the hal daemon was not running, or . (it was -- I got a process number for it when I 
reinstalled it but still startx failed).  

Using ext3 solved all the problems.

---

### Post by Orographic on 2009-12-16
I've been using Ext4 on all partitions since the end of October with no problems. I did have one crash whilst downloading a large iso but it seems it was related to the screen going into sleep mode. I turned sleep mode off a month ago and no problems since. I've downloaded dozens of large iso files, copied them to usb keys, usb external drives etc since late October and no probs at all. So, maybe it is specific hardware?

Mine is:

Gigabyte 945GZM-S2 with onboard graphics.
E2200HD BenQ monitor
2G DDR2 667mhz ram

I do have a plenty of EXT4 images made from Clonezilla and also an EXT3 image if I need it. Clonezilla is certainly recommended by me. I follow the standard image creation and restore process in the help file on their site and it has worked every time - about fifty times in fact. Its slightly trickier than say Acronis at first (which I also use often) but its free and very reliable and always being updated with the latest drivers etc. Give yourself a week or two with it and its so easy, you can use it without thinking - almost.

---

### Post by Orographic on 2009-12-16
> **atoztoa said:**
> Copying large files in NTFS or FAT32 partitions to ext4 is much slower...

What exactly is the purpose Karmic has ext4?

I also haven't found this on my machine. I copy large files in NTFS and FAT32 often and have found them to be much faster.

---

### Post by jimpr13 on 2009-12-16
NTFS yes is faster but fat32 isn't the same

---

### Post by ridsacun on 2009-12-17
> **jimpr13 said:**
> NTFS yes is faster but fat32 isn't the same
I've been using Ext4 on all partitions since the end of October with no problems. I did have one crash whilst downloading a large iso but it seems it was related to the screen going into sleep mode. I turned sleep mode off a month ago and no problems since. I've downloaded dozens of large iso files, copied them to usb keys, usb external drives etc since late October and no probs at all. So, maybe it is specific hardware?

---

### Post by iTheBadGuy on 2009-12-21
I'm looking for better performance. My PC specs are: 

AMD Sepron(tm) Processor 3000+
1.81GHz 512MB of RAM (DDR1). 
Although windows says it's only 384MB(wtf?)

Video card is a Nvidia Gforce 6100 nForce 405, 256MB of RAM (It's Integrated RAMDAC)

You can see why I'm looking for a OS that performs faster under my circumstances.. I also would like to mount my NTFS drive to move all my data from the NTFS drive to the EXT3/4 drive. So which is better for me?. EXT4 or 3?.

---

### Post by oygle on 2009-12-23
I have just done a fresh install of 9.10 , and then saw some posts about EXT4 is installed by default.

Is it a "safe" filing system ? I don't want to transfer my backup data files, unless I'm 100% certain that EXT4 will not cause data loss.

Oygle

---

### Post by bcn17 on 2009-12-24
> **oygle said:**
> I have just done a fresh install of 9.10 , and then saw some posts about EXT4 is installed by default.

Is it a "safe" filing system ? I don't want to transfer my backup data files, unless I'm 100% certain that EXT4 will not cause data loss.

Oygle


I have been using ext4 since 9.04 and have not had any problems what so ever. I run a SSD eee pc, and 2 desktops with a few HDs each. I wouldn't expect any problems. Depending on the necessity of your data though a backup in ext3 wouldn't be a bad idea. You should have 2 copies with anything that important anyway. Might as well diversify your filesystems.

---

### Post by ossimusraadicus on 2009-12-24
Can anyone tell me where in the Karmic Koala installer is there an option to install ext3 instead of ext4?

I had written a longer post describing what I'm trying to do...but the Ubuntu forums timed me out and when I went to post, my whole post was deleted!  Frustrating >:(

Anyway, I've been looking around in the installer and in the forum here, and all I can see are ideas on downgrading from ext4 to ext3, instead of just installing ext3 from the actual Ubuntu Karmic Koala installer.

Whoever helps is of the awesome.

---

### Post by Zoot7 on 2009-12-24
> **ossimusraadicus said:**
> Can anyone tell me where in the Karmic Koala installer is there an option to install ext3 instead of ext4?
If you set up the partitions manually you can select the filesystem. Ext3 and Ext4 are choices of many.

---

### Post by ivyrose on 2009-12-24
helo.. im juz new hir in dis forum:KS

---

### Post by n4pgw on 2010-01-03
It has been over 6 months since the original post on the topic of ext3 and ext4.  9.10 defaults to ext4, but I read where it is 'experimental'.  Since it is an old thread I must ask now for the year 2010, Which is safer - ext3 or ext4?  

Also, can a used partition be reformatted to ext3 without losing data?

Thank you
Buck

---

### Post by Zoot7 on 2010-01-03
> **n4pgw said:**
> It has been over 6 months since the original post on the topic of ext3 and ext4.  9.10 defaults to ext4, but I read where it is 'experimental'.  Since it is an old thread I must ask now for the year 2010, Which is safer - ext3 or ext4?  

Also, can a used partition be reformatted to ext3 without losing data?

Thank you
Buck
Ext3 has been around a very long time now, so it's pretty tried, tested and stable. The odds of it letting you down are slim to nil.
Ext4, I've read about issues but I haven't had any myself. I use Ext4 for my system partition, but I still use Ext3 as my home partition and also on some external hard drives as I don't like trusting a lot of data to a relatively new file system.
That said though, I gather a lot of the old problems associated with Ext4 have been fixed, and what's more a good portion of the popular distros default to installing on an Ext4 partition.
It's up to you really, but if you *really* want to be safe, stick with Ext3. ;)

As for reformatting a partition back to Ext3 from Ext4, I don't think it's possible. It is however possible to go the other way, but not back as far as I know.

---

### Post by oygle on 2010-01-05
> **bcn17 said:**
> I have been using ext4 since 9.04 and have not had any problems what so ever. I run a SSD eee pc, and 2 desktops with a few HDs each. I wouldn't expect any problems. Depending on the necessity of your data though a backup in ext3 wouldn't be a bad idea. You should have 2 copies with anything that important anyway. Might as well diversify your filesystems.

Okay, thanks for your reply. I do have an external HDD for backup, so that should be EXT3 no doubt.

Reading other posts in this thread, quite a few advise it is safer to use EXT3 as your filing system. I did not see any option in the Karmic installation, where it would let me choose either EXT3 or EXT4. At his stage in the Karmic installtion (everything updated, but no data on the HDD as yet), it would still be better if I made it EXT3. However, I see I cannot go from EXT4 ==> EXT3. so my only option is to re-install, after I reformat the HDD to EXT3.

Oygle

---

### Post by Zoot7 on 2010-01-05
> **oygle said:**
> Okay, thanks for your reply. I do have an external HDD for backup, so that should be EXT3 no doubt.

Reading other posts in this thread, quite a few advise it is safer to use EXT3 as your filing system. **I did not see any option in the Karmic installation, where it would let me choose either EXT3 or EXT4.** At his stage in the Karmic installtion (everything updated, but no data on the HDD as yet), it would still be better if I made it EXT3. However, I see I cannot go from EXT4 ==> EXT3. so my only option is to re-install, after I reformat the HDD to EXT3.

Oygle
When you're setting up the partitions, select "Manual", you'll get the option to choose the filesystem, mountpoint etc.
It's actually best to probably set up the partitions with something like Gparted prior to actually installing anything IMO.

---

### Post by oygle on 2010-01-06
> **Zoot7 said:**
> When you're setting up the partitions, select "Manual", you'll get the option to choose the filesystem, mountpoint etc.

I'm able to choose EXT3, but that leaves no room for swap. What mountpoint should I define for the primary partition, and how big should the swap size be ?

It's a 500Gb hard drive. The 'manual' part of the install says it is a 500105 Mb size, and 10884Mb used, that is, with just primary - /dev/sda1 defined.

> **Zoot7 said:**
> 
It's actually best to probably set up the partitions with something like Gparted prior to actually installing anything IMO.

I tried that with Karmic, and it wouldn't let me. It started to do the partitioning, and then failed each time.

Thanks,

Oygle

---

### Post by Sef on 2010-01-06
> I...how big should the swap size be ?Swap should be no bigger than 1 gb.  

> I'm able to choose EXT3, but that leaves no room for swap. What mountpoint should I define for the primary partition, ...?

It's a 500Gb hard drive. The 'manual' part of the install says it is a 500105 Mb size, and 10884Mb used, that is, with just primary - /dev/sda1 defined.I would partition it like this (single boot):

1st partition: 8-10 gb;  mountpoint: root;  file system: ext3 or ext4

2nd partition: 1 gb;      mountpoint: ----;    file system: swap

3rd partition: all;          mountpoint: home; file system: ext3 or ext4

**Back up** all files before partitioning.

_Update_: 

> I tried that with Karmic, and it wouldn't let me. It started to do the partitioning, and then failed each time.

Were you using the GParted Live CD?

I have used ext 4 since Jaunty and have never had a problem with it.

---

### Post by oygle on 2010-01-06
> **Sef said:**
> Swap should be no bigger than 1 gb.

Oops, I read [here](https://help.ubuntu.com/community/SwapFaq) that it should be twice the physical RAM, and as my RAM is 4 Gb, I made the swap size 8Gb. So, swap seems way too big , and an overkill, especially as it's a 64 bit computer with dual processors, etc.

The Karmic install has started now, unfortunately, but no doubt I can 'resize' after the install finishes.

> **Sef said:**
> 
I would partition it like this (single boot):

1st partition: 8-10 gb;  mountpoint: root;  file system: ext3 or ext4

2nd partition: 1 gb;      mountpoint: ----;    file system: swap

3rd partition: all;          mountpoint: home; file system: ext3 or ext4

**Back up** all files before partitioning.

Okay, thanks for those figures. I'll try and resize to those after the install. Yes, everything is backed up.

> **Sef said:**
> 
Were you using the GParted Live CD?

I had installed GParted to karmic, and was using that. I guess it didn't wanto to 'clobber' itself, and I should have run GParted from the CD.

> **Sef said:**
> 
I have used ext 4 since Jaunty and have never had a problem with it.

I hear conflicting reports on EXT4. Some people have no problems, others do. I just thought that as this HDD was going to be used for all my data, then I shouldn't use EXT4, as there were reports that it was unstable at times.

Thanks,

Oygle

---

### Post by Sef on 2010-01-07
> Oops, I read [here]("https://help.ubuntu.com/community/SwapFaq") that it should be twice the physical RAM, and as my RAM is 4 Gb, I made the swap size 8Gb. So, swap seems way too big , and an overkill, especially as it's a 64 bit computer with dual processors, etc.

When ram was much less, then 1.5 times ram for swap was what was recommended.   Unless you do something extremely graphics intensive, 4 gb ram will be more than enough.

---

### Post by Zoot7 on 2010-01-07
> **oygle said:**
> I'm able to choose EXT3, but that leaves no room for swap. What mountpoint should I define for the primary partition, and how big should the swap size be ?

It's a 500Gb hard drive. The 'manual' part of the install says it is a 500105 Mb size, and 10884Mb used, that is, with just primary - /dev/sda1 defined.



I tried that with Karmic, and it wouldn't let me. It started to do the partitioning, and then failed each time.

Thanks,

Oygle
Having a big swap partition is largely pointless given that with a large amount of RAM you won't be using the swap all that much. As Sef said, 1GB is plenty.
The Karmic partitioner was touted to have problems, I'd try the Gparted liveCD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
I suggest you make an extended partition and stick the swap and Ext3 partition inside in it. And as for a mount point you'd select **"/"**.

---

### Post by n4pgw on 2010-01-07
> **Zoot7 said:**
> Having a big swap partition is largely pointless given that with a large amount of RAM you won't be using the swap all that much. As Sef said, 1GB is plenty.


Other than the use of extra hdd space, is there a penalty for a larger than needed swap space?

There are rare occassions that I edit graphics, but I setup a 10 GB swap space on the internal drive just to make sure I don't fall short.  As far as resources goes, that 10 GB is not missed.

(I have 2GB internal RAM on 32 bit processor)

---

### Post by oygle on 2010-01-07
> **Zoot7 said:**
> 
The Karmic partitioner was touted to have problems, I'd try the Gparted liveCD. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
I suggest you make an extended partition and stick the swap and Ext3 partition inside in it. And as for a mount point you'd select **"/"**.

I used GParted from the (Ubuntu Karmic) Live CD, and because there was an extra partition already added, I couldn't get it to actually 'move' all or part of a partition to another partition. As there was no data on the hdd, I opted for a fresh Karmic install, where I can manually specify exactly what the partitions will be. Here is the setup now, possibly a slight overkill on swap, at 2Gb, but better (less than) it was before, and I have the extra partition, mounted at /home, as Sef suggested.

Thanks,

Oygle

---

### Post by Zoot7 on 2010-01-07
> **n4pgw said:**
> Other than the use of extra hdd space, is there a penalty for a larger than needed swap space?
Not that I know of, no.

> **oygle said:**
> I used GParted from the (Ubuntu Karmic) Live CD, and because there was an extra partition already added, I couldn't get it to actually 'move' all or part of a partition to another partition. As there was no data on the hdd, I opted for a fresh Karmic install, where I can manually specify exactly what the partitions will be. Here is the setup now, possibly a slight overkill on swap, at 2Gb, but better (less than) it was before, and I have the extra partition, mounted at /home, as Sef suggested.
Good that you're sorted, I wouldn't worry about the swap size. ;)

---

### Post by running_rabbit07 on 2010-01-07
Will Ubuntu run on NTFS?

---

### Post by michy99 on 2010-01-08
NTFS does not support linux file permissions. You can use it for a data partition for files that you want to access from Windows, but not for a system partition.

---

### Post by mikechant on 2010-01-08
Sef said:
> Swap should be no bigger than 1 gb. 

I would just qualify this by saying that it's always been my understanding that if you want to use the 'hibernate' function you need a swap space at least equal to your RAM size to be sure the hibernation will work.

---

### Post by running_rabbit07 on 2010-01-08
> **mikechant said:**
> Sef said:


I would just qualify this by saying that it's always been my understanding that if you want to use the 'hibernate' function you need a swap space at least equal to your RAM size to be sure the hibernation will work.

I agree. Being most of my HDDs are larger than 200 gigs, I use 3-5 gigs for Swap.

---

### Post by olbaldy77 on 2010-01-14
Hi, I'm in the process of building a new computer and I've loved using Ubuntu on my Dell Dimension 8200 (circa last millennium :().

I plan on gaming (WoW, TF2, L4D, etc.) with Wine, can I install those programs on a disk formatted in Ext3 or Ext4? Are there any pitfalls I should be on the lookout for?

I would be eternally grateful for any advice. Thank you.

---

### Post by Sef on 2010-01-15
> Sef said:
 	Quote:
 	 	 		 			 				Swap should be no bigger than 1 gb. 			 		 	 	 
I would just qualify this by saying that it's always been my understanding that if you want to use the 'hibernate' function you need a swap space at least equal to your RAM size to be sure the hibernation will work.

I did check on that, and that is true if one uses hibernate.  Make it equal to your ram.

---

### Post by DarinB on 2010-01-15
one interesting thought maybe some of the problems with ext 4 also stem from the grub 2 upgrade. I am not very knowledgeable about the real details but it just seems that too many changes were made in karmic to ever be really tested. i did hear that Linus Torvalds said that "ext 4 is crap" and we might as well go back to ext 2!!!!!

---

### Post by n0dix on 2010-01-16
I recommend you to install Ext4, is faster than Ext3 for specific things.

---

### Post by wedgehead on 2010-01-23
> **dmagett said:**
> I believe this is accurate..correct me if not. A reason to stay with ext3:
I use Acronis to back up Windows systems. Acronis (using boot CD) will backup ext3 systems. I use this to backup my Ubuntu 9.04 systems. I was told it won't work on ext4.

Besides Acronis, there are other Windows imaging softwares that only recognize ext3, such as Norton/Symantec Ghost products.  If you're a person with a dual-boot machine, it's nice to be able to image _all_ of your partitions while in a Windows mode.  (I'm rarely in a Windows mode). So, keeping with the proven ext3 allows you to use certain free imaging software which includes Macrium Reflect, and certain Paragon Drive Backup products.  These freeware products include a (Linux-based) boot CD, in case your machine is super-hosed such that you can't boot into Windows).  IMO, it's valuable to have confidence that the image you just created will restore when you need it, and will restore easily.  The command-line "solutions" for imaging don't give me that confidence.

---

### Post by Sef on 2010-01-24
> Besides Acronis, there are other Windows imaging softwares that only recognize ext3, such as Norton/Symantec Ghost products. If you're a person with a dual-boot machine, it's nice to be able to image _all_ of your partitions while in a Windows mode. (I'm rarely in a Windows mode). So, keeping with the proven ext3 allows you to use certain free imaging software which includes Macrium Reflect, and certain Paragon Drive Backup products. These freeware products include a (Linux-based) boot CD, in case your machine is super-hosed such that you can't boot into Windows). IMO, it's valuable to have confidence that the image you just created will restore when you need it, and will restore easily. The command-line "solutions" for imaging don't give me that confidence.

I use [clonezilla]("http://clonezilla.org") for imaging my hard drive; it will image both Windows and Linux, including ext4.

For paritioning, I prefer [GParted]("http://gparted.sourceforge.net"), which is a gui partitioner.

---

### Post by -EvilGrin- on 2010-01-25
Is there a way to switch filesystem (from ext2 to ext3) like you can do on windows, without reinstalling system? Cos I'd like to switch partition with system to ext3.

---

### Post by mikechant on 2010-01-26
> Is there a way to switch filesystem (from ext2 to ext3) like you can do on windows, without reinstalling system? Cos I'd like to switch partition with system to ext3

See this FAQ:
[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

Tells you how to switch ext2->ext3 and ext3->ext2 without reformatting. Basically you're just creating/removing the journal.

You can do the same sort of thing with ext2/3->ext4 using other tune2dfs commands but in that case you won't get the full benefits of ext4.

---

### Post by alpha-buntu on 2010-01-27
I tried serveral tools to acces ext4 partitions from windows. None worked. For me, the switch to ext4 was to soon.

Also, well known tools for partition cloning, imaging and so on do not work with ext4. If I had known this a bit earlier, I would have not used ext4.

---

### Post by Sef on 2010-01-27
>  Also, well known tools for partition cloning, imaging and so on do not  work with ext4. If I had known this a bit earlier, I would have not used  ext4.

Clonezilla images the drive just fine.

GParted partioned my hard drive into ext4 without a hitch.

---

### Post by ned903 on 2010-02-01
I have duall boot with xp working terrifically with FAT32 filesystem, mounting is also easier since Red Hat, now Ubuntu does it all on 32 bit processor and a 32 bit filesystem,

yup,

ned:popcorn:

---

### Post by themarker0 on 2010-02-01
Not meaning to necro post, but is ext4 stable now? I am hoping to upgrade my system with it.

---

### Post by oshunluvr on 2010-02-02
No - kernel "regression" has slowed it to a virtual crawl. Personally, I'm sticking with reiserfs for the foreseeable future.

---

### Post by Sef on 2010-02-02
> Not meaning to  necro post, but is ext4 stable now? I am hoping to upgrade my system  with it.  You are not necro posting.  In fact, you are about 12 months short of it.    

Ext4 has worked fine with me, and the majority of users.   I have used it since Jaunty.  Before installing, **back up** your **data**.

---

### Post by Deer Hunter on 2010-02-03
> **michy99 said:**
> NTFS does not support linux file permissions. You can use it for a data partition for files that you want to access from Windows, but not for a system partition.

Thank you Sir!!  That is a question that I have been wondering about, as I am planning to daul-boot XP and Karmic, with a separate data partition accessible by both OS's.  So, leave my Windows as NTFS, install my Karmic as ext4, and the data as NTFS and we should be good to go, sounds like.

---

### Post by Sef on 2010-02-03
> ...as I am planning to daul-boot XP and Karmic, with a separate data  partition accessible by both OS's.  So, leave my Windows as NTFS,  install my Karmic as ext4, and the data as NTFS and we should be good to  go, sounds like.It sounds good.  If you have any other questions, please post them.

---

### Post by themarker0 on 2010-02-04
> **Sef said:**
> You are not necro posting.  In fact, you are about 12 months short of it.    

Ext4 has worked fine with me, and the majority of users.   I have used it since Jaunty.  Before installing, **back up** your **data**.

I misread it seems. Thank you very much sir.

---

### Post by Sef on 2010-02-04
> I misread it seems. Thank you very much sir.

You're welcome.  And please ask any other questions.

---

### Post by ellen96 on 2010-02-06
I need some serious help with my connection! How do I get my Swedish Telenor company's Huwaei E-1750 model moden to work with my Linux system - What do I need to do? Please..:o
 
Kind reg
 
/ellen96

---

### Post by sandy8925 on 2010-02-06
Ext4 is damn good. It's way faster than ext3 and so far I've found it to be stable. My laptop's battery has conked out and the power cable is loose so it gets switched off abruptly many (more than 100) times but I've never experienced any problem so far.

I guess it might be possible to get proper ext4 in jaunty by compiling a newer kernel version yourself. But might not work for intrepid and older since there's too much gap.

---

### Post by ltoso on 2010-02-06
Hi,
i have just installed ubuntu 9.10 with ext4 , kernal as you know is
2.6.31
is it stable in case of 9.10 or you recommend i should convert it bact to ext3

is there a convertor available that can directly convert ext4 to ext3

or i should reinstall it using ext3

Please recommend

Regards
ltoso

---

### Post by Sef on 2010-02-06
> i have just installed ubuntu 9.10 with ext4 , kernal as you know is
2.6.31
is it stable in case of 9.10 or you recommend i should convert it bact  to ext3

is there a convertor available that can directly convert ext4 to ext3

or i should reinstall it using ext3

Please recommend

In the vast majority of cases, it is perfectly stable.   

Are you having problems?   The only way to go from ext4 to ext3 is to do a clean install (afaik.)

---

### Post by ltoso on 2010-02-06
Hi,
i am not having any problems, but i got a little worried after reading all the posts in here, what do you recommend, should i continue using it or do a clean install again, i am loving my desktop and not in mood to do all the settings again, but if you think it is unstable can lead to loosing all of my data then i should reinstall it using ext3.

what do you recommend
Regards
ltoso

---

### Post by Sef on 2010-02-07
> i am not having any problems, but i got a little worried after reading  all the posts in here, what do you recommend, should i continue using it  or do a clean install again, i am loving my desktop and not in mood to  do all the settings again, but if you think it is unstable can lead to  loosing all of my data then i should reinstall it using ext3.

what do you recommend

I would recommend to stick with ext4.  People who have problems will post.  Those who do not them will not.  Keep you data backed up no matter what file system you use.

---

### Post by mikechant on 2010-02-08
ellen96 said:
> I need some serious help with my connection! How do I get my Swedish Telenor company's Huwaei E-1750 model moden to work with my Linux system - What do I need to do? Please..

What you need to do is open a new thread for your problem rather than stick your question on the end of a totally unrelated issue. You've got a much better chance of getting an answer then!

I suggest you select the 'Networking and Wireless' forum, then click on 'forum tools' near the top and select 'post a new thread'

---

### Post by Pritamsng on 2010-02-10
Thanks bro...
 
really ext4 is not good. I checked... some system hanging and partation error issue i faced in ext 4.

---

### Post by Sef on 2010-02-10
> Thanks bro...
 
really ext4 is not good. I checked... some system hanging and partation  error issue i faced in ext 4.

For you, it may not be good and ext3 would be a better choice for you.  But for the majority of people, it works fine.

---

### Post by alvarojavier on 2010-02-10
> **Sef said:**
> For you, it may not be good and ext3 would be a better choice for you.  But for the majority of people, it works fine.

That's real. Im working with 10 PCs networked, and I need setting up just 2 Servers.
Now Im migrating from Windoze to Ubuntu, and Im installing Ubuntu 64 + Ext4 in workstations. Server version with Ext3, so:
For server, I recomend use Ext3.
I will make some changes to config, but It's working very good.

---

### Post by importControl.Mind on 2010-02-12
I tried ext4 awhile ago and it was fine, until a power outage fried the filesystem. Ext3 frags big time on a TB harddrive.
Now am on XFS and it's great. :)

---

### Post by harry2006 on 2010-02-21
thanks for sharing your views. 
but i guess the adavantages of ext4 outshines the disadvantages .... what u say ?

---

### Post by DouglasAdams on 2010-02-22
> **harry2006 said:**
> .... what u say ?
i say wots the current situation please ??

---

### Post by DouglasAdams on 2010-02-26
> **san_antonio9.10 said:**
> **<snip>**

thanks for that. 
i already did what you "suggest".
but now i'd like to know what the experts on this forum think!!
sort of like me reading all the car reviews but now i'd like to talk to people who actually own and use the car i'm thinking of buying.
provided that's ok with you of course ...

---

### Post by mikechant on 2010-02-26
> <snip> <snip> 

  <snip> I'll report my current ext4 experience on my netbook and desktop machines.

a) eeePC 1000 (8Gb+32Gb SSDs) running Ubuntu Netbook 9.04/9.10
I've used ext4 on this exclusively for about a year, and in that time I've had several unclean shutdowns (battery), and there have been no visible data corruption/loss problems.
However, I store very little data on this netbook.

b) Dell 530 Desktop running Ubuntu 9.04/9.10/Studio, 1Tb+500Gb internal drives, 1Tb+400Gb external backup drives.

Using ext4 for root partitions but not /home or data. Also currently I have an (internal drive) ext4 copy of my ext3 data partition (about 300Gb each) which I rsync/check periodically, and the external backup drives have backups of /home and data partitions on each, one drive ext3 and the other ext4.
I.e. 4 copies of my main data partition, two ext3 and two ext4.

I've a several unclean shutdowns in Ubuntu studio (due to the realtime kernel being a bit more crash prone than the standard kernel) and one or two in normal Ubuntu. 

So far I have had no data corruption or loss visible, and I have also done a number of cross checks between the ext3/ext4 data copies on the internal and external drives and they all match exactly with md5sum. Files checked include DVD isos (4Gb) since problems were reported with large files by some people.

I'm now happy enough with ext4 that as soon as I have some spare time I'm going to switch to using it exclusively (but keep one final ext3 backup for at least a year).

---

### Post by Silent Warrior on 2010-03-01
... I... never had a problem with EXT4 even when it wasn't considered fit for general use... 'Course, my shutdowns are usually admirably clean, so I haven't put it through its paces good and proper, but still no problems with corruption and missing files - and file-system checking on boot-up really is blistering fast!
On the one hand, it was FRIGHTFULLY nervous to convert an EXT3-drive/partition without formating it... I don't recommend THAT.

---

### Post by emagar on 2010-03-01
Thanks for this compact & clear info!

---

### Post by HalfWord on 2010-03-02
I've recently switched to ext4 and I'm satisfied for now.

I've first converted two xfs filesystems, my /usr was getting tight and I couldn't resize xfs from gparted, so I created a fresh ext4 fs on a new larger partition. After I've seen it working fine and its fragmentation numbers (e2fsck non-contiguous files) being ridiculously low compared to my other filesystems, I did the same with my /var fs to get rid of xfs. I've always liked xfs very much, but I cannot resize it and presumably ext4 has most of its features I really care for. 

After that went well, I've converted my /home fs afterwards, by mounting it as ext4 in fstab. It worked perfectly, and I was delighted seeing non-contiguous files percent falling before my eyes after each check :) Then I got the courage to enable all ext4 features I've seen are active by default using tune2fs (extents for example, delayed allocation and other goodies), fsck-ed it to get it to a consistent state and it works perfectly just as a new ext4 fs do. The ease of upgrading and lack of problems during it amazed me! I've also explicitly enabled journal checksumming for all the ext4 fs' just in case some missed it, to combat fs corruption ;)

I've left just my rootfs as ext3 to be on the safe side - and afterwards I realized I better did so - I still use grub 1, and I've read it doesn't like ext4...

That, and my old dirty trick, I always have the /tmp fs as ext2 to avoid journalling overhead, that's a fs where I don't care if some files get corrupted :) And since it's a small fs, its boot-time fsck-ing in case of a crash I barely notice :)

---

### Post by takisan on 2010-03-07
It's sort-of like FAT32 vs. NTFS. NTFS is actually better but FAT is more compatible.

---

### Post by HalfWord on 2010-03-09
> **takisan said:**
> It's sort-of like FAT32 vs. NTFS. NTFS is actually better but FAT is more compatible.

I wouldn't quite compare_any_ linux/EXT FS with FAT FS ;)

---

### Post by wizarddrummer on 2010-03-13
Been using ext4 for about a month.

I didn't realize I had it until I read how to check. (didn't know the difference with I did the install)

I have no UPS; I have muchas problemas with power going down. It hasn't trashed any data as far as I can tell.

---

### Post by Max Derner on 2010-03-13
I've just tried to change to Ubuntu Karmic Koala from a crashed Windows Vista. After a hard shut down Vista messed up the hard drive. I can't even mount it and whenever I try to install Ubuntu it gets stuck a 5% and says it can't install the ext4 file. So does anyone think it could be ext4 of the fact I can't mount the bugger. I'm thinking about changing the hard drive.
 
Cheers, Max.

---

### Post by DouglasAdams on 2010-03-13
> **Max Derner said:**
> ...from a crashed Windows Vista.
... Vista messed up the hard drive.
... install Ubuntu it gets stuck a 5%
... I'm thinking about changing the hard drive.

if the hd is [was] stuffed by vista and won't mount then it will probably need re-partitioning before anything will install to it.
that is going to throw away all your data on the hd
... but so is changing the hd.
if you need to recover any data from the drive, do that first!
then boot from a live cd and use gparted to delete all your existing partitions and start again.
after re-partitioning use the check option to make sure it's fine.

---

### Post by Sef on 2010-03-13
> Quote:
 	 	 		 			 				 					Originally Posted by **Max Derner** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8959603#post8959603") 				
 				[I]...from a crashed Windows Vista.
... Vista messed up the hard drive.
... install Ubuntu it gets stuck a 5%
... I'm thinking about changing the hard drive.[/I]
 			 		 	 	 
if the hd is [was] stuffed by vista and won't mount then it will  probably need re-partitioning before anything will install to it.
that is going to throw away all your data on the hd
... but so is changing the hd.
if you need to recover any data from the drive, do that first!
then boot from a live cd and use gparted to delete all your existing  partitions and start again.
after re-partitioning use the check option to make sure it's fine.

[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") may resolve your problem.

---

### Post by movieman on 2010-03-15
> **harry2006 said:**
> but i guess the adavantages of ext4 outshines the disadvantages .... what u say ?

Not so far as I can see. The benchmarks I've seen show a negligible performance improvement over ext3, but ext4 is far more likely to lose your data.

I recently had to do my first manual fsck in about eight years, and it was on my only ext4 partition; I have over 100 ext3 partitions on different machines which have been running for far longer than the one with ext4 and they've never needed a manual fsck.

---

### Post by d3v1150m471c on 2010-03-15
never had any trouble with ext4

---

### Post by uRock on 2010-03-15
Yeah, I had the power trip three times in a row last night and lost zero files with EXT4.

---

### Post by l4zy on 2010-03-15
i've been usin ext4 on my Ubuntu Desktop for 4 months == Not any problems.

I also have ext4 on my backup-server, it used every 3 hour to write backups over nfs. 1GB network, no speed issues / crahes or anything. It has been running 3½ months without any issues..

Also*my media-box has etx4 / nfs-share no speed issues or crashes. 

Runnin kernel: 2.6.31-20-generic

---

### Post by ManyuX95 on 2010-03-16
I know, in fact I love that my PC turns off in just 7 seconds. My hackintos usually took like 20-30 seconds to turn off, ubuntu 9.04 like 15 seconds and windows like 30 seconds. Also startup is awesome and when you transfer files it goes preety fast :D I say YES! to EXT4

---

### Post by hkphooey on 2010-04-07
Having just been through the process of migrating 30 Windows machines to Ubuntu, I just have to say that there are still a number of problems with ext4 and imaging tools such as gparted, clonezilla, and partimage. 

If you are deploying Ubuntu by making a Master Image and then cloning it onto computers, then ext3 is definitely the way to go for now.

---

### Post by SecretCode on 2010-04-07
> **hkphooey said:**
> ... there are still a number of problems with ext4 and imaging tools such as gparted, clonezilla, and partimage. 

Can you give some examples? What should I worry about?

---

### Post by hkphooey on 2010-04-07
Well partimage flat out doesn't support ext4. 

Gparted is meant to, but after trying for a day I gave up. The partition transferred OK, but wouldn't boot.

Clonezilla is meant to, but after trying for a day I gave up. Various errors on restoring the image file, although making the image seemed to work.

fsarchiver is meant to, but I just tried that about 30 minutes ago, and it didn't work first time ... not sure if I can devote another day to that one ..

So ... based on that, my advice is to save yourself the trouble and just use ext3 if you're doing a lot of imaging.

---

### Post by SecretCode on 2010-04-07
Hmm. As you say, Clonezilla (via partclone) claims to support it. But I ran a restore test ... and got some errors, as you say. Disturbing.

Has anyone done a successful save **and restore** of an ext4 partition (or disk with ext4 partition) using clonezilla?

---

### Post by neglesaks on 2010-05-04
Chipping in with personal experience:

Used ext4 on several drives since 9.04. No issues. No data loss that I'm aware of ( I do regular diff runs to compare data, also to safeguard against spotty HD's).

Advantages noticed with ext4 over ext3:

Deleting a large number of files or a large amount of data is much faster; for ext3, deleting, say 50 gigs of data, will leave the hard disk churning away for minutes after the file is gone in nautilus. Not so in ext4.

fsck'ing is much faster, usually instantaneous. Takes 5-15 minutes for 1 TB HD with ext3.

Have not done any CPU load testing.

Overall, I'm quite satusfied with ext4, though I miss the promised file creation dates and ext4 utilities (such as defrag).

---

### Post by ltoso on 2010-05-05
I thought Defrag was only needed in windows operating system and not required in case of linux filesystems

Regards
Ltoso

---

### Post by neglesaks on 2010-05-05
> **ltoso said:**
> I thought Defrag was only needed in windows operating system and not required in case of linux filesystems

Regards
Ltoso

That's a myth. Any filesystem with files bigger than the size of a single allocation block will become fragmented eventually, and Linux fs's are no exception.

---

### Post by movieman on 2010-05-05
MythTV frontend refused to boot last week due to ext4 corruption; which is exceptionally stupid because iotop shows it hardly ever writes anything to the SSD... all non-essential files go to tmpfs.

I knew I should have stuck with ext3 rather than risk using ext4 again after my previous experience on the netbook. Even 'experimental' btrfs seems to be much more robust.

---

### Post by huwjenjinn on 2010-09-07
> **neglesaks said:**
> That's a myth. Any filesystem with files bigger than the size of a single allocation block will become fragmented eventually, and Linux fs's are no exception.

It's a little unfair to say it's a myth when it's been designed to resist fragmentation. 

My understanding of Linux filesystems is they are highly resistant to fragmentation until the disk or disks near maximum capacity. Clearly at the extremis of any filesystem usage, extremely large files on near maximum capacity disks, will be susceptible to some fragmentation. But to say it's a complete myth is plain misleading in this instance.

---

### Post by DouglasAdams on 2010-09-07
would, might, a sign of any fragmentation be that Linux seems to decide more often that it needs to do a disk check during a reboot or is that totally unrelated to fragmentation?

btw, my / & /boot use ext4, everything else is ext3

---

