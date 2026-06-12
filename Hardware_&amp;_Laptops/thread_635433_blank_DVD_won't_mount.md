---
title: "blank DVD won't mount"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by Cirrocco on 2007-12-08
bit of an odd one here.

Ubuntu won't mount a blank DVD.
I tried -R +R DL and they all react the same.

it's like the DVD player is looking for a table of contents - it just reads and reads.

If I put in a blank CD I get the prompt to burn a cd, and it shows up on the desktop as blank.

I tried Gnome Baker and K3B but since Ubuntu doesn't recognize it as a blank CD - they don't work either.

/I have a Latitude D830 with a DVD rewritable drive installed
/Gutsy x64

here's the appropriate line from the fstab
```
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec                0  0
```

can anyone help?

---

### Post by Cirrocco on 2007-12-10
OK,

so blank DVD-R, DVD+R, DVD-DL will not mount.
but blank CD+R, CD-R don't have any problems.

and DVDs with stuff on them work fine.

has anyone else encountered this?

---

### Post by bij33 on 2007-12-11
I have the same problem. Blank DVD causes the error message "Invalid mount option when attempting to mount the volume". "Can not mount volume" appears and DVD icon within "Computer" disappears. /etc/fstab looks good....
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Appreciate any help.

---

### Post by Cirrocco on 2007-12-14
I'm not getting any errors...just a disk that spins up and down, over and over.

is there a command to verify what the label on the drive says it is?

I've been through my lspci but I can see anything that says DVD or CDROM

do optical drives even show up in lspci print-outs?

---

### Post by Zwack on 2007-12-14
no, drives don't show up in lspci output.  They are not pci devices.  lshw will pull up more information about your system than you want though...

I hope that this helps...

Z.

---

### Post by geraldm on 2007-12-15
To mount a DVD or CD there must be a filesystem on the disk.  Since blank CDs or DVDs do not have a filesystem, they should never mount.
To write to a blank disk, the filesystem could be created on the hard disk, then populated with files.  Mount that on a loop device to check its contents, and if OK, then you can burn it to the blank, unmounted disk.
After that, the disk should mount with the proper mount command.

---

### Post by Cirrocco on 2007-12-17
OK, maybe 'mount' is the wrong word for it.

when you pop in a blank disk - Ubuntu is supposed to say "hey, that's a blank disk, would you like to burn something?"
or
"I'm not going to say anything, but I'll just go ahead and put a 'blank dvd' icon on your desktop."

mine doesn't do that.
mine does nothing unless it's a blank CD.
If I put in a blank CD, it does what it's supposed to.

---

### Post by JohnnyC44 on 2008-01-25
I have the same/similar problem.  Using a Dell E1505 and Gutsy: no issues with CDs reading or writing or playing DVDs, but when I try to burn a DVD nothing happens.  Tried K3b and it just sets there with the Start button grayed out.  I then used the Gnome CD/DVD Creater app and it keeps prompting me to insert a recordable media.  And the disk won't eject.  I've tried this with several disks and a couple of different brands and get the same result.

---

### Post by JohnnyC44 on 2008-01-31
Anyone?

---

### Post by erdomi on 2008-02-02
I have the same problem:  no recognition of a blank DVD.  CDs work fine, but I'd like to back up a lot of data.  Any help?

---

### Post by The Bishop on 2008-03-10
I have similar problem:  won't mount any DVD, blank or otherwise.  CD's work fine.  I just installed Gutsy on a Compaq Presario V2000.  Glad I didn't "upgrade" the Feisty I run on my eMachine desktop.  Totem plays DVDs on it, no problem, just by loading one up.  Any help to resolve this issue would be greatly appreciated.  Otherwise, I'll have to "downgrade" to Feisty.

---

