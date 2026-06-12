---
title: "Seagate Momentus XT Hybrid HDD"
date: 2010-06-17
forum: Hardware
---

### Post by cj.surrusco on 2010-06-17
Looks like Seagate is taking another crack at hybrid hard drives. The benchmarks show that it performs much better than a regular 7200rpm drive. 

[http://www.washingtonpost.com/wp-dyn/content/article/2010/06/17/AR2010061700159.html]("http://www.washingtonpost.com/wp-dyn/content/article/2010/06/17/AR2010061700159.html")

Now, I know that it works by moving commonly used files to the 4GB flash memory, but what controls the file movement? Is it done by the hard drive itself, or does it require drivers in the operating system? What I'm basically asking is, how easy will it be to get one of these working on a Linux system?

---

### Post by Jim_in_Omaha on 2010-07-23
Are there any Linux users running this drive? And your opinions?

---

### Post by vistamacbuntu on 2010-08-09
just got mine today. i plan to clone my current install of mint/kubuntu to avoid the hassle of reconfiguration.

hopefully tomorrow.

good luck to me.:popcorn:

---

### Post by cascade9 on 2010-08-09
> **cj.surrusco said:**
> Now, I know that it works by moving commonly used files to the 4GB flash memory, but what controls the file movement? Is it done by the hard drive itself, or does it require drivers in the operating system? 

Done by the drive itself, apparently- 

> The Momentus XT drive installs as easily as a traditional 9.5mm-high notebook drive for new systems or laptop upgrades and, unlike early hybrid drives, operates independently of the operating system and the motherboard chipset.[http://www.xbitlabs.com/news/storage/display/20100524133650_Seagate_Reveals_New_Hybrid_Drive_Claims_World_s_Highest_Speed_Mobile_HDD.html](http://www.xbitlabs.com/news/storage/display/20100524133650_Seagate_Reveals_New_Hybrid_Drive_Claims_World_s_Highest_Speed_Mobile_HDD.html)

Just a pity its a read only NAND cache (not read/write like an SSD) and only has 1 NAND chip, when SSDs have multipule chips in parallel, so its never going to be as fast as a SSD. 

Decent in-depth review here- 

[http://www.anandtech.com/show/3734/seagates-momentus-xt-review-finally-a-good-hybrid-hdd](http://www.anandtech.com/show/3734/seagates-momentus-xt-review-finally-a-good-hybrid-hdd)

---

### Post by vistamacbuntu on 2010-08-11
I am now using a 500GB Momentus XT Hybrid HDD.  My setup is a Thinkpad X200 that used to have a 160GB Hitachi 7200 RPM hard drive.  I have a franken-installation of Linux Mint 8 upgraded to Mint 9 (which as most know is based on Ubuntu 10.04) and topped up with Kubuntu (installed separately via Synaptic) with recently updated KDE 4.5.  Whew.  Suffice it to say, this is not a clean install and boot times were already past a minute just getting to KDM login and maybe another minute to get to my desktop with loaded apps (Pidgin, Skype, Konsole, etc.)

I cloned my HDD using a USB booted copy of Mint and let it run overnight. Note to those who want to do a clone via dd command, it takes time! Maybe it's my hardware, but I mounted my hybrid Momentus XT through an external SATA drive and got an average of 4.8 MB/sec... took about 8 hours).  

Swapped drives, booted and it works perfectly.  :p

Booted about 4 times so the SSD portion can "know" the data I use often.  I still have some tweaking to do like the expanding the unused partition, but I just wanted to share my impression that it is definitely faster during boot.  I'll share more impressions later on if this thread has interest after I've done a bit of daily stuff on my laptop.

---

### Post by vistamacbuntu on 2010-08-12
Repartitioned using GPARTED and was able to increase my home partition to 400GB+.  It was like math problems all over again because my home partition was at the leftmost side and had no empty space beside it.  Took about 1.5 hours to run.

Things working great.  Feels faster. 

However, the true test is how I feel about my desktop after 3-5 days of not shutting down.  This is when I typically feel swap is being used by some app (Wine? Firefox? Soffice?)

Additionally, it's a little noisier than my previous 160GB Hitachi.

---

### Post by vistamacbuntu on 2010-08-14
Notice that Wine apps (Excel which I still need to use a lot since it's superior to OO's Calc) startup much faster now.  Especially when it's the second or third time starting the app.

This is a huge plus for me.

---

### Post by Carlie Powell on 2010-10-27
Lenovo Y550P i7

Having it lockup with a load. It works fine in Win7 with same apps or intense usage. Not sure but it requires a Hard Reboot, the mouse works. I had noticed it during the synaptic download/install. I thought it was jus the installing process but its use, as well. Any ideas guys??

---

### Post by Carlie Powell on 2010-10-27
I got it working it was Nouveau and Nvidia 240M conflict, I got it resolved. I hav it working with Plymouth Splash and 256.x Nvidia driver on preivous hard drive (now external) accessing the same file and operation, so that was it. :KS

---

### Post by ctothej on 2010-12-07
I'm having I/O freeze issues that coincide with the hard drive activity light when the drive tries to prefetch data into cache (I am supposing). It is very annoying and causing usability issues for me. I will be recloning my drive back to a normal 7200 rpm drive soon because of this issue. 

I'm on 10.10 x64.

---

### Post by FedeGhigo on 2010-12-25
I'm too having the same problem: on 10.10, I use it for vmware workstation, and when I resume a virtual machine, very often it crashes with different dumps, no problem with other drives.

---

### Post by pmorton on 2011-02-16
Got the same freeze-up issue; its seems to be related in my case to Virtualbox, ie it doesn't occur if Virtualbox isn't running. Thought I might try the SD24 firmware fix which is supposed to resolve the problem. Anyone got any experience?

---

### Post by FedeGhigo on 2011-02-17
I updated to SD24, same issue (it just looks less frequent).

---

### Post by dbworth on 2011-02-19
Hi guys,

Dell Precision Laptop (a few years old) w/ new Seagate Momentus XT.
New install  of Kubuntu 10.10

I'm getting some lock-up problems and I've barely done much to the install yet.

KDM will lock-up for 30 seconds or so, then be okay for 5 mins, the lock-up again...... repeat..... very annoying  :-)
Can't notice any problem in console.

.

UPDATE:  Okay I noticed cairo-dock (the new/alternative version I think) had started doing some weird things. Icons effects were acting weird, so I tried to kill it and it wouldn't die well. Ended up purging all cairo dock stuff and it's running perfect now. Presumably the more I tweaked produced some bad combination of add-ons or visual effects, but killing cairo dock fixed it for me.

So far the Momentus XT is going well, it's fast to boot but I don't restart much anyway  =]

---

### Post by FedeGhigo on 2011-04-01
Installed firmware SD25, problems increased, I use it not for Ubuntu 10.10 os, but for running Vmware Virtual Machines from an Ubuntu OS; it's formatted ext4. When I copy on it a perfectly running virtual machine (XP i.e.) and then start it, it immediately starts complaining about corrupted files....Vmware Workstation 7.1.4. The worst part of this is that there is no warning on the Seagate site, while I think this should be done, since the main mission for an HDD i think is still to reliably save data on it.

---

### Post by pmorton on 2011-04-04
> **FedeGhigo said:**
> I updated to SD24, same issue (it just looks less frequent).

I've now been upgraded to SD24 for a while, and have the exact same experience as you; less frequent, but still occurring.

---

### Post by PSY0NIC on 2011-04-04
> **pmorton said:**
> I've now been upgraded to SD24 for a while, and have the exact same experience as you; less frequent, but still occurring.

So I'm assuming this was never fixed.  Having same issues since 10.4.

---

### Post by pmorton on 2011-05-13
> **PSY0NIC said:**
> So I'm assuming this was never fixed.  Having same issues since 10.4.

I'm now onto firmware fix SD25, but the problem persists; always as a result of using Virtualbox.  The drive itself is astonishingly fast, so it's a shame it's marred by this glitch.

---

### Post by waterloo2005 on 2011-05-27
Is Momentus XT now stable enough for linux ?

How about virtualbox file, now? thanks

---

### Post by FatalChaos on 2011-05-31
> **waterloo2005 said:**
> Is Momentus XT now stable enough for linux ?

How about virtualbox file, now? thanks

I've been looking for the same info, and although I haven't found anything definitive the latest firmware version is still SD25, which one of the earlier posters claimed increased problems.

---

### Post by Mr. Code Depot on 2011-07-06
Hi all, I use  this (hybrid drive in Thinkpad R500) for a month now - of  course some tweaking is needed, but when you pass this initial  inconvenience it working like a charm.

This is link to forum at manufacturer's website 
[http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/bd-p/Momentus](http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/bd-p/Momentus)

To tweak I use hdparam (spindown,aam ...)
[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

I hope it will be helpful in some way ;)

---

### Post by ironclaw on 2011-07-12
> **FedeGhigo said:**
> Installed firmware SD25, problems increased, I use it not for Ubuntu 10.10 os, but for running Vmware Virtual Machines from an Ubuntu OS; it's formatted ext4. When I copy on it a perfectly running virtual machine (XP i.e.) and then start it, it immediately starts complaining about corrupted files....Vmware Workstation 7.1.4. The worst part of this is that there is no warning on the Seagate site, while I think this should be done, since the main mission for an HDD i think is still to reliably save data on it.
FedeGhigo, pmorton, PSY0NIC, and everyone else having similar issues: I have created a [thread here]("http://ubuntuforums.org/showthread.php?t=1803004") about large files being corrupted on Momentus XT drives. I have provided instructions there for reproducing file corruption on a Momentus XT, and I'd like to know if you are able to reproduce the problem.

The problems with virtualization images fits my hypothesis that the Momentus XT is corrupting large files.

---

### Post by JayGB1982 on 2011-07-16
> **Mr. Code Depot said:**
> Hi all, I use  this (hybrid drive in Thinkpad R500) for a month now - of  course some tweaking is needed, but when you pass this initial  inconvenience it working like a charm.

This is link to forum at manufacturer's website 
[http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/bd-p/Momentus](http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/bd-p/Momentus)

To tweak I use hdparam (spindown,aam ...)
[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

I hope it will be helpful in some way ;)
Hi There,

I purchased a 500GB Momentus XT in the week. I am currently running 10.10 as I have issue's with the Geforce 7600m chipset under 11.04 causing lock-ups from suspend and also what appears to be graphics corruption (possibly overheating?)

Anyway I was wondering if you could share your Hdparam settings for this drive?

I literally have no idea where to start.

---

### Post by danwat1234 on 2011-08-25
Here is the official Seagate Momentus XT SD26 firmware update. SD26 is the latest version of the drive's firmware as of the end of August, 2011.



Windows version (easiest):
[http://www.sendspace.com/file/mhlkbf](http://www.sendspace.com/file/mhlkbf)


Bootable iso version:
[http://www.sendspace.com/file/rifiz5](http://www.sendspace.com/file/rifiz5)

---

### Post by lolleepop on 2011-09-09
> **JayGB1982 said:**
> Hi There,

I purchased a 500GB Momentus XT in the week. I am currently running 10.10 as I have issue's with the Geforce 7600m chipset under 11.04 causing lock-ups from suspend and also what appears to be graphics corruption (possibly overheating?)

Anyway I was wondering if you could share your Hdparam settings for this drive?

I literally have no idea where to start.

This! I'm dual booting MacBook 4,1 with Os X 10.7 and Ubuntu 10.04. Almost everything is working, but if I suspend in Ubuntu everything goes to **** (failed command: READ DMA EXT etc. when I force shutdown). My Momentus XT 500 GB has the latest SD26 firmware..

---

### Post by chronos00 on 2011-09-25
I have been searching A LOT around this issue. The latest I have found is in [this forum]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/UNIFIED-THREAD-Momentus-XT-spreadsheet/td-p/99676").

Note that the Seagate site's administrator is asking every Momentum XT user to fill the google spreadsheet with our system information and experience. It would be great if everyone here did this, so that the next firmware upgrades also solve problems presented on Linux plataforms.

Also, there is a new firmware available; **SD28**. Instructions here:
[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=215451](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=215451)


Has anyone tried to use hdparm to load the firmware to the drive? What is your experience loading the new firmware? And how have you done it?

Regards

---

### Post by ironclaw on 2011-09-25
Hi Chronos00. What issues are you having with the Momentus XT? As far as I know, there are no outstanding issues in SD28 in Linux. I have tested the Momentus XT under SD28 with the instructions that I posted in the [Seagate Forums]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/td-p/109008#M3343"), and found no issues. I updated to SD28 the day it was released, and have been using the Momentus XT on a daily basis. So far, I have found no conspicuous issues.

I don't think you want to use hdparm to load the firmware. Seagate recommends downloading the SD28 bootable ISO image, burning that to a CD, and booting from the CD to update to SD28.

I recommend downloading the SD28 bootable ISO image, and using [grub-imageboot]("http://michael-prokop.at/blog/2011/01/07/booting-iso-images-from-within-grub2/") to boot the ISO image without having to burn it to a CD. If you are on Oneiric beta, you should be able to install grub-imageboot from the repositories. Otherwise, you can install from a [.deb package]("http://deb.grml.org/pool/main/g/grub-imageboot/").

Once grub-imageboot is installed, put the SD28 ISO image into /boot/images/, and run
```
sudo update-grub2
```
Now reboot, and you will able to choose to boot from the ISO image at the GRUB menu. Follow the Seagate prompts to update to SD28.

---

### Post by chronos00 on 2011-09-25
I havn't yet upgraded to SD28; I am still on SD23 (the original firmware my drive came with). I am currently on a trip, and I am not able to perform a backup of my data right now. But this issue is driving me crazy! So with your amazing recomendation of grub-imageboot, I might take my chances with the upgrade anyway.

The problem I have with the drive is that it randomly, and constantly, freezes for a couple of seconds the computer. This is happening as often as once every 10 seconds, when I do anything more demanding than typing text, like this one... Even after typing a google search, after hitting enter, my laptop would freeze for 2 seconds.

I have just tried changing disc's APM setting to disabled, using hdparm. I have the feeling this improved the situation, but I am still testing... If this doesn't get any better, I'll try your suggestion for booting this updating ISO image.

Con I consider this upgrade process fairly safe? (aside of knowing that if the systems halts or powers off during upgrade, the drive is gone for good...)

---

### Post by ironclaw on 2011-09-25
I'm afraid I haven't experienced the issue that you have, so I don't know if SD28 will fix it.

I've updated three Momentus XTs about 6-9 times in total without issues (with about half of these updates using grub-imageboot). *However, I have once managed to brick a Momentus XT by forcing a downgrade from SD25 to SD24.* I've downgraded successfully several times before, so I don't know why it failed that time, and I don't know what the success/brick ratio is for normal updates. If your data is irreplaceable, I... can't really recommend that you update with grub-imageboot. After all, grub-imageboot *is* a relatively new package, and there may be undetected issues.

Update with grub-imageboot at your own risk. 8-[

---

### Post by chronos00 on 2011-09-25
hehe, noted. I understand. I am in fact used to this kind of risky situations, but data is by far my most valuable asset on any computer, so I guess I'll have to hold myself back :p

So your problem was only the data corruption? (and this is a pretty big problem, so by only I mean there is no other problem).

When I first read your post, several weeks ago, I was tempted to try reproduce the problem with your guide. But once again, I held myself because I could possibly corrupt my existing data. Is this correct? Is there any way to try to reproduce the problem without riskng existing data?

Because now that I think of it, I may ALSO have the same problem you experienced...

---

### Post by ironclaw on 2011-09-25
> **chronos00 said:**
> So your problem was only the data corruption? (and this is a pretty big problem, so by only I mean there is no other problem).
Yes, that's the only problem that I've ever been aware of on my Momentus XTs.

> **chronos00 said:**
> I held myself because I could possibly corrupt my existing data. Is this correct? Is there any way to try to reproduce the problem without riskng existing data?
Actually, I think it is highly unlikely that existing data can be corrupted by testing the Momentus XT with my instructions. I am quite confident that the data corruption is caused by the Momentus XT incorrectly writing large files. In other words, as long as your system is not overwriting large files while the testing is in progress, your existing data should be safe.

In fact, there's an additional layer of safety because I've found that corruption does not occur if you are reading and writing on the same Momentus XT - so if you copy a large file both from and to the Momentus XT, nothing bad will happen.

The only realistic scenario where data corruption occurs is if you copy a large file from an external device onto the Momentus XT. This is how I first experienced the problem.

Just to be extra safe, if you try to reproduce the data corruption issue, I would recommend that you reboot the system just before and just after testing.

If you have time to do the testing before updating to SD28, I would be very interested to hear the results.

---

### Post by chronos00 on 2011-09-26
Count on it.

I'll have a couple of weeks before returning home and being able to backup my data, so until then I'll have plenty of time for testing.

I remember reading you had changed your guide a couple of times. What test would you like me to run? I mean, what is the last guide you wrote?

Regards

---

### Post by ironclaw on 2011-09-26
Thanks! I appreciate it. Use [this guide]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/td-p/109008#M3343"). The commands in any outdated guide are all crossed out, so as long as the commands are visible, you are looking at the most up-to-date guide.

I think you don't have an external drive with you(?) In this case, you will want to setup tmpfs, as I state in the guide. I hope you have at least 2GB of RAM - 1GB of RAM should also work, but the test file size will be smaller, and the problem takes longer to reproduce with smaller test files.

What filesystem are you on? I've consistently reproduced the issue on ext4, ext2, NTFS, and Btrfs, but strangely ext3 seems to be safe from data corruption.

---

### Post by htt-thalan on 2011-10-20
> **ironclaw said:**
> Thanks! I appreciate it. Use [this guide]("http://forums.seagate.com/t5/Momentus-XT-Momentus-Momentus/Momentus-XT-corrupting-large-files-Linux/td-p/109008#M3343"). The commands in any outdated guide are all crossed out, so as long as the commands are visible, you are looking at the most up-to-date guide.

I think you don't have an external drive with you(?) In this case, you will want to setup tmpfs, as I state in the guide. I hope you have at least 2GB of RAM - 1GB of RAM should also work, but the test file size will be smaller, and the problem takes longer to reproduce with smaller test files.

What filesystem are you on? I've consistently reproduced the issue on ext4, ext2, NTFS, and Btrfs, but strangely ext3 seems to be safe from data corruption.

Boy am I glad I read this thread before switching to the new 11.11 on my Seagate XT Hybrid disk :-)

Now my knowledge on Linux is limited (only started learning 2 years ago) but I do recall Ext4 having some minor (or major, depending on your philosophical viewpoint) possible problems with regards to file corruption. Is that problem still present and maybe interfering with your results?

I have a normal 500gb  Sata disk at hand to replace my drive with (saves me having to make a seperate ghost of my current installation besides the normal file backup) to try out 11.11 on my Qosmio notebook, but I would much rather enjoy the speed of the new kernel with my Hybrid XT disk than some outdated 5400rpm Sata disk.

If it's a dodgy setup though, I might have to wait a while before I switch. Have been running Win7 on the XT disk after I purchased it, exactly because I was already expecting some compatibilty issues with Linux, albeit my previous hesitation was inspired by the then-new Trim support needed for SSD disks and I wasn't sure if the Hybrid counts as one.

---

### Post by ironclaw on 2011-10-23
> **htt-thalan said:**
> 
Now my knowledge on Linux is limited (only started learning 2 years ago) but I do recall Ext4 having some minor (or major, depending on your philosophical viewpoint) possible problems with regards to file corruption. Is that problem still present and maybe interfering with your results?

As far as I know, the delayed allocation changes from ext3 to ext4 only affects scenarios involving a kernel panic or a sudden power loss. Ext4 should be rock stable under normal circumstances, so I don't think this had to do with the previous file corruption issues on Momentus XTs.

> **htt-thalan said:**
> 
If it's a dodgy setup though, I might have to wait a while before I switch. Have been running Win7 on the XT disk after I purchased it, exactly because I was already expecting some compatibilty issues with Linux, albeit my previous hesitation was inspired by the then-new Trim support needed for SSD disks and I wasn't sure if the Hybrid counts as one.


You should have no issues with Linux as long as you update the Momentus XT firmware to [SD28]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=215451"). Also, I don't think the Momentus XT accepts TRIM commands - it manages its SSD cache independent of the OS.

---

### Post by superbonus on 2011-11-07
I've had the stuttering issue (but no file corruption) since a month after I bought my XT 6 months ago. I started on firmware SD24 and went to SD25 and then to SD28. I thought the SD28 firmware had solved my problems but only a week after flashing the stuttering returned worse than ever. It's almost unusable now; I get a 2 - 5 second stutter every time I load a new page in my browser. I wish Seagate would sort this out and stop selling the drive until they do.

---

### Post by edubbler on 2011-12-16
Installing one of these tomorrow.

Any filesystem recommendations? I'm torn between xfs & ext4 but open to any recommendation.

---

### Post by oldsmoke on 2012-01-25
put 1 in a couple days ago seems fine no super speed increases but is doing fine my install problems with file systems seem related to 11.10
the prob is installs fail if i pick any other file system such as xfs or jfs.

---

### Post by edubbler on 2012-02-16
> **oldsmoke said:**
> put 1 in a couple days ago seems fine no super speed increases but is doing fine my install problems with file systems seem related to 11.10
the prob is installs fail if i pick any other file system such as xfs or jfs.

I've been running perfectly fine on XFS. Noticeable bump in boot up time.

Just FYI

---

