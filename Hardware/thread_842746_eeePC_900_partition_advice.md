---
title: "eeePC 900 partition advice"
date: 2008-06-27
forum: Hardware
---

### Post by kurainisei on 2008-06-27
Hi there. I would like to install a fresh Ubuntu on My eeePc 900. Thing is, using the standard partition, I have just 500MB on my first disk (the 4 GB fast SSD).
Do you think it will make sense if I make a partition on my 16GB SSD where I put /usr?
Or the 16GB SSD is just too slow and I might encounter performance problems?

I'm a bit of a newbie here, so, if you can help me on this, it would be appreciated :)

---

### Post by kurainisei on 2008-06-27
er... bump.. noone can help me?

---

### Post by housam on 2008-06-27
Ubuntu needs at least 4GB of space to be installed. with your specs , I think you should install it at your 16 GB HDD.

---

### Post by kurainisei on 2008-06-27
> **housam said:**
> Ubuntu needs at least 4GB of space to be installed. with your specs , I think you should install it at your 16 GB HDD.

Mmmm... my installation is about 3GB. My question was: since the 16GB SSD is pretty slow, should I be concerned in installing the /usr (which, I understand, uses a lot of space) in that SSD?

---

### Post by housam on 2008-06-27
you need only 2 partitions to install ubuntu . one for the root (/) ext3 format and the other for the swap . no need for any other partitions . there will be a /usr folder  inside the root partition.

---

### Post by ronacc on 2008-06-27
> **kurainisei said:**
> Mmmm... my installation is about 3GB. My question was: since the 16GB SSD is pretty slow, should I be concerned in installing the /usr (which, I understand, uses a lot of space) in that SSD?

I have the whole of hardy installed on an 8gb sd card (a fast one) and it is quite acceptable , dosen't boot as fast as xandros from the ssd but up and running is snappy enough given the slow 32bit cpu.

---

### Post by kurainisei on 2008-06-28
> **ronacc said:**
> I have the whole of hardy installed on an 8gb sd card (a fast one) and it is quite acceptable , dosen't boot as fast as xandros from the ssd but up and running is snappy enough given the slow 32bit cpu.

That's interesting. Are there any difficulties in making Ubuntu run on an SD Card? When I first installed Ubuntu, I noticed that there were some problems in mounting the SD card, Which I solved with a couple lines of code.
Which SD card did you use?

