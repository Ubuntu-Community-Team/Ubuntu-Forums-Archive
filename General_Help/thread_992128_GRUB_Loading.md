---
title: "GRUB Loading"
date: 2008-11-24
forum: General Help
---

### Post by mitso on 2008-11-24
I installed UBUNTU 8.04  on a computer with
a 160g drive in 4 equal partitions. I let uBUNTU
decide where to install - it picked partition 3.
I can only see partitions 1&3. It is the only system
on the computer.
DOS sees all 4 and reports nothing installed on any.

It has been running flawlessly every day for more than a month including all the updates.

This morning I booted Partition Magic by floppy to
check on the partition. It shows all the details
with nothing on partitions 1,2,&4.
I didn't run any of the PM programs.

When I tried to go into UBUNTU, I see:

"GRUB Loading stage1.5...

 Grub loading.   please wait...
 Error 17"

This has never shown before. 
I've tried several times in the past 6 hours but it's always the same. I've tried several key combination but nothing affects it. 

Must I reinstall and make sure it goes into the first partition ?

---

### Post by oilchangeguy on 2008-11-24
> **mitso said:**
> I installed UBUNTU 8.04  on a computer with
a 160g drive in 4 equal partitions. I let uBUNTU
decide where to install - it picked partition 3.
I can only see partitions 1&3. It is the only system
on the computer.
DOS sees all 4 and reports nothing installed on any.

It has been running flawlessly every day for more than a month including all the updates.

This morning I booted Partition Magic by floppy to
check on the partition. It shows all the details
with nothing on partitions 1,2,&4.
I didn't run any of the PM programs.

When I tried to go into UBUNTU, I see:

"GRUB Loading stage1.5...

 Grub loading.   please wait...
 Error 17"

This has never shown before. 
I've tried several times in the past 6 hours but it's always the same. I've tried several key combination but nothing affects it. 

Must I reinstall and make sure it goes into the first partition ?

first, what makes you think you're using dos? when will people understand that a black background and white text is NOT dos!! second, why are you using partition magic to check on your partitions? you already know there's nothing on three of them. and is there a special reason you have your hard drive split into four sections? i'd suggest just having one partition. and use the partition manager on the live cd, not partition magic.

---

### Post by daz23 on 2008-11-24
Try to fix your boot issue with Super Grub Disk boot cd 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by cariboo on 2008-11-24
Go here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download which ever version you want and boot off of it, this will help you sort out your boot problems.

Dos can not see Ext3 partitions, Windows can with a third party add on such as this:

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Jim

---

### Post by mitso on 2008-11-24
First of all, I have been using DOS since Heathkit
started HDOS and IBM started PCDOS and Microsoft
started DOS. That's about 20 years - I know DOS.

I prefer having operating system on 1 partition and
my stuff on separate partitions- for some 20 years.
Is there anything wrong with that ?

My question  is how do I get rid of GRUB and get into UBUNTU? THat's what I'm asking. Not the
advantage or disadvantage of partitining. I also
want to uae all my partitions

---

### Post by oilchangeguy on 2008-11-24
> **mitso said:**
> First of all, I have been using DOS since Heathkit
started HDOS and IBM started PCDOS and Microsoft
started DOS. That's about 20 years - I know DOS.

I prefer having operating system on 1 partition and
my stuff on separate partitions- for some 20 years.
Is there anything wrong with that ?

My question  is how do I get rid of GRUB and get into UBUNTU? THat's what I'm asking. Not the
advantage or disadvantage of partitining. I also
want to uae all my partitions

your present computer does NOT have dos on it. again black background and white text does not mean it's dos. and you can't get rid of grub (grand unified boot loader) and expect to get into ubuntu.

---

### Post by mitso on 2008-11-24
Thanks jaz23 and cariboo907. Sorry I didn't see
your posts before I sounded off a bit. I don't usually.
I really didn't want to reinstall, it has gone 
so smoothly I didn't want to disturb anything.
If I could get my 2 "missing partitions" back
it would be perfect. Thanks again you 2.

---

### Post by mitso on 2008-11-24
TO: oilchangeguy:

