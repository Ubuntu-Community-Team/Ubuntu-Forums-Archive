---
title: "MYBOOK 500GB switch to XP"
date: 2008-11-19
forum: General Help
---

### Post by eaks on 2008-11-19
Hey guys.. heres the issue here.. I was oringally only using XP pro.. then decided i would try a dual boot with ubuntu so i installed it.. and tried to acess my 500gb WD MYBOOK.. it was seen by linux but not allowing me to access any files in it.. So i search around and find that i need to mount it.. I try to mount by just right clicking and going to mount device.. this doesn't work.. So I do some more research and find some terminal commands to get it working.. i Do these commands and it works.. then i go back to XP pro and now i cant access the drive.. I plug it in and it shows up as E:.. but when i open it i get an error saying that the drive is not accessible and that the information is currupt or unreadable.. The weird thing is that in the device manager of XP it shows up as 500gb MYBOOK but not under my computer.. i also checked with some partioning tools i have and its still the windows filesystem and should work..

I have tried to unmount in linux by using the right click unmount but this never unmounts it correctly (i can still use the mybook in linux.. and when booting to XP i still cant use it)

So anyone have anything for me to try?

PS: my original hdd with linux and xp pro dual booting has an issue in the XP boot sectors so i cannot boot it up or run any live cds or repair console and in grub i told it to hide all the partions so grub gives me an error 22.. I need the info off of the mybook to bring some files over that i had saved from my old XP drive so im hopping this is possible through the ubuntu live cd!!

Thanks

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
little confused about all the problems your having. 

but you should be able to boot the live cd and mount the external then get the data off to cds or dvds?

i image that the file system is slightly corrupt so we can try to use fsck to repair the file system
i have never had to do this my self and do not personally know the reliability of this working, so I would back everything up first.
```
 fsck.vfat -a "path to device" 
```
were the path to device is something like can be found by typeing 
```
 sudo fdisk -l 
```

now the error 22 thing

---

### Post by eaks on 2008-11-19
hey man.. im really confused about what you just wrote.. Do i use the fsck.vfat -a "path.." command to unmount my external hdd? or is that to fix the filesystem in my bad hdd?

And what should i look for after the sudo fdisk -1 command? im pretty sure ive tried that command before and it didn't work through the live cd but i may be mistaken!

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
ok so you have the liveCD booted up
can you
post the out put from the sudo fdisk -l  here

its and lower case L not 1

it just list the way all the partitions are set up

ya I see how i was confusing
because windows cant read it. it maybe corrupted just a little bit so we should try to repair the file system and the 
fsck.vfat -a "path" should be able to do that

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
But we maybe going about this all the wrong way. 
if you just wanna get the files off of it then why dont you just mount it under the livecd and copy them off

or we could try to fix grub first

don't know what do you wanna try

---

### Post by eaks on 2008-11-19
well i dont really care about grub/linux.. i found i wasn't using it much.. and when i was everything i was doing i could have done threw xp.. 

What i want to do is get my MYBOOK unmounted so i can use it with XP and then i also wanna try to repair my hdd threw linux (but repair my xp partiton.. and then i dont care if i have linux or not)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
ya just looked at your other post
thinking

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
when you power down you computer it should automatically unmount the hard drive, unless there is a problem.
also even if you suddenly lost power and linux didn't have time to unmount the partition xp should be-able to read it.
So if xp can't read it its not because it's mounted, it's because it's corrupted.
Thats why i want to use fsck to fix it.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
did you get all of your partitions unhidden
i have never used that feature of grub before

---

### Post by eaks on 2008-11-19
nope all partitions are still hidden.. also.. I am faily certian that my MYBOOK is working 100% it never really bothered me but always happend.. i would just copy the files over in linux and boot to xp.. but now that i cant do this i just wnana get my drive to be able to be used in xp.. the drive works fine in linux though.. read/write/whatever.. but it isn't able to be opened in XP nor was it ever able to be opened in XP AFTER I MOUNTED in linux!!

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
eeerrr time for more thinking

and you said you cant get the xp install cd to boot

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
ok so it may not be the best solution to all the problems your haveing 
but it seems like you could just reinstall ubuntu
this would reinstall grub and remove it's configuration.
then you can boot ubuntu and or xp agin

just need to check and see how grub hides the partions
and make sure that doing this will reset everything

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
As a side note i have a mybook 500gb and it can be read from both xp and ubuntu so its confusing that your wouldn't and still be 100% ok

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
hideing a partion is only reliveant to dos/ windows file systems 
so the grub error 22 is not from that 
it sounds more like you happen to have a hard drive failure at about the same time you were messing around with your system.

if i were you i would try to get all files that are important to you off that disk before you try to do anything farther then i would attempt to reinstall xp

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-19
so i have to go to work be back on in latter

---

### Post by eaks on 2008-11-19
thanks for all the help so far.. but i have concluded that the boot sectors on the drive are no good.. i am going to try and reinstall ubuntu on that drive later tonight or tomorrow and see if ubuntu works threw that.. if it does im hopping i will be able to mount my drive (windows xp partition) and grab some files and throw them on my MYBOOK.. then hopefully somehow have my mybood working in windows!

ALSO: I think you may be mistaking a few things i am saying.. 
I am having tonz of issues at the present time.. my internal hdd was messing up (causing the boot errors in windows/grub and all that) im currently working on that as well..

The MYBOOK is only used as an external drive.. had no issues with it in xp till i mounted it in linux!

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-21
right so how are things going

---

### Post by hambone79 on 2008-11-23
I know this doesn't really help, but I had some really flaky behavior out of my WD Mybook 500GB right before it crapped out. It would work in one OS but not another, then one day it just wouldn't work at all. If I were you, I would give the Western Digital diagnostic program a try and see if it can detect any problems.

---

