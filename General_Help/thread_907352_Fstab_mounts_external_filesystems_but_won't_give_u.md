---
title: "Fstab mounts external filesystems but won't give user permissions to write"
date: 2008-09-01
forum: General Help
---

### Post by clinto on 2008-09-01
I'm not sure what I'm doing wrong.  I did the same exact thing in Archlinux and didn't have the same problem.

```

doon@ubundoonix:/media$ sudo fdisk -l
[sudo] password for doon: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb503

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        5737    20482875    5  Extended
/dev/sda3            5738       38786   265466092+  83  Linux
/dev/sda4           38787       38913     1020127+  82  Linux swap / Solaris
/dev/sda5            3188        4462    10241406   83  Linux
/dev/sda6            4463        5737    10241406   83  Linux

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4908    39423478+   7  HPFS/NTFS
/dev/sdb2            4909        5005      779152+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00064894

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   83  Linux

```

sda6 = ubuntu's /
sda3 = ext3 data storage
sdb1 = ntfs (in process of wiping and installing windows)
sdc1 = ext3 data storage

```

doon@ubundoonix:/media$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=a4559ebf-cf02-47b7-bda5-fd780254971e 	/               	ext3    relatime,errors=remount-ro 		0       1
# /dev/sdb4
UUID=c894e056-6f1f-4e0a-9c88-b55ae94c8aae 	none            	swap    sw              			0       0
# /dev/sdc2
UUID=355837a8-4144-4f96-a604-321478debfd3 	none            	swap    sw              			0       0
/dev/scd0       				/media/cdrom0   		udf,iso9660 user,noauto,exec,utf8 	0       0
/dev/fd0        				/media/floppy0  	auto    rw,user,noauto,exec,utf8 		0       0
/dev/sdb1					/media/win		ntfs	nls=utf8,umask=0222 			0 	0
/dev/sdc1					/media/sata		ext3	rw,user,auto,sync,suid			0 	0
/dev/sda3					/media/tempmedia1	ext3	rw,user,auto,sync,suid			0 	0

```

I can write to the ntfs fine.  Both of the ext3 mount with root permissions.  I'm not sure if I have the options wrong, or maybe ubuntu has a fit if I use the device path instead of the UUID?  I'd like to have user permissions so that my torrent app can save to an external filesystem at least.

