---
title: "2 Problems I Haven't Come Across an Answer To Yet"
date: 2008-07-25
forum: General Help
---

### Post by FRAjeff on 2008-07-25
So I'm freshly upgraded from Windows.
So I have NO IDEA what I'm doing.
So treat me like a COMPLETE noob.

I love Ubuntu so far!
But I'm running into 2 problems I haven't come across an answer to as of yet, and I was wondering if you wonderful people would mind helping me out.

Every time I start up the computer, it seems to "lose" my Local Disk 2 (2nd hard drive). All of my music is on said hard drive, so if I forget about the fact that it has lost my 2nd HD, and I open Rhythmbox, it starts deleting all of my music. In order to get it to find the 2nd HD, I must manually navigate to the Computer, then into Local Disk 2 (at which point the desktop shortcut reappears), and then into my music folder (if I dont do the second step, all of the music still deletes). Then after I do that, if I open up Rhythmbox, all of the music re-adds itself. This isn't a pressing issue, it's just a minor annoyance.

The second one is a bit more of an issue. I'm not sure whether the issue is just rhythmbox or whether it's universal in my computer. If I'm listening to a song, and I decide to pause it, and then, say, watch a video on youtube, the youtube video will have no sound. Then if I go back into Rhythmbox and I click play, the song will not start playing. It just acts as though I had never pressed the button. Then I notice that Pidgin has stopped making all sounds as well. So I decided to do a "test hardware", and when it tested my speakers, sure enough, it played a sound. I thought "cool, its fixed!", but this is not true, as no other programs will display sound anymore. In order to fix the issue, I have to restart the computer and hope to god that I don't have to pause at all. This has happened many-a-time now, and is QUITE the annoyance.

Thanks to everyone who offers any form of a solution!

Jeff

---

### Post by dark_phantom on 2008-07-25
Is your second hard drive an external usb?  Post the contents of /etc/fstab and df -hl from a terminal when you can see the 2nd HD.

---

### Post by FRAjeff on 2008-07-25
Nope, it's internal SATA.

df -hl
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.5G   65G   4% /
varrun                759M  100K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M   52K  759M   1% /dev
devshm                759M  264K  759M   1% /dev/shm
lrm                   759M   39M  720M   6% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       71G  2.5G   65G   4% /home/jeff/.gvfs
/dev/sdb1             233G   84G  150G  36% /media/Local Disk 2

```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=584aa87c-d2ef-4b64-b6e5-f11259d12a03 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d549c1b9-029d-4d79-a9a5-03732d73d0ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


Thanks for the speedy response!

---

### Post by forger on 2008-07-25
I think there was an application that manages hard drives using a graphical user interface..

try open a terminal and do this:
> sudo apt-get install pysdm
gksu pysdm


it should help you configure the hard drive properly

---

### Post by forger on 2008-07-25
> **FRAjeff said:**
> 
The second one is a bit more of an issue. I'm not sure whether the issue is just rhythmbox or whether it's universal in my computer. If I'm listening to a song, and I decide to pause it, and then, say, watch a video on youtube, the youtube video will have no sound. Then if I go back into Rhythmbox and I click play, the song will not start playing. It just acts as though I had never pressed the button.

I think this can be solved if you play around with the options in System > Preferences > Sound
for example, set all the options for sound to use pulseaudio

then log out and log in again and try it out again :)

if it doesn't work, set it all to alsa and log out / log in, and so on

---

### Post by sdennie on 2008-07-25
To fix your sound issue, you can either try the tips in this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) or, you can go to System->Preferences->Sound and change everything from whatever it currently is to ALSA.  You'll probably need to restart all applications that have sounds after doing that.

---

### Post by FRAjeff on 2008-07-25
I'll let you guys know what happens next time I reboot, which seems to be when all the issues happen. Thanks for all the responses!!

---

### Post by FRAjeff on 2008-07-25
Thanks to all of the amazing people here on the forums,
both of my issues would appear to be remedied for the time being!

I just changed all of my sound options to ALSA, which fixed the sound issue.

The Hard Drive issue was solved by installing pysdm as Forger suggested, and configuring each hard drive with it. After a quick reboot, the music program and torrent programs still couldn't find said drive, and all of the music was deleted again. Once I re-added the music, however, it would seem that a more permanent connection was made, as three restarts have proven, without having a single issue.

THANKS EVERYONE!
YOU ARE THE GREATEST!

Jeff

---

### Post by BLTicklemonster on 2008-07-25
> **FRAjeff said:**
> Nope, it's internal SATA.

df -hl
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.5G   65G   4% /
varrun                759M  100K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M   52K  759M   1% /dev
devshm                759M  264K  759M   1% /dev/shm
lrm                   759M   39M  720M   6% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       71G  2.5G   65G   4% /home/jeff/.gvfs
/dev/sdb1             233G   84G  150G  36% /media/Local Disk 2

```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=584aa87c-d2ef-4b64-b6e5-f11259d12a03 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d549c1b9-029d-4d79-a9a5-03732d73d0ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


Thanks for the speedy response!


First off, you need to get more information on /dev/sdb1

Is it ntfs or fat32 or what? Find that out by mounting the drive like you normally do, then go to System, Administration, System Monitor, then click the tab on the right that says File Systems. It should tell you what you need to know under Type.

Then use this to figure out what to put in your fstab.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

to edit your fstab, open the terminal, and type

sudo gedit /etc/fstab

(immediately save it as oldfstab)

and add your new line like this:

# /dev/sda1
UUID=584aa87c-d2ef-4b64-b6e5-f11259d12a03 /               ext3    relatime,errors=remount-ro 0       1
[COLOR="Red"]/dev/sdb1 (put information from the link here like it says to in the link)[/COLOR]
# /dev/sda5
UUID=d549c1b9-029d-4d79-a9a5-03732d73d0ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Save it as fstab now, then do this:

sudo mkdir /media/music

sudo mount /dev/sdb1 /media/music

but don't run that until you have your fstab edited.


(if for some reason the fstab is messed up now, you can sudo gedit /etc/oldfstab and just save it as fstab and be back to square one)


*edit:

doh, you just posted. Well here's this anyway. 

Glad you resolved your problem.

---

### Post by FRAjeff on 2008-07-25
Hey, man, thanks anyway though! If I run into any other problems, I'll be sure to try this out! Thanks a bunch!

---

### Post by geeth on 2008-07-25
wrong thread

---

