---
title: "I broke it (drive mount options), help me fix it? :)"
date: 2008-09-29
forum: Hardware
---

### Post by mfeltman on 2008-09-29
Hey folks.

I was playing around with my external Maxtor drive which in a previous life was the backup volume for my Mac OS X machine.  It's formatted HSF+, and Ubuntu was mounting it as read-only which was a major drag.

So, I went into the drive properties and in the little "mounting options" text box, I typed 'rw', then unmounted and attempted to re-mount.

Oops.  "Invalid mounting options, cannot mount volume", Ubuntu says.

I can't get back to the drive properties dialog now to undo what I did, because when I try, Ubuntu attempts to mount the volume I'm right-clicking on and BAM, error, brick-wall.

Where can I fix this?  The drive doesn't even appear in /etc/fstab, so please don't tell me to go there.  Thanks!

---

### Post by mfeltman on 2008-09-30
Nobody?  Bueller?

---

### Post by Idefix82 on 2008-09-30
Can you provide the contents of your /dev directory?

---

### Post by mfeltman on 2008-09-30
Ack!  I just went to pull it out of my laptop bag but it's securely docked on my desk at home...

I'll put it up this afternoon...  sorry, thanks for attempting to help anyway!

If I were going to guess, my /dev directory would contain /sda1, /sda2, sdb3, and sdb5.  sdb3 & 5 are the volumes on my external Maxtor recognized by Ubuntu (there's some other "unpartitioned" or "unknown" space on there that I know nothing about.

---

### Post by mfeltman on 2008-09-30
Whoa.  Double post.

---

### Post by gfk on 2008-09-30
I've done that, can't remember on what though, I've read that you shouldn't do it like how you did.

I'm not sure how to do it the right way though.

Maybe this may help [http://ubuntuforums.org/showpost.php?p=5530231&postcount=44]("http://ubuntuforums.org/showpost.php?p=5530231&postcount=44")
Or this [http://ubuntuforums.org/showthread.php?t=842841&highlight=mount+points+drive+properties]("http://ubuntuforums.org/showthread.php?t=842841&highlight=mount+points+drive+properties")
Maybe this [http://ubuntuforums.org/showthread.php?t=663774&highlight=mount+points+drive+properties]("http://ubuntuforums.org/showthread.php?t=663774&highlight=mount+points+drive+properties")

---

### Post by Idefix82 on 2008-09-30
Well, if you know the name of the partition you want to mount you should try something like
```

sudo mkdir media/annoyingHD
sudo mount -r sdb3 /media/annoyingHD
```
and similarly for sdb5 with a different mount point like "annoyingHD2". Obviously you can change "annoyingHD" to "veryAnnoyingHD" :)

---

### Post by mfeltman on 2008-09-30
Thanks!  I'll give it a try when I get home.

Once I can mount it, I need to figure out how to permanently mount it as writable.  From what I've found, Ubuntu DOES support writing to HFS+ so I'm not sure why it mounts as read-only.  There's some wacky permissions issues, too, where I can't even read from certain directories (but can from others, even though the owner of all the directories should be the same.)

I tried a sudo chown -r on the drive but it was read only, so I modified the mounting options....

;-)

---