### Post by JohnnyC44 on 2008-03-24
From all the similar posts I find, this seems to be a major issue with many Ubuntu users and there is no clear resolution to be found in the forums.  And now I'm seeing in posts that the Hardy beta has the same problem.  Can we get a moderator to consolidate these threads and oversee a solution?  Really, not being able to burn a DVD is a big hole in Ubuntu's boat.:(

---

### Post by chromerium on 2008-03-29
I have the same problem. Looks like it is fixed in hardy, however, as I was able to burn a DVD in that.

---

### Post by u4david on 2008-04-22
Same problem.
7.10 
2.6.22-14-generic
any cd FINE
dvd with data FINE
blank dvd in dual boot windows xp FINE
same dvd in ubuntu Blink blink blblblinkblink blinking but NOT RECOGNIZING!!!

---

### Post by paulderol on 2008-04-26
confirmed in gutsy, and now also in hardy. this seems to be a problem with dvd writers, particularly laptops. In my case, the attempt to spin up the dvd will delay grub indefinitely until the eject button is stricken. 


I'm experiencing it on a Thinkpad z60m with ATI graphics and i386 architecture, dvd writer ultrabay drive. About to shift drives in my desktop and i'll see what comes of that. This really does look like a long standing issue that is getting some, but not nearly enough attention. If there is anything i can do, please let me know...

---

### Post by Craigupdegrove on 2008-04-28
I get the same thing in hardy. Why is it so hard to get someone to fix it? my 5in 1 card reader doesnt' work either except for SD cards

---

### Post by badboyz107 on 2008-05-06
Okay so no one is having any luck with this at all?

I just removed my old lite-on cd burner, that ONLY worked with K3b no other burning program worked at all.
Always with the 
"insert blank media" 
problem.

I installed a brand new lite-on dvd burner and now I cant seem to burn cd's or dvd's with ANY program.  

  *-cdrom:0
       description: DVD reader
       product: KOREADVSDVS-LDR DSL-710A 010514A0
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: LT14
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
       configuration: status=nodisc
  *-cdrom:1
       description: DVD-RAM writer
       product: ATAPI DVD A DH20A4P
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 9P57
       capabilities: packet atapi cdrom removable nonmagnetic dma lba                  iordy audio cd-r cd-rw dvd dvd-r dvd-ram configuration: mode=udma2 status=nodisc

I don't know exactly what to do from here.  Anyone else have suggestions??

---

### Post by Zimmer on 2008-05-06
[http://ubuntuforums.org/showthread.php?t=574902&page=2](http://ubuntuforums.org/showthread.php?t=574902&page=2)

---

### Post by dash86no on 2008-05-13
Good morning from Tokyo.

I'm an Ubuntu convert since Gutsy and I'm really loving the OS in general. So much in fact, that I installed Hardy with no Windows Dual Boot. 

I'm using an IBM T40 laptop so of course I've got a few problems, wireless etc. nothing that's such a big deal. However, the problem detailed in this thread is occuring for me too and it's a bit of a show stopper. 

The details:

Can: listen to audio CD, play data CD, read blank CD-R, write to balnk CD-R, read DVD

Can't: Read blank DVD-R (as a result also can't burn)

System: Ubuntu Hardy on an IBM Thinkpad T40. When I get home tonight i'll post output from fstab if that will help.

---

### Post by dash86no on 2008-05-14
Evening chaps.

Output from fstab as promised:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I'm going to do some testing with various media now. To be fair, I haven't used this computer with any other OS other than Ubuntu so I can't rule out this is a hardware thing. I'll get a Knoppix live CD (USB, wouldn't work with cd, right?) running on it tonight to test because the last thing I want is windows contaminating my nice clean Hardy installation. 

Cheers,

Dash

---

### Post by paulderol on 2008-05-14
I have repaired this on my desktop by splitting my cd burner and dvd burner into seperate ide channels. also people may want to check their jumpers. switching them into an equally true position may also work [from master or slave to cable select or vice verse]. If it is the splitting of the channel then this may explain why laptops are having much issue, since they usually kick it on the same channel, do they not? 

anyway, color me relatively repaired.

---

### Post by dash86no on 2008-05-14
I solved my issue too. 

Embarrased to say that my drive does not support DVD burning; got the laptop for free from a friend and never even thought the drive would be anything other than DVD-RW

If anyone's got a spare thinkpad DVD RW drive lying around let me know....

---

### Post by Verdehead on 2008-05-15
I have the same problem in Ubuntu 8.04.  I downloaded the new Fedora-9 and went to burn it to a DVD and it told me I didn't have space on the drive.  Fedora was 3.3G and the drive should hold 4.7G.  I tried both -R and +R disks and got the same thing.  I just bought a new Pioneer DL burner and was going to install it but now maybe I should take it back in the unopened box until this is resolved.

G'day,
Verdehead

---

### Post by JohnnyC44 on 2008-05-20
Well, this issue has now been resolved for me after posting to the Dell Linux forums, and it was a d'oh moment!!!

PhillyFloyd over at Dell had me type this command in a terminal window:

**sudo cdrecord -scanbus**

The relevant output for this purpose is:

[I]scsibus1:
1,0,0 100) 'SONY ' 'CDRWDVD CRX880A ' 'KD09' Removable CD-ROM
1,1,0 101) *
1,2,0 102) *
1,3,0 103) *
1,4,0 104) *
1,5,0 105) *
1,6,0 106) *
1,7,0 107) *[/I]

