---
title: "NTFS can't be mounted"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by Kanafani on 2006-10-18
Hello.

I've recently installed ubuntu at my school computer, which's primary operating system is win xp. Problem comes when mounting the ntfs parition. I've no expirence of ntfs in linux, since I've only got linux at home.

The parition is listen in nautlius in the "Computer" "folder".

I'm using a swedish version of ubuntu, so this is a rough translation of what's happening when you try to open the partion.

"Can not mount the selected volume.

error: unit /dev/sda2 is not unmountable
error: could not execute pmount"

For those who know swedish and think they could translate it more accurate here's the original text:

"Kan inte montera den valda volymen.

fel: enheten /dev/sda2 är inte löstagbar
fel: kunde inte köra pmount"

I've tried the guides at ubuntuguide.org, but that didn't solve things.

---

### Post by xyz on 2006-10-18
Hi-
Would this HowTo make it clearer for you?

"Mounting Windows Partitions in Ubuntu"
[Psychocats]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by wislon on 2006-10-18
Alternatively, check out ntfs-3g? Do a search on the forum here, there's an excellent HOWTO somewhere here.

---

### Post by xyz on 2006-10-19
> **wislon said:**
> Alternatively, check out ntfs-3g? Do a search on the forum here, there's an excellent HOWTO somewhere here.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
[http://www.ubuntuforums.org/showthread.php?t=255896](http://www.ubuntuforums.org/showthread.php?t=255896)

---

### Post by masterK on 2006-10-31
hey guys, i'm quite new with ubuntu.
i have a very big problem, i searched all over this forum but couldn't find it.. :
i can see my ntfs partition but cannot open it..it gives this message: you don't have enough authority to acces "disks-conf-hda3" (i translated it from dutch it's something like this:P) 

how can i acces it?

thanks in advance

---

### Post by xyz on 2006-11-01
> **masterK said:**
> hey guys, i'm quite new with ubuntu.
i have a very big problem, i searched all over this forum but couldn't find it.. :
i can see my ntfs partition but cannot open it..it gives this message: you don't have enough authority to acces "disks-conf-hda3" (i translated it from dutch it's something like this:P) 

how can i acces it?

thanks in advance
Hi masterK,
It's nice to see you "searched" the forum for an answer to your question but how about starting with the links suggested in the above posts.
If you still have a problem then, feel  free to ask.

---

### Post by masterK on 2006-11-02
well, that is the problem:P i still have problems..
plz help me out :S

---

### Post by masterK on 2006-11-02
update: i installed ubuntu again, but now with internet, and it had quite a lot updates, now i could see my drive, even with the windows name(music - clips - movies). now i tried a link somewhere here, i think the lowest link here above, and now i can't see it on my mainscreen anymore.. i can still see it in locations-computer though. now it gives a message that i can't translate, sorry:P something about that it cannot mount it, can only mount in root or something... what can i do to just listen to the music on this partition? (ps. i got 1 hd, 3 partitions, 1=linux, 2=music - clips - movies, 3=swap partition..)
hope it can be fixed, thanks.

---

### Post by xyz on 2006-11-02
Your first question is : NTFS can't be mounted?
Your second (and main interest) is : what can i do to just listen to the music on this partition?

My question is (that's what I need to understand to be able to help):
[A problem understanting this?]("http://www.psychocats.net/ubuntu/mountwindows")
In order "to just listen to the music on this partition", you need to do what's explained in the above link. I'm not sure about this but is there something you don't understand in the HowTo?
Let us know a bit more clearly! Thanks.

---

### Post by masterK on 2006-11-05
haha, ok, thanks anyway, i'm gonna try it right now.

---

### Post by masterK on 2006-11-05
well, i did exactly what was said. at the very last command(sudo mount -a) i got this error:

error opening partition device: apparaat of bron bezig
failed to startup volume: apparaat of bron bezig
failed to mount '/dev/hda3': apparaat of bron bezig
mount is denied because the ntfs volume is already exclusively opened. the volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser'command.

(translation of "apparaat of bron bezig" = device or source busy)

thanks

---

### Post by masterK on 2006-11-06
please help me out on the above post...

thanks in advance!

---

### Post by masterK on 2006-11-08
so i think no one is gonna respond on this, probably too hard.. well thanks anyway, i'll just stop using ubuntu

greetz

---

### Post by givré on 2006-11-08
Hum, did you reboot ?

---

### Post by masterK on 2006-11-14
> **givré said:**
> Hum, did you reboot ?

yeah i did. still nothing:neutral:

---

### Post by xyz on 2006-11-15
I already gave you that link
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
and I need to know if you were able to follow that guide.

If this (translation of "apparaat of bron bezig" = device or source busy) is true, it usually mean your partition is mounted. You need to umount it before you can change the permissions which is what you need to be able to access it.

Again take a look at the above link and try to ask us more precise questions if you don't understand something.

Are you OK with command line/terminal? If yes then post the output of the following command line in your next post:
```
sudo fdisk -l
```

---

### Post by Compaq Armada 7800 on 2006-11-15
deffinately install the ntfs kernel module. if it comes down to this... "smbmount (location)"

---

### Post by masterK on 2006-11-16
eh, what can be in place of location? if it's /windows, or /dev/hda3, than the command doesn't work;)

