---
title: "CD/DVD drive will not work"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by ZaphodNE on 2007-04-17
OK gang, how the hell does a CD drive simply stop working.  I have a clean install of Edgy.....the drive worked perfectly fine....now it's dead.

I blame XGL / Beryl but that's only a guess.

Can someone please, please explain how to get this drive working again.  A reinstall of Edgy is not an option.  I'll just go back to Windows as this kind of stuff is CRAP!!!

There is an entry in /media/cdrom0....like that means anything to me.

fstab has nothing at all regarding a cd drive.

Frustrated as hell.....if someone has a cooler head than mine I would truely appreciate their guidance.

thank you in advance!

---

### Post by Zwalther on 2007-04-17
I think it's highly unlikely (almost impossible) that it has anything to do with beryl/xgl.

You might try some of the following:
1 type 'sudo eject /dev/hdc'. I'm not sure if your drive is /dev/hdc, so you might want to use something else there. This should open/close the tray.
2 type 'sudo mount /dev/hdc /media/cdrom0'. That's a way of manually mounting it. I know that's not what you want in the end, but it will give you more information on why it doesn't work automatically.
3 Are all the cables connected ok? (I'm not kidding you, I've seen sponaneously (slightly) disconnected cable more then I can count. Especially if you've assembled the machine yourself. They usually look fine until you press them hard on the motherboard or disk again.)

If you have any more information, just post it here again.

---

### Post by tommcd on 2007-04-18
Can you post your fstab? You should have something like:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

If not, then just add it in with 'gksudo gedit /etc/fstab'
EDIT: you don't ned to worry about the UUID stuff. Your fstab will work fine without it.

---

### Post by ZaphodNE on 2007-04-18
Just added the suggested /dev/hdc line to fstab, but it had no apparent effect after a reboot.  Inserted an audio CD, which shows up on the desktop.  Sound Juicer locks up after hitting the Play button.  CD Player will not start at all.  Of course, cannot play a DVD.

I'm completely confused.

Here is my fstab.......

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce9e3a18-9f43-4628-be59-c84f2ec62357 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9bd79a41-3ce9-40be-926b-61a1b576fa06 none            swap    sw              0       0
/dev/hdc       /media/cdrom0   udf,iso9660 ro,user,noauto     0       0

---

### Post by ZaphodNE on 2007-04-18
[dmccoll@Ubu /etc]$ sudo eject /dev/hdc
Password:
eject: unable to find or open device for: `/dev/hdc'
[dmccoll@Ubu /etc]$ sudo mount /dev/hdc /media/cdrom0
mount: special device /dev/hdc does not exist

WHAT IS A SPECIAL DEVICE???

fstab looks like this............


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ce9e3a18-9f43-4628-be59-c84f2ec62357 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9bd79a41-3ce9-40be-926b-61a1b576fa06 none            swap    sw              0       0
/dev/hdc       /media/cdrom0   udf,iso9660 ro,user,noauto     0       0

---

### Post by Zwalther on 2007-04-18
I'm not sure why mount calls it a special device. But the files in /dev/ are your devices. Your harddisk is /dev/sda and your soundcard could for instance be /dev/audio. (Don't try to write data directly to those files because it will mess up your hardware or your partitions.)

Ok, so your dvd drive is probably not /dev/hdc. That's why adding that line to your fstab didn't work.

I'm not exactly sure how to find out what your cd drive is. Try 'ls /dev/hd*' and 'ls /dev/sd*'. One of these should be your cd drive. /dev/sda is your harddrive.

If you can post the output of those two command here I might be able to say which one your dvd drive is.

---

### Post by tommcd on 2007-04-19
Do what Zwalther said to identify your cdrom. The /dev/hdc I gave you was just a generic (although typical) example. You may have to change it to what your cdrom is actually identified as. Also, make sure you have a mount point at /media/cdrom0. If you don't, create it with "sudo mkdir /media/cdrom0" (that's a zero and not the letter O). When you put in a music cd an icon pops up on the desktop. The disc is being mounted then. What happens if you insert a data cd? Can you open it?

More troubleshooting:

Run "sudo cdrecord -scanbus"
from "man cdrecord"
"  Scan  all  SCSI devices on all SCSI busses and print the inquiry strings. This option may be used to find  SCSI  address  of  the CD/DVD-Recorder  on a system.  The numbers printed out as labels are computed by: bus * 100 + target"

You should get something like:

scsibus3:
3,0,0   300) 'LITE-ON ' 'DVDRW SHW-160P6S' 'PS01' Removable CD-ROM
3,1,0   301) *
        3,2,0   302) *
        3,3,0   303) *
        3,4,0   304) *
        3,5,0   305) *
        3,6,0   306) *
        3,7,0   307) *

Also, insert a cd and run "dmesg | tail" This may give errors about the drive that you can (hopefully) google to find out what is wrong.

Try running rhythmbox from terminal, and try to play a cd. This may output errors to identify the problem.

---

### Post by ZaphodNE on 2007-04-19
First off, many thanks to both Zwather and tommcd for hanging with me.  I love the whole Ubuntu concept, and both of you exhibit it to the max.  I have an Ubuntu friend here at home and we've been toying with the idea of 'getting involved'.....the two of you have probably inspired me to do just that.  Again, thank you!

Back to the issue.............

Here is output is output that Zwalther requested..........

[dmccoll@Ubu /etc]$ ls /dev/hd*
ls: /dev/hd*: No such file or directory
[dmccoll@Ubu /etc]$ sudo ls /dev/hd*
Password:
ls: /dev/hd*: No such file or directory
[dmccoll@Ubu /etc]$ sudo ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5
[dmccoll@Ubu /etc]$ sudo ls -al /dev/sd*
brw-rw---- 1 root disk 8, 0 2007-04-18 18:27 /dev/sda
brw-rw---- 1 root disk 8, 1 2007-04-18 18:27 /dev/sda1
brw-rw---- 1 root disk 8, 2 2007-04-18 18:27 /dev/sda2
brw-rw---- 1 root disk 8, 5 2007-04-18 18:27 /dev/sda5
[dmccoll@Ubu /etc]$ sudo ls /media
cdrom  cdrom0
[dmccoll@Ubu /etc]$ sudo ls -al /media
total 12
drwxr-xr-x  3 root root 4096 2007-04-16 16:20 .
drwxrwxrwx 21 root root 4096 2007-04-10 15:50 ..
lrwxrwxrwx  1 root root    6 2007-03-23 14:20 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-03-23 14:20 cdrom0

Regarding the question from 'tommcd', everything I put into the drive (CD/DVD/data CD) shows up on the desktop.  Data CD (in this case .jpg files and .pdf files) are recognized and read perfectly.  Applications start as expected in both cases and work flawlessly.  Audio and video is completely down.  But Edgy does understand that something has been inserted in the drive in all cases.  Hate to bring it up again, but this is why I blame XGL / Beryl.  They managed to trash my VNC4 connection as well.....that I know for a fact.

tommcd.......I'll work more on your further debugging suggestions later tonight.

Again to you both.....many, many thanks!!

Oh, the Big Island is the ONLY island!!!  It just rocks!!

---

### Post by Zwalther on 2007-04-19
It nice to a an inspiration to someone sometimes. My wife and my little sister always tell me I'm just annoying so I think I'm gonna send them your post :)

It seems I misunderstood your problem and you might be right about XGL. I (and I think tommcd) understood you didn't see your drive at all, but now I understand you can read data cd's.

That probably means that your problem is not your drive but that you can't play movies. Can you play other kinds of movies from the internet or for example on your harddisk in "/usr/share/example-content/Experience ubuntu.ogg"? That might have to do with XGL after all. It is possible that you need to take some steps to get video's working with your video card and beryl. Didn't the beryl install howto's say anything about this?
If you can, you should upgrade to feisty. It should all work better there anyway. It probably has newer drivers for your videocard.

And you're right: the Big Island is absolutely the best. (Although I've been to Kauai a couple of weeks ago and I must say it's a very good runner up :) )

---

### Post by ZaphodNE on 2007-04-20
I'm going for the Feisty upgrade......clean install, no upgrade since  my Edgy install is clean and I have nothing I care about to preserve.  It'll be a hassle to reinstall everything, but I'm just stymied with the cd/dvd drive at this point.....nothing I do will make it work.....it's just gone.

Again, many thanks to you both......Aloha and Thank You Philly!!!  You're the best!

---

### Post by ZaphodNE on 2007-04-20
Mahalo, Bro....thank you very much!!

---

### Post by ZaphodNE on 2007-04-21
Again to both Zwalter and tommcd....thank you!!

Somehow found myself upgraded to Feisty (I'll spare you the gory details) but seem to be in good shape now.


Be real, enjoy life, thanks for helping!!

---

### Post by dag0 on 2007-04-23
I jump into this too ;-)

I also have some problem with cd/dvd on my laptop (HP pavilion zt3000 serie, it says zt3420EU) . When i insert the media I get this: 
[COLOR="Red"]Cannot mount Volume. Invalid mount option when attempting to mount the volume,[/COLOR]

[COLOR="Black"]Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4a5c7f37-e54c-461d-8777-4be03db68ef0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b0bca30f-4427-4ceb-9036-cf85c7f2adba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope someone can help me :-) I use Ubuntu 7.04 


And I also get this:
 sudo mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm a newbie but i really like to use Ubuntu 

Best Regards
DAG
 [/COLOR]

---

### Post by Zwalther on 2007-04-23
Hi DAG,

You have a different error. There has a bug been filed ( [https://bugs.launchpad.net/ubuntu/+bug/106910](https://bugs.launchpad.net/ubuntu/+bug/106910) ) that looks like your problem.

Did you try looking at the last lines of the output of 'dmesg' just after a mount error?

Is it an OS X cd? Then look here for the fix: [https://bugs.launchpad.net/ubuntu/+source/pmount/+bug/65534](https://bugs.launchpad.net/ubuntu/+source/pmount/+bug/65534)

---

### Post by dag0 on 2007-04-23
ok..
Sorry if this is wrong thread...

I get this msg at the bottom at dmesg:
[ 9809.876000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

I notice this when I try to burn a DVD-R with K3B program..Have not tried the cd/dvd before now when i tried to burn a DVD-R.


I just try the DVD-R I made with the Ubuntu 7.04 from iso file and that is working. I can brows the folders it works normal. The reason is the I can't use cd-r or ordenary cd's in the unit (broken) but this has not been any problem before.

And with earlier versions of Ubuntu and even (SimplyMEPIS, when I was waiting for Feisty Fawn) it worked as normal...

I have no osX stuff...

Thanks for reply :-)

DAG

---

### Post by Zwalther on 2007-04-23
I'm not sure if I understand what your problem is.

You say you can read a dvd that was made with the Ubuntu 7.04 iso that you downloaded, right? So I guess reading dvd's works fine.

But you can't read a cd? Or do you have problems writing cds?

If you can't read cds, it probably the bug in the link and you should wait until that gets fixed by someone else (or you :) )

If you have problems writing cds/dvds then I'm not sure if I can help. Did you try writing one with nautilus (in gnome, right-click on an iso and select 'write to disc'). Nautilus has less options that you can mess up :)

---

### Post by dag0 on 2007-04-24
I get the message: Cannot mount volume when I insert a emty DVD disc.
I can play movies, both region 1 & 2 so this works perfect.


Maybe I explained little difficult earlier, I'm norwegian and not so good in english :-)


Thanks for your reply

Dag

---

