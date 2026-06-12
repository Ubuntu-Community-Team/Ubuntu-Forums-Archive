---
title: "Suggestions for an affordable NAS for backups and Plex (media center)"
date: 2014-06-11
forum: Hardware
---

### Post by sberla54 on 2014-06-11
Hello everyone,
i've got this in idea in mind and i need your suggestions: i would like to buy a NAS that is reasonably cheap but totally reliable and that can be my Plex media center too. 

I want to put all my important data there and i want to be 100% sure that i won't lose them. So far, i'm still making DVD of the stuff i want to keep for a long time, and using an external drive for "light" stuff, like music, and a WD TV Live with an external drive for "heavy" stuff, like movies and TV series.
I would like to use Plex as media server and media client so i'm oriented towards a QNAP, that has the integrated Plex app and is cheaper than a Synology.
I was thinking about a little Raspberry Pi with RasPlex ([http://www.rasplex.com/](http://www.rasplex.com/)) linux, connected with HDMI to the TV and with wireless or ethernet (i can't decide) to the LAN.

I was considering the Qnap TS-212P ([http://www.amazon.com/TS-212P-Personal-Network-Attached-Storage/dp/B00G2HZNXO/ref=sr_1_1?ie=UTF8&qid=1402523008&sr=8-1](http://www.amazon.com/TS-212P-Personal-Network-Attached-Storage/dp/B00G2HZNXO/ref=sr_1_1?ie=UTF8&qid=1402523008&sr=8-1) / [http://www.qnap.com/useng/index.php?sn=862&c=355&sc=688&t=696&n=19604](http://www.qnap.com/useng/index.php?sn=862&c=355&sc=688&t=696&n=19604))
It's cheap, 173 dollars, it has 2 bays, so i can do a RAID 1, but i'm not sure it could do some good transcoding when needed because of CPU (Marvell 6282 1.6GHz) and RAM CPU (512MB DDR3)

I've got a Western Digital Elements 2 TB USB 2.0 Desktop external disk ([http://www.amazon.com/Elements-Desktop-External-Hard-Drive/dp/B002QEBMCI/ref=sr_1_2?ie=UTF8&qid=1402523455&sr=8-2](http://www.amazon.com/Elements-Desktop-External-Hard-Drive/dp/B002QEBMCI/ref=sr_1_2?ie=UTF8&qid=1402523455&sr=8-2)) and i could open it and use it as one of the disks for the NAS.
I also have got an external USB Western Digital My Book 2 TB ([http://www.amazon.com/Book-USB-Hard-Drive-Backup/dp/B00E3RH5W2/ref=sr_1_1?ie=UTF8&qid=1402525023&sr=8-1):](http://www.amazon.com/Book-USB-Hard-Drive-Backup/dp/B00E3RH5W2/ref=sr_1_1?ie=UTF8&qid=1402525023&sr=8-1):) is it a 3.5' drive? I could open it, so i'll have 2 free disks.

Then a 40 dollars Raspberry Pi ([http://www.amazon.com/RASPBERRY-MODEL-756-8308-Raspberry-Pi/dp/B009SQQF9C/ref=sr_1_1?ie=UTF8&qid=1402523619&sr=8-1](http://www.amazon.com/RASPBERRY-MODEL-756-8308-Raspberry-Pi/dp/B009SQQF9C/ref=sr_1_1?ie=UTF8&qid=1402523619&sr=8-1)) would be the only thing left.
Total cost: 173 + 40 = almost 210 dollars, pretty affordable.

Now, the point. I've got some doubts:
01) Is it a RAID 1 a good choice for reliable backups? It's simply a mirror, so if both disks don't fail at the same time i should be pretty safe, shouldn't i?
02) What other kind of RAID or storage could i do with a 2 bays NAS?
03) Considering that i should already have 2 free 2 Tb disks, i could buy another Western Digital Green 2 TB SATA3 ([http://www.amazon.com/WD-Green-Desktop-Hard-Drive/dp/B008YAHW6I/ref=sr_1_2?ie=UTF8&qid=1402523554&sr=8-2](http://www.amazon.com/WD-Green-Desktop-Hard-Drive/dp/B008YAHW6I/ref=sr_1_2?ie=UTF8&qid=1402523554&sr=8-2)) for 82 dollars and then a 3 bays NAS. Could i have more space like that? Maybe doing a RAID5 using 2 disks for data and 1 for bit redundancy, so that i have 4 Gb of space?
04) Is the CPU of the Qnap TS-212P good enough as a Plex server?
05) Is a Raspberry Pi good enough as a Plex client? Could it work in wireless? I can download up to 5 Mb/sec (40 Mbit of bandwidth) with my wireless N router.

Sorry for all those questions. I know it's a long post but it's an intriguing project and trying to keep it cheap isn't so easy. Besides, i'm a total newbie in this stuff.

Thank you in advance.

---

### Post by TheFu on 2014-06-11
Cannot suggest any NAS - I build my own. Sorry.  All the others seem so very limited compared to a configured Ubuntu Server with storage. If you are new to this, check out FreeNAS to learn some more.

Also, I would strongly suggest that you do NOT confuse backups with RAID.  Backups are always necessary for things you don't want to loose. ALWAYS.  RAID is for HA - high availability, not backups.  Don't touch RAID until you have solid, 100% recoverable backups working.

If the data isn't on at least 2 different physical systems, you do NOT have a backup.  For media that you are willing to loose, something like SnapRAID may be sufficient protection - I dunno. I still use backups and buy 2 HDDs at a time - primary and backup disk.

A few yrs ago, I built an XBMC machine with an AMD-E350 APU for $150 (this is like a dual-core Atom in performance).  About 6 months ago, i added plex server to that. It isn't powerful enough to transcode on the fly (no commercial NAS will be), but it is a great media player and NFS server here. 100% silent thanks to a pico-PSU.

The idea for R-Pi is common, until you look at the specs closer and throughput.  For a toy, it is fine.  For an unlimited media playback device, it leaves much to be desired.  I have a Chromecast, WDTV Live HD, MediaGate and my home-built XBMC box - the home-built one blows all the others away.  All the others have limited format support - being burned by string file formats is frustrating - how many FLV formats are there that most devices do not handle anyway?

---

### Post by sberla54 on 2014-06-12
> [COLOR=#000000]Also, I would strongly suggest that you do NOT confuse backups with RAID. Backups are always necessary for things you don't want to loose. ALWAYS. RAID is for HA - high availability, not backups. Don't touch RAID until you have solid, 100% recoverable backups working.[/COLOR]

Yes, you're pretty right if we think at a work scenario but i think there's no need to over-complicate the home scenario. I mean, so far i've always followed your logic: "be sure to have two copies of an important data, on two differend phisical media". With a NAS, i stay loyal to this logic. The NAS is only one but the phisical media are 2 or 3.
As long as somebody doesn't steal my NAS or my home doesn't get burned to the ground, what else can i fear?
By the way, i'm subscribed to CrashPlan that also does an online backup of the most important data.

> [COLOR=#000000]A few yrs ago, I built an XBMC machine with an AMD-E350 APU for $150 (this is like a dual-core Atom in performance). About 6 months ago, i added plex server to that. It isn't powerful enough to transcode on the fly (no commercial NAS will be), but it is a great media player and NFS server here. 100% silent thanks to a pico-PSU.[/COLOR]

I've read on some articles that some NAS are able to transcode without a problem. I just don't understand what is the reccomended hardware.
A question for you that are more expert than me: how often is transcoding needed? In which occasions?

> [COLOR=#000000]The idea for R-Pi is common, until you look at the specs closer and throughput. For a toy, it is fine. For an unlimited media playback device, it leaves much to be desired.[/COLOR]

RasPlex seems pretty cool and with good performance, on the contrary: [https://www.youtube.com/watch?v=C-A4Kxq3V0I](https://www.youtube.com/watch?v=C-A4Kxq3V0I)

---

### Post by TheFu on 2014-06-12
2 copies in RAID don't fix a corrupted file. The corrupted file is stored twice.  Versioned backups DO!

Rpi can playback specific files great - using hardware encoders with specific (paid) drivers. Those are mpeg2 and h.264.  Is any of your media anything other than those?  If so - you'll want a little more powerful CPU to handle decoding in the chip.

Ok ... a NAS **can** transcode - just like my AMD E350 can ... just not in real time for specific device requirements.  I wouldn't throw anything less than a Core i5 at a real-time transcode problem if hidef is involved.  If you like, you CAN pre-transcode to the required formats.  Just don't expect it to happen quickly.

As for the Rpi being a good NAS - I guess that depends on your thoughput expectations.  GigE this ain't.  USB3, this ain't.  Perhaps I'm being a little elitist, but i have tried to use the WDTV-Live as a NAS - 100Mbps is just ... slow.  NAS devices don't need too much CPU, but they do need GigE wired, IMHO. And they need support for NFS (and Linux-based file systems) - not NTFS and CIFS.  Life will be much better that way.  A few friends have commercial NAS devices.  I get to hear them cuss about the restricted "certified" HDD support.  Perhaps that has changed, I dunno.  Spending $800 for a 4-drive NAS seems crazy to me when building a 10 HDD box can be accomplished for $600. Just look at the build-guides over at FreeNAS websites.  A C2D CPU is not quite enough power for real-time transcoding according to this: [http://forums.freenas.org/index.php?threads/plex-transcoding-performance-initial-measurements.16360/](http://forums.freenas.org/index.php?threads/plex-transcoding-performance-initial-measurements.16360/)  I've seen other recommendations to get a Core i5, not i3 if transcoding is needed.

So ... I guess it comes down to your requirements for transcoding.  I record TV OTA - that results in 480p-1080i MPEG2 files.  Most are watch-once and delete.  To watch those on any Android device means transcoding to h.264/AAC ... a Core i5 is needed to do that in realtime.  Forget using an R-pi for that.

After all, if you want a cheap player, the WD TV already does that - why not keep using it?  It supports many more formats than a R-pi can - in hardware.  

Or build the r-pi and learn what I mean later. It is an interesting piece of hardware for certain uses - I'm certain you will find a purpose.

---

### Post by sberla54 on 2014-06-12
Thank you for your answer! You've really been useful!

> [COLOR=#000000]2 copies in RAID don't fix a corrupted file. The corrupted file is stored twice. Versioned backups DO![/COLOR]

You're totally right!
This is what i have in mind: i'm going to keep using CrashPlan for versioned backups, local and online. The local backup is going to be stored on the NAS, so that it is always mirrored or in RAID. The online is in the cloud.
Apart from that, i'm going to store a single copy of the less important data, like music and movies, directly on the NAS. It's easier to lose them but that's ok.

> [COLOR=#000000]Rpi can playback specific files great - using hardware encoders with specific (paid) drivers. Those are mpeg2 and h.264. Is any of your media anything other than those? If so - you'll want a little more powerful CPU to handle decoding in the chip.[/COLOR]

I think you're mistaking on this point.
I've read a couple of articles and a lot of people is using Plex on Rpi with RasPlex and they're happy about it: [http://www.techmadeeasy.co.uk/2013/06/07/review-rasplex-for-raspberry-pi/](http://www.techmadeeasy.co.uk/2013/06/07/review-rasplex-for-raspberry-pi/)
[http://lifehacker.com/5929913/build-a-xbmc-media-center-with-a-35-raspberry-pi](http://lifehacker.com/5929913/build-a-xbmc-media-center-with-a-35-raspberry-pi)

> [COLOR=#2B2B2B][FONT=Lato]While it’s no where near as powerful as a full PC, a Raspberry Pi running Rasplex provides a decent level of performance.  It’s not quite as fluid as a PC or Mac running the standard version of Plex, but it runs rings around the official version available for my Samsung Smart TV, and builds on the success of the XBMC distributions already available for the Pi.[/FONT][/COLOR]

> [FONT=Georgia]However, compared to [/FONT][other more powerful builds]("http://lifehacker.com/5936546/how-i-built-the-media-center-of-my-dreams-for-under-500")[FONT=Georgia], there are some things the Pi does not do. It will not stream content from the internet (like Hulu), and you may experience stuttering with 1080p videos. 
[/FONT][FONT=Georgia]The Raspberry Pi's menus will definitely feel a bit slower as well, and it won't load high-res fanart as well as more powerful builds—so if you're looking to have a particularly tricked-out, gorgeous XBMC skin, you might be out of luck here. However, as a secondary media center for a smaller TV, or as a media center for simple 720p playback, it's a force to be reckoned with.[/FONT]

I don't see 1080 videos so often, sometimes i see 720. have you seen this video test? [https://www.youtube.com/watch?v=C-A4Kxq3V0I](https://www.youtube.com/watch?v=C-A4Kxq3V0I)

> [COLOR=#000000]Ok ... a NAS **can** transcode - just like my AMD E350 can ... just not in real time for specific device requirements. I wouldn't throw anything less than a Core i5 at a real-time transcode problem if hidef is involved. If you like, you CAN pre-transcode to the required formats. Just don't expect it to happen quickly.[/COLOR]


That's bad :/ 
It could crash my whole project..
I've found this couple of howtos from Plex about NAS and i'm going to read them ASAP:
[https://support.plex.tv/hc/en-us/articles/201373793](https://support.plex.tv/hc/en-us/articles/201373793)
[https://support.plex.tv/hc/en-us/articles/201373823](https://support.plex.tv/hc/en-us/articles/201373823)

> [COLOR=#000000]As for the Rpi being a good NAS - I guess that depends on your thoughput expectations. GigE this ain't. USB3, this ain't. Perhaps I'm being a little elitist, but i have tried to use the WDTV-Live as a NAS - 100Mbps is just ... slow. NAS devices don't need too much CPU, but they do need GigE wired, IMHO. And they need support for NFS (and Linux-based file systems) - not NTFS and CIFS. Life will be much better that way. A few friends have commercial NAS devices. I get to hear them cuss about the restricted "certified" HDD support. Perhaps that has changed, I dunno. Spending $800 for a 4-drive NAS seems crazy to me when building a 10 HDD box can be accomplished for $600. Just look at the build-guides over at FreeNAS websites. A C2D CPU is not quite enough power for real-time transcoding according to this: [/COLOR][http://forums.freenas.org/index.php?...rements.16360/]("http://forums.freenas.org/index.php?threads/plex-transcoding-performance-initial-measurements.16360/")[COLOR=#000000] I've seen other recommendations to get a Core i5, not i3 if transcoding is needed.[/COLOR]


The Rpi will only be the Plex client, attached to the TV. Nothing else.
You're right about Gigabit ethernet being really better than Fast ethernet. I've got a Gigabit router so it would be a shame to waste its LAN speed.
I'm going to read the FreeNAS article, thank you!

> [COLOR=#000000]So ... I guess it comes down to your requirements for transcoding. I record TV OTA - that results in 480p-1080i MPEG2 files. Most are watch-once and delete. To watch those on any Android device means transcoding to h.264/AAC ... a Core i5 is needed to do that in realtime. Forget using an R-pi for that.[/COLOR]


Roger that!

Now i'm curious: could you please tell me how much money you spent on your Media Center and what's the exact hardware and software? If it's small and silent, i have no problem trying to use FreeNAS with Plex on it.

---

### Post by TheFu on 2014-06-12
> **sberla54 said:**
> Now i'm curious: could you please tell me how much money you spent on your Media Center and what's the exact hardware and software? If it's small and silent, i have no problem trying to use FreeNAS with Plex on it.

My system is NOT perfect.  It is much better than anything else I've used.

The HW I have isn't available anymore.  I got a deal on a MB+APU+Case for $99 in mid-2012.
* Gigabyte AMD E350 APU (that is MB, CPU, GPU all in one).
* Case is a steel monster that I could stand on from Istar.
* Bought 4G of RAM for $28
* Swapped out the jet-engine-like power supply for a pico-PSU 80W from mini-box.com ($45?)
* Reused an old 320G Seagate HDD ... until last fall, swapped in a 4TB Hitachi.

No monitor - it connects to an HDMI switch - usually displays through a projector.
No keyboard - I ssh into it.
Wired GigE networking.
[Blog on the system build.]("http://blog.jdpfu.com/2012/08/15/building-a-new-to-me-system")

Software:
* Ubuntu Server 12.04. I patch about quarterly, to stay out of the dog house if anything bad happens.
* XBMC "Frodo"
* Plex-XBMC addon (not the Plex client)
* Plex Server (whatever is current today)
* nfsv4 - this is for other systems to access the storage. I avoid CIFS/samba here now; ran that for many, many, years - since the mid-1990s. The NFS performance is noticeably faster than CIFS, plus it behaves like local storage.

We all start out thinking that backups for media aren't important. Eventually, you'll think about the time (hrs, days, weeks) it took to create the collection and $150 for a 4TB HDD doesn't seem like all that much to have backups that are trivially restored.  Remote backups for wedding and baby photos are great. Not so great when you have 12+TB of stuff. How will that stuff be restored?  Trickle-down theory? ;)

I backup media differently than everything else. For everything except media, I use rdiff-backup. Here's a [good explanation with examples.]("http://www.kirya.net/articles/backups-using-rdiff-backup/")  It is an amazing backup tool, though I wouldn't use it for remote storage that I didn't 100% control, trust, own, since it does NOT encrypt.  I haven't found any backup tools that encrypt, but remain useable and non-beta quality.

Oh - freeNAS will not be good on my little E350 - not enough RAM and the disk IO on that MB just isn't all that great for multiple HDDs. Plus, only 1 HDD fits inside it.  Having external storage next to a high-traffic TV isn't smart, IMHO.  I consider 8G to be the bare minimum for ZFS and RAIDz2 really wants 6 HDDs.  In short - no FreeNAS for me, but anyone building a NAS themselves should read up on the FreeNAS suggested hardware.

If the Rpi is just a playback device - then you'll want something that can transcode for it on the Plex Server side.  If you're going that way - a pre-built device like a WDTV, Roku, A-TV, even a ChromeCast for the player is much easier than an R-Pi.  Just sayin.  Heck, if you have a smart TV - the r-pi is excess and not necessary, provided the Plex Server can transcode for it.

You have much to consider.

---

### Post by sberla54 on 2014-06-12
> [COLOR=#000000]My system is NOT perfect. It is much better than anything else I've used.[/COLOR]

[COLOR=#000000]The HW I have isn't available anymore. I got a deal on a MB+APU+Case for $99 in mid-2012.[/COLOR]
[COLOR=#000000]* Gigabyte AMD E350 APU (that is MB, CPU, GPU all in one).[/COLOR]
[COLOR=#000000]* Case is a steel monster that I could stand on from Istar.[/COLOR]
[COLOR=#000000]* Bought 4G of RAM for $28[/COLOR]
[COLOR=#000000]* Swapped out the jet-engine-like power supply for a pico-PSU 80W from mini-box.com ($45?)[/COLOR]
[COLOR=#000000]* Reused an old 320G Seagate HDD ... until last fall, swapped in a 4TB Hitachi.[/COLOR]

[COLOR=#000000]No monitor - it connects to an HDMI switch - usually displays through a projector.[/COLOR]
[COLOR=#000000]No keyboard - I ssh into it.[/COLOR]
[COLOR=#000000]Wired GigE networking.[/COLOR]
[Blog on the system build.]("http://blog.jdpfu.com/2012/08/15/building-a-new-to-me-system")

[COLOR=#000000]Software:[/COLOR]
[COLOR=#000000]* Ubuntu Server 12.04. I patch about quarterly, to stay out of the dog house if anything bad happens.[/COLOR]
[COLOR=#000000]* XBMC "Frodo"[/COLOR]
[COLOR=#000000]* Plex-XBMC addon (not the Plex client)[/COLOR]
[COLOR=#000000]* Plex Server (whatever is current today)[/COLOR]
[COLOR=#000000]* nfsv4 - this is for other systems to access the storage. I avoid CIFS/samba here now; ran that for many, many, years - since the mid-1990s. The NFS performance is noticeably faster than CIFS, plus it behaves like local storage.[/COLOR]

It seems pretty affordable and pretty easy to setup, indeed. I will think about something similar too. (The blog isn't loading...)

> [COLOR=#000000]Oh - freeNAS will not be good on my little E350 - not enough RAM and the disk IO on that MB just isn't all that great for multiple HDDs. Plus, only 1 HDD fits inside it. Having external storage next to a high-traffic TV isn't smart, IMHO. I consider 8G to be the bare minimum for ZFS and RAIDz2 really wants 6 HDDs. In short - no FreeNAS for me, but anyone building a NAS themselves should read up on the FreeNAS suggested hardware.[/COLOR]


And i will keep this in mind.

What about your backups? Where do you store them? I suppose that 4 Gb Hitachi is dedicated to media... do you backup them? Where? And where else do you backup your important data?

> [COLOR=#000000]We all start out thinking that backups for media aren't important. Eventually, you'll think about the time (hrs, days, weeks) it took to create the collection and $150 for a 4TB HDD doesn't seem like all that much to have backups that are trivially restored. Remote backups for wedding and baby photos are great. Not so great when you have 12+TB of stuff. How will that stuff be restored? Trickle-down theory? [/COLOR]:wink:


Understand me: losing my music and my movie library would make me crazy, that's obvious, but, as i've said before, i think a some kind of RAID would be enough for me. It could happen a couple of times that an album or a movie gets currupted, but that's not the end of the world. The important thing is that i don't risk to lose everything because of an hardware failure.

> [COLOR=#000000]I backup media differently than everything else. For everything except media, I use rdiff-backup. Here's a [/COLOR][good explanation with examples.]("http://www.kirya.net/articles/backups-using-rdiff-backup/")[COLOR=#000000] It is an amazing backup tool, though I wouldn't use it for remote storage that I didn't 100% control, trust, own, since it does NOT encrypt. I haven't found any backup tools that encrypt, but remain useable and non-beta quality.[/COLOR]

I know rdiff-backup, i used to use it before switching to CrashPlan, that is pretty good, does encrypt but its client is a little bit too heavy on my system.

> [COLOR=#000000]If the Rpi is just a playback device - then you'll want something that can transcode for it on the Plex Server side. If you're going that way - a pre-built device like a WDTV, Roku, A-TV, even a ChromeCast for the player is much easier than an R-Pi. Just sayin. Heck, if you have a smart TV - the r-pi is excess and not necessary, provided the Plex Server can transcode for it.[/COLOR]

Plex is way more cool than a WDTV or a ChromeCast, don't you think?
I could just buy a cheap NAS and attach it to my WDTV, but it hasn't a third that the features that Plex has. You use XBMC and Plex, you know it.
ChromeCast was my primary choice as the Plex client but it has a lot of problems with external subtitles, that are truly important to me.

Considering that you seem to really know what your talking about, may i ask you to answer me some of my initial questions about RAID? :) Like 1, 2 and 3. I mean, what kind of RAID are commonly used? RAID0 sucks, RAID1 is just a mirror, what kind of RAID should i choose if i want to use 2 or 3 disks for the data and 1 or 2 for the redundancy? 
I would like to create, for example, a RAID with 4 disks of 2 Tb and have 6 Tg of space.
It seems like a 3 bays NAS doesn't even exists, am i right? There are only 2 and 4 bays (and more..).

---

### Post by TheFu on 2014-06-12
> **sberla54 said:**
> It seems pretty affordable and pretty easy to setup, indeed. I will think about something similar too. (The blog isn't loading...)
Is there an error or just stuck.  I do block a small selection of subnets around the world - after finding abuse from them. I also block certain clients - mostly abusive RSS readers.

> **sberla54 said:**
> What about your backups? Where do you store them? I suppose that 4 Gb Hitachi is dedicated to media... do you backup them? Where? And where else do you backup your important data?
My home network is a business network too.  I have a backup server with lots of storage.  Some of the servers also have RAID1 storage in an external disk array. Non-media files are backed up from about 30 different machines (really 7, but adding all the virtual machines) using rdiff-backup. I retain 60-120 days of daily backups there.  Media files are backed up to a different machine with temporary storage. I have 2 dual SATA dock USB3 devices. That means 4xHDDs can be used for media backup concurrently. Also, those docks are easily swapped with different HDDs, as needed.

The xbmc machine ()OS, settings, /home, /var) is backed up with rdiff-backup too.

> **sberla54 said:**
> Understand me: losing my music and my movie library would make me crazy, that's obvious, but, as i've said before, i think a some kind of RAID would be enough for me. It could happen a couple of times that an album or a movie gets currupted, but that's not the end of the world. The important thing is that i don't risk to lose everything because of an hardware failure.

RAID cannot replace backups. Sorry that I've failed to clearly state the reasons why. It is my failure.  RAID can be added AFTER backups are working perfectly if HA is needed. There are many failures that backups can solve where RAID is screwed.

> **sberla54 said:**
> I know rdiff-backup, i used to use it before switching to CrashPlan, that is pretty good, does encrypt but its client is a little bit too heavy on my system.

Odd. I've never had any issues with it. I suppose trickle 24/day could appear to be less network load. Backups take between 0-4 minutes per server. Many systems are less than 30 seconds to backup, if nothing changed.  Restore (I do screw up sometimes) takes about 30-45 minutes for everything ... except the media files.

> **sberla54 said:**
> Plex is way more cool than a WDTV or a ChromeCast, don't you think?
I could just buy a cheap NAS and attach it to my WDTV, but it hasn't a third that the features that Plex has. You use XBMC and Plex, you know it.

The WDTV is a playback device thru the DLNA client. It is on the same level as the R-pi.  My WDTV only supports USB storage - not any "NAS" - are we using the same terms for the same meaning?

> **sberla54 said:**
> ChromeCast was my primary choice as the Plex client but it has a lot of problems with external subtitles, that are truly important to me.
I use mkv containers and put the subtitles inside using mkvmerge.  Managing 1 file is much easier for me.

> **sberla54 said:**
> Considering that you seem to really know what your talking about, may i ask you to answer me some of my initial questions about RAID? :) Like 1, 2 and 3. I mean, what kind of RAID are commonly used? RAID0 sucks, RAID1 is just a mirror, what kind of RAID should i choose if i want to use 2 or 3 disks for the data and 1 or 2 for the redundancy? 
I would like to create, for example, a RAID with 4 disks of 2 Tb and have 6 Tg of space.
It seems like a 3 bays NAS doesn't even exists, am i right? There are only 2 and 4 bays (and more..).

I've only used RAID1, RAID10, RAID5 and RAIDz.  Wikipedia can answer those questions better than I can.  I stopped using RAID5 over a year ago. There is a possible issue where data sent to the disks won't get written, so the array will become corrupted. There are also predictions that with larger HDDs, should a drive in a RAID set fail, another drive will fail during the rebuild after a replacement HDD is added to the array. I don't know that I believe it, but to me, storage is cheap and not worth screwing around over. The purpose for all these systems is to process data and to protect the data.  It is not about the hardware.  RAIDz is the only RAID that i know which validates what was asked to be written actually was written. RAIDz is only available through ZFS ... which requires much more CPU and RAM than I'm willing to put towards a storage server. I figure between RAID and backups, I'm covered.

You can create whatever sort of RAID you like in software (mdadm). There are standard ways to do RAID1, RAID10, RAID5, RAID6 and all the others. Do a little reading from reputable sources to ensure you don't choose something bad.  These choices impact the redundancy and ease of resolution when something bad happens.  BTW, something bad is always gonna happen, even if it is self-inflicted. It is when you go with hardware RAID or commercial "easy" products that limitations begin. Follow the manual for the device and it should be fine.

BTW - some people use SnapRAID for media collections.

---

### Post by sberla54 on 2014-06-12
> [COLOR=#000000]My home network is a business network too. I have a backup server with lots of storage. Some of the servers also have RAID1 storage in an external disk array. Non-media files are backed up from about 30 different machines (really 7, but adding all the virtual machines) using rdiff-backup. I retain 60-120 days of daily backups there. Media files are backed up to a different machine with temporary storage. I have 2 dual SATA dock USB3 devices. That means 4xHDDs can be used for media backup concurrently. Also, those docks are easily swapped with different HDDs, as needed.[/COLOR]

Massive! :)

> [COLOR=#000000]RAID cannot replace backups. Sorry that I've failed to clearly state the reasons why. It is my failure. RAID can be added AFTER backups are working perfectly if HA is needed. There are many failures that backups can solve where RAID is screwed.[/COLOR]

Don't apologize, you've been totally clear. The fact is that i was too excited about this project of a single place where to stock everything that it's difficult to give up and change my mind :)

> [COLOR=#000000]Odd. I've never had any issues with it. I suppose trickle 24/day could appear to be less network load. Backups take between 0-4 minutes per server. Many systems are less than 30 seconds to backup, if nothing changed. Restore (I do screw up sometimes) takes about 30-45 minutes for everything ... except the media files.[/COLOR]

I was saying that CrashPlan was slow and heavy, not r-diff :)

> [COLOR=#000000]The WDTV is a playback device thru the DLNA client. It is on the same level as the R-pi. My WDTV only supports USB storage - not any "NAS" - are we using the same terms for the same meaning?[/COLOR]


I'm talking about the Western Digital WD TV Live ([http://www.amazon.com/Live-Media-Player-Wi-fi-1080p/dp/B005KOZNBW/ref=sr_1_1?ie=UTF8&qid=1402615261&sr=8-1](http://www.amazon.com/Live-Media-Player-Wi-fi-1080p/dp/B005KOZNBW/ref=sr_1_1?ie=UTF8&qid=1402615261&sr=8-1)) media player. It's a small device that can read from USB but can also access any network drive, so i could mount the NAS as an NFS share and play movies from there.


> [COLOR=#000000]I've only used RAID1, RAID10, RAID5 and RAIDz. Wikipedia can answer those questions better than I can. I stopped using RAID5 over a year ago. There is a possible issue where data sent to the disks won't get written, so the array will become corrupted. There are also predictions that with larger HDDs, should a drive in a RAID set fail, another drive will fail during the rebuild after a replacement HDD is added to the array. I don't know that I believe it, but to me, storage is cheap and not worth screwing around over. The purpose for all these systems is to process data and to protect the data. It is not about the hardware. RAIDz is the only RAID that i know which validates what was asked to be written actually was written. RAIDz is only available through ZFS ... which requires much more CPU and RAM than I'm willing to put towards a storage server. I figure between RAID and backups, I'm covered.[/COLOR]

[COLOR=#000000]You can create whatever sort of RAID you like in software (mdadm). There are standard ways to do RAID1, RAID10, RAID5, RAID6 and all the others. Do a little reading from reputable sources to ensure you don't choose something bad. These choices impact the redundancy and ease of resolution when something bad happens. BTW, something bad is always gonna happen, even if it is self-inflicted. It is when you go with hardware RAID or commercial "easy" products that limitations begin. Follow the manual for the device and it should be fine.[/COLOR]

[COLOR=#000000]BTW - some people use SnapRAID for media collections.[/COLOR]

Clear! Thank you for your explanation!
I've got a lot to consider.

---