I have a floppy with windows 98.
It has about 20 programs of all sorts that i have been using since since 1978 on something over 50 or maybe 75 computers I've built. I always have an
"A drive" on every computer I build. It's the
floppy disk in the floppy drive that I use to run DOS.
It would be more helpfull if you would answer the question - as the other responders did -rather than 
show off your limited knowledge.

---

### Post by philinux on 2008-11-24
I didn't think dos could read ext3 file systems. It might know the partitions are there not the file structure. The livecd would be better for that.

---

### Post by oilchangeguy on 2008-11-24
> **mitso said:**
> TO: oilchangeguy:

I have a floppy with windows 98.
It has about 20 programs of all sorts that i have been using since since 1978 on something over 50 or maybe 75 computers I've built. I always have an
"A drive" on every computer I build. It's the
floppy disk in the floppy drive that I use to run DOS.
It would be more helpfull if you would answer the question - as the other responders did -rather than 
show off your limited knowledge.

wow, how did you fit win 98 on a floppy? or do you mean a win 98 start up floppy? even that's not dos.

---

### Post by jerrykenny on 2008-11-24
Can you boot off your installation cd . . . but type "rescue"  at the initial boot prompt ?

Debian cd's have this facility, and will then ask you which partition you have the "rrot" partition installed on, so it can then boot into the installed (on yer hard drive) version

---

### Post by caljohnsmith on 2008-11-24
Did you install Ubuntu with the Live CD? If so, how about booting that up, open a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
That will give some important clues about what is causing your Grub error. :)

---

### Post by lswb on 2008-11-24
The grub documentation says that error 17 happens when grub can see a partition but does not recognize what type of filesystem is installed on it. Older versions of Partition Magic may not recognize linux filesystems so it is prossible that PM tried to "help" by changing something in the partition boot record.

Can you boot from a live CD? If so, open a terminal. It seems likeley that ubuntu was installed in /dev/sda3 from what you have posted. Try this command

e2fsck /dev/sda3 

and answer "yes" to the questions unless they seem really outrageous. If the e2fsck program is not present on the live CD, it is in the e2fsprogs package.

Most likely all your data is intact. Good luck, and sorry about all the grief one of the other respondents had given you.

---

### Post by mitso on 2008-11-24
To philinux:

Yes, neither Dos nor windows can read ext3
that's why I used Partition Magic which can.
My statement that Dos sees all 4 and said nothing
written on them I thought said that.

To oilchangeguy:

You obviously don't know what Dos is so I'll end
that part of discusion.

To Jaz23 & cariboo907

I have my super GRUB Disk but it's giving me
problems I havn't worked out yet. I may be back in
a day or 2 for more help

---

### Post by mitso on 2008-11-24
Thanks all you new guys ! I never thought to boot
from the live CD which I have. I'll do what you suggested and get back to you guys.

Just an aside - I'm too old to get upset about trivia. I started my computer career with an
IBM course in Assembly Language Programing in
1955. Recently at age 88 I've decided I had
enough of Windows and am enbarking on a new
adventure with Linux. 95% of you guys on these
sites are great - a few try to impress with
their limited knowledge. I've seen many such
in my years, and just slough them off.

Thanks again guys.

---

### Post by philinux on 2008-11-24
Yep the livecd takes some beating.

---

### Post by mitso on 2008-11-25
caljohnsmith
 
I finally got into UBUNTU with a Super Grub Disk as
suggested by Jaz23.

But, I couldn't get past the first line of code you suggested.
Here is what I got,


mitso@mitso-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000feda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74172104    37086021    c  W95 FAT32 (LBA)
/dev/sda2        78798825   312576704   116888940    f  W95 Ext'd (LBA)
/dev/sda5        78798888   156296384    38748748+   b  W95 FAT32
/dev/sda6       156296448   157035374      369463+   b  W95 FAT32
/dev/sda7       157035438   231785819    37375191   83  Linux
/dev/sda8       231785883   235079144     1646631   82  Linux swap / Solaris
/dev/sda9       235079208   312576704    38748748+   b  W95 FAT32

