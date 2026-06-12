---
title: "Installing Ubuntu 8.10 to External HDD (Not Appearing in Installer)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by lake54 on 2009-05-29
Right, it's probably easiest to treat me as a total Linux noob, but I am a geek on Windows. I'm familiar with some stuff (like how to do step-by-step stuff in Terminal) but I won't understand it if you say "Do this then that" - you'll have to really do it step-by-step.

Hope that cleared "me" up for you!

I'm running Ubuntu Desktop 8.10 via a Live CD at the moment, but want to install to my external HDD (via USB) on one of its four partitions (NTFS).

I've got two internal hard disks, and this external HDD, yet when I go to install (or even USB startup disk creator) it doesn't show up. They show on the desktop (after I force-mounted them) but refuse to show there.

They're currently mounted at /media/Name if that helps - I have a feeling Ubuntu will only 'detect' /dev/ mounted drives?

If you need any more info then just say.

Any help will be greatly appreciated :-)

James Milligan / Lake54
PS: I'm on the ubuntu-uk mailing list

---

### Post by oldos2er on 2009-05-29
While you're "in" the LiveCD, can you open a terminal (Applications, Accessories, Terminal), and post the output from this command:
```
sudo fdisk -l
```
?

---

### Post by lake54 on 2009-05-29
I've got memtest running at the moment but as soon as it's finished I'll reply back. Thanks so far and in anticipation!

James

---

### Post by lake54 on 2009-05-29
OK the results are here:

[http://paste.ubuntu.com/183874/](http://paste.ubuntu.com/183874/)

From what I understand, it's sdc4 I wish to install to. The boot asterisk was when I tried before to add the boot flag to that partition to see if that had any effect - no success as yet. I'll remove that now.

Hope that helps you somewhat.

James

---

### Post by lake54 on 2009-05-29
Anyone got any advice at all?

Sorry to be rushing slightly - I was going to use it tomorrow to convince the boss to swap to Ubuntu! (We're a small IT company, I'm the Saturday guy)

James

---

### Post by oldos2er on 2009-05-29
When the partitioner runs during installation, choose 'Manual', and you should see a drop-down box that lets you choose sdc. It doesn't need to be mounted; and in fact it may need to be unmounted.

---

### Post by lake54 on 2009-05-29
I did try that both mounted and unmounted but it still only showed the internal disks.

Added to this I reformatted the partition from NTFS to ext3 but it still wasn't recognised.

James

---

### Post by oldos2er on 2009-05-29
I'm quickly running out of ideas. Were the NTFS partitions on sdc shut down cleanly?

---

### Post by lake54 on 2009-05-29
Technically no - they weren't safely removed in Windows so I had to force mount.

Should I try this?

---

### Post by oldos2er on 2009-05-29
Ubuntu is smart enough not to mount a "dirty" NTFS partition, unless you force it. Try shutting them down cleanly, and see if that helps.

---

### Post by lake54 on 2009-05-30
Right I've disconnected by internal hard drives, but before I did this I tried installing via the boot menu rather than through the live cd itself - it seemed to pick it up, but wanted to use the other partitions on my internal HDDs as well, which I of course don't want to do.

I've now booted into the Live CD and tried through the installer again but it just shows blank.

I've also tried creating 2 partitions - one for the swap file (precisely 4 gig) and the other for the installation of Ubuntu (if this isn't right let me know!).

I currently, therefore, have the following 'layout' on my external HDD:

CF - 50 GB - Primary Partition
IT - 50 GB - Primary Partition
Personal - 100 GB - Primary Partition
Ubuntu - 32.3 GB - Extended Partition:
- 4 GB Swap Partition
- 28.3 GB 'Data' Partition

Unfortunately I'm just left with the primary partitions and an empty extended partition as I can't create the data partition in ext3, and the linux-swap partition won't go on either (I used the linux-swap format - is this correct?)

Thanks for your help so far!

Was roasting at work today - been a very hot day in the UK for once! Pity there was no air con though...

James

---

### Post by lake54 on 2009-05-30
Anyone? I was hoping to get it boxed off tonight if I could.

Don't want to rush anyone though!

James

---

### Post by oldos2er on 2009-05-30
How did you create the swap and data partitions? With the LiveCD'd partition editor, or something else?

---

### Post by lake54 on 2009-05-31
GParted on the Live CD

---

### Post by lake54 on 2009-05-31
Anyone?

---

### Post by oldos2er on 2009-05-31
I'm trying to understand what's going on...you're booted from the LiveCD, you run gparted to create the partitions you want, then you run the installer, choose 'Manual', and can't find these partitions?

 Could you take a screenshot of the partitioner after you choose manual?

---

### Post by lake54 on 2009-05-31
Right:

External HDD formatted as above post, bar the Ubuntu partition which was NTFS.

Ran Live CD, formatted Ubuntu partition to ext3

Not picked up in installer.

Screenshot:

