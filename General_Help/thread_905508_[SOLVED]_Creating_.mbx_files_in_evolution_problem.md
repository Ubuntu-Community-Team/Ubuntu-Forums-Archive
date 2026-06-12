---
title: "[SOLVED] Creating .mbx files in evolution problem"
date: 2008-08-30
forum: General Help
---

### Post by rkw1956 on 2008-08-30
Hi

Don't know if this is the right place to post but here goes - if anyone knows a more appropriate place to post please let me know.

I'm half way through a mail migration when I hit a problem that has stopped me in my tracks!

I've been saving .mbx files in my documents folder ready to transfer elsewhere, but have now hit a problem.

Now when I select an email folder in order to save content as .mbx file in stead of letting me do so a message displays...

The folder contents could not be displayed

Error stating file '/media/disk-1/hsp': No such file or directory

I've tried rebooting but it still won't save as as .mbx file.

Before, I would select the email folder in evolution, press control A to highlight all the emails then go to File | Save message and that is when I now get the above dialog box with the error message.

I've tried other email folders but it still does the same thing.

Can anyone shed any light on why this is happening and what I can do to rectify the issue?

Cheers Richard

---

### Post by EmanresuusernamE on 2008-08-30
"Error stating file '/media/disk-1/hsp': No such file or directory"

Either the filesystem pointing to that location is not mounted, or there is no folder called hsp on that mount point.  If you can access /media/disk-1 then look and see if the hsp folder exists.  If you can't get to /media/disk-1, you need to remount it.  If it's an NTFS filesystem, then try using the "-o force" option with mount.  I don't know what drive your disk is located at but something along the lines of the following should do for an NTFS drive:

```
sudo mount -o force -t ntfs-3g /dev/<Drive> /media/disk-1
```

---

### Post by rkw1956 on 2008-08-30
I sort of see what you're saying but how do I know which drive it is assuming <Drive> means select the appropriate drive. Sorry for being dumb!

---

### Post by EmanresuusernamE on 2008-08-30
First type in:
mount
That should list everthing that's mounted.  Second:
ls /dev
That will list everything in your /dev directory.  Hard drives are usually /dev/[h,s]d[a,b,c,d...] and the partitions are like /dev/[h,s]d[a,b,c,d...][1,2,3,4...].

Think of it this way, most IDE hard drives will be listed as hd[a,b,c,d...] depending on which IDE cable and part of it is attached to the drive.  The primary master IDE is hda and partitions on it are hda1, hda2, had3, ect.  SCSI, SATA and USB drives are usually listed as: sda, sdb, sdc, ect., which all depends on which is detected first. And then partitions are sda1, sda2, ect.  

Before I get too complicated and confuse you, I'll shut myself up and ask you to show us the results of your mount and ls /dev commands.

---

### Post by EmanresuusernamE on 2008-08-30
> **rkw1956 said:**
> Sorry for being dumb!
It's not dumb, windows has probably kept you in the dark for so long, you're eyes haven't adjusted yet.  Welcome to the real world outside of the Matrix.

---

### Post by rkw1956 on 2008-08-30
Thanks for being so understanding!

By saying type mount I assume you mean in a terminal window.

I have a little experience of unix commands as I have a managed dedicated web server and picking up more as I go. :)

Started running disk analyser, which is why I've only just checked back.

I'll run those commands and reply asap.

---

### Post by rkw1956 on 2008-08-30
BTW, it's a dual boot system with Vista and Ubuntu 8.04. Got so fed up with Vista that it finally pushed me into installing Ubuntu - much prefer being able to delve into the innards of a system than being told what I can and can't do by a dialog box.

I get accused of wanting to be geeky, but to me I find it interesting - is that what people mean when they say it's sad, because I don't think it is. :)

Will have to cook tea now for my daughters so I may be a while but will report back on that mount stuff you gave me.

---

### Post by EmanresuusernamE on 2008-08-30
> **rkw1956 said:**
> much prefer being able to delve into the innards of a system than being told what I can and can't do by a dialog box.
Not always getting a dialog box is what really got to me.  I'm very geeky, and to me it doesn't seem that you're trying to be geeky.  You want to have control of your system, which to me is reasonable since you probably paid a lot of money for it and want your monies worth.

