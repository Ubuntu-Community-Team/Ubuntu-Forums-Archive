---
title: "Raid Enclosure"
date: 2016-05-27
forum: Hardware
---

### Post by aaron50 on 2016-05-27
Hello all,

I have built myself a headless media and file share server using a handful of old computers i had laying around. The server is running ubuntu 14.04LTS with Plex, Emby, and Samba as my main media and file sharing sources. All of my data is currently stored on a 4tb external hard drive that is plugged into the server via usb, and us mounted automatically when the server boots up.

I enjoy the server, but it has come time that i do a massive upgrade of my system. I am going to be building an entirely new server, and was thinking about the easiest way to store my data. I was thinking about using an external raid enclosure like [this]("http://www.bhphotovideo.com/bnh/controller/home?O=&sku=1186694&gclid=CMa7lc_t-swCFQIOaQodQzMN6w&Q=&ap=y&c3api=1876%2C52934714882%2C&is=REG&A=details"). I figured the advantages of this are that i can use my windows PC to get the drives and raid configured and them just plug it into my new server and transfer all of my content, and if a drive fails then i just swap it out and the enclosure does all the work of restoring the data. I am not a programmer, and have never used raid before, so i don't feel like i could set up an internal raid card, or even know where to begin with that. My question is it as easy as I am explaining to set one of these enclosures up and to swap out the drives. I can just get it going through my windows computer, then plug it into my server and transfer the files, or will i have to configure the raid enclosure from my linux machine. Can anyone give me some advice on what i should do, or the best enclosure to buy.

---

### Post by TheFu on 2016-05-27
No, it isn't as easy as you are explaining.

$260 for an enclosure seems very high priced.  RAID comes in 3 styles
a) HW RAID
b) FakeRAID
c) SW RAID

HW-RAID is where you get a quality RAID card, usually about $250+ for it and normal only do this for true business servers where that level of performance is needed. Be certain to get 2 of the RAID cards from identical lots, to reduce the HW incompatibilities inherent with RAID HW.

Fake-RAID is that stuff built into motherboards or cheap "raid cards".  They offload the parity operations to the main CPU, so they aren't as fast as the HW-RAID, but we are still tied to the exact, specific RAID used at the hardware level.

SW-RAID is what mdadm on Linux uses.  It is extremely flexible, but slower. It isn't tied to the hardware used, so any JBOD controller can be used.  When I say slower, it isn't as slow as USB2, but it isn't as fast as a single WD-Black HDD connected to a quality SATA controller either. For media, it is still WAY faster than needed.

So .... I would question whether you need RAID at all.  RAID doesn't replace backups and there are lots of forum questions there from people who don't have backups, but had a RAID failure. Sadly, much of the times, restoring from backups is the only solution to a corrupted RAID array.

RAID is for HA - High Availability and maybe for higher performance.  If you don't get a $350+ quality RAID card, then you clearly don't need the performance, so it is only for HA.  Is it really that important to have a movie keep streaming if a HDD fails in a home environment?  Don't forget, you still **MUST** have backups too.

No, you cannot setup RAID on a Windows machine, then connect it to a Linux machine.  There are different block formats and different file systems used.  You might be able to get it working, but I wouldn't because when there are issues later - and RAID always comes with issues - how will you troubleshoot it?

For media, I just use straight HDDs with USB connected disks where a mirror is created a few times weekly. Provided you stay away from very low quality HDDs (anything from Seagate these days) and have a good rsync setup, you won't loose a bit if there is a failure. 

Samba?  NFS is faster and provides the permissions that Plex expects.  Use Plex to serve the clients - any DLNA client will work with plex.  I use a r-pi, WD-TV Live, ChromeCast, Android DLNA clients and Kodi/PlexBMC for access. No need for any Plex-made clients to use the Plex server.