Is that enough to make sense of the problem ?

Hope you can find some time to reply.

Thanks again to all you guys for the help.

---

### Post by caljohnsmith on 2008-11-25
OK, since you can boot into Ubuntu OK with the Super Grub Disk, how about doing the following commands:
```
sudo grub
grub> root (hd0,6)
grub> setup (hd0)
grub> quit
```
And please post the output. Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And make sure the "hiddenmenu" line near the beginning has a pound sign in front of it:
```
#hiddenmenu
```
Then reboot, and let me know exactly what happens on start up. We can work from there if you want. :)

---

### Post by mitso on 2008-11-25
Booting with the Super Grub Disk isn't the simplest.
There are several windows(dirty word?)with multiple
lists to go thru.It takes me 3 or 4 times to boot.
Here goes. ( You're pushing me into Bash before I'm 
ready. ROFL)I hit enter after each line - correct?

grub> root (hd0.6)
Error 11 Unrecognized device string
grub>
grub> root (hd0)
grub
grub> quit
Probing devices to guess Bios drives.This may take a
        long time.
        (nothing happens after a long time )
grub>
-----------------------------------------------
gksudo gedit /boot/grub/menu.lst

    (about 100 lines of stuff -1/3 of the way down
there is are 3 lines:
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

-------------------------------------------------

#hiddenmenu

   (nothing)

---

### Post by caljohnsmith on 2008-11-25
Try the Grub commands again, and if you can, it would be good to copy/paste them since you have some typos in the ones you tried (and yes, press enter after each one). Again, please post the results; you can simply copy/paste the contents of the terminal window into your browser. Let me know how that goes.

---

### Post by mitso on 2008-11-25
Caljohnsmith,


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

I haven't tried to boot normally yet, after i saw the proper response
I had to make sure I sent this to you. My problem was - I thought that
was a period between the 0&6. (hd0,6).

I have a copy of this in case it won't bshave and boot properly.

Thanks a billion - nah - maybe a million.

---

### Post by mitso on 2008-11-25
No normal boot Error 17 again.

---

### Post by caljohnsmith on 2008-11-25
Some people in the past have gotten a Grub error 17 because of problems with their HDD cabling; can you open up your computer and simply re-seat the HDD cable to make sure it is snugly secured? And just to check, you haven't changed any of your BIOS settings recently, have you? 

If re-seating the HDD connector doesn't change anything, then you could try installing Grub to the MBR (Master Boot Record) in a slightly different way to see how it will affect your booting problem:
```
sudo grub
grub> root (hd0,6)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
```
If you do the steps above, you definitely won't get a Grub error 17 on start up, because the above steps omit installing Grub's stage1.5 file which is giving you that error; instead Grub's stage1 file in the MBR will point directly to the physical location of Grub's stage2 file needed for booting and loading the menu.lst. So if using the above method doesn't work, you might just get text on the screen that says "GRUB" or something like that on start up, and the computer will hang. Let me know what happens though. :)

---

### Post by mitso on 2008-11-26
Error 17 again !

sudo grub
grub> root (hd0,6)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub>

And this time triple checked my entry.
 I hate to put you thru all of this - would it be better to re-install in partition 1.

---

### Post by caljohnsmith on 2008-11-26
Other than your internal 160 GB drive, do you have any other drives (USB or otherwise) connected to your computer when you start up? Try the following command, but please make sure you get it exactly right, because it can be dangerous if you mistype anything:
```
sudo dd if=/dev/zero of=/dev/sda seek=1 count=20
```
Then reboot, and let me know what happens on start up.

---

### Post by mitso on 2008-11-26
mitso@mitso-desktop:~$ sudo dd if=/dev/zero of=/dev/sda seek=1 count=20
20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 9.1588e-05 s, 112 MB/s
mitso@mitso-desktop:~$ 


Error 17 again. Sorry i took so long - had trouble booting.

No other drive. The only usb device is the printer - which I
switch between the 2 computers. I've tried booting with and without
it always error 17..

To review how this happened. I installed Ubuntu about a month ago.
The installation went smoothly. I've used it practically every day since.
I'm "dual booting" with 2 computers and a KVM switch. The only
"problem" was my "missing" 2 partitions.
About a week ago, i decided to try and activate them. I booted
with a floppy in DOS. DOS saw all 4 and said they were empty.
I then booted with a Partition Magic floppy which I knew could read
ext3 files. It saw all. UBUNTU had broken them down further -there
were  FAT and ext3 partitions 9 in all. I removed the floppy and 
rebooted - ERROR 17 !

I checked all connections - they are all secure. The HD is a SATA.

---

### Post by caljohnsmith on 2008-11-26
> **mitso said:**
> 
I'm "dual booting" with 2 computers and a KVM switch.
So what is on your other computer? Does it have Grub/linux too? I think that might be the issue, because I don't see how you could still be getting a Grub error 17 if you are booting the sda drive on start up; with that previous dd command I gave, that should have erased Grub's stage1.5 file, which is the file that was giving that error 17. Just to be sure, how doing the following command:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
```
And then attach the "sda.MBR.gz" file to your next post so I can look at it.

---

### Post by mitso on 2008-11-26
mitso@mitso-desktop:~$ sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
[sudo] password for mitso: 
20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 0.000100248 s, 102 MB/s
mitso@mitso-desktop:~$ 

The other computer has Widows 2000 and nothing else.
It never had any Linux system on it.

I can't tell you how much I appeciate all you are doing.
When you decide it's enough I'll understand.
With many thanks.

---

### Post by caljohnsmith on 2008-11-26
[QUOTE=mitso]mitso@mitso-desktop:~$ sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
[sudo] password for mitso:
20+0 records in
20+0 records out
10240 bytes (10 kB) copied, 0.000100248 s, 102 MB/s
mitso@mitso-desktop:~$

The other computer has Widows 2000 and nothing else.
It never had any Linux system on it.

I can't tell you how much I appeciate all you are doing.
When you decide it's enough I'll understand.
With many thanks.[/QUOTE]
You're welcome, I hope we can get to the root cause of your problem without too much trouble. :) That last command should have created a "sda.MBR.gz" file on your desktop; can you please attach that to your next post? In the Ubuntuforum.org message box in your browser, just click the little paper clip icon at the top of the message box, and you can upload the file. Also, can you make sure your Windows 2000 computer is turned off, reboot, and let me know if you still get the Grub error 17?

---

### Post by mitso on 2008-11-26
I saw the sda.MBR.gz icon.
When I try to open it,t just gives the size 10 Kb. 
But, I can't find the message box with the little
paper clip.

I want to send this before I try to reboot.

---

### Post by caljohnsmith on 2008-11-26
Actually, I mean that when you type your message at ubuntuforums.org in your web browser to reply, there is a little paper clip icon you can click on to attach a file: 

[IMG]http://img388.imageshack.us/img388/6356/screenshotsr1.jpg[/IMG]

---

### Post by mitso on 2008-11-26
I SEE SAID THE BLIND MAN ! I hope I did it right.

One other thing. When starting to boot, it now start with:

GRUB LOADING STAGE 2  Before your efforts it was Stage 1.5

The second window that comes up is still:
Error 17: Cannot mount selected partition.

With the Windows computer turned off its Stage2 & error 17.

---

### Post by caljohnsmith on 2008-11-26
Well it looks like Grub is correctly installed to the MBR (Master Boot Record), and the fact that Grub tries to load stage2 would confirm that; I think you might actually have a hardware issue, maybe with your [HDD's cabling]("http://ubuntuforums.org/showthread.php?t=768101"), because that has caused Grub error 17 for other people in the past. Can you open up your computer and re-seat the HDD cable? Or is there any chance you can swap that drive out and try booting it in another computer? I don't think reinstalling Ubuntu will help at this point; I think you will most likely end up with the same Grub error.

---

### Post by mitso on 2008-11-26
I did check the cabling - its all tight,

This is one of the mysteries of the computer world,

I'll let it sleep till tomorow and then decide what to do,

I thank you ever so much. One thing I'm sure of Ubuntu is with me
to the end. 

I'm also sure I'll be back with more questions.

One last question - is there a good book to learn Bash ?

Again, I can't thank you enough.

---

### Post by meierfra. on 2008-11-26
Just to help with the diagnosis:

Boot from the Super Grub CD. At the first Super Grub menu press "c". Post the output of

```
find /boot/grub/stage2

find /boot/grub/menu.lst
```

(Press "Esc" to get back to the Super grub menu).

Also  could you describe which of the Super Grub options lets you boot into Ubuntu?

---

### Post by mitso on 2008-11-26
HI meierfra,

the results for both was the same:

(fd0)
(hd0,6)

To boot from the Super Disk is "hit and try">
I hit "enter" on 3 consecutive windows -
each window has several lines. I must pick
the proper line - sometimes I get back to the preceeding
window and have to hit the same line 2 or 3 times.
I haven't fully resolved it yet. 

I hope this anwers your questions

---

### Post by caljohnsmith on 2008-11-26
About a good book on bash, I don't know of any off-hand, but here are a few Websites that have some good tutorials and info on bash scripting:

[http://www.linuxcommand.org](http://www.linuxcommand.org)
[http://bash-hackers.org/wiki/doku.php](http://bash-hackers.org/wiki/doku.php)
[http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)
[http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)
[http://bash.cyberciti.biz/](http://bash.cyberciti.biz/)

Also, one option to get around your booting problem would be to make your own Grub boot CD that would either have your Ubuntu's menu.lst, or point to the current menu.lst in your Ubuntu partition; you would boot the CD and get the Grub menu that you should get if booting your HDD worked. If you want help with that, just let me know and I'll type out the steps. :)

---

### Post by mitso on 2008-11-27
First of all, I want to thank all you guys and\or
gals - especially caljohsmith - that contributed to
my UBUNTU experience. I suspect the problem is a
program glitch not any physical damage to the drive.

1. It installed and ran perfectly for over a month.
2. It only saw 2 of the 4 partition
3. I booted with a floppy. DOS saw 4 all original
   but empty.
4. Ubuntu booted normally after that.
5. A day or so later I booted with floppy and ran
   Ghostpe 2001. It showed 9 partition of different sizes but not which were FAT or ext3.
6. Ubuntu booted normally after that.
7. A day or so later I booted with a Partiton Magic
   floppy. It showed all 9 and which were FAT or  ext3.
8. I didn't run any of the PM programs.
9. I removed the floppy- rebooted - Error 17 !

I really want a clean installation of UBUNTU. If
I have to reinstall so be it. Booting with a floppy 
is really a crutch.
Thanks again for all the help I'm even more anxious than before to get into BASH.
One thing I'm sure of:
     I"LL BE BACK FOR MORE ADVICE!!

---

### Post by lswb on 2008-11-27
Just FYI, once you have things sorted out, there is a very good downloadable bash tutorial called the Advanced Bash Scripting guide available as either html or pdf. It is even available in ubuntu repositories, search for "abs" in synaptic. The repository version is usually a little out of date, you can get the latest at the authors web site,

[http://personal.riverusers.com/~thegrendel](http://personal.riverusers.com/~thegrendel)

You'll need to start a browser and view the index.html file in the appropriate directory to view it after installation. The repository version gets installed in  /usr/share/doc.

---

### Post by mitso on 2008-11-28
Thanks lswb. Another helpfull response ! I've had
over a dozen helpfull responses and only 1 
negative. That's not bad odds ! I've been dealing
with techies on the internet since it's begining
and I've found that to be about normal. NOT BAD !
Thanks again to all, I'll be back.

---

### Post by mitso on 2008-12-02
I can't say SOLVED to the GRUB problem, but I can say solved to the the problem that put me into the GRUB problem - the search for my "missing" partitions.
I re-installed with manual partitioning - all went smoothly. None of the partitions were listed anyplace I could see. But, with even my limited BASH exposure I was able to use fdisk and /etc/fstab
and find them.
Many thanks again to all you guys !

---