---

### Post by rkw1956 on 2008-08-31
Hi, back again...

Results of mount command:

rkw@rkw-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/rkw/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rkw)

Results of ls /dev command:

adsp       ptyb9  ptyq9  ptyv9  ram3        tty56  ttye4  ttyt0  ttyy0
audio      ptyba  ptyqa  ptyva  ram4        tty57  ttye5  ttyt1  ttyy1
bus        ptybb  ptyqb  ptyvb  ram5        tty58  ttye6  ttyt2  ttyy2
cdrom      ptybc  ptyqc  ptyvc  ram6        tty59  ttye7  ttyt3  ttyy3
cdrw       ptybd  ptyqd  ptyvd  ram7        tty6   ttye8  ttyt4  ttyy4
console    ptybe  ptyqe  ptyve  ram8        tty60  ttye9  ttyt5  ttyy5
core       ptybf  ptyqf  ptyvf  ram9        tty61  ttyea  ttyt6  ttyy6
disk       ptyc0  ptyr0  ptyw0  random      tty62  ttyeb  ttyt7  ttyy7
dri        ptyc1  ptyr1  ptyw1  rtc         tty63  ttyec  ttyt8  ttyy8
dsp        ptyc2  ptyr2  ptyw2  scd0        tty7   ttyed  ttyt9  ttyy9
dvd        ptyc3  ptyr3  ptyw3  sda         tty8   ttyee  ttyta  ttyya
dvdrw      ptyc4  ptyr4  ptyw4  sda1        tty9   ttyef  ttytb  ttyyb
fd         ptyc5  ptyr5  ptyw5  sda2        ttya0  ttyp0  ttytc  ttyyc
fd0        ptyc6  ptyr6  ptyw6  sda5        ttya1  ttyp1  ttytd  ttyyd
fd0u1040   ptyc7  ptyr7  ptyw7  sda6        ttya2  ttyp2  ttyte  ttyye
fd0u1120   ptyc8  ptyr8  ptyw8  sequencer   ttya3  ttyp3  ttytf  ttyyf
fd0u1440   ptyc9  ptyr9  ptyw9  sequencer2  ttya4  ttyp4  ttyu0  ttyz0
fd0u1600   ptyca  ptyra  ptywa  sg0         ttya5  ttyp5  ttyu1  ttyz1
fd0u1680   ptycb  ptyrb  ptywb  sg1         ttya6  ttyp6  ttyu2  ttyz2
fd0u1722   ptycc  ptyrc  ptywc  shm         ttya7  ttyp7  ttyu3  ttyz3
fd0u1743   ptycd  ptyrd  ptywd  snapshot    ttya8  ttyp8  ttyu4  ttyz4
fd0u1760   ptyce  ptyre  ptywe  snd         ttya9  ttyp9  ttyu5  ttyz5
fd0u1840   ptycf  ptyrf  ptywf  sndstat     ttyaa  ttypa  ttyu6  ttyz6
fd0u1920   ptyd0  ptys0  ptyx0  sr0         ttyab  ttypb  ttyu7  ttyz7
fd0u360    ptyd1  ptys1  ptyx1  stderr      ttyac  ttypc  ttyu8  ttyz8
fd0u720    ptyd2  ptys2  ptyx2  stdin       ttyad  ttypd  ttyu9  ttyz9
fd0u800    ptyd3  ptys3  ptyx3  stdout      ttyae  ttype  ttyua  ttyza
fd0u820    ptyd4  ptys4  ptyx4  tty         ttyaf  ttypf  ttyub  ttyzb
fd0u830    ptyd5  ptys5  ptyx5  tty0        ttyb0  ttyq0  ttyuc  ttyzc
full       ptyd6  ptys6  ptyx6  tty1        ttyb1  ttyq1  ttyud  ttyzd
fuse       ptyd7  ptys7  ptyx7  tty10       ttyb2  ttyq2  ttyue  ttyze
hidraw0    ptyd8  ptys8  ptyx8  tty11       ttyb3  ttyq3  ttyuf  ttyzf
hpet       ptyd9  ptys9  ptyx9  tty12       ttyb4  ttyq4  ttyv0  urandom
initctl    ptyda  ptysa  ptyxa  tty13       ttyb5  ttyq5  ttyv1  usbdev1.1_ep00
input      ptydb  ptysb  ptyxb  tty14       ttyb6  ttyq6  ttyv2  usbdev1.1_ep81
kmem       ptydc  ptysc  ptyxc  tty15       ttyb7  ttyq7  ttyv3  usbdev2.1_ep00
kmsg       ptydd  ptysd  ptyxd  tty16       ttyb8  ttyq8  ttyv4  usbdev2.1_ep81
log        ptyde  ptyse  ptyxe  tty17       ttyb9  ttyq9  ttyv5  usbdev3.1_ep00
loop0      ptydf  ptysf  ptyxf  tty18       ttyba  ttyqa  ttyv6  usbdev3.1_ep81
lp0        ptye0  ptyt0  ptyy0  tty19       ttybb  ttyqb  ttyv7  usbdev4.1_ep00
MAKEDEV    ptye1  ptyt1  ptyy1  tty2        ttybc  ttyqc  ttyv8  usbdev4.1_ep81
mem        ptye2  ptyt2  ptyy2  tty20       ttybd  ttyqd  ttyv9  usbdev5.1_ep00
mixer      ptye3  ptyt3  ptyy3  tty21       ttybe  ttyqe  ttyva  usbdev5.1_ep81
mixer1     ptye4  ptyt4  ptyy4  tty22       ttybf  ttyqf  ttyvb  usbdev6.1_ep00
net        ptye5  ptyt5  ptyy5  tty23       ttyc0  ttyr0  ttyvc  usbdev6.1_ep81
null       ptye6  ptyt6  ptyy6  tty24       ttyc1  ttyr1  ttyvd  usbdev6.3_ep00
nvidia0    ptye7  ptyt7  ptyy7  tty25       ttyc2  ttyr2  ttyve  usbdev6.3_ep81
nvidiactl  ptye8  ptyt8  ptyy8  tty26       ttyc3  ttyr3  ttyvf  usbdev7.1_ep00
oldmem     ptye9  ptyt9  ptyy9  tty27       ttyc4  ttyr4  ttyw0  usbdev7.1_ep81
parport0   ptyea  ptyta  ptyya  tty28       ttyc5  ttyr5  ttyw1  usbdev8.1_ep00
port       ptyeb  ptytb  ptyyb  tty29       ttyc6  ttyr6  ttyw2  usbdev8.1_ep81
ppp        ptyec  ptytc  ptyyc  tty3        ttyc7  ttyr7  ttyw3  vcs
psaux      ptyed  ptytd  ptyyd  tty30       ttyc8  ttyr8  ttyw4  vcs1
ptmx       ptyee  ptyte  ptyye  tty31       ttyc9  ttyr9  ttyw5  vcs2
pts        ptyef  ptytf  ptyyf  tty32       ttyca  ttyra  ttyw6  vcs3
ptya0      ptyp0  ptyu0  ptyz0  tty33       ttycb  ttyrb  ttyw7  vcs4
ptya1      ptyp1  ptyu1  ptyz1  tty34       ttycc  ttyrc  ttyw8  vcs5
ptya2      ptyp2  ptyu2  ptyz2  tty35       ttycd  ttyrd  ttyw9  vcs6
ptya3      ptyp3  ptyu3  ptyz3  tty36       ttyce  ttyre  ttywa  vcs7
ptya4      ptyp4  ptyu4  ptyz4  tty37       ttycf  ttyrf  ttywb  vcs8
ptya5      ptyp5  ptyu5  ptyz5  tty38       ttyd0  ttys0  ttywc  vcsa
ptya6      ptyp6  ptyu6  ptyz6  tty39       ttyd1  ttyS0  ttywd  vcsa1
ptya7      ptyp7  ptyu7  ptyz7  tty4        ttyd2  ttys1  ttywe  vcsa2
ptya8      ptyp8  ptyu8  ptyz8  tty40       ttyd3  ttyS1  ttywf  vcsa3
ptya9      ptyp9  ptyu9  ptyz9  tty41       ttyd4  ttys2  ttyx0  vcsa4
ptyaa      ptypa  ptyua  ptyza  tty42       ttyd5  ttyS2  ttyx1  vcsa5
ptyab      ptypb  ptyub  ptyzb  tty43       ttyd6  ttys3  ttyx2  vcsa6
ptyac      ptypc  ptyuc  ptyzc  tty44       ttyd7  ttyS3  ttyx3  vcsa7
ptyad      ptypd  ptyud  ptyzd  tty45       ttyd8  ttys4  ttyx4  vcsa8
ptyae      ptype  ptyue  ptyze  tty46       ttyd9  ttys5  ttyx5  watchdog
ptyaf      ptypf  ptyuf  ptyzf  tty47       ttyda  ttys6  ttyx6  xconsole
ptyb0      ptyq0  ptyv0  ram0   tty48       ttydb  ttys7  ttyx7  zero
ptyb1      ptyq1  ptyv1  ram1   tty49       ttydc  ttys8  ttyx8
ptyb2      ptyq2  ptyv2  ram10  tty5        ttydd  ttys9  ttyx9
ptyb3      ptyq3  ptyv3  ram11  tty50       ttyde  ttysa  ttyxa
ptyb4      ptyq4  ptyv4  ram12  tty51       ttydf  ttysb  ttyxb
ptyb5      ptyq5  ptyv5  ram13  tty52       ttye0  ttysc  ttyxc
ptyb6      ptyq6  ptyv6  ram14  tty53       ttye1  ttysd  ttyxd
ptyb7      ptyq7  ptyv7  ram15  tty54       ttye2  ttyse  ttyxe
ptyb8      ptyq8  ptyv8  ram2   tty55       ttye3  ttysf  ttyxf