@housam: I know I need just two partitions. I wanted to move /usr away because the 4GB SSD is too small (I've about 500MB left now) and the 14GB SSD is a bit slow to move there the whole system. I'm asking if this is a clever solution, or if I should find another one. Thanks!

---

### Post by kurainisei on 2008-06-29
Other ideas?

---

### Post by dominiquec on 2008-06-29
Generally, I like to keep the /home partition separate.  For the / partition, everything fits nicely in under 5GB (but 7GB should be safe).  Should be no problem with putting /usr in another partition, though.

---

### Post by kurainisei on 2008-06-29
Can I choose to install the applications to another location? I believe that, going on like that, I will run out of space where installing new stuff.

---

### Post by geekygirl on 2008-06-29
Having the exact same discussion with myself here right now about partitioning for the eee 900!

This is what I came up with:

4G SSD: /  (used ext2), no swap
8G SSD: nothing as yet but should I need it I can use this for /var and /usr and just symbolic link them
16G SDHC: /home (ext2)

No swap as I am using 2G of memory.

You could also:

4G SSD:  / (ext2)
8G SSD: /home (ext2) less room but thats what external and portable HDD's are for!
16G SDHC: /usr (ext2, 5G) and /var (ext2, 5G), /tmp (ext2, 50mb) and the rest as swap

I think the latter is just overkill though!

---

### Post by kurainisei on 2008-06-29
How do you symbolic link /usr and /var to the 8GB SSD (which is an external SD card, am I right?)
Thanks, I'm a bit of a newbie.

---

### Post by dominiquec on 2008-06-29
I believe it's:

sudo ln -s source_directory new_directory

---

### Post by starcannon on 2008-06-29
> **housam said:**
> you need only 2 partitions to install ubuntu . one for the root (/) ext3 format and the other for the swap . no need for any other partitions . there will be a /usr folder  inside the root partition.

While technically true, it is of great wisdom to put /home on its own partition; doing so greatly increases ones long term sanity.

As to the OP's original question, if your install is only taking up 3gb, then perhaps just give it the entire 4gb fast ssd, and put /home on the 16gb ssd. It's actually very similar to how I have my Asus Eee 4g setup. I put / on the internal 4gb ssd, and then I put home on a 16gb sdhc card; this works excellent, though on that particular eee I do need to get around to custom compiling a kernel so that suspend/resume from sdhc works correctly.

---

### Post by geekygirl on 2008-06-29
> **kurainisei said:**
> How do you symbolic link /usr and /var to the 8GB SSD (which is an external SD card, am I right?)
Thanks, I'm a bit of a newbie.

Possibly something like this:

```
sudo ln -s /usr/ /*SDHC card details here*/usr

```

I haven't had to try it yet but I think something like that should work - need one of the gurus in here to check and make sure I am also on the right path lol ;)

---

### Post by kurainisei on 2008-06-30
> **starcannon said:**
> While technically true, it is of great wisdom to put /home on its own partition; doing so greatly increases ones long term sanity.

As to the OP's original question, if your install is only taking up 3gb, then perhaps just give it the entire 4gb fast ssd, and put /home on the 16gb ssd. It's actually very similar to how I have my Asus Eee 4g setup. I put / on the internal 4gb ssd, and then I put home on a 16gb sdhc card; this works excellent, though on that particular eee I do need to get around to custom compiling a kernel so that suspend/resume from sdhc works correctly.

Thing is, the 4GB fast SSD is just too small: as for now, the installations takes almost all the space (just 500 MB are left) and I'm a bit worried about the updates and the install of new applications.

So I need to understand which is the best way to go, in order to count on more space. External SD card seems a good solution, but I'm open to other advices :)

---

### Post by starcannon on 2008-06-30
> **kurainisei said:**
> Thing is, the 4GB fast SSD is just too small: as for now, the installations takes almost all the space (just 500 MB are left) and I'm a bit worried about the updates and the install of new applications.

So I need to understand which is the best way to go, in order to count on more space. External SD card seems a good solution, but I'm open to other advices :)

I thought the Eee 900 has 20gb of total internal ssd space? If so then I'd put the 4g ssd to / and perhaps another 4gb to /usr on the bigger one, and the rest to /home.

Just my 2 cents.

If its an Asus Eee 4g 701, then you could do the same thing with a 16gb sdhc card. I didn't I just put / on the 4gb ssd, and put /home on the 16gb sdhc and have had no issues with it, 4gb is tight, but its not my main computer, indeed the things that take up the most space are my mp3's if not for those I could have easily gotten away with a 2gb sdhc card.

---

### Post by DagMan on 2008-07-13
I put the 4gigs to /usr and 2gigs to /
/ uses 185 megs after all the extra apps I've installed though a larger 2 gig partition is still the way to go for me in case I end up putting lots of things in /opt

the 4 gig /usr partition is almost 70% full right now.  
the bulk of the /usr partition is in /usr/lib and /usr/share
and that's actually how I'de partitioned ubuntu in the past.

It's my recomendation, to put the 4 gig partition on /usr/share put 4 gigs on /usr/lib and / can be small though it still needs extra room just in case.  The installer will give a warning if it's too small.  at 2 gigs I didn't get a warning.

I also usually put 2 gigs at /var because the downloaded .deb files live in a subfolder there, and it's to reduce fragmentation, though I'd heard that fragmentation isn't worry since there isn't a hard drive that has to physically move something to seek on the drive.

Apologies if some of that is already discussed, I happened to click here while googling for something else and only read the last couple posts.

---

### Post by sjkfl on 2008-09-07
I'm a Linux newbie, so please forgive me.

I downloaded [Ubuntu Eee 8.04]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Eee-38681.shtml") but have one question that has me stuck.  

The 4 GB SSD (/dev/sda) has 4 partitions:
[LIST=0]
[*]2.4 GB Linux
[*]1.5 GB Linux
[*]8 MB FAT32
[*]8 MB EFI
[/LIST]
The 16 GB flash drive (/dev/sdb) has only one Linux partition.
 
Looking in File Manager, / (root?) is installed on /dev/sda1 (1.5 GB) and /Home is installed on /dev/sdb0 (16 GB), but then what is the 2.4 GB partition for?

I read at [http://wiki.eeeuser.com/eee_pc_701](http://wiki.eeeuser.com/eee_pc_701) that the first two partitions are joined with UNIONFS.  I don't know what that means, but don't know how to do that when installing Ubuntu.  Should I delete those two partitions and make that the / (root) partition?

If applications are installed, by default, to /opt, I'm thinking I'd have more applications installed than personal documents, so would it be an idea to split the 16 GB sdb into two partitions?  One for /opt and one for /home?

Thank you for your help.

Steve

---