My optical drive is a CD-RW/DVD -- NOT a burner as I had assumed!
My apologies for wasting anyone's time here. And thanks again for all the support you've given me over the past year.

---

### Post by woollypigs on 2008-05-23
I got the same problem, my laptop (sony VGN-SZ2XP) will read/burn CD's just fine. But it will not see any DVD's at all, blank or burned. The drive is a MATSHITA UJ-832D, and have work just fine in XP, e.g. read/burn CD and DVD's. 

But since I started to use Ubuntu (6.04) the DVD have not worked. Using the sudo cdrecord -scanbus I got this...

0,0,0 0) 'MATSHITA' 'UJ-832D         ' '1.70' Removable CD-ROM

So for me that means that Ubunutu is not using the right driver, since it is a DVD in my laptop.

---

### Post by Darkslight on 2008-06-03
Didn't think there would be an easy fix solution but i was kinda hoping for a solution, alas it seems to be quite a universal problem :(

I've currently got Ubuntu 7.10 on a toshiba satellite laptop

When i try and use the CD/DVD Creator i can put the .avi files in and press 'write to disc' the pop up window for the options comes up fine but press 'write' on it and it comes up with:

'Insert a rewritable or blank disk

Please put a disc, with at least 181.2 MiB free, into the drive.  The following disc types are supported:
DVD+R DL, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+RW, CD-R, CD-RW'

even though there is already a blank dvd in there, i have tried it with multiple dvd's (not cd's as i haven't got any atm)

Earlier in the year my laptop was an XP then Vista machine and it hasn't had any problems writing to dvds until now so i know it's not my laptop as such

Well not much i can do now.. all the best to someone in finding a solution :D, will post again if i find something (chances are not likely =_= )

---

### Post by Alfred_McGee on 2008-06-08
DVDs that I have watched many times before in Ubuntu Hardy suddenly will not mount. I just did a fresh install, too. CDs mount, no problem. Normally, even before you install the necessary DVD software, inserting a DVD will always lead to a sputtering attempt to play it in Totem, or at least to an icon appearing on the desktop, but now I get nothing but some whirring sounds. Do I have a hardware problem on my Acer Aspire 5570z (purchased in September), or was it the latest batch of Ubuntu updates that did this? Actually, it couldn't have been the updates because the problem existed before I reinstalled a single one of them. Last week, Ubuntu updates crashed my wifi card, but reinstalling my OS fixed that... And why is this thread already in the Archives when it is so recent and apparently unsolved?