---

### Post by masterK on 2006-11-16
the output:

Schijf /dev/hda: 81.9 GB, 81964302336 bytes
255 koppen, 63 sectoren/spoor, 9964 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1            9243        9964     5799465    5  Uitgebreid
/dev/hda3               2        9242    74228301    7  HPFS/NTFS
/dev/hda5            9243        9838     4787338+  83  Linux
/dev/hda6            9839        9964     1012063+  82  Linux-swap / Solaris

Partitietabel ingangen zijn niet in schijfvolgorde

sorry, i installed ubuntu in dutch by exident.

maybe if i reinstall, and do everything over again, would that help?
i wan't it in englisch anyway;)

---

### Post by xyz on 2006-11-17
Hi-
Can you please also post the out put of:
```
sudo gedit /etc/fstab
```
"/etc/fstab" is the file that shows you how (if) your partitions are mounted, meaning accessible.
This is mine, for instance:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**/dev/hda2**       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda1**       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0      


**/dev/hda3**       /media/hda3  vfat iocharset=utf8,umask=000 0 0    
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


The line beginning with "/dev/hda2" is my Ubuntu partion.
The line beginning with "/dev/hda1" is my XP Home partition which is mounted read AND write meaning that I can, for instance listen to music and/or add a file to it from my Ubuntu. In order to be able to achieve this, I followed this HowTo:  [by Givré]("http://ubuntuforums.org/showthread.php?t=217009")

The line beginning with "/dev/hda3" is my FAT 32 -a file system allowing read AND write access from Ubuntu AND Windows.

Since you seem to wish to reinstall in English then I guess you have 'nothing' to lose. So an idea would be to practice mounting your partitions right now. I mean you can 'afford' to mess up your system learning because you'll be reinstalling anyways.

Note also that "doing everything over again" will not solve your problem. You'll still have to mount your partitions the right way!
I hope this can be of help. Evybody here knows it's not that easy at first.