It sounds like you really aren't ready for RAID and the added complexities it brings. Plus, I don't think you need it.  I have 2 external disk arrays - a cheapo ($99) USB3/eSATA array that has a power issue - the button must be pressed after an outage, which makes it useless for a server and other array something like this: [http://www.addonics.com/products/mst.php](http://www.addonics.com/products/mst.php) which has been working non-stop for almost a decade.  I've moved the 2nd array from RAID5 (320G disks) to RAID1 (2TB disks) and through 3 different servers with different disk controllers.  It is mdadm (Linux SW RAID), so highly flexibly.  Those disks are for virtual machines, a true HA need.  

If you want a disk enclosure and you want RAID built-in, then you want a NAS. Be certain to look for NAS devices that support NFS, not just samba.  Most quality NAS devices with good RAID run about $600, but you might be able to find a used ReadyNAS for $200. Just be aware that these devices only support very specific HDDs - usually WD Red or Black models and some Hitachis. Other disks won't work.  Some people can build their own NAS with parts from old PCs lying around.  I did about 18 months ago with a new MB and CPU for $99.  Everything else was was already excess - case, PSU, RAM, a few HDDs, few Intel PRO/1000 NICs,   This new NAS is fast - very fast.  Since the build, I've added (6) 4TB HDDs - 3 internal, 3 external for rsync mirrors using eSATA connections.

BTW, you didn't ask, but it is always best to use a Linux file system for any data unless you must be able to access it directly from Widnows.  If you will always access it over the network, then use a Linux file system like ext4, btrfs, zfs, or one of the 20 others - then run Samba and NFS to make that storage available to the different clients.  NFS is fast, so use that for any non-Windows clients.

---

### Post by aaron50 on 2016-05-27
Fu, i appreciate all of the information that you have given me.

I am only using samba because all of my other machines are windows, this is my first experience with linux (as you can probably tell) and i am not a mac guy. the reason i am using a ntfs right now is because when i set up my external hard drive, i did it on my windows machine, and was not aware of the other types. By the time i had it set up i realized that ext4 would have been so much better for a lot of different reasons, one being permissions. Since i only have one drive that is that large, i could not reformat the disk, but intend to format my new drives as ext4.

I am not looking at nas units, because you really have to step up in price to get a decent cpu, one that can handle the transcoding of all my media.

You have really scared me off of raid, which is a good thing because i am not really comfortable yet with linux and that would have made things much more difficult, and potentially dangerous if data was lost.

if i go with just a simple tower that you suggested, can i use 2 drives and just create a mirror on the other two? I cannot see myself using more than 8tb of space right now, so if i had 4-4tb drives would that work? also, would the computer see 2 drives or would it see it as 1, assuming the other 2 are the mirror?

---

### Post by TheFu on 2016-05-27
**Update**: [http://www.hardware-revolution.com/best-cpu-apu-processor-april-2016/](http://www.hardware-revolution.com/best-cpu-apu-processor-april-2016/) has good, cheap, CPUs.
I have a G3258 (not overclocked). Would be worth comparing to the newer G4400 and the G3260. Just be aware that DDR4 RAM will cost more. The G3258 appears to still be a better CPU overall, at least to me.  Less power, higher performance, unlocked, and usually cheaper.  Being "newer" doesn't make the G4400 _better_.

Glad to have helped with some guidance. Wait a few days. Hopefully others will respond with different opinions and different points of view. **There are some really smart folks here** with different experiences around this stuff.

The mirror I'm talking about is via rsync ... it is delayed until you run the rsync command with the correct options. All 4 disks would be seen - just mount the primaries somewhere different from the 'backups' .... 

On my plex system, I do
* /D/M --- movies
* /D/T --- TV
and 
/Backup/M - rsync mirror of movies
/Backup/T --- rsync mirror of TV

When those disks are full, use Plex to add more areas ... /D/M2, /D/M3 and mount the next storage into those areas.  I avoid having any permanent storage under /media or /mnt ... those are for temporary stuff only, IMHO.

If you use an Intel G3258 CPU with a $50 MB, then for about $100, you'll have a plex system that can transcode 2 HiDef streams concurrently.  Sadly, the G3258 isn't as cheap these days as it was last year, so it might be $120 for MB+CPU today.  BTW, this box with a solid GigE NIC would be a good NAS too. Mine works well.  Might be worth looking for a $50 CPU with similar or better performance.  Sometimes there is a big jump from generation to generation and Intel messes up their pricing like they did with the G3258 (it was WAY too low).  Plus that CPU is a 53W one, so not a huge power sucker like the Core i5/i7 or any desktop from AMD.  AMD does make some great low-power CPUs, but they are usually too slow to transcode on-the-fly like you'd want with Plex.

If you have good backups, then you don't need to worry about data loss.  The chances of 1 disk failing in a year can be calculated. The chances that 2 disks will fail in the same year, within a week are pretty small, unless they are old.  Google did a study years ago about this and BackBlaze releases their HDD failure studies every quarter with more than 100K HDDs involved - sorry, I don't remember the exact number.  My take-away from the most recent publish study was to 
a) avoid seagate
b) buy hitachi 7200 when possible and WD Red/Black if not. There are specific models to avoid, but those aren't in sizes I buy, so don't recall the details.