---

### Post by ariel on 2008-06-09
Same problem in a dell laptop d820.

cdrecord -scanbus  returns

scsibus1:
    1,0,0    100) '_NEC    ' 'DVD+-RW ND-6650A' '102C' Removable CD-ROM


This is the entry in /etc/fstab:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Blank DVDs are not detected. Brasero keeps claiming there's no media inserted. 

Any hint?

---

### Post by soxs on 2008-06-09
Post the output of ```
mount
``` when you put in a cd (wait tilll it is mounted)
I had to change scd0 to hda in order get it working, but it has tobe done according to the output from mount. Copy/Paste is evil.

---

### Post by Alfred_McGee on 2008-06-09
[B]With a CD in the drive, mounted and working perfectly:
[/B]
$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/u/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=u)
/dev/scd0 on /media/cdrom0 type iso9660 (rw,nosuid,nodev,utf8,user=u)

[B]With a DVD in the drive, unrecognized:
[/B]
$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/u/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=u)

**Question**: Is this a hardware failure? Is there any other way it could possibly have endured through a reinstall of Hardy?

Update: I went to System-> Administration-> System Log, then put in a DVD. I got 

Kernel [...] sr: Sense Key: Hardware Error [current]
Kernel [...] sr: Add. Sense: Tracking servo failure

If there's anyone who thinks this might NOT be a hardware problem, I would love to hear from you, but I won't hold my breath.

---

### Post by soxs on 2008-06-10
It's at least no software error as the mountpoint is correct and cd is working. Cleaning you lense might help, otherwise you will need a new one..

---

### Post by Alfred_McGee on 2008-06-10
But if a dirty lens were preventing DVDs from even mounting, wouldn't there be a problem playing CDs as well?

---

### Post by soxs on 2008-06-11
CDs have a much larger physcial "filesystem" so a dirty lense *may* be able to still read cds. It is possible, but very unlikly, it was just a thought, but as you say, it seems to be extremly unlikly. So I suggest to get your hand s on another cd-drive.

---

### Post by paulderol on 2008-06-12
i thought we had determined that this was NOT a hardware issue, as it has something to do with the particular dvds, rather than the reader. How many of these are laptops that are sharing a channel between hard drive and optical drives? [i mentioned earlier that a brand new dvd writer drive did not work until it was seperated from the other optical and hard drives.) i don't know if this has anything to do with it, but my desktop does now play dvds of all kinds, while my laptop alternately does and does not play certain dvds, and attempts to spin them up during startup, and cannot boot until then. 

Is anyone else having this problem with the dvd drive precluding grub until the disc is ejected? is it possible to produce debug messages from pre-grub states, i.e., how can i produce an output of the dvd drive trying to read the disk before Grub starts?

---

### Post by soxs on 2008-06-13
The spinning up at boot time ic caused by the bios and your default boot order. I guess your boot order is floppy-cd-hd, at least *-cd-hd-*

Did you try ejecting the cd before booting and inserting it again when logged in?
And what kind of DVDs do not mount?

---

### Post by paulderol on 2008-06-13
i have the boot order as cd-hd on my laptop and cd-dvd-hd [or dvd-cd-hd] on my desktop.the desktop is fine. as far as the laptop--it will recognize neither blank dvds nor some burned ones, and it won't read dual layer dvds, but it's not designed to do that, cds work splendidly, aside from periodic i/o errors which are corrected with a remount... 

when i eject it and put it back in after startup it tries to spin it up again, to no conclusion. 

when i get to my laptop after coffee, i'll try to mount one and pull a dmesg from it for ya, as well as the lines from fstab.

any thoughts on why splitting the ide channels worked on my desktop?

---

### Post by soxs on 2008-06-13
Maybe splitting ide channels worked, as you did put 2x masters at a cable or a jumper was defect and did not work anymore (so in that case probably 2 slaves at one IDE lane)

---