I'm getting e2fsck errors on the sda3 partition, but the sdc1 is fine:
```

doon@ubundoonix:/media$ sudo e2fsck /dev/sda3
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(17899777--17899783) -17909026 -(17915534--17915541) -(17918714--17918721) -(17924840--17924846) -(17927887--17927894) -(17929597--17929604) -17931445 -(17933051--17933058) -(17935578--17935582) -(17938958--17938963) -(17948066--17948073) -(17952480--17952485) -(17952490--17952497) -(17958235--17958242) -(17959662--17959668) -(17959747--17959748) -(17960768--17960772) -(22757583--22757589) -(22758281--22758288) -(22760391--22760398) -(22762084--22762091) -(22762152--22762156) -(22766660--22766667) -(22766766--22766773) -(22768004--22768011) -(22768065--22768067) -(22768606--22768613) -(26440324--26440331) -(35989527--35989534) -(36001992--36001996) -(36001998--36002005) -(36012705--36012712) -(36013177--36013183) -(36075813--36075815) -(36160848--36160855) -(36341324--36341331) -(36349647--36349654) -(36445111--36445118) -(36445947--36445954) -36452895 -(38156955--38156958) -(38162185--38162187) -(38164351--38164358) -(38166086--38166089) -(38167549--38167556) -(38169536--38169543) -(38169824--38169831) -(38170192--38170199) -(38170270--38170277) -(38170471--38170478) -(38170534--38170541) -(38171127--38171133) -(38171300--38171307) -(38171872--38171879) -(38172088--38172095) -(38172110--38172111) -(38172165--38172172) -(38172309--38172316) -(38172388--38172395) -(38172558--38172560) -38172576 -(38172668--38172673) -(38172811--38172818) -(38172929--38172936) -38173015 -(38173151--38173156) -(38173432--38173439) -(38173684--38173691) -(38173856--38173863) -(38173904--38173911) -(38173969--38173976) -(38174037--38174038) -(38174134--38174141) -(38174212--38174219) -38174304 -(38174494--38174501) -(38174540--38174547) -(38174603--38174610) -(38174651--38174658) -(38174699--38174706) -(38174716--38174719) -(38175264--38175265) -(38175277--38175281) -(38175322--38175329) -(38175374--38175377) -(38175405--38175409) -(38175411--38175418) -(41730715--41730718) -(44321636--44321643) -(47580308--47580315) -(47819306--47819313) -(47823392--47823399) -(47833416--47833422) -(47834876--47834878) -(47835981--47835985) -(47836530--47836537) -(47836785--47836792) -(47837231--47837238) -(47837747--47837754) -(47838566--47838573) -(47839464--47839471) -(47840150--47840157) -(47840442--47840449) -(47840484--47840491) -(47841020--47841027) -(47841820--47841825) -(47842049--47842051) -(47842369--47842374) -(47858108--47858115) -(47880444--47880451) -(50385322--50385329) -(54365560--54365567) -(54365969--54365976) -(54365978--54365985) -(54395476--54395478) -(54395546--54395552) -(54395607--54395614) -(54395641--54395648) -(54986642--54986647) -(54988357--54988364) -(54988543--54988545) -(54988550--54988557) -(54988565--54988566) -(54990740--54990747) -(54991807--54991814) -(54991834--54991839) -(54991927--54991934) -(54992226--54992233) -(54992352--54992359) -(54992557--54992564) -(54992872--54992879) -(54992935--54992942) -(54993109--54993116) -(54993334--54993341) -(54993428--54993435) -(54993491--54993498) -(54993648--54993655) -(54993749--54993756) -(54993797--54993804) -(54993925--54993930) -(54994112--54994119) -(54994175--54994182) -(54994238--54994245) -(54994301--54994308) -(54994364--54994371) -(54994391--54994398) -(54994423--54994430) -(54994432--54994439) -(55335224--55335231) -(55372875--55372882) -(55374433--55374440) -(55376228--55376235) -(55377245--55377252) -(55377581--55377583) -(55379737--55379744) -(55381957--55381964) -(55382124--55382128) -(55382693--55382700) -(55384704--55384705) -(55384759--55384766) -(55384973--55384980) -(55387653--55387655) -(55389189--55389195) -(55389316--55389323) -(55391157--55391164) -(55392012--55392013) -(55392314--55392315) -(55394564--55394571) -(55394641--55394648) -(55396314--55396321) -(55396835--55396838) -(55397749--55397756) -(55397855--55397858) -(55398449--55398450) -(55398720--55398727) -(57825108--57825115) -(57828393--57828400) -(57829259--57829265) -(57832291--57832298) -(57833554--57833561) -(57834590--57834597) -(57836140--57836144) -(57837173--57837178) -(57838071--57838078) -(57842328--57842335) -(57842766--57842773) -(57845235--57845241) -(57845429--57845435) -(57847452--57847459) -(57848534--57848541) -(57854405--57854412) -(57855735--57855742) -(57857790--57857797) -(57860836--57860843) -(57862974--57862981) -(57866339--57866346) -(57869976--57869983) -(57872104--57872106) -(58334289--58334296) -(58730327--58730334) -(58748108--58748114) -(58772704--58772705) -(58799440--58799447) -(58799503--58799504) -(58839308--58839315) -(58884080--58884081) -(58942347--58942350) -(58947654--58947661) -(58968632--58968635) -(60328725--60328732) -(60329326--60329333) -(60330712--60330719) -(60330873--60330877) -(60330957--60330964) -(60331897--60331904) -(60331996--60332002) -(60332871--60332878) -(60334051--60334058) -(60336549--60336556) -60337582 -(60337820--60337827) -(60339640--60339645) -(60340675--60340682) -(60342066--60342073) -(60342125--60342132) -(60343227--60343232) -(60343305--60343312) -(60343959--60343966) -(60347423--60347430) -(60348094--60348101) -(60349504--60349509) -(60350537--60350544) -(60351474--60351481) -(60351564--60351571) -(60352276--60352283) -(60353547--60353550) -(60354650--60354657) -(60357163--60357170) -(60359613--60359620) -(60360658--60360665) -(60360787--60360794) -(60361403--60361410) -(60363189--60363196) -(60363217--60363224) -(60363341--60363347) -(60364401--60364408) -(60364437--60364442) -(60365232--60365239) -60365500 -(60366341--60366348) -(60366537--60366542) -(60367565--60367572) -(60367576--60367581) -(60369549--60369552) -(60369630--60369637) -(60370497--60370501) -(60370672--60370679) -(60372696--60372703) -(60373763--60373764) -60374791 -(60376690--60376697) -(60376776--60376783) -(60377265--60377272) -(60378901--60378905) -60381425 -(60381511--60381518) -(60382416--60382423) -(60383458--60383465) -60383573 -(60383965--60383972) -(60384044--60384049) -(60384051--60384058) -(60386116--60386123) -(60387142--60387147) -(60388052--60388056) -(60388182--60388189) -(60389099--60389103) -(60389214--60389221) -(60390239--60390246) -(60391264--60391271) -(60392569--60392571) -(60392628--60392631) -(60393813--60393820) -(60394698--60394705) -(60394857--60394864) -(60395834--60395841) -(60395901--60395906) -(60397966--60397973) -(60399000--60399007) -(60400035--60400042) -(60400992--60400999) -(60402106--60402112) -(60403130--60403137) -(60404059--60404066) -(60404167--60404168) -(60406230--60406237) -(60407256--60407263) -(60408246--60408248) -(60408286--60408292) -(60409318--60409319) -(60411370--60411377) -(60413074--60413080) -(60414098--60414105) -(60415393--60415400) -(60415498--60415505) -(60416521--60416528) -(60417383--60417390) -(60417554--60417561) -(60418473--60418480) -(60418597--60418604) -(60419603--60419610) -(60420639--60420645) -(60421665--60421672) -(60422701--60422703) -(66023626--66023628) -(66068778--66068785) -(66073004--66073011) -(66079307--660793

* Cut it off, it asks me if I want to fix.

```
I'm afraid to let it fix it though because I have all my music on this partition.  I wanted to back it up to sdc1 first.

