---
title: "HDD Spindown problem"
date: 2010-12-07
forum: Hardware
---

### Post by Creed007 on 2010-12-07
Hey Guys,

I'm very new to the whole Linux stuff. Yesterday I installed Ubuntu on my homeserver. It works very fine, but now I discovered a problem (well it may isn't a problem to everybody but I don't like this^^).
Ubuntu seems to be unable to spin down the HDDs that are idling for a cuple of hours. My server is running 24/7 and at least to save a minumum of energy I want my HDDs to spin down :D

I googled a few hours but I didn't found something proper...
The only thing was this:
[http://www.spencerstirling.com/computergeek/powersaving.html#harddrive](http://www.spencerstirling.com/computergeek/powersaving.html#harddrive)
But me as a noob has a few problems with this ^^

Ans something other: my hdd's are crypted with TrueCrypt so I can't mount them like the guy in the article told me... (or?)

Please help me or tell me a distribution you kown that can handle the spindown of my HDDs (SATA HDDs).

Thanks a lot and please excuse my strange english.. I just learned this in school xD

greetz,
Creed007

---

### Post by matt_symes on 2010-12-07
Hi

Have a look at the command

hdparm

from man  hdparm

> 
-B     Query/set Advanced Power Management feature, if the  drive  sup&#8208;
              ports  it.  A  low value means aggressive power management and a
              high value means better performance.   Possible  settings  range
              from  values  1 through 127 (which permit spin-down), and values
              128 through 254 (which do not permit  spin-down).   The  highest
              degree  of power management is attained with a setting of 1, and
              the highest I/O performance with a setting of 254.  A  value  of
              255 tells hdparm to disable Advanced Power Management altogether
              on the drive (not all drives support disabling it, but most do).


Might give you a starting place.

Kind regards

---

### Post by Creed007 on 2010-12-07
Yea, I have read something about this, but I thought this will just work if Ubuntu isn't accessing the HDD.
What I read was that Ubuntu is doing this automaticaly and that I have to mount my drives with this special params:

/dev/hdd1 /mount_directory reiserfs rw,noatime 0 0

My problem is that I don't have usual drives, because of TrueCrypt. Truecrypt mounts the drives automaticaly after entering the password ... :/

---

### Post by matt_symes on 2010-12-07
Hi

Ahh yes. I don't know much about truecrypt i'm afraid, so i cant really help there.

I will give you a friendly bump though in the hope some else will know. ;)

***Bump***

EDIT: As an aside, have  you asked on the truecrypt forums? You might find out how it gets mounted after you enter the password and change the mount options.
EDIT2: I did not read the link you put in your first post until  now so it looks like  i gave you duplicate advice. Sorry about that. hdparm is the way i have seen it done before.

Kind regards

---

### Post by Creed007 on 2010-12-07
I discovered that I can add mount parameters in TrueCrypt so I added this one:
noatime 0 0
I hope this is correct?

Well I will see if they will be spinned down in 30 min (that was the default time I guess...)

I'll edit here to give you a report.

Thanks for your help btw.

P.S.: if this won't work, do you know any other distribution that maybe fits to what I want?

greetz

---

### Post by matt_symes on 2010-12-07
Hi

> noatime 0 0

Yes, looks good. It will not  update the inode access time all the time. 

It will not run any fsck checks on the drive at all though. Maybe this is what you want with truecrypt but i am not 100% sure.

Kind regards

---

### Post by Creed007 on 2010-12-07
No, it don't seems to work but maybe it's my fault... I will test some other configs tomorrow and tell you the results.
I hope we can handle this :D

// I can't get it work like I want it to work :(

greetz
Creed007

---

