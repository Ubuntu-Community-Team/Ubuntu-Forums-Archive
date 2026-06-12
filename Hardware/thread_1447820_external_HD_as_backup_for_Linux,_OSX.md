---
title: "external HD as backup for Linux, OSX"
date: 2010-04-05
forum: Hardware
---

### Post by eltonw on 2010-04-05
I am finding more and more that DVD's are less and less reliable as a a backup medium, especially RW disks. The slightest scratch, no matter how careful one may be, means that important data is lost forever. 

CD/DVD repair kits do not always help.

IMHO, the fact that HDs are enclosed make them more reliable, _though_ ... as with anything else ... _not infallible_. As such, I am considering the purchase of an external USB HD (perhaps 1 Tb) to back up my ubuntu linux and OSX machines. 

[FONT=Arial Black](I do not use Windows).[/FONT]

Some searching here and there leave me a bit more confused. [FONT=Trebuchet MS]Would I need special drivers for a NON-windows system?[/FONT] 

My idea would be to create two, four, or more partitions on the external drive, format as VFAT (so that long filenames created in linux or OS/X would be compatible). In the case of any failure, just the contents of a partition would be lost, _rather than everything on the entire disk_.

Also, to my thinking, I could even use two partitions to create duplicate backups, particularly with aforethought to possible partition failure.

I am looking at some external self-powered drives on places such as newegg, for example.

Any recommendations, caveats on **particular brands**? Comments WRT **backup methods**? FS TYPE?

TIA....

respectfully,

---

### Post by byStanderone on 2010-04-05
...hi, you can give a little push to your thread by giving the specs of your ubuntu box, am sure there are lots of members who'd like to help.

---

### Post by Cracauer on 2010-04-05
I strongly recommend against USB as the interface for external harddrives. Even if you happen to have a decent USB chip and cables in your computer right now, it only takes connecting it to some other PC in the future and the dices roll from scratch. Firewire or SATA.

Then, the weakness of this kind of backup is that you only have one generation of backup, or in your case two. If you have silent memory corruption on your primary computer, or you fatfinger something you recognize only much later, then all your backups have been overwritten with the bad data by the time you notice.

Partitioning doesn't protect you against the harddrive breaking, which will be a common kind of defect.

There is no easy solution for any of this given modern harddrive sizes and lack of suitable backup devices with shelfable media. Myself I went with a snapshotted, raided solution in the basement for backups as described here:
[http://www.cons.org/cracauer/backup.html](http://www.cons.org/cracauer/backup.html)

It's a little more effort than plugging in a Firewire drive but hey just a couple months of work and you'll be right there :)

---

### Post by tux99 on 2010-04-05
I wouldn't give up too soon on DVD-Rs, there are some (Verbatim Archival) which are resistant to scratches and very suitable for long term archiving of data. But ultimately no medium is perfect, the trick is to have at least 2 copies of everything important, ideally on different types of media.
There is an interesting article about this [here]("http://www.linuxtech.net/tips+tricks/best_safe_long-term_data_storage.html").

You should also categorize your data, in 3 categories:
- irreplaceable data you absolutely cant afford to loose (personal photos, documents, cam-corder shoots)
- data that can be replaced but requires effort and expense to do so (movies, music files, etc)
- back-ups of software and OS installs

You should deal with each category separately and start with the first one for obvious reasons.
A raid array is certainly not adequate for the first category (at least not without further back-up copies).

---

### Post by eltonw on 2010-04-06
> **by Standerone said:**
> ...hi, you can give a little push to your thread by giving the specs of your ubuntu box, am sure there are lots of members who'd like to help.

It is an Asus EEE 1000 PC netbook, with 2 SDDs (total 40 Gb). The other machine is a MacBook with a 250 Gb HD. I regularly update or try different linux distros on the netbook. The laptop is for multimedia, lots of music, graphics work. Hence the greater part of my backups would be with Time Machine on the Macbook.

Once in a while, I would swap out the USB plug and connect it to back up the netbook on a separate partition.

