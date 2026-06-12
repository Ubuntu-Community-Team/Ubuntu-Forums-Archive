---
title: "Dual boot won't boot to linux!"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by gravediggers on 2006-01-09
Hi,

I actually had this going on another thread that was a sticky relating to something else (I swear it was an accident!), so I thought I'd do the right thing and start my own! I am actually installing Debian Sarge 3.1 on this machine ('cos I've already got Ubuntu breezy on another machine), but I may consider Kubuntu (pick up the CD's tomorrow).

The original posts were:

> A lot of the other threads I have read recently re dual boot seem to claim that GRUB won't find OS on a 2nd drive. You obviously don't have that problem!

I am just about to (this weekend??) install linux (Sarge - no point have Breezy on both machines) on my new sata drive I have just installed into my windows box. Windows is on the 80GB PATA IDE Master (2 NTFS partitions), while the SATA is mainly extra NTFS, but has 10GB FAT32 for sharing, and about 43GB (unallocated at this point) for Linux. This sound similar to what you've done, except it sounds like you have ubuntu on the first hd and winxp on the 2nd, and you're 2nd hd is PATA whereas mine is SATA. Do you foresee me having any problems?

and  later:

> Well, I installed Sarge on my freespace on the SATA and when it got to the part to install GRUB, I chose to install it to hda1 (my winXP primary patition). When i rebooted I expected it either to work (see both OS) or boot into WinXP. However I got
Loading GRUB
Hard disk Error (or some similar cryptic message)
Oh well! Try 2 .....

This time loaded GRUB in Linux / (ie, sda3)
Rebooted to live CD......
sudo mkdir /mnt/fat32part
sudo mount /dev/sda2 /mnt/fat32part (sda2 is my fat32 partition)
then.........
sudo dd if=/dev/sda3 of=/mnt/fat32part/bootsect.lnx bs=512 count=1
reboot to WinXP
Copied bootsect.lnx to C:\
edited boot.ini to include last line
c:\bootsect.lnx="Sarge 3.1"
Reboot....
On boot get the choice - use "Sarge 3.1"...
get GRUB Geom Failed.

I think the strategy is correct, but think there is a basic error with instaling GRUB.

I then checked out some some grub documentation (it's a lot to take in) as well as other other posts for similar on this and other forums. One person getting GRUB Geom Failed found by setting framebuffer=false during install fixed the problem, but it didn't for me.
The GRUB documentation related that error to GRUB being installed incorrectly even though the installing software may think the installation was successful. This basically alligns with what I felt was the problem anyway.

Now, there are 100 ways to skin a cat, and I know some of you would have attacked the dual boot a different way to suit your own systems, and your individual needs. However, the way I'm trying to do it suits me, so don't just knock it because you've done it different. By the same token, I'm willing to change the methodology if the reasoning is good.

So:
1) Is there a basic error with what I a doing?
2) Is there an easy way to install grub manually (the documentation is a little bit heavy!).
3) If I changed to boot to the drive with linux on (i think i have to choose SCSI in BIOS????), would this help. I obviously still have to manually load GRUB.

If anyone has any thoughts (or bad experiences now resolved) then I'd be glad to hear!

Just to recap my setup:

hda1 Primary IDE Master NTFS WinXP (This is what my BIOS currently boots to with ntloader)
hda2 NTFS my work area
sda1 SATA drive NTFS
sda2 FAT32 common area
sda3 where linux is installed

---

### Post by gravediggers on 2006-01-09
No replies yet to my last post - can anyone help?

Have just been doing a little reading on some other posts and was going to do the following to reinstall GRUB to boot partition of my linux installation.
in terminal $ *grub*
at grub prompt *grub> setup (hda1,2)*        my sata drive is my 2nd drive boot is partition #3
*grub> quit*

then as in my above post, copy the first 512 bytes as a file to by c: drive

Does this sound right?

---

### Post by gravediggers on 2006-01-10
Begging for help - please!!!

grub> find /vmlinuz
 (hd1,2)

grub> setup (hd1,2)

Error 12: Invalid device requested

grub>

/dev/sda3  (hd1,2) is my boot partition.

---

### Post by gravediggers on 2006-01-10
Ok

```
grub> root (hd1,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub>
```

How come it says "Filesystem is ext2fs..." when it is ext3?

---

### Post by gravediggers on 2006-01-10
Guys,

I'm getting very disillusioned with this!:mad: 
Will consider a gender adjustment if if that will help! - LOL!