Doesn't make much sense to me, if any.

Does it tell you anything?

---

### Post by rkw1956 on 2008-08-31
Something else that occurs to me...

I am highlighting all the emails in the evolution mailbox, and then going to File, Save messages. So why does evolution think the emails are located at /media/disk-1/hsp ? Isn't that a location for a removable drive, because it's going to /media ?

My reasoning may be flawed through lack of knowledge, though.

---

### Post by rkw1956 on 2008-08-31
It wasn't evolution looking to find a mailbox in the wrong location, it was me not selecting the right directory to save the .mbx file to.

Feel really stupid now, but problem solved! :)

Thanks for all your help.

I'll try not to be so stupid next time.

---

### Post by rkw1956 on 2008-08-31
Problem solved. Evolution wasn't looking in the wrong place to find contents of mailbox, it trying to save contents to a directory that didn't exist. As soon as I figured that out I changed the destination and it saved fine.

Just me being stupid.

Thanks for all your help!

---

### Post by EmanresuusernamE on 2008-09-02
> **rkw1956 said:**
> Something else that occurs to me...

I am highlighting all the emails in the evolution mailbox, and then going to File, Save messages. So why does evolution think the emails are located at /media/disk-1/hsp ? Isn't that a location for a removable drive, because it's going to /media ?

My reasoning may be flawed through lack of knowledge, though.

Sorry it took so long to get back to you. /media is a general location for all of the drives that are auto-mounted by Ubuntu, or manually mounted by yourself.  You can mount a drive to practically any location, (say for a few that will cause large amounts of grief such as directly into the /media directory).

> **rkw1956 said:**
> Does it tell you anything?
Lots:
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
Tells me that your system is using either a SCSI hard drive, unlikely, or a SATA hard drive, likely.  And you probably used the guided partition settings.  It should be pretty safe to assume that sda1 and sda2 are your Vista partitions and that if Ubuntu won't mount them, you can use the following options to try and force it, (although it may be safer for you to just restart Vista and then have it shut down properly):

sudo mkdir /media/sda1
sudo mkdir /media/sda2
sudo mount /dev/sda1 /media/sda1 -o force -t ntfs-3g
sudo mount /dev/sda2 /media/sda2 -o force -t ntfs-3g

The first two commands makes sure that you have someplace to put the links to the FS.  The second two actually force the mounting if the hard drives where unmounted improperly.

Do not mount a file system directly into the /media or /mnt directories or your Ubuntu will become very unfriendly with you

---