**[COLOR="Green"]@ Cracauer[/COLOR]**: The commonality of both machines is USB, **[COLOR="Red"]neither [COLOR="Black"]machine[/COLOR] has a firewire port[/COLOR]**, so even though I did consider the faster throughput, that type of connection is out of the question. As for partitioning I realise that hard drives **do** also eventually fail. [COLOR="Olive"][FONT="Century Gothic"]But my thinking is that if a partition gets corrupted, I don't lose everything in one shot.[/COLOR][/FONT]
With respect to your mention of a RAID array, I am not running a business: this is just personal data. Cost is also a factor. AFAIK, A RAID array would cost me more than a single external HD.:confused:
[FONT="Comic Sans MS"][COLOR="DarkRed"]The reason I am using portables rather than (a) desktop(s) is that I live in a really tiny apartment.[/COLOR][/FONT] (Otherwise I'd have gotten a 17" laptop, instead of a 13" one!:lolflag:

[COLOR="DarkRed"]**@ tux99:**[/COLOR]I'm not esactly "giving up" on DVD, BUT the fact is that type of media is more susceptible to damage, since it is not enclosed like a HD.[COLOR="Sienna"] (Remember when all CD drives used a cartridge?)[/COLOR] Actually, since SDDs have no moving parts, unlike HDDs, that would be even better, but solid state drives are still steep in price.

I do agree with you about doing double backups with one backup "off premises". That is one rule that I have always borne in mind, since I ran my first XT with Windows 3.0 and DR-DOS.

I also see your point and (you have read my mind) WRT categorizing data by level of rarity. I hope to scan old photos (of which I have no negatives), and in the case of such data (photos, school certificates), I would even do TRIPLE and physically separated backups of such data.

[FONT="Georgia"][COLOR="Indigo"]I really appreciate the feedback you all have offered.[/COLOR][/FONT] Since no mention was made of 'drivers" I guess thet would not be a concern for me.

THANK you very much!:)

---

### Post by Cracauer on 2010-04-06
You can get a firewire PCMCIA card. As I said in no event would I trust my data to USB.

---

### Post by eltonw on 2010-04-07
> **Cracauer said:**
> You can get a firewire PCMCIA card. As I said in no event would I trust my data to USB.

OK. And **next question**: HOWTO connect a PCMCIA card to an [COLOR="Sienna"]**[FONT="Arial Black"]Asus EEE 1000 PC[/FONT]**[/COLOR] netbook or to an **[COLOR="Sienna"][FONT="Arial Black"]Apple Macbook[/FONT][/COLOR]** 13" Dual?:confused: [U][I][COLOR="Red"][FONT="Verdana"]

Neither[/COLOR][/I][/U] portable *[COLOR="Red"]has **firewire[/COLOR]*** ports, *_[COLOR="Red"]nor **PCMCIA**[/COLOR]_* slots[/FONT].:confused:

---

### Post by Cracauer on 2010-04-08
> **eltonw said:**
> OK. And **next question**: HOWTO connect a PCMCIA card to an [COLOR="Sienna"]**[FONT="Arial Black"]Asus EEE 1000 PC[/FONT]**[/COLOR] netbook or to an **[COLOR="Sienna"][FONT="Arial Black"]Apple Macbook[/FONT][/COLOR]** 13" Dual?:confused: [U][I][COLOR="Red"][FONT="Verdana"]

Neither[/COLOR][/I][/U] portable *[COLOR="Red"]has **firewire[/COLOR]*** ports, *_[COLOR="Red"]nor **PCMCIA**[/COLOR]_* slots[/FONT].:confused:

You'll have to get something network attached then.

---

### Post by dyslexia on 2010-04-08
Absolutely nothing wrong with USB, although under Panther OSX does have a habit of eating USB-STORAGE drives.  (maybe they were trying to push firewire? it IS faster, but more expensive interface)

Anyways, cheapo ten dollar enclosures work great, and if you buy a 2.5" drive that's exactly the same size as your source drive, and record an image on it you have nothing to lose.  Much safer than buying a big "Colossus" and trying to save everythiing on that.

---

### Post by srs5694 on 2010-04-08
> **dyslexia said:**
> Anyways, cheapo ten dollar enclosures work great, and if you buy a 2.5" drive that's exactly the same size as your source drive, and record an image on it you have nothing to lose.  Much safer than buying a big "Colossus" and trying to save everythiing on that.

Two drives of "the same size" are seldom *exactly* the same size. If you've got, say, a 250GB drive and so go and buy a 250GB drive to use as a backup, you may find that the backup drive is actually a few MB smaller than the original drive. Depending on how you create the backup, this can result in the backup drive having any number of problems that can make it difficult to use when it comes time to recover data. OTOH, if the backup drive is slightly larger than the original, problems are much less likely.

