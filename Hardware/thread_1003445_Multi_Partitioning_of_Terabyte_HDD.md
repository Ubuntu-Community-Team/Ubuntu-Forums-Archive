---
title: "Multi Partitioning of Terabyte HDD"
date: 2008-12-06
forum: Hardware
---

### Post by theDaveTheRave on 2008-12-06
Dear all,

I have a question regarding HDD setup on a server I am setting up.

Originally I asked this question in this thread 

[http://ubuntuforums.org/showthread.php?t=283131&page=2]("http://ubuntuforums.org/showthread.php?t=283131&page=2")

frequented by the totaly gurubuntu-tastic Bodhi Zazen (who should receive credit for all the help he has given regaring fstab in the past.... and will again in the future no doubt ;).

This is a copy of my post there, slightly edited for brevity / clarity etc....

A bit of History, and my situation....

I don't know if this makes sense or not,

I know my boss won't be keen on the idea of using another filing system on a selection of 1TB HDD, as such they have an NTFS rather than native Linux filesystem installed, my preference would have been for either EXT3 or Reiser (I think??), but they are staying as NTFS so as they can be easily swapped over to another windows pc ](*,) , should disaster strike and the Ubuntu server die (year right as if:lol:)

Check out our web page to see some of the stuff we are doing

[-http://nuclear.movement.googlepages.com]("http://nuclear.movement.googlepages.com")

and here are some sample movies

[-http://nuclear.movement.googlepages.com/research2]("http://nuclear.movement.googlepages.com/research2")

Anyway... my question is this.

When my colleagues are creating their data sets they start with about 60GB of video data, after analysis and stuff they normaly have it trimmed to about 20 or 30.


What I was thinking, is when they "finalise" their movies they could potentially store them on a "separate" partition of the drive.

Do logical partitions of drive space exist in a "physical" manner (ie when I split a drive into a partition is partition1 physically all together and partition2 physcialy after it??

if so could I do the following.

Have one of my TB disks read only, so as I can do the following:

Determine the size of a set of films for one experiment, then create a partition at the "front" of that disk of exactly the desired size to hold just that set of films. copy the films into this new partition (and potentially mount it as a separate read only sub folder).

When they have the next set of films ready do the same procedure, resizing the remaining larger portion of the disk to hold just the films from the next experiment?

and keep doing this, meaning that each experiment will exist on a separate partition that is READ ONLY and as it of a fixed size on the disk can't become "fragmented".

Are there any dangers to doing this? such as the continual repartitioning of the remaining space etc, will it corrupt the data in the partition at the front??

Another question,

Would doing this make access the "films" faster for my colleagues??

Would I then have an easier time of creating "archives" and backup procedures for the data??

Thanks in advance for your asstance.

David

---

### Post by kidders on 2008-12-07
Hi there,

I'm not sure I like the idea of continually repartitioning a disk. Every time you do it, there'd be a slight risk of screwing up the entire disk, so repeating the procedure over and over seems unwise.

It seems like fragmentation is a legitimate concern though ... the filesystem that contains the 60GB working copies of your movies will probably get pretty messy quite quickly, assuming your colleagues would do all their work there.

What would you think of something like this? ...

[LIST]
[*]You could split the available disk space in three once, and leave it that way. Two of the partitions would be scratch filesystems, and one for finalised videos.
[*]Whenever one of the scratch filesystems gets too full, or becomes very badly fragmented, you could overwrite it with a fresh, new one (ie run "mkfs"). In the meantime, your colleagues could continue working on the second one.
[*]Once the videos are done, they could be moved to the third filesystem, and left there until there's no longer enough space to keep them all.
[*]If speed is a priority, I don't think ReiserFS is a suitable filesystem choice. It performs very well on filesystems full of small files (<4k), and can reduce internal fragmentation of larger files (with a significant performance penalty), but I don't think it's the right choice for multimedia.
[*]Ext3 is a better option, but for no reason other than its customisability. Ext2 would be much faster, but is unjournalised ... not that filesystem journals are of much benefit with large files anyway.
[*]Personally, I would consider JFS. Any thoughts?
[/LIST]

> **theDaveTheRave said:**
> Do logical partitions of drive space exist in a "physical" manner (ie when I split a drive into a partition is partition1 physically all together and partition2 physcialy after it??I'm not 100% sure what you're asking here. Logical partitions (like primary ones) do physically exist as separately administered bodies of data, but they do not necessarily sit one after the other on your disk. Storing data that way would focus wear & tear on particular parts of the physical device, rather than spreading it over the entire disk.

> **theDaveTheRave said:**
> Are there any dangers to doing this?Not if it works perfectly every time. The only risk comes from (a) making a mistake while operating as root, and (b) failure of the repartitioning process ... both of which inevitably happen from time to time.

> **theDaveTheRave said:**
> Would doing this make access the "films" faster for my colleagues??Not necessarily. Assuming there's a network involved, there are other issues to consider, including ...[LIST]
[*]The efficiency of the file sharing protocol you choose (eg NFS, Samba, AFP, etc).
[*]The probability of serving files stored on lots of different filesystems (ie rather than just one), to many people at the same time.
[*]The performance of your network.
[*]How CPU-intensive the filesystems you choose are.
[/LIST]

Regarding backups, I would seriously consider doing two things ...
[LIST]
[*]Using RAID. A terabyte of data is an awful lot to lose because of a single disk failure. Implemented properly, using RAID can also boost the performance of a filesystem. It would also mean that a failure wouldn't result in your colleagues being unable to do any work while 100s of gigabytes of data was restored from backups.
[*]Taking nightly backups of work in progress (eg one of the scratch partitions I suggested), and perhaps weekly backups of finalised movies. This would protect you from "Oops... did I just hit 'Save' or 'Save as' ?!"
[/LIST]

Does any of that help?

---

### Post by theDaveTheRave on 2008-12-08
Kidders,

Thanks for the response, its stuff for me to think about and inform the team of.

On RAID devices:

Originally the 4TB disks were going to be a RAID device, and set asside specifically for backup. However in the 8 months that they have had the system (I've only just arrived there and been given the tast of setup), they have generated A LOT more data (ie movies), and they have realised that they need the 4TB's of space to hold it all.

Bakcups are also something that I have been asked to look into.

My main personal concern is that the files will become horribly fragmented when opening and saving them all the time (especially as they inbed them into presentations and stuff).

The main concern of my boss is that if we have a server failure then we will loose access to the data if it is in a non NTFS format (which seems fair enough in a way).

You say about the danger of permanently repartitioning, but I'm not sure I have made myself very clear on my idea.

for arguments sake lets pretend that the disk has 10 blocks.

I'm ready to allocate 2 blocks to hold some data, and I will only allocate those first 2, the remaining 8 will be "unalocated", at a later date I will then take the next 2 parts of the "unalocated" space and allocate them as a "new part"

the result would now be 3 partitions, 

partition A holding the original 2 blocks
partition B holding the new 2 blocks (ie blocks 3 and 4)

the remaining bit (blocks 5,6,7 8,9 and 10) as unalocated space... untill I do the same procedure again.

I this way I am not permanently "repartitioning" the space but allocating it fresh each time.

Does this sound like a reasonable solution or do you think that there are still considerable dangers involved?

Thanks for you time, and input.

David

---

### Post by kidders on 2008-12-08
Hey again,

> **theDaveTheRave said:**
> You say about the danger of permanently repartitioning, but I'm not sure I have made myself very clear on my idea.Don't worry ... I understood what you were describing. Think of it this way ...

If you open a large text document, add a single word to the end of it and hit "Save", you're not really appending something onto end ... you're overwriting the whole thing with an entirely new version. The same idea applies to modifying partition tables. Any change is equally risky, no matter what the specifics of the change happen to be.

Imo, it's not safe to modify a partition table containing filesystems you can't afford to lose.

> **theDaveTheRave said:**
> My main personal concern is that the files will become horribly fragmented when opening and saving them all the timeI can imagine! That was the rationale behind my "two scratch filesystems" suggestion. If I were you, I would opt for as fast a pair of filesystems as I could, and reformat them whenever fragmentation gets out of hand (eg once every 2 months or so).

> **theDaveTheRave said:**
> The main concern of my boss is that if we have a server failure then we will loose access to the data if it is in a non NTFS format (which seems fair enough in a way).I agree. It's not wise to run a mission-critical service with no redundancy. Disk failure (which is far more likely, in theory) is also a concern though.

---

### Post by theDaveTheRave on 2008-12-09
Kidders

Great info, thanks.

I've never actually experienced a HDD failure! the most infuriating failure for me was when I lost the power source, In the end I needed to get a new internal box for connecting the power too! You can imagine it took quite a while for me to realise that was the problem... in fact thinking back on it I don't know why I decided that was the cause, but I splashed out for a new one and everything has been fine ever since... and the box is now about 15 years old - it contains 2 HDD that I have had since around that time and more from updgrades - admitedly it is getting tight on "physical" space, but never any HDD failures!

Your idea of 2 scratch filing systems does appeal to me, it just seems a little complex to set up (not a problem just requires a little thought and effort). Then I need to make it seemless to the rest of the team - I can't have my boss (or anyone else) thinking that it doesn't seem like a sensible setup.

I guess that documentation is the key thing there however.

---