After doing what I did in the last post, I copied the first 512B to a file, put it in C:\ and edited boot.ini as mentioned earlier. Rebooted, chose Linux and got 'GRUB Geom Error'.

Any help?:confused:

---

### Post by Kipper on 2006-01-10
I hate to say this, but did you do the obvious and "Google" on "GRUB Geom Error"?  I got 13,500 hits, so someone somewhere has been there and got the same problem. 

Personally, I did'nt make much sense of the explanation of the GRUB error message which you can find here: [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

At first sight, there seems to be nothing wrong with your strategy. Which, if I've understood your posts correctly, is to use Windows NTLDR as your boot mechanism and have a menu entry which should load GRUB and hence enable you to boot your Linux install(s). 

But I would ask was there any particular reason you did not simply install GRUB on the MBR of your SATA drive? I know this means changing the boot order in your BIOS, and creating an entry in "meun.lst" to chainload and boot your XP install, but it will get you going with a dual boot system as opposed to beating your head against the wall over this problem.

To be honest, I cannot see why it's happening. Possilbities are: (a) could be tied up with the SATA controller, (b) Windows XP is choking on your method.

I've done the copy 512 bytes from bootsector of Linux partition to Windows thing myself, and go it to work with Win98 and Win2000, but not tried it with WinXP. 

But now I have adopted the method of having two hard drives, one for Linux only and one for Windows. I set the boot order to boot from the Linux drive, installed GRUB on the MBR of the drive and chainload if I need to boot into WinXP. If I hose GRUB in anyway, a GRUB boot disk or rescue disk should get me out of trouble. WinXP is left alone. If I need to I can change the boot order in my BIOS and boot straight to WinXp.

By the way, there is no such thing as a ext3 grub stage1.5, just e2fs. There is no link between that and using ext3 for your Linux Filesystem that I know of. GRUB sees ext2 and ext3 as the same thing, which they nearly are.

Sorry, I cannot relsove your problem without suggesting a different approach.

---

### Post by Sef on 2006-01-10
Here's what Gentoo's documentation says about GRUB Error 12 and suggest a fix:

> 3. Grub Error 12

Situation

Code Listing 3.1: Grub Output

12 : Invalid device requested.

This error is returned if the device strings syntax is correct but other than that, an error occurred that isn't defined by any other error. 

Solution

When you installed grub in your boot record using the interactive commands, did you execute the two lines below in the grub prompt? 

Code Listing 3.2: Interactive installation commands

grub> root (hd0,0)
grub> setup (hd0)

(hd0,0) must be replaced with your boot partition and (hd0) with the HDD you have chosen. Remember that (hd0) will install the bootloader in the Master Boot Record of the first hard disk, the primary master.

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

I hope this helps you.

---

### Post by gravediggers on 2006-01-10
Thanks guys for the replies.

[QUOTE=Kipper]I hate to say this, but did you do the obvious and "Google" on "GRUB Geom Error"?  I got 13,500 hits, so someone somewhere has been there and got the same problem. [/QUOTE]