rsync is one of those amazing tools that all Linux/Unix people should know.  In my list of greatest things created/found/invented by Humans:
1) Fire
2) Wheel
3) Vaccines
4) Unix
5) ssh
6) rsync
7) Democracy ;)

THAT's how good rsync is.  Of course, rsync isn't the best tool for normal, versioned, backups, but it can get you 80% there.  For static, non-changing media, rsync is what I use.

---

### Post by him610 on 2016-05-27
> I am not a programmer

You don't need to be a programmer, you just need to be able to read and comprehend the instructions.

> not looking at nas units

Did you consider building one from available parts and use an open source NAS solution?
Check out this link....
[http://www.nas4free.org/]("http://www.nas4free.org/")

---

### Post by aaron50 on 2016-05-27
Fu, thanks again for the solid advice. I was going to ask about what you could recommend in terms of cpu, hard drives, and and motherboard and you read my mind. You wouldn't recommend going all out for an i5 or i7? I will look into rsync.

Him, Thanks for the advice. 

To your points, I can read and comprehend most instructions, my problem is that if for some reason it doesn't work exactly as I want, or I want to configure the program in some way, I cannot figure out why and sometimes on the forums people speak well above my head.

i did consider building a nas. I was actually, when I began my project of building a server, looking at freenas. I didn't do this because, from what I read, an Ubuntu server is more expandable. Also I kind of wanted to take on the challenge of a command line based server. Now since this is becoming something I really want to put money into, I am open to a more professional opinion. I guess since I am building my own server, I could run freenas or nas4free on it instead of Ubuntu. If you don't mind me asking, what are some of the advantages/disadvantages of running Ubuntu 14.04 with Lubuntu vs running a free nas software. I can imagine that the nas is much more user friendly in that there is a limited menu of things to do which is a blessing and a curse, but what are some other things, performance for instance?

---

### Post by TheFu on 2016-05-28
Flexibility is why NOT to use a pre-created NAS distro.  FreeNAS has fallen out of favor for some of the forked versions. I'm not into that area anymore, so can't recommend any. Plus there is ZFS - which is amazing, powerful, and different.  ZFS in FreeNAS really wants 6 HDDs.  And if you use some of the more advanced capabilities, it is RAM hungry, to put it mildly.  There are guidelines around ZFS deployments that really, really, really need to be followed. Also, the FreeNAS distros using ZFS **NEED** ECC RAM and you probably want server-class components.  Nothing wrong with any of this, provided the 2x costs don't bother you.  If you want to run NAS4free, get a supermicro MB and follow the suggested hardware carefully.

My NAS/Plex/Calibre/ + about 5 other services box doesn't have a GUI.  GUIs introduce bugs and a slight amount of overheard. Mine usually doesn't have a monitor connected or keyboard or mouse.  Lubuntu doesn't come with admin tools which will make your life easier anyway, to just use the CLI/shell and get over it.  Treat it like a server. Manage it like a server, from the shell.

What would be the purpose for having an i5 or i7?  More power use, as in Watts, and if you plan to transcode everything in-advance, there could be a reason, but you can also use a queuing system (Task Spooler) and let the slower CPU work overnight.  It is a NAS, so it needs to be on all-the-time, to be of any use to other machines.  I suppose if I were building a new desktop, then I'd go for a $200 Core i5 and $100 MB - that's my normal method.  Stopped dealing with GPUs years ago - the onboard Intel is fine for my needs. The G3258 can run virtual machines too, just not as many as a Core i5+.  Look through some benchmarks for the type of workloads you expect to run when selecting the CPU.  Just because my needs are strictly for a "server" without any GUI, that doesn't mean you have those same needs.  

BTW, my normal "desktop" runs inside a VM in a private cloud which is accessed over the network using x2go.  The VM server is a 1st gen Core i5 that runs 8 other VMs. It has 8G of RAM with some left over for disk buffers.  That means I have remote display machines - one is a recent Chromebook (core i3) and the other is a 1st Gen Core i5 laptop - the new chromebook is a little faster.  I'm using the remote connection now and use it 10 hrs a day from across the room or around the world.  For the stuff I do, distance doesn't matter much, though I only watch video when on the same LAN.  Even 5 miles away, video over a remote connection just doesn't work.  Audio works from anywhere in the world, however.

Oh - and freeNAS/NAS4free are based on BSD - that is both a blessing and a curse.  BSD isn't linux, so while 90% is the same, that last 10% is very different which is where all the disk, network, firewall, hardware management come in.

---

### Post by aaron50 on 2016-05-28
Thanks Fu, the main things that I use my current server for and will be using my new server for is streaming movies and music, I have a pic frame that pulls from the server, and I use it as a file share server. The reason I ask about the I5 or i7 is because I have a lot of blu-Ray movies in raw lossless mkv format and currently I cant stream those because the server can't handle it. I also let my parents and wife's parents use the server for video, they just log into plex and stream to their house, so I could be streaming up to 4 or so movies at a time max, but will more than likely never be more than 2 at a time. The reason I ask about the nas vs just Ubuntu and maybe Lubuntu to manage outside the CLI is for the file share and backup. I want to keep some things private in my local network, only my wife and I have access and it is password protected, and I want the backups to be regular and on a schedule so I don't have to think about it. 

Knowing these requirements and possibly expanded use in the future would you still recommend the G3258? Also, it sounds like you would just recommend going the cli/Lubuntu route instead of a free nas software, is that correct, or am I reading it wrong? I really appretiate all of the help and advice you have. I have little to no experience in this stuff, it started as a fun project because I like to tinker with things, and now has moved into something that my wife actually wants, believe it or not. Right now my server is only on for a little bit when we want to watch a movie or need to look at a file, because I have everything on one hard drive and I cannot risk it failing, ha. So I really want to have a 24/7 server that I am not worried about.

---

### Post by TheFu on 2016-05-29
File sharing and backups have ZERO to do with having a GUI, at least for me. Use sftp (worldwide; use keys, not passwords) or NFS (LAN only) for sharing and rdiff-backup and rsync for backups.  rsync for media and rdiff-backup for everything else. Keep at least 30 days of incremental backups. I keep 60 days on desktops and 120 days on high-risk systems.

No plex account here. Couldn't take the invasion of privacy and it works fine locally without it. No remote streaming, but I could use my VPN, I suppose.  Using a remote mount, like sshfs DOES work, but that isn't easy enough for non-tech people.

Pre-transcode the huge Bluray files into h.264 - save 2/3rds of the storage.  I don't know if transcoding 4 streams in real-time is possible.  The local streams wouldn't need to be transcoded if they are h.264 already, plus that will make the network bandwidth needs that much lower.  I assume you have wired GigE locally, so that really doesn't matter. Wifi is spotty, even when humans don't see that trouble.  For the remote streamers, just cut the resolution down to DVD quality.  Only you can determine how much CPU is needed.  I know that the G3258 does 2 HiDef streams (mpeg2 --> h.264) here. My normal playback devices don't support 1080 mpeg2 playback so I go to 720p (or lower) h.264 for anything that isn't already.  Don't have any bluray here.  If you are chasing 4K video - get the highest-end Core i7 you can afford, but I wouldn't expect live transcoding to be possible with any CPU yet (but I honestly don't know).  I'm still mostly happy with 720p and 480p looks fine on our 100in projector.  Zero plans here to move to 1080p playback. We're old and eyesight is failing ... ;)

A NAS distro may or may not be what you want. I don't know and don't have enough current information to suggest either way.  But there isn't anything a NAS distro can do that normal Ubuntu Server can't do too, it just doesn't have a point-n-click web GUI for it (and you definitely shouldn't load one!).

Higher powered CPU means more heat and more noise for the cooling. If the server is in the basement away from people and you don't care if $40/yr in extra power is used just for this single machine, do what you like.  I've been swapping out power-hungry systems for lower powered ones for years now - last power bill was $67 with 8+ machines running 24/7/365.  3 of those use less than 10W - most playback devices are under 2W peak. My "servers" use less than 250W total most of the time.  Can't wait for an old Core i7 transcoding box to die so I have an excuse to get below 100W on that machine. Actually, I probably won't bother replacing it - will just move all initial transcoding over to the G3258. Sure, it will take longer, but as long as it is real-time or faster, that's fine.  The machine has plenty of extra CPU available that should get more use. If you do this, be certain to manage the process priorities so that things needing lots of CPU now get it and things running in batch get only what is left over.

---

### Post by aaron50 on 2016-05-31
Fu, thank you for all of your help. I'm going to look into everything you suggested and go that route. I won't be using any nas software, and will be backing up instead of using raid. Thank you again.

---

### Post by aaron50 on 2016-06-01
Fu, one last question. Does it matter what i use for the hard drive that the operating system(ubuntu 14.04) is on? I have an old 100GB HHD, but was considering getting a new SSD for the operating system, will i see improvement or would this be a waste of money?

---

### Post by TheFu on 2016-06-01
> **aaron50 said:**
> Fu, one last question. Does it matter what i use for the hard drive that the operating system(ubuntu 14.04) is on? I have an old 100GB HHD, but was considering getting a new SSD for the operating system, will i see improvement or would this be a waste of money?

TL;DR - no. SSDs aren´t helpful for this situation to justify the expense, to me.

Long-winded version ... 
I consider SSDs to be a waste of money for most purposes. They are faster, but Linux is really, really, really, good at buffering disk access when things are predictable.  RAM is automatically used for disk buffers, when available.  For example, I do a little video editing with hidef content.  The files start out as 17G or so for 2 hrs.  Then I remove all commercials (11G) and transcode to 720p h.264 the files are 2.8G in size without any artifacts seen by me that weren´t in the original OTA transmission.  Here´s the memory use for the transcoding machine:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7975       5675       2300          0         29       3200
-/+ buffers/cache:       2445       5530
Swap:         6579        686       5893

```
It has 8G of RAM. 2.4G are in use as disk buffers (mainly for file transfers), but 2.3G of RAM is free if more were needed.  The commercial removal was done on a Windows machine, but this storage was used. It is a 1TB Blue drive in the transcoding box. Transcoding is both disk and CPU intensive, but the CPU is more important so disk performance isn´t the critical point.  The network file transfers are all going through disk buffers anyway, so those happen at about 920Mbps (1 GigE network here).  The buffers are in RAM - so wire-speed is what I see for those until the spinning disk reads are what delay things.  Note the small use of swap?  I could easily remove all swap from this system and not notice it.

All that is to say - SSDs just aren´t needed for a media server or even an average transcoding machine.  However, if I were a professional in the video creation industry where time was money, I´d have a 4-way stripe (RAID0) of SSDs for all ¨in-work¨ media since my CPU would be the $1800 Xeon designed for that workload and disk performance WOULD matter.  I wouldn´t leave any temporary files on that stripe overnight, since 1 failure would lead to total data loss, but for a workspace where disk performance matters more than anything else, fine.  Of course, I´d also have 32G (or more) of RAM in that box which would be used mostly as disk buffers too. ;)

Probably more than you wanted to know, but server system performance comes down to a limitation of 4 things:
* CPU
* RAM
* Disk I/O
* Network I/O

For desktops, might add GPU performance to that list. Built-in GPUs have more performance than I´ve needed the last 10 yrs, so I never consider that a bottleneck. The last discrete GPU I bought was a $30 nVidia 430GT, which replaced a 5 yr old 7600GS. It doesn´t matter for a media server and hasn´t since the built-in GPUs added mpeg2 and h.264 drivers to make the GPU handle all that processing.  Heck, a Raspberry Pi has this in HW too, for $35. It just isn´t important anymore.

Performance tuning is all about removing the cheap roadblocks until it isn´t possible to fix the remaining ones.  RAM is hardly ever the issue on my systems and most of them have 4, 6, 8G total.  Only 1 has 16G (it was cheap) ... just checked it - 10G are used for disk buffers.  Hardly an efficient use of RAM, IMHO.

The only time I´ve found SSDs useful are in ultra-book laptops where power use, portability and standby are used constantly. Folks claim that SSD performance makes all the difference - perhaps it does if you reboot all the time.  I don´t and your media center won´t be rebooting all the time either.  Starting an app that needs more than 2 seconds is a problem with the application, IMHO. Find a better application if you can´t wait for it.  The simple answer in that case is to avoid huge applications written using either Java or Mono frameworks.  But I digress. I´ve never found any desktop application written in java that wasn´t a hog - big and slow - for what it accomplished.

---

