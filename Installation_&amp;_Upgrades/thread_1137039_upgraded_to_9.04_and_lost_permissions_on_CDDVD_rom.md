---
title: "upgraded to 9.04 and lost permissions on CD/DVD roms"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by mrdak on 2009-04-25
In the dvd drive properties it just says permissions are unknown. The drives mount with a disk but will not function.  By the way, the upgrade went pretty smooth except for this. But it's only been a day ;). 

Is there a terminal command for all permissions?
Thanks

---

### Post by mrdak on 2009-04-25
bump

---

### Post by mrdak on 2009-04-25
I hope it's cool to bump my question TTT  

I need help with setting permissions ?_______  YES?

---

### Post by Black_Wolf_92 on 2009-04-25
try this: Basically, i've never had troubles with CD permissions, but these is the usual permissions command for OTHER mounted media, so it should work.

You've got 2 things i want you to try. FIRST type this in the console.
> sudo gedit /etc/fstab
And look at the sdc0 line, mine looks like this:
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

If yours is different, make a BACKUP of your fstab file, and paste my line on yours. If it doesn't fix the problem, just grab the line from your backup, and put it back over the top again (best not to create another issue if this doesn't fix the problem).


IF IT DIDN"T FIX YOUR PROBLEM:
type this into your console

> sudo chmod a+x /media/cdrom
sudo chmod a+x /media/cdrom0
sudo chmod -R 777 /media/cdrom
sudo chmod -R 777 /media/cdrom0


These codes are basically allowing ALL PERMISSIONS to both the mount points of the cdrom. This one SHOULD fix your problem, however the first one is much neater, and easier to reverse things if it goes wrong.

---

### Post by bsmith1051 on 2009-04-25
It's more likely something that failed to update in 'fstab' that something in the permissions.  Which version of Ubuntu did you upgrade from?  At some point in the past 2(?) versions they changed the labeling system, but my 'fstab' didn't get updated automatically.

FYI - here's what my 'fstab' looks like:
```
> gksudo gedit /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by mrdak on 2009-04-26
well here's the fstab file. I didn't try anything yet. 

Also, I went from 8.10 to 9.04 automatically, and the drives worked just fine prior to that.

Thanks......

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=87d876e6-62dc-4224-9925-e5207ae5de55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd3
UUID=5703d8a1-8667-4087-a1d3-f45c57ffd33e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mrdak on 2009-04-26
ttt

---

### Post by mrdak on 2009-04-26
It seems that only certain video dvds won't play.... 

Mplayer will play some of my dvd's. But like the following......

like Jeff Beck Live at Ronnie scotts, will not work. I get the permissions error and VLC opens the main title, it starts to play but crashes. What DVD player could someone suggest. Or any help with the permissions would be most appreciated.

tyvm

---

### Post by mrdak on 2009-04-26
bump

---

### Post by Black_Wolf_92 on 2009-04-27
Your problem could be your dvd codecs (to deal with the encryption)

Google "libdvdcss2 and w32codecs ubuntu" i guarentee you'll find a guide better than what i can explain.

---

### Post by bsmith1051 on 2009-04-27
How old is your DVD drive?  When I upgraded from 8.04 to 8.10 I had 'new' problems with DVDs, and eventually I just bought a new drive and that solved it.

I think the ATA compatibility varies from kernel to kernel?

---

### Post by mrdak on 2009-04-28
> **Black_Wolf_92 said:**
> Your problem could be your dvd codecs (to deal with the encryption)

Google "libdvdcss2 and w32codecs ubuntu" i guarentee you'll find a guide better than what i can explain.


Excellent................. That did it and here's the link

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 


Thanks B W 

mrdak

---

### Post by Black_Wolf_92 on 2009-04-29
great, good to see you solved the problem ;)

Most problems are getting resolved now, might make the jump to jaunty soon on my main desktop

---