Anyone know what I might be doing wrong that it doesn't let me have user privileges?

* I forgot to add that I was using the ext2 driver in windows on the sda3 fs, that's probably why it's throwing errors.

---

### Post by clinto on 2008-09-05
No one?  This has to be something very simple that I'm just missing.  I'm going to change the device path to UUID just in case and try that in the meantime.  But it would help me so much if someone could give some insight.  I need to get so much done, but I can't move any files.  If I move them using root, it seems to give fsck errors.

---

### Post by clinto on 2008-09-05
Well, I've been poking around, changed my fstab:

```

doon@ubundoonix:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=a4559ebf-cf02-47b7-bda5-fd780254971e 	/               	ext3    relatime,errors=remount-ro 		0       1
# /dev/sdb4
UUID=c894e056-6f1f-4e0a-9c88-b55ae94c8aae 	none            	swap    sw              			0       0
# /dev/sdc2
UUID=355837a8-4144-4f96-a604-321478debfd3 	none            	swap    sw              			0       0
/dev/scd0       				/media/cdrom0   		udf,iso9660 user,noauto,exec,utf8 	0       0
/dev/fd0        				/media/floppy0  	auto    rw,user,noauto,exec,utf8 		0       0
# /dev/sdb1
UUID=1D501ABA7BE3745F				/media/win		ntfs	nls=utf8,umask=0222 			0 	0
#/dev/sdc1
UUID=3c0d607a-a9c5-419c-b139-6c8a6af6d8fc	/media/sata		ext3	defaults,user				0 	2
#/dev/sda3
UUID=803f6d69-3abd-45bf-90c1-15908b09a33b	/media/tempmedia1	ext3	defaults,user				0 	2

```

Still, no user permissions to sdc1 or sda3.  When I check permissions in nautilus, it now says, "The permissions could not be determined." (on a side note, why does ubuntu like to name my ata devices as scsi?)  

```

doon@ubundoonix:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/win type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/sata type ext3 (rw,noexec,nosuid,nodev)
/dev/sda3 on /media/tempmedia1 type ext3 (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/doon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=doon)

```

I'm still a newb with permissions.  Someone suggested I mess with umask options.  Any other ideas?

---

### Post by clinto on 2008-09-06
Since I'm talking to myself here, I'll just go on with my progress...

So, I realize now I wasn't thinking right.  I need to change the permissions on all the files in those filesystems, mounting has nothing to do with it.

So, I was going to chmod -R 777 mountpoint.  Would that be bad doing that to the mount point, since technically, the mountpoint is in ubuntu's filesystem?  Would it apply all permissions to the files in the external filesystem?  Or is it only going to change the permissions on the mountpoint directory?  Or is it going to make Ubuntu cry because mountpoints need to have root permissions or something...?  ubuntu likes to be a little girl with that sort of stuff I find. :p

---

### Post by mc4man on 2008-09-06
Is sdc1 an internal partition or an external drive?

---

### Post by clinto on 2008-09-07
> **mc4man said:**
> Is sdc1 an internal partition or an external drive?
My motherboard doesn't have sata support(p4 478 board), so i purchased a pci sata/raid card and bought a 500gb sata drive.

So it's an internal drive, it's not going anywhere, I'm not disconnecting it at any point.

---

### Post by cggaret on 2008-09-15
When I first mounted my external drive I had to change the owner for the drive (chown).  As I understand it, this is a lot better than changing permissions to 777.  You still need to do the recursive thing though (-R).  Hope this helps.

---