[http://www.killermentality.com/james/installer.png](http://www.killermentality.com/james/installer.png)
[http://www.killermentality.com/james/manual.png](http://www.killermentality.com/james/manual.png)

Hope that helped somewhat.

James

---

### Post by lake54 on 2009-05-31
Oh also - [http://www.killermentality.com/james/GParted.png](http://www.killermentality.com/james/GParted.png)

The partition I'm trying to install on is /dev/sdc4

---

### Post by oldos2er on 2009-05-31
> **lake54 said:**
> 
Screenshot:

[http://www.killermentality.com/james/installer.png](http://www.killermentality.com/james/installer.png)


 Ok, from this screenshot, click 'Manual', and please post a screenshot.

 Your patience is appreciated.

---

### Post by lake54 on 2009-05-31
> **oldos2er said:**
> Ok, from this screenshot, click 'Manual', and please post a screenshot.

 Your patience is appreciated.
On the manual partitioning step it just shows the two internal disks with their partitions. No mention at all about my external one.

Sorry I keep posting about 'anyone' etc it's just I'm so eager to use Ubuntu!

Thanks for your help oldos2er

James

---

### Post by lake54 on 2009-06-01
*bump*

I'm also going to install Ubuntu to one of my internal HDDs, as one of the partitions failed the other day. Can Ubuntu be installed to one partition on a secondary Windows Drive (i.e. it's not C) and keep the other data partition which I use for backups intact?

If so, should I just follow the standard install (I use the apcmag.com guides - very well presented and thorough IMO).

Thanks,

James

EDIT: Also, how can I set GRUB to automatically boot XP instead of Ubuntu? My parents won't really want to use Ubuntu yet, so it's easier to let them use XP for now. If possible, setting the boot menu to 3 second timeout should be quick enough for me.

---

### Post by lake54 on 2009-06-01
OK I've formatted my second internal HDD to the following:

[http://www.killermentality.com/james/partitions.png](http://www.killermentality.com/james/partitions.png)

A) Is this right
B) Following from the previous post, how do I set GRUB to boot XP by default after a 3 second timeout?
C) My original issue, a portable installation of Ubuntu.

Thanks!

James

---

### Post by Partyboi2 on 2009-06-01
You can edit your /boot/grub/menu.lst file to change the time down to 3 secs and to make windows the default one.
Open a terminal and open your menu.lst
```
gksu gedit /boot/grub/menu.lst
``` look for this part and change the timeout to 3
 > ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        [COLOR=Red]3[/COLOR]To set windows to the default option you can use one of the options mentioned [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc"). After you have made the changes and saved back in the terminal update grub with
```
sudo update-grub
```
If you are still unsure how to set windows as the default post your /boot/grub/menu.lst and someone will be able to help.

---

### Post by lake54 on 2009-06-01
Thanks - I think I should be able to manage that now.

Have I created the partitions correctly as per the screenshot in my last post?

James

---

### Post by Partyboi2 on 2009-06-01
> **lake54 said:**
> Thanks - I think I should be able to manage that now.

Have I created the partitions correctly as per the screenshot in my last post?

James
The link is a dead link, it comes back as 'page not found'

---

### Post by lake54 on 2009-06-01
OK the link is now working - the filename was capitalized (Part...) so sorry!

James

---

### Post by lake54 on 2009-06-01
If someone could reply yes I'd be really grateful - can't wait to start using Ubuntu!

---

### Post by VastOne on 2009-06-01
> **lake54 said:**
> If someone could reply yes I'd be really grateful - can't wait to start using Ubuntu!

Out of curiosity, is your bios setup for USB to be available at power on? 

I went through this a bit with having a bear of a time getting to my bios because using a wireless kb and mouse that was USB connected would not work until I went into my bios and told it to allow USB to startup when power was on.

Just a thought...

---

### Post by lake54 on 2009-06-01
Would that affect the Installer which is accessed through the Live CD though?

James

---

### Post by lake54 on 2009-06-01
Oh and just to add, I'm pretty sure it is set up to be able to boot from USB.

James

---

### Post by VastOne on 2009-06-01
> **lake54 said:**
> Would that affect the Installer which is accessed through the Live CD though?

James

I guess I missed the theme of this...I thought you were having issues even seeing this external drive during the LiveCD process.

---

### Post by lake54 on 2009-06-01
Yes - from the original 'thread' I was trying to make a portable installation of Ubuntu on my external hard drive - neither the USB creator nor the 'Full' Installer from the Live CD environment sees the external HDD.

I've also started posting (I suppose misleadingly) about partitioning my secondary internal HDD to hold Ubuntu permanently - my main question for that is "Are the partitions I spoke about earlier correct and safe so that no data is damaged on /sda or /sdb1?"

Thanks for your help VastOne

---

### Post by lake54 on 2009-06-01
Should I take the plunge? I mean the data on sdb1 isn't that important, it's all being used somewhere, and if the worst comes to the worst I've got my disks ready to roll (XP, backup etc).

EDIT:

/dev/sdb6 (the third partition, second is sdb5 - swap, first is sdb1 - ntfs data partition) is formatted in ext3 and set to mount point /

James

---

### Post by lake54 on 2009-06-01
Edited slightly

---

### Post by oldos2er on 2009-06-01
> **lake54 said:**
> Should I take the plunge? I mean the data on sdb1 isn't that important, it's all being used somewhere, and if the worst comes to the worst I've got my disks ready to roll (XP, backup etc).

EDIT:

/dev/sdb6 (the third partition, second is sdb5 - swap, first is sdb1 - ntfs data partition) is formatted in ext3 and set to mount point /

James

 If you don't care about the data on sdb6, then go for it. Sorry I couldn't be of more help re the USB drive.

---

### Post by lake54 on 2009-06-01
OK, wish me luck! I'm currently reparitioning the drive now, and about to install. Hopefully get it done or at least started before 8!

James

---

### Post by lake54 on 2009-06-01
Quick question:

If I create one partition for the swap (5GB), and another partition for the install (mount point /) is that all that is needed? I need to ensure that sda and sdb1 aren't overwritten at all.

Quick response would be most appreciated :-)

James

---

### Post by lake54 on 2009-06-01
Right I'm on step 7, and I have this in the settings box:

> If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sdb)