Also, as I have already stated in an earlier post:
[ Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")
Good luck!

---

### Post by masterK on 2006-11-17
> **xyz said:**
> Hi-
Can you please also post the out put of:
```
sudo gedit /etc/fstab
```
"/etc/fstab" is the file that shows you how (if) your partitions are mounted, meaning accessible.
This is mine, for instance:


The line beginning with "/dev/hda2" is my Ubuntu partion.
The line beginning with "/dev/hda1" is my XP Home partition which is mounted read AND write meaning that I can, for instance listen to music and/or add a file to it from my Ubuntu. In order to be able to achieve this, I followed this HowTo:  [by Givré]("http://ubuntuforums.org/showthread.php?t=217009")

The line beginning with "/dev/hda3" is my FAT 32 -a file system allowing read AND write access from Ubuntu AND Windows.

Since you seem to wish to reinstall in English then I guess you have 'nothing' to lose. So an idea would be to practice mounting your partitions right now. I mean you can 'afford' to mess up your system learning because you'll be reinstalling anyways.

Note also that "doing everything over again" will not solve your problem. You'll still have to mount your partitions the right way!
I hope this can be of help. Evybody here knows it's not that easy at first.

Also, as I have already stated in an earlier post:
[ Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")
Good luck!

he, is saw you are online right now! yesterday it worked!! and i didn't do anything, now it asked for a codec of my mp3 so i installed vlc player, and everything worked. now i restarted my computer today and i have the same problem again, i have not enough rights.. i'm gonna try your above post now.. thanks!

---

### Post by masterK on 2006-11-17
sorry, i'm alraidy messing up my computer (as you said8) ) i copied your hda1, only my xp pro partition is on hda 3, so i only copied the last part, here's my output now(it still doesn't work..):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3	/media/hda3	ntfs-3g	defaults,locale=en_US.utf8 0 0

i'm trying some more now..](*,)

---

### Post by Skilputt on 2006-11-17
Hello masterK!

I think I may have the same problem. I have a dual boot on my primary master which works fine and my windows partition mounts perfectly. However I have 3 other hard drives that are visible in computer, and I have no trouble viewing their content when viewing them from root. 
I have tried to change their mount points and permissions as instructed in [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), but  with no luck. My /etc/fstab file is as follows:

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

**/dev/sda**	/storage1	ntfs	defaults,nls=utf8,umask=0222 0 0
**/dev/sdb**	/storage2	ntfs 	defaults,nls=utf8,umask=0222 0 0
[/INDENT]

/dev/sda and /dev/sdb are the ones I want access to as a user...

They do not mount into their directories, and when I try to mount them all it sais in the terminal is:
[INDENT]mount: /dev/sda already mounted or /storage1 busy
mount: /dev/sdb already mounted or /storage2 busy[/INDENT]

Tried unmounting them but:
[INDENT]umount: /dev/sda not mounted
umount: /dev/sda not mounted[/INDENT]

So I am confused... ](*,) 

I just want to be able to read them from linux as they are NTFS, but I dont want to have to view them from root the whole time. The wierd thing is, the last time I installed ubuntu, they mounted fine for all users on the desktop. The only thing I think I did different this time around was I had the hard drives installed when I first booted linux up where as last time I installed them well after all the updates... Any help would be appreciated

Any direction would be greatly appreciated!

---

### Post by Skilputt on 2006-11-17
Murphies law!
Five minutes after posting I figured it out... after a whole day of strugling... :) 
In the /etc/fstab file I replaced the:
/dev/sda with the actual partition: /dev/sda1
and the likewise with /dev/sdb
After a (succesful) remount all was fine!

So one must map the actual partition to a mount folder, and not just the whole drive... oops

Hope it stays that way though. :-k

---

### Post by masterK on 2006-11-17
great you finaly have it working now, i'm strugling for weeks now, and yesterday it worked, without me doing anything, but now nothing anymore..
i've just reinstalled my ubuntu, and updating it right now(had 5.1) see what this is gonna do.

---

### Post by masterK on 2006-11-17
alright, i finished reinstalling, and i see the ntfs partition on my desktop.. it even shows the name i gave it in windows! but i still can't acces it becouse i don't have enough rights.. this is the output of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     ntfs    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


what do i need to change if i want to read and write?
thanks for helping me out!!

---

### Post by xyz on 2006-11-18
> what do i need to change if i want to read and write?
thanks for helping me out!!
[Look where it says "For Edgy"]("http://www.ubuntuforums.org/showthread.php?t=217009")
If something's unclear, come back and ask.
Good day!

---

### Post by masterK on 2006-11-18
> **xyz said:**
> [Look where it says "For Edgy"]("http://www.ubuntuforums.org/showthread.php?t=217009")
If something's unclear, come back and ask.
Good day!

but it isn't a removable device, it's a partition in a 80GB disk where another partition is installed with ubuntu...

---

### Post by masterK on 2006-11-18
ok, i tried, but now if i open places-computer i see the old one (the one who showed the name) but if i open it, i get this message:

Unable to mount the selected volume.
<details>
mount: only root can mount /dev/hda3 on /media/ntfsdisk

what is the problem here?

---

### Post by masterK on 2006-11-18
> **masterK said:**
> ok, i tried, but now if i open places-computer i see the old one (the one who showed the name) but if i open it, i get this message:

Unable to mount the selected volume.
<details>
mount: only root can mount /dev/hda3 on /media/ntfsdisk

what is the problem here?

oh btw, if i enter sudo mount -a in a terminal, i get this:

Failed to mount '/dev/hda3': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

please help me, i need it done soon..](*,) :-k

---

### Post by xyz on 2006-11-19
I don't if this will apply to your situation but I got that kind of message once.

I had suspended Windows and forgot I had. Then, by accident, unplugged my computer the next day. Forgetting that Windows was in 'standby', I simply booted on my Ubuntu and got the messages you got.

So I restarted and booted on Win and then shut it down properly. Then booting Ubuntu was fine. Hopefully this will apply to you.

---

