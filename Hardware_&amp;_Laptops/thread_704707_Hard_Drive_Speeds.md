---
title: "Hard Drive Speeds"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by Syndacate on 2008-02-22
This isn't an Ubuntu question per-se, more like a hardware in general question - which is why I'm asking it here.

I'm hoping somebody could clear this up for me.

Right, so most SATA drives are 7200 RPM.  Mac has some weird obsession with 5400 RPM drives, and then there's the Raptor 9k RPM drives which a small group of tools seem to think is hot ****.

So, the way I see it, your processor will max out (most of the time) before you can reach the harddrive's maximum speed - but I could be wrong - either way, I'm not interested in speed, I'm interested in longevity.

My main problem with hard drives is their motor is going to die - and when it does, if you don't have an image of the drive backed up - you're boned.  This idea has always been a major puck up the *** for me.

So, which will live the longest?

I mean the 7200 RPM drives aren't spinning as fast as the 9000 RPM ones, but the 9000 RPM ones also probably have a motor that can take the beating?  So why does mac use 5400 RPM ones?  I mean if you ask me slower would be better in terms of longevity, less wear on and tear on anything - but the motors could be different, hence, it be the same, or is it still different?  Or are 9000 RPM drives lasting longer because they have a motor that can do 9000 RPM but don't usually hit 9000 RPM (so the motor's not working hard, often).

It goes hand in hand with engines in cars, I do believe, as I am a mechanic in most of my free time.  In town you'll get the same gas mileage with a 3.0 V6 than you would with a Honda 1.6L 4 banger simply because it has to do less work - but when pinned you'll obviously chew through more gas.  Then there's engines like the 1.3/2.0 twin rotor engines that Mazda uses in their RX lines that operate with minimal modifications at 10k or so, but use a lot of gas - but you have to changes the apex seals often or they crap out early.

So yeah, I realize it's a close game with car engines/longevity in terms of logistics, but I can't really put my finger on how it works with harddrives.

Can anybody lend a hand here?

---

### Post by Existentialist on 2008-02-22
As with many computer components, the long run killer of things is often the heat.  The faster the drive is spinning, the higher the heat output generally which is why laptops often use 5400rpm drives.  The number of physical platters used by the drives is the other important factor.  Usually, the more platters, the more heat.  To relate back to your motor metaphor, the less massive the vehicle, the less work the motor must do no matter what size the motor is.  Regardless of these facts, some drives tend to run hotter than others, probably just due to the quality of the motor and other components.  Here is a chart from tomshardware comparing drive surface temps of a good variety of drives:
[http://www23.tomshardware.com/storage.html?modelx=33&model1=117&model2=676&chart=39](http://www23.tomshardware.com/storage.html?modelx=33&model1=117&model2=676&chart=39)

Heat is not the only important factor, you also have the essentially random chance of your drive failing due to a number of other factors that you have no control over.  If data security is such an important factor, obviously backing up your data is one option, along with a RAID configuration involving mirroring.  Now days, most motherboards have built in RAID support, and you can easily maintain 2 copies of your data with insignificant performance loss.

One note on the bottleneck of the cpu on hd read rates.  Most hard drives range from 50-100MB/sec.  In fact, the actual bottleneck is the drive it self, the SATA interface which has a theoretical limit of 300MB/sec for SATAII has yet to even be close to utilized fully by drives.

I do want to touch on the hd rotation speed, since I am one of the tools who uses a 10K RPM drive.  The faster the drive's rotational speed, the less delay when the heads must seek data on other portions of the physical platter.  So on something like an OS drive, often during heavy use, such as booting, there are many small files spread around the disk that need to be read, and having a faster spinning drive results in these files being accessed more quickly.  This is why when looking at server drives you can find up to 15K drives.

To answer the question about which drives will live the longest, often it is going to be relatively random.  If you are willing to spend the money, new flash based SSD (solid state drives) will most likely be the most reliable in the long run as they have no moving parts.  They are also going to be the fastest at random access times (7200rpm ~ 13ms | 10000rpm ~ 8ms | SSD < 1ms).  If you are not willing to spend $500 for 32GB, then I know Western Digital makes some of there drives in RAID editions which are designed for 24/7 operation.  But to be honest I have no idea what, if any, difference there is with these then their other versions.  So just about any hard drive will tend to have similar reliabilities to other drives if you look at them as a whole, unfortunately sometimes you will get a bad drive.  If they don't fail almost immediately, they usually last for quiet a while.

---

### Post by Syndacate on 2008-02-23
> **Existentialist said:**
> As with many computer components, the long run killer of things is often the heat.  The faster the drive is spinning, the higher the heat output generally which is why laptops often use 5400rpm drives.  The number of physical platters used by the drives is the other important factor.  Usually, the more platters, the more heat.  To relate back to your motor metaphor, the less massive the vehicle, the less work the motor must do no matter what size the motor is.  Regardless of these facts, some drives tend to run hotter than others, probably just due to the quality of the motor and other components.  Here is a chart from tomshardware comparing drive surface temps of a good variety of drives:
[http://www23.tomshardware.com/storage.html?modelx=33&model1=117&model2=676&chart=39](http://www23.tomshardware.com/storage.html?modelx=33&model1=117&model2=676&chart=39)

Heat is not the only important factor, you also have the essentially random chance of your drive failing due to a number of other factors that you have no control over.  If data security is such an important factor, obviously backing up your data is one option, along with a RAID configuration involving mirroring.  Now days, most motherboards have built in RAID support, and you can easily maintain 2 copies of your data with insignificant performance loss.

One note on the bottleneck of the cpu on hd read rates.  Most hard drives range from 50-100MB/sec.  In fact, the actual bottleneck is the drive it self, the SATA interface which has a theoretical limit of 300MB/sec for SATAII has yet to even be close to utilized fully by drives.

I do want to touch on the hd rotation speed, since I am one of the tools who uses a 10K RPM drive.  The faster the drive's rotational speed, the less delay when the heads must seek data on other portions of the physical platter.  So on something like an OS drive, often during heavy use, such as booting, there are many small files spread around the disk that need to be read, and having a faster spinning drive results in these files being accessed more quickly.  This is why when looking at server drives you can find up to 15K drives.

To answer the question about which drives will live the longest, often it is going to be relatively random.  If you are willing to spend the money, new flash based SSD (solid state drives) will most likely be the most reliable in the long run as they have no moving parts.  They are also going to be the fastest at random access times (7200rpm ~ 13ms | 10000rpm ~ 8ms | SSD < 1ms).  If you are not willing to spend $500 for 32GB, then I know Western Digital makes some of there drives in RAID editions which are designed for 24/7 operation.  But to be honest I have no idea what, if any, difference there is with these then their other versions.  So just about any hard drive will tend to have similar reliabilities to other drives if you look at them as a whole, unfortunately sometimes you will get a bad drive.  If they don't fail almost immediately, they usually last for quiet a while.

Yeah, obviously, like with most people, money is a problem for me.  I have my 750gb external - there's a reason I specifically bought from buffalo (opposed to mybook) or something and that's b/c buffalo splits things into 2 drives, so the enclosure is a 750, but it's real dual 375's - which is a pain in the *** to read on Ubuntu, but I like that just from knowing if one craps out, I don't lose everything.  Though most of the stuff on there is media type things so it's not like it's irreplaceable if it does.  Obviously if I had more money I'd mirror my externals.  As far as my current internal drive goes, I have a SATA 200GB partitioned 120gb windows (I never intended to use Ubuntu 24/7 as I do now), and since my mobo is so old it can only read 127 max per partition, so I used the remaining 60GB to make my Ubuntu partition - which I use about 20 at a given time as i back up most of my media (excluding pictures and music) on my external.

With all of that said, when I grow a pair of balls I intend to hit up nortan partition magic and extend the partition from the windows side - try to give Ubuntu ~60more gb so I'm not so pressed - and cancatinate that 60 from the windows side onto my current linux partition so I wind up with more linear space.

That's later.  In the meanwhile, I need to find a way to back up my hard drive (a hard disk image) - but just of my Ubuntu partition.

I know Vista has a nice feature where you can auto create a hard disk image once a week.  This drive being older than life I'm sure it's nearing its time, and unlike most people, I really get raped/killed on reformats.  I need to find out how to back up my Ubuntu partition as a hard drive image - I'd do that once a week or so so I feel safe even if this craps out - as there's nothing important on the remaining windows part.  Though I'd like to do that before I try to extend my linux partition so I don't roast something on accident while trying to change the partitions - or if I do, I at least have my image so nothing is lost.

My friend was telling me about Norton Ghost - which does pretty much what I want it to do - guess I'm looking for the Linux version of that :-X.

Though this is sorta not completely related to my topic.

I simply don't care as much about hard disk speeds as I'm not running a server and I can wait the extra time on installs and the like as much as I care about longevity of the drive - as like I said, I get killed on reformats, it's not something I can do easily, like other people can do it at the drop of a hat.  I spend too much time getting all my stuff together than to just fry it b/c the luck of the draw.

So theoretically, based on what you've told me, a 7200 RPM drive that is very reputable (or made by a reputable manufacturer) would be ideal as the components are good and it would create the least heat?

---

### Post by kbless7 on 2008-02-24
I personally don't use any hard drives under 7200. They actually make 15K hard drives which is absolutely insane. They transfer faster than solid states.

---

### Post by Syndacate on 2008-02-24
Yeah, that wasn't quite what I was asking.

Actually I said in there how I cared less about speed, if anything.

---

### Post by Existentialist on 2008-02-24
Linux has a command, dd, which will allow you to clone a hard drive, partition, or any other course of data relatively easily.  This is something that you want to read up on and make sure you switch things like the source and destination of the backup, as it will overwrite data and partitions.  Here is a something to read to get you started and familiar with dd:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)

As for the hard drives, 7200rpm is going to be the most common, and you will most likely have to go out of your way to find a good 5400rpm drive.  I have always used Western Digital, and have yet to have one crash, although one was DOA.  You say you have an older motherboard, can we assume this means you will be using an IDE drive?  And what size hard drive are you looking for approximately?

---

### Post by Syndacate on 2008-02-25
Actually it does have IDE, but it also has SATA, when I put this together SATA like, JUST came out, so it has 2 of each.

I have a 200GB SATA in there.  I'm not looking to buy another hard drive, I'm just trying to bring closure to this debate me 'n some friends have been having about which will last the longest - as you can see I'm pretty anal about my drive's lasting, I'm pretty scared that they're just gonna take a crap and I'm gonna lose all my stuff, so :-X.

I'll read up on the dd command.

---

### Post by Existentialist on 2008-02-25
If you want something interesting to read about hard drive failure, this study was done by Google.  In it, the authors attempt to find correlations between certain factors and hard drives failure rate.

[http://labs.google.com/papers/disk_failures.pdf](http://labs.google.com/papers/disk_failures.pdf)

---

### Post by Syndacate on 2008-02-25
So lemme make sure I'm understanding this right:

If I type:
```

dd if=/ of=/media/sda1/backup

```

Should back up my entire linux partition?

I have about 80GB on sda1 that's free, my partition for linux (root) is 60 total, but is about 23 used, so the backup it creates on sda1, is that going to be 60GB, or 23GB?

Can you confirm that the code is right?  Obviously I'm a little touchy about doing this as you can see from my previous hard drive comments ;).

---

### Post by Existentialist on 2008-02-25
Check out this site about linux backups, it has some scripts and ideas for how to properly backup your data.

[http://www.linux-backup.net/](http://www.linux-backup.net/)

I think it may be down right now, its really slow for me.  I have never actually done a backup with dd, but I believe you are missing something at the end.  According to the site I linked to:
Copying / on /dev/hda1 to a /dev/hdb1 ( backup disk ):

dd if=/dev/hda1 of=/dev/hdb1 bs=1024k

I would like to be of more help to you, but with something as easy to mess up as this (and your obvious concern with loosing data); I would prefer help you find the recourses to learn how to, or leave it to others on these forums that know more about doing this then I do.

---

### Post by Syndacate on 2008-02-25
> **Existentialist said:**
> Check out this site about linux backups, it has some scripts and ideas for how to properly backup your data.

[http://www.linux-backup.net/](http://www.linux-backup.net/)

I think it may be down right now, its really slow for me.  I have never actually done a backup with dd, but I believe you are missing something at the end.  According to the site I linked to:
Copying / on /dev/hda1 to a /dev/hdb1 ( backup disk ):

dd if=/dev/hda1 of=/dev/hdb1 bs=1024k

I would like to be of more help to you, but with something as easy to mess up as this (and your obvious concern with loosing data); I would prefer help you find the recourses to learn how to, or leave it to others on these forums that know more about doing this then I do.

Alright, I'll look around for it, the reason I didn't put a bitsize at the end of it was it said that would do no truncation, iono, I'll look around, anybody else feel free to chime in.

---

### Post by Daelyn on 2008-02-25
> **Syndacate said:**
> So lemme make sure I'm understanding this right:

If I type:
```

dd if=/ of=/media/sda1/backup

```

Should back up my entire linux partition?

I have about 80GB on sda1 that's free, my partition for linux (root) is 60 total, but is about 23 used, so the backup it creates on sda1, is that going to be 60GB, or 23GB?

Can you confirm that the code is right?  Obviously I'm a little touchy about doing this as you can see from my previous hard drive comments ;).

Don't run that command mate. It will most likley bug out.

Your ```
if=/
``` will copy the whole /media directory too. So, copy onto itself while it copies. will not be a good idea.

Copying device to device is on the other hand the right way to go.
I suggest you boot into a Live CD while doing the copying so you keep mounts (external media etc) won't cause issues for you.

so. basically
```
 dd if=/dev/<device1> of=/dev/<device2> conv=notrunc,noerror 
```
will copy the entire contents of device 1 to device 2.

Have a look through the manual of DD, so there isn't some switch I've forgotten about. Still a newbie :)

---

### Post by Syndacate on 2008-02-25
Well I don't want the whole hard drive, just the "Filesystem" - the root that Ubuntu is installed on, a 70GB partition on my 200GB HD.

I don't think you can just type **if=Filesystem**.

It seems there's a lot of programs that can do this, too, I'm not sure which path I'm going to take yet, I have to do some more research on programs such as arcnois (sp?), clonzilla, that other one that started with a P, vs, dd.

:-X

PS:
I read the time to save via dd is very long, compared to some other programs out there, I'll be saving to an external USB.

---

### Post by Acapulco on 2008-02-26
> **Syndacate said:**
> This isn't an Ubuntu question per-se, more like a hardware in general question - which is why I'm asking it here.

I'm hoping somebody could clear this up for me.

Right, so most SATA drives are 7200 RPM.  Mac has some weird obsession with 5400 RPM drives, and then there's the Raptor 9k RPM drives which a small group of tools seem to think is hot ****.

So, the way I see it, your processor will max out (most of the time) before you can reach the harddrive's maximum speed - but I could be wrong - either way, I'm not interested in speed, I'm interested in longevity.

My main problem with hard drives is their motor is going to die - and when it does, if you don't have an image of the drive backed up - you're boned.  This idea has always been a major puck up the *** for me.

So, which will live the longest?

I mean the 7200 RPM drives aren't spinning as fast as the 9000 RPM ones, but the 9000 RPM ones also probably have a motor that can take the beating?  So why does mac use 5400 RPM ones?  I mean if you ask me slower would be better in terms of longevity, less wear on and tear on anything - but the motors could be different, hence, it be the same, or is it still different?  Or are 9000 RPM drives lasting longer because they have a motor that can do 9000 RPM but don't usually hit 9000 RPM (so the motor's not working hard, often).

It goes hand in hand with engines in cars, I do believe, as I am a mechanic in most of my free time.  In town you'll get the same gas mileage with a 3.0 V6 than you would with a Honda 1.6L 4 banger simply because it has to do less work - but when pinned you'll obviously chew through more gas.  Then there's engines like the 1.3/2.0 twin rotor engines that Mazda uses in their RX lines that operate with minimal modifications at 10k or so, but use a lot of gas - but you have to changes the apex seals often or they crap out early.

So yeah, I realize it's a close game with car engines/longevity in terms of logistics, but I can't really put my finger on how it works with harddrives.

Can anybody lend a hand here?

Take a look at:

[http://en.wikipedia.org/wiki/Mean_time_between_failures]("http://en.wikipedia.org/wiki/Mean_time_between_failures")
 
The MTBF (Mean Time Between Failures) is how some people measure the "reliability" of a component in terms of how much time is it expected to last before a failure. So, even when that might not be accurate in terms of your particular drive, it can shed some light on which brands/products have a longer *average* time before failing. 

As fas as I know, components with bigger MTBF numbers, the more time you can expect it to last, but again, it's an average.

I hope that helped.

---

### Post by Syndacate on 2008-02-28
> **Acapulco said:**
> Take a look at:

[http://en.wikipedia.org/wiki/Mean_time_between_failures]("http://en.wikipedia.org/wiki/Mean_time_between_failures")
 
The MTBF (Mean Time Between Failures) is how some people measure the "reliability" of a component in terms of how much time is it expected to last before a failure. So, even when that might not be accurate in terms of your particular drive, it can shed some light on which brands/products have a longer *average* time before failing. 

As fas as I know, components with bigger MTBF numbers, the more time you can expect it to last, but again, it's an average.

I hope that helped.

Yeah, I understand that, thank you.

The thing is like Microsoft recommends a reformat every 6 months, I cannot afford that - at all.  I have too much data and can't afford to lose it all.  Therefore, I need to be able to ghost my hard drive, much like Norton Ghost can do for Windows.  In this case, I want to ghost my filesystem, or "** -r /**" --- I need to be able to back it all up so that if my hard drive takes a crap I can't lose the info I have on there - thats' why I'm looking for a method of backup.  Though a backup isn't really tested hardcore until the **** actually hits the fan - so in the meanwhile (the meanwhile before the drive craps out and I need to use the latest backup), I was just looking for the drive that has the longest durability so I don't have to worry (as much) about this.  Though obviously there's freak hard drives and such which tips averages and the like, but averages are still good.  Again, thank you.

---