The following partitions are going to be formatted:
 partition #5 of SCSI3 (0,0,0) (sdb) as swap
 partition #6 of SCSI3 (0,0,0) (sdb) as ext3

But in the Advanced bit, I'm confused as where to set the bootloader to be. sda has my XP install, sdb will have my Ubuntu install.

[http://www.killermentality.com/james/whichone.png](http://www.killermentality.com/james/whichone.png)

Thanks!

James

---

### Post by oldos2er on 2009-06-01
By default Grub will install itself to the MBR of the first hard disk. It should pick up your Windows automatically so that you can boot whichever OS you choose. See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by lake54 on 2009-06-02
Ah right - so it kind of works like this:

MBR is on sda

This picks up the XP installation on sda1

It will pick up Ubuntu installation on sdb

etc? If so, that's perfect.

Thanks once again for your help. I'm so nearly ready to dive into the Ubuntu world!

Also just a quick note on the Live CD - it's great as well. I've been using it nearly everyday for a week now, using it each time from a fresh boot. Apart from the long load time, it runs great!

James

---

### Post by lake54 on 2009-06-02
I'm installing now anyway - it's on 5% creating the partitions - any idea how long this should last?

Never mind just started.

James

---

### Post by lake54 on 2009-06-02
OK just got error 5 (i/o regarding faulty hard disk or something).

Going to create partitions in gpart via live cd and try again. if it doesnt work from there, im going to try alternate and see if it works from there.

thanks for all the help!

james

EDIT:

Regarding the error - the HDD I'm using was originally an external desktop hard drive - could it be spinning down, causing the error? If so, how can I stop this?

James

---

### Post by lake54 on 2009-06-02
OK booting to the installer rather than the live cd worked - I'm now typing from my newly installed Ubuntu install :-)

Just going to check that XP works fine, then I'm done ;-)

You'll definitely be seeing me a lot more on the forums as well guys

Lake54 - James

---

### Post by lake54 on 2009-06-02
Right, I'm now typing this from a fully installed Ubuntu system :-)

The only thing that doesn't work is my sound - I have a Creative Soundblaster X-Fi XtremeGamer (I think) - I grabbed the drivers from the Creative site, and installed em etc. When I go to System > Preferences > Sounds, and select the device etc and click Test, it works. Yet when I go in Firefox to a page it doesn't play the sound - any ideas?

Thanks!

james

EDIT: Some sounds do work - for example, Pidgin makes sounds for incoming IMs etc. That works fine. Youtube is just mute though. No sound at all (video plays fine though).

If it'd be better posting a new thread/new category let me know.

---

### Post by ulgor on 2009-06-04
@all: very interesting post, i am just about to install 9.04 on my external USB drive.

@lake54: i had the same problem a few months ago. the new version of flash player (youtube = flash) solved my problem, though. if your other sounds (pidgin) are ok, its most likely a flash player/sound server issue.
...try fiddling with the Pules Audio settings in your settings/preferences, i.e. set ALL inputs/outputs to be managed by pulse audio server, not just a few, or use ALSA/jack without Pulse. I found that combining pulse/jack/alsa/flash caused the most problems. There are hundreds of threads concerning sound/flash issues, just search for "flash sound" etc.

---

### Post by lake54 on 2009-06-05
Hey ulgor,

[http://ubuntuforums.org/showthread.php?t=1177233](http://ubuntuforums.org/showthread.php?t=1177233) I created a new thread a short time ago for it - it's not just flash etc.

I think I must have tried every combination!

I still haven't managed to get Ubuntu to install to an external HDD, but if I do I'll let you know how I did it.

James

---