Well no, but I did at least read the  GRUB manual to some extent. And I searched this forum for similar GRUB Geom, and as a result tried an install with framebuffer=false (didn't help). I will try a wider search today.

[QUOTE=Kipper]But I would ask was there any particular reason you did not simply install GRUB on the MBR of your SATA drive? I know this means changing the boot order in your BIOS, and creating an entry in "meun.lst" to chainload and boot your XP install, but it will get you going with a dual boot system as opposed to beating your head against the wall over this problem.[/QUOTE]

The installer installed GRUB to the hda MBR the first time, and I should have rebooted to a choice of WinXP or linux. This failed (hard disk failed or similar message) so had to do fixmbr in XP rescue console. The other choice was to load it to an area I specified. Thus I chose /dev/sda3, 'cos that were the boot sector of that isntall is, and I would get to it via NTLDR. Yes, I could have chosen the MBR of the sata drive then added XP to menu.lst, and changed boot order in BIOS, but I didn't.

However, that option is looking worth a try! I might need a little direction though!
 - do I just specify /dev/sda1 when installing, does this get to MBR on 1st sector?
 - as I've already installed, should I just go to grub prompt and
```
grub> root (hd1,2)
grub> setup (hd1)
```
     to install to sda MBR?
- then, if I change the boot order in BIOS to boot to SATA drive, is this now the first drive, and there GRUB pointing to wrong thing?? hd1 now hd0??:confused: 
 - and what to choose in BIOS for SATA (SCSI??) ?


[QUOTE=Kipper]To be honest, I cannot see why it's happening. Possilbities are: (a) could be tied up with the SATA controller, (b) Windows XP is choking on your method.[/QUOTE]
I don't think it XP 'cos the only part of XP to go near it is ntldr. However, I am suspecting you might be right about the sata controller, but how can I tell?

[QUOTE=Sef]12 : Invalid device requested.

This error is returned if the device strings syntax is correct but other than that, an error occurred that isn't defined by any other error. [/QUOTE]

I had looked up that error at the time, and decided that who ever wrote that message must have been a M$ ring in, or a lawyer. Very cryptic!

[QUOTE=Sef]When you installed grub in your boot record using the interactive commands, did you execute the two lines below in the grub prompt? 

Code Listing 3.2: Interactive installation commands

grub> root (hd0,0)
grub> setup (hd0)

(hd0,0) must be replaced with your boot partition and (hd0) with the HDD you have chosen. Remember that (hd0) will install the bootloader in the Master Boot Record of the first hard disk, the primary master. [/QUOTE]

Well, no. I wasn't wanting to write to MBR of first drive, because that's what I did (via the installer) right back at the start.

----------------

Sef - I apologize - I thought you re asking me the question - then I followed your link, and saw that you had posted an excerpt from the guide!

---

### Post by Sef on 2006-01-10
Have you seen this thread:

Written by vnbuddy2002

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Link: [http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto]("http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto")

---

### Post by gravediggers on 2006-01-10
That's actually quite handy! Like doing an install without actually doing it.:) 

However, it is the GRUB step that is the problem. I read through syslog and it says that installing GRUB was suscessful, but when i go to boot it fails

---

### Post by Kipper on 2006-01-11
Hello again, being on other sides of the world means were are not in synch. I'm already yesterday's man as fas as you are concerned. But enough of these philosophical musing and let's get back to the whacky world of dual-boot systems.

I wonder if you have made any progress with what you want to do.

To re-cap, if your Linux install is still on your SATA drive, then installing GRUB in order to attempt to boot it should be (fingers crossed etc.) straightforward.

Sef has posted a possilbe way to use of the &#8220;Linux-expert&#8221; install to get GRUB on your system where you want it. Using the partitioner without formating could be interesting, Can it really be used like that? I always create a floopy boot disk in and addtiion to putting GRUB somehwere on the hard drive. And in the Ubuntu (expert) install you definitely have to &#8220;go back&#8221; and use the bootloader option twice to do this.  

But this method uses &#8220;grub-install&#8221; and I think I would pefer the &#8220;rescue CD&#8221; route and to use GRUB interactively with root(x,y) setup (x,y) quit etc.

Set you system to boot from the SATA disk. GRUB should see the SATA drive as hd0, and your IDE drive as hd1.

Use the &#8220;rescue CD&#8221; method to get to a GRUB prompt (grub>). 

Once at the GRUB prompt, just type the word root, a space,  and a left bracket. Then press TAB. You should see something like:

[B]grub> root (hd
 Possible disks are:  hd0 hd1
grub> root (hd
[/B]

This will show the hard drives recognised. Now type in &#8220;0,&#8221; (a zero and one comma) and press TAB again and you should see a list ot partitions GRUB recognises on the SATA drive (hd0).

If the partition layout looks as you expect, go ahead and install GRUB on the SATA drive's MBR with:

[B]grub> root (hd0,2)
grub> setup (hd0)
grub> quit[/B]

I'm assuming all your GRUB files created by your previous GRUB install actually do reside on partition /dev/sda3. It might be a good idea check that they do before you attempt all this. These commands are saying put the GRUB bootloader in the SATA drive's MBR but look for the second stage boot files etc. on partition /dev/sda3.

RE-boot your system to see if it's finding your Linux Install. You may or may not be able to boot into windows on your IDE drive yet. 

Assumming all is fine. Find and edit the GRUB &#8220;Menu.lst&#8221; file on /dev/sda3.  I would expect this to be in the directory /boot/grub. Either edit any exisitng &#8220;windows&#8221; section or add this:

title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

This should get Windows to boot form your SATA drive's GRUB boot menu.

The only fly in the oinment I can see if the possiblity that yout SATA controller/BIOS does not allow GRUB to function. Incidenty, if you ever clobber /dev/sda3 you have to set up GRUB agian. Hnece it's a good idea to make yourself a GRUB floopy boot disk.

There a good page on all this at [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

I hope this sorts things out, let's know if you have success or otherwise..

PS you might also find this post of interest as if shows you the "rescue + grub-install method" 
[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)

---

### Post by gravediggers on 2006-01-11
Kipper,

Thanks for checking back - yeah, we do seem to be a few hours out of sycnh.

There is a lot in your last post, and I will have to look through it again in more detail at home (at work presently). I will address some of the points now though (not in any particular order).

Yes, the stage 1 and 2 files are in sda3 under /boot/grub.

I haven't tried the method posted by Sef using the installer to get to GRUB, although it sounds very useful. It was easier (and I had more control) using the live cd and using grub in interactive mode.

Ok. The first thing I tried differently this time (2 steps at once to save a lot of rebooting, and loading of live cd) was:
```
grub> root (hd1,3)
grub> setup (hd1)
grub> root (hd1,3)
grub> setup (hd0)
```

so now I should have the bootloader on MBR of both drives and pointing at my linux installation kernel on sda3. Reboot (BIOS bootdevice set to HDD0), with following result:
[I]GRUB loading Stage1.5
GRUB loading, please wait .....
GRUB Hard Disk Error[/I]

Ok. so I reboot (and set boot to SCSI) with result:
[I]GRUB loading Stage1.5
GRUB Hard Disk Error[/I]

Now I try booting from floppy made earlier with something like (from memory):
```
cd /boot/grub
cat stage1 stage2 > /dev/fd0
```
with the result:
*GRUB Loading stage2Read Error*

Ok. so I have a boot floppy that doesn't work, and two bung MBR's. Swap drive boot order back to HDD0, reboot with XP CD, go to rescue console, *fixmbr*.

At this stage, I was certain that I either had a version of GRUB that wasn't compatilble with my chipset(VIA) or BIOS, or it was corrupt. OK, I've got the Kubuntu 5.10 install CD handy, so time to throw away Sarge and go with Breezy (and there was much rejoicing!! - LOL!).

Install went almost sweetly (couldn't connect to the repositories for the extra packages and security updates - will fix post install) and so I got to the GRUB part again. I just chose the default install to MBR of the XP drive. After finishing the install, and rebooting I was back where I was before -
*GRUB Hard Disk Error*

So guess what I will do next is download GRUB (later version) and reinstall it and make myself a decent boot floppy. Thanks for the link to the LINUX Journal article on GRUB - that's great. I will try and get a chance soon to check the other link.

---

### Post by gravediggers on 2006-01-11
Anyone know what version of grub I should download as an safe alternative version to try (i think the version in the current distro is 0.95)? I was thinking of trying 0.97.

Also what is difference between
  grub-0.97.tar.gz 
and
  grub-0.97-i386-pc.tar.gz ???

---

### Post by gravediggers on 2006-01-12
OK. Well forget the last post about GRUB. It was my BIOS that was crappy! I updated to the latest (still 18 months old) version, and it has much better IDE support. After testing that it booted into XP OK (got to keep the wife happy), I booted to the live cd and setup GRUB to hda MBR (WinXP) 
```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,2)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
```
and when I rebooted I got the boot menu with Kubuntu as 1st choice and XP as last choice. Booted into Kubuntu OK and completed the installation. Many thanks to Kipper, Handy, and Sef for the help along the way!

---

### Post by Kipper on 2006-01-12
Ok, "GRUB hard disk error" is explained as:

*The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.*

See here: [http://orgs.man.ac.uk/documentation/grub/grub_14.html](http://orgs.man.ac.uk/documentation/grub/grub_14.html)

Are you using large drives? As I'm just wondering if you should set your BIOS to use LBA on your drives, and if this will cure your problem.

You'll be a GRUB expert when you've finished this.

---

### Post by gravediggers on 2006-01-12
Well, the text of that explains both the errors.
GRUB Hard Disk Failed when I install in MBR, and
GRUB Geom Error when I install else where.

Thanks for you're help on this, and I'm sure that now I've got it working, I'll be able to pass that help on to others.:)

---

### Post by Kipper on 2006-01-12
I'm glad you were able to resolve the problem in the end. Another happy penguin  in the land Oz. It's a fairy tale m8!

---

### Post by gravediggers on 2006-01-12
Thanx 4 the help m8!

---

### Post by handy on 2006-01-12
Ahh... Gravediggers, what a marathon!

Lots of learning in that one.

All's well that ends.  :rolleyes: 

Cheers,

handy

---