I've seen several posts on this forum from people who've been burned by this issue. It's really not that big a deal if you're aware of it and if you know how to deal with it, but if you're not aware of the issues, it's likely to cause problems.

(To deal with the issue, you've got to do something other than a "raw" byte-for-byte backup. You could create a filesystem and use tar to do the backup, for instance; but doing something like a dd backup of the whole disk is likely to cause problems if the target is even a little bit smaller than the source.)

---

### Post by usndmac on 2010-04-08
I see no issues with USB, have never had any issue. Have had poor cable issues with firewire, but given good cables it's fine as well.

I recently ended up with a WD 1TB Book thingy. I whacked the crapware they put on for windoze and partitioned.

It works fine. It was free.

If I was actually paying for it, I'd get an external sata, one of those ones that the drive can be swapped. Then just buy sata drives as needed.

---

### Post by dyslexia on 2010-04-08
Lets see:  3 30 gig drives, two 80 gig drives, two 160 gigers, three 320 gig drives... different manufacturers, all of them standard sizes. (i.e. none "a few megs" bigger or smaller).   Not saying it couldn't happen, though. if the last partition is "defragged" shouldn't really matter anyways.

---

### Post by srs5694 on 2010-04-08
> **dyslexia said:**
> Lets see:  3 30 gig drives, two 80 gig drives, two 160 gigers, three 320 gig drives... different manufacturers, all of them standard sizes. (i.e. none "a few megs" bigger or smaller).   Not saying it couldn't happen, though. if the last partition is "defragged" shouldn't really matter anyways.

You've reported data with insufficient precision. Try typing "sudo fdisk -lu /dev/sda" on each of your drives (substituting the appropriate device filename, of course). Among other things, you'll see a line like this:

```

256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors

```

Pay attention to that last value, the total number of sectors. Unless they're the same model, the probability of two drives of the "same size" having exactly the same number of sectors is rather low, in my experience. Among systems I own, two different "80GB" disks have 160836480 and 160086528 sectors, for instance.

---

### Post by dyslexia on 2010-04-09
The drives I have with me, three 320 gig drives:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43119db3


Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95380471


Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd15ddbee


```

One is a Western Digital (sdc), One is Seagate (sdd) and I'm not sure what brand is in the laptop (sda).

I know it is possible to alter the drive geometry, I really don't know much about it or why someone would want to do that.

---

### Post by srs5694 on 2010-04-09
Congratulations, it appears that you've got disks from two or three different manufacturers with identical sizes. This is, however, not something you can count on, as my own figures show. Unless you check it, you're asking for trouble if you do a dd or other byte-for-byte copy from one disk to another with the same claimed size using GB or TB precision. There have been posts on this forum in the last couple of weeks from people who've been burned by making that mistake. I just want people to be aware of this risk rather than end up with a backup that doesn't work.

---

### Post by eltonw on 2010-04-10
> **usndmac said:**
> I see no issues with USB, have never had any issue. Have had poor cable issues with firewire, but given good cables it's fine as well.

I recently ended up with a WD 1TB Book thingy. I whacked the crapware they put on for windoze and partitioned.

It works fine. It was free.

If I was actually paying for it, I'd get an external sata, one of those ones that the drive can be swapped. Then just buy sata drives as needed.

Thank you.8-) I have not had problems with USB (so far), either. Since the two portables (Asus netbook, and Apple MacBook) are side by side, I won't need to have any abnormally long USB connection. My idea is just to swap out the USB external HD as needed. (Primarily it will be to backup the Mac, which has a larger drive).

---

### Post by yelvington on 2010-04-10
I'm powerfully tempted to go off on a rant about Apple's poor support for standards, but let's just say that you should buy a big USB drive but keep the receipts and return it if OSX doesn't immediately like it. 

If it does, wipe the drive clean of the Windows software that comes with it and partition the drive to your liking. Any OSX partitions should come BEFORE any Linux partitions, because stupid OSX may quit looking when it finds a Linux partition. (Did I say I was tempted to go off on a rant?)

Time Machine can back up your OSX system to an OSX partition. Any Linux solution, such as Deja Dup, will work with your Linux partitions.

And you should have no trouble plugging the device into non-Macintosh computers running Linux. I've done a lot of backups and migrations of Linux systems and never had a problem.

---

