---
title: "removing file system mount points"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Post Monkeh on 2009-07-19
dunno if that title explained things very well.

when i first installed ubuntu, i stupidly fiddled about with my partitions and mount points. i  mounted my main file system, but also chose seperate mount points for my usr, home, and opt folders.

my home folder is fine (75gb), but my opt (9.3gb of which only 300mb have been used in 6 months) and usr (10gb of which 6 gb have been used) aren't really proportioned correctly.  rather than resizing them, is there any way to change my settings from a live cd and just copy the folders back onto my main file system and merge the partitions?

---

### Post by louieb on 2009-07-19
> just copy the folders back onto my main file system and merge the partitions?     Maybe easy, maybe not easy, but certainly doable. 

Take /opt for example. say its on sda2  and / (root) is on sda1 
Boot from a live CD.  

and copy the content of sda2 to the /opt folder on sda1. When your done edit /etc/fstab and remove (or comment out) the /opt mount point for sda2.  (might want to make a backup of the file 1st - just in case  something went wrong). 

Boot the hard drive install it should work the same as before. If so your ready to merge. 

Boot the live CD and used Gparted to delete sda2 and grow sda1 into the now unused space.

Of course it may be harder depending on how you laid out the partitions.
Could you post a screen shot of GParted?

---

### Post by Post Monkeh on 2009-07-19
not at home at the minute (posting from my phone) so i can't get into gparted, but i know home is on the last partition (well before my swap partitions) merging the partitions should be handy enough, i just wasn't sure if i could remove the references to the seperate partitions. I'll give it a go when i get an hour to play with it. Cheers.

---

### Post by Post Monkeh on 2009-07-20
ok, that's buggered it.

i'm back on ok, but i can't open any apps that require root authentication.  i dunno if i've screwed up my user groups or if it's because i moved the usr directory, but when i try to open any application that requires root priviledges, i see the "starting administrative application" box qappear on my task bar, but i don't get asked for a password.

when i try to sudo anything in a terminal, i get told "sudo: must be setuid root"
if i try to "su" to get a root terminal, it asks me for a password, but tells me "su: Authentication failure"


here's my fstab before i moved the partitions.

```
UUID=09806e27-3a9e-4489-b4ab-42dbc8e3dbf6 swap swap sw 0 0
UUID=7294dc46-ff3c-4bd4-86a5-76df06044730 swap swap sw 0 0
UUID=875c05e9-f9cb-406a-bad1-7cfc1c66f45a / ext3 defaults 0 1
UUID=1e845f49-f701-4afb-bc48-bc44600f0268 /opt ext3 defaults 0 2
UUID=bcc8cb8f-881d-4b3d-9df5-fce6ed43ae70 /usr ext3 defaults 0 2
UUID=d85c550a-4df4-44b3-822b-22440d4ced7e /home ext3 defaults 0 2
UUID=7e15589a-b426-4c97-b1ba-ed68a5913b5f swap swap sw 0 0
```


and after

```
UUID=09806e27-3a9e-4489-b4ab-42dbc8e3dbf6 swap swap sw 0 0
UUID=7294dc46-ff3c-4bd4-86a5-76df06044730 swap swap sw 0 0
UUID=875c05e9-f9cb-406a-bad1-7cfc1c66f45a / ext3 defaults 0 1
UUID=d85c550a-4df4-44b3-822b-22440d4ced7e /home ext3 defaults 0 2
UUID=7e15589a-b426-4c97-b1ba-ed68a5913b5f swap swap sw 0 0
```

i also have an "fstab-disk-manager-save" that i presume is just a backup from some adjustment i've made in the past

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=875c05e9-f9cb-406a-bad1-7cfc1c66f45a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d85c550a-4df4-44b3-822b-22440d4ced7e /home           ext3    relatime        0       2
# /dev/sda11
UUID=1e845f49-f701-4afb-bc48-bc44600f0268 /opt            ext3    relatime        0       2
# /dev/sda12
UUID=bcc8cb8f-881d-4b3d-9df5-fce6ed43ae70 /usr            ext3    relatime        0       2
# /dev/sda7
UUID=8b41094b-5847-41ca-a2ee-87cfa378794f none            swap    sw              0       0
# /dev/sda8
UUID=09806e27-3a9e-4489-b4ab-42dbc8e3dbf6 none            swap    sw              0       0
# /dev/sda9
UUID=7294dc46-ff3c-4bd4-86a5-76df06044730 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

one thing is, i had to copy the files and immediately merge the partitions because my root partition only had 4gb free and the usr folder had 6.3gb in it..

well i suppose i could have just merged the 10gb opt partition but i thought in for a penny, in for a pound, i made sure everything copied but obviously something has gone wrong.

---

### Post by Post Monkeh on 2009-07-20
as an update. i checked my account settings. everything was fine - i have admin priviledges. it just looks like the admin privileges don't give you admin priveleges lol

---

### Post by louieb on 2009-07-20
My bad. I should have pointed out to copy in such a way that mode, ownership and permissions are preserved.  with the cp command its the -p option.  

Under what id did you do the copy? yours or sudo or root? Afraid it could be difficult to get permissions restored. As a start owner should be root with full permissions. All others should have read and execute.

---

### Post by Post Monkeh on 2009-07-20
bit late to tell me that now :P

oh well. live and learn. i used -vR so i could make sure everything was copied, i didn't know i should have retained permissions, but i will next time.

i used the live cd installer, so it wasn't my account, but it wasn't root i don't think.

i've re-installed anyway, i guessed it would be a pain even if it was repairable.  i had my home folder on a seperate partition anyway so i just have to reinstall my programs which isn't a massive problem since i got most of it straight from add/remove or synaptic anyway.

---

