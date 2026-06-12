---
title: "root partition full"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by pandanuma on 2009-08-13
ubuntu 8.10 won't boot account root partition (8.15 gigs) 100 percent full.
while trying to make a backup using SimpleBackup I somehow saved the backup to root partition...my bad
went into windohs dual boot and downloaded 9.04 and repartitioned my /home partition so I could enlarge root but could not figure out how to move free disk space to where I could add it to root...

so instead...can I safely install 9.04 and keep my /home partition intact?
will a full /root partition create install problems?
is there a better solution?

note: I have a 500gig external drive that I just dragged my /home directory to a few months ago as a quick and dirty backup but is not upto date

---

### Post by Tclarkie on 2009-08-13
have you tried booting off ubuntu cd, installing gparted, and then edit the partition

---

### Post by Tclarkie on 2009-08-13
or you could go into terminal and (i know u should be careful when told to su, but this is clean) 
sudo su
chown ubuntu /"backup file"
(username ubuntu or whatever it logs you in as off the cd)
rm /"backup file"
(replace "backup file" with file name

---

### Post by pandanuma on 2009-08-13
I tried burning a sysrescue disk but that did not boot up...
burned ubuntu 9.04 because it has gparted(?) and used that to get some unalocated disk space
so far so good...
got stumped account free space needs to be beside/near my /root partition and not sure how to do that
the partition program shows 2 smaller partitions between /root and my freed up space...
hmmm...just took a quick look at gparted web site and should be a tab to 'move' partitions...but could not find it when I was resizing the first time...
will try again if all else fails...

---

### Post by pandanuma on 2009-08-13
tried using terminal to confirm backup file was causing problem but could not find any files that might be the culprit...
then before I could do anything else /root was full and booting didnt work
is there a general list of files I need in root that I could make sure I have and delete any that I dont need?

---

### Post by Tclarkie on 2009-08-13
cli9ck on partition, and unmount

---

### Post by Tclarkie on 2009-08-13
in the boot cd, just have a look around the filesystem to find the really big file....

if not i will help later got to go

---

### Post by pandanuma on 2009-08-13
> **Tclarkie said:**
> cli9ck on partition, and unmount

clik on which partition?
the unalocated one?
I seem to recall during my searching for a solution that partitions have to be unmounted first...:redface:
so...my memory is not so good and also my memory is not so good...

---

### Post by Tclarkie on 2009-08-13
unmount the filesystem, then drag the bar to the desired amount of space

---

### Post by pandanuma on 2009-08-13
progress...
booted up with 9.04 cd and copied all my files to external harddrive
using gparted on 9.04 cd, fearlessly fiddled with partitions...
moved unalocated free space next to /root partition and enlarged it to 11.9 gigs...
rebooted and bobs yer uncle...:P
now just have to figure out how to give tclarkie a thankyou...

---

### Post by Tclarkie on 2009-08-14
heres how tell anyone you know that fits in to the description about this group
[http://ubuntuforums.org/group.php?groupid=572](http://ubuntuforums.org/group.php?groupid=572)

---

### Post by pandanuma on 2009-08-14
set back...HELP...
noticed my /root partion was filling up AGAIN but still cannot find new(?) files that are causing it.

after much searching found this in:  /media/sda1/System Volume Information

filename: {59638d74-8727-11de-8065-001a920cbd56}{3808876b-c176-4e48-b7ae-04046e6cc752}
type:  program (application/octet-stream)

there are 4 other similar files for a total of 5.1 gigs
owner is root (group is:  plugdev ???)

Can I safely delete these files?
wait...my root partition should be /dev/sda6/ why am I talking about sda1??!
cannot seem to access sda6 with file browser...help again...

---

### Post by Tclarkie on 2009-08-15
so wats your prob' again?

---

### Post by pandanuma on 2009-08-15
dang...had big long rely but timed out and lost all my typing...
so...11.4 gig /root is 95 percent full
nvidia drivers giving me greif...maximum resolution is only 800x600
'detect monitor' button does not work...
upgraded to 9.04 but did not solve full /root problem or resolution...
just about ready to delete ubuntu partion and do fresh install

---

### Post by Tclarkie on 2009-08-16
this sounds like it should be looked at by a pro

---

### Post by Tclarkie on 2009-08-16
how imporant is it that it needs to be fixed, is it just a "Hobby" computer or do you use it for work

---

### Post by pandanuma on 2009-08-16
> **Tclarkie said:**
> how imporant is it that it needs to be fixed, is it just a "Hobby" computer or do you use it for work

its me home computer...I use it for everything.
if the /root partition fills up, things stop working...
I cannot send emails, and if you turn the computer off it will not boot again...you have to use a live cd...

I just did a semi fresh install :confused: 
popped in the 9.04 cd and installed it...

***WARNING*** I lost all my downloaded programs and broke a lot of things I had running nicely like youtube :(

deleted /root and /swap partition
resized /home [to get back 3gigs I stole from it to make the old /root bigger]
repartitioned /root, /swap and added /usr

worked like a charm...except...
it did not fix my low screen resolution 800x600
it did fix my full /root partition!!! 
14 percent of 6gigs...yes!
cannot access my thunderbird email system
not sure what else is broken

I called it a 'semi' fresh install because I tried to save my home partition and I did.
During the install I did not touch my other logical partition and now I can only access it with the root password...thats okay with me for now...
I did not know where to mount that partition so thats what I got...at least I did not lose it completely.

so fixed that pesky full /root problem but...
made a lot more work for myself...
I am going to be very busy

---

### Post by Partyboi2 on 2009-08-16
Hi, have you gone to System>Admin>Hardware Drivers and enabled the driver version for your nvidia?

---

### Post by pandanuma on 2009-08-16
> **Partyboi2 said:**
> Hi, have you gone to System>Admin>Hardware Drivers and enabled the driver version for your nvidia?

just tried to do that
looks like it downloads the drivers but does not 'activate' them
clicking on the activate button brings up the download but nuthing happens...

I installed them a few months ago and worked good for a while but things started to go sideways after that...
someone recommended these drivers cause problems so uninstalled them
'display preference' screen 'detect monitor' button does not work...

---

### Post by Partyboi2 on 2009-08-16
>  clicking on the activate button brings up the download but nuthing happens... Leave it for awhile, sometimes it is downloading but the progress is not being shown on the bar.

---

### Post by pandanuma on 2009-08-16
its all coming back to me now...
slowly...
installed thunderbird and there was all my old email :P
movie player complained about playing mp4 and other files...but it was eager to search for required codecs and then there was music...
and video...but still have to tweek youtube...
installed flashplayer but still no joy...

fixed /root problem
concerned about my new /user partition...3gigs is already 83 percent full and climbing with every new program install

*just need to work on setting the screen resolution but time to put the computer to bed for now...

---

### Post by Partyboi2 on 2009-08-16
Once you get the Nvidia driver installed you can run
```
gksu nvidia-settings
``` and try and change the resolution to something better.
Can you post the output to
```
sudo fdisk -l
df -h
``` So we can get a better idea of you partition setup.

---

### Post by pandanuma on 2009-08-16
nvidia drivers finally installed
did not have to tweek anything...turned on computer this morning and screen resolution excellent

partitions...
/dev/sda1  windows  122gigs (does not show in system monitor)
/dev/sda6  /
/dev/sda5  /home
/dev/sda3  /media/disk   (not mounted??)
/dev/sda8  /usr  2.8gigs  87 percent full

/swap (not listed by system monitor)

---

### Post by pandanuma on 2009-08-17
here finally are results of
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15972   128288680+   7  HPFS/NTFS
/dev/sda2           29585       30401     6562552+   7  HPFS/NTFS
/dev/sda3           15973       22990    56372085   83  Linux
/dev/sda4           22991       29584    52966305    5  Extended
/dev/sda5           22991       27854    39070017   83  Linux
/dev/sda6           27855       28644     6345643+  83  Linux
/dev/sda7           29217       29584     2955928+  82  Linux swap / Solaris
/dev/sda8           28645       29010     2939863+  83  Linux

Partition table entries are not in disk order

and:  df-h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             6.0G  1.1G  4.7G  18% /
tmpfs                 431M     0  431M   0% /lib/init/rw
varrun                431M  104K  431M   1% /var/run
varlock               431M     0  431M   0% /var/lock
udev                  431M  192K  431M   1% /dev
tmpfs                 431M  564K  430M   1% /dev/shm
lrm                   431M  2.5M  429M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5              37G   25G   11G  71% /home
/dev/sda8             2.8G  2.4G  278M  90% /usr

*note...youtube now works after flashplayer download and reboot

---

### Post by Partyboi2 on 2009-08-17
Is there any reason why you needed /usr on its own partition? If you have some free space on your windows partition or /dev/sda3 you could resize it down and move the unallocated space through to /devsda8, but that can be a lengthy process.

---

### Post by pandanuma on 2009-08-17
> **Partyboi2 said:**
> Is there any reason why you needed /usr on its own partition? If you have some free space on your windows partition or /dev/sda3 you could resize it down and move the unallocated space through to /devsda8, but that can be a lengthy process.

while researching prior to re installing 9.04 I followed the advice from this link...
[https://help.ubuntu.com/9.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/9.04/installation-guide/i386/apcs03.html) 

and ...
> For multi-user systems or systems with lots of disk space, it's best to put /usr, /var, /tmp, and /home each on their own partitions separate from the / partition. 

thought I would at least put /usr on separate partition
[incase of meltdown I could fix one partition without affecting another one...right?]

A few years ago I had basically followed the recommendations from this site:
 [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) 
to set up a dual boot machine but for the life of me could not find it again when looking to '*improve*' my partitions.
[came upon the site again just a few minutes ago...go figure...]

A /windows /root /swap /home setup has served me well...why fix it if it wernt brokin...

---

### Post by pandanuma on 2009-08-20
/usr partition is now too full to allow synaptic to upgrade software...
I now want to go back to my original partition layout with /usr in the /home partition.

how do I go about that?
should I drag /usr into /home and then delete the /usr partition and increase the size of /home?

---

